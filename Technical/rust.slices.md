Slices

String Slices

- Slices let us reference only part of an array.
 Example:
 ```rust
let s = String::from("hello world");

let hello = &s[0..5];
let world = &s[6..11];
```

Create slisces with the following bracket syntax:

`[starting index ... ending index]`
 - Starting index: first position in the slices (inclusive)
 - ending index: One more than the last position in the slice (exclusive)
 - `&s[0..5]` includes the indexes `[0,1,2,3,4]`
- `&s[0..2]` is equivalent to  `&s[..2]`
	- starting at 0 the first index can be dropped
- Similar to the 0 index, indexing to the last element can be done like so:
	- `&s[3..len]` == `&s[3..]`
- Both values can be dropped to take a slice of the entire string:
	- `&s[..]`