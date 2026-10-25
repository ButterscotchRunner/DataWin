# Bytecode (WIP!)

In WAD version 8 and later, Bytecode is stored in the CODE chunk, after the list of addresses in the beginning of the chunk, and as indicated on each code's offset field.

The bytecode is composed by opcodes:
u32     | u32
------- | ---
Op word | Other information?

## Op word
31..24 | 23..20 | 19..16 | 15..0
------ | ------ | ------ | -----
Opcode | Type 2 | Type 1 | Extra

TODO: Does this order also apply for big endian WADs?

TODO: Only checked on WAD version 16 for v1.4.9999, what about other versions?

## Other information?
