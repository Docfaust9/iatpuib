    library(dplyr)

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

    starwars

    ## # A tibble: 87 × 14
    ##    name        height  mass hair_…¹ skin_…² eye_c…³ birth…⁴ sex   gender homew…⁵
    ##    <chr>        <int> <dbl> <chr>   <chr>   <chr>     <dbl> <chr> <chr>  <chr>  
    ##  1 Luke Skywa…    172    77 blond   fair    blue       19   male  mascu… Tatooi…
    ##  2 C-3PO          167    75 <NA>    gold    yellow    112   none  mascu… Tatooi…
    ##  3 R2-D2           96    32 <NA>    white,… red        33   none  mascu… Naboo  
    ##  4 Darth Vader    202   136 none    white   yellow     41.9 male  mascu… Tatooi…
    ##  5 Leia Organa    150    49 brown   light   brown      19   fema… femin… Aldera…
    ##  6 Owen Lars      178   120 brown,… light   blue       52   male  mascu… Tatooi…
    ##  7 Beru White…    165    75 brown   light   blue       47   fema… femin… Tatooi…
    ##  8 R5-D4           97    32 <NA>    white,… red        NA   none  mascu… Tatooi…
    ##  9 Biggs Dark…    183    84 black   light   brown      24   male  mascu… Tatooi…
    ## 10 Obi-Wan Ke…    182    77 auburn… fair    blue-g…    57   male  mascu… Stewjon
    ## # … with 77 more rows, 4 more variables: species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>, and abbreviated variable names
    ## #   ¹​hair_color, ²​skin_color, ³​eye_color, ⁴​birth_year, ⁵​homeworld

    starwars<-starwars

## Task 1

    starwars %>% 
      nrow()

    ## [1] 87

## Task 2

    starwars %>% 
      ncol()

    ## [1] 14

## Task 3

    starwars %>% 
      glimpse()

    ## Rows: 87
    ## Columns: 14
    ## $ name       <chr> "Luke Skywalker", "C-3PO", "R2-D2", "Darth Vader", "Leia Or…
    ## $ height     <int> 172, 167, 96, 202, 150, 178, 165, 97, 183, 182, 188, 180, 2…
    ## $ mass       <dbl> 77.0, 75.0, 32.0, 136.0, 49.0, 120.0, 75.0, 32.0, 84.0, 77.…
    ## $ hair_color <chr> "blond", NA, NA, "none", "brown", "brown, grey", "brown", N…
    ## $ skin_color <chr> "fair", "gold", "white, blue", "white", "light", "light", "…
    ## $ eye_color  <chr> "blue", "yellow", "red", "yellow", "brown", "blue", "blue",…
    ## $ birth_year <dbl> 19.0, 112.0, 33.0, 41.9, 19.0, 52.0, 47.0, NA, 24.0, 57.0, …
    ## $ sex        <chr> "male", "none", "none", "male", "female", "male", "female",…
    ## $ gender     <chr> "masculine", "masculine", "masculine", "masculine", "femini…
    ## $ homeworld  <chr> "Tatooine", "Tatooine", "Naboo", "Tatooine", "Alderaan", "T…
    ## $ species    <chr> "Human", "Droid", "Droid", "Human", "Human", "Human", "Huma…
    ## $ films      <list> <"The Empire Strikes Back", "Revenge of the Sith", "Return…
    ## $ vehicles   <list> <"Snowspeeder", "Imperial Speeder Bike">, <>, <>, <>, "Imp…
    ## $ starships  <list> <"X-wing", "Imperial shuttle">, <>, <>, "TIE Advanced x1",…

## Task 4

    starwars %>% 
      select(species) %>%
      na.omit() %>% 
      distinct() 

    ## # A tibble: 37 × 1
    ##    species       
    ##    <chr>         
    ##  1 Human         
    ##  2 Droid         
    ##  3 Wookiee       
    ##  4 Rodian        
    ##  5 Hutt          
    ##  6 Yoda's species
    ##  7 Trandoshan    
    ##  8 Mon Calamari  
    ##  9 Ewok          
    ## 10 Sullustan     
    ## # … with 27 more rows

