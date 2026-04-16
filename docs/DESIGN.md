# DESIGN.md — Sistema de diseño del proyecto

> Este archivo define el lenguaje visual del proyecto.
> El agente @ui-design lo lee automáticamente para generar UI consistente.
>
> OPCIÓN A: Reemplaza este archivo con uno descargado de getdesign.md
> OPCIÓN B: Llena las secciones de abajo para crear tu propio sistema

---

## 1. Identidad visual

**Nombre de marca:** [NOMBRE]
**Descripción del estilo:** [ej: "minimalismo elegante con acento verde", "dark cinematic con toques neón"]
**Personalidad:** [ej: profesional / amigable / técnico / premium / playful]

---

## 2. Paleta de colores

### Colores principales
```
Brand Primary:    #[HEX]   — color principal, CTAs, links activos
Brand Secondary:  #[HEX]   — acento, highlights
Background:       #[HEX]   — fondo base (light)
Background Dark:  #[HEX]   — fondo base (dark)
Foreground:       #[HEX]   — texto principal
Foreground Muted: #[HEX]   — texto secundario
```

### Colores de estado
```
Success:  #[HEX]
Error:    #[HEX]
Warning:  #[HEX]
Info:     #[HEX]
```

### Superficies
```
Surface:        #[HEX]   — cards, paneles
Surface Raised: #[HEX]   — dropdowns, modales
Border:         #[HEX]   — bordes y divisores
```

---

## 3. Tipografía

```
Display / Headings: [Nombre de fuente] — [peso: 700/800]
Body:               [Nombre de fuente] — [peso: 400/500]
Mono:               [Nombre de fuente] — para código

Escala:
  xs:   12px
  sm:   14px
  base: 16px
  lg:   18px
  xl:   20px
  2xl:  24px
  3xl:  30px
  4xl:  36px
  5xl:  48px
```

---

## 4. Espaciado y layout

```
Espaciado base: 4px
Escala: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96

Border radius:
  sm:   [valor]px
  md:   [valor]px
  lg:   [valor]px
  full: 9999px

Contenedor máximo: [valor]px
Columnas de grid:  [número]
```

---

## 5. Sombras

```
sm:  [definición CSS]
md:  [definición CSS]
lg:  [definición CSS]
```

---

## 6. Componentes base

### Botón primario
```
Background: [color]
Text:       [color]
Radius:     [valor]
Padding:    [valor]
Hover:      [efecto]
Font weight:[valor]
```

### Card
```
Background: [color]
Border:     [color y grosor]
Radius:     [valor]
Padding:    [valor]
Shadow:     [valor]
```

### Input
```
Background: [color]
Border:     [color]
Radius:     [valor]
Focus ring: [color]
```

---

## 7. Iconografía

```
Librería:  lucide-react (incluida en shadcn)
Tamaño base: 16px / 20px / 24px
Stroke width: [valor]
```

---

## 8. Animaciones y movimiento

```
Duración base:    [ms]
Easing:           [cubic-bezier o nombre]
Hover transitions: [descripción]
Page transitions:  [descripción]
```

---

## 9. Notas de implementación para el agente

```
- [Cualquier regla específica del diseño que el agente debe respetar]
- [Ej: "Las cards nunca tienen sombra en dark mode"]
- [Ej: "Los botones destructivos siempre son outline, nunca filled"]
- [Ej: "Los headings usan letter-spacing: -0.02em"]
```
