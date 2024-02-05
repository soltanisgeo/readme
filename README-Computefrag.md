# computeFrag
<br>
A code for computing empirical fragility curves based on logistic regression
<br>
[![Zenodo](https://zenodo.org/badge/DOI/DOI_NUMBER.svg)](https://doi.org/10.5281/zenodo.5167276)
<br>
<p align="center">
  <img src="https://github.com/soltanisgeo/readme/blob/main/damageScale-git.png" />
</p>
<br>
<br>
This code provides an ensemble of the fragility curves and their corresponding confidence bands for a set of mutually exclusive and collectively exhaustive (MECE) damage states (DS), where DS<sub>i</sub>: i=0,N<sub>DS</sub>. The fragility is defined as the probability of damage D exceeding the threshold D<sub>i</sub> for damage state DS<sub>i</sub> and is denoted as P(D>Di|IM).  The set of damage levels (D<sub>i</sub>, i=0,N<sub>DS</sub>) mark the thresholds of damage states (DS<sub>i</sub>). 
<br>
The parameters of the empirical fragilities associated with different damage level are estimated jointly using Bayesian inference by employing a Markov Chain Monte Carlo Simulation (MCMC) scheme. 
<br>
<br>
The **inputs** of the code are the following:

<br>**inputFileName: The filename of a csv file containing two columns, one for the intensity measure and one for the damage state. In this example, it is the file IM_and_DS.csv.

<br>**NDS: The number of the damage states.

<br>**dIM, IM_max: The step and the maximum absolute value for the IM vector.

<br>**dvec_alpha0, dvec_alpha1: The increments of the vectors of the two logistic regression parameters.

<br>**confid: The number of standard deviations defining the confidence interval for the robust fragility (fixed for all the DS).

<br>
<br>
The **outputs** of the code are the following:

<br>**sample_theta_model: Ns=500 samples generated from the posterior joint probability distribution for logistic fragility model parameters (e.g., a total of 10 parameters for 5 DS, 2 parameters/DS) using the MCMC procedure. 

<br>**rfragility: Robust (the mean fragility among the Ns=500 realizations for each DS) fragility curve with the row showing the IM vector and a number of columns equal to the number of DS.

<br>**sfragility: The standard deviation of the Ns=500 fragility curve samples (the same structure as rfragility). For having the fragility with a confidence, you should do this operation: rfragility+confid*sfragility (e.g., if confid=±1, we have 16th and 84th percentiles, if confid=±2, we have 2nd and 98th percentiles).

<br>**etaIMc: The median of rfragility (i.e., the IM value corresponding to 50% probability from rfragility). It is a vector with its length equal to the number of DS.

<br>**betaIMc: The equivalent logarithmic standard deviation of the rfragility (i.e., half of the logarithmic distance between IM values corresponding to 84% and 16% probabilities, respectively). It is a vector with its length equal to the number of DS.

<br>
<br>
**To execute the code, run the script computeFrag.py.**
<br>
**Requirements:** MATLAB, numpy, pandas