# Emulator Coding style

While i strongly suspect the code of the emulator is a big copy-paste, decompiling (not dissasembling!) the firmware of the calculator is easier said than done.\
SH-4 support in Ghidra is quite basic and has some big flaws making code harder to read and understand, most notably not correctly recognizing the immideate pools and making most function calls calls to a function pointer.\
Combined with the weird memory map of the calculator makes Ghidra almost impossible to use, as Ghidra will not find most functions.\
\
IDA will find most, but not all functions, and will, for the most part, correctly dissasemble them (IDA recognizes the immideate pools), but IDA doesnt support decompiling SH-4 assembly.\
\
\
All this makes it easier to just decompile the emulator using IDA.

# Weird emulator quirks

The emulator is probably compiled without Optimizations; "Dead" or redundant code is quite easy to spot, although only Ghidra sees it (IDA probably "optimizes" them out? Or maybe Ghidra is bugged?)\
Running the emulator in a debugger is almost impossible; The emulators code seems to have in and out opcodes in it. I have yet to fully investigte this though.
