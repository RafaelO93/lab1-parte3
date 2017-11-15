---
title: "Ano de 2017 e a atual situação"
date: 2017-11-13T17:10:48-03:00
draft: false
---
<p>Após abril o açude passou a receber as águas do Rio São Francisco</p>
<div id="vis" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec = {
   "$schema": "https://vega.github.io/schema/vega-lite/v2.json",
   "data": {
        "url": "https://api.insa.gov.br/reservatorios/12172/monitoramento",
        "format": {
        "type": "json",
        "property": "volumes",
         "parse": {
            "DataInformacao": "utc:'%d/%m/%Y'"
                }
      }
    },
  "transform":[
    {"filter": {"field": "DataInformacao", "range":  [{"year": 2017, "month": "jan", "date": 1}, {"year": 2017, "month": "nov", "date":1}] }}
  ],
  "width": 300,
  "heigth": 300,
  "mark": "point",
  "encoding": {
    "x": {
      "timeUnit": "month",
      "field": "DataInformacao",
      "type": "ordinal",
      "axis": {"title": "Data de registro"}
    },
    "y": {
      "aggregate": "mean",
      "field": "VolumePercentual",
      "type": "quantitative",
      "axis": {"title": "Volume Percentual"}
    }
  }
     };

      vegaEmbed('#vis', spec).catch(console.warn);
</script>
