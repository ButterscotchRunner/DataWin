# Common types

## Common concepts

### Word size
The minimum size of numbers is 8 bits.

### Signed numbers
Signed numbers are stored using two's complement encoding.

### Endianness
Most of the data files use little-endian encoding, though the PlayStation 3 runner uses big-endian.

This also affect chunk IDs, which means they're probably stored as an unsigned 4-word number instead of 4 characters.

### Pointers
All pointers are absolute positions, with 0 being the start of the file.

Pointers are signified by the aterisk \* symbol after the type name.

### Text
Text is Unicode, encoded using the UTF-8 standard.

## void
An unknown value that uses a single word. Usually used for padding.

## Data types

All of these are affected by endianness.

Name | Word size | Notes
--- | --- | ---
u8 | 1 | Unsigned 8-bit integer. Can store from 0 to 255, inclusive.
u16 | 2 | Unsigned 16-bit integer. Can store from 0 to 65,535, inclusive.
u32 | 4 | Unsigned 32-bit integer. Can store from 0 to 4,294,967,295, inclusive.
u64 | 8 | Unsigned 64-bit integer. Can store from 0 to 18,446,744,073,709,551,615, inclusive.
s8 | 1 | Signed 8-bit integer. Can store from -128 to 127, inclusive.
s16 | 2 | Signed 16-bit integer. Can store from -32,768 to 32,767, inclusive.
s32 | 4 | Signed 32-bit integer. Can store from -2,147,483,648 to 2,147,483,647, inclusive.
s64 | 8 | Signed 64-bit integer. Can store from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807, inclusive.
b32 | 4 | binary32 from IEEE 754
b64 | 8 | binary64 from IEEE 754

## boolean
u8. 0 is "false", while any other number is "true", though 1 is preferred for "true".

## string
A variable-length string of text, terminated with a word of 0.
