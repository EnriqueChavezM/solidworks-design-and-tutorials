# 01. Miembros Estructurales y Perfiles en CAD 🏗️

El módulo de **Piezas Soldadas** (*Weldments*) permite diseñar estructuras de bastidores, marcos y soportes tubulares o perfilados de manera eficiente. La herramienta **Miembro Estructural** extruye perfiles estandarizados (ISO, ANSI, DIN) a lo largo de los segmentos de un croquis 2D o 3D.

---

## 🎯 Objetivos del Módulo

- **Modelar bastidores complejos:** Utilizar croquis 2D y 3D como líneas de centro para la colocación de perfiles.
- **Aplicar estándares de la industria:** Seleccionar perfiles normalizados (tubos cuadrados, rectangulares, vigas en I, ángulos L, etc.).
- **Alinear la geometría del perfil:** Ubicar el punto de origen del perfil respecto a las líneas de trazado para controlar dimensiones exteriores.

---

## Tabla de contenido

- [01. Miembros Estructurales y Perfiles en CAD 🏗️](#01-miembros-estructurales-y-perfiles-en-cad-️)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Croquis de Estructura (Estructura Alámbrica 2D/3D)](#1-croquis-de-estructura-estructura-alámbrica-2d3d)
  - [2. Configuración del Miembro Estructural](#2-configuración-del-miembro-estructural)
  - [3. Gestión de Grupos de Perfiles](#3-gestión-de-grupos-de-perfiles)
  - [4. Ubicación y Rotación del Perfil](#4-ubicación-y-rotación-del-perfil)
  - [5. Buenas Prácticas y Criterios de Diseño](#5-buenas-prácticas-y-criterios-de-diseño)
  - [6. Ejemplo Práctico: El marco de una mesa metálica](#6-ejemplo-práctico-el-marco-de-una-mesa-metálica)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Croquis de Estructura (Estructura Alámbrica 2D/3D)

La base para construir una pieza soldada es la estructura alámbrica (*Wireframe*), que define el esqueleto sobre el cual se posicionarán los perfiles:

- **Croquis 2D:** Adecuado para marcos planos, cerchas de un solo plano o bastidores sencillos.
- **Croquis 3D:** Esencial para estructuras tridimensionales (chasis, torres, plataformas) donde las líneas se extienden en los ejes $X, Y, Z$.
- **Continuidad de segmentos:** Las líneas y arcos del croquis determinan la trayectoria de extrusión del perfil.

---

## 2. Configuración del Miembro Estructural

Al seleccionar la herramienta **Miembro Estructural**, se deben definir tres parámetros jerárquicos de biblioteca:

1. **Estándar:** Define la norma técnica de fabricación (ej. *ISO*, *ANSI Pulgada*, *DIN*).
2. **Tipo:** Especifica la geometría de la sección transversal (ej. *Tubo cuadrado*, *Tubo rectangular*, *Canal en C*, *Ángulo igual*).
3. **Tamaño:** Especifica las dimensiones y espesor de pared exactos (ej. $40 \times 40 \times 4$, $2 \times 2 \times 3/16$).

---

## 3. Gestión de Grupos de Perfiles

Los segmentos de croquis seleccionados para aplicar miembros estructurales se organizan por **Grupos**:

- **Grupos continuos:** Colección de segmentos conectados punto a punto en un mismo plano. Permiten aplicar uniones a inglete o a tope automáticas entre ellos.
- **Grupos paralelos:** Colección de segmentos independientes pero paralelos entre sí (ej. las cuatro columnas verticales de una mesa).
- **Tratamiento de esquinas:** Permite elegir entre corte a inglete ($45^\circ$), tope simple o tope invertido para las intersecciones de perfiles dentro del grupo.

---

## 4. Ubicación y Rotación del Perfil

Por defecto, el perfil de la biblioteca se centra sobre la línea de croquis. Sin embargo, para controlar las dimensiones externas de la estructura es necesario modificar su alineación:

- **Ubicación del perfil (*Locate Profile*):** Permite cambiar el punto de perforación (*Pierce Point*) seleccionando cualquiera de los vértices o puntos de centro del perfil trazado.
- **Ángulo de rotación:** Permite girar la sección transversal un ángulo especificado ($\theta$) respecto a la línea del croquis (ej. orientar un ángulo L a $45^\circ$ o $90^\circ$).
- **Alineación respecto a ejes/superficies:** Alinea uno de los ejes del perfil paralelamente a una línea o plano de referencia externo.

---

## 5. Buenas Prácticas y Criterios de Diseño

- **Regla de oro:** Acota la estructura alámbrica (*Croquis 3D*) según las **dimensiones exteriores máximas** del bastidor y utiliza la función **Ubicar Perfil** para que la pared exterior del tubo coincida exactamente con las líneas del croquis.
- **Minimiza el número de grupos:** Organiza los perfiles en el menor número de grupos posible para permitir que el software resuelva las esquinas e ingletes de forma automática.
- **Estandarización de biblioteca:** Si tu empresa utiliza perfiles no comerciales o personalizados, puedes crear un croquis de la sección deseada y guardarlo en la biblioteca con formato `.sldlfp` (*Lib Feat Part*).

---

## 6. Ejemplo Práctico: El marco de una mesa metálica

Imagina que necesitas construir una mesa rectangular de $1000 \times 600\text{ mm}$ y una altura de $800\text{ mm}$.

### Paso a Paso

1. **Crear el "Esqueleto" (Croquis 3D):**
   - Todo parte de las líneas que definen la forma de tu estructura.
   - Abres un nuevo archivo de pieza en SolidWorks.
   - Seleccionas la herramienta de Croquis 3D (3D Sketch).
   - Dibujas un rectángulo flotando en el aire (representando la parte superior de la mesa) y cuatro líneas verticales hacia abajo que representan las patas.
   - Acotas todo con las medidas reales (1000 mm de largo, 600 mm de ancho y 400 mm de alto). Este croquis es como los cimientos de una casa.

2. **Activar la herramienta de Miembro Estructural:**
   - Te vas a la pestaña de Piezas Soldadas (si no la ves, haz clic derecho en cualquier pestaña superior y actívala).
   - Haces clic en el botón **Miembro Estructural** (Structural Member).

3. **Seleccionar el Perfil Comercial:**
   - SolidWorks te pedirá que elijas el estándar del material que vas a usar en el mundo real:
     - **Norma:** ISO o ANSI (por ejemplo, ISO).
     - **Tipo:** Tubo cuadrado, tubo rectangular, perfil C, perfil angular, etc. (elegimos Tubo cuadrado).
     - **Tamaño:** Seleccionas una medida comercial, por ejemplo, $40\text{ mm} \times 40\text{ mm} \times 4\text{ mm}$.

4. **Aplicar el perfil a las líneas:**
   - En la zona gráfica, vas haciendo clic en las líneas de tu croquis 3D.
   - SolidWorks extruirá automáticamente el perfil seleccionado a lo largo de esas líneas, adaptando la forma como si estuvieras cortando y soldando tubos reales.
   - Puedes organizar los perfiles en Grupos (por ejemplo, un grupo para el marco superior y otro grupo para las cuatro patas) para que las intersecciones se corten correctamente.

5. **Ajustar Esquinas y Cortes (Uniones):**
   - En las esquinas del marco superior, puedes configurar el tipo de corte: corte a 45° (inglete) para que embonen perfectamente, o cortes rectos traslapados.
   - También puedes usar la herramienta Recortar/Extender si un tubo choca contra otro para que la soldadura quede limpia.

6. **Ventaja principal:** Si el cliente o el diseño cambia y la mesa ahora debe medir $1200\text{ mm}$, solo modificas la medida en el croquis 3D inicial y SolidWorks actualiza automáticamente todos los tubos, generando además la lista de cortes (Cut List) lista para producción con las medidas exactas de cada tramo que debes cortar.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica24.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#01-miembros-estructurales-y-perfiles-en-cad-️)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
