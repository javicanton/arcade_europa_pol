# EUROPA ARCADE

Juego arcade para estudiar los países y capitales de Europa (2º ESO). Un único archivo (`index.html`), sin dependencias ni compilación.

## Cómo se juega

Hay dos modos. **Completo** pregunta por los 46 países de siempre. **Básico** pregunta solo por estos 23: Georgia, Armenia, Azerbaiyán, Turquía, Chipre, Macedonia del Norte, Grecia, Bulgaria, Rumanía, Hungría, Moldavia, Albania, Polonia, Rusia, Ucrania, Bielorrusia, Suecia, Noruega, Islandia, Lituania, Letonia, Estonia y Finlandia. En el básico el mapa se amplía hacia el este para incluir Turquía y el Cáucaso; al volver al completo, el mapa queda como antes.

Dentro de cada modo hay 4 niveles de 10 preguntas aleatorias y 5 vidas:
  1. ¿Qué país es? (país parpadeando, 4 opciones)
  2. ¿Cuál es su capital? (4 opciones)
  3. Localiza el país en el mapa
  4. Localiza el país a partir de su capital
- Acierto: 100 puntos + hasta 200 por rapidez + bonus de racha, multiplicado por el nivel (x1 a x4).
- Fallo o tiempo agotado: -50 por nivel y una vida menos.
- Modo **Estudiar el mapa**: toca cualquier país para ver su nombre y capital, sin puntuación.
- Ajustes rápidos en `index.html`: `VIDAS`, `PREGUNTAS` y el tiempo de cada nivel en `LEVELS`.

El modo completo incluye 46 países (los 44 de la ONU con capital en Europa, más Chipre y Kosovo). El básico añade Turquía, Georgia, Armenia y Azerbaiyán, que no entran en las preguntas del completo. Mapa: Natural Earth (dominio público).

El ranking de cada modo se guarda aparte. El completo sigue en `scores` de Firebase; el básico usa `scoresBasic` (mismas reglas de lectura y escritura, con índice en `score`).
