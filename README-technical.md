# Autoencoder Node Saliency (ANS)
Autoencoder Node Saliency (ANS) measures the distribution of the latent representations generated by an autoencoder, ranks and identifies specialty nodes that are able to seperate two given classes. ANS explains the unsupervised learning process in autoencoders.

This ANS code contains the function that computes Autoencoder Node Saliency.


### Setup
To set up the Python environment needed to train and run this model:
1. Install [conda](https://docs.conda.io/en/latest/) package manager. 
2. Clone this repository. 
3. Create the environment as shown below.

```bash
   conda env create -f environment.yml -n ans 
   conda activate ans 
         ```

# Use
To include the function, import the ans module in the beginning of your Python code.
```
from ans import ans
```
A bytecode module "ans.pyc" will be generated.

### Input:
ans.py reads in three inputs
  - A: Activation values of each sample  
  - L: Class labels of each sample
  
  numBins: Number of bins used in the evaluation (default = 10)

Activation values are generated using the optimal weight and bias terms in the autoencoder. Class labels should be given in datasets. The Data folder contains the A and L values used in the example. 
  
  
### Output:
  - NED: Normalized entropy difference from both labels, 0 and 1.  
  - NED0: Normalized entropy difference from labels 0. 
  - NED1: Normalized entropy difference from labels 1.
  - sns_incr: Supervised node saliency with increasing probability distribution. 
  - sns_bi: Supervised node saliency with binary distribution.  
  - g0Count: Histogram bar counts for class 0 at each node. 
  - g1Count: Histogram bar counts for class 1 at each node.  

# Results
Details on how to generate results described in the two papers can be found in the following two examples.

### MNIST Dataset
- Ya Ju Fan. "Autoencoder Node Saliency: Selecting Relevant Latent Representations." CoRR, abs/1711.07871. 2017. [Link to paper.](https://doi.org/10.1016/j.patcog.2018.12.015)

An example of applying ANS on the MNIST dataset can be found in 

```
python apply_ans_mnist_01.py
```
It generates the top histogram in Figure 2(a) in the paper. 

### Normal and Cancer Cells
- Ya Ju Fan, Jonathan E. Allen, Sam Ade Jacobs and Brian C. Van Essen. "Distinguishing between Normal and Cancer Cells Using Autoencoder Node Saliency." Second ISC HPC Applications in Precision Medicine Workshop. July 2018. [Link to paper.](https://arxiv.org/abs/1901.11152)

  An example of applying ANS on cancer genome datasets can be found in

```
python apply_ans_tumorNormal.py
```
It generates the top histogram in Figure 6 in the paper.

### Plots
Each of the example generates three plots: the NED curves, the SNS curve and the histogram of the activation values labeled by the two classes on the best classifying node.