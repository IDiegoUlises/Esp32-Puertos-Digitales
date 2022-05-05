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
* Puertos d13,d12,d14,d27,d26,d25,d33,d32,d35,d34,vn,vp a probar
* todos los puertos funcionan correctamente pero los puertos d35,d34,vn(gpio39),vp(gpio36) no funcionan y encontre documentacion que estos puertos sirven solamente como entradas
