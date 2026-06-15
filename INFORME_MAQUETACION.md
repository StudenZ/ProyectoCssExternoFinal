# INFORME DE PRÁCTICA: MAQUETACIÓN WEB CON CSS EXTERNO
## TEMA: MAQUETACIÓN MULTICAPA MEDIANTE BOX MODEL, FLEXBOX Y GRID LAYOUT EN DARKKITCHEN

---

### **1. PORTADA**

* **Institución:** [Nombre de tu Institución Educativa - Ej. Universidad Técnica]
* **Facultad:** [Facultad de Ingeniería / Ciencias de la Computación]
* **Asignatura:** Desarrollo Web / Programación Web
* **Actividad:** Informe de Maquetación Web con Hojas de Estilo Externas (CSS3)
* **Estudiante:** Moises
* **Curso / Paralelo:** [Ej. 6to Semestre - Paralelo A]
* **Docente:** [Nombre del Docente]
* **Fecha de Entrega:** 15 de junio de 2026

---

### **ÍNDICE DE FIGURAS**
*(Nota: Si copia este informe a Microsoft Word, puede ir a la pestaña "Referencias" > "Insertar tabla de ilustraciones" para generar el índice dinámico automáticamente. A continuación se presenta la relación correspondiente al documento).*

* **Figura 1:** Estructura de directorios y organización del proyecto.
* **Figura 2:** Implementación del Box Model y Reset de márgenes globales.
* **Figura 3:** Distribución y alineación de elementos de la cabecera (Header) mediante Flexbox.
* **Figura 4:** Diseño del contenedor de tarjetas de favoritos mediante Flexbox flexible (`flex-wrap`).
* **Figura 5:** Maquetación asimétrica tipo mosaico responsivo en la Galería usando CSS Grid.
* **Figura 6:** Diseño de rejilla fluida para el Catálogo de Servicios con CSS Grid y tarjetas adaptativas.
* **Figura 7:** Vista previa de la Página Principal (Inicio) con secciones unificadas y Banner Hero.
* **Figura 8:** Vista de la sección de Favoritos destacada con tarjetas organizadas con Flexbox.
* **Figura 9:** Vista de la Galería de Promociones con distribución Grid interactiva.
* **Figura 10:** Vista de la página secundaria "Pedir Ahora" (Formulario adaptativo estructurado con Flexbox).

---

### **2. ENLACE DEL REPOSITORIO GITHUB**

El desarrollo continuo del sitio web y la incorporación de las hojas de estilo externas para la maquetación se encuentran alojados en el siguiente repositorio de GitHub:

