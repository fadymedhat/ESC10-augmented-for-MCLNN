
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/fadymedhat/ESC10-augmented-for-MCLNN/blob/master/LICENSE)

# ESC10 dataset augmented for MCLNN

The [ESC10](https://github.com/karoldvl/ESC-10) environmental sound dataset.

| Clip Duration  | Format | Original Clips Count | Categories| Augmentation Count | Augmented Clips Count |  
|:---:|:---:|:---:|:---:|:---:|:---:|
| 5 secs | .wav (originally .ogg)  | 400 | 10 | 12  | 5200 | 

A 5-seconds file may contain events shorter than 5 seconds, accordingly the authors of the dataset padded all files
 to unify the 5 seconds length for all files.
 
 This folder contains:
  * Scripts required to prepare an augmented version of the ESC10 dataset for the MCLNN processing.
  * Pretrained weights and indices for the 5-fold cross-validation in addition to the standardization parameters.
  
 ## Prepossessing
 
The following are the steps involved in preparing the augmented ESC10 dataset:
1) Follow the steps in [ESC10-for-MCLNN](https://github.com/fadymedhat/ESC10-for-MCLNN) to download and preprocess the original ESC10 dataset.
2) Apply the controlled deformations for each clip using the scripts provided [here](https://github.com/fadymedhat/ESC10-augmented-for-MCLNN/tree/master/ESC10_12augment_preparation_scripts).  

  
#### Preparation scripts prerequisites

The [preparation scripts](https://github.com/fadymedhat/ESC10-augmented-for-MCLNN/tree/master/ESC10_12augment_preparation_scripts) require the following packages to be installed beforehand:

* [Rubber Band](https://breakfastquay.com/rubberband/) v1.8.1 An audio time-stretching and pitch-shifting library and utility program
* numpy 1.11.2+mkl
* librosa 0.4.0
* h5py 2.6.0
* muda 0.2.0
   
#### Steps

1. Download the dataset using the [ESC10_download](https://github.com/fadymedhat/ESC10-for-MCLNN/tree/master/ESC10_download) script, make sure the files of each category are in a separate folder.
If you prefer to download the dataset directly, make sure the files are ordered following the [esc10aug_8pitch_4stretch_storage_ordering](https://github.com/fadymedhat/ESC10-augmented-for-MCLNN/blob/master/esc10aug_8pitch_4stretch_storage_ordering.txt) file.
2. Position the scripts of the [Preparation Scripts](https://github.com/fadymedhat/ESC10-augmented-for-MCLNN/tree/master/ESC10_12augment_preparation_scripts) directory in the downloaded dataset parent directory and execute them in order following the "id_XX" index in the file name after applying any necessary configuration.
3. Configure the spectrogram transformation within the [Dataset Transformer](https://github.com/fadymedhat/MCLNN/tree/master/dataset_transformer) and generate the MCLNN-Ready hdf5 for the dataset.
4. Generate the indices for the folds using the [Index Generator](https://github.com/fadymedhat/MCLNN/tree/master/index_generator) script.
