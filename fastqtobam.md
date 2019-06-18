# fastqtobam

## Alignment

### genome indexing 
bwa index -a bwtsw reference.fa

bwtsw: Algorithm implemented in BWT-SW. This method works with the whole human genome

### alignment to generate sam (remember to redirect output to file)
bwa mem -t 4 reference.fa read_1 read_2 > yourfile.sam  

-t: thread

### sort bam according to genomic position 
samtools sort -o output.bam -O bam -@ 8 inputfile.bam  

-o: write to file instead on terminal
-O: output format
-@: number of threads

### index bam file by samtools - index a coordinate-sorted bam file (need to index bam file in order to view with genome viewer)
samtools index yourfile.bam 

## -- Aligned reads ready to be view in genome viewer such as IGV and Tablet. 

--------------------------------------------------------------------------------------------------------
### sam to bam 
samtools view -b inputfile -o output_sorted.bam

-b: write output as bam

==============================================================

#### info from 
https://www.biostars.org/p/65146/  
http://bio-bwa.sourceforge.net/bwa.shtml  
http://www.htslib.org/doc/samtools-1.1.html
