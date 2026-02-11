# Title: Learning Probability Density Functions using Data Only

# Assignment Overview
In this assignment, the goal is to learn the probability distribution of data using only samples, without assuming any predefined mathematical form. A Generative Adversarial Network (GAN) is used to learn the distribution of a transformed variable created from real NO₂ concentration data.

# Dataset
Dataset used: India Air Quality Data, 
Feature Used: NO₂ concentration, 
Dataset Link: https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data

# Objective
The objectives of this assignment are:
To transform NO₂ values (x) into a new variable (z) using the given equation, 
To train a GAN to learn the distribution of z using data samples only, 
To generate new samples from the trained generator, 
To estimate and visualize the probability density function of z.

# Transformation Used

The transformation applied on NO2 values is based on the roll number: z = x + ar × sin(br × x), where: ar = 0.05 × (r mod 7), br = 0.3 × ((r mod 5) + 1), r is the university roll number.

# GAN Architecture
Generator:
1. Takes random noise sampled from N(0,1)
2. Uses fully connected layers with ReLU activation
3. Generates synthetic samples of z

Discriminator:
1. Takes real and generated samples as input
2. Uses fully connected layers with LeakyReLU activation
3. Classifies samples as real or fake

The generator and discriminator are trained together so that the generator learns to produce realistic samples.

# Methodology
The following steps are performed:
1. Load the dataset and extract NO₂ values
2. Remove missing or invalid entries
3. Compute the transformation parameters using the roll number
4. Transform x values into z
5. Normalize the data for stable GAN training
6. Train a GAN using only samples of z
7. Generate a large number of samples from the trained generator
8. Estimate the PDF using histogram and KDE-based visualization
9. Compare real and generated distributions visually

# PDF Estimation
The probability density function is estimated as follows:
1. The real transformed data (z) is visualized using a normalized histogram
2. The GAN-generated samples are used to estimate the PDF using Kernel Density Estimation (KDE)
                   
No parametric PDF is assumed during GAN training. KDE is used only as a visualization tool.

# Results
a_r = 2.0,
b_r = 1.2.

A plot is generated showing:
1. Histogram of real transformed samples
2. KDE curve obtained from GAN-generated samples

This comparison shows how well the GAN has learned the underlying distribution.

PDF Plot (obtained from GAN samples):
<img width="900" height="533" alt="image" src="https://github.com/user-attachments/assets/78bb5b58-b48f-4532-b2e0-b73a5dde4825" />

# Observations
Mode Coverage:
The GAN successfully captures the main peak and overall shape of the transformed distribution.

Training Stability:
The generator and discriminator losses remain stable throughout training, indicating balanced learning.

Quality of Generated Distribution:
The KDE curve from GAN-generated samples closely follows the histogram of real data, with minor deviations in the tails.

# Conclusion

This assignment shows that a GAN can learn an unknown probability distribution directly from data samples. The trained generator produces samples whose distribution closely matches the real transformed data.
