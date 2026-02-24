# Diseño de bases de datos

El **diseño de bases de datos** es el proceso sistemático de analizar una realidad (negocio, organización o sistema) y transformarla en una estructura lógica que permita **almacenar, organizar y recuperar información de forma eficiente, consistente y escalable**.

No se trata solo de crear tablas o colecciones de documentos si no que implica:

* Entender los requerimientos del negocio
* Identificar entidades y relaciones
* Definir reglas de integridad
* Minimizar redundancia
* Optimizar consultas futuras
* Anticipar crecimiento y cambios

Un buen diseño reduce errores, mejora el rendimiento y facilita el mantenimiento. Un mal diseño genera datos duplicados, inconsistencias y sistemas difíciles de escalar.

---

## ¿Qué es un diseño de base de datos?

Es la **representación estructurada de cómo se almacenarán los datos** dentro de un sistema gestor de bases de datos, como por ejemplo postgresql, sql server, mariadb, cosmos, mongodb, etc. 

El diseño suele dividirse en tres niveles:

### Diseño conceptual

Describe la realidad del negocio sin preocuparse por tecnología.
Se utilizan diagramas Entidad-Relación (ER). Diseñar a nivel conceptual prácticamente no se hace en la práctica.

Ejemplo:

* Cliente
* Pedido
* Producto
* Un cliente realiza pedidos
* Un pedido contiene productos

### Diseño lógico

Traduce el modelo conceptual al modelo de datos específico (relacional, documental, etc.).

Aquí se definen:

* Tablas o colecciones
* Atributos
* Claves primarias
* Claves foráneas
* Relaciones


### Diseño físico

Define cómo se almacenan realmente los datos:

* Índices
* Particionamiento
* Tipos de datos específicos
* Estrategias de almacenamiento

Este nivel depende del motor (por ejemplo, Microsoft SQL Server o MongoDB). Normalmente trabajamos directamente a nivel de diseño físico, el cual ya considera todos los anteriores. 

## ¿Qué son los modelos de datos?

Un **modelo de datos** es la forma estructural en que un sistema organiza la información.

Define:

* Cómo se representan los datos
* Cómo se relacionan
* Cómo se consultan

Existen múltiples modelos, pero los más usados hoy son:

* Relacional
* Documental (NoSQL)
* Grafos

Cada uno responde mejor a distintos tipos de problemas.

# Ejemplo comparativo de modelado

Supongamos un sistema de red social simple donde:

* Un usuario puede seguir a otros usuarios
* Un usuario puede publicar contenido

## Modelo Relacional

### Tablas:

**Usuarios**

* id_usuario (PK)
* nombre
* email

**Publicaciones**

* id_publicacion (PK)
* contenido
* id_usuario (FK)

**Seguidores**

* id_seguidor (FK)
* id_seguido (FK)

### Características:

* Estructura rígida
* Relaciones mediante claves foráneas
* Integridad referencial fuerte
* Ideal para sistemas transaccionales (OLTP)

Ventaja: consistencia
Desventaja: consultas complejas pueden requerir múltiples JOIN

## Modelo Documental

Usado por motores como MongoDB.

### Colección: usuarios

```json
{
  "_id": "U1",
  "nombre": "Ana",
  "email": "ana@email.com",
  "seguidores": ["U2", "U3"],
  "publicaciones": [
    {
      "id": "P1",
      "contenido": "Hola mundo"
    }
  ]
}
```

### Características:

* Estructura flexible
* No requiere esquema fijo
* Datos anidados
* Ideal para aplicaciones web modernas

Ventaja: flexibilidad
Desventaja: puede duplicar información

## Modelo Graph

Usado por motores como Neo4j.

Aquí los datos se modelan como:

### Nodos:

* Usuario
* Publicación

### Relaciones:

* (Usuario)-[:SIGUE]->(Usuario)
* (Usuario)-[:PUBLICA]->(Publicación)

Visualmente:

```
(Ana) ---SIGUE---> (Carlos)
(Ana) ---PUBLICA--> (Post1)
```

### Características:

* Relaciones como ciudadanos de primera clase
* Excelente para consultas de redes
* Ideal para recomendaciones, redes sociales, fraude

Ventaja: consultas de relaciones profundas son muy eficientes
Desventaja: no siempre ideal para datos altamente estructurados y tabulares


# Comparación conceptual

| Aspecto            | Relacional    | Documental  | Graph                |
| ------------------ | ------------- | ----------- | -------------------- |
| Estructura         | Rígida        | Flexible    | Basada en relaciones |
| Relaciones         | JOIN          | Referencias | Aristas directas     |
| Escenarios ideales | Finanzas, ERP | Apps web    | Redes sociales       |


Procedamos a hacer nuestro primer diseño relacional para un pequeño sistema.

**Sistema:** Registro de limpieza de baños. Una empresa de limpieza que atiende múltiples centros comerciales en horarios específicos, quiere tener una bitácora digital de aquellas personas que realizan la limpieza de los baños de los centros comerciales, registrando tanto la persona, la hora de inicio y final y cualquier comentario o situación que se haya presentado. Teniendo en cuenta que cada centro comercial puede tener varios baños. Proceda a diseñar una base de datos que funcione como bitácora de trabajo para esta empresa. La base de datos debe llevar control de los empleados de limpieza, los centros comerciales, los baños dentro de cada centro comercial y la bitácora respectiva. 

1. Cree un markdown file para la especificación y proceda a escribir las siguientes especificaciones:

- Motor de base de datos y su versión
- Nombre de la base de datos (al ser nombres de objetos no pueden tener espacios)
- Contexto: escriba un breve resumen del sistema que se desea crear. 
- Definición de tablas:  
    - proceda a averiguar todas las entidades necesarias para modelar los datos del sistema que se quiere hacer
    - averigue los requerimientos de información que requiere almacenar cada entidad, es decir, aprenda como funciona el negocio
    - agregue los diferentes campos a las entidades usando la sintaxis  nombreDeTabla(nombreDeCampo1:[tipoDeDato], ..., nombreDeCampo2:[tipoDeDato]). Averigue los tipos de datos y sus tamaños dependiendo del motor de bases de datos seleccionado. 


2. Solicite la creación de un script de base de datos con las instrucciones necesarias DDL para crear la base de datos, sus entidades, restricciones y definiciones. Además que genere un diagrama físico de la base de datos.  

3. Validación básica de la base de datos

- Los tipos de datos tienen el espacio y son del tipo requerido para responder al requerimiento
- Están las llaves primarias debidamente definidas en cada tabla
- Están las llaves foráneas debidamente definidas en cada tabla que lo requiera
- Solicite ejemplos de la información que se almacenaría en cada tabla y observe si existe información que se duplicaría innecesariamente o bien que ahorraría espacio no repetirla, especialmente si se trata de texto 


