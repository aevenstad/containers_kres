# cgMLSTFinder

## Build singularity image
```
singularity build cgMLSTFinder.sif cgmlstfinder.def
```

## Install databases
Instructions to install database from https://bitbucket.org/genomicepidemiology/cgmlstfinder:

```
# Go to the directory where you want to store the cgmlst database
cd /path/to/some/dir
# Clone install script from git repository
git clone https://bitbucket.org/genomicepidemiology/cgmlstfinder_db.git
cd cgmlstfinder_db
cgMLST_DB=$(pwd)
# Install cgMLST database (look at https://bitbucket.org/genomicepidemiology/cgmlstfinder_db.git for more information)
python3 INSTALL.py
```

To install a specific database use:
```
# Install specific database
python3 INSTALL.py -s ecoli
```

## Run cgMLSTFinder
In a directory with fasta assemblies:
```
FASTA=$(ls *fa | tr "\n" ",")
FASTA=$(echo ${FASTA%,})

singularity exec \
  -B /path/to/database/cgmlstfinder_db/:/opt/database +
  cgMLSTFinder.sif \
  python3 /usr/src/cgMLST.py +
  -s ecoli \
  -o cgMLSTFinder_out \
  -i $FASTA \
  -db /opt/database
```
