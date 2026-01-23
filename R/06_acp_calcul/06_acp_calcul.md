06_acp_calcul
================
2026-01-23

### Diagonalisation de la matrice de corrélation

``` r
# =================================================================
# ANALYSE EN COMPOSANTES PRINCIPALES (ACP) - VERSION SÉCURISÉE
# =================================================================

library(FactoMineR)
library(factoextra)

# 1. Calcul de l'ACP

res.pca <- PCA(data_standardise, scale.unit = TRUE, ncp = 2, graph = FALSE)

valeurs_propres <- get_eigenvalue(res.pca)

# 2. Affichage pour vérification
print("Résultat de la diagonalisation (Valeurs propres) :")
```

    ## [1] "Résultat de la diagonalisation (Valeurs propres) :"

``` r
print(round(valeurs_propres, 3))
```

    ##        eigenvalue variance.percent cumulative.variance.percent
    ## Dim.1       5.030           31.435                      31.435
    ## Dim.2       2.627           16.418                      47.853
    ## Dim.3       2.030           12.690                      60.544
    ## Dim.4       1.589            9.929                      70.472
    ## Dim.5       1.146            7.163                      77.635
    ## Dim.6       0.828            5.174                      82.809
    ## Dim.7       0.705            4.408                      87.217
    ## Dim.8       0.630            3.939                      91.157
    ## Dim.9       0.433            2.709                      93.866
    ## Dim.10      0.412            2.578                      96.443
    ## Dim.11      0.241            1.508                      97.951
    ## Dim.12      0.143            0.892                      98.843
    ## Dim.13      0.104            0.651                      99.495
    ## Dim.14      0.071            0.446                      99.941
    ## Dim.15      0.009            0.058                      99.999
    ## Dim.16      0.000            0.001                     100.000

### Extraction des composantes principales

## Cercle des Corrélations

``` r
# 1. On extrait les coordonnées des variables sur les axes conservés
# Cela s'appelle aussi les "chargements" (loadings)
var_extraction <- res.pca$var$coord

# 2. Affichage des contributions pour les 2 premières composantes
print("Coordonnées des variables sur les composantes extraites :")
```

    ## [1] "Coordonnées des variables sur les composantes extraites :"

``` r
print(round(var_extraction[, 1:2], 3))
```

    ##                                   Dim.1  Dim.2
    ## BALANCE                          -0.489  0.671
    ## BALANCE_FREQUENCY                -0.141  0.360
    ## PURCHASES                         0.750  0.473
    ## ONEOFF_PURCHASES                  0.334  0.370
    ## INSTALLMENTS_PURCHASES            0.749  0.311
    ## CASH_ADVANCE                     -0.539  0.400
    ## PURCHASES_FREQUENCY               0.873  0.210
    ## ONEOFF_PURCHASES_FREQUENCY        0.321  0.332
    ## PURCHASES_INSTALLMENTS_FREQUENCY  0.803  0.152
    ## CASH_ADVANCE_FREQUENCY           -0.657  0.388
    ## CASH_ADVANCE_TRX                 -0.632  0.410
    ## PURCHASES_TRX                     0.841  0.341
    ## CREDIT_LIMIT                      0.047  0.261
    ## PAYMENTS                         -0.046  0.506
    ## MINIMUM_PAYMENTS                 -0.323  0.644
    ## PRC_FULL_PAYMENT                  0.294 -0.279

``` r
# 3. Visualisation : Le Cercle des Corrélations
# C'est l'outil principal de l'étape d'extraction
fviz_pca_var(res.pca, 
             col.var = "contrib", # Couleur selon la contribution
             gradient.cols = c("#00AFBB", "#E7B800", "#FC4E07"),
             repel = TRUE) +
  labs(title = "Cercle des Corrélations - Composantes Extraites",
       x = "Dimension 1", y = "Dimension 2")
```

![](06_acp_calcul_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

## matrice de correlation entre nos variables et les nouvelles axes

``` r
print(res.pca$var$coord)
```

    ##                                        Dim.1      Dim.2
    ## BALANCE                          -0.48902767  0.6711018
    ## BALANCE_FREQUENCY                -0.14116606  0.3602039
    ## PURCHASES                         0.74978897  0.4725885
    ## ONEOFF_PURCHASES                  0.33431336  0.3703220
    ## INSTALLMENTS_PURCHASES            0.74917877  0.3107144
    ## CASH_ADVANCE                     -0.53906475  0.4004040
    ## PURCHASES_FREQUENCY               0.87332934  0.2103526
    ## ONEOFF_PURCHASES_FREQUENCY        0.32113792  0.3316369
    ## PURCHASES_INSTALLMENTS_FREQUENCY  0.80346894  0.1519754
    ## CASH_ADVANCE_FREQUENCY           -0.65707352  0.3876397
    ## CASH_ADVANCE_TRX                 -0.63228389  0.4104415
    ## PURCHASES_TRX                     0.84082914  0.3412041
    ## CREDIT_LIMIT                      0.04674838  0.2607260
    ## PAYMENTS                         -0.04600641  0.5059647
    ## MINIMUM_PAYMENTS                 -0.32264556  0.6442084
    ## PRC_FULL_PAYMENT                  0.29397094 -0.2792557

## L’inertie totale expliquée par les deux premiers axes

``` r
# 1. On s'assure que eig.val est un data.frame
eig.val <- as.data.frame(get_eigenvalue(res.pca))

# 2. On récupère la valeur cumulée de la 2ème ligne (Dim 1 + Dim 2)
# On utilise les crochets [ligne, colonne] pour être 100% sûr
inertie_2_axes <- eig.val[2, "cumulative.variance.percent"]

# 3. Affichage propre
cat("L'inertie totale expliquée par les deux premiers axes est de :", 
    round(inertie_2_axes, 2), "%\n")
```

    ## L'inertie totale expliquée par les deux premiers axes est de : 47.85 %
