# fastqtobam
From filtered sequencing reads (fastq) right up to aligned reads (bam file) for visualisation in genome viewer

General workflow (alignment): index genome -> alignment (output as sam file) -> sort according to genomic position (and into bam file) -> index sorted reads -> genome viewer

## Alignment

### genome indexing 
```
bwa index -a bwtsw reference.fa
```
bwtsw: Algorithm implemented in BWT-SW. This method works with the whole human genome

### alignment to generate sam (remember to redirect output to file)
```
bwa mem -t 4 reference.fa read_1 read_2 > yourfile.bam  
```
-t: thread

### sort bam according to genomic position of reference genome 
step above only generate alignment according to your read sequence (as it is come out from your sequencer), your genome visualiser require reads to be in the correct order as the reference genome in order to open the file.
```
samtools sort -o output.bam -O bam -@ 8 inputfile.bam  
```
-o: write to file instead on terminal  
-O: output format  
-@: number of threads

### index bam file by samtools - index a coordinate-sorted bam file (need to index bam file in order to view with genome viewer)
After sorting, it requires index to find refer to a read quickly (much like books in a library are sorted as catologue that enable fast retrieval).
```
samtools index yourfile.bam 
```
### Aligned reads ready to be view in genome viewer such as IGV and Tablet. 

--------------------------------------------------------------------------------------------------------
### sam to bam 
converting sam to bam file
```
samtools view -b inputfile -o output.bam
```
-b: write output as bam

==============================================================

#### info from 
[biostar thread - read alignment to specific chromosome](https://www.biostars.org/p/65146/)  
[BWA manual](http://bio-bwa.sourceforge.net/bwa.shtml)  
[samtools manual](http://www.htslib.org/doc/samtools-1.1.html)
