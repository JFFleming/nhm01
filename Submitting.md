# Submitting your first job to nhm01 #

nhm01 uses a queuing system called "slurm" to process and queue jobs. Unlike the computer you might be used to using at your desk, when you log in to nhm01, the log in area is not home to a lot of computational power. Instead, tasks are submitted to the computational nodes, a set of high-efficiency parts you can't get direct access to.

You can submit tasks to these nodes using a command called sbatch and something called a pbs script. The submission command looks like this:

```
sbatch Example.pbs
```

Once something has been sent, you'll see an id number appear like this

```
Submitted batch job 10054
```

You can then use the command squeue to see what is happening to your job, which will look like this

```
squeue -u <yourUsername>

             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
             10054      main Example  jamesfl  R       2:02      1 nhm01.hpc.uio.no

```
JOBID gives you the number of the job.
Partition tells you which computational node it is running on. 
Name will be the name you gave it in the pbs script (below). 
User is your Username.
ST is the Status of the job. The two most likely that you will see are R for Running or PD for Pending.
Time is the time that has elapsed since you started the job. Here, it has been running for 2 hours and 2 minutes.
Nodes is the number of nodes running the process.
Nodelist is the address of where those nodes are.

# Understanding a pbs Script

But to submit a job, you have to wrtie a pbs script, and that means understanding how they work! Using [Example.pbs](Example_files/Example.pbs), this is a breakdown of the pbs format.
Not all HPCs are the same, so it is important to note that if you are used to, for example, Saga, there are key difference between how the nhm01 pbs script is formatted. For example, we have no project numbers.

```
#!/bin/bash
```
this first line just tells the HPC what language we have written the commands of the pbs script in. Here, it's in bash.

```
# Job name:
#SBATCH --job-name=Example
#
```
"--job-name=" gives your job a name so you can easily find it in squeue. Be aware the squeue will crop namesthat are too long, so keep relevant identifiers at the start if you want to submit lots of similar jobs and keep track of them.

```
# Wall time limit
#SBATCH --time=01-00:00:00
#
```
"--time=" tells the HPC how long to run the job for. In the Example script, it is for 1 day. Time is measured as \<Days\>-\<Hours\>:\<Minutes\>:\<Seconds\>

```
# Other parameters:
#SBATCH --mem-per-cpu=3G
#SBATCH	--ntasks=16
```
These two parameters are linked together. 
"--mem-per-cpu=" tells the HPC how much memory it should use on each of the cpus you are requesting of it. Check the technical specifications to know how much memory each CPU has.
"--ntasks=" tells the computer how many of those CPUS it should request. nhm01 only has 128 overall, so please try to be considerate of others when you submit. 


```
#SBATCH --chdir=/storage/path/to/location
```
"--chdir=" tells the HPC where the files it should act on are. So this should be the address of where you are keeping those files. You can find that out by typing 'pwd' in that directory.


```
## Set up job environment:
set -o errexit  # Exit the script on any error
set -o nounset  # Treat any unset variables as an error

module --quiet purge  # Reset the modules to the system default
module load CMake/3.16.4-GCCcore-9.3.0
```

This first bit (the two commands that start with set) basically help us avoid any serious errors if there is a mistake in the script.
"module --quiet purge" resets the node to a blank slate before we start running our jobs on it. Think of it a bit like cleaning a lab bench before you start work.
"module load" is then where you tell the HPC to load the modules required (see Modules.md) to run your work. If you need multiple, you will need multiple module load lines, one after the other.

```
## Do some work:
<program line>
```

Finally, this line is what you would put in to the command line if your were running this job on your home computer. It is the final bit that actually tells the HPC what to do when it receives your job.


# A special note on queuing and jobs on nhm01

Some HPCs you may be used to use sophisticated queuing systems that give some users priority, and then reduce that priority if they submit lots of jobs, which allows other users to run jobs in the middle of one user submitting many.
nhm01 does not have a system that is this sophisticated, and instead operates on a "first come first served" basis. As such, please try to be considerate of other users when submitting jobs, taking into account that the computer has only 128 CPUs.
