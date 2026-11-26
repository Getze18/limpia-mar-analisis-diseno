# Diagrama de clases

Clases principales del juego. Se programarán en **Python con pygame**: las clases que se dibujan en pantalla (Aspi, Pez, Basura) heredan de `pygame.sprite.Sprite`.

```mermaid
classDiagram
    class Juego {
        -int nivelActual
        -bool enPausa
        +iniciar() void
        +cambiarNivel(numero: int) void
        +pausar() void
    }
    class Nivel {
        -int numero
        -int tiempoLimite
        -Laberinto laberinto
        +actualizar(dt: float) void
        +estaCompleto() bool
    }
    class Laberinto {
        -list mapa
        -int tamanoCelda
        +esPared(x: int, y: int) bool
        +dibujar(pantalla) void
    }
    class Personaje {
        <<abstract>>
        #int x
        #int y
        #float velocidad
        +mover(laberinto: Laberinto) void
        +dibujar(pantalla) void
    }
    class Aspi {
        -str direccion
        -bool turboActivo
        +leerTeclado(teclas) void
        +aspirar(objeto) void
    }
    class Pez {
        -str especie
        +elegirDireccion() void
        +reaparecer() void
    }
    class Basura {
        -str tipo
        -int puntos
        +recoger() int
    }
    class Marcador {
        -int puntaje
        -int basuraRecogida
        -int pecesAspirados
        +sumar(puntos: int) void
        +restar(puntos: int) void
        +calcularEstrellas() int
    }

    Juego "1" *-- "5" Nivel : contiene
    Nivel "1" *-- "1" Laberinto : usa
    Nivel "1" o-- "1" Aspi : tiene
    Nivel "1" o-- "2..6" Pez : tiene
    Nivel "1" o-- "1..*" Basura : tiene
    Nivel "1" --> "1" Marcador : actualiza
    Personaje <|-- Aspi
    Personaje <|-- Pez
    Aspi ..> Basura : aspira
    Aspi ..> Pez : choca con
```

| Clase | Responsabilidad |
|---|---|
| Juego | Controla el ciclo principal de pygame, el cambio de niveles y la pausa. |
| Nivel | Guarda el tiempo, revisa si ya no queda basura y actualiza todo cada cuadro. |
| Laberinto | Lee el mapa (pasillos y paredes) y dice si una casilla es pared. |
| Personaje | Clase base abstracta con posición y movimiento; la heredan Aspi y Pez. |
| Aspi | La aspiradora del jugador; se mueve con el teclado y aspira lo que toca. |
| Pez | Nada solo por los pasillos; si Aspi lo toca, reaparece en otro lugar. |
| Basura | Objeto que da puntos al recogerse (lata, botella, bolsa, llanta). |
| Marcador | Lleva puntaje, basura recogida y peces aspirados, y calcula las estrellas. |

**Relaciones:** composición (◆) cuando la parte no existe sin el todo (un Nivel y su Laberinto); agregación (◇) cuando los objetos se crean y quitan durante el nivel (peces, basura); herencia (△) de Personaje a Aspi y Pez.
