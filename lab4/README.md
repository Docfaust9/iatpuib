\##Task 1

    df_package <- ls(package:nycflights13)

    ## Warning in ls(package:nycflights13): 'package:nycflights13' converted to
    ## character string

    df_package %>%
      length

    ## [1] 5

\##Task2

    airlines <- nycflights13::airlines
    airports <- nycflights13::airports
    flights <- nycflights13::flights
    planes <- nycflights13::planes
    weather <- nycflights13::weather
    airlines %>% nrow() 

    ## [1] 16

    airports %>% nrow()

    ## [1] 1458

    flights %>% nrow()

    ## [1] 336776

    planes %>% nrow()

    ## [1] 3322

    weather %>% nrow()

    ## [1] 26115

\##Task 3

    airlines %>% ncol() 

    ## [1] 2

    airports %>% ncol()

    ## [1] 8

    flights %>% ncol()

    ## [1] 19

    planes %>% ncol()

    ## [1] 9

    weather %>% ncol()

    ## [1] 15

\##Task 4

    airlines %>% glimpse() 

    ## Rows: 16
    ## Columns: 2
    ## $ carrier <chr> "9E", "AA", "AS", "B6", "DL", "EV", "F9", "FL", "HA", "MQ", "O…
    ## $ name    <chr> "Endeavor Air Inc.", "American Airlines Inc.", "Alaska Airline…

    airports %>% glimpse() 

    ## Rows: 1,458
    ## Columns: 8
    ## $ faa   <chr> "04G", "06A", "06C", "06N", "09J", "0A9", "0G6", "0G7", "0P2", "…
    ## $ name  <chr> "Lansdowne Airport", "Moton Field Municipal Airport", "Schaumbur…
    ## $ lat   <dbl> 41.13047, 32.46057, 41.98934, 41.43191, 31.07447, 36.37122, 41.4…
    ## $ lon   <dbl> -80.61958, -85.68003, -88.10124, -74.39156, -81.42778, -82.17342…
    ## $ alt   <dbl> 1044, 264, 801, 523, 11, 1593, 730, 492, 1000, 108, 409, 875, 10…
    ## $ tz    <dbl> -5, -6, -6, -5, -5, -5, -5, -5, -5, -8, -5, -6, -5, -5, -5, -5, …
    ## $ dst   <chr> "A", "A", "A", "A", "A", "A", "A", "A", "U", "A", "A", "U", "A",…
    ## $ tzone <chr> "America/New_York", "America/Chicago", "America/Chicago", "Ameri…

    flights %>% glimpse() 

    ## Rows: 336,776
    ## Columns: 19
    ## $ year           <int> 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2…
    ## $ month          <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
    ## $ day            <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
    ## $ dep_time       <int> 517, 533, 542, 544, 554, 554, 555, 557, 557, 558, 558, …
    ## $ sched_dep_time <int> 515, 529, 540, 545, 600, 558, 600, 600, 600, 600, 600, …
    ## $ dep_delay      <dbl> 2, 4, 2, -1, -6, -4, -5, -3, -3, -2, -2, -2, -2, -2, -1…
    ## $ arr_time       <int> 830, 850, 923, 1004, 812, 740, 913, 709, 838, 753, 849,…
    ## $ sched_arr_time <int> 819, 830, 850, 1022, 837, 728, 854, 723, 846, 745, 851,…
    ## $ arr_delay      <dbl> 11, 20, 33, -18, -25, 12, 19, -14, -8, 8, -2, -3, 7, -1…
    ## $ carrier        <chr> "UA", "UA", "AA", "B6", "DL", "UA", "B6", "EV", "B6", "…
    ## $ flight         <int> 1545, 1714, 1141, 725, 461, 1696, 507, 5708, 79, 301, 4…
    ## $ tailnum        <chr> "N14228", "N24211", "N619AA", "N804JB", "N668DN", "N394…
    ## $ origin         <chr> "EWR", "LGA", "JFK", "JFK", "LGA", "EWR", "EWR", "LGA",…
    ## $ dest           <chr> "IAH", "IAH", "MIA", "BQN", "ATL", "ORD", "FLL", "IAD",…
    ## $ air_time       <dbl> 227, 227, 160, 183, 116, 150, 158, 53, 140, 138, 149, 1…
    ## $ distance       <dbl> 1400, 1416, 1089, 1576, 762, 719, 1065, 229, 944, 733, …
    ## $ hour           <dbl> 5, 5, 5, 5, 6, 5, 6, 6, 6, 6, 6, 6, 6, 6, 6, 5, 6, 6, 6…
    ## $ minute         <dbl> 15, 29, 40, 45, 0, 58, 0, 0, 0, 0, 0, 0, 0, 0, 0, 59, 0…
    ## $ time_hour      <dttm> 2013-01-01 05:00:00, 2013-01-01 05:00:00, 2013-01-01 0…

    planes %>% glimpse() 

    ## Rows: 3,322
    ## Columns: 9
    ## $ tailnum      <chr> "N10156", "N102UW", "N103US", "N104UW", "N10575", "N105UW…
    ## $ year         <int> 2004, 1998, 1999, 1999, 2002, 1999, 1999, 1999, 1999, 199…
    ## $ type         <chr> "Fixed wing multi engine", "Fixed wing multi engine", "Fi…
    ## $ manufacturer <chr> "EMBRAER", "AIRBUS INDUSTRIE", "AIRBUS INDUSTRIE", "AIRBU…
    ## $ model        <chr> "EMB-145XR", "A320-214", "A320-214", "A320-214", "EMB-145…
    ## $ engines      <int> 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, …
    ## $ seats        <int> 55, 182, 182, 182, 55, 182, 182, 182, 182, 182, 55, 55, 5…
    ## $ speed        <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ engine       <chr> "Turbo-fan", "Turbo-fan", "Turbo-fan", "Turbo-fan", "Turb…

    weather %>% glimpse() 

    ## Rows: 26,115
    ## Columns: 15
    ## $ origin     <chr> "EWR", "EWR", "EWR", "EWR", "EWR", "EWR", "EWR", "EWR", "EW…
    ## $ year       <int> 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013,…
    ## $ month      <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,…
    ## $ day        <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,…
    ## $ hour       <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 13, 14, 15, 16, 17, 18, …
    ## $ temp       <dbl> 39.02, 39.02, 39.02, 39.92, 39.02, 37.94, 39.02, 39.92, 39.…
    ## $ dewp       <dbl> 26.06, 26.96, 28.04, 28.04, 28.04, 28.04, 28.04, 28.04, 28.…
    ## $ humid      <dbl> 59.37, 61.63, 64.43, 62.21, 64.43, 67.21, 64.43, 62.21, 62.…
    ## $ wind_dir   <dbl> 270, 250, 240, 250, 260, 240, 240, 250, 260, 260, 260, 330,…
    ## $ wind_speed <dbl> 10.35702, 8.05546, 11.50780, 12.65858, 12.65858, 11.50780, …
    ## $ wind_gust  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, 20.…
    ## $ precip     <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,…
    ## $ pressure   <dbl> 1012.0, 1012.3, 1012.5, 1012.2, 1011.9, 1012.4, 1012.2, 101…
    ## $ visib      <dbl> 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10,…
    ## $ time_hour  <dttm> 2013-01-01 01:00:00, 2013-01-01 02:00:00, 2013-01-01 03:00…

