# forja-stdlib-gui

Módulo GUI nativo para **Forja (fa)**.

Proporciona la API de widgets, layouts y temas Material You para aplicaciones de escritorio usando Xilem.

## Instalación

```fa
importar "gui"
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

### Layouts

- `columna(hijos...)` — Contenedor vertical (flex)
- `fila(hijos...)` — Contenedor horizontal (flex)  
- `pila(hijos...)` — Superposición Z
- `desplazable(hijo)` — Contenedor con scroll
- `grilla(hijos..., filas, columnas)` — Grid

### Widgets básicos

- `etiqueta(texto)`, `texto_grande(texto)`, `texto_mediano(texto)` — Labels
- `boton(texto, callback)` — Botón
- `entrada_texto(variable)` — Input de texto
- `casilla(etiqueta)` — Checkbox
- `deslizante(variable, min, max)` — Slider
- `barra_progreso(valor)` — Progress bar

### Material Design 3

- `boton_relleno`, `boton_tonal`, `boton_perfilado`, `boton_texto`, `boton_elevado`
- `campo_texto`, `campo_perfilado`, `campo_contraseña`
- `tarjeta`, `tarjeta_elevada`, `tarjeta_perfilada`
- `barra_superior`, `barra_navegacion`, `pestañas`
- `dialogo_alerta`, `notificación`, `información`
- Y muchos más (50+ widgets)

### Iconos Material Design

```fa
icono_material("home", 32, "primary")
icono_material("favorite", 24, "error")
icono_material("settings", 48, "#FF5722")
```

Estilos disponibles: `filled`, `outlined`, `rounded`, `sharp`, `twotone`.

## Ejemplo mínimo

```fa
importar "gui"

funcion main() {
    columna(
        texto_grande("Hola desde Forja"),
        boton("Saludar", &saludar)
    )
}

funcion saludar(valor: Texto) -> Texto {
    retornar "¡Hola!"
}
```
