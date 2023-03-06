# monarch-life-stages
Using CNN to identify lifestages in images of Monarch butterflies from iNaturalist

## Summary
Monarch butterflies are endangered and likely to go extinct without significant intervention. I have developed a CNN model to extract life stage information from iNaturalist observations so conservation efforts can be focused on Monarch breeding habitat.

## Project Description

### Data Source
iNaturalist uses ML to classify millions of observations of plants, animals, and insects from app users. Most of the observations, however, do not contain information like lifecycle stage, or how many. Images classified as *Danaus plexippus* may be the familiar orange and black adult monarch butterfly, pupae, caterpillars, or even swarms.

On December 26, 2022, 183,263 research grade observations were exported from the [iNaturalist Export Utility](https://www.inaturalist.org/observations/export) [(query)](q=Danaus+plexippus&quality_grade=research&identifications=any&geoprivacy=open&d1=20180101). The exported data includes url links to the images (AWS S3)

[exported data (84.1MB)](https://nextcloud.healyleavitt.com/index.php/s/cAdfwSWLpeWmjY6)

### CNN Model
To extract life stage information from geotagged iNaturalist observations, I developed a [CNN model](https://github.com/chealyleavitt/monarch-life-stages/blob/main/1_inception_model.ipynb). I trained this model with approximately 5,000 iNaturalist observations that I hand categorized as either adult, larva, pupa or egg. For the model itself I took a transfer learning approach and used the pre-trained model Inception V3. I chose to freeze the first 200 layers of the Inception V3 model, and train the remaining layers with my categorized butterfly life stage images. With this approach I was able to achieve 97% validation accuracy.


### Model Application
I then applied the model to all 30,000 Monarch butterfly observations logged on the iNaturalist app in 2019, and used the model output to create plots of lifestage temporal and spatial distribution.
