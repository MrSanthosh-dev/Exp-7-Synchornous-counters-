## Exp-6-Synchornous-counters - up counter and down counter 
### AIM: 
To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  
– PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:  
Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
/* write all the steps invloved */



### PROGRAM 
```
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: Santhosh S
RegisterNumber:  212222100047
```
```
module proj6counters(D,C,B,A,clk);
output reg D,C,B,A;
input clk;
always@(posedge clk)
begin 
D=(C&B&A)^D;
C=(B&A)^C;
B=(A^B);
A=1^A;
end 
endmodule
```
### DOWN COUNTER
```
module downcounter(clk,a);
input clk;
output reg[3:0]a;
always@(posedge clk)
begin
a[3]=(~a[2] & ~a[1] & ~a[0])^ a[3];
a[2]=(~a[1] & ~a[0]) ^ a[2];
a[1]=(~a[0] ^ a[1]);
a[0]=1 ^ a[0];
end
endmodule
```

### RTL LOGIC UP COUNTER AND DOWN COUNTER  
### RTL LOGIC UP COUNTER
![image](https://github.com/MrSanthosh-dev/Exp-7-Synchornous-counters-/assets/117916573/e778f52d-77a7-4804-a615-5b609b8dc54e)
### RTL LOGIC DOWN COUNTER  
![image](https://github.com/MrSanthosh-dev/Exp-7-Synchornous-counters-/assets/117916573/38e763ef-a1cb-4909-ad6f-6c2a3f5bfa92)


### TIMING DIGRAMS FOR COUNTER  
### UP COUNTER
![image](https://github.com/MrSanthosh-dev/Exp-7-Synchornous-counters-/assets/117916573/99c3f8fd-fd27-4370-878d-a68a8375e45b)
### DOWN COUNTER
![image](https://github.com/MrSanthosh-dev/Exp-7-Synchornous-counters-/assets/117916573/fb717988-19f5-4fd6-9349-25465347142c)

### TRUTH TABLE 
### UP COUNTER
![image](https://github.com/MrSanthosh-dev/Exp-7-Synchornous-counters-/assets/117916573/7420db36-e48f-4ac9-a800-c8f2c4eb574e)
### DOWN COUNTER
![image](https://github.com/MrSanthosh-dev/Exp-7-Synchornous-counters-/assets/117916573/a5264cc7-7a87-4594-8529-e098f8a8e735)

### RESULTS 
Thus,the implementation of 4 bit up and down counters and validate  functionality has been successfully executed.
