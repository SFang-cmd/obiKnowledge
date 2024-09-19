- **Accuracy = fraction of samples that are correctly predicted**
- However, even accuracy isn't necessarily the "right" metric
	- Imbalanced data: if 99% of sample data are negative, then accuracy of predicting $f_{\beta}(x)=0$ is **99%**
	- Not all Mistakes are the same: "better that ten guilty persons go free than that one innocent person be convicted"

The **Confusion Matrix:** Predicted vs Actual class

|     | Yes | No  |
| --- | --- | --- |
| Yes | TP  | FN  |
| No  | FP  | TN  |
