# 02. Corte Extruido en CAD ✂️

La operación **Corte Extruido** (*Extruded Cut*) es la herramienta fundamental de modelado sustractivo en sistemas CAD paramétricos. A diferencia de la extrusión saliente (que añade material), el corte extruido elimina volumen de un sólido existente proyectando un perfil o croquis 2D a lo largo de una trayectoria lineal.

---

## 🎯 Objetivos del Módulo

- Entender el concepto de diseño sustractivo para la creación de agujeros, vacíos, ranuras y rebajes.
- Seleccionar adecuadamente la condición final de corte para asegurar la intencionalidad del diseño paramétrico.
- Utilizar técnicas avanzadas como la inversión del lado de corte y el control del alcance en piezas multicuerpo.

---

## 📌 Tabla de Contenidos

- [02. Corte Extruido en CAD ✂️](#02-corte-extruido-en-cad-️)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [📌 Tabla de Contenidos](#-tabla-de-contenidos)
  - [1. Requisitos del Croquis 2D](#1-requisitos-del-croquis-2d)
  - [2. Condiciones Finales de Corte](#2-condiciones-finales-de-corte)
  - [3. Opciones Especiales y Avanzadas](#3-opciones-especiales-y-avanzadas)
    - [Invertir Lado a Cortar (*Flip Side to Cut*)](#invertir-lado-a-cortar-flip-side-to-cut)
    - [Ángulo de Salida (*Draft*)](#ángulo-de-salida-draft)
    - [Corte Normal (*Normal Cut*)](#corte-normal-normal-cut)
  - [4. Alcance de la Operación (Feature Scope)](#4-alcance-de-la-operación-feature-scope)
  - [5. Buenas Prácticas](#5-buenas-prácticas)
  - [2. Ejemplo Práctico: Vaciado Central o Perforación Pasante en el Bloque](#2-ejemplo-práctico-vaciado-central-o-perforación-pasante-en-el-bloque)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Requisitos del Croquis 2D

Para ejecutar un corte extruido correctamente, el croquis debe trazarse en una cara plana de un sólido existente o en un plano de referencia:

- **Perfil Cerrado:** Define el área exacta que se extraerá del sólido.
- **Múltiples Contornos:** Se pueden seleccionar varios contornos cerrados dentro del mismo croquis para realizar perforaciones simultáneas.
- **Perfiles Abiertos:** Permite realizar un corte de lado a lado en una pieza utilizando la geometría del perfil para dividir la masa sobrante.

---

## 2. Condiciones Finales de Corte

Elegir la condición final correcta garantiza que la pieza se comporte de manera paramétrica ante cambios futuros de dimensiones:

| Condición Final | Descripción | Caso de Uso Recomendado |
| :--- | :--- | :--- |
| **Hasta la profundidad especificada (*Blind*)** | Remueve material hasta una distancia fija dada ($D_1$). | Cajas, alojamientos para rodamientos o agujeros ciegos. |
| **Por todo (*Through All*)** | Atraviesa todo el sólido desde el origen del croquis en adelante. | Perforaciones pasantes estándar (pasos de pernos, cables). |
| **Por todo - Ambos (*Through All - Both*)** | Corta en ambas direcciones atravesando todo el material disponible. | Pasadores centrales o barrenos cuando el croquis está en un plano medio. |
| **Hasta el siguiente (*Up to Next*)** | Detiene el corte al encontrar la primera cara o superficie del sólido. | Agujeros en paredes contiguas sin afectar el resto de la pieza. |
| **Hasta la superficie (*Up to Surface*)** | Extiende el corte hasta tocar una cara plana o curva seleccionada. | Vaciados que deben terminar exactamente en un plano interno. |
| **Equidistante de la superficie (*Offset from Surface*)** | Detiene el corte a una distancia fija antes de llegar a la cara elegida. | Vaciados con espesores de pared inferior constantes. |

---

## 3. Opciones Especiales y Avanzadas

### Invertir Lado a Cortar (*Flip Side to Cut*)

Por defecto, la herramienta elimina el material que se encuentra **dentro** del perfil del croquis. Si se activa esta opción, se removerá todo el volumen **exterior** al contorno, conservando únicamente el núcleo interno.

### Ángulo de Salida (*Draft*)

Aplica una conicidad al corte conforme profundiza en el material. Es fundamental para diseñar cavidades en moldes de inyección o matrices de forja donde se requiere extracción.

### Corte Normal (*Normal Cut*)

Útil principalmente cuando se trabaja con superficies o piezas de chapa metálica (*Sheet Metal*), asegurando que las caras resultantes del corte permanezcan perpendiculares al plano de la chapa.

---

## 4. Alcance de la Operación (Feature Scope)

En modelos que contienen más de un cuerpo sólido (*Multicuerpo / Multi-body*), es necesario definir qué cuerpos responderán al corte:

- **Todos los cuerpos:** El corte afectará a cualquier sólido que se cruce en su trayectoria.
- **Cuerpos seleccionados:** Permite especificar mediante una lista explícita qué piezas se verán afectadas, ignorando las demás aunque estén en el paso del corte.

---

## 5. Buenas Prácticas

1. **Regla de oro:** Para taladros o perforaciones que siempre deban atravesar completamente la pieza, utiliza siempre **Por todo (*Through All*)** en lugar de una distancia especificada (*Blind*). Si el grosor de la pieza aumenta en el futuro, el corte seguirá siendo pasante automáticamente.
2. **Reutilización de planos:** Evita crear planos innecesarios si puedes iniciar el croquis de corte directamente sobre una cara existente de la pieza.
3. **Uso del asistente para taladros:** Si el corte corresponde a un barreno estandarizado para tornillería o roscado, es preferible utilizar la herramienta *Asistente para Taladro* (*Hole Wizard*) en lugar de un *Corte Extruido* convencional.

---

## 2. Ejemplo Práctico: Vaciado Central o Perforación Pasante en el Bloque

Vamos a tomar el bloque rectangular que modelamos en la práctica anterior (de 100 mm x 60 mm x 30 mm de alto) y le realizaremos una cavidad rectangular rebajada o un agujero pasante en el centro.

### Paso a Paso

1. **Seleccionar la Cara de Trabajo:**
   - Haz clic sobre la **cara superior** de tu bloque 3D para seleccionarla.
   - Haz clic en el ícono de **Croquis (Sketch)** en la barra flotante para abrir un nuevo croquis directamente sobre esa superficie plana.

2. **Dibujar la Geometría del Corte:**
   - Presiona la barra espaciadora y selecciona la vista **Normal a (Normal to)** para orientar la pantalla de frente hacia ti.
   - Selecciona la herramienta **Rectángulo de centro** y dibuja un rectángulo más pequeño en el centro (por ejemplo, de **60 mm x 30 mm**), acotándolo adecuadamente respecto a los bordes o vinculándolo con el origen.

3. **Acceder a la Operación de Corte:**
   - Ve a la pestaña **Operaciones (Features)** en la barra de comandos superior.
   - Haz clic en la herramienta **Extruir Corte**.

4. **Configurar los Parámetros del Corte:**
   - En el panel de propiedades de la izquierda, cambia la condición final a **Hasta la profundidad especificada (Blind)**.
   - Asigna una profundidad de **10 mm** (para generar una caja o rebaje interno sin atravesar toda la pieza). *Nota: Si quisieras un agujero totalmente pasante, podrías seleccionar "Por todo".*
   - Observa la vista previa en 3D: la flecha debe apuntar hacia el interior del material sólido (hacia abajo). Si apunta hacia afuera, usa el botón de invertir dirección.

5. **Confirmar la Operación:**
   - Haz clic en la **paloma verde (Aceptar)**.
   - Gira la pieza con el botón central del ratón para comprobar que se ha esculpido la cavidad interior correctamente.
   - Revisa el **Árbol de Diseño (FeatureManager)**: verás que debajo de `Extruir1` ahora aparece una nueva operación llamada `Cortar-Extruir1`.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica11.png" width="500" alt="Captura de pantalla de la práctica 11">

---

[Inicio](#02-corte-extruido-en-cad-️)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
