# GEN8
General info of data.

Type | Name | Condition
--- | --- | ---
boolean | Is Debugger Disabled? |
u16 | WAD Version |
void[2] | Padding |

If the 8 >= WAD Version and the remaining bytes are 84:

Type | Name | Condition
--- | --- | ---
nullUTF8* | File Name |
u32 | Last Object |
u32 | Last Tile |
u32 | Game ID |
u8[16] | DirectPlay GUID |
u32[2] | Default Window Size (Width, Height) |
u32 | Information |
u32 | License CRC32 |
u8[16] | License MD5 |
void[4] | Unknown | Not read by the Runner
u32 | Room Order Count |
s32[roomOrderCount] | The order of the rooms |

Anything Else:

Type | Name | Condition
--- | --- | ---
nullUTF8* | File Name |
nullUTF8* | Configuration | WAD Version is 9 or greater
u32 | Last Object |
u32 | Last Tile |
u32 | Game ID |
u8[16] | DirectPlay GUID |
nullUTF8* | Game Name | WAD Version is 9 or greater
u32[4] | GameMaker Version (Major, Minor, Release, Build) | WAD Version is 9 or greater
u32[2] | Default Window Size (Width, Height) |
u32 | Information |
u32 | License CRC32 |
u8[16] | License MD5 |
s32 | Timestamp | WAD Version is 8 (or less?)
s32 | Timestamp | WAD Version is 12 or less
u64 | Timestamp | WAD Version is 13 or greater
void[4] | Padding | WAD Version is 12 or less
nullUTF8* | Display Name |
u64 | Active Targets | WAD Version is 11 or greater
u64 | Function Classifications | WAD Version is 12 or greater
u32 | Steam App ID | WAD Version is 13 or greater
u32 | Debugger Port | WAD Version is 14 or greater
simpleList | Room Order |
void[24] | Unknown | GameMaker Version Major is 2 or greater (GameMaker Studio 2+)
