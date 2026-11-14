# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...647A.173K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. 39581corr ©ESO 2021
February 4, 2021

## ALMA/ NICER observations of GRS 1915 + 105 indicate a return to a

### **hard state**


K. I. I. Koljonen [⋆] and T. Hovatta


The Finnish Centre for Astronomy with ESO, University of Turku
Aalto University Metsähovi Radio Observatory, Metsähovintie 114, FI-02540 Kylmälä, Finland


Received ; accepted


**ABSTRACT**


_Context._ GRS 1915+105 is a transient black hole X-ray binary consistently emitting 10–100% of the Eddington luminosity in the
X-ray band over the last three decades until mid-2018 when the source luminosity suddenly decreased by an order of magnitude. This
phase was followed by a change to a state with even lower average X-ray fluxes never seen before during the outburst but presenting
renewed flaring activity at different wavelengths, albeit with mean fluxes still in decline.
_Aims._ GRS 1915+105 has the longest orbital period known among low-mass X-ray binaries, the largest accretion disk size, and
therefore the largest mass supply for accretion. The high inclination of the disk allows the study of geometrical effects of the accretion
flow such as changes in the height-to-radius ratio or the effect of accretion disk winds on the intrinsic emission that is expected during
the outburst decay. In addition, the transient jet is expected to change to a compact, self-absorbed, steady jet.
_Methods._ We conducted two full polarization _Atacama_ _Large_ _Millimeter_ _Array_ observations to study the jet properties during the
outburst decay by analyzing the spectral, polarization, and intra-epoch variability for both observation epochs. In addition, we analyzed
almost daily _Neutron_ _Star_ _Interior_ _Composition_ _Explorer_ pointing observations, modeling X-ray power spectral densities, spectral
energy distributions, and light curves with a physically motivated model to follow the changing accretion disk properties throughout
the outburst decay and relating them to the jet emission.
_Results._ We show that the X-ray and millimeter (mm) spectral, timing, and polarization properties are consistent with those of a
typical decaying X-ray binary outburst and that GRS 1915+105 has descended into the low-luminosity hard X-ray state. The jet
emission in the mm is consistent with a compact, steady jet with ∼1% linear polarization, and the magnetic field is likely aligned with
the jet position angle. Relating the mm emission to the X-ray emission reveals that the source has changed from a higher radio/X-ray
correlation index to a lower one; _L_ radio ∝ _L_ [0] _X_ [.][6] [.]


**Key words.** Accretion, accretion disks – binaries: close – stars: black holes – stars: winds, outflows – X-rays : binaries



**1.** **Introduction**


GRS 1915+105 is a transient, black hole X-ray binary (XRB)
that started its decades-long outburst in 1992 (Castro-Tirado
et al. 1994). During the outburst, it was one of the brightest
XRBs, consistently emitting 10–100% of the Eddington luminosity in the X-ray band. However, in mid-2018, the source
luminosity decreased suddenly by an order of magnitude and
has diminished since. GRS 1915+105 hosts a K-type giant star
(Greiner et al. 2001) with a mass of ∼0.5 solar masses as a donor
(Steeghs et al. 2013), firmly establishing it as a low-mass XRB.
It has the longest orbital period known among low-mass XRBs
(33.9 days; Steeghs et al. 2013) and therefore the largest accretion disk size and mass supply for accretion.
GRS 1915+105 was the first Galactic source known to
exhibit apparent superluminal motion of the jet components
(Mirabel & Rodríguez 1994). The source presented both transient and steady jet phases during its outburst. The transient jet
phases occurred approximately once every year and consisted
of bright events at infrared and radio wavelengths (Pooley &
Fender 1997; Klein-Wolt et al. 2002). In between the transient
jet phases, the steady jet phases were periods of prolonged hard
X-ray emission (Foster et al. 1996; Dhawan et al. 2000; Fuchs


⋆ e-mail: `karri.koljonen@utu.fi`



et al. 2003) and a low radio flux density of ∼10 mJy (Ogley et al.
2000) indicating emission from a compact self-absorbed jet. The
transient jet phase in XRBs often coincides with a time when the
X-ray spectrum changes rapidly. This spectral evolution is taken
to arise from a physical change in the accretion disk structure
where the optically thin and geometrically thick disk is replaced
by an optically thick and geometrically thin disk due to increased
mass accretion rate (Gallo et al. 2003). During this time, strong
radio flares are observed, and bright, optically thin synchrotron
“blobs” or internal shocks can be seen emanating from the central source in radio interferometric images (Fender et al. 1999).


Due to the strong radio emission and trackable jet components, the jet and system parameters of GRS 1915+105 are
known relatively well. The jet component velocities range between 0.65 _c_ and 0.98 _c_, jet inclination is 60-70 deg to the line of
sight, the mass of the black hole is 10-14 solar masses, and the
distance is 7-10 kpc (Fender et al. 1999; Reid et al. 2014). Due
to the high inclination, we are looking at the accretion disk relatively edge-on. This allows us to potentially study the evolution
of the accretion flow geometry, such as changes in the height-toradius ratio of the accretion flow or the effect of accretion disk
winds on the intrinsic emission (e.g. Lee et al. 2002; Miller et al.
2016; Neilsen et al. 2018).


Article number, page 1 of 18

_A&A proofs:_ manuscript no. 39581corr



In July 2018, GRS 1915+105 entered an unusually extended
low-flux X-ray phase followed by a change to a state with even
lower average X-ray fluxes never seen before during the outburst
but presenting renewed flaring activity at different wavelengths,
most notably in the radio (Koljonen et al. 2019; Trushkin et al.
2019; Motta et al. 2019, 2021). Detailed X-ray observations suggest that diminished and obscured accretion might be feeding
the variable jets (Koljonen & Tomsick 2020; Miller et al. 2020;
Neilsen et al. 2020; Motta et al. 2021; Balakrishnan et al. 2020).
The obscuring matter is likely located close to the X-ray source
either ejected from the accretion disk by a disk wind or originating from a puffed-up or warped accretion flow.
In this paper, we present two full polarization _Atacama Large_
_Millimeter_ _Array_ (ALMA) and nearly daily _Neutron_ _Star_ _Inte-_
_rior Composition Explorer_ ( _NICER_ ) monitoring observations of
GRS 1915+105 that were taken during the outburst decay before
the source entered to the obscured state. The observations and
data reduction processes are described in Section 2. In Section 3,
we go through the detailed timing and spectral analyses of both
_NICER_ and ALMA data sets. We show that the X-ray and millimeter (mm) spectral and timing properties of GRS 1915+105
show consistent behavior of a decaying XRB outburst indicating that GRS 1915+105 has descended to a low-luminosity hard
state. The outburst decay of GRS 1915+105 offers us a detailed
view of the physical processes in the accretion flow and the jet
leading from the outburst towards quiescence and to the anomalous obscured state. In Section 4, we discuss the accretion disk
and jet properties during the different phases of the outburst
decay, and speculate on accretion disk properties in a scenario
where the outburst has ended. Finally, we conclude in Section 5.


**2.** **Observations**


_2.1._ _ALMA_


We conducted two band 3 (90–105 GHz) full polarization
ALMA observations in Cycle 6 on November 1, 2018, and
March 21, 2019, during the outburst decay of GRS 1915+105.
Both epochs lasted approximately two hours, consisting of several alternating scans of the science source (∼ 10 min), polarization calibrator (∼2 min), and phase calibrator sources (∼0.5
min). The polarization calibrator source in both epochs was
J1924−2914, and the phase calibrator source was J1922+1530
in the first epoch and J1905+0952 in the second epoch.
We performed the data reduction with the _Common Astron-_
_omy Software Applications_ (CASA) package version 5.4.0-70 by
running the calibration script provided with the data. We flagged
the first ten channels in the second spectral window due to bad
D-terms for both epochs. In addition, antennas DA63 and DA41
for the first and second epochs, respectively, were flagged for all
spectral windows due to outlier values in gain amplitude. Also,
for the second epoch, we flagged antennas DA42 and DA48 for
the first spectral window due to outlier values in the X- and Ypolarized phase difference. The resulting images show that the
source is a point source within the beam (∼0.6 [′′] and ∼2.5 [′′] in
the first and second epochs, respectively) without any observed

structure.
Flux densities were compared with both imaging methods
and a delta function was fitted to the uv-plane using uvmultifit
3.0.0 (Martí-Vidal et al. 2014); we find that they agree with each
other. We estimated the Stokes Q and U polarized fluxes averaging over all spectral windows and all scans. To conduct spectral
and timing studies, we estimated Stokes I fluxes for each spectral
window individually averaging in time over the whole observa

Article number, page 2 of 18



tions, and for each scan length by averaging over all spectral
windows. We made the same analysis for the science, polarization, and phase calibrator sources.
To verify that the variability in the target on scan-length integrations is not due to instrumental effects, we did the following
tests. We examined the gain amplitudes from the phase calibration to verify that any changes in the amplitudes are not correlated with the flux density variations. We also examined the water vapor radiometer data of each antenna to detect any correlated
changes in atmospheric conditions and the target flux density, but
none were present. The mean precipitable water vapor content
during the first and second epochs was 1.3 mm and 0.9 mm, respectively. Combined with the more extended configuration during the first epoch, we expect a larger scatter in the flux density
due to changing atmospheric conditions during the first epoch.
This is indeed seen in our third check where we divided the array
into two individual sub-arrays (DV and DA antennas separately)
and repeated the flux density estimation. During the first epoch,
the flux density estimates from the sub-arrays vary up to 0.2 mJy,
and during the second epoch they vary by less than 0.1 mJy.


_2.2._ _NICER_


We downloaded all _NICER_ data from the High Energy Astrophysics Science Archive Research Center (HEASARC) using a
time range of MJD 58238–58634 (May 2018 – May 2019) beginning from the outburst decay phase and ending in the descent
to the obscured phase. We disregarded observations with exposure times of less than 500 seconds. This resulted in 87 pointings,
shown in Table A1.
We reduced the observations using nicerdas version 6a with
parameters nicercal_filtexpr="EVENT_FLAGS=bx1x000",
which removes all undershoot, overshoot, forced trigger, and
fast-only events, and cor_range="4-" to remove high particle
radiation intervals associated with the Earth’s auroral zones.
We selected PI energy channels between 30 and 1200 (0.3–12
keV). We extracted the X-ray spectra using xselect v2.4g. We
used the photon redistribution matrix (RMF) and the on-axis
average ancillary response file (ARF) for all 52 detectors
combined from HEASARC’s Calibration Database (CALDB).
For the background we use a public background file available in
HEASARC (nixtiback20190807.pi).
For the timing analysis, we calculated the power spectral
densities (PSDs) directly from the cleaned event files using a
binning of 2 [−][7] s (or 2 [−][4] s in case of the data in the obscured
phase), an energy band 1–10 keV, and a segment length of 16 s
(or 256 s in case of the data in the obscured phase). We normalize all the PSD to rms variability. All the segments were further
averaged over the whole pointing and binned geometrically by a
factor of 1.05 before importing them to the Interactive Spectral
Interpretation System (isis; Houck & Denicola 2000) for model
fitting.
For the spectral analysis, we binned the data adaptively in
the ranges 0.3-1.5 keV to S/N=5-10, 1.5-5.0 keV to S/N=20-70,
5.0-8.0 keV to S/N=15-50, and 8.0-12.0 keV to S/N=10-30 depending on the flux and exposure time of the pointing to ensure
similar statistics for each spectrum. We performed spectral fitting using isis. We estimated the errors on the parameter values
and fluxes through Monte Carlo analysis. For those spectra with
1-10 keV flux densities below 0.3×10 [−][8] erg s [−][1] cm [−][2], an additional unabsorbed power-law component was needed to nicely
fit the low-energy data below 1 keV that could arise from imperfect background subtraction. However, the normalization of this
component is very small, containing only 0.003-0.006% of the

K. I. I. Koljonen and T. Hovatta: ALMA/ _NICER_ observations of GRS 1915+105





10.00


1.00


0.10































