Scenario-1 : Earth Observation [25 Marks]
The Ministry of Environment has commissioned an AI-based audit of the Delhi Airshed to identify land use patterns and pollution sources. You are provided the following datasets:
Shapefile of the Delhi-NCR region (EPSG:4326) [File]
Sentinel-2 RGB image patches (128×128 pixels, 10m/pixel resolution), with each image filename mapped to its center coordinates (latitude, longitude) in .png format. [File]
Shapefile of the Delhi-Airshed region (EPSG:4326) [File]
A land_cover.tif raster (ESA WorldCover 2021, 10m resolution) [File]
Your goal is to build a full pipeline involving spatial gridding, land cover classification.
Q1. Spatial Reasoning & Data Filtering [5 Marks]
Plot the Delhi-NCR shapefile using matplotlib and overlay a 60×60 km uniform grid (1 marks)
Overlay this grid on a satellite basemap using geemap or leafmap (1 mark)
Mark the four corners and the center of each grid cell (1 mark)
Filter images based on whether their center coordinates fall within the grid (1 mark)
Count and report the number of images before and after filtering (1 mark)
Q2. Label Construction & Dataset Preparation [10 Marks]
For each image, extract a 128×128 patch from the land_cover.tif centered at the image's coordinate (2 marks)
Assign a label using the mode (most frequent) land cover class in the patch (2 marks)
Map ESA class codes to 11 standardized labels (1 mark)
Handle edge cases and discuss treatment of no-data pixels or mixed class dominance (2 marks)
Perform a 60/40 train-test split randomly (1 mark)
Visualize class distribution and discuss balance (or imbalance) (2 marks)
Q3. Model Training & Supervised Evaluation [10 Marks]
Train a CNN classifier (e.g., ResNet18) on the training set (3 marks)
Evaluate using a custom F1 score implementation (2 marks)
Evaluate using torchmetrics.F1Score and compare results (2 marks)
Show and explain a confusion matrix (2 marks)
Plot 5 correct and 5 incorrect predictions with images and labels (1 mark)
Supporting Information
Image Size: 128×128 pixels
Resolution: 10m/pixel (Sentinel-2 RGB)
CRS for Gridding: EPSG:32644
Label Source: ESA WorldCover 2021 (land_cover.tif, 10m resolution)
VLM Candidates: BLIP (Salesforce), OFA (Microsoft), GIT (Google)
Visualization SDK: Use geemap.Map().add_basemap("SATELLITE")
Label Assignment Logic: Each image’s label is derived from the mode value in the corresponding 128×128 label patch extracted from land_cover.tif, centered on its coordinate. For instance:
8000 pixels = class 50 (Built-up)
3000 pixels = class 40 (Cropland)
512 pixels = class 10 (Tree cover)
The assigned label would be Built-up (50), as it is the dominant class.
