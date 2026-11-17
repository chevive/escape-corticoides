# Escape room · Laboratorio en cuarentena

Juego para proyectar en la clase de corticoides (Katzung, *Farmacología básica y clínica*, 15.ª ed., cap. 39).
Farmacología · Carrera de Biotecnología · Universidad de las Fuerzas Armadas ESPE (NRC 35101).

- **Proyectar:** https://chevive.github.io/escape-corticoides/
- Versión anterior para celular: https://chevive.github.io/escape-corticoides/celular.html

## Qué es

En la planta de BioCorti S.A. se contaminó un lote de glucocorticoides y las puertas se cerraron. Cada grupo (laboratorio) tiene **6 candados**, uno por sala. El juego se proyecta y lo maneja el docente desde la computadora; los estudiantes no necesitan celular.

## Cómo se juega

1. El docente abre el enlace en la computadora conectada al proyector, elige el número de grupos (2 a 6) y los segundos por pregunta (60 por defecto) y toca **Activar la alarma**.
2. Hay **6 salas**. En cada sala, **cada grupo recibe su propia pregunta**, distinta a la de los demás, en su turno.
3. En su turno, el docente toca **Mostrar pregunta** y corre el tiempo en la pantalla. El grupo responde en voz alta y el docente toca la opción que dijo (o la tecla A, B, C o D).
4. **Acierto:** se abre su candado 🔓 y suma el tiempo que tardó. **Error o tiempo agotado:** el candado queda cerrado ❌ y suma el tiempo completo más 30 s.
5. Cada grupo tiene **2 antídotos 50/50**: eliminan dos opciones incorrectas y suman 15 s.
6. Al final de cada sala se muestra el marcador. Al terminar la sala 6 se muestra el **resultado final**.
7. **Gana el laboratorio con el menor tiempo total.** No se puede ayudar a otro grupo.

El orden de los turnos rota en cada sala (en la sala 1 empieza G1, en la 2 empieza G2, etc.). Después de cada respuesta la pantalla muestra la opción correcta y una explicación corta.

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
- **A, B, C, D:** registra la respuesta del grupo.
- **Antídoto 50/50:** elimina dos opciones incorrectas (máximo 2 por grupo).
- **Pausar** (o Espacio) y **Se acabó el tiempo**.
- **Siguiente turno** (o Enter), **Siguiente sala** y **Reiniciar juego** (pide la clave del docente).
- El avance se guarda en el navegador de la computadora: si se recarga la página, el juego sigue donde estaba.

## Calificación sugerida (sobre 20)

2 puntos por candado abierto (máximo 12), participación y explicación en el cierre (0 a 5) y posición en el ranking por tiempo (1.º 3 · 2.º 2,5 · 3.º 2 · 4.º 1,5 · 5.º 1 · 6.º 0,5).

## Especificaciones técnicas

- **Una sola página:** `index.html` (HTML, CSS y JavaScript juntos), sin servidor ni base de datos; solo carga las fuentes Chakra Petch e Inter de Google Fonts.
- **Publicación:** GitHub Pages desde la rama `main`, carpeta `/(root)`. Cada cambio se publica solo en 1 o 2 minutos.
- **Diseño:** pantalla de proyector (16:9), tema oscuro, marcador de los grupos siempre visible abajo.
- **Estado:** `localStorage`, clave `escape-corti-proj-v2`.
- **Parámetros:** segundos por pregunta (configurable al inicio), penalización por error o tiempo agotado de 30 s (`PEN_FAIL`), costo del antídoto de 15 s (`PEN_ANTI`) y clave para reiniciar (`PIN`).
- **Preguntas:** arreglo `SALAS` en `index.html`. Cada pregunta es `[enunciado, [correcta, distractor, distractor, distractor], explicación]`; la primera opción es la correcta y el juego mezcla el orden al mostrarlas, siempre igual para la misma pregunta.

## Créditos

Docente: MD. Luis Esteban Visarrea Recalde, Mgtr. Contenido basado en Katzung BG, Vanderah TW. *Farmacología básica y clínica*, 15.ª ed., cap. 39 (Adrenocorticosteroides y antagonistas adrenocorticales).
