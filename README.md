/This project sensors if there is light from the LDR and voltage regulator. If there is, it turns
on the phone and after the phone has turned on it provides power to the phone for 10min. 

*/


int sensorPin = A0;   // select the input pin for ldr
int sensorValue = 0;  // variable to store the value coming from the sensor

void setup() {
  pinMode(2, OUTPUT); //pin connected to the relay that turns the phone on
  pinMode(3, OUTPUT); //pin connected to the relay that powers the phone
  Serial.begin(9600); //sets serial port for communication
}

void loop() {
  // read the value from the sensor:
  sensorValue = analogRead(sensorPin);    
  Serial.println(sensorValue); //prints the values coming from the sensor on the screen
  
  if(sensorValue >400 ) //setting a threshold value
  {
  digitalWrite(2,HIGH); //turn relay ON to switch the phone on
  digitalWrite(3,HIGH); //turn relay ON to provide power to the phone
  delay(4000);          // wait for 4 seconds
  digitalWrite(2, LOW); // turn phone switch relay OFF as the phone has now started. 
  delay(600000);        // wait 10mins
  digitalWrite(3, LOW); // turn power relay OFF
  delay(1800000);       // wait for 30 min

  }  
else 
  digitalWrite(2,LOW); //turn relay OFF
  digitalWrite(3,LOW); //turn relay OFF
  
}