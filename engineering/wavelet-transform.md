# Wavelet Transform

### Wavelet Transform VS Fourier Transform

The Fourier Transform provides frequency information of a signal \(frequencies + respective magnitudes\). However, it does _not_ tell us **when in time** those frequencies exist. 

Therefore, the Fourier Transform is applied to stationary signals since it lacks the capability to provide frequency information for a localized signal region in time.

### Short-Term Fourier Transform

The short term fourier transform gives us a time-frequency representation of our signal by assuming some portion of the non-stationary signal is stationary and then taking a vanilla fourier transform of each stationary portion.



![Example of STFT Window](../.gitbook/assets/image%20%2834%29.png)

The STFT is a trivial extension of the Fourier Transform mathematically:

![Explicit definition for FT &amp; STFT](../.gitbook/assets/image%20%2820%29.png)

The limitations of the STFT are relatively intuitive:

1. The window function is finite, so the frequency resolution decreases.
2. Fixed length of the window means that the time and frequency resolutions are fixed for the entire length of the signal.
   1. We cannot know which frequencies exist at what time instance... but we can know what frequency bands exist at what time intervals.

### The Wavelet Transform

This transform results in analyzing a signal into different frequencies at different resolutions -- multiresolution analysis.

![](../.gitbook/assets/image%20%2833%29.png)





