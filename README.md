从零开始设计一个CPU （Verilog）
====
版本 V1.0  

vivado 2019.2

=========================

资源
-------
B站 视频地址：https://www.bilibili.com/video/BV1S7411f7sZ/

作业说明（包括指令设计和模块结构）  
版权问题不再提供下载：  
~~https://github.com/luyufan498/CPU_start_from_0/blob/master/Assignment_CPU.pdf~~


源码（未打包）：
https://github.com/luyufan498/CPU_start_from_0/tree/master/SourceCode

打包工程（vivado打开即用）：
https://github.com/luyufan498/CPU_start_from_0/tree/master/Projects


参考讲义  
版权问题不再提供下载：  
~~https://github.com/luyufan498/CPU_start_from_0/blob/master/Microprocessor%20Design.pdf  
https://github.com/luyufan498/CPU_start_from_0/blob/master/General%20Purpose%20Microprocessor%20Design.pdf~~



汇编程序
------

给定一个非零自然数N，计算小于N的自然数之和

0000100011 //0// READ INPUT TO R3

1000000001 //1// INIT R0 = 1

1010000000 //2// INIT R1 = 0

0100010100 //3// R1 = R0 + R1  

0010000001 //4// R0 = R0 + 1

0001110011 //5// IF R0 < R3 THEN Z = 0 ELSE Z = 1

0001010011 //6// IF Z == 0  THEN GO ADDR 03 ELSE GO NEXT ADDR

0000100101 //7// OUTPUT R1

0000000000 //8// OVER

------------------------------

给定一个数N，计算N除以11的余数

0000100011 //0// read R3

1000001011 //1// INIT R0 = 11

0001110011 //2// IF R0 < R3 THEN Z = 0 ELSE Z = 1

0001100110 //3// IF Z == 1  THEN GO ADDR 06 ELSE GO NEXT ADDR

0011111011 //4// R3 = R3 - 11

0001000011 //5// GO TO ADDR 03 

0101110011 //6// R3 = R1 - R3 

0000100111 //7// OUTPUT R3

0000000000 //8// OVER

------------------------------

给定一个自然数N，计算最大约数

0000100011 //0// READ INPUT TO R3

1000000000 //1// INIT R0 = 0

0010000001 //2// R0 = R0 + 1

0001110011 //3// IF R0 < R3 THEN Z = 0 ELSE Z = 1

0001010111 //4// IF Z == 0  THEN GO ADDR 07 ELSE GO NEXT ADDR

0000100110 //5// OUTPUT R2

0000000000 //6// OVER

0000010111 //7// R1 = R3

0001110001 //8// IF R0 < R1 THEN Z = 0 ELSE Z = 1

0001101100 //9// IF Z == 1  THEN GO ADDR 12 ELSE GO NEXT ADDR

0101010100 //10// R1 = R1 - R0

0001000010 //11// GO TO ADDR 02 

0101010001 //12// R1 = R0 - R1

0001011111 //13// IF Z == 0 (MEANS R0 != 0) GO ADDR 15

0000011001 //14// R2 = R1

0001000010 //15// GO ADDR 02 



 
