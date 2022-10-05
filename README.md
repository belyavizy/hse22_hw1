# hse22_hw1
### Команды, которые были выполнены на сервере
```shell
seqtk sample -s1002 oil_R1.fastq 5000000 > sub1.fastq
seqtk sample -s1002 oil_R2.fastq 5000000 > sub2.fastq
seqtk sample -s1002 oilMP_S4_L001_R1_001.fastq 1500000 > subR1.fastq
seqtk sample -s1002 oilMP_S4_L001_R2_001.fastq 1500000 > subR2.fastq

mkdir fastqc_wo_trim
mkdir multiqc_wo_trim
ls sub* | xargs -P 4 -tI{} fastqc -o fastqc_wo_trim {}
multiqc -o multiqc_wo_trim/ fastqc_wo_trim/


mkdir fastqc_w_trim
mkdir multiqc_w_trim
rm sub*.fastq
ls sub*.* | xargs -P 4 -tI{} fastqc -o fastqc_w_trim {}
multiqc -o multiqc_w_trim/ fastqc_w_trim/

time platanus assemble –f sub*.trimmed
time platanus scaffold -c out_contig.fa -IP1 *.trimmed -OP2 *.int_trimmed
platanus gap_close -c out_scaffold.fa -IP1 *.trimmed -OP2 *.int_trimmed
rm sub1.fastq.trimmed sub2.fastq.trimmed subR1.fastq.int_trimmed subR2.fastq.int_trimmed
```

### Скриншоты MultiQC
Результаты до обрезания
![image](https://user-images.githubusercontent.com/95979982/194148742-72312503-f8f7-44aa-a906-43cfb05cd9e3.png)
![image](https://user-images.githubusercontent.com/95979982/194152442-bb70b040-814a-43ff-8a71-974f1e2a1549.png)
![image](https://user-images.githubusercontent.com/95979982/194153162-e7408c97-6e63-4208-a539-318931db772c.png)
![image](https://user-images.githubusercontent.com/95979982/194153262-56a4e869-87f3-44d3-8508-b190d8ac7a8a.png)
![image](https://user-images.githubusercontent.com/95979982/194153331-583cbbff-e2f6-4740-ae5f-70c010ae1b00.png)
![image](https://user-images.githubusercontent.com/95979982/194153385-c9727a19-8768-480c-bc3b-9b2a52cf86cf.png)

Результаты после обрезания
![image](https://user-images.githubusercontent.com/95979982/194153711-9db3ec20-b681-4b1e-bdbe-390b953c36de.png)
![image](https://user-images.githubusercontent.com/95979982/194154103-f0a122e9-f5df-48c7-b8a4-277b6fe5f2ed.png)
![image](https://user-images.githubusercontent.com/95979982/194154340-42fdedcc-8968-438c-9468-2fd9cc1c000d.png)
![image](https://user-images.githubusercontent.com/95979982/194155264-97a1b2a2-94a6-478d-afe3-097c21fe1296.png)
![image](https://user-images.githubusercontent.com/95979982/194155417-ccf1ad7f-d930-45fd-8736-b74a3c7a992e.png)
![image](https://user-images.githubusercontent.com/95979982/194155457-fe42f3e6-7657-4c23-b712-9fc9b0396022.png)
![image](https://user-images.githubusercontent.com/95979982/194155519-62172b05-1142-4cd0-8069-10d6b518691c.png)
![image](https://user-images.githubusercontent.com/95979982/194155679-00e0ab5b-48fc-43c8-a0f3-bbacbcca75af.png)
![image](https://user-images.githubusercontent.com/95979982/194155715-f2f50ad7-6d6c-4ba0-999f-721917857f5b.png)

### Ссылка на коллаб с кодом для анализа
[Google Collab](https://colab.research.google.com/drive/1FcyT6aLK6eWTwwlNIvzM10TjOfY2Dy35?usp=sharing)