#include <SoftwareSerial.h> // TX RX software library for bluetooth

#include <Servo.h> // servo library 
Servo servo1;

int bluetoothTx = 10; // bluetooth tx to 10 pin
int bluetoothRx = 11; // bluetooth rx to 11 pin

SoftwareSerial bluetooth(bluetoothTx, bluetoothRx);

void setup()
{
  servo1.attach(9);  
  Serial.begin(9600);
  bluetooth.begin(9600);
}

void loop()
{
  if(bluetooth.available()> 0 )
  {
    int servopos = bluetooth.read();
      servo1.write(servopos);
}
}