## Task 5

    starwars %>% 
      filter(height==max(na.omit(height)))

    ## # A tibble: 1 × 14
    ##   name        height  mass hair_c…¹ skin_…² eye_c…³ birth…⁴ sex   gender homew…⁵
    ##   <chr>        <int> <dbl> <chr>    <chr>   <chr>     <dbl> <chr> <chr>  <chr>  
    ## 1 Yarael Poof    264    NA none     white   yellow       NA male  mascu… Quermia
    ## # … with 4 more variables: species <chr>, films <list>, vehicles <list>,
    ## #   starships <list>, and abbreviated variable names ¹​hair_color, ²​skin_color,
    ## #   ³​eye_color, ⁴​birth_year, ⁵​homeworld

## Task 6

    starwars %>% 
      filter(height<170)

    ## # A tibble: 23 × 14
    ##    name        height  mass hair_…¹ skin_…² eye_c…³ birth…⁴ sex   gender homew…⁵
    ##    <chr>        <int> <dbl> <chr>   <chr>   <chr>     <dbl> <chr> <chr>  <chr>  
    ##  1 C-3PO          167    75 <NA>    gold    yellow      112 none  mascu… Tatooi…
    ##  2 R2-D2           96    32 <NA>    white,… red          33 none  mascu… Naboo  
    ##  3 Leia Organa    150    49 brown   light   brown        19 fema… femin… Aldera…
    ##  4 Beru White…    165    75 brown   light   blue         47 fema… femin… Tatooi…
    ##  5 R5-D4           97    32 <NA>    white,… red          NA none  mascu… Tatooi…
    ##  6 Yoda            66    17 white   green   brown       896 male  mascu… <NA>   
    ##  7 Mon Mothma     150    NA auburn  fair    blue         48 fema… femin… Chandr…
    ##  8 Wicket Sys…     88    20 brown   brown   brown         8 male  mascu… Endor  
    ##  9 Nien Nunb      160    68 none    grey    black        NA male  mascu… Sullust
    ## 10 Watto          137    NA black   blue, … yellow       NA male  mascu… Toydar…
    ## # … with 13 more rows, 4 more variables: species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>, and abbreviated variable names
    ## #   ¹​hair_color, ²​skin_color, ³​eye_color, ⁴​birth_year, ⁵​homeworld

## Task 7

    starwars %>% mutate(imt=mass/(height^2))

    ## # A tibble: 87 × 15
    ##    name        height  mass hair_…¹ skin_…² eye_c…³ birth…⁴ sex   gender homew…⁵
    ##    <chr>        <int> <dbl> <chr>   <chr>   <chr>     <dbl> <chr> <chr>  <chr>  
    ##  1 Luke Skywa…    172    77 blond   fair    blue       19   male  mascu… Tatooi…
    ##  2 C-3PO          167    75 <NA>    gold    yellow    112   none  mascu… Tatooi…
    ##  3 R2-D2           96    32 <NA>    white,… red        33   none  mascu… Naboo  
    ##  4 Darth Vader    202   136 none    white   yellow     41.9 male  mascu… Tatooi…
    ##  5 Leia Organa    150    49 brown   light   brown      19   fema… femin… Aldera…
    ##  6 Owen Lars      178   120 brown,… light   blue       52   male  mascu… Tatooi…
    ##  7 Beru White…    165    75 brown   light   blue       47   fema… femin… Tatooi…
    ##  8 R5-D4           97    32 <NA>    white,… red        NA   none  mascu… Tatooi…
    ##  9 Biggs Dark…    183    84 black   light   brown      24   male  mascu… Tatooi…
    ## 10 Obi-Wan Ke…    182    77 auburn… fair    blue-g…    57   male  mascu… Stewjon
    ## # … with 77 more rows, 5 more variables: species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>, imt <dbl>, and abbreviated variable
    ## #   names ¹​hair_color, ²​skin_color, ³​eye_color, ⁴​birth_year, ⁵​homeworld

