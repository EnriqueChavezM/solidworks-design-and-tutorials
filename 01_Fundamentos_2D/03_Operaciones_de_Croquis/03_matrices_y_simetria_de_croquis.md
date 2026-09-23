# 03. Matrices y Simetría de Croquis 📐

En esta sección se documenta el uso de las herramientas de multiplicación geométrica en el entorno de croquis 2D en SolidWorks: **Matriz Lineal**, **Matriz Circular** y **Simetría de Entidades**, diseñadas para automatizar el trazado de patrones repetitivos de forma paramétrica.

---

## 🎯 Objetivos del Módulo

- **Automatizar patrones repetitivos:** Aprender a replicar geometrías en direcciones lineales y radiales sin necesidad de dibujarlas una por una.
- **Garantizar la simetría estructural:** Utilizar ejes de simetría para reflejar diseños complejos de manera perfectamente equilibrada.
- **Mantener el control paramétrico:** Comprender cómo las cotas de separación e instancia actualizan todo el patrón automáticamente ante cualquier modificación.

---

## Tabla de contenido

- [03. Matrices y Simetría de Croquis 📐](#03-matrices-y-simetría-de-croquis-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Simetría de Entidades (Mirror Entities)](#1-simetría-de-entidades-mirror-entities)
    - [Parámetros Clave](#parámetros-clave)
    - [Cómo utilizarla](#cómo-utilizarla)
  - [2. Matriz Lineal de Croquis (Linear Sketch Pattern)](#2-matriz-lineal-de-croquis-linear-sketch-pattern)
    - [Parámetros Principales del PropertyManager (Linear Sketch Pattern)](#parámetros-principales-del-propertymanager-linear-sketch-pattern)
  - [3. Matriz Circular de Croquis (Circular Sketch Pattern)](#3-matriz-circular-de-croquis-circular-sketch-pattern)
    - [Parámetros Principales del PropertyManager (Circular Sketch Pattern)](#parámetros-principales-del-propertymanager-circular-sketch-pattern)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Brida Circular con Perforaciones Múltiples y Simetría](#5-ejemplo-práctico-brida-circular-con-perforaciones-múltiples-y-simetría)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Simetría de Entidades (Mirror Entities)

La herramienta **Simetría** refleja una o varias entidades de croquis al otro lado de una línea constructiva de referencia (eje de simetría).

### Parámetros Clave

- **Entidades para simetría:** Selección de las líneas, círculos o contornos que se desean reflejar.
- **Con respecto a (Mirror about):** La línea constructiva central que actúa como espejo.
- **Copiar (Copy):** Si está activada, mantiene el dibujo original y genera una copia reflejada; si se desactiva, traslada la geometría original al otro lado del eje.

### Cómo utilizarla

1. Dibuja una **línea constructiva (centerline)** que sirva como eje de simetría.
2. Selecciona la herramienta **Simetrizar entidades** en la barra de croquis.
3. Elige las entidades a reflejar y selecciona el eje de simetría. Haz clic en la paloma verde para aceptar.

---

## 2. Matriz Lineal de Croquis (Linear Sketch Pattern)

Permite duplicar entidades seleccionadas en una o dos direcciones rectilíneas (ejes $X$ e $Y$) de forma equidistante.

### Parámetros Principales del PropertyManager (Linear Sketch Pattern)

- **Eje X e Y (Dirección 1 y 2):** Define el espaciamiento lineal (`Spacing`) y el número total de instancias (`Instance Count`, $N$).
- **Ángulo:** Permite inclinar la dirección de la matriz lineal respecto a la horizontal.
- **Instancias para omitir (Instances to Skip):** Permite hacer clic sobre puntos de vista previos de la matriz para desactivar elementos individuales que no se requieran.

---

## 3. Matriz Circular de Croquis (Circular Sketch Pattern)

Duplica entidades alrededor de un punto central o vértice siguiendo una trayectoria radial o circular.

### Parámetros Principales del PropertyManager (Circular Sketch Pattern)

- **Punto de centro (Center):** El origen o arco de referencia sobre el cual rotará la matriz (por defecto se asigna un círculo base).
- **Ángulo total:** Define el rango de distribución (típicamente $360^\circ$ para ciclos completos o $180^\circ$ para medios giros).
- **Número de instancias ($N$):** Cantidad total de elementos repetidos uniformemente en el arco estipulado.
- **Igual separación (Equal spacing):** Distribuye automáticamente los elementos de forma proporcional en función del ángulo total.

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Usa siempre ejes constructivos:** Antes de aplicar simetrías o matrices complejas, asegúrate de trazar líneas de centro bien definidas y acotadas respecto al Origen.
2. **Prioriza matrices en croquis vs. operaciones 3D:** Si las repeticiones son perforaciones o perfiles planos sencillos, realizarlas en el croquis 2D suele ser más ligero; sin embargo, para cuerpos 3D complejos o grandes ensamblajes, se recomienda aplicar matrices a nivel de operaciones (*Feature Patterns*).
3. **Controla las cotas de patrón:** Al generar matrices lineales o circulares, SolidWorks asigna cotas automáticas de cantidad ($D1$, $D2$) y separación que puedes vincular mediante fórmulas si el diseño lo requiere.

---

## 5. Ejemplo Práctico: Brida Circular con Perforaciones Múltiples y Simetría

Vamos a modelar una brida o tapa de montaje que incluye un patrón circular de agujeros para pernos y una característica lateral simétrica.

### Paso a Paso

1. **Crear Líneas Constructivas de Referencia:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja una **Línea constructiva** horizontal y otra vertical que crucen exactamente por el **Origen (`0,0`)**. Estas serán tus ejes de simetría y centros de giro.

2. **Dibujar la Entidad Original:**
   - Dibuja un círculo pequeño (que simule un agujero para perno) ubicado en el cuadrante superior izquierdo respecto al origen. Acótalo en posición y diámetro.

3. **Aplicar Matriz Circular de Croquis:**
   - Selecciona la herramienta **Matriz circular de croquis** en la barra superior.
   - En el panel de propiedades, selecciona el **punto central** (puedes hacer clic en el origen o en el centro del círculo de referencia).
   - Define el número total de instancias (por ejemplo, **6 elementos**) y asegúrate de que el ángulo sea de **360°**.
   - En la casilla de entidades para repetir, selecciona el círculo pequeño que dibujaste en el paso 2. Verás una vista previa de los 6 agujeros distribuidos uniformemente. Haz clic en la paloma verde.

4. **Aplicar Simetría de Croquis (Mirror):**
   - Dibuja una pequeña ranura o muesca decorativa a la izquierda de tu pieza principal.
   - Selecciona la herramienta **Simetrizar entidades**.
   - En "Entidades para Simetrizar", selecciona los trazos de tu muesca.
   - En "Simetrizar respecto a", haz clic en la **línea constructiva vertical** del centro. Observa cómo aparece instantáneamente la copia exacta reflejada al lado derecho.

5. **Verificación:**
   - Comprueba que las cotas y las relaciones de las instancias principales controlen el comportamiento de toda la matriz (si cambias el diámetro del círculo original, los otros 5 se actualizarán automáticamente).
   - Asegúrate de que el croquis conserve un estado **Completamente definido**.

### Captura / Evidencia
<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica09.png" width="500" alt="Captura de pantalla de la práctica 09">

---

[Inicio](#03-matrices-y-simetría-de-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
