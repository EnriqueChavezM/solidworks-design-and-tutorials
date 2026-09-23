# 03. Intención de Diseño en Croquis 📐

En esta sección se documenta el concepto de **Intención de Diseño** (*Design Intent*), uno de los pilares fundamentales en el modelado paramétrico con SolidWorks. Comprender este concepto te permite construir modelos inteligentes que responden de manera predecible y controlada cuando se modifican sus dimensiones.

---

## 🎯 Objetivos del Módulo

- **Comprender el modelado paramétrico:** Aprender a diseñar pensando en *cómo* y *por qué* se moverá o cambiará la pieza en el futuro.
- **Aprovechar las simetrías y orígenes:** Utilizar el sistema de coordenadas (`0,0`) como eje central de control.
- **Evitar fallos en el árbol de operaciones:** Prevenir que el modelo colapse o rompa relaciones geométricas al actualizar cotas o modificar piezas ensambladas.

---

## Tabla de contenido

- [03. Intención de Diseño en Croquis 📐](#03-intención-de-diseño-en-croquis-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. ¿Qué es la Intención de Diseño?](#1-qué-es-la-intención-de-diseño)
  - [2. Estrategias Clave para una Buena Intención de Diseño](#2-estrategias-clave-para-una-buena-intención-de-diseño)
    - [1. Anclar siempre el modelo al Origen](#1-anclar-siempre-el-modelo-al-origen)
    - [2. Priorizar Relaciones sobre Cotas Excesivas](#2-priorizar-relaciones-sobre-cotas-excesivas)
    - [3. Diseñar de lo General a lo Particular](#3-diseñar-de-lo-general-a-lo-particular)
  - [3. Errores Comunes que Rompen la Intención de Diseño](#3-errores-comunes-que-rompen-la-intención-de-diseño)
  - [4. Ejemplo Práctico: Placa de Montaje Paramétrica](#4-ejemplo-práctico-placa-de-montaje-paramétrica)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. ¿Qué es la Intención de Diseño?

La **intención de diseño** es la estrategia que implementas al crear un croquis o una pieza para definir cómo debe comportarse ante futuras modificaciones.

Por ejemplo, si diseñas una placa metálica con un agujero céntrico:

- **Diseño sin intención (Incorrecto):** Dibujar el agujero en cualquier parte de la placa y acotarlo midiendo solo desde la esquina izquierda y la esquina inferior. Si la placa cambia de tamaño, el agujero se desplazará de forma imprecisa.
- **Diseño con intención (Correcto):** Hacer que el centro del agujero coincida exactamente con el centro geométrico de la placa o utilizar relaciones de simetría respecto al **Origen**. Si la placa se expande, el agujero mantendrá su posición centrada de manera automática.

---

## 2. Estrategias Clave para una Buena Intención de Diseño

### 1. Anclar siempre el modelo al Origen

El **Origen del Sistema de Coordenadas `(0,0)`** es el punto fijo del espacio 3D.

- **Regla de oro:** Al menos un elemento principal de tu croquis (el centro de un círculo simétrico, la intersección de ejes o una esquina clave) debe estar vinculado directamente al Origen mediante relaciones de *Coincidente* o *Punto Medio*. Esto evita que el croquis flote libremente o se desplace por error.

### 2. Priorizar Relaciones sobre Cotas Excesivas

En lugar de saturar tu croquis con cotas numéricas para alinear elementos, utiliza restricciones geométricas:

- Usa **Simetría** si dos elementos deben reaccionar de forma idéntica a ambos lados de un eje.
- Usa **Igualdad** si múltiples perforaciones o contornos comparten las mismas dimensiones.
- Usa **Paralelismo** o **Colinealidad** para mantener alineaciones estructurales.

### 3. Diseñar de lo General a lo Particular

- Comienza trazando la **geometría envolvente o contorno principal** de la pieza.
- Añade las operaciones secundarias (como nervios, vaciados, chaflanes y pequeños agujeros) en las etapas posteriores del modelado.

---

## 3. Errores Comunes que Rompen la Intención de Diseño

1. **Acotar desde geometrías temporales:** Evita basar cotas críticas en aristas que podrían eliminarse o modificarse drásticamente en operaciones futuras (como redondeos o cortes avanzados).
2. **Dejar grados de libertad ocultos:** Si un croquis tiene líneas en color azul, significa que carece de la intención de diseño suficiente y puede deformarse de manera no deseada al editar parámetros.
3. **Abusar de la herramienta "Fijo" (Fixed):** Restringir elementos con la relación *Fijo* desactiva la lógica paramétrica del software; utilízala únicamente de forma estrictamente temporal o en perfiles importados estáticos.

---

## 4. Ejemplo Práctico: Placa de Montaje Paramétrica

Imagina que te piden diseñar un soporte que pueda fabricarse en tres tamaños diferentes (pequeño, mediano y grande) cambiando una sola cota.

### Paso a Paso

1. **Anclaje al Origen:**
   - Abre un croquis en el plano **Alzado** y dibuja un rectángulo de centro **directamente sobre el origen**. Esto asegura que la pieza crezca simétricamente hacia todos los lados al modificar sus cotas.

2. **Geometría Relacionada:**
   - Coloca dos agujeros en los extremos. En lugar de medir cada uno por separado desde los bordes, selecciona ambos centros y añade una relación de **Horizontalidad** respecto al origen, y una relación de **Igualdad** entre sus diámetros de **25 mm**.

3. **Prueba de Esfuerzo (Cambio de Parámetros):**
   - Cambia la cota de largo total de **100 mm** y un angulo de **125°** entre sus lineas de construcción.
   - *Resultado esperado:* Gracias a la intención de diseño basada en la simetría desde el origen, la placa se expande uniformemente de ambos lados y los agujeros conservan su posición relativa sin desalinearse.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica06.png" width="500" alt="Captura de pantalla de la práctica 06">

---

[Inicio](#03-intención-de-diseño-en-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
