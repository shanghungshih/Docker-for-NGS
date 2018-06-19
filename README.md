# DockerForNGS
This is docker for NGS analysis
https://hub.docker.com/u/adgh456/
- Notes: remember to mount your localPath to container and direct outputPath to specific mounted path of container!
- - -
## NGSMainWES
This contains human genome hg19 fasta, dbsnp138, COSMIC_v38 and some scripts.
1. genome coordinate：ucsc.hg19.fasta
2. dbSNP：dbsnp_138.hg19.vcf
3. COSMIC：CosmicAllMutsHeaderSorted.vcf
4. some scripts
5. seq_bed: agilent_region_OSCC_hg19_rmheader.bed (v2 only)
6. gnomad: gnomad.exomes.r2.0.2.sites.vcf.bgz (v3 only)
```
sudo docker pull adgh456/ngs-main:wes
sudo docker pull adgh456/ngs-main:wes_v2
```
- Usage:
```
sudo docker run --rm -v $localPath:/ref_data -i adgh456/ngs-main:wes_v2 mv /box_ref_data/* /box_scripts/* /ref_data
```
## AfterQC
This is for pair-end NGS raw data auto-trimming and it'll output good, bad fastq and a html report. (using pypy to accelerate operation)
```
sudo docker pull adgh456/afterqc:afterqc_pypy2
```
- Usage:
```
sudo docker run --rm -v $localPath:/AfterQC/data -i adgh456/afterqc:afterqc_pypy2 pypy after.py -h
```
## Bwa
This is for fasta indexing, fastq data alignment and generate sam file.
```
sudo docker pull adgh456/bwa:0.7.15
```
- Usage:
```
sudo docker run --rm -v $localPath:/data -i adgh456/bwa:0.7.15 bwa --help
```
## Samtools
This is for building index for fasta, sam, bam...
```
sudo docker pull adgh456/samtools:1.3.1
# or
sudo docker pull adgh456/samtools:0.1.19
```
- Usage:
```
sudo docker run --rm -v $localPath:/data -i adgh456/samtools:1.3.1 samtools --help
```
## Picard
This is for building fasta dict.
```
sudo docker pull adgh456/picard:2.9.0-1-gf5b9f50-SNAPSHOT
```
- Usage:
```
sudo docker run --rm -v $localPath:/data -i adgh456/picard:2.9.0-1-gf5b9f50-SNAPSHOT java -jar picard.jar --help
```
## GATK3
gatk-v3.8-registered image was already registered. No need to register everytime.
```
sudo docker pull adgh456/gatk:gatk-v3.8-registered
```
- Usage:
```
sudo docker run --rm -v $localPath:/data -i adgh456/gatk:gatk-v3.8-registered gatk --help
```
## GATK4
```
sudo docker pull broadinstitute/gatk:4.0.4.0
```
- Usage:
```
sudo docker run --rm -v $localPath:/gatk/data -i broadinstitute/gatk:4.0.4.0 gatk --help
```
## GATK for CNV
This is for copy number variant detection.
```
sudo docker pull adgh456/gatk:1.0.0.0-alpha1.2.3
```
- Usage:
```
sudo docker run --rm -v $localPath:/gatk-protected-1.0.0.0-alpha1.2.3/data -i adgh456/gatk:1.0.0.0-alpha1.2.3 java -jar /gatk-protected-1.0.0.0-alpha1.2.3/build/libs/gatk-protected.jar --help
```
## MSIsensor
This is for Microsatellite Instability detection.
```
sudo docker pull adgh456/msisensor:0.2
```
- Usage:
```
sudo docker run --rm -v $localPath:/data -i adgh456/msisensor:0.2 msisensor --help
```
## Breakmer
This is for Structural variants detection.
```
sudo docker pull adgh456/breakmer:v0.0.2
```
## Meerkat
This is for Structural variants detection.
```
sudo docker pull adgh456/meerkat:v0.189
```
## Phial
This is for FDA-approved drug annotation and visualization (input: maf.txt from Oncotator).
```
sudo docker pull adgh456/phial:v1.0
```
## NCBI-edirect
This is for access NCBI API (ex. get NM).
```
sudo docker pull adgh456/edirect
```
## NCBI-remap
This is for NCBI coordinates remap.
```
sudo docker pull adgh456/tools:ncbi-remap
```
## bam-reheader
This is for bam reheader.
```
sudo docker pull adgh456/tools:bam-reheader
```
