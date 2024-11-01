# Deep Learning Model Report for Alphabet Soup

## Overview of the Analysis
The purpose of this analysis was to build a deep learning model capable of predicting the success of charity funding applications for Alphabet Soup, a hypothetical non-profit. Using historical data on previous funding applications, we created a neural network to classify whether a future application will be successful (1) or not (0). By achieving a high prediction accuracy, this model could help Alphabet Soup allocate funds more effectively and improve the overall success rate of their funded projects.

## Results

### Data Preprocessing

- **Target Variable**:  
  The target variable for our model is `IS_SUCCESSFUL`, which indicates whether a funding application was successful.

- **Feature Variables**:  
  The feature variables include `ASK_AMT`, `APPLICATION_TYPE`, `CLASSIFICATION`, `AFFILIATION`, `USE_CASE`, `ORGANIZATION`, `INCOME_AMT`, and `STATUS`, which were one-hot encoded to allow the neural network to process categorical data effectively.

- **Variables Removed**:  
  The `EIN` and `NAME` columns were removed from the dataset as they serve as unique identifiers and do not contribute meaningful information to the predictive power of the model.

### Compiling, Training, and Evaluating the Model

- **Model Architecture**:  
  The original model was designed with the following architecture:
  - **Input Layer**: The input layer took in a number of features equal to the number of one-hot encoded columns (features) after preprocessing.
  - **Hidden Layers**: We used two hidden layers with 80 and 30 neurons, respectively, and a ReLU activation function for each layer. This architecture was chosen to balance model complexity and computational efficiency.
  - **Output Layer**: A single neuron with a sigmoid activation function was used in the output layer to provide a probability of the application being successful.

- **Model Performance**:  
  The target performance for the model was an accuracy of at least 75%. However, the original model consistently underperformed, reaching accuracy levels below this threshold, even after various optimizations.

- **Improvement Attempts**:
  - **Increased Neurons**: We experimented with increasing the number of neurons in each hidden layer.
  - **Added Dropout Layers**: To reduce overfitting, we added dropout layers with dropout rates between 0.2 and 0.4.
  - **Batch Normalization**: We included batch normalization layers to stabilize learning and improve convergence.
  - **Different Activation Functions**: Various activation functions, including ReLU, ELU, and Swish, were tested across the hidden layers to see if they could improve performance.
  - **Additional Hidden Layers**: We also experimented with deeper architectures, adding up to eight layers with a mix of neuron counts, dropout, and batch normalization.

  Despite these efforts, the model's performance remained below the 75% accuracy target.

### Summary
The deep learning model demonstrated potential but fell short of the target accuracy. The performance may be hindered by the limitations of the neural network architecture or the nature of the data itself. For future attempts, a model change could be beneficial. A recommendation would be to explore ensemble models, such as Random Forest or XGBoost, which are known to perform well on tabular data with categorical features. Ensemble methods could capture complex patterns that the neural network struggled with and may be better suited for this specific classification problem.