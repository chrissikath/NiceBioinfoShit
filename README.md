# NiceBioinfoShit

- Gute Seite zur NGS Analyse
https://biomedicalhub.github.io/genomics/02-part2-remapping.html

- SAM documentation
http://samtools.github.io/hts-specs/SAMv1.pdf

- Gute Seite für allgemeine bioinfo Sachen -> Ist ein Buch was irgendwann rauskommen soll 
https://eriqande.github.io/eca-bioinf-handbook/alignment-of-sequence-data-to-a-reference-genome-and-associated-steps.html

## Nützliche Bash Befehle
PS1='[\W]--% '
--> Zeigt dir danach immer an in welchem Ordner man sich befindet

## Mapping, Count etc. 

- Mapping with STAR
  - ist ein Mapping Algorithmus, heißt aligned die paired-end Sequencing files and das Genome 
```
#!/bin/sh    
GENOMEDIR="/home/horn/2021_Celegans/20210902_alex_data/genome/wormbase/STARIndex/
FASTQ="/home/biochemistry/2003KNO-0044/01.RawData/"                                                    
MAPPINGS="/home/christina/results/mappings/"
# mixed                                                                   
for i in $(ls $FASTQ*.fastq.gz | cut -d"_" -f1 | rev | cut -d"/" -f1 | rev | uniq); do  #           
  echo $i                                                                                      
  STAR --genomeDir $GENOMEDIR \ #StarIndex Ordner (muss vorher erstellt werden)
  --readFilesCommand zcat \ 
  --readFilesIn ${FASTQ}${i}_1.fastq.gz ${FASTQ}${i}_2.fastq.gz  \ #paired-end sequenzen
  --runThreadN 20 --outFileNamePrefix "../analysis/$i" \ # output Ordner
  --outSAMtype BAM Unsorted --quantMode GeneCounts \                                                  
  --outSAMstrandField intronMotif                                                     
done
```




