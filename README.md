# 2D-Mechanical-Arm
CÓDIGO:

#include <Servo.h>
Servo servomotor;
Servo servomotor1;
Servo servomotor2;

int angulo = 90;//Variable para el ángulo, inicia en 90°
int angulo1 = 90;// Variable para el ángulo1, inicia en 90º
int angulo2 = 90;// Variable para el ángulo2, inicia en 90º

int aumentar = 12;  //Pin del pulsador para aumentar el angulo
int disminuir = 13; //Pin  del pulsador para disminuir el angulo
int aumentar1 = 11; //Pin del pulsador para aumentar el angulo del segundo servomotor
int disminuir1 = 10; // Pin del pulsador para disminuir el angulo del segundo servomotor.
int aumentar2 = 8; //Pin del pulsador para aumentar el angulo del tercer servomotor
int disminuir2 = 9; //Pin del pulsador para disminuir el angulo del tercer servomotor


void setup() {
  servomotor.attach(6);  //Pin PWM 6 del Arduino
  servomotor1.attach(3); //Pin PWM 3 del Arduino
  servomotor2.attach(5); //Pin PWM 5 del Arduino
  pinMode(disminuir, INPUT);
  pinMode(aumentar, INPUT);
  pinMode(disminuir1, INPUT);
  pinMode(aumentar1, INPUT);
  pinMode(disminuir2, INPUT);
  pinMode(aumentar2, INPUT);

  servomotor.write(angulo);  //Posiciona el servo inicialmente en la mitad (90°)
  servomotor1.write(angulo1);// Posiciona el servo1 inicialmente en la mitad (90º)
  servomotor2.write(angulo2);// Posiciona el servo2 inicialmente en la mitad (90º)
}

void loop() {

  //Aumenta el angulo mientras se mantenga presionado
  if (digitalRead(aumentar) == LOW)
  {
    angulo++;
    if (angulo >= 180)
    {
      angulo = 180;      //El ángulo no aumenta mas alla de 180 grados
    }
  }

  //Disminuye el angulo mientras se mantenga presionado
  if (digitalRead(disminuir) == LOW)
  {
    angulo--;
    if (angulo <= 0)
    {
      angulo = 0;      //El ángulo no disminuye mas alla de 0 grados
    }
  }
  servomotor.write(angulo);  //Manda el ángulo al servo dependiendo del pulsador presionado
  delay(10);



  //Aumenta el ángulo1 mientras se mantenga presionado
  if (digitalRead(aumentar1) == LOW)
  {
    angulo1++;
    if (angulo1 >= 180)
    {
      angulo1 = 180;      //El ángulo1 no aumenta mas alla de 180 grados
    }
  }

  //Disminuye el ángulo1 mientras se mantenga presionado
  if (digitalRead(disminuir1) == LOW)
  {
    angulo1--;
    if (angulo1 <= 0)
    {
      angulo1 = 0;      //El ángulo1 no disminuye mas alla de 0 grados
    }
  }
  servomotor1.write(angulo1);  //Manda el ángulo1 al servo dependiendo del pulsador presionado
  delay(10);



  //Aumenta el ángulo2 mientras se mantenga presionado
  if (digitalRead(aumentar2) == LOW)
  {
    angulo2++;
    if (angulo2 >= 180)
    {
      angulo2 = 180;      //El ángulo2 no aumenta mas alla de 180 grados
    }
  }

  //Disminuye el ángulo2 mientras se mantenga presionado
  if (digitalRead(disminuir2) == LOW)
  {
    angulo2--;
    if (angulo2 <= 0)
    {
      angulo2 = 0;      //El ángulo2 no disminuye mas alla de 0 grados
    }
  }
  servomotor2.write(angulo2);  //Manda el ángulo2 al servo dependiendo del pulsador presionado
  delay(10);

}	

