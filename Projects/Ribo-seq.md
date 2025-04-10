# **Ribosome profiling（Ribo-seq）**
## **Introduction to Ribosome Profiling**
- [Ribosome profiling](https://en.wikipedia.org/wiki/Ribosome_profiling), also known as Ribo-seq, is a commonly used translational sequencing technique developed to monitor translation in vivo on a genome-wide scale. 
- Ribo-seq involves sequencing RNA fragments that are bound to ribosomes during translation, providing accurate information on all translatable molecules in a sample , and enabling precise quantification. It serves as a bridge between the transcriptome and proteome . 
- The basic principle of Ribo-seq is the selective isolation and sequencing of ribosome-protected mRNA fragments, known as ribosome-protected fragments (RPFs). RPFs represent the positions of actively translating ribosomes on the transcriptome.
- More information about ribosome profiling you can read [my review](https://academic.oup.com/bib/article/26/1/bbae641/7922579?login=false).

## **Upstream Workflow of Ribosome Profiling Data**
### **00.rawdata, download**

```
##activate your ribo-seq data analysis environment
conda activate ribo
##download raw date via fastq-dump
nohup fastq-dump --gzip --split-3 --defline-qual '+' --defline-seq '@\$ac-\$si/\$ri'   SRR9047189 &
##check data integrity
cat nohup.out | grep Written
```

### **01.beforeQC, quality control **

```
ls 00.raw/*.gz | xargs fastqc -t 12 -o 01.beforeqc
```

