# PR-CTICA-6

INDICADOR DE NIVEL DE AGUA

Este repositorio muestra como podemos programar una ESP32 con el sensor Ultrasonico y conectar leds de manera que sirvan como un indicador visual del nivel de agua

INTRODUCCIÓN

DESCRIPCIÓN

La Esp32 la utilizamos en un entorno de adquision de datos pero en este caso utilizaremos el simulador WOKWI.

MATERIAL NECESARIO

WOKWI

Tarjeta ESP 32

HC-SR04 Ultrasonic Distance Sensor

Instrucciones de preparación de entorno

1- Abrir la terminal de programación y colocar la siguente programación:

// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=2 && safetyDistance<=5)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=5 && safetyDistance<=10) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=7 && safetyDistance<=14) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=9 && safetyDistance<=18) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
 digitalWrite(led1,  LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}

2- Hacer la conexion de los sensores Ultrasonico con la ESP32 y los leds como se muestra en la siguente imagen.

![Captura de pantalla 2024-01-19 183436](https://github.com/robertopatino42/PR-CTICA-6/assets/153964688/ac496a9a-f182-4139-9905-73432481643d)

Resultados

Cuando haya funcionado se visualizarán los valores dentro del monitor serial como se muestra en la siguente imagen.

![Captura de pantalla 2024-01-19 183509](https://github.com/robertopatino42/PR-CTICA-6/assets/153964688/e8a8f68c-4879-44d8-97e9-19565e4864a4)
