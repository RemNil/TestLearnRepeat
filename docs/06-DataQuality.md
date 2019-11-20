# Data quality

## OpenFDA
According to the [published data](https://open.fda.gov/) from the U.S. Food and Drug Administration (FDA), there are about 10.5 million drug adverse event reports [(Nov. 2019)](https://open.fda.gov/about/statistics/) reported to the [FDA](https://www.fda.gov/).



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

It seems there is a problem in that the text data is parsed into n-grams without due diligence with regard to the meaning of the operation. For example, "diabetes" and "mellitus" are listed as distinct terms (althoug with different frequencies).




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




## Quetiapine
FDA Adverse Event Reporting System ([FAERS](https://open.fda.gov/data/faers/)). [Here](https://open.fda.gov/apis/drug/event/) is quick explanation:
<!--html_preserve--><div id="htmlwidget-38db2e763a0997477178" style="width:100%;height:400px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-38db2e763a0997477178">{"x":{"visdat":{"432413071c80":["function () ","plotlyVisDat"]},"cur_data":"432413071c80","attrs":{"432413071c80":{"x":{},"y":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Adverse drug events reported to FDA for quetiapine","xaxis":{"domain":[0,1],"automargin":true,"title":"","categoryorder":"count","categoryarray":[16416,16393,8068,7140,6399,5202,4795,3798,3229,2536,2131,1885,1780,1744,1671,1658,1373,1328,1326,1304,1293,1265,1240,1119,1095,1078,992,972,954,926,896,859,852,846,834,800,799,798,794,761,705,695,666,635,634,604,585,576,573,572,569,558,554,520,518],"type":"category"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Events reported"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["depression","bipolar","anxiety","schizophrenia","sleep","insomnia","pain","hypertension","psychotic","parkinson","diabetes","dementia","schizoaffective","gastrooesophageal","affective","hallucination","arthritis","agitation","sclerosis","hyperactivity","infection","attention","stress","traumatic","hypothyroidism","pulmonary","narcolepsy","rheumatoid","mood","constipation","asthma","delusion","migraine","psychosis","mania","muscle","panic","hepatitis","cancer","cardiac","nausea","personality","fibromyalgia","epilepsy","paranoid","obsessive","thyroid","compulsive","convulsion","crohn","thrombosis","attack","psoriasis","myeloma","headache"],"y":[16416,16393,8068,7140,6399,5202,4795,3798,3229,2536,2131,1885,1780,1744,1671,1658,1373,1328,1326,1304,1293,1265,1240,1119,1095,1078,992,972,954,926,896,859,852,846,834,800,799,798,794,761,705,695,666,635,634,604,585,576,573,572,569,558,554,520,518],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script><!--/html_preserve--> To better understand what this data means, we need to really dig into the openFDA API.

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

