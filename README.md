# MCPU

------------------------------------------------------------------------------------------------------------------------
 [*] OpCodes
------------------------------------------------------------------------------------------------------------------------

 - Miscellaneous -
 @Instruction(name = "MSC", operands = 1)
 @Operand(bit = 5, name = "Load Page") // If high, use operand as page number and load into CPU
 @Operand(bit = 6-8, name = "MSC Table/Page") // Miscellaneous Table at Line TODO

 - Addition -
 @Instruction(name = "ADD", operands = 1) // Adds value of register provided and accumulator
 @Operand(bit = 6-8, name = "Register Address")

 - Subtraction -
 @Instruction(name = "SUB", operands = 1) // Subtracts value of register provided from accumulator
 @Operand(bit = 6-8, name = "Register Address")

 - AND Gate -
 @Instruction(name = "AND", operands = 2) // Performs AND logic on values of accumulator and register provided
 @Operand(bit = 5, name = "Invert") // If high, perform invert output
 @Operand(bit = 6-8, name = "Register Address")

 - XOR Gate -
 @Instruction(name = "XOR", operands = 2) // Performs XOR logic on values of accumulator and register provided
 @Operand(bit = 5, name = "Invert") // If high, perform invert output
 @Operand(bit = 6-8, name = "Register Address")

 - OR Gate -
 @Instruction(name = "OR", operands = 2) // Performs OR logic on values of accumulator and register provided
 @Operand(bit = 5, name = "Invert") // If high, perform invert output
 @Operand(bit = 6-8, name = "Register Address")

 - Barrel Shift -
 @Instruction(name = "BSH", operands = 1) // Barrel shifts accumulator by amount given right
 @Operand(bit = 6-8, name = "Shift Amount")

 - Increment/Decrement -
 @Instruction(name = "INC", operands = 2) // Increments or decrements register given
 @Operand(bit = 5, name = "Decrement") // If low, increment register provided; if high, decrement register provided
 @Operand(bit = 6-8, name = "Register Address")

 - Store -
 @Instruction(name = "STR", operands = 2) // Store value to destination register
 @Operand(bit = 5, name = "Register Store") If low, store value of register to accumulator; if high, store value of accumulator to register
 @Operand(bit = 6-8, name = "Register Address")

 - Immediate -
 @Instruction(name = "IMM", operands = 2) // Store Immediate value into register
 @Operand(bit = 6-8, name = "Register Address")
 @Operand(bit = 9-16, name = "Immediate")

 - Memory-
 @Instruction(name = "MEM", operands = 3) //
 @Operand(bit = 5, name = "Memory Store") // If low, load value of memory address to register; if high, load value of register to memory address
 @Operand(bit = 6-8, name = "Register Address")
 @Operand(bit = 9-16, name = "Memory Address") //

 - Port -
 @Instruction(name = "PRT", operands = 2) //
 @Operand(bit = 5, name = "Output") // If low, store value of input port to register; if high, load value of register to output port
 @Operand(bit = 6-8, name = "Register Address")

 - Stack -
 @Instruction(name = "STK", operands = 2) //
 @Operand(bit = 5, name = "Pop") // If low, push value of register to stack; if high, pop value of stack to register
 @Operand(bit = 6-8, name = "Register Address")

 - Pointer -
 @Instruction(name = "POI", operands = ) // Change value of pointer
 @Operand(bit = 9-16, name = "Immediate") // Value to be used

 - Jump -
 @Instruction(name = "JMP", operands = ) // Change value of program counter
 @Operand(bit = 9-16, name = "Immediate") // Value to jump to

 - Predicate -
 @Instruction(name = "PRD", operands = 3) //
 @Operand(bit = 5, name = "Invert") // If high, invert output of condition
 @Operand(bit = 6-8, name = "Condition Table") // Condition Table at line TODO
 @Operand(bit = 9-16, name = "Immediate") // Value to jump to

------------------------------------------------------------------------------------------------------------------------
 [*] Register Layout
------------------------------------------------------------------------------------------------------------------------

 - Zero Register -
 @Register(name = "ZR", position = "0")

 - General Purpose Register -
 @Register(name = "GPR", position = "1")

 - General Purpose Register -
 @Register(name = "GPR", position = "2")

 - General Purpose Register -
 @Register(name = "GPR", position = "3")

 - General Purpose Register -
 @Register(name = "GPR", position = "4")

 - Temporary -
 @Register(name = "TMP", position = "5")

 - Pointer -
 @Register(name = "POI", position = "6")

 - Accumulator -
 @Register(name = "ACC", position = "7")

 - Status Register -
 @Register(name = STS) // Stores values of flags

------------------------------------------------------------------------------------------------------------------------
 [*] Memory Table
------------------------------------------------------------------------------------------------------------------------

 - L1 Cache -
 @Memory(name = "L1-dCache", size = 16)
 @Memory(name = "L1-iCache", size = 32)

 - L2 Cache -
 @Memory(name = "L2", size = 64)

 - RAM -
 @Memory(name = "RAM Memory", size = 128)

 - Main Memory
 @Memory(name = "Main Memory", size = 512)

------------------------------------------------------------------------------------------------------------------------
 [*] Miscellaneous Table
------------------------------------------------------------------------------------------------------------------------

 - Halt -
 @Instruction(name = "HLT", opcode = "000") // Halt the CPU

 - Flush Cache -
 @Instruction(name = "FLC", opcode = "001") // Flush L1 Cache
 
 - No Operation -
 @Instruction(name = "NOP", opcode = "010") // No Operation

 - No Operation -
 @Instruction(name = "NOP", opcode = "011") // No Operation

------------------------------------------------------------------------------------------------------------------------
 [*] Condition Table
------------------------------------------------------------------------------------------------------------------------

 - Carry -
 @Condition(name = "Carry", bit = 8)

 - Zero -
 @Condition(name = "Zero", bit = 7)

 - Negative -
 @Condition(name = "Negative", bit = 6)
