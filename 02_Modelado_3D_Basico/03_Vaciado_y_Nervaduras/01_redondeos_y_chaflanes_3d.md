# 01. Redondeos y Chaflanes 3D en CAD 📐

En esta sección se documentan las herramientas de acabado de aristas Redondeo (Fillet) y Chaflán (Chamfer). Estas operaciones permiten modificar vértices y bordes tridimensionales para mejorar la estética, eliminar concentradores de esfuerzo mecánico y facilitar los procesos de manufactura.

---

## 🎯 Objetivos del Módulo

- **Suavizar transiciones tridimensionales:** Aplicar radios continuos en aristas vivas para reducir concentraciones de tensión.
- **Preparar geometrías para manufactura:** Diseñar bordes biselados que faciliten el ensamble y el desmolde.
- **Mantener la intención de diseño:** Comprender el orden de operaciones dentro del árbol de diseño para evitar fallas de reconstrucción.

---

## Tabla de contenido

- [01. Redondeos y Chaflanes 3D en CAD 📐](#01-redondeos-y-chaflanes-3d-en-cad-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Redondeos 3D (Fillet)](#1-redondeos-3d-fillet)
    - [Tipos de Redondeo](#tipos-de-redondeo)
  - [2. Chaflanes 3D (Chamfer)](#2-chaflanes-3d-chamfer)
    - [Métodos de Definición](#métodos-de-definición)
  - [3. Opciones Avanzadas y Propagación](#3-opciones-avanzadas-y-propagación)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Aplicación de Redondeos y Chaflanes a una Carcasa o Bloque](#5-ejemplo-práctico-aplicación-de-redondeos-y-chaflanes-a-una-carcasa-o-bloque)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Redondeos 3D (Fillet)

La herramienta Redondeo sustituye una arista viva por una superficie curva de radio especificado.

### Tipos de Redondeo

1. **Tamaño constante:** Aplica un radio uniforme ($R$) a lo largo de todas las aristas seleccionadas.
2. **Tamaño variable:** Permite asignar valores de radio distintos en los diferentes puntos finales o nodos a lo largo de una misma arista.
3. **Redondeo de cara:** Crea un radio tangente entre dos caras no adyacentes o no conectadas directamente.
4. **Redondeo completo (Full Round):** Genera una cara completamente curva continua utilizando tres caras contiguas como referencia.

---

## 2. Chaflanes 3D (Chamfer)

La herramienta Chaflán bisela una arista viva cortando el borde en un ángulo determinado.

### Métodos de Definición

1. **Ángulo-Distancia:** Especifica una distancia de corte y un ángulo de inclinación (por ejemplo, $2\text{ mm} \times 45^\circ$).
2. **Distancia-Distancia:** Permite establecer distancias de corte independientes ($D_1 \neq D_2$) para biseles asimétricos o iguales ($D_1 = D_2$).
3. **Vértice (Chaflán de esquina):** Aplica un corte triaxial sobre una esquina donde convergen tres aristas sólidas.

---

## 3. Opciones Avanzadas y Propagación

1. **Propagación tangente (Tangency Propagation):** Si está activa, el redondeo o chaflán se extenderá automáticamente a lo largo de todas las aristas conectadas que mantengan continuidad tangencial.
2. **Opciones de esquina (Corner Options):** Permite controlar la convergencia de múltiples redondeos en una sola esquina mediante arreglos planos o de suavizado esférico.
3. **Mantenimiento de características:** Controla cómo se comportan los cortes o salientes cercanos al intersectar con la zona biselada o redondeada.

## 4. Buenas Prácticas y Criterios de Diseño

1. **Aplica redondeos y chaflanes al final:** Coloca estas operaciones al final del árbol de diseño 3D. Aplicarlas al inicio puede complicar el trazado de croquis secundarios sobre caras que hayan perdido sus bordes rectos.
2. **Orden jerárquico de radios:** Aplica primero los redondeos de mayor radio y posteriormente los redondeos de menor radio o detalles secundarios.
3. **Optimización de manufactura:** Utiliza chaflanes en los extremos de ejes y barrenos para facilitar la entrada de pernos y rodamientos durante el ensamble.

---

## 5. Ejemplo Práctico: Aplicación de Redondeos y Chaflanes a una Carcasa o Bloque

Vamos a tomar nuestro bloque rectangular base y refinar sus aristas exteriores e interiores utilizando estas operaciones de manufactura.

### Paso a Paso

1. **Partir de un Croquis Cerrado:**
   - Abre tu pieza anterior o crea un nuevo croquis en el plano **Alzado** con un **Rectángulo de centro** de **100 mm x 100 mm**. Asegúrate de que el croquis esté completamente definido (en color negro).
   - Ve a la pestaña **Operaciones (Features)** en la barra de comandos superior.
   - Haz clic en la herramienta **Extruir saliente/base**.
   - Asigna una profundidad de **100 mm** en la casilla de medida.

2. **Abrir la Herramienta de Redondeo (Fillet):**
   - Ve a la pestaña **Operaciones (Features)** en la barra superior.
   - Haz clic en la herramienta **Redondeo**.
   - En el panel de propiedades izquierdo, selecciona el tipo *Radio constante* y define un valor de radio (por ejemplo, **R = 5 mm**).

3. **Seleccionar las Aristas a Redondear:**
   - Haz clic sobre las **aristas verticales exteriores** del bloque 3D. Verás una vista previa en color amarillo de cómo se curvan las esquinas.
   - (Opcional) Puedes seleccionar caras completas para redondear todas las aristas adyacentes de un solo clic.
   - Haz clic en la **paloma verde (Aceptar)** para confirmar la operación.

4. **Aplicar Chaflán (Chamfer):**
   - Haz clic en la flecha debajo de la herramienta Redondeo y selecciona **Chaflán**.
   - En el panel de propiedades, selecciona la opción **Distancia - Distancia** (o Distancia-Ángulo) e introduce un valor de **5 mm**.
   - Haz clic sobre las **aristas horizontales exteriores** del bloque 3D. Verás una vista previa en color amarillo de cómo se curvan las esquinas.
   - (Opcional) Puedes seleccionar caras completas para redondear todas las aristas adyacentes de un solo clic.
   - Haz clic en la **paloma verde** para generar el bisel.

5. **Verificación en el Árbol de Diseño:**
   - Revisa tu *FeatureManager*: verás que se han añadido las operaciones `Redondeo1` y `Chaflán1` de forma secuencial al final de tu historial de modelado.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica15.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#01-redondeos-y-chaflanes-3d-en-cad-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
