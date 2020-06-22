## How to choose optimal window size for your genome analysis
The short answer is that the best window size is a balance between statistical power and biological effect size. You need the window to be large enough that you get enough data in it to be able to achieve significance, but you need it to be small enough that it doesn't end up larger than the region whose methylation is changing so you don't get averaging against the surrounding regions.

We also don't generally recommend using fixed size windows (eg 500bp), since the uneven distribution of CpGs within the genome means that different windows will have very different numbers of CpGs within them, and you therefore get a statistical power bias which can mean getting biases in the regions of the genome where you find hits. We tend to prefer defining windows based on the number of CpGs then contain, which then means you get a variation in resolution, but a more even statistical power.
-- simon andrews

[RNA-Seq Analysis Practicals](http://www.bioinformatics.babraham.ac.uk/training/Methylation_Course/Differential%20Methylation%20lecture.pdf)

[Using the DMR Scan Package](http://bioconductor.riken.jp/packages/3.7/bioc/vignettes/DMRScan/inst/doc/DMRScan_vignette.pdf)
