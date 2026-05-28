
# Title:

> [!abstract] Motivation
> - Mapping of specific environmental variables over long time periods is difficult due to limited amount of labeled time series data
> - Landsat with its 5 different missions requires special care concerning variability in spectral signature and temporal resolution across sensors

> [!question] What research questions will be answered?
> - What impact does temporal resolution have on prediction accuracy of Landsat time series, considering stable surfaces
> - How can a robust landsat model be trained to predict environmental variable time series

> [!info] What will be done?
> - Development of a pretrained model for annual TSER/TSC prediction over 39 years of Landsat time series
> - Annual model trained on environmental time series data (?), sequentially predicting annual target variable based on Landsat annual time series and predicted values
> - Loss calculated on fully predicted time series

> [!success] What are the expected results?
> - time series prediction results more stable with integration of previous predictions
> - can also serve in a data assimilation way


## Introduction

## Methods
#### Data
- Time serious environmental data:
	- evapotranspiration measurements
	- high resolution canopy height from lidar radar missions
	- reoccurring species plot observations

#### Modelling method
##### Architecture
1. Base TSTpad model which takes annual time series 
2. head for TST that takes TSTpad embedding + full target time series with mask to predict next time series point in the sequence
3. wrapper around TSTpad that sequentially fills the time series target sequence by passing a random year and a the slowly filling target sequence
4. repeat until time series target sequence is full
5. Maybe a last step with all embeddings from TSTpad and the final sequence should be run across the sequence and should predict a kind of softmax addition to the sequence for smoothing (with a skip connection to avoid catastrophic overrides) (Maybe crossattention between embedings and precomputed sequence)

##### Training
- Loss is calculated on the full time series or a sparse representation if only sparse data is available

##### Inference
- not sure how to load patches to the model as artefacts might occur if randomly loaded. Maybe by fixing the random sequential fill to a fixed order or predicting overlapping patches (Fix order for each Sentinel tile).
- variability of the model comes from 5 different random orders of predictions

## Results

## Discussion

## Conclusion

## Literature

