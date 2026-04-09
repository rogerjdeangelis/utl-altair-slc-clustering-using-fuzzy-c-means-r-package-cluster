# utl-altair-slc-clustering-using-fuzzy-c-means-r-package-cluster
Altair slc clustering using fuzzy c means r package cluster
    %let pgm=utl-altair-slc-clustering-using-fuzzy-c-means-r-package-cluster;

    %stop_submission;

    Altair slc clustering using fuzzy c means r package cluster

    Graphic
    https://github.com/rogerjdeangelis/utl-altair-slc-clustering-using-fuzzy-c-means-r-package-cluster/blob/main/fuzz.pdf

    Ascii Graphic
    https://github.com/rogerjdeangelis/utl-altair-slc-clustering-using-fuzzy-c-means-r-package-cluster/blob/main/fuzz.txt

    Too long to post on a list, see github
    https://github.com/rogerjdeangelis/utl-altair-slc-clustering-using-fuzzy-c-means-r-package-cluster

    Fuzzy c-Means for Rapid Miner

    Altair Community post
    https://community.altair.com/discussion/44288/fuzzy-c-means-for-rapid-miner?tab=all

    PROBLEM

                                        Feature2
     Feature3       1          2          3          4          5          6          7
          --+----------+----------+----------+----------+----------+----------+----
          | Plot of Feature3 * Feature2 = Hard_Cluster                            |
          |                                                                       |
     10.0 +                                                                       + 10.0
          |                                                                       |
          |                                 2                                     |
          |                            2 *  * * 2                                 |
          |                           2 * 2* 2*** 2                               |
      7.5 +                           2 ***2* *2 * 2                              +  7.5
          |                          2 ***2****** 2                               |
          |                       * 2 2 ***** * * 2                               |
          |                             * 2 *** 2                                 |
          |                                  2                                    |
      5.0 +                                                    * 3                +  5.0
          |          1 *  1 * 1                              3 * 3                |
          |     1 * 1 1 *** * * 1                        3 * ***** 3 3            |
          |  1 ** * ***1****1* 1                        3 **** * ***** 3          |
          |        1 1 **** *1 * 1                      3 *3 ***33 * 3  * 3       |
      2.5 +   1 * * * *** 1 1  * 1                      * 3 * ***  * 3            +  2.5
          |            * 1                                3 ***3 3                |
          |                                                * 3 3                  |
          |                                                                       |
          |                                                                       |
      0.0 +                                                                       +  0.0
          | WORKX.FUZZOUT                   Hard                                  |
          |  ID  Feature1 Feature2 Feature3 Cluster                               |
          |                                                                       |
          |   1    2.69     2.98     4.99    1                                    |
          |   2    1.72     2.22     6.52    1                                    |
          |   3    2.18     3.58     5.08    1                                    |
          |  ...                                                                  |
          |  72    4.95     5.82     5.18    2                                    |
          |  73    5.31     5.74     7.48    2                                    |
          |  74    4.52     5.47     1.71    2                                    |
          |  ...                                                                  |
          | 148    7.78     3.43     4.40    3                                    |
          | 149    8.35     3.05     4.44    3                                    |
          | 150    7.47     2.19     6.09    3                                    |
          --+----------+----------+----------+----------+----------+----------+----
            1          2          3          4          5          6          7

                                         Feature2

         For ascii plot of

             Feature3 * Feature1
             Feature2 * Feature1

             https://github.com/rogerjdeangelis/utl-altair-slc-clustering-using-fuzzy-c-means-r-package-cluster/blob/main/fuzz.txt


    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */
    options validvarname=v7;
    libname workx sas7bdat "d:/wpswrkx";

    proc datasets lib=workx kill;
    run;quit;

    data workx.fuzz;
       input ID  Feature1    Feature2    Feature3 @@;
    cards4;
    1.00 2.69 2.98 4.99  51.0 5.16 5.00 6.45  0101 8.60 2.45 7.67
    2.00 1.72 2.22 6.52  52.0 4.61 6.17 3.33  0102 8.52 3.02 3.26
    3.00 2.18 3.58 5.08  53.0 5.79 6.59 6.47  0103 7.50 2.40 5.11
    4.00 2.32 2.86 6.47  54.0 5.32 7.03 3.26  0104 8.92 3.10 5.10
    5.00 2.20 2.77 4.71  55.0 5.04 5.31 4.09  0105 7.67 3.65 3.84
    6.00 1.95 2.38 4.88  56.0 5.14 5.42 7.38  0106 8.05 2.48 3.00
    7.00 2.76 3.00 5.96  57.0 5.34 5.65 4.42  0107 7.79 2.63 5.00
    8.00 1.95 2.60 6.99  58.0 5.04 5.47 6.66  0108 7.94 3.02 6.31
    9.00 3.01 2.73 2.51  59.0 3.50 5.68 4.42  0109 8.09 2.49 7.95
    10.0 1.97 3.64 4.93  60.0 5.14 5.91 1.85  0110 8.06 2.81 1.18
    11.0 2.65 2.91 4.86  61.0 4.82 5.40 3.30  0111 7.99 3.44 3.60
    12.0 3.14 2.46 3.48  62.0 5.09 7.02 2.82  0112 8.05 3.48 4.38
    13.0 1.31 3.08 2.93  63.0 5.29 6.05 4.03  0113 7.76 3.19 1.67
    14.0 1.86 2.82 3.74  64.0 5.70 5.96 4.33  0114 7.75 2.07 3.50
    15.0 1.93 3.30 6.17  65.0 4.64 6.25 4.69  0115 7.17 2.97 3.45
    16.0 2.32 3.72 4.17  66.0 5.65 6.02 4.51  0116 7.81 3.53 3.55
    17.0 1.86 2.50 3.43  67.0 5.17 5.93 8.78  0117 7.74 3.41 0.62
    18.0 0.67 3.23 5.33  68.0 5.52 6.74 2.23  0118 9.35 2.90 5.43
    19.0 0.78 3.04 2.53  69.0 5.46 5.89 4.17  0119 7.32 1.65 3.74
    20.0 2.66 3.45 7.09  70.0 5.36 5.36 5.70  0120 8.07 3.03 8.04
    21.0 1.85 2.89 4.03  71.0 4.48 6.19 8.26  0121 7.25 3.29 6.59
    22.0 1.11 3.42 5.38  72.0 4.95 5.82 5.18  0122 7.26 3.02 2.09
    23.0 1.91 2.13 5.10  73.0 5.31 5.74 7.48  0123 8.06 3.08 5.20
    24.0 2.61 3.84 5.00  74.0 4.52 5.47 1.71  0124 7.50 3.22 3.81
    25.0 2.95 3.43 8.62  75.0 4.73 6.21 7.89  0125 8.00 2.80 6.78
    26.0 1.78 2.92 3.35  76.0 5.29 5.91 3.62  0126 7.79 3.65 5.11
    27.0 1.87 2.28 7.29  77.0 5.38 6.26 4.45  0127 7.69 3.24 3.89
    28.0 1.12 3.32 5.06  78.0 5.23 5.88 2.78  0128 6.99 2.38 5.88
    29.0 2.23 3.24 3.33  79.0 4.56 5.67 5.27  0129 7.39 3.69 5.31
    30.0 1.68 3.00 4.86  80.0 4.45 6.63 8.57  0130 8.09 3.60 4.67
    31.0 2.23 3.08 6.49  81.0 5.76 5.86 9.84  0131 8.28 3.41 9.04
    32.0 2.35 2.71 4.15  82.0 5.13 6.47 2.85  0132 7.75 2.17 3.94
    33.0 2.52 3.18 3.46  83.0 5.04 5.40 5.97  0133 8.00 2.72 4.06
    34.0 1.70 3.15 5.31  84.0 4.94 5.77 7.78  0134 8.56 3.32 1.91
    35.0 2.25 2.86 6.98  85.0 4.40 5.87 4.61  0135 8.72 3.02 4.92
    36.0 1.14 2.33 4.85  86.0 5.31 5.80 4.56  0136 7.45 3.17 6.78
    37.0 1.61 3.35 2.23  87.0 4.89 6.67 4.39  0137 7.94 4.23 0.86
    38.0 1.57 3.28 2.39  88.0 4.91 5.99 6.20  0138 8.60 2.59 4.50
    39.0 0.79 2.58 3.46  89.0 5.47 6.12 7.79  0139 7.77 1.94 2.64
    40.0 2.02 2.20 3.95  90.0 5.41 5.53 6.38  0140 7.97 3.14 7.88
    41.0 2.10 3.10 4.96  91.0 5.70 5.64 5.64  0141 7.96 2.66 7.72
    42.0 1.82 2.83 6.34  92.0 4.76 6.50 4.40  0142 7.56 3.22 5.67
    43.0 2.38 3.13 4.13  93.0 5.33 6.63 6.00  0143 7.78 2.59 7.86
    44.0 1.64 2.35 2.77  94.0 5.70 6.62 3.90  0144 7.99 4.11 3.27
    45.0 1.32 2.52 6.21  95.0 4.44 5.31 4.44  0145 7.79 2.94 6.90
    46.0 2.22 3.54 5.55  96.0 4.57 7.02 7.19  0146 8.56 2.76 3.83
    47.0 1.59 3.20 7.31  97.0 4.43 6.51 5.88  0147 7.76 2.92 5.64
    48.0 2.72 3.29 1.64  98.0 4.27 5.99 5.48  0148 7.78 3.43 4.40
    49.0 1.78 3.91 5.17  99.0 5.04 6.35 4.49  0149 8.35 3.05 4.44
    50.0 2.33 3.06 7.71  0100 5.33 5.51 6.86  0150 7.47 2.19 6.09
    ;;;;
    run;

    proc sort data=workx.fuzz;
    by id;
    run;

    /**************************************************************************************************************************/
    /*  WORKX.FUZZ total obs=150                                                                                              */
    /*                                                                                                                        */
    /*  ID    Feature1    Feature2    Feature3                                                                                */
    /*   1      2.69        2.98        4.99                                                                                  */
    /*   2      1.72        2.22        6.52                                                                                  */
    /*   3      2.18        3.58        5.08                                                                                  */
    /*   4      2.32        2.86        6.47                                                                                  */
    /*   5      2.20        2.77        4.71                                                                                  */
    /* ...                                                                                                                    */
    /* 146      8.56        2.76        3.83                                                                                  */
    /* 147      7.76        2.92        5.64                                                                                  */
    /* 148      7.78        3.43        4.40                                                                                  */
    /* 149      8.35        3.05        4.44                                                                                  */
    /* 150      7.47        2.19        6.09                                                                                  */
    /**************************************************************************************************************************/

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    %utlfkil(d:/pdf/fuzz.pdf);

    options validvarname=v7;
    options set=RHOME "C:\Progra~1\R\R-4.5.2\bin\r";
    proc r;
    export data=workx.fuzz r=input_df;
    submit;
    # Load required libraries
    library(cluster)
    library(ggplot2)
    library(tidyr)
    library(dplyr)
    library(gridExtra)

    # Set seed for reproducibility
    set.seed(42)

    # ============================================
    # PART 1: CREATE INPUT DATAFRAME
    # ============================================

    # Create synthetic dataset with 3 clusters
    n_points <- nrow(input_df)

    # Display first few rows of input dataframe
    cat("First 6 rows of INPUT dataframe:\n")
    print(head(input_df))
    cat("\n")

    # ============================================
    # PART 2: PERFORM FUZZY C-MEANS CLUSTERING
    # ============================================

    # Perform Fuzzy C-Means on ALL THREE features
    features_for_clustering <- input_df[, c("Feature1", "Feature2", "Feature3")]

    fcm_result <- fanny(features_for_clustering,
                        k = 3,
                        memb.exp = 2,
                        maxit = 100)

    # Add results to dataframe
    output_df <- input_df
    output_df$Hard_Cluster <- fcm_result$clustering
    membership_matrix <- fcm_result$membership
    colnames(membership_matrix) <- paste0("Membership_Cluster", 1:3)
    output_df <- cbind(output_df, membership_matrix)

    # PROOF: Compare clustering with and without Feature3
    # Run FCM on just Feature1 and Feature2
    fcm_2d <- fanny(input_df[, c("Feature1", "Feature2")], k = 3, memb.exp = 2)

    # Run FCM on all three features
    fcm_3d <- fanny(input_df[, c("Feature1", "Feature2", "Feature3")], k = 3, memb.exp = 2)

    # Compare cluster assignments
    comparison_df <- data.frame(
      ID = 1:n_points,
      Cluster_2D = fcm_2d$clustering,
      Cluster_3D = fcm_3d$clustering,
      Different = fcm_2d$clustering != fcm_3d$clustering
    )

    cat("Impact of including Feature3:\n")
    cat("Points with different cluster assignments when Feature3 is included:",
        sum(comparison_df$Different), "out of", n_points, "\n")
    cat("Percentage changed:", round(100 * sum(comparison_df$Different)/n_points, 2), "%\n\n")

    pdf("d:/pdf/fuzz.pdf")
    # Visualize Feature3's importance
    p1 <- ggplot(output_df, aes(x = Feature1, y = Feature2, color = factor(Hard_Cluster))) +
      geom_point(alpha = 0.7, size = 3) +
      labs(title = "Clusters in Feature1-Feature2 Space", subtitle = "Feature3 not shown") +
      theme_minimal()

    p2 <- ggplot(output_df, aes(x = Feature1, y = Feature3, color = factor(Hard_Cluster))) +
      geom_point(alpha = 0.7, size = 3) +
      labs(title = "Clusters in Feature1-Feature3 Space", subtitle = "Feature2 not shown") +
      theme_minimal()

    p3 <- ggplot(output_df, aes(x = Feature2, y = Feature3, color = factor(Hard_Cluster))) +
      geom_point(alpha = 0.7, size = 3) +
      labs(title = "Clusters in Feature2-Feature3 Space", subtitle = "Feature1 not shown") +
      theme_minimal()

    # Arrange plots
    grid.arrange(p1, p2, p3, nrow = 3)


    dev.off()

    endsubmit;
    import r=output_df data=workx.fuzzout;
    import r=input_df data=workx.fuzzinp;
    run;

    options validvarname=v7 ps=255;

    proc print data=workx.fuzzout(firstobs=72)  width=min;
    format  _numeric_ 4.2;
    run;quit;


    /**************************************************************************************************************************/
    /*|                                                                                                                       */
    /*| WORKX.FUZZOUT total obs=150                                                                                           */
    /*|                                            Hard_     Membership_    Membership_    Membership_                        */
    /*|  ID  Feature1    Feature2    Feature3    Cluster     Cluster1       Cluster2       Cluster3                           */
    /*|                                                                                                                       */
    /*|  1      2.69        2.98        4.99       1.00         0.72           0.17           0.11                            */
    /*|  2      1.72        2.22        6.52       1.00         0.62           0.22           0.17                            */
    /*|  3      2.18        3.58        5.08       1.00         0.74           0.16           0.10                            */
    /*|  4      2.32        2.86        6.47       1.00         0.62           0.22           0.15                            */
    /*|  5      2.20        2.77        4.71       1.00         0.77           0.14           0.10                            */
    /*| ...                                                                                                                   */
    /*| 72      4.95        5.82       5.18        2.00         0.15           0.69           0.16                            */
    /*| 73      5.31        5.74       7.48        2.00         0.23           0.51           0.26                            */
    /*| 74      4.52        5.47       1.71        2.00         0.30           0.43           0.28                            */
    /*| ...                                                                                                                   */
    /*| 146     8.56        2.76        3.83       3.00         0.12           0.19           0.69                            */*/
    /*| 147     7.76        2.92        5.64       3.00         0.12           0.19           0.69                            */
    /*| 148     7.78        3.43        4.40       3.00         0.10           0.17           0.73                            */
    /*| 149     8.35        3.05        4.44       3.00         0.10           0.16           0.74                            */
    /*| 150     7.47        2.19        6.09       3.00         0.17           0.23           0.60                            */
    /*|                                                                                                                       */
    /*|                                                                                                                       */
    /*|                                        Feature2                                                                       */
    /*|            1          2          3          4          5          6          7                                        */
    /*|          --+----------+----------+----------+----------+----------+----------+----                                    */
    /*|          | Plot of Feature3 * Feature2 = Hard_Cluster                            |                                    */
    /*| Feature3 |                                                                       |                                    */
    /*|     10.0 +                                                                       + 10.0                               */
    /*|          |                                                                       |                                    */
    /*|          |                                 2                                     |                                    */
    /*|          |                            2 *  * * 2                                 |                                    */
    /*|          |                           2 * 2* 2*** 2                               |                                    */
    /*|      7.5 +                           2 ***2* *2 * 2                              +  7.5                               */
    /*|          |                          2 ***2****** 2                               |                                    */
    /*|          |                       * 2 2 ***** * * 2                               |                                    */
    /*|          |                             * 2 *** 2                                 |                                    */
    /*|          |                                  2                                    |                                    */
    /*|      5.0 +                                                    * 3                +  5.0                               */
    /*|          |          1 *  1 * 1                              3 * 3                |                                    */
    /*|          |     1 * 1 1 *** * * 1                        3 * ***** 3 3            |                                    */
    /*|          |  1 ** * ***1****1* 1                        3 **** * ***** 3          |                                    */
    /*|          |        1 1 **** *1 * 1                      3 *3 ***33 * 3  * 3       |                                    */
    /*|      2.5 +   1 * * * *** 1 1  * 1                      * 3 * ***  * 3            +  2.5                               */
    /*|          |            * 1                                3 ***3 3                |                                    */
    /*|          |                                                * 3 3                  |                                    */
    /*|          |                                                                       |                                    */
    /*|          |                                                                       |                                    */
    /*|      0.0 + WORKX.FUZZOUT                                                         +  0.0                               */
    /*|          |                                 Hard                                  |                                    */
    /*|          |  ID  Feature1 Feature2 Feature3 Cluster                               |                                    */
    /*|          |                                                                       |                                    */
    /*|          |   1    2.69     2.98     4.99    1                                    |                                    */
    /*|          |   2    1.72     2.22     6.52    1                                    |                                    */
    /*|          |   3    2.18     3.58     5.08    1                                    |                                    */
    /*|          |  ...                                                                  |                                    */
    /*|          | 148    7.78     3.43     4.40    3                                    |                                    */
    /*|          | 149    8.35     3.05     4.44    3                                    |                                    */
    /*|          | 150    7.47     2.19     6.09    3                                    |                                    */
    /*|          --+----------+----------+----------+----------+----------+----------+----                                    */
    /*|            1          2          3          4          5          6          7                                        */
    /*|                                                                                                                       */
    /*|                                         Feature2                                                                      */
    /*|  For ascii plot of                                                                                                    */
    /*|                                                                                                                       */
    /*|      Feature3 * Feature1                                                                                              */
    /*|      Feature2 * Feature1                                                                                              */
    /*|                                                                                                                       */
    /*| https://github.com/rogerjdeangelis/utl-altair-slc-clustering-using-fuzzy-c-means-r-package-cluster/blob/main/fuzz.txt */
    /**************************************************************************************************************************/
    /*
    | | ___   __ _
    | |/ _ \ / _` |
    | | (_) | (_| |
    |_|\___/ \__, |
             |___/
    */

    1                                          Altair SLC        10:43 Thursday, April  9, 2026

    NOTE: Copyright 2002-2025 World Programming, an Altair Company
    NOTE: Altair SLC 2026 (05.26.01.00.000758)
          Licensed to Roger DeAngelis
    NOTE: This session is executing on the X64_WIN11PRO platform and is running in 64 bit mode

    NOTE: AUTOEXEC processing beginning; file is C:\wpsoto\autoexec.sas
    NOTE: AUTOEXEC source line
    1       +  ï»¿ods _all_ close;
               ^
    ERROR: Expected a statement keyword : found "?"

    NOTE: AUTOEXEC processing completed

    1
    2         %utlfkil(d:/pdf/fuzz.pdf);
    3
    4         options validvarname=v7;
    5         options set=RHOME "C:\Progra~1\R\R-4.5.2\bin\r";
    6         proc r;
    NOTE: Using R version 4.5.2 (2025-10-31 ucrt) from C:\Program Files\R\R-4.5.2
    7         export data=workx.fuzz r=input_df;
    NOTE: Creating R data frame 'input_df' from data set 'WORKX.fuzz'

    8         submit;
    9         # Load required libraries
    10        library(cluster)
    11        library(ggplot2)
    12        library(tidyr)
    13        library(dplyr)
    14        library(gridExtra)
    15
    16        # Set seed for reproducibility
    17        set.seed(42)
    18
    19        # ============================================
    20        # PART 1: CREATE INPUT DATAFRAME
    21        # ============================================
    22
    23        # Create synthetic dataset with 3 clusters
    24        n_points <- nrow(input_df)
    25
    26        # Display first few rows of input dataframe
    27        cat("First 6 rows of INPUT dataframe:\n")
    28        print(head(input_df))
    29        cat("\n")
    30
    31        # ============================================
    32        # PART 2: PERFORM FUZZY C-MEANS CLUSTERING
    33        # ============================================
    34
    35        # Perform Fuzzy C-Means on ALL THREE features
    36        features_for_clustering <- input_df[, c("Feature1", "Feature2", "Feature3")]
    37
    38        fcm_result <- fanny(features_for_clustering,
    39                            k = 3,
    40                            memb.exp = 2,
    41                            maxit = 100)
    42
    43        # Add results to dataframe
    44        output_df <- input_df
    45        output_df$Hard_Cluster <- fcm_result$clustering
    46        membership_matrix <- fcm_result$membership
    47        colnames(membership_matrix) <- paste0("Membership_Cluster", 1:3)
    48        output_df <- cbind(output_df, membership_matrix)
    49
    50        # PROOF: Compare clustering with and without Feature3
    51        # Run FCM on just Feature1 and Feature2
    52        fcm_2d <- fanny(input_df[, c("Feature1", "Feature2")], k = 3, memb.exp = 2)
    53
    54        # Run FCM on all three features
    55        fcm_3d <- fanny(input_df[, c("Feature1", "Feature2", "Feature3")], k = 3, memb.exp = 2)
    56
    57        # Compare cluster assignments
    58        comparison_df <- data.frame(
    59          ID = 1:n_points,
    60          Cluster_2D = fcm_2d$clustering,
    61          Cluster_3D = fcm_3d$clustering,
    62          Different = fcm_2d$clustering != fcm_3d$clustering
    63        )
    64
    65        cat("Impact of including Feature3:\n")
    66        cat("Points with different cluster assignments when Feature3 is included:",
    67            sum(comparison_df$Different), "out of", n_points, "\n")
    68        cat("Percentage changed:", round(100 * sum(comparison_df$Different)/n_points, 2), "%\n\n")
    69
    70        pdf("d:/pdf/fuzz.pdf")
    71        # Visualize Feature3's importance
    72        p1 <- ggplot(output_df, aes(x = Feature1, y = Feature2, color = factor(Hard_Cluster))) +
    73          geom_point(alpha = 0.7, size = 3) +
    74          labs(title = "Clusters in Feature1-Feature2 Space", subtitle = "Feature3 not shown") +
    75          theme_minimal()
    76
    77        p2 <- ggplot(output_df, aes(x = Feature1, y = Feature3, color = factor(Hard_Cluster))) +
    78          geom_point(alpha = 0.7, size = 3) +
    79          labs(title = "Clusters in Feature1-Feature3 Space", subtitle = "Feature2 not shown") +
    80          theme_minimal()
    81
    82        p3 <- ggplot(output_df, aes(x = Feature2, y = Feature3, color = factor(Hard_Cluster))) +
    83          geom_point(alpha = 0.7, size = 3) +
    84          labs(title = "Clusters in Feature2-Feature3 Space", subtitle = "Feature1 not shown") +
    85          theme_minimal()
    86
    87        # Arrange plots
    88        grid.arrange(p1, p2, p3, nrow = 3)
    89
    90
    91        dev.off()
    92
    93        endsubmit;

    NOTE: Submitting statements to R:

    > # Load required libraries
    > library(cluster)
    Warning message:
    package 'cluster' was built under R version 4.5.3
    > library(ggplot2)
    Warning message:
    package 'ggplot2' was built under R version 4.5.3
    > library(tidyr)
    Warning message:
    package 'tidyr' was built under R version 4.5.3
    > library(dplyr)
    Attaching package: 'dplyr'
    The following objects are masked from 'package:stats':
        filter, lag
    The following objects are masked from 'package:base':
        intersect, setdiff, setequal, union
    Warning message:
    package 'dplyr' was built under R version 4.5.3
    > library(gridExtra)
    Attaching package: 'gridExtra'
    The following object is masked from 'package:dplyr':
        combine
    Warning message:
    package 'gridExtra' was built under R version 4.5.3
    >
    > # Set seed for reproducibility
    > set.seed(42)
    >
    > # ============================================
    > # PART 1: CREATE INPUT DATAFRAME
    > # ============================================
    >
    > # Create synthetic dataset with 3 clusters
    > n_points <- nrow(input_df)
    >
    > # Display first few rows of input dataframe
    > cat("First 6 rows of INPUT dataframe:\n")
    > print(head(input_df))
    > cat("\n")
    >
    > # ============================================
    > # PART 2: PERFORM FUZZY C-MEANS CLUSTERING
    > # ============================================
    >
    > # Perform Fuzzy C-Means on ALL THREE features
    > features_for_clustering <- input_df[, c("Feature1", "Feature2", "Feature3")]
    >
    > fcm_result <- fanny(features_for_clustering,
    +                     k = 3,
    +                     memb.exp = 2,
    +                     maxit = 100)
    >
    > # Add results to dataframe
    > output_df <- input_df
    > output_df$Hard_Cluster <- fcm_result$clustering
    > membership_matrix <- fcm_result$membership
    > colnames(membership_matrix) <- paste0("Membership_Cluster", 1:3)
    > output_df <- cbind(output_df, membership_matrix)
    >
    > # PROOF: Compare clustering with and without Feature3
    > # Run FCM on just Feature1 and Feature2
    > fcm_2d <- fanny(input_df[, c("Feature1", "Feature2")], k = 3, memb.exp = 2)
    >
    > # Run FCM on all three features
    > fcm_3d <- fanny(input_df[, c("Feature1", "Feature2", "Feature3")], k = 3, memb.exp = 2)
    >
    > # Compare cluster assignments
    > comparison_df <- data.frame(
    +   ID = 1:n_points,
    +   Cluster_2D = fcm_2d$clustering,
    +   Cluster_3D = fcm_3d$clustering,
    +   Different = fcm_2d$clustering != fcm_3d$clustering
    + )
    >
    > cat("Impact of including Feature3:\n")
    > cat("Points with different cluster assignments when Feature3 is included:",
    +     sum(comparison_df$Different), "out of", n_points, "\n")
    > cat("Percentage changed:", round(100 * sum(comparison_df$Different)/n_points, 2), "%\n\n")
    >
    > pdf("d:/pdf/fuzz.pdf")
    > # Visualize Feature3's importance
    > p1 <- ggplot(output_df, aes(x = Feature1, y = Feature2, color = factor(Hard_Cluster))) +
    +   geom_point(alpha = 0.7, size = 3) +
    +   labs(title = "Clusters in Feature1-Feature2 Space", subtitle = "Feature3 not shown") +
    +   theme_minimal()
    >
    > p2 <- ggplot(output_df, aes(x = Feature1, y = Feature3, color = factor(Hard_Cluster))) +
    +   geom_point(alpha = 0.7, size = 3) +
    +   labs(title = "Clusters in Feature1-Feature3 Space", subtitle = "Feature2 not shown") +
    +   theme_minimal()
    >
    > p3 <- ggplot(output_df, aes(x = Feature2, y = Feature3, color = factor(Hard_Cluster))) +
    +   geom_point(alpha = 0.7, size = 3) +
    +   labs(title = "Clusters in Feature2-Feature3 Space", subtitle = "Feature1 not shown") +
    +   theme_minimal()
    >
    > # Arrange plots
    > grid.arrange(p1, p2, p3, nrow = 3)
    >
    >
    > dev.off()
    >

    NOTE: Processing of R statements complete

    94        import r=output_df data=workx.fuzzout;
    NOTE: Creating data set 'WORKX.fuzzout' from R data frame 'output_df'
    NOTE: Data set "WORKX.fuzzout" has 150 observation(s) and 8 variable(s)

    95        import r=input_df data=workx.fuzzinp;
    NOTE: Creating data set 'WORKX.fuzzinp' from R data frame 'input_df'
    NOTE: Data set "WORKX.fuzzinp" has 150 observation(s) and 4 variable(s)

    96        run;
    NOTE: Procedure r step took :
          real time : 3.029
          cpu time  : 0.031


    97
    98        options validvarname=v7 ps=255;
    99
    100       proc print data=workx.fuzzout(obs=5) width=min;
    101       format  _numeric_ 4.2;
    102       run;quit;
    NOTE: 5 observations were read from "WORKX.fuzzout"
    NOTE: Procedure print step took :
          real time : 0.015
          cpu time  : 0.000


    103
    ERROR: Error printed on page 1

    NOTE: Submitted statements took :
          real time : 3.156
          cpu time  : 0.140

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
