# ¿Qué hace exitosa una canción?

Segunda pieza de mi portafolio de análisis de datos, con los mismos datos de Spotify de la pieza 1. Pregunta: **¿qué rasgos de audio se relacionan más con la popularidad de una canción?**

## Datos

- Dataset: TidyTuesday **Spotify Songs** (32,833 filas, 23 columnas).
- Después de la limpieza: 32,828 filas; 28,352 canciones distintas (`df_unicas`), que es la base de este análisis para que una canción en varias playlists no pese varias veces.
- `track_popularity` es un puntaje de 0 a 100, no son reproducciones.
- `playlist_genre` es el género de la playlist, no del artista.

## Método

1. Correlación de cada rasgo de audio con `track_popularity`.
2. Comparación del audio promedio del 10% más popular con el 10% menos popular.
3. La correlación repetida dentro de cada género, porque el género puede confundir el resultado.

## Hallazgos

### Correlación con la popularidad

| Rasgo | Correlación |
|---|---|
| energy | -0.104 |
| acousticness | 0.092 |
| danceability | 0.047 |
| loudness | 0.037 |
| valence | 0.023 |
| tempo | 0.004 |

Ningún rasgo de audio por sí solo explica el éxito: todas las correlaciones son débiles (ninguna pasa de 0.10).

### Top 10% vs. bottom 10%

| Rasgo | Top 10% (popularidad ≥ 69, 2,972 canciones) | Bottom 10% (popularidad ≤ 1, 3,162 canciones) |
|---|---|---|
| danceability | 0.67 | 0.64 |
| energy | 0.67 | 0.74 |
| valence | 0.53 | 0.52 |
| tempo | 121.44 | 120.89 |
| acousticness | 0.20 | 0.14 |
| loudness | -6.26 | -6.73 |

Las canciones más populares son un poco más acústicas, menos energéticas y un poco más fuertes. En tempo y valence casi no hay diferencia.

### Por género

El patrón se cumple en los 6 géneros: la energía es negativa en todos (de -0.05 en rock a -0.12 en r&b y rap) y la acousticness es positiva en 5 de 6 (la más alta en edm, 0.16). Ningún género invierte el resultado.

## Conclusión

En Spotify, ningún rasgo de audio predice por sí solo el éxito; las canciones más populares tienden a ser un poco menos energéticas y un poco más acústicas, y eso se cumple en todos los géneros. Correlación no es causa: un rasgo puede acompañar a las canciones populares sin ser la razón de su éxito.

## Herramientas

Python, pandas, NumPy, Kaggle y Tableau.

## Enlaces

- Notebook en Kaggle: https://www.kaggle.com/code/juansernarivera/g-neros-y-playlists-en-spotify
- Dashboard en Tableau Public: https://public.tableau.com/views/GnerosyplaylistsenSpotify/Dashboard1
- Primera pieza del portafolio (Géneros y playlists en Spotify): https://github.com/juanserna-lgtm/generos-playlists-spotify
