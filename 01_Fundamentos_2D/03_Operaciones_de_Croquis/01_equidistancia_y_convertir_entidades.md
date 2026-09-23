# 01. Equidistancia y Convertir Entidades en Croquis 📐

En esta sección se documentan dos de las herramientas de productividad y parametrización más potentes del entorno de croquis 2D en SolidWorks: **Convertir Entidades** y **Equidistanciar Entidades (Offset)**. Ambas permiten reutilizar geometría existente y acelerar significativamente el modelado paramétrico.

---

## 🎯 Objetivos del Módulo

- **Reutilizar geometría 3D en 2D:** Aprender a proyectar aristas y contornos de modelos previos directamente sobre un nuevo croquis.
- **Crear perfiles paralelos:** Dominar la herramienta de equidistancia para generar paredes, espesores o contornos desfasados de forma automática.
- **Mantener la asociatividad paramétrica:** Comprender cómo los cambios en la geometría original se reflejan dinámicamente en las entidades proyectadas o equidistanciadas.

---

## Tabla de contenido

- [01. Equidistancia y Convertir Entidades en Croquis 📐](#01-equidistancia-y-convertir-entidades-en-croquis-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Convertir Entidades (Convert Entities)](#1-convertir-entidades-convert-entities)
    - [Características Clave](#características-clave)
    - [Cómo utilizarla](#cómo-utilizarla)
  - [2. Equidistanciar Entidades (Offset Entities)](#2-equidistanciar-entidades-offset-entities)
    - [Parámetros Principales del PropertyManager](#parámetros-principales-del-propertymanager)
  - [3. Buenas Prácticas y Criterios de Diseño](#3-buenas-prácticas-y-criterios-de-diseño)
  - [4. Ejemplo Práctico: Tapa de Carcasa con Paredes Paralelas](#4-ejemplo-práctico-tapa-de-carcasa-con-paredes-paralelas)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Convertir Entidades (Convert Entities)

La herramienta **Convertir Entidades** proyecta una copia exacta de aristas, contornos, caras o líneas de un modelo 3D existente (o de otro croquis) sobre el plano de trabajo activo.

### Características Clave

- **Asociatividad (Relación *En arista* / *On Edge*):** Las líneas creadas se vinculan paramétricamente al elemento original. Si la pieza 3D base cambia de dimensiones, el croquis convertido se actualizará automáticamente.
- **Uso ideal:** Creación de tapas para carcasas, bases que deben coincidir exactamente con una cara existente, o protuberancias que nacen a partir de contornos previos.

### Cómo utilizarla

1. Abre un croquis en el plano o cara deseada.
2. Selecciona la arista, cara o contorno completo que deseas copiar.
3. Haz clic en el ícono **Convertir entidades** en la barra de croquis. El sistema generará líneas negras vinculadas al original.

---

## 2. Equidistanciar Entidades (Offset Entities)

La herramienta **Equidistancia** crea copias paralelas de líneas, arcos o contornos completos a una distancia uniforme especificada por el usuario.

### Parámetros Principales del PropertyManager

- **Distancia de equidistancia:** Define la separación numérica exacta ($D$) entre la entidad original y la nueva copia.
- **Invertir dirección (Reverse):** Cambia el lado hacia el cual se aplicará el desfase (hacia adentro o hacia afuera del contorno).
- **Opciones de cadena (Select chain):** Selecciona automáticamente todas las entidades conectadas al hacer clic en una sola línea del contorno.
- **Tapas (Cap ends):** Permite cerrar los extremos de una equidistancia abierta convirtiéndola en un contorno cerrado (útil para crear ranuras o paredes de espesor constante).
  - *Tipos de tapa:* Arcos (`Arcs`) o líneas rectas (`Lines`).
- **Construir base geométrica (Add dimensions):** Añade una cota explícita al valor de la equidistancia para poder modificarla posteriormente haciendo doble clic.

---

## 3. Buenas Prácticas y Criterios de Diseño

1. **Cuidado con las referencias externas:** Cuando usas *Convertir Entidades*, el croquis depende de una pieza o croquis externo. Si eliminas la entidad original por error, el croquis puede mostrar advertencias de referencia rota.
2. **Cadena Seleccionada (Select Chain):** Al usar *Equidistanciar entidades*, asegúrate de que la opción de selección en cadena esté activa para que no tengas que seleccionar cada línea una por una.
3. **Usa Equidistancia para espesores de pared:** Al diseñar tapas, cubiertas o perfiles estructurales, utiliza *Offset* en lugar de redibujar manualmente líneas paralelas; esto garantiza un espesor uniforme y fácil de parametrizar.
4. **Limpieza de excesos:** Al aplicar equidistancias en geometrías complejas con esquinas agudas, es posible que se generen líneas encimadas o bucles. Utiliza la herramienta de **Recortar entidades** (*Trim Entities*) para limpiar los sobrantes antes de extruir.

---

## 4. Ejemplo Práctico: Tapa de Carcasa con Paredes Paralelas

Vamos a diseñar la base de una tapa o carcasa rectangular que requiere un espesor de pared constante y un rebaje interior utilizando estas herramientas.

### Paso a Paso

1. **Crear el Perfil Exterior:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja un rectángulo centrado de **100 mm x 60 mm**.

2. **Aplicar Equidistancia (Offset) para el Espesor de Pared:**
   - Selecciona la herramienta **Equidistanciar entidades** en la barra de herramientas de croquis.
   - En el panel de propiedades izquierdo, define una distancia de **5 mm**.
   - Haz clic sobre una de las líneas del rectángulo; SOLIDWORKS seleccionará todo el contorno cerrado en cadena.
   - Si la vista previa apunta hacia afuera, marca la casilla **Invertir dirección (Reverse)** para que el desfase ocurra hacia el interior de la pieza.
   - Haz clic en la paloma verde (Aceptar). Se generarán automáticamente las cotas de distancia y el nuevo contorno paralelo.

3. **Simular Conversión de Entidades (Proyecto de Arista):**
   - Imagina que tenemos una perforación previa o un elemento de referencia. (Puedes dibujar un círculo pequeño en el origen o imaginar que proyectamos desde una operación 3D).
   - Selecciona la herramienta **Convertir entidades**.
   - Haz clic sobre la arista o círculo de referencia que deseas duplicar en tu croquis actual. Observa cómo aparece la línea con un color negro especial y una relación geométrica de referencia externa.

4. **Verificación y Limpieza:**
   - Comprueba que los contornos cerrados estén listos para futuras extrusiones.
   - Asegúrate de que las cotas generadas por el offset te otorguen el control deseado sobre el grosor de la pared.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica07.png" width="500" alt="Captura de pantalla de la práctica 07">

---

[Inicio](#01-equidistancia-y-convertir-entidades-en-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
