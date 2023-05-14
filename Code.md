# CODE

## FASTQ Sample QA/QC

### For File 2

    cp /tmp/gen711_project_data/fastp-single.sh .
    chmod +x fastp-single.sh
    ./fastp-single.sh 120 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-2 trimmed_fastqs_2
    conda activate qiime2-2022.8
    qiime tools import --type "SampleData[PairedEndSequencesWithQuality]" --input-format CasavaOneEightSingleLanePerSampleDirFmt --input-path /home/users/ndb1029/711-final-project/trimmed_fastqs --output-path /home/users/ndb1029/711-final-project/trimmed_fastqs/qiime_fastqs
    qiime cutadapt trim-single --i-demultiplexed-sequences qiime_trimmed_fastqs_1.qza --p-front TACGTATGGTGCA --p-discard-untrimmed --p-match-adapter-wildcards --verbose --o-trimmed-sequences qiime_fastqs.qza
    qiime demux summarize --i-data qiime_fastqs.qza --o-visualization demux1


### Denoising File 2
    qiime dada2 denoise-single --i-demultiplexed-seqs qiime_fastqs.qza --p-trunc-len 150 --p-trim-left 13 --p-n-threads 4 --o-denoising-stats denoising-stats.qza --o-table feature_table.qza --o-representative-sequences rep-seqs.qza
    qiime metadata tabulate --m-input-file denoising-stats.qza --o-visualization denoising-stats.qzv
    qiime feature-table tabulate-seqs --i-data rep-seqs.qza --o-visualization rep-seqs.qzv


### For File 1:
    conda activate genomics
    cp /tmp/gen711_project_data/fastp-single.sh .
    chmod +x fastp-single.sh
    ./fastp-single.sh 120 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-1 trimmed_fastqs_1
    conda activate qiime2-2022.8
    qiime tools import --type "SampleData[SequencesWithQuality]" --input-format CasavaOneEightSingleLanePerSampleDirFmt --input-path /home/users/ndb1029/711-final-project/trimmed_fastqs_1 --output-path qiime_trimmed_fastqs_1
    qiime cutadapt trim-single --i-demultiplexed-sequences qiime_trimmed_fastqs_1.qza --p-front TACGTATGGTGCA --p-discard-untrimmed --p-match-adapter-wildcards --verbose --o-trimmed-sequences qiime_fastqs1.qza
    qiime demux summarize --i-data qiime_fastqs1.qza --o-visualization demux_1

### Denoising File 1
    qiime dada2 denoise-single --i-demultiplexed-seqs qiime_fastqs1.qza --p-trunc-len 50 --p-trim-left 13 --p-n-threads 4 --o-denoising-stats denoising-stats.qza --o-table feature_table.qza --o-representative-sequences rep-seqs.qza
    qiime metadata tabulate --m-input-file denoising-stats.qza --o-visualization denoising-stats.qzv
    qiime feature-table tabulate-seqs --i-data rep-seqs.qza --o-visualization rep-seqs.qzv
    
    
# Taxonomy
  conda activate qiime2-2022.8

    qiime feature-table merge-seqs --i-data /home/users/ndb1029/711-final-project/gza_files_1/rep-seqs.qza --i-data /home/users/ndb1029/711-final-project/trimmed_fastqs/rep-seqs.qza --o-merged-data /home/users/ndb1029/711-final-project/Taxonomy/table/merged.rep-seqs.qza

    qiime feature-classifier classify-sklearn --i-classifier /tmp/gen711_project_data/reference_databases/classifier.qza --i-reads /home/users/ndb1029/711-final-project/Taxonomy/table/merged.rep-seqs.qza --o-classification /home/users/ndb1029/711-final-project/Taxonomy/classifier/FMT-taxonomy.qza


    qiime taxa barplot --i-table /home/users/ndb1029/711-final-project/gza_files_1/feature_table.qza --i-taxonomy /home/users/ndb1029/711-final-project/Taxonomy/classifier/FMT-taxonomy.qza --o-visualization /home/users/ndb1029/711-final-project/Taxonomy/barplot1/barplot-1.qzv


    qiime taxa barplot --i-table /home/users/ndb1029/711-final-project/trimmed_fastqs/feature_table.qza --i-taxonomy /home/users/ndb1029/711-final-project/Taxonomy/classifier/FMT-taxonomy.qza --o-visualization /home/users/ndb1029/711-final-project/Taxonomy/barplot2/barplot-2.qzv
    
    
