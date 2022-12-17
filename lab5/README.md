    install.packages('dplyr')

    ## Installing package into '/cloud/lib/x86_64-pc-linux-gnu-library/4.2'
    ## (as 'lib' is unspecified)

    install.packages('stringr')

    ## Installing package into '/cloud/lib/x86_64-pc-linux-gnu-library/4.2'
    ## (as 'lib' is unspecified)

\##Intro

    library(dplyr)

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

    library(stringr)

\##Create and format data

    dns<-read.csv('dns.log',sep='\t')
    colnames(dns)<-c('timestamp', 'uid', 'source_ip', 'source_port', 'destination_ip', 'destination_port', 'protocol', 'trans_id', 'domain', 'qclass', 'qclass_name', 'qtype', 'qtype_name', 'rcode', 'rcode_name', 'QR', 'AA', 'TC.RD', 'RA', 'Z', 'answers', 'TTL', 'rejected')

\##Task 1

    dest <- dns %>%
      select(destination_ip) %>%
      distinct()
    colnames(dest)=c('ip')

    src <- dns %>%
      select(source_ip) %>%
      distinct()
    colnames(src)=c('ip')

    all_ip<-union(src, dest)%>%
      distinct()

    all_ip%>%
      count()

    ##      n
    ## 1 1359

\##Task 2

    internal_ip <- all_ip%>%
      filter(grepl("(192.168.)([0-9]{1,3}[.])[0-9]{1,3}|(10.0.)([0-9]{1,3}[.])[0-9]{1,3}|(100.64.)([0-9]{1,3}[.])[0-9]{1,3}|(172.16.)([0-9]{1,3}[.])[0-9]{1,3}", all_ip$ip))%>%
      count()

    external_ip <- count(all_ip)-internal_ip

    internal_ip/external_ip

    ##          n
    ## 1 11.94286

\##Task 3

    sources <- dns %>% 
      group_by(source_ip)%>%
      summarise(count_ip = length(source_ip), .groups = 'drop')

    colnames(sources)<-c('ip', 'count_ip')

    destinations <- dns %>% 
      group_by(destination_ip)%>%
      summarise(count_ip = length(destination_ip), .groups = 'drop')

    colnames(destinations)<-c('ip', 'count_ip')

    all_ip_count <- union(sources, destinations)

    all_ip_count %>%
      arrange(desc(count_ip))%>%
      slice(1:10)

    ## # A tibble: 10 × 2
    ##    ip              count_ip
    ##    <chr>              <int>
    ##  1 192.168.207.4     266542
    ##  2 10.10.117.210      75943
    ##  3 192.168.202.255    68720
    ##  4 192.168.202.93     26522
    ##  5 172.19.1.100       25481
    ##  6 192.168.202.103    18121
    ##  7 192.168.202.76     16978
    ##  8 192.168.202.97     16176
    ##  9 192.168.202.141    14967
    ## 10 ff02::1:3          14411

\##Task 4

    domains<-dns %>%
      filter(grepl('[a-z0-9]+(\\.[a-z0-9]+)*\\.[a-z]{2,5}', dns$domain)) %>%
      group_by(domain)%>%
      summarise(count_domain = length(domain), .groups = 'drop')%>%
      arrange(desc(count_domain))%>%
      slice(1:10)
    domains

    ## # A tibble: 10 × 2
    ##    domain                          count_domain
    ##    <chr>                                  <int>
    ##  1 teredo.ipv6.microsoft.com              39273
    ##  2 tools.google.com                       14057
    ##  3 www.apple.com                          13390
    ##  4 time.apple.com                         13109
    ##  5 safebrowsing.clients.google.com        11658
    ##  6 44.206.168.192.in-addr.arpa             7248
    ##  7 imap.gmail.com                          5543
    ##  8 stats.norton.com                        5537
    ##  9 www.google.com                          5217
    ## 10 ratings-wrs.symantec.com                4464

\##Task 5

    dns %>%
      filter(domain == domains$domain)%>%
      arrange(timestamp)%>%
      mutate(time_diff = timestamp - lag(timestamp))%>%
      select(time_diff)%>%
      summary()

    ## Warning in domain == domains$domain: longer object length is not a multiple of
    ## shorter object length

    ##    time_diff       
    ##  Min.   :    0.00  
    ##  1st Qu.:    0.00  
    ##  Median :    1.25  
    ##  Mean   :    9.79  
    ##  3rd Qu.:    4.48  
    ##  Max.   :49967.17  
    ##  NA's   :1

\##Task 6

    dns %>%
      group_by(destination_ip)%>%
      arrange(destination_ip)%>%
      summarise(counter_requests=length(destination_ip), counter_unique_sources=length(unique(source_ip)), .groups = 'drop')%>%
      mutate(division = counter_requests/counter_unique_sources)%>%
      arrange(desc(division))%>%
      slice(1:10)

    ## # A tibble: 10 × 4
    ##    destination_ip  counter_requests counter_unique_sources division
    ##    <chr>                      <int>                  <int>    <dbl>
    ##  1 172.19.1.100               25481                      1   25481 
    ##  2 8.26.56.26                  5974                      1    5974 
    ##  3 156.154.70.22               5821                      1    5821 
    ##  4 172.16.42.255               4962                      1    4962 
    ##  5 68.87.64.150                4838                      1    4838 
    ##  6 68.87.75.198                4171                      1    4171 
    ##  7 192.168.207.4             266542                    111    2401.
    ##  8 ff02::1:3                  14411                      9    1601.
    ##  9 192.168.202.255            68720                     44    1562.
    ## 10 192.168.204.255             1434                      1    1434
