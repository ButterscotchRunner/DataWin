# GameMaker QOI (GMQOI)
GameMaker Studio 2 (TODO: which version exactly?) introduced a propietary extension of the [Quite OK Image format (QOI)](https://qoiformat.org) for storing texture data. Differences with the vanilla version include:
* Values are endian dependent instead of always big-endian
* Images are always RGBA instead of being able to choose between RGB and RGBA
* Different index hashing function (`(Red xor Green xor Blue xor Alpha) modulo 64`)

Type | Name
--- | ---
u32 | Magic (`qoif`)
u16[2] | Dimensions (Width, Height)
u32 | Data Length
void[Data Length] | Operations Data

## Magic
Format identifier (0x716F6966, `qoif`). Do note that it's probably affected by endianness since little-endian WADs have those stored backwards (`fioq`).

## Dimensions
How big is the image. Unlike vanilla QOI, there are stored as u16.

## Data Length
Length of the encoded data.

## Operations Data
List of operations needed to decode the image, see below for operations.

## Operations
### GMQOI_OP_INDEX

7 6 | 5 4 3 2 1 0
--- | ---
0 0 | Index

### GMQOI_OP_DIFF_8

7 6 | 5 4 | 3 2 | 1 0
--- | --- | --- | ---
1 0 | Red | Green | Blue

All values are signed, storing from -2 to 1, inclusive.

### GMQOI_OP_DIFF_16
7 6 5 | 4 3 2 1 0 | 7 6 5 4  | 3 2 1 0
--- | --- | --- | ---
1 1 0 | Red | Green | Blue

All values are signed.

Red can store from -16 to 15, inclusive.

Green and Blue can store from -8 to 7, inclusive.
### GMQOI_OP_DIFF_24

7 6 5 4 | 3 2 1 0 7 | 6 5 4 3 2 | 1 0 7 6 5 | 4 3 2 1 0
--- | --- | --- | --- | ---
1 1 1 0 | Red | Green | Blue | Alpha

All values are signed, storing from -16 to 15, inclusive.

### GMQOI_OP_RUN_8

7 6 5 | 4 3 2 1 0
--- | ---
0 1 0 | Run

### GMQOI_OP_RUN_16

7 6 5 | 4 3 2 1 0 7 6 5 4 3 2 1 0
--- | ---
0 1 1 | Run

### GMQOI_OP_COLOR

7 6 5 4 | 3 | 2 | 1 | 0
--- | --- | --- | --- | ---
1 1 1 1 | Read Red? | Read Green? | Read Blue? | Read Alpha?

The amount of bytes needed to read is dependent on how many bits are enabled, for example:
* if not Read Red, don't do anything
* if Read Green, then the next byte is the Green value
* if not Read Blue, don't do anything
* if Read Alpha, then the next byte is the Alpha value

The length of the operation of the example above would be 3 bytes (operation + Green byte + Alpha byte).

## bzip2-compressed GMQOI (QOZ2)
Basically a GMQOI image compressed with [bzip2](https://sourceware.org/bzip2/).

Type | Name | Condition
--- | --- | ---
u32 | Magic (`qoz2`) | 
u16[2] | Dimensions (Width, Height) |
u32 | bzip2 Stream Length | GameMaker 2022.5 or later
void[bzip2 Stream Length] | bzip2 Stream

### Magic
Format identifier (0x716F7A32, `qoz2`). Like GMQOI, probably endian-sensitive. On little-endian WADs it's stored as `2zoq`.

### Dimensions
How big is the image.

### bzip2 Stream Length
Length of the bzip2 stream. Exclusive to GameMaker version 2022.5 and later.

### bzip2 Stream
Contains the GMQOI data in bzip2 compressed form.