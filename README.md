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

# LAB TODAY APRIL 28

cp /tmp/gen711_project_data/fastp-single.sh .
chmod +x fastp-single.sh
./fastp-single.sh 120 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-2 trimmed_fastqs_2

conda activate qiime2-2022.8

# TRIMMED_FASTQ1:

qiime cutadapt trim-single --i-demultiplexed-sequences qiime_trimmed_fastqs_1.qza --p-front TACGTATGGTGCA --p-discard-untrimmed --p-match-adapter-wildcards --verbose --o-trimmed-sequences qiime_fastqs.qza

qiime demux summarize --i-data qiime_fastqs.qza --o-visualization demux1


###denoising
qiime dada2 denoise-single --i-demultiplexed-seqs qiime_fastqs.qza --p-trunc-len 150 --p-trim-left 13 --p-n-threads 4 --o-denoising-stats denoising-stats.qza --o-table feature_table.qza --o-representative-sequences rep-seqs.qza

qiime metadata tabulate --m-input-file denoising-stats.qza --o-visualization denoising-stats.qzv

qiime feature-table tabulate-seqs --i-data rep-seqs.qza --o-visualization rep-seqs.qzv


# .gza files saved under:
/home/users/ndb1029/711-final-project/trimmed_fastqs 
