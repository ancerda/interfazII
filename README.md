interfazII

##### hola mundo

##### LED intermitente (Blink)
```js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(8, LOW);   // Apagar LED
  delay(3000);             // Esperar 1 segundo
    
  digitalWrite(8, HIGH);  // Encender LED
  delay(3000);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  delay(1500);             // Esperar 1 segundo
}
```

##### control por pulsador
```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}

void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
<img src="https://raw.githubusercontent.com/ancerda/interfazII/refs/heads/main/img/led%20control%20pulsador.png"/>

##### potenciador
```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}

void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
#### semaforo
```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  //digitalWrite(LED_4, LOW);   // Verde peatones apagado
  //digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  //delay(2000); // 2 segundos 
}
```
<img src="https://raw.githubusercontent.com/ancerda/interfazII/refs/heads/main/img/semaforocap.png"/>

#### botón potenciometro

#### random pulsador

#### potenciometro processing

```js

import gab.opencv.*;
import processing.video.*;
import java.awt.*;

Capture cam;
OpenCV opencv;

void setup() {
  background(0);
  size(640, 480);
  
  cam = new Capture(this, 640, 480);
  cam.start();
  
  opencv = new OpenCV(this, 640, 480);
  opencv.loadCascade(OpenCV.CASCADE_FRONTALFACE); // Carga el detector de rostro
}

void draw() {
  if (cam.available()) {
    cam.read();
  }
  
  image(cam, 0, 0);
  
  opencv.loadImage(cam);
  
  // Detecta rostros
  Rectangle[] faces = opencv.detect();
  
  noFill();
  stroke(0, 255, 0);
  
  for (int i = 0; i < faces.length; i++) {
    Rectangle face = faces[i];
    
    // Dibuja rectángulo del rostro
    rect(face.x, face.y, face.width, face.height);
    
    // Estimar posición de los ojos: arriba del rostro, a los lados
    float eyeY = face.y + face.height * 0.35;
    float eyeOffsetX = face.width * 0.2;
    
    float leftEyeX = face.x + eyeOffsetX;
    float rightEyeX = face.x + face.width - eyeOffsetX;
    
    fill(255, 0, 0);
    noStroke();
    ellipse(leftEyeX, eyeY, 20, 20);
    ellipse(rightEyeX, eyeY, 20, 20);
  }
}

```
