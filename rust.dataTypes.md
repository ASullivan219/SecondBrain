Datatypes

- immutable by default

Floating-Point
```rust
fn main() { 
	let x = 2.0; // f64 let y: f32 = 3.0; // f32 
}
```

The Boolean-Type
```rust
fn main() { 
	let t = true; 
	let f: bool = false; // with explicit type annotation 
}
```

Character Types
```rust
fn main() {
    let c = 'z';
    let z: char = 'ℤ'; // with explicit type annotation
    let heart_eyed_cat = '😻';
}
```

- capable of unicode and utf-8

Tuples

```rust
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

```rust
fn main() {
    let tup = (500, 6.4, 1);

    let (x, y, z) = tup;

    println!("The value of y is: {y}");
}
```

```rust
fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;

    let six_point_four = x.1;

    let one = x.2;
}
```

Arrays
- every elementmust have the same type
```rust
fn main() {
    let a = [1, 2, 3, 4, 5];
}
```

- cannot grow or shrink in size. Use vectors from the standard library if you need an array that can grow
```rust
#![allow(unused)]
fn main() {
let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
}

```

```rust
#![allow(unused)]
fn main() {
	let a: [i32; 5] = [1, 2, 3, 4, 5];
}
```

```rust
#![allow(unused)]
fn main() {
	let a = [3; 5];
}
```
- above initializes an array to contain the same value for each element

Accessing Array Elements

```rust
fn main() {
    let a = [1, 2, 3, 4, 5];

    let first = a[0];
    let second = a[1];
}
```
- Accessing values outside of the length of the array will give a similar error:
```
thread 'main' panicked at 'index out of bounds: the len is 5 but the index is 10', src/main.rs:19:19 note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
```
- This kind of chek is not always done in low level programming languages. THey will allow you to access memory outside of the bounds of the array.
