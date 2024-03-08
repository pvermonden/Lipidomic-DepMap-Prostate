# Files for DepMap analysis of expression of ferroptosis candidate genes
The code entitled "Expression_22Q4_22RV1_PC3" was used to analyse the RNAseq data from DepMap public database for 22RV1 and PC3 cell lines. 
The table used as input is under the file "Expression_public_22Q4_22RV1_PC3_subsetted.csv". The table gathering all the genes from GSEA list used to screen in the DepMap data is under the file "GSEA_selection_PLA.csv".

# Files for Lipidomic data analysis on 22RV1, PC3 and LNCaP cell lines
Lipidomic data anlysis was performed in the R_project "0192CEFTMS_analysis". Raw data files (0192CE_FTMS only 2022-10-19-prostate) were directly obtained from processed MS data and contain the raw abundances of lipid species in prostate cancer cells and the metadata about lipid species and prostate cancer cell lines (i.e. treatments, timing, cell lines). 

**0192CE_FTMS only 2022-10-19-prostate data** were processed in the **R02_byCellLine** code as follows. First data were globally explored. Lipid species with a frequency of 70% missing values were filtered out and lipid species abundances were log2 transformed. To explore the lipidomic data, Principal Component Analysis (PCA) was conducted on all log-transformed lipid species abundances for all cell lines by using the MissMDA R package (version 1.18), to impute the remaining missing values by regularized iterative PCA algorithm. Processed data (i.e. matrices of processed abundances of lipid species and log2-transformed abundances of lipid species) can be found in the file processed_data > **R02_prostate**.

From the log2-transformed **R02_prostate** data, lipid species whose abundance changes with treatments were identified in the **R03_DEA_interaction** code as follows. Differential Expression Analysis (DEA) was conducted on the abundances of all lipid species in log2-transformed for all cell lines by performing a regression with the treatment effect based on the proDA package (version 1.10.0)86. Significance was then established with a Wald test on the model coefficient of interest and p-values were adjusted with False Discovery Rate (FDR) for multiple testing. The final output data with the log-fold-changes in the abundance of lipid species and the log-adjusted-p-values are found in the results > file **R03_prostate**.

The code **R04_Lipidomic_data_charts** computes : 
- Volcano plots of differential lipid species abundances for each cell line with treatments based on the result data "R03_prostate"
- PCA score plot for all lipid species and all cell lines based on the processed data "R02_prostate" (log2 transformed)
