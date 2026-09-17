# Práctica 02: Polígonos y Ranuras

En esta sección exploraremos herramientas geométricas avanzadas del **Croquis 2D** en SOLIDWORKS: los **Polígonos** (ideales para cabezas de tornillos, tuercas o geometrías simétricas) y las **Ranuras (Slots)** (muy utilizadas para guías, correderas o alojamientos de pernos con ajuste).

---

## 1. Resumen de Herramientas

* **Polígono:** Permite crear figuras geométricas regulares (de 3 hasta 99 lados). Podemos configurarlo de dos formas:
  * *Inscrito (Inscribed Circle):* El círculo de referencia pasa por los vértices externos del polígono.
  * *Circunscrito (Circumscribed Circle):* El círculo de referencia es tangente a los lados planos del polígono.
* **Ranura (Slot):** Crea figuras alargadas con extremos redondeados de forma rápida. Las variantes más comunes son:
  * *Ranura recta de centro a centro:* Define la longitud mediante la distancia entre los centros de los dos arcos extremos.
  * *Ranura recta de punto inicial a punto final:* Define el tamaño total de extremo a extremo exterior.
  * *Ranura de arco de centro:* Ideal para trayectorias de giro o pivotes.

---

## 2. Ejemplo Práctico: Placa con Ranura de Ajuste y Alojamiento Hexagonal

Vamos a modelar una placa de soporte de **120 mm x 50 mm** que incluye una **ranura central** para ajuste deslizante y un **hexágono** en un extremo (simulando un alojamiento para tuerca).

### Paso a Paso:

1. **Crear el Contorno Base:**
   * Abre un croquis en el plano **Alzado**.
   * Dibuja un **Rectángulo de centro** desde el origen (`0,0`) y acótalo a **120 mm de largo** por **50 mm de alto**.

2. **Añadir el Polígono (Hexágono):**
   * Selecciona la herramienta **Polígono**.
   * En el panel de propiedades izquierdo, asegúrate de configurar el número de lados en **6** (Hexágono).
   * Coloca el centro del polígono en la parte izquierda de la placa (por ejemplo, alineado horizontalmente con el origen).
   * Usa la **Cota inteligente** para definir el diámetro del círculo de construcción a **25 mm** y usa una relación horizontal para alinear uno de sus vértices o caras.

3. **Añadir la Ranura (Slot):**
   * Selecciona la herramienta **Ranura recta de centro a centro**.
   * Dibuja la ranura en la mitad derecha de la placa, asegurándote de que su eje longitudinal sea horizontal.
   * Acota la distancia entre los dos centros de los arcos a **30 mm**.
   * Acota el radio de la ranura a **10 mm**.
   * Utiliza cotas adicionales desde el origen para posicionar la ranura exactamente a la distancia deseada (por ejemplo, a 30 mm hacia la derecha del centro).

4. **Verificación:**
   * Agrega relaciones geométricas de **horizontalidad** o **verticalidad** entre los centros de las figuras y el origen para asegurar que el croquis no se mueva de manera imprevista.
   * Revisa que todas las entidades pasen de color azul a **negro (Completamente definido)**.

---

## 3. Captura / Evidencia

<img src="/01_Fundamentos_2D/Practicas/Practica02.png" width="500">

---

## 4. Tips y Buenas Prácticas Aprendidas

* **Uso del Círculo de Referencia en Polígonos:** Recuerda que al acotar un polígono, SOLIDWORKS toma el círculo inscrito o circunscrito. Define esto con claridad según si necesitas controlar la medida de llave de tu tuerca (de plana a plana) o el espacio exterior.
* **Simetría en Ranuras:** Si vas a duplicar ranuras, aprovecha las líneas constructivas y la herramienta **Simetrizar entidades (Mirror Entities)** para ahorrar tiempo y mantener un diseño paramétrico limpio.

---

**[Regresar al Documento](/01_Fundamentos_2D/02_Poligonos_y_ranuras.md)**

---
