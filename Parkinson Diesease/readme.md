**Parkinsons Disease**

Parkinson’s Disease (PD) is a degenerative neurological disorder marked by decreased dopamine levels in the brain. 
It manifests itself through a deterioration of movement, including the presence of tremors and stiffness. 
There is commonly a marked effect on speech, including dysarthria (difficulty articulating sounds), hypophonia (lowered volume), and monotone (reduced pitch range).

This is a classification problem, "Status" of the patient 0 being healthy and 1 for having the disease.

> Link to DataSet : https://archive.ics.uci.edu/ml/datasets/Parkinsons#:~:text=Data%20Set%20Information%3A,(%22name%22%20column).

Description of the Columns in the dataset.

- name : ASCII subject name and recording number
- MDVP:Fo(Hz) : Average vocal fundamental frequency
- MDVP:Fhi(Hz) - Maximum vocal fundamental frequency
- MDVP:Flo(Hz) : Minimum vocal fundamental frequency
- MDVP:Jitter(%),MDVP:Jitter(Abs),MDVP:RAP,MDVP:PPQ,Jitter:DDP - Several measures of variation in fundamental frequency
- MDVP:Shimmer,MDVP:Shimmer(dB),Shimmer:APQ3,Shimmer:APQ5,MDVP:APQ,Shimmer:DDA : Several measures of variation in amplitude
- NHR,HNR : Two measures of ratio of noise to tonal components in the voice
- status : Health status of the subject (one) - Parkinson's, (zero) - healthy
- RPDE,D2 : Two nonlinear dynamical complexity measures
- DFA : Signal fractal scaling exponent
- spread1,spread2,PPE : Three nonlinear measures of fundamental frequency variation.

> The target Varaiable has imbalanced classes.

The Name data which provides no valuable information for the model building has been droppped. The data consists of frequency measures and amplitudes, there is high correlation amomg the data (especially amomg the frequencies attributes and among the amplitude attributes).


