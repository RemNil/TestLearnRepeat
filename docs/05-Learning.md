# Learning

According to the [published data](https://open.fda.gov/) from the U.S. Food and Drug Administration (FDA), there are [ShinyAPP openFDA](https://openfda.shinyapps.io/RR_D/).

## Why learn at all?
[NCATS](https://pubs.acs.org/doi/pdf/10.1021/acsptsci.9b00056)

## What to learn first?
[Intriguing](http://serayamaouche.net/code/R/Rcode.html)

## How to learn best?


```
## Fetching: https://api.fda.gov/drug/event.json?search=&count=patient.patientonsetage
```

```
## Fetching: https://api.fda.gov/drug/event.json?search=patient.drug.openfda.generic_name:quetiapine&api_key=ex0HLx7faxU5MnmTGJ9GqIRiS2qf0oP6KY8KzF3F&count=seriousnesscongenitalanomali
```

```
## Fetching: https://api.fda.gov/drug/event.json?search=&api_key=ex0HLx7faxU5MnmTGJ9GqIRiS2qf0oP6KY8KzF3F&count=patient.patientonsetage
```

<img src="05-Learning_files/figure-html/unnamed-chunk-1-1.png" width="672" />

```
## Fetching: https://api.fda.gov/drug/event.json?search=patient.drug.openfda.generic_name:quetiapine&api_key=ex0HLx7faxU5MnmTGJ9GqIRiS2qf0oP6KY8KzF3F&count=patient.drug.drugindication
```

```
## 'data.frame':	100 obs. of  2 variables:
##  $ term : chr  "disorder" "unknown" "indication" "for" ...
##  $ count: int  31444 25378 25377 25370 23727 23684 16416 16393 8068 7140 ...
```

<img src="05-Learning_files/figure-html/unnamed-chunk-1-2.png" width="672" />