* **Enlace del Repositorio:** [https://github.com/StudenZ/ProyectoCssExternoFinal.git](https://github.com/StudenZ/ProyectoCssExternoFinal.git)
* **Evidencia de Continuidad:** El repositorio contiene el historial de commits que demuestra la evolución del sitio web, desde la maquetación HTML base hasta la estructuración modular con hojas de estilo externas (CSS).

---

### **3. DESCRIPCIÓN BREVE DEL SITIO WEB**

El sitio web desarrollado se denomina **DarkKitchen**, un portal para una hamburguesería artesanal que funciona bajo el modelo de "cocina fantasma" (entrega directa a domicilio y retiro). El objetivo primordial del sitio es ofrecer una experiencia digital inmersiva, elegante y rápida, permitiendo al usuario explorar la historia de la marca, revisar el menú detallado con precios, examinar promociones especiales mediante un mosaico interactivo, realizar búsquedas con filtros y gestionar pedidos en línea mediante un formulario estructurado.

Mediante la maquetación CSS externa, se mejoraron significativamente las siguientes secciones:
1. **Cabecera y Navegación:** Convertida en una barra adhesiva (*sticky header*) con desenfoque de fondo (*glassmorphism*), distribuyendo el logotipo y el menú de navegación de forma simétrica.
2. **Sección de Favoritos (Langing Page):** Transformada en un bloque de tarjetas de productos destacado, alineado horizontalmente con Flexbox para ajustarse a cualquier tamaño de pantalla.
3. **Galería de Promociones:** Estructurada en un mosaico dinámico asimétrico (*CSS Grid Mosaic*) con tarjetas de tamaños especiales (ancho doble y alto doble) que colapsan en una sola columna en dispositivos móviles.
4. **Catálogo de Servicios (Menú):** Diseñado sobre una rejilla bidimensional que adapta de forma automática el número de columnas según la resolución de la pantalla.
5. **Formulario de Contacto / Pedidos:** Organizado mediante filas y columnas flexibles para una correcta alineación de datos personales, opciones de comida y mapas de ubicación.

---

### **4. ESTRUCTURA DE ARCHIVOS**

El proyecto mantiene una estructura modular y limpia, separando las páginas HTML en una carpeta específica y distribuyendo los estilos CSS de forma individual por sección para mejorar la mantenibilidad y el rendimiento.

```text
ProyectoWeb/
├── css/
│   ├── buscar.css        <-- Estilos de la página de filtros y búsqueda
│   ├── contacto.css      <-- Estilos del formulario de pedidos y ubicación
│   ├── galeria.css       <-- Estilos del mosaico de promociones (CSS Grid)
│   ├── general.css       <-- Variables de diseño, reset, header, footer y formularios comunes
│   ├── index.css         <-- Estilos de la landing page y acordeón FAQ
│   └── servicios.css     <-- Estilos de catálogo del menú y tabla comparativa
├── img/                  <-- Recursos gráficos y capturas del proyecto
├── index.html            <-- Página principal (Inicio)
└── pages/                <-- Páginas secundarias del portal
    ├── buscar.html
    ├── contacto.html
    ├── galeria.html
    ├── login.html
    ├── nosotros.html
    ├── registro.html
    └── servicios.html
```

#### *Captura de la Estructura de Archivos en el Editor de Código:*

![Figura 1: Estructura de archivos y organización del proyecto.](./img/informe/figura1_estructura_archivos.png)
*Descripción: La organización del sitio web muestra la carpeta `css` conteniendo el archivo unificado `general.css` junto con hojas de estilos independientes para cada página secundaria, garantizando modularidad.*

---

### **5. CÓDIGO RELEVANTE DE BOX MODEL**

El diseño se fundamenta en el Modelo de Caja (*Box Model*). Para controlar con precisión las dimensiones globales y evitar desbordamientos, se utiliza el selector universal con la propiedad `box-sizing: border-box`. Esto asegura que los paddings y bordes se incluyan dentro del ancho y alto total de cada elemento.

#### **Reset Global y Box-Sizing (`general.css`):**
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box; /* Incluye padding y border en el tamaño total */
}
```

#### **Control del Modelo de Caja en Secciones (`general.css`):**
Las secciones utilizan márgenes inferiores dinámicos, rellenos internos uniformes y bordes detallados para una óptima visualización:
```css
section {
  background-color: var(--bg-secondary);
  border: 1px solid var(--border-color);
  border-radius: var(--border-radius-md);
  padding: 40px; /* Espaciado interno para separar el contenido del borde */
  margin-bottom: 40px; /* Margen externo para distanciar los bloques */
  box-shadow: var(--shadow-sm);
}
```

#### *Captura del Código Box Model en el Editor:*

![Figura 2: Implementación del Box Model y Reset de márgenes globales.](./img/informe/figura2_box_model.png)
*Descripción: Fragmento de código correspondiente a `general.css` donde se visualiza el reset global y las propiedades de modelo de caja (`padding`, `margin-bottom`, `border` y `box-shadow`) aplicadas a los bloques de contenido.*

---

### **6. CÓDIGO RELEVANTE DE FLEXBOX**

Flexbox se empleó en maquetaciones unidimensionales donde se requería alinear elementos de forma lineal (horizontal o vertical) y adaptar los anchos automáticamente de acuerdo al dispositivo.

#### **Alineación de la Cabecera (Header en `general.css`):**
Permite que el logotipo y el menú de navegación se sitúen en los extremos opuestos y se alineen verticalmente al centro:
```css
header {
  display: flex;
  justify-content: space-between; /* Distribución en los extremos */
  align-items: center; /* Centrado vertical */
  position: sticky;
  top: 0;
  z-index: 1000;
  background-color: rgba(10, 11, 14, 0.85);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border-color);
  padding: 15px 5%;
}
```

#### **Contenedor de Tarjetas de Productos Destacados (Favoritos en `index.css`):**
Se utiliza Flexbox con capacidad multilinea (`flex-wrap: wrap`) para ordenar los productos favoritos de forma horizontal y pasarlos a modo vertical automáticamente si el ancho disminuye:
```css
.tarjetas-container {
  display: flex;
  flex-wrap: wrap; /* Permite saltos de línea responsivos */
  gap: 30px; /* Separación inteligente entre tarjetas */
  justify-content: center; /* Centrado de tarjetas */
}

