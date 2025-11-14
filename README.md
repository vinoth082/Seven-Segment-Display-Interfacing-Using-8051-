# Seven-Segment-Display-Interfacing-Using-8051

## Aim:
To interface a seven-segment display with the 8051 microcontroller and display digits 0 to 9 sequentially using an assembly language program in Keil and simulate it in Proteus.

## Apparatus Required:
•	Laptop with Keil uVision software
•	Proteus Design Suite
 
## Circuit Diagram Setup in Proteus:
1.	Open Proteus and create a new project.
2.	Add the following components from the library:
o	8051 Microcontroller (AT89C51)
o	Seven Segment Display (Common Anode/Cathode)
o	Resistors (330Ω)
3.	Connect:
o	Seven Segment Display to Port P2 of the microcontroller.
o	Power (VCC & GND) and appropriate resistors.
4.	Save the design and proceed to programming in Keil.

## Algorithm:
1.	Load DPTR with the address of the lookup table containing seven-segment hex values.
2.	Load R1 with 10 (loop counter for digits 0-9).
3.	Fetch digit patterns from the lookup table and send them to P2.
4.	Call a delay subroutine.
5.	Increment DPTR to get the next digit pattern.
6.	Repeat steps 3-5 until all 10 digits are displayed.
7.	Repeat the process infinitely.

## Explanation:
•	Lookup Table (0100H - 0109H): Stores hexadecimal values for displaying digits 0-9.
•	MOVC A, @A+DPTR: Retrieves the corresponding segment pattern for the digit.
•	MOV P2, A: Sends data to Port 2, which is connected to the seven-segment display.
•	ACALL D: Calls the delay subroutine to maintain visibility of each digit.
•	Delay Subroutine: Creates a time delay using nested loops.
•	SJMP L: Runs the digit display sequence in an infinite loop.

## Simulation in Proteus:
1.	Open Proteus and load the HEX file generated from Keil.
2.	Connect P2 of the microcontroller to the seven-segment display.
3.	Run the simulation and observe the digits 0 to 9 appearing sequentially.

## Program:


```
ORG 0000H
	UP: MOV P2, #0C0H
	ACALL DELAY
	MOV P2, #0F9H
	ACALL DELAY
	MOV P2, #0A4H
	ACALL DELAY
	MOV P2, #0B0H
	ACALL DELAY
	MOV P2, # 99H
	ACALL DELAY
	MOV P2, # 92H
	ACALL DELAY
	MOV P2, # 82H
	ACALL DELAY
	MOV P2, #0F8H
	ACALL DELAY
	MOV P2, #80H 
	ACALL DELAY
	MOV P2, #90H
	ACALL DELAY


DELAY: MOV R5, #10
	H1: MOV R4, #180
	H2: MOV R3, #255
	H3:DJNZ R3,H3
	DJNZ R4,H2
	DJNZ R5,H1
	RET
	END

```

## Output:

<img width="1300" height="1093" alt="image" src="https://github.com/user-attachments/assets/40c52a2e-d38f-4306-9f9a-91231173582f" />

<img width="1766" height="1082" alt="image" src="https://github.com/user-attachments/assets/00a7aa55-4345-4ae6-9377-0a55fedb43c3" />



## Result:
The seven-segment display has been successfully interfaced with the 8051 microcontroller, and the digits 0 to 9 are displayed sequentially using Keil and Proteus.


