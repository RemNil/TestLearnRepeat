# Pharmacovigiliance

## OpenFDA
According to the [published data](https://open.fda.gov/) from the U.S. Food and Drug Administration (FDA), there are about 10.5 million drug adverse event reports [(Nov. 2019)](https://open.fda.gov/about/statistics/) reported to the [FDA](https://www.fda.gov/).

## Pharmacovigiliance
To analyse pharmacovigilance (adverse drug event) data, there are several national and international databases for Open Science. [EMA EudraVigilance](http://www.adrreports.eu/de/index.html) is not open accessible due to data protection concerns but academic institutions can apply on [request](https://www.ema.europa.eu/en/human-regulatory/research-development/pharmacovigilance/eudravigilance/access-eudravigilance-data). [WHO VigiBase] is the largest database with over 20 million anonymized reports of suspected adverse effects submitted since 1968. It is not publicly accessible.

(http://www.adrreports.eu/de/search_subst.html#)[Quetiapine EudraVigilance)

[OpenVigil 2.1-MedDRA](http://openvigil.sourceforge.net/) contains th U.S. american FDA Adverse Event Reporting System (AERS, mostly domestic data) and BfArM data from 2005 to 9/2015.



```r
library(openfda)
Numb_query = fda_query("/drug/event.json") %>%
             fda_api_key("ex0HLx7faxU5MnmTGJ9GqIRiS2qf0oP6KY8KzF3F") %>%
             fda_count("patient.drug.drugindication");

quetia_num = Numb_query %>% fda_filter("patient.drug.openfda.generic_name", "quetiapine") %>% fda_exec()
```

```
## Fetching: https://api.fda.gov/drug/event.json?search=patient.drug.openfda.generic_name:quetiapine&api_key=ex0HLx7faxU5MnmTGJ9GqIRiS2qf0oP6KY8KzF3F&count=patient.drug.drugindication
```

It seems there is a problem in that the text data is parsed into n-grams without due diligence with regard to the meaning of the operation. For example, "diabetes" and "mellitus" are listed as distinct terms (although with different frequencies).




```r
library(dplyr)
library(plotly)

                           
indica.terms <- c("depression", "bipolar", "anxiety", "schizophrenia", "sleep", "insomnia",
                  "pain", "hypertension", "psychotic", 
                  "parkinson", "diabetes","dementia",
                  "schizoaffective", "gastrooesophageal", 
                  "affective", "hallucination",
                  "arthritis", "agitation", "sclerosis", 
                  "hyperactivity", "infection",	
                  "attention", "stress", "traumatic", 
                  "hypothyroidism", "pulmonary",
                  "narcolepsy", "rheumatoid","mood", 
                  "constipation", "asthma", "delusion",
                  "migraine", "psychosis", "mania", "muscle", 
                  "panic", "hepatitis", "cancer",
                  "cardiac", "nausea", "personality", 
                  "fibromyalgia", "epilepsy", "paranoid",
                  "obsessive", "thyroid", "compulsive", 
                  "convulsion", "crohn", "thrombosis",
                  "attack", "psoriasis", "myeloma", 
                  "headache")

quetiapine_sAE <- filter(quetia_num, quetia_num$term %in% indica.terms) %>% arrange(desc(count))
  

sapply(quetiapine_sAE, class)
```

```
##        term       count 
## "character"   "integer"
```




### Data cleaning
If we run a search on the official release of the [FDA data](https://open.fda.gov/) using the [openFDA R package](https://github.com/rOpenHealth/openfda), we obtain a lot of nonsense data. For example, for [quetiapine](https://en.wikipedia.org/wiki/Quetiapine), we see that there are frequencies returned for terms such as "disorder", "unknown", "indication", "for", "product", etc. However, what we would want is simply a list with medical indications and the frequency of reported [sAE](https://en.wikipedia.org/wiki/Serious_adverse_event).




term                 count
------------------  ------
disorder             31444
unknown              25378
indication           25377
for                  25370
product              23727
used                 23684
depression           16416
bipolar              16393
anxiety               8068
schizophrenia         7140
sleep                 6399
disease               6103
insomnia              5202
pain                  4795
hypertension          3798
s                     3670
psychotic             3229
therapy               3082
drug                  2797
blood                 2689
parkinson             2536
type                  2464
prophylaxis           2216
diabetes              2131
i                     2028
mellitus              2006
use                   1927
dementia              1885
reflux                1781
schizoaffective       1780
gastrooesophageal     1744
affective             1671
cholesterol           1669
hallucination         1658
multiple              1551
major                 1511
abnormal              1401
arthritis             1373
agitation             1328
sclerosis             1326
hyperactivity         1304
infection             1293
attention             1265
increased             1257
stress                1240
deficit               1200
syndrome              1190
post                  1161
traumatic             1119
chronic               1097
hypothyroidism        1095
mental                1092
pulmonary             1078
pressure              1041
narcolepsy             992
rheumatoid             972
mood                   954
constipation           926
cessation              924
smoking                922
asthma                 896
delusion               859
migraine               852
psychosis              846
back                   844
mania                  834
muscle                 800
panic                  799
hepatitis              798
c                      794
cancer                 794
of                     789
cardiac                761
supplementation        731
nausea                 705
cell                   697
personality            695
fibromyalgia           666
2                      659
epilepsy               635
paranoid               634
behaviour              630
obsessive              604
atrial                 600
fibrillation           592
obstructive            585
thyroid                585
compulsive             576
convulsion             573
crohn                  572
thrombosis             569
vitamin                568
tube                   563
defect                 561
neural                 559
attack                 558
psoriasis              554
contraception          523
myeloma                520
headache               518



### Further readings
[ShinyAPP openFDA](https://openfda.shinyapps.io/RR_D/).

[ICH M2 EWG](https://admin.ich.org/sites/default/files/inline-files/ICH_ICSR_Specification_V2-3.pdf)



term                 count
------------------  ------
disorder             31444
unknown              25378
indication           25377
for                  25370
product              23727
used                 23684
depression           16416
bipolar              16393
anxiety               8068
schizophrenia         7140
sleep                 6399
disease               6103
insomnia              5202
pain                  4795
hypertension          3798
s                     3670
psychotic             3229
therapy               3082
drug                  2797
blood                 2689
parkinson             2536
type                  2464
prophylaxis           2216
diabetes              2131
i                     2028
mellitus              2006
use                   1927
dementia              1885
reflux                1781
schizoaffective       1780
gastrooesophageal     1744
affective             1671
cholesterol           1669
hallucination         1658
multiple              1551
major                 1511
abnormal              1401
arthritis             1373
agitation             1328
sclerosis             1326
hyperactivity         1304
infection             1293
attention             1265
increased             1257
stress                1240
deficit               1200
syndrome              1190
post                  1161
traumatic             1119
chronic               1097
hypothyroidism        1095
mental                1092
pulmonary             1078
pressure              1041
narcolepsy             992
rheumatoid             972
mood                   954
constipation           926
cessation              924
smoking                922
asthma                 896
delusion               859
migraine               852
psychosis              846
back                   844
mania                  834
muscle                 800
panic                  799
hepatitis              798
c                      794
cancer                 794
of                     789
cardiac                761
supplementation        731
nausea                 705
cell                   697
personality            695
fibromyalgia           666
2                      659
epilepsy               635
paranoid               634
behaviour              630
obsessive              604
atrial                 600
fibrillation           592
obstructive            585
thyroid                585
compulsive             576
convulsion             573
crohn                  572
thrombosis             569
vitamin                568
tube                   563
defect                 561
neural                 559
attack                 558
psoriasis              554
contraception          523
myeloma                520
headache               518



### Further readings
[ShinyAPP openFDA](https://openfda.shinyapps.io/RR_D/).

