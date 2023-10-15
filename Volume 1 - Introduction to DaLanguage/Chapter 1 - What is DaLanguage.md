# What is DaLanguage?

DaLanguage is a general purpose programming language with a focus on flexibility
and expressibility. DaLanguage aims to make it possible to express any and all
formal constructs with code. As a result, DaLanguage has a dynamic syntax and
semantics.

With DaLanguage you can manipulate and transform your programs in anyway you
see fit. A single program can either be interpreted, compiled, transpiled, or in
general be used to create other structured output that is based on the
*description* of the computation, not what the *result* of the computation is.

## Example

For example, take the following simple program written in the instruction layer,
as described in part 1:

```
(add, num1, num2)
{
    add(num1, num2);
}
```

DaLanguage allows us to use this program in a variety of ways, here are some
contrived ones, in increasing order of absurdness and fun:

### Interpretation

The simplest way to use this program is to interpret it:

- Set `add` to some instruction that takes two numbers, adds them and prints the
  result. An instruction in this case is some action we have the tool working
  with DaLanguage take when the instruction is executed. See part 1 for details;
- Set `num1` and `num2` to some numbers.

### Compilation

Define a way to compile this program:

- Set `add` to an instruction that takes in two memory addresses, or registers,
  whatever you want, and:
    - Emits an opcode corresponding to some ISA's `ADD` instruction;
    - Emits the memory addresses/register numbers/whatever for its values.
      Values are the things inside the instruction's brackets, see part 1 for
      details;
    - Emits a single or multiple opcodes for printing the result in the same ISA.
- Set `num1` and `num2` to memory addresses/registers/literals/whatever.

With this we can easily create a compiled binary for any ISA, we just need the
proper definitions for our instructions, however they may be fed into the tool
we're using for DaLanguage.

### Transpilation

Define a way to transpile this program, for simplicity we'll transpile to python,
however the same method can be used to transpile to any other language:

- Set `add` to be an instruction that writes to `stdout` the string:
  `"print($num1 + $num2)"`, where `$num1` and `$num2` are the values given to
  the instruction;
- Set `num1` and `num2` to some python expression that evaluates to a number.

The program would now output a python program that does the computation for us.

### Lookup

Assume we have a table of precomputed values, define:

- `add` to be an instruction that looks up the value pair and prints the
  result;
- `num1` and `num2` to be numbers for which we have precomputed addition for
  in our table.

### Request

Assume we have a web server somewhere that we may contact to do the computation
for us, define:

- `add` to send a request to our server with the values as request parameters.
  Once it receives a response, it prints it;
- `num1` and `num2` to some numbers in a format our server can understand.

Of course in this case we'd need to handle a lot more, like what happens if
we don't get a response or we get an error? What if the server is unavailable?
Or a whole slew of other errors that push this near the top of the absurdness
list.

### Synthesis

This example is rather fictitious, but still plausible. We'll assume that there
exists some machine capable of creating hardware on the fly given proper control
instructions. We won't get into details for example's sake. We don't consider
HDLs as they'd be in the same vein as transpilation.

Define the following:

- `add` to be an instruction that controls our imaginary machine such that it
  creates a circuit that can add two numbers. Set the inputs to this circuit to
  be the values given to the instruction, that we assume are also instructions.
  Finally make the machine synthesize some sort of way to display the output of
  addition, connect the output of the addition circuit to the input of the
  display;
- `num1` and `num2` to be some instructions that make the machine create an
  input method for numbers, maybe a button or a hard-coded constant. Connect the
  output of this method to the given value, which we assume is an input.

We've now created hardware from our software. Again, this scenario is highly
contrived but still theoretically possible.

## Conclusion

DaLanguage may be bent over, crumpled and topologically morphed from a doughnut
into a cup without breaking. And all of that with its simplest layer, the
instruction layer. We'd be able to do so much more with the other layers. For
example, we could write snappier expression with the meta layer, parse other
languages and manage our different definitions of `add`, `num1` and `num2`
within DaLanguage without any tool specific shenanigans. With the trait layer
we can be sure DaLanguage won't break with some maneuver, we could make our
prose machine verifiable and better communicated to other developers and set the
groundwork for more expansions in the ways we're able to use the simple number
addition instruction we defined.
