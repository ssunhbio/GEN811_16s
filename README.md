README


# Project Name: Bioinformatic analysis for spatial and temporal trends of 16S data from weekly water samples taken in Great Bay Estuary, New Hampshire

## Authors: Sara Smith, Marley Gonsalves, Natalie Danek, Elijah St. Pierre


## Background


## Methods

Weekly water samples were collected from 3 sites and monthly water samples from 4 sites, all within the Great Bay Watershed in New Hampshire. The weekly sites included the Coastal Marine Lab (CML) in New Castle, NH, the Jackson Estuarine Lab (JEL) in Durham, NH and Wiswall Mill (WIS) in Durham, NH. The monthly sites included Hilton Park (HILT) in Dover, NH, Miriam Jackson Park off Main Street (MAIN) in Epping, NH, the Lamprey River Boat Launch (LAMP) in Epping, NH and Newmarket Boat Launch (NBL) in Newmarket, NH. 500 mL of site sample was filtered in triplicate through 0.2 um 47 mm Cytiva filters using Thermo Scientific Nalgene Reusable Filter Units. The filters were stored in –80 C until extraction.  

DNA extractions were done with Zymo Biomics Mini-DNA prep kit with bead beating. DNA concentration was obtained using Qubit™ 1X dsDNA HS (High Sensitivity) Assay Kits. 16S PCR was conducted using 16S-V4 primer pair: forward (515F): GTGCCAGCMGCCGCGGTAA, and reverse (806R): GGACTACHVGGGTWTCTAAT (Kozich et al., 2013). The PCR amplification profile was 2 minutes at 95 °C, 30 cycles of 20 seconds at 95 °C, 30 seconds at 50 °C, 1 minute at 72 °C, 1 minute at 72 °C, 72 °C for 5 minutes, and then held at 4 °C. Following PCR, 5 µL of product was run on an electrophoresis gel, with a 100 bp ladder and a negative control to check for contamination. Sample concentrations were standardized when needed by dilution of Nuclease Free Water to 10 ng µL-1. 30 µL per sample were sent to Michigan State University (MSU) in a 96 well PCR-type plate for paired-end 16S AVITI sequencing.  

