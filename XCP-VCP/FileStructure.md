# XCP File structure

Havent found much, but i do know a bit about the header

# Sources
My own decompilation, and this forum post: https://www.casiopeia.net/forum/viewtopic.php?f=25&t=1678

# Header
First 10 bytes - Must be the string "VCP.XDATA". (C-Style)\
Next 8 bytes - ASCII encoded hex. Code checks if the value is 0x5f4d4353 or 0x5f464c53. Probably file type? HEX to ASCII decodes first to "_MCS" and second to "_FLS"\
Next 2 bytes - Length of string following, including null-terminator.\
Next n-bytes - String of folder name, such as "main"\
Next 2 bytes - Length of string following, including null-terminator.\
Next n-bytes - String of variable name\
Next 8 bytes - Length of some following bytes\
Next n-bytes - Dont really know\
Next 8 bytes - Length of some following bytes\
Next n-bytes - Dont really know\
Next 2 bytes - Checksum

# Weird quirks
Most "Integers" in the header are ASCII-Encoded Hex. While this on its own is not too absurd, the fact that the text "_MCS" and/or "_FLS" is encoded in this way is weird. The code also stores this "text" in an integer, although on the calculator this is not too absurd - it would save a byte and the developers used a embedded RTOS that would normally see use in alot lower spec applications.
