05_correlation
================
2026-01-23

- [Loading data](#loading-data)
- [calculing correlation matrice](#calculing-correlation-matrice)
- [saving](#saving)
- [displing Corr matrixe](#displing-corr-matrixe)

## Loading data

start with loading data

``` r
  data_standardise <- read.csv("C:\\Users\\EL OUARDI\\Desktop\\projet statistique\\ACP-Analyse-Cartes-Credit\\data\\processed\\credit_card_clean_standardised.csv")
```

## calculing correlation matrice

``` r
matrice_corr <- cor(data_standardise)
```

``` r
print(matrice_corr)
```

    ##                                      BALANCE BALANCE_FREQUENCY   PURCHASES ONEOFF_PURCHASES
    ## BALANCE                           1.00000000       0.340838461 -0.13252549      -0.01962190
    ## BALANCE_FREQUENCY                 0.34083846       1.000000000 -0.02483226      -0.02757476
    ## PURCHASES                        -0.13252549      -0.024832261  1.00000000       0.72682276
    ## ONEOFF_PURCHASES                 -0.01962190      -0.027574756  0.72682276       1.00000000
    ## INSTALLMENTS_PURCHASES           -0.17251525      -0.007682454  0.71272011       0.03671801
    ## CASH_ADVANCE                      0.38691073       0.027698171 -0.21726334      -0.13288262
    ## PURCHASES_FREQUENCY              -0.27328520      -0.009744590  0.60187192       0.11838078
    ## ONEOFF_PURCHASES_FREQUENCY       -0.02005236      -0.009155622  0.52761139       0.74089699
    ## PURCHASES_INSTALLMENTS_FREQUENCY -0.26146055       0.005407157  0.48389127      -0.05652728
    ## CASH_ADVANCE_FREQUENCY            0.37689327       0.136871923 -0.29078263      -0.14146074
    ## CASH_ADVANCE_TRX                  0.35661508       0.117679832 -0.26384847      -0.13269265
    ## PURCHASES_TRX                    -0.20589812       0.008428391  0.68218504       0.24031126
    ## CREDIT_LIMIT                      0.19958502      -0.065117438  0.15946227       0.16207366
    ## PAYMENTS                          0.27361180       0.011777841  0.18799820       0.13925069
    ## MINIMUM_PAYMENTS                  0.80982282       0.311433530 -0.05286750      -0.03148090
    ## PRC_FULL_PAYMENT                 -0.38358200      -0.289867882  0.09448645       0.01166484
    ##                                  INSTALLMENTS_PURCHASES CASH_ADVANCE PURCHASES_FREQUENCY
    ## BALANCE                                    -0.172515249   0.38691073       -0.2732852045
    ## BALANCE_FREQUENCY                          -0.007682454   0.02769817       -0.0097445899
    ## PURCHASES                                   0.712720109  -0.21726334        0.6018719215
    ## ONEOFF_PURCHASES                            0.036718006  -0.13288262        0.1183807754
    ## INSTALLMENTS_PURCHASES                      1.000000000  -0.18035060        0.7547549471
    ## CASH_ADVANCE                               -0.180350598   1.00000000       -0.3009678407
    ## PURCHASES_FREQUENCY                         0.754754947  -0.30096784        1.0000000000
    ## ONEOFF_PURCHASES_FREQUENCY                  0.011190963  -0.15797936        0.1792376125
    ## PURCHASES_INSTALLMENTS_FREQUENCY            0.761855718  -0.25900387        0.9629713784
    ## CASH_ADVANCE_FREQUENCY                     -0.277059656   0.59622667       -0.3955185477
    ## CASH_ADVANCE_TRX                           -0.247360990   0.65317260       -0.3570455646
    ## PURCHASES_TRX                               0.747620779  -0.24224971        0.8958027134
    ## CREDIT_LIMIT                                0.065958960   0.12923470        0.0086976602
    ## PAYMENTS                                    0.132011087   0.24296260        0.0001302561
    ## MINIMUM_PAYMENTS                           -0.042901154   0.22286766       -0.1087312319
    ## PRC_FULL_PAYMENT                            0.125109484  -0.10034623        0.2041442687
    ##                                  ONEOFF_PURCHASES_FREQUENCY
    ## BALANCE                                        -0.020052357
    ## BALANCE_FREQUENCY                              -0.009155622
    ## PURCHASES                                       0.527611394
    ## ONEOFF_PURCHASES                                0.740896985
    ## INSTALLMENTS_PURCHASES                          0.011190963
    ## CASH_ADVANCE                                   -0.157979363
    ## PURCHASES_FREQUENCY                             0.179237612
    ## ONEOFF_PURCHASES_FREQUENCY                      1.000000000
    ## PURCHASES_INSTALLMENTS_FREQUENCY               -0.051978274
    ## CASH_ADVANCE_FREQUENCY                         -0.146255401
    ## CASH_ADVANCE_TRX                               -0.132146851
    ## PURCHASES_TRX                                   0.299153915
    ## CREDIT_LIMIT                                    0.112620140
    ## PAYMENTS                                        0.081427020
    ## MINIMUM_PAYMENTS                               -0.001253995
    ## PRC_FULL_PAYMENT                               -0.005965577
    ##                                  PURCHASES_INSTALLMENTS_FREQUENCY CASH_ADVANCE_FREQUENCY
    ## BALANCE                                              -0.261460547             0.37689327
    ## BALANCE_FREQUENCY                                     0.005407157             0.13687192
    ## PURCHASES                                             0.483891268            -0.29078263
    ## ONEOFF_PURCHASES                                     -0.056527280            -0.14146074
    ## INSTALLMENTS_PURCHASES                                0.761855718            -0.27705966
    ## CASH_ADVANCE                                         -0.259003873             0.59622667
    ## PURCHASES_FREQUENCY                                   0.962971378            -0.39551855
    ## ONEOFF_PURCHASES_FREQUENCY                           -0.051978274            -0.14625540
    ## PURCHASES_INSTALLMENTS_FREQUENCY                      1.000000000            -0.34744171
    ## CASH_ADVANCE_FREQUENCY                               -0.347441714             1.00000000
    ## CASH_ADVANCE_TRX                                     -0.314042475             0.92178825
    ## PURCHASES_TRX                                         0.849741344            -0.31227179
    ## CREDIT_LIMIT                                         -0.025152466            -0.05628371
    ## PAYMENTS                                             -0.010185738             0.17922997
    ## MINIMUM_PAYMENTS                                     -0.098302859             0.25576919
    ## PRC_FULL_PAYMENT                                      0.202809671            -0.13434262
    ##                                  CASH_ADVANCE_TRX PURCHASES_TRX CREDIT_LIMIT      PAYMENTS
    ## BALANCE                                0.35661508  -0.205898118   0.19958502  0.2736118038
    ## BALANCE_FREQUENCY                      0.11767983   0.008428391  -0.06511744  0.0117778407
    ## PURCHASES                             -0.26384847   0.682185037   0.15946227  0.1879981978
    ## ONEOFF_PURCHASES                      -0.13269265   0.240311265   0.16207366  0.1392506918
    ## INSTALLMENTS_PURCHASES                -0.24736099   0.747620779   0.06595896  0.1320110866
    ## CASH_ADVANCE                           0.65317260  -0.242249705   0.12923470  0.2429626013
    ## PURCHASES_FREQUENCY                   -0.35704556   0.895802713   0.00869766  0.0001302561
    ## ONEOFF_PURCHASES_FREQUENCY            -0.13214685   0.299153915   0.11262014  0.0814270204
    ## PURCHASES_INSTALLMENTS_FREQUENCY      -0.31404248   0.849741344  -0.02515247 -0.0101857378
    ## CASH_ADVANCE_FREQUENCY                 0.92178825  -0.312271792  -0.05628371  0.1792299664
    ## CASH_ADVANCE_TRX                       1.00000000  -0.280534831  -0.05375584  0.1912572896
    ## PURCHASES_TRX                         -0.28053483   1.000000000   0.04595985  0.0612899490
    ## CREDIT_LIMIT                          -0.05375584   0.045959853   1.00000000  0.1763114426
    ## PAYMENTS                               0.19125729   0.061289949   0.17631144  1.0000000000
    ## MINIMUM_PAYMENTS                       0.25346843  -0.059260540   0.02378230  0.2189633231
    ## PRC_FULL_PAYMENT                      -0.12250014   0.149836761   0.02009903  0.0888731422
    ##                                  MINIMUM_PAYMENTS PRC_FULL_PAYMENT
    ## BALANCE                               0.809822816     -0.383581997
    ## BALANCE_FREQUENCY                     0.311433530     -0.289867882
    ## PURCHASES                            -0.052867502      0.094486455
    ## ONEOFF_PURCHASES                     -0.031480897      0.011664840
    ## INSTALLMENTS_PURCHASES               -0.042901154      0.125109484
    ## CASH_ADVANCE                          0.222867656     -0.100346227
    ## PURCHASES_FREQUENCY                  -0.108731232      0.204144269
    ## ONEOFF_PURCHASES_FREQUENCY           -0.001253995     -0.005965577
    ## PURCHASES_INSTALLMENTS_FREQUENCY     -0.098302859      0.202809671
    ## CASH_ADVANCE_FREQUENCY                0.255769188     -0.134342620
    ## CASH_ADVANCE_TRX                      0.253468432     -0.122500136
    ## PURCHASES_TRX                        -0.059260540      0.149836761
    ## CREDIT_LIMIT                          0.023782304      0.020099026
    ## PAYMENTS                              0.218963323      0.088873142
    ## MINIMUM_PAYMENTS                      1.000000000     -0.327408751
    ## PRC_FULL_PAYMENT                     -0.327408751      1.000000000

## saving

``` r
write.csv(matrice_corr, "C:\\Users\\EL OUARDI\\Desktop\\projet statistique\\ACP-Analyse-Cartes-Credit\\data\\processed\\matrice_corr.csv", row.names = FALSE)
```

## displing Corr matrixe

``` r
library(kableExtra)
library(magrittr)
library(webshot2)
# 1. On prépare les données
df_corr <- as.data.frame(round(matrice_corr, 2))

# 2. On crée le tableau avec un dégradé de bleu (style Pandas/Seaborn)
df_corr |>
  kbl() |>
  kable_styling(bootstrap_options = c("striped", "hover", "condensed"), full_width = F) |>
  column_spec(1, bold = T, border_right = T) |>
  column_spec(2:ncol(df_corr)+1, 
              background = spec_color(as.matrix(df_corr), end = 0.9, option = "D", direction = -1))
```

    ## Warning in ensure_len_html(background, nrows, "background"): The number of provided values
    ## in background does not equal to the number of rows.

<table class="table table-striped table-hover table-condensed" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">

<thead>

<tr>

<th style="text-align:left;">

</th>

<th style="text-align:right;">

BALANCE
</th>

<th style="text-align:right;">

BALANCE_FREQUENCY
</th>

<th style="text-align:right;">

PURCHASES
</th>

<th style="text-align:right;">

ONEOFF_PURCHASES
</th>

<th style="text-align:right;">

INSTALLMENTS_PURCHASES
</th>

<th style="text-align:right;">

CASH_ADVANCE
</th>

<th style="text-align:right;">

PURCHASES_FREQUENCY
</th>

<th style="text-align:right;">

ONEOFF_PURCHASES_FREQUENCY
</th>

<th style="text-align:right;">

PURCHASES_INSTALLMENTS_FREQUENCY
</th>

<th style="text-align:right;">

CASH_ADVANCE_FREQUENCY
</th>

<th style="text-align:right;">

CASH_ADVANCE_TRX
</th>

<th style="text-align:right;">

PURCHASES_TRX
</th>

<th style="text-align:right;">

CREDIT_LIMIT
</th>

<th style="text-align:right;">

PAYMENTS
</th>

<th style="text-align:right;">

MINIMUM_PAYMENTS
</th>

<th style="text-align:right;">

PRC_FULL_PAYMENT
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

BALANCE
</td>

<td style="text-align:right;">

1.00
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

0.34
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

-0.02
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

-0.17
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

0.39
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

-0.27
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

-0.02
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

-0.26
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

0.38
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

0.36
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

-0.21
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

0.20
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

0.27
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

0.81
</td>

<td style="text-align:right;background-color: rgba(68, 1, 84, 255) !important;">

-0.38
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

BALANCE_FREQUENCY
</td>

<td style="text-align:right;">

0.34
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

-0.02
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

-0.03
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

0.03
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

0.14
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

0.12
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

-0.07
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

0.31
</td>

<td style="text-align:right;background-color: rgba(39, 126, 142, 255) !important;">

-0.29
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

PURCHASES
</td>

<td style="text-align:right;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

-0.02
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.73
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.71
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

-0.22
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.60
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.53
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.48
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

-0.29
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

-0.26
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.68
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.16
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.19
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

-0.05
</td>

<td style="text-align:right;background-color: rgba(81, 196, 106, 255) !important;">

0.09
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

ONEOFF_PURCHASES
</td>

<td style="text-align:right;">

-0.02
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.03
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.73
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.04
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.12
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.74
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.06
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.14
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.24
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.16
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.14
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.03
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.01
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

INSTALLMENTS_PURCHASES
</td>

<td style="text-align:right;">

-0.17
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.71
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.04
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

-0.18
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.75
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.76
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

-0.28
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

-0.25
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.75
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.07
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.13
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

-0.04
</td>

<td style="text-align:right;background-color: rgba(93, 201, 98, 255) !important;">

0.13
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

CASH_ADVANCE
</td>

<td style="text-align:right;">

0.39
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

0.03
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

-0.22
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

-0.18
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

-0.30
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

-0.16
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

-0.26
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

0.60
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

0.65
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

-0.24
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

0.13
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

0.24
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

0.22
</td>

<td style="text-align:right;background-color: rgba(42, 118, 142, 255) !important;">

-0.10
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

PURCHASES_FREQUENCY
</td>

<td style="text-align:right;">

-0.27
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.60
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.12
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.75
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

-0.30
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.18
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.96
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

-0.40
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

-0.36
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.90
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.00
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

-0.11
</td>

<td style="text-align:right;background-color: rgba(132, 212, 75, 255) !important;">

0.20
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

ONEOFF_PURCHASES_FREQUENCY
</td>

<td style="text-align:right;">

-0.02
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.53
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.74
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.16
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.18
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.05
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.15
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.30
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.11
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.08
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

0.00
</td>

<td style="text-align:right;background-color: rgba(49, 181, 123, 255) !important;">

-0.01
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

PURCHASES_INSTALLMENTS_FREQUENCY
</td>

<td style="text-align:right;">

-0.26
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

0.48
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

-0.06
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

0.76
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

-0.26
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

0.96
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

-0.05
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

-0.35
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

-0.31
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

0.85
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

-0.03
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

-0.10
</td>

<td style="text-align:right;background-color: rgba(127, 211, 78, 255) !important;">

0.20
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

CASH_ADVANCE_FREQUENCY
</td>

<td style="text-align:right;">

0.38
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

0.14
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.29
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.14
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.28
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

0.60
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.40
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.15
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.35
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

0.92
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.31
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.06
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

0.18
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

0.26
</td>

<td style="text-align:right;background-color: rgba(42, 120, 142, 255) !important;">

-0.13
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

CASH_ADVANCE_TRX
</td>

<td style="text-align:right;">

0.36
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

0.12
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.26
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.25
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

0.65
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.36
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.31
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

0.92
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.28
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.05
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

0.19
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

0.25
</td>

<td style="text-align:right;background-color: rgba(41, 123, 142, 255) !important;">

-0.12
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

PURCHASES_TRX
</td>

<td style="text-align:right;">

-0.21
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.68
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.24
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.75
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

-0.24
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.90
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.30
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.85
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

-0.31
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

-0.28
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.05
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.06
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

-0.06
</td>

<td style="text-align:right;background-color: rgba(108, 205, 90, 255) !important;">

0.15
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

CREDIT_LIMIT
</td>

<td style="text-align:right;">

0.20
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

-0.07
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.16
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.16
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.07
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.13
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.11
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

-0.03
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

-0.06
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

-0.05
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.05
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.18
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.02
</td>

<td style="text-align:right;background-color: rgba(32, 147, 140, 255) !important;">

0.02
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

PAYMENTS
</td>

<td style="text-align:right;">

0.27
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.19
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.14
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.13
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.24
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.00
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.08
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.18
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.19
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.06
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.18
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.22
</td>

<td style="text-align:right;background-color: rgba(35, 137, 142, 255) !important;">

0.09
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

MINIMUM_PAYMENTS
</td>

<td style="text-align:right;">

0.81
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

0.31
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

-0.05
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

-0.03
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

-0.04
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

0.22
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

-0.11
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

0.00
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

-0.10
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

0.26
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

0.25
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

-0.06
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

0.02
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

0.22
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

1.00
</td>

<td style="text-align:right;background-color: rgba(71, 45, 122, 255) !important;">

-0.33
</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;border-right:1px solid;">

PRC_FULL_PAYMENT
</td>

<td style="text-align:right;">

-0.38
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

-0.29
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

0.09
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

0.01
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

0.13
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

-0.10
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

0.20
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

-0.01
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

0.20
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

-0.13
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

-0.12
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

0.15
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

0.02
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

0.09
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

-0.33
</td>

<td style="text-align:right;background-color: rgba(178, 221, 45, 255) !important;">

1.00
</td>

</tr>

</tbody>

</table>

``` r
save_kable(df_corr, file = "C:\\Users\\EL OUARDI\\Desktop\\projet statistique\\ACP-Analyse-Cartes-Credit\\R\\images\\matrice_correlation.png")
```

    ## file:///C:/Users/EL OUARDI/AppData/Local/Temp/RtmpWC23Tq/matrice_correlation33a8400827e8.html screenshot completed

    ## save_kable will have the best result with magick installed.
