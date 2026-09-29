# 02. Pliegues y Despliegue en Chapa Metálica 📐

En esta sección se documenta el manejo de operaciones de deformación plástica, cortes en zonas dobladas y desarrollo plano en el módulo de Chapa Metálica (Sheet Metal). El control entre el estado plegado y el desplegado es esencial para garantizar la manufacturabilidad y la generación de archivos de fabricación (DXF/DWG) para corte por láser o punzonado.

---

## 🎯 Objetivos del Módulo

- **Crear dobleces a partir de líneas 2D:** Utilizar croquis simples para definir líneas de doblado sobre caras planas existentes
- **Realizar operaciones en estado desplegado:** Aplicar cortes, barrenos o troquelados a través de zonas de pliegue sin distorsionar la geometría 3D.
- **Gestionar el patrón plano (Flat Pattern):** Exportar planos de desarrollo precisos con líneas de centro de pliegue y ángulos de doblado.

---

## Tabla de contenido

- [02. Pliegues y Despliegue en Chapa Metálica 📐](#02-pliegues-y-despliegue-en-chapa-metálica-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Pliegue Croquizado (Sketched Bend)](#1-pliegue-croquizado-sketched-bend)
  - [2. Desdoblar y Doblar Temporal (Unfold / Fold)](#2-desdoblar-y-doblar-temporal-unfold--fold)
  - [3. Patrón Plano / Desarrollo (Flat Pattern)](#3-patrón-plano--desarrollo-flat-pattern)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Realizando un Corte Transversal sobre Pliegues Abiertos](#5-ejemplo-práctico-realizando-un-corte-transversal-sobre-pliegues-abiertos)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Pliegue Croquizado (Sketched Bend)

La herramienta **Pliegue Croquizado** permite añadir un dobles a una chapa existente trazando una única línea recta sobre una cara plana.

- **Parámetros Principales del PropertyManager**
  - **Cara fija (Fixed Face):** Define qué lado de la pieza permanecerá inmóvil durante la operación de doblado.
  - **Línea de pliegue:** La línea de croquis trazada que marca la posición exacta del eje de doblado.
  - **Posición del pliegue:** Determina cómo se ubica el radio de dobles respecto a la línea trazada (Línea central del pliegue, Material en el interior, Material en el exterior o Pliegue en el exterior).
  - **Ángulo de pliegue:** Especifica el ángulo de inclinación del dobles (ej. $90^\circ$, $45^\circ$).

---

## 2. Desdoblar y Doblar Temporal (Unfold / Fold)

Cuando se requiere realizar cortes, ranuras o troquelados que atraviesan una zona de dobles, no se debe cortar sobre la superficie curva en 3D. Se utiliza la pareja de herramientas **Desdoblar (Unfold)** y **Doblar (Fold)**.

- **Flujo de Trabajo para Cortes en Pliegues**
  1. **Desdoblar (Unfold):** Selecciona una cara fija y los pliegues específicos que deseas aplanar temporalmente.
  2. **Operación de Corte:** Crea un croquis en la zona aplanada y ejecuta un Corte Extruido.
  3. **Doblar (Fold):** Vuelve a aplicar los pliegues seleccionados para regresar la pieza a su estado tridimensional con el corte perfectamente adaptado.

---

## 3. Patrón Plano / Desarrollo (Flat Pattern)

El **Patrón Plano** es la última operación del árbol de diseño en piezas de chapa metálica. Mantiene desactivado por defecto el desarrollo plano y se activa para inspeccionar o exportar la lámina extendida.

- **Propiedades y Estado de Despliegue**
    1. **Líneas de pliegue (Bend Lines):** Muestra las líneas de centro del dobles con anotaciones automáticas de dirección (UP/DOWN), ángulo y radio.
    2. **Cálculo de tolerancia de pliegue:** Utiliza el Factor K o las tablas de doblado asignadas para calcular la longitud desplegada exacta ($L_{flat}$).
    3. **Exportación a DXF/DWG:** Permite enviar el contorno y las líneas de pliegue directamente a software de manufactura CNC para corte por láser o plasma.

---

## 4. Buenas Prácticas y Criterios de Diseño

1. Usa siempre Desdoblar/Doblar para perforaciones en esquinas: Evita hacer cortes directos sobre caras cilíndricas de pliegues; aplanar la zona primero garantiza que el desarrollo plano no tenga deformaciones en la matriz de corte.
2. Líneas de pliegue continuas: Asegúrate de que las líneas trazadas para un Pliegue Croquizado crucen completamente la cara plana de extremo a extremo.
3. Verificación de interferencias en Patrón Plano: Activa temporalmente la herramienta de Patrón Plano para confirmar que no existan traslapes de material (overlapping) en las esquinas cuando la pieza se desarrolle.

---

## 5. Ejemplo Práctico: Realizando un Corte Transversal sobre Pliegues Abiertos

Imagina que necesitas perforar un agujero o hacer un corte que atraviesa exactamente una línea de doblez. Si intentas hacerlo con la pieza doblada, la geometría se distorsionará al aplanarla. Veamos el flujo de trabajo correcto:

### Paso a Paso

1. **Partir de una Pieza Doblada:**
   - Utiliza la escuadra o canaleta de chapa metálica que modelaste en la práctica anterior (con al menos un doblez a 90°).

2. **Aplicar la Operación Desplegar (Unfold):**
   - Ve a la pestaña **Chapa metálica** en la barra superior.
   - Haz clic en la herramienta **Desplegar (Unfold)**.
   - En el panel de propiedades, configura los siguientes campos:
     - *Cara fija (Fixed Face):* Haz clic en la cara inferior plana de tu escuadra. Esta será la zona de referencia que no se moverá.
     - *Pliegues a desplegar (Pliegues a desdoblar):* Haz clic en la pestaña de pliegue o selecciona la opción "Recopilar todos los pliegues" (*Collect all bends*).
   - Haz clic en la **paloma verde (Aceptar)**. Observa cómo la esquina doblada se endereza instantáneamente, mostrando la lámina completamente plana en esa sección.

3. **Realizar el Corte sobre la Lámina Abierta:**
   - Abre un croquis directamente sobre la superficie que acabas de desplegar.
   - Dibuja un círculo o ranura que cruce la zona donde antes estaba el doblez.
   - Aplica un **Corte extruido** con la condición *Por todo* para perforar la lámina. (Si miras la vista previa, el corte se hace de forma limpia sobre el metal plano).

4. **Volver a Doblar (Fold):**
   - Ve a la pestaña **Chapa metálica** y haz clic en la herramienta **Doblar (Fold)**.
   - Selecciona la misma cara fija inferior y utiliza la opción de recopilar todos los pliegues.
   - Haz clic en la **paloma verde**. Observa cómo la pieza recupera su forma tridimensional doblada y el agujero que acabas de hacer ahora se extiende de manera perfecta a través de la esquina plegada.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica22.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#02-pliegues-y-despliegue-en-chapa-metálica-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
