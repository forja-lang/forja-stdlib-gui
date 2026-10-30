# forja-stdlib-gui

Módulo GUI nativo para **Forja (fa)**.

Proporciona la API de widgets, layouts y temas Material You para aplicaciones de escritorio usando Xilem.

## Instalación

```fa
importar gui
```

Requiere compilar Forja con el feature `gui`:

```bash
cargo build --features gui
```

## Módulos incluidos

| Archivo | Descripción |
|---|---|
| `gui.fa` | API completa: layouts, widgets, botones, inputs, navegación, iconos Material Design |

## Funciones principales

### Diseños predeterminados

Dos estilos listos para usar, cada uno en claro y oscuro. Envolvé el layout raíz:

| Función | Modo | Estilo |
|---|---|---|
| `tema_fluent(hijo)` | Claro | Fluent (Windows 11): fondo Mica, acento `#005FB8`, esquinas 4-8px |
| `tema_fluent_oscuro(hijo)` | Oscuro | Fondo `#202020`, acento `#4CC2FF` |
| `tema_liquid_glass(hijo)` | Claro | Liquid Glass: superficies vidriosas, acento `#007AFF`, esquinas 20-32px |
| `tema_liquid_glass_oscuro(hijo)` | Oscuro | Fondo `#0A0C10`, acento `#0A84FF` |

Alias: `tema_windows11`, `tema_vidrio` y variantes `_oscuro`. Para un tema
Material You desde un color semilla: `tema_material("#FF5722", hijo)`.

### Layouts

- `columna(hijos...)` — Contenedor vertical (flex)
- `columna_con_gap(hijos, gap, alineacion)` — Columna con separación
- `columna_centrada(hijos...)` — Columna centrada horizontalmente
- `fila(hijos...)` — Contenedor horizontal (flex)
- `fila_con_gap(hijos, gap, alineacion)` — Fila con separación
- `pila(hijos...)` — Superposición Z
- `desplazable(hijo)` — Contenedor con scroll
- `grilla(hijos, columnas, gap)` — Grid responsivo: las columnas se reparten el ancho
  disponible (se adaptan al resize) y cada fila mide lo que mide su contenido
  (autosize). En pantallas angostas baja a 2 o 1 columna sola.
- `flujo(hijos, gap)` — Flow con salto de línea automático
- `contenedor(hijo, ancho_maximo)` — Ancho máximo
- `relleno(hijo, px)`, `expansor(hijo)`, `centrado(hijo)`
- `adaptable(compacto, medio, expandido)` — Tres variantes según el ancho
- `caja_fija(hijo, ancho, alto)`, `caja_relativa(hijo, ratio)`

### Widgets básicos

- `etiqueta(texto)`, `titulo(texto)`, `texto_grande(texto)`, `texto_mediano(texto)` — Labels
- `boton(texto, callback)` — Botón
- `entrada_texto(variable)` — Input de texto
- `casilla(etiqueta, variable)` — Checkbox
- `deslizante(variable, min, max)` — Slider
- `barra_progreso(variable)` — Progress bar

### Navegación

- `navegador(pantallas, var_actual, tipo, &cb)` — Pantallas con navegación;
  tipo: `barra()`, `riel()`, `cajon()` o `"pestañas"`; animación: `fade()`, `slide()`
- `pantalla(id, titulo, contenido, icono)` — Una pantalla del navegador
- `item_navegacion(icono, etiqueta)` — Ítem de la barra/riel
- `barra_superior(titulo, acciones)`, `barra_inferior(acciones)`
- `barra_navegacion`, `riel_navegacion`, `cajon_navegacion`, `pestañas`
- `migaja_de_pan(items)`, `asistente_pasos(pasos, actual, &cb)`

### Material Design 3

- `boton_relleno`, `boton_tonal`, `boton_perfilado`, `boton_texto`, `boton_elevado`
- `campo_texto`, `campo_perfilado`, `campo_contraseña`
- `tarjeta`, `tarjeta_elevada`, `tarjeta_perfilada`
- `dialogo_alerta`, `notificación`, `información`
- Y muchos más (200+ widgets) — ver el catálogo completo en la documentación

### Iconos Material Design

Los iconos son paths SVG reales (dibujados con Vello), no emojis: toman el color
del tema y se ven bien en cualquier tamaño y DPI.

```fa
icono_material("home", 32, "primary")
icono_material("favorite", 24, "error")
icono_material("settings", 48, "#FF5722")
```

Estilos disponibles: `filled`, `outlined`, `rounded`, `sharp`, `twotone`.

## Ejemplo mínimo

```fa
importar gui

funcion main() {
    tema_fluent(
        columna(
            titulo("Hola desde Forja"),
            boton("Saludar", &saludar)
        )
    )
}

funcion saludar(valor: Texto) -> Texto {
    retornar "¡Hola!"
}
```
