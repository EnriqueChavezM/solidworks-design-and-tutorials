# 02. Recortes y Extremos de Tubo en CAD ✂️

En el diseño de estructuras soldadas, las intersecciones entre perfiles no siempre se resuelven de forma limpia de manera automática. La herramienta **Recortar/Extender (Trim/Extend)** y la colocación de **Tapas en Extremo (End Caps)** son fundamentales para ajustar la geometría de los tubos en los nodos de unión y sellar las cavidades abiertas para prevenir la corrosión o la entrada de suciedad.

---

## 🎯 Objetivos del Módulo

- **Resolver intersecciones complejas:** Ajustar la longitud de los perfiles para evitar colisiones volumétricas en los nodos de la estructura.
- **Definir tipos de esquinas:** Manejar esquinas a inglete, a tope y penetraciones de tubo sobre caras planas o curvas.
- **Sellar cavidades de tubos:** Aplicar tapas de extremo paramétricas respetando holguras para cordones de soldadura.

---

## Tabla de contenido

- [02. Recortes y Extremos de Tubo en CAD ✂️](#02-recortes-y-extremos-de-tubo-en-cad-️)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Operación Recortar/Extender (Trim/Extend)](#1-operación-recortarextender-trimextend)
    - [Tipos de Recorte](#tipos-de-recorte)
  - [2. Límites de Recorte (Trimming Boundaries)](#2-límites-de-recorte-trimming-boundaries)
  - [3. Tapas en Extremo (End Caps)](#3-tapas-en-extremo-end-caps)
    - [Parámetros Principales](#parámetros-principales)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Ajustando las Esquinas de un Bastidor Metálico](#5-ejemplo-práctico-ajustando-las-esquinas-de-un-bastidor-metálico)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Operación Recortar/Extender (Trim/Extend)

La herramienta **Recortar/Extender** permite modificar la longitud de uno o varios miembros estructurales utilizando otros cuerpos sólidos o caras planas como límites de corte.

### Tipos de Recorte

Al seleccionar los cuerpos a recortar (*Bodies to be trimmed*), se debe especificar la prioridad y el tipo de esquina:

- **Extremo a inglete (*End Miter*):** Recorta los dos miembros adyacentes en un ángulo bisectriz (por ejemplo, $45^\circ$ para una esquina de $90^\circ$).
- **Extremo a tope 1 (*End Butt 1*):** El primer miembro seleccionado se recorta contra la cara exterior del segundo miembro.
- **Extremo a tope 2 (*End Butt 2*):** Invierte la prioridad del corte entre los dos miembros seleccionados.

---

## 2. Límites de Recorte (Trimming Boundaries)

El recorte de un perfil se puede ejecutar utilizando dos tipos de referencias:

| Tipo de Límite | Descripción | Caso de Uso |
| :--- | :--- | :--- |
| **Cuerpos (*Bodies*)** | Utiliza la geometría 3D completa de otro perfil como matriz de corte. | Intersección de tubos cilíndricos o perfiles en T y K. |
| **Caras / Planos (*Faces/Planes*)** | Utiliza un plano de referencia o la cara plana de un sólido para hacer un corte limpio. | Extremos de bastidores que deben asentarse sobre placas base o el suelo. |

> **Permitir extensión:** Si esta opción está activa, la herramienta extenderá el perfil hasta alcanzar el límite seleccionado si este no llega físicamente a tocarlo.

---

## 3. Tapas en Extremo (End Caps)

La operación **Tapa en Extremo** permite cerrar la abertura de un perfil hueco (tubo cuadrado, rectangular o cilíndrico) mediante una platina metálica de espesor uniforme.

### Parámetros Principales

- **Cara plana de referencia:** Selección de la cara abierta del tubo donde se aplicará la tapa.
- **Dirección del espesor:**
  - *Hacia afuera:* Extiende la tapa por fuera del tubo (aumenta la longitud total de la pieza).
  - *Hacia adentro:* Hunde la tapa dentro de la cavidad del tubo.
- **Relación de desfase (Offset):**
  - *Grosor de la pared:* Alinea la tapa con la arista exterior del tubo.
  - *Desfase numérico:* Reduce el tamaño de la tapa respecto al borde exterior para dejar una bisel de preparación para el cordón de soldadura.
- **Tratamiento de esquinas:** Permite añadir redondeos o chaflanes a las esquinas exteriores de la tapa.

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Recorta antes de aplicar cartelas o soldadura:** El orden correcto en el árbol de operaciones exige resolver todos los recortes de miembros estructurales **antes** de añadir cartelas de refuerzo (*Gussets*) o cordones de soldadura.
2. **Deja holguras para soldadura en las tapas:** Utiliza un desfase negativo en la tapa de extremo (ej. $-1\text{ mm}$ a $-2\text{ mm}$) para crear un bisel o escalón que facilite la deposición del cordón de soldadura a ras.
3. **Revisa la lista de cortes:** Tras recortar o extender perfiles, asegúrate de actualizar la *Lista de Cortes* para verificar que los ángulos de corte en los extremos ($Angle1, Angle2$) y las longitudes finales se hayan registrado correctamente para la fabricación.

---

## 5. Ejemplo Práctico: Ajustando las Esquinas de un Bastidor Metálico

Vamos a tomar un marco rectangular básico hecho con perfiles tubulares donde las esquinas se superponen, y aplicaremos los recortes necesarios para dejarlos listos para soldar.

### Paso a Paso

1. **Generar el Bastidor Base:**
   - Asegúrate de tener un croquis estructural rectangular y aplica la herramienta *Miembro estructural* con un tubo cuadrado (ej. **40x40x4 mm**) en todos sus lados. Al hacerlo por defecto, notarás que algunos perfiles se atraviesan o se superponen en las esquinas.

2. **Acceder a la Herramienta Recortar/Extender:**
   - Ve a la pestaña **Piezas soldadas (Weldments)** en la barra superior.
   - Haz clic en la herramienta **Recortar/Extender**.

3. **Configurar los Parámetros de Corte:**
   - **Cuerpos para recortar (Bodies to be trimmed):** Selecciona los perfiles verticales o horizontales que necesitan ser cortados.
   - **Tipo de recorte:** Selecciona la opción de **Corte a inglete (Mitre cut)** si es una esquina de 90 grados, o **Corte a tope** seleccionando la cara del perfil que servirá como límite.
   - **Distancia de soldadura (Weld gap):** (Opcional) Introduce un valor pequeño (ej. **1 mm**) si deseas dejar una holgura técnica entre los tubos para la penetración del arco de soldadura.

4. **Confirmar la Operación:**
   - Haz clic en la **paloma verde (Aceptar)**. Observa cómo los extremos de los perfiles se adaptan de forma limpia y automática, eliminando las colisiones internas y preparando la unión para el taller.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica25.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#02-recortes-y-extremos-de-tubo-en-cad-️)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
