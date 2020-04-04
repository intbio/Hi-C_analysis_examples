# Hi-C_analysis_examples

A repo to store various Hi-C analysis examples.

## Distiller-nf
We use https://github.com/mirnylab/distiller-nf

### Liberman-Eiden 2009 data example
```
module load conda3
source activate genomics
cd _scratch
mkdir lib_eiden_2009; cd lib_eiden_2009
nextflow clone mirnylab/distiller-nf  ./

### Modify configs/local.config or replace it with distiller/newton.configs
### line 72 enable = false
### add section
### singularity {
### enabled = true
### runOptions = '-B /home/_shared/genomics_dbs:/home/_shared/genomics_dbs'
### }

### download distiller/lib_eiden_2009.yml
nextflow distiller.nf -params-file lib_eiden_2009.yml
```


### Distiller example test on newton
```
module load conda3
source activate genomics
nextflow clone mirnylab/distiller-nf  ./
cd test
bash setup_test.sh
cd ..
### Modify configs/local.config
### line 72 enable = false
### add section
###  singularity {
###    enabled = true
###}
nextflow distiller.nf -params-file ./test/test_project.yml 
```

# Задачи
1) определиться с пайплайном
2) определиться с данными
