*** 

### To Reader: Sorry, Source code of MCIBox is comming ......


# MCIBox
Current Version 1.0. Recent update was on 202206 by Simon Zhongyuan Tian.
### [A. MCI-view](https://github.com/tianzhongyuan/MCI-view)

MCI-view: a multiplex clustering algorithms based browser for single-molecule chromatin interaction visualization.


### [B. MCI-2kde](https://github.com/tianzhongyuan/MCI-view)
MCI-2kde: a two-dimensional kernel density estimation algorithm based unsupervised machine learning method for micro-domains definition automatically.

***

##  A. MCI-view 

***

* MCI-view is a [Shiny Server](https://shiny.rstudio.com) visualization browser for multiplex-chromatin interaction data.
* Data used in MCI-view:[SPRITE](https://linkinghub.elsevier.com/retrieve/pii/S0092867418306366), [GAM](https://www.nature.com/articles/nature21411), [ChIA-Drop and RNAPII CHIA-Drop](http://www.nature.com/articles/s41586-019-0949-1).


<img src="screenshot4wiki/FLOW.png"/> 

### 1. Source Data Preparation

#### 1.1 Create RGN file


* RGN is a file formate that MCI-view required, which includes following columns seprated by TAB:
```
chromsome start end fragment_number complex_id 
```
* RGN file is generated by [ChIA-DropBox](https://github.com/TheJacksonLaboratory/ChIA-DropBox) pipeline, which is a tool to process ChIA-Drop/RNAPII ChIA-Drop data. It also supplies interfaces for SPRITE and GAM generating RGN files and statistic information.

#### 1.2 Split RGN file by chromsome
* RGN file is then splited by chromosomes and compressed to RDS formate (we defined as: "chr2L.SUBRDS.smp"), which is a special data format of R.
* Copy the direrctory (e.g.: M.GAM0001) of these RDS files to the DATA/ folder.
* Tools to convert RGN file to SUBRDS.smp are listed in the MKRDS/ directory.

***

### 2. Installation


#### 2.1 MCI-view Runtime Environment

Current version MCI-view is a [Shiny](https://www.rstudio.com/products/shiny/shiny-server) based web browser launched by [RStudio](https://www.rstudio.com/) in Ubuntu or MacOS circumstances. 

```
OS = macOS Big Sur version 11.4
R = version 4.1.1 (2021-08-10) -- "Kick Things"
RStudio = 2021.09.0 Build 351
Shiny = 1.7.1
```
or
```
OS = Ubuntu 20.04.3 LTS
R = version 3.6.3
RStudio = 2021.09.0+351 Ghost Orchid (desktop)
Shiny = 1.7.1
```

#### 2.2 Install R Package for MCI-view
* When we run MCI-view for the first time, RStudio will ask us to install some R packages, please choose to install all by default.
* The package installation process may require us to restart MCI-view several times, please do so until MCI-view can display the interface.

#### 2.3 Run MCI-view Shiny Browser
```
1. Install RStudio in our local machine according to 2.1
2. Install all packages in you RStudio according to 2.2 
3. In RStudio launching ui.R or server.R in you cloned directory to run MCI-view
```

***

### 3. Start MIC-view and load data

1. Please unzip ZIP files (such as DATA/genome/gene/mm9.gvz.zip) before running MCI-view. 
1. Detail parameter setting see https://github.com/ZhengmzLab/MCIBox/wiki/MCIBox-Manual.
#### Loading Data Source

* After preparing the data source through STEP-1, the directory of the data source needs to be copied to the DATA directory in the MCI-view directory, and then restart the MCI-view program, we can be in the FIN drop-down menu. The newly added data source has been found.

> <img src="screenshot4wiki/SC001-FIN.png"/> 

* Defaultly, the header of each source data represents its species (F=fly; H=human; M=mouse). 
* Change refrence genome, after you changed to a new data of a different species:

<img src="screenshot4wiki/SC002-R-dm3.png"/> 


https://user-images.githubusercontent.com/104511799/175238306-00bbeb72-10a7-4553-b64a-9d56e0cad231.mp4


***


### 4. High Dimension View


<img src="screenshot4wiki/SC003-HD-CLU_v2.png"/> 



https://user-images.githubusercontent.com/104511799/175243109-1f52490c-eef4-484f-aaa3-8e4c5ce2d6a2.mp4

***

### 5. Low Dimension View


<img src="screenshot4wiki/SC005-LD_v2.png"/> 



https://user-images.githubusercontent.com/104511799/175245655-6dcd760d-8204-41ec-a86f-7acad757d7e8.mp4

***


### 6. Views for Accumulated Bin based Data
<img src="screenshot4wiki/SC004-1D2D_v2.png"/> 



https://user-images.githubusercontent.com/104511799/175249851-a8c33ab3-930c-4ba9-ac3f-37660414e322.mp4

***


### 7. Views for Loci Filtering Data

<img src="screenshot4wiki/SC007-loci_v2.png"/> 


https://user-images.githubusercontent.com/104511799/175258599-b0569457-d8c1-41ac-b517-54951dbd64fd.mp4

* Chromatin organization pattern view (CTCF)
* Transcription regulation pattern view (Super-enhancers)
* Target loci view 



https://user-images.githubusercontent.com/88769457/176336651-81686cb2-c939-4bfa-9cce-fa09a950892c.mp4


* Transcription pattern view (RNAPII)
### 8. Operations of gene track and genome region


<img src="screenshot4wiki/SC009-rgn_v2.png"/> 



https://user-images.githubusercontent.com/104511799/175257554-69210a76-4679-4926-92df-898b9090ea5c.mp4

***

### 9. Statistic Information

<img src="screenshot4wiki/STA_INFO.png"/> 


***



### 10 Information of dimensionality reduction and clustering algorithms



<img src="screenshot4wiki/PARA.png"/> 

***
***


## B. MCI-2kde


* MCI-2kde is a two-dimensional kernel density estimation algorithm based unsupervised machine learning method for micro-domains definition automatically.

* Operation Process:
  1. Select __LC-view__ checkBox in the FIN-panel.
  2. Select __Fragment__ and __Cluster__ checkBoxes in the LD-panel.
  3. Select __2kde__ checkBox in the LD-panel.
  4. Then in 2K-Panel, Fragment-views of clusters, with density contour map, and the defined microTF square boundaries.
  5. One could adjust the microTF boundaries by adjusting nlevel range parameters in the __2K__ dropdownList.
  6. Click the __DM_DOWN__ button within  2K-dropdownList, one can save the microTF information.
  7. One can select/unselect checkbox of visulization from the __domain item__ dropdownList
  

<img src="screenshot4wiki/SC006-2kde_v2.png"/> 


https://user-images.githubusercontent.com/104511799/175262302-934e6aba-93f4-40c7-a9b7-7cb1f920b02a.mp4

