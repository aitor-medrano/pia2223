# Modelado de datos

Tras nuestra visita al IES Navarro Santafé y conocer cómo se realiza la captura de datos desde los sensores, pasando por los PLC y luego su envío mediante NodeRED, necesitamos definir qué datos vamos a almacenar, la estructura de almacenamiento y su periodicidad.

## Sensórica

Así pues, nos vamos a plantear la siguiente sensórica:

| Ambiente exterior | Ambiente interior | Cultivo
| ---               | ----              | ---
| Humedad relativa  | Humedad relativa  | Humedad sustrato
| Lluvia            | CO2               | Conductividad
| Luminosidad       | Luminosidad       | PH
| Temperatura       | Temperatura       | Temperatura agua
| Presión atmosférica |                 | Nivel de agua (Requiere monitorización precisa, seguramente frecuencia de 1 segundo)
| Velocidad viento
| Dirección viento

## Modelando

Para almacenar los datos nos vamos a centrar en *MongoDB*, y en concreto las **series temporales**, con ayuda de la [documentación oficial de MongoDB sobre Time Series](https://www.mongodb.com/docs/manual/core/timeseries-collections/).

Para ello, se pide investigar cómo podemos crear colecciones de series temporales y cuál es el modelo de datos idóneo. Para ello, nos podemos plantear las siguientes preguntas:

* ¿Almacenamos todos los sensores en una única colección?
* ¿Creamos una colección por cada tipo de medida?, es decir, una para las temperaturas (la interna, externa, del cultivo), otra para la humedad...
* ¿Necesitamos crear colecciones con los datos agregados, siguiendo el enfoque del [patrón cubo](https://aitor-medrano.github.io/iabd2223/sa/03modelado.html#cubo)?

## Generación de datos sintéticos

Antes de conectar con la sensórica real, es útil la creación de datos sintéticos que simulen los datos que se recibirán, intentando simular también su periodicidad.

Para ello, en la [primera sesión](06autoponic.md#node-red) ya vimos cómo podíamos generar datos y almacenarlos en MongoDB con ayuda de NodeRED y del conector [node-red-contrib-mongodb4](https://flows.nodered.org/node/node-red-contrib-mongodb4).

## Analítica

Una vez modeladas las colecciones, debemos pensar en la creación de determinados datasets con los datos que puede necesitar nuestro cuadro de mandos. 

!!! info "Conexión directa a MongoDB o via DataLake"
    Mediante las herramientas de visualización de datos vamos a poder:
    
    * acceder directamente a *MongoDB*
    * o a un dataset con los datos ya agregados para que luego el cuadro de mandos tenga mejor rendimiento.

Para ello, necesitamos pensar en las consultas agregadas que vamos a generar y luego persistir en nuestro lago de datos.

## Elementos evaluables

* (10p) Informe con el modelo de datos diseñado, argumentado las decisiones tomadas, mostrando ejemplos de colecciones con datos rellenados. El informe también tiene que contener una primera aproximación a las posibles consultas qué vamos a necesitar realizar para nuestro cuadro de mandos.
* (6p) Flujo de datos en NodeRED que inserte datos en *MongoDB* siguiendo la estructura de datos modelada.
* (4p) Implementación de las consultas planteadas en el informe mediante el *framework* de agregación, de manera que realicen algún tipo de agrupación y cálculo sobre los datos almacenados. Las consultas realizadas se persistirán en una nueva colección, y se adjuntará el comando necesario para exportar los datos tanto a JSON como a CSV.

## Dudas para resolver

* ¿Es necesario saber en qué iteración/fase estamos de un determinado cultivo?
* La duración de las fases de los cultivos, ¿es homogénea? ¿todas las fases duran lo mismo? ¿deberíamos guardar el tipo de cultivo y su duración?
* ¿Cuales son las fases por las que pasa un cultivo? ¿sembrado, en germinación, recogida...?

## Plazo de entrega

* Jueves 23 Febrero - 23:59: Informe de modelado
* Jueves 9 Marzo - 23:59 - Flujo de datos en NodeRED y consultas agregadas en MongoDB.
