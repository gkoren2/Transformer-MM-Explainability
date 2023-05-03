# difsrx 
created to support the combination of difsr with transformer explainablity (from https://github.com/hila-chefer/Transformer-Explainability.git)

## the steps   
1. clone the difsr environment (see below how to create)
2. install whatever needed to run the Transformer Explainability 


## creating difsr
to create the environment to run this project: 
```
 conda create -n difsr python=3.9
 conda activate difsr
```
install pytorch according to the instructions from their site. at the moment of creating the env, it was:
```
conda install pytorch torchvision torchaudio pytorch-cuda=11.6 -c pytorch -c nvidia
```
then continue with the following installations:
```
conda install -c anaconda jupyter
conda install -c conda-forge jupyter_contrib_nbextensions
conda install pandas scikit-learn tqdm
conda install -c conda-forge matplotlib   # not sure its necessary

pip install colorama colorlog tensorboard
```


## adding the requirements for Transformer-Explainability
note that it required adapting the code as originaly it works with older environments 

simply go over the list of requirements, whatever can be added through conda, install through conda.
the only package that required pip was opencv_python

at the end, you should install captum and gensim (not detailed in the requirements):
```
conda install -c conda-forge gensim
conda install -c pytorch captum
```

to install transformers, clone the repository, and install from source:
```
pip install -e .
```

note that at the time of installation, the branch tag was v4.16.0-3917-g849367ccf


## changing code 
the only change had to be done is in `BertForSequenceClassification.forward()': change the `return_dict` default value from `None` to `False`

after that, the BertExplainability notebook should run properly

` 
