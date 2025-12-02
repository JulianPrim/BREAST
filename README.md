# Breast cancer Expression Analysis Software Tool (BREAST)
viewer of Wu et al. single cell atlas of breast tumors (PMID: 34493872) and global T47D public ChIP-seq data downloaded from ChIP-Atlas.

To use the single cell part of the viewer: 
Download the release "seurat_obj.rds", put it in a folder, the same as the App.R code that you will create in R). In R, set up your working directory in that folder. Copy-Paste the script, install all the packages and press runApp.

Here is the global home view of our tool:
<img width="906" height="675" alt="image" src="https://github.com/user-attachments/assets/b67fc956-35c5-4519-963a-adbebb9e3ef1" />


To use the single cell part of the viewer: 
Download the release "seurat_obj.rds", put it in a folder, the same as the App.R code that you will create in R). In R, set up your working directory in that folder. Copy-Paste the script, install all the packages and press runApp.

<img width="974" height="806" alt="image" src="https://github.com/user-attachments/assets/a02a5d97-bebc-42e6-8024-c338d49ed669" />

You can select a type of tumor microenvironment between ER+, HER2 and TNBC (Triple negative breast cancer). In each, you can display either a feature plot or a jitter plot of the gene available in the wu et al. dataset, of your choice. Until here, this viewer is not better than the original publication on the single cell portal, but we added a function to use Findmarkers on given populations and genes, allowing to infer on genes functions and impacts in the breast cancer tumor microenvironemnent. The output is a downloadable csv table with statistics. The parameters of the graphs are adjustable to render good quality and publishable graphs without any new coding steps. 
