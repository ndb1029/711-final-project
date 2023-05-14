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
<img width="1077" alt="Screenshot 2023-05-14 at 7 30 16 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/5aaca985-ed42-491f-b3dc-ccd862881cb7">

## Alpha Diversity
<img width="1071" alt="Screenshot 2023-05-14 at 7 29 55 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/ffa5a645-7982-497b-a925-eaa1ea1f0a44">

## PCA Analysis
<img width="1029" alt="Screenshot 2023-05-14 at 7 29 45 PM" src="https://github.com/ndb1029/711-final-project/assets/130377747/397d1d39-bdf0-48de-bca4-db79ec6afb8d">


# Citations
  Kang, DW., Adams, J.B., Gregory, A.C. et al. Microbiota Transfer Therapy alters gut ecosystem and improves gastrointestinal and autism symptoms: an open-label study.Microbiome 5, 10 (2017). https://doi.org/10.1186/s40168-016-0225-7
  
  Hsiao, Elaine Y PhD. Gastrointestinal Issues in Autism Spectrum Disorder. Harvard Review of Psychiatry 22(2):p 104-111, March/April 2014. | DOI: 10.1097/HRP.0000000000000029
 


# Presentation 
