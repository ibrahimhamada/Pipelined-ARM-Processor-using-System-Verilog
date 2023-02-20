# Implementation-of-Pipelined-ARM-Processor-using-System-Verilog
The project aims to Implement the pipelined ARM processor using system Verilog with a Hazard Unit.

My Project of the Computer Architecture and Assembly Language Course Offered in Fall 2021 @ Zewail City.


The block diagram of the processor is given in the following Figure:
![image](https://user-images.githubusercontent.com/58476343/220199268-c9415e09-841e-49f9-a99e-6629af76294b.png)


The processor should support the following instructions:

            1) Data processing instructions where the second source can be either an immediate value or a source register, with no shifts. 
            2) Data processing instructions must include ADD, SUB, AND, ORR, BIC, and EOR. 
            3) Arithmetic Logic Unit (ALU) must be extended to support all these instructions.
            4) LDR and STR instructions with positive immediate offset (offset mode).
            5) Branch instruction
 
Also, the processor must handle the following hazards:

            1) Read After Write (RAW) Hazard
            2) LDR Hazard
            3) Control Hazards due to Branch or PC write
     
