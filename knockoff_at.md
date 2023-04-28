## Background Information: what is KnockoffGWAS?

**Knockoffs** are a feature for variable selection, originally introduced for linear regression. Knockoffs can largely be understood as *negative controls*, or in experimental terms, a group that does not receive a treatment and should show no change over the course of the experiment. In slightly more statistical terms, knockoffs contain the property that you cannot distinguish the knockoff from the real vector without looking at the response vector. This allows for greater type 1 error (false discovery rate) control.

**GWAS** (genome-wide association study) is an approach where markers (SNPs) are scanned across complete genomes of many different individuals to find genetic variants associated with a specific phenotype. Typically this is useful for finding genetic variants that contribute to complex diseases or traits. However, because of linkage disequilibrium, this makes GWAS tricky to interpret. LD describes the degree to which an allele of one genetic variant is inherited or correlated with an allele of a nearby genetic variant within a given population. Due to this, some of the variants that show up more frequently in individuals with the phenotype than those without (meaning they are "associated") do not actually directly cause the phenotype, but are just "tagging along" with the real causal variants. Usually, to filter out the noise, we would have to do finer mapping and sequencing.

This is where *KnockoffGWAS* comes in.

**KnockoffGWAS** is used to identify causal variants for complex (polygenic) traits via genome-wide fine-mapping while also accounting for linkage disequilibrium and false discovery rate. Where most GWAS is univariate, *KnockoffGWAS* is a multivariate algorithm that compares multiple variables at one time while also not making parametric assumptions about the unknown relation between genotypes and phenotype. Genotypes are treated as random samples from a model. A generation of imperfect copies of these variables, or knockoffs, serve as negative controls. This means we can correct for linkage disequilibrium AND account for unknown population structure, while also being able to leverage powerful multivariate algorithms to analyze large-scale data sets.

**Our goal:** We want to apply knockoff statistical methods, previously proven on human genomes, to plant genomes. We think that *Arabidopsis thaliana* would be a good organism to model this technique on because of its thorough and complete documentation. We also hope to expand on the window size within which the *KnockoffGWAS* algorithm scans for SNPs to allow for greater customizability and precision. Essentially, we are interested in where exactly the "hit" is coming from--is it within an exon, an intron? etc.

For a nice tutorial and more information about the source code for Knockoff GWAS, take a look at [this repository](https://github.com/msesia/knockoffgwas).Previously this pipeline has been used to analyze genetic data in the [UK Biobank](https://msesia.github.io/knockoffgwas/ukbiobank.html).

## Generating Knockoffs

## 