|1Feb18 12May18 20Aug18 28Nov18 8Mar19 16Jun19<br>4<br>s−1] 1 2<br>Ep. Ep.<br>3 cm−2 ALMA ALMA<br>sV<br>nke<br>2 h2 o- t2 o0<br>[MAXIpF<br>1<br>0<br>500<br>.<br>200<br>. keV<br>100<br>. keV/F2-10<br>050<br>.<br>020<br>.<br>010<br>. F10-20<br>005<br>.<br>002<br>.<br>001<br>.07<br>.. Ex dp eo cn ae yntial Linear decay brighR te e- Obscure<br>0 6 ning<br>cm−2]<br>05<br>.<br>04 . sk −e 1V<br>g10<br>03 . [10−8F e1 r-<br>02<br>.<br>01<br>.<br>00<br>.<br>a<br>4<br>[Hz]<br>ef<br>3 frequency<br>d<br>b<br>2<br>c<br>QPO<br>1<br>0 g<br>58150 58250 58350 58450 58550 58650<br>MJD|Col2|12May18 20Aug18 28Nov18 8Mar19 16Jun19|Col4|Col5|
|---|---|---|---|---|
|0<br>1<br>2<br>3<br>4<br>1 Feb 18<br>12 May 18<br>20 Aug 18<br>28 Nov 18<br>8 Mar 19<br>16 Jun 19<br>F2-20 keV<br> [MAXI photons cm−2 s−1]<br>ALMA Ep. 1<br>ALMA Ep. 2<br>0.01<br>0.02<br>0.05<br>0.10<br>0.20<br>0.50<br>1.00<br>2.00<br>5.00<br>F10-20 keV/F2-10 keV<br>0.0<br>0.1<br>0.2<br>0.3<br>0.4<br>0.5<br>0.6<br>0.7<br>Exponential<br>decay<br>Linear decay<br>Re-<br>brightening Obscure<br>F1-10 keV<br>[10−8 erg s−1cm−2]<br>58150<br>58250<br>58350<br>58450<br>58550<br>58650<br>0<br>1<br>2<br>3<br>4<br>QPO frequency [Hz]<br>MJD<br>a<br>b<br>c<br>d<br>ef<br>g|||ALMA Ep. 1<br>ALMA Ep. 2||
|0<br>1<br>2<br>3<br>4<br>1 Feb 18<br>12 May 18<br>20 Aug 18<br>28 Nov 18<br>8 Mar 19<br>16 Jun 19<br>F2-20 keV<br> [MAXI photons cm−2 s−1]<br>ALMA Ep. 1<br>ALMA Ep. 2<br>0.01<br>0.02<br>0.05<br>0.10<br>0.20<br>0.50<br>1.00<br>2.00<br>5.00<br>F10-20 keV/F2-10 keV<br>0.0<br>0.1<br>0.2<br>0.3<br>0.4<br>0.5<br>0.6<br>0.7<br>Exponential<br>decay<br>Linear decay<br>Re-<br>brightening Obscure<br>F1-10 keV<br>[10−8 erg s−1cm−2]<br>58150<br>58250<br>58350<br>58450<br>58550<br>58650<br>0<br>1<br>2<br>3<br>4<br>QPO frequency [Hz]<br>MJD<br>a<br>b<br>c<br>d<br>ef<br>g|||||
|0<br>1<br>2<br>3<br>4<br>1 Feb 18<br>12 May 18<br>20 Aug 18<br>28 Nov 18<br>8 Mar 19<br>16 Jun 19<br>F2-20 keV<br> [MAXI photons cm−2 s−1]<br>ALMA Ep. 1<br>ALMA Ep. 2<br>0.01<br>0.02<br>0.05<br>0.10<br>0.20<br>0.50<br>1.00<br>2.00<br>5.00<br>F10-20 keV/F2-10 keV<br>0.0<br>0.1<br>0.2<br>0.3<br>0.4<br>0.5<br>0.6<br>0.7<br>Exponential<br>decay<br>Linear decay<br>Re-<br>brightening Obscure<br>F1-10 keV<br>[10−8 erg s−1cm−2]<br>58150<br>58250<br>58350<br>58450<br>58550<br>58650<br>0<br>1<br>2<br>3<br>4<br>QPO frequency [Hz]<br>MJD<br>a<br>b<br>c<br>d<br>ef<br>g|Exponential<br>decay<br>|Exponential<br>decay<br>|Linear decay<br>Re<br>brighte|-<br>ning Obscure|
|0<br>1<br>2<br>3<br>4<br>1 Feb 18<br>12 May 18<br>20 Aug 18<br>28 Nov 18<br>8 Mar 19<br>16 Jun 19<br>F2-20 keV<br> [MAXI photons cm−2 s−1]<br>ALMA Ep. 1<br>ALMA Ep. 2<br>0.01<br>0.02<br>0.05<br>0.10<br>0.20<br>0.50<br>1.00<br>2.00<br>5.00<br>F10-20 keV/F2-10 keV<br>0.0<br>0.1<br>0.2<br>0.3<br>0.4<br>0.5<br>0.6<br>0.7<br>Exponential<br>decay<br>Linear decay<br>Re-<br>brightening Obscure<br>F1-10 keV<br>[10−8 erg s−1cm−2]<br>58150<br>58250<br>58350<br>58450<br>58550<br>58650<br>0<br>1<br>2<br>3<br>4<br>QPO frequency [Hz]<br>MJD<br>a<br>b<br>c<br>d<br>ef<br>g|a<br>b|a<br>b|c<br>d|ef<br>g|


**Fig. 1.** _Top_ : _MAXI_ /GSC 2–20 keV daily light curve of GRS 1915+105
since February 2018 with ALMA observations marked as dashed vertical lines. The data points are colored and marked according to the
hardness-intensity diagram shown in Fig. 2. _Middle_ / _top_ : _MAXI_ /GSC
10–20 keV / 2-10 keV daily hardness ratio. _Middle_ / _bottom_ : _NICER_ 1–
10 keV light curve with flux densities estimated from spectral fitting
and the light curve decay fitted with an exponential and a linear decay models (solid line). The different decay phases are indicated and
shown as an alternating shading scheme. _Bottom_ : QPO frequencies as
determined from modeling the _NICER_ PSD. The exponential and linear decay phases show different rates of decay for the QPO frequency
(shown as dotted lines). The seven lettered observations correspond to
example PSD and spectra shown in Figs. 3, 7, and 6.


total flux and affecting only the soft X-rays below 1 keV with a
fairly steep spectral slope of Γ ∼2.5.


**3.** **Results**


_3.1._ _X-ray monitoring_


The ALMA observations coincided with a stable low-luminosity
X-ray state where the observed luminosity is much lower and
X-ray hardness higher than the usual outburst values. This state
was superseded by an even lower luminosity state with a higher



0.01

0.01 0.10 1.00

F 10-20 keV /F 2-10 keV


**Fig. 2.** _MAXI_ /GSC hardness-intensity diagram of GRS 1915+105 from
daily monitoring observations since August 2009. The blue data points
(both dark triangles and light blue squares) indicate the low-luminosity
state since August 2018 with increased spectral hardness. The light blue
squares correspond to the obscured decay phase with even lower flux
densities and harder spectra with occasional, strong X-ray flares (red
diamonds) and highly variable radio emission, in addition to a softer
state in August-September 2020 with the flux densities back to the level
of the low-luminosity state (yellow dots). The numbered green boxes
correspond to the ALMA epochs that took place during the linear and
rebrightening decay phases of the outburst decay.


X-ray hardness ratio that is most likely an effect of obscuration (Koljonen & Tomsick 2020; Miller et al. 2020; Neilsen
et al. 2020; Motta et al. 2021; Balakrishnan et al. 2020). Figure 1 shows the _Monitor_ _of_ _All-sky_ _X-ray_ _Image_ /Gas Slit Camera ( _MAXI_ /GSC) 2–20 keV count rate, _MAXI_ /GSC hardness ratio, _NICER_ 1–10 keV flux density, and quasi-periodic oscillation
(QPO) frequencies as measured from the PSD during the decay states: black circles denoting the exponentially decaying outburst, blue triangles denoting a linearly decaying phase, and light
blue squares denoting the obscured state (with sporadic flares
denoted as red diamonds). In between the linear decay phase
and the obscured phase, GRS 1915+105 exhibited an increase in
flux density and QPO frequency departing from the linear decay
trend, which we denote as a rebrightening phase.
Figure 2 shows the hardness-intensity diagram from the
_MAXI_ /GSC daily observations of GRS 1915+105 since Aug
2009. The three decay states separate easily from each other with
a change in the countrate and the X-ray hardness. Assuming that
GRS 1915+105 is accreting at the Eddington limit for the highest count rates (∼7 photons cm [−][2] s [−][1] ) —a reasonable argument
based on both observations (e.g., Done et al. 2004; but taking
into account the effect of the smaller distance estimate in Reid
et al. 2014) and simulations (e.g., Truss & Wynn 2004)— the
outburst phase corresponds to luminosities 0.1 < _L_ / _L_ Edd < 1.0,
the linear decay phase to ∼0.04 L Edd, and the obscured phase
to ∼0.01 L Edd (which agrees with values obtained by Koljonen & Tomsick 2020 and Miller et al. 2020). During the obscured phase, there were prominent flares with X-ray luminosi

Article number, page 3 of 18

_A&A proofs:_ manuscript no. 39581corr



ties reaching ∼0.04–0.18 L Edd, and more recently, in AugustSeptember 2020, a softer state with X-ray luminosities around
∼0.04 L Edd . Assuming a black hole mass of 12 M ⊙ (Reid et al.
2014) the Eddington luminosity is L Edd = 1.5 × 10 [39] erg s [−][1] .


_3.2._ _X-ray spectral and timing properties during the outburst_
_decay phases_


In this section, we describe the X-ray spectral and timing properties during the outburst decay in detail. As described above,
we divide the data in four separate phases with distinct behavior
in the X-ray light curve as well as in X-ray spectral and timing
properties.


3.2.1. Description of the spectral model


We fit the individual pointing spectra from the _NICER_ dataset
with a model consisting of an absorbed power law and reflection model components (relxill; García et al. 2014; Dauser
et al. 2014) modified by Gaussian emission and/or absorption
line components when necessary. In addition, for spectra with
1-10 keV fluxes below 0.3×10 [−][8] erg s [−][1] cm [−][2] we added an unabsorbed power-law model component to take into account the
effect of imperfect background subtraction as mentioned in Section 2.2.

For the photoelectric absorption component, we chose
vphabs, which allow the abundances of the elements of the neutral absorber to be changed. GRS 1915+105 is known to be
surrounded by local, cold material likely in the form of an accretion disk wind that absorbs the X-ray emission in addition
to the interstellar absorption (Lee et al. 2002; Martocchia et al.
2006). Following Martocchia et al. (2006), we grouped elements
that have either a small effect in the energy range in question or
whose origin is likely to be the same into the following groups:
(1) H, He, C, N, O, Ne, Na, (2) Mg, (3) Al, (4) Si, (5) S, (6)
Cl, Ar, Ca, and (7) Cr, Co, Ni, and Fe. Depending on the quality
of the spectrum, we grouped the abundances to an even smaller
number of groups (the smallest division consisting of two groups
with one for lighter elements than aluminum and one for heavier
elements). In the fitting process, we found that the iron abundance tended towards unphysically low values, and therefore we
decided to fix it to the solar value. In addition, we added emission and/or absorption lines of neutral and ionized iron (Fe I Kα
at 6.40 keV, Fe XXV Kα complex at 6.7 keV, Fe XXV Kβ at
7.80 keV, Fe XXVI Lyα at 6.97 keV, and Fe XXVI Lyβ at 8.27
keV), sulfur (2.3 keV), argon (3.0 keV), and calcium (3.7 keV)
when necessary, mainly for the better quality spectra. Thus, the
total model can be described as: vphabs × (relxill + lines) +

powerlaw.

In the fitting procedure, we first fitted the spectra with the
largest exposure times to pinpoint the values of some of the
relxill parameters that were then kept fixed when modeling the
lower quality spectra. These included the inner radius of the accretion disk R in, spin of the black hole _a_, and the reflection factor
R f of relxill. However, we found that the spin is not constrained,
and the inner radius presents large values indicating that the Xray spectra are not sensitive to relativistic effects. Therefore, we
decided to fix the spin to zero. We further fixed the inclination to
70 degrees (Reid et al. 2014; Mirabel & Rodríguez 1994), and
iron abundance to the solar value. Other parameters were left as
default values and fixed, except the power-law photon index (Γ),
ionization parameter (log ξ), and model normalization, which
were allowed to vary for all spectral fits.


Article number, page 4 of 18



3.2.2. Description of the PSD model


We fit all the PSDs with up to three Lorentzians: a Lorentzian
centered at zero frequency for the band-limited noise and two
Lorentzians for the QPO and its upper harmonic. In addition to
the Lorentzian components, a power-law component is needed
to model the higher luminosity PSD during the high-luminosity
part of the exponential decay. We also model the Poisson noise
present in the PSD as a constant power component.


3.2.3. The exponential and linear decay phases


In Fig. 1, both the _NICER_ 1-10 keV flux density and the QPO frequencies show similar evolution with a transition from a steeper
(exponential) decay to a more shallow (linear) decay at ∼ MJD
58330. We take this change as the approximate transition time of
the two decay phases. The _NICER_ PSDs during the exponential
and linear decay phases suggest a typical hard state PSD similar to what is observed in plateau and radio-quiet states with a
band-limited noise component and a type-C QPO. The QPO frequency is tightly correlated with the X-ray luminosity decreasing
approximately linearly from 4 Hz to 2 Hz during the exponential
decay phase and further to ∼1.5 Hz during the linear decay phase
and inversely correlated with the X-ray hardness ratio, both of
which are typical for type-C QPOs (Casella et al. 2005).
We fit all the PSDs with the model described in Section 3.2.2
(examples are given in Fig. 3, _panels_ _b–c_ ). The total rms of
the Lorentzians correlates with the X-ray hardness ratio starting at ∼20% at the beginning of the exponential decay phase
and reaching ∼35% in the linear decay phase. The rms evolution
is mainly due to increasing rms of the zero-centered Lorentzian
while the rms of the QPO and harmonic are on average 7±1%
and 6±1%, respectively. The coherence parameter of the QPO
component is always Q>5 indicating peaked noise. In addition
to the Lorentzian components, a power-law component is needed
to model the higher luminosity PSD during the high-luminosity
part of the exponential decay ( _panel_ _a_ in Fig. 3). It shows decreasing rms variability during the decay and presents a powerlaw index of Γ ∼ 1.0. All model parameters for each PSD are
tabulated in Table A1.

We also checked whether the QPO frequencies presented any
time lags between a soft (2–4 keV) and a hard X-ray (5–10 keV)
band (see Fig. 4). On average, the main QPO frequency shows
soft lags (soft photons lagging hard photons) and the upper harmonic hard lags (hard photons lagging soft photons) of about 10
msec when the QPO frequency is above 2 Hz. When the QPO
frequency descends below 2 Hz; that is, during the linear decay
phase, the lag at the QPO frequency averages to zero lag, but
the upper harmonic frequency shows hard lags. This behavior is
consistent with earlier studies during the outburst phase (Reig
et al. 2000; Qu et al. 2010; Pahari et al. 2013; Zhang et al. 2020),
where the phase lag has a log-linear relationship with the QPO
frequency and changes sign approximately at 2 Hz.
During the exponential decay phase, the X-ray spectra show
a slowly hardening and diminishing Comptonization component.
The power-law photon index of the relxill component decreases
from Γ = 2.5 to Γ = 2.0, ionization parameter from log ξ = 4.5 to
log ξ = 3.5, and abundances of the absorber likely linked to the
diminishing ionizing flux. The most prominent line features in
the spectra are Fe I Kα and S Kα. In the linear decay phase,
the continuum model parameters settle to a more stable state
with Γ=1.93±0.06 and log ξ = 3.52±0.07. Typical values for the
power-law index in an XRB hard state are Γ=1.5-2.0, while intermediate and soft states have Γ - 2 (Remillard & McClintock

K. I. I. Koljonen and T. Hovatta: ALMA/ _NICER_ observations of GRS 1915+105



10 [−][2]


10 [−][3]


10 [−][2]


10 [−][3]









|2<br>3|a)|Col3|b)|Col5|c)|Col7|
|---|---|---|---|---|---|---|
|3<br>2|a)||||||
|2|2|2|2|2|2|2|
|2|d)||e)||f)||
|2|d)|101<br>10−1<br>100<br>Frequency [|101<br>10−1<br>100<br>Frequency [|101<br>10−1<br>100<br>Hz]|101<br>10−1<br>100<br>Hz]|101|


**Fig. 3.** PSD from six different epochs labeled in Fig. 1 ( _bottom panel_ ). The PSDs are fitted with a model consisting of a zero-frequency Lorentzian
modeling the broadband noise, one or two narrow Lorentzians modeling the QPO (fundamental and first upper harmonic components), an additional power-law component needed for PSD in panels _a_, _d_, _e_, and _f_, and Poisson noise as a constant power component (removed from the PSDs
shown here).



2006). The model parameter evolution is shown in Fig. 5, and the
corresponding parameter values are provided in Table A2. In addition, Fig. 6 shows the spectra from the same _NICER_ pointings
as shown in Fig. 3.


3.2.4. The rebrightening phase


After a gap in the monitoring data of GRS 1915+105 (MJD
58460–58550, see Fig. 1), the flux density and QPO frequency
had departed from the decay profile as the source entered the
rebrightening phase. During this phase, the flux density and the
QPO frequency are not correlated although both present an increase of about a factor of two with the QPO frequency rising up
to 3 Hz but vanishing completely during the flux drop leading to
the obscured phase.
In the X-ray PSD, a broad-band low-frequency component
is visible in addition to a band-limited noise component and a
type-C QPO ( _panels d–f_ in Fig. 3). As above, we model the additional component with a power-law model. The rms variability
of the power-law component increases, and the power-law index
presents higher values up to Γ ∼ 1.5. On the contrary, the rms of
the zero-centered Lorentzian decreases slightly.
In the X-ray spectra, the power-law photon index and
the ionization parameter present elevated but steady values of
Γ=2.14±0.06 and log ξ = 3.73±0.05 as compared with the linear
decay phase. The abundances show an increasing trend, high


ionization absorption lines appear in the spectra, and the emission lines disappear (Fig. 5, and Table A2).


We further concentrated on the iron-line region towards the
end of the rebrightening phase and in the obscured phase. Figure
8 shows the evolution of the iron lines during the transition, and
the corresponding line model parameters are presented in Table
1. The rebrightening phase is dominated by the absorption lines
with Fe XXV Kα being the most dominant line with a resolved
FWHM of 160-180 eV (corresponding to a velocity of 70008000 km/s) and equivalent width of about 100 eV. The line center
is also gradually redshifted from 6.70 keV (corresponding to a
zero redshift) to 6.59 keV (corresponding to a redshift of ∼4900
km/s). In addition, Fe XXV Kβ and Fe XXVI Lyβ absorption
lines are also visible and possibly Ni Kα line in one pointing at
MJD 58608.5, although the energy of the line is off by 0.1 keV.


During the rebrightening phase, there is a clear evolution of
the ratio of Fe XXVI Lyβ and Fe XXV Kβ column densities
(estimated according to Lee et al. (2002); their Eq. 1) indicating
a decreasing ionization factor from log ξ ∼ 3 to log ξ ∼ 2.6
(Kallman & Bautista 2001). These values are lower than what is

∼
obtained with the continuum fitting where log ξ 3.7 throughout
the rebrightening phase.


Article number, page 5 of 18

_A&A proofs:_ manuscript no. 39581corr















**Fig. 4.** Lag distributions of the QPO frequencies between 2-4 keV and
5-10 keV bands. The main QPO frequency and the first upper harmonic
frequency display, on average, soft and hard lags, respectively, when the
main QPO frequency is above 2 Hz. When the QPO frequency is below
2 Hz, the average lag at the main QPO frequency vanishes, and the first
upper harmonic QPO frequency shows hard lags.


3.2.5. The obscured phase


The change to the obscured state occurs likely at MJD 58608 or
soon after. When the source transits to the obscured phase, there
is a rapid drop in Γ, log ξ, and flux, and a change from the highly
ionized iron absorption lines to emission lines. In the obscured
phase, the PSD is consistent with a pure power-law noise (Fig. 7)
indicating that all the intrinsic timing information is lost leaving
only the scattered component with Γ ∼ 2.0.
In the obscured phase, the spectral model used for fitting the
data of the previous _NICER_ pointings did not provide good fits.
Instead, we used the modeling results of Koljonen & Tomsick
(2020), and added a neutral lower ionization reflection component to the model (xillver) with all parameters tied to the relxill
component except normalization. Thus, the model can be now
described as: vphabs × (relxill + xillver + lines) + powerlaw.
We further set the ionization parameter to 1, fixed the reflection
factor to −2 corresponding to an obscured reflection scenario,
and allowed the inclination to vary freely ( likely corresponding to some mean scattering angle of the obscuring cloud). The
model parameter evolution is shown in Fig. 5, and the corresponding parameter values are shown in Table A2.
In the obscured phase, the absorption lines turn to emission
together with a strong neutral iron emission line (modeled with
xillver, but also fitted separately with a gaussian line to be able
to compare values to other lines shown in Table 1). The equivalent widths of the emission lines vary from ∼50 eV to ∼150
eV, most likely indicating changes in the obscuring matter. Exceptionally, in one pointing at MJD 58623, the Fe XXV Kα line
seems to be in both absorption and emission (see Fig. 8). In the
previous observation, taken half a day earlier, the absorption is
not visible. While the absorption of the Fe XXV Kα line occurs
preferably in the resonant line (6.70 keV), the emission is char

Article number, page 6 of 18











