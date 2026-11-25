// Line Follower - 3 wheeled robot
int leftSensor = 2;   // L
int rightSensor = 3;  // R
int leftMotorFwd = 5;
int leftMotorRev = 6;
int rightMotorFwd = 9;
int rightMotorRev = 10;

void setup() {
  pinMode(leftSensor, INPUT);
  pinMode(rightSensor, INPUT);
  pinMode(leftMotorFwd, OUTPUT);
  pinMode(leftMotorRev, OUTPUT);
  pinMode(rightMotorFwd, OUTPUT);
  pinMode(rightMotorRev, OUTPUT);
}

void loop() {
  int L = digitalRead(leftSensor);
  int R = digitalRead(rightSensor);

  // Both White -> Forward
  if (L == HIGH && R == HIGH) {
    forward();
  }
  // Only Left Black -> Turn Left
  else if (L == LOW && R == HIGH) {
    turnLeft();
  }
  // Only Right Black -> Turn Right
  else if (L == HIGH && R == LOW) {
    turnRight();
  }
  // Both Black -> Stop
  else if (L == LOW && R == LOW) {
    stopRobot();
  }
}

void forward() {
  digitalWrite(leftMotorFwd, HIGH);
  digitalWrite(leftMotorRev, LOW);
  digitalWrite(rightMotorFwd, HIGH);
  digitalWrite(rightMotorRev, LOW);
}
void turnLeft() {
  digitalWrite(leftMotorFwd, LOW);
  digitalWrite(leftMotorRev, LOW);
  digitalWrite(rightMotorFwd, HIGH);
  digitalWrite(rightMotorRev, LOW);
}
void turnRight() {
  digitalWrite(leftMotorFwd, HIGH);
  digitalWrite(leftMotorRev, LOW);
  digitalWrite(rightMotorFwd, LOW);
  digitalWrite(rightMotorRev, LOW);
}
void stopRobot() {
  digitalWrite(leftMotorFwd, LOW);
  digitalWrite(leftMotorRev, LOW);
  digitalWrite(rightMotorFwd, LOW);
  digitalWrite(rightMotorRev, LOW);
}
