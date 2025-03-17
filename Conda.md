# Installing new programs using conda installation
Programs that are not installed can often be installed using conda. FOr doing so you need first do the following steps and then you can use conda as described, for example, on the [conda documentation](https://docs.conda.io/en/latest/).

As the conda installations generate environments that allow a smooth running of the program with all depedencies installed it can become very quickly too large for your home directory (see [introduction](Introduction.md)). You should therefore install miniconda in the storage area. There is a dedicated folder for it.

```
# Go into the dedicated folder:

cd /storage/conda 

# Generate your own folder in it to which only you have access rights:

mkdir -m 700 <username> 

# Go into this folder and install miniconda 3 in there, for example with your username (in my case <username>=torsths):

cd <username>
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /storage/conda/<username>/miniconda.sh
bash ./miniconda.sh -b -u -p /storage/conda/<username>
rm ./miniconda.sh 
```

You can always call up this conda installation on the command line (or any bash script) using:

```
source /storage/conda/<username>/etc/profile.d/conda.sh
```
This will then be your base environment for all installations and analyses until you call up another conda installation.
If you want to have this installation as your default installation you can use the following command:

```
echo -e "\nsource /storage/conda/<username>/bin/activate\n" >> ~/.bashrc
```
After executing this command, you will have to log out and back in again for it to become effective for the first time.

# Some useful conda commands
Here are some commands, which might be good to know:

```
#The cache can be cleaned by running
conda clean -a

#Creating an environment by in default folder
conda create -n <my-env>

#Creating an environment by specifying the environment path with the --prefix option
conda create -p <path-to-a-folder>/myenvs/<my-env>

#Activate environment
conda activate <my-env>

#Activate environment by specifying the folder upfront
conda activate <path-to-a-folder>/myenvs/<my-env>

#Install sources (e.g., numpy) in an environment after activation
conda install numpy
#or also specify the channel to find the source (e.g., scipy)
conda install -c conda-forge scipy

#Creating an environment by in default folder and install a package from either conda-forge or bioconda repository
conda create -n <my-env> -c conda-forge -c bioconda <package>=<version> #(e.g., earlgrey=5.1.1)

#Add channels to channel path
conda config --add channels bioconda
conda config --add channels conda-forge
conda config --set channel_priority strict

#Some packages (e.g., jupyter) can only be installed with pip, but this can also be done through Conda:
conda install pip 
pip install jupyter

#List the packages installed in the environment by running
conda list

#List the environments by running
conda env list

#Remove an environment by using remove or uninstall
conda deactivate
conda remove -n my-env --all
conda uninstall -n my-env --all
```

# Uninstalling a conda installation
In the case it is needed you can uninstall a miniconda installation as follows (for example, an installation in your home directory as used in here).
```
cd /home/<username>
conda deactivate
rm -rf ./miniconda3

#if no other conda installation is present you can remove the following entirely
rm -rf ./.condarc ./.conda

#if you have other conda installations present you need to do the following
nano ./.conda/environments.txt
#remove all environments referencing environments to the deleted installation and save it

#you should also check your .bashrc file if any reference to the uninstalled should be deleted from there
nano ~/.bashrc
#remove all environments referencing environments to the deleted installation and save it

```