|24<br>.<br>23 cm−2)<br>.<br>22<br>.<br>21 (1022<br>.<br>20<br>. NH<br>19<br>.<br>18<br>.<br>20 cm−2)<br>10<br>(1022<br>5<br>NX<br>2|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|1.8<br>1.9<br>2.0<br>2.1<br>2.2<br>2.3<br>2.4<br>NH (1022 cm−2)<br>2<br>5<br>10<br>20<br>NX (1022 cm−2)<br>|Mg<br>Al<br>Si<br>S<br>Cl/Ar/Ca|Mg<br>Al<br>Si<br>S<br>Cl/Ar/Ca|Mg<br>Al<br>Si<br>S<br>Cl/Ar/Ca|||
|1.8<br>1.9<br>2.0<br>2.1<br>2.2<br>2.3<br>2.4<br>NH (1022 cm−2)<br>2<br>5<br>10<br>20<br>NX (1022 cm−2)<br>||||||
|~~7~~<br>8<br>eV]|~~7~~<br>8<br>eV]|~~7~~<br>8<br>eV]|~~7~~<br>8<br>eV]|||
|4<br>5<br>6<br> energy [k|4<br>5<br>6<br> energy [k|4<br>5<br>6<br> energy [k|4<br>5<br>6<br> energy [k|4<br>5<br>6<br> energy [k||
|~~3~~<br><br>ine|~~3~~<br><br>ine|~~3~~<br><br>ine|~~3~~<br><br>ine|~~3~~<br><br>ine||
|2<br><br>L||||||
|1.5<br>2.0<br>2.5<br>Γ<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>ξ<br>1.0<br>1.2<br>1.4<br>1.6<br>χ2 d.o.f<br>00<br>0.1<br>0.2<br>0.3<br>0.4<br>0.5<br>0.6<br>0.7<br>-10 keV (10−8 erg s−1 cm−2)||||||
|1.5<br>2.0<br>2.5<br>Γ<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>ξ<br>1.0<br>1.2<br>1.4<br>1.6<br>χ2 d.o.f<br>00<br>0.1<br>0.2<br>0.3<br>0.4<br>0.5<br>0.6<br>0.7<br>-10 keV (10−8 erg s−1 cm−2)||||||
|1.5<br>2.0<br>2.5<br>Γ<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>ξ<br>1.0<br>1.2<br>1.4<br>1.6<br>χ2 d.o.f<br>00<br>0.1<br>0.2<br>0.3<br>0.4<br>0.5<br>0.6<br>0.7<br>-10 keV (10−8 erg s−1 cm−2)||||||
|1.5<br>2.0<br>2.5<br>Γ<br>2.5<br>3.0<br>3.5<br>4.0<br>4.5<br>ξ<br>1.0<br>1.2<br>1.4<br>1.6<br>χ2 d.o.f<br>00<br>0.1<br>0.2<br>0.3<br>0.4<br>0.5<br>0.6<br>0.7<br>-10 keV (10−8 erg s−1 cm−2)|Exponential decay<br>Linear decay<br>Re-<br>brightening<br>Obscured<br>a<br>b<br>c<br>d<br>e f<br>g|Exponential decay<br>Linear decay<br>Re-<br>brightening<br>Obscured<br>a<br>b<br>c<br>d<br>e f<br>g|Exponential decay<br>Linear decay<br>Re-<br>brightening<br>Obscured<br>a<br>b<br>c<br>d<br>e f<br>g|Exponential decay<br>Linear decay<br>Re-<br>brightening<br>Obscured<br>a<br>b<br>c<br>d<br>e f<br>g|Exponential decay<br>Linear decay<br>Re-<br>brightening<br>Obscured<br>a<br>b<br>c<br>d<br>e f<br>g|


58250 58300 58350 58400 58450 58500 58550 58600 58650



MJD


**Fig.** **5.** Spectral fit results of the _NICER_ data. From top to bottom, the
model parameter evolution is shown for the abundance of lighter elements (lighter than magnesium all fixed to the same value), heavier
elements (Mg, Al, Si, S, and Cl/Ar/Ca displayed with different colors),
line energies for the emission/absorption lines (displayed with different
colors), the photon power law index (Γ), ionization parameter (log ξ),
the corresponding fit quality (χ [2] /d.o.f), and the absorbed 1-10 keV flux
density with the colored letters corresponding to spectra shown in Fig.
6. The alternate shading shows the times of the different decay phases.


acterized by the forbidden line (6.64 keV), especially for high
column densities (Bianchi et al. 2005). Therefore, the observation of the absorption and emission line indicates at least two
scattering components during this time. Extrapolating the linear
decay to the obscured state (see Fig. 5, bottom panel) shows that
the observed flux density during the obscured state is a factor
of 1.2-8.8 lower than the linear decay profile. The observations

K. I. I. Koljonen and T. Hovatta: ALMA/ _NICER_ observations of GRS 1915+105


MJD 58555.7


MJD 585 ~~69~~ .4


MJD 58583 ~~.0~~


MJD 58589.2


MJD 58596.6



10 [0]


10 [−][1]



a)
b)
c)
d)
e)
f)
g)



10 [−][2]


10 [−][3]


10 [−][4]


1.4
1.2
1.0
0.8
0.6

1 10


Energy [keV]


**Fig.** **6.** _NICER_ spectra and best-fit models from the seven different
epochs labeled in Fig. 1 ( _bottom panel_ ) and Fig. 5 ( _bottom panel_ ). The
coloring scheme is according to the colored letters shown in Fig. 5 ( _bot-_
_tom panel_ ).

#### g)


10 [−][2]


10 [−][3]


10 [−][2] 10 [−][1] 10 [0] 10 [1]


Frequency [Hz]


**Fig. 7.** Pure power-law PSD from the obscured epoch labeled in Fig. 1
( _bottom panel_ ). The Poisson noise is subtracted.


presenting the lowest fluxes during the obscured phase show a
similar trend with the linear decay, but with 0.045×10 [−][8] erg s [−][1]
cm [−][2] of flux removed, meaning that at most approximately 80%
of the intrinsic flux density is absorbed and/or scattered in the
1–10 keV band.


_3.3._ _ALMA results_


The two ALMA epochs coincided with the linear decay phase
and the rebrightening phase (Fig. 1). The corresponding mean
Stokes I flux densities of these epochs were 2.5 mJy and 2.9
mJy. A typical radio-quiet level for GRS 1915+105 is <20 mJy
(Muno et al. 2001; Klein-Wolt et al. 2002). The flux density rise
in the rebrightening phase is consistent with the rise in the Xray flux indicating a connection between the two. As the spectral
windows in the ALMA band 3 are separated into two sidebands
with a 10 GHz break in between, 90–93 GHz and 102–105 GHz,
we were able to estimate the in-band source spectra for the two
epochs shown in Fig. 9. In both cases the spectra is flat with



MJD 58604.4


MJD 58608.5


MJD 58622.5


MJD 58623.0


MJD 58631.1


5.5 6.0 6.5 7.0 7.5 8.0 8.5 9.0


Energy [keV]


**Fig.** **8.** Evolution of the iron lines from absorption to emission when
GRS 1915+105 changed from the rebrightening phase (top seven spectra) to the obscured phase (bottom three spectra). Two spectra from the
obscured phase (MJD 58622 and MJD 58623) are overlaid to highlight
the possible absorption feature of Fe XXV Kα line. The best-fit models
are shown as solid lines.


spectral indices α 1 = −0.09 ± 0.05 and α 2 = 0.11 ± 0.05 ( _S_ ν ∝
ν [α] ), which are typical values for a self-absorbed synchrotron jet.


The source was weakly polarized during both epochs with
polarization fractions of 1.3-1.6 %. We could only detect significant Stokes U polarization indicating linear polarization with a
position angle close to −45 degrees. The values for the Stokes
fluxes from uv-plane fitting and imaging analysis are presented
in Table 2. We note that ∼1% linear polarization is a typical
value for self-absorbed synchrotron jet polarization in hard-state
XRBs. The optically thick, steady jets in XRBs show low levels
of linear polarization, from undetectable to a few percent (e.g.,
Corbel et al. 2000; Russell et al. 2015). This also agrees with earlier results from the steady jet phase with the polarization factor
of the stationary core of 1-2% (Fender et al. 2002).


The jet position angle in GRS 1915+105 was previously determined by tracking the jet components: -36.7 [◦] ±3.4 [◦] (northwest
direction) and 146.5 [◦] ±2.8 [◦] (southeast direction; Miller-Jones
et al. 2007), 130 [◦] ±1 [◦] (Reid et al. 2014), 133 [◦] –157 [◦] (Dhawan
et al. 2000), 142 [◦] ±2 [◦] (Fender et al. 1999), and 151 [◦] ±3 [◦] (Rodríguez & Mirabel 1999). As the position angle is degenerate
with ±180 [◦], our values also correspond to 136 [◦] –147 [◦], which
agrees well with the values of the jet position angle at similar
angular scales. Thus, the polarization position angles of ALMA
observations are consistent with being parallel to the jet. Due
to absorption effects, the intrinsic electric vector position angle
of the steady jet is expected to align parallel to the magnetic
field, which is expected to be parallel to the jet axis. If this is the
case, this would mean that the effect of Faraday rotation would
be quite small. All the above results point to the fact that GRS
1915+105 exhibits a canonical compact steady optically thick
XRB jet during both ALMA epochs.


Article number, page 7 of 18

_A&A proofs:_ manuscript no. 39581corr


**Table 1.** Neutral and ionized absorption and emission iron line modeling results of the _NICER_ data during the descent to the obscured state. The
corresponding X-ray spectra and models are plotted in Fig. 8. The line widths of all lines except in a few cases for Fe XXV Kα line are below

∼
detector resolution ( 0.01 keV).


MJD: 58555.7 58569.4 58583.0 58589.2 58596.6 58604.4 58608.5 58622.5 58623.0 58631.1

**Fe I K** α
Energy (keV) – – – 6.31 − [+] 0 [0] . [.] 04 [03] – – – 6.400±0.005 6.38±0.01 6.411±0.007
EW (eV) – – – 14 [+] − [5] 6 – – – 138±8 48±6 90±7
**Fe XXV K** α
Energy (keV) 6.70±0.03 6.66±0.01 6.65±0.20 6.63±0.01 6.63±0.01 6.619±0.008 6.59±0.01 6.65±0.01 6.64/6.70 6.67±0.01
EW (eV) −23±8 −37±6 −33±6 −50 [+] − [5] 6 −87 [+] − [9] 14 −133 [+] − [10] 9 −87 [+] − [11] 20 46±7 25±15/−29±14 154±9
σ (keV) 0.01 0.01 0.01 0.01 0.07 [+] − [0] 0 [.] . [01] 02 0.10±0.01 0.06 [+] − [0] 0 [.] . [02] 01 0.01 0.01/0.01 0.01
N (10 [17] cm [−][2] ) 2.6 4.3 3.8 5.8 10 16 – – – –
**Fe XXVI Ly** α
Energy (keV) 6.97±0.04 6.97±0.02 6.95±0.02 6.93±0.02 6.97±0.02 6.98±0.02 – 7.00 − [+] 0 [0] . [.] 01 [02] 6.98 − [+] 0 [0] . [.] 04 [05] 6.98±0.01
EW (eV) −17±8 −26±6 −27±6 −36±6 −32±6 −33±6 – 119 [+] − [12] 14 57±16 150±12
N (10 [17] cm [−][2] ) 3.7 5.7 5.9 8.0 6.9 7.3 – – – –
**Fe XXV K** β
Energy (keV) – – – 7.84±0.03 7.84±0.02 7.83±0.02 7.81±0.02 – – 7.82 [+] − [0] 0 [.] . [02] 04
EW (eV) – – – −37±9 −43±8 −54±11 −55±11 – – 33±12
**Fe XXVI Ly** β
Energy (keV) – – – 8.14±0.04 8.23±0.03 8.21±0.02 8.21±0.04 – – 8.27 [+] − [0] 0 [.] . [03] 06
EW (eV) – – – −28±10 −43±9 −52 [+] − [10] 11 −31±14 – – 31±14


**Table 2.** Polarized flux densities of ALMA observations. All Stokes fluxes are shown for both epochs and spectral windows from uv-plane fitting,
but the position angle and polarization fraction are only calculated for the full band. We also show the Stokes I and U from full band imaging
analysis for comparison.

|UVMultiFit|Imaging|
|---|---|
|Epoch<br>Spw<br>I<br>Q<br>U<br>PA<br>p<br>(mJy)<br>(mJy)<br>(mJy)<br>(deg)<br>(%)|I<br>U<br>(mJy)<br>(mJy)|
|Ep. 1<br>All<br>2.499±0.007<br>0.001±0.007<br>-0.031±0.006<br>-44±6<br>1.3±0.2|2.573±0.026<br>-0.040±0.014|



90.5 GHz 2.519±0.013 0.004±0.012 -0.035±0.013

92.5 GHz 2.526±0.014 -0.010±0.015 -0.055±0.015

102.5 GHz 2.501±0.013 0.005±0.012 -0.021±0.012

104.5 GHz 2.487±0.012 0.013±0.012 -0.059±0.012
Ep. 2 All 2.895±0.007 0.019±0.007 -0.043±0.007 -33±4 1.6±0.2 2.883±0.029 -0.043±0.003
90.5 GHz 2.871±0.012 0.008±0.012 -0.062±0.012

92.5 GHz 2.874±0.014 0.010±0.014 -0.028±0.014

102.5 GHz 2.892±0.012 0.002±0.012 -0.042±0.012

104.5 GHz 2.928±0.012 0.029±0.012 -0.051±0.012



3.3.1. Intra-epoch variability


As the ALMA data consists of several scans per epoch, in addition to time-averaged analysis, we also studied the intra-epoch
variability of the mm emission from GRS 1915+105. In this
analysis, we considered only Stokes I flux densities because
of the weakness of the polarized flux densities. The full-band
Stokes I flux densities for individual scans varied between 2.3
and 2.7 mJy in Epoch 1 and 2.6 and 3.3 mJy in Epoch 2 (Fig.
10). In the same figure, we also plot the variability of the phase
calibrators. Although the variations of the phase calibrator and
the target are not correlated in either epoch, the phase calibrator
used during the first epoch (J1922+1530) also shows variability of similar amplitude as the target. As discussed in Sect. 2.1,
the combined effect of a more extended array configuration and
worse atmospheric conditions during the first epoch make the
estimates of short-term variability less reliable. However, during the second epoch, the phase calibrator is very stable, and
we conclude that the variability seen on timescales of minutes
is intrinsic to the source, demonstrating usefulness of ALMA in
studying fast variability in XRBs.


Article number, page 8 of 18



3.3.2. Millimeter/X-ray correlation


Radio/X-ray correlation is one of the most important pieces of
observational evidence in connecting the mass accretion rate
onto the compact object during an outburst event to the massloading of the jet that seems to be at work in both XRBs (e.g.,
Hannikainen et al. 1998; Corbel et al. 2003; Gallo et al. 2003)
and AGNs (e.g., Merloni et al. 2003; Falcke et al. 2004). During
low-luminosity hard X-ray states in XRBs, the logarithmically
scaled X-ray and radio luminosities present a tight relation of
_L_ radio ∝ _L_ X [∼][0][.][7] . This relation can be explained by assuming that
the X-ray emission arises from Compton scattering in advectiondominated accretion flow (ADAF) and the radio emission from
the optically thick synchrotron emission in the jet (Heinz & Sunyaev 2003).

To investigate the radio/X-ray correlation of GRS 1915+105,
we searched for millimeter and X-ray observations during radioquiet/plateau states to compare them with our ALMA data. We
used the 350 GHz James Clerk Maxwell Telescope (JCMT)
observations from Ogley et al. (2000) that were taken during
a radio-quiet state and 94 GHz Nobeyama Millimeter Array
(NMA) observations from Ueda et al. (2002) that were taken
during a radio plateau state, both of which should present a compact steady jet. The corresponding 3-10 keV X-ray fluxes were

K. I. I. Koljonen and T. Hovatta: ALMA/ _NICER_ observations of GRS 1915+105


2.8



2.7


2.6


2.5


2.4


2.3


2.2

357

356

355

354

353

352

3.4


3.2


3.0


2.8


2.6


90.5


90.0


89.5



























85 90 95 100 105 110


Frequency [GHz]


**Fig. 9.** ALMA band 3 spectra of GRS 1915+105 and calibrator sources
from the two epochs.


estimated using quasi-simultaneous archival RXTE data taken
from HEASARC and reduced according to standard procedures.
The resulting mm/X-ray correlation can be seen in Fig. 11 with
a correlation coefficient of 0.58±0.05. For comparison, we plotted the GX 339-4 hard-state radio/X-ray correlation (gray triangles; same X-ray band, but radio luminosity is from 8.4 GHz;
from Koljonen & Russell 2019). Both have similar correlation
coefficients (assuming flat spectrum), reinforcing the hard-state
nature of GRS 1915+105 during ALMA observations and the
decay phase.



89.0

0 10 20 30 40 50 60 70 80 90 100 110 120


Time since obs. start [min]


**Fig.** **10.** Band 3 light curve from the two ALMA epochs in time bins
of one scan length (∼10 min). The top two panels show the data from
Epoch 1 and the bottom two panels from Epoch 2 for GRS 1915+105
and the phase calibrators J1922+1530 and J1905+0952. The horizontal lines and the gray bands show the mean value of the flux density
throughout the epochs as tabulated in Table 2.


**4.** **Discussion**


To briefly summarize the above results, we find that GRS
1915+105 exhibits typical XRB hard-state properties during the
exponential and linear decay phases. These include decreasing
X-ray luminosity down to ∼1% of the Eddington luminosity,
PSD with a band-limited noise profile and a type-C QPO with
a harmonic, an absorbed power-law spectrum that can be fitted
with a Comptonization model, and a weakly polarized, compact,
optically thick jet. The mm/X-ray correlation shows similar coefficient to that of canonical low-luminosity XRBs in the radiatively inefficient track, further suggesting that the source is in the
canonical hard state. The X-ray light curve profile showing first
an exponential decay followed by a linear decay is a hallmark
of a viscous and irradiation-controlled decay observed during
the end stages of transient XRB outbursts (e.g., Tetarenko et al.
2018). However, the following rebrightening phase displayed
similar X-ray and radio properties to the preceding exponential
and linear decay phases, with elevated X-ray and radio luminosity marking a departure from the linear decay trend. In addition,
the PSDs show an additional red noise power-law component increasing in rms, and the X-ray spectra show high-ionization absorption lines and modeling results indicate increasing absorption. When the source transits to the obscured state, the X-ray
properties change markedly with an order of magnitude drop


