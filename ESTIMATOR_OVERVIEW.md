# Overview of sktime's estimators

## Table of contents
* [Transformers (simple)](#Transformers-(simple))
* [Transformers (paired)](#Transformers-(paired))
* [Time series classifiers](#Time-series-classifiers)
* [Time series regressors](#Time-series-regressors)
* [Forecasters](#Forecasters)


## Transformers (simple)
Simple (or first-degree) transformations:

### Atoms

#### Single time series to primitives
| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
| e.g. Fitted parameter feature extraction | | |


#### Single time series to single time series
| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
| e.g. Fourier transform | | |

#### Nested data frame to nested data frame
| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
| Interval segmenter  (fixed) | transformers.compose.IntervalSegmenter | @mloning  |  |
| Interval segmenter (random)  | transformers.compose.RandomIntervalSegmenter | @mloning  |  |
| Piecewise Aggregate Approximation  | transformers.series_as_features.dictionary_based.PAA | @MatthewMiddlehurst  | [ Keogh et al (2001) - Dimensionality reduction for fast similarity search in large time series databases](https://link.springer.com/article/10.1007/PL00011669) |
| Symbolic Aggregate Approximation  | transformers.series_as_features.dictionary_based.SAX | @MatthewMiddlehurst  | [ Lin et al (2007) - Experiencing SAX: a novel symbolic representation of time series](https://link.springer.com/article/10.1007/s10618-007-0064-z) |
| Symbolic Fourier Approximation  | transformers.series_as_features.dictionary_based.SFA | @MatthewMiddlehurst  | [ Schäfer (2012) - SFA: a symbolic fourier approximation and index for similarity](https://dl.acm.org/doi/abs/10.1145/2247596.2247656) |

#### Nested data frame to tabular data frame

| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
| Tabularise (UK)  | transformers.compose.Tabulariser | @mloning  |  |
| Tabularize (US)  | transformers.compose.Tabularizer | @mloning  |  |
| Auto-correlation function  | transformers.spectral_based.AutoCorrelationFourierTransformer | @jsellier  |  |
| Cosine Transform  | transformers.spectral_based.CosineTransformer | @jsellier  |  |
| Discrete Fourier Transform  | transformers.spectral_based.DiscreteFourierTransformer | @jsellier  |  |
| Power Spectrum | transformers.spectral_based.PowerSpectrumTransformer | @jsellier  |  |
| tsfresh Feature Extractor | transformers.summarise.\_tsfresh.TSFreshFeatureExtractor | @mloning @Ayushmaanseth |  |
| tsfresh Relevant Feature Extractor | transformers.summarise.\_tsfresh.TSFreshRelevantFeatureExtractor | @mloning @Ayushmaanseth |  |
| Derivative Series | transformers.summarise.DeriativeSlopeTransformer | @mloning |  |
| Plateau Finder | transformers.summarise.PlateauFinder | @mloning |  |
| Random Interval Feature Extractor | transformers.summarise.RandomIntervalFeatureExtractor | @mloning |  |
| Matrix profile | transformers.matrix_profile | Claudia Rincon Sanchez | (custom implementation) |
| Principal component scores after tabularization | transformers.PCATransformer | @prockenschaub | [ Hotelling (1933) - Analysis of a complex of statistical variables into principal components](https://psycnet.apa.org/record/1934-00645-001) |
| Shapelet transform | transformers.ShapeletTransform | @jasonlines| [ Hills et al (2014) - Classification of time series by shapelet transformation](https://link.springer.com/article/10.1007/s10618-013-0322-1) |
| Shapelet transform (contracted) | transformers.ContractedShapeletTransform | @jasonlines| [ Hills et al (2014) - Classification of time series by shapelet transformation](https://link.springer.com/article/10.1007/s10618-013-0322-1) |
| Shapelet transform (random sampled) | transformers.RandomEnumerationShapeletTransform | @jasonlines| [ Hills et al (2014) - Classification of time series by shapelet transformation](https://link.springer.com/article/10.1007/s10618-013-0322-1) |

#### Multivariate nested data frame to univariate nested data frame (n-mts-to-n-1-ts)

| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
| Concatenate variables  | transformers.compose.ColumnConcatenator | @mloning  |  |

### Composition

#### Pipeline

| Name | Class | Maintainer | References |
| ------| ------ | ------- | ------ | ------- |
| n-ts-to-X | Concatenate column-wise | transformers.compose.ColumnTransformer | @mloning |  |
| n-ts-to-X | Feature union | pipeline.FeatureUnion | @mloning |  |

### Reduction

| From/output | To/input | Name | Class | Maintainer | References |
| ------ | ------ | ------ | ------- | ------ | ------- |
| n-ts-to-df | 1-ts-to-df | Apply row-wise | transformers.compose.RowwiseTransformer | @mloning |  |

# Transformers (paired)
Paired (or second-degree) transformations:

> Note: the interface for 2nd degree transformers is currently under re-factoring, and currently not consistent or homogenous.

## Atoms

### Distances

| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
| BOSS Distance | classifiers.dictionary_based.boss.boss_distance | @MatthewMiddlehurst | [Schäfer (2014) - The BOSS is concerned with time series classification in the presence of noise](https://link.springer.com/article/10.1007/s10618-014-0377-7) |
| Histogram Intersection | classifiers.dictionary_based.tde.histogram_intersection | @MatthewMiddlehurst |  |

### Kernels
| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
|  |  |  |  |


# Time series classifiers

## Atoms

### Univariate time series classifiers

| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
| BOSS Ensemble | classifiers.dictionary_based.boss.BossEnsemble | @MatthewMiddlehurst | [Schäfer (2014) - The BOSS is concerned with time series classification in the presence of noise](https://link.springer.com/article/10.1007/s10618-014-0377-7) |
| BOSS Atom | classifiers.dictionary_based.boss.BossIndividual | @MatthewMiddlehurst | [Schäfer (2014) - The BOSS is concerned with time series classification in the presence of noise](https://link.springer.com/article/10.1007/s10618-014-0377-7) |
| Temporal Dictionary Ensemble | classifiers.dictionary_based.tde.TemporalDictionaryEnsemble | @MatthewMiddlehurst |  |
| TDE Atom | classifiers.dictionary_based.tde.IndividualTDE | @MatthewMiddlehurst |  |
| Elastic Ensemble | classifiers.distance_based.elastic_ensemble.ElasticEnsemble | @jasonlines | [Lines, Bagnall (2015) - Time Series Classification with Ensembles of Elastic Distance Measures](https://link.springer.com/article/10.1007/s10618-014-0361-2) |
| Proximity Forest | classifiers.distance_based.boss.ProximityForest | @goastler | [Lucas et al (2019) - Proximity Forest: an effective and scalable distance-based classifier for time series](https://link.springer.com/article/10.1007/s10618-019-00617-3) |
| Proximity Stump | classifiers.distance_based.boss.ProximityStump | @goastler | [Lucas et al (2019) - Proximity Forest: an effective and scalable distance-based classifier for time series](https://link.springer.com/article/10.1007/s10618-019-00617-3) |
| Random Interval Spectral Forest (RISE) | classifiers.frequency_based.rise.RandomIntervalSpectralForest | @TonyBagnall | [Lines et al (2018) - Time Series Classification with HIVE-COTE: The Hierarchical Vote Collective of Transformation-Based Ensembles](https://ieeexplore.ieee.org/document/7837946) |
| Shapelet Transform Classifier | classifiers.shapelet_based.stc.ShapeletTransformClassifier | @TonyBagnall | [Hills et al (2014) - Classification of time series by shapelet transformation](https://ieeexplore.ieee.org/document/7837946) |
| Time Series Forest | classifiers.interval_based.tsf.TimeSeriesForestClassifier | @TonyBagnall | [Deng et al (2013) - A Time Series Forest for Classification and Feature Extraction](https://www.sciencedirect.com/science/article/pii/S0020025513001473) |
| Time Series k-NN | classifiers.distance_based.time_series_neighbors.KNeighborsTimeSeriesClassifier | @jasonlines |  |
| ROCKET | transformers.rocket.Rocket | @angus924 | [Dempser et al (2019) ROCKET: Exceptionally fast and accurate time series classification using random convolutional kernels](https://arxiv.org/abs/1910.13051) |
| Mr-SEQL | classifiers.shapelet_based.MrSEQLClassifier | @lnthach | [Interpretable Time Series Classification Using Linear Models and Multi-resolution Multi-domain Symbolic Representations](https://link.springer.com/article/10.1007/s10618-019-00633-3) |
| ShapeDTW | classifiers.distance_based._shape_dtw.ShapeDTW | @Multivin12 | [shapeDTW: Shape Dynamic Time Warping](https://www.sciencedirect.com/science/article/pii/S0031320317303710?via%3Dihub) |
| WEASEL | classifiers.dictionary_based.weasel.WEASEL | @patrickZIB | [Fast and Accurate Time Series Classification with WEASEL](https://dl.acm.org/doi/abs/10.1145/3132847.3132980) |

### Multivariate time series classifiers

| name | sktime class | maintainer | literature
| ------ | ------- | ------ | ------- |
| WEASEL+MUSE | classifiers.dictionary_based.weasel.MUSE | @patrickZIB | [Multivariate time series classification with WEASEL+ MUSE](https://arxiv.org/abs/1711.11343) |

## Composition

### Ensembling (abstract/1st order)

(only abstract ensembles in this list - hard-coded ensembles go in one of the lists for atoms)

| Of | Name | Class | Maintainer | References
| ------ | ------ | ------ | ------- | ------ |
| univariate TSC | boosting TSC  | classifiers.compose.ensemble.TimeSeriesForestClassifier | @mloning  |  |

### Pipelines

| Components | Name | Class | Maintainer | References
| ------ | ------ | ------- | ------ | ------- |
| Transformers, classifiers, regressors | pipeline | sktime.pipeline.Pipeline |  |  |

### Reduction

| From/output | To/input | Name | Class | Maintainer | References
| ------ | ------ | ------ | ------- | ------ | ------- |
| multivariate TSC| univariate TSC | column ensembler  | classifiers.compose.column_ensembler.ColumnEnsembleClassifier | @abostrom  |  |

# Time series regressors

## Atoms

### Univariate time series regressors

| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
|  |  |  |  |

### Multivariate time series regressors

| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
|  |  |  |  |

# Forecasting

## Atoms

### Endogenous time series forecasters

| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
| Naive forecaster | NaiveForecaster | @mloning |
| Holt-Winters exponential smoothing forecaster | ExpSmoothingForecaster | @mloning, @big-o |
| Theta forecaster | ThetaForecaster | @big-o | [Unmasking the Theta method](https://www.sciencedirect.com/science/article/pii/S0169207001001431)

### Multivariate Time Series Forecasting

| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
|  |  |  |  |


## Composition
| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
|  |  |  |  |


### Pipeline
| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
|  |  |  |  |


### Ensembling
| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
|  |  |  |  |



# Forecasters
| name | sktime class | maintainer | literature
| ------ | ------- | ------ | ------- |

### Reduction
| Name | Class | Maintainer | References |
| ------ | ------- | ------ | ------- |
|  |  |  |  |
