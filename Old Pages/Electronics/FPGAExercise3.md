    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    Digital Design and FPPGA Workshop
    HacDC
    William Gibb (teachmeFPGA@gmail.com)
    Week 3 - Introduction to Combinatorial Verilog
    Full adder and ALU exercise
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    For our exercises this week, we'll be working with a few different modeling
    styles, focused around a 4-bit full adder.  We'll be working with a model
    where the 1 bit full adder circuit is explicitly defined, and break that down
    into half adders, behavioral and structural models.

    The full adder circuit can be constructed from 1-bit half adder circuits.
    The truth table for the half adder is as follows.
    A B | S Cout
    =========
    0 0 | 0 0
    0 1 | 1 0
    1 0 | 1 0
    1 1 | 0 1
    =========
    S = A xor B
    Cout = A and B

    Two of these cells, plus an additional OR gate, can be used to implement a
    full adder.  The S output of the first half adder cell is connected to the
    input of the second cell, as is the Cin.  The S output of the second cell is
    the sum S.  The Cout is computed by ORing the Cout of both cells.

    Likewise, the truth table for the Full Adder is as follows, for reference.
    Cin A B | S Cout
    ===============
     0 0 0 | 0 0
     0 0 1 | 1 0
     0 1 0 | 1 0
     0 1 1 | 0 1
     1 0 0 | 1 0
     1 0 1 | 0 1
     1 1 0 | 0 1
     1 1 1 | 1 1
    ================

    To do
    0) Copy the full adder codes below to files in your working directory.
    Be sure to copy a makefile to the directory.
    0.a) mkdir a new directory for this example.  name it something useful, such as "adder_exercise"
    0.b) create a new file for each verilog module, in the form modulename.v where module name is the name of the module. We'll need full_adder.v, full_adder_4bit.v, add test_adder.v.
    0.c) copy and paste the code for each module into the file.  be sure that anything in the file that isn't verilog code is commented out.
    0.d) if your in the vm, type copymake.sh into the command line to copy a makefile into your working directory

    1) Change the values of the makefile to test the full adder.
    1.a) Change the line SRC and TESTBENCH to include only the .v files created earlier.  if you need to add a new source to a project, add it to your makefile as well.

    2) Verify the full adder works by simulation.

    3) Write a description of the half adder, at gate level

    4) Write a full adder description, using the half adders you wrote in step
    3.  Give this full adder module a different module name than the provided
    model.

    5) Write a 4 bit full adder module using the new 1 bit full adder.  Be sure to
    give it a module name different than the name of the provided module.

    6) Take a break if you feel needed...or keep on coding

    7) Write a 4 bit full adder module using the new 1 bit full adder from step 6.
    Be sure to give it a module name different than the name of the provided
     module.

    8) One last adder - Write a 4 bit behavioral adder module.  Use 4 bit inputs
    and outputs in this module.  Again, give it a new name.

    9) Add the new models to the makefile.
           -half adder
           -full adder from half adders
           -4 bit full adder from step 5
           -full adder from step 6
           -4 bit full adder from step 7
           -4 bit full adder from step 8

    9) Modify the testbench to instantiate the new modules.  You'll need to
    instantiate the 4 bit full adder from step 5, step 7 and step 8.  This is why
    they all need to have unique module names.  You'll need to add three 4 bit
    wires for connecting the sum output of these new adders, as well as
    three 1 bit wires for connecting the cout output of these new adders.

    10) Simulate and verify all of the models behave the same way.

    Once this is done, and you have simulated the adders and shown that they all
    behave the same way, you'll have built the following types of modules
    - Structural Model (step 5)
    - Behavioral & Hierarchical Model (step 7)
    - Behavioral Model (step 8)

    After that is done, people are encouraged to take the ALU presented in the
    slides and are encouraged to expand the functionality of the ALU to 8 total
    functions.  The functions that should be added to the ALU are as follows:
    - r = ~A (R equals the complement of A)
    - r = A ^ B (R equals A xor B)
    - r = A << B (R equals A left shifted B bits)

    After this functionality has been added to the ALU model, the test bench used
    for the 4 bit full adder can be modified to simulate the ALU.
    Steps to do this
    0) Copy the test bench and makefile to your working directory
    1) Add/remove wires and regs as needed
    2) Replace the DUT with the ALU
    3) Expand the inputs in order to test all of the ALU functions.

    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    Full Adder Code
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module full_adder(a, b, cin, sum, cout);
           input    a, b, cin;
           output  sum, cout;

           reg sum, cout;

           always @(a or b or cin)
           begin
                   sum = a ^ b ^ cin;
                   cout= (a & b) | (a & cin) | (b & cin);
           end
    endmodule
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module full_adder_4bit (a, b, cin, sum, cout);
           input[3:0]    a, b;
           input           cin;
           output [3:0] sum;
           output cout;

           wire            c1, c2, c3;

           // instantiate 1-bit adders
           full_adder FA0(a[0],b[0], cin, sum[0], c1);
           full_adder FA1(a[1],b[1], c1, sum[1], c2);
           full_adder FA2(a[2],b[2], c2, sum[2], c3);
           full_adder FA3(a[3],b[3], c3, sum[3], cout);

    endmodule
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module test_adder;
           reg[3:0]  a, b;
           reg cin;
           wire [3:0] sum;
           wire         cout;

           full_adder_4bit dut(a, b, cin,
           sum, cout);

           initial
           begin
                   a = 4'b0000;
                   b = 4'b0000;
                   cin= 1'b0;
                   #50;
                   a = 4'b0101;
                   b = 4'b1010;
                   // sum = 1111, cout= 0
                   #50;
                   a = 4'b1111;
                   b = 4'b0001;
                   // sum = 0000, cout= 1
                   #50;a = 4'b0000;
                   b = 4'b1111;
                   cin= 1'b1;
                   // sum = 0000, cout= 1
                   #50;
                   a = 4'b0110;
                   b = 4'b0001;
                   // sum = 1000, cout= 0
           end // initial begin

            initial
            begin
                    $dumpfile ("waves.lxt");
                    $dumpvars(0,test_adder);
            end

    endmodule// test_adder
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    ALU Code
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module mul16(i0,i1,prod);
           input [15:0] i0,i1;
           output [31:0] prod;
           // this is a magnitude multiplier
           // signed arithmetic later
           assign prod = i0 * i1;
    endmodule
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module add32(i0,i1,sum);
           input [31:0] i0,i1;
           output [31:0] sum;
           assign sum = i0 + i1;
    endmodule
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module sub32(i0,i1,diff);
           input [31:0] i0,i1;
           output [31:0] diff;
           assign diff = i0 - i1;
    endmodule
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module mux32two(i0,i1,sel,out);
           input [31:0] i0,i1;
           input sel;
           output [31:0] out;

           assign out = sel? i1 : i0;
    endmodule
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module mux32three(i0,i1,i2,sel,out);
           input [31:0] i0,i1,i2;
           input [1:0] sel;
           output [31:0] out;

           reg[31:0] out;

           always @ (i0 or i1 or i2 or sel)
           begin
                   case (sel)
                   2???b00: out = i0;
                   2???b01: out = i1;
                   2???b10: out = i2;
                   default: out = 32???bx;
                   endcase
           end
    endmodule
    +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    module alu(a, b, f, r);
           input [31:0] a, b;
           input [2:0] f;
           output [31:0] r;

           // wire declarations
           wire [31:0] addmux_out, submux_out;
           wire [31:0] add_out, sub_out, mul_out;

           // module declarations
           mux32two   adder_mux(b, 32'd1, f[0], addmux_out);
           mux32two   sub_mux(b, 32'd1, f[0], submux_out);
           add32      our_adder(a, addmux_out, add_out);
           sub32      our_subtracter(a, submux_out, sub_out);
           mul16      our_multiplier(a[15:0], b[15:0], mul_out);
           mux32three output_mux(add_out, sub_out, mul_out, f[2:1], r);

    endmodule

[Category:FPGAWorkshop](Category:FPGAWorkshop "wikilink")