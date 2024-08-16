/*
Name- Ansh Sharma 
Student_ID : 2310994763

This program is created in reponse to the task 1.1 of SIT210(Embedded systems Development)

In this programm , i have achieved the objective of blinking my name through builtin led with the help of morse code
To achieve this task  i have created procedures/functions to preform certain specific task which in turn helped me achieve them
For example i have created blinkdot() and blinkdash() for display of "." and "-" 
Further i have used the 2 function to make further function to achieve the task of blinking the individual letters of my name that are A, N , S , H
then i have set up a input from button after which the blinking will happen

*/


// setting up the input pin from the button to be 2
const int buttonPin = 2; 
// declaring the variables for the duration of blinking
const int shortBlink = 200;
const int longBlink = 600;
const int ElementDelay = 200;
const int LetterDelay = 600;
 

void setup() {
  Serial.begin(9600);

  // the builtin led is set for output
  pinMode(LED_BUILTIN,OUTPUT);  
 
 // setting up the  digitalpin 2 to recieve input from the button
  pinMode(buttonPin, INPUT_PULLUP); 
  delay(100);
}

void loop() {

  int buttonState = digitalRead(buttonPin);
  Serial.println(digitalRead(buttonPin));
 
  if (buttonState==LOW) {
    // calling the function for blinking of the individual letters of my name
    blinkA();
    blinkN();
    blinkS();
    blinkH();
  }
  else
  {
    
    digitalWrite(LED_BUILTIN,LOW);
  }
 
}

// creating a procedure for dot 
void blinkdot() {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(shortBlink);
  digitalWrite(LED_BUILTIN, LOW);
  delay(ElementDelay);
}

// creating a procedure for dash
void blinkdash() {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(longBlink);
  digitalWrite(LED_BUILTIN, LOW);
  delay(ElementDelay);
}

// creating a procedure for blinking A whose morse code is ".-"
void blinkA() {
  blinkdot();
  blinkdash();
  delay(LetterDelay);
}

// creating a procedure for blinking A whose morse code is "-."
void blinkN() {
  blinkdash();
  blinkdot();
  delay(LetterDelay);
}

// creating a procedure for blinking A whose morse code is "..."
void blinkS() {
  blinkdot();
  blinkdot();
  blinkdot();
  delay(LetterDelay);
}

// creating a procedure for blinking A whose morse code is "...."
void blinkH() {
  blinkdot();
  blinkdot();
  blinkdot();
  blinkdot();
  delay(LetterDelay);
}
