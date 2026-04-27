# Backblaze-panne-disques-durs
Predict hard drive failures using a hybrid CNN-LSTM model based on SMART time series data.


Dataset

•
Source: Likely Backblaze Hard Drive Data (common for this TP).

•
Features: SMART attributes.

•
Labels: 0 for normal, 1 for failure/imminent failure.

Key Steps

1.
Data Preprocessing:

•
Filter normal and failing disks.

•
Handle temporal gaps (fix_date_gaps).

•
Generate sequences of fixed length (sequence_length).

•
Label sequences: 0 for normal, 1 for sequences preceding a failure (lookahead_days).

•
Merge and balance classes.

•
Save as Pickle.



2.
Data Loading and Preparation:

•
Load Pickle files.

•
Separate X (features) and y (labels).

•
Normalization (StandardScaler) based on training data.

•
Reshape X into 3D tensor: (samples, time_steps, features).



3.
Model Architecture (CNN-LSTM):

•
CNN Block: 2x Conv1D layers, ReLU activation.

•
Dimensionality Reduction: MaxPooling1D.

•
LSTM Block: 2x Stacked LSTM layers, Dropout.

•
Classification Block: Dense layers, L2 regularization, Tanh/Sigmoid activation for binary output.



4.
Training:

•
Optimizer: Adam.

•
Loss: Binary Crossentropy.

•
Metrics: Accuracy, MAE.

•
Callbacks: EarlyStopping, ModelCheckpoint.



5.
Evaluation:

•
Plot learning curves (loss, accuracy).

•
Evaluate on test set.

•
Classification report (Precision, Recall, F1-score).

•
Confusion matrix.



Parameters to Define

•
sequence_length

•
lookahead_days

•
num_normal_disks

•
max_normal_sequences




