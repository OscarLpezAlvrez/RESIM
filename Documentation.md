# RESIM

RESIM is an interactive application that serves as a user-friendly tool. To obtain the expected value of resin production, the user must enter the plot location, dasometric variables, extraction method, and stimulant paste. The entered values are then assigned to a cluster and used to model the resin production based on the assigned model and entered variables.

To implement the models in the web application, the following actions were necessary: 
- Assigning territorial entities
- Cluster assignment model
- Informatic implementation.

## Assigning territorial entities

Territorial entity assignment is necessary for both cluster assignment and production modelling, as it determines the zone of influence for the indicated parcel. The Voronoi polygons were used to establish the zones of influence based on the location of the plots used for modelling. Figure 1 shows these zones. Each location is assigned a zone of influence depending on which polygon it belongs to.

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/02b626a5-29f8-4eb2-b409-947e99843f7e"
    alt="voronoi"
    >
  <figcaption>
    Figure 1. Voronoi polygons of the area of influence of the study. Green area is the distribution range zone of *Pinus pinasteer* delimited by Caudullo et al. (2017).
  </figcaption>
</figure>

## Cluster assignment model

Once the zone of influence has been assigned, it must be determined to which cluster it belongs according to the input variables. To achieve this, an XGBoost algorithm classification model was used, which obtained an accuracy of 90% on the test data. The variables that were most important in the model were analysed using SHAP values, as shown in Figure 2. The figure illustrates that the variables with the greatest impact on the classification model were those related to the extraction methods (MCM and TNM), followed by the dasometric variables (DBH and HT), and to a lesser extent, the location variables and those of the stimulant pastes used (ETH and ASF). The production estimation model is applied to the assigned cluster.

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/f76d7939-595f-4acc-bb9d-0e1b689f9751"
    >
  <figcaption>
    Figure 2. SHAP values of the variables employed in the classification model.
  </figcaption>
</figure>

## Informatic implementation

Figure 3 displays the operating diagram of the web application. After determining the appropriate cluster for the computer data, the application was implemented using a Shiny server based on the R language to create the different models for classification and prediction.

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/27d1716c-4aab-4910-8016-45cb0e6ea134"
    >
  <figcaption>
    Figure 3. Diagram of how the application works.
  </figcaption>
</figure>

------------
    
Figure 4 displays the main page of the application. It includes a viewer for selecting the plot, a selector with methods and pastes, and a box for entering the dasometric data of the trees in the plot. The results can be viewed on screen, printed, or exported to CSV.

<figure>
  <img
    src="https://github.com/OscarLpezAlvrez/RESIM/assets/105171851/dae901b9-7c0e-47b4-baa6-20c0565057e7"
    >
  <figcaption>
    Figure 4. View of the RESIM web application.
  </figcaption>
</figure>

## References

Caudullo, G., Welk, E., & San-Miguel-Ayanz, J. (2017). Chorological maps for the main European woody species. Data in Brief, 12, 662–666. <https://doi.org/10.1016/J.DIB.2017.05.007>

