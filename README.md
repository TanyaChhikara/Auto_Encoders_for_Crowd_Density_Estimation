<h1>Auto-Encoders for Crowd Density Estimation</h1>

<h3>About The Project</h3>
<p> Counting the number of people in an image or video
has attracted the attention of several researchers due to their 
increasing use in situations like video monitoring, public safety, 
crowd control, etc. Redirecting the focus from primitive 
techniques like detection, regression, and clustering, this research 
utilizes the advanced concepts of CNNs and Computer Vision. The 
project introduces a method that infers the headcount of the crowd 
by generating a density map using the Gaussian filter. An auto-encoder model, which is an unsupervised machine learning 
algorithm has been trained upon a dataset of around 1200 
pictures. It comprises 4 convolutional layers for the encoder and 4 
deconvolutional layers for the decoder (Conv2DTranspose). The 
model outperforms the cutting-edge crowd-counting methods and 
the mean squared error of the predicted values with respect to 
the test values obtained is reported to be 0.649%.</p>

<h3>Codes</h3>
<li><a href="https://colab.research.google.com/drive/1KxgQiBYpxsE1B_NP9P0ZFNtPiskQ3A_f?usp=sharing">Auto-Encoders Part 1</a><br></li>
<li><a href="https://colab.research.google.com/drive/1TbDJ2ZSOkdE58pmAa4p1_JYoL3jNDNNI?usp=sharing">Auto-Encoders Part 2</a><br></li>

<h3>Dataset Used</h3>
The Shanghai Tech dataset, a recent large-scale crowd-counting dataset composed of 1198 photos and 330,165 labelled heads, has been used in this study. The dataset, which is divided into Parts A and B, is one of the largest in terms of the total number of annotated individuals. Part A is made up of 482 images that were picked at random from the Internet, while Part B is made up of pictures that were taken on the streets of Shanghai’s major cities. Images in Part A have a higher density than those in Part B. Both components are further separated into sets for training and evaluation. While Part B’s training and test have 400 and 316 photos, respectively, Part A’s training and test have 300 and 182 images. The dataset succeeds in its objective to produce a difficult dataset with a variety of scene kinds and densities. The dataset also includes MATLAB files with the coordinates of the human heads in each of the test and training photos.
<br>
<h3> Dataset Description</h3>
<img src="https://github.com/TanyaChhikara/Auto_Encoders_for_Crowd_Density_Estimation/blob/main/media/image1.png" alt="Smiley face" height=450px>
<h3> Contributions of the Paper </h3>
To sum up, the following folds represent the bulk of this paper's contributions: 
<li> Counting Crowding from any Angle: In this research, a convolution neural network that can count people properly in a single image from nearly any angle is presented. As of now, the dataset used contains the maximum marked heads for crowd counting. On all test cases, the approach surpasses cutting-edge crowd-counting techniques. </li>
<li>Conv2d - Conv2dtranpose Auto Encoder Process: An auto-encoder is an unsupervised machine-learning technique that attempts to recreate a picture using fewer bits from the latent space representation after receiving it as input. In this research, an architecture was developed with 4 convolution layers for the encoder and 4 deconvolutional layers (Conv2DTranspose) for the decoder. Thus, the auto-encoder and decoder model performed in this paper has become immensely popular for reconstructing images to obtain high cases of accuracy. </li>

<h3> Data Pre-Processing </h3>

<p> The processing begins with analysing the images in the dataset. They are in the form of NumPy n-Dimensional arrays (for example, the shape of an image is (704, 1024, 3) where the third number i.e. 3 represents that the image has three values corresponding to the red, green, and blue colours respectively) and are displayed using OpenCV’s imread() function. Further, the MATLAB files are loaded using scipy.io.loadmat function. These files in the dataset contain information/coordinates where humans (or rather their heads) are located. It returns a dictionary with variable names as keys (header, version,  global, and image info) and loaded matrices as values. From this dictionary, the ‘image_info’ key and its values are utilized to gather the coordinates of the image. Looping across each pair of coordinates, a marker is drawn on the train image. 
<br> 
<br>
<img src="https://github.com/TanyaChhikara/Auto_Encoders_for_Crowd_Density_Estimation/blob/main/media/image2.jpg" alt="Smiley face" height=450px>

