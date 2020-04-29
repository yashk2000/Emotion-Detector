# Emotion-Detector
This is a CNN based emotion detector.

It can detect 6 facial expressions:

- Angry
- Disgust
- Fear
- Happy
- Sad
- Surprise
- Neutral

The CNN has been traind on the [FER2013](https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data) dataset available on Kaggle. 

# 1) Building the dataset: 

To build the dataset, run `buildDataset.py` to build the dataset. Provide the path to the dataset inside the file.

```bash
python buildDataset.py
```

# 2) Training:

To train the CNN, use the `trainRecognizer.py` class. You can train the model using checkpoints. When the model seems to be overfitting or underfitting, pause the training, adjust the script and resume training from the same checkpoint. 

```bash
python trainRecognizer.py --checkpoints checkpoints
```

To resume from the epoch where the training wa stopped: 

```bash
python trainRecognizer.py --checkpoints checkpoints --model checkpoints/epoch_40.hdf5 --start-epoch 40
```

# 3) Testing the model:

I used the model obtained at epoch 75 for all purposes. To test the model run `testRecognizer.py`. 

```bash
python test_recognizer.py --model checkpoints/epoch_75.hdf5
```

# 4) Using the model on a real time feed:

To detect emotions in a real time feed from the camera, use the `emotionDetector.py` script. In order to detect multiple faces use the `emotionDetectorMultipleFaces.py` script. 

```bash
python emotionDetector.py --cascade haarcascade_frontalface_default.xml --model checkpoints/epoch_75.hdf5
python emotionDetectorMultipleFaces.py --cascade haarcascade_frontalface_default.xml --model checkpoints/epoch_75.hdf5
```

