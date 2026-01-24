## Loading data

start with loading data

      data <- read.csv("../../data/processed/data_after_ACP.csv")
    head(data)

    ##         Dim.1     Dim.2
    ## 1  0.04166444 -2.884879
    ## 2 -0.71457840 -1.526207
    ## 3  2.45432650  1.038869
    ## 4  1.64647430  1.135281
    ## 5 -2.40885914  1.058930
    ## 6  3.02272301 -0.717887

## choosing the number of Clusters

    # Utilisation des scores de l'ACP (data_segmentation créée précédemment)
    library(factoextra)

    fviz_nbclust(data, kmeans, method = "wss") +
      geom_vline(xintercept = 3, linetype = 2) + # Exemple si le coude est à 3
      labs(title = "Méthode du Coude pour choisir le nombre de clusters")

![](12_segmentation_clustering_files/figure-markdown_strict/unnamed-chunk-2-1.png)

## applying clutering

    # On lance le K-means
    set.seed(123) # Pour avoir des résultats reproductibles
    km_res <- kmeans(data, centers = 3, nstart = 25)

    # On ajoute le numéro du cluster à nos données
    data$cluster <- as.factor(km_res$cluster)
    head(data)

    ##         Dim.1     Dim.2 cluster
    ## 1  0.04166444 -2.884879       1
    ## 2 -0.71457840 -1.526207       1
    ## 3  2.45432650  1.038869       2
    ## 4  1.64647430  1.135281       2
    ## 5 -2.40885914  1.058930       3
    ## 6  3.02272301 -0.717887       2

## displying Clusters

    fviz_cluster(km_res, data = data[, 1:2],
                 ellipse.type = "convex", 
                 palette = "jco",
                 ggtheme = theme_minimal())

![](12_segmentation_clustering_files/figure-markdown_strict/unnamed-chunk-4-1.png)

## combining the original data and clusters data

    raw_data <- read.csv("../../data/processed/credit_card_clean.csv")
    head(data)

    ##         Dim.1     Dim.2 cluster
    ## 1  0.04166444 -2.884879       1
    ## 2 -0.71457840 -1.526207       1
    ## 3  2.45432650  1.038869       2
    ## 4  1.64647430  1.135281       2
    ## 5 -2.40885914  1.058930       3
    ## 6  3.02272301 -0.717887       2

## data for the interpretation

    # 1. On ajoute les résultats du clustering au dataset d'origine (celui avec les 15 variables)
    donnees_finales <- cbind(raw_data, Cluster = km_res$cluster)

    # 2. On calcule la moyenne de chaque variable par cluster
    profil_clusters <- aggregate(. ~ Cluster, data = donnees_finales, FUN = mean)

    # 3. On affiche le résultat (transposé pour mieux lire)# 3. On affiche lmedian()e résultat (transposé pour mieux lire)
    print(t(profil_clusters))

    ##                                          [,1]         [,2]         [,3]
    ## Cluster                          1.000000e+00 2.000000e+00 3.000000e+00
    ## BALANCE                          6.913011e+02 7.515273e+02 1.789253e+03
    ## BALANCE_FREQUENCY                9.503914e-01 9.696104e-01 9.942006e-01
    ## PURCHASES                        1.141340e+02 5.677699e+02 8.377584e+01
    ## ONEOFF_PURCHASES                 6.991208e+01 2.147707e+02 6.220350e+01
    ## INSTALLMENTS_PURCHASES           4.424840e+01 3.530786e+02 2.208750e+01
    ## CASH_ADVANCE                     1.569858e+02 1.130327e+02 8.323818e+02
    ## PURCHASES_FREQUENCY              1.652317e-01 7.538095e-01 8.376434e-02
    ## ONEOFF_PURCHASES_FREQUENCY       5.761583e-02 1.128571e-01 4.209767e-02
    ## PURCHASES_INSTALLMENTS_FREQUENCY 1.025386e-01 6.644048e-01 3.994253e-02
    ## CASH_ADVANCE_FREQUENCY           5.518757e-02 3.071427e-02 2.104885e-01
    ## CASH_ADVANCE_TRX                 8.198675e-01 5.457143e-01 3.508621e+00
    ## PURCHASES_TRX                    2.336424e+00 1.317000e+01 1.451724e+00
    ## CREDIT_LIMIT                     2.231192e+03 2.719500e+03 2.862500e+03
    ## PAYMENTS                         4.429796e+02 6.280590e+02 7.138512e+02
    ## MINIMUM_PAYMENTS                 2.895549e+02 3.535365e+02 5.773985e+02
    ## PRC_FULL_PAYMENT                 2.138187e-02 3.166474e-02 3.602395e-03

    write.csv(t(profil_clusters), "../../data/processed/data_pour_Interprétation_des_profils_obtenus.csv", row.names = FALSE)
