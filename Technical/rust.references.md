references 

To avoid having to create new variables to get around Rust's dropping of values we can use references.

A reference is like a pointer in that its an address we can follow to access the data stored at that address. A reference is guaranteed to point to a valid value of a particular type for the life of that reference.

```rust
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1);

    println!("The length of '{}' is {}.", s1, len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

In the example above:
- We pass a reference to the string S1 to the calculate length function with the `&` operator
- This allows you to refer to a value without taking ownership of that value
- When you pass a reference to a function you can not modify the value

The following snippet will not compile:
```rust
fn main() {
    let s = String::from("hello");

    change(&s);
}

fn change(some_string: &String) {
    some_string.push_str(", world");
}
```

- To modify the value you need to make the reference mutable like in the code sample below:

```rust
fn main() {
    let mut s = String::from("hello");

    change(&mut s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```

- This comes with one large restriction there can only be ONE mutable reference to a value. Trying to initiate two will give a compiler error
	- This allows for mutation but in a very controlled fashion, this also however prevents data races at compile time.
	- Curly braces can be used to force a new scope, to allow for mutliple mutable references, the mutable references just can not be Simultaneous
- Rust also  enforces a similar rule for combining mutable and immutable references the code below results in an error:
```rust
fn main() {
    let mut s = String::from("hello");

    let r1 = &s; // no problem
    let r2 = &s; // no problem
    let r3 = &mut s; // BIG PROBLEM

    println!("{}, {}, and {}", r1, r2, r3);
}
```

A references scope starts where it is introduces and goes till the last time it is used. For example the following code does not produce a compiler error.

```rust
fn main() {
    let mut s = String::from("hello");

    let r1 = &s; // no problem
    let r2 = &s; // no problem
    println!("{} and {}", r1, r2);
    // variables r1 and r2 will not be used after this point

    let r3 = &mut s; // no problem
    println!("{}", r3);
}

```