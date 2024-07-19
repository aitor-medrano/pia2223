# Dataset

En esta sesión nos vamos a centrar en generar el dataset necesario para entrenar el modelo de IA del PIA Lara.

Nuestro objetivo es generar un dataset que contenga todas las características que hemos recogido con la aplicación de captura.

Para ello, utilizaremos los audios que hemos recopilado mediante la aplicación de captura y tenemos almacenados en S3 están codificados con el formato [Opus](https://es.wikipedia.org/wiki/Opus_(c%C3%B3dec)) dentro de un contenedor [Ogg](https://es.wikipedia.org/wiki/Ogg).

Recordad que tenemos la estructura de datos en *MongoDB* con la colección `audios` con la siguiente estructura:

``` json
{
  "_id": {
    "$oid": "641dfed8093018b216fa33d8"
  },
  "aws_object_id": "63ea809051c7dd6fe6e4527f_1679687384.wav",
  "usuario": {
    "id": {
      "$oid": "63ea809051c7dd6fe6e4527f"
    },
    "mail": "cliente@lara.com",
    "nombre": "Rocío López",
    "parent": "tecnico@lara.com"
  },
  "fecha": {
    "$date": "2023-03-24T20:49:44.782Z"
  },
  "texto": {
    "id": {
      "$oid": "640cb6abbd72df924a9f636b"
    },
    "texto": "Comí un flan que me dio flato.",
    "tag": "syllabus",
    "tipo": "syllabus"
  },
  "duracion": 3
}
```

### Dataset ampliado

Cómo todavía no sabemos con qué audios es conveniente entrenar el modelo, vamos a generar previamente un dataset ampliado con todos los datos disponibles, almacenando otros datos que podamos considerar de interés, como el técnico, el tag, el mail del cliente, así como su sexo u otros datos que podamos llegar a necesitar.

Sobre este dataset ampliado podremos ejecutar diferentes procesos que nos generar el dataset que emplearemos para cada uno de los modelos.

Es decir, si queremos probar con todos los audios grabados por mujeres, en vez de volver a conectarnos a *MongoDB* y *S3* para descargar y unir los datos, sobre el dataset ampliado generaremos la versión reducida.

### Representación del audio

Para el *dataset* necesitamos crear una representación numérica del audio. Puedes utilizar librerías como [librosa](https://github.com/librosa/librosa) o [soundfile](https://pysoundfile.readthedocs.io/en/latest/).

## Elementos evaluables

1. Script de generación del dataset ampliado (debe conectarse a MongoDB)
2. Script de generación del dataset reducido (mediante paso de parámetros, y debe utilizar los datos del dataset anterior).
3. Fichero JSON con los datos del dataset ampliado
4. Fichero JSON con unos datos reducidos

## Plazo de entrega

* Jueves 18 Mayo - 23:59: Archivo zip con los datos y scripts.
