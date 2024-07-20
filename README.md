// Step1 Library Inclusion and Pin Definitions.
#include <LedControl.h>
int DIN = 12;
int CS =  11;
int CLK = 10;


//Step 2 Creates an instance of the LedControl object.
LedControl lc=LedControl(DIN,CLK,CS,0);
void setup(){
 lc.shutdown(0,false);       
 lc.setIntensity(0,15);      
}


// Step 3 Loop Function, Defines two byte arrays Talking and Silent.
void loop(){ 
    byte SMILE[8]=   {0x00,0x42,0xe7,0x42,0x00,0x3c,0x42,0x3c};
        printByte(Talk);
         delay(250);
             byte SAD[8]=   {0x00,0x42,0xe7,0x42,0x00,0x00,0x3c,0x00};
        printByte(Silent);
         delay(250);
 }


// Step  4 printByte Function.
void printByte(byte character [])
{
  int i = 0;
  for(i=0;i<8;i++)
  {
    lc.setRow(0,i,character[i]);
  }
}
