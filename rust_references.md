In Rust, references are created explicitly with the &
operator, and dereferenced explicitly with the * operator:

// Back to Rust code from this point onward.

let x = 10;
let r = &x; // &x is a shared reference to x
assert!(*r == 10); // explicitly dereference r

To create a mutable reference, use the &mut operator:

let mut y = 32;
let m = &mut y; // &mut y is a mutable reference to y
*m += 32; // explicitly dereference m to set y's value
assert!(*m == 64); // and to see y's new value

Since references are so widely used in Rust, the . operator
implicitly dereferences its left operand, if needed:
struct Anime { name: &'static str, bechdel_pass: bool };
let aria = Anime { name: "Aria: The Animation", bechdel_pass:
true };
let anime_ref = &aria;
assert_eq!(anime_ref.name, "Aria: The Animation");
// Equivalent to the above, but with the dereference written out:
assert_eq!((*anime_ref).name, "Aria: The Animation");

Vec’s sort method takes a mutable reference to the vector,
so these two calls are equivalent:

let mut v = vec![1973, 1968];
v.sort(); // implicitly borrows a mutable reference to v 
(&mut v).sort(); // equivalent, but more verbose

In a nutshell, whereas C++ converts implicitly between
references and lvalues (that is, expressions referring to
locations in memory), with these conversions appearing
anywhere they’re needed, in Rust you use the & and *
operators to create and follow references, with the
exception of the . operator, which borrows and
dereferences implicitly.
