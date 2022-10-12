Functions
- functions do not need to be defined in a specific order as long as the function call has the proper scope to see the function
```rust
fn main() {
    println!("Hello, world!");

    another_function();
}

fn another_function() {
    println!("Another function.");
}
```

Parameters

```rust
fn main() {
    another_function(5);
}

fn another_function(x: i32) {
    println!("The value of x is: {x}");
}
```

Return Values

- return values are not names in rust must declare their type with an arrow
- The return keyword can be used to return early but most of the time implicit returns are used as the last expression in a function
- ending the last line of a function with a semi-colon gives a compile error

```rust
fn five() -> i32 {
    5
}

fn main() {
    let x = five();

    println!("The value of x is: {x}");
}

```