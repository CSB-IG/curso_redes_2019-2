Medidas de redes
================

## Cytoscape

Calcular medidas de redes en Cytoscape es muy sencillo utilizando la
herramienta NetworkAnalyzer.

Simplemente hay que entrar a Tools \> NetworkAnalyzer \> Analyze Network
… Un cuadro de diálogo preguntará si se trata de una red dirigida o no
dirigida. Al aceptar, todos los parámetros calculables de la red
aparecerán ya sea en las tablas de la parte inferior, o en el panel de
resultados

## Igraph - R

Para analizar las propiedades de la red, se usan funciones sobre un
objeto de red igraph.

``` r
library(igraph)
```

    ## 
    ## Attaching package: 'igraph'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     decompose, spectrum

    ## The following object is masked from 'package:base':
    ## 
    ##     union

``` r
g <- igraph::graph.famous("Zachary")

sp <- shortest.paths(g) #calcula caminos mas cortos
```

``` r
degree(g) #calcula el grado
```

    ##  [1] 16  9 10  6  3  4  4  4  5  2  3  1  2  5  2  2  2  2  2  3  2  2  2
    ## [24]  5  3  3  2  4  3  4  4  6 12 17

``` r
betweenness(g) #calcula betweenness centrality
```

    ##  [1] 231.0714286  28.4785714  75.8507937   6.2880952   0.3333333
    ##  [6]  15.8333333  15.8333333   0.0000000  29.5293651   0.4476190
    ## [11]   0.3333333   0.0000000   0.0000000  24.2158730   0.0000000
    ## [16]   0.0000000   0.0000000   0.0000000   0.0000000  17.1468254
    ## [21]   0.0000000   0.0000000   0.0000000   9.3000000   1.1666667
    ## [26]   2.0277778   0.0000000  11.7920635   0.9476190   1.5428571
    ## [31]   7.6095238  73.0095238  76.6904762 160.5515873

``` r
transitivity(g, type = "local") #calcula clustering coefficient local
```

    ##  [1] 0.1500000 0.3333333 0.2444444 0.6666667 0.6666667 0.5000000 0.5000000
    ##  [8] 1.0000000 0.5000000 0.0000000 0.6666667       NaN 1.0000000 0.6000000
    ## [15] 1.0000000 1.0000000 1.0000000 1.0000000 1.0000000 0.3333333 1.0000000
    ## [22] 1.0000000 1.0000000 0.4000000 0.3333333 0.3333333 1.0000000 0.1666667
    ## [29] 0.3333333 0.6666667 0.5000000 0.2000000 0.1969697 0.1102941

Aquellos parámetros de nodos o aristas que se calculan se pueden agregar
como información de estos al objeto de red

``` r
V(g) #accede a los nodos
```

    ## + 34/34 vertices, from 7da26a9:
    ##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
    ## [24] 24 25 26 27 28 29 30 31 32 33 34

``` r
V(g)$grado <- degree(g) #define una nueva propiedad, grado
```

## NetworkX - Python

``` r
import matplotlib.pyplot as plt
import networkx as nx

G = nx.karate_club_graph()

nx.degree_centrality(G) #grado
nx.betweenness_centrality(G) #betweenness
nx.clustering(G) #clustering coefficient
nx.shortest_path_length(G) #shortest paths
```