Article number, page 9 of 18

_A&A proofs:_ manuscript no. 39581corr









L 3-10 keV (erg s [−1] )


**Fig. 11.** GRS 1915+105 mm/X-ray correlation (blue points). The highluminosity data are from JCMT (Ogley et al. 2000) and NMA (Ueda
et al. 2002) together with quasi-simultaneous RXTE observations. In
comparison, GX 339-4 hard-state radio/X-ray correlation is shown
(gray triangles; same X-ray band, but radio luminosity is from 8.4
GHz; from Koljonen & Russell 2019). Both have similar correlation
slopes (assuming flat spectrum), reinforcing the hard-state nature of
GRS 1915+105 during ALMA observations.


in the X-ray flux, the PSDs show a pure red noise profile, and
the X-ray spectra becomes much harder with prominent highionization emission lines.


_4.1._ _Comparison with the previous low X-ray flux states_


During the outburst, we divided the low-X-ray-flux states of
GRS 1915+105 into two different states depending on the
strength of the radio flux density: a radio-quiet hard (χ) state with
a radio flux density of a few mJy, and a plateau state with the
radio flux density presenting higher, typically 50-100 mJy flux
densities (Foster et al. 1996; Pooley & Fender 1997; Fender et al.
1999). The former is close to a ‘normal’ XRB hard state, while
the latter is probably a high-luminosity excursion from a very
high state. For both states, the jet properties are similar (apart
from the flux density) and correspond to a steady, flat-spectrum,
optically thick compact jet. Selecting observations at the plateau
state which presents a compact steady jet, Rushton et al. (2010)
were able to find a radio/X-ray relation of _L_ radio ∝ _L_ X [∼][1][.][7][±][0][.][3] or
_L_ radio ∝ _L_ X [∼][1][.][1][±][0][.][1] if only taking the coronal emission into account
when estimating the X-ray luminosity (Peris et al. 2016).
Many XRBs show a steeper radio/X-ray correlation during
high-luminosity phases of the hard state (e.g., Coriat et al. 2011).
It is unclear whether the change depends on the source being
in outburst rise or decline (Koljonen & Russell 2019; Islam &
Zdziarski 2018) or there exists multiple correlations depending
on the physical qualities of the systems (Gallo et al. 2012). The
different physical mechanisms for multiple correlations have
been suggested to arise from differences in radio emission properties (Casella & Pe’er 2009; Espinasse & Fender 2018), differences in X-ray emission properties (Meyer-Hofmeister & Meyer


Article number, page 10 of 18



2014; Coriat et al. 2011; Xie & Yuan 2016), or inclination effects
on X-ray emission properties (Heil et al. 2015; Muñoz-Darias
et al. 2013; Motta et al. 2018; Petrucci et al. 2001; Nied´zwiecki
2005) and radio emission properties (Soleri & Fender 2011;
Motta et al. 2018). Whatever the case, the change of the correlation coefficient of GRS 1915+105 to _L_ radio ∝ _L_ X [∼][0][.][6] indicates a
change in the evolution of the outburst to a low-luminosity hard

state.
Both plateau and χ states show similar X-ray timing properties to those observed during the exponential and linear decay
with a PSD presenting a flat-top noise profile and a type-C QPO.
However, the radio-quiet state shows QPOs with central frequencies greater than ∼2 Hz while the plateau state shows QPOs with
central frequencies lower than ∼2 Hz (Pahari et al. 2013). Interestingly, similar behavior is seen in the transition from exponential and linear decay phases that display a transitional QPO
frequency of 2 Hz. In addition, it has been found that the average
QPO phase lag is positive above and negative below 2 Hz (Reig
et al. 2000; Lin et al. 2000; Qu et al. 2010; Pahari et al. 2013;
Zhang et al. 2020), and a similar trend can be observed between
the exponential and linear outburst decay phases. This effect has
been attributed to a pivoting lag-energy spectrum with the lag
increasing with energy for progressively lower QPO frequencies
and decreasing for progressively higher QPO frequencies (Pahari et al. 2013; Zhang et al. 2020).
Several explanations for the phase lag behavior have been
discussed in the literature. van den Eijnden et al. (2017) relate
the phase lags to the inclination of the system. Soft lags are observed from high-inclination systems, and hard lags are observed
from low-inclination systems for QPO frequencies exceeding 2
Hz. In particular, for GRS 1915+105, the phase lag behavior
is linked to an evolving two-temperature corona (Nobili et al.
2000) or two precessing regions of the accretion flow (van den
Eijnden et al. 2016). While differing in physical picture, the underlying assumption in both scenarios is the same, presenting
two (or more) regions located at different radii and having a different spectral response. The difference in the location produces
the change in the QPO frequency, while the different spectral
response produces the change in the phase lag. Effectively, this
means that for high QPO frequencies the spectral response of the
inner part of the accretion flow is harder than that of the outer
part, while for low QPO frequencies the outer part presents a
harder response. The zero time lag with ∼2 Hz QPO frequency
would correspond to a similar spectral response from both regions.
During the transition to the linear decay phase, the lag at the
QPO frequency decreases, indicating that the dominating emission region has moved outwards. Relating this behavior to the
plateau/radio-quiet state of the outburst phase means that the
plateau is a hard X-ray state with a compact hot inner flow while
the radio-quiet state presents more expanded hot inner flow.
However, the behavior of the radio emission is different, with the
radio flux density staying at a low level of 1-3 mJy throughout
the linear decay phase (Motta et al. 2021) while the plateau state
presents much higher radio flux densities. However, this can be
expected, as the mass accretion rate during the outburst phase is
at least an order of magnitude higher (see Fig. 2).


_4.2._ _Viscous outburst decay?_


Assuming the observed light-curve profile obeys the standard
XRB outburst decay profile, we fit the _NICER_ light curve with
a model used in Powell et al. (2007), Heinke et al. (2015), and
Tetarenko et al. (2018) corresponding to an exponential decay

K. I. I. Koljonen and T. Hovatta: ALMA/ _NICER_ observations of GRS 1915+105



on a viscous timescale and a linear decay on an irradiationcontrolled timescale. The full model can be written as:


( _f_ _t_ − _f_ 2 ) exp (−( _t_ − _t_ _break_ )/τ _e_ ) + _f_ 2 if _t_ ≤ _t_ _b_
_f_ _X_ =, (1)
� _f_ _t_ (1 − ( _t_ − _t_ _b_ )/τ _l_ ) if _t_   - _t_ _b_


where τ _e_ is the viscous (exponential) timescale, τ _l_ is the
irradiation-controlled (linear) timescale, _t_ _b_ is the transition time,
_f_ _t_ is the flux density at the transition, and _f_ 2 is the asymptotic
flux density of the exponential decay. The fit resulted in the following parameters: τ _e_ = 58 ± 4 days, τ _l_ = 461 ± 6 days, _t_ _b_ =
58328±1 days (MJD), _f_ _t_ = 0.195 ± 0.001× 10 [−][8] erg s [−][1] cm [−][2],
and _f_ 2 = 0.07 ± 0.02× 10 [−][8] erg s [−][1] cm [−][2] .
Taken at face value, the timescale of the exponential decay
(58 days) appears to be relatively low. The approximate viscous
time of the whole disk is at least _t_ visc ≈ α [−][1] ( _H_ / _R_ ) [−][2] _t_ dyn ∼ 500
days, where we take the viscosity parameter as α = 0.2, the
scale height to radius ratio as _H_ / _R_ = 0.1, and _t_ dyn ∼ 1 day as
the reciprocal of the Keplerian frequency at the circularization
radius (∼2×10 [12] cm). However, the average viscosity parameter of the whole disk is likely much lower as only the irradiated
part of the disk is in the hot state, which would make the viscous timescale even longer. Possible mechanisms to decrease the
viscous time include increasing the value of the average viscosity parameter and/or increasing the scale height to a radius ratio
from the canonical values. In addition, the outflowing wind reduces the viscous timescale by a factor of (1 − _e_ _w_ ), which for the
strong disk wind of GRS 1915+105 can be a sizable effect.
Typically, observation of the exponential decay requires that
the disk has been completely ionized and _R_ irr - _R_ out . As GRS
1915+105 harbors such a large disk, this is likely not the case.
Instead, it appears that the outburst decay behaves as if GRS
1915+105 has only a disk size of _R_ out = _R_ irr ∼ 5×10 [11] cm. Alternatively, the exponential decay may arise from another process
that reduces the mass accretion rate to the black hole. Cannizzo
(2000) discusses a case where the evaporation of the thin accretion disk into a hot inner flow close to the compact object is dominant over the viscous evolution. Strong evaporation leads to an
e-folding decay rate associated with the loss of material from the
inner accretion disk that can be ten times faster than the viscous
evolution. Indeed, the critical luminosity for the disk evaporation scheme to hold is considered to be approximately 5% of the
Eddington luminosity (Meyer-Hofmeister 2004), which matches
with the luminosities observed at the end of the exponential de
cay.


_4.3._ _Geometrical implications of the outburst decay_


Based on the canonical scenario, the X-ray spectra showing a
slowly hardening and diminishing Comptonization component
corresponds to the reducing radiative cooling of the optically
thin and hot inner accretion flow as the optically thick accretion disk recedes or evaporates to larger radii. If the power-law
component in the PSD during the exponential decay is flicker
noise (with Γ ∼1) from the accretion disk (Lyubarskii 1997),
this supports the receding or evaporating disk. However, a disk
component is not statistically needed to fit the X-ray spectra, but
as the absorption towards GRS 1915+105 is high, the modeling
of the curved soft X-ray part of the spectra can be degenerate and
a low-temperature disk could still produce some of the soft Xrays. Similarly, the rms of the zero-centered Lorentzian increases
from 10% to 20%, which implies that the dilution from the disk
is not impacting the rms in the linear decay phase. In the linear



decay phase, the spectral evolution stops and settles into a stable
state with slowly decreasing flux density and QPO frequency. If
the type-C QPO frequency is tied to the size of the precessing
hot inner flow (Ingram et al. 2009), this means that the disk is
still receding, but does not present enough cooling of the inner
flow for the spectral evolution to remain constant.
In the rebrightening phase, the evolution of both the spectral
and timing properties have departed from the linear decay. The
X-ray power-law photon index and ionization parameter from
the continuum modeling, in addition to the X-ray and radio flux
densities, present elevated values. Thus, it seems that the mass
accretion rate has increased slightly to the compact object. At
the same time, the X-ray spectra show high-ionization absorption lines and the power-law component steepens and becomes
prominent in the PSD during the latter part of the rebrightening
phase, indicating an increased amount of absorbing and scattering material along the line of sight. The redshifted Fe XXV Kα
could arise from inflowing dense clumps in the disk atmosphere
ans/or corona (Kubota et al. 2018). However, this scenario does
not explain why Fe XXVI Lyα line is not redshifted. Alternative
to a redshifted line, several ionization zones that produce several
absorbing charge states can broaden the absorption line without
invoking a fast wind (Miller et al. 2020). This scenario would
indicate a relatively dense medium of N H =3–6×10 [23] cm [−][2] in
the line of sight.
Based on _Chandra_ data, Miller et al. (2020) argued that the
obscuration is caused by a “failed wind” that arises close to
the black hole and is unable to escape from the system. Their
first _Chandra_ observation coincided with the latter part of the
rebrightening phase (MJD 58603) where there was evidence of
obscuration through photoionized absorption. Alternatively, the
emerging obscuration could arise in a radially stratified, puffedup outer disk as discussed in Neilsen et al. (2020). Based on photoionization modeling of _NICER_ spectra during an X-ray flare in
the obscured state, these latter authors argued that the X-ray absorption takes place further out in a vertically extended outer
disk (R∼few×10 [11] cm). The puffed-up outer disk could either
arise from changes in the inner accretion flow increasing the
temperature and scale-height of the outer disk by irradiation, or
a structural change of the outer disk connected to the ending of
the outburst and a switch to the quiescent state.
Based on these scenarios and our modeling of the _NICER_
data, the failed wind or puffed-up outer disk would gradually
form during the rebrightening phase. This can be seen both in
the continuum modeling, in the absorption line evolution, and
in the X-ray PSD evolution. In the continuum, local absorption
from lighter elements, as well as the increase of the reflection
factor, indicates increasing scattering in the surrounding matter with time. At the same time, the equivalent widths of the
highly ionized iron absorption lines increase, and the ratio of Fe
XXVI/Fe XXV decreases, indicating the presence of increased
cooler material in the line of sight. Also, the steepening powerlaw component in the PSD as well as the dilution of the rms
of the zero-centered Lorentzian is consistent with a scattering
medium slowly entering the line of sight. The additional luminosity seen in the rebrightening phase with respect to the linear
decay could arise from reaccreting the failed wind or some interaction with the wind, such as for example backscattering of
emission from the far side of the scattering cloud, or a structural change of the inner accretion flow resulting in an increase
in the mass accretion rate. Although the X-ray observations may
indicate an emerging wind in the rebrightening phase, which in
principle could work as a depolarizing medium for the mm emission from the jet, the polarization fraction of the mm emission


Article number, page 11 of 18

_A&A proofs:_ manuscript no. 39581corr



increases in the rebrightening phase. This could either mean that
the depolarization of the putative wind does not present a measurable effect on the polarization or that the mm emission line of
sight does not coincide with the disk wind.


The change to the obscured state occurs likely at MJD 58608
or soon after. The spectra during the _NICER_ pointing still show
highly ionized absorption lines but present a clear drop in the
photon power law index, ionization parameter, and flux density
of the continuum departing from the levels of the rebrightening
phase. The rest of the _NICER_ pointings are well into the obscured phase. Extrapolating the flux decay from the linear decay
phase shows that ∼80% of the observed flux is absorbed or scattered.


_4.4._ _The fate of the GRS 1915+105 outburst_


The fate of the GRS 1915+105 outburst is currently unclear.
Nevertheless, a return to a “regular” hard state, not been seen before during the outburst, can be established based on the present
work, as detailed above. If the outburst of GRS 1915+105 is
taken to be similar to other XRBs, a return to a hard state heralds
the impending end of the outburst and an eventual return to quiescence. On the other hand, recent work on the obscured state by
Balakrishnan et al. (2020), Motta et al. (2021), and Neilsen et al.
(2020) shows that GRS 1915+105 has exhibited both strong Xray and radio flaring, indicating a significant mass accretion rate
to the compact object. However, due to the heavily modified Xray spectra by the obscuring material, the intrinsic X-ray luminosity is difficult to estimate accurately with values ranging from
1% (Koljonen & Tomsick 2020; Miller et al. 2020) to 10% (Balakrishnan et al. 2020; Neilsen et al. 2020) and possibly reaching
100% of the Eddington ratio occasionally (Balakrishnan et al.
2020). In addition, it is not altogether clear whether the radiative
efficiency of the jet remains constant. If there is matter expelled
in the direction of the jet, it can interact with the jet material
producing shocks and more efficient dissipation of the jet kinetic

energy.


Possible clues as to the underlying mass accretion rate may
come from the much softer state observed during September
2020. Based on _MAXI_ /GSC data (Motta et al. 2021, see also Fig.
2), the X-ray spectrum can be fitted with a thermal model with a
flux corresponding to the level observed in the linear decay phase
(assuming no obscuration). Excursions to lower hardness ratios
during the outburst decays of XRBs are seen, for example during
the 2002/2003 outburst of GX 339−4 (Belloni et al. 2005). On
the other hand, it is not clear in what way the softer state during
September 2020 is affected by absorption and the source could
also present larger intrinsic luminosities (Motta et al. 2021).


As discussed in Miller et al. (2020) and Motta et al. (2021),
GRS 1915+105 may be experiencing a phase of high obscuration under which the source continues to accrete at the same
rate as before. At some point in the future, when the obscuring
matter is lifted, we will see the rise in the apparent luminosity,
which could be what happened in 1992 at the “onset” of the outburst. On the other hand, given the results presented above, it
is reasonable to assume that GRS 1915+105 has reached a lowluminosity hard state and could be on its way to quiescence. As
the accretion disk of GRS 1915+105 is very large, we are seeing
the return to quiescence play out in slow motion as compared to
other XRBs with much smaller disks, and this process can therefore take years.


Article number, page 12 of 18



_4.5._ _Implications of an_ ∼ _30 year outburst_


