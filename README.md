# Machine Learning using the National Comorbidity Survey

The goal of this project was to use machine learning to predict suicidal behavior based on a subsection of a dataset containing survey responses.  Variable selection was performed by referencing recent psychological literature to identify variables which have been shown to be associated with suicidal behavior.

The original data are accessible from [the ICPSR website](https://www.icpsr.umich.edu/icpsrweb/NAHDAP/studies/6693)

Citation:

Kessler, Ronald C. National Comorbidity Survey: Baseline (NCS-1), 1990-1992. Ann Arbor, MI: Inter-university Consortium for Political and Social Research (distributor), 2008-09-12. [https://doi.org/10.3886/ICPSR06693.v6]

Summary data regarding suicidal behavior were gathered from the [National Center for Health Statictics, Centers for Disease Control and Prevention](https://www.cdc.gov/nchs/products/databriefs/db330.htm)

`scrape_vars.ipynb` is the Jupyter notebook for scraping the variables from the DS1 code book.  In addition to creating a Mongo DB, 
the notebook creates 3 temporary files: `variables.csv`, `titles.csv`, `variables.json`.  The last file contains the same variable
maps that are stored in the Mongo DB.  `scrape4.ipynb` is the scraping from the DS2 code book.

`sort_variables.ipynb` is the Jupyter notebook that attempts to classify each variable based on the results of the scraping by looking
at the values of each label found.  It then attempts to convert the entire dataset.

There are various `.json` files that include temporary workfiles for sorting and scraping variables.  Saving the intermediate work allows
one to start over at a point other than the beginning.

`r-joined.csv` is the joined .csv file of the DS1 and DS2 data sets.

`coding-variables.ipynb` is the Jupyter notebook for converting variable's integer-coded values to their
descriptive values.

`reduced-data2.csv` is the subset of the data used for fitting our models.

`morefitting.ipynb` is the Jupyter notebook with the Lasso Logistic Regression.  Adjusting the threshold to 
acheive the desired recall is demonstrated.  The code to plot the L1 Regularization Paths was found here:
[L1 Regularized Path for Logistic Regression](https://scikit-learn.org/stable/auto_examples/linear_model/plot_logistic_path.html)
All credit is due to the Author: Alexandre Gramfort <alexandre.gramfort@inria.fr>

The file also includes several other fits including Decision Trees, Random Forests, Boosting, Support Vector Classifiers, and Neural Nets.  With the last method was not explored in detail, most methods struggle with the recall in this problem.
 
