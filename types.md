# Data types

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

## unsigned1
A single word representing an unsigned integer. Can store from 0 to 255, inclusive.

## unsigned2
Two words representing an unsigned integer. Can store from 0 to 65,535, inclusive.

## unsigned4
Four words representing an unsigned integer. Can store from 0 to 4,294,967,295, inclusive.

## boolean
unsigned1. 0 is "false", while any other number is "true", though 1 is preferred for "true".

## nullUTF8
A string of text, terminated with a word of 0.

## binary32
Single-precision floating point number from IEEE 754. Takes up four words.