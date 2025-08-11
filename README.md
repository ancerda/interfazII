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
