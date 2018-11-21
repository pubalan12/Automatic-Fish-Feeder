#include <Servo.h>
Servo servo;

int second =0 ;
int pos = 180; // variable to store the servo position

void setup() 
  {
    servo.attach(9); // attaches the servo on pin 9 to the servo object
    servo.write(pos);
    shake();
    delay(15);
    shake1();
    delay(15);
    servo.detach(); //stop sending pulses to reserve power on the Arduino.
    Serial.begin(9600);
  }

void loop() 
{
  static unsigned long lastTick = 0;
  if (millis() - lastTick >= 1000) 
    {
      lastTick = millis();
      second++;
      Serial.println(second);
    }

  if (second >= 90000) //or 43200 for twice a day //86400 for 1 time
    {
      servo.attach(9);
      delay(15);
      shake();
      delay(15);
      shake1();
      servo.detach(); //stop sending pulses to reserve power on the Arduino.
      second = 0; //reset counter
    }
}

void shake() 
{ 
  for (pos = 50; pos >= 0; pos -= 2)// goes from 180 degrees to 0 degrees
   {
    servo.write(pos); // tell servo to go to position in variable 'pos'
    delay(15); // waits 15ms for the servo to reach the position
   }
}

void shake1() 
{
  for (pos = 0; pos <= 210; pos += 2) // goes from 0 degrees to 180 degrees // in steps of 1 degree
    {
      servo.write(pos); // tell servo to go to position in variable 'pos'
      delay(15); // waits 15ms for the servo to reach the position
    }
}
