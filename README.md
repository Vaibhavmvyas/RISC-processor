The provided Verilog code describes the implementation of a MIPS-like processor with a focus on arithmetic and logical operations, as well as control instructions that manipulate condition flags. The functionality of the code can be described as follows:
Instruction Set Architecture (ISA) Overview:
The code defines an instruction set architecture that includes various arithmetic, logical, and control instructions. The instructions are encoded using bit fields within the instruction word. Here are the major components of the instruction encoding:
The IR (Instruction Register) holds the current instruction being executed. Different bit fields within the IR are used to specify the operation type, source and destination registers, immediate values, and other control signals.
Instructions are divided into categories, such as arithmetic, logical, load/store, and control instructions.
Processor Module:
The top module is the main processor module that represents the MIPS-like processor. Let's explore its key functionalities:
Register Files:
GPR represents the General Purpose Registers, which are organized in an array.
SGPR represents a special register used for storing the most significant bits of the result of a multiplication operation (mul instruction).
Condition Flags:
The processor maintains several condition flags: sign, zero, overflow, and carry. These flags are updated based on the results of arithmetic and logical operations.
Control Flow and State Machine:
The processor operates as a finite state machine (FSM) with different states such as idle, fetch_inst, dec_exec_inst, next_inst, sense_halt, and delay_next_inst.
The state transitions are controlled by the next_state signal, which is updated based on the current state and specific conditions.
Instruction Execution and Decoding:
The decode_inst task decodes the instruction stored in the IR and performs the corresponding operation. It also updates the jmp_flag and stop signals for control flow manipulation.
The decode_condflag task updates the condition flags based on the result of arithmetic and logical operations.
Memory and Data Movement:
The code contains placeholders for memory access instructions such as storedin, storereg, senddout, and sendreg. These instructions are intended to perform operations on a data memory and communicate with the outside world.
Program Execution:
The processor reads instructions from a memory file called "inst_data.mem" using the $readmemb function.
The FSM governs the flow of fetching instructions, decoding and executing them, and handling control flow and halting conditions.
Testbench:
The tb (testbench) module provides the necessary clock and reset signals to the top module. It also initializes the sys_rst signal and simulates the clock for a specific duration.
