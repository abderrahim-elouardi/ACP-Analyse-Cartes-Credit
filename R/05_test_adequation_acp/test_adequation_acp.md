Test d’Adéquation de l’ACP
================

- [Test d’Adéquation de l’ACP](#test-dadéquation-de-lacp)
  - [Pourquoi tester l’adéquation?](#pourquoi-tester-ladéquation)
  - [1. Charger les données](#1-charger-les-données)
  - [2. Test KMO (Kaiser-Meyer-Olkin)](#2-test-kmo-kaiser-meyer-olkin)
    - [Interprétation du KMO](#interprétation-du-kmo)
  - [3. Test de Bartlett](#3-test-de-bartlett)
    - [Interprétation du test de
      Bartlett](#interprétation-du-test-de-bartlett)
  - [5. Conclusion](#5-conclusion)

# Test d’Adéquation de l’ACP

## Pourquoi tester l’adéquation?

Avant de faire une ACP, il faut vérifier que: 1. Les variables sont
corrélées entre elles 2. L’ACP a du sens pour ces données

------------------------------------------------------------------------

## 1. Charger les données

``` r
# Charger les packages
library(here)
library(psych)

# Charger les données
data_standardise <- read.csv(here("data/processed/credit_card_clean_standardised.csv"))

# Voir les dimensions
dim(data_standardise)
```

    ## [1] 2035   16

``` r
head(data_standardise)
```

    ##       BALANCE BALANCE_FREQUENCY  PURCHASES ONEOFF_PURCHASES
    ## 1 -1.16484022        -1.7752961 -0.5284451       -0.5332023
    ## 2 -0.24530706         0.3579945 -0.7810196       -0.4606229
    ## 3  0.94544674         0.3579945  0.5556532       -0.5332023
    ## 4 -0.01186224         0.3579945  1.9085175        2.4674559
    ## 5  2.06894320         0.3579945 -0.8319162       -0.5332023
    ## 6 -1.01228073         0.3579945  0.4392272       -0.5332023
    ##   INSTALLMENTS_PURCHASES CASH_ADVANCE PURCHASES_FREQUENCY
    ## 1             -0.2254552  -0.60793025          -0.4912412
    ## 2             -0.6665289  -0.60793025          -0.7214774
    ## 3              1.3502041  -0.60793025           1.8111020
    ## 4              0.2581539  -0.60793025          -0.0307742
    ## 5             -0.6665289   0.02263345          -0.9517109
    ## 6              1.1809872  -0.60793025           1.8111020
    ##   ONEOFF_PURCHASES_FREQUENCY PURCHASES_INSTALLMENTS_FREQUENCY
    ## 1                 -0.6494267                      -0.53241259
    ## 2                  0.1001926                      -0.76036406
    ## 3                 -0.6494267                       1.97506456
    ## 4                  0.1001926                      -0.07650691
    ## 5                 -0.6494267                      -0.76036406
    ## 6                 -0.6494267                       1.97506456
    ##   CASH_ADVANCE_FREQUENCY CASH_ADVANCE_TRX PURCHASES_TRX CREDIT_LIMIT   PAYMENTS
    ## 1            -0.80746785       -0.7750409    -0.5578980   -0.9245572 -1.0142776
    ## 2            -0.80746785       -0.7750409    -0.7042968   -0.8074573  0.2508589
    ## 3            -0.80746785       -0.7750409     0.9060897   -0.1634076  0.2527978
    ## 4            -0.80746785       -0.7750409    -0.1187017    2.5884409  0.2772585
    ## 5            -0.06829058       -0.2555389    -0.8506955    0.2464421  0.5888600
    ## 6            -0.80746785       -0.7750409     0.9060897    0.2464421 -0.9784259
    ##   MINIMUM_PAYMENTS PRC_FULL_PAYMENT
    ## 1       -0.9716397       -0.3886979
    ## 2       -0.5690476       -0.3886979
    ## 3        0.5293573       -0.3886979
    ## 4       -0.3121839       -0.3886979
    ## 5        2.2804592       -0.3886979
    ## 6       -0.8817929       -0.3886979

------------------------------------------------------------------------

## 2. Test KMO (Kaiser-Meyer-Olkin)

Le test KMO mesure si les données sont bonnes pour une ACP.

``` r
# Calculer la matrice de corrélation
cor_matrix <- cor(data_standardise)

# Faire le test KMO
kmo_result <- KMO(cor_matrix)

# Voir le résultat
print(kmo_result)
```

    ## Kaiser-Meyer-Olkin factor adequacy
    ## Call: KMO(r = cor_matrix)
    ## Overall MSA =  0.65
    ## MSA for each item = 
    ##                          BALANCE                BALANCE_FREQUENCY 
    ##                             0.66                             0.78 
    ##                        PURCHASES                 ONEOFF_PURCHASES 
    ##                             0.57                             0.38 
    ##           INSTALLMENTS_PURCHASES                     CASH_ADVANCE 
    ##                             0.55                             0.87 
    ##              PURCHASES_FREQUENCY       ONEOFF_PURCHASES_FREQUENCY 
    ##                             0.70                             0.47 
    ## PURCHASES_INSTALLMENTS_FREQUENCY           CASH_ADVANCE_FREQUENCY 
    ##                             0.65                             0.72 
    ##                 CASH_ADVANCE_TRX                    PURCHASES_TRX 
    ##                             0.70                             0.93 
    ##                     CREDIT_LIMIT                         PAYMENTS 
    ##                             0.46                             0.82 
    ##                 MINIMUM_PAYMENTS                 PRC_FULL_PAYMENT 
    ##                             0.61                             0.82

### Interprétation du KMO

- **KMO \> 0.8**: Très bon ✅
- **KMO 0.6-0.8**: Bon ✅
- **KMO \< 0.6**: Mauvais ❌

``` r
# Extraire la valeur KMO globale
kmo_result <- KMO(cor_matrix)

# Extraire le KMO global (NUMÉRIQUE)
kmo_global <- as.numeric(kmo_result$MSA)

# Interpréter
if (kmo_global > 0.6) {
  print(" Les données sont bonnes pour l'ACP")
} else {
  print(" Les données ne sont pas bonnes pour l'ACP")
}
```

    ## [1] " Les données sont bonnes pour l'ACP"

------------------------------------------------------------------------

## 3. Test de Bartlett

Le test de Bartlett vérifie que les variables sont corrélées.

``` r
# Calculer le test de Bartlett manuellement
n <- nrow(data_standardise)
det_cor <- det(cor_matrix)

# Statistique du test
bartlett_stat <- -n * log(det_cor)

# P-value
df <- (ncol(data_standardise) * (ncol(data_standardise) - 1)) / 2
p_value <- 1 - pchisq(bartlett_stat, df)

# Afficher les résultats
print(paste("Statistique de Bartlett:", round(bartlett_stat, 3)))
```

    ## [1] "Statistique de Bartlett: 41064.326"

``` r
print(paste("P-value:", formatC(p_value, format = "e", digits = 2)))
```

    ## [1] "P-value: 0.00e+00"

### Interprétation du test de Bartlett

- **P-value \< 0.05**: Les variables sont corrélées (bon pour ACP)
- **P-value \> 0.05**: Les variables ne sont pas corrélées (mauvais pour
  ACP)

``` r
if (p_value < 0.05) {
  print(" Les variables sont corrélées - ACP appropriée")
} else {
  print(" Les variables ne sont pas corrélées - ACP non appropriée")
}
```

    ## [1] " Les variables sont corrélées - ACP appropriée"

------------------------------------------------------------------------

## 5. Conclusion

``` r
# Résumé final
cat("KMO global:", round(kmo_global, 3), "\n")
```

    ## KMO global: 0.646

``` r
cat("P-value Bartlett:", formatC(p_value, format = "e", digits = 2), "\n\n")
```

    ## P-value Bartlett: 0.00e+00

``` r
if (kmo_global > 0.6 && p_value < 0.05) {
  cat(" L'ACP EST APPROPRIÉE\n")
  cat("Vous pouvez continuer avec l'ACP!\n")
} else {
  cat(" L'ACP PEUT NE PAS ÊTRE APPROPRIÉE\n")
  cat("Soyez prudent dans l'interprétation.\n")
}
```

    ##  L'ACP EST APPROPRIÉE
    ## Vous pouvez continuer avec l'ACP!
