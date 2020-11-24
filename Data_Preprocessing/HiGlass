# HiGlass Visualisation
**!  Only multiresolutional files in the .cool format can be viewd with the HiGlass**

In the *genomics* environment:
```
cp <your .mcool file> /home/_shared/higlass/hg-tmp 
COOLER=<your .mcool file>

sudo -u docker docker exec higlass-container ls /tmp
sudo -u docker docker exec higlass-container python higlass-server/manage.py ingest_tileset --filename /tmp/$COOLER --filetype cooler --datatype matrix

```
Then go to the http://newton.bioeng.ru:8888/, press "+" in the upper-right corner then select your cooler and explore the heatmap
