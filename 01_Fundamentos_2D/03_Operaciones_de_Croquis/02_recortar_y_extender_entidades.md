# 02. Recortar y Extender Entidades en Croquis 📐

En esta sección se documenta el uso de dos de las herramientas de edición y limpieza de croquis más utilizadas en SolidWorks: **Recortar Entidades (Trim Entities)** y **Extender Entidades (Extend Entities)**, las cuales permiten refinar perfiles y corregir intersecciones rápidamente.

---

## 🎯 Objetivos del Módulo

- **Dominar la limpieza de croquis:** Aprender a eliminar excesos de líneas, intersecciones y cruces indeseados.
- **Conocer los modos de recorte:** Utilizar el recorte inteligente (*Power Trim*) y otras variantes para acelerar el flujo de trabajo.
- **Ajustar geometrías abiertas:** Extender líneas o arcos hasta encontrar una arista límite de manera precisa.
  
---

## Tabla de contenido

- [02. Recortar y Extender Entidades en Croquis 📐](#02-recortar-y-extender-entidades-en-croquis-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Recortar Entidades (Trim Entities)](#1-recortar-entidades-trim-entities)
    - [Modos de Recorte Principales](#modos-de-recorte-principales)
  - [2. Extender Entidades (Extend Entities)](#2-extender-entidades-extend-entities)
    - [Cómo utilizarla](#cómo-utilizarla)
  - [3. Buenas Prácticas y Criterios de Edición](#3-buenas-prácticas-y-criterios-de-edición)
  - [4. Ejemplo Práctico: Creación de una Placa con Esquinas Rebajadas y Contornos Cruzados](#4-ejemplo-práctico-creación-de-una-placa-con-esquinas-rebajadas-y-contornos-cruzados)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Recortar Entidades (Trim Entities)

La herramienta **Recortar** ofrece varios modos de operación seleccionables en el PropertyManager lateral:

### Modos de Recorte Principales

1. **Recorte inteligente (Power Trim) — *El más utilizado*:**
   - Mantén presionado el clic izquierdo y arrastra el cursor como si fuera una cuchilla o "lápiz". Cualquier entidad que toque la línea trazada se recortará automáticamente hasta la intersección más cercana.
2. **Recorte hasta más cercano (Trim closest):**
   - Haz clic individualmente sobre el segmento de línea o arco que deseas eliminar; el tramo se borrará hasta la siguiente intersección.
3. **Recorte fuera de esquinas (Trim outside):**
   - Permite seleccionar dos líneas de límite y elimina todo lo que se encuentre por fuera de ellas.
4. **Mantener recortado / Borrar fuera:**
   - Modos avanzados para conservar solo los segmentos internos o externos delimitados por cruces de geometría.

---

## 2. Extender Entidades (Extend Entities)

La herramienta **Extender** alarga una línea, arco o parábola abierta hasta tocar la siguiente entidad límite disponible en el croquis.

### Cómo utilizarla

1. Selecciona la herramienta **Extender Entidades** en la barra de croquis.
2. Haz clic sobre el extremo de la línea o arco que deseas alargar.
3. El sistema proyectará y alargará la entidad automáticamente hasta la primera intersección o línea de contorno válida.

---

## 3. Buenas Prácticas y Criterios de Edición

1. **Evita dejar cabos sueltos (*Open loops*):** Al recortar entidades, asegúrate de que los puntos finales coincidan perfectamente mediante relaciones de *Coincidente*; de lo contrario, la operación de extrusión 3D fallará por perfil abierto.
2. **Usa *Power Trim* con precaución:** Al ser una herramienta rápida, puedes borrar por accidente una línea de referencia o cota si cruzas el cursor de más. Usa `Ctrl + Z` para deshacer inmediatamente si es necesario.
3. **Verifica las intersecciones:** Antes de salir del croquis, confirma que no queden líneas cruzadas o superpuestas que generen conflictos en el motor de operaciones 3D.

---

## 4. Ejemplo Práctico: Creación de una Placa con Esquinas Rebajadas y Contornos Cruzados

Vamos a simular un escenario común donde trazamos geometrías básicas superpuestas para luego "limpiar" los sobrantes y obtener un perfil único listo para extrusión.

### Paso a Paso

1. **Dibujar Líneas Cruzadas o Superpuestas:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja un rectángulo base de **100 mm x 60 mm**.
   - Dibuja un círculo o líneas adicionales que crucen las esquinas o el interior del rectángulo (por ejemplo, líneas diagonales que sobresalgan de los vértices).

2. **Utilizar el Recorte Inteligente (Power Trim):**
   - Selecciona la herramienta **Recortar entidades** en la barra superior del croquis.
   - Asegúrate de que esté seleccionado el modo **Recorte inteligente** (por defecto).
   - Haz clic y arrastra el cursor sobre las líneas sobrantes que salen de las esquinas del rectángulo. Observa cómo desaparecen instantáneamente al entrar en contacto con la "cuchilla".

3. **Crear una Intersección para Recortar:**
   - Dibuja una línea que atraviese de lado a lado una sección interna del rectángulo.
   - Utiliza de nuevo el *Recorte inteligente* para eliminar el segmento central, dividiendo el espacio en secciones limpias.

4. **Probar la Herramienta Extender:**
   - Dibuja una línea corta que se haya quedado "corta" y no alcance a tocar otra pared lateral.
   - Selecciona la herramienta **Extender entidades** y haz clic sobre esa línea abierta; automáticamente se estirará hasta conectar de manera precisa con la entidad límite más cercana.

5. **Verificación:**
   - Asegúrate de que el contorno final permanezca completamente cerrado (sin aberturas ni cabos sueltos), lo cual es un requisito indispensable para que SOLIDWORKS pueda extruirlo en 3D sin errores.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica08.png" width="500" alt="Captura de pantalla de la práctica 08">

---

[Inicio](#02-recortar-y-extender-entidades-en-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