# Taxonomy Plots 
![level-7-bars-2](https://user-images.githubusercontent.com/130377747/235944118-d5ec5bd2-8c5a-49cd-bab1-49c9ca4f8a96.svg)
![level-7-bars](https://user-images.githubusercontent.com/130377747/235944124-410505f8-da6d-4a54-b0d8-d692a458b38e.svg)


# Metadata for sample 1
    cp /tmp/gen711_project_data/FMT_3/sample-metadata.tsv /home/users/ndb1029/711-final-project
    qiime taxa barplot --i-table /home/users/ndb1029/711-final-project/gza_files_1/feature_table.qza --m-metadata-file sample-metadata.tsv --i-taxonomy /home/users/ndb1029/711-final-project/Taxonomy/classifier/FMT-taxonomy.qza --o-visualization my-barplot.qzv

    qiime phylogeny align-to-tree-mafft-fasttree --i-sequences /home/users/ndb1029/711-final-project/trimmed_fastqs/rep-seqs.qza --o-alignment alignments --o-masked-alignment masked-alignment --o-tree unrooted-tree --o-rooted-tree rooted-tree --p-n-threads 4

    qiime diversity core-metrics-phylogenetic --i-phylogeny /home/users/ndb1029/711-final-project/trimmed_fastqs/rooted-tree.qza --i-table feature_table.qza --p-sampling-depth 500 --m-metadata-file sample-metadata.tsv --p-n-jobs-or-threads 4 --output-dir core-metrics

    qiime feature-table relative-frequency --i-table /home/users/ndb1029/711-final-project/trimmed_fastqs/core-metrics/rarefied_table.qza --o-relative-frequency-table relative_rarefied_table

    qiime diversity pcoa-biplot --i-features /home/users/ndb1029/711-final-project/trimmed_fastqs/core-metrics/relative_rarefied_table.qza --i-pcoa /home/users/ndb1029/711-final-project/trimmed_fastqs/core-metrics/unweighted_unifrac_pcoa_results.qza --o-biplot unweighted_unifrac_pcoa_biplot

    qiime emperor biplot --i-biplot /home/users/ndb1029/711-final-project/trimmed_fastqs/core-metrics/unweighted_unifrac_pcoa_biplot.qza --m-sample-metadata-file sample-metadata.tsv --o-visualization unweighted_unifrac_pcoa_biplot

    qiime diversity alpha-group-significance --i-alpha-diversity /home/users/ndb1029/711-final-project/trimmed_fastqs/core-metrics/shannon_vector.qza --m-metadata-file sample-metadata.tsv --o-visualization alpha-group-significance

    qiime diversity beta-group-significance --i-distance-matrix /home/users/ndb1029/711-final-project/trimmed_fastqs/core-metrics/unweighted_unifrac_distance_matrix.qza --m-metadata-file sample-metadata.tsv  --m-metadata-column <column_in_metadata_that_groups_replicates> --p-pairwise --o-visualization unweighted_unifrac-beta-group-significance




# Metadata for Sample 2:
    qiime taxa barplot --i-table /home/users/ndb1029/711-final-project/trimmed_fastqs/feature_table.qza --m-metadata-file sample-metadata.tsv --i-taxonomy /home/users/ndb1029/711-final-project/Taxonomy/classifier/FMT-taxonomy.qza --o-visualization my-barplot2.qzv

    qiime phylogeny align-to-tree-mafft-fasttree --i-sequences /home/users/ndb1029/711-final-project/gza_files_1/rep-seqs.qza --o-alignment alignments --o-masked-alignment masked-alignment --o-tree unrooted-tree --o-rooted-tree rooted-tree --p-n-threads 4

    qiime diversity core-metrics-phylogenetic --i-phylogeny /home/users/ndb1029/711-final-project/gza_files_1/rooted-tree.qza --i-table feature_table.qza --p-sampling-depth 500 --m-metadata-file sample-metadata.tsv --p-n-jobs-or-threads 4 --output-dir core-metrics

    cp /tmp/gen711_project_data/FMT_3/sample-metadata.tsv /home/users/ndb1029/711-final-project/gza_files_1/core-metrics

    qiime feature-table relative-frequency --i-table /home/users/ndb1029/711-final-project/gza_files_1/core-metrics/rarefied_table.qza --o-relative-frequency-table relative_rarefied_table

    qiime diversity pcoa-biplot --i-features /home/users/ndb1029/711-final-project/gza_files_1/core-metrics/relative_rarefied_table.qza --i-pcoa /home/users/ndb1029/711-final-project/gza_files_1/core-metrics/unweighted_unifrac_pcoa_results.qza --o-biplot unweighted_unifrac_pcoa_biplot

    qiime emperor biplot --i-biplot /home/users/ndb1029/711-final-project/gza_files_1/core-metrics/unweighted_unifrac_pcoa_biplot.qza --m-sample-metadata-file sample-metadata.tsv --o-visualization unweighted_unifrac_pcoa_biplot

    qiime diversity alpha-group-significance --i-alpha-diversity /home/users/ndb1029/711-final-project/gza_files_1/core-metrics/shannon_vector.qza --m-metadata-file sample-metadata.tsv --o-visualization alpha-group-significance


