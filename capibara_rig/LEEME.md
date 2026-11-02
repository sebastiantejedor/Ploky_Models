# Capibara — rig listo para animar

"izq / der" = lado izquierdo/derecho **visto desde quien mira el dibujo**.
Cada grupo trae `data-pivot="x y"` con el punto de rotación sugerido (viewBox 600 × 720).
El SVG no usa recortes (clipPath), CSS interno ni transformaciones: solo grupos, trazos y rellenos,
para que abra limpio en Illustrator, Inkscape, After Effects, Rive, Figma, etc.

## Archivos
| Archivo | Para qué |
|---|---|
| `Capibara_rig.svg` | Personaje por capas, fondo transparente (el principal) |
| `Capibara_rig_con_fondo.svg` | Igual, con fondo blanco |
| `Capibara_demo_animado.svg` | Demo con CSS (respira, parpadea, mastica, mueve orejas). Ábrelo en el navegador |
| `partes/` | Cada pieza en su propio SVG, mismo lienzo |

## Jerarquía (de atrás hacia adelante)
```
sombra
pierna_izq   pivote 250,575   ├ pierna_izq_forma └ pierna_izq_pie
pierna_der   pivote 350,575   ├ pierna_der_forma └ pierna_der_pie
cuerpo       pivote 300,600   ├ cuerpo_forma     └ cuerpo_barriga
brazo_izq    pivote 190,390   ├ brazo_izq_forma  └ brazo_izq_mano
brazo_der    pivote 410,390   ├ brazo_der_forma  └ brazo_der_mano
cabeza       pivote 300,345
├ mechon        pivote 302,110
├ oreja_izq     pivote 192,134 (interior incluido)
├ oreja_der     pivote 408,134
├ cabeza_forma
├ hocico        pivote 300,290
├ ojo_izq       pivote 222,180 ├ ojo_izq_blanco ├ ojo_izq_pupila (iris + brillo) └ ojo_izq_cerrado (oculto)
├ ojo_der       pivote 378,180 ├ ojo_der_blanco ├ ojo_der_pupila (iris + brillo) └ ojo_der_cerrado (oculto)
├ nariz         pivote 300,247 (brillo + 2 fosas)
└ boca          pivote 300,292 ├ boca_cerrada (sonrisa + dientes) └ boca_abierta (oculta: interior, lengua, dientes)
```

## Trucos de animación
- **Parpadeo:** alterna `ojo_*_blanco` + `ojo_*_pupila` (se ocultan) con `ojo_*_cerrado` (se muestra).
- **Mirar:** mueve `ojo_*_pupila` hasta ±8 px en X y ±10 px en Y y no se sale del ojo.
- **Hablar / masticar:** alterna `boca_cerrada` y `boca_abierta`.
- **Respirar:** escala `cuerpo` (pivote abajo) ~1.01–1.02 en Y.
- Brazos, piernas y cabeza son piezas completas con su propio contorno: giran sin costuras
  (probado con cabeza 9°, brazos hasta 60° y piernas 25°).
- Elementos ocultos (`display="none"`): `ojo_*_cerrado` y `boca_abierta`.
