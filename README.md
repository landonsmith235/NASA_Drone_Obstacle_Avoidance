![alt text](https://github.com/landonsmith235/NASA_Drone_Obstacle_Avoidance/blob/1307f958e99e8eae1abf26fd522700ed982ab1ab/Images/intro_slide.jpg)

## **Overview**
While the advent of autonomous drone delivery services may seem inevitable when evaluating the pace at which funding is pouring into the development of drone technology, there are still major technological hurdles that need to be conquered to bring automated drone flight mainstream. Among these hurdles, ensuring that a drone can protect the payload it is carrying as well as its own integrity by effectively evading obstacles is the most crucial to solve. In an attempt to reduce the likelihood of drone aviation accidents, NASA’s Resilient Autonomy team worked alongside the DoD and FAA to create a drone obstacle avoidance system called the Expandable Variable Autonomy Architecture, or EVAA. Unfortunately, the occurrence of the Covid-19 pandemic led to the inability of the team to complete flight tests that utilized the technology and caused the project to be discontinued. For the sake of continuity, this project seeks to pick up where NASA’s Resilient Autonomy team left off and create a drone obstacle avoidance database that can be communally utilized by proprietary flight path planning algorithms to enhance aviation safety.

## ** Relevant Repository Contents & Descriptions**
### **NASA Presentation 3-15-2023.pptx**
This file is a Microsoft PowerPoint presentation that was given to two representatives from NASA as well as Saint Mary's College of CA faculty. The presentation provides an overview of the methodologies utilized throughout the project. 

### **Drone Obstacle Avoidance Report.docx**
This file is a report written in Microsoft Word that serves as a more granular explanation of the methodologies discussed in the aforementioned PowerPoint presentation. The report document and PowerPoint presentation slides should serve to guide readers through the entire scope of the project.

### **Datasets Folder**
This folder contains all datasets that are associated with the project. Due to the .ply files being far too large to store on Github, a truncated file titled sample_ply_file.txt has been included to give readers a sense of the structure of a .ply file. In order to to acquire the full-sized .ply files, readers can utilize the [OpenTopography](https://www.google.com](https://opentopography.org/)) website and pull the following datasets using the geographical bounding box minX, minY (-13614349.164060349, 4557303.475503025) & maxX, maxY (-13613408.779604943, 4558076.336715533):

* CA AlamedaCo 2 2021
* USGS LPC CA NoCAL Wildfires B5b 2018
* ARRA-CA SanFranCoast 2010

The files obtained from the OpenTopography website will be point cloud data formatted as .laz files. In order to extract relevant data, we will need to convert these files from .laz to .ply. To accomplish this, we can use [CloudCompare](https://www.danielgm.net/cc/), which is an open source 3D point cloud processing software. Once we are in possession of all three of the .ply files derived from our .laz formatted point cloud data, we can begin to processing our data utilizing a Python script called NASA Data Cleaning.ipynb found in the Code folder in this Github repository. This Python script structures our data in accordance with the needs of this project and outputs the remaining two files found in the Datasests folder, called complete_dataset_with_nulls.csv and interpolated.csv. These datasets are utilized in the creation of our Bayesian Regression Model, as detailed in the report and PowerPoint slides.

### **Code Folder**
The Code folder contains two files, titled NASA Data Cleaning.ipynb and NASA Project Bayesian Model.Rmd. As mentioned in the section devoted to the Datasets Folder, the NASA Data Cleaning.ipynb file is meant to transform our .ply files into data that is applicable to our project goal. Once our data has been transformed into the complete_dataset_with_nulls.csv and interpolated.csv files, we then utilize the file titled NASA Project Bayesian Model.Rmd. This R Markdown file creates our Bayesian Regression model, visualizes our results, and appends the results to a PostgreSQL database as detailed within the report and PowerPoint slides. 
