# Data mining illustrated ads with object detection

This work is a compagnon project of the [GallicaPix PoC](www.gallicapix.bnf.fr). It has been conducted during the 2019 Helsinki Digital Humanities Hackathon, within the Newspapers and Capitalism [group](https://blogs.helsinki.fi/digital-humanities-hackathon/category/newspapers-and-capitalism/), and thanks to the [NewsEye](https://www.newseye.eu/) European project.

It leverages a dataset of heritage French periodical illustrated ads built under the [GallicaPix](https://github.com/altomator/Image_Retrieval) umbrella.

This [graph](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/Dailies_FR_1910-1920_issues-pages-ads.htm) presents the main characteristics of the dataset:
- 65k illustrated ads data mined in French periodicals (mainly dailies), 
- the periodicals dataset from which these ads have been data mined gathers 36k issues, 265k pages, from 16 daily titles and 15 magazine titles.

![Ads dataset statistics](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/ads-dataset.jpg)
[Illustrated ads dataset](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/Periodical_FR_1910-1920_issues-pages-ads.htm)

## Object detection
Yolo v3 have been applied to the ads images (see "Face and object detection" section on the Image Retrieval [page](https://github.com/altomator/Image_Retrieval). Seven "transports" classes are used: bicycle, car, motorbike, aiplane, train, truck, boat. Yolo v3 generated 17.5k annotations (1,400 on the means of transport classes).

Yolo v3 may have some serious issues on inferencing objects on heritage newspapers ads. Mean recall is around 30% and mean precision 58%. As expected, the best performances are observed on the technical objects that have changed shape the least between 1910 and today, namely bicycles. The airplanes of that era are not recognized at all.

## Human annotations
Consequently, a human annotation campaign has been applied to the whole dataset, in order to fix false positives and false negatives. 6k annotations have been produced, using the editing features of the [GallicaPix](www.gallicapix.bnf.fr) web app.

![GallicaPix editor](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/gp-edition.jpg)

Transfert training of a dedicated CNN model, leveraging this ground truth, might be a good option for a near future.

## Analysis
The following charts mainly show the impact of the WW1 on the economy, through the quantity of ads published, and the evolution of transport techniques. 

![Means of transport vs other ads, per year](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/total-year.jpg)
[Means of transport vs other ads, per year](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/Periodical_FR_1910-1920_ads-year.htm)

![Means of transport illustrated ads, per month](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/total-month.jpg)
Means of transport illustrated ads, per month: [% of published ads per page](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/Periodical_FR_1910-1920_mean-ads-month.htm) and [total of published ads](http://www.euklides.fr/blog/altomator/Image_Retrieval/Ads-data-mining/Periodical_FR_1910-1920_total-ads-month.htm)

For example, the analysis shows that military truck stocks were massively converted to civilian use from 1919 onwards.

The insights that one may learn from these data must be mitigated by the following facts:
- the source dataset may be biased (roughly 30 titles),
- some ads may have been missed, some illustrated ads are actually editorial content,
- most of the analysis is based on object detection, which may be irrelevant in some cases (e.g. advertisements for car spare parts are not taken into account; transport ads may be purely textual)
- some of the means of transport may also be used to illustrate another context, not relevant to this analysis (e.g. sport/leisure/health)












 

