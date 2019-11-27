# Preprocessing
Two datasets are necessary for the experiments in this project. The laughter datasets can be created by following the steps [here](https://github.com/Jack-0-0/Laughter-Detection/tree/master/preprocessing).

This section will detail how to convert the hyena audio files into train, test and validation datasets in the format [id, spectrogram, label]. 

## Requirements
The following packages are needed for preprocessing:
* Python 3.7.0
* tqdm 4.36.1
* numpy 1.17.2
* pandas 0.25.1
* librosa 0.7.0
* jupyter 1.0.0

## Datasets
Expected data structure:

* cc16_352a
  * cc16_352a_audio
    * cc352a001_0h22k.wav
    * cc352a001_2h22k.wav
    * cc352a001_4h22k.wav
    * ...
  * cc16_352a_audit
    * cc352a001_0h_labels_MM.txt
    * cc352a001_2h_labels_MM.txt
    * cc352a001_4h_labels_MM.txt
* cc16_352b
  * cc16_352b_audio
    * cc352b003_0h22k.wav
    * cc352b003_2h22k.wav
    * cc352b003_4h22k.wav
    * ...
  * cc16_352b_audit
    * cc352b003_0h_labels_CW.txt
    * cc352b003_2h_labels_CW.txt
    * cc352b003_4h_labels_CW.txt
* ...


## Usage
First use create_ds_hyena.ipynb to create datasets in the format [id, spectrogram, label]. The file creates a dataset for just one hyena at a time as the hyena dataset is quite large. Set the paths at the top of the file and then run each code block in order. Repeat for all five hyenas.

Then use train_val_test_hyena.ipynb to create the train, validation and test hyena datasets in both non normalised and PCEN format. Set the paths at the top of the file and then run each code block in order.
