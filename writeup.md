A short report (1–2 pages) covering:

- **Baseline comparison:** MLP vs. base CNN — what was the accuracy difference? Why does the CNN do better (or not)?
- **Experiment summary:** A table of all your MLflow runs showing architecture, key hyperparameters, and test accuracy.
- **Analysis of experiments:** For each experiment in Parts 4 and 5, what did you change, what did you expect, and what happened? Reference your MLflow metrics.
- **Visualization discussion:** What do the learned filters look like? How do the feature maps relate to the input?
- **Reflection:** What surprised you? If you had another week, what would you try next?


Starting off, comparing the MLP and base CNN, the accuracy increase is not too big but still substantial (0.9802 -> 0.9917), however using the confusion matrix we can see the MLP struggles significantly more classifying 2,3, and 4s (double digit entries in misses.) compared to the base CNN. After expermineting with the CNN architecture, the results were as followed:

Name     | Architecture                    | Accuracy
======================================================
CNN_Base | CNN-1-16-32-128-10 3x3 kernel   | 0.9917
CNN_Exp1 | CNN-1-16-32-64-128-10 3x3 kern  | 0.9923
CNN_Exp2 | CNN-1-16-32-128-10 5x5 kernel   | 0.9921
CNN_Exp3 | CNN-1-16-32 3x3 kern + dropout  | 0.9930

For experiment 1, I added a third convolution layer, which added some depth and added some small accuracy. This outcome wasn't unexpected as I expected some increase with an additional conv. layer. For experiment 2, I changed the kernel size to 5x5, which wasn't as effective of an increase compared to the extra conv. layer, and I didn't expect a substantial increase as well. And finally, for experiment 3, I implemented dropout which had the highest test accuracy of all the experiments, which honestly surprised as I thought it would've been in line with the other experiments.

Refering to the visualizations, the learned filters were interesting as they're a bunch of blobs of 3x3 pixels, but I can vaguely see how they can be utilized based on the number. As for the feature extraction, I can see how the various edge detections and filters make up the sample image (7), and how the conv2 layer simplifies/generalizes it more.

For the most part, nothing was too surprising, and if I had another week I think I would try and implement both the dropout, and maybe more conv layers just to experiment.





