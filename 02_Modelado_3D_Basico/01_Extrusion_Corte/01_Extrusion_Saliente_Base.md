# 01. Extrusión Saliente/Base en CAD 📦

La operación **Extruir Saliente/Base** (*Extruded Boss/Base*) es la técnica fundamental del modelado 3D paramétrico. Consiste en proyectar un perfil o croquis 2D perpendicularmente a su plano para generar un cuerpo sólido tridimensional.

---

## 🎯 Objetivos del Módulo

- Comprender la transformación geométrica de perfiles 2D a volúmenes 3D.
- Dominar el uso de direcciones y condiciones finales de profundidad.
- Generar sólidos con ángulos de salida (*Draft*) y espesores delgados (*Thin Feature*).

---

## Tabla de Contenidos

- [01. Extrusión Saliente/Base en CAD 📦](#01-extrusión-salientebase-en-cad-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de Contenidos](#tabla-de-contenidos)
  - [1. Requisitos del Croquis 2D](#1-requisitos-del-croquis-2d)
  - [2. Parámetros Principales de la Operación](#2-parámetros-principales-de-la-operación)
  - [3. Condiciones Finales (End Conditions)](#3-condiciones-finales-end-conditions)
  - [4. Opciones Avanzadas de Extrusión](#4-opciones-avanzadas-de-extrusión)
    - [Ángulo de Salida (*Draft*)](#ángulo-de-salida-draft)
    - [Operación Lámina (*Thin Feature*)](#operación-lámina-thin-feature)
  - [5. Buenas Prácticas](#5-buenas-prácticas)
  - [6. Ejemplo Práctico: Creación del Bloque Base de una Carcasa](#6-ejemplo-práctico-creación-del-bloque-base-de-una-carcasa)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Requisitos del Croquis 2D

Para ejecutar una extrusión limpia y sin errores topológicos, el croquis previo debe cumplir con ciertas reglas:

- **Perfil cerrado:** No deben existir puntos abiertos ni segmentos desconectados.
- **Sin auto-intersecciones:** Las líneas del perfil no deben cruzarse entre sí (formar figuras en "8").
- **Completamente definido:** Se recomienda definir todas las cotas y relaciones geométricas antes de aplicar la operación 3D.

| Tipo de Croquis | Validez para Extrusión | Resultado |
| :--- | :--- | :--- |
| **Perfil Único Cerrado** | ✅ Válido | Sólido único compacto |
| **Perfiles Anidados** | ✅ Válido | Sólido con huecos/vacíos internos |
| **Perfil Abierto** | ⚠️ Requiere *Operación Lámina / Thin Feature* | Sólido de pared delgada |
| **Perfil Cruzado** | ❌ Error de geometría | La operación falla |

---

## 2. Parámetros Principales de la Operación

Al activar la herramienta **Extruir Saliente/Base**, se configuran los siguientes parámetros en el gestor de propiedades:

1. **Desde (Start Condition):** Especifica el punto de origen de la extrusión (*Plano de croquis*, *Superficie/Cara/Plano*, *Vértice* o *Equidistancia*).
2. **Dirección 1 / Dirección 2:** Permite extruir volumen hacia uno o ambos lados del croquis de forma simétrica o independiente.
3. **Profundidad ($D_1$):** Valor numérico de la distancia a extruir (mm, in).

---

## 3. Condiciones Finales (End Conditions)

Las condiciones finales permiten definir la longitud de la extrusión según referencias geométricas dinámicas:

- **Hasta la profundidad especificada (*Blind*):** Extruye a una distancia exacta fija.
- **Plano medio (*Mid Plane*):** Extruye dividiendo la distancia equitativamente a ambos lados del plano del croquis.
- **Hasta la superficie (*Up to Surface*):** Extiende el sólido hasta adaptarse a una cara curva o plana existente.
- **Hasta el siguiente (*Up to Next*):** Termina la extrusión en la primera superficie que encuentra en su trayectoria.
- **Hasta el cuerpo (*Up to Body*):** Utilizado en modelado multicuerpo para detener la extrusión al tocar otro sólido.

---

## 4. Opciones Avanzadas de Extrusión

### Ángulo de Salida (*Draft*)

Permite aplicar una inclinación cónica o piramidal a las caras extruidas durante la creación del sólido.

- **Uso principal:** Diseño de piezas para moldeo por inyección de plástico o fundición que requieren desmolde.

### Operación Lámina (*Thin Feature*)

Crea una pared de espesor constante a partir de un perfil abierto o cerrado.

- **Parámetros:** Espesor de pared ($t$) y dirección del espesor (Hacia adentro, Hacia afuera o Plano medio).

---

## 5. Buenas Prácticas

1. **Regla de oro:** Siempre que la pieza sea simétrica respecto al origen, utiliza la condición Plano Medio en la primera extrusión base. Esto facilitará enormemente el uso de planos de simetría y ensamblajes posteriores.
2. **Nombres claros:** Renombra la operación en el árbol de diseño (ej. Extrusión_Base_Principal).
3. **Un solo cuerpo base:** Evita crear cuerpos desconectados en la primera operación a menos que estés trabajando explícitamente en diseño multicuerpo.

---

## 6. Ejemplo Práctico: Creación del Bloque Base de una Carcasa

Vamos a transformar uno de nuestros croquis rectangulares previos en un sólido tridimensional con una profundidad específica.

### Paso a Paso

1. **Partir de un Croquis Cerrado:**
   - Abre tu pieza anterior o crea un nuevo croquis en el plano **Alzado** con un **Rectángulo de centro** de **100 mm x 60 mm**. Asegúrate de que el croquis esté completamente definido (en color negro).

2. **Acceder a la Operación 3D:**
   - Ve a la pestaña **Operaciones (Features)** en la barra de comandos superior.
   - Haz clic en la herramienta **Extruir saliente/base**.

3. **Configurar los Parámetros en el Panel Izquierdo:**
   - En la condición final (*From / Direction 1*), selecciona **Hasta profundidad especifica**.
   - Asigna una profundidad de **30 mm** en la casilla de medida.
   - (Opcional) Activa la casilla de *Plano medio* si deseas que el bloque crezca simétricamente hacia adelante y hacia atrás respecto al plano del croquis.

4. **Confirmar la Operación:**
   - Haz clic en la **paloma verde (Aceptar)** para generar el sólido.
   - Observa cómo tu croquis 2D se ha convertido en un bloque 3D y cómo ha aparecido la operación `Extruir1` en el **Árbol de Diseño (FeatureManager)** de la izquierda.

5. **Verificación:**
   - Utiliza el ratón (clic central presionado) para rotar la vista en 3D y comprobar que el volumen se generó correctamente.

### Captura / Evidencia
<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica10.png" width="500" alt="Captura de pantalla de la práctica 10">

---

[Inicio](#01-extrusión-salientebase-en-cad-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
