# 📱 Módulo 5: Diseño Responsive

## 🎯 Objetivos del módulo

Al finalizar este módulo podrás:

- Crear diseños que se adapten a cualquier dispositivo
- Dominar Media Queries
- Aplicar la filosofía Mobile-First
- Usar unidades relativas correctamente
- Optimizar imágenes para responsive
- Implementar diseños fluidos

---

## 📚 Contenido

### 1. Introducción al Diseño Responsive

### 2. Viewport y Meta Tag

### 3. Media Queries

### 4. Breakpoints Comunes

### 5. Mobile-First vs Desktop-First

### 6. Unidades Relativas

### 7. Imágenes Responsive

### 8. Tipografía Responsive

### 9. Diseño Fluido vs Adaptativo

### 10. Testing Responsive

---

## 1️⃣ Introducción al Diseño Responsive

### ¿Qué es Responsive Design?

El **diseño responsive** es una técnica que hace que tu sitio web se **adapte automáticamente** a diferentes tamaños de pantalla y dispositivos.

### Los 3 Pilares

```
1. Layouts Fluidos (Grid flexible)
2. Imágenes Flexibles
3. Media Queries
```

### Estadísticas Importantes

- 📱 **60%+** del tráfico web es desde móviles
- 🚀 **53%** de usuarios abandonan si la página tarda >3s
- ✅ **Google** prioriza sitios mobile-friendly en búsquedas

---

## 2️⃣ Viewport y Meta Tag

### El Meta Tag Esencial

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <!-- ⭐ SIEMPRE incluye este meta tag -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <!-- Explicación:
         - width=device-width: El ancho = ancho del dispositivo
         - initial-scale=1.0: Zoom inicial 100%
    -->
  </head>
</html>
```

⚠️ **Sin este meta tag, tu sitio NO será responsive en móviles**

### Opciones Adicionales

```html
<!-- Prevenir zoom (NO recomendado - afecta accesibilidad) -->
<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"
/>

<!-- Recomendado: Permitir zoom -->
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

---

## 3️⃣ Media Queries

### Sintaxis Básica

```css
/* CSS por defecto (todos los dispositivos) */
body {
  font-size: 16px;
}

/* ⭐ Media Query: Solo en pantallas >= 768px */
@media (min-width: 768px) {
  body {
    font-size: 18px;
  }
}
```

### Tipos de Media Queries

```css
/* POR ANCHO */
@media (min-width: 768px) {
  /* >= 768px */
}
@media (max-width: 767px) {
  /* <= 767px */
}

/* RANGO */
@media (min-width: 768px) and (max-width: 1024px) {
  /* Entre 768px y 1024px */
}

/* POR TIPO DE MEDIO */
@media screen {
  /* Pantallas */
}
@media print {
  /* Impresión */
}

/* POR ORIENTACIÓN */
@media (orientation: portrait) {
  /* Vertical */
}
@media (orientation: landscape) {
  /* Horizontal */
}

/* COMBINADAS */
@media screen and (min-width: 768px) and (orientation: landscape) {
  /* Pantalla >= 768px Y horizontal */
}

/* CARACTERÍSTICAS MODERNAS */
@media (prefers-color-scheme: dark) {
  /* Modo oscuro */
}
@media (prefers-reduced-motion: reduce) {
  /* Sin animaciones */
}
```

---

## 4️⃣ Breakpoints Comunes

### Breakpoints Estándar

```css
/* ===================================
   BREAKPOINTS RECOMENDADOS
   =================================== */

/* Extra Small (Móviles) - Por defecto */
/* 0px - 575px */

/* Small (Móviles grandes) */
@media (min-width: 576px) {
  /* Estilos para >= 576px */
}

/* Medium (Tablets) */
@media (min-width: 768px) {
  /* Estilos para >= 768px */
}

/* Large (Desktop) */
@media (min-width: 992px) {
  /* Estilos para >= 992px */
}

/* Extra Large (Desktop grande) */
@media (min-width: 1200px) {
  /* Estilos para >= 1200px */
}

/* Extra Extra Large (Pantallas muy grandes) */
@media (min-width: 1400px) {
  /* Estilos para >= 1400px */
}
```

### Breakpoints de Frameworks Populares

