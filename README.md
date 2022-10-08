# hse22_hw1


### Создаем ссылки
```bash
ln -s /usr/share/data-minor-bioinf/assembly/*.fastq
```
### Ставим SEED=912 и выбираем соучайные чтения
```bash
seqtk sample -s$SEED oil_R1.fastq 5000000 > sub1.fastq
seqtk sample -s$SEED oil_R2.fastq 5000000 > sub2.fastq
seqtk sample -s$SEED oilMP_S4_L001_R1_001.fastq 1500000 > matep1.fastq
seqtk sample -s$SEED oilMP_S4_L001_R2_001.fastq 1500000 > matep2.fastq
```

###Оценка чтений с помощью FastQ
```bash
mkdir fastqc
ls sub* matep* | xargs -tI{} fastqc -o fastqc {}
```

###Создаем отчет с помощью MultiQ
```bash
mkdir multiqc
multiqc -o multiqc fastqc
```

###Отчет

###Обрезаем чтения
platanus_trim sub*
platanus_internal_trim matep*



