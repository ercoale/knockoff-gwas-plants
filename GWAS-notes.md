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

## GWAS Pipeline

The standard approach is to identify promising signals for the association of a phenotype with one variant at a time via a linear model. Population structure is corrected for with aditional covariates, such as top principal compenents of the genotype matrix. P values are the threshold to control for the familywise error rate (FWER), or the probability of at least 1 false positive when multiple comparisons are being tested, such as Bonferroni corretion and Tukey HSD test.Variants associated with the phenotype and highly correlated with one another are clustered into distinct groups to avoid redundancy. 

The results of the univariate tests are then used as input for fine mapping and polygenic risk scores. Fine mapping identifies causal variants among similarly associated SNPs in LD, and polygenic risk scores are predictors of a trait for future samples based on a large number of genetic variants across the genome (I assume this means how many times you predict to find your trait?). This method, however, does not guarantee control over type-I errors, and results are difficult to interpret and actual causal variants nowhere to be found. 

# KnockoffGWAS

## Knockoffs

Knockoffs are randomly generated negative control variables that are indistinguishable from the original null variables (not directly associated with the phenotype). Because they are interchangeable, we can find variants that actually influence the phenotype because their association with the phenotype will be significantly stronger than those of their knockoffs. A knockoff filter is an algorithm that computes the knockoff-based significance threshold, which controls FDR--this filter can be applied to any association statistics. For the knockoff filter, a a model for the distribution of the original variables is needed.

## Knockoff Methodology

