# Diseño de software - Ingeniería en Computación - Caso #1 - 15%

# DUA streamliner 
Para trabajar en forma individual o máximo grupos de 2. 

## Sistema Inteligente para la Generación Automatizada del DUA

El **Documento Único Aduanero (DUA)** es el instrumento oficial utilizado para declarar mercancías ante la autoridad aduanera. Funciona como el documento estandarizado que consolida información clave del importador o exportador, el consignatario, la mercancía, el régimen aduanero, los valores, tributos, transporte y documentos soporte. En Costa Rica, su estructura y campos están definidos por el Ministerio de Hacienda, y su correcta elaboración es crítica para evitar retrasos, multas o rechazos en los procesos de importación y exportación.

La correcta preparación del DUA implica interpretar múltiples documentos fuente: facturas comerciales, listas de empaque, certificados de origen, conocimientos de embarque, pólizas, permisos especiales, contratos, entre otros. Estos documentos suelen venir en formatos heterogéneos como Excel, Word, PDF e incluso imágenes escaneadas. Cada empresa, proveedor o agente utiliza estructuras distintas, lo que convierte el llenado manual en un proceso repetitivo, propenso a errores y altamente dependiente del conocimiento experto.

---

## Intención del DUA streamliner 

La intención es desarrollar un sistema automatizado que permita a importadores y exportadores simplificar drásticamente el proceso de elaboración del DUA.

### 1. Entrada del Sistema

El usuario únicamente deberá proporcionar:

* Un **folder path** (ruta de carpeta local o en red).
* Dentro de esa carpeta se encontrarán:

  * Archivos Excel (.xlsx)
  * Documentos Word (.docx)
  * Archivos PDF
  * Imágenes (facturas o documentos escaneados)

El sistema no exigirá formatos rígidos predefinidos, sino que será capaz de interpretar distintas estructuras documentales.

---

### 2. Procesamiento Inteligente

El sistema realizará las siguientes funciones:

#### a) Lectura Multiformato

* Uso de motores de lectura para Word y Excel.
* Extracción de texto estructurado y no estructurado desde PDFs.
* OCR avanzado para imágenes escaneadas.

#### b) Extracción Semántica

Mediante modelos de IA entrenados para comprender terminología aduanera, el sistema identificará:

* Datos del importador/exportador
* Información del proveedor
* Descripción comercial y arancelaria de mercancías
* Cantidades, pesos, valores FOB/CIF
* Incoterms
* Información de transporte
* Número y fecha de factura
* País de origen y procedencia
* Régimen aduanero aplicable

La extracción no será únicamente por coincidencia textual, sino por **interpretación contextual**, permitiendo identificar información incluso cuando los documentos tengan formatos distintos.

---

### 3. Mapeo al Template Oficial del DUA

Con base en el template oficial vigente del DUA definido por el Ministerio de Hacienda, el sistema:

* Mapeará automáticamente cada dato extraído a su casilla correspondiente.
* Validará coherencia básica (ejemplo: sumatoria de valores, consistencia de monedas, fechas).
* Marcará campos ambiguos o con baja confianza.

---

### 4. Generación del Documento Word Prellenado

Como resultado, el sistema generará:

* Un archivo **Word (.docx)** con el DUA completamente rellenado.
* Campos con codificación visual:

  * Verde: alta confianza
  * Amarillo: confianza media
  * Rojo: requiere revisión

El objetivo no es eliminar al experto aduanero, sino convertirlo en **validador estratégico**, reduciendo el trabajo operativo manual.

---
## Actividades:

El objetivo de este caso es que se cubran aspectos de diseño de un sistema tales como: 

- Frontend o aplicación de usuario 
- Backend (lógica de negocios) 
- Data (modelos de datos) 
- Control de calidad, cómo se va a realiza el control de calidad del sistema 
- Deployment, en donde y cómo se va a poner el sistema en la etapa de desarrollo, testing, stage y producción; tomando en cuenta CI CD 
- Cubrir aspectos del diseño como: UX UI, diseño orientado a objetos, patrones arquitectónicos, paradigmas de arquitectura, diseño de  arquitectura, seguridad, disponibilidad, confiabilidad, observability, diseño de recursos, diseño en la nube, entre otros. 

Para realizar este caso, el profesor en modo acompañamiento, abordará cada uno de los aspectos de diseño mencionandos anteriormente y en clase se trabajaran guías para ir construyendo el diseño de esta solución.  Cada entregable se irá evaluando en cumplimiento y finalmente habrá una nota final al terminar el diseño completo. Dichos entregables se harán por medio del classroom. 


Para iniciar el caso, debe realizar las siguientes tareas:

1. Estudiar la información en las referencias 
2. Conseguir ejemplos de documentos que se usan para llenar un DUA y un DUA llenado 
3. Investigar como funcionan los procedimientos de importación y exportación
4. Investigar diseños de soluciones hechas que hagan algo similar, tomar nota de tecnologías, arquitecturas, lenguajes, herramientas, cloud services, bases de datos, entre otros. 
5. Cree un repositorio de github donde va a recidir el caso y diseño completo.
6. Agregue un readme.md en el root donde se va a  realizar la documentación. Inicie con una portada que tenga el nombre del proyecto, el problema que se quiere resolver y los autores. 
7. Esto se evaluará interactivamente el miércoles 4 de Marzo. 

Referencias:

- Qué es DUA: https://alianza-logistics.com/documento-unico-aduanero-2/
- Template del documento DUA: https://www.hacienda.go.cr/docs/Mensaje_TD_DUA-V3-17-12-03-2025.pdf
- Cómo llenar el DUA: https://gestionesenlinea.es/formulario-dua-documento-unico-administrativo/

