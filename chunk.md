# Chunk
Chunk follow a type-length-value structure:

Type | Name
--- | ---
unsigned4 | Chunk Type ID
unsigned4 | Chunk Length
void[Chunk Length] | Chunk Data

## Chunk Type ID
A four-word identifier that specifies the type of the chunk.

It normally uses four uppercase ASCII values, however it is not a string as big-endian files have the names backwards (such as FORM being MROF).

## Chunk Length
The size of the Chunk Data.

## Chunk Data
The contents of the chunk. Whatever it describes depends on the chunk type.