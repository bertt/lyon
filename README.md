# lyon

Live demo: https://bertt.github.io/lyon/

## Processing data

Source data: https://geoservices.ign.fr/ressource/210003

RGE ALTI® 5M - D069 Rhône - Octobre 2022

Processing:

Unzip 

```
$ 7z x RGEALTI_2-0_5M_ASC_LAMB93-IGN69_D069_2022-10-03.7z
```

Create tif files

```
$ cd RGEALTI_2-0_5M_ASC_LAMB93-IGN69_D069_2022-10-03\RGEALTI\1_DONNEES_LIVRAISON_2023-01-00223\RGEALTI_MNT_5M_ASC_LAMB93_IGN69_D069
$ find *.asc | parallel --bar 'gdalwarp -s_srs EPSG:2154 {} {=s:asc:tif:=}'
```

Warp

```
$ docker run -it -v $(pwd):/data geodan/terrainwarp -c EPSG:5698 -m 1
```

Tile

```
$ docker run -it -v $(pwd):/data geodan/terraintiler
```

Create client



