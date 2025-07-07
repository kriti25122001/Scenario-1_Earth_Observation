🌍 Scenario 1: Earth Observation [25 Marks]
The Ministry of Environment has commissioned an AI-based audit of the Delhi Airshed to identify land use patterns and pollution sources. This project involves building a full spatial pipeline including gridding, land cover classification, and model training.

📦 Provided Datasets
Delhi-NCR Region Shapefile (EPSG:4326)

Sentinel-2 RGB Image Patches

Size: 128×128 pixels

Resolution: 10m/pixel

Format: .png

Each filename maps to its center coordinates (latitude, longitude)

Delhi-Airshed Region Shapefile (EPSG:4326)

ESA WorldCover 2021 Raster (land_cover.tif, 10m resolution)

🧭 Q1: Spatial Reasoning & Data Filtering [5 Marks]
Plot the Delhi-NCR Shapefile using matplotlib and overlay a 60×60 km uniform grid. [1 mark]

Overlay the Grid on a satellite basemap using geemap or leafmap. [1 mark]

Mark Key Points: the four corners and the center of each grid cell. [1 mark]

Filter Images based on whether their center coordinates fall within the grid. [1 mark]

Report Counts: Number of images before and after filtering. [1 mark]

🧱 Q2: Label Construction & Dataset Preparation [10 Marks]
Extract Label Patches: For each image, extract a 128×128 patch from land_cover.tif centered on its coordinate. [2 marks]

Assign Labels: Use the mode (most frequent) land cover class in the patch. [2 marks]

Map ESA Class Codes to 11 standardized labels. [1 mark]

Handle Edge Cases: Discuss handling of no-data pixels or mixed class dominance. [2 marks]

Train-Test Split: Perform a random 60/40 split. [1 mark]

Class Distribution: Visualize and discuss class balance/imbalance. [2 marks]

🧠 Q3: Model Training & Supervised Evaluation [10 Marks]
Train a CNN Classifier (e.g., ResNet18) on the training set. [3 marks]

Evaluate with Custom F1 Score implementation. [2 marks]

Evaluate with torchmetrics.F1Score and compare results. [2 marks]

Display Confusion Matrix and explain insights. [2 marks]

Visualize Predictions: Plot 5 correct and 5 incorrect predictions with images and labels. [1 mark]

ℹ️ Supporting Information
Image Size: 128×128 pixels

Resolution: 10m/pixel (Sentinel-2 RGB)

CRS for Gridding: EPSG:32644

Label Source: ESA WorldCover 2021 (land_cover.tif)

Visualization SDK: Use geemap.Map().add_basemap("SATELLITE")
