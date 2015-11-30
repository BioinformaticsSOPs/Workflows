Option 1: GATK Best Practices
Tools:
Trimmomatic
FastQC
PicardTools
GATK
TRAMS

Workflow:
0. download/setup 
 1. reference genome (fasta) 
 2. reference GBK
 3. dbSNP (or blank.vcf if none)
1. Trimmomatic   #assuming Truseq3 adapters, single ended, adapt as needed ILLUMINACLIP:TruSeq3-SE:2:30:10 LEADING:3 TRAILING:3 MINLEN:75
2.Fastqc
3. BWA mem to reference genome (using read groups)
4. PICARDTOOLS
 1. SortSAM
 2. MarkDuplicates
 3. BuildBamIndex
5. GATK
 1. RealignerTargetCreator
 2. IndelRealigner
 3. BaseRecalibrator -o prelimTable
 4. BaseRecalibrator -BQSR -o post_proc
 5. PrintReads 
6. Picardtools
 1. BuildBamIndex
7. GATK 
 1. HaplotypeCaller
 2. if multiple samples:
  1. CombineGVCFs
  2. GenotypeGVCFs
 3. VariantAnnotator
 4. VariantEval
 5. VariantsToTable
8. TRAMS (plus custom script)
 1. custom perl vcf2trams.pl (makes trams compatable file)
 2. TRAMS.py 

