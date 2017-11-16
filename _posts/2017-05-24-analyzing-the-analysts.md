---
title: Analyzing the analysts with tidytext
date: 2017-05-24 14:55
tags: 
  - sdp
  - data
---

The publication of a [Capstone Report](https://sdp.cepr.harvard.edu/fellowship-capstone-reports) is the culmination of the [Strategic Data Project's Fellowship](https://sdp.cepr.harvard.edu/fellowship). These reports highlight the impact Fellows have on their respective education agencies. There are more than thirty Capstone reports on the SDP website, sorted into four broad categories: 

- Data Capacity, Quality, & Culture
- Teacher Effectiveness
- Post-secondary Access & Success
- School Improvement & Redesign

This gives us a general idea of the topics Fellows were covering in their reports, but it would be nice to get a little more detail without having to read more than two dozen reports.

Enter `tidytext`.

I've been meaning to play around with the `tidytext` R package for several months. After seeing a really fun blog post using it to [analyze Seinfeld scripts](http://mdgbeck.netlify.com/post/tidytext-analysis-of-seinfeld/), I decided to try and apply the `tidytext` tools to the SDP Capstone reports, so I read through a few chapters of [Text Mining with R](http://tidytextmining.com/preface.html) and got to work.

## Getting the reports

Getting the text of each Capstone Report wasn't too challenging. I started by parsing the lines of the webpage that you'd use to manually download the PDFs of each capstone report, then I filtered it for all the direct links to each individual PDF. After running a simple for loop, I had all 38 PDFs on my MacBook. Here's the code I used:

```R

library(RCurl)
library(tidyverse)
library(stringr)

# download report pdf's ####

# get content of sdp capstone report webpage
sdp_url <- getURL("https://sdp.cepr.harvard.edu/fellowship-capstone-reports")
sdp_webpage <- readLines(tc <- textConnection(sdp_url)); close(tc)

# create df of webpage content
sdp_df <- tibble(line = 1:360, content = sdp_webpage)

# find and clean links to report pdf's
capstone_links <- sdp_df %>%
  mutate(link_present = str_detect(content, "https://sdp.cepr.harvard.edu/files/cepr-sdp/files/")) %>%
  filter(link_present == TRUE) %>%
  mutate(clean_link = str_extract(content, "https://sdp.cepr.harvard.edu/files/cepr-sdp/files/.+\\.pdf"))

# download report pdfs and save them in '/reports'
for(i in seq_along(1:length(capstone_links$clean_link))){
  
  report_url <- capstone_links$clean_link[i]
  
  download.file(report_url, str_c("reports/capstone", i,".pdf"))
}

```

## Getting the text

After downloading the Capstone Reports, I needed to extract the text in each report, so I relied a function from the `pdftools` package. My code could probably be more efficient and there were some font-related errors, but I was able to extract the text from each report as a series of bigrams and then plot the result. Again, here's the code I used: 


```R 
library(tidyverse)
library(stringr)
library(pdftools)
library(tidytext)
library(ggraph)
library(igraph)

# create empty df
bigram_df <- tibble(word1 = character(), word2 = character(), 
                    n = numeric(), report_num = numeric())

# loop through each capstone pdf
for(k in 1:38){
  
  # parse text from capstone pdf
  report_text <- pdf_text(str_c("reports/capstone", k,".pdf"))
  
  # unnest text into bigrams
  report_bigrams <- tibble(chapter = report_text) %>%
    unnest_tokens(bigram, chapter,token = "ngrams", n = 2)
  
  # split bigrams into separate columns
  bigrams_sep <- report_bigrams %>% 
    separate(bigram, c("word1", "word2"), sep = " ")
  
  # filter out stopwords, numbers, dupes; add count and report number
  bigrams_filtered <- bigrams_sep %>% 
    filter(!word1 %in% stop_words$word) %>% 
    filter(!word2 %in% stop_words$word) %>% 
    filter(!str_detect(word1, "[0-9]")) %>% 
    filter(!str_detect(word2, "[0-9]")) %>% 
    filter(word1 != word2) %>%
    count(word1, word2, sort = TRUE) %>%
    mutate(report_num = k)
  
  # add to df
  bigram_df <- bind_rows(bigram_df, bigrams_filtered)
  
}

# prep data for graphing; only count bigrams w/ n > 20
bigram_graph <- bigram_df %>% 
  filter(n > 20) %>% 
  graph_from_data_frame()

# set arrow type
a <- grid::arrow(type = "closed", length = unit(.15, "inches"))

set.seed(23)

# plot bigram graph
ggraph(bigram_graph, layout = "fr") +
  geom_edge_link(aes(edge_alpha = n), show.legend = FALSE,
                 arrow = a, end_cap = circle(.03, 'inches')) +
  geom_node_point(color = "lightblue", size = 3) +
  geom_node_text(aes(label = name), vjust = 1, hjust = 1) +
  theme_void()

# save plot
ggsave("figures/capstone_bigrams.png", width = 12, height = 8, units = "in")

```
  
![capstone bigrams](https://raw.githubusercontent.com/alspur/capstone_text_analysis/master/figures/capstone_bigrams.png)

The resulting plot paints a nice picture of what SDP Fellows wrote about in their Capstone Reports. There's a lot of focus on college readiness and teacher effectiveness, which were two of the "buckets" on the SDP website, but it's helpful to see what other words were frequently tied to those phrases. It also helps to see what some of the less-popular topics covered. 

The `tidytext` package is a ton of fun to work with - I'm looking forward to using it more and finding new sources of text to analyze!