# 02. Polígonos y Ranuras en Croquis 📐

En esta sección se documenta el uso de herramientas geométricas avanzadas del entorno de croquis 2D en SolidWorks, enfocadas en la creación eficiente de polígonos regulares y alojamientos mecánicos (ranuras).

---

## 🎯 Objetivos del Módulo

- **Dominar polígonos regulares:** Aprender a trazar y parametrizar hexágonos, octágonos y otras figuras simétricas.
- **Crear ranuras mecánicas:** Utilizar distintos tipos de ranuras (*slots*) para alojamientos de pernos, pasadores o guías de desplazamiento.
- **Controlar restricciones paramétricas:** Aplicar relaciones de tangencia, simetría y cotas angulares o radiales.

---

## Tabla de Contenido

1. [Polígonos Regulares (Polygon)](#-1-polígonos-regulares-polygon)
    1. [Tipos de Construcción de Polígonos](#-tipos-de-construcción-de-polígonos)
    2. [Parámetros Clave](#️-parámetros-clave)
2. [Ranuras (Slots)](#-2-ranuras-slots)
    1. [Ranura Recta de Centro a Centro (Straight Slot)](#-1-ranura-recta-de-centro-a-centro-straight-slot)
    2. [Ranura Recta por Puntos (Point-to-Point Slot)](#-2-ranura-recta-por-puntos-point-to-point-slot)
    3. [Ranura en Arco de Centro (Centerpoint Arc Slot)](#-3-ranura-en-arco-de-centro-centerpoint-arc-slot)
    4. [Ranura en Arco de 3 Puntos (3-Point Arc Slot)](#-4-ranura-en-arco-de-3-puntos-3-point-arc-slot)
3. [Buenas Prácticas al Trabajar con Polígonos y Ranuras](#️-3-buenas-prácticas-al-trabajar-con-polígonos-y-ranuras)
4. [Archivos de Práctica Relacionados](#-4-archivos-de-práctica-relacionados)

---

## ⬡ 1. Polígonos Regulares (Polygon)

La herramienta de polígonos permite crear formas geométricas con un número de lados definido (desde 3 hasta 99) de forma perfectamente simétrica.

### 🔹 Tipos de Construcción de Polígonos

1. **Círculo Inscrito:** El polígono se dibuja *dentro* de un círculo imaginario de referencia (los lados son tangentes al círculo interior).
2. **Círculo Circunscrito:** El polígono se dibuja *alrededor* de un círculo imaginario (los vértices tocan el círculo exterior).

### ⚙️ Parámetros Clave

- **Número de lados:** Puedes ajustarlo en el PropertyManager (ej. `6` para un hexágono, útil para cabezas de tornillos o tuercas).
- **Orientación:** Controlada mediante una relación horizontal o vertical en uno de sus lados o vértices.

---

## 💊 2. Ranuras (Slots)

Las ranuras son entidades muy comunes en diseño mecánico para alojar pernos con juego de movimiento o guías de ensamblaje. SolidWorks ofrece 4 tipos principales:

### 🔹 1. Ranura Recta de Centro a Centro (Straight Slot)

Se define especificando los dos centros de los arcos extremos y luego el ancho (radio).

- **Uso ideal:** Correderas lineales y guías de desplazamiento simétricas.

### 🔹 2. Ranura Recta por Puntos (Point-to-Point Slot)

Se define mediante un punto inicial, un punto final y el ancho.

### 🔹 3. Ranura en Arco de Centro (Centerpoint Arc Slot)

Se traza a partir de un centro común, un radio y un ángulo de apertura en arco.

- **Uso ideal:** Mecanismos de ajuste circular, palancas o guías radiales.

### 🔹 4. Ranura en Arco de 3 Puntos (3-Point Arc Slot)

Se define mediante dos puntos extremos del arco y un punto intermedio sobre la curvatura.

---

## 🛠️ 3. Buenas Prácticas al Trabajar con Polígonos y Ranuras

1. **Alineación de vértices o lados:** Usa relaciones geométricas de *Horizontal* o *Vertical* en los lados planos de un hexágono para asegurar que quede orientado correctamente respecto a los ejes principales de la pieza.
2. **Acotación inteligente de ranuras:** Acota siempre la distancia entre centros (longitud útil) y el radio o diámetro total de la ranura, evitando sobredefinir las curvas de los extremos.
3. **Uso de simetría:** Si las ranuras son repetitivas (por ejemplo, ranuras de ventilación o de fijación), traza una y utiliza la herramienta de *Matriz lineal de croquis* (`Linear Sketch Pattern`) o *Simetría* (`Mirror Entities`).

---

## 📄 4. Archivos de Práctica Relacionados

[Practica 2](/01_Fundamentos_2D/Practicas/Practica02.md)

---

[Inicio](#02-polígonos-y-ranuras-en-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
