# 01. Líneas, Círculos y Rectángulos en Croquis 📐

En esta sección se documentan las herramientas geométricas fundamentales de SolidWorks para el trazado de entidades primarias dentro del entorno de croquis 2D.

---

## 🎯 Objetivos del Módulo

- **Dominar el entorno de croquis:** Comprender el uso correcto de entidades básicas de dibujo.
- **Optimizar la intención de diseño:** Construir geometrías simétricas y centradas usando el origen como referencia.
- **Evitar geometrías redundantes:** Conocer las variantes de rectángulos, círculos y líneas según las necesidades de la pieza.

---

## Tabla de Contenido

1. [Entidades de Línea (Line)](#1-entidades-de-línea-line)
   1. [Línea Constructiva (Centerline)](#línea-constructiva-centerline)
   2. [Línea Normal (Sólida)](#línea-normal-sólida)
2. [Círculos y Arcos](#2-círculos-y-arcos)
   1. [Círculo por Centro (Center Circle)](#círculo-por-centro-center-circle)
   2. [Círculo Perimetral (Perimeter Circle)](#círculo-perimetral-perimeter-circle)
3. [Tipos de Rectángulos](#3-tipos-de-rectángulos)
   1. [Rectángulo de Centro (Center Rectangle)](#rectángulo-de-centro-center-rectangle)
   2. [Rectángulo de Esquina (Corner Rectangle)](#rectángulo-de-esquina-corner-rectangle)
4. [Buenas Prácticas en el Croquis](#4-buenas-prácticas-en-el-croquis)
5. [Ejemplo Práctico: Placa de Montaje Básica](#5-ejemplo-práctico-placa-de-montaje-básica)

---

## 1. Entidades de Línea (Line)

La línea es la entidad base para construir contornos abiertos o cerrados. En SolidWorks se clasifica principalmente en:

### Línea Constructiva (Centerline)

Se utiliza como eje de simetría o referencia geométrica. **No interviene en las operaciones de extrusión 3D**.

- **Cómo usarla:** Selecciona la herramienta Línea y activa la opción *Línea constructiva* en el menú lateral izquierdo (PropertyManager).
- **Atajo / Sintaxis visual:** Aparece representada con trazos discontinuos (raya y punto).

### Línea Normal (Sólida)

Contorno activo que formará parte de los perfiles sólidos de la pieza.

---

## 2. Círculos y Arcos

### Círculo por Centro (Center Circle)

Define primero el centro geométrico y luego se expande el radio o diámetro.
**Uso ideal:** Creación de barrenos, ejes y alojamientos cilíndricos simétricos.

### Círculo Perimetral (Perimeter Circle)

Se define mediante 3 puntos tangentes (útil para encajar círculos dentro de geometrías existentes).

---

## 3. Tipos de Rectángulos

SolidWorks ofrece diferentes formas de trazar rectángulos según la estrategia de diseño paramétrico.

### Rectángulo de Centro (Center Rectangle)

Expande el rectángulo de manera simétrica a partir de su centro geométrico.
**Ventaja clave:** Permite que el centro del rectángulo coincida automáticamente con el Origen (0,0), facilitando la simetría futura de la pieza.

### Rectángulo de Esquina (Corner Rectangle)

Se traza especificando una esquina inicial y la esquina opuesta. Requiere acotación posterior con respecto a los ejes de coordenadas para evitar que quede flotando (Under-defined).

---

## 4. Buenas Prácticas en el Croquis

1. **Aprovecha el Origen:** Siempre que sea posible, vincula el primer punto clave de tu croquis (el centro de un rectángulo o círculo base) directamente al Origen del sistema.  
2. **Usa Geometría de Referencia:** Apóyate en líneas constructivas para establecer ejes de simetría antes de aplicar herramientas de simetría (Mirror Entities).
3. **Controla el color de las líneas:**
   - 🔵 *Azul:* Geometría incompleta o con grados de libertad libres.
   - ⬛ *Negro:* Geometría completamente acotada y restringida (Fully Defined).

---

## 5. Ejemplo Práctico: Placa de Montaje Básica

Vamos a modelar una placa rectangular de **100 mm x 60 mm** con un agujero pasante centrado de **20 mm** de diámetro.

### Paso a Paso

1. **Iniciar el Croquis:**
   - Abre una nueva pieza en SOLIDWORKS.
   - Selecciona el plano **Alzado (Front Plane)** y haz clic en la herramienta **Croquis** (Sketch).

2. **Dibujar el Rectángulo:**
   - Selecciona la herramienta **Rectángulo de centro** (Center Rectangle).
   - Haz clic exactamente en el **Origen (0,0)** para que el croquis quede completamente centrado y vinculado al sistema de coordenadas.
   - Arrastra el cursor y haz clic sin importar las medidas exactas por ahora.

3. **Añadir el Círculo:**
   - Selecciona la herramienta **Círculo**.
   - Coloca el centro haciendo clic en el origen (aprovechando que el punto medio ya está definido).
   - Extiende el radio y haz clic.

4. **Acotación Inteligente (Smart Dimension):**
   - Selecciona **Cota inteligente** en la barra de herramientas superior.
   - Haz clic en la línea horizontal superior del rectángulo y asígnale una medida de **100 mm**.
   - Haz clic en la línea vertical lateral y asígnale **60 mm**.
   - Haz clic en el borde del círculo y asígnale un diámetro de **20 mm**.

5. **Verificación:**
   - Al terminar, todas las líneas del croquis deben cambiar de color **azul a negro**, lo que indica que el croquis está **Completamente Definido (Fully Defined)**.

### Captura / Evidencia

<img src="/01_Fundamentos_2D/Practicas/Practica01.png" width="500">

---

[Inicio](#01-líneas-círculos-y-rectángulos-en-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
