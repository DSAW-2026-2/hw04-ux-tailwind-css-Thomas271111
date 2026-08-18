# Bitácora de IA — HW04 (UX + Tailwind)

## ¿Usé IA para generar clases de Tailwind y para los wireframes?

Sí, usé Claude para reconstruir todo `index.html` y `about.html` con clases de utilidad de Tailwind, partiendo del diseño que ya teníamos en CSS normal de HW03 (mismo contenido, misma estructura semántica, solo cambiando cómo se aplican los estilos). No usé IA para los wireframes de Figma — esos los hice yo directamente en la herramienta.

## Paleta de colores: qué sugirió la IA y qué cambié

La IA mantuvo la paleta que ya habíamos definido en HW03 en vez de proponer una nueva desde cero (verde `#3f6b3f` como color principal, navy `#2f4a5c` como acento, fondo crema `#faf8f4`, texto `#2b2b26`), porque ya la habíamos ajustado juntos hace unas tareas y no tenía sentido reinventarla. Lo que sí tuve que decidir yo fue la paleta del **modo oscuro**, que no existía antes: la IA propuso usar directamente los grises por defecto de Tailwind (`gray-900` para el fondo, `gray-100` para el texto, `gray-800` para las tarjetas) en vez de intentar oscurecer manualmente los mismos tonos verdes/crema de la versión clara. Lo dejé así porque usar la escala de grises estándar de Tailwind es mucho más simple de mantener consistente en todos los componentes que estar calculando manualmente una versión oscura de cada color custom que ya tenía — y para el acento en modo oscuro sí pedí que usara un azul claro (`sky-400`) en vez del navy oscuro original, porque el navy casi no se distingue sobre un fondo `gray-900`.

## Qué aprendí de Tailwind que no habría aprendido si la IA hiciera todo

Lo que más me costó entender (y que tuve que preguntarle a la IA para que me explicara, no solo para que lo generara) fue cómo funciona el prefijo `dark:` — al principio pensé que Tailwind detectaba el modo oscuro del sistema operativo automáticamente y ya, pero en realidad por defecto Tailwind v4 sí hace eso (`prefers-color-scheme`), y para que el botón de la página controle el modo manualmente (y no solo el sistema operativo del usuario), hay que decirle explícitamente a Tailwind que el modo oscuro depende de una clase (`.dark`) en el `<html>`, y ser yo quien le agregue o quite esa clase con JavaScript. Sin entender eso, habría asumido que con solo escribir clases `dark:` ya tenía un botón funcional, y no habría entendido por qué el toggle no cambiaba nada la primera vez que lo probé.

También aprendí que Tailwind permite selectores "raros" como `:target` (el que uso para el acordeón de FAQ) usando la sintaxis de variante arbitraria `[&:target]:block` — no es algo que viene documentado como una clase con nombre propio (`target:block`), hay que saber que se puede envolver cualquier selector CSS válido entre corchetes.