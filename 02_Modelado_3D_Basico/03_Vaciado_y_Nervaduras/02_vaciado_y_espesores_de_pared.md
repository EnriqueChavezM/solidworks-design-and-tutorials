# 02. Vaciado y Espesores de Pared en CAD 🧼

La operación **Vaciado (Shell)** permite convertir un sólido masivo en una pieza hueca de pared delgada con un espesor constante o variable. Es una herramienta clave en el diseño de carcasas, recipientes, cubiertas y piezas destinadas a procesos de moldeo por inyección de plástico o fundición.

---

## 🎯 Objetivos del Módulo

- **Optimizar masa y material:** Remover el núcleo interno no estructural de un modelo 3D manteniendo la rigidez del contorno.
- **Controlar espesores constantes:** Garantizar tolerancias de pared uniformes para procesos de manufactura.
- **Configurar vaciados avanzados:** Asignar espesores diferenciados a caras específicas según requerimientos mecánicos.

---

## Tabla de contenido

- [02. Vaciado y Espesores de Pared en CAD 🧼](#02-vaciado-y-espesores-de-pared-en-cad-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Operación de Vaciado (Shell)](#1-operación-de-vaciado-shell)
    - [Parámetros Principales del PropertyManager](#parámetros-principales-del-propertymanager)
  - [2. Tipos de Vaciado](#2-tipos-de-vaciado)
  - [3. Consideraciones de Geometría y Radio Cero](#3-consideraciones-de-geometría-y-radio-cero)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Conversión de un Bloque Sólido en una Carcasa Plástica](#5-ejemplo-práctico-conversión-de-un-bloque-sólido-en-una-carcasa-plástica)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Operación de Vaciado (Shell)

El vaciado remueve el material del interior de la pieza dejando paredes del espesor especificado. Si no se seleccionan caras para eliminar, el sistema creará un cuerpo totalmente cerrado con cavidad interna hueca.

### Parámetros Principales del PropertyManager

- **Espesor ($t$):** Especifica el grosor constante de las paredes del sólido.
- **Caras a eliminar (Faces to Remove):** Selección de una o más caras que serán removidas para abrir el interior de la pieza.
- **Vaciado hacia afuera (Shell Outward):** En lugar de reducir el volumen interno, añade el espesor de pared hacia la superficie exterior del sólido.
- **Configuración de múltiples espesores:** Permite seleccionar caras individuales y asignarles un espesor distinto al valor general.

---

## 2. Tipos de Vaciado

1. **Vaciado de Cara Abierta:**
   - Se elimina al menos una cara (ej. la parte superior de un contenedor), creando un volumen hueco accesible desde el exterior.
2. **Vaciado Cero / Sólido Cerrado:**
   - No se selecciona ninguna cara para remover. El resultado es un cuerpo cerrado hueco por dentro (útil para flotadores, pelotas o piezas impresas en 3D con cavidad interna).
3. **Vaciado con Espesores Múltiples:**
   - Permite combinar paredes delgadas generales con bases o zonas de anclaje más gruesas dentro de la misma operación.

---

## 3. Consideraciones de Geometría y Radio Cero

- **Relación entre Radio Interno y Espesor:** Si el modelo incluye redondeos previos con un radio $R$, el vaciado generará un radio interno de $R - t$ (si es hacia adentro). Si el radio del redondeo es menor o igual al espesor ($R \le t$), la reconstrucción del sólido fallará por auto-intersección de caras.
- **Espesor mínimo de manufactura:** Piezas plásticas inyectadas requieren mantener un espesor uniforme para evitar rechupados (*sink marks*) o deformaciones por enfriamiento desigual.

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Aplica redondeos exteriores antes del vaciado:** Si agregas redondeos a las aristas exteriores antes de la operación de vaciado, el software creará automáticamente los redondeos interiores concéntricos de forma limpia.
2. **Usa la vista de sección para verificación:** Utiliza la herramienta *Vista de sección (Section View)* tras realizar el vaciado para verificar que no existan zonas sólidas no deseadas ni paredes delgadas colapsadas.
3. **Orden en el árbol de operaciones:** El vaciado debe aplicarse **antes** de añadir detalles finos como nervaduras, torres de fijación (*bosses*) o roscas internas, para evitar que estas características sean vaciadas por accidente.

---

## 5. Ejemplo Práctico: Conversión de un Bloque Sólido en una Carcasa Plástica

Vamos a tomar el bloque rectangular macizo que modelamos en prácticas anteriores y lo convertiremos en una caja o carcasa hueca con un espesor de pared controlado.

### Paso a Paso

1. **Partir de un Sólido Base:**
   - Asegúrate de tener tu bloque rectangular sólido (por ejemplo, de 100 mm x 60 mm x 40 mm) completamente libre de operaciones de corte internas complejas para empezar desde una base limpia.

2. **Acceder a la Herramienta de Vaciado:**
   - Ve a la pestaña **Operaciones (Features)** en la barra de comandos superior.
   - Haz clic en la herramienta **Vaciado (Shell)**.

3. **Configurar los Parámetros en el Panel Izquierdo:**
   - En la casilla de **Espesor (Thickness 1)**, introduce el valor deseado para las paredes (por ejemplo, **3 mm**).
   - Haz clic en la casilla de **Caras a eliminar** y selecciona la **cara superior** del bloque. Observa la vista preliminar en amarillo: verás cómo el interior del bloque desaparece, dejando únicamente una cáscara con paredes de 3 mm de grosor y el fondo intacto.

4. **Confirmar la Operación:**
   - Haz clic en la **paloma verde (Aceptar)** para generar el vaciado.
   - Gira la pieza con el botón central del ratón para comprobar que el interior ha quedado completamente hueco y uniforme.
   - Revisa el **Árbol de Diseño (FeatureManager)**: notarás que se ha añadido la operación `Vaciado1` al final de tu historial.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica16.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#02-vaciado-y-espesores-de-pared-en-cad-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
