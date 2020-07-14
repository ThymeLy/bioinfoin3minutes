## ChIP-seq

In a ChIP experiment for DNA-binding proteins, DNA fragments associated with a specific protein are enriched. The DNA-binding protein is crosslinked to DNA in vivo by treating cells with formaldehyde and the chromatin is sheared by sonication into small fragments, which are generally in the 200–600 bp range. An antibody specific to the protein of interest is used to immunoprecipitate the DNA–protein complex. Finally, the crosslinks are reversed and the released DNA is assayed to determine the sequences bound by the protein. 

### ChIP-seq technical issue
loading the correct amount of sample: too little sample will result in too few tags; too much sample will result in fluorescent labels that are too close to one another, and therefore lower quality data

In ChIP experiments that aim to map nucleosome positions or histone modifications, micrococcal nuclease (MNase) digestion without crosslinking is most often used to fragment the chromatin. Although sonication has also been used in this context29, MNase treatment is generally preferred because it removes linker DNA more efficiently than sonication and therefore allows more precise mapping of each nucleosome.  
However, MNase digestion has a more pronounced sequence bias than sonication, and bias due to chromatin solubility.

### experimental design ChIP-seq
- antibody quality
  - cross reactivity: for histone modifications for instance, the reactivity of the antibody with unmodified histones or non-histone proteins should be checked by western blotting.

- sample quality

- control experiment
  - Shearing of DNA, for example, does not result in uniform fragmentation of the genome: open chromatin regions tend to be fragmented more easily than closed regions, which creates an uneven distribution of sequence tags across the genome. Also, repetitive sequences might seem to be enriched because of inaccuracies in the number of copies of the repeats in the assembled genome.  
  - a peak in the ChIP–seq profile should be compared with the same region in a matched control sample to determine its significance.
  - Types of control samples:
    - Input DNA (a portion of the DNA sample removed prior to immunoprecipitation (IP)); 
    - mock IP DNA (DNA obtained from IP without antibodies)
      - very little material can be pulled down in the absence of an antibody and therefore the results of multiple mock IPs may not be consistent.
      - When analysing histone modifications, using the ratio between data from the ChIP sample and from the bulk nucleosomes is also informative, as this ratio corresponds to the fraction of nucleosomes with the particular modification at that location
    - DNA from nonspecific IP (IP performed using an antibody, such as immunoglobulin G, against a protein that is not known to be involved in DNA binding or chromatin modification)

- sequencing depth
  -  One reasonable criterion for determining sufficient sequencing depth would be that the results of a given analysis do not change when more reads are obtained. In terms of the number of binding sites, this criterion translates to the presence of a 'saturation point' after which no further binding sites are discovered with additional reads.
  - each ChIP–seq data set could be annotated with a minimal saturated enrichment ratio (MSER) — a point at which saturation occurs — to give a sense of the sequencing depth achieved. 

### Data analysis
#### scoring peaks
- sharp, broad, mixed peaks
  Sharp peaks are generally found for protein–DNA binding or histone modifications at regulatory elements, whereas broad regions are often associated with histone modifications that mark domains 
- The performance of a peak caller can be tested by validating a large set of sites using quantitative PCR or by computing the distribution of distances from each peak to a nearby known protein-binding sequence motif.

#### downstream analysis
The most common follow-up analysis is discovery of binding sequence motifs. The sequences of the top-scoring sites can be entered into motif-finding algorithm programs such as MEME79, MDScan80, Weeder81 and WebMOTIFS82. 

1. annotate the location of the peaks on the genome in relation to known genomic features, such as the transcriptional start site, exon–intron boundaries and the 3′ ends of genes. 

The transcriptional start sites of active genes, for instance, are known to be enriched with histone H3 trimethylated at lysine 4 (H3K4me3), and enhancers are enriched with histone H3 monomethylated at lysine 4 (H3K4me1)25,83. It is informative to view this type of data at a relative scale — for example, by rescaling all genes to have the same length so that the average profile over the gene body can be viewed — as well as absolute scale. To find relationships between the profiles, a correlation analysis can be performed, as well as more advanced clustering methods. 

2. Classifying ChIP–seq patterns by their relationship to expression data

if the expression level of a gene correlates with the binding status of a transcriptional activator, this might indicate that the gene is a target of that activator, or if a chromatin mark is enriched at the promoters of genes with high expression, it can be inferred to be related to transcriptional activation. For a group of genes with a common feature — for example, genes that bind the same transcription factor or have the same modifications — Gene Ontology analysis can be performed to see whether a particular molecular function or biological process is over-represented in those genes 

3. discovery of novel elements based on ChIP–seq data. 

For example, the locations of H3K4me3 and histone H3 trimethylated at lysine 36 (H3K36me3), which are known to be found at promoters and across transcribed regions, respectively, can be used to identify large non-coding RNAs87. Combined with SNP information, ChIP–seq data can also be used to investigate allele-specific binding and modification27. 
