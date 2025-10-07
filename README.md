## Summary

Pandas is used for data exploration, cleaning, and analysis. The dataframe is downcasted to optimize memory usage and make computations faster.  


The analysis explores the [Beer Review dataset](https://data.world/socialmediadata/beeradvocate) to answer key questions about beer quality and recommendations. 

- Which breweries produce the strongest beers by ABV.
- How to recommend top beers based on review scores, popularity, and style diversity.
- Which factors (taste, palate, aroma, appearance, ABV) most influence overall beer ratings using correlation analysis.
- How to recommend beers whose aroma and appearance best match their style by comparing individual scores to style averages.

Results are presented in tables for easy comparison and interpretation.


______

## 1. Which brewery produces the strongest beers by abv ?

| Brewery Name                                         | Mean ABV   | Max ABV   | Count  |
|------------------------------------------------------|------------|-----------|--------|
| Schorschbräu                                         | 19.23      | 57.70     | 34     |
| BrewDog                                              | 9.91       | 41.00     | 4033   |
| De Struise Brouwers                                  | 10.76      | 39.00     | 3866   |
| Hair of the Dog Brewing Company / Brewery and ...    | 9.41       | 29.00     | 3769   |
| Boston Beer Company (Samuel Adams)                   | 6.41       | 27.00     | 38812  |


**Schorschbräu** produces the strongest beer of *ABV 57.7%*, but only has 34 beers in the dataset. 

Also, **BrewDog** and **De Struise Brouwers** produce very strong beers respectively 41% and 39% ABV and they have more reviews and beers.

___________

## 2. If you had to pick 3 beers to recommend to someone, how would you approach the problem ?

Solution: Usually "best" means a combination of high review scores, popularity, and diversity of styles. To find that filter out not popular beers, calculate average of overall rating, and sort by average rating.

| Beer Name                          | Beer Style                        | Avg Rating | Review Count |
|-------------------------------------|-----------------------------------|------------|--------------|
| Citra DIPA                         | American Double / Imperial IPA    | 4.630952   | 252          |
| Cantillon Blåbær Lambik            | Lambic - Fruit                    | 4.628205   | 156          |
| Deviation - Bottleworks 9th Anniversary | American Wild Ale             | 4.620536   | 112          |
| Trappist Westvleteren 12           | Quadrupel (Quad)                  | 4.617925   | 1272         |
| Founders CBS Imperial Stout        | American Double / Imperial Stout  | 4.591052   | 637          |


**Citra DIPA, Cantillon Blåbær Lambik, Deviation - Bottleworks 9th Anniversary** beers have decent number of reviews and their overall average score is higher than 4.6

_________________________

## 3. What are the factors that impacts the quality of beer the most ?

Solution: To find the impact factors of qaulity I will check *review aroma, appearance, palate, taste, abv* columns correlation to the **overall review**. 

| Column Name         |Correlation|
|---------------------|-----------|
| review_overall      | 1.000000  |
| review_taste        | 0.787193  |
| review_palate       | 0.699040  |
| review_aroma        | 0.612826  |
| review_appearance   | 0.498576  |
| beer_abv            | 0.138512  |

**review_taste** with **0.79** has the strongest impact on overall beer quality. It means that better the taste, the higher the overall review. 
**review_palate - 0.70** and **review_aroma - 0.62**  plays significantly affects how people rate beer.
**review_appearance - 0.50**, appearance matters less than taste, palate, and aroma.

At least **beer_abv - 0.14**, alcohol content has a weak positive correlation with quality.

*Overall, taste, palate - mouthfeel, and aroma are the most important factors for beer quality.*



## 4. I enjoy a beer which aroma and appearance matches the beer style.  What beer should I buy ?

| Beer Name                      | Beer Style                    | Review Overall | Review Aroma | Review Appearance |
|---------------------------------|-------------------------------|----------------|--------------|-------------------|
| ÜberFest Pilsner                | German Pilsener               | 5.0            | 4.0          | 4.5               |
| "Best Of Both Worlds" Stout     | American Stout                | 5.0            | 4.5          | 4.5               |
| Aries American Wheat            | American Pale Wheat Ale       | 5.0            | 4.0          | 5.0               |
| Armadillo Amber                 | American Amber / Red Ale      | 5.0            | 4.5          | 4.0               |
| Patchway Pale Ale               | American Pale Ale (APA)       | 5.0            | 4.5          | 4.0               |




**ÜberFest Pilsner, "Best Of Both Worlds" Stout, Aries American Wheat** beers are top 3 for recommend people who prefer aroma and appearance matches to beer style. 