Demultiplexed 16S fastq files from MSU were transferred to Ron using Filezilla, then split amongst group members for analysis (Table 1). Metadata files were generated in excel with the first column being the sample IDs of the data they were analyzing, and the following columns including the data the sample was collected, site, and other measurements associated with each sample. This was saved as a .txt file and loaded into Ron. Qiime 2 (qiime2-amplicon-2026.1) was used in a Conda environment, and Cutadapt was used to remove the primers (Bolyen et al., 2019). A manifest file was created and run through QIIME tools import. The data was then summarized into a .qzv file and visualized with the QIIME2 View (https://view.qiime2.org/) to create quality scores plots. Forward and reverse reads were cut where the quality score fell below 30 (Table 1). A feature table summary was generated, and a feature table was used to map IDs to sequences. Silva (silva-138-99-nb-classifier) was used to assign taxonomy. Rooted phylogeny trees were created for each site, and summary tables were visualized to determine rarefaction value. Depth was based on 100% sample retention while still allowing for sufficient diversity (Table 1). Samples below depth were dropped from analysis. Diversity values and Principal Coordinate Analyses (PCOA) were generated using qiime diversity core-metrics-phylogenetic. 

*TABLE 1*
|Group Member | Data Set | Forward Cut | Reverse Cut | Rarefaction | 
| -------- | -------- | -------- | -------- | -------- | 
| Sara Smith | Coastal Marine Lab 2025| 240 | 200 | 64548 | 
| Elijah St. Pierre | Coastal Marine Lab 2025  | 240 | 200 | 64548 | 
| Marley Gonsalves  | Jackson Estuary Lab February to December 2025  | 240 | 200 | 64548 | 
| Natalie Danek   | Wiswall, Main St. Lamprey River, and Newmarket Boat Launch September to December 2025 | 240 | 200 | 64548 | 

## Findings


![plot](Plots/CML2025_taxa_barplot.png)
Obvious trends - Level 4 taxa barplot of the Coastal Marine Lab 2025 microbial community made through a Visual Studio Code Qiime 2 conda environment, visualized with Qiime 2 View. Though many taxa were present year-round, strong seasonality impacting relative abundance was witnessed. Flavobacteriales (light green; most frequent genus: NS5 Marine Group) and Rhodobacteriles (light purple; most frequent genus: Planktomarina) were consistently the dominant, with relative frequency ranging from 15.329%-51.629% and 11.750%-42.775% respectively. Both were largely dominant in the late winter to early spring period (January – April). Flavobacteriales had the highest frequencies in February and early March, while Rhodobacterales had the highest frequencies in March (>50% of sample).  Chloroplast (yellow) also saw a brief high relative frequency (1/21/25: 26.867%) in winter, but it was short lived, with overall frequency between 1-11%.  In contrast, Psueudomonadales (orange) had low relative frequency in the winter months (~2-7%), but in late March began to represent a large portion of the community (10-20%).  This frequency range persisted throughout the rest of the year.  Burkholderiales (dark blue) made up between 3-5% for most of the year, but began to grow in relative frequency starting in March, reaching a max in April (5/15/2025: 21.362%) before returning to prior abundance. Actinomarinales (dark purple) was seen at low values at the beginning of the year, and dropped below 1% between the end of April to the beginning of August. However, from August to the end of September, frequency spiked (8/20/2025: 17%) and remained in the double digits until October.  A variation of this trend was seen in Puniceispirillales (brown), which was absent from January to mid-March, but slowly increased throughout March – November, maxing in June (7/15/2025: 7.804), then maintaining 5-7% relative frequency until December.   

![plot](Plots/CML2025PCOA.png)
Bray Curtis PCOA of the Coastal Marine Lab 2025 microbial community made through a Visual Studio Code Qiime 2 conda environment using qiime diversity core-metrics-phylogenetic and visualized with Qiime 2 View. The Bray Curtis PCOA showed clear clustering of samples by monthly time points, indicating strong seasonality within the CML environment and reinforcing conclusion from the taxa barplot. March samples fell within both winter (January to March) and Spring (April/May) clusters, while August showed more similarity to the fall and early winter months than the summer. 

*Natalie - HILT, LAMP, MAIN, NBL, WIS results* 
![plot](Plots/Figure7_Natalie.png)
Figure 7. Taxonomic bar plot made with QIIME2 View of the relative frequency at level 4 (Class) of the HILT, LAMP, MAIN, NBL sites, which were sampled monthly from September to December in 2025, and the WIS site which was sampled weekly during that time period.  

In this plot, on the x ais is the site_date and on the y axis is the relative frequency of the different assigned taxa on the class level. The two sites with the most saltwater input and that experience tidal changes, HILT and NBL, are very similar to each other. The other 3 sites, LAMP, MAIN, and WIS, which are much farther from saltwater sources and do not experience tidal changes, have a lot of similarities to one another. HILT and NBL have a lot more of Flavobacteriales (tan, 17-28%), Pseudomonadales (dark blue, 8- 16%) and Rhodobacterales (pink, 7-20%) compared to the other sites. The other sites, LAMP, MAIN, and WIS all have the highest frequency of Burkholderiales (green, 22-60%) and second highest frequency of Frankiales (purple, 3-28%). HILT and NBL have significantly smaller amounts of Burkholderiales (green, 3-9%). NBL has a small frequency of  Frankiales (purple, 4-5%) and HILT, which is the most salty of these sites, has none. This graph therefore demonstrates a clear influence of saltwater input on taxonomic frequencies, leading to significant site differences throughout this watershed. 



## References

Bolyen, E., Rideout, J. R., Dillon, M. R., Bokulich, N. A., Abnet, C. C., Al-Ghalith, G. A., Alexander, H., Alm, E. J., Arumugam, M., Asnicar, F., Bai, Y., Bisanz, J. E., Bittinger, K., Brejnrod, A., Brislawn, C. J., Brown, C. T., Callahan, B. J., Caraballo-Rodríguez, A. M., Chase, J., … Caporaso, J. G. (2019). Reproducible, interactive, scalable and extensible microbiome data science using QIIME 2. Nature Biotechnology, 37(8), 852–857. 10.1038/s41587-019-0209-9 
