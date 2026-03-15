# Diving Jump Classification using LSTM

Project completed during the **Image Processing and Computer Vision** course in my *Systems Engineering studies specialising in Data Engineering*.

## Project Goal

The goal of this project was to build a system that automatically classifies diving jumps from a user-uploaded video.
The model distinguishes between two types of dives:

* **Inward**
* **Twist**

Classification is performed using a **Long Short-Term Memory (LSTM)** neural network trained on sequences of body pose landmarks extracted from video frames.

> Note: The full implementation of this project is kept **private**. This repository contains the project description and results.

---

## Dataset

The dataset consists of **20 diving videos**:

* 10 inward dives
* 10 twist dives

Pose estimation was performed using **MediaPipe Pose**, extracting **33 body landmarks** per frame.

Each frame contains:

* **66 features** (x and y coordinates of landmarks)

The LSTM processes **sequences of 30 frames** starting from the moment when the first significant movement is detected.

---

## Model

The classifier was implemented using **PyTorch** with an LSTM architecture:

* input size: **66**
* hidden units: **64**
* layers: **2**
* classes: **2 (inward, twist)**

Training setup:

* Batch size: **16**
* Epochs: **50**
* Learning rate: **0.001**
* Loss function: **CrossEntropyLoss**
* Optimizer: **Adam**

---

## Model Performance

The model was evaluated on a small test set containing **4 unseen dives**.

Results:

* Accuracy: **75%**
* Correct classifications: **3 / 4**

The small dataset limits generalization, but the results confirm that **LSTM can capture temporal patterns in diving motion**.

---

## User Interface

A **Streamlit GUI** was implemented that allows users to:

* upload a diving video
* run automatic classification
* view prediction probabilities

An additional **trainer mode** compares two dives and highlights the one with a higher predicted score.

---

## Technologies

Python 3.10

Main libraries:

* PyTorch
* MediaPipe
* OpenCV
* NumPy
* Scikit-learn
* Streamlit

---

## Conclusion

The project demonstrates that **LSTM networks are suitable for analysing human motion sequences**.
Focusing on the **initial phase of the dive** significantly improves classification performance.

---

## References

* https://medium.com/@doublekien/lstm-with-pytorch-664065718df4
* https://insightai.global/long-short-term-memory-lstm/
* https://youtu.be/YCzL96nL7j0