<p> The next step is to create a blank canvas using NumPy’s zeroes function with dimensions equal to that of the image. This blank canvas will further be used to create density plots using a Gaussian filter. At every pair of coordinates obtained above, the value of the matrix is set to 1. The blurring, noise reduction, and feature removal of the images are accomplished using a 2-D convolution operator known as the Gaussian smoothing operator. In this sense, it is similar to the mean filter, but it makes use of a distinct kernel that has a Gaussian (crescent) crest.
<br>
The output of this function is an array of the same shape as the input which implies that a density kernel is generated for the exact input image. 
The last step of the pre-processing includes using Scipy’s gaussian filter function to create a density kernel for the image in the dataset by passing the above-mentioned properties to the function. Multiple cmap values can be utilised to generate these maps.
<br> 
<br>
<img src= "https://github.com/TanyaChhikara/Auto_Encoders_for_Crowd_Density_Estimation/blob/main/media/image3.jpeg" alt="Smiley face" height=450px>

<h3>Conv2d - Conv2dtranpose Auto Encoder Process </h3>

The two train and test arrays formulated in the above processing process are now utilized for the model training that uses a Conv2d - Conv2dtranpose Auto Encoder Process. A machine learning technique known as an autoencoder attempts to rebuild a picture using fewer bits from the latent space representation after receiving it as input.
<br> 
<br>
<img src="https://github.com/TanyaChhikara/Auto_Encoders_for_Crowd_Density_Estimation/blob/main/media/image6.png" alt="Smiley face" height=450px>

<h3>Results</h3>
Using the model, density plots are reconstructed as a prediction. The two prediction plots here are the outputs of the same image plotted using two different values of cmap to show variation. The model is trained using 10 epochs and the MSE loss associated with every iteration is shown in the table given. The mean loss while training the model is = 0.01605. 
<br> 
<br>
<img src="https://github.com/TanyaChhikara/Auto_Encoders_for_Crowd_Density_Estimation/blob/main/media/image8.jpg" alt="Smiley face" height=150px>

The mean of the predicted values of the first four predictions (images) is shown above. 

<h3>References</h3>
<pre>
[1]	P. Karpagavalli and A. V. Ramprasad in “Estimating the density of the people and counting the number of people in a crowded environment for human safety,” 2013 International Conference on Communication and Signal Processing, 2013, pp. 663-667, doi: 10.1109/iccsp.2013.6577138. (Corpus ID: 45820790)
[2]	H. Yang and H. Zhao in “A novel method for crowd density estimations,” IET International Conference on Information Science and Control Engineering 2012 (ICISCE 2012), 2012, pp. 1-4, doi: 10.1049/cp.2012.2297, (INSPEC Accession Number: 14031120
[3]	X. Ding, Z. Lin, F. He, Y. Wang and Y. Huang, "A Deeply-Recursive Convolutional Network For Crowd Counting," 2018 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), 2018, pp. 1942-1946, doi: 10.1109/ICASSP.2018.8461772.
[4]	J. Ferryman and A.-L. Ellis in the “Performance evaluation of crowd image analysis using the pets2009 dataset,” PRL, vol. 44, pp. 3–15, 2014
[5]	C. C. Loy, K. Chen, S. Gong, and T. Xiang, “Crowd counting and profiling: Methodology and evaluation,” in MSVAC. Springer, 2013, pp. 347–382
[6]	J. C. S. J. Junior, S. R. Musse, and C. R. Jung, “Crowd analysis using computer vision techniques,” ISPM, vol. 27, no. 5, pp. 66–77, 2010
[7]	T. Li, H. Chang, M. Wang, B. Ni, R. Hong, and S. Yan, “Crowded scene analysis: A survey,” TCSVT, vol. 25, no. 3, pp. 367–386, 2015
[8]	T. Teixeira, G. Dublon, and A. Savvides, “A survey of human-sensing: Methods for detecting presence, count, location, track, and identity,”ACM Computing Surveys, vol. 5, no. 1, pp. 59–69, 2010
[9]	V. A. Sindagi and V. M. Patel, “A survey of recent advances in CNN- based single image crowd counting and density estimation,” PRL, vol. 107, pp. 3–16, 2018
[10]	D. Ryan, S. Denman, S. Sridharan, and C. Fookes, “An evaluation of crowd counting methods, features and regression models,” CVIU, vol. 130, pp. 1–17, 2015
[11]	S. A. M. Saleh, S. A. Suandi, and H. Ibrahim, “Recent survey on crowd density estimation and counting for visual surveillance,” EAAI, vol. 41, pp. 103–114, 2015
[12]	M. S. Zitouni, H. Bhaskar, J. Dias, and M. E. Al-Mualla, “Advances and trends in visual crowd analysis: A systematic survey and evaluation of crowd modelling techniques,” Neurocomputing, vol. 186, pp. 139–159, 2016
[13]	M. Fu, P. Xu, X. Li, Q. Liu, M. Ye, and C. Zhu, “Fast crowd density estimation with convolutional neural networks,” EAAI, vol. 43, pp. 81– 88, 2015
</pre>
