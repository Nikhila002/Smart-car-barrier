# Smart-car-barrier
An IoT module that is used to monitor the vehicles automatically. This hardware module is developed using the Arduino, Ultrasonic Sensor and the Servo motor.
code is mentioned below:-



#include<Servo.h>
Servo myservo;
const int trigPin=3;
const int echoPin=5; 
long tmeduration;
int distance;
void setup() {

  myservo.attach(9);
  pinMode(trigPin,OUTPUT);
  pinMode(echoPin,INPUT);
  Serial.begin(9600);
  
  }
void loop() {
  digitalWrite(trigPin,LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin,HIGH);
  delayMicroseconds(10);
   digitalWrite(trigPin,LOW);
  
tmeduration=pulseIn(echoPin,HIGH);
distance=(0.034*tmeduration)/2;

if(distance<=20){
  
  myservo.write(90);
  }
  else{
    myservo.write(0);}
  
  Serial.print("distance:");
    Serial.println(distance);
  
    delay(1);
}

