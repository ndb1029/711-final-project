# 711-final-project

# Metabarcoding of human guts: Fecal microbiota transplant (FMT) study
  By: Nicole Benjamin, Megan Buff & Kim Bonanno
  
# Background
  The Fecal Microbiome Transplant study subdataset was adapted from research paper "Microbiota Transfer Therapy alters gut ecosystem and improves gastrointestinal and autism symptoms: an open-label study" (Kang et al., 2017). In this study, researchers are trying to identify if a fecal microbiome transplant would help alleviate both autisim spectrum disorder and gastrointestinal symptoms.
 
  Autism Spectrum Disorder (ASD) is a developmental disability which has a wide range of symptoms depending on the individual. The severity of ASD is assesed by several different system. Kang utilized Autism Diagnostic Interview-Revised (ADI-R), the Parent Global Impressions-III (PGI-III), and Childhood Autism Rating Scale (CARS). There has been a correlation with individuals with ASD tend to have more gastrointestinal problems than those who do not have ASD (Hsiao et al., 2014). The Gastrointestinal(GI) Tract consists of all of the organs which foods and liquids travel from digestion to excretion. It has been found that ASD individuals most commonly experience the following sympotms: chronic constipation, abdominal pain, and diarrhea. 

# Methods
  Researchers were testing whether a fecal microbiota transplant would alleviate both the severity of GI and ASD symptoms. To test this, thirty eight individuals under the age of 18 were enrolled in this study. These individuals had both ASD and GI problems. Twenty of these indiviudals were used as a control and the other eighteen were the experimental group and underwent a transplant. Data was then collected over eighteen weeks. 
  
  Data collection consisted primarily from fecal sample swabs, and ocassionally stool samples. Parents were then asked to rate their child's ASD symptoms and severity of GI problems. Using the samples, microbial DNA was extracted using PowerSoil® DNA Isolation Kit (Kang et al., 2017). A librray was then prepped and a barcoded primer set was used to sequence, identify, then amplify the 16S rRNA V4 region of the microbial DNA.
  
  A subset of Kang's data was then extracted to utilzie in the QUIIME 2 exercise. This subset of data consists of a total of ten individuals. Then, between six and sixteen samples per individual were added to the dataset. 
  
  As a group, we downloaded the fastq file to our RON computer cluster. Using the conda envionrment we trimmed and preparred the two samples for further analyzation. Next, we denoised the data using the quiime enviornment. When the samples were ready, we continued to use quiime features to obtain infographics and data on the taxonomy and diversity of our samples. We used https://view.qiime2.org to visualize any files that were obtained.

# Findings
## Barplots of Taxonomy
<img width="1073" alt="Screenshot 2023-05-14 at 7 30 09 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/350bec14-8052-4cb2-bd15-b05e06e1a45c">
  Table 1. This table lists the bacteria identified in each of the samples. 

<img width="1077" alt="Screenshot 2023-05-14 at 7 30 16 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/5aaca985-ed42-491f-b3dc-ccd862881cb7">
  Figure 1. A barplot graph comparing Sample Type metadata across treatments, stool, and swabs. Sample 1 focuses on treatment and stool. While sample 2 focuses on stool and swabs. Sample 2 is more general as purple is more prominent, indicating that actinobacteria is present.
  
<img width="1047" alt="Screenshot 2023-05-16 at 4 02 54 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/02ec5d7b-3efc-4121-b7db-e0337bd38bc4">
  Figure 2. These two barplots are comparing microbiota diversity between control group to treatment group. Sample 2 is more general than sample 1 as it mostly contains generalized bacteria and Actinobacteria.

<img width="1026" alt="Screenshot 2023-05-16 at 4 03 04 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/4e32019c-f1b5-49fb-804e-b78f6806a1e0">
  Figure 3. These barplots compare the microbiota of ages between both samples. Sample 1 has a clear trend of similar bacteria based on age. Age 8.1 has primarily one type of bacteria, as seen in orange. Age 10.7 has primarily Actinobacteria. And age 12.5 has primarily Bacteria, Firmicutes, Clostridia, and Clostridiales.

<img width="1028" alt="Screenshot 2023-05-16 at 4 03 13 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/0b74f0f1-0da8-448a-ab87-d94a6f4568f6">
  Figure 4. These boxplots compare microbiota across weight among sample 1 and 2. Samples with 50 kg primarily have related bacteria as denoted by orange. Samples with 63 kg primarily has Bacteria, Firmicutes, Clostridia, and Clostridiales. 


## Alpha Diversity
<img width="1059" alt="Screenshot 2023-05-16 at 4 04 22 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/90945c09-d82e-499a-ae34-7b3a7896869c">
<img width="1068" alt="Screenshot 2023-05-16 at 4 04 03 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/4a889c90-b764-44ba-ad7c-16a9440f31ff">
<img width="1084" alt="Screenshot 2023-05-16 at 4 04 33 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/71a59d62-c5d9-4530-bf13-79555574c8fc">


## PCA Analysis
<img width="1029" alt="Screenshot 2023-05-14 at 7 29 45 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/397d1d39-bdf0-48de-bca4-db79ec6afb8d">
<img width="1070" alt="Screenshot 2023-05-16 at 4 05 03 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/1ddc3b7c-8831-47de-91a3-8ba42a14b09f">


# Citations
  Kang, DW., Adams, J.B., Gregory, A.C. et al. Microbiota Transfer Therapy alters gut ecosystem and improves gastrointestinal and autism symptoms: an open-label study.Microbiome 5, 10 (2017). https://doi.org/10.1186/s40168-016-0225-7
  
  Hsiao, Elaine Y PhD. Gastrointestinal Issues in Autism Spectrum Disorder. Harvard Review of Psychiatry 22(2):p 104-111, March/April 2014. | DOI: 10.1097/HRP.0000000000000029
 


# Presentation 
