# 01. Brida Base y Brida de Arista en Chapa Metálica 📐

En esta sección se documentan las dos operaciones elementales para el modelado de piezas de chapa metálica (*Sheet Metal*): la **Brida Base/Pestaña** (que establece las propiedades globales del material y el primer cuerpo plano) y la **Brida de Arista** (que genera dobleses y paredes derivadas a partir de los bordes existentes).

---

## 🎯 Objetivos del Módulo

- **Iniciar modelos de chapa metálica:** Definir correctamente los parámetros globales de espesor, radio de pliegue y deformación del material.
- **Generar plegados perimetrales:** Construir paredes y pestañas de doblado a partir de las aristas del sólido laminar.
- **Controlar la intencionalidad dimensional:** Manejar la posición del material respecto al marco exterior de la pieza.

---

## Tabla de contenido

- [01. Brida Base y Brida de Arista en Chapa Metálica 📐](#01-brida-base-y-brida-de-arista-en-chapa-metálica-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Brida Base / Pestaña (Base Flange/Tab)](#1-brida-base--pestaña-base-flangetab)
    - [Parámetros Globales de Chapa](#parámetros-globales-de-chapa)
  - [2. Brida de Arista (Edge Flange)](#2-brida-de-arista-edge-flange)
    - [Parámetros Principales del PropertyManager](#parámetros-principales-del-propertymanager)
  - [3. Posición de la Brida y Longitud de Doblez](#3-posición-de-la-brida-y-longitud-de-doblez)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Modelado de un Soporte o Escuadra Metálica](#5-ejemplo-práctico-modelado-de-un-soporte-o-escuadra-metálica)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Brida Base / Pestaña (Base Flange/Tab)

La **Brida Base** es la primera operación utilizada al crear una pieza de chapa metálica. Convierte un croquis 2D cerrado o abierto en un cuerpo laminar con espesor uniforme.

### Parámetros Globales de Chapa

Al generar la primera brida base, el software define las reglas del árbol para todo el cuerpo:

- **Espesor ($t$):** Calibre o grosor de la lámina de metal.
- **Radio de pliegue predeterminado ($R$):** Radio interno mínimo aplicado a todos los dobleses automáticos.
- **Factor K / Margen de dobles (*K-Factor*):** Constante empírica que representa la ubicación de la fibra neutra del material durante la deformación plástica, clave para el cálculo del desarrollo plano (*Unfold*).
- **Desahogo automático (*Auto Relief*):** Tipo de corte (Rectangular, Rasgado, Cilíndrico) que se aplica automáticamente en las esquinas donde se intersecta un pliegue para evitar deformaciones no deseadas del material.

---

## 2. Brida de Arista (Edge Flange)

La **Brida de Arista** permite añadir pestañas o paredes dobladas seleccionando una o varias aristas del cuerpo de chapa existente.

### Parámetros Principales del PropertyManager

- **Longitud de la brida:** Define la extensión de la nueva pared (medida desde la condición virtual de intersección o la cara interna/externa).
- **Ángulo de la brida:** Permite inclinar la nueva pared en un ángulo distinto a $90^\circ$ respecto a la cara base.
- **Editar el perfil de la brida:** Permite modificar el croquis de la pestaña agregada para crear formas trapezoidales, con muescas o redondeadas en lugar de rectangulares completas.

---

## 3. Posición de la Brida y Longitud de Doblez

Controla cómo se sitúa el nuevo pliegue respecto al borde original seleccionado:

| Opción de Posición | Comportamiento del Material |
| :--- | :--- |
| **Material en el interior** | La cara externa del nuevo pliegue se alinea con la arista original; la pieza no sobrepasa el límite. |
| **Material en el exterior** | Todo el pliegue y la nueva pared se posicionan por fuera de la arista seleccionada. |
| **Pliegue en el exterior** | El pliegue inicia justo a partir del borde exterior de la cara base. |
| **Pliegue desde la condición virtual** | Alinea la tangente del doblado respecto a la proyección geométrica de las caras. |

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Estandariza los calibres:** Configura la tabla de calibres (*Gauge Table*) o consulta las especificaciones del proveedor antes de modelar para trabajar con espesores de lámina reales (ej. Calibre 14, 16, 18).
2. **Radio mínimo de doblado:** Procura que el radio de pliegue interno sea al menos igual o mayor al espesor del material ($R \ge t$) para prevenir grietas o fracturas mecánicas en el proceso de doblado en prensa.
3. **Mismo sentido de desahogo:** Mantén habilitada la opción de desahogo automático para garantizar que el archivo desplegado no contenga esquinas superpuestas al exportar a formatos DXF/DWG para corte por láser o plasma.

---

## 5. Ejemplo Práctico: Modelado de un Soporte o Escuadra Metálica

Vamos a diseñar una escuadra de montaje metálica doblando una chapa plana mediante una arista lateral.

### Paso a Paso

1. **Crear el Croquis Base:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja una línea horizontal (ej. **80 mm**) y una línea vertical conectada en L (ej. **60 mm**). *Nota: A diferencia del modelado sólido normal, en chapa metálica los perfiles pueden ser líneas abiertas.*
   - Cierra el croquis.

2. **Aplicar la Brida Base / Pestaña:**
   - Ve a la pestaña **Insertar > Chapa metálica** en la barra de comandos superior (si no la ves visible, haz clic derecho sobre cualquier pestaña y actívala).
   - Haz clic en la herramienta **Brida base/pestaña**.
   - En el panel de propiedades izquierdo, desmarca o ajusta los parámetros principales:
     - Asigna un espesor de lámina de **1.5 mm**.
     - Define una profundidad de extrusión en condición *Ciego* o *Plano medio* (ej. **50 mm** de ancho para la escuadra).
   - Haz clic en la **paloma verde (Aceptar)**. Observa cómo el icono de la operación en el árbol cambia y se genera una pieza de chapa con sus propiedades de pliegue.

3. **Añadir una Brida de Arista (Edge Flange):**
   - Selecciona la herramienta **Insertar > Chapa metálica > Brida de arista** en la barra de chapa metálica.
   - Haz clic sobre una de las aristas lineales exteriores de tu escuadra recién creada.
   - Mueve el cursor hacia afuera o hacia adentro para indicar la dirección en la que se levantará la nueva pared.
   - En el panel de propiedades, asigna una longitud de pestaña (ej. **30 mm**) y un ángulo de **90°**.
   - Revisa cómo SOLIDWORKS calcula automáticamente el radio de curvatura interior y los alivios de esquina.
   - Haz clic en la **paloma verde** para confirmar.

4. **Verificación del Desplegado (Flatten):**
   - Haz clic en el botón **Desplegar (Flatten)** en la barra de chapa metálica. Podrás ver cómo la pieza tridimensional se aplana matemáticamente en una lámina bidimensional lista para corte láser, simulando el proceso real de manufactura.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica21.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#01-brida-base-y-brida-de-arista-en-chapa-metálica-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