## Task 8

    starwars %>% 
      mutate(vyt=mass/height) %>%
      arrange(vyt) %>% 
      slice(1:10)

    ## # A tibble: 10 × 15
    ##    name        height  mass hair_…¹ skin_…² eye_c…³ birth…⁴ sex   gender homew…⁵
    ##    <chr>        <int> <dbl> <chr>   <chr>   <chr>     <dbl> <chr> <chr>  <chr>  
    ##  1 Ratts Tyer…     79    15 none    grey, … unknown      NA male  mascu… Aleen …
    ##  2 Wicket Sys…     88    20 brown   brown   brown         8 male  mascu… Endor  
    ##  3 Wat Tambor     193    48 none    green,… unknown      NA male  mascu… Skako  
    ##  4 Yoda            66    17 white   green   brown       896 male  mascu… <NA>   
    ##  5 Sly Moore      178    48 none    pale    white        NA <NA>  <NA>   Umbara 
    ##  6 Adi Gallia     184    50 none    dark    blue         NA fema… femin… Corusc…
    ##  7 Padmé Amid…    165    45 brown   light   brown        46 fema… femin… Naboo  
    ##  8 Barriss Of…    166    50 black   yellow  blue         40 fema… femin… Mirial 
    ##  9 Ayla Secura    178    55 none    blue    hazel        48 fema… femin… Ryloth 
    ## 10 Shaak Ti       178    57 none    red, b… black        NA fema… femin… Shili  
    ## # … with 5 more variables: species <chr>, films <list>, vehicles <list>,
    ## #   starships <list>, vyt <dbl>, and abbreviated variable names ¹​hair_color,
    ## #   ²​skin_color, ³​eye_color, ⁴​birth_year, ⁵​homeworld

## Task 9

    starwars %>% 
      filter_at(vars(species, birth_year), all_vars(!is.na(.))) %>%
      group_by(species) %>% 
      summarise(mean_age = mean(birth_year), .groups = 'drop')

    ## # A tibble: 15 × 2
    ##    species        mean_age
    ##    <chr>             <dbl>
    ##  1 Cerean             92  
    ##  2 Droid              53.3
    ##  3 Ewok                8  
    ##  4 Gungan             52  
    ##  5 Human              53.4
    ##  6 Hutt              600  
    ##  7 Kel Dor            22  
    ##  8 Mirialan           49  
    ##  9 Mon Calamari       41  
    ## 10 Rodian             44  
    ## 11 Trandoshan         53  
    ## 12 Twi'lek            48  
    ## 13 Wookiee           200  
    ## 14 Yoda's species    896  
    ## 15 Zabrak             54

## Task 10

    starwars %>% 
      filter(!is.na(eye_color)) %>%
      count(eye_color, sort = TRUE) %>%
      slice(1:1)

    ## # A tibble: 1 × 2
    ##   eye_color     n
    ##   <chr>     <int>
    ## 1 brown        21

## Task 11

    starwars %>% 
      filter_at(vars(species, name), all_vars(!is.na(.))) %>%
      group_by(species) %>% 
      summarise(mean_name = mean(nchar(name)), .groups = 'drop')

    ## # A tibble: 37 × 2
    ##    species   mean_name
    ##    <chr>         <dbl>
    ##  1 Aleena        13   
    ##  2 Besalisk      15   
    ##  3 Cerean        12   
    ##  4 Chagrian      10   
    ##  5 Clawdite      10   
    ##  6 Droid          4.83
    ##  7 Dug            7   
    ##  8 Ewok          21   
    ##  9 Geonosian     17   
    ## 10 Gungan        11.7 
    ## # … with 27 more rows
