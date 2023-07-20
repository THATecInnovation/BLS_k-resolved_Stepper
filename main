const int ENA = 2;
const int DIR = 3;
const int PUL = 4;

int steps;
int i;
String received;

void setup() {
  pinMode(ENA, OUTPUT);
  pinMode(DIR, OUTPUT);
  pinMode(PUL, OUTPUT);
  digitalWrite(ENA,LOW);
  Serial.begin(9600);
  Serial.flush();
}

void loop() {
  if (Serial.available() > 0) {
    received = Serial.readString();
    if (received == "Init"){
      Serial.println(received);
    }
    else if (received == "Direction: Pos"){
      digitalWrite(DIR,HIGH);
      Serial.println(received);
    }
    else if (received == "Direction: Neg"){
      digitalWrite(DIR,LOW);
      Serial.println(received);
    }
    else if (received.indexOf("Steps:") == 0){
      int steps = received.substring(6,received.length()).toInt();
      Serial.println(received);
      for(i=0;i<steps;i++){
        digitalWrite(PUL, HIGH);
        delay(10);
        digitalWrite(PUL, LOW);
      }
    }
    else{
      Serial.print("ERROR! Received: ");
      Serial.println(received);
    }
  }
  delay(100);
}
