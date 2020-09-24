```json
{
    "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
    "data": {"url": "data/cars.json"},
    "transform": [{"filter": {"field": "Weight_in_lbs", "lt": 3000}}],
    "mark": "circle",
    "encoding": {
        "x": {"field": "Horsepower", "type": "quantitative"},
        "y": {"field": "Miles_per_Gallon", "type": "quantitative"}
    }
}
```
