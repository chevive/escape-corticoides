# Escape room · Laboratorio en cuarentena

Juego para la clase de corticoides (Katzung, *Farmacología básica y clínica*, 15.ª ed., cap. 39).
Farmacología · Carrera de Biotecnología · Universidad de las Fuerzas Armadas ESPE (NRC 35101).

- **Jugar:** https://chevive.github.io/escape-corticoides/
- **Proyector (cuenta regresiva de 75 min):** https://chevive.github.io/escape-corticoides/#proyector

## Qué es

En la planta de BioCorti S.A. se contaminó un lote de glucocorticoides y el sistema de seguridad cerró todas las puertas. Cada grupo (laboratorio) debe abrir 7 salas con lo que sabe del cap. 39 para salir antes que los demás. Cada sala se abre con un código que sale del capítulo.

## Cómo se juega (estudiantes)

1. Abran el enlace en **un celular por grupo**.
2. Elijan su laboratorio (G1 a G6) y toquen **Entrar al laboratorio**. Empieza el cronómetro.
3. Lean la sala, resuelvan las preguntas, escriban el código y toquen **Abrir**.
4. Si el código es correcto, se abre la sala siguiente. Si es incorrecto, quedan **1 minuto en cuarentena** sin poder intentar.
5. Tienen **2 antídotos**: cada uno muestra la pista de la sala en la que están y resta 0,5 puntos.
6. Al abrir la sala 7 aparece **¡Escaparon!** con el tiempo total y el de cada sala. Muestren esa pantalla al docente.

**Reglas**

- Pueden usar el libro, sus apuntes y las diapositivas de la clase. Internet no.
- En cada sala presenta el código un integrante distinto; el docente puede preguntarle por qué.
- No cambien de celular: el avance se guarda en el navegador de ese celular. Si recargan la página, no se pierde.

## Las 7 salas

| Sala | Nombre | Tema del cap. 39 | Formato del código |
| --- | --- | --- | --- |
| 1 | La fábrica | Zonas de la corteza suprarrenal, colesterol y regulación de la aldosterona | 3 dígitos |
| 2 | El reloj | Eje CRH–ACTH–cortisol, ritmo circadiano y transporte del cortisol en la sangre | 3 dígitos |
| 3 | La llave y el núcleo | Mecanismo de acción: receptor citoplasmático, hsp90, núcleo y GRE | 5 letras en orden |
| 4 | La balanza | Dosis equivalentes entre prednisona, metilprednisolona, dexametasona e hidrocortisona | 6 cifras |
| 5 | Las enzimas | 11β-HSD tipo 1 y tipo 2, profármacos y hepatopatía | 3 dígitos |
| 6 | El precio | Efectos adversos, supresión del eje, retiro y dosis de estrés | 3 dígitos |
| 7 | La salida | Antagonistas e inhibidores (metirapona, mifepristona, espironolactona, ketoconazol) y prueba de supresión con dexametasona | 5 dígitos |

## Cómo usarlo en clase (docente)

| Hora | Momento | Qué pasa |
| --- | --- | --- |
| 09:00–09:10 | Alarma | Historia y reglas; el proyector muestra la cuenta regresiva. |
| 09:10–10:25 | Escape | Los grupos abren las 7 salas en el celular. |
| 10:25–10:45 | Desactivación | Cada grupo explica en 2 minutos una sala; el docente explica la 7. |
| 10:45–10:55 | Pase de salida | Tres preguntas individuales en papel. |
| 10:55–11:00 | Podio | Orden de salida y nota. |

- **Proyector:** abrir el enlace con `#proyector` y tocar **Iniciar**. Tiene botones para pausar y reiniciar; se pone rojo en los últimos 5 minutos.
- **Reiniciar un celular:** enlace «Reiniciar (solo docente)» al pie de la página, con la clave del docente.
- **Calificación sugerida (sobre 20):** 2 puntos por sala abierta (máximo 14), explicación de su sala de 0 a 3, orden de salida (1.º 3 · 2.º 2,5 · 3.º 2 · 4.º 1,5 · 5.º 1 · 6.º 0,5) y −0,5 por antídoto.
- Los códigos, las pistas y las respuestas están en la clave del docente, que no se publica.

## Especificaciones técnicas

- **Una sola página:** `index.html`, con HTML, CSS y JavaScript juntos. No necesita servidor, base de datos ni librerías; solo carga las fuentes Chakra Petch e Inter de Google Fonts.
- **Publicación:** GitHub Pages desde la rama `main`, carpeta `/(root)`. Cada cambio en `index.html` se publica solo en 1 o 2 minutos.
- **Diseño:** pensado para celular (unos 390 px de ancho), tema oscuro de «laboratorio en cuarentena».
- **Vistas:** inicio (elección de grupo), sala, final y proyector (`#proyector`). Ventanas: cuarentena, sala desbloqueada, antídoto, reglas y reinicio.
- **Estado:** se guarda en el `localStorage` de cada navegador, con la clave `escape-corti-v1`: grupo, hora de inicio, sala actual, hora de apertura de cada sala, antídotos usados y fin de la cuarentena. El proyector usa la clave `escape-corti-proj`. No hay marcador compartido entre celulares.
- **Códigos:** no están escritos en la página. Se guarda solo el hash FNV-1a de 32 bits del texto `corti|<número de sala de 0 a 6>|<CÓDIGO>`. El código se normaliza antes de compararlo: mayúsculas, sin espacios, sin guiones y sin otros símbolos.
- **Parámetros:** cuarentena de 60 s (`QUAR`), 2 antídotos por grupo, cuenta regresiva de 75 min (`TOTAL`) y clave del docente para reiniciar (`PIN`).

## Cómo modificar una sala

1. Abra `index.html` y busque el arreglo `ROOMS`. Cada sala tiene:
   - `t`: título.
   - `b`: texto de la sala con sus preguntas (`Q('A', 'pregunta', ['opción 1', 'opción 2', …])`).
   - `fmt`: formato del código que ve el estudiante.
   - `len`: largo del código.
   - `hint`: pista del antídoto.
   - `h`: hash del código correcto.
2. Para un código nuevo, calcule su hash en la consola del navegador (F12), cambiando el número de sala (0 a 6) y el código:

   ```js
   const fnv = s => { let h = 0x811c9dc5; for (const x of new TextEncoder().encode(s)) { h ^= x; h = Math.imul(h, 0x01000193) >>> 0; } return h >>> 0; };
   fnv('corti|0|TUCODIGO');
   ```

3. Ponga el número que sale en `h`, guarde el cambio en GitHub (commit) y espere 1 o 2 minutos.

## Créditos

Docente: MD. Luis Esteban Visarrea Recalde, Mgtr. Contenido basado en Katzung BG, Vanderah TW. *Farmacología básica y clínica*, 15.ª ed., cap. 39 (Adrenocorticosteroides y antagonistas adrenocorticales).
