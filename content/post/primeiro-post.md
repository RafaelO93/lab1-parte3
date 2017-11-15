---
title: "Visualização geral de 1990-2017"
date: 2017-11-15T18:00:09-03:00
draft: false
---
<p>Uma visualização geral indo do ano de 1990 até 2017 mostrando o percentual por ano.</p>
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
  "mark": "bar",
  "encoding": {
    "x": {
      "timeUnit": "year",
      "field": "DataInformacao",
      "type": "ordinal",
      "axis": {"title": "Ano do registro"}
    },
    "y": {
      "aggregate": "mean",
      "field": "VolumePercentual",
      "type": "quantitative",
      "axis": {"title": "Volume Percentual de água"}
    }
  }
     };

      vegaEmbed('#vis', spec).catch(console.warn);
</script>