In this section, we entertain the possibility that the outburst began in 1992 and that the source is heading towards quiescence
in the near future, and what that would imply in terms of system
parameters.
Truss & Done (2006) give estimates on the outburst duration based on the assumed amount of matter accreted during the
whole outburst. These latter authors estimate that for the disk
size of _R_ disk = 27 × 10 [11] cm the outburst duration would exceed
a thousand years assuming that all the matter in the disk is accreted and that the surface density throughout the disk is equal to
the critical surface density required to trigger an outburst through
the thermal-viscous instability. However, using a more realistic
surface density profile and a mass loss due to a disk wind, Truss
& Done (2006) were able to reduce this to 76-160 years (where
the range comes from assuming zero or Eddington mass loss for
the disk wind). This timescale is still too long for a 30-year outburst.
The duration can be further decreased assuming that only a
part of the disk participates in the outburst. Truss & Done (2006)
give a range of _t_ outburst /(1+ _e_ _w_ ) = 47 − ˙23 years˙ depending on
the mass loss of the disk wind _e_ _w_ = _M_ _w_ / _M_ Edd = 0 − 1, and
using a radius of influence of the incident X-rays of _R_ irr,11 = 15,
which fits with the assumed duration of 30 years with _e_ _w_ ∼ 0.75.
The average mass loss rate of the wind has been estimated to
be approximately _M_ [˙] _w_ ≈ 10 [19] g s [−][1] (Neilsen et al. 2012; Miller
et al. 2016). Assuming that during the outburst GRS 1915+105
accreted close to the Eddington accretion rate implies a mass
accretion rate of _M_ [˙] Edd = ˙1.7 ×˙ 10 [19] g s [−][1] for a 12 solar mass
black hole, giving _e_ _w_ = _M_ _w_ / _M_ Edd ≈ 0.6, which is compatible
with the value estimated from the outburst duration.
A more rigorous study with smooth particle hydrodynamics
simulations including the effects of the thermoviscous instability, tidal torques, irradiation by central X-rays, and wind massloss resulted in a similar outburst length of _t_ out = 20 − 40 yr
for an irradiation efficiency of ϵ ∼ 10 [−][3] (Deegan et al. 2009).
Truss & Done (2006) give a slightly larger value for the irradiation efficiency of ϵ = 1.6 × 10 [−][3] for the above radius _R_ irr and
given Eddington luminosity and a standard radiation efficiency
of η = 0.1. However, both studies concluded that the irradiation
efficiency (on average) cannot be higher as it would make the
outburst length much longer.
Based on the assumed outburst duration and the small value
of the irradiation efficiency, it seems clear that only a part of the
disk has participated in the outburst. In the following, we estimate the fraction of the disk mass accreted during the outburst
of GRS 1915+105. The mass accreted during the outburst can
be estimated from the time-averaged rate of mass loss from the
accretion disk:


⟨ _M_ [˙] disk ⟩ = ⟨ _M_ [˙] Edd ⟩ + ⟨ _M_ [˙] _w_ ⟩− _M_ [˙] 2, (2)


where values for _M_ [˙] Edd and _M_ [˙] _w_ are given above. The masstransfer rate from the companion _M_ [˙] 2 can be estimated from Deegan et al. (2009) and Ritter (1999):



0.98
_M_ ⊙ yr [−][1], (3)
�



− _M_ [˙] 2 ∼ 7.3 × 10 [−][10] _M_ 2
� M ⊙



1.74 _P_ orb
� � 1d



which gives − _M_ [˙] 2 ∼ 1.3 × 10 [18] g s [−][1] for system parameters of GRS 1915+105. Alternatively, we can use the modeled
asymptotic flux density of the exponential decay fitted to the

K. I. I. Koljonen and T. Hovatta: ALMA/ _NICER_ observations of GRS 1915+105



light curve, _f_ 2 = 0.7 × 10 [−][8] erg s [−][1] cm [−][2], which for the distance of 8.6 kpc and a standard radiative efficiency of η = 0.1
corresponds to ∼7×10 [18] g s [−][1] when taking into account a bolometric correction of 10, which is typical for a hard-state XRB
(Koljonen & Russell 2019). This is of similar order to the value
estimated from Eq. 3. Inserting − _M_ [˙] 2 = 1.3 × 10 [18] g s [−][1] to Eq.
2 results in _M_ [˙] disk ∼ 2.6 × 10 [19] g s [−][1], which for the assumed
outburst duration of 30 years is 2.3×10 [28] g mass lost. To regain
this mass via the mass-transfer rate from the companion would
take approximately 560 years.
An approximate or upper limit for the total mass of the disk
before the onset of the outburst can be roughly estimated from:


_R_ out
_M_ disk = 2π _R_ Σ( _R_ ) _dR_, (4)
� 0


and assuming that the surface density, Σ, at all radii, _R_, is
equal to the critical surface density, Σ max, to trigger an outburst
via the thermal-viscous instability (Hameury et al. 1998):



1.14
g cm [−][2], (5)
�



present evidence of increased absorption and scattering (Sects.
3.2.3 and 3.2.4) likely in the form of an accretion disk wind or a
puffed-up outer disk (Sect. 4.3).
Due to the large mass reservoir of the accretion disk in GRS
1915+105, and assuming the outburst is ending in the near future, the source would have managed to accrete or eject only
a small part of the matter available in the disk during its threedecade-long outburst (Sect 4.5). The relatively short outburst duration also requires both a strong disk wind and a small irradiation efficiency leading to the irradiated part of the disk being
much less than the size of the disk. This is in direct discrepancy
with the exponential decay profile, which is typically linked to

                                      the viscous decay of fully irradiated disks. We speculate that effi
cient evaporation of the inner accretion disk could be responsible
for the e-folding decay profile (Sect 4.2). Of course, all of these
problems could be solved by assuming that the outburst is still
continuing and we have only witnessed a peculiar transit first to
a canonical low-luminosity hard state and secondly to a heavily
obscured but intrinsically bright accretion state (Sect 4.4).
Since the beginning of its outburst, GRS 1915+105 has
shown remarkable behavior in emission from the accretion disk
and the jet, and the recent observations of a variety of new accretion states show no exception. The peculiarities likely arise
from the large disk size and our near-edge-on viewing angle to
the disk, allowing us to study the geometrical effects of the accretion flow. In addition, due to the long viscous time of the
accretion disk in GRS 1915+105, we might also be witnessing events in slow motion as compared to much smaller disks
in other XRBs, which enhances the importance of detailed studies of GRS 1915+105 in the near future.


_Acknowledgements._ K. I. I. K. was supported by the Academy of Finland project
320085. T. H. was supported by the Academy of Finland projects 317383,
320085, and 322535. We thank the anonymous referee for useful comments.
In addition, we thank the staff of the Nordic ARC Node for help in analyzing
the reliability of the fast variability in our ALMA data. This paper makes use of
the following ALMA data: ADS/JAO.ALMA#2018.1.00621.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan),
together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic
of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research has made use of
data and/or software provided by the High Energy Astrophysics Science Archive
Research Center (HEASARC), which is a service of the Astrophysics Science
Division at NASA/GSFC.


**References**


Balakrishnan, M., Miller, J. M., Reynolds, M. T., et al. 2020, arXiv e-prints,
arXiv:2012.15033

Belloni, T., Homan, J., Casella, P., et al. 2005, A&A, 440, 207
Bianchi, S., Matt, G., Nicastro, F., Porquet, D., & Dubau, J. 2005, MNRAS, 357,
599
Cannizzo, J. K. 2000, ApJ, 534, L35
Casella, P., Belloni, T., & Stella, L. 2005, ApJ, 629, 403
Casella, P. & Pe’er, A. 2009, ApJ, 703, L63
Castro-Tirado, A. J., Brandt, S., Lund, N., et al. 1994, ApJS, 92, 469
Corbel, S., Fender, R. P., Tzioumis, A. K., et al. 2000, A&A, 359, 251
Corbel, S., Nowak, M. A., Fender, R. P., Tzioumis, A. K., & Markoff, S. 2003,
A&A, 400, 1007
Coriat, M., Corbel, S., Prat, L., et al. 2011, MNRAS, 414, 677
Dauser, T., Garcia, J., Parker, M. L., Fabian, A. C., & Wilms, J. 2014, MNRAS,
444, L100
Deegan, P., Combet, C., & Wynn, G. A. 2009, MNRAS, 400, 1337
Dhawan, V., Mirabel, I. F., & Rodríguez, L. F. 2000, ApJ, 543, 373
Done, C., Wardzi´nski, G., & Gierli´nski, M. 2004, MNRAS, 349, 393
Dubus, G., Hameury, J. M., & Lasota, J. P. 2001, A&A, 373, 251
Dubus, G., Lasota, J.-P., Hameury, J.-M., & Charles, P. 1999, MNRAS, 303, 139
Espinasse, M. & Fender, R. 2018, MNRAS, 473, 4122
Falcke, H., Körding, E., & Markoff, S. 2004, A&A, 414, 895
Fender, R. P., Garrington, S. T., McKay, D. J., et al. 1999, MNRAS, 304, 865


Article number, page 13 of 18



−0.38
_R_
� � 10 [10] cm



Σ max = 13.4α [−] _c_ [0][.][83]



_M_ 1
� _M_ ⊙



where α _c_ is the cold viscosity parameter. Inserting Eq. 5
to Eq. 4, and using α _c_ = 0.02 and _M_ 1 / _M_ ⊙ = 12 gives _M_ disk
= 2.7×10 [22] _R_ [3] 10 [.][14] g. Assuming that the disk can at least reach
the circularization radius, which for GRS 1915+105 is approximately 2×10 [12] cm, gives _M_ disk = 4.5 × 10 [29] g, resulting in 5% of
the total mass being accreted or lost during outburst. Similarly,
the radius which corresponds to the lost disk mass is approximately _R_ = 8 × 10 [11] cm.
Using the irradiation law from Dubus et al. (2001), _T_ irr [4] [=]
ϵ _L_ Edd /4πσ SB _R_ [2] irr [, the irradiated temperature needed to fully ion-]
ize an accretion disk layer, _T_ _H_ ∼10 [4] K (Dubus et al. 1999), the
irradiation efficiency of ϵ = 10 [−][3], and Eddington luminosity for
_L_ bol = 1.5 × 10 [39] erg s [−][1] cm [−][2] results in _R_ irr ∼ 5 × 10 [11] cm
for the irradiation radius, which is much less than the size of the
disk (∼2×10 [12] cm), but close to the radius where mass equates
the mass lost from the disk in the outburst as determined above.
Thus, assuming the outburst is nearing its end, we can conclude
that the disk region that participated in the outburst is bounded
by the irradiation radius, which is on the order of 5–8×10 [11] cm,
and contains about 5% of the total disk mass.


**5.** **Conclusions**


We conducted two full polarization ALMA observations together with almost daily _NICER_ pointing observations to study
the jet and accretion disk properties during the outburst decay in
2018–2019 (Sect. 2). We divided the outburst decay into four distinct phases: an exponential decay phase, a linear decay phase, a
rebrightening phase, and an obscured phase (Sect. 3.1). The first
two phases commonly occur during a decaying XRB outburst,
and we show that the X-ray spectral and timing properties of
GRS 1915+105 are indeed typical for a decaying XRB outburst
(Sect. 3.2). In addition, the jet emission in the mm is consistent
with a compact, steady jet showing ∼1% linear polarization, and
the magnetic field likely aligned with the jet position angle (Sect.
3.3). Together with archival mm observations in the hard state,
we formed a mm/X-ray correlation that revealed a correlation
coefficient of 0.6 between the logarithmically scaled luminosities (Sect. 3.3.2). The latter two decay phases are anomalous and

_A&A proofs:_ manuscript no. 39581corr


Fender, R. P., Rayner, D., Trushkin, S. A., et al. 2002, MNRAS, 330, 212
Foster, R. S., Waltman, E. B., Tavani, M., et al. 1996, ApJ, 467, L81
Fuchs, Y., Mirabel, I. F., & Claret, A. 2003, A&A, 404, 1011
Gallo, E., Fender, R. P., & Pooley, G. G. 2003, MNRAS, 344, 60
Gallo, E., Miller, B. P., & Fender, R. 2012, MNRAS, 423, 590
García, J., Dauser, T., Lohfink, A., et al. 2014, ApJ, 782, 76
Greiner, J., Cuby, J. G., McCaughrean, M. J., Castro-Tirado, A. J., & Mennickent, R. E. 2001, A&A, 373, L37
Hameury, J.-M., Menou, K., Dubus, G., Lasota, J.-P., & Hure, J.-M. 1998, MNRAS, 298, 1048
Hannikainen, D. C., Hunstead, R. W., Campbell-Wilson, D., & Sood, R. K. 1998,
A&A, 337, 460
Heil, L. M., Uttley, P., & Klein-Wolt, M. 2015, MNRAS, 448, 3348
Heinke, C. O., Bahramian, A., Degenaar, N., & Wijnand s, R. 2015, MNRAS,
447, 3034
Heinz, S. & Sunyaev, R. A. 2003, MNRAS, 343, L59
Houck, J. C. & Denicola, L. A. 2000, in Astronomical Society of the Pacific Conference Series, Vol. 216, Astronomical Data Analysis Software and Systems
IX, ed. N. Manset, C. Veillet, & D. Crabtree, 591
Ingram, A., Done, C., & Fragile, P. C. 2009, MNRAS, 397, L101
Islam, N. & Zdziarski, A. A. 2018, MNRAS, 481, 4513
Kallman, T. & Bautista, M. 2001, ApJS, 133, 221
Klein-Wolt, M., Fender, R. P., Pooley, G. G., et al. 2002, MNRAS, 331, 745
Koljonen, K., Vera, R., Lahteenmaki, A., & Tornikoski, M. 2019, The Astronomer’s Telegram, 12839, 1
Koljonen, K. I. I. & Russell, D. M. 2019, ApJ, 871, 26
Koljonen, K. I. I. & Tomsick, J. A. 2020, A&A, 639, A13
Kubota, M., Odaka, H., Tamagawa, T., & Nakano, T. 2018, ApJ, 868, L26
Lee, J. C., Reynolds, C. S., Remillard, R., et al. 2002, ApJ, 567, 1102
Lin, D., Smith, I. A., Liang, E. P., & Böttcher, M. 2000, ApJ, 543, L141
Lyubarskii, Y. E. 1997, MNRAS, 292, 679
Martí-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563,
A136
Martocchia, A., Matt, G., Belloni, T., et al. 2006, A&A, 448, 677
Merloni, A., Heinz, S., & di Matteo, T. 2003, MNRAS, 345, 1057
Meyer-Hofmeister, E. 2004, A&A, 423, 321
Meyer-Hofmeister, E. & Meyer, F. 2014, A&A, 562, A142
Miller, J. M., Raymond, J., Fabian, A. C., et al. 2016, ApJ, 821, L9
Miller, J. M., Zoghbi, A., Raymond, J., et al. 2020, ApJ, 904, 30
Miller-Jones, J. C. A., Rupen, M. P., Fender, R. P., et al. 2007, MNRAS, 375,
1087
Mirabel, I. F. & Rodríguez, L. F. 1994, Nature, 371, 46
Motta, S., Williams, D., Fender, R., et al. 2019, The Astronomer’s Telegram,
12773, 1
Motta, S. E., Casella, P., & Fender, R. P. 2018, MNRAS, 478, 5159
Motta, S. E., Kajava, J. J. E., Giustini, M., et al. 2021, arXiv e-prints,
arXiv:2101.01187
Muñoz-Darias, T., Coriat, M., Plant, D. S., et al. 2013, MNRAS, 432, 1330
Muno, M. P., Remillard, R. A., Morgan, E. H., et al. 2001, ApJ, 556, 515
Neilsen, J., Cackett, E., Remillard, R. A., et al. 2018, ApJ, 860, L19
Neilsen, J., Homan, J., Steiner, J. F., et al. 2020, ApJ, 902, 152
Neilsen, J., Petschek, A. J., & Lee, J. C. 2012, MNRAS, 421, 502
Nied´zwiecki, A. 2005, MNRAS, 356, 913
Nobili, L., Turolla, R., Zampieri, L., & Belloni, T. 2000, ApJ, 538, L137
Ogley, R. N., Bell Burnell, S. J., Fender, R. P., Pooley, G. G., & Waltman, E. B.
2000, MNRAS, 317, 158
Pahari, M., Neilsen, J., Yadav, J. S., Misra, R., & Uttley, P. 2013, ApJ, 778, 136
Peris, C. S., Remillard, R. A., Steiner, J. F., et al. 2016, ApJ, 822, 60
Petrucci, P. O., Merloni, A., Fabian, A., Haardt, F., & Gallo, E. 2001, MNRAS,
328, 501
Pooley, G. G. & Fender, R. P. 1997, MNRAS, 292, 925
Powell, C. R., Haswell, C. A., & Falanga, M. 2007, MNRAS, 374, 466
Qu, J. L., Lu, F. J., Lu, Y., et al. 2010, ApJ, 710, 836
Reid, M. J., McClintock, J. E., Steiner, J. F., et al. 2014, ApJ, 796, 2
Reig, P., Belloni, T., van der Klis, M., et al. 2000, ApJ, 541, 883
Remillard, R. A. & McClintock, J. E. 2006, ARA&A, 44, 49
Ritter, H. 1999, MNRAS, 309, 360
Rodríguez, L. F. & Mirabel, I. F. 1999, ApJ, 511, 398
Rushton, A., Spencer, R., Fender, R., & Pooley, G. 2010, A&A, 524, A29
Russell, T. D., Miller-Jones, J. C. A., Curran, P. A., et al. 2015, MNRAS, 450,
1745
Soleri, P. & Fender, R. 2011, MNRAS, 413, 2269
Steeghs, D., McClintock, J. E., Parsons, S. G., et al. 2013, ApJ, 768, 185
Tetarenko, B. E., Lasota, J. P., Heinke, C. O., Dubus, G., & Sivakoff, G. R. 2018,
Nature, 554, 69
Trushkin, S. A., Nizhelskij, N. A., Tsybulev, P. G., Bursov, N. N., & Shevchenko,
A. V. 2019, The Astronomer’s Telegram, 12855, 1
Truss, M. & Done, C. 2006, MNRAS, 368, L25
Truss, M. R. & Wynn, G. A. 2004, MNRAS, 353, 1048
Ueda, Y., Yamaoka, K., Sánchez-Fernández, C., et al. 2002, ApJ, 571, 918
van den Eijnden, J., Ingram, A., & Uttley, P. 2016, MNRAS, 458, 3655
van den Eijnden, J., Ingram, A., Uttley, P., et al. 2017, MNRAS, 464, 2643
Xie, F.-G. & Yuan, F. 2016, MNRAS, 456, 4377
Zhang, L., Méndez, M., Altamirano, D., et al. 2020, MNRAS, 494, 1375


