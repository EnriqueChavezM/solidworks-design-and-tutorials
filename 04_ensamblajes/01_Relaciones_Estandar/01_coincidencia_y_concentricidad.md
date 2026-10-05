# 01. Coincidencia y Concentricidad en Ensamblajes 🧩

Las **Relaciones de Posición Estándar** (*Standard Mates*) son las restricciones geométricas fundamentales empleadas para conectar piezas independientes dentro de un entorno de ensamblaje 3D, eliminando grados de libertad ($DoF$) mecánicos.

---

## 🎯 Objetivos del Módulo

- **Restringir grados de libertad:** Posicionar componentes en el espacio mediante referencias geométricas de caras, ejes y vértices.
- **Alinear piezas cilíndricas y planas:** Dominar el uso de concentricidad y coincidencia para el montaje de pernos, bujes y ejes.
- **Prevenir sobre-restricciones:** Evitar conflictos entre relaciones redundantes en el árbol de ensamblaje.

---

## Tabla de contenido

- [01. Coincidencia y Concentricidad en Ensamblajes 🧩](#01-coincidencia-y-concentricidad-en-ensamblajes-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Coincidencia (Coincident Mate)](#1-coincidencia-coincident-mate)
  - [2. Concentricidad (Concentric Mate)](#2-concentricidad-concentric-mate)
  - [3. Alineación y Bloqueo de Rotación](#3-alineación-y-bloqueo-de-rotación)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Ensamblando un Eje en un Soporte Cilíndrico](#5-ejemplo-práctico-ensamblando-un-eje-en-un-soporte-cilíndrico)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Coincidencia (Coincident Mate)

La relación de **Coincidencia** fuerza a dos entidades geométricas (caras planas, aristas, vértices o planos de referencia) a compartir el mismo plano o posición en el espacio.

- **Entre caras planas:** Elimina 1 grado de libertad de traslación y 2 grados de libertad de rotación.
- **Entre línea/arista y cara:** Obliga a la línea a yacer sobre el plano proyectado de la cara.
- **Entre vértices:** Alinea dos puntos en una ubicación única ($X, Y, Z$).

---

## 2. Concentricidad (Concentric Mate)

La relación de **Concentricidad** fuerza a dos caras cilíndricas, cónicas, arcos o ejes a compartir una misma línea central o eje de simetría.

- **Aplicación en barrenos y pernos:** Alinea el eje del perno con el eje del orificio manteniendo libre la rotación axial y el desplazamiento a lo largo del eje.
- **Bloquear rotación (*Lock Rotation*):** Opción integrada en las relaciones concéntricas que impide que la pieza gire sobre su propio eje sin necesidad de agregar una relación extra de plano.

---

## 3. Alineación y Bloqueo de Rotación

Al aplicar una relación de posición, se puede invertir la orientación geométrica del componente mediante las opciones de alineación:

| Alineación | Descripción |
| :--- | :--- |
| **Alineado (*Aligned*)** | Los vectores normales de las caras seleccionadas apuntan en la misma dirección. |
| **Alineación opuesta (*Anti-Aligned*)** | Los vectores normales de las caras apuntan en sentido contrario (caras enfrentadas). |

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Fija el componente base:** El primer componente insertado en el ensamblaje debe fijarse en el origen ($0,0,0$) de las coordenadas globales para actuar como ancla rígida.
2. **Relaciona con planos principales:** En lugar de relacionar caras externas que puedan cambiar o ser modificadas por operaciones como redondeos, aplica coincidencia entre los **Planos Principales** (Alzado, Planta, Vista Lateral) de las piezas.
3. **SmartMates (Relaciones inteligentes):** Presiona la tecla `ALT` mientras arrastras una arista circular para aplicar simultáneamente concentricidad y coincidencia de cara en una sola acción.

---

## 5. Ejemplo Práctico: Ensamblando un Eje en un Soporte Cilíndrico

Vamos a conectar un eje cilíndrico *(Practica27-A)* dentro del barreno de un soporte base *(Practica27-B)* utilizando las relaciones estándar fundamentales.

### Paso a Paso

1. **Abrir el Entorno de Ensamblaje e Insertar Componentes:**
   - Crea un nuevo archivo de **Ensamblaje (.sldasm)** en SOLIDWORKS.
   - Haz clic en **Insertar componentes** y selecciona el archivo del soporte base. *Nota de diseño:* El primer componente que insertes se fijará automáticamente en el origen del ensamblaje (verás una letra `(f)` al lado de su nombre en el árbol).
   - Vuelve a hacer clic en *Insertar componentes* y selecciona la pieza del eje cilíndrico.

2. **Aplicar Relación de Concentricidad:**
   - Haz clic en la herramienta **Relación de posición (Mate)** en la barra superior.
   - Selecciona la **cara cilíndrica exterior** del eje y luego haz clic sobre la **cara cilíndrica interior** del barreno del soporte.
   - SOLIDWORKS detectará automáticamente la relación lógica y aplicará *Concentricidad*. Observa la vista previa: el eje ahora está alineado al centro del orificio, aunque todavía se desliza libremente hacia adentro y hacia afuera.
   - Haz clic en la marca de verificación parcial o acepta el mate.

3. **Aplicar Relación de Coincidencia (Tope Axial):**
   - Selecciona la **cara plana inferior** (el hombro o base) del eje.
   - Selecciona la **cara plana superior** de la placa de soporte.
   - En el panel de propiedades, asegúrate de que la relación activa sea **Coincidente**.
   - Haz clic en la **paloma verde (Aceptar)** para confirmar. El eje ahora se ha posicionado perfectamente al tope de la placa.

4. **Verificación de Grados de Libertad:**
   - Intenta arrastrar el eje con el botón izquierdo del ratón. Notarás que ya no se traslada en los ejes $X$ o $Y$, pero **gira libremente** sobre su propio eje central, simulando el comportamiento físico real de un perno o flecha ajustada.

### Captura / Evidencia

- **Archivos**
  - [Eje Cilíndrico](/06_retos_y_proyectos/01_Practicas/Practica27-B.SLDPRT)
  - [Placa Base](/06_retos_y_proyectos/01_Practicas/Practica27-B.SLDPRT)
  - [Ensamble](/06_retos_y_proyectos/01_Practicas/Practica27_Ensamblaje.SLDASM)
  
<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica27.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#01-coincidencia-y-concentricidad-en-ensamblajes-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
