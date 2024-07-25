#define trigPin 2
#define echoPin 3
#define ledPin 13
#define buzzerPin 12

int max_height = 6; // actual tank height in cm
int threshold = 3; // Sludge level threshold in cm

long duration, distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
}

void loop() {
  // Trigger ultrasonic sensor
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH); // Measure echo pulse duration

  distance = duration * 0.0343 / 2; // Calculate distance (assuming speed of sound = 34300 cm/s)

  int sludgeLevel = max_height - distance; // Calculate sludge level (tank height - water level)

  if (sludgeLevel >= threshold) // Check if sludge level exceeds threshold
  {
    digitalWrite(ledPin, HIGH); // Turn on LED
    tone(buzzerPin, 1000); // Activate buzzer with a 1kHz tone
  } else {
    digitalWrite(ledPin, LOW); // Turn off LED
    noTone(buzzerPin); // Stop the buzzer
  }

  delay(1000); // Adjust delay as needed
}
