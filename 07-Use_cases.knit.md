# Use cases


## Quetiapine



### Adverse events: Quetiapine






### Clinical Trials: Quetiapine







### Pubmed search: Quetiapine

















FDA Adverse Event Reporting System ([FAERS](https://open.fda.gov/data/faers/)). [Here](https://open.fda.gov/apis/drug/event/) is quick explanation:
<!--html_preserve--><div id="htmlwidget-c137d8aa3337360b0032" style="width:100%;height:400px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c137d8aa3337360b0032">{"x":{"visdat":{"52f0163c4486":["function () ","plotlyVisDat"]},"cur_data":"52f0163c4486","attrs":{"52f0163c4486":{"x":{},"y":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Adverse drug events reported to FDA for quetiapine","xaxis":{"domain":[0,1],"automargin":true,"title":"","categoryorder":"count","categoryarray":[16416,16393,8068,7140,6399,5202,4795,3798,3229,2536,2131,1885,1780,1744,1671,1658,1373,1328,1326,1304,1293,1265,1240,1119,1095,1078,992,972,954,926,896,859,852,846,834,800,799,798,794,761,705,695,666,635,634,604,585,576,573,572,569,558,554,520,518],"type":"category"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Events reported"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["depression","bipolar","anxiety","schizophrenia","sleep","insomnia","pain","hypertension","psychotic","parkinson","diabetes","dementia","schizoaffective","gastrooesophageal","affective","hallucination","arthritis","agitation","sclerosis","hyperactivity","infection","attention","stress","traumatic","hypothyroidism","pulmonary","narcolepsy","rheumatoid","mood","constipation","asthma","delusion","migraine","psychosis","mania","muscle","panic","hepatitis","cancer","cardiac","nausea","personality","fibromyalgia","epilepsy","paranoid","obsessive","thyroid","compulsive","convulsion","crohn","thrombosis","attack","psoriasis","myeloma","headache"],"y":[16416,16393,8068,7140,6399,5202,4795,3798,3229,2536,2131,1885,1780,1744,1671,1658,1373,1328,1326,1304,1293,1265,1240,1119,1095,1078,992,972,954,926,896,859,852,846,834,800,799,798,794,761,705,695,666,635,634,604,585,576,573,572,569,558,554,520,518],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script><!--/html_preserve--> To better understand what this data means, we need to really dig into the openFDA API.


<!--html_preserve--><div id="htmlwidget-6d8ec6e7b39c4718b951" style="width:100%;height:400px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-6d8ec6e7b39c4718b951">{"x":{"data":[{"orientation":"v","width":[0.9,0.9,0.9,0.9,0.9,0.9,0.9,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999,0.899999999999999],"base":[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],"x":[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29],"y":[1,1,3,2,11,21,22,44,64,100,98,150,184,228,261,291,314,259,259,280,277,283,310,256,302,287,258,248,190],"text":["Year: 1991<br />Counts:   1","Year: 1992<br />Counts:   1","Year: 1993<br />Counts:   3","Year: 1994<br />Counts:   2","Year: 1995<br />Counts:  11","Year: 1996<br />Counts:  21","Year: 1997<br />Counts:  22","Year: 1998<br />Counts:  44","Year: 1999<br />Counts:  64","Year: 2000<br />Counts: 100","Year: 2001<br />Counts:  98","Year: 2002<br />Counts: 150","Year: 2003<br />Counts: 184","Year: 2004<br />Counts: 228","Year: 2005<br />Counts: 261","Year: 2006<br />Counts: 291","Year: 2007<br />Counts: 314","Year: 2008<br />Counts: 259","Year: 2009<br />Counts: 259","Year: 2010<br />Counts: 280","Year: 2011<br />Counts: 277","Year: 2012<br />Counts: 283","Year: 2013<br />Counts: 310","Year: 2014<br />Counts: 256","Year: 2015<br />Counts: 302","Year: 2016<br />Counts: 287","Year: 2017<br />Counts: 258","Year: 2018<br />Counts: 248","Year: 2019<br />Counts: 190"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(21,122,202,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(255,255,255,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Types of PubMed records containing 'Quetiapine' = 5004","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,29.6],"tickmode":"array","ticktext":["1991","1992","1993","1994","1995","1996","1997","1998","1999","2000","2001","2002","2003","2004","2005","2006","2007","2008","2009","2010","2011","2012","2013","2014","2015","2016","2017","2018","2019"],"tickvals":[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29],"categoryorder":"array","categoryarray":["1991","1992","1993","1994","1995","1996","1997","1998","1999","2000","2001","2002","2003","2004","2005","2006","2007","2008","2009","2010","2011","2012","2013","2014","2015","2016","2017","2018","2019"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-35,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"<br /> Year <br /> Query date: 2019-11-24 11:12:39","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-15.7,329.7],"tickmode":"array","ticktext":["0","100","200","300"],"tickvals":[0,100,200,300],"categoryorder":"array","categoryarray":["0","100","200","300"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Types of articles","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":"transparent","line":{"color":"rgba(51,51,51,1)","width":0.66417600664176,"linetype":"solid"},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"52f030741718":{"x":{},"y":{},"type":"bar"}},"cur_data":"52f030741718","visdat":{"52f030741718":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->


[SUSAR](https://bi.ema.europa.eu/analyticsSOAP/saw.dll?PortalPages&PortalPath=%2Fshared%2FPHV%20DAP%2F_portal%2FDAP&Action=Navigate&P0=1&P1=eq&P2=%22Line%20Listing%20Objects%22.%22Substance%20High%20Level%20Code%22&P3=1+21689)

[EudraVigil](http://www.adrreports.eu/de/search_subst.html#)

## Enasidenib

## Deep Brain Stimulation 


### Clinical Trials: DBS







### Pubmed search: DBS












