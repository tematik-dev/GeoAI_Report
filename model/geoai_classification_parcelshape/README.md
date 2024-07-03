# GeoAI Report
## Parcel Shape
![](https://img.shields.io/badge/Task-Classification-gold) ![](https://img.shields.io/badge/Release-V.3.1-blue) ![](https://img.shields.io/badge/Status-Deployed-darkgreen)

> ***Update v.3.1*** <br>
> Increasing model performance (accuracy and processing time)

### Background
<p align=justify> This deep learning model serves the purpose of classifying land parcel shapes based on vector data. Its primary objective is to inform users and consumers about the shape of a desired land parcel. The model categorizes parcels into the following shape types: Irregular, L-shaped, Rectangular, Round, Square, Trapezoid, and Triangular. The practical applications of this classification extend to various stakeholders. For instance: </p>

- Property developers often prefer square or rectangular shapes because of its convenience in calculating area.
- Government entities may prioritize triangular or round parcels for park development in order to increase green open space area and because of the lack of interest by public to develop in those shapes.
- Warehouse managers might find L-shaped parcels suitable for their needs because heavy vehicle can get in from one end and store cargos in the other end. Other than that, L-shaped parcels are usually located near street intersections which might benefit retail shop developers.

<p align=justify> By providing accurate shape classification, this model facilitates informed decision-making in land use and development scenarios. </p>

____

### Description
<p align=justify> As explained in the background section, the shapes classified by the model are: Irregular, L-shaped, Rectangular, Round, Square, Trapezoid, and Triangular. The classification for each shape isn't limited to orderly shape or shape with neat/straight sidelines. Shape with curvy/jagged sides is also classified into these 7 shapes according to the shape similarity and not automatically classified into irregular. Here's the sample images and description for each shape: </p>

![image_shapetable]

| Shape | Description |
| ------ | ------ |
| Irregular | Parcel with uncommon shape based on the mentioned/referenced shapes below |
| L | parcel with shape forming an "L" letter |
| Rectangular | Parcel with shape forming a rectangular shape. This parcel is classified as rectangular if the length of the longer sides are 1.5 longer than the shorter sides |
| Square | Parcel with shape forming a square where each side has similar length. This parcel is classified as square if the length difference between each  sides is less than or equal to 1.5 |
| Trapezoid | Parcel with shape forming a trapezoid |
| Triangular | Parcel with shape forming a triangular shape |
| Round | Parcel with shape forming a round shape |

____

### Model Architecture
<p align=justify> The model is based on ResNet-18 with a little adjustments/customizations on its layers to our needs hence we call it "Custom ResNet-18. The adjustments were performed to address the issue where the model were having a hard time to recognize the image patterns since the image just a plain white/black, so there's no pattern to be recognized directly unlike standard RGB camera images. Here's the original ResNet-18 architecture according to <a href="https://link.springer.com/article/10.1007/s10916-019-1475-2">Ramzan., et al (2019)</a> : </p>

<p align=left>
<img src="https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_resnet18architecture.png" width=90% height=90%>
</p>

____

### Metric
Any GeoAI models are subject to change. Models may differ slightly or entirely from previous versions depending on the needs of ATR/BPN. Please stay updated through this page if you plan to use ATR/BPN thematic data.

<br>

![Image01]

<br>

## Contact
Any request or report can be delivered through our geoportal

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [image_shapetable]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_shapetable.png>
   [image_resnet18architecture]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_resnet18architecture.png>
   [Image01]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/src/Image01.png>
   [Parcel Shape Classification]: <https://github.com/joemccann/dillinger>
   [Tree Species Detection]: <https://github.com/joemccann/dillinger.git>


   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
