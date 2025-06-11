# Brand Name Initial Classifier using Deep Learning

This project trains a deep learning model to classify the **first character** of brand names using TensorFlow and Keras. The goal is to predict the starting letter (A-Z) of a brand based on a synthetic or character-level representation of the name.

## 🧠 Model
- Utilizes an LSTM (Long Short-Term Memory) network to handle sequential character data.
- One-hot encoding is used to represent characters for input to the model.
- The model is trained on brand names and labels corresponding to their first letter.

## 📊 Evaluation
- The accuracy of the model is evaluated on a test set.
- A confusion matrix is generated to visualize performance across different character classes.