```css
/* BOOTSTRAP 5 */
/* xs: 0px (por defecto) */
/* sm: 576px */
/* md: 768px */
/* lg: 992px */
/* xl: 1200px */
/* xxl: 1400px */

/* TAILWIND CSS */
/* sm: 640px */
/* md: 768px */
/* lg: 1024px */
/* xl: 1280px */
/* 2xl: 1536px */
```

### Breakpoints Basados en Contenido ⭐

```css
/* ✅ MEJOR PRÁCTICA: Basados en tu diseño, no en dispositivos */

/* Cuando el menú necesita colapsar */
@media (max-width: 800px) {
  .nav-menu {
    display: none;
  }
}

/* Cuando el texto se ve muy largo */
@media (min-width: 900px) {
  .article {
    max-width: 65ch; /* 65 caracteres */
  }
}
```

---

## 5️⃣ Mobile-First vs Desktop-First

### Mobile-First ⭐ (Recomendado)

```css
/* ===================================
   MOBILE-FIRST
   Empieza con móvil, expande hacia desktop
   =================================== */

/* Base: Móvil (por defecto) */
.container {
  padding: 1rem;
}

.grid {
  display: grid;
  grid-template-columns: 1fr; /* 1 columna */
}

/* Tablet y superior */
@media (min-width: 768px) {
  .container {
    padding: 2rem;
  }

  .grid {
    grid-template-columns: repeat(2, 1fr); /* 2 columnas */
  }
}

/* Desktop y superior */
@media (min-width: 1024px) {
  .container {
    padding: 3rem;
  }

  .grid {
    grid-template-columns: repeat(3, 1fr); /* 3 columnas */
  }
}
```

### Desktop-First

```css
/* ===================================
   DESKTOP-FIRST
   Empieza con desktop, reduce hacia móvil
   =================================== */

/* Base: Desktop (por defecto) */
.container {
  padding: 3rem;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columnas */
}

/* Tablet y menor */
@media (max-width: 1023px) {
  .container {
    padding: 2rem;
  }

  .grid {
    grid-template-columns: repeat(2, 1fr); /* 2 columnas */
  }
}

/* Móvil */
@media (max-width: 767px) {
  .container {
    padding: 1rem;
  }

  .grid {
    grid-template-columns: 1fr; /* 1 columna */
  }
}
```

### ¿Por Qué Mobile-First?

✅ **Ventajas de Mobile-First**:

1. Prioriza la experiencia móvil (mayoría de usuarios)
2. Carga más rápido (CSS progresivo)
3. Fuerza a priorizar contenido esencial
4. Mejor para performance
5. Progressive Enhancement (mejora progresiva)

❌ **Desventajas de Desktop-First**:

1. Móvil se siente como "afterthought"
2. Más difícil reducir que expandir
3. Puede afectar performance en móviles

---

## 6️⃣ Unidades Relativas

### Unidades Absolutas vs Relativas

```css
/* ===================================
   ABSOLUTAS (Evitar para responsive)
   =================================== */
width: 400px; /* Siempre 400px */
font-size: 16px; /* Siempre 16px */

/* ===================================
   RELATIVAS (Usar para responsive) ⭐
   =================================== */

/* PORCENTAJES (%) - Relativo al padre */
width: 50%; /* 50% del ancho del padre */
padding: 10%; /* 10% del ancho del padre */

/* EM - Relativo al font-size del elemento */
font-size: 2em; /* 2x el tamaño actual */
padding: 1em; /* Igual al font-size */

/* REM - Relativo al font-size del root (html) ⭐ RECOMENDADO */
font-size: 1.5rem; /* 1.5x el tamaño del html */
padding: 2rem; /* 2x el tamaño del html */

/* VW/VH - Relativo al viewport */
width: 50vw; /* 50% del ancho de la ventana */
height: 100vh; /* 100% del alto de la ventana */
font-size: 5vw; /* 5% del ancho de viewport */

/* VMIN/VMAX */
font-size: 3vmin; /* 3% del lado más pequeño */
font-size: 3vmax; /* 3% del lado más grande */

/* CH - Ancho del carácter '0' */
max-width: 65ch; /* Máximo 65 caracteres de ancho */
```

### Mejores Prácticas

