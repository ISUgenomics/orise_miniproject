SeqTech\_LitReview
================
Jennifer Chang
10/2/2020

## Sequencing Technology

  - HiSeq
  - MiSeq
  - NovaSeq
  - Nanopore
  - PacBio

<!-- end list -->

``` r
library(tidyverse)
library(magrittr)

# todo: loop this later
hiseq <- read_delim("csv-HiSeq-set.csv", delim = ",")
miseq <- read_delim("csv-MiSeq-set.csv", delim = ",")
novaseq <- read_delim("csv-NovaSeq-set.csv", delim = ",")
nanopore1 <- read_delim("csv-nanopore-set.csv", delim = ",")
nanopore2 <- read_delim("csv-nanopore-set2.csv", delim = ",")
pacbio <- read_delim("csv-pacbio-set.csv", delim = ",")

names(hiseq) <- names(hiseq) %>% gsub(" ", "_", .) %>% gsub("/", "_", .)
names(miseq) <- names(hiseq) %>% gsub(" ", "_", .)  %>% gsub("/", "_", .)
names(novaseq) <- names(hiseq) %>% gsub(" ", "_", .)  %>% gsub("/", "_", .)
names(nanopore1) <- names(hiseq) %>% gsub(" ", "_", .)  %>% gsub("/", "_", .)
names(nanopore2) <- names(hiseq) %>% gsub(" ", "_", .)  %>% gsub("/", "_", .)
names(pacbio) <- names(hiseq) %>% gsub(" ", "_", .)  %>% gsub("/", "_", .)
```

## Merge Into an Excel File

``` r
hiseq$HiSeq = TRUE
miseq$MiSeq = TRUE
novaseq$NovaSeq = TRUE
nanopore1$Nanopore = TRUE
nanopore2$Nanopore = TRUE
pacbio$PacBio = TRUE

new_columns = c(names(hiseq), "HiSeq", "MiSeq", "NovaSeq", "Nanopore", "PacBio")

# ===== Add column if it's not already there
fncols <- function(data, cname) {
  add <- cname[!cname %in% names(data)]
  if (length(add) != 0) data[add] <- NA
  data
}

formatDf <- function(df, columns) {
  df <- df %>%
    fncols(., columns) %>%
    dplyr::select(all_of(columns))
  return(df)
}

hiseq <- hiseq %>% formatDf(., new_columns)
miseq <- miseq %>% formatDf(., new_columns)
novaseq <- novaseq %>% formatDf(., new_columns)
nanopore1 <- nanopore1 %>% formatDf(., new_columns)
nanopore2 <- nanopore2 %>% formatDf(., new_columns)
pacbio <- pacbio %>% formatDf(., new_columns)

uniqMerge <- function(vc) {
  vc <- vc %>%
    na.omit(.) %>%
    unique(.) %>%
    paste(., collapse = ",", sep = "")
  if (grepl(",", vc)) {
    vc <- vc %>%
      stringr::str_split(., ",", simplify = T) %>%
      as.vector(.) %>%
      unique(.) %>%
      paste(., collapse = ",", sep = "")
  }
  return(vc)
}
names(hiseq)
#>  [1] "PMID"             "Title"            "Authors"          "Citation"        
#>  [5] "First_Author"     "Journal_Book"     "Publication_Year" "Create_Date"     
#>  [9] "PMCID"            "NIHMS_ID"         "DOI"              "HiSeq"           
#> [13] "MiSeq"            "NovaSeq"          "Nanopore"         "PacBio"
merged_df <- dplyr::bind_rows(
  hiseq,
  miseq,
  novaseq,
  nanopore1,
  nanopore2,
  pacbio
) %>%
  dplyr::group_by(PMID) %>%
  dplyr::summarize(
    PMCID = PMCID %>% uniqMerge(.),
    HiSeq = HiSeq %>% uniqMerge(.),
    MiSeq = MiSeq %>% uniqMerge(.),
    NovaSeq = NovaSeq %>% uniqMerge(.),
    Nanopore = Nanopore %>% uniqMerge(.),
    PacBio = PacBio %>% uniqMerge(.),
    Year = Publication_Year %>% uniqMerge(.),
    Title = Title %>% uniqMerge(.),
    Authors = Authors %>% uniqMerge(.),
    Journal_Book = Journal_Book %>% uniqMerge(.),
    Citation = Citation %>% uniqMerge(.),
    DOI = DOI %>% uniqMerge(.),
    Create_Date = Create_Date %>% uniqMerge(.)
  )
#> `summarise()` ungrouping output (override with `.groups` argument)

writexl::write_xlsx(merged_df, path="SeqTech_new.xlsx")
```
