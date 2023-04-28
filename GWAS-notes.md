# Genome-wide Association Study (GWAS)

Note that most of this information is being pulled from the following paper: <https://www.pnas.org/content/118/40/e2105841118>

## How GWAS is supposed to work

*GWAS* is meant to uncover the genetic basis of complex polygenic traits. It does not predict phenotype based on genotype information, but actually identifies the precise genetic variants that impact the phenotype, which help reveal the biological pathway by which the phenotype occurs. Multivariate models allow us to explain a higher fraction of phenotypic variance, to find new loci, and to identify variants that actually have causal effects. The way we measure error is based on the number of falsely discovered genetic loci and a multiplicity adjustment to control for the effects of a large number of variables. False discovery rate (FDR) is important to control. We expect that amongst many hundreds or thousands of true discoveries, we will have a few false discoveries.

# Challenges of GWAS

## FDR Control

The simplest polygenic model is one that describes phenotype as the result of additive genetic effects, which suggests a linear regression analysis. However, because of there being hundreds of thousands of explanatory variables, the classical linear regression is not a useful method. Penalized regression and Bayesian models have their own shortcomings, and sample splitting results in loss of power AND does not guarantee FDR control.

## Linkage Disequilibrium

Linkage disequilibrium (LD) is the result of strong local dependence between SNPs on the same chromosome. SNPs are chosen to "cover" the genome, and while the actual causal variants might not be observed, the data on the closest SNPs act as proxy. Genotyping platforms generally rely on closely-spaced SNPs whose alleles are strongly dependent. This causes a problem for variable selection, because the signals are all very similar in multivariate regression models. This makes results harder to interpret, especially in terms of controlling for false discoveries.

## Population Structure

Samples lack independence (individuals share some degree of relatedness), inducing long-range LD across the entire genome. This can lead to flase associations, especially if the sample size is large--even weak associations can appear to be statistically significant. 

# GWAS Pipeline


