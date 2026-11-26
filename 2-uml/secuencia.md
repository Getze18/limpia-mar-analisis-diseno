# Diagrama de secuencia: "Limpiar el laberinto"

Escenario principal del juego: el jugador mueve a Aspi, recoge basura y en un momento choca con un pez. Las flechas punteadas son mensajes de retorno.

```mermaid
sequenceDiagram
    autonumber
    actor J as Jugador
    participant N as Nivel
    participant A as Aspi
    participant L as Laberinto
    participant B as Basura
    participant P as Pez
    participant M as Marcador

    J->>A: presiona flecha (dirección)
    A->>L: esPared(x, y)
    L-->>A: false (se puede avanzar)
    A->>A: mover()
    N->>N: revisar choques
    alt Aspi toca basura
        N->>B: recoger()
        B-->>N: puntos (10 o 50)
        N->>M: sumar(puntos)
    else Aspi toca un pez
        N->>M: restar(100)
        N->>P: reaparecer()
        N-->>J: aviso "¡Cuidado con los peces!"
    end
    N->>N: estaCompleto()
    opt Ya no queda basura
        N->>M: calcularEstrellas()
        M-->>N: estrellas (0 a 3)
        N-->>J: muestra pantalla de resultados
    end
```

**Relación con el SRS:** cubre RF-03 (mover a Aspi), RF-04 (recoger basura), RF-05 (penalización por pez) y RF-07 (resultados).
