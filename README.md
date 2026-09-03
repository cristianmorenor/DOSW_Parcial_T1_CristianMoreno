# DOSW_Parcial_T1_CristianMoreno

**Nombre completo:** Cristian Moreno  
**Grupo DOSW:** DOSW-1  

## Punto 1
## 1. Diagrama de Contexto

### Generalidades del sistema

ECI Paw Connect es una plataforma que digitaliza el proceso de adopción de mascotas de la
fundación Paw Connect. El sistema se encarga de gestionar un catálogo distribuido en una estructura jerárquica
de refugios aliados de la forma : Red Nacional → Ciudad → Refugio, donde cada refugio contiene las
mascotas disponibles segun los filtros de busqeuda. La plataforma permite recorrer cualquier nivel de esa jerarquía de forma
transparente, tratando un refugio individual y la red completa de la misma manera, por otro lado ofrece
distintas formas de recorrer el catálogo (filtros), por especie, por rango de edad, por compatibilidad o
por refugio. Cada solicitud de adopción avanza por los estados: PENDIENTE → EN_REVISIÓN → APROBADA / RECHAZADA → COMPLETADA.

La información se persiste o almacena en AWS Mongo Atlas y los reportes estadísticos se publican en AWS S3 Buckets.

### Diagrama de contexto realizado en draw.io:

![Diagrama de contexto de ECI Paw Connect](docs/images/diagrama-contexto.png)

### Actores identificados

Los actores identificados son:
- **Adoptador .** Es el usuario final de la plataforma, el cual explora el catálogo filtrando por especie,
  rango de edad, compatibilidad o refugio, dependiendo tambien del refugio y registra su solicitud de adopción.

- **Administrador de Refugio.** Adminsitra sobre un único refugio. Inscribe en el catálogo las mascotas
  de su refugio con sus atributos mencionados y hace avanzar el estado de las solicitudes que recibe, llevándolas del 
  estado incial al final.

- **Administrador de la Fundación/Red.** Opera sobre la red completa, donde afilia nuevos refugios, organiza
  la jerarquía agrupándolos por ciudad y consulta los reportes consolidados de toda la red a traves de los actores externos.

### Sistemas externos

- **AWS MongoDB Atlas.** Almacena la información de mascotas, refugios y solicitudes de adopción.

- **AWS S3 Buckets.** Almacena los reportes estadísticos que genera el sistema.


## Punto 2

## 2. Requerimientos del Sistema

### Requerimientos Funcionales



**RF-01 Consultar el catálogo en cualquier nivel de la jerarquía de refugios**

ECI Paw Connect debe tener la capacidad de poder permitir consultar el catálogo de mascotas sobre
cualquier punto de la jerarquía de refugios, mediante la misma operación. Al consultar un refugio, el sistema debe
devolver solo las mascotas de ese refugio, al consultar una ciudad o la red nacional, debe
devolver la consolidación de las mascotas de todos los refugios que contiene en cualquier nivel de
profundidad. 

*Patrón asociado al requerimiento: **Composite**. Un refugio (como hoja) y una agrupación de refugios (como compuesto)
exponen la misma interfaz, de forma que el cliente los trata de manera uniforme y la jerarquía puede crecer sin impacto
sobre las consultas realizadas.


**RF-02  Recorrer el catálogo con múltiples criterios de búsqueda**

ECI Paw Connect debe tener la capacidad de permitir al Adoptador recorrer el catálogo de mascotas
aplicando uno de los siguientes criterios de búsqueda mencionados previamente: por especie, por rango de edad en meses, por
compatibilidad o por refugio. El sistema devuelve el resultado

*Patrón asociado a este requerimiento: **Iterator**. Cada criterio se implementa como un iterador concreto que expone la
misma interfaz de recorrido, lo que permite intercambiar la forma de navegar el catálogo e  incorporar nuevos criterios 
sin modificar al cliente que consume los resultados.

**RF-03 Registrar mascotas en el catálogo de un refugio**

ECI Paw Connect debe tener la capacidad de permitir al Administrador de Refugio poder inscribir una
mascota en el catálogo de su refugio asocidado, dionde registra su número de identificación, nombre, especie, 
edad en meses, tamaño y sus tres indicadores de compatibilidad: con niños, con otras mascotas y con espacios reducidos. 
El sistema debe rechazar el registro cuando el número de identificación ya exista en la red o cuando alguno de
los atributos obligatorios esta ausente, e informar al administrador la causa del rechazo de la operación.

### Requerimientos No Funcionales

**RNF-01 — Rendimiento de las búsquedas**

El sistema deberá resolver y responder cualquier consulta sobre el catálogo en un tiempo máximo de 1 segundo para el 90% 
de las peticiones, bajo condiciones normales de operación, incluyendo  aquellas búsquedas que recorren la totalidad de la 
red nacional.

**RNF-02 — Escalabilidad del catálogo**

El sistema deberá soportar hasta 10.000 mascotas registradas distribuidas en la jerarquía de
refugios,de acuerdo a lo expuesto en el RFN-01 manteniendo el mismo comportamiento en las operaciones de recorrido y consulta.










## Herramientas

- **Modelado:** Draw.io
- **Diseño de interfaces:** Figma

---

## Evidencias de acceso previo al parcial

### Ejecución con Maven

![Evidencia Maven](docs/images/evidencia-maven.png)

### Acceso a herramienta de modelado

![Evidencia herramienta de modelado](docs/images/evidencia-modelado.png)

### Acceso a Figma

![Evidencia Figma](docs/images/evidencia-figma.png)