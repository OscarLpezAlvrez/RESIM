# RESIM

RESIM se trata de una aplicación interactiva, en la que el usuario debe de introducir la localización de su parcela, las variables dasométricas, el método de extracción y la pasta estimulante. Una vez que el usuario introduce estos valores se le asigna la pertenencia a uno de los cluster y se modeliza la producción en función a las variables introducidas y al modelo asignado.

Para implementar los modelos en la aplicación web que es capaz de servir de herramienta accesible a cualquier usuario fue necesario realizar las siguientes acciones:
- Asignación entidad territorial
- Modelo de asignación de cluster
- Implementación informática

## Asignación entidad territorial

Tanto para asignar a que cluster pertenece la parcela asignada, asi como para modelizar la producción, es necesario asignar una zona de influencia a la parcela indicada. Para ello se trazó un plano de influencia calculando los polígonos de Voronoi a partir de las parcelas empleadas para modelizar (#voronoi). Por lo tanto, cada vez que se seleciona una ubiación se le asigna una zona de influencia en función de su pertencia a uno o a otro polígono.

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/02b626a5-29f8-4eb2-b409-947e99843f7e"
    alt="voronoi"
    >
  <figcaption>
    Voronoi polygons of the area of influence of the study. Green area is the distribution range zone delimited by Caudullo et al. (2017).
  </figcaption>
</figure>

## Modelo asignación de cluster

Una vez se asigna la zona de influencia a la que pertence la parcela, se debe de establecer a que cluster pertenece de acuerdo a las variables de entrada. Para ello se ajustó un modelo de asignación. Para construir este modelo se empleó el algorítmo de machine learning XGBoost, que consiguió una precisión del 90%. Una vz que se asigna un cluster 

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/f76d7939-595f-4acc-bb9d-0e1b689f9751"
    >
  <figcaption>
    SHAP values de las variables empleadas en el modelo de clasificación.
  </figcaption>
</figure>

## Implementación informática


![esquema](https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/27d1716c-4aab-4910-8016-45cb0e6ea134)


![aplicacion](https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/dae901b9-7c0e-47b4-baa6-20c0565057e7)


## References

Caudullo, G., Welk, E., & San-Miguel-Ayanz, J. (2017). Chorological maps for the main European woody species. Data in Brief, 12, 662–666. <https://doi.org/10.1016/J.DIB.2017.05.007>

