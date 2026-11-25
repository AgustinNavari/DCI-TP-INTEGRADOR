## \# Shield de motor paso a paso para Arduino Nano ESP32

## 

## Trabajo práctico integrador de la asignatura Diseño de Circuitos

## Impresos del posgrado de FIUBA.

## 

## \- \*\*Autor:\*\* Agustín Navari

## \- \*\*Cursada:\*\* octubre–diciembre de 2026

## \- \*\*Driver:\*\* Toshiba TB67S249FTG

## \- \*\*Plataforma:\*\* Arduino Nano ESP32

## \- \*\*Estado:\*\* diseño del PCB y ruteo en desarrollo.

## 

## \## Descripción y objetivo

## 

## El proyecto consiste en el diseño de una placa para controlar un

## motor paso a paso bipolar mediante un Arduino Nano ESP32, utilizando

## el driver TB67S249FTG.

## 

## El diseño toma como referencia el módulo Pololu 2973 y adapta sus

## interfaces al formato de una placa portadora para el Nano ESP32.

## Incluye conectores hembra para alojar el módulo y un conector adicional

## que permite acceder a sus pines.

## 

## Las señales de control utilizan la lógica de 3,3 V del Nano.

## Las salidas de diagnóstico del driver, con pull-ups a su alimentación

## interna de 5 V, se exponen en un conector independiente y no se

## conectan directamente al microcontrolador.

## 

## \## Características del diseño

## 

## \- Alimentación del motor de 24 V nominales.

## \- Alimentación del Nano mediante USB o una entrada externa independiente.

## \- Protección contra inversión de polaridad en la alimentación del motor.

## \- Control de movimiento mediante STEP, DIR y ENABLE.

## \- Configuración mediante jumpers y conexiones opcionales al Nano.

## \- Ajuste del límite de corriente mediante potenciómetro.

## \- PCB de dos capas, previsto para cobre de 1 oz.

## 

## Se adopta una corriente objetivo de 1,7 A por fase para dimensionar

## las conexiones de salida. La corriente continua admisible de la placa

## queda pendiente de validación térmica.

## 

## \## Estructura del repositorio

## 

## \- \*\*doc/\*\*: propuesta, cálculos y documentación propia del diseño.

## \- \*\*info/\*\*: hojas de datos y documentación de referencia de terceros.

## \- \*\*pcb/\*\*: proyecto KiCad, bibliotecas propias, modelos 3D y archivos

## &#x20; de fabricación generados.

## 

## La propuesta del trabajo se encuentra en

## \[doc/propuesta/README.md](doc/propuesta/README.md).

## 

## \## Referencias

## 

## \- \[Pololu 2973 — TB67S249FTG Full Breakout](https://www.pololu.com/product/2973)

## \- \[Arduino Nano ESP32](https://docs.arduino.cc/hardware/nano-esp32/)

## \- \[Consigna del trabajo integrador](https://github.com/cese-dci/DCI-TP-INTEGRADOR)

