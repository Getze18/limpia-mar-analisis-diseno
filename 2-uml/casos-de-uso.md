# Diagrama de casos de uso

**Actores**
- **Jugador:** la persona que juega.
- **Sistema de récords:** actor secundario que guarda los mejores puntajes en un archivo.

**Relaciones**
- «include»: *Jugar nivel* siempre incluye *Mover a Aspi* y *Recoger basura*.
- «extend»: *Recibir penalización* extiende a *Mover a Aspi* solo cuando Aspi toca un pez.
- «extend»: *Pausar juego* extiende a *Jugar nivel* solo si el jugador presiona Esc.

```mermaid
flowchart LR
    Jugador["🎮 Jugador"]
    Records["💾 Sistema de récords"]

    subgraph Sistema["Sistema: Limpia-Mar"]
        CU1(["Ver menú principal"])
        CU2(["Ver cómo jugar"])
        CU3(["Seleccionar nivel"])
        CU4(["Jugar nivel"])
        CU5(["Mover a Aspi"])
        CU6(["Recoger basura"])
        CU7(["Recibir penalización por pez"])
        CU8(["Pausar juego"])
        CU9(["Ver resultados"])
        CU10(["Consultar récords"])
    end

    Jugador --- CU1
    Jugador --- CU2
    Jugador --- CU3
    Jugador --- CU4
    Jugador --- CU10
    CU4 -.->|"«include»"| CU5
    CU4 -.->|"«include»"| CU6
    CU7 -.->|"«extend»"| CU5
    CU8 -.->|"«extend»"| CU4
    CU4 --- CU9
    CU9 --- Records
    CU10 --- Records
```

| Caso de uso | Descripción |
|---|---|
| Ver menú principal | Pantalla con Jugar, Cómo jugar, Récords y Salir. |
| Ver cómo jugar | Explica los controles, qué da puntos y qué los quita. |
| Seleccionar nivel | Elige uno de los niveles desbloqueados. |
| Jugar nivel | Partida en un laberinto con tiempo límite. |
| Mover a Aspi | Mueve la aspiradora con flechas o W, A, S, D. |
| Recoger basura | Aspi aspira la basura y suma puntos. |
| Recibir penalización por pez | Si Aspi toca un pez, se restan 100 puntos. |
| Pausar juego | Detiene el nivel con Esc. |
| Ver resultados | Muestra puntaje, basura recogida, peces aspirados y estrellas. |
| Consultar récords | Muestra el mejor puntaje de cada nivel. |
