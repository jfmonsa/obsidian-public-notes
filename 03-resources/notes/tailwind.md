---
mocs:
    - "[[public-notes/03-resources/frontend.moc.md|Frontend]]"
tags:
    - dev/frontend
---

1. Layout y Flexbox

    flex, inline-flex: Iniciar contenedor flex.
    flex-row, flex-col: Dirección del eje principal (fila o columna).
    items-center, items-start, items-end: Alineación vertical en flex.
    justify-center, justify-between, justify-end, justify-start: Alineación horizontal en flex.
    gap-x-4, gap-y-2: Espaciado entre elementos hijos.

2. Espaciado

    p-4, px-2, py-1: Padding (espaciado interno).
    m-4, mx-2, my-1: Margin (espaciado externo).
    Los números indican la escala de Tailwind (entre 0 y 96+, también existen px, 0.5, full, etc.).

3. Tamaño

    w-8, w-full, w-screen: Ancho.
    h-8, h-full, h-screen: Alto.
    min-w-, max-w-, min-h-, max-h-: Tamaños mínimos y máximos.

4. Colores

    bg-blue-500, bg-gray-100: Fondo.
    text-red-600, text-white: Color del texto.
    border-blue-300, border-gray-400: Color de borde.

5. Tipografía

    text-lg, text-sm, text-2xl: Tamaño de fuente.
    font-bold, font-semibold, font-light: Peso de fuente.
    uppercase, lowercase, capitalize: Transformaciones de texto.
    tracking-wide, leading-tight: Espaciado entre letras y líneas.

6. Bordes y Sombra

    rounded, rounded-lg, rounded-full: Bordes redondeados.
    border, border-2, border-t-0: Borde y grosor.
    shadow, shadow-lg, shadow-md: Sombras.

7. Estados y Responsividad

    hover:bg-blue-700, focus:outline-none: Estados interactivos.
    md:p-8, lg:text-xl: Modificadores responsive (sm, md, lg, xl, 2xl).

8. Display y Posicionamiento

    block, inline-block, hidden: Display.
    absolute, relative, fixed, top-0, left-4: Posicionamiento.

9. Otros útiles

    overflow-auto, overflow-hidden: Control de desbordamiento.
    z-10, z-50: Z-index.
    cursor-pointer, select-none: Cursor y selección de texto.
    opacity-50: Opacidad.
    transition, duration-300: Transiciones animadas.

# TIps
1. use cheat sheets
2. use apply for contantent you don't controll like cms or md file
3. automatica class sorting with prettier
4. copy paste things 