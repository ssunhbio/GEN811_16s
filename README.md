README


**Project Name**: Bioinformatic analysis for spatial and temporal trends of 16S data from weekly water samples taken in Great Bay Estuary, New Hampshire

**Authors**: Sara Smith, Marley Gonsalves, Natalie Danek, Elijah St. Pierre


**Background**

Aquatic habitats, including rivers, estuaries, and coasts, are habitats that offer ecological and economic services such as habitat for fish and shellfish, water filtration, nutrient cycling, and recreation. Many of these cycles and processes associated with these services are facilitated by microbes, such as bacteria and archaea (Crump and Bowen, 2024). Microbes are highly diverse, and their community composition and structure may change rapidly due to temperature, nutrient availability, competition, or other pressures (Pannard, 2008), which means that repeated sampling is necessary to fully capture their trends. This is especially apparent in dynamic systems with flowing water, where environmental parameters are constantly changing. This study aims to characterize the microbial community composition in a variety of habitats, ranging from freshwater to brackish to marine, near the New Hampshire coast, supplementing existing monitoring within the area. This information will be used to inform aquaculture practices, track potentially hazardous taxa (such as those associated with harmful algal blooms or antibiotic resistance), and provide a baseline for future change in a changing climate.  

**Methods**

Water samples were collected weekly from 3 sites and monthly from 4 sites, all within the Great Bay Watershed in New Hampshire. The weekly sites included the Coastal Marine Lab (CML) in New Castle, NH, the Jackson Estuarine Lab (JEL) in Durham, NH and Wiswall Mill (WIS) in Durham, NH. The monthly sites included Hilton Park (HILT) in Dover, NH, Miriam Jackson Park off Main Street (MAIN) in Epping, NH, the Lamprey River Boat Launch (LAMP) in Epping, NH and Newmarket Boat Launch (NBL) in Newmarket, NH. 500 mL of water from sample was filtered in triplicate through 0.2 um 47 mm Cytiva filters using Thermo Scientific Nalgene Reusable Filter Units. The filters were stored in –80 C until extraction.  

DNA was extracted with ZymoBIOMICS DNA miniprep kits with bead beating. DNA concentration was measured using Qubit™ 1X dsDNA HS (High Sensitivity) Assay Kits. 16S PCR was conducted using 16S-V4 primer pair: forward (515F): GTGCCAGCMGCCGCGGTAA, and reverse (806R): GGACTACHVGGGTWTCTAAT (Kozich et al., 2013). The PCR amplification profile was 2 minutes at 95 °C, 30 cycles of 20 seconds at 95 °C, 30 seconds at 50 °C, 1 minute at 72 °C, 1 minute at 72 °C, 72 °C for 5 minutes, and then held at 4 °C. Following PCR, 5 µL of product was run on an electrophoresis gel, with a 100 bp ladder and a negative control to check for contamination. Sample concentrations were standardized when needed by dilution of Nuclease Free Water to 10 ng µL-1. 30 µL per sample was sent to Michigan State University (MSU) in a 96 well PCR-type plate for paired-end 16S AVITI sequencing.  

Demultiplexed 16s fastq files from MSU were transferred to Ron using Filezilla, then split amongst group members for analysis (Table 1). Each dataset was analyzed in the same way, using the following procedure. 

| Group Member | Data Set | Sequence 1 Forward/Reverse Cut | Sequence 2 Forward/Reverse Cut | Rarefaction | 
| -------- | -------- | -------- | -------- | -------- | 
| Sara Smith | CML 2025| 240/200 | 240/200 | 64548 | 
| Elijah St. Pierre | CML 2024  | 240/200 | 240/200 | 64548 | 
| Marley Gonsalves    | JEL February to December 2025  | 240/200 | 240/200 | 64548 | 
| Natelie Danek   | WIS, MAIN, LAMP, and NBL September to December 2025 | 240/200 | 240/240 | 64548 | 

*Table 1. Data set distribution and unique variables used for analysis.*

