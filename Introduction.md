# nhm01
nhm01 is the University of Oslo Natural History Museum's High Processing Computer. 

# Applying for an account on nhm01
If you need an account at nhm01, and you work at the museum, then email me at j.f.fleming(@)nhm.uio.no. This email should include the short form of your UiO username. I’ll forward it on to the Drift team, and normally this gets sorted in about a week.

# Getting Started
Logging into nhm01 can be a little more challenging than some other similar HPCs, as it requires a "Proxy Jump". Proxy Jumps are a way to use another server (in this case the University's login server) as a middle-way between two points.
To log in to nhm01, use the following command, replacing \<user\> with your username:

```
ssh -J <user>@login.uio.no <user>@nhm01.hpc.uio.no 
```

To allow administration of your account by NHM please use the following command:

```
setfacl -R -m u:torsths:rwx /home/<user>
```
This command should also be used on any directory you set up anew.

If you need to copy files to nhm01, you can do it like this:

```
scp -o 'ProxyJump <user>@login.uio.no' <filename> <user>@nhm01.hpc.uio.no:/destination/of/copy
```
# How nhm01 is structured
nhm01 is a relatively small HPC in comparison to the machines that you might be used to working on. nhm01's storage is partitioned in a very particular way. You can find this out (and find out how much storage is being used right now) using the command:

```
df-h
```
This will produce an output that looks like this

```
Filesystem                  Size  Used Avail Use% Mounted on
devtmpfs                   1006G     0 1006G   0% /dev
tmpfs                      1006G  4.3M 1006G   1% /dev/shm
tmpfs                      1006G  2.6M 1006G   1% /run
tmpfs                      1006G     0 1006G   0% /sys/fs/cgroup
/dev/mapper/internvg-root    10G  164M  9.9G   2% /
/dev/mapper/internvg-usr     10G  5.7G  4.4G  57% /usr
/dev/mapper/nvmevg-scratch  7.0T  4.2T  2.9T  60% /scratch
/dev/sda2                   508M  297M  211M  59% /boot
/dev/mapper/internvg-var     10G  7.4G  2.7G  74% /var
/dev/sda1                   200M  5.8M  195M   3% /boot/efi
/dev/mapper/internvg-opt     10G  998M  9.1G  10% /opt
/dev/mapper/internvg-tmp     10G  140M  9.9G   2% /tmp
/dev/mapper/datavg-storage   64T   27T   38T  42% /storage
/dev/mapper/internvg-home   300G  239G   61G  80% /home
tmpfs                       202G     0  202G   0% /run/user/326307
tmpfs                       202G     0  202G   0% /run/user/356492
tmpfs                       202G     0  202G   0% /run/user/342885
tmpfs                       202G     0  202G   0% /run/user/309450
tmpfs                       202G     0  202G   0% /run/user/322113
tmpfs                       202G     0  202G   0% /run/user/338283
```

As you can see here, all users on nhm01 share the filesystem /dev/mapper/internvg-home, better known as /home, which is currently 80% full in this example. Because of this limited storage in home (300GB shared between all users), we'd like users to be a bit more vigilant about where they store their data. We don't have individual user quotas, so that requires everyone to take a little more care.

/storage is designed for easy access to stored data, and /scratch for running analyses. For more long-term storage please use other solutions such as offered by UiO (https://www.uio.no/english/services/it/research/storage/).

# What these Technical Specifications mean practically
  For jobs that include fewer, large calculations, nhm01 is great, and might even be preferred vs., say, waiting in the bigmem queue on Saga. Genome Assembly, especially, is somewhere that nhm01 should excel.
  For jobs that include lots of little calculations, such as phylogenetic tree searches, nhm01 might not be the optimal choice.

# Generating folders
nhm01 is a relatively small HPC in comparison to the machines that you might be used to working on. nhm01's storage is partitioned in a very particular way. You can find this out (and find out how much storage is being used right now) using the command:

```
df-h
```
This will produce an output that looks like this

# Technical Specifications
\<Insert Here\>

