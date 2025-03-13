# K-means-Segmentation-Marine-Snow
Marine snow, or carbon-rich particles that sink from the surface ocean to the seafloor, play an important role in ocean nutrient cycling and are a major mechanism of atmospheric carbon sequestration. Difficult and costly to measure, it is important to understand the rate and magnitude of marine snow transport in order to build accurate models of the global carbon cycle for climate change predictions.


## Dataset & Segmentation Algorithm
I employed a free, scalable approach to quantify marine snow using semantic segmentation of pre-existing publicly available digital still marine imagery from the Ocean Observatories Initiative Regional Cabled Array, camera CAMDSC102. The camera is located on the Oregon Shelf and is suspended at 200 m depth in the water column with a constant horizontal frame of view and two static lasers pointed out into the open water.

Bicubic rescaling using PIL from was used to compress the images from 5344x4008 to  1024x1024 pixels. Images were preprocessed with CLAHE to improve contrast and HSV conversion which converts pixel RGB values to hue, saturation and values. Finally, superpixels were created using SLIC to reduce computing cost before K-Means clustering was applied. Representative images were segmented and visually analyzed to determine the ideal number of clusters prior to running the algorithm on the entire dataset using this tool by Atticus Carter: https://github.com/AI-Ecology-Lab/K-Means-Segmentation.

![Screenshot 2025-03-12 171610](https://github.com/user-attachments/assets/81a4e8e0-5b05-4dce-90cd-9ee8a0c26e6a)

Five clusters was determined to be optimal because it reliably separated visibly apparent marine snow particles into one cluster distinct from the background and the laser. One cluster each was assigned to "marine snow" and "laser" and the remaining clusters were merged into “background”.


## Model Use-Case #1: Quantifying relative marine snow amount using percent coverage of frame 

### Hypothesis: Percent coverage of marine snow at 195 m depth will be positively correlated with surface water chlorophyll concentration across seasons at the same latitude and longitude. 
K-Means clustering yields percent coverage of a frame over time, which can be used to obtain a relative measurement of marine snow. By comparing this to well-studied and easier to measure ocean properties, a proxy for marine snow using underwater imagery can be obtained.

Use K-Means clustering to obtain percent coverage of a marine imagery with a constant frame of view of marine snow. Obtain chlorophyll concentration measurements of the surface waters at the same time and location. Apply linear regression to determine the relationship between chlorophyll and marine snow at that location. Repeat across different times and sites to see if that relationship is variable temporally or spatially.

![Screenshot 2025-03-12 174242](https://github.com/user-attachments/assets/12cc7982-879c-4105-a957-9c19399cf24a)






### this is 3 
 #### this is 4






 **double asterisks**
 this is a big block of normal text hiiiii


 find dataset here: https://huggingface.co/datasets/vdejong/PC01A_Marine_Snow/tree/main/data
 
![Screenshot 2025-03-12 171610](https://github.com/user-attachments/assets/81a4e8e0-5b05-4dce-90cd-9ee8a0c26e6a)
