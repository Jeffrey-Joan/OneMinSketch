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
  - Min-sketch : ~80,000
  - Count-sketch : ~ 40,000
  - Custom-Sketch : ~ ~17,500
- Another observation is how different the variance of the error for infrequent and random hitters are for the Custom sketch(OneMinSketch) as opposed to that of Min-Sketch and Count-Sketch