Article number, page 14 of 18

K. I. I. Koljonen and T. Hovatta: ALMA/ _NICER_ observations of GRS 1915+105


**Table .1.** _NICER_ timing analysis parameters.


**Exponential decay phase**


Model: (P)owerlaw (L)orentzian (0) Lorentzian (1) = QPO Main freq. Lorentzian (2) = QPO 1st harmonic
_NICER_ Date Exp. Γ σ 0 rms 0 ν 1 Q 1 rms 1 ν 2 Q 2 rms 2
obs. MJD (s) (Hz) (%) (Hz) (%) (Hz) (%)


A137 58238.609 5491 PL012 0.8 − [+] 0 [0] . [.] 1 [1] 6±1 9±1 4.18±0.04 4.1 [+] − [0] 0 [.] . [7] 6 [6.3][±][0.4] 8.8 [+] − [0] 0 [.] . [3] 2 4 [+] − [3] 2 3.4±0.7
A138 58238.998 1935 PL012 1.0 − [+] 0 [0] . [.] 3 [6] 5 [+] − [2] 1 10±1 3.86±0.05 5±1 6.6±0.6 7.9±0.5 2 [+] − [3] 1 5 [+] − [1] 2
A139 58243.886 1386 L012 – 7±1 13±1 3.56±0.04 7 [+] − [2] 1 6.9±0.6 7.2 [+] − [0] 0 [.] . [2] 3 7 [+] − [11] 5 4±1
A140 58244.015 1440 PL012 0.8 − [+] 0 [0] . [.] 3 [7] 6 [+] − [1] 2 12 [+] − [1] 2 3.36±0.04 5 [+] − [2] 1 7.3 [+] − [0] 0 [.] . [8] 7 6.8±0.2 5 [+] − [4] 2 5±1
A142 58260.064 1038 L01 – 9±1 16.4 [+] − [0] 0 [.] . [7] 7 [3.09][±][0.03] 13 [+] − [7] 4 6.0 [+] − [0] 0 [.] . [6] 7 – – –
A143 58261.847 1141 PL012 1.0 − [+] 0 [0] . [.] 3 [7] 7±2 11 [+] − [1] 2 3.64±0.05 7±2 6.9 [+] − [0] 0 [.] . [8] 7 7.5±0.2 6 [+] − [11] 4 5 [+] − [2] 1
A144 58262.504 764 L012 – 5±1 14±1 3.16±0.06 9 [+] − [6] 3 6.2 [+] − [0] 0 [.] . [8] 9 6.7±0.3 7 [+] − [11] 3 5±1
A145 58263.330 1275 L012 – 4 [+] − [2] 1 13±2 3.04±0.05 7±2 7.0 [+] − [0] 0 [.] . [8] 9 5.8 [+] − [0] 0 [.] . [4] 6 2 [+] − [3] 1 8 [+] − [2] 3
A146 58264.674 709 L01 – 7±1 16±1 2.77±0.04 12 [+] − [6] 3 7.2 [+] − [0] 0 [.] . [7] 8 – – –
A147 58265.962 873 L012 – 7±1 15 [+] − [1] 2 2.73±0.04 10 [+] − [4] 3 6.8 [+] − [0] 0 [.] . [7] 8 5.5±0.2 5 [+] − [5] 3 6 [+] − [2] 1
A148 58266.669 862 L012 – 4±1 15±2 2.48±0.02 10 [+] − [4] 3 8.2±0.8 5.1 [+] − [0] 0 [.] . [2] 3 3 [+] − [3] 1 8±2
A149 58268.664 994 L012 – 6.5 [+] − [0] 0 [.] . [8] 7 18±1 2.19±0.03 8 [+] − [3] 2 7.8 [+] − [0] 0 [.] . [7] 8 4.5±0.1 9 [+] − [7] 4 5±1
A150 58269.500 1619 L012 – 5.6 [+] − [0] 0 [.] . [7] 8 17±1 2.22±0.03 7 [+] − [2] 1 8.2±0.6 4.4±0.1 6 [+] − [6] 3 6 [+] − [2] 1
A152 58271.366 1787 L012 – 4.9±0.8 14±1 3.11±0.03 8±2 7.1±0.6 6.2±0.2 4 [+] − [3] 2 6±1
A153 58272.468 1452 L012 – 7.1±0.9 16±1 2.88±0.03 9 [+] − [3] 2 6.6±0.6 5.8±0.1 9 [+] − [11] 4 5±1
A154 58273.432 1450 L012 – 7±1 16±1 2.94±0.02 13 [+] − [6] 4 5.8±0.6 5.8 [+] − [0] 0 [.] . [1] 2 8 [+] − [15] 5 4 [+] − [2] 1
A155 58274.583 965 L01 – 6 [+] − [1] 2 15 [+] − [1] 2 2.78±0.03 12 [+] − [6] 3 6.6±0.7 – – –
A156 58275.484 2311 L012 – 5.4±0.8 15±1 2.65±0.02 8±2 7.5 [+] − [0] 0 [.] . [6] 5 5.2±0.1 5 [+] − [2] 1 7±1
A157 58277.491 17109 L012 – 5.8±0.2 17.7 [+] − [0] 0 [.] . [3] 3 [2.15][±][0.01] 7.6 [+] − [0] 0 [.] . [6] 6 [8.4][±][0.2] 4.33±0.03 4.7 [+] − [0] 0 [.] . [7] 6 [6.8][±][0.4]
A158 58277.994 5221 L012 – 5.9±0.4 17.4 [+] − [0] 0 [.] . [5] 6 [2.18][±][0.01] 7±1 8.5 [+] − [0] 0 [.] . [3] 4 4.41 [+] − [0] 0 [.] . [05] 06 5 [+] − [1] 1 6.6±0.6
A159 58299.046 1127 L012 – 5.4±0.9 18±1 1.91±0.03 10 [+] − [4] 3 7.8 [+] − [0] 0 [.] . [8] 9 4.0±0.1 6 [+] − [4] 3 7±1


**Linear decay phase**


Model: (P)owerlaw (L)orentzian (0) Lorentzian (1) = QPO Main freq. Lorentzian (2) = QPO 1st harmonic
_NICER_ Date Exp. Γ σ 0 rms 0 ν 1 Q 1 rms 1 ν 2 Q 2 rms 2
obs. MJD (s) (Hz) (%) (Hz) (%) (Hz) (%)


A160 58308.830 719 L012 – 6±1 18 [+] − [1] 2 1.92 [+] − [0] 0 [.] . [05] 02 >9 7±1 3.90±0.09  - 5 6 [+] − [2] 2
A161 58309.147 2705 L012 – 5.1±0.6 18.6 [+] − [0] 0 [.] . [8] 9 [1.86][±][0.02] 13 [+] − [4] 3 6.8±0.6 3.75 [+] − [0] 0 [.] . [05] 04 9 [+] − [5] 3 6 [+] − [1] 1
A162 58310.839 812 L01 – 5.3 − [+] 0 [0] . [.] 7 [9] 19±1 1.89±0.02 17 [+] − [15] 7 7±1 – – –
A163 58312.125 508 L012 – 4 [+] − [2] 1 15±3 1.87 [+] − [0] 0 [.] . [03] 04 >6 7 [+] − [2] 1 4.3±0.3 2 [+] − [3] 1 11 [+] − [2] 3
A164 58313.539 929 L012 – 3.9 [+] − [0] 0 [.] . [9] 8 17 [+] − [1] 2 1.74±0.02 11 [+] − [7] 4 8±1 3.67±0.07 9 [+] − [5] 3 7 [+] − [1] 1
A165 58314.695 806 L01 – 6±1 20±1 2.00 [+] − [0] 0 [.] . [04] 06 >6 7±1 – – –
A166 58315.595 812 L012 – 6±1 18±1 2.04±0.02 >14 7±1 4.05 [+] − [0] 0 [.] . [06] 05  - 11 6 [+] − [1] 1
A167 58316.560 537 L01 – 6 [+] − [2] 1 19 [+] − [1] 2 1.90 [+] − [0] 0 [.] . [06] 08 10 [+] − [13] 4 7 [+] − [1] 2 – – –
A168 58326.992 779 L012 – 4±1 17±2 1.48 [+] − [0] 0 [.] . [05] 04 >9 8 [+] − [1] 2 3.04±0.09 7 [+] − [7] 3 7 [+] − [2] 2
A169 58327.056 735 L012 – 1.3 − [+] 0 [3] . [.] 5 [8] 13±2 1.47±0.03 6 [+] − [10] 2 10 [+] − [1] 3 3.0 [+] − [0] 0 [.] . [3] 6  - 0.6 14 [+] − [3] 9
A170 58328.021 1561 L012 – 4.7±0.7 19±1 1.74 [+] − [0] 0 [.] . [03] 02 >11 6.7 [+] − [0] 0 [.] . [8] 9 3.54±0.07 10 [+] − [8] 4 6 [+] − [1] 1
A171 58329.051 1612 L012 – 2.9 [+] − [0] 0 [.] . [9] 7 16 [+] − [2] 1 1.86±0.02 13 [+] − [5] 3 8.1 [+] − [0] 0 [.] . [8] 9 3.8 [+] − [0] 0 [.] . [2] 1 4 [+] − [5] 2 8 [+] − [2] 2
A172 58330.015 2974 L012 – 3±1 14±2 1.97±0.03 6±1 9±1 4.1±0.1 2 [+] − [2] 1 10 [+] − [2] 2
A174 58332.663 558 L01 – 6 [+] − [2] 1 19±2 1.87±0.03 15 [+] − [10] 6 8±1 – – –
A175 58333.421 822 L01 – 7±1 20±1 1.73 [+] − [0] 0 [.] . [03] 04 10 [+] − [12] 4 7±1 – – –
A176 58334.333 795 L012 – 4 [+] − [1] 3 17 [+] − [2] 6 1.77±0.04 7 [+] − [6] 4 9±1 3.7 [+] − [0] 0 [.] . [2] 4 5 [+] − [11] 4 7 [+] − [2] 3
A180 58343.136 928 L01 – 5.1 [+] − [0] 0 [.] . [8] 7 21±1 1.54 [+] − [0] 0 [.] . [03] 02 >8 6±1 – – –
A181 58347.188 2543 L012 – 4.8 [+] − [0] 0 [.] . [8] 9 18 [+] − [1] 2 1.79±0.04 6 [+] − [2] 1 8.1±0.8 3.7±0.1 5 [+] − [3] 2 7 [+] − [2] 1
A182 58350.534 1170 L01 – 6.0 [+] − [0] 0 [.] . [8] 7 22±1 1.62 [+] − [0] 0 [.] . [03] 02 15 [+] − [13] 7 7±1 – – –
A186 58358.279 1052 L01 – 6±1 21±1 1.88 [+] − [0] 0 [.] . [02] 03 12 [+] − [6] 4 8±1 – – –
A189 58361.304 1256 L012 – 5±1 18 [+] − [1] 2 1.77±0.02 15 [+] − [9] 5 7.8 [+] − [0] 0 [.] . [8] 9 3.6±0.1 8 [+] − [9] 4 7 [+] − [2] 2
A190 58362.268 1261 L012 – 7 [+] − [1] 2 20 [+] − [1] 3 2.02±0.02 14 [+] − [9] 5 7.9±0.9 4.2 [+] − [0] 0 [.] . [4] 2 >2 5±2
A192 58365.357 1485 L012 – 5.9±0.9 20±1 2.02±0.02 13 [+] − [6] 4 8.7±0.8 4.2±0.1  - 5 5 [+] − [2] 2
A193 58378.221 1287 L012 – 5.4±0.9 20±1 1.81±0.02 14 [+] − [11] 5 8±1 3.69 ±0.07 13 [+] − [20] 8 6 [+] − [2] 1
A195 58415.814 1526 L012 – 1.1 [+] − [0] 0 [.] . [4] 3 12 [+] − [1] 2 1.65±0.02 8 [+] − [4] 3 9±1 3.1 [+] − [0] 0 [.] . [3] 8 0.9 [+] − [0] 0 [.] . [8] 5 [15] − [+] 2 [3]
A197 58420.314 3858 L012 – 4.6 [+] − [0] 0 [.] . [5] 4 20.7 [+] − [0] 0 [.] . [6] 7 [1.25][±][0.01] 14 [+] − [4] 3 7.2±0.6 2.5±0.1 >20 3.2 [+] − [0] 0 [.] . [5] 6
A198 58424.756 5647 L01 – 4.2±0.4 19.3 [+] − [0] 0 [.] . [7] 8 [1.51][±][0.01] 13 [+] − [5] 3 7.7±0.5 3.07±0.04 9 [+] − [5] 3 5.8 [+] − [0] 0 [.] . [9] 8
A199 58425.013 6025 L012 – 4.2±0.4 19.3 [+] − [0] 0 [.] . [7] 8 [1.62] − [+][0] 0 [.] . [01] 02 9 [+] − [2] 1 7.9±0.5 3.35 [+] − [0] 0 [.] . [07] 05 7 [+] − [3] 2 6 [+] − [1] 1
A201 58426.946 1720 L012 – 3±1 17±2 1.61±0.02 9 [+] − [4] 3 8±1 3.4±0.1 6 [+] − [5] 3 7 [+] − [2] 2
A206 58438.095 636 L012 – 5 [+] − [1] 2 20 [+] − [2] 4 1.49 [+] − [0] 0 [.] . [06] 05 7 [+] − [13] 4 8 [+] − [1] 2 3.3 [+] − [0] 0 [.] . [1] 3 >2 6 [+] − [2] 3
A208 58440.027 856 L01 – 4.7 [+] − [0] 0 [.] . [9] 8 21±1 1.39±0.03 >6 6 [+] − [1] 2 – – –
A209 58449.092 3065 L012 – 1.3 [+] − [1] 0 [.] . [0] 4 12 [+] − [1] 2 1.39±0.04 4 [+] − [3] 1 9 [+] − [2] 4 2.8 [+] − [0] 0 [.] . [2] 4 1.3 [+] − [1] 0 [.] . [0] 6 [13][±][2]
A210 58450.958 804 L01 – 4±1 21±1 1.28 [+] − [0] 0 [.] . [02] 03 >9 7 [+] − [1] 2 – – –
A211 58451.022 2391 L012 – 0.6 [+] − [0] 0 [.] . [4] 2 9±2 1.55 [+] − [0] 0 [.] . [04] 49 >10 5 [+] − [1] 2 3.2 [+] − [0] 0 [.] . [3] 6 1.1 [+] − [0] 0 [.] . [8] 5 [13][±][2]


Article number, page 15 of 18

_A&A proofs:_ manuscript no. 39581corr


A212 58452.888 798 L01 – 5±1 19±2 1.57±0.05 10 [+] − [7] 4 7±1 – – –
A213 58453.725 904 L01 – 4±1 20 [+] − [1] 2 1.45±0.04 8 [+] − [7] 3 8 [+] − [1] 2 – – –
A214 58455.205 850 L01 – 5±1 21 [+] − [1] 2 1.36 [+] − [0] 0 [.] . [05] 04 7 [+] − [7] 3 8 [+] − [1] 2 – – –
A215 58456.234 2826 L012 – 1.2 − [+] 0 [0] . [.] 3 [6] 13 [+] − [2] 1 1.35±0.02 7±2 9±1 2.8 [+] − [0] 0 [.] . [1] 2 1.5 [+] − [1] 0 [.] . [0] 6 [13][±][2]
A216 58457.264 1278 L012 – 4±1 20±1 1.37 [+] − [0] 0 [.] . [02] 01 >15 7±1 2.9±0.1 >10 5 [+] − [1] 2
A217 58458.229 1185 L012 – 4±1 20 [+] − [1] 2 1.35±0.02 >9 6±1 2.8±0.1 >6 6±2
A218 58459.259 1262 L012 – 3±1 18 [+] − [2] 4 1.16 [+] − [0] 0 [.] . [03] 02 7 [+] − [4] 2 9 [+] − [2] 1 2.4±0.1 6 [+] − [8] 4 >5
A220 58461.255 853 L01 – 5±1 21 [+] − [1] 2 1.35 [+] − [0] 0 [.] . [02] 03 >8 7±1 – – –
A221 58462.092 764 L01 – 6±1 21±2 1.60±0.05 8 [+] − [6] 3 8 [+] − [1] 2 – – –
A222 58463.251 510 L01 – 6±1 21±2 1.60±0.05 8 [+] − [6] 3 8 [+] − [1] 2 – – –


**Rebrightening phase**


Model: (P)owerlaw (L)orentzian (0) Lorentzian (1) = QPO Main freq. Lorentzian (2) = QPO 1st harmonic
_NICER_ Date Exp. Γ σ 0 rms 0 ν 1 Q 1 rms 1 ν 2 Q 2 rms 2
obs. MJD (s) (Hz) (%) (Hz) (%) (Hz) (%)


