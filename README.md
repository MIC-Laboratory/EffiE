1. Folder -> "checkpoints" contains:
    - A pretrained finetune-base model's weights.
    - 98.3% acc over test and train set for 4 Ninapro DB5 gestures:
        1. Relaxation
        2. Flexion
        3. Thumbs Up
        4. Fist

2. Folder -> "Ninapro_DB5" contains:
    - The Ninapro DB5 dataset I obtained from https://zenodo.org/record/1000116#.YraeZHaZNLE

3. Folder -> "visuals" contains:
    - Accuracy and Loss logs when I trained my finetune-base model: (visuals\acc_log.jpg + visuals\loss_log.jpg)
    - Demonstration of how Myo Armband was weared when Ninapro DB5 collected their samples. (visuals\armband_position.png)
    - Demonstration of the finetune-base model's architecture: (visuals\model.png)
    - Overview of gestures and data samples: (visuals\Data.png + visuals\gestures.png)

4. File -> "config.py" contains:
    - Configuration Variables and Parameters

5. File -> "dataset.py" contains:
    - Utilities for extracting and preprocessing sEMG signals data

6. File -> "model.py" contains:
    - Code for A.I. model implementation and utility functions for it.

7. File -> "realtime.py" contains:
    - Main Program for Real-Time system which establishes BLE connection,
        defines GUI, and finetunes realtime samples from a pretrained finetune-base model.

8. File -> "requirements.txt" contains:
    - List of libraries I used through this github repo
    - To replicate my environment, run this under activated conda env: pip install -r requirements.txt

9. File -> "scaling_params.json" contains: (If it exist)
    - Json with MEAN and Standard Deviation for each sensor Channel.

10. File -> "train.py" contains:
    - A sample run of how to perform:
        - Data Preprocessing over Ninapro DataBase5
        - Training finetune-base model (Saving weights along the way)
        - Visualize training logs (model accuracy and loss during training)