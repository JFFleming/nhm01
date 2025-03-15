# Installing new programs using conda installation
Programs that are not installed can often be installed using conda. FOr doing so you need first do the following steps and then you can use conda as described, for example, on the [conda documentation](https://docs.conda.io/en/latest/).

As the conda installations generate environments that allow a smooth running of the program with all depedencies installed it can become very quickly too large for your home directory (see [introduction](Introduction.md)). You should therefore install miniconda in the storage area. There is a dedicated folder for it.

```
# Go into the dedicated folder:

cd /storage/conda 

# Generate your own folder in it to which only you have access rights:

mkdir -m 700 <username> 

# Go into this folder and install miniconda 3 in there:

cd <username>
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /storage/conda/<username>/miniconda.sh
bash ./miniconda.sh -b -u -p /storage/conda/<username>
rm ./miniconda.sh 
```

You can always call up this conda installation on the command line (or any bash script) using:

```
source /storage/conda/torsths/etc/profile.d/conda.sh
```
This will then be your base environment for all installations and analyses until you call up another conda installation.
If you want to have this installation as your default installation you can use the following command:

```
echo "source /storage/conda/torsths/bin/activate" >> ./.bashrc
```

