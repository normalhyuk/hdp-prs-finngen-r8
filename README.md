# PRS model for hypertensive disorders of pregnancy
Jung, S. H., Kim, H., Jung, Y. M., Shivakumar, M., …, Kim, D. & Lee, S. M. (2024) Cardiovascular risk according to healthy lifestyle with genetic predisposition of hypertensive disorders of pregnancy.

---

### Hypertensive disorders of pregnancy ([O15_HYPTENSPREG](https://r8.finngen.fi/pheno/O15_HYPTENSPREG))
> [FinnGen_r8_PRScs_auto.gz](https://github.com/dokyoonkimlab/hdp-prs-finngen-r8/blob/main/prs-model/015_HYPTENSPREG_FinnGen_r8_PRScs_auto.gz)

## Data Source (GWAS summary statistics)
- **FinnGen Release 8 (R8):** Includes association data at 20,175,454 variants for 2,202 endpoints based on 342,499 Finnish individuals (190,879 females and 151,620 males).
- **HDP Cases:** Identified using ICD codes:  
  - ICD-8: `63701`, `63703`, `63704`, `63709`, `63710`, `63799`, `66120`  
  - ICD-9: `642`  
  - ICD-10: `O10`, `O11`, `O13`, `O14`, `O15`, `O16`
  - **Result:** 13,071 cases and 177,808 controls.
- **GWAS Analysis:** Performed by FinnGen using **SAIGE**, adjusting for:
  - Sex
  - Age
  - 10 principal components (PCs)
  - Genotyping batch

## PRS Generation
### 1. Data Preparation
- FinnGen summary statistics were mapped from **GRCh38** to **GRCh37/hg19** using the [liftOver tool](https://genome.ucsc.edu/cgi-bin/hgLiftOver) to ensure compatibility with UK Biobank genotyped data (GRCh37/hg19).

### 2. PRS Construction
- **Bayesian Prediction Method:**  
  We used [**PRS-CS**](https://github.com/getian107/PRScs) to infer the posterior mean effect size of variants, leveraging the **1000 Genomes Project (phase 3 EUR)** as the external linkage disequilibrium (LD) reference panel.
  - A total of 1,102,676 mapped variants were used.
- **Computation:**  
  Individual PRSs were calculated as a weighted sum of risk alleles using beta coefficients from PRS-CS. This was implemented using [**PLINK v1.90**](https://www.cog-genomics.org/plink/) with the `–score` command.

## References
1.	Kurki, Mitja I., et al. "FinnGen provides genetic insights from a well-phenotyped isolated population." _Nature_ **613.7944** (2023): 508-518.
2.	Zhou, Wei, et al. "Efficiently controlling for case-control imbalance and sample relatedness in large-scale genetic association studies." _Nature genetics_ **50.9** (2018): 1335-1341.
3.	Nassar, Luis R., et al. "The UCSC genome browser database: 2023 update." _Nucleic acids research_ **51.D1** (2023): D1188-D1195.
4.	Ge, Tian, et al. "Polygenic prediction via Bayesian regression and continuous shrinkage priors." _Nature communications_ **10.1** (2019): 1776.
5.	Chang, Christopher C., et al. "Second-generation PLINK: rising to the challenge of larger and richer datasets." _Gigascience_ **4.1** (2015): s13742-015.

