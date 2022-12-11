# personal notes
the most interesting part to me is the virtual machine. basically that means simulate
a underlying os. with this ability to customize runtime, it can unlock many potentials.

## how a virtual machine is implemented

for a virtual machine to work, it has to 
* able to branching, looping, this indicates it must has a conditional jump ability to some code address
* call subroutine, this is done using function frame to booking values at registers or some other medium
* store computation result. in a normal stack based machine, this is stored at regsiters. 

![virtual machine](virtual%20machine.svg)


# lust: Lua in Rust

This project implements a parser, compiler, and virtual machine
evaluator for a minimal subset of Lua. It is written from scratch in
Rust.

See the companion blog post, [Writing a minimal Lua implementation
with a virtual machine from scratch in Rust
](https://notes.eatonphil.com/lua-in-rust.html), for a guided
walkthrough of the code.

## Example

```bash
$ cargo build --release
$ cat test/fib.lua
function fib(n)
   if n < 2 then
      return n;
   end

   local n1 = fib(n-1);
   local n2 = fib(n-2);
   return n1 + n2;
end

print(fib(30));
$ time ./target/release/lust test/fib.lua
832040
./target/release/lust test/fib.lua  0.29s user 0.00s system 99% cpu 0.293 total
$ time lua test/fib.lua
832040
lua test/fib.lua  0.06s user 0.00s system 99% cpu 0.063 total
```

## More examples

See the test directory.