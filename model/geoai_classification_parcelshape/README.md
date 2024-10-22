# GeoAI Report
## Parcel Shape
![](https://img.shields.io/badge/Task-Classification-gold) ![](https://img.shields.io/badge/Data-Vector-white) ![](https://img.shields.io/badge/Release-V.3.1-blue) ![](https://img.shields.io/badge/Status-Deployed-darkgreen)

> ***Update V.3.1*** <br>
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

<p align=center>
<img src="https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_resnet18architecture.png" width=90% height=90%>
</p>

____

### Performance
<p align=justify> This is the 3rd model (Version 3.1) of parcel shape classifier. The previous classifiers (V.1 and V.2) were made using the same major backbone, ResNet, but they were using different layer numbers and configuration. The first generation was using default ResNet-50, while the second generation was using default ResNet-18. Since major improvement in terms of efficiency was obtained, customization was carried out on ResNet-18 to enhance the model and create the third generation (Custom ResNet-18). The history of our model's performances are shown below. (Note: Inference speed was tested on Central Jakarta City land parcel). </p>

<p align=center>
   <img src="https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_metriceachversion.png" width=80% height=80%>
</p>

<p align=justify> The images show that V.3.1 outperforms other models in terms of accuracy and efficiency (inference speed). The confusion matrix and per-class accuracy (producer and user accuracy) of model V.3.1 are shown below. </p> 

<div align=center>
<img src="https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_confmatrix.png" width=60% height=60%>

| Metric | Irregular | L | Rectangular | Square | Trapezoid | Triangular | Round |
| ------ | ------ | ------ | ------ | ------ | ------ | ------ | ------ |
| Producer's Accuracy | 0.86 | 0.92 | 0.96 | 1.00 | 0.87 | 0.97 | 1.00 |
| Users's Accuracy | 0.92 | 0.95 | 0.90 | 0.97 | 0.91 | 0.94 | 1.00 |

</div>

____

### Output
<p align=justify> The obtained information from parcel shape thematic data is the shape iteself and confidence score in the form of fields in vector data. Here are the sample images </p>

| Shape | Confidence |
| ------ | ------ |
| ![image_exampshape] | ![image_exampconfid] |

____

### Short Explanation
<p align=justify> Through our inspection, we've found some misclassified shapes (ofc, since we can't get 100% accuracy). Most of the known misclassified shapes are L shape which is reflected in the confusion matrix. This happens because some of the irregular shapes have similar appearances like the ones in L shape. For example, some irregular shapes are T-shaped which kind of similar to L shape. These two almost have identical overall appearance, but the main difference is just an extra stripe in T shape. Because of this, these two are misclassified interchangeably. However, we can still get over this problem by looking at the confidence level. The misclassified shapes are having lower confidence value compared to other shapes with correct classification. Here are the examples: </p>

<p align=center>
   <img src="https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_compareclassconf.png" width=60% height=60%>
</p>



[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [image_shapetable]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_shapetable.png>
   [image_resnet18architecture]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_resnet18architecture.png>
   [image_metriceachversion]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_metriceachversion.png>
   [image_confmatrix]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_confmatrix.png>
   [image_exampshape]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_exampshape.png>
   [image_exampconfid]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_exampconfid.png>
   [image_compareclassconf]: <https://github.com/tematik-dev/GeoAI_Report/blob/main/model/geoai_classification_parcelshape/src/image_compareclassconf.png>
