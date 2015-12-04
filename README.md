# mvicuna
The mvicuna tool for the analysis of viral NGS data

**VICUNA** is a *de novo* assembly program targeting populations with high mutation rates. It creates a single linear representation of the mixed population on which intra-host variants can be mapped. For clinical samples rich in contamination (e.g., >95%), VICUNA can leverage existing genomes, if available, to assemble only target-alike reads. After initial assembly, it can also use existing genomes to perform guided merging of contigs. For each data set (e.g., Illumina paired read, 454), VICUNA outputs consensus sequence(s) and the corresponding multiple sequence alignment of constituent reads. VICUNA efficiently handles ultra-deep sequence data with tens of thousands fold coverage.

## Running **VICUNA**

`mvicuna -h`

```
Parameters
-ipfq: comma separated input paired fastq files; the ith and (i+1)th files form a pair (i is an odd number)
-isfq: comma separated input single end fastq files
-fa: comma separated input single end fasta files
-opfq: comma separated final 2 output fastq paired files
-osfq: final output singleton fastq file
-batch: default 500000; number of sequence (pairs) to be loaded in the memory (>=10000)-pthreads: default 8; number of cores to use
-w, -w2: default 17, 5; sketching window sizes
-lc_n, -lc_mono, -lc_di: default 30, 50, 80; defining low complexity sequence
    max percentage of ambiguous bases, mono nucleotides, and dinucleotides
-tasks: default DupRm,Trim,PairedReadMerge,SFrqEst;
    a list of comma separated tasks {DupRm, Trim, PairedReadMerge, SFrqEst}
-silent: default false; no screen print-out
-noclean: default false; do not remove intermediate files

TASK: DupRm
-drm_op: comma separated output paired fq files post dup rm
-drm_perc_sim: default 98; percent similarity
-drm_max_mismatch: default 5; max mismatches allowed

TASK: PairedReadMerge
-prm_op: 2 comma separated output unmerged fq files
-prm_os: merged single-end fq file

TASK: Trim
-trm_vecfa: input fasta file storing vectors/primers
-trm_op: comma separated output fq paired files
-trm_os: merged single-end fq files
-trm_min_match: default 13; min match b/t vector and a read to be trimmed
-trm_min_rlen: default 70; min read length post-trimming
-trm_q: default 2 (ASCII 35 #); min phred score (ASCII >= 33)

TASK: SFrqEst -- sequence frequency estimation
-fe_k: default 14 (<= 16); substring length to calibrate
```

## Credits
Xiao Yang, Patrick Charlebois, Sante Gnerre, Matthew G Coole, Niall J. Lennon, Joshua Z. Levin, James Qu, Elizabeth M. Ryan, Michael C. Zody, and Matthew R. Henn (2012) De novo assembly of highly diverse viral populations. BMC Genomics 13:475.

## Funding
Support for this tool was provided by the National Institute of Allergy and Infectious Diseases through the Genome Sequencing Center for Infectious Diseases