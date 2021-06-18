# Replication data and code for "The Social Divide of Social Distancing: Shelter-in-Place Behavior in Santiago during the Covid-19 Pandemic", Management Science (forthcoming)

This repository contains R code and csv datasets to replicate the figures and tables reported in the main paper and in the Appendix (Electronic Companion).

### Replication code

The main code is the R markdown file `main_replication_v1.Rmd`, which loads all the needed datasets and runs the code to generate Figures and Tables in the same order as they appear in the paper. The notebook explains step-by-step different code chunks that replicate each part of the paper.


### Datasets

The folder `data` contains the following datasets:

#### Dictionary of `zone_lockdown.csv`

This dataset is used to replicate Figure 1. Each row corresponds to a municipality-week and the data includes confirmed cases, population and lockdown information.

- Codigo.comuna = id of municipality
- NOM_COMUNA = name of municipality
- Casos.confirmados = Confirmed cases in the municipality
- Poblacion = population of the municipality
- week = week number
- week_start = starting date of the week
- week_end = ending date of the week
- lockdown = fraction of municipality's population under lockdown.


#### Data dictionary of `fig2_data.csv`

This dataset is used to replicate Figure 2. Each rows corresponds to a municipality-week and contains data on measures of mobility.

- X : index
- NOM_COMUNA = name of municipality
- COMUNA = numerical id of municiplaity
- week_start = date where week starts
- wnorm.out.max.avg = population weighted normalized mobility
- norm.out.prop.avg = risk-adjusted normalized mobility
- frac.lock = fraction of population in municipality that is under lockdown.
- frac.D_E = fraction of population in municipality that belongs to the low socioeconomic segment


#### Data dictionary of `infections_data.csv`:

This dataset is used to estimate the regression models (4) and (5) and replicate Tables 1 and 3 in the paper. This dataset is also used to run several robustness tests in the appendix. Each row is a municipality-week and the data includes infection and mobility variables.

- NOM_COMUNA = name of municipality
- week = week number (as factor)
- weeknum = week number (as numeric)
- R = infection rate
- R.adj = death-adjusted infection rate
- lag.frac.lock = lagged percentage of municipality in lockdown in week
- lag.mob.out.max = lagged mobility measure
- lag.mob.risk.prop = lagged risk-adjusted mobility measure
- lag.mob.out.max.cor = lagged mobility measure adjusted for under-reporting
- lag.mob.out.sum = lagged mobility measure with sum of weekly mobility rather than max
- lag.mob.risk.prop.cor = lagged risk adjusted mobility measure adjusted for under-reporting
- lag.mob.risk.prop.sum = lagged risk adjusted mobility measure with sum of weekly mobility rather than max
- lag.Trip.Out = lagged public transportation mobility measure
- lag.Trip.Risk = lagged risk adjusted public transportation mobility measure
- sample.sel150 = boolean filter for data entry selection where cases are greater than 150


#### Data dictionary of `panel_data_mobility.csv`.

This dataset is used to estimate the regression model (3) with Mobility as dependent variable. The results of this estimation are reported in Table 2 and Figure 3. The same dataset is used for additional robustness analysis reported in the appendix. 

Main variables:

- MobOut = Mobility measure capturing the fraction of the population that leave censal zone (define in equation (1)) 
- MobRisk = Risk adjusted measure of mobility.
- LockLocal = fraction of population under a localized lockdown.
- HighSEG, MedSEG, LowSEG = Fraction of population in the zone that belongs to High, Medium and Low Socio-Economic Segment
- zona censal = id of the censal zone
- week = week number (as factor)
- weeknum = week number (as numeric)
- week_start = starting date of the week.

Additional variables used in the appendix for robustness analysis:

- MobOut.cor and MoRisk.cor = similar to other measures but uses correction for missing cellphones
- LockOther = fraction of population whose destination is in lockdown. This measure captures lockdown externalities across zones, used for robustness analysis in the appendix.
- lag.norm.new.symptoms = lagged weekly new infections in the municipality where the zone is located.


#### Data dictionary of `fig3_appendix_data.csv`

This dataset is used to replicate Figure 3 in the appendix E of the paper. Each rows corresponds to a municipality-week and contains data on measures of mobility.

- date = date id
- week_start = date where week starts
- comuna_code = numerical id of municipality
- comuna = name of municipality
- new_cases = number of new cases in municipality-week
- new_deaths = number of new deaths in municipality-week
- estimate = estimate of case under-reporting rate
- lower = lower estimate of case under-reporting rate
- upper = upper estimate of case under-reporting rate
- trueCasesMid = death-adjusted number of cases
- trueCasesLow = lower estimate of death-adjusted number of cases
- trueCasesHigh = upper estiamte of death-adjusted number of cases
