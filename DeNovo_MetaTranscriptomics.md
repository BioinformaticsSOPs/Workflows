Software:

|Tools | Download Link | License|
|-----|---------------| -------|
|Trimmomatic/FastQC | | |
|BWA | | |
|TransSPADES| | |
|Salmon| | |
|EdgeR/DESeq| | |
|TransRate| |  |


*Additional Suggestions (@blahah404):
for assembly use:
IDBA-tran
SOAPDenovo-tran
RNAspades

Use: assemblotron to find best values for assembly
https://github.com/Blahah/assemblotron

use: Transfuse to merge transcripts
https://github.com/cboursnell/transfuse*

Workflow:
1. Trim/QA/QC (should be its own module)
2. TransSpades
3. TransRate (?)
4. bwa reads to assembly
5. Salmon on BAM
6. EdgeR/DeSeq on Salmon outputs


