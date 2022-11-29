# Almacenamiento de datos

Tras la visita al *IES Victoria Kent*, consensuamos los prototipos y el modelo de datos de cada equipo.

A partir de ahí, vamos a dividir la clase en dos equipos, los cuales trabajaran de forma autónoma, cada uno con su modelo y prototipo, con el fin de desarrollar el almacenamiento de datos en MongoDB.

Las funcionalidades a implementar en esta sesión son:

* Almacenamiento de los datos personales de los clientes: datos de acceso a la aplicación, patologías y *dis*, nombre, sexo, fecha de nacimiento, provincia, fecha de la última operación.
* Grabación de un audio: fecha, texto, identificador del audio (los audios los trabajaremos en la próxima sesión del PIA), datos del usuario (id, nombre, edad, disfonías), etiquetas del texto, duración, ¿estado del ánimo?, valoración del audio subido (¿dificultad? ¿fidelidad?, ...).
* Respecto a los textos: texto, etiquetas, dificultad, creador (id y nombre del usuario).
* ¿Sesiones?: título, fecha, un conjunto de textos, las disfonias del cliente.
* Los roles de la aplicación serán: Administrador, Técnico y Cliente.
* El administrador puede crear textos, técnicos y clientes.
* El técnico puede crear textos y clientes.
* El cliente puede sube audio, ya sea de textos predefinidos o creados en caliente. 
* Los usuarios con perfil `Administrador` o `Técnico` podrán obtener los siguientes listado:
    * Todas las grabaciones de un cliente, pudiendo filtrar por fechas.
    * Todas las grabaciones a partir de un determinado filtro (edad, sexo, patología, ...), pudiendo filtrar además por fechas.

## Elementos entregables

* Proyecto publicado en GitHub. 

## Plazos de entrega

* Jueves 1 Dic - 23:59: Proyecto publicado en *GitHub*
* Viernes 2 Dic (aula): Demostración de la aplicación desde el perfil de `Técnico` y de `Cliente`.

## Elementos evaluables

* 80% Aplicación de captura de datos, teniendo en cuenta la documentación, legibilidad y calidad del código.
* 20% Demostración de la funcionalidad.