---
title: "De olho em Boqueirão com d3+SVG "
date: 2017-11-28T09:34:05-03:00
draft: false
---

<script src="https://d3js.org/d3.v4.min.js"></script>

<div class="container">
    <div class="row">
      <h2>Visualização Boqueirão com d3</h2>
    </div>
    <div class="row mychart" id="chart">
    </div>
  </div>

<script type="text/javascript">
    "use strict"
    var alturaSVG = 500,
        larguraSVG = 1750;
    function desenhaVis(dados) {
          var grafico = d3.select('#chart') // cria elemento <svg> com um <g> dentro
                            .append('svg')
                              .attr('width', larguraSVG)
                              .attr('height', alturaSVG);
           var grupo = grafico.selectAll('g')
                   .data(dados)
                   .enter()
                   .append('g');
         grupo.append('circle')
            .attr("cx", function(d) { return (d.mes) * 125; })
            .attr("cy", 250)
            .attr("r", function(d) { return d.noventa_percentil * 0.60; })
            .style("fill", "goldenrod");
          grupo.append('circle')
             .attr("cx", function(d) { return (d.mes) * 125; })
             .attr("cy", 250)
             .attr("r", function(d) { return d.dez_percentil; })
             .style("fill", "steelblue");
        grupo.append('text')
             .text(function(d){
                return d.mes;
             })
             .attr("x", function(d) { return (d.mes) * 125 - 8; }) //Localização de onde o número ficará na barrano eixo X
             .attr("y", 250);
    }
    d3.csv('../dados/boqueirao-por-mes.csv', function(dados) {
      desenhaVis(dados);
    });
 </script>

</div>