```css
/* ✅ RECOMENDADO */
:root {
  font-size: 16px; /* Base fija */
}

body {
  font-size: 1rem; /* 16px */
}

h1 {
  font-size: 2.5rem; /* 40px */
}

.container {
  max-width: 1200px;
  padding: 0 1rem;
  margin: 0 auto;
}

.card {
  padding: 1.5rem;
  margin-bottom: 2rem;
}

/* ❌ EVITAR píxeles en todo */
.card {
  padding: 24px;
  margin-bottom: 32px;
}
```

---

## 7️⃣ Imágenes Responsive

### Imágenes Fluidas

```css
/* ⭐ LA REGLA DE ORO */
img {
  max-width: 100%;
  height: auto;
  display: block;
}

/* Ahora las imágenes NUNCA se salen del contenedor */
```

### Picture Element (HTML 5.1)

```html
<picture>
  <!-- Móvil: imagen pequeña -->
  <source media="(max-width: 767px)" srcset="imagen-small.jpg" />

  <!-- Tablet: imagen mediana -->
  <source media="(max-width: 1023px)" srcset="imagen-medium.jpg" />

  <!-- Desktop: imagen grande -->
  <source media="(min-width: 1024px)" srcset="imagen-large.jpg" />

  <!-- Fallback -->
  <img src="imagen-default.jpg" alt="Descripción" />
</picture>
```

### Srcset y Sizes

```html
<!-- Diferentes resoluciones para diferentes densidades de píxeles -->
<img
  src="imagen-400.jpg"
  srcset="imagen-400.jpg 400w, imagen-800.jpg 800w, imagen-1200.jpg 1200w"
  sizes="
        (max-width: 600px) 100vw,
        (max-width: 1200px) 50vw,
        400px
    "
  alt="Descripción"
/>
```

### Background Images Responsive

```css
.hero {
  background-image: url("hero-mobile.jpg");
  background-size: cover;
  background-position: center;
}

@media (min-width: 768px) {
  .hero {
    background-image: url("hero-tablet.jpg");
  }
}

@media (min-width: 1024px) {
  .hero {
    background-image: url("hero-desktop.jpg");
  }
}
```

---

## 8️⃣ Tipografía Responsive

### Fluid Typography con clamp()

```css
/* ⭐ TÉCNICA MODERNA: clamp() */
h1 {
  /* min, preferred, max */
  font-size: clamp(2rem, 5vw, 4rem);
  /* Mínimo 2rem, preferido 5vw, máximo 4rem */
}

p {
  font-size: clamp(1rem, 2vw, 1.25rem);
}
```

### Escalas Tipográficas Responsive

```css
/* Base móvil */
:root {
  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.25rem;
  --text-2xl: 1.5rem;
  --text-3xl: 1.875rem;
  --text-4xl: 2.25rem;
}

/* Escala más grande en desktop */
@media (min-width: 1024px) {
  :root {
    --text-xs: 0.875rem;
    --text-sm: 1rem;
    --text-base: 1.125rem;
    --text-lg: 1.25rem;
    --text-xl: 1.5rem;
    --text-2xl: 1.875rem;
    --text-3xl: 2.25rem;
    --text-4xl: 3rem;
  }
}

h1 {
  font-size: var(--text-4xl);
}
```

### Line-height Responsive

```css
body {
  /* Móvil: line-height más espacioso para lectura */
  line-height: 1.8;
}

@media (min-width: 768px) {
  body {
    /* Desktop: line-height normal */
    line-height: 1.6;
  }
}
```

---

## 9️⃣ Diseño Fluido vs Adaptativo

### Diseño Fluido (Fluid)

```css
/* Se adapta SUAVEMENTE a cualquier tamaño */
.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}
```

### Diseño Adaptativo (Adaptive)

```css
/* Cambia en BREAKPOINTS específicos */
.container {
  width: 100%;
}

@media (min-width: 576px) {
  .container {
    width: 540px;
  }
}

@media (min-width: 768px) {
  .container {
    width: 720px;
  }
}

@media (min-width: 992px) {
  .container {
    width: 960px;
  }
}

@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
```

### Híbrido ⭐ (Recomendado)

```css
/* Combina ambos enfoques */
.container {
  width: 90%; /* Fluido */
  max-width: 1200px; /* Limitado */
  margin: 0 auto;
}

@media (min-width: 768px) {
  .container {
    width: 85%; /* Ajuste en breakpoint */
  }
}
```

---

## 🔟 Testing Responsive

### Herramientas del Navegador

