```json
{
    "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
    "data": {"url": "data/movies.json"},
    "mark": "bar",
    "encoding": {
        "x": {"field": "IMDB Rating", "type": "quantitative", "bin": true},
        "y": {"aggregate": "count", "type": "quantitative"},
        "color": {"aggregate": "sum", "field": "Production Budget",
            "scale": {"type": "log"}
        }
    }
}
```
