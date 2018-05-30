#NiDM Development Setup

##Install python3
	  sudo apt-get install python3

##Install Anaconda
	  cd ~/Downloads
	  wget https://repo.anaconda.com/archive/Anaconda3-5.1.0-Linux-x86_64.sh
	  sudo ./Anaconda3-5.1.0-Linux-x86_64.sh
	  echo 'export PATH=/home/vagrant/anaconda3/bin:$PATH' >> ~/.bashrc
	  source ~/.bashrc


##Setup conda environment

	cd ~/
	sudo apt-get -y install graphviz
	git clone https://github.com/incf-nidash/PyNIDM.git
	conda create -n pynidm_py3 python=3 pytest graphviz -y
	source activate pynidm_py3
	cd PyNIDM
	pip install -e .
	pytest
	pip install rdflib requests fuzzywuzzy owlready2 pygithub pybids duecredit

##Download a datasets
Navigate to https://openneuro.org/datasets/ds001365/versions/00001
Click the small download icon to download the dataset to ~/Download
      cd ~/workspace
      tar -xvf ~/Downloads/Indiv*.tar

##Add NiDM data to CMU_b dataset
      cd ~/workspace/Indiv_Diffs_ReadingSkill
      ~/PyNIDM/bin/BIDSMRI2NIDM.py -d ~/workspace/Indiv_Diffs_ReadingSkill



