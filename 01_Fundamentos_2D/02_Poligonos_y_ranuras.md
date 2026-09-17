# 02. Polígonos y Ranuras en Croquis 📐

En esta sección se documenta el uso de herramientas geométricas avanzadas del entorno de croquis 2D en SolidWorks, enfocadas en la creación eficiente de polígonos regulares y alojamientos mecánicos (ranuras).

---

## 🎯 Objetivos del Módulo

- **Dominar polígonos regulares:** Aprender a trazar y parametrizar hexágonos, octágonos y otras figuras simétricas.
- **Crear ranuras mecánicas:** Utilizar distintos tipos de ranuras (*slots*) para alojamientos de pernos, pasadores o guías de desplazamiento.
- **Controlar restricciones paramétricas:** Aplicar relaciones de tangencia, simetría y cotas angulares o radiales.

---

## Tabla de Contenido

1. [Polígonos Regulares (Polygon)](#1-polígonos-regulares-polygon)
    1. [Tipos de Construcción de Polígonos](#tipos-de-construcción-de-polígonos)
    2. [Parámetros Clave](#parámetros-clave)
2. [Ranuras (Slots)](#2-ranuras-slots)
    1. [Ranura Recta de Centro a Centro (Straight Slot)](#1-ranura-recta-de-centro-a-centro-straight-slot)
    2. [Ranura Recta por Puntos (Point-to-Point Slot)](#2-ranura-recta-por-puntos-point-to-point-slot)
    3. [Ranura en Arco de Centro (Centerpoint Arc Slot)](#3-ranura-en-arco-de-centro-centerpoint-arc-slot)
    4. [Ranura en Arco de 3 Puntos (3-Point Arc Slot)](#4-ranura-en-arco-de-3-puntos-3-point-arc-slot)
3. [Buenas Prácticas al Trabajar con Polígonos y Ranuras](#3-buenas-prácticas-al-trabajar-con-polígonos-y-ranuras)
4. [Ejemplo Práctico: Placa con Ranura de Ajuste y Alojamiento Hexagonal](#4-ejemplo-práctico-placa-con-ranura-de-ajuste-y-alojamiento-hexagonal)

---

## 1. Polígonos Regulares (Polygon)

La herramienta de polígonos permite crear formas geométricas con un número de lados definido (desde 3 hasta 99) de forma perfectamente simétrica.

### Tipos de Construcción de Polígonos

1. **Círculo Inscrito:** El polígono se dibuja *dentro* de un círculo imaginario de referencia (los lados son tangentes al círculo interior).
2. **Círculo Circunscrito:** El polígono se dibuja *alrededor* de un círculo imaginario (los vértices tocan el círculo exterior).

### Parámetros Clave

- **Número de lados:** Puedes ajustarlo en el PropertyManager (ej. `6` para un hexágono, útil para cabezas de tornillos o tuercas).
- **Orientación:** Controlada mediante una relación horizontal o vertical en uno de sus lados o vértices.

---

## 2. Ranuras (Slots)

Las ranuras son entidades muy comunes en diseño mecánico para alojar pernos con juego de movimiento o guías de ensamblaje. SolidWorks ofrece 4 tipos principales:

### 1. Ranura Recta de Centro a Centro (Straight Slot)

Se define especificando los dos centros de los arcos extremos y luego el ancho (radio).

- **Uso ideal:** Correderas lineales y guías de desplazamiento simétricas.

### 2. Ranura Recta por Puntos (Point-to-Point Slot)

Se define mediante un punto inicial, un punto final y el ancho.

### 3. Ranura en Arco de Centro (Centerpoint Arc Slot)

Se traza a partir de un centro común, un radio y un ángulo de apertura en arco.

- **Uso ideal:** Mecanismos de ajuste circular, palancas o guías radiales.

### 4. Ranura en Arco de 3 Puntos (3-Point Arc Slot)

Se define mediante dos puntos extremos del arco y un punto intermedio sobre la curvatura.

---

## 3. Buenas Prácticas al Trabajar con Polígonos y Ranuras

1. **Alineación de vértices o lados:** Usa relaciones geométricas de *Horizontal* o *Vertical* en los lados planos de un hexágono para asegurar que quede orientado correctamente respecto a los ejes principales de la pieza.
2. **Acotación inteligente de ranuras:** Acota siempre la distancia entre centros (longitud útil) y el radio o diámetro total de la ranura, evitando sobredefinir las curvas de los extremos.
3. **Uso de simetría:** Si las ranuras son repetitivas (por ejemplo, ranuras de ventilación o de fijación), traza una y utiliza la herramienta de *Matriz lineal de croquis* (`Linear Sketch Pattern`) o *Simetría* (`Mirror Entities`).

---

## 4. Ejemplo Práctico: Placa con Ranura de Ajuste y Alojamiento Hexagonal

Vamos a modelar una placa de soporte de **120 mm x 50 mm** que incluye una **ranura central** para ajuste deslizante y un **hexágono** en un extremo (simulando un alojamiento para tuerca).

### Paso a Paso

1. **Crear el Contorno Base:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja un **Rectángulo de centro** desde el origen (`0,0`) y acótalo a **120 mm de largo** por **50 mm de alto**.

2. **Añadir el Polígono (Hexágono):**
   - Selecciona la herramienta **Polígono**.
   - En el panel de propiedades izquierdo, asegúrate de configurar el número de lados en **6** (Hexágono).
   - Coloca el centro del polígono en la parte izquierda de la placa (por ejemplo, alineado horizontalmente con el origen).
   - Usa la **Cota inteligente** para definir el diámetro del círculo de construcción a **25 mm** y usa una relación horizontal para alinear uno de sus vértices o caras.

3. **Añadir la Ranura (Slot):**
   - Selecciona la herramienta **Ranura recta de centro a centro**.
   - Dibuja la ranura en la mitad derecha de la placa, asegurándote de que su eje longitudinal sea horizontal.
   - Acota la distancia entre los dos centros de los arcos a **30 mm**.
   - Acota el radio de la ranura a **10 mm**.
   - Utiliza cotas adicionales desde el origen para posicionar la ranura exactamente a la distancia deseada (por ejemplo, a 30 mm hacia la derecha del centro).

4. **Verificación:**
   - Agrega relaciones geométricas de **horizontalidad** o **verticalidad** entre los centros de las figuras y el origen para asegurar que el croquis no se mueva de manera imprevista.
   - Revisa que todas las entidades pasen de color azul a **negro (Completamente definido)**.

### Captura / Evidencia

<img src="/01_Fundamentos_2D/Practicas/Practica02.png" width="500">

---

[Inicio](#02-polígonos-y-ranuras-en-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
