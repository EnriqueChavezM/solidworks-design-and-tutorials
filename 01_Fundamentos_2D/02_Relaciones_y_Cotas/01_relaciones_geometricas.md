# 01. Relaciones Geométricas en Croquis 📐

En esta sección se documenta el uso y la aplicación de las **relaciones geométricas** en SolidWorks. Estas restricciones constituyen la base del diseño paramétrico, permitiendo definir el comportamiento, la orientación y la interacción entre entidades sin depender exclusivamente de cotas numéricas.

---

## 🎯 Objetivos del Módulo

- **Dominar el control paramétrico:** Restringir la geometría mediante reglas lógicas antes de aplicar dimensiones.
- **Identificar los estados del croquis:** Diferenciar visualmente cuando un croquis está insuficiente, completamente o sobredefinido.
- **Optimizar la intención de diseño:** Garantizar que las piezas respondan correctamente ante futuros cambios de dimensiones sin romper el modelo.

---

## Tabla de contenido

- [01. Relaciones Geométricas en Croquis 📐](#01-relaciones-geométricas-en-croquis-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Estados de Definición del Croquis](#1-estados-de-definición-del-croquis)
  - [2. Relaciones Geométricas Fundamentales](#2-relaciones-geométricas-fundamentales)
    - [Relaciones de Orientación y Posición](#relaciones-de-orientación-y-posición)
    - [Relaciones entre Múltiples Entidades](#relaciones-entre-múltiples-entidades)
  - [3. Relaciones Automáticas vs. Manuales](#3-relaciones-automáticas-vs-manuales)
  - [4. Buenas Prácticas de Restricción Paramétrica](#4-buenas-prácticas-de-restricción-paramétrica)
  - [5. Ejemplo Práctico: Palanca de Acoplamiento Simétrica](#5-ejemplo-práctico-palanca-de-acoplamiento-simétrica)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Estados de Definición del Croquis

En SolidWorks, el color de las entidades dentro del boceto 2D indica directamente su grado de restricción:

| Color | Estado | Significado Técnico |
| :---: | :--- | :--- |
| 🔵 **Azul** | **Insuficientemente definido** (*Under-defined*) | La geometría posee grados de libertad libres; puede moverse o cambiar de tamaño al arrastrarla. |
| ⬛ **Negro** | **Completamente definido** (*Fully Defined*) | **Estado ideal.** Toda la posición y dimensiones están fijadas respecto al Origen. |
| 🔴 **Rojo** | **Sobredefinido** (*Over-defined*) | Existen cotas o relaciones geométricas contradictorias que generan conflicto. |
| 🟡 **Amarillo** | **Solución no válida** | La geometría actual no se puede calcular matemáticamente. |

---

## 2. Relaciones Geométricas Fundamentales

Las relaciones se aplican seleccionando dos o más entidades mediante la tecla `Ctrl + Clic` y asignando la restricción deseada en el menú lateral (**PropertyManager**):

### Relaciones de Orientación y Posición

- **Horizontal / Vertical:** Alinea una línea o un par de puntos a lo largo de los ejes $X$ o $Y$ del plano.
- **Coincidente:** Fuerza a un punto a situarse exactamente sobre una línea, arco u otro punto.
- **Fijo:** Inmoviliza un punto o línea en el espacio (usar únicamente en casos excepcionales de bocetado rápido).

### Relaciones entre Múltiples Entidades

- **Perpendicular:** Modifica dos líneas para que formen un ángulo exacto de $90^\circ$.
- **Paralelo:** Mantiene la misma dirección angular entre dos o más líneas.
- **Colineal:** Obliga a dos o más segmentos de línea a compartir la misma línea infinita de trazado.
- **Concéntrico:** Alinea los centros geométricos de dos o más arcos o círculos.
- **Tangente:** Garantiza una transición suave de curvatura entre una línea y un arco, o entre dos arcos.
- **Igual:** Iguala las longitudes de varias líneas o los radios/diámetros de varios círculos de forma simultánea.
- **Simétrico:** Fuerza a dos entidades a mantenerse a la misma distancia respecto a una línea constructiva (eje de simetría).

---

## 3. Relaciones Automáticas vs. Manuales

1. **Relaciones Automáticas:** SolidWorks añade restricciones en tiempo real mientras trazas (por ejemplo, los íconos amarillos de *Horizontal*, *Vertical* o *Coincidente* que aparecen junto al cursor).
2. **Relaciones Manuales:** Se agregan posteriormente seleccionando las entidades con `Ctrl + Clic` y usando el panel **Agregar relaciones**.

---

## 4. Buenas Prácticas de Restricción Paramétrica

1. **Relaciones antes que Cotas:** Aplica siempre primero las relaciones geométricas de posición e igualdad antes de colocar cotas numéricas. Esto reduce drásticamente la cantidad de dimensiones necesarias.
2. **Usa el Origen `(0,0)`:** Al menos un punto clave del croquis base debe estar vinculado directamente al Origen para anclar el modelo en el espacio 3D.
3. **Uso de Líneas Constructivas:** No escatimes en usar líneas de centro (**constructivas**); son tus mejores aliadas para aplicar simetrías y ubicar componentes de referencia sin que afecten la extrusión final de la pieza.
4. **Aprovecha la relación de Igualdad:** En lugar de acotar 4 barrenos idénticos con $12\text{ mm}$, acota solo uno y aplica la relación de **Igualdad** a los otros tres. Si la cota cambia en el futuro, todos se actualizarán automáticamente.

---

## 5. Ejemplo Práctico: Palanca de Acoplamiento Simétrica

Vamos a modelar una pieza tipo palanca con dos perforaciones circulares en sus extremos, utilizando relaciones geométricas para asegurar que los círculos se mantengan simétricos y alineados.

### Paso a Paso

1. **Crear Líneas Constructivas (Ejes de Simetría):**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja una **Línea constructiva** horizontal que pase por el origen `(0,0)` y otra vertical. Esto servirá como referencia de simetría.

2. **Dibujar la Geometría Base:**
   - Dibuja dos círculos separados a cada lado del origen.
   - Dibuja un contorno que los una mediante líneas rectas tangentes a los círculos exteriores.
   - Dibuja dos círculos dentro de cada círculo (barreno)

3. **Aplicar Relaciones Geométricas:**
   - **Concentricidad:** Selecciona el contorno circular exterior de un extremo y el círculo interior del barreno; aplica la relación **Concéntrico**. Haz lo mismo con el otro extremo.
   - **Igualdad:** Selecciona ambos círculos pequeños de los extremos y aplica la relación **Igual**. Así, si cambias el diámetro de uno, el otro se actualizará automáticamente.
   - **Horizontalidad:** Selecciona los centros de los dos círculos extremos y la línea constructiva central, aplicando una relación **Horizontal** para que queden alineados simétricamente respecto al origen.
   - **Tangencia:** Asegúrate de que las líneas que unen los extremos formen una transición suave seleccionando la línea y el círculo correspondientes y aplicando **Tangente**.

4. **Acotación Inteligente de Control:**
   - Gracias a las relaciones aplicadas, ahora solo necesitas acotar la distancia entre centros de los círculos (por ejemplo, **100 mm**), el diámetro de los círculos (por ejemplo, **50 mm**), la separación entre barreno y el  diámetro externo de los barrenos (por ejemplo, **15 mm**). El croquis mantendrá su simetría de manera automática.

5. **Verificación:**
   - Comprueba que las líneas cambien a color **negro**, indicando que el croquis está **Completamente Definido** gracias a la combinación correcta de relaciones geométricas y pocas cotas.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica04.png" width="500" alt="Captura de pantalla de la práctica 04">

---

[Inicio](#01-relaciones-geométricas-en-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
