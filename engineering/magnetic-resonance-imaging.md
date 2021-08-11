# Magnetic Resonance Imaging \(MRI\)

## How does MRI work?

MRI is fundamentally rooted in the principle of Nuclear Magnetic Resonance \(NMR\):

### Nuclear Magnetic Resonance \(NMR\)

> Certain atomic nuclei demonstrate the ability to absorb and re-emit radiofrequency energy when placed in a magnetic field.

#### How does MRI utilize NMR?

1. The very strong magnetic field imposed by the large magnets in the MRI machine **aligns the nuclei.**
2. The MRI machine then emits a radiofrequency pulse to knock the nuclei out of alignment.
3. The nuclei then precess, giving off an RF signal \(NMR phenomenon\).
   1. **T2 Relaxation:** The RF signal doesn't last forever -- each type of tissue takes a different amount of time to stop emitting the RF signal.
4. The nuclei then realign with the field
   1. **T1 Relaxation:** The amount of time it takes for the nuclei to realign with the field.

{% embed url="http://www.giphy.com/gifs/YIyiAdC2CdlrTtaB9P" %}

### The Larmor Equation

$$
\omega = \gamma B
\newline \text{where }
\newline\omega:\text{frequency of spin precession}
\newline \gamma:\text{a constant inherent to the specific nucleus we're investigating}
\newline B:\text{strength of magnetic field}
$$

_Important conclusion:_ The frequency of precession $$\omega$$is proportional to the magnetic field  strength $$B$$.

### Mechanical Deconstruction

![MRI Machine Deconstructed](../.gitbook/assets/image%20%2832%29.png)

The _large magnet_ \(purple\) that encapsulates all of the other components is responsible for establishing a _strong_ permanent magnetic field.

The _gradient coils_ are modulated \(by altering the $$\vec B$$field in $$\hat x, \hat y, \hat z$$\) to be able to localize where each rf signal is coming from. They are designed such that they produce linearly varying magnetic fields when current flows through them.

The _RF coils_ are responsible for sending/receiving the RF tipping pulse into the tissue \([step 2/3 above](magnetic-resonance-imaging.md#how-does-mri-utilize-nmr)\).

### The Proton, Spin, & Precession

All clinical MRI machines are utilizing the single proton at the nucleus of hydrogen atoms for scanning. Traditional nomenclature refers to the hydrogen nucleus as a generic proton -- but it is noted that we are only really imaging protons _from hydrogen nuclei._

![](../.gitbook/assets/image%20%2822%29.png)

The main property of protons that we are leveraging here is their quantum-mechanical _spin --_ which can be decomposed into a value representing its intrinsic angular momentum & its magnetic moment \(that effectively lets it act as a _tiny_ bar magnet\).

The aforementioned magnetic moment can be quantified in terms of the particle's spin quantum number and a constant called _gyromagnetic ratio_ $$\gamma$$:

$$
\vec \mu = \hbar\vec S\gamma
$$

### Signal Detection & the Larmor Equation

When the proton is knocked off-axis by the RF coils, they precess about the magnetic axis imposed by the large magnet $$B$$. Their precessing frequency  $$\omega$$matches the frequency of the magnetic flux going through a nearby coil of wire:

![](../.gitbook/assets/image%20%2826%29.png)

Per Lenz's Law, this changing magnetic flux induces a voltage through the wire proportional to the rate of change of the flux. This is how we are able to detect an RF signal back!

$$
\text{Lenz's Law:} \space V = -\frac{d\phi}{dt}
$$

We can now simulate our detected signal and come to a few profound conclusions:

![](../.gitbook/assets/image%20%2838%29.png)

We know our detected signal is sinusoidal -- the true insight comes from the[ Larmor Equation](magnetic-resonance-imaging.md#the-larmor-equation):

1. Nuclei with different gyromagnetic ratio will precess at different frequencies in the same magnetic field -- allowing us to possibly distinguish between them.
2. Increasing the magnetic field strength $$\vec B$$ is the _only_ way to increase the frequency of precession $$\omega$$, since the gyromagnetic ratio is a value inherent to nuclei.
   * Even better, increasing the magnetic field strength also increases the amplitude of our signal, due to Lenz's law's formulation around the _rate of change of magnetic flux_, which would be higher with higher frequencies.
3. The greater the flip angle, the larger the magnitude of our detected signal, since it would impose a larger change in magnetic flux -- corresponding to a higher voltage signal.

![](../.gitbook/assets/image%20%2828%29.png)

#### A brief intermission about flip angle

Technically, a particle can only stably exist in one of two states: spin-up & spin-down. However, the quantum reality is that the flip angle is encapsulated in the transition between those two states, which happens in a continuous manner.

### Detected Signal

$$
S(t) =N_{tot} P \sin(\theta)\gamma B \cos(\omega t) e^{-t/T_2}\newline \text{where} \newline
N_{tot}: \text{number of spins}
\newline P: \text{polarization} = \frac{N_\uparrow - N_\downarrow}{N_\uparrow + N_\downarrow}
\newline \theta: \text{flip angle}
$$

In reality, there are many, _many_ nuclei being affected by this MRI procedure. Their collective contribution to the signal is encapsulated within the $$N$$constant in the equation above.

### T2 Weighting & Echo Time

Since each precessing nuclei also imposes a changing magnetic field on the nuclei around it, the spins eventually fall out of sync, which slowly decays the signal output since they become dephased. This is demonstrated by the _Free Induction Decay \(FID\)_ plot:

![Free Induction Decay \(FID\)](../.gitbook/assets/image%20%2845%29.png)

The differing rates of decay can be used \(alongside a threshold\) to differentiate between different types of tissue. The quicker the signal decays \(and the shorter the T2 duration\), the quicker the spins fall out of phase. If we transition into the rotating frame \(setting $$\omega=0$$to better observe the decay rates\), we can arrive at the following modified FID:

![](../.gitbook/assets/image%20%2831%29.png)

The _Echo Time_ is the amount of time we wait to scan the image after we perform [step 2 of our MRI procedure](magnetic-resonance-imaging.md#nuclear-magnetic-resonance-nmr) \(knocking the spins out of alignment with the B field, causing them to precess\). This is a threshold set by the MRI technician to maximize contrast between tissues. This type of imaging \(where the echo time is set to some threshold to maximize tissue contrast\) is called a _T2 Weighted Image_:

![T2 Weighted Image](../.gitbook/assets/image%20%2841%29.png)

### Spin Density Image

The above FID plot simplifies the thresholding by assuming that all the signals have the same starting amplitude -- which is a false assumption since each type of tissue has varying densities of hydrogen atoms \(and thus protons\). A more accurate FID plot that captures the true nuance behind the selection of the echo time threshold is shown below. 

![A more accurate FID plot](../.gitbook/assets/image%20%2835%29.png)

Additionally, this plot seems to indicate that there are certain thresholds that would make our signals indistinguishable \(when the signal amplitudes cross each other\). The reason for this quick aside is to note that in some cases \(such as below\), the quicker we detect the signal, the better of a signal we actually get -- which isn't represented in the initial FID plot above.

If we set our _echo time_ to $$0$$, the $$e^{-0/T_2}$$term goes to 1, and we are simply measuring the number of protons in each tissue. The output of this type of imaging \(with echo time= $$0$$\) is called a Spin Density Image:

![Spin Density Image](../.gitbook/assets/image%20%2839%29.png)

### T1 Relaxation

At this point in time, we can assume that the protons have been completely dephased \(all out of alignment\), which corresponds to the signals converging to 0 on the FID plots above. They then re-align with the magnetic field $$\vec B$$, in a process called T1 Relaxation.

![](../.gitbook/assets/image%20%2842%29.png)

$$
M(t) = M_0(1 - e^{-t/T_1})
$$

### T1 Weighting & Relaxation Time

#### Boltzmann Magnetization

As the spins align with the magnetic field, they converge on to the sample's _Boltzmann Magnetization._ The rate at which they converge back to the Boltzmann Magnetization is determined by the nuclei's $$T_1$$parameter, which is another factor used to contrast differing tissues in the imaging process.

The _Repetition Time \(TR\)_ is a threshold set by the MRI technician to maximize the tissue contrast due to the varying $$T_1$$ for each incoming signal. This is analogous to _Echo Time \(TE\),_ but for T1 Relaxation as opposed to T2 Relaxation.

The longer the $$T_1$$duration is for a given nuclei \(and thus a tissue\), the slower the corresponding signal converges back onto the Boltzmann Magnetization, and the darker the tissue appears in a $$T_1$$weighted image:

![T1 Weighted Image](../.gitbook/assets/image%20%2844%29.png)

### The Complete NMR Experiment

The $$\text{Total Magnetization Vector } M(t)$$can be intuitively broken apart into its two components, which are very well described by the $$T_1 \& T_2$$parameters previously explained.

$$
\text{Longitudinal [z]}: M(t) = M_0(1-e^{-t/T_1})\newline
\text{Transverse [x, y]}: M(t) = M_0e^{-t/T_2}
$$

{% embed url="http://www.giphy.com/gifs/BZpLtnHaBMfl1TrRCw" %}

#### Point of Confusion + My Reasoning:

> In [the video @ 27:48](https://youtu.be/TQegSF4ZiIQ?t=1658), it is stated that we can only really measure the Transverse component \(since that is the only component delivering a detectable signal to the RF coils\). This was a point of confusion for me, until I focused a bit on what the actual signal is composed of, and realized that the signal is a function of a changing magnetic flux through the coil -- via Lenz's Law. 
>
> If I understand correctly, as the spins realign, they are constructively building the sample's overall magnetization collectively in a capacitor-like fashion. The accumulated magnetization is due to all of the protons pointing in the same direction \(also in the same direction as the $$\vec B$$field as shown in the image below\). However, their accumulated magnetization \(Boltzmann Magnetization\) should theoretically not be creating a trivial signal through the RF coils? My understanding is that since the spins start off out of sync \(from T2\), the RF coils would read a low indistinguishable signal since the rate of change of the magnetic flux is convoluted due to all of the spins being out of phase. As they realign with the magnetic field, they individually produce less and less magnetic flux through the RF coils due to their reduced spin angle \(thus producing less magnetic flux in the first place\), which means that the rate of change of magnetic flux is also going down -- AKA the generated signal due to Lenz's Law is also quite small and indistinguishable. So how exactly do we measure the T1 Relaxation period and use it to generate contrast?

![](../.gitbook/assets/image%20%2836%29.png)

The longitudinal magnetization is the magnetization in the direction of the original $$\vec B$$field. The transverse magnetization is the magnetization in the direction orthogonal to the RF Coils \(orthogonal to the longitudinal magnetization\). Therefore, the only detectable signal we can obtain is from the transverse magnetization, since that is what produces the magnetic flux _through_ the RF coil.

### How do we excite \(flip\) spins?

We send in an RF pulse, denoted $$\vec B_1$$, perpendicular to $$\vec B_0$$of the same Larmor frequency $$\omega $$as our precessing spin.

A 90 degree flip would convert all of our longitudinal magnetization and convert it into transverse magnetization. 

#### The math

Since a flip essentially converts our longitudinal magnetization into transverse magnetization, the math involved in computing the signal detected by the RF coil _after the flip_ is derived by substituting the longitudinal equation into the transverse one as the starting magnetization \(instead of the Boltzmann magnetization since we might not always be fully "charged back up"\).

$$
M(t) = M_0(1 - e^{-TR/T_1})
\rightarrow S(t) = M_0(1-e^{-TR/T_1}) e^{-t/T_2}
$$

Therefore, we can draw the conclusion that the longer we set our relaxation time to be, the more longitudinal magnetization we accumulate, resulting in a higher transverse magnetization initial value. This means that the longer our relaxation time is, the stronger \(better fidelity & higher amplitude\) of a signal we observe post-flip from the RF coils.

### The Full Tissue Signal

$$
S(TR, TE) = M_0(1-e^{-TR/T_1}) e^{-TE/T_2}
$$

1. Given all of our samples' given $$T_1$$, we pick a $$TR$$
   * This dictates how much longitudinal magnetization we accumulate which then gets converted into transverse magnetization after a 90 degree spin flip \(pulse from RF coil\).
   * The choice of$$TR$$dictates how much signal each tissue begins its $$T_2$$decay with.
2. We send a pulse from the RF coil into the tissue, which converts the longitudinal magnetization into transverse magnetization.
   * Each tissue's signal reading decays per the tissue's respective $$T_2$$rate.

### Picking TR & TE

![](../.gitbook/assets/image%20%2824%29.png)

1. If we choose our $$TR $$to be much longer than $$T_1$$ and a $$TE$$ very close to our $$T_2$$, then our signal equation is $$T_2$$weighted.
2. If we choose our $$TR $$to be very close to our $$T_1$$ and a $$TE$$ much smaller than $$T_2$$, then our signal equation is $$T_1$$weighted.
3. If we choose our $$TR $$to be much longer than $$T_1$$ and a $$TE$$ much smaller than $$T_2$$, then our signal is a $$\text{Spin Density Image}$$since the only distinguishing factor between the tissues is the $$\text{Boltzmann Magnetization}$$.

### Boltzmann Factor

The Boltzmann factor determines what our sample's polarization is in a strong magnetic field \(such as in an MRI\).

The polarization of our sample in a strong magnetic field in Boltzmann equilibrium is:

$$
\frac{\gamma \hbar B_0}{2 k T}
\newline \space \newline\text{where}
\newline k: \text{Boltzmann's Constant} \newline
T: \text{Sample's temperature in Kelvin}
$$

### Spin Echo EUREKA!

Ok the spin echo explanation in the second video \(listen in [Sources](magnetic-resonance-imaging.md#sources)\) genuinely blew my mind. Here is me explaining it to myself once it finally clicked:

{% file src="../.gitbook/assets/spin-echo-eureka.m4a" caption="EUREKA MOMENT!" %}

I won't bother with explaining it here -- the video does a much better job than I ever could. But here is a mild overview:

![Spin Echo Diagram](../.gitbook/assets/image%20%2818%29.png)

Due to external field inhomogeneity, the actual signal decays much faster than we expect from T2 Relaxation. The signal actually decays so much faster that it makes the T2 Relaxation decay difference between tissues almost indistinguishable. As a result, we get another sample from the t2 decay.

### 



### Sources

{% embed url="https://www.youtube.com/watch?v=TQegSF4ZiIQ&ab\_channel=thePIRL" %}

{% embed url="https://www.youtube.com/watch?v=M7yh0To6Wbs&ab\_channel=thePIRL" %}



