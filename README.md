# Historical-Building-Recognition-System
This historical building recognition system can perform classification of the historical buildings in Malacca, Malaysia. The model is trained with images of three historical buildings, namely Stadhuys, St Paul Church, and  A'Famosa. The images are taken from different angles and at different times of a day.

# Data description
The input data for this project are 3 historical buildings in Malacca, which consist of A'Famosa, Stadhuys, and St. Paul Church. The pictures are taken at multiple angle, day, time and weather. The pictures are taken once per week and at 3 different times to capture the different variations of lighting and weather for 3 weeks.

| A'Famosa | Stadhuys | St Paul Church |
|----------|----------|----------------|
| ![AFamosa](/Flowcharts/1_1.jpg?raw=true)       | ![Stadhuys](/Flowcharts/2_3.jpg?raw=true)        | ![StPaul](/Flowcharts/3_29.jpg?raw=true)              | 

# Experiment setup
The total number of pictures collected is 162, each building consists of 54 pictures. The pictures are cropped to extract the area of interest and then resized to 100x100. All 162 cropped and resized pictures are then separated to training and testing set at 114 and 48 respectively.

# Description of design & implementation
### Preprocessing
![flowchart1](/Flowcharts/flowchart1.png?raw=true)
1. Classify the images collected from Week 1 to Week 3 into 3 folders, which are A Famosa, Stadhuys and St Paul Church.
2. Rename all of the images, with the prefix 1 representing A Famosa, 2 representing Stadhuys and 3 representing St Paul Church. We used a program called Bulk Rename Utility to rename all of the images with their respective prefixes.
3. Crop the ROI using a program called BatchCrop and resized it to 100 * 100 pixels.
4. Put all of the resized images into a folder called Data.

### Import images
![flowchart2](/Flowcharts/flowchart2.png?raw=true)
1. Import all of the images from the ‘Data’ folder and they will be converted using a for loop in the program. All of the data will be kept in an array.
2. Convert the array into a numpy array so that we can see the shape of it.
3. Reshape the numpy array into (162,10000).
4. Save the reshaped numpy array into image.txt.

### Feature extraction using PCA
![flowchart3](/Flowcharts/flowchart3.png?raw=true)
1. Load the images and labels from ‘image.txt’ and ‘label.txt’ respectively.
2. Split the data into training and testing set. Set the random state as 42 to make sure the splitting is always the same everytime the program is run.
3. Extract the top 50 eigenfaces from the dataset.
4. Project the input data on the eigenface orthonormal basis.
5. Observe the intraclass and interclass distance. Intraclass distance is the distance between two points in the same class. Interclass distance is the distance between two points in different classes.

### Classification
![flowchart4](/Flowcharts/flowchart4.png?raw=true)
1. Use StandardScaler to scale the data.
2. Apply transformation to data.
3. Create a model (NN, SVC, KNN) with 3 hidden layers. Fit the training data to the model to train the model.
4. Observe the classification report and confusion matrix. The accuracy is stated in the classification report.

# Authors
Joey Lim, Y.F.,Tan.

# Others
This project is made for my `TPR 2251 Pattern Recognition` subject. The original program of this assignment is modified and updated.
