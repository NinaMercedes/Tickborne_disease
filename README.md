# Tickborne_disease
Quick pipeline/ notes to process bacterial genome data to find genomic regions for amplicon sequencing... Example for Rickettsia sp. 
First compiles list of WGS, Illumina samples for Rickettsia spp. and pop them into samples.txt file.

## ENA Downloads
Note this has the fastq2matrix.sh command commented out so it only downloads the reads...
```
cd ~/Rickettsia
mkdir wgs
cat samples.txt | xargs -I {} -P 10 sh -c "bash run_new_sample_Rickettsia.sh {}"
```
## Make a Conda Env
```
conda create -n bacteria_pipeline
conda activate bacteria_pipeline
# Shovilll
conda install -c conda-forge -c bioconda -c defaults shovill
shovill --check

```
## A Quick Assembly: Shovill
Let's use an example file to test the makeshift pipeline...

```
cd ~/Rickettsia/example
mkdir shovill_out
cd ~/Rickettsia
cat example.txt | xargs -I {} -P 10 sh -c "bash shovill.sh {}"
# works now let's use the modified script for assembly of all samples we downloaded
cat samples.txt | xargs -I {} -P 10 sh -c "bash shovill.sh {}"
```

