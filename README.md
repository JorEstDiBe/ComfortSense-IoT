# ComfortSense-IoT

## Arquitectura técnica
El sistema estará compuesto por sensores ambientales conectados a un ESP32, el cual se encargará de leer las variables del entorno, procesarlas y enviarlas por WiFi mediante el protocolo MQTT. Los datos serán recibidos por un dashboard web, donde se visualizarán en tiempo real para evaluar el nivel de confort ambiental del espacio monitoreado.

Los sensores principales propuestos son:
- Sensor de temperatura y humedad: DHT22 o BME280
- Sensor de luz: BH1750
- Sensor opcional de calidad de aire: MQ-135

Flujo general del sistema:
Sensores → ESP32 → WiFi/MQTT → Dashboard web

## Restricciones y limitaciones

El proyecto utilizará un ESP32 como dispositivo principal, por lo que se deben tener en cuenta algunas restricciones de hardware y operación:

- **Memoria limitada:** aunque el ESP32 tiene buena capacidad para proyectos académicos, no es adecuado para procesamiento pesado o almacenamiento local extenso.
- **Dependencia de red WiFi:** la transmisión por MQTT requiere una conexión estable a internet o a una red local.
- **Precisión de sensores económicos:** sensores como el DHT22 o MQ-135 pueden tener variaciones y requieren calibración básica.
- **Consumo energético:** aunque el sistema puede funcionar por USB, si se quisiera alimentar con batería habría que optimizar consumo.
- **Escalabilidad limitada:** si se agregan demasiados sensores o lógica compleja, puede aumentar la carga del microcontrolador.

### Recursos del hardware seleccionado
- Microcontrolador: ESP32
- Conectividad: WiFi y Bluetooth integrados
- RAM aproximada: 520 KB SRAM
- Flash típica: 4 MB
- Alimentación: 5V por USB o 3.3V regulados

## Presupuesto estimado

| Componente | Cantidad | Costo aproximado |
|---|---:|---:|
| ESP32 | 1 | 35,000 - 45,000 COP |
| DHT22 o BME280 | 1 | 15,000 - 35,000 COP |
| BH1750 | 1 | 10,000 - 20,000 COP |
| MQ-135 (opcional) | 1 | 12,000 - 25,000 COP |
| Protoboard y cables | 1 set | 15,000 - 25,000 COP |

**Total estimado:** entre 75,000 y 150,000 COP, dependiendo de los sensores seleccionados.

