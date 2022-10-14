Ownership Rules:
- Each value in Rust has an owner
- There can be only one owner at a time
- When the owner goes out of scop the value is dropped

Explaining Ownership with the string type:

- Rust has two types of strings:
	- Static strings that are known at compile time `let s = "Hello, world"`
	- And dynamic strings that are allocated on the heap at run time, like so: `let mut s = String::from("hello")`

static strings are immutable.

Dynamic strings are mutable like so:
```rust
fn main() {
    let mut s = String::from("hello");

    s.push_str(", world!"); // push_str() appends a literal to a String

    println!("{}", s); // This will print `hello, world!`
}
```

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1;
}
```

Rust does not do deep copying unless specifically implemented for a data structure. In the code above s1 is _moved_ into the s2 pointer. s1 is then invalidated and can not be used.

The following code gives a compilation error:
```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1;

    println!("{}, world!", s1);
}
```

If you do want a deep copy you can use the following syntax:
```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1.clone();

    println!("s1 = {}, s2 = {}", s1, s2);
}
```

Rust has a special annotation called the `Copy` trait that we can place on types that are stored on the stack, as integers are. If a type implements the `Copy` trait, variables that use it do not move, but rather are trivially copied, making them still valid after assignment to another variable.

Rust won’t let us annotate a type with `Copy` if the type, or any of its parts, has implemented the `Drop` trait. If the type needs something special to happen when the value goes out of scope and we add the `Copy` annotation to that type, we’ll get a compile-time error.

Here are some of the types that implement `Copy`:

-   All the integer types, such as `u32`.
-   The Boolean type, `bool`, with values `true` and `false`.
-   All the floating point types, such as `f64`.
-   The character type, `char`.
-   Tuples, if they only contain types that also implement `Copy`. For example, `(i32, i32)` implements `Copy`, but `(i32, String)` does not.

Ownership and functions

```rust
fn main() {
    let s = String::from("hello");  // s comes into scope

    takes_ownership(s); // s's value moves into the function...
                        // ... and so is no longer valid here

    let x = 5;         // x comes into scope

    makes_copy(x);     // x would move into the function,
					// but i32 is Copy, so it's okay to still
                    // use x afterward

} 
// Here, x goes out of scope, then s. But because s's value was moved, nothing
// special happens.

fn takes_ownership(some_string: String) { 
// some_string comes into scope
    println!("{}", some_string);
} 
// Here, some_string goes out of scope and `drop` is called. The backing
// memory is freed.

fn makes_copy(some_integer: i32) { 
// some_integer comes into scope
    println!("{}", some_integer);
} 
// Here, some_integer goes out of scope. Nothing special happens.

```


- returning values can also transfer ownership, but giving and taking ownership can be quite tedious:
```rust
fn takes_and_gives_back(a_string: String) -> String { 
// a_string comes into scope 
	a_string 
// a_string is returned and moves out to the calling function 
}
```
- 