B101 58548.692 3818 PL012 0.7 − [+] 0 [0] . [.] 2 [4] 5±1 16±2 2.07±0.01 13 [+] − [5] 4 6.6±0.6 4.20 [+] − [0] 0 [.] . [07] 06 9 [+] − [5] 3 6±1
B201 58555.709 3107 PL012 1.0 − [+] 0 [1] . [.] 4 [4] 6±1 18 [+] − [1] 3 2.03±0.01 18 [+] − [9] 5 6.8±0.6 4.06±0.07 9 [+] − [5] 3 6±1
B301 58562.664 2867 PL012 0.6 − [+] 0 [0] . [.] 1 [2] 4±1 13±2 2.23±0.02 14 [+] − [8] 4 6.8±0.7 4.55 [+] − [0] 0 [.] . [05] 06 9 [+] − [5] 3 7±1
B401 58569.429 3222 PL012 1.1 − [+] 0 [0] . [.] 2 [4] 5±1 16 [+] − [1] 2 2.42± 0.02 11 [+] − [4] 3 6.6± 0.7 4.94±0.08 9 [+] − [5] 3 6±1
B501 58577.106 731 PL012 1.5 − [+] 0 [0] . [.] 4 [5] 6 [+] − [4] 2 16 [+] − [3] 4 2.42 [+] − [0] 0 [.] . [06] 07 9 [+] − [11] 5 7±2 4.9 [+] − [0] 0 [.] . [3] 2 >3 7±2
B601 58583.037 3011 PL012 1.0 − [+] 0 [0] . [.] 2 [3] 5±1 16 [+] − [2] 3 2.21±0.01 15 [+] − [6] 3 8.0±0.6 4.49 [+] − [0] 0 [.] . [09] 08 7 [+] − [4] 3 7±1
B701 58589.157 2983 PL012 1.2 − [+] 0 [0] . [.] 2 [2] 6±2 15±2 2.49±0.03 8±2 7.4±0.8 5.17±0.14 4 [+] − [2] 1 8 [+] − [2] 1
B801 58596.557 3766 PL012 1.3±0.1 6±1 17±2 2.08±0.02 8 [+] − [2] 1 10.2±0.7 4.30 [+] − [0] 0 [.] . [08] 07 7 [+] − [4] 2 7±1
B901 58604.414 3601 PL012 1.4±0.1 7±3 13 [+] − [3] 4 3.10±0.05 5 [+] − [2] 1 9±1 6.2 [+] − [0] 0 [.] . [2] 3 5 [+] − [5] 2 7±2
C001 58608.537 4432 PL1 1.32±0.05 – – 3.2±0.2 3 [+] − [3] 2 0.09±0.02 – – –


**Obscured phase**


Model: (P)owerlaw (L)orentzian (0) Lorentzian (1) = QPO Main freq. Lorentzian (2) = QPO 1st harmonic
_NICER_ Date Exp. Γ σ 0 rms 0 ν 1 Q 1 rms 1 ν 2 Q 2 rms 2
obs. MJD (s) (Hz) (%) (Hz) (%) (Hz) (%)


C202 58622.518 14421 P 1.3±0.2 – – – – – – – –
C203 58623.033 4618 P 1.2 − [+] 0 [0] . [.] 3 [4] – – – – – – – –
C204 58624.065 6830 P 1.9±0.1 – – – – – – – –

C205 58625.030 4314 P 2.0±0.1 – – – – – – – –

C206 58625.998 3673 P 1.7±0.2 – – – – – – – –
C207 58627.417 6401 P 1.8 − [+] 0 [0] . [.] 2 [3] – – – – – – – –
C208 58628.057 4627 P 2.3 − [+] 0 [0] . [.] 2 [3] – – – – – – – –
C209 58629.024 1532 – – – – – – – – – –
C301 58631.089 15866 P 1.7 − [+] 0 [0] . [.] 4 [5] – – – – – – – –
C302 58632.247 8146 P 2.0 − [+] 0 [0] . [.] 3 [4] – – – – – – – –
C303 58633.601 4790 P 1.7±0.3 – – – – – – – –

C304 58634.246 3514 – – – – – – – – – –


Article number, page 16 of 18

K. I. I. Koljonen and T. Hovatta: ALMA/ _NICER_ observations of GRS 1915+105


**Table .1.** _NICER_ spectral analysis parameters.


**Exponential decay phase**


_NICER_ N(H) N(Mg) N(Al) N(Si) N(S) N(Ca) Γ log ξ R f R in F abs F unabs χ [2] red
obs. 10 [22] atoms/cm [2] 10 [−][8] erg/s/cm [2] 10 [−][8] erg/s/cm [2]


A137 2.40±0.01 3.7±0.2 17±1 3.2±0.1 2.2±0.2 4±1 2.71±0.02 4.70±0.05 0.17 [+] − [0] 0 [.] . [03] 03 [44] − [+][54] 21 0.58±0.04 2.02±0.13 1.32
A138 2.38±0.01 3.2±0.3 16±2 2.9±0.1 2.1±0.4 5±1 2.62 [+] − [0] 0 [.] . [02] 03 4.48 [+] − [0] 0 [.] . [07] 10 0.17 44 0.56±0.02 1.82±0.07 1.06
A139 2.30±0.01 3.5±0.3 10±2 2.8±0.2 1.7±0.4 8±2 2.45 [+] − [0] 0 [.] . [04] 03 4.12 [+] − [0] 0 [.] . [06] 09 0.17 44 0.53±0.03 1.48±0.07 1.43
A140 2.30±0.01 3.1±0.4 11±2 2.7±0.2 2.2±0.5 8±2 2.44±0.04 4.04 [+] − [0] 0 [.] . [05] 06 0.17 44 0.52±0.03 1.44±0.07 1.20
A142 2.29±0.02 3.2 − [+][0] 0 [.] . [5] 4 11±3 2.9±0.2 2.7±0.6 11 [+] − [2] 2 [.] . [5] 4 2.43±0.04 4.04 [+] − [0] 0 [.] . [08] 07 0.17 44 0.40±0.03 1.13±0.06 1.19
A143 2.32±0.02 3.3±0.4 14±3 3.0±0.2 2.4 [+] − [0] 0 [.] . [52] 58 11±2 2.54 [+] − [0] 0 [.] . [04] 03 4.3±0.1 0.17 44 0.44±0.03 1.34±0.07 1.07
A144 2.29±0.02 2.7±0.5 9±3 3.0 [+] − [0] 0 [.] . [2] 3 2.3±0.7 11±3 2.40 [+] − [0] 0 [.] . [04] 05 4.0±0.1 0.17 44 0.42±0.03 1.14±0.06 1.04
A145 2.28 [+] − [0] 0 [.] . [02] 01 2.5±0.4 11±2 2.8±0.2 2.7 − [+] 0 [0] . [.] 54 [60] 10±2 2.38±0.03 4.0±0.1 0.17 44 0.40±0.02 1.08±0.04 1.02
A146 2.25±0.02 2.8 − [+][0] 0 [.] . [5] 6 8 [+] − [3] 4 2.9±0.3 2.6±0.8 11±3 2.31±0.05 3.7±0.1 0.17 44 0.38±0.02 0.97±0.05 1.28
A147 2.24±0.02 2.9±0.5 11±3 2.8 [+] − [0] 0 [.] . [3] 2 3.0±0.7 14±3 2.32±0.04 3.8±0.1 0.17 44 0.38±0.02 0.99±0.04 1.01
A148 2.26±0.02 2.1±0.5 9±3 2.8±0.3 3.1 − [+] 0 [0] . [.] 74 [75] 11±3 2.25±0.05 3.6±0.1 0.17 44 0.37±0.02 0.92±0.05 1.24
A149 2.21±0.02 2.6±0.5 9±3 3.0±0.2 3.7 − [+] 0 [0] . [.] 57 [65] 13±3 2.18 [+] − [0] 0 [.] . [04] 03 3.6±0.1 0.17 44 0.35±0.01 0.84±0.02 1.33
A150 2.22±0.01 2.7±0.4 12±2 3.1±0.2 4.3 [+] − [1] 0 [.] . [03] 56 13±2 2.21 [+] − [0] 0 [.] . [03] 04 3.6±0.1 0.17 44 0.35±0.01 0.86±0.03 1.14
A152 2.26±0.01 2.8±0.3 10±2 2.8±0.2 2.3 [+] − [0] 0 [.] . [44] 46 10±2 2.34 [+] − [0] 0 [.] . [03] 02 4.00 [+] − [0] 0 [.] . [07] 06 0.17 44 0.37±0.01 0.97±0.03 1.19
A153 2.26 [+] − [0] 0 [.] . [02] 01 2.9±0.4 12±2 3.0±0.2 3.1 [+] − [0] 0 [.] . [55] 54 11±2 2.37±0.03 3.79 [+] − [0] 0 [.] . [06] 07 0.17 44 0.35±0.01 0.94±0.03 1.20
A154 2.25±0.01 3.1±0.4 10±2 3.0±0.2 3.0±0.6 13±2 2.37±0.03 3.86 [+] − [0] 0 [.] . [07] 09 0.17 44 0.34±0.01 0.93±0.03 1.29
A155 2.25±0.02 3.0±0.5 13±3 3.0±0.2 3.8 [+] − [0] 0 [.] . [65] 64 14±2 2.38 [+] − [0] 0 [.] . [03] 04 3.9±0.1 0.17 44 0.34±0.02 0.95±0.04 1.09
A156 2.26±0.01 2.1±0.3 7±2 2.7±0.2 2.3 [+] − [0] 0 [.] . [42] 51 10±2 2.24±0.03 3.70 [+] − [0] 0 [.] . [05] 06 0.17 44 0.34±0.01 0.81±0.02 1.15
A157 2.19±0.01 2.7±0.1 7±1 3.2±0.1 4.1±0.4 10±2 2.12±0.02 3.70 [+] − [0] 0 [.] . [05] 07 0.23 [+] − [0] 0 [.] . [12] 04 [100] − [+][0] 62 [0.32][±][0.03] 0.74±0.08 1.22
A158 2.19±0.01 2.8±0.2 7±2 3.2±0.2 4.3±0.5 6±2 2.10±0.02 3.71 [+] − [0] 0 [.] . [05] 04 0.35 100 0.31±0.01 0.71±0.01 1.15
A159 2.20±0.01 =N(H) 3.4±0.3 =N(Al) =N(Al) =N(Al) 2.00±0.03 3.50 [+] − [0] 0 [.] . [06] 08 0.35 100 0.24±0.01 0.51±0.01 1.01


**Linear decay phase**


_NICER_ N(H) N(Mg) N(Al) N(Si) N(S) N(Ca) Γ log ξ R f R in F abs F unabs χ [2] red
obs. 10 [22] atoms/cm [2] 10 [−][8] erg/s/cm [2] 10 [−][8] erg/s/cm [2]


A160 2.21 [+] − [0] 0 [.] . [01] 02 =N(H) 2.8±0.3 =N(Al) =N(Al) =N(Al) 2.02 [+] − [0] 0 [.] . [03] 04 3.6±0.1 0.35 100 0.212±0.004 0.444±0.006 1.09
A161 2.20±0.01 =N(H) 3.2±0.2 =N(Al) =N(Al) =N(Al) 2.03±0.02 3.54 [+] − [0] 0 [.] . [05] 06 0.35 100 0.204±0.002 0.436±0.004 1.12
A162 2.20 [+] − [0] 0 [.] . [01] 02 =N(H) 3.1 [+] − [0] 0 [.] . [3] 4 =N(Al) =N(Al) =N(Al) 2.02±0.04 3.6±0.1 0.35 100 0.204±0.004 0.432±0.007 1.09
A163 2.22±0.02 =N(H) 2.9 [+] − [0] 0 [.] . [4] 3 =N(Al) =N(Al) =N(Al) 2.05±0.05 3.5±0.1 0.35 100 0.196±0.006 0.421±0.009 1.07
A164 2.20 [+] − [0] 0 [.] . [01] 02 =N(H) 2.9 [+] − [0] 0 [.] . [2] 3 =N(Al) =N(Al) =N(Al) 2.01 [+] − [0] 0 [.] . [03] 04 3.43 [+] − [0] 0 [.] . [05] 07 0.35 100 0.194±0.005 0.407±0.009 1.11
A165 2.21±0.02 =N(H) 3.0 [+] − [0] 0 [.] . [4] 8 =N(Al) =N(Al) =N(Al) 2.04±0.04 3.60 [+] − [0] 0 [.] . [10] 15 0.35 100 0.200±0.006 0.430±0.011 1.08
A166 2.21 [+] − [0] 0 [.] . [02] 01 =N(H) 3.4 [+] − [0] 0 [.] . [3] 4 =N(Al) =N(Al) =N(Al) 2.08±0.04 3.6±0.1 0.35 100 0.196±0.005 0.433±0.008 0.98
A167 2.18±0.02 =N(H) 3.2±0.5 =N(Al) =N(Al) =N(Al) 1.97 [+] − [0] 0 [.] . [04] 05 3.6 [+] − [0] 0 [.] . [1] 2 0.35 100 0.185±0.002 0.383±0.005 1.18
A168 2.22±0.02 =N(H) 3.5 [+] − [0] 0 [.] . [6] 4 =N(Al) =N(Al) =N(Al) 1.98±0.04 3.6 [+] − [0] 0 [.] . [1] 2 0.35 100 0.164±0.003 0.347±0.005 1.05
A169 2.20±0.02 =N(H) 3.1 [+] − [0] 0 [.] . [3] 6 =N(Al) =N(Al) =N(Al) 1.93±0.04 3.8 [+] − [0] 0 [.] . [2] 3 0.35 100 0.169±0.007 0.343±0.014 0.98
A170 2.21±0.01 =N(H) 3.1±0.3 =N(Al) =N(Al) =N(Al) 1.98±0.03 3.51 [+] − [0] 0 [.] . [06] 09 0.35 100 0.172±0.002 0.359±0.004 1.03
A171 2.19±0.01 =N(H) 3.4±0.3 =N(Al) =N(Al) =N(Al) 2.00±0.03 3.52 [+] − [0] 0 [.] . [06] 08 0.35 100 0.173±0.002 0.366±0.003 1.09
A172 2.19±0.01 =N(H) 3.1±0.2 =N(Al) =N(Al) =N(Al) 1.99±0.02 3.52 [+] − [0] 0 [.] . [05] 06 0.35 100 0.175±0.001 0.365±0.002 1.12
A174 2.19±0.02 =N(H) 3.3±0.5 =N(Al) =N(Al) =N(Al) 2.00 [+] − [0] 0 [.] . [04] 05 3.5 [+] − [0] 0 [.] . [1] 2 0.35 100 0.165±0.003 0.350±0.005 1.01
A175 2.20±0.01 =N(H) 2.8±0.3 =N(Al) =N(Al) =N(Al) 1.97±0.04 3.5±0.1 0.35 100 0.168±0.004 0.343±0.008 1.13
A176 2.18±0.02 =N(H) 3.3±0.4 =N(Al) =N(Al) =N(Al) 1.96±0.04 3.6 [+] − [0] 0 [.] . [1] 2 0.35 100 0.165±0.002 0.340±0.004 1.05
A180 2.18±0.01 =N(H) 3.1±0.3 =N(Al) =N(Al) =N(Al) 1.91±0.04 3.4±0.1 0.35 100 0.164±0.004 0.328±0.009 1.16
A181 2.17±0.01 =N(H) 3.0±0.2 =N(Al) =N(Al) =N(Al) 1.89±0.02 3.6±0.1 0.35 100 0.165±0.001 0.325±0.003 1.12
A182 2.17±0.02 =N(H) 2.9±0.4 =N(Al) =N(Al) =N(Al) 1.88±0.04 3.5 [+] − [0] 0 [.] . [1] 2 0.35 100 0.157±0.002 0.306±0.005 1.19
A186 2.16±0.02 =N(H) 3.0±0.4 =N(Al) =N(Al) =N(Al) 1.86±0.04 3.5 [+] − [0] 0 [.] . [1] 2 0.35 100 0.161±0.002 0.315±0.005 1.13
A189 2.19±0.01 =N(H) 3.4±0.3 =N(Al) =N(Al) =N(Al) 1.97±0.03 3.6±0.1 0.35 100 0.151±0.001 0.314±0.004 1.06
A190 2.20±0.01 =N(H) 3.3±0.4 =N(Al) =N(Al) =N(Al) 2.00 [+] − [0] 0 [.] . [03] 04 3.6±0.1 0.35 100 0.158±0.002 0.335±0.003 1.08
A192 2.18±0.01 =N(H) 3.0±0.3 =N(Al) =N(Al) =N(Al) 1.98±0.03 3.6±0.1 0.35 100 0.157±0.002 0.324±0.004 1.02
A193 2.19±0.01 =N(H) 3.2 [+] − [0] 0 [.] . [3] 4 =N(Al) =N(Al) =N(Al) 1.98±0.03 3.47 [+] − [0] 0 [.] . [06] 09 0.35 100 0.150±0.002 0.312±0.005 0.96
A195 2.20±0.01 =N(H) 3.4 [+] − [0] 0 [.] . [2] 3 =N(Al) =N(Al) =N(Al) 2.01 [+] − [0] 0 [.] . [03] 04 3.47 [+] − [0] 0 [.] . [06] 08 0.35 100 0.131±0.002 0.279±0.004 1.02
A197 2.15 [+] − [0] 0 [.] . [01] 02 3.2±0.4 14±3 3.7±0.2 4.3±0.5 12±2 2.00±0.03 3.59 [+] − [0] 0 [.] . [07] 09 0.35 100 0.127±0.002 0.282±0.003 1.17
A198 2.17±0.01 2.9±0.3 12±2 3.4±0.2 4.9±0.6 7 [+] − [4] 3 2.00 [+] − [0] 0 [.] . [03] 04 3.52 [+] − [0] 0 [.] . [05] 07 0.35 100 0.131±0.002 0.285±0.003 1.03
A199 2.17±0.01 2.8±0.3 8±2 3.1±0.2 3.0±0.4 8±2 1.97±0.02 3.62 [+] − [0] 0 [.] . [06] 08 0.35 100 0.135±0.002 0.283±0.004 1.22
A201 2.14±0.01 =N(H) 3.1±0.3 =N(Al) =N(Al) =N(Al) 1.81±0.03 3.5±0.1 0.35 100 0.138±0.003 0.262±0.005 1.22
A206 2.20±0.02 =N(H) 3.1±0.4 =N(Al) =N(Al) =N(Al) 1.93±0.05 3.4±0.1 0.35 100 0.132±0.005 0.266±0.010 1.16
A208 2.21±0.02 =N(H) 3.1±0.3 =N(Al) =N(Al) =N(Al) 1.93±0.04 3.4±0.1 0.35 100 0.131±0.004 0.264±0.008 1.01
A209 2.19±0.02 =N(H) 3.3±0.3 =N(Al) =N(Al) =N(Al) 1.89±0.04 3.5±0.1 0.35 100 0.124±0.003 0.246±0.007 1.25
A210 2.21±0.02 =N(H) 3.0±0.4 =N(Al) =N(Al) =N(Al) 1.90±0.05 3.4±0.1 0.35 100 0.122±0.004 0.244±0.009 1.19
A211 2.21±0.01 =N(H) 3.0±0.2 =N(Al) =N(Al) =N(Al) 1.92±0.03 3.6±0.1 0.35 100 0.126±0.001 0.252±0.002 1.13
A212 2.21±0.02 =N(H) 2.9±0.4 =N(Al) =N(Al) =N(Al) 1.92±0.05 3.6 [+] − [0] 0 [.] . [1] 2 0.35 100 0.124±0.002 0.249±0.005 1.20
A213 2.21±0.02 =N(H) 3.4±0.3 =N(Al) =N(Al) =N(Al) 1.94±0.04 3.5 [+] − [0] 0 [.] . [1] 2 0.35 100 0.117±0.002 0.241±0.004 1.14
A214 2.21±0.02 =N(H) 3.0±0.3 =N(Al) =N(Al) =N(Al) 1.91 [+] − [0] 0 [.] . [05] 04 3.7 [+] − [0] 0 [.] . [1] 2 0.35 100 0.122±0.004 0.245±0.009 1.16


