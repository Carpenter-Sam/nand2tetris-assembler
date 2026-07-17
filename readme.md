This project has moved to: Carpenter-Sam/nand2tetris
This project has moved to: Carpenter-Sam/nand2tetris
This project has moved to: Carpenter-Sam/nand2tetris
This project has moved to: Carpenter-Sam/nand2tetris


# Nand2Tetris Assembler

This is an assembler written in Rust for Week 6 of the Nand2Tetris course.

The assembler translates Hack assembly language into Hack machine code. It performs two passes over the input file:

1. **First pass** – Searches for labels and records their instruction addresses.
2. **Second pass** – Translates assembly instructions into machine code and writes the output to a file.

The assembler ignores comments (`//`), blank lines, and most whitespace.

## A-Commands

A-commands are values in the form:

```text
@value
```

* If `value` is a number between `0` and `32767` (inclusive), it is converted directly into binary.
* Otherwise, `value` is treated as a symbol.

  * Existing labels and symbols are resolved using a symbol table.
  * New symbols are assigned RAM locations according to the Hack specification.

## C-Commands

C-commands have the form:

```text
dest = comp ; jump
```

where:

* `dest` (optional) specifies where the result is stored.
* `comp` specifies the computation to perform.
* `jump` (optional) specifies a jump condition.

The assembler splits each C-command into its component fields, translates them individually, and then combines the resulting machine-code bits into the final instruction.
For more details, including a deeper explanation as to how this assembler and the Nand2Tetris assembly language in general works, please visit the Nand2Tetris site:

https://www.nand2tetris.org/

## How to run
```bash
cargo run Program.asm
```

The machine code version will be output to `output.txt`.
Example programs can be found in the `txtfiles` folder.

## Notes

This was one of my first Rust projects and was developed fairly quickly as part of the Nand2Tetris course. It is not intended to be a polished production project, and error handling is fairly minimal.
