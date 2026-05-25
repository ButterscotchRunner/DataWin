# GEN8
General info of data.

## Contents
Type | Name | Condition
--- | --- | ---
boolean | Is Debugger Disabled? |
unsigned2 | WAD Version |
void[1] | Padding |
nullUTF8* | File Name |
nullUTF8* | Configuration | WAD Version is 9 or greater
unsigned4 | Last Object |
unsigned4 | Last Tile |
unsigned4 | Game ID |
unsigned1[16] | DirectPlay GUID |
nullUTF8* | Game Name | WAD Version is 9 or greater
unsigned4[4] | GameMaker Version (Major, Minor, Release, Build) | WAD Version is 9 or greater
unsigned4[2] | Default Window Size (Width, Height) |
unsigned4 | Information |
unsigned4 | License CRC32 |
unsigned1[16] | License MD5 |
signed4 | Timestamp | WAD Version is 8 (or less?)
signed4 | Timestamp | WAD Version is 12 or less
unsigned8 | Timestamp | WAD Version is 13 or greater
void[4] | Padding | WAD Version is 12 or less
nullUTF8* | Display Name |
unsigned8 | Active Targets | WAD Version is 11 or greater
unsigned8 | Function Classifications | WAD Version is 12 or greater
unsigned4 | Steam App ID | WAD Version is 13 or greater
unsigned4 | Debugger Port | WAD Version is 14 or greater
simpleList | Room Order |
void[24] | Unknown | GameMaker Version Major is 2 or greater (GameMaker Studio 2+)