.tarjeta {
  flex: 1 1 280px; /* Flex-grow, flex-shrink y flex-basis inicial */
  max-width: 340px;
  background-color: var(--bg-tertiary);
  border: 1px solid var(--border-color);
  border-radius: var(--border-radius-md);
  padding: 24px;
  display: flex;
  flex-direction: column; /* Alineación vertical del contenido de la tarjeta */
  justify-content: space-between; /* Empuja el botón y precio a la base */
  transition: all var(--transition-normal);
}
```

#### *Captura del Código Flexbox en el Editor:*

![Figura 3: Distribución y alineación de elementos de la cabecera (Header) mediante Flexbox.](./img/informe/figura3_flexbox_header.png)
*Descripción: Código en `general.css` que demuestra la declaración de flexbox en el header del sitio web.*

![Figura 4: Diseño del contenedor de tarjetas de favoritos mediante Flexbox flexible (`flex-wrap`).](./img/informe/figura4_flexbox_tarjetas.png)
*Descripción: Configuración del contenedor de favoritos en `index.css` que garantiza que las tarjetas de productos se distribuyan en cuadrículas adaptables usando Flexbox.*

---

### **7. CÓDIGO RELEVANTE DE GRID**

Para maquetaciones bidimensionales complejas (filas y columnas simultáneas) se recurrió a CSS Grid, logrando un mosaico interactivo de promociones y un catálogo de menú responsivo.

#### **Mosaico Asimétrico en Galería (`galeria.css`):**
En pantallas grandes se generan 3 columnas de igual tamaño (`repeat(3, 1fr)`). Ciertas tarjetas toman un ancho doble (`grid-column: span 2`) o un alto doble (`grid-row: span 2`), logrando un efecto tipo revista o *mosaico*:
```css
.galeria-grid {
  display: grid;
  grid-template-columns: 1fr; /* Una columna por defecto en móviles */
  gap: 24px;
  margin-bottom: 40px;
}

