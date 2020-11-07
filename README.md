Mel-frequency cepstral coefficients (MFCCs) are most commonly used audio features having wide application in the field of audio. MFCCs are used for automatic speech
recognition (ASR) as well for speaker recognition. MFCC feature provides unique coefficient to a particular sample of audio. The number of step are followed MFCC
calculation like framing, windowing, DFT, Mel scale conversion and finally applying DCT. 
The block diagram of MFCC is given below:-



![MFCC](https://user-images.githubusercontent.com/58771064/98448633-71ca0800-2153-11eb-8c1f-b32898857aeb.png)


Lets see each steps in details:-

# Pre-Emphasis: 
pre-emphasis is a process used to increase the amplitude of high frequency components. The high frequency components have amplitude low as compared to low
frequency components that reduces the signal to noise ratio of signal. pre-emphasis of signal increases the energy of signal at higher frequency. If x(n) is the audio signal then
pre-emphasis can be done using formula
