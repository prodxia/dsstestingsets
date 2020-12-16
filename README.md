# dsstestingsets
Data Science Testing Sets

## Tables inside this repository for testing purpose

## The Tables

Table name: members

Description: Member ID and information. Contains information for both
investor and borrower, which is flagged in the member\_type column

Primary\_key = member\_id

``` r
members
```

    ## # A tibble: 8 x 6
    ##   MEMBER_ID COUNTRY_CODE COMPANY_NAME   FULL_NAME  CITIZENSHIP_COUN~ MEMBER_TYPE
    ##       <dbl> <chr>        <chr>          <chr>      <chr>             <chr>      
    ## 1        52 SG           NULL           Jamie Yeo  SG                investor   
    ## 2        51 SG           NULL           Desmond C~ SG                investor   
    ## 3        23 ID           NULL           Peter Ong  US                investor   
    ## 4        24 ID           NULL           Derrick L~ MY                investor   
    ## 5        63 MY           NULL           Fany Wong  MY                investor   
    ## 6        21 SG           Good books pt~ NULL       NULL              borrower   
    ## 7        74 SG           Apple inc      NULL       NULL              borrower   
    ## 8        93 SG           Fruit pte ltd  NULL       NULL              borrower

Table name: loans

Description: Shows the loans and corresponding borrower (member\_id) who
took the loan. Each loan can only have 1 borrower

primary\_key = loan\_id

foreign\_key = member\_id \>\> members.member\_id

``` r
loans
```

    ## # A tibble: 6 x 2
    ##   LOAN_ID MEMBER_ID
    ##   <chr>   <chr>    
    ## 1 9391    21       
    ## 2 9493    93       
    ## 3 837     17       
    ## 4 5235    42       
    ## 5 123     51       
    ## 6 ...     ...

Table name: investments

Description: Shows loan details along with the investors that invested
in the loan. Summing the amount will give you the total amount raised
for each loan.

foreign\_key = member\_id \>\> members.member\_id

foreign\_key = loan\_id \>\> loans.loan\_id

``` r
investments
```

    ## # A tibble: 8 x 4
    ##   LOAN_ID MEMBER_ID `AMOUNT (USD)` INVESTMENT_DATE    
    ##   <chr>   <chr>              <dbl> <chr>              
    ## 1 9391    52                   500 2018-03-21 06:22:00
    ## 2 9391    51                 10000 2018-03-26 07:59:00
    ## 3 9391    24                   300 2017-08-02 23:59:00
    ## 4 837     23                   200 2017-06-21 06:02:00
    ## 5 837     21                    50 2017-09-18 07:27:00
    ## 6 5235    52                   400 2017-08-29 15:04:00
    ## 7 5235    63                   300 2017-10-05 09:40:00
    ## 8 5235    51                   300 2018-03-08 08:07:00

