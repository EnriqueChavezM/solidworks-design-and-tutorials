# Práctica 01: Líneas, Círculos y Rectángulos

En esta sección se documenta el uso de las herramientas geométricas básicas en el **Croquis 2D** de SOLIDWORKS, fundamentales para iniciar cualquier modelo paramétrico.

---

## 1. Resumen de Herramientas

* **Línea:** Permite trazar segmentos rectos continuos. Podemos alternar entre líneas constructivas (líneas de centro) y líneas de croquis normales.
* **Círculo:** Herramienta para crear circunferencias definiendo primero el centro y luego el radio/diámetro. Ideal para perforaciones y ejes.
* **Rectángulo:** Permite crear figuras de cuatro lados de forma rápida. Destacan variantes como:
  * *Rectángulo de esquina* (desde un vértice opuesto a otro).
  * *Rectángulo de centro* (expandiéndose simétricamente desde el origen o centro).

---

## 2. Ejemplo Práctico: Placa de Montaje Básica

Vamos a modelar una placa rectangular de **100 mm x 60 mm** con un agujero pasante centrado de **20 mm** de diámetro.

### Paso a Paso

1. **Iniciar el Croquis:**
   * Abre una nueva pieza en SOLIDWORKS.
   * Selecciona el plano **Alzado (Front Plane)** y haz clic en la herramienta **Croquis** (Sketch).

2. **Dibujar el Rectángulo:**
   * Selecciona la herramienta **Rectángulo de centro** (Center Rectangle).
   * Haz clic exactamente en el **Origen (0,0)** para que el croquis quede completamente centrado y vinculado al sistema de coordenadas.
   * Arrastra el cursor y haz clic sin importar las medidas exactas por ahora.

3. **Añadir el Círculo:**
   * Selecciona la herramienta **Círculo**.
   * Coloca el centro haciendo clic en el origen (aprovechando que el punto medio ya está definido).
   * Extiende el radio y haz clic.

4. **Acotación Inteligente (Smart Dimension):**
   * Selecciona **Cota inteligente** en la barra de herramientas superior.
   * Haz clic en la línea horizontal superior del rectángulo y asígnale una medida de **100 mm**.
   * Haz clic en la línea vertical lateral y asígnale **60 mm**.
   * Haz clic en el borde del círculo y asígnale un diámetro de **20 mm**.

5. **Verificación:**
   * Al terminar, todas las líneas del croquis deben cambiar de color **azul a negro**, lo que indica que el croquis está **Completamente Definido (Fully Defined)**.

---

## 3. Captura / Evidencia

<img src="/01_Fundamentos_2D/Practicas/Practica01.png" width="500">

---

## 4. Tips y Buenas Prácticas Aprendidas

* **Vincular al Origen:** Siempre es una buena práctica iniciar el primer elemento geométrico desde el origen del plano (`0,0`) para evitar que el croquis flote libremente por el espacio de trabajo.
* **Completamente Defino:** Nunca dejes un croquis en azul (subdefinido) para piezas formales; utiliza cotas o relaciones geométricas (horizontal, vertical, coincidente) hasta que todo quede en negro.

---

**[Regresar al Documento](/01_Fundamentos_2D/01_lineas_circulos_y_rectangulos.md)**

---
