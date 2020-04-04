# Hi-C_analysis_examples

A repo to store various Hi-C analysis examples.

## Distiller-nf

We use https://github.com/mirnylab/distiller-nf

# Distiller example test on newton
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
