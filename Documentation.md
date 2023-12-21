# RESIM

RESIM se trata de una aplicación interactiva que es capaz de servir de herramienta accesible a cualquier usuario. En ella se debe de introducir la localización de una parcela, las variables dasométricas, el método de extracción y la pasta estimulante para obtener el valor esperado de la produción de resina. Una vez se introducen estos valores se le asigna la pertenencia a uno de los cluster y se modeliza la producción en función a las variables introducidas y al modelo asignado.

Para implementar los modelos en la aplicación web fue necesario realizar las siguientes acciones:
- Asignación entidad territorial
- Modelo de asignación de cluster
- Implementación informática

## Asignación entidad territorial

Tanto para la asignación de cluster, asi como para modelizar la producción, es necesario saber a que zona de influencia pertenece la parcela indicada. Para ello se trazó un plano de influencia calculando los polígonos de Voronoi a partir de la localización de las parcelas empleadas para modelizar (Figure 1). Por lo tanto, cada vez que se seleciona una ubiación se le asigna una zona de influencia en función de su pertencia a uno o a otro polígono.

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/02b626a5-29f8-4eb2-b409-947e99843f7e"
    alt="voronoi"
    >
  <figcaption>
    Figure 1. Voronoi polygons of the area of influence of the study. Green area is the distribution range zone of *Pinus pinasteer* delimited by Caudullo et al. (2017).
  </figcaption>
</figure>

## Modelo asignación de cluster

Una vez se asigna la zona de influencia, se debe de establecer a que cluster pertenece de acuerdo a las variables de entrada. Para ello se construyó un modelo de clasificación empleando el algorítmo de machine learning XGBoost, que obtuvo una precisión del 90% en los datos de test. Analizando brevemente las variables que fueron más importantes en el modelo anteriormente mencionado mediante los SHAP values que se encuentran en la Figura 2. En esta figura se puede observar como las variables que más influyen en el modelo de clasificaciónfueron las variables relativas a los métodos de extracción (MCM y TNM), seguidas de las variables dasométricas (DBH y HT) y en menor medida las variables de localización y las de las pastas estimulants empleadas (ETH y ASF). Una vez que se asigna un cluster se le aplica el modelo de estimación de la producción correspondiente.

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/f76d7939-595f-4acc-bb9d-0e1b689f9751"
    >
  <figcaption>
    Figure 2. SHAP values de las variables empleadas en el modelo de clasificación.
  </figcaption>
</figure>

## Implementación informática

En la Figura 3 se pude obserevar el diagrama de funcionamiento de la apliación web. Para construirla se empleó un servidor Shiny basado en el lenguaje de R.

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/27d1716c-4aab-4910-8016-45cb0e6ea134"
    >
  <figcaption>
    Figure 3. Diagrama de funcionamiento de la aplicación.
  </figcaption>
</figure>

En la Figura 4 se puede ver la portada 

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/dae901b9-7c0e-47b4-baa6-20c0565057e7"
    >
  <figcaption>
    Figure 4. Vista de la aplicación RESIM.
  </figcaption>
</figure>

## References

Caudullo, G., Welk, E., & San-Miguel-Ayanz, J. (2017). Chorological maps for the main European woody species. Data in Brief, 12, 662–666. <https://doi.org/10.1016/J.DIB.2017.05.007>

