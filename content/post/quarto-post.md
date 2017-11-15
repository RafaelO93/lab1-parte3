---
title: "A última sangria em 2011  "
date: 2017-11-13T18:00:09-03:00
draft: false
---
<p> O açude sangrou pela última vez, em 2011, ele teve a melhor fase de sua história. Segundo os dados da Aesa, ele passou 202 dias transbordando água sem parar.</br> 
ele passou 202 dias transbordando água sem parar. A sangria começou no dia 6 de março de 2011 e só parou no dia 22 de setembro desse ano que podemos visualizar pelo gráfico</p>
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
    {"filter": {"field": "DataInformacao", "range":  [{"year": 2011, "month": "jan", "date": 1}, {"year": 2011, "month": "dec", "date":31}] }}
  ],
  "width": 300,
  "heigth": 300,
  "mark": "area",
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
