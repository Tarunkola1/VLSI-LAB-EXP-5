EXP-5

date:

              SIMULATION AND IMPLEMENTATION OF FINITE STATE MACHINE

AIM: To simulate and synthesis finite state machine using vivado2023.3.

APPARATUS REQUIRED: vivado 2023.3

PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

LOGIC DIAGRAM:

![image](https://github.com/Tarunkola1/VLSI-LAB-EXP-5/assets/161431337/1097d125-6cd6-4663-a426-6c0a75783eef)

VERILOG CODE:
```
module Sequence_Detector_Moore(clock,reset,sequence_in,detector_out);
input clock, reset, sequence_in; 
output reg detector_out; 
parameter  S0=2'b00,S1=2'b01,S2=2'b10,S3=2'b11;
reg [1:0] current_state, next_state; 
// sequential memory of the Moore FSM
always @(posedge clock, posedge reset)
begin
 if(reset==1) 
 current_state <= S0;
 else
 current_state <= next_state; 
end 
// to determine next state 
always @(current_state,sequence_in)
begin
 case(current_state) 
 	S0:begin
		if(sequence_in==1)
   			next_state = S1;
  		else
   			next_state = S0;
 	   end
 	S1:begin
if(sequence_in==0)
   			next_state = S2;
  		else
   			next_state = S1;
 	   end
S2:begin
  	if(sequence_in==1)
   		next_state = S3;
 	 else
   		next_state = S0;
    end 
  S3:begin
  	if(sequence_in==0)
   		next_state = S0;
  	else
   		next_state = S1;
     end
	default:next_state = S0;
endcase
end
// to determine the output of the Moore FSM, output only depends on current state
always @(current_state)
begin 
 case(current_state) 
 	S0:   detector_out = 0;
 	S1:   detector_out = 0;
 	S2:  detector_out = 0;
 	S3:  detector_out = 1;
 	default:  detector_out = 0;
 endcase
end 
endmodule
```

OUTPUT WAVEFORM:

![image](https://github.com/Tarunkola1/VLSI-LAB-EXP-5/assets/161431337/5d34f4b0-9523-4b58-9e03-404ecd73d406)

RESULT:
THUS THE SIMULATION OF FINITE STATE MACHINE USING VIVADO IS VERIFIED

