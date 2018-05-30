# NIDM Development Setup

## Install python3
Best to use python 3 for future compatibility. 

	  sudo apt-get install python3

## Install Anaconda
Use a conda environment so packages won't conflict with other applications.

	  cd ~/Downloads
	  wget https://repo.anaconda.com/archive/Anaconda3-5.1.0-Linux-x86_64.sh
	  sudo ./Anaconda3-5.1.0-Linux-x86_64.sh
	  echo 'export PATH=/home/vagrant/anaconda3/bin:$PATH' >> ~/.bashrc
	  source ~/.bashrc


## Setup conda environment
This will create a pynidm_py3 conda environment and install the packages needed to use PyNIDM and the RDFLib to query nidm.ttl files.

	cd ~/
	sudo apt-get -y install graphviz
	git clone https://github.com/incf-nidash/PyNIDM.git
	conda create -n pynidm_py3 python=3 pytest graphviz -y
	source activate pynidm_py3
	cd PyNIDM
	pip install -e .
	pytest
	pip install rdflib requests fuzzywuzzy owlready2 pygithub pybids duecredit

## Download a datasets
Starting with a BIDS formatted dataset you can create a nidm.ttl file. You can find free/open datasets at OpenNeuro. An exmaple is the [Indiv_Diffs_readingSkill](https://openneuro.org/datasets/ds001365/versions/00001) dataset. On the dataset details page you will need to click the small download icon to download the dataset. I didn't see the icon at first. It looks like ![download icon](https://raw.githubusercontent.com/albertcrowley/nidm-training/master/download-icon.png | width=100)  Store it in ~/Downloads.

	cd ~/workspace
	tar -xvf ~/Downloads/Indiv*.tar

## Add NIDM data to CMU_b dataset
      cd ~/workspace/Indiv_Diffs_ReadingSkill
      ~/PyNIDM/bin/BIDSMRI2NIDM.py -d ~/workspace/Indiv_Diffs_ReadingSkill



