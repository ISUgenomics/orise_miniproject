# ORISE Miniproject

## Introduction

### Why search for a minimal genome?

Small genome organisms provide a practice dataset for genome assembly, and can hint at a minimal gene set for a living organism. For example, Craig Venter's group was examining small-genome organisms to identify a "minimal genome" and "synthesize a working genome from scratch" ([Nature article](https://www.nature.com/news/2006/061009/full/news061009-10.html#:~:text=How%20small%20can%20a%20genome,and%20182%20protein-coding%20genes)). Since many of the single cell organisms have already been explored, I restricted my minimal-genome organism search to plant or insect species.

### What plant or insect has a minimal genome?

For plant species, the smallest nuclear genome seemed to be the bladderwort (Utricularia gibba) with a length of 82Mb ([Ibarra-Laclette et al, 2013](ttps://pubmed.ncbi.nlm.nih.gov/23665961/)) or more recently 100Mb ([Lan et al, 2017](https://pubmed.ncbi.nlm.nih.gov/28507139/)). The bladderwort plants are carnivorous (insect eating), which might explain nutrient-processing gene loss, and its short genome length. However while the nucleotide length seems to be among the smallest plant genomes, the number of genes are quite high (25K?) (cite or link) with at least 2 whole genome duplication events from near species grape and tomato. Since bladderwort sits in freshwater ponds, catching insects in little bladders, several of the genes may be related to defense against an aquatic environment. It's possible that grape may be a more appropriate minimal-genome test subject.

There are [several bioprojects](https://www.ncbi.nlm.nih.gov/bioproject/?term=utricularia+gibba) associated with bladderwort including isolating regulatory elements for other crop species ([PRJNA595351](https://www.ncbi.nlm.nih.gov/bioproject/595351)). 

For insect species, the smallest genome seems to be the arctic midge with an estimated genome length of 96Mb (find citation here). However since the arctic midge is only located in Antarctica, obtaining a sample might be difficult. Midges that are currently being sequenced in the [ag100pest project](http://i5k.github.io/ag100pest) include Oat stem midge (Mayetiola avenae) and Barley stem midge (Mayetiola hordei).  

## Methods

### Genome Sequencing

Utricularia gibba (bladderwort) tissue was obtained from X at 

Evaluate: 

* PacBio
* NovaSeq
* HiC

### Genome Assembly


## References


### genome_assembly

* Kadota, M., Nishimura, O., Miura, H., Tanaka, K., Hiratani, I. and Kuraku, S., 2020. [Multifaceted Hi-C benchmarking: what makes a difference in chromosome-scale genome scaffolding?](https://pubmed.ncbi.nlm.nih.gov/31919520/). GigaScience, 9(1), p.giz158.

### Bladderwort

Full genome assembly from PacBio reads in 2017

* Lan, T., Renner, T., Ibarra-Laclette, E., Farr, K.M., Chang, T.H., Cervantes-Pérez, S.A., Zheng, C., Sankoff, D., Tang, H., Purbojati, R.W. and Putra, A., 2017. [Long-read sequencing uncovers the adaptive topography of a carnivorous plant genome](https://pubmed.ncbi.nlm.nih.gov/28507139/). Proceedings of the National Academy of Sciences, 114(22), pp.E4435-E4441.

Method from above:

* U. gibba tissue from Michoacan, Mexico, kept in sterile tissue culture
* DNA sequenced via Pacific Biosciences (PacBio) Single Molecule, Real-Time (SMRT) technology, 10 SMRT cells, P6-C4 PacBio chemistry
  * agarose gel
  * SYBR Safe (Invitrogen)
  * Covaris g-TUBE
  * 0.45X AMPure PB Beads (PacBio)
  * Library prep by PacBio 2020kb SMRTbell Template Preparation Protocol
    * Price for kit? [https://www.pacb.com/products-and-services/consumables/template-preparation-multiplexing-kits/](https://www.pacb.com/products-and-services/consumables/template-preparation-multiplexing-kits/) Might just need to contact them and get a quote.
* HGAP.3 assembly
* Genome features annotated and analyized
* GO enrichment

Earlier genome assembly in 2013

* Ibarra-Laclette, E., Lyons, E., Hernández-Guzmán, G., Pérez-Torres, C.A., Carretero-Paulet, L., Chang, T.H., Lan, T., Welch, A.J., Juárez, M.J.A., Simpson, J. and Fernández-Cortés, A., 2013. [Architecture and evolution of a minute plant genome](https://pubmed.ncbi.nlm.nih.gov/23665961/). Nature, 498(7452), pp.94-98.

# Discussion


<details><summary>organize later</summary>
Learning Materials

* Overview of sequencing technology: https://youtu.be/mI0Fo9kaWqo
* Illumina NovaSeq vs Nanopore demonstration: https://youtu.be/rA8MUR4pqNE 
* ISU sequencing costs: http://www.biotech.iastate.edu/biotechnology-service-facilities/dna-facility/#rates
* How to calculate coverage
* Table of DNA sequencers, number and length of reads: https://en.wikipedia.org/wiki/List_of_DNA_sequencers 
* How to calculate costs? Price it by amount of DNA/coverage (determine budget)
  
  
* Additionally, Bladdarwort plants are sold online for $10/plant. I'm not sure how to obtain midge insects and picking more than one sequencing methods (e.g. Nanopore, NovaSeq) would provide a comparison of cost, read quality, and genome assembly methods. A 82Mb organism could be sequenced for about $4500 cost (estimated budget attached)

Recent Bladderwort Publications:

* Morris, R.J. and Blyth, M., 2019. How water flow, geometry, and material properties drive plant movements. Journal of experimental botany, 70(14), pp.3549-3560.
* Ravee, R., Salleh, F.I.M. and Goh, H.H., 2018. Discovery of digestive enzymes in carnivorous plants with focus on proteases. PeerJ, 6, p.e4914.
* Hepler, N.K., Bowman, A., Carey, R.E. and Cosgrove, D.J., 2020. Expansin gene loss is a common occurrence during adaptation to an aquatic environment. The Plant Journal, 101(3), pp.666-680.


* Cost: $9.95/plant  https://carnivorousplantnursery.com/products/utricularia-vulgaris: 
(https://carnivorousplantnursery.com/collections/bladderworts/products/utricularia-gibba )
* Publications seem to focus on minimal genome, digestive protease enzymes (applications to molecular biology?), and gene loss in aquatic plants.

</details>