\##Task 5

    airlines %>%
      select(carrier) %>%
      distinct() %>%
      count()

    ## # A tibble: 1 × 1
    ##       n
    ##   <int>
    ## 1    16

\##Task 6

    a <- airports %>%
      filter(name=='John F Kennedy Intl')%>%
      select(faa)

    flights %>%
      filter(!is.na(time_hour))%>%
      filter(dest==a, time_hour >= as.POSIXct("2013-05-01 00:00:00", tz="UTC"), time_hour <= as.POSIXct("2013-05-31 24:59:59", tz="UTC")) %>%
      count()

    ## Warning in check_tzones(e1, e2): 'tzone' attributes are inconsistent

    ## Warning in check_tzones(e1, e2): 'tzone' attributes are inconsistent

    ## # A tibble: 1 × 1
    ##       n
    ##   <int>
    ## 1     0

\##Task 7

    airports %>%
      filter(lat==max(lat))

    ## # A tibble: 1 × 8
    ##   faa   name                      lat   lon   alt    tz dst   tzone
    ##   <chr> <chr>                   <dbl> <dbl> <dbl> <dbl> <chr> <chr>
    ## 1 EEN   Dillant Hopkins Airport  72.3  42.9   149    -5 A     <NA>

\##Task 8

    airports %>%
      filter(lon==max(lon))

    ## # A tibble: 1 × 8
    ##   faa   name           lat   lon   alt    tz dst   tzone            
    ##   <chr> <chr>        <dbl> <dbl> <dbl> <dbl> <chr> <chr>            
    ## 1 SYA   Eareckson As  52.7  174.    98    -9 A     America/Anchorage

