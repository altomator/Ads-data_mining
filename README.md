# Data mining newspapers illustrated ads with object detection

This work is a compagnon project of the [GallicaPix PoC](https://gallicapix.bnf.fr/). It has been conducted during the 2019 Helsinki Digital Humanities Hackathon, within the Newspapers and Capitalism [group](https://blogs.helsinki.fi/digital-humanities-hackathon/category/newspapers-and-capitalism/), and thanks to the [NewsEye](https://www.newseye.eu/) European project.

It leverages a dataset of heritage French periodical illustrated ads built under the [GallicaPix](https://github.com/altomator/Image_Retrieval) umbrella.

This graph presents the main characteristics of the dataset:
- 1910-1920 time period,
- 65k illustrated ads data mined in French periodicals (mainly dailies), 
- the periodicals dataset from which these ads have been data mined gathers 36k issues, 265k pages, from 16 daily titles and 15 magazine titles.

Note: another dataset is also available ([Vogue magazine](https://gallica.bnf.fr/ark:/12148/cb343833568/date), French edition, 1920-1940)

![Ads dataset statistics](https://github.com/altomator/Ads-data_mining/blob/master/EN_charts/ads-dataset.jpg)
[Illustrated ads dataset](https://altomator.github.io/Ads-data_mining/EN_charts/Periodical_FR_1910-1920_issues-pages-ads.htm)

## Object detection
Yolo v3 have been applied to the ads images (see "Face and object detection" section on the Image Retrieval [page](https://github.com/altomator/Image_Retrieval)). Seven "transports" classes are used: bicycle, car, motorbike, aiplane, train, truck, boat. Yolo v3 generated 17.5k annotations (1,400 on the means of transport classes).

Yolo v3 may have some serious issues on inferencing objects on heritage newspapers ads. Mean recall is around 30% and mean precision 58%. As expected, the best performances are observed on the technical objects that have changed shape the least between 1910 and today, namely bicycles. The airplanes of that era are not recognized at all.

![Airplane example](https://github.com/altomator/Ads-data_mining/blob/master/ads/airplanes/airplane4.jpg)

## Human annotations
Consequently, a human annotation campaign has been applied to the whole dataset, in order to fix false positives and false negatives. 6k annotations have been produced, using the editing features of the [GallicaPix](https://gallicapix.bnf.fr/) web app.


## Trained models 
Transfert training of a dedicated CNN model, leveraging this ground truth, might be a good option. A simple model of 3 classes, 15 images per class, trained with IBM Watson Visual Recognition (*discontinued on 1 December 2021*), gives good results on test images taken from newspapers not used in the training set.

Inferencing the dataset images can then be done with a cURL command (or with any scripting language):

`curl -X POST -u "apikey:{apikey}" --form "images_file=@ftest_image.jpg" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19& classifier_ids=DefaultCustomModel_1457318034"`


## Analysis
The following charts mainly show the impact of the WW1 on the economy, through the quantity of ads published, and the evolution of transport techniques. 


[Means of transport vs other ads, per year](https://altomator.github.io/Ads-data_mining/EN_charts/Periodical_FR_1910-1920_ads-year.htm)

Means of transport illustrated ads, per month: [% of published ads per page](https://altomator.github.io/Ads-data_mining/EN_charts/Periodical_FR_1910-1920_mean-ads-month.htm) and [total of published ads](https://altomator.github.io/Ads-data_mining/EN_charts/Periodical_FR_1910-1920_total-ads-month.htm)

For example, the analysis shows that military truck stocks were massively converted to civilian use from 1919 onwards.

The insights that one may learn from these data must be mitigated by the following facts:
- the source dataset may be biased (roughly 30 titles),
- some ads may have been missed, some illustrated ads are actually editorial content,
- most of the analysis is based on object detection, which may be irrelevant in some cases (e.g. advertisements for car spare parts are not taken into account; transport ads may be purely textual)
- some of the means of transport may also be used to illustrate another context, not relevant to this analysis (e.g. sport/leisure/health)












 

