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