#include <SoftwareSerial.h>
SoftwareSerial mySerial(2, 3); //RX, TX respetively
String c;
int R=0;
void setup()
{
                
  mySerial.begin(9600);
  Serial.begin(9600);  
  pinMode(5,OUTPUT);//m1p            
  pinMode(6,OUTPUT);//m1m

  pinMode(7,OUTPUT);//m2p             
  pinMode(8,OUTPUT);//m2m
  
   digitalWrite(5,LOW);//mrp
   digitalWrite(6,LOW);//mrm
       
   digitalWrite(7,LOW);//mlp
   digitalWrite(8,LOW);//mlm

  Serial.println("voice control ROBOT"); 
}

void loop() // run over and over
{ 
  
    if (mySerial.available() > 0) 
  {
     c = mySerial.readString();
     
    if(c[0]=='f')
    {     
       digitalWrite(5,HIGH);//mrp
       digitalWrite(6,LOW);//mrm
       
       digitalWrite(7,HIGH);//mlp
       digitalWrite(8,LOW);//mlm
       
       Serial.println("forward");    //*forward#*right#*left#*back#*stop# 
       
      
    }
     if(c[0]=='r')
    {     
       digitalWrite(5,LOW);//mrp
       digitalWrite(6,LOW);//mrm
       
       digitalWrite(7,HIGH);//mlp
       digitalWrite(8,LOW);//mlm
       
       Serial.println("right");  
         
      
    }
     if(c[0]=='l')
    {     
       digitalWrite(5,HIGH);//mrp
       digitalWrite(6,LOW);//mrm
       
       digitalWrite(7,LOW);//mlp
       digitalWrite(8,LOW);//mlm
       
       Serial.println("left");  
      
      
    }
     if(c[0]=='b')
    {     
       digitalWrite(6,HIGH);//mrp
       digitalWrite(5,LOW);//mrm
       
       digitalWrite(8,HIGH);//mlp
       digitalWrite(7,LOW);//mlm
       
       Serial.println("back");  
    
      
    }
    if(c[0]=='s')
    {     
       digitalWrite(5,LOW);//mrp
       digitalWrite(6,LOW);//mrm
       
       digitalWrite(7,LOW);//mlp
       digitalWrite(8,LOW);//mlm
       
       Serial.println("stop");  
    
      
    }
      
  }
      
}

