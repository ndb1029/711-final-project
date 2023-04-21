# 711-final-project
## Nicole, Kim, Megan
My name Megan Buff 
Fecal microbiota transplant (FMT) study. Metabarcoding of human guts

# Overview of pipeline

git clone https://github.com/ndb1029/711-final-project.git

touch testfile.txt
echo 'a test' > testfile.txt 
git add testfile.txt

cp /tmp/gen711_project_data/fastp.sh /home/users/ndb1029/711-final-project/fastp.sh
OR
cp /tmp/gen711_project_data/fastp.sh ~/fastp.sh

chmod +x /home/users/ndb1029/711-final-project/fastp.sh

head fastp.sh 
# read the file

mkdir trimmed_fastq

# ONLY FOWARD READS for fecal 

./fastp-single.sh 150 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-1 /home/users/ndb1029/711-final-project/trimmed_fastqs

./fastp-single.sh 150 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-2 /home/users/ndb1029/711-final-project/trimmed_fastqs


conda activate qiime2-2022.8

qiime tools import \
   --type "SampleData[PairedEndSequencesWithQuality]"  \
   --input-format CasavaOneEightSingleLanePerSampleDirFmt \
   --input-path /home/users/ndb1029/711-final-project/trimmed_fastqs \
   --output-path /home/users/ndb1029/711-final-project/trimmed_fastqs/qiime_fastqs \


   qiime cutadapt trim-paired \
    --i-demultiplexed-sequences qiime_fastqs \
    --p-cores 4 \
    --p-front-f TACGTATGGTGCA \
    --p-discard-untrimmed \
    --p-match-adapter-wildcards \
    --verbose \
    --o-trimmed-sequences /home/users/ndb1029/711-final-project/trimmed_fastqs /qiime_fastqs.qza

qiime demux summarize \
--i-data qiime_fastqs.qza \
--o-visualization /home/users/ndb1029/711-final-project/trimmed_fastqs/qiime_fastqs.qzv 
