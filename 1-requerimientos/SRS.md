# Especificación de Requerimientos de Software (SRS)

**Proyecto:** Limpia-Mar
**Versión:** 1.0
**Basado en:** IEEE 830-1998 (versión simplificada)
**Autores:** Álvaro Getzemani Hernández Sánchez y Gonzalo David Martínez Medina

---

## 1. Introducción

### 1.1 Propósito
Este documento describe qué debe hacer el videojuego Limpia-Mar. Sirve para que el equipo tenga claro qué construir y para que el docente pueda revisar que cada función se cumpla.

### 1.2 Alcance
Limpia-Mar es un juego 2D de laberinto para computadora, de un solo jugador. Incluye: menú principal, pantalla de instrucciones, 5 niveles, recolección de basura, peces que se mueven por el laberinto, pausa, resultados y tabla de récords. No incluye modo multijugador, juego en línea ni versión para celular.

### 1.3 Glosario

| Término | Significado |
|---|---|
| Aspi | La aspiradora submarina que controla el jugador. |
| Laberinto | El mapa del nivel: pasillos de agua separados por rocas y coral. |
| Basura | Objetos que hay que aspirar: botellas, latas, bolsas y llantas. |
| Pez | Animal que nada por el laberinto; no se debe aspirar. |
| Puntaje | Puntos que el jugador acumula en el nivel. |
| Penalización | Puntos que se restan al aspirar un pez. |
| Turbo | Objeto especial que da más velocidad a Aspi por 5 segundos. |
| Estrellas | Calificación de 0 a 3 al terminar un nivel. |

## 2. Descripción general

### 2.1 Usuarios
| Usuario | Descripción |
|---|---|
| Jugador | Persona de 8 años en adelante que usa teclado. No necesita experiencia previa en videojuegos. |

### 2.2 Restricciones
- El juego se desarrolla en Python con la biblioteca pygame.
- Debe correr en Windows 10 o superior.
- El equipo es de 2 personas y el tiempo es de un semestre.
- Todo el texto del juego está en español.

### 2.3 Supuestos
- La computadora del jugador tiene teclado y una pantalla de al menos 1280×720.
- No se necesita internet para jugar.
- Se entrega un ejecutable para que no haya que instalar Python.

## 3. Requerimientos

### 3.1 Requerimientos funcionales

| ID | RF-01 |
|---|---|
| **Título** | Menú principal |
| **Descripción** | El sistema debe mostrar un menú con las opciones Jugar, Cómo jugar, Récords y Salir. |
| **Prioridad** | Alta |
| **Criterio de aceptación** | Al abrir el juego aparece el menú y cada opción lleva a su pantalla. |

| ID | RF-02 |
|---|---|
| **Título** | Seleccionar nivel |
| **Descripción** | El sistema debe mostrar los 5 niveles y permitir jugar solo los desbloqueados. El nivel 1 está desbloqueado desde el inicio. |
| **Prioridad** | Alta |
| **Criterio de aceptación** | Un nivel bloqueado muestra un candado y no se abre; al ganar un nivel se desbloquea el siguiente. |

| ID | RF-03 |
|---|---|
| **Título** | Mover a Aspi por el laberinto |
| **Descripción** | El jugador debe mover a Aspi con las flechas o con W, A, S, D. Aspi no puede atravesar las paredes del laberinto. |
| **Prioridad** | Alta |
| **Criterio de aceptación** | Al presionar una dirección Aspi avanza por el pasillo; al chocar con una pared se detiene. |

| ID | RF-04 |
|---|---|
| **Título** | Recoger basura |
| **Descripción** | Cuando Aspi pasa sobre una basura, el sistema debe quitarla del mapa y sumar puntos: 10 por basura chica (lata, botella) y 50 por basura grande (llanta). |
| **Prioridad** | Alta |
| **Criterio de aceptación** | Al pasar sobre una lata el marcador sube 10 puntos y la lata desaparece. |

