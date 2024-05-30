# Parcial-SPD
Código Arduino. Parcial SPD-UTN

- Emiliano Garcia

## Proyecto: Sistema de incendio con Arduino

## Descripción
El objetivo de este proyecto fue diseñar un sistema de incendio utilizando Arduino que pueda detectar cambios de temperatura 
y activar un sistema de respuesta en caso de detectar un incendio. Además, se mostrará el nivel de temperatura en un display de 7 segmentos.
## Función principal
Detectar un incendio.

![1er Parcial SPD](https://github.com/EmiyG/Parcial-SPD/assets/123533958/820ef9be-9a4b-42bd-a552-8761ffbae487)


~~~ C LOGICA PRINCIPAL

  if (sistemaEncendido) {
    // Leer el valor del sensor de temperatura
    int valorSensor = analogRead(SENSOR_TEMPERATURA);

    // Mapear valor del sensor al rango de temperatura (-40 a 125 grados Celsius)
    float temperaturaCelsius = map(valorSensor, 20, 350, -40, 125);

    // Mostrar la temperatura en la consola
    Serial.print("Temperatura: ");
    Serial.print(temperaturaCelsius);
    Serial.println(" C");

    // Mostrar la temperatura en el display de 7 segmentos
    int nivelTemperatura = determinarNivelTemperatura(temperaturaCelsius);
    numerosDisplay(nivelTemperatura);

    // Encender o apagar los LEDs según la temperatura
    if (temperaturaCelsius > 60) {
      digitalWrite(LED_1, HIGH);
      digitalWrite(LED_2, HIGH);
      // Mover el servomotor a la posición deseada (por ejemplo, 90 grados)
      miServo.write(90);
    } else {
      digitalWrite(LED_1, LOW);
      digitalWrite(LED_2, LOW);
      // Mover el servomotor a otra posición (por ejemplo, 0 grados)
      miServo.write(0);
    }

    // Esperar 1 segundo antes de leer nuevamente
    delay(1000);
  }
}
~~~

## :robot: Link al proyecto
- [proyecto](https://www.tinkercad.com/things/euJDCtFru7V-1er-parcial-spd)

---














