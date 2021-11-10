# Social-Distancing-Detector
int input = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Clear the trigger
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Sets the trigger pin to HIGH state for 10 microseconds
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // Reads the echo pin, and returns the sound wave travel time in microseconds
  return pulseIn(echoPin, HIGH);
}

void setup()
{
  Serial.begin(9600);

  pinMode(3, OUTPUT);
  pinMode(13, OUTPUT);
}

void loop()
{
  input = 0.01723 * readUltrasonicDistance(0, 1);
  Serial.println(input);
  if (input <= 50) {
    digitalWrite(3, HIGH);
    digitalWrite(13, LOW);
  } else {
    digitalWrite(3, LOW);
    digitalWrite(13, HIGH);
  }
  delay(10); // Delay a little bit to improve simulation performance
}
