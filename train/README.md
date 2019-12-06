# Train
cross_species_train.py trains the hyena networks and saves the results. The file can be set to create the baseline model without pre-training.
It can also be used to create two types of network that use pre-training with the laughter network as the parent model:
* ‘frozen’ where all layers are not trainable except for the last layer.
* ‘unfrozen’ where all layers are trainable.

## Requirements
The following packages are needed to train the networks:
* Python 3.4.8
* Tensorflow-gpu 1.12.0
* Keras 2.2.4
* numpy 1.16.2
* matplotlib 2.2.4
* cuda 9.0

## Datasets
Train, test and validation datasets (with and without PCEN) can be found at import/c4dm-04.

Alternatively they can be created as described [here](/preprocessing).

## Usage
Open cross_species_train.py and change the variables under the settings section at the top of the file. 

##### Example 1
To train the baseline network that uses PCEN, the settings would be:

```python
########################
####### Settings ####### 
########################

# set path for training data
train = np.load('hyena_train_PCEN.npy')
# set path for validation data
val = np.load('hyena_val_PCEN.npy')
# set path for test data
test = np.load('hyena_test_PCEN.npy')

# set path for pretrained model
pre_tr_path = 'laughter_model_PCEN.h5'

# choose which GPU to use
gpu = "3"

# set number of mels
# all pretrained and baseline networks are at 8,000 Hz so keep mels set to 45
mels = 45

# set model type
# set to 'baseline' to train model without any pretraining
# set to 'frozen' to train model with pretraining but all layers frozen except last layer
# set to 'unfrozen' to train model with pretraining with all layers unfrozen
model_type = 'baseline'

# set whether scaling should be used
# only set to True if using pretraining and not using PCEN
scaling = False

# set paths to laughter datasets, this data will be used to scale the hyena data if necessary
if scaling:
	train_ch = np.load('ch_train_6_6_64_ds.npy')
	train_de = np.load('de_train_6_6_64_ds.npy')
	train_en = np.load('en_train_6_6_64_ds.npy')

# set save folder identifier
# save folder will be named in format saved_models/date_time_filename_sfid 
sfid = 'baseline_PCEN' 

########################
```
##### Example 2
To create the network which uses pre-training with all layers frozen except for the last layer without PCEN but with scaling, the settings would be:

```python
########################
####### Settings ####### 
########################

# set path for training data
train = np.load('hyena_train.npy')
# set path for validation data
val = np.load('hyena_val.npy')
# set path for test data
test = np.load('hyena_test.npy')

# set path for pretrained model
pre_tr_path = 'laughter_model_no_norm.h5'

# choose which GPU to use
gpu = "3"

# set number of mels
# all pretrained and baseline networks are at 8,000 Hz so keep mels set to 45
mels = 45

# set model type
# set to 'baseline' to train model without any pretraining
# set to 'frozen' to train model with pretraining but all layers frozen except last layer
# set to 'unfrozen' to train model with pretraining with all layers unfrozen
model_type = 'frozen'

# set whether scaling should be used
# only set to True if using pretraining and not using PCEN
scaling = True

# set paths to laughter datasets, this data will be used to scale the hyena data if necessary
if scaling:
	train_ch = np.load('ch_train_6_6_64_ds.npy')
	train_de = np.load('de_train_6_6_64_ds.npy')
	train_en = np.load('en_train_6_6_64_ds.npy')

# set save folder identifier
# save folder will be named in format saved_models/date_time_filename_sfid 
sfid = 'frozen' 

########################
```
##### Example 3
To create the network which uses pre-training with all layers unfrozen with PCEN data, the settings would be:

```python
########################
####### Settings ####### 
########################

# set path for training data
train = np.load('hyena_train_PCEN.npy')
# set path for validation data
val = np.load('hyena_val_PCEN.npy')
# set path for test data
test = np.load('hyena_test_PCEN.npy')

# set path for pretrained model
pre_tr_path = 'laughter_model_PCEN.h5'

# choose which GPU to use
gpu = "3"

# set number of mels
# all pretrained and baseline networks are at 8,000 Hz so keep mels set to 45
mels = 45

# set model type
# set to 'baseline' to train model without any pretraining
# set to 'frozen' to train model with pretraining but all layers frozen except last layer
# set to 'unfrozen' to train model with pretraining with all layers unfrozen
model_type = 'unfrozen'

# set whether scaling should be used
# only set to True if using pretraining and not using PCEN
scaling = False

# set paths to laughter datasets, this data will be used to scale the hyena data if necessary
if scaling:
	train_ch = np.load('ch_train_6_6_64_ds.npy')
	train_de = np.load('de_train_6_6_64_ds.npy')
	train_en = np.load('en_train_6_6_64_ds.npy')

# set save folder identifier
# save folder will be named in format saved_models/date_time_filename_sfid 
sfid = 'unfrozen' 

########################
```
Save cross_species_train.py with required settings and then run the file.

When the model is finished training, a folder will be created which contains:
* ROC AUC for  the test set
* F1, TPR, FPR scores for the test set and val set
* Network architecture
* Plots of loss and accuracy for each epoch
* History file
* Network save file which can be used for later evaluation
