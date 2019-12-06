# Evaluation
There are two evaluation notebooks for the cross species experiments to plot the ROC AUCs:
* evaluation_cs.ipynb for the scaled data.
* evaluation_cs_PCEN.ipynb for PCEN data. 

## Requirements
The following packages are needed:
* Python 3.7.0
* numpy 1.17.2
* matplotlib 3.1.1
* scikit-learn 0.21.3
* jupyter 1.0.0
* tensorflow-gpu 2.0.0
* cuda 10.0-cudnn7.5.1
* Keras 2.3.0

## Datasets and Trained Models
The evaluation notebooks use trained models, these can be found in cross_species_models.zip in the ‘baseline’ and ‘fine_tuned’ folders.

The laughter datasets used to scale the unnormalised data can be found in laughter_ds.zip.
The hyena datasets can be found at import/c4dm-04/jackr. 

Alternatively, the datasets can be created as described in the preprocessing section [here](/preprocessing). The trained models can be created by following the steps in the train section [here](/train).

## Usage
At the top of the notebooks:
* set the paths for the training data
* set path to the test data
* set the paths to the models for evaluation

Then run each code block in order to produce the ROC plots.
