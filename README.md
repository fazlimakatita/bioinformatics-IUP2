# Network Pharmacology Analysis of *Ginkgo biloba* as a Natural Anti-Alzheimer Agent

>this repository is used as a complete tools and procedure guide as well as the comprehensive amount of data that were not able to be explained in the report and poster

## Tools
- **KnapSack** (www.knapsackfamily.com/knapsack_core/top.php): Natural Compound Database
- **SwissADME** (www.swissadme.ch/): Analyze gastrointestinal (GI) absorption, Blood Brain Barrier (BBB) permeability, Lipinski validation, and bioavailability score
- **SwissTargetPrediction** (www.swisstargetprediction.ch/predict.php): Find target genes from compounds
- **OMIM** (www.omim.org/): Obtaining target genes for Alzheimer's Disease
- **Cytoscape** (www.cytoscape.org/): Analyze compound-target network
- **STRING** (www.string-db.org/): Analyze protein-protein interaction (PPI), gene ontology (GO), and KEGG pathways

## Procedure
### *Ginkgo biloba* Bioactive Compounds Screening and Prediction of Targeted Genes
1. Open KnapSack Natural Compound Database and search "*Ginkgo biloba*"
2. Identify the SMILES structure of each compound
3. Input all of the SMILES structure to SwissADME to analyze the pharmacokinetic properties of each compound, filtering based on GI absorption, BBB permeability, Lipinski validation, and a bioavailability score of ≥0.55
4. The selected compounds will then be subjected to SwissTargetPrediction analysis for the target genes that each compound may express
### Alzheimer Target Genes Prediction and Venn Diagram Construction
1. Open OMIM and input "*Alzheimer's disease*" and set the confidence score to high confidence (0.700)
2. Open Gene Map Table and download the genes as an Excel file
3. The genes are then separated through Power Query Editor to be split by comma
4. The gene and locus column are saved
### Compound-Target Network Construction
1. Open Cytoscape > import network from file system > import the file consisting of the intersect target genes and compounds
2. The compounds column is set as the source node and the target genes compound is set as the target nodes
3. Press tools > analyze network to obtain the degree, betweeness centrality, and closeness centrality of the network
4. Install cytocluster plug in
5. Press Apps > cytocluster > ClusterOne algorithm > Advanced Parameters 
6. Settings include: Minimum size at 10, Minimum density at 0.5, and Seeding method at from every node > Analyze
7.  The clustering result is saved under csv format
8.  New network > From selected nodes, selected edges > Tools > Analyze network > ok
9.  The columns were all deleted except for betweeness centrality, closeness centrality, and degree
### Protein-Protein Interactions (PPI) Network Analysis and Hub Genes Identification
1. STRING database is set into multiple proteins > 56 intersect genes were inputted > organisms set to homo sapiens
2. Advanced settings > high confidence (0.700) > continue 
3. PPI network is export in the tsv format and visualized in cytoscape
4. Cytoscape > import > network from file > tools > analyze network
5. Style > column > degree and mapping type > continuous mapping to determine the colour based on the degree
6. Hub genes were identified using the CytoHubba plug ins under MNC, MCC, and Degree algorithm. Conducted by: Apps > cytoHubba > target network > nodes scores > calculate
7. Pick top 10 MCC and submit
8. The same steps were conducted on the remaining algorithms : MNC and Degree
9. The intersection of hub genes from 3 algorithms were obtained from Interactivenn.
10. The 6 key hub genes were obtained and used for further enrichment analysis.
### Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) Analysis
1. The 6 key hub genes were imported to STRING Database under multiple protein and restricted to homo sapiens
2. Analysis > save export these components: Biological Process (Gene Ontology), Molecular Function (Gene Ontology), and KEGG pathways
