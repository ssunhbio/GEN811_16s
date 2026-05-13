README

My Project Name


Authors


Background


Methods
Weekly water samples were collected from 3 sites and monthly water samples from 4 sites, all within the Great Bay Watershed in New Hampshire. The weekly sites included the Coastal Marine Lab (CML) in New Castle, NH, the Jackson Estuarine Lab (JEL) in Durham, NH and Wiswall Mill (WIS) in Durham, NH. The monthly sites included Hilton Park (HILT) in Dover, NH, Miriam Jackson Park off Main Street (MAIN) in Epping, NH, the Lamprey River Boat Launch (LAMP) in Epping, NH and Newmarket Boat Launch (NBL) in Newmarket, NH. Once collected, samples were brought back to the lab and 500 mL of site sample was filtered in triplicate through 0.2 um 47 mm Cytiva filters using Thermo Scientific Nalgene Reusable Filter Units. The filters were stored in –80 C until extraction.  

DNA extractions were done with Zymo Biomics Mini-DNA prep kit with bead beating. O Qubit analysis was done on every sample to determine the concentration of DNA using Qubit™ 1X dsDNA HS (High Sensitivity) Assay Kits. Then, 16S PCR was conducted on every sample, using 16S-V4 primer pair: forward (515F): GTGCCAGCMGCCGCGGTAA, and reverse (806R): GGACTACHVGGGTWTCTAAT (Kozich et al., 2013). The PCR amplification profile was 2 minutes at 95 °C. Then, 30 cycles of 20 seconds at 95 °C, 30 seconds at 50 °C, and 1 minute at 72 °C. This was followed by 72 °C for 1 minute, 72 °C for 5 minutes, and then held at 4 °C. Following PCR, 5 µL of every PCR product was run on an electrophoresis gel to verify the existence of DNA. Each gel included a 100 bp ladder so that PCR products can be sized, as well as a negative control to check for contamination. Samples concentrations were standardized; any with a concentration above 10 ng µL-1 were diluted down to that concentration with Nuclease Free Water. Then, 30 µL of each sample was sent to Michigan State University in a 96 well PCR-type plate for paired-end 16S AVITI sequencing.  

The raw fastq files were transferred to Ron using Filezilla. The full set of samples was split amongst the group members for analysis. Sara analyzed the 2025 CML data, EJ analyzed the 2024 CML data, Marley analyzed the JEL data, and Natalie analyzed the data for WIS, MAIN, LAMP, MAIN, and NBL sites. Everyone made a metadata file in excel with the first column being the sample IDs of the data they were analyzing, and the following columns including the data the sample was collected, site, and other measurements associated with each sample. This was saved as a .txt file and loaded into Ron. In Ron, the conda qiime2-amplicon-2026.1 environment was activated in order to use QIIME2 to analyze the 16S data (Bolyen et al., 2019). Our data was already demultiplexed, and paired end reads. A text file with only the needed sample ID’s was made and used to pull out just the specific dates/sites being analyzed. Cutadapt was used to remove the primers. A manifest file was created and run through QIIME tools import. The data was then summarized into a .qzv file using the metadata .tsv file. This file was loaded into the QIIME2 View to create plots of the quality scores. The sequence base when the quality scores dropped before 30 was noted for both the forward and reverse reads. The forward and reverse reads were then cut off to remove those low quality reads. A feature table summary was then created in order to create a visual summary of the data, pulling in information from the metadata file. Feature table tabulate was used to map the IDs to the sequences. Silva (silva-138-99-nb-classifier) was used to assign taxonomy. A QIIME taxa bar plot .qzv file was generated. This was loaded into QIIME2 View to visualize the bar plot showing the taxonomic frequencies of the different samples.  

To perform further analysis, a rooted phylogeny tree was created. The summary table was loaded into QIIME2 view  and used to chose the rarefaction value. In the interactive sample detail,  the slider was moved until the percentage after the number of samples starts to drop below 100%. This value was used as the rarefaction value. Next, qiime diversity core-metrics-phylogenetic  was used to generate different diversity values for different types of plots including PCOA and Bray Curtis. 


Findings


Natalie - HILT, LAMP, MAIN, NBL, WIS results 

Figure 7. Taxonomic bar plot of the relative frequency at level 4 (Class) of the HILT, LAMP, MAIN, NBL sites, which were sampled monthly from September to December in 2025, and the WIS site which was sampled weekly during that time period.  

In this plot, on the x ais is the site_date. This barplot shows clear differences by site. The two sites with the most saltwater input and that experience tidal changes, HILT and NBL. are very similar to each other while the other 3 sites, LAMP, MAIN, and WIS, which are much farther from saltwater sources and do not experience tidal changes, have a lot of similarities to one another. HILT and NBL have a lot more of Flavobacteriales (tan, 17-28%), Pseudomonadales (dark blue, 8- 16%) and Rhodobacterales (pink, 7-20%) compared to the other sites. The other sites, LAMP, MAIN, and WIS all have the highest frequency of Burkholderiales (green, 22-60%) and second highest frequency of Frankiales (purple, 3-28%). HILT and NBL have significantly smaller amounts of Burkholderiales (green, 3-9%). NBL has a small frequency of  Frankiales (purple, 4-5%) and HILT, which is the most salty of these sites, has none. This graph therefore demonstrates a clear influence of saltwater input on taxonomic frequencies, leading to significant site differences.  

