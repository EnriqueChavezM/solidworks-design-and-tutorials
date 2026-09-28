# 02. Curvas Guía y Hélices en CAD 🌀

Las **Hélices** y **Curvas Guía** son entidades auxiliares fundamentales para controlar el comportamiento, la torsión y la forma de operaciones tridimensionales complejas como *Barridos* y *Recubrimientos*. Permiten llevar el modelado más allá de trayectorias rectilíneas o planas convencionales.

---

## 🎯 Objetivos del Módulo

- **Generar trayectorias helicoidales y espirales:** Crear muelles, resortes, roscas personalizadas y brocas.
- **Controlar deformaciones 3D:** Utilizar curvas guía para deformar secciones transversales en barridos y recubrimientos.
- **Garantizar la continuidad geométrica:** Aplicar relaciones de perforar (*Pierce*) entre croquis para asegurar la estabilidad del modelo.

---

## Tabla de contenido

- [02. Curvas Guía y Hélices en CAD 🌀](#02-curvas-guía-y-hélices-en-cad-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Hélices y Espirales (Helix and Spiral)](#1-hélices-y-espirales-helix-and-spiral)
    - [Parámetros de Definición](#parámetros-de-definición)
      - [Variantes de Hélice](#variantes-de-hélice)
  - [2. Curvas Guía (Guide Curves)](#2-curvas-guía-guide-curves)
    - [Reglas de Aplicación](#reglas-de-aplicación)
  - [3. Relación de Perforar (Pierce Relation)](#3-relación-de-perforar-pierce-relation)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Modelado de un Resorte Helicoidal o Broca](#5-ejemplo-práctico-modelado-de-un-resorte-helicoidal-o-broca)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Hélices y Espirales (Helix and Spiral)

Una **Hélice** es una curva 3D generada a partir de un círculo base que sirve como diámetro de referencia.

### Parámetros de Definición

Las hélices se definen combinando dos de los siguientes tres parámetros, además del ángulo inicial:

1. **Paso de rosca (*P* / Pitch):** Distancia axial recorrida en una vuelta completa ($360^\circ$).
2. **Revoluciones (*N*):** Número total de vueltas de la hélice.
3. **Altura (*H*):** Longitud total axial de la hélice.

#### Variantes de Hélice

- **Paso constante:** El paso $P$ se mantiene uniforme a lo largo de toda la altura.
- **Paso variable:** Permite definir tablas donde el paso y el diámetro cambian progresivamente (útil para resortes de suspensión o amortiguadores).
- **Hélice cónica (*Taper Helix*):** Inclina la trayectoria generando un ángulo de salida cónico.
- **Espiral plana:** Genera un trazado 2D en forma de caracol contenido en un solo plano.

---

## 2. Curvas Guía (Guide Curves)

Las **Curvas Guía** son líneas o arcos 2D/3D que restringen y moldean cómo se expande, contrae o deforma el perfil a lo largo de la trayectoria.

### Reglas de Aplicación

- **Intersección obligatoria:** La curva guía debe tocar o intersectar físicamente el contorno de cada perfil involucrado en la operación.
- **Suavidad de curvatura:** Curvas guía con cambios bruscos de dirección o radios de curvatura excesivamente cerrados provocarán errores de auto-intersección en el sólido.
- **Múltiples curvas guía:** Se pueden agregar varias curvas guía (ej. superior, inferior y laterales) para un control de forma tridimensional completo.

---

## 3. Relación de Perforar (Pierce Relation)

La relación de **Perforar** es la restricción geométrica indispensable al trabajar con curvas 3D y croquis 2D.

- **Concepto:** Vincula un **punto** del croquis activo (ej. un vértice o punto de centro) con una **línea/curva fuera del plano** (ej. la hélice o curva guía), obligando al punto a permanecer enganchado a la curva en el lugar donde esta atraviesa el plano del croquis.
- **Diferencia con Coincidente:** *Coincidente* proyecta el punto sobre el plano; *Perforar* clava el punto directamente en la curva 3D.

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Usa siempre la relación *Perforar*:** Antes de ejecutar un barrido con hélice o curva guía, asegura que los puntos de control del perfil tengan una relación de perforar con la trayectoria.
2. **Controla el ángulo inicial de la hélice:** Ajusta el ángulo inicial a $0^\circ$, $90^\circ$, $180^\circ$ o $270^\circ$ para hacer coincidir el inicio de la hélice con uno de los planos principales (Alzado, Planta o Vista Lateral). Esto facilitará el trazado del perfil 2D sin necesidad de crear planos auxiliares.
3. **Monitorea el radio de curvatura:** Asegúrate de que el radio de la curva guía sea siempre mayor que la mitad del espesor del perfil para evitar colapsos en las esquinas internas.

---

## 5. Ejemplo Práctico: Modelado de un Resorte Helicoidal o Broca

Vamos a crear una hélice tridimensional que sirva como trayectoria para barrer un perfil circular, simulando un resorte de compresión.

### Paso a Paso

1. **Crear el Círculo Base para la Hélice:**
   - Abre un croquis en el plano **Planta** y dibuja un círculo con un diámetro específico (ej. **Ø 50 mm**). Cierra el croquis (este círculo define el radio de la hélice).

2. **Generar la Hélice (Trayectoria 3D):**
   - Ve al menú superior **Insertar > Curva > Hélice y espiral**.
   - Selecciona el círculo que acabas de dibujar.
   - En el panel de propiedades, configura los parámetros de la hélice:
     - *Definir por:* **Paso y revoluciones (Pitch and revolutions)**.
     - *Paso (Pitch):* **10 mm** (distancia vertical entre cada vuelta).
     - *Revoluciones (Revolutions):* **8 vueltas**.
     - *Ángulo inicial:* 0°.
   - Haz clic en la **paloma verde**. Observa cómo se ha generado una línea tridimensional en espiral.

3. **Crear el Perfil del Resorte:**
   - Crea un **Plano de referencia** utilizando como primer punto el inicio de la hélice y como referencia secundaria la línea de la hélice para asegurarte de que quede perfectamente perpendicular al inicio de la trayectoria.
   - Abre un croquis en ese plano nuevo y dibuja un círculo pequeño centrado exactamente en el punto de inicio de la hélice (ej. **Ø 5 mm** para simular el alambre del resorte). Cierra el croquis.

4. **Ejecutar el Saliente por Barrido con la Hélice:**
   - Ve a **Operaciones > Saliente/Base barrido**.
   - Selecciona el círculo pequeño como **Perfil** y la hélice 3D como **Trayectoria**.
   - Haz clic en la **paloma verde** para confirmar. Se habrá modelado un resorte tridimensional completo.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica19.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#02-curvas-guía-y-hélices-en-cad-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
