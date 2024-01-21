Decoding Upper Limb movements from the EEG Signals

Jo-fan Chien*, Dawei Li*, Haoyin Xu*, and Qin Li*

Introduction

To better improve the life quality of the disabled population, modern prostheses with various mechanisms
are developed for those with limb trauma and dysfunctions. As researchers point out, an appropriate prosthesis
with supporting community service could greatly improve one's ability to produce income and participate
in communities such as being involved in education and social activities [1]. The current prosthesis could be
categorized into three major types: passive prosthesis, active prosthesis, and lastly a hybrid prosthesis. The
former prioritized the external appearance and the comfort of the tool, while the latter two provide some
functional support with mechanical feedback [2]. However, the precision of these hybrid prostheses remained
to be poor and the user usually takes a signicantly longer time to be adapted to them [3]. Hence, to provide
a better design of the active prosthesis, we proposed that EEG signal could be a great source of predicting
one's intended movement. We aim to predict different types of upper limb movements based on the EEG
signal. We hypothesize that different upper limb movements would produce different EEG signals and we
can predict the upper limb motion based on EEG signals. This project may help us better understand the
associations between neural activities and the control of limb movements. Besides, this exploratory work
would promote the design of next-generation prothesis and benet the people with the needs.

Method

2.1 Data and Preprocessing

The original data were obtained from the public access folder from the Muller-Putz Group[4]. The
dataset includes experimental runs obtained from 15 healthy subjects. In each trial, subjects are instructed
to perform different upper limb movements. There are 6 movements in total: elbow exion, elbow extension,supination, pronation, hand close, and hand open. Lastly, there were also some resting trials to serve as the control. The sampling rate was 512Hz and each trial is approximately 7 seconds.
A 1Hz high-pass lter and a 60Hz notch lter were applied to remove the baseline drift and the ground
noise. The cleanline() method from EEGLAB toolbox was also applied to remove any linear noise [5]. Bad
channels/data were removed and interpolated through the artifact subspace reconstruction (ASR) method.
Lastly, the raw data were epoched from -2 seconds (2 seconds before the event onset) to 5 seconds after the
onset. The entire preprocessing process was performed through the EEGLAB toolbox on Matlab.
In order to analyze the frequency domain information, we extracted the band power for each channel.
We performed band-pass lters for  (1-3.5 Hz),  (4-7 Hz),  (7.5-13 Hz),  (13.5-30 Hz) and 
 (30.5-50
Hz) respectively. A Hibert transform was performed on each ltered epoched time series within the time
window of each trial, followed by averaging over the absolute values, to obtain the band power for each trial.
Signals from all the 61 electrodes with their band power are merged. Overall, there are 305 features used in
the frequency domain data, i.e. 5 (band power/electrode)  61 (electrode) = 305 (features).
As a prevalent method for dimensionality reduction, Principal Component Analysis (PCA) can project
the 305 frequency features onto the space formed by the principal components, which preserves the largest
variance. The features extracted by PCA were compared to the original features in predicting the labels.
In this study, Subject One with a total of 256 trials was analyzed. Due to the incompletion of data and
changes in event marker naming styles, we had difficulties interpreting the data from other subjects and
would not involve them in this study.
2.2 Model Training and Algorithms
In this project, we majorly used two types of models, namely the support vector machine and the
convolutional neural network to t the EEG signals with the upper limb motion.

References
[1] P. Gallagher and D. Desmond, Measuring quality of life in prosthetic practice," Prosthetics
& Orthotics International, vol. 31, no. 2, pp. 167
[2] R. Brack and E. H. Amalu, A review of technology, materials and r&d challenges of upper limb
prosthesis for improved user suitability," Journal of Orthopaedics, vol. 23, pp. 88
[3] L. A. Wheaton, Neurorehabilitation in upper limb amputation: understanding how neurophysiological
changes can aect functional rehabilitation," Journal of NeuroEngineering and Rehabilitation, vol. 14,
no. 1, May 2017.
[4] P. Ofner, A. Schwarz, J. Pereira, and G. R. Muller-Putz, \Upper limb movements can be decoded from
the time-domain of low-frequency EEG," PLOS ONE, vol. 12, no. 8, p. e0182578, Aug. 2017. 
[5] A. Delorme and S. Makeig, EEGLAB: an open source toolbox for analysis of single-trial EEG dynamics
including independent component analysis," Journal of Neuroscience Methods, vol. 134, no. 1, pp. 9
[6] V. J. Lawhern, A. J. Solon, N. R. Waytowich, S. M. Gordon, C. P. Hung, and B. J. Lance, \Eegnet:
a compact convolutional neural network for eeg-based brain{computer interfaces," Journal of neural
engineering, vol. 15, no. 5, p. 056013, 2018.