```
Chrome DevTools:
1. F12 → Toggle Device Toolbar (Ctrl+Shift+M)
2. Selecciona dispositivo predefinido
3. O ingresa dimensiones personalizadas
4. Prueba orientación portrait/landscape
```

### Dispositivos Comunes para Probar

```
📱 iPhone SE: 375 x 667
📱 iPhone 12/13: 390 x 844
📱 iPhone 12/13 Pro Max: 428 x 926
📱 Samsung Galaxy S21: 360 x 800
📱 iPad: 768 x 1024
📱 iPad Pro: 1024 x 1366
💻 Laptop: 1366 x 768
🖥️ Desktop: 1920 x 1080
```

### Responsive Testing Checklist

- [ ] Móvil (320px - 767px)
- [ ] Tablet portrait (768px - 1023px)
- [ ] Tablet landscape (1024px - 1199px)
- [ ] Desktop (1200px+)
- [ ] Navegación funciona en todos los tamaños
- [ ] Imágenes se ven bien
- [ ] Texto es legible
- [ ] Botones son fáciles de tocar (min 44x44px)
- [ ] No hay scroll horizontal
- [ ] Forms funcionan correctamente

---

## 📋 Patrones Responsive Comunes

### 1. Mostly Fluid

```css
.grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

@media (min-width: 768px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .grid {
    grid-template-columns: repeat(3, 1fr);
    max-width: 1200px;
    margin: 0 auto;
  }
}
```

### 2. Column Drop

```css
/* Columnas se apilan en móvil */
.layout {
  display: flex;
  flex-direction: column;
}

@media (min-width: 768px) {
  .layout {
    flex-direction: row;
  }

  .sidebar {
    flex: 0 0 250px;
  }

  .main {
    flex: 1;
  }
}
```

### 3. Layout Shifter

```css
.container {
  display: grid;
  grid-template-areas:
    "header"
    "main"
    "sidebar"
    "footer";
}

@media (min-width: 768px) {
  .container {
    grid-template-areas:
      "header header"
      "sidebar main"
      "footer footer";
    grid-template-columns: 200px 1fr;
  }
}
```

### 4. Off Canvas

```css
.sidebar {
  position: fixed;
  left: -250px;
  width: 250px;
  transition: left 0.3s;
}

.sidebar.active {
  left: 0;
}

@media (min-width: 1024px) {
  .sidebar {
    position: static;
    left: 0;
  }
}
```

---

## 🏋️ Ejercicios Prácticos

### Ejercicio 1: [Landing Page Responsive](./ejercicio-1-landing-responsive/)

Crea una landing page mobile-first.

### Ejercicio 2: [Grid Responsive](./ejercicio-2-grid-responsive/)

Gallery con breakpoints personalizados.

### Ejercicio 3: [Navbar Responsive](./ejercicio-3-navbar-responsive/)

Navegación que se adapta a todos los tamaños.

### Ejercicio 4: [Typography Responsive](./ejercicio-4-typography/)

Sistema tipográfico con clamp().

### Ejercicio 5: [Images Responsive](./ejercicio-5-images/)

Imágenes optimizadas con picture y srcset.

---

## 📚 Recursos

- [MDN - Responsive Design](https://developer.mozilla.org/es/docs/Learn/CSS/CSS_layout/Responsive_Design)
- [Google - Web Fundamentals](https://developers.google.com/web/fundamentals/design-and-ux/responsive)
- [This is Responsive](https://responsivedesign.is/)
- [Am I Responsive?](http://ami.responsivedesign.is/)

---

## ✅ Checklist

Antes de pasar al Módulo 6, asegúrate de:

- [ ] Incluir meta viewport en todas las páginas
- [ ] Entender min-width vs max-width
- [ ] Dominar mobile-first approach
- [ ] Usar unidades relativas (rem, %, vw/vh)
- [ ] Implementar imágenes responsive
- [ ] Crear tipografía fluida con clamp()
- [ ] Probar en múltiples dispositivos
- [ ] Usar DevTools para testing responsive
- [ ] Conocer breakpoints comunes
- [ ] Completar los 5 ejercicios prácticos

---

**Anterior**: [← Módulo 4: Layouts](../modulo-4-layouts/README.md)  
**Siguiente**: [Módulo 6: Frameworks CSS →](../modulo-6-frameworks/README.md)
