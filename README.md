# Shield de motor paso a paso para Arduino Nano ESP32

Trabajo práctico integrador de la asignatura Diseño de Circuitos Impresos del posgrado de FIUBA.

- **Autor:** Agustín Navari
- **Cursada:** octubre–diciembre de 2026
- **Driver:** Toshiba TB67S249FTG
- **Plataforma:** Arduino Nano ESP32
- **Estado:** diseño del PCB y ruteo en desarrollo.

## Descripción y objetivo

El proyecto consiste en el diseño de una placa para controlar un motor paso a paso bipolar mediante un Arduino Nano ESP32, utilizando el driver TB67S249FTG.

El diseño toma como referencia el módulo Pololu 2973 y adapta sus interfaces al formato de una placa portadora para el Nano ESP32. Incluye dos conectores hembra de 15 posiciones para alojar el módulo y un conector adicional de 2 × 15 posiciones que permite acceder a sus pines.

El objetivo es desarrollar el esquemático, seleccionar los componentes y diseñar el PCB, contemplando los requisitos eléctricos, térmicos, mecánicos y de fabricación.

## Características del diseño

- Alimentación del motor de 24 V nominales.
- Alimentación del Nano mediante USB o una entrada externa independiente.
- Protección contra inversión de polaridad en la alimentación del motor mediante un MOSFET.
- Control de movimiento mediante las señales STEP, DIR y ENABLE.
- Configuración de funciones del driver mediante jumpers.
- Conexión opcional de señales de configuración al Nano.
- Ajuste del límite de corriente mediante potenciómetro.
- Conector independiente para las salidas de diagnóstico.
- PCB de dos capas, previsto para cobre de 1 oz y espesor de placa de 1,6 mm.

## Interfaz con el Arduino Nano ESP32

Las entradas de control del driver admiten las señales de lógica de 3,3 V del Nano ESP32.

Las señales STEP, DIR y ENABLE se conectan directamente al microcontrolador. Otras funciones pueden conectarse mediante jumpers, permitiendo liberar esos pines cuando no se utilizan para controlar el driver.

Los pines del Nano también se encuentran disponibles en un conector de expansión. Los pines conectados permanentemente al driver comparten su función con este conector y no quedan disponibles como señales independientes.

Las salidas de diagnóstico MO, LO1 y LO2 utilizan resistencias de pull-up a la alimentación interna de 5 V del driver. Se exponen en un conector independiente y no se conectan directamente al Nano.

La alimentación VCC generada por el Toshiba se utiliza únicamente para el circuito del driver y su configuración. No se conecta a la salida de 3,3 V ni a VUSB del Nano.

## Alimentación

La placa dispone de entradas separadas para la alimentación del motor y del Nano ESP32. Ambas comparten GND.

- **Motor:** entrada de 24 V nominales, con protección contra inversión de polaridad.
- **Nano:** alimentación mediante USB o una fuente externa regulada de 9–12 V conectada a su entrada VIN a través de un diodo de protección.

La entrada de alimentación del Nano no debe conectarse directamente a la fuente de 24 V del motor.

## Criterios de diseño del PCB

Se adopta una corriente objetivo de 1,7 A por fase para dimensionar las conexiones de salida del motor.

El cálculo inicial de ancho de pistas considera cobre de 35 µm, capas externas y un incremento de temperatura de 10 °C. Las conexiones próximas al encapsulado utilizan estrechamientos cortos que se ensanchan al disponer de espacio.

La corriente continua admisible de la placa queda pendiente de validación térmica. El valor de referencia del módulo comercial no garantiza el mismo desempeño en este diseño.

La distribución de componentes y el ruteo contemplan:

- Capacitores de desacople próximos a los pines correspondientes.
- Conexiones cortas y amplias en los recorridos de potencia.
- Planos de GND y vías para conectar ambas caras.
- Disipación del driver mediante su pad expuesto y cobre asociado.
- Separación entre señales de configuración y recorridos de potencia.
- Reserva del área necesaria para la antena del Nano ESP32.
- Acceso a conectores, jumpers y potenciómetro.

## Estado del proyecto

El esquemático fue elaborado y revisado mediante ERC y una revisión funcional de las conexiones.

Actualmente se trabaja en la distribución de componentes y el ruteo del PCB. Quedan pendientes la revisión final del layout, la verificación DRC y la generación de los archivos de fabricación.

El diseño todavía no cuenta con validación experimental de funcionamiento ni de desempeño térmico.

## Estructura del repositorio

- **doc/**: propuesta, cálculos, decisiones de ingeniería y documentación propia del diseño.
- **info/**: hojas de datos y documentación de referencia de terceros.
- **pcb/**: proyecto KiCad, bibliotecas propias, modelos 3D y archivos de fabricación generados.

La propuesta del trabajo se encuentra en [doc/propuesta/README.md](doc/propuesta/README.md).

## Apertura del proyecto

Abrir el archivo `.kicad_pro` ubicado en el directorio `pcb/` desde el administrador de proyectos de KiCad.

Las bibliotecas y los modelos 3D propios deben mantenerse dentro del repositorio y utilizar rutas relativas al proyecto mediante `${KIPRJMOD}`.

Los archivos del proyecto se desarrollan con KiCad 10. Se recomienda utilizar la misma versión principal al trabajar desde distintas computadoras.

## Licencia

La licencia de hardware abierto del proyecto se encuentra pendiente de selección.

Antes de la entrega final se incorporará su identificación en esta sección y el texto completo de la licencia en un archivo ubicado en la raíz del repositorio.

La documentación de terceros conserva sus respectivas licencias y avisos de autoría.

## Referencias

- [Pololu 2973 — TB67S249FTG Stepper Motor Driver Carrier, Full Breakout](https://www.pololu.com/product/2973)
- [Arduino Nano ESP32 — documentación oficial](https://docs.arduino.cc/hardware/nano-esp32/)
- [Consigna del trabajo práctico integrador](https://github.com/cese-dci/DCI-TP-INTEGRADOR)

