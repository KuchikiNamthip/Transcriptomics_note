For RNA-seq analysis, you'll need both a reference genome and gene annotations. The most commonly used options are:

# Reference Genomes:
    1. GENCODE/Ensembl:
        - `Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz`: Preferred by many RNA-seq pipelines due to comprehensive annotations
    2. UCSC:
        - `hg38.fa.gz` from the UCSC Genome Browser: Uses "chr" prefix in chromosome names

# Gene Annotations:
    1. GENCODE:
        - gencode.v44.annotation.gtf.gz (or latest version)
        - Considered the gold standard for human gene annotations
        - Provides comprehensive annotation of coding and non-coding genes

    2. Ensembl:
        - Homo_sapiens.GRCh38.110.gtf.gz (or latest version)
        - GENCODE annotations are actually integrated into Ensembl

    3. RefSeq:
        - From NCBI
        - More conservative annotations focusing on well-supported transcripts

# Note
    - For RNA-seq analysis, it's important to use matching reference genome and annotation files (both using the same assembly version). Many researchers prefer the GENCODE/Ensembl combination for RNA-seq because it provides the most comprehensive set of annotated genes and transcripts.
    
    - When using these files in tools like STAR, HISAT2, or Salmon, you'll need to create indices from both the reference genome and annotation files.