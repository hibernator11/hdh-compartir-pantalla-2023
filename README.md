# Uso de Wikidata en bibliotecas
Proyecto presentado en la actividad HDH "Café con" con la Asociación de Humanidades Digitales Hispánicas

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/hibernator11/hdh-cafe-con-2023/HEAD)

[![DOI](https://zenodo.org/badge/620414822.svg)](https://zenodo.org/badge/latestdoi/620414822)

<img src="imagenes/logos.png">

## Introducción

Este proyecto para la actividad [Café con](https://humanidadesdigitaleshispanicas.es/cafe-con-gustavo-candela-4-de-abril-de-2023/) Se introduce Wikidata como plataforma para facilitar el acceso, enriquecimiento y el aumento de la visibilidad a través de la edición de recursos y el uso de SPARQL para recuperar información en forma de datos tabulares y visualizaciones.


## Datos abiertos y enlazados

La Biblioteca Virtual Miguel de Cervantes publicó su catálogo de metadatos como [datos abiertos y enlazados](https://data.cervantesvirtual.com/datos-enlazados) (en inglés, Linked Open Data) utilizando como vocabulario principal [Resource, Description and Access](http://www.rdaregistry.info/). El repositorio se ha enriquecido con [Wikidata](https://www.wikidata.org) a través de diferentes propiedades creadas con el objetivo de enlazar [autores](https://www.wikidata.org/wiki/Property:P2799) y [obras](https://www.wikidata.org/wiki/Property:P3976).

Gracias al enriquecimiento, existe la posibilidad de explorar nuevas formas de acceso al catálogo por medio de nuevas propiedades proporcionadas por Wikidata (p. ej. nacionalidad o movimiento del autor) o visualizaciones basadas en el uso de gráficas y mapas.

<img src="imagenes/buscador.png" width="60%">

## Representación de las nacionalidades de los autores
El siguiente ejemplo muestra las nacionalidades de los autores de Wikidata enlazados a la Biblioteca Virtual Miguel de Cervantes. El siguiente [enlace](https://w.wiki/6WRC) permite ejecutar la siguiente sentencia SPARQL en el editor de consultas de Wikidata.

```
#defaultView:Map
SELECT DISTINCT ?autor ?autorLabel (SAMPLE(?imagen) as ?img) (SAMPLE(?coordenadas) as ?co)
WHERE {   
       ?autor wdt:P2799 ?idbvmc.
       ?autor wdt:P27 ?pais .
       OPTIONAL {?pais wdt:P625 ?coordenadas.}
       OPTIONAL {?autor wdt:P18 ?imagen .}      
    SERVICE wikibase:label { bd:serviceParam wikibase:language "es" }
} GROUP BY ?autor ?autorLabel
```

<img src="imagenes/mapa-autores.png">

## Miembros de la International GLAM Labs Community
La International GLAM Labs Community cuenta con un listado de miembros que se muestran en forma de mapa en su [web](https://glamlabs.io/member-map/). Cada miembro dispone de una entrada en Wikidata que contiene una propiedad ["miembro de"](https://www.wikidata.org/wiki/Property:P463) y con valor el identificador de la International GLAM Labs community [Q72936141](https://www.wikidata.org/wiki/Q72936141). De esta forma se puede obtener como resultado de una sentencia SPARQL un mapa representando a sus miembros.

<img src="imagenes/mapa-glamlabs.png">

## Proyectos basados en Jupyter Notebooks en instituciones GLAM
Las instituciones GLAM han comenzado a utilizar Jupyter Notebooks para reutilizar y documentar el uso de sus colecciones digitales que permiten el acceso computacional. Recientemente, la International GLAM Labs Community creó una nueva sección para este tipo de proyectos disponible en https://glamlabs.io/computational-access-to-digital-collections/. Para cada uno de ellos se creó una instancia en wikidata enlazando a las colecciones que utiliza. Consultar el [siguiente enlace](https://doi.org/10.1002/asi.24835) para más información.

<img src="imagenes/graph-glam-labs-notebooks.png">

## Información adicional

- Gustavo Candela. Towards a semantic approach in GLAM Labs: The case of the Data Foundry at the National Library of Scotland. Journal of Information Science. Just Accepted (2023). https://doi.org/10.1177/01655515231174386
- Gustavo Candela. An automatic data quality approach to assess semantic data from cultural heritage institutions. J. Assoc. Inf. Sci. Technol. 74(7): 866-878 (2023). https://doi.org/10.1002/asi.24761
- Gustavo Candela, Javier Pereda, Dolores Sáez, Pilar Escobar, Alexander Sánchez, Andrés Villa Torres, Albert A. Palacios, Kelly McDonough, and Patricia Murrieta-Flores. 2023. An ontological approach for unlocking the Colonial Archive. J. Comput. Cult. Herit. Just Accepted (April 2023). https://doi.org/10.1145/3594727
- Sally Chambers et al. (2023). Position Statements -> Collections as Data: State of the field and future directions (Version 1). Zenodo. https://doi.org/10.5281/zenodo.7897735
- Candela, G., Chambers,S., & Sherratt, T. (2023). An approach to assess the quality of Jupyter projects published by GLAM institutions. Journal of the Association for Information Science and Technology, 1–15. https://doi.org/10.1002/asi.24835
- [BVMC Labs](https://data.cervantesvirtual.com)
- [Collections as Data](https://collectionsasdata.github.io/)
- [International GLAM Labs Community](https://glamlabs.io/)
- [Impact Centre of Competence](https://www.digitisation.eu/)
- [GLAM Workbench](https://glam-workbench.net/)

## Licencia y términos de uso

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Licencia Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />Esta obra está bajo una <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Licencia Creative Commons Atribución 4.0 Internacional</a>.

## Agradecimientos
Este proyecto es el resultado de varios años de trabajo en el marco de la [Biblioteca Virtual Miguel de Cervantes](https://www.cervantesvirtual.com/), en colaboración con la [International GLAM Labs Community](https://glamlabs.io), [Impact Centre of Competence](https://www.digitisation.eu/), la [Biblioteca Nacional de Escocia](https://data.nls.uk/projects/the-national-librarians-research-fellowship-in-digital-scholarship-2022-23/), la [Universidad de Lancaster](https://unlockingarchives.com), Wikimedia España, Wikimedia UK y numerosos investigadores internacionales de diferentes instituciones de patrimonio cultural y académico.


