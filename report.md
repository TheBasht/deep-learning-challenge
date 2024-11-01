# Deep Learning Model Report for Alphabet Soup

## Overview of the Analysis
The purpose of this analysis was to build a deep learning model capable of predicting the success of charity funding applications for Alphabet Soup, a hypothetical non-profit. Using historical data on previous funding applications, we created a neural network to classify whether a future application will be successful (1) or not (0). By achieving a high prediction accuracy, this model could help Alphabet Soup allocate funds more effectively and improve the overall success rate of their funded projects.

## Results

### Data Preprocessing

- **Target Variable**:  
  The target variable for our model is `IS_SUCCESSFUL`, which indicates whether a funding application was successful.

- **Feature Variables**:  
  The feature variables include `ASK_AMT`, `APPLICATION_TYPE`, `CLASSIFICATION`, `AFFILIATION`, `ORGANIZATION`, and `INCOME_AMT`, which were one-hot encoded to allow the neural network to process categorical data effectively.

- **Variables Removed**:  
  The columns `EIN`, `NAME`, `STATUS`, `SPECIAL_CONSIDERATIONS`, and `USE_CASE` were removed from the dataset. These columns either served as unique identifiers or were determined to be unnecessary for predictive modeling, as they do not add meaningful information to the model's performance in the optimized version.

### Compiling, Training, and Evaluating the Model

- **Model Architecture**:  
  The original model was designed with the following architecture:
  - **Input Layer**: The input layer took in a number of features equal to the number of one-hot encoded columns (features) after preprocessing.
  - **Hidden Layers**: We used two hidden layers with 80 and 30 neurons, respectively, and a ReLU activation function for each layer. This architecture was chosen to balance model complexity and computational efficiency.
  - **Output Layer**: A single neuron with a sigmoid activation function was used in the output layer to provide a probability of the application being successful.

- **Model Architecture**:  
  The optimized model was designed with the following architecture:
  
  - **Input Layer**: This layer took in a number of features equal to the number of one-hot encoded columns (features) after preprocessing.

  - **Hidden Layers**: We employed an architecture with up to 8 hidden layers to enhance model performance. Each layer had varying numbers of neurons, designed to capture complex relationships in the data:
    - **Layer 1**: 512 neurons with a `swish` activation function, followed by a Dropout of 0.4 for regularization and Batch Normalization.
    - **Layer 2**: 256 neurons with `swish`, Dropout of 0.4, and Batch Normalization.
    - **Layer 3**: 128 neurons with `swish`, Dropout of 0.4, and Batch Normalization.
    - **Layer 4**: 128 neurons with `swish`, Dropout of 0.4, and Batch Normalization.
    - **Layer 5**: 64 neurons with `swish`, Dropout of 0.4, and Batch Normalization.
    - **Layer 6**: 64 neurons with `swish`, Dropout of 0.4, and Batch Normalization.
    - **Layer 7**: 32 neurons with `swish`, Dropout of 0.4, and Batch Normalization.
    - **Layer 8**: 16 neurons with `swish`, Dropout of 0.4, and Batch Normalization.
    
    The `swish` activation function was chosen for all hidden layers to take advantage of its smooth, non-monotonic properties, which have shown to help in training deep networks. This setup was executed with the assistance of a GPU to handle the computational demands efficiently.

  - **Output Layer**: A single neuron with a `sigmoid` activation function was used in the output layer to provide a probability of the application being successful.
  
  - **Early Stopping**: To prevent overfitting, early stopping was implemented, monitoring validation loss with a patience parameter of 10 epochs.
  
  This model was trained with up to 8 hidden layers and optimized using a GPU for faster computation.


  Despite these efforts, the model's performance remained below the 75% accuracy target.

### Summary
The deep learning model demonstrated potential but fell short of the target accuracy. The performance may be hindered by the limitations of the neural network architecture or the nature of the data itself.