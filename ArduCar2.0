#include <SoftwareSerial.h>
#include <Servo.h>
#include <MeetAndroid.h>

/*define logic control output pin*/
int in1=9;
int in2=8;
int in3=7;
int in4=6;
/*define channel enable output pins*/
int ENA=10;
int ENB=5;
int ABS=135;
/*define forward function*/
String message;

const int rxpin = 2;  //Andiamo ad assegnare al pin 2 l’indirizzo di ricezione dati (e lo colleghiamo al pin TXD del modulo)
const int txpin = 3;  //Assegnamo invece al pin 3 l’indirizzo di trasmissione dati (collegandolo al pin RXD del nostro componente
SoftwareSerial bluetooth(rxpin, txpin);  //Assegnamo ad un nome (bluetooth) i suoi pin di ricezione e trasmissione, per facilitarci la scrittura del codice
MeetAndroid meetAndroid(rxpin,txpin,9600);

void setup() {
  Serial.begin(9600); // open serial port to receive data
  bluetooth.begin(9600); //set baud rate

  /*pinMode(motorPin1, OUTPUT);
  pinMode(motorPin2, OUTPUT);*/
  pinMode(in1,OUTPUT);
  pinMode(in2,OUTPUT);
  pinMode(in3,OUTPUT);
  pinMode(in4,OUTPUT);
  pinMode(ENA,OUTPUT);
  pinMode(ENB,OUTPUT);
  
  // steering in central position
  delay(100);

  // create array loop to iterate over every item in the array
  /*for (int thisReading = 0; thisReading < numOfReadings; thisReading++) {
    readings[thisReading] = 0;
  }*/

  // register callback function
  //meetAndroid.registerFunction(moveCar, 'a');
}

/*void Parsing(char carattere)
{
    if(carattere=='1')
    {
      for(int i=1; i<1000; i++)
        avanti();
    }
}*/
void Parsing(String stringa){
  Serial.println(stringa);
   String motore;
   String direzione;

   int commaIndex = stringa.indexOf(',');
   motore = stringa.substring(0, commaIndex);
  direzione = stringa.substring(commaIndex + 1);

  if(motore=="1" && direzione=="0")
    avanti();
  
  if(motore=="0")
    fermo();

  if(motore=="2" && direzione=="0")
    indietro();

  if(motore=="1" && direzione=="1")
    avanti_destra();
      
  if(motore=="1" && direzione=="2")
    avanti_sinistra();
  
  if(motore=="2" && direzione=="1")
    indietro_destra();

  if(motore=="2" && direzione=="2")
    indietro_sinistra();
}

 void avanti(){
  analogWrite(ENA,ABS);
  analogWrite(ENB,ABS);
  digitalWrite(in1,HIGH);
  digitalWrite(in2,LOW);
  digitalWrite(in3,HIGH);
  digitalWrite(in4,LOW);
 }

 void fermo(){
  analogWrite(ENA,ABS);
  analogWrite(ENB,ABS);
  digitalWrite(in1,LOW);
  digitalWrite(in2,LOW);
  digitalWrite(in3,LOW);
  digitalWrite(in4,LOW);
 }

 void indietro(){
  analogWrite(ENA,ABS);
  analogWrite(ENB,ABS);
  digitalWrite(in1,LOW);
  digitalWrite(in2,HIGH);
  digitalWrite(in3,LOW);
  digitalWrite(in4,HIGH);
 }

 void avanti_destra(){
  analogWrite(ENA,ABS);
  analogWrite(ENB,ABS);
  digitalWrite(in1,HIGH);
  digitalWrite(in2,LOW);
  digitalWrite(in3,LOW);
  digitalWrite(in4,LOW);
 }

 void avanti_sinistra(){
  analogWrite(ENA,ABS);
  analogWrite(ENB,ABS);
  digitalWrite(in1,LOW);
  digitalWrite(in2,LOW);
  digitalWrite(in3,HIGH);
  digitalWrite(in4,LOW);
 }

 void indietro_destra(){
  analogWrite(ENA,ABS);
  analogWrite(ENB,ABS);
  digitalWrite(in1,LOW);
  digitalWrite(in2,HIGH);
  digitalWrite(in3,LOW);
  digitalWrite(in4,LOW);
 }

 void indietro_sinistra(){
  analogWrite(ENA,ABS);
  analogWrite(ENB,ABS);
  digitalWrite(in1,LOW);
  digitalWrite(in2,LOW);
  digitalWrite(in3,LOW);
  digitalWrite(in4,HIGH);
 }
 
void loop() {

 /* char Android[3];
  for(int i=0;i<3;i++)
    Android[i]=' ';
  meetAndroid.getString(Android);

  if(Android[0]!=' '&&Android[1]!=' '&&Android[2]!=' ')
     Serial.println(Android);
  Parsing(Android);*/

 /* for(int i=1; i<1000; i++)
    Parsing("1,0");
  for(int i=1; i<2000; i++)
    Parsing("2,0");
  for(int i=1; i<500; i++)
    Parsing("0,0");
  for(int i=1; i<1000; i++)
    Parsing("1,1");
  for(int i=1; i<3000; i++)
    Parsing("2,2");if(!bluetooth.available())
  {
      Serial.println("No");
      
  }
  else
  {
    Serial.println("SI");
  }*/
 while(bluetooth.available()){
    message+=char(bluetooth.read());
    
    if(message.length() ==3)
    {
      String stringa=message;
      message="";
      Parsing(stringa);
    }
     
  }
   
   /*if(bluetooth.available()){  //Se il bluetooth riceve qualche dato
      
      
      Parsing(c);
    }*/
  
   
  

  
}
