# Pipelined-ARM-Processor-using-System-Verilog
The project aims to Implement the pipelined ARM processor using system Verilog with a Hazard Unit.

My Project of the Computer Architecture and Assembly Language Course Offered in Fall 2021 @ Zewail City.


The block diagram of the processor is given in the following Figure:
![image](https://user-images.githubusercontent.com/58476343/220199268-c9415e09-841e-49f9-a99e-6629af76294b.png)


## The processor should support the following instructions:

            1) Data processing instructions where the second source can be either an immediate value or a source register, with no shifts. 
            2) Data processing instructions must include ADD, SUB, AND, ORR, BIC, and EOR. 
            3) Arithmetic Logic Unit (ALU) must be extended to support all these instructions.
            4) LDR and STR instructions with positive immediate offset (offset mode).
            5) Branch instruction
 
## Also, the processor must handle the following hazards:

            1) Read After Write (RAW) Hazard
            2) LDR Hazard
            3) Control Hazards due to Branch or PC write
     

## The Processor is tested using the following Testbench File

            ADDR            PROGRAM                   ; COMMENTS               HEX CODE
            00         MAIN SUB R0, R15, R15          ; R0 = 0                 E04F000F
            04              ADD R2, R0, #5            ; R2 = 5                 E2802005
            08              ADD R3, R0, #12           ; R3 = 12                E280300C
            0C              SUB R7, R3, #9            ; R7 = 3                 E2437009
            10              ORR R4, R7, R2            ; R4 = 3 OR 5 = 7        E1874002
            14              AND R5, R3, R4            ; R5 = 12 AND 7 = 4      E0035004
            18              ADD R5, R5, R4            ; R5 = 4 + 7 = 11        E0855004
            
            1C              SUBS R8, R7, R2           ; R8=3-5=-2,set Flags    E0578002
            20              ADDLT R7, R5, #1          ; R7 = 11 + 1 = 12       B2857001
            24              BGE AROUND                ; should NOT be taken    AA000000
            28              SUB R7, R7, R2            ; R7 = 12 - 5 = 7        E0477002
            2C       AROUND STR R7, [R3, #84]         ; mem[12+84] = 7         E5837054
            30              LDR R2, [R0, #96]         ; R2 = mem[96] = 7       E5902060       
            34              ADD R12, R2, #114         ; R12 = 114 + 7 = 121    E282C072
            
            38              BIC R3, R12, R7           ; R3 = 121 & ~ 7 = 120   E1CC3007
            3C              EOR R5, R3, R12           ; R5 = 120 ^ 121 = 1     E023500C
            
            PCWRITE:
            40              ADD R15, R15, #0                                   E28FF000
            44              ADD R4 , R0, R0                                    E2898005
            48              ADD R5 , R0, R0                                    E0805000
            4C              ADD R12 , R4, R5                                   E084C005
            
            50              B END                     ; always taken           EA000001
            54              ADD R2, R0, #13           ; shouldn't happen       E280200D
            58              ADD R2, R0, #10           ; shouldn't happen       E280200A
            5C          END STR R2, [R0, #100]        ; mem[100] = 7           E5802064


