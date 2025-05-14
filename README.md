# GeometricRegressor_V1
An analysis of angular and other geometric relations in training and output features of datasets
## The Geometric Relations Analyser

The geometric relations analyser is an algorithm to test certain key variables for a potentially new supervised machine learning model tentatively called **Geometric Regressor**.

The analyser is built to explore the mathematical principles and, most importantly, the statistical reliability of parameters that might potentially be used in the Geometric Regressor

In a nutshell, here is how Geometric Regressor is envisioned:

Consider the input/training data of a dataset/data frame (using columns A, B, C, and D as an example) and the output/prediction/target column, T, of the dataset. The model would interpret the dataset by mapping data points onto a two-dimensional plane.  
If $A_i$, $B_i$, $C_i$, $D_i$ and $T_i$ are datapoints in the same row in the dataset in their corresponding columns, the input datapoints  $A_i$, $B_i$, $C_i$ and $D_i$ are on the same X-axis and the target datapoint $T_i$ on another axis, say, Y-axis. Lines mapping each of the input datapoints to the target datapoint create triangular shapes, and it is the geometric relations of these shapes that we seek to investigate across all rows of the dataset. We aim to investigate any geometric properties, ratios, equations, etc, that would be consistent across other rows and later be used to predict other target datapoints.

## Parameters to be investigated:

### Single-ray angle $\theta_{k}$
(A ray is just a mapping/projection from an input datapoint to the output datapoint)

$\theta_{k} = \text{arctan}(X_{k}/T)$ where $X_{k}$ is the signed horizontal distance of feature k from O, O is the origin.  

**Stability hypothesis**  
If each feature is roughly a fixed multiple of T (e.g, $X_{k} ≈ \theta_{k}T$ ), then $\theta_{k}$ approaches a constant arctan$(\theta_{k})$.

**For prediction**  
At inference: choose a learned $\hat{\theta_{k}}$ and calculate  $T_{pred} =  X_{k}/\text{tan} \theta_{k}$.  

### Angle ratios $\theta_{i}/\theta_{j}$

Take any two rays/mapping i, j and use the ratio of those angles. In this case we shall investigate all the different combinations.

**Stability hypothesis**  
Products of proportionalities cancel T out entirely, so tiny noise in T or uniform scaling leaves the ratio unchanged.

Gives you a relation(for prediction):  
   
$X_{i}/X_{j} = \text{tan}(\theta_{i})/\text{tan}(\theta_{j})$

### Slope differences  

Let the slope the projection K to target be $m_{k} = T/X_{k}$ and that of another datapoint l be $m_{l}$  
Then take the difference $m_{k} - m_{l}$

**Stability hypothesis**  
For perfect linear relationships the difference is constant; with noise it clusters.

For the different features/parameters, we can take the weighted mean to be the final predicted T



