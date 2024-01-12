# Sistema de Seguridad Vehicular

Este proyecto implementa un sistema de seguridad para vehículos que incluye la lectura continua de la velocidad del vehículo, detección de umbrales de seguridad y acciones de emergencia, así como la comunicación con una Raspberry Pi a través de MQTT.

## Descripción del Sistema

El sistema consta de los siguientes componentes:

1. **Pulsador para Iniciar el Sistema:**
   - El sistema se activa mediante un pulsador.
   - Una vez activado, el display LCD mostrará "SYSTEM ON".
   - Permanecerá activo indefinidamente mientras la EK esté alimentada.

2. **Lectura Continua de Velocidad:**
   - La velocidad se emula mediante la lectura de un potenciómetro conectado al módulo ADC.
   - Se utiliza un filtro de mediana móvil para evitar valores atípicos.

3. **Comunicación con Raspberry Pi:**
   - Todos los valores filtrados se envían a la Raspberry Pi por UART.
   - La Raspberry Pi guarda las lecturas en un log (csv o txt) con timestamp.

4. **Freno de Emergencia:**
   - Se activa cuando la velocidad supera el 75% de la velocidad máxima.
   - Comando de freno: parpadeo del LED y mensaje de "PELIGRO" en el display LCD.
   - Emisión de un zumbador durante 1 segundo.

5. **Comunicación MQTT:**
   - La Raspberry Pi publica un mensaje en un broker MQTT cuando se activa el freno de emergencia.
   - El mensaje contiene la velocidad actual y un timestamp.

6. **Restauración del Sistema:**
   - Cuando la velocidad baja del umbral de emergencia, se restaura el display LCD y el LED.

7. **Cliente MQTT en Ordenador Portátil:**
   - Se ejecuta un cliente MQTT (suscriptor) en un ordenador portátil.
   - El cliente está suscrito al topic correspondiente y muestra mensajes en la terminal.

## Configuración y Uso

1. **Requisitos de Hardware:**
   - Lista de componentes y conexiones necesarias.

2. **Configuración del Proyecto en e2studio:**
   - Instrucciones para configurar el entorno de desarrollo.

3. **Compilación y Carga del Firmware:**
   - Pasos para compilar el código y cargarlo en la EK.

4. **Configuración de la Raspberry Pi y MQTT Broker:**
   - Instrucciones para configurar la Raspberry Pi y el broker MQTT.

5. **Ejecución del Cliente MQTT en el Ordenador Portátil:**
   - Pasos para ejecutar y configurar el cliente MQTT en el ordenador portátil.

## Enlaces de Interés

- [Documentación del microcontrolador](enlace_microcontrolador)
- [Biblioteca MQTT utilizada](enlace_mqtt_library)
- [Instalación de Mosquitto en la Raspberry Pi](enlace_instalacion_mosquitto)
- [Guía de e2studio](enlace_e2studio_guide)