Metadata files were generated in Excel; the first column of the metadata files contained the IDs of each sample in the respective dataset, and the following columns included site, date of sample collection, and related environmental parameters (e.g. chlorophyll a concentration, and picoeukaryote/nanoeukaryote/cyanobacteria cell counts). Metadata files were saved as .txt files and loaded into Ron. QIIME 2 (qiime2-amplicon-2026.1) was used in a Conda environment, and cutadapt was used to remove primers (Bolyen et al., 2019; Martin, 2011). A manifest file was created and used to import the fastq files into QIIME 2 with QIIME tools import. The data was then summarized into a .qzv file and visualized with the QIIME2 View (https://view.qiime2.org/) to create quality score plots. Forward and reverse reads were cut where the quality score fell below 30 (Table 1). A feature table summary was generated, and a feature table was used to map IDs to sequences. Data was denoised using dada2 (Callahan et al., 2016). The SILVA database (silva-138-99-nb-classifier) was used to assign taxonomy (Chuvochina et al., 2026). Rooted phylogeny trees were created for each site, and summary tables were visualized to determine rarefaction value (Katoh et al. 2002; Price et al. 2010).  Depth was based on 100% sample retention while still allowing for sufficient diversity (Table 1). Samples below depth were dropped from analysis. All metrics, including the weighted UniFrac, Bray‐Curtis dissimilarity, and Principle Coordinate Analysis (PCoA) were estimated after samples were rarefied using qiime diversity core-metrics-phylogenetic (Bolyen et al., 2019; Lozupone et al. 2007; Bray et al. 1957). 

**Findings**

*Sara - CML 2025 results*
![plot](Plots/CML2025_taxa_barplot.png)
Obvious trends - Level 4 taxa barplot of the Coastal Marine Lab 2025 microbial community made through a Visual Studio Code Qiime 2 conda environment, visualized with Qiime 2 View. Though many taxa were present year-round, strong seasonality impacting relative abundance was witnessed. Flavobacteriales (light green; most frequent genus: NS5 Marine Group) and Rhodobacteriles (light purple; most frequent genus: Planktomarina) were consistently the dominant, with relative frequency ranging from 15.329%-51.629% and 11.750%-42.775% respectively. Both were largely dominant in the late winter to early spring period (January – April). Flavobacteriales had the highest frequencies in February and early March, while Rhodobacterales had the highest frequencies in March (>50% of sample).  Chloroplast (yellow) also saw a brief high relative frequency (1/21/25: 26.867%) in winter, but it was short lived, with overall frequency between 1-11%.  In contrast, Psueudomonadales (orange) had low relative frequency in the winter months (~2-7%), but in late March began to represent a large portion of the community (10-20%).  This frequency range persisted throughout the rest of the year.  Burkholderiales (dark blue) made up between 3-5% for most of the year, but began to grow in relative frequency starting in March, reaching a max in April (5/15/2025: 21.362%) before returning to prior abundance. Actinomarinales (dark purple) was seen at low values at the beginning of the year, and dropped below 1% between the end of April to the beginning of August. However, from August to the end of September, frequency spiked (8/20/2025: 17%) and remained in the double digits until October.  A variation of this trend was seen in Puniceispirillales (brown), which was absent from January to mid-March, but slowly increased throughout March – November, maxing in June (7/15/2025: 7.804), then maintaining 5-7% relative frequency until December.   

![plot](Plots/CML2025PCOA.png)
Bray Curtis PCOA of the Coastal Marine Lab 2025 microbial community made through a Visual Studio Code Qiime 2 conda environment using qiime diversity core-metrics-phylogenetic and visualized with Qiime 2 View. The Bray Curtis PCOA showed clear clustering of samples by monthly time points, indicating strong seasonality within the CML environment and reinforcing conclusion from the taxa barplot. March samples fell within both winter (January to March) and Spring (April/May) clusters, while August showed more similarity to the fall and early winter months than the summer. 

*Natalie - HILT, LAMP, MAIN, NBL, WIS results* 

![plot](Plots/TaxaBarplot_Natalie.png)

Figure #. Taxonomic bar plot made with QIIME2 View of the relative frequency at level 4 (Class) of the HILT, LAMP, MAIN, NBL sites, which were sampled monthly from September to December in 2025, and the WIS site which was sampled weekly during that time period.  

In this plot, on the x ais is the site_date and on the y axis is the relative frequency of the different assigned taxa on the class level. The two sites with the most saltwater input and that experience tidal changes, HILT and NBL, are very similar to each other. The other 3 sites, LAMP, MAIN, and WIS, which are much farther from saltwater sources and do not experience tidal changes, have a lot of similarities to one another. HILT and NBL have a lot more of Flavobacteriales (tan, 17-28%), Pseudomonadales (dark blue, 8- 16%) and Rhodobacterales (pink, 7-20%) compared to the other sites. The other sites, LAMP, MAIN, and WIS all have the highest frequency of Burkholderiales (green, 22-60%) and second highest frequency of Frankiales (purple, 3-28%). HILT and NBL have significantly smaller amounts of Burkholderiales (green, 3-9%). NBL has a small frequency of  Frankiales (purple, 4-5%) and HILT, which is the most salty of these sites, has none. This graph therefore demonstrates a clear influence of saltwater input on taxonomic frequencies, leading to significant site differences throughout this watershed. 

![plot](Plots/PCOA_Natalie.png)

Figure #. 

**Citations**

Bolyen, E., Rideout, J. R., Dillon, M. R., Bokulich, N. A., Abnet, C. C., Al-Ghalith, G. A., Alexander, H., Alm, E. J., Arumugam, M., Asnicar, F., Bai, Y., Bisanz, J. E., Bittinger, K., Brejnrod, A., Brislawn, C. J., Brown, C. T., Callahan, B. J., Caraballo-Rodríguez, A. M., Chase, J., … Caporaso, J. G. (2019). Reproducible, interactive, scalable and extensible microbiome data science using QIIME 2. Nature Biotechnology, 37(8), 852–857. 10.1038/s41587-019-0209-9 

Bray, J.R. and Curtis, J.T. (1957), An Ordination of the Upland Forest Communities of Southern Wisconsin. Ecological Monographs, 27: 325-349. https://doi.org/10.2307/1942268 

Callahan, B.J., McMurdie, P.J., Rosen, M.J., Han, A.W., Johnson, A.J.A., and Holmes, S.P. (2016). DADA2: High-resolution sample inference from Illumina amplicon data. Nature Methods, 13(7), 581-583. doi: 10.1038/nmeth.3869 

Chuvochina M, Gerken J, Frentrup M, Sandikci Y, Goldmann R, Freese HM, Göker M, Sikorski J, Yarza P, Quast C, Peplies J, Glöckner FO, Reimer LC (2026) SILVA in 2026: a global core biodata resource for rRNA within the DSMZ digital diversity. Nucleic Acids Research, gkaf1247. 

Crump, B. C., & Bowen, J. L. (2024). The Microbial Ecology of Estuarine Ecosystems. Annual Review of Marine Science, 16(1), 335–360. https://doi.org/10.1146/annurev-marine-022123-101845 

Katoh K, Misawa K, Kuma K, et al. MAFFT: a novel method for rapid multiple sequence alignment based on fast Fourier transform. Nucleic Acids Res. 2002;30:3059‐3066. 

Lozupone CA, Hamady M, Kelley ST, et al. Quantitative and qualitative beta diversity measures lead to different insights into factors that structure microbial communities. Appl Environ Microbiol. 2007;73:1576‐1585. 

Martin, M. (2011). Cutadapt removes adapter sequences from high-throughput sequencing reads. EMBnet.journal, 17(1), 10. https://doi.org/10.14806/ej.17.1.200   

Pannard, A., Claquin, P., Klein, C., Le Roy, B., & Véron, B. (2008). Short-term variability of the phytoplankton community in coastal ecosystem in response to physical and chemical conditions’ changes. Estuarine, Coastal and Shelf Science, 80(2), 212–224. https://doi.org/10.1016/j.ecss.2008.08.008 

Price MN, Dehal PS, Arkin AP. FastTree 2–approximately maximum‐likelihood trees for large alignments. PLoS ONE. 2010;5:e9490. 
