# Mapa měst ČR

Jednoduchá webová mapa v knihovně [Leaflet](https://leafletjs.com/) (v1.9.4), která zobrazuje města ČR z GeoJSONu.

## Struktura

```
index.html     – stránka, načítá Leaflet, styl.css a map.js
map.js         – inicializace mapy, podklad OSM, načtení body.geojson, popupy
styl.css       – vzhled stránky a popupů
body.geojson   – data (body měst)
README.md      – tento soubor
```

## Data

`body.geojson` je `FeatureCollection` bodů (WGS 84, pořadí souřadnic **[lon, lat]**).
Každý prvek má atributy:

| atribut   | typ    | popis                    |
|-----------|--------|--------------------------|
| `id`      | číslo  | jednoznačný identifikátor |
| `nazev`   | text   | název města (popup, tooltip) |
| `popisek` | text   | krátký popis do popupu    |

Další město přidáš novým prvkem do pole `features`:

```json
{
  "type": "Feature",
  "properties": { "id": 3, "nazev": "Brno", "popisek": "Krajské město Jihomoravského kraje." },
  "geometry": { "type": "Point", "coordinates": [16.6068, 49.1951] }
}
```

Výřez mapy se automaticky přizpůsobí všem bodům.

## Spuštění

GeoJSON se načítá přes `fetch()`, proto stránku **nelze otevřít dvojklikem** (`file://` prohlížeč zablokuje). Spusť ji přes lokální server, např.:

```bash
python -m http.server 8000
```

a otevři <http://localhost:8000>. Alternativně VS Code + Live Server, nebo nahrát na webhosting.
