# EUROPA ARCADE

Juego arcade para estudiar los países y capitales de Europa y las provincias de España (2º ESO). Un único archivo (`index.html`), sin dependencias ni compilación.

## Cómo se juega

Hay dos modos. **Completo** pregunta por todos los países del mapa (los 46 de siempre más Turquía, Georgia, Armenia y Azerbaiyán). **Básico** pregunta solo por estos 23: Georgia, Armenia, Azerbaiyán, Turquía, Chipre, Macedonia del Norte, Grecia, Bulgaria, Rumanía, Hungría, Moldavia, Albania, Polonia, Rusia, Ucrania, Bielorrusia, Suecia, Noruega, Islandia, Lituania, Letonia, Estonia y Finlandia. El mapa se amplía hacia el este para mostrar Turquía y el Cáucaso en ambos modos y al estudiar.

Dentro de cada modo hay 4 niveles de 10 preguntas aleatorias y 5 vidas:
  1. ¿Qué país es? (país parpadeando, 4 opciones)
  2. ¿Cuál es su capital? (4 opciones)
  3. Localiza el país en el mapa
  4. Localiza el país a partir de su capital
- Acierto: 100 puntos + hasta 200 por rapidez + bonus de racha, multiplicado por el nivel (x1 a x4).
- Fallo o tiempo agotado: -50 por nivel y una vida menos.
- Modo **Estudiar el mapa**: toca cualquier país para ver su nombre y capital, sin puntuación.
- Ajustes rápidos en `index.html`: `VIDAS`, `PREGUNTAS` y el tiempo de cada nivel en `LEVELS`.

El modo completo incluye 50 países (los 44 de la ONU con capital en Europa, más Chipre, Kosovo, Turquía, Georgia, Armenia y Azerbaiyán). Mapa: Natural Earth (dominio público).

El ranking de cada modo se guarda aparte. El completo sigue en `scores` de Firebase; el básico usa `scoresBasic` (mismas reglas de lectura y escritura, con índice en `score`).

## Modo España

Pregunta por las 50 provincias, en 4 niveles con las mismas reglas de puntos y vidas:
  1. ¿Qué provincia es? (4 opciones)
  2. ¿De qué comunidad autónoma es? (4 opciones)
  3. Localiza la provincia en el mapa
  4. Localiza la provincia a partir de su capital

Canarias aparece en un recuadro y las líneas gruesas separan comunidades autónomas. Ceuta y Melilla se dibujan, pero no se preguntan porque no son provincias. **Estudiar España** muestra el nombre, la capital y la comunidad de cada provincia. Para los nombres se usa la forma oficial cuando solo hay una (A Coruña, Ourense, Girona, Lleida, Gipuzkoa, Bizkaia, Illes Balears) y la castellana en las de doble denominación (Álava, Alicante, Castellón, Valencia). Mapa: es-atlas (IGN/CNIG).

El ranking de España se guarda en `scoresEspana` de Firebase. Esa ruta necesita las mismas reglas que `scoresBasic` (lectura y escritura, con índice en `score`); si no se añaden, el ranking de España solo se guarda en cada navegador.