Article number, page 17 of 18

_A&A proofs:_ manuscript no. 39581corr


A215 2.21±0.01 =N(H) 2.9±0.2 =N(Al) =N(Al) =N(Al) 1.87±0.02 3.45 [+] − [0] 0 [.] . [05] 07 0.35 100 0.124±0.002 0.243±0.004 1.26
A216 2.19±0.02 =N(H) 2.9±0.3 =N(Al) =N(Al) =N(Al) 1.85±0.04 3.5±0.1 0.35 100 0.123±0.002 0.239±0.005 1.22
A217 2.21±0.02 =N(H) 2.6±0.3 =N(Al) =N(Al) =N(Al) 1.85±0.04 3.5 [+] − [0] 0 [.] . [1] 2 0.35 100 0.124±0.003 0.239±0.006 1.16
A218 2.20±0.02 =N(H) 3.0±0.3 =N(Al) =N(Al) =N(Al) 1.82±0.04 3.7±0.2 0.35 100 0.120±0.004 0.230±0.009 1.26
A220 2.22±0.02 =N(H) 3.1±0.3 =N(Al) =N(Al) =N(Al) 1.90±0.04 3.5 [+] − [0] 0 [.] . [1] 2 0.35 100 0.121±0.002 0.243±0.005 1.11
A221 2.21±0.02 =N(H) 2.6±0.4 =N(Al) =N(Al) =N(Al) 1.85±0.05 3.5 [+] − [0] 0 [.] . [1] 2 0.35 100 0.119±0.002 0.230±0.005 1.28
A222 2.23±0.02 =N(H) 2.7±0.4 =N(Al) =N(Al) =N(Al) 1.91±0.05 3.5 [+] − [0] 0 [.] . [1] 2 0.35 100 0.120±0.002 0.239±0.004 1.18


**Rebrightening phase**


_NICER_ N(H) N(Mg) N(Al) N(Si) N(S) N(Ca) Γ log ξ R f R in F abs F unabs χ [2] red
obs. 10 [22] atoms/cm [2] 10 [−][8] erg/s/cm [2] 10 [−][8] erg/s/cm [2]


B101 2.19±0.01 2.9±0.4 9±2 3.4±0.2 4.4±0.4 14±2 2.14±0.02 3.66 [+] − [0] 0 [.] . [07] 05 0.35 100 0.151±0.003 0.363±0.007 1.13
B201 2.15±0.02 3.5±0.4 7±3 3.4±0.2 4.4 − [+][0] 0 [.] . [6] 5 14±2 2.07 [+] − [0] 0 [.] . [04] 03 3.6±0.1 0.35 100 0.160±0.004 0.367±0.008 1.15
B301 2.19 [+] − [0] 0 [.] . [01] 02 3.1±0.4 11±2 3.4±0.2 4.8±0.4 14±2 2.16±0.02 3.67 [+] − [0] 0 [.] . [07] 05 0.35 100 0.172±0.004 0.422±0.009 1.42
B401 2.19±0.01 3.7±0.4 9 [+] − [2] 3 3.5 [+] − [0] 0 [.] . [1] 3 4.5 [+] − [0] 0 [.] . [3] 6 14±2 2.20 [+] − [0] 0 [.] . [01] 04 3.77 [+] − [0] 0 [.] . [05] 09 0.35 100 0.165±0.004 0.419±0.008 1.14
B501 2.15±0.03 4.1±0.9 16 [+] − [5] 6 3.2±0.4 6±1 19 [+] − [4] 5 2.15±0.06 3.7 [+] − [0] 0 [.] . [2] 1 0.35 100 0.148±0.008 0.370±0.017 1.01
B601 2.21±0.01 3.5±0.4 11±2 3.7±0.2 5.0±0.4 13±2 2.18±0.02 3.69 [+] − [0] 0 [.] . [07] 03 0.35 100 0.177±0.004 0.445±0.009 1.56
B701 2.21 [+] − [0] 0 [.] . [02] 01 3.6±0.4 14±2 3.6±0.1 5.2±0.3 14±2 2.20±0.01 3.71 [+] − [0] 0 [.] . [03] 05 0.35 100 0.164±0.003 0.423±0.008 1.21
B801 2.22±0.02 4.1±0.4 16±2 4.1±0.2 6.1±0.4 10±2 2.09±0.02 3.70 [+] − [0] 0 [.] . [08] 02 10 [+] − [0] 6.23 100 0.141±0.005 0.35±0.01 1.31
B901 2.29±0.02 4.2 − [+][0] 0 [.] . [5] 4 23±3 3.9±0.2 5.4 [+] − [0] 0 [.] . [4] 3 8±2 2.20±0.01 3.70±0.02 10 [+] − [0] 4.96 100 0.120±0.002 0.327±0.006 1.28


**Obscured phase**


_NICER_ N(H) N(Mg) N(Al) N(Si) N(S) N(Ca) Γ log ξ R f R in F abs F unabs χ [2] red
obs. 10 [22] atoms/cm [2] 10 [−][8] erg/s/cm [2] 10 [−][8] erg/s/cm [2]


C001 2.21±0.02 4.7±0.6 22±4 3.2±0.3 4.2±0.8 6±2 1.89 [+] − [0] 0 [.] . [03] 06 3.16 [+] − [0] 0 [.] . [03] 05 −2 1 0.072±0.002 0.161±0.005 1.49
C202 2.03±0.03 4.1 − [+][0] 0 [.] . [9] 8 27 [+] 5 [6] 3.7±0.3 5.9±0.9 =N(H) 1.44±0.03 2.80 [+] − [0] 0 [.] . [03] 05 −2 1 0.021±0.002 0.031±0.003 1.09
C203 2.08 [+] − [0] 0 [.] . [05] 07 8±2 37 [+] 9 [10] 5.5 [+] − [0] 0 [.] . [7] 6 10±2 =N(H) 1.64 [+] − [0] 0 [.] . [03] 04 2.44 [+] − [0] 0 [.] . [04] 06 −2 1 0.034±0.002 0.055±0.004 1.65
C204 2.23 [+] − [0] 0 [.] . [03] 04 5±1 30±5 3.1±0.3 5.0±0.8 =N(H) 1.69 [+] − [0] 0 [.] . [03] 04 2.74±0.01 −2 1 0.048±0.003 0.084±0.005 1.57
C205 2.18 [+] − [0] 0 [.] . [04] 05 4±1 16±7 2.2±0.4 2±1 =N(H) 1.53±0.06 2.80 [+] − [0] 0 [.] . [03] 05 −2 1 0.039±0.004 0.059±0.007 1.69
C206 2.13±0.05 7 [+] − [2] 1 29 [+] 9 [10] 3.4 [+] − [0] 0 [.] . [6] 5 6±2 =N(H) 1.64 [+] − [0] 0 [.] . [05] 06 2.73±0.02 −2 1 0.032±0.003 0.053±0.006 1.47
C207 2.09 [+] − [0] 0 [.] . [04] 06 3±1 25 [+] 8 [7] 1.7 [+] − [0] 0 [.] . [4] 6 =N(H) =N(H) 1.51 [+] − [0] 0 [.] . [05] 08 2.77 [+] − [0] 0 [.] . [03] 04 −2 1 0.016±0.002 0.024±0.003 1.54
C208 2.0±0.1 2±2 27±10 2.6±0.7 =N(H) =N(H) 1.20 [+] − [0] 0 [.] . [04] 01 2.82 [+] − [0] 0 [.] . [02] 03 −2 1 0.029±0.001 0.036±0.002 1.42
C209 2.13 [+] − [0] 0 [.] . [1] 3 5 [+] − [5] 4 14 [+] 24 [14] 3±2 =N(H) =N(H) 1.63±0.2 3.01 [+] − [0] 0 [.] . [2] 1 −2 1 0.011±0.003 0.019±0.007 1.28
C301 2.25±0.04 5±1 28±5 2.5±0.3 =N(H) =N(H) 1.63 [+] − [0] 0 [.] . [02] 03 2.82 [+] − [0] 0 [.] . [02] 03 −2 1 0.022±0.001 0.037±0.002 1.55
C302 1.8±0.1 =N(H) =N(H) =N(H) =N(H) =N(H) 1.20 [+] − [0] 0 [.] . [06] 01 3.01±0.01 −2 1 0.0062±0.0005 0.0078±0.0006 1.45
C303 2.0±0.1 =N(H) 19 [+] 18 [14] =N(H) =N(H) =N(H) 1.3±0.1 2.75 [+] − [0] 0 [.] . [02] 03 −2 1 0.010±0.002 0.012±0.002 1.16
C304 1.8 [+] − [0] 0 [.] . [1] 2 =N(H) =N(H) =N(H) =N(H) =N(H) 1.2 [+] − [0] 0 [.] . [2] 1 2.75 [+] − [0] 0 [.] . [04] 02 −2 1 0.009±0.002 0.011±0.003 1.33


Article number, page 18 of 18


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].redshift_or_distance.evidence[1]",
  "value": "7-10 kpc (8.6 kpc)",
  "failed_quote": "Alternatively, we can use the modeled asymptotic flux density of the exponential decay fitted to the light curve, f_2 = 0.7 × 10^-8 erg s^-1 cm^-2, which for the distance of 8.6 kpc"
 },
 {
  "path": "science.targets[0].distance_source.evidence[1]",
  "value": "Fender et al. 1999; Reid et al. 2014",
  "failed_quote": "Alternatively, we can use the modeled asymptotic flux density of the exponential decay fitted to the light curve, f_2 = 0.7 × 10^-8 erg s^-1 cm^-2, which for the distance of 8.6 kpc"
 },
 {
  "path": "data.other_facilities[2].provided.evidence[0]",
  "value": "Quasi-simultaneous archival 3-10 keV X-ray data from HEASARC corresponding to archival millimeter observations",
  "failed_quote": "The corresponding 3-10 keV X-ray fluxes were estimated using quasi-simultaneous archival RXTE data taken from HEASARC and reduced according to standard procedures."
 },
 {
  "path": "processing.calibration.pipeline_or_manual.evidence[0]",
  "value": "Scripted calibration using the calibration script provided with the data plus manual flagging",
  "failed_quote": "We performed the data reduction with the Common Astronomy Software Applications (CASA) package version 5.4.0-70 by running the calibration script provided with the data."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Run provided ALMA calibration script in CASA, apply manual channel and antenna flags for bad D-terms and gain/phase outliers, image the data, and fit a delta function to the uv-plane using uvmultifit to measure Stokes I, Q, U fluxes (full band, per spectral window, and per scan).",
  "failed_quote": "We performed the data reduction with the Common Astronomy Software Applications (CASA) package version 5.4.0-70 by running the calibration script provided with the data."
 },
 {
  "path": "analysis_steps[0].fitting.evidence[1]",
  "value": "uv-plane delta function fitting in uvmultifit 3.0.0 and power-law spectral index fitting (S_nu propto nu^alpha)",
  "failed_quote": "In both cases the spectra is flat with spectral indices α1 = −0.09 ± 0.05 and α2 = 0.11 ± 0.05 (S_ν ∝ ν^α), which are typical values for a self-absorbed synchrotron jet."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Combine ALMA Band 3 luminosities and NICER 3-10 keV luminosities with archival JCMT/NMA and RXTE data to fit the mm/X-ray correlation slope, and fit the NICER 1-10 keV light curve with an exponential-to-linear decay model.",
  "failed_quote": "Assuming the observed light-curve profile obeys the standard XRB outburst decay profile, we fit the NICER light curve with a model used in Powell et al. (2007), Heinke et al. (2015), and Tetarenko et al. (2018) corresponding to an exponential decay on a viscous timescale and a linear decay on an irradiation-controlled timescale."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[1]",
  "value": "Distance d = 8.6 kpc, black hole mass M = 12 M_sun, Eddington luminosity L_Edd = 1.5 x 10^39 erg s^-1, flat radio/mm spectrum",
  "failed_quote": "Alternatively, we can use the modeled asymptotic flux density of the exponential decay fitted to the light curve, f_2 = 0.7 × 10^−8 erg s^−1 cm^−2, which for the distance of 8.6 kpc and a standard radiative efficiency of η = 0.1 corresponds to ∼7×10^18 g s^−1"
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "ALMA data reduction, calibration, flagging, and imaging",
  "failed_quote": "We performed the data reduction with the Common Astronomy Software Applications (CASA) package version 5.4.0-70 by running the calibration script provided with the data."
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "ALMA Epoch 1 in-band spectral index (alpha_1) = -0.09 dimensionless",
  "failed_quote": "In both cases the spectra is flat with spectral indices α1 = −0.09 ± 0.05 and α2 = 0.11 ± 0.05 (S_ν ∝ ν^α), which are typical values for a self-absorbed synchrotron jet."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "ALMA Epoch 2 in-band spectral index (alpha_2) = 0.11 dimensionless",
  "failed_quote": "In both cases the spectra is flat with spectral indices α1 = −0.09 ± 0.05 and α2 = 0.11 ± 0.05 (S_ν ∝ ν^α), which are typical values for a self-absorbed synchrotron jet."
 },
 {
  "path": "findings_qualitative[3].evidence[1]",
  "value": "In the obscured phase, highly ionized iron absorption lines transition to emission lines, QPOs vanish leaving pure power-law red noise, and up to ~80% of the intrinsic 1-10 keV flux is absorbed or scattered.",
  "failed_quote": "The observations presenting the lowest fluxes during the obscured phase show a similar trend with the linear decay, but with 0.045×10^−8 erg s^−1 cm^−2 of flux removed, meaning that at most approximately 80% of the intrinsic flux density is absorbed and/or scattered in the 1–10 keV band."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "GRS 1915+105 changed from a higher radio/X-ray correlation index to a lower one (L_radio propto L_X^0.6), reinforcing its transition to a canonical low-luminosity hard state.",
  "failed_quote": "Relating the mm emission to the X-ray emission reveals that the source has changed from a higher radio/X-ray correlation index to a lower one; L_radio ∝ L_X^0.6."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[0]",
  "value": "Heavy obscuration in the obscured state makes the intrinsic X-ray luminosity difficult to estimate accurately.",
  "failed_quote": "However, due to the heavily modified X-ray spectra by the obscuring material, the intrinsic X-ray luminosity is difficult to estimate accurately with values ranging from 1% (Koljonen & Tomsick 2020; Miller et al. 2020) to 10% (Balakrishnan et al. 2020; Neilsen et al. 2020) and possibly reaching 100% of the Eddington ratio occasionally (Balakrishnan et al. 2020)."
 }
]
```
