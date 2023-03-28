# Osteoarthritis
Using scRNA-Seq to reveal the mechanisms of osteoarthritis
## 1.Raw data to fastq files
Using bamtofastq tool to convert BAM files produced by 10x software to FASTQ files.
## 2.Fastq files to matrix
using cellranger to get matrix <br>
e.g.,
```
cellranger count --id=D10 \
                   --transcriptome=/home/hou/data/RNA/tools/refdata-cellranger-GRCh38-1.2.0 \
                   --fastqs=/data4/prj_duanli_20180209/D898bp
                   --sample=D898bp \
                   --localcores=20 \
                   --uiport=10000 
```
## 3.Standard pre-processing workflow
### 3.1 Load the dataset and creat Seurat object
e.g.,
```
health1.data <- Read10X(data.dir = "/home/huangcy/data/project/OA/D10/outs/filtered_gene_bc_matrices/GRCh38/")
health1 <- CreateSeuratObject(counts = health1.data, project = "Health1", min.cells = 3, min.features = 200)
```
### 3.2 QC and selecting cells for further analysis
### 3.3 Normalizing the data
### 3.4 Identification of highly variable features
### 3.5 Scaling the data
### 3.6 Perform linear dimensional reduction
### 3.7 Cluster the cells and run non-linear dimensional reduction (UMAP/tSNE)
### 3.8 Finding differentially expressed features (cluster biomarkers)
### 3.9 Assigning cell type identity to clusters
##  4.scRNA-seq integration of OA samples and healthy sample
### 4.1 Load dataset and perform integration
e.g., <br>
```
public_sample.list <- list(oLT113,oLT116,oLT118,MT113,MT116,MT118)
public_sample.anchors <- FindIntegrationAnchors(object.list = public_sample.list, dims = 1:30)
public_sample.integrated <- IntegrateData(public_sample.anchors, dims = 1:30)
```
### 4.2 Perform an integrated analysis









