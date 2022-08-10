# Desktop Finetuning CNN for sEMG Gesture Recognition
## About
This project aims to achieve efficient sEMG gesture recognition through Convolutional Neural Network (CNN) and Finetuning. Finetuning is a technique of transfer learning, which, we aim to generalize model learnings from the larger dataset to a more specific, downstream dataset. In this case, we performed offline training with a large recorded sEMG dataset and retrained it with real-time collected data. Additionally, we compiled our model with Tensorflow Lite, optimized for micro-controller applications.

## Data Collections
To acquire real-time sEMG signals, we utilized Thalmic Lab's Myo Armband, with BLE connections established via. the python Bleak library. The Myo Armband contains 8 channels of raw sEMG signal sampled at 200 Hz. As for offline training data, we adopted the NinaPro DB5, which also uses Myo Armband for data acquisition. From NinaPro DB5, we utilized 7 gestures from Exercise B: 

    1. Rest (0)
    2. Thumb Up (13)
    3. Flexion of ring and little finger, extension of the others (15)
    4. Abduction of all fingers (17)
    5. Fingers flexed together in fist (18)
    6. Wrist flexion (25)
    7. Wrist Extension (26)

## Quick Start

#### Real Time Gesture Recognition
Let's perform a simple 4 gesture recognition. Enable bluetooth on your PC and have the Myo Armband attached on your arm. Then, run `realtime.py` and follow guidelines printed on the command prompt, to perform the 4 gestures: "Rest", "Fist", "Thumbs Up", and "Ok Sign". After real time sEMG is collected, the pre-trained model from folder "checkpoints" will be finetuned with these samples. Lastly, this model will perform gesture recognition! (Optional: You may also export the finetuned model's weights by controlling variable "finetuned_path")

#### Advanced
If you would like to perform other gestures, you may also finetune with other gestures from NinaPro DB5, simply by controlling the variable "targets" in `config.py`. Then, edit the "GESTURES" in `realtime.py` for realtime gesture recognition upon other gestures.

###### Special NOTE
It might not be a good idea to pre-train with all 53 gestures from NinaPro DB5 as we have detected Nan loss doing so.


## Files Overview
1. Folder -> "checkpoints" contains:
    - A pretrained finetune-base model's weights.
    - 89% acc over test and train set for 7 Ninapro DB5 gestures:
        1. relax
        2. thumbs up
        3. flexion
        4. open hand
        5. fist
        6. wrist flexion
        7. wrist extension

2. Folder -> "finetuned":
    - Placeholder for a finetuned model's weights.

3. Folder -> "Ninapro_DB5" contains:
    - The Ninapro DB5 dataset I obtained from https://zenodo.org/record/1000116#.YraeZHaZNLE

4. Folder -> "tensorflow_lite" contains:
    - Placeholder for a compiled finetuned TF Lite model's weights.

5. Folder -> "visuals" contains:
    - Demonstration of how Myo Armband was weared when Ninapro DB5 collected their samples. (visuals\armband_position.png)
    - Overview of gestures and data samples: (visuals\Data.png + visuals\gestures.png)

6. File -> "config.py" contains:
    - Configuration Variables and Parameters

7. File -> "dataset.py" contains:
    - Utilities for extracting and preprocessing sEMG signals data

8. File -> "model.py" contains:
    - Code for A.I. model implementation and utility functions for it.

8. File -> "realtime.py" contains:
    - Main Program for Real-Time system which establishes BLE connection,
        defines GUI, and finetunes realtime samples from a pretrained finetune-base model.
    - OPTIONAL: Export finetuned model's weights

9. File -> "requirements.txt" contains:
    - List of libraries I used through this github repo
    - To replicate my environment, run this under activated conda env: pip install -r requirements.txt

10. File -> "scaling_params.json" contains: (If it exist)
    - Json with MEAN and Standard Deviation for each sensor Channel.

11. File -> "tensorflow_lite.py" contains:
    - Code for compiling Tensorflow model to Tensorflow Lite model.

12. File -> "train.py" contains:
    - A sample run of how to perform:
        - Data Preprocessing over Ninapro DataBase5
        - Training finetune-base model (Saving weights along the way)
        - Visualize training logs (model accuracy and loss during training)