| ID | RF-05 |
|---|---|
| **Título** | Penalización por aspirar un pez |
| **Descripción** | Si Aspi toca un pez, el sistema debe restar 100 puntos, mostrar el aviso "¡Cuidado con los peces!" y soltar al pez en otro pasillo. El puntaje nunca baja de 0. |
| **Prioridad** | Alta |
| **Criterio de aceptación** | Con 150 puntos, al tocar un pez el marcador baja a 50 y aparece el aviso. |

| ID | RF-06 |
|---|---|
| **Título** | Movimiento de los peces |
| **Descripción** | Los peces deben nadar solos por los pasillos y cambiar de dirección en los cruces. Cada nivel tiene más peces que el anterior (2 en el nivel 1, 6 en el nivel 5). |
| **Prioridad** | Alta |
| **Criterio de aceptación** | Durante el nivel los peces se mueven sin atravesar paredes y el número de peces coincide con el nivel. |

| ID | RF-07 |
|---|---|
| **Título** | Terminar nivel y mostrar resultados |
| **Descripción** | El nivel termina cuando se recoge toda la basura (gana) o se acaba el tiempo (pierde). El sistema muestra basura recogida, peces aspirados, puntaje y de 0 a 3 estrellas. |
| **Prioridad** | Alta |
| **Criterio de aceptación** | Al recoger la última basura aparece la pantalla de resultados con los 4 datos correctos. |

| ID | RF-08 |
|---|---|
| **Título** | Pausar el juego |
| **Descripción** | Al presionar Esc el juego se detiene y muestra las opciones Continuar, Reiniciar nivel y Salir al menú. |
| **Prioridad** | Media |
| **Criterio de aceptación** | En pausa el tiempo y los peces se detienen; al continuar siguen desde donde estaban. |

| ID | RF-09 |
|---|---|
| **Título** | Guardar y consultar récords |
| **Descripción** | El sistema debe guardar el mejor puntaje de cada nivel en un archivo local y mostrarlo en la pantalla de Récords. |
| **Prioridad** | Media |
| **Criterio de aceptación** | Después de cerrar y volver a abrir el juego, el récord sigue apareciendo. |

### 3.2 Requerimientos no funcionales

| ID | RNF-01 |
|---|---|
| **Título** | Rendimiento |
| **Descripción** | El juego debe correr a 60 cuadros por segundo con 6 peces en pantalla. |
| **Prioridad** | Alta |
| **Criterio de aceptación** | Con el contador de FPS, no baja de 55 en una computadora con 4 GB de RAM. |

| ID | RNF-02 |
|---|---|
| **Título** | Facilidad de uso |
| **Descripción** | Un jugador nuevo debe entender cómo jugar con la pantalla "Cómo jugar", sin ayuda de otra persona. |
| **Prioridad** | Alta |
| **Criterio de aceptación** | 4 de 5 personas que prueban el juego recogen su primera basura en menos de 30 segundos. |

| ID | RNF-03 |
|---|---|
| **Título** | Portabilidad |
| **Descripción** | El ejecutable debe abrir en Windows 10 y 11 sin instalar nada extra. |
| **Prioridad** | Media |
| **Criterio de aceptación** | El ejecutable abre en dos computadoras distintas, una con Windows 10 y otra con Windows 11. |

| ID | RNF-04 |
|---|---|
| **Título** | Tiempo de carga |
| **Descripción** | El juego debe pasar del menú a un nivel en menos de 3 segundos. |
| **Prioridad** | Baja |
| **Criterio de aceptación** | Medido con cronómetro en 3 intentos, ninguno pasa de 3 segundos. |

### 3.3 Revisión de calidad

Cada requerimiento se revisó con este checklist:

| ID | Correcto | No ambiguo | Completo | Consistente | Factible | Verificable |
|---|:-:|:-:|:-:|:-:|:-:|:-:|
| RF-01 a RF-09 | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| RNF-01 a RNF-04 | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