@media (min-width: 768px) {
  .galeria-grid {
    grid-template-columns: repeat(3, 1fr); /* Tres columnas en escritorio */
  }

  .item-ancho {
    grid-column: span 2; /* Ocupa 2 columnas de ancho */
  }

  .item-alto {
    grid-row: span 2; /* Ocupa 2 filas de alto */
    height: 664px; /* Altura calculada según el gap de 24px */
  }
}
```

#### **Catálogo de Servicios Auto-Ajustable (`servicios.css`):**
Utiliza la propiedad `auto-fit` combinada con `minmax` para acomodar tantas columnas como quepan en la pantalla de manera 100% automática, sin necesidad de definir múltiples media queries para cada tamaño de pantalla:
```css
#menu-lista {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); /* Grilla auto-adaptable */
  gap: 30px;
  padding: 20px 0 40px 0;
}
```

#### *Captura del Código Grid en el Editor:*

![Figura 5: Maquetación asimétrica tipo mosaico responsivo en la Galería usando CSS Grid.](./img/informe/figura5_grid_galeria.png)
*Descripción: Código de la galería asimétrica en `galeria.css` que combina CSS Grid con Media Queries para lograr spans de filas y columnas.*

![Figura 6: Diseño de rejilla fluida para el Catálogo de Servicios con CSS Grid y tarjetas adaptativas.](./img/informe/figura6_grid_servicios.png)
*Descripción: Uso de `repeat(auto-fit, minmax(...))` en `servicios.css` para crear un catálogo de menú inteligente y fluido.*

---

### **8. EVIDENCIAS VISUALES DEL RESULTADO**

*(Nota: Reemplace estas figuras con capturas reales de su navegador para la versión final de su informe).*

#### **Página Principal (Inicio):**
![Figura 7: Vista previa de la Página Principal (Inicio) con secciones unificadas y Banner Hero.](./img/informe/figura7_pantalla_inicio.png)
*Descripción: Captura de pantalla de la página de Inicio donde se aprecia la barra de navegación superior fija (sticky glassmorphism), el Banner Hero de presentación con fondo degradado y la correcta distribución de la marca.*

#### **Sección de Favoritos con Flexbox:**
![Figura 8: Vista de la sección de Favoritos destacada con tarjetas organizadas con Flexbox.](./img/informe/figura8_pantalla_favoritos.png)
*Descripción: Tres tarjetas destacadas (Classic Smash, Bacon BBQ y Dark Fries) alineadas de forma equidistante con Flexbox, manteniendo dimensiones equivalentes e imágenes adaptadas.*

#### **Galería / Catálogo con Grid:**
![Figura 9: Vista de la Galería de Promociones con distribución Grid interactiva.](./img/informe/figura9_pantalla_galeria.png)
*Descripción: Visualización del mosaico asimétrico de promociones. Las tarjetas destacadas ocupan mayor espacio horizontal o vertical debido al uso de spans en CSS Grid.*

#### **Página Secundaria (Estructura de Pedidos):**
![Figura 10: Vista de la página secundaria "Pedir Ahora" (Formulario adaptativo estructurado con Flexbox).](./img/informe/figura10_pantalla_contacto.png)
*Descripción: Página de contacto y pedidos (`contacto.html`) mostrando el formulario estructurado en secciones con fieldsets estilizados y campos agrupados en filas dinámicas con Flexbox.*

---

### **9. EXPLICACIÓN DE LA MAQUETACIÓN REALIZADA**

La maquetación de **DarkKitchen** se estructuró a través del uso integrado de tres metodologías CSS indispensables: **Box Model**, **Flexbox** y **CSS Grid**. 

En primer lugar, se aplicó un sistema de diseño fundamentado en el **Box Model** en el archivo `general.css`. Al configurar el reset con `box-sizing: border-box`, se garantizó que los anchos declarados fuesen respetados sin importar los márgenes internos (`padding`) y bordes aplicados. Cada bloque de sección principal (`section`) se separó sistemáticamente con un `margin-bottom: 40px` y se le asignó un `padding: 40px` para dotar de "aire" visual a la interfaz, mejorando la concentración del usuario.

En segundo lugar, se implementó **Flexbox** para la distribución unidimensional del contenido. En la cabecera (`header`), Flexbox gestiona el posicionamiento del logotipo y el menú mediante `justify-content: space-between` de forma limpia y sin floats obsoletos. De igual forma, en la sección de favoritos de la landing page y en el formulario de pedidos, Flexbox permite alinear inputs en filas (`flex-direction: row`) que cambian dinámicamente a columnas (`flex-direction: column`) en dispositivos móviles, lo que optimiza el flujo táctil del cliente al realizar una orden.

En tercer lugar, se recurrió a **CSS Grid** para la distribución bidimensional compleja. En el catálogo de servicios de `servicios.css`, la propiedad `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))` calcula de forma automatizada las columnas óptimas, distribuyendo las tarjetas de comida en filas ordenadas y adaptables. Por su parte, la galería de imágenes de `galeria.css` hace uso avanzado de `grid-column: span 2` y `grid-row: span 2` para destacar promociones particulares en un formato de mosaico visualmente atractivo, resolviendo el problema de las grillas estáticas rígidas.

---

### **10. CONCLUSIÓN**

La maquetación web estructurada mediante CSS externo es un pilar fundamental en el desarrollo web moderno. El uso conjunto de Box Model, Flexbox y Grid Layout permite a los desarrolladores estructurar interfaces complejas que no solo son visualmente atractivas, sino también altamente funcionales, accesibles y adaptables a múltiples dispositivos (diseño responsivo). 

Específicamente, **Box Model** proporciona un control matemático preciso sobre el tamaño de las cajas; **Flexbox** agiliza la alineación y el flujo de elementos en filas o columnas dinámicas; y **CSS Grid** otorga la libertad creativa y técnica para diseñar grillas bidimensionales de alta complejidad. La separación de estas reglas de estilo en archivos independientes por página web asegura una arquitectura de código limpia, escalable y mantenible a largo plazo, facilitando el trabajo colaborativo y optimizando los tiempos de carga en producción.
