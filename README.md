# Brain Signal-Based Brand Initial Classifier using Deep Learning

This project uses brain signal data (e.g., HBO, HBR, HbT levels) to classify the **first letter** of perceived brand names. The data is likely derived from fNIRS or a similar non-invasive neuroimaging technique that tracks blood oxygenation in the brain.

## 🧠 Data Description
- Features include HBO (oxyhemoglobin), HBR (deoxyhemoglobin), and potentially total hemoglobin (HbT).
- These signals are correlated with neural activity during brand recognition or perception tasks.
- Labels correspond to the **first character** of the brand name shown to the participant.

## 📈 Model
- Deep learning model (LSTM-based) processes temporal brain signal data.
- The model learns to predict the initial letter (A-Z) of the brand name based on signal patterns.

## 🔬 Evaluation
- Accuracy is measured using a test set.
- A confusion matrix provides insight into which characters are most/least accurately predicted.
