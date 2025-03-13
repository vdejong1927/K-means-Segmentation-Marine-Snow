# K-Means-Segmentation-Marine-Snow
Marine snow, or aggregates of carbon-rich particle that sink from the surface ocean to the seafloor, play an important role in ocean nutrient cycling and are a major mechanism of atmospheric carbon sequestration. Difficult and costly to measure, it is important to understand the rate and magnitude of marine snow transport in order to build accurate models of the global carbon cycle for climate change predictions.


## Segmentation Algorithm
I employed a free, scalable approach to quantify marine snow using semantic segmentation of pre-existing, publicly available digital still marine imagery from the Ocean Observatories Initiative Regional Cabled Array. The camera (CAMDSC102) is located on the Oregon Shelf and is suspended at 200 m depth in the water column with a constant horizontal frame of view and two static lasers pointed out into the open water.

Bicubic rescaling using PIL from was used to compress the images from 5344x4008 to  1024x1024 pixels. Images were preprocessed with CLAHE to improve contrast and HSV conversion which converts pixel RGB values to hue, saturation and values. Finally, superpixels were created using SLIC to reduce computing cost before K-Means clustering was applied. Representative images were segmented and visually analyzed to determine the ideal number of clusters prior to running the algorithm on the entire dataset using this tool by Atticus Carter: https://github.com/AI-Ecology-Lab/K-Means-Segmentation.

![Screenshot 2025-03-12 171610](https://github.com/user-attachments/assets/81a4e8e0-5b05-4dce-90cd-9ee8a0c26e6a)

Five clusters was determined to be optimal because it reliably separated visibly apparent marine snow particles into one cluster distinct from the background and the laser. One cluster each was assigned to "marine snow" and "laser" and the remaining clusters were merged into “background”.



## Model Use-Case #1: Quantifying relative marine snow amount using percent coverage of frame 

### Hypothesis: Percent coverage of marine snow at 195 m depth will be positively correlated with surface water chlorophyll concentration across seasons at the same latitude and longitude. 
K-Means clustering yields percent coverage of a frame over time, which can be used to obtain a relative measurement of marine snow. By comparing this to well-studied and easier to measure ocean properties, a proxy for marine snow using underwater imagery can be obtained.

Use K-Means clustering to obtain percent coverage of a marine imagery with a constant frame of view of marine snow. Obtain chlorophyll concentration measurements of the surface waters at the same time and location. Apply linear regression to determine the relationship between chlorophyll and marine snow at that location. Repeat across different times and sites to see if that relationship is variable temporally or spatially.

![Screenshot 2025-03-12 174242](https://github.com/user-attachments/assets/12cc7982-879c-4105-a957-9c19399cf24a)



## Model Use Case #2: Biofouling detection
### Hypothesis: If percent coverage of laser clusters is determined to be above 5% at any time, the camera is experiencing biofouling.

During investigation into anomalous data while developing use-case #1, I detected biofouling on the camera. Having chosen a random, representative image from the end of the dataset that yielded a clear separation between the desired clusters, I applied the algorithm to the entire set of images and got puzzling results: 

![Screenshot 2025-03-12 204021](https://github.com/user-attachments/assets/8ec866ba-2c68-471e-8d69-84f360f16c7d)

To determine the cause of the high laser values, I analyzed individual images from before and after the data gap preceded by the same representative image used during the initial segmentation to encourage consistent cluster identification patterns. 

![Screenshot 2025-03-12 204121](https://github.com/user-attachments/assets/4e57b572-db72-49ba-a64b-68add4e1a01d)

As RCA maintenance routinely occurs during August, it is likely that the camera was displaying biofouling early in the month and turned off for cleaning during the data gap. Although the source of noise in the frame post-cleaning is unclear, this investigation highlights future use-cases involving instrument maintenance: either of the camera itself or separate, potentially difficult to access, instrumentation that is in its the camera’s frame of view.


## Dataset 
Dataset can be found here: https://huggingface.co/datasets/vdejong/PC01A_Marine_Snow.

This project uses imagery from the Ocean Observatory Initiative Regional Cabled Array (OOI RCA) Slope Base Shallow Profiler (DOI: 10.58046/OOI-RS01SBPS) digital still camera (CAMDSC102). The raw imagery can be accessed via the OOI Raw Data Archive at https://rawdata.oceanobservatories.org/files/RS01SBPS/PC01A/CAMDSC102/
Funding for the OOI RCA is provided by the National Science Foundation (NSF) through a Cooperative Agreement. Any opinions, findings, and conclusions or recommendations expressed in this material are those of the authors and do not necessarily reflect the views of the National Science Foundation.









### this is 3 
 #### this is 4






 **double asterisks**
 this is a big block of normal text hiiiii


 find dataset here: https://huggingface.co/datasets/vdejong/PC01A_Marine_Snow/tree/main/data
 
![Screenshot 2025-03-12 171610](https://github.com/user-attachments/assets/81a4e8e0-5b05-4dce-90cd-9ee8a0c26e6a)
