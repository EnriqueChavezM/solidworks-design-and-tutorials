# 03. Nervaduras y Ángulos de Salida en CAD 📐

En esta sección se documenta el uso de dos herramientas clave para la optimización estructural y la manufacturabilidad de piezas moldeadas: **Nervadura (Rib)** y **Ángulo de Salida (Draft)**. Ambas operaciones permiten reforzar sólidos de pared delgada sin añadir masa innecesaria y asegurar que las piezas puedan extraerse de sus moldes sin sufrir daños.

---

## 🎯 Objetivos del Módulo

- **Reforzar estructuras delgadas:** Crear elementos rígidos de soporte a partir de perfiles 2D sencillos.
- **Garantizar la desmoldeabilidad:** Aplicar conicidades a las caras verticales para facilitar la extracción en procesos de inyección o fundición.
- **Optimizar el uso de material:** Prevenir la acumulación excesiva de masa y reducir tiempos de enfriamiento durante la manufactura.

---

## Tabla de contenido

- [03. Nervaduras y Ángulos de Salida en CAD 📐](#03-nervaduras-y-ángulos-de-salida-en-cad-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Operación de Nervadura (Rib)](#1-operación-de-nervadura-rib)
    - [Parámetros Principales del PropertyManager](#parámetros-principales-del-propertymanager)
  - [2. Operación de Ángulo de Salida (Draft)](#2-operación-de-ángulo-de-salida-draft)
    - [Tipos de Ángulo de Salida](#tipos-de-ángulo-de-salida)
  - [3. Criterios de Diseño para Piezas Moldeadas](#3-criterios-de-diseño-para-piezas-moldeadas)
  - [4. Buenas Prácticas y Errores Comunes](#4-buenas-prácticas-y-errores-comunes)
  - [2. Ejemplo Práctico: Reforzando una Carcasa con Nervaduras y Ángulo de Salida](#2-ejemplo-práctico-reforzando-una-carcasa-con-nervaduras-y-ángulo-de-salida)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Operación de Nervadura (Rib)

La herramienta **Nervadura** genera un soporte plano o perfilado de espesor constante extrudiendo un croquis de línea abierta hasta que entra en contacto con las paredes sólidas del modelo.

### Parámetros Principales del PropertyManager

- **Espesor ($t$):** Especifica el grosor de la nervadura.
- **Dirección del espesor:** Define si el espesor se distribuye hacia el Lado 1, Lado 2 o centrado respecto al croquis (*Plano medio*).
- **Dirección de extrusión:**
  - *Paralelo al croquis:* Extruye en el plano del dibujo.
  - *Perpendicular al croquis:* Extruye en dirección normal al plano del trazado.
- **Ángulo de salida integrado:** Permite añadir una inclinación cónica a las paredes de la nervadura directamente dentro de la misma operación.

---

## 2. Operación de Ángulo de Salida (Draft)

La herramienta **Ángulo de Salida** aplica una inclinación medida en grados ($\alpha$) a las caras seleccionadas de un modelo para facilitar su desmolde.

### Tipos de Ángulo de Salida

- **Plano neutro (Neutral Plane):** Selecciona una cara o plano fijo a partir del cual se calcula la inclinación; el plano neutro no cambia de tamaño.
- **Línea de separación (Parting Line):** Utiliza una arista o curva de separación existente para definir la conicidad a lo largo de la junta del molde.
- **Escalonado (Step Draft):** Varía la inclinación utilizando bordes o caras de separación escalonadas.

---

## 3. Criterios de Diseño para Piezas Moldeadas

1. **Regla del espesor de la nervadura:** Para evitar rechupados (*sink marks*) en la superficie exterior opuesta, el espesor de la base de la nervadura no debe superar el **50% al 60%** del espesor de la pared principal a la que se conecta.
2. **Valor del ángulo de salida recomendados:**
   - Piezas de plástico estándar: **$1^\circ$ a $2^\circ$** por lado.
   - Caras con texturas o acabados rugosos: **$3^\circ$ a $5^\circ$** (o más, según la profundidad de la textura).
   - Fundición de metal: **$1.5^\circ$ a $3^\circ$**.

---

## 4. Buenas Prácticas y Errores Comunes

1. **Líneas abiertas para nervaduras:** No es necesario cerrar el contorno del croquis al trazar una nervadura; basta con extender la línea hasta aproximarse a las paredes sólidas.
2. **Invertir la dirección del material:** Si aparece un error al generar la nervadura, verifica la flecha de dirección de extrusión para asegurarte de que apunta hacia el sólido y no hacia el espacio vacío.
3. **Orden de aplicación:** Aplica los **Ángulos de Salida** al inicio sobre los cuerpos sólidos primarios, crea las **Nervaduras** con su propia inclinación y añade los **Redondeos 3D** al final de todo el árbol de operaciones.

---

## 2. Ejemplo Práctico: Reforzando una Carcasa con Nervaduras y Ángulo de Salida

Vamos a tomar la carcasa hueca que creamos en la práctica anterior y le añadiremos refuerzos internos y el desmolde técnico necesario.

### Paso a Paso

1. **Utilizando el modelo la practica anterior**
2. **Crear una Nervadura Interna (Rib):**
   - Abre un croquis sobre el **plano medio** que atraviese el centro de tu carcasa hueca (o en la cara superior abierta mirando hacia el fondo).
   - Dibuja una simple **línea abierta** que conecte una pared interior con la pared opuesta. No necesitas cerrar la línea; la herramienta Rib se encarga de extender el perfil hasta chocar con el sólido.
   - Ve a la pestaña **Operaciones** y haz clic en **Nervadura**.
   - En el panel de propiedades, configura el espesor de la nervadura (ej. **10 mm**).
   - Asegúrate de que la flecha de dirección apunte hacia el interior del material de la carcasa.
   - Define si el material se extruye simétricamente o hacia un lado, y haz clic en la **paloma verde**. Observa cómo se genera el soporte de refuerzo interno.

3. **Aplicar Ángulo de Salida (Draft):**
   - Ve a la pestaña **Operaciones** y haz clic en **Ángulo de salida**.
   - En el campo de ángulo, introduce un valor pequeño (por ejemplo, **5°**).
   - **Plano neutro (Neutral Plane):** Selecciona el fondo interior de tu carcasa como la cara de referencia fija.
   - **Caras a desmoldar:** Selecciona las paredes verticales interiores y exteriores de la carcasa **(Cara de  ángulo de salida)**.
   - Haz clic en la **paloma verde**. Aunque a simple vista el cambio es casi imperceptible, las paredes ahora tienen una ligera conicidad técnica de 5 grados.

4. **Verificación en el Árbol de Diseño:**
   - Revisa tu *FeatureManager*: verás las operaciones `Nervadura1` y `Ángulo_de_salida1` integradas al final de tu historial.
  
### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica17.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#03-nervaduras-y-ángulos-de-salida-en-cad-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
