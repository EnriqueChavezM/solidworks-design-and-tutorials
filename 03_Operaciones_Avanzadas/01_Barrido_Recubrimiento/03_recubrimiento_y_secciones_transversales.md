# 03. Recubrimiento y Secciones Transversales en CAD 📐

La operación **Recubrimiento (Loft)** es una de las herramientas de modelado de superficies y sólidos más potentes en CAD. Permite generar volúmenes fluidos y orgánicos mediante la transición suave entre dos o más perfiles planos (secciones transversales) ubicados en distintos planos del espacio.

---

## 🎯 Objetivos del Módulo

- **Modelar geometrías de transición complejas:** Conectar perfiles de formas heterogéneas (ej. pasar de un cuadrado a un círculo).
- **Alinear conectores de croquis:** Controlar los nodos de paso para evitar estrangulamientos o torsiones no deseadas en la superficie.
- **Aplicar condiciones de tangencia:** Utilizar restricciones de vector para lograr continuidad suave con superficies o planos adyacentes.

---

## Tabla de contenido

- [03. Recubrimiento y Secciones Transversales en CAD 📐](#03-recubrimiento-y-secciones-transversales-en-cad-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Conceptos Fundamentales del Recubrimiento](#1-conceptos-fundamentales-del-recubrimiento)
  - [2. Conectores y Control de Torsión](#2-conectores-y-control-de-torsión)
  - [3. Restricciones de Inicio y Fin (Start/End Constraints)](#3-restricciones-de-inicio-y-fin-startend-constraints)
  - [4. Curvas Guía y Parámetros del Centro](#4-curvas-guía-y-parámetros-del-centro)
  - [5. Buenas Prácticas y Criterios de Diseño](#5-buenas-prácticas-y-criterios-de-diseño)
  - [2. Ejemplo Práctico: Adaptador de Transición (De Cuadrado a Círculo)](#2-ejemplo-práctico-adaptador-de-transición-de-cuadrado-a-círculo)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Conceptos Fundamentales del Recubrimiento

A diferencia del barrido (que desplaza un solo perfil a lo largo de una ruta), el recubrimiento requiere de **múltiples croquis paralelos o desplazados en el espacio 3D**:

- **Secciones Transversales (Profiles):** Croquis que definen la forma del sólido en diferentes etapas axiales.
- **Secuencia de selección:** Los perfiles deben seleccionarse en un orden lógico consecutivo (de un extremo al otro).
- **Corte por recubrimiento (Lofted Cut):** Utiliza la misma lógica de múltiples perfiles para remover material interno con transiciones complejas.

---

## 2. Conectores y Control de Torsión

Al seleccionar los perfiles, el software crea **puntos de conexión (Connectors)** automáticos que unen los vértices o nodos de cada croquis.

- **Alineación de conectores:** Es crucial asegurar que los puntos azules de control estén alineados en la misma posición relativa de cada perfil.
- **Prevención de torsión:** Si los conectores están cruzados, el sólido generado se retorcerá sobre su propio eje, produciendo fallas de geometría o auto-intersección.
- **Mismo número de segmentos:** Es recomendable trazarlos con un número similar de vértices o usar la herramienta *Dividir entidades* (*Split Entities*) para que la correspondencia de puntos sea exacta.

---

## 3. Restricciones de Inicio y Fin (Start/End Constraints)

Permiten controlar la dirección del vector con el que el sólido emerge o entra en los perfiles terminales:

| Restricción | Efecto sobre la Geometría |
| :--- | :--- |
| **Ninguno (Default)** | La superficie sigue la trayectoria recta directa entre perfiles. |
| **Normal al perfil** | Fuerza a la superficie a salir perpendicularmente ($90^\circ$) respecto al plano del croquis inicial o final. |
| **Tangencia a la cara** | Aplica continuidad suave de tangencia ($G^1$) con las caras de un sólido contiguo. |
| **Curvatura continua** | Asegura continuidad de radio de curvatura ($G^2$) para acabados estéticos de clase A. |

---

## 4. Curvas Guía y Parámetros del Centro

- **Curvas Guía (Guide Curves):** Líneas 2D o 3D que fuerzan el contorno exterior del recubrimiento a seguir un perfil lateral específico entre las secciones transversales.
- **Línea de centro (Centerline Loft):** Sustituye la trayectoria de transición lineal directa por una curva que actúa como el eje neutro del sólido, manteniendo las secciones perpendiculares a dicha línea.

---

## 5. Buenas Prácticas y Criterios de Diseño

1. **Selecciona puntos homólogos:** Al hacer clic para añadir perfiles a la lista del recubrimiento, haz clic siempre cerca de la misma esquina o posición en cada croquis.
2. **Utiliza geometría de referencia limpia:** Crea planos auxiliares bien definidos con cotas paramétricas de desfase para colocar las secciones transversales.
3. **Puntos de croquis coincidentes:** Garantiza que las curvas guía tengan relaciones de **Perforar (Pierce)** o **Coincidente** con los vértices de cada uno de los perfiles para prevenir errores de reconstrucción.

---

## 2. Ejemplo Práctico: Adaptador de Transición (De Cuadrado a Círculo)

Vamos a modelar una pieza de transición industrial (como un ducto de ventilación o una tolva) que pasa de una base cuadrada a una salida redonda.

### Paso a Paso

1. **Crear el Primer Perfil (Base):**
   - Abre un croquis en el plano **Planta**.
   - Dibuja un **Rectángulo de centro** de **100 mm x 100 mm**. Cierra el croquis.

2. **Crear un Plano de Referencia Paralelo:**
   - Ve a **Operaciones > Geometría de referencia > Plano**.
   - Selecciona el plano *Planta* como referencia y asigna una distancia de separación vertical (ej. **80 mm**). Haz clic en la paloma verde para crear el `Plano1`.

3. **Crear el Segundo Perfil (Salida):**
   - Abre un nuevo croquis sobre el `Plano1` recién creado.
   - Presiona la barra espaciadora y selecciona la vista *isométrica*.
   - Dibuja un **círculo** concéntrico con un diámetro específico (ej. **Ø 60 mm**). Cierra el croquis.

4. **Ejecutar el Saliente por Recubrimiento (Loft):**
   - Ve a la pestaña **Operaciones (Features)** en la barra superior.
   - Haz clic en la herramienta **Saliente/Base recubierto**.
   - En el panel de propiedades izquierdo, haz clic secuencialmente en el **rectángulo** de la base y luego en el **círculo** superior (asegúrate de hacer clic en puntos correspondientes de ambos perfiles, como los conectores verdes, para evitar torsiones extrañas).
   - Observa la vista previa en 3D de cómo las paredes se funden suavemente del cuadrado al círculo.
   - Haz clic en la **paloma verde (Aceptar)** para generar el sólido final.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica20.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#03-recubrimiento-y-secciones-transversales-en-cad-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
