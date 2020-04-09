# Data mining illustrated ads with object detection

This work is a compagnon project of the GallicaPix PoC. It has been conducted during the 2019 Helsinki Digital Humanities Hackathon, within the Newspapers and Capitalism [group](https://blogs.helsinki.fi/digital-humanities-hackathon/category/newspapers-and-capitalism/), and thanks to the [NewsEye](https://www.newseye.eu/) European project.

It leverages a dataset of heritage French newspapers illustrated ads built under the [GallicaPix](https://github.com/altomator/Image_Retrieval) umbrella:
- 213 pages, 40k issues
- 63k ads

This [graph](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/Dailies_FR_1910-1920_issues-pages-ads.htm) presents the main characteristics of the dataset.

![Ads dataset statistics](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/ads-dataset.png)

## Object detection
Yolo v3 have been applied to the ads images (see "Face and object detection" section on the Image Retrieval [page](https://github.com/altomator/Image_Retrieval)). Seven "transports" classes are used: bicycle, car, motorbike, aeroplane, train, truck, boat. Yolo v3 generated 17.5k annotations (1.400 on the means of transport classes).

Yolo v3 may have some serious issues on inferencing objects on heritage newspapers ads. Mean recall is around 30% and mean precision 58%. As expected, the best performances are observed on the technical objects that have changed shape the least between 1910 and today, namely bicycles. the airplanes of that era are not recognized at all.

## Human annotations
Consequently, a human annotation campaign has been applied to the whole dataset, in order to fix false positives and false negatives. 3,5k annotations have been produced, using the editing features of the GallicaPix web app.

![GallicaPix editor](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/gp-edition.jpg)

## Analysis








## Analysis






 

