## MFCC Feature Extraction

Mel-frequency cepstral coefficients (MFCCs) are most commonly used audio features having wide application in the field of audio. MFCCs are used for automatic speech
recognition (ASR) as well for speaker recognition. MFCC feature provides unique coefficient to a particular sample of audio. The number of step are followed MFCC
calculation like framing, windowing, DFT, Mel scale conversion and finally applying DCT. 
The block diagram of MFCC is given below:-



![MFCC](https://user-images.githubusercontent.com/58771064/98448633-71ca0800-2153-11eb-8c1f-b32898857aeb.png)


Lets see each steps in details:-

# Pre-Emphasis: 
pre-emphasis is a process used to increase the amplitude of high frequency components. The high frequency components have amplitude low as compared to low
frequency components that reduces the signal to noise ratio of signal. pre-emphasis of signal increases the energy of signal at higher frequency and improves signal to noise ratio of signal. If x(n) is the audio signal then pre-emphasis can be done using formula:-

                                y(n)= x(n)-a*x(n-1)         where a=0.95
# Framing and windowing: 
Spectral content of speech signal continuously changes overtime (for example formant changes as a function of spoken phoneme). Applying DFT over a long window doesn’t reveal transition in spectral content. So the procedure for computing DFT is to divide the audio sample into small frames of equal length. The speech signal can segmented into small frames of length . to 50 msec with the overlap of 25 to 50 %. 

# windowing:
Next step is to define window function. Each of the frames multiplied with window functions in order to remove the discontinuity at the boundary of each frames. windowing reduces the effect of spectral leakage. it reduces the amplitude of discontinuity at the boundry of each finite sequence acquired by the digitizer. window consist of multiplying time record by finite length window with an amplitude that varry smoothly and gradually towards zeros at the end, that makes the end point sharper. The most commonly used window function is hamming window.

                            Y (n) = X (n) * W (n) ,Where W (n) is the window function


![widowing](https://user-images.githubusercontent.com/58771064/98449109-ef434780-2156-11eb-9250-42e6ceaa5c16.png)


# DFT:
DFT is used to convert the time domain signal into frequency domain. By applying DFT we get frequency response of the signal. Output of DFT is a spectrum. The log of
magnitude of DFT is taken to get the envelope of the spectrum.

![dft envelop](https://user-images.githubusercontent.com/58771064/98449187-75f82480-2157-11eb-83fa-e1e05a8783e2.png)
                             


# Mel Filter bank: 
The final step to computing filter banks is applying triangular filters, on a Mel-scale. After getting envelope our taget is to detect the formant frequency using some filter along the spectrim if we detect the formant then avarage power of the specific filter is high. 

As the frquency perceived by human being is not in linear scale. so instead of taking linear filter, mow we convert the filter bandwidth as per mel scale. The equation for conversion of normal frequency (Hz) scale to Mel-scale (m) is given by the equation-
                                                         
                                                         m=2595*log10(1+f/700)

![triangular window](https://user-images.githubusercontent.com/58771064/98449349-d5a2ff80-2158-11eb-9c10-864c797fe71f.png)
                   

# Discrete cosine transform:
DCT is applied on the 20 log energy obtained from the triangular band pass filters to have L mel-scale cepstral coefficients. Here we can use IDFT also but it requires complex arithmetic. DCT implements same function as IDFT more efficintly by taking the advantage of redundancy in the signal.DCT formula is given below-

                                              Cm=∑𝑘=1/𝑁 cos [m*(k-0.5)*π/N]* ,m=1,2……L

                                                                  Where, N = Number of triangular band pass filters
                                                                         L =Number of mel-scale cepstral coefficients.                                                                                 
Usually N=40 and L=13. DCT is used to convert the frequency domain signal into Que-frequency domain. These features are known as the mel-Frequency cepstral coefficients (MFCC).





                                            
