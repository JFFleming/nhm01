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
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh 
```


