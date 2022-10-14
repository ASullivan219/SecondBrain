Control Flow

IF statements:

```rust
fn main() {
    let number = 3;

    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```

- conditional must be a boolean, the following will not compile:

```Rust
fn main() {
    let number = 3;

    if number {
        println!("number was three");
    }
}
```

- Will not try to automatically conver non-booleans to a boolean type

If in a let statement;
```rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };
    println!("The value of number is: {number}");
}
```

both arms of the if conditional must be the same type or else you get a compilation error.

i.e `let number = if condition { 5 } else {"six"}`

Will give a compilation error.