\##Task 9

    planes %>%
      filter(!is.na(year))%>%
      filter(year==min(year))%>%
      select(tailnum)

    ## # A tibble: 1 × 1
    ##   tailnum
    ##   <chr>  
    ## 1 N381AA

\##Task 10

    a <- airports %>%
      filter(name=='John F Kennedy Intl')%>%
      select(faa)

    b<-weather %>%
      filter(origin==a$faa, month==9)%>%
      select(temp)

    5/9*(mean(b$temp)-32)

    ## [1] 19.38764

\##Task 11

    flights%>%
      filter(month==6)%>%
      group_by(carrier)%>%
      summarise(count_flights=length(flight), .groups = "drop")%>%
      arrange(desc(count_flights))%>%
      slice(1:1)

    ## # A tibble: 1 × 2
    ##   carrier count_flights
    ##   <chr>           <int>
    ## 1 UA               4975

\##Task 12

    flights

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_de…¹ dep_d…² arr_t…³ sched…⁴ arr_d…⁵ carrier
    ##    <int> <int> <int>    <int>      <int>   <dbl>   <int>   <int>   <dbl> <chr>  
    ##  1  2013     1     1      517        515       2     830     819      11 UA     
    ##  2  2013     1     1      533        529       4     850     830      20 UA     
    ##  3  2013     1     1      542        540       2     923     850      33 AA     
    ##  4  2013     1     1      544        545      -1    1004    1022     -18 B6     
    ##  5  2013     1     1      554        600      -6     812     837     -25 DL     
    ##  6  2013     1     1      554        558      -4     740     728      12 UA     
    ##  7  2013     1     1      555        600      -5     913     854      19 B6     
    ##  8  2013     1     1      557        600      -3     709     723     -14 EV     
    ##  9  2013     1     1      557        600      -3     838     846      -8 B6     
    ## 10  2013     1     1      558        600      -2     753     745       8 AA     
    ## # … with 336,766 more rows, 9 more variables: flight <int>, tailnum <chr>,
    ## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
    ## #   minute <dbl>, time_hour <dttm>, and abbreviated variable names
    ## #   ¹​sched_dep_time, ²​dep_delay, ³​arr_time, ⁴​sched_arr_time, ⁵​arr_delay

    flights%>%
      filter(year==2013)%>%
      filter(dep_delay>0)%>%
      group_by(carrier)%>%
      summarise(delay_times=length(flight), .groups = "drop")%>%
      arrange(desc(delay_times))%>%
      slice(1:1)

    ## # A tibble: 1 × 2
    ##   carrier delay_times
    ##   <chr>         <int>
    ## 1 UA            27261
