W11 MTCARS Linear Regression, Mini Batch,Stochastic,Batch


W12 boston best features multiple regression

W21 pima csv analysis ,tpr,tnr,roc

W22 log regression metrics,confusion,knn

W31 titanic pipelines bayes classification sensititvity specififcity

W32 womens clothing text processing naïve bayes precisin recall f1

W41 German Credit DT,GRID SEARCH , GRAPHVIZ,TEXT REPRESENTATION

W42 Fuel consumption polynomial regression

W51 weatherAUS VIF Feature extraction

W52 USPRIZE preprocessing lasso+ridge

W61 WINE graphs mlp mlp weight

W62 CANCER visualizing svm gridsearchcv




import scipy.stats as scs

def categories(series):
    return range(int(series.min()), int(series.max()) + 1)

def chi_square_of_df_cols(df, col1, col2):
    df_col1, df_col2 = df[col1], df[col2]
    cats1, cats2 = categories(df_col1), categories(df_col2)

    def aux(is_cat1):
        return [sum(is_cat1 & (df_col2 == cat2))
                for cat2 in cats2]

    result = [aux(df_col1 == cat1)
              for cat1 in cats1]

    return scs.chi2_contingency(result)
 
chi_square_of_df_cols(df2,'shelf','rating')
