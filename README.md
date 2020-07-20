# Hi-C_analysis_examples

A repo to store various Hi-C analysis examples.

## Distiller-nf
We use https://github.com/mirnylab/distiller-nf

### Liberman-Eiden 2009 data example
```
module load conda3
source activate genomics
cd ~/_scratch
mkdir lib_eiden_2009; cd lib_eiden_2009
nextflow clone mirnylab/distiller-nf  ./
git checkout 4d147a1 # this is the commit we were testing with
curl https://raw.githubusercontent.com/intbio/Hi-C_analysis_examples/master/distiller/newton.config > configs/local.config

### This will modify configs/local.config and replace it with distiller/newton.configs
### line 72 enable = false
### add section
### singularity {
### enabled = true
### runOptions = '-B /home/_shared/genomics_dbs:/home/_shared/genomics_dbs'
### }

curl https://raw.githubusercontent.com/intbio/Hi-C_analysis_examples/master/distiller/lib_eiden_2009.yml > lib_eiden_2009.yml
### This will download  distiller/lib_eiden_2009.yml

vdb-config -s /repository/user/main/public/root="/home/_shared/genomics_dbs/sra"
sed -i.bak 's/HOME=/#HOME=/' distiller.nf
### This will in distiller.nf comment out line 137 # HOME=`readlink -e ./` this will allow sra-tools to use local cache

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

# HiGlass Visualisation
**!** Only multiresolutional files in the .cool format can be viewd with the HiGlass

In the *genomics* environment:
```
cp <your .mcool file> /home/_shared/higlass/hg-tmp 
COOLER=<your .mcool file>

sudo -u docker docker exec higlass-container ls /tmp
sudo -u docker docker exec higlass-container python higlass-server/manage.py ingest_tileset --filename /tmp/$COOLER --filetype cooler --datatype matrix
```
Then go to the http://newton.bioeng.ru:8888/, press "+" in the upper-right corner then select your cooler and explore the heatmap

# Задачи
1) определиться с пайплайном
2) определиться с данными
