# 02. Cotas Inteligentes en SolidWorks 📐

En esta sección se documenta el uso de la herramienta de **Cota Inteligente** (*Smart Dimension*) y los principios fundamentales para acotar correctamente un croquis en SolidWorks, asegurando un diseño paramétrico robusto y completamente definido.

---

## 🎯 Objetivos del Módulo

- **Dominar la cota inteligente:** Comprender cómo una sola herramienta se adapta al tipo de entidad seleccionada (líneas, arcos, círculos o ángulos).
- **Evitar la sobrecotización:** Aprender qué dimensiones son estrictamente necesarias para definir un modelo sin duplicar información.
- **Mantener la intención de diseño:** Asegurar que las cotas reflejen la función de ingeniería de la pieza.

---

## Tabla de contenido

- [02. Cotas Inteligentes en SolidWorks 📐](#02-cotas-inteligentes-en-solidworks-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Tipos de Acotación con Cota Inteligente](#1-tipos-de-acotación-con-cota-inteligente)
    - [1. Cotas Lineales](#1-cotas-lineales)
    - [2. Cotas Radiales y Diametrales](#2-cotas-radiales-y-diametrales)
    - [3. Cotas Angulares](#3-cotas-angulares)
  - [2. Modificación y Propiedades de las Cotas](#2-modificación-y-propiedades-de-las-cotas)
  - [3. Buenas Prácticas de Acotación en CAD](#3-buenas-prácticas-de-acotación-en-cad)
  - [4. Ejemplo Práctico: Placa Ranurada con Acotación Funcional](#4-ejemplo-práctico-placa-ranurada-con-acotación-funcional)
    - [Paso a Paso](#paso-a-paso)
  - [Captura / Evidencia](#captura--evidencia)

---

## 1. Tipos de Acotación con Cota Inteligente

Al activar la herramienta de **Cota Inteligente**, SolidWorks detecta automáticamente la geometría seleccionada y muestra el tipo de dimensión correspondiente:

### 1. Cotas Lineales

- **Entre dos puntos o vértices:** Mide la distancia horizontal, vertical o en línea recta entre ambos puntos.
- **De una línea completa:** Seleccionando una arista o línea recta se obtiene su longitud total.
- **Distancia entre paralelas:** Seleccionando dos líneas paralelas se define la separación entre ellas.

### 2. Cotas Radiales y Diametrales

- **Diámetro ($\varnothing$):** Se aplica seleccionando el contorno completo de un círculo o arco completo. El sistema añade automáticamente el símbolo de diámetro.
- **Radio ($R$):** Se aplica seleccionando arcos parciales o empalmes (*fillets*).

### 3. Cotas Angulares

- Seleccionando dos líneas que se cruzan o convergen (o una línea y una arista de referencia), se define el ángulo exacto de apertura en grados ($^\circ$).

---

## 2. Modificación y Propiedades de las Cotas

Cuando haces clic en una cota para colocarla o la seleccionas posteriormente, se abre el panel de propiedades (**Modify / PropertyManager**):

- **Nombre de la cota (Name):** Permite cambiar el identificador interno de la variable (por ejemplo, cambiar `@D1` por `Largo_Placa`), lo cual es útil si trabajas con ecuaciones o configuraciones paramétricas.
- **Unidades y Tolerancias:** Puedes asignar tolerancias simétricas, límites, ajustes de precisión decimal o cambiar las unidades específicas de esa cota de forma independiente si fuera necesario.

---

## 3. Buenas Prácticas de Acotación en CAD

1. **No sobredefinas el croquis:** Si añades una cota numérica a una entidad que ya está completamente restringida por relaciones geométricas previas, SolidWorks te advertirá que el croquis está **sobredefinido** (las cotas se mostrarán en color gris/alerta o rojo). Elige siempre dejar la cota como *conductora* o eliminarla si es redundante.
2. **Acota desde líneas base o simetrías:** Intenta acotar siempre a partir del **Origen** o de ejes de simetría principales. Esto evita que los errores de dimensión se acumulen en cadena a lo largo de piezas complejas.
3. **Mantén las cotas fuera de la geometría:** Coloca las cotas de manera limpia y ordenada fuera de los contornos de la pieza para facilitar la lectura del plano o del boceto en el árbol de operaciones.

---

## 4. Ejemplo Práctico: Placa Ranurada con Acotación Funcional

Vamos a modelar una placa de montaje rectangular que requiere múltiples tipos de acotación (lineal, diametral, radial y angular) manteniendo una correcta jerarquía de diseño.

### Paso a Paso

1. **Configurar el Sistema de Unidades:**
   - Mira en la barra de estado inferior derecha de SOLIDWORKS y asegúrate de que esté configurado en **MMGS** (Milímetros, gramos, segundos).

2. **Crear la Geometría Base:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja un rectángulo y añade un par de círculos o ranuras en su interior (puedes basarte en prácticas anteriores).

3. **Aplicar Cotas Lineales (Distancias y Longitudes):**
   - Selecciona la herramienta **Cota Inteligente**.
   - Haz clic en la línea inferior del rectángulo y luego en la línea superior para definir la altura total (ejemplo: **80 mm**).
   - Haz clic en la arista izquierda y luego en la arista derecha para definir el ancho total (ejemplo: **140 mm**).

4. **Aplicar Cotas de Posición:**
   - Para ubicar una perforación interna, haz clic en el **centro del círculo** y luego en la arista de referencia lateral para definir su distancia exacta en el eje X (ejemplo: **25 mm desde el borde**).
   - Repite el proceso seleccionando el centro del círculo y la arista inferior para definir su posición en el eje Y.

5. **Aplicar Cotas Radiales y Diametrales:**
   - Haz clic en el contorno de un círculo exterior; SOLIDWORKS detectará automáticamente que es una circunferencia y te permitirá colocar la cota de **Diámetro (Ø)**.
   - Si tienes un arco o un redondeo(fillet), haz clic sobre él para colocar la cota de **Radio (R)**.

6. **Verificación del Croquis:**
   - Revisa que todas las entidades clave tengan sus cotas necesarias y que el croquis esté **Completamente Definido (Fully Defined)** en color negro, sin cotas sobredefinidas (en rojo o amarillo, lo cual indicaría un conflicto).

---

## Captura / Evidencia

<img src="/06_retos_y_proyectos/01_Practicas/Practica05.png" width="500">

---

[Inicio](#02-cotas-inteligentes-en-solidworks-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)


[def]: #1-tipos-de-acotación-con-cota-inteligente