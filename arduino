const int nivel_maxim = 100;
int secventa[nivel_maxim];
int sunet[nivel_maxim];
int secventa_jucator[nivel_maxim];
int nivel = 1;
int note = 0;
int velocity = 1000;
 
 
void setup() {   //declaram pinii
  pinMode(13, OUTPUT); //led verde
  pinMode(12, OUTPUT); //led rosu
  pinMode(11, OUTPUT); //led galben
  pinMode(10, OUTPUT); //led albastru
 
  pinMode(7, INPUT_PULLUP); //buton 1
  pinMode(6, INPUT_PULLUP); //buton 2
  pinMode(5, INPUT_PULLUP); //buton 3
  pinMode(4, INPUT_PULLUP); //buton 4
 
  pinMode(3, OUTPUT); //buzzer
}
 
void loop() {
  if (nivel == 1) {
    generare_secventa();
 
    for (int i = 13; i >= 10; i--) { //leduri on/off
      digitalWrite(i, HIGH);
      delay(100);
      digitalWrite(i, LOW);
    }
  }
 
  if (digitalRead(7) == LOW || nivel != 1) { //butonul de start = 1
    show_secventa();
    get_secventa();
  }
  }
 
void generare_secventa() {
  randomSeed(millis()); //se genereaza secventele random
 
  for (int i = 0; i < nivel_maxim; i++) {
    secventa[i] = random(10, 14);
 
    switch (secventa[i]) { //asociem un sunet fiecarei culori
      case 10:
        note = 349; //Fa
        break;
            case 11:    
        note = 329; //Mi
        break;
      case 12:
        note = 293; //Re
        break;
      case 13:
        note = 261; //Do
        break;
    }
    sunet[i] = note;
  }
}
 
void show_secventa() {
  digitalWrite(13, LOW);
  digitalWrite(12, LOW);
  digitalWrite(11, LOW);
  digitalWrite(10, LOW);
 
  for (int i = 0; i < nivel; i++) {
    digitalWrite(secventa[i], HIGH);
    tone(3, sunet[i]);
    delay(velocity);
    digitalWrite(secventa[i], LOW);
    noTone(3);
    delay(200);
  }
}
 
void get_secventa() {
  int flag = 0; //flag - secventa corecta
 
  for (int i = 0; i < nivel; i++) {
    flag = 0;
 
    while (flag == 0) {
 
      if (digitalRead(7) == LOW) {
        digitalWrite(13, HIGH);
        tone(3, 261); //Do
        delay(velocity);
        noTone(3);
        secventa_jucator[i] = 13;
        flag = 1;
        delay(200);
 
        if (secventa_jucator[i] != secventa[i]) {
          secventa_gresita();
          return ;
        }
        digitalWrite(13, LOW);
      }
 
      if (digitalRead(6) == LOW) {
        digitalWrite(12, HIGH);
        tone(3, 293); //Re
        delay(velocity);
        noTone(3);
        secventa_jucator[i] = 12;
        flag = 1;
        delay(200);
 
        if (secventa_jucator[i] != secventa[i]) {
          secventa_gresita();
          return ;
        }
        digitalWrite(12, LOW);
      }
 
      if (digitalRead(5) == LOW) {
        digitalWrite(11, HIGH);
        tone(3, 329); //Mi
        delay(velocity);
        noTone(3);
        secventa_jucator[i] = 11;
        flag = 1;
        delay(200);
 
        if (secventa_jucator[i] != secventa[i]) {
          secventa_gresita();
          return ;
        }
        digitalWrite(11, LOW);
      }
 
      if (digitalRead(4) == LOW) {
        digitalWrite(10, HIGH);
        tone(3, 349); //Fa
        delay(velocity);
        noTone(3);
        secventa_jucator[i] = 10;
        flag = 1;
        delay(200);
 
        if (secventa_jucator[i] != secventa[i]) {
          secventa_gresita();
          return ;
        }
        digitalWrite(10, LOW);
      }
    }
  }
  secventa_corecta();
}
 
void secventa_corecta() {
  digitalWrite(13, LOW);
  digitalWrite(12, LOW);
  digitalWrite(11, LOW);
  digitalWrite(10, LOW);
  delay(250);
 
  digitalWrite(13, HIGH);
  digitalWrite(12, HIGH);
  digitalWrite(11, HIGH);
  digitalWrite(10, HIGH);
  delay(500);
 
  digitalWrite(13, LOW);
  digitalWrite(12, LOW);
  digitalWrite(11, LOW);
  digitalWrite(10, LOW);
  delay(500);
 
  if (nivel < nivel_maxim) {
    nivel++;
  }
  velocity -= 50; //creste dificultatea
}
 
void secventa_gresita() {
  for (int i = 0; i < 3; i++) {
    digitalWrite(13, HIGH);
    digitalWrite(12, HIGH);
    digitalWrite(11, HIGH);
    digitalWrite(10, HIGH);
    tone(3, 233);
    delay(250);
 
    digitalWrite(13, LOW);
    digitalWrite(12, LOW);
    digitalWrite(11, LOW);
    digitalWrite(10, LOW);
    noTone(3);
    delay(250);
  }
  nivel = 1;
  velocity = 1000;
}
