# OneMinSketch
**What if we only update the minimum hash among all k options in Count-Min Sketch ?**

- This would reduce the number of updates that are applied to every counter-
- Which could potentially reduce the impact of collisions
- To test out this modified sketch we run several experiments

## Experiment
- We test our custom sketch(OneMinSketch) against the min-sketch, and count sketch
- We also track the performance for various R values(Length of hash array):
  - 2^9 (512)
  - 2^10
  - 2^11
  - 2^12
  - 2^14
  - 2^18 (262,144)
- We track the accuracy of the counts for the,
  - 100 most frequent hitters(heavy hitters)
  - 100 most infrequent hitters
  - 100 random hitters
- Our dataset consists of 3.5 million URL queries(hitters)

## Analysis 

 

| Count Sketch                                                                                                        | OneMinSketch                                                                                                                                  | Min Sketch                                                                                                         |
| :---:                                                                                                               |     :---:                                                                                                                                     |                                                                                                              :---: |
|![Count_sketch_9](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/528e8856-cf19-4989-acca-67f2e025238b) | ![Custom_sketch_9](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/1b2738c1-2915-4367-afc4-6565516746ca) | ![Min_sketch_9](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/34823775-e4f7-40fa-9589-5998dad830df) |
| When R=2^9                                                                                                          |  When R=2^9                                                                                                                                   |  When R=2^9                                                                                                        |


- The loss for all the heavy hitters are tend to zero across all the sketches
- If we observe the upper range of the various sketches:
  - Min-sketch    : ~ 80,000
  - Count-sketch  : ~ 40,000
  - Custom-Sketch : ~ 17,500
- Another observation is how different the variance of the error for infrequent and random hitters are for the Custom sketch(OneMinSketch) as opposed to that of Min-Sketch and Count-Sketch





| Count Sketch                                                                                                        | OneMinSketch                                                                                                                                  | Min Sketch                                                                                                         |
| :---:                                                                                                               |     :---:                                                                                                                                     |                                                                                                              :---: |
|![Count_sketch_10](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/63f093bb-dafc-44c1-ad05-0f127c697a9a)| ![Custom_sketch_10](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/5d5a6d3a-2a12-48bf-b679-422207ae4feb) |![Min_sketch_10](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/6443c3df-68e3-4b79-9f12-26d1eea5e5d2) |
| When R=2^10                                                                                                         |  When R=2^10                                                                                                                                  |  When R=2^10                                                                                                       |
|![Count_sketch_11](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/6980229d-3328-4696-b816-fb9e48a38648)| ![Custom_sketch_11](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/919102eb-ce50-4a97-9ccb-35ce5be465de) |![Min_sketch_11](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/ab89e34d-3374-40b0-9f4e-3555137855da) |
| When R=2^11                                                                                                         |  When R=2^11                                                                                                                                  |  When R=2^11                                                                                                       |
|![Count_sketch_12](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/b7fa7f2e-21b4-4973-ab04-28fd02340484)| ![Custom_sketch_12](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/eb22d11a-e6ba-460f-8acf-4446ee965d7f) |![Min_sketch_12](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/94721828-f8db-4ad6-bbe3-21c95f8e14ee) |
| When R=2^12                                                                                                         |  When R=2^12                                                                                                                                  |  When R=2^12                                                                                                       |
|![Count_sketch_14](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/4011abcd-4988-4430-bbbb-e4d70e8ce721)| ![Custom_sketch_14](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/da827a67-f106-43b5-9264-3d8e168e6ad2) |![Min_sketch_14](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/3fd63e44-ca7d-403c-8d39-ff8a78db4e7c) |
| When R=2^14                                                                                                         |  When R=2^14                                                                                                                                  |  When R=2^14                                                                                                       |
|![Count_sketch_18](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/6f05e7d7-b57f-40af-85d8-99754edfbaed)| ![Custom_sketch_18](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/3d2b4a5b-1236-4921-a69d-6e54ca270397) |![Min_sketch_18](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/c080f6a7-2164-45dd-96ac-f9e9bfcbff00) |
| When R=2^18                                                                                                         |  When R=2^18                                                                                                                                  |  When R=2^18                                                                                                       |

- The variance of the error for the infrequent and random keys for the custom sketch is more spread across relative to the previous graphs
- In general, range of the Custom-sketch is much lower than the Min-sketch and Count-sketch. Although, the majority of the error tends to go to the
extremes
![MAE_freq](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/8e241cca-491d-40c6-b711-5c93b669d238)
![MAE_infreq](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/3057c0af-0103-4315-a8d8-d960138c23ad)
![MAE_rand](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/02adce66-8eec-482f-84f3-91107846fd7a)



| Mean Absolute Error for Frequent hitters                                                                            | Mean Absolute Error for Infrequent hitters                                                                                                    | Mean Absolute Error for Infrequent hitters                                                                         |
| :---:                                                                                                               |     :---:                                                                                                                                     |                                                                                                              :---: |
|![MAE_freq](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/8e241cca-491d-40c6-b711-5c93b669d238)       | ![MAE_infreq](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/3057c0af-0103-4315-a8d8-d960138c23ad) |![MAE_rand](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/02adce66-8eec-482f-84f3-91107846fd7a)      |


*The observed trends persist across all R values, as depicted in the Mean Absolute Error (MAE) plot for R values [9, 10, 11, 12, 14, 18]. Notably, Custom-Sketch closely mirrors Count-Sketch in terms of MAE. Particularly intriguing is the significant superiority of Custom-Sketch over Min-Sketch and slight advantage over Count-Sketch for Heavy-hitters when R is small.Conversely, for random and infrequent hitters, the MAE curves of Custom-Sketch and Count-Sketch align closely.*

![Intersection of Top-500 vs  Actual Top-100](https://github.com/Jeffrey-Joan/OneMinSketch/assets/57098615/73273afe-d4e0-4b2b-942e-6d3487f891e2)

- Another useful trait of sketches is keeping track of the top-n hitters
- Hence, the above graph is the number of top-500 hitters in the sketch that are the actual top 100 hitters across all R values
- We can observe that when R=9, custom-sketch has the most number of actual top 100 hitters in its top-500
- For other R values, Count-Min Sketch performs marginally better than the Custom-Sketch
- However, our Custom-Sketch Convincingly beats the Count Sketch


## Conclusion

- Our Custom-Sketch(OneMinSketch) is an ideal sketch to use when there is significant memory constraints because it convincingly beats Min-Sketch and Count-Sketch when R is small
- Based on Mean Absolute Error, our Custom model(OneMinSketch) convincingly outperforms the Count-Min Sketch
- Based on Top 100 hitters vs Top 500 hitters of the sketch, Our Custom-Sketch(OneMinSketch) convincingly outperforms the Count-Sketch
- Making the Custom-Sketch(OneMinSketch) a very balanced and powerful sketch for tackling streaming data
