# ComfortSense-IoT

### Visión del Proyecto

En muchos espacios de estudio y trabajo, las condiciones ambientales no son adecuadas, lo que afecta la concentración, la productividad y el bienestar de las personas. Factores como la temperatura, la iluminación o la calidad del aire suelen pasar desapercibidos, aunque tienen un impacto directo en el rendimiento diario.

Este proyecto propone el desarrollo de un sistema IoT de bajo costo basado en un ESP32, capaz de monitorear variables ambientales en tiempo real y calcular un índice de confort. La información será enviada a un dashboard accesible, permitiendo a los usuarios tomar decisiones informadas para mejorar su entorno. Está dirigido a estudiantes, oficinas y hogares que buscan optimizar sus condiciones de estudio o trabajo de forma simple y eficiente.

### Descripción General del Sistema

El sistema propuesto por el equipo funciona mediante la captura de variables ambientales utilizando sensores conectados a un microcontrolador ESP32. Estos sensores registran datos como temperatura, humedad y nivel de iluminación del entorno.

El ESP32 procesa esta información y calcula un índice de confort en tiempo real. Posteriormente, los datos son enviados a través de WiFi utilizando el protocolo MQTT hacia un servidor o plataforma de visualización.

Finalmente, un dashboard permite al usuario visualizar las condiciones del ambiente y, en caso necesario, recibir alertas cuando los niveles no sean adecuados para actividades como estudiar o trabajar.

### MVP (Minimum Viable Product)

Las siguientes funcionalidades corresponden a la propuesta planteada para el sistema de monitoreo inteligente de confort ambiental, definiendo los elementos esenciales para validar su funcionamiento en un entorno real.

1. Funcionalidades Must-have
- **Lectura de temperatura y humedad (DHT22 o BME280):** Permite capturar variables ambientales básicas que influyen directamente en el confort térmico del usuario. Estos datos son fundamentales para el cálculo del índice de confort.
- **Lectura de nivel de iluminación (BH1750):** Mide la intensidad de luz en el entorno, un factor clave para actividades como estudiar o trabajar, ya que influye en la fatiga visual y la concentración.
- **Procesamiento de datos en el ESP32:** El microcontrolador se encarga de recibir, interpretar y preparar los datos recolectados por los sensores, actuando como el núcleo del sistema.
- **Cálculo de un índice de confort en tiempo real:** A partir de las variables medidas, se genera un valor que representa el nivel de confort del ambiente, facilitando la interpretación de los datos por parte del usuario.
- **Envío de datos mediante WiFi usando MQTT:** Permite transmitir la información recolectada hacia un servidor o plataforma externa de forma eficiente y en tiempo real.
- **Visualización en un dashboard básico:** Proporciona al usuario una interfaz sencilla donde puede consultar las condiciones ambientales actuales de manera clara.

2. Funcionalidades Nice-to-have
- **Medición de calidad del aire (MQ-135):** Añade una dimensión adicional al análisis del entorno, permitiendo detectar contaminantes o condiciones poco saludables en el aire.
- **Generación de alertas:** Notifica al usuario cuando las condiciones ambientales no son adecuadas, permitiendo actuar de manera oportuna.
- **Almacenamiento de datos históricos:** Guarda registros de las mediciones para analizar tendencias y cambios en el tiempo.
- **Visualización avanzada (gráficas y tendencias):** Mejora la experiencia del usuario mediante representaciones visuales más completas e intuitivas.
- **Generación de recomendaciones:** Sugiere acciones al usuario (como ventilar el espacio o ajustar la iluminación) basadas en los datos recolectados.

Este conjunto de funcionalidades permite validar la propuesta del sistema de forma práctica, asegurando una base sólida sobre la cual se pueden implementar mejoras futuras.

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

## Backlog inicial y organización ágil

El backlog inicial del proyecto fue organizado en un tablero de GitHub Project, donde las tareas fueron priorizadas y clasificadas en:
- **Must-have:** funcionalidades mínimas necesarias para el MVP
- **Nice-to-have:** mejoras opcionales
- **Spike:** tarea de investigación técnica para reducir riesgo

El repositorio contiene el backlog inicial y la planeación base del proyecto.

## Planeación y Ejecución Ágil

### Spike Arquitectónico (Gestión de Riesgos)

El principal riesgo técnico del proyecto es validar la comunicación completa entre el dispositivo IoT y la visualización de datos en tiempo real. Aunque el uso del ESP32, los sensores ambientales y MQTT está ampliamente documentado por separado, la mayor incertidumbre está en comprobar que todo el flujo funcione de manera integrada y estable: lectura del sensor, procesamiento en el ESP32, envío por WiFi mediante MQTT y recepción correcta en un dashboard.

Por esta razón, durante el primer release se desarrollará un **Spike Arquitectónico** enfocado exclusivamente en validar la viabilidad técnica del sistema de extremo a extremo.

#### Riesgo principal identificado
La integración **ESP32 → WiFi/MQTT → Dashboard** puede presentar fallos de conexión, errores en el formato de los mensajes, latencia, pérdida de datos o problemas de compatibilidad entre librerías, broker y dashboard.

#### Objetivo del Spike
Comprobar que el sistema puede capturar al menos una variable ambiental desde un sensor conectado al ESP32 y transmitirla correctamente por MQTT hacia un dashboard o herramienta de monitoreo en tiempo real.

#### Alcance del Spike
El Spike incluirá las siguientes pruebas mínimas:

- Configuración del entorno de desarrollo del ESP32
- Lectura de al menos un sensor ambiental (temperatura/humedad o luz)
- Conexión del ESP32 a una red WiFi
- Publicación de datos en un tópico MQTT
- Recepción y visualización de esos datos en un dashboard o cliente MQTT
- Validación del formato del mensaje enviado

#### Resultado esperado
Al finalizar el Spike, el equipo debe tener evidencia de que la arquitectura base del proyecto es viable. Esto permitirá reducir el riesgo técnico antes de avanzar al desarrollo completo del MVP.

#### Criterios de éxito del Spike
Se considerará exitoso si se cumple lo siguiente:

1. El ESP32 logra conectarse correctamente a la red WiFi.
2. El ESP32 lee datos válidos desde al menos un sensor.
3. Los datos se publican correctamente en un tópico MQTT.
4. El dashboard o cliente MQTT recibe y muestra esos datos.
5. El flujo puede repetirse de forma estable durante varias pruebas consecutivas.

#### Evidencia esperada
Como evidencia del Spike se espera incluir:

- Capturas de la visualización de datos en el dashboard o cliente MQTT
- Fragmentos de código o enlace al código implementado
- Registro de pruebas realizadas
- Conclusiones sobre la viabilidad técnica y posibles ajustes a la arquitectura
