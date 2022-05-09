# Esp32 Puertos Digitales
<img src="https://github.com/IDiegoUlises/Esp32-Puertos-Digitales/blob/main/Images/ESP32-DOIT-DEVKIT.jpg" width="1000" height="400" />

* **Tiene 30 puertos**
* **Voltaje de alimentacion es de 5 Volt**
* **Voltaje de los pines es de 0 a 3.3 Volt**
* **la siguiente es informacion no oficial y debe ser verificada**
* **25 puertos digitales de salida**
* **15 Puertos PWM(en otra fuente dice que son 25 verificar)**
* **2 Puertos Conversor analogico digital**
* **9 Pin touch**


### Conexion Puerto Digital
<img src="https://github.com/IDiegoUlises/Esp32-Puertos-Digitales/blob/main/Images/Apagar-y-prender.jpg" width="500" height="500" />

### Usando Puerto Digital Para Parpadeo de un Led
```c++
int led = 23;

void setup()
{
  pinMode(led, OUTPUT);
}

void loop()
{
  digitalWrite(led, HIGH);
  delay(1000);
  digitalWrite(led, LOW);
  delay(1000);
}
```
### Investigacion
* Puertos d13,d12,d14,d27,d26,d25,d33,d32,d35,d34,vn,vp todos los puertos probados y todo funcionan menos 4 pines
* todos los puertos GPIO funcionan correctamente pero los puertos d35(gpio35),d34(gpio34),vn(gpio39),vp(gpio36) no funcionan como salida como output y encontre documentacion que estos puertos sirven solamente como entradas
* Ahora falta probar las entradas

### El pin 5 solo se puede hacer una lectura con INPUT_PULLUP
```c++
void setup() {
  Serial.begin(9600);
  pinMode(5, INPUT_PULLUP);
  pinMode(23,OUTPUT);
}

void loop()
{
  int puerto1 = digitalRead(5);
  if (puerto1 == LOW)
  {
    Serial.println("Puerto 5 pulsado");
    digitalWrite(23,HIGH);
    delay(1000);
    digitalWrite(23,LOW);
  }

  delay(100);
}
```

### El pin 1 y 3 Utilizan el puerto serial para utilizar estos puertos no se deben utilizar el puerto serial porque al ser una entrada interfiere con la comunicacion serial y cuando se este subiendo el sketch estos puertos no deben recibir voltaje ya que marcara un error al subir el sketch y no se subira porque cuando se suba el sketch atraves del computador interferira con la comunicacion serial

```c++
void setup() {
  //Serial.begin(9600);
  pinMode(1, INPUT_PULLUP); //puerto 1 o puerto 3
  pinMode(23,OUTPUT);
}

void loop()
{
  int puerto1 = digitalRead(1);
  if (puerto1 == LOW)
  {
    digitalWrite(23,HIGH);
    delay(1000);
    digitalWrite(23,LOW);
  }
  delay(100);
}
```
