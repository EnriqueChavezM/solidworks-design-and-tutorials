# 03. Condiciones Finales en Operaciones 3D 🎯

En el diseño CAD paramétrico, las **Condiciones Finales** (*End Conditions*) definen el comportamiento de profundidades y límites para las operaciones de adición o sustracción de material (como *Extruir Saliente* y *Corte Extruido*). Seleccionar la condición adecuada garantiza que la intención de diseño se mantenga intacta ante cambios dimensionales futuros.

---

## 🎯 Objetivos del Módulo

- Entender la diferencia entre profundidades explícitas (fijas) y referencias geométricas dinámicas.
- Elegir la condición final óptima para asegurar la asociatividad paramétrica del modelo.
- Prevenir fallas de reconstrucción en el árbol de operaciones cuando cambien los espesores o posiciones de las caras.
  
---

## 📌 Tabla de Contenidos

- [03. Condiciones Finales en Operaciones 3D 🎯](#03-condiciones-finales-en-operaciones-3d-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [📌 Tabla de Contenidos](#-tabla-de-contenidos)
  - [1. Clasificación de las Condiciones Finales](#1-clasificación-de-las-condiciones-finales)
  - [2. Descripción Detallada por Tipo](#2-descripción-detallada-por-tipo)
    - [Hasta la profundidad especificada (*Blind*)](#hasta-la-profundidad-especificada-blind)
    - [Por todo (*Through All*)](#por-todo-through-all)
    - [Hasta el siguiente (*Up to Next*)](#hasta-el-siguiente-up-to-next)
    - [Hasta el vértice (*Up to Vertex*)](#hasta-el-vértice-up-to-vertex)
    - [Hasta la superficie (*Up to Surface*)](#hasta-la-superficie-up-to-surface)
    - [Equidistante de la superficie (*Offset from Surface*)](#equidistante-de-la-superficie-offset-from-surface)
    - [Hasta el cuerpo (*Up to Body*)](#hasta-el-cuerpo-up-to-body)
    - [Plano medio (*Mid Plane*)](#plano-medio-mid-plane)
  - [3. Opciones Paramétricas Relacionadas](#3-opciones-paramétricas-relacionadas)
  - [4. Criterios de Selección y Buenas Prácticas](#4-criterios-de-selección-y-buenas-prácticas)
  - [5. Ejemplo Práctico: Bloque de Alturas Variables con Múltiples Condiciones](#5-ejemplo-práctico-bloque-de-alturas-variables-con-múltiples-condiciones)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Clasificación de las Condiciones Finales

Las condiciones finales se dividen en dos categorías principales según cómo determinan la longitud del sólido o corte:

| Categoría | Descripción | Ejemplos |
| :--- | :--- | :--- |
| **Numéricas / Explícitas** | La profundidad se define mediante un valor escalar fijo (mm, pulg). | *Hasta la profundidad especificada (Blind)*, *Plano medio (Mid Plane)*. |
| **Geométricas / Dinámicas** | La profundidad se vincula a un elemento existente de la pieza (cara, vértice, superficie o plano). | *Por todo*, *Hasta la superficie*, *Hasta el siguiente*, *Equidistante de la superficie*. |

---

## 2. Descripción Detallada por Tipo

### Hasta la profundidad especificada (*Blind*)

- **Mecanismo:** Extiende la operación a una distancia exacta $D_1$ ingresada manualmente.
- **Uso recomendado:** Geometrías aisladas que no dependen de la posición de otras caras o salientes.

### Por todo (*Through All*)

- **Mecanismo:** Atraviesa todo el material disponible en la dirección seleccionada, sin importar la distancia.
- **Uso recomendado:** Barrenos pasantes o vaciados que siempre deban cruzar la pieza de extremo a extremo.

### Hasta el siguiente (*Up to Next*)

- **Mecanismo:** Se extiende únicamente hasta intersectar con la primera superficie o cara que encuentra en su trayectoria.
- **Uso recomendado:** Perforaciones en paredes de tubos o cavidades internas donde no se desea afectar la pared opuesta.

### Hasta el vértice (*Up to Vertex*)

- **Mecanismo:** Termina la operación en un plano imaginario que pasa por el vértice seleccionado y es paralelo al plano del croquis.
- **Uso recomendado:** Alineación precisa de alturas o longitudes respecto a esquinas de otras características.

### Hasta la superficie (*Up to Surface*)

- **Mecanismo:** Proyecta la operación hasta tocar la superficie o cara plana/curva seleccionada, adaptándose a su forma.
- **Uso recomendado:** Extrusiones que deben asentarse sobre cilindros, superficies orgánicas o caras inclinadas.

### Equidistante de la superficie (*Offset from Surface*)

- **Mecanismo:** Detiene la operación a una distancia o tolerancia especificada ($t$) antes o después de llegar a la cara elegida.
- **Uso recomendado:** Vaciados de geometría compleja que deben mantener un grosor de pared uniforme respecto al exterior.

### Hasta el cuerpo (*Up to Body*)

- **Mecanismo:** Detiene la extensión al hacer contacto con un sólido específico dentro de una pieza multicuerpo.
- **Uso recomendado:** Diseño de componentes independientes en un mismo entorno de trabajo (ej. insertos, refuerzos).

### Plano medio (*Mid Plane*)

- **Mecanismo:** Aplica la profundidad total dividida equitativamente ($D_1 / 2$) a ambos lados del plano donde reside el croquis.
- **Uso recomendado:** Primera extrusión base para piezas simétricas respecto al origen o plano de referencia.

---

## 3. Opciones Paramétricas Relacionadas

- **Invertir dirección:** Cambia el sentido vectorial de la condición final hacia el lado opuesto del croquis.
- **Dirección 2:** Permite asignar una condición final independiente para el lado posterior del croquis (por ejemplo, *Hasta la superficie* en Dirección 1 y *Blind* en Dirección 2).
- **Condiciones de origen (*Start Condition*):** Al igual que el final, la operación puede iniciar desde una superficie, un vértice o un desfase especificado en lugar del plano del croquis.

---

## 4. Criterios de Selección y Buenas Prácticas

1. **Regla de oro:** Minimiza el uso de *Hasta la profundidad especificada (Blind)* siempre que exista una referencia geométrica clara a la cual vincular la operación.
2. **Robusteza ante cambios:** Si cambias el grosor de un bloque de $20\text{ mm}$ a $35\text{ mm}$, un corte de $20\text{ mm}$ (*Blind*) quedará ciego e incompleto, mientras que un corte *Por todo* o *Hasta la superficie* se actualizará automáticamente sin errores.
3. **Simplificación del árbol:** Usar *Plano Medio* en la primera operación facilita el uso de los planos principales (Alzado, Planta, Vista lateral) para futuras simetrías y matrices sin necesidad de crear planos auxiliares.

---

## 5. Ejemplo Práctico: Bloque de Alturas Variables con Múltiples Condiciones

Vamos a ilustrar cómo usar distintas condiciones finales en un mismo modelo para entender su comportamiento paramétrico.

### Paso a Paso

1. **Crear el Bloque Base:**
   - Abre un croquis en el plano **Alzado**, dibuja un rectángulo de **120 mm x 80 mm** y lo extruimos usando la condición **Plano medio** a una profundidad de **40 mm**.

2. **Aplicar Extrusión con "Hasta el Siguiente":**
   - Imagina que quieres añadir una columna o soporte escalonado sobre una de las caras internas.
   - Abre un croquis en la cara superior del bloque, dibuja un círculo pequeño y selecciona **Extruir Corte**.
   - En lugar de poner una medida ciega, selecciona **Hasta el siguiente**. Observa cómo la columna crece exactamente hasta unirse con la estructura superior interna sin que tengas que calcular la distancia matemática.

3. **Aplicar Corte con "Por Todo":**
   - Abre un croquis en una de las paredes laterales del bloque, dibuja un círculo de **65 mm** de diámetro para simular un conducto o paso de perno.
   - Selecciona **Extruir Corte** y configura la condición final como **Por todo (Through All)**.
   - Confirma la operación. No importa si más adelante decides hacer el bloque más ancho; el agujero siempre lo atravesará por completo de lado a lado.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica12.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#03-condiciones-finales-en-operaciones-3d-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
