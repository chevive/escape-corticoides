# Escape room · Laboratorio en cuarentena

Juego para proyectar en la clase de corticoides (Katzung, *Farmacología básica y clínica*, 15.ª ed., cap. 39).
Farmacología · Carrera de Biotecnología · Universidad de las Fuerzas Armadas ESPE (NRC 35101).

- **Proyectar:** https://chevive.github.io/escape-corticoides/
- Versión anterior para celular: https://chevive.github.io/escape-corticoides/celular.html

## Qué es

En la planta de BioCorti S.A. se contaminó un lote de glucocorticoides y las puertas se cerraron. Cada grupo (laboratorio) tiene **6 candados**, uno por sala. El juego se proyecta y lo maneja el docente desde la computadora; los estudiantes no necesitan celular.

## Cómo se juega

1. El docente abre el enlace en la computadora conectada al proyector, elige el número de grupos (2 a 6) y los minutos por grupo (15 por defecto) y toca **Activar la alarma**.
2. **Cada grupo tiene 15 minutos en total.** Su reloj corre solo durante su turno, como en el ajedrez; el tiempo que no usa lo conserva para las salas siguientes.
3. Hay **6 salas**. En cada sala, **cada grupo recibe su propia pregunta**, distinta a la de los demás, en su turno.
4. En su turno, el docente toca **Mostrar pregunta** y corre el reloj del grupo. El grupo responde en voz alta y el docente toca la opción que dijo (o la tecla A, B, C o D).
5. Cada grupo tiene **2 intentos** por pregunta. Si acierta, abre su candado 🔓 y gana **3,33 puntos** (20 ÷ 6).
6. Si falla los 2 intentos o **se le acaban sus 15 minutos**, **queda fuera del juego** y conserva los puntos que ya tenía. En las salas siguientes se salta su turno.
7. **No hay ayudas** y no se puede ayudar a otro grupo.
8. **Nota sobre 20:** abrir los 6 candados = 20/20. El empate se decide por el menor tiempo usado.

El orden de los turnos rota en cada sala (en la sala 1 empieza G1, en la 2 empieza G2, etc.). La opción correcta y su explicación aparecen solo cuando el grupo acierta o queda fuera.

| Candados abiertos | Nota / 20 |
| --- | --- |
| 6 | 20,00 |
| 5 | 16,67 |
| 4 | 13,33 |
| 3 | 10,00 |
| 2 | 6,67 |
| 1 | 3,33 |
| 0 | 0,00 |

## Las 6 salas (6 preguntas distintas en cada una, 36 en total)

| Sala | Nombre | Tema del cap. 39 |
| --- | --- | --- |
| 1 | La fábrica y el reloj | Zonas de la corteza, colesterol, eje CRH–ACTH–cortisol, ritmo circadiano y transporte |
| 2 | La llave y el núcleo | Receptor citoplasmático, hsp90, GRE, transactivación y transrepresión |
| 3 | Los efectos | Efectos metabólicos, sobre la sangre, antiinflamatorios y sobre grasa y músculo |
| 4 | La balanza y las enzimas | Potencias y dosis equivalentes, duración, efecto mineralocorticoide y 11β-HSD 1 y 2 |
| 5 | El precio | Efectos adversos, supresión del eje, retiro, dosis de estrés e infecciones |
| 6 | La salida | Addison, metirapona, mifepristona, espironolactona, prueba de supresión con dexametasona y maduración pulmonar fetal |

## Controles del docente

- **Mostrar pregunta** (o Enter): muestra la pregunta del grupo en turno y arranca el tiempo.
- **A, B, C, D:** registra la respuesta del grupo. Si es incorrecta y le queda un intento, su reloj sigue corriendo.
- **Pausar** (o Espacio): detiene el reloj del grupo en turno.
- **Siguiente** (o Enter), **Siguiente sala** y **Reiniciar juego** (pide la clave del docente).
- El avance se guarda en el navegador de la computadora: si se recarga la página, el juego sigue donde estaba.

## Especificaciones técnicas

- **Una sola página:** `index.html` (HTML, CSS y JavaScript juntos), sin servidor ni base de datos; solo carga las fuentes Chakra Petch e Inter de Google Fonts.
- **Publicación:** GitHub Pages desde la rama `main`, carpeta `/(root)`. Cada cambio se publica solo en 1 o 2 minutos.
- **Diseño:** pantalla de proyector (16:9), tema oscuro, marcador de los grupos siempre visible abajo.
- **Estado:** `localStorage`, clave `escape-corti-proj-v4`.
- **Parámetros:** minutos por grupo (15, configurable al inicio), intentos por pregunta (`TRIES` = 2), puntos por candado (20 ÷ número de salas) y clave para reiniciar (`PIN`).
- **Preguntas:** arreglo `SALAS` en `index.html`. Cada pregunta es `[enunciado, [correcta, distractor, distractor, distractor], explicación]`; la primera opción es la correcta y el juego mezcla el orden al mostrarlas, siempre igual para la misma pregunta.

## Créditos

Docente: MD. Luis Esteban Visarrea Recalde, Mgtr. Contenido basado en Katzung BG, Vanderah TW. *Farmacología básica y clínica*, 15.ª ed., cap. 39 (Adrenocorticosteroides y antagonistas adrenocorticales).
