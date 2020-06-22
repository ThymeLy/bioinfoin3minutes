## How to choose optimal window size for your genome analysis
The short answer is that the best window size is a balance between statistical power and biological effect size. You need the window to be large enough that you get enough data in it to be able to achieve significance, but you need it to be small enough that it doesn't end up larger than the region whose methylation is changing so you don't get averaging against the surrounding regions.

We also don't generally recommend using fixed size windows (eg 500bp), since the uneven distribution of CpGs within the genome means that different windows will have very different numbers of CpGs within them, and you therefore get a statistical power bias which can mean getting biases in the regions of the genome where you find hits. We tend to prefer defining windows based on the number of CpGs then contain, which then means you get a variation in resolution, but a more even statistical power.
- - simon andrews
from [Sliding window methylation analysis suggestions- SEQanswers](http://seqanswers.com/forums/showthread.php?t=84489)

I think it depends on overall coverage. If you have many many reads, you can set windows quite small, if you have few reads, you'll have to allow large windows. In the case of chromosomes (or contigs) of only 100-1000 bp, then you need many reads. Yoon et al (2009) say the distribution is like a Poisson with overdispersion. I find that the overdispersion is quite strong and so you can't say it is a Poisson distribution. Furthermore, mappability highly influence number of reads per window. In our paper we say that "From our experience in several different samples, selecting window size in which there are 30–180 read counts per window on average strikes a reasonable balance between error variability and bias of CNA"

Basically we have observed that with less than 30 reads per window it gets quite common that you have no reads and you can't tell if it is by chance (and low mappability) or because of actual copy loss. You "hit the bottom" and lose information about that window. On the other side, going above 180 reads per window doesn't do much, but reducing your resolution. Still if you have very high coverage, you can go beyoind that.

In fact, the CNAnorm script that converts bam file to window (bam2window.pl) let you set the size of the window OR the average number of reads in the sample with least reads. It calculates the right window size according to the sum of the chromosomes/contigs length as reported in the header of the sam/bam files.

Also, consider that with very short chromosomes/contigs, you might have some edge effect, as a considerable number of windows will be smaller than the others. 
- -Stefano Berri
from [Choosing Window Size (Sliding Window Approach) During Cnv Analysis By Readdepth Approach](https://www.biostars.org/p/17899/)

[RNA-Seq Analysis Practicals](http://www.bioinformatics.babraham.ac.uk/training/Methylation_Course/Differential%20Methylation%20lecture.pdf)

[Using the DMR Scan Package](http://bioconductor.riken.jp/packages/3.7/bioc/vignettes/DMRScan/inst/doc/DMRScan_vignette.pdf)
