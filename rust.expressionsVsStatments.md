Rust has both expressions and statements.

Expressions
- return a value

Statements
- do not return a value

lets cann not equal another let value because `let` is a statement. however lets CAN equal an expression 

examples:
```rust
fn main() {
    let y = {
        let x = 3;
        x + 1
    };

    println!("The value of y is: {y}");
}
```
- The block within the `{}` evaluate to a value and is thus an expression
- notice no `;` at the end of the expression


