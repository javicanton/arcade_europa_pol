# EUROPA ARCADE

Juego arcade para estudiar los países y capitales de Europa (2º ESO). Un único archivo (`index.html`), sin dependencias ni compilación.

## Publicar en GitHub Pages

1. Crea un repositorio público (por ejemplo `europa-arcade`) y sube `index.html` a la raíz.
2. En **Settings > Pages**, elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. En un par de minutos estará en `https://TU-USUARIO.github.io/europa-arcade/`.

## Activar el ranking público (opcional)

GitHub Pages solo sirve archivos estáticos, así que sin este paso el ranking se guarda en el navegador de cada alumno. Para un ranking común a toda la clase:

1. En <https://console.firebase.google.com> crea un proyecto y, dentro, una **Realtime Database** (ubicación europea).
2. En la pestaña **Reglas**, pega esto y publica:

```json
{
  "rules": {
    "europa": {
      "scores": {
        ".read": true,
        ".indexOn": ["score"],
        "$id": {
          ".write": "!data.exists()",
          ".validate": "newData.hasChildren(['name','score','ts']) && newData.child('name').isString() && newData.child('name').val().matches(/^[A-Z0-9]{1,3}$/) && newData.child('score').isNumber() && newData.child('score').val() >= 0 && newData.child('score').val() <= 45000 && newData.child('ts').isNumber()"
        }
      }
    }
  }
}
```

3. Copia la URL de la base de datos y pégala en `index.html`, en la constante `RANKING_URL`, añadiendo `/europa` al final:

```js
const RANKING_URL = "https://TU-PROYECTO-default-rtdb.europe-west1.firebasedatabase.app/europa";
```

Notas:

- Solo se guardan 3 iniciales, la puntuación y la fecha (ningún dato personal).
- Las reglas impiden borrar o modificar puntuaciones y limitan el máximo, pero un alumno con conocimientos técnicos podría enviar una puntuación inventada. Para borrar entradas, usa la consola de Firebase.

## Cómo se juega

- 4 niveles de 10 preguntas aleatorias y 5 vidas:
  1. ¿Qué país es? (país parpadeando, 4 opciones)
  2. ¿Cuál es su capital? (4 opciones)
  3. Localiza el país en el mapa
  4. Localiza el país a partir de su capital
- Acierto: 100 puntos + hasta 200 por rapidez + bonus de racha, multiplicado por el nivel (x1 a x4).
- Fallo o tiempo agotado: -50 por nivel y una vida menos.
- Modo **Estudiar el mapa**: toca cualquier país para ver su nombre y capital, sin puntuación.
- Ajustes rápidos en `index.html`: `VIDAS`, `PREGUNTAS` y el tiempo de cada nivel en `LEVELS`.

Incluye 46 países (los 44 de la ONU con capital en Europa, más Chipre y Kosovo). Mapa: Natural Earth (dominio público).
