# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...971...52M\sonnetcc\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Multiwavelength Observations of Sgr A\*. II. 2019 July 21 and 26

## Abstract

We report on the final two days of a multiwavelength campaign of Sgr A\* observing in the radio, submillimeter, infrared, and X-ray bands in July 2019. Sgr A\* was remarkably active, showing multiple flaring events across the electromagnetic spectrum. We detect a transient $\sim35$-minute periodicity feature in *Spitzer* light curves on 21 July 2019. Time-delayed emission was detected in ALMA light curves, suggesting a hotspot within the accretion flow on a stable orbit. On the same night, we observe a decreased flux in the submillimeter light curve following an X-ray flare detected by *Chandra* and model the feature with an adiabatically expanding synchrotron hotspot occulting the accretion flow. The event is produced by a plasma $0.55~R_{\text{S}}$ in radius with an electron spectrum $p=2.84$. It is threaded by a $\sim130$ Gauss magnetic field and expands at $0.6\%$ the speed of light. Finally, we reveal an unambiguous flare in the infrared, submillimeter, and radio, demonstrating that the variable emission is intrinsically linked. We jointly fit the radio and submillimeter light curves using an adiabatically expanding synchrotron hotspot and find it is produced by a plasma with an electron spectrum $p=0.59$, $187$ Gauss magnetic field, and radius $0.47~R_{\text{S}}$ that expands at $0.029c$. In both cases, the uncertainty in the appropriate lower and upper electron energy bounds may inflate the derived equipartition field strengths by a factor of 2 or more. Our results confirm that both synchrotron- and adiabatic-cooling processes are involved in the variable emission’s evolution at submillimeter and infrared wavelengths.

# Introduction

The Milky Way Galaxy hosts Sagittarius A\* (Sgr A\*), a $4.152\times10^{6}~\text{M}_\odot$ supermassive black hole, at its center. At a distance of $8178$ pc (cite: Boehle2016; Gravity2019), it is one of only two black holes whose angular extent is large enough to be directly imaged by Earth-sized very long baseline interferometry (VLBI) experiments like the Event Horizon Telescope (cite: EHT2022a). One complication in imaging its near-event-horizon-scale features is its variability. Sgr A\* has a gravitational timescale $t_g = r_{g}/c = GM/c^3\sim20$ seconds, and the Keplerian orbital period at the innermost stable circular orbit (ISCO) is $\sim30$ minutes if Sgr A\* does not spin (cite: Gravity2018), making it variable over a short duration. Imaging near-event-horizon features requires observations many times longer than these variability timescales, which corrupts the visibilities produced by intrinsic structures and smears them in the final image. Statistical attempts have been used to mitigate some of its variable nature and create a best-fit event-horizon-scale image (cite: Broderick2022). However, understanding the cause of the variability will ultimately benefit future imaging attempts of this source.

Sgr A\*’s variability has been observed in the radio (cite: Lu2011; FYZ2011; Brinkerink2015), submillimeter/millimeter (cite: Dexter2014; Subroweit2017; Iwata2020), infrared (cite: Hora2014; Witzel2018), and X-rays (cite: Baganoff2001; Markoff2001; Neilsen2015; Ponti2015; Yuan2016). Large-amplitude hourly timescale variability, which we denote “flares,” occurs roughly once to a few times per day. At radio and (sub)mm, these flares appear in addition to slowly varying “quiescent”-like emission from an accretion flow near the event horizon. At radio frequencies, this emission is optically thick. Toward submm frequencies, its optical depth decreases, and the emission is either marginally optically thick or optically thin at 230 GHz and optically thin at 345 GHz (cite: Bower2019). (cite: Wielgus2022a) suggest that the submm quiescent emission at 230 GHz and higher is optically thin, but there may be regions within it that have higher-than-average optical depth. The causes of the flares and the slowly varying quiescent emission are unknown; multiwavelength observations are crucial to unraveling this mystery.

Coordinated multiwavelength observations have led to insights into the flaring emission. The time of the peak flaring emission at lower frequencies is delayed relative to those at high frequencies. Between radio and submm, the time delays are on the order of tens of minutes to an hour (cite: Brinkerink2015; Mossoux2017; Michail2021c). Similar lags have been discovered across a single radio frequency band using the NSF’s Karl G. Jansky Very Large Array (cite: Brinkerink2021; Michail2021b). At IR, the emission has been observed to lead or simultaneously occur with submm (cite: YusefZadeh2006a; Fazio2018). The appearance or lack of delays depends on the observing frequency (i.e., 230 vs. 345 GHz) and the emission’s physical properties.

There is a curious connection between flares in the IR and X-rays. First, every X-ray flare has an IR counterpart, but the opposite is not true (cite: DoddsEden2009). These “missing” flares may be caused by limited observational sensitivity in the X-rays, as there is large-scale quiescent X-ray emission near Sgr A\*. The missing X-ray flares may not be sufficiently bright to overcome this large-scale emission, leaving only the strongest flares to be observed. Second, the time delay between IR and X-ray light curves has not been well-established. (cite: Boyce2019) suggested the X-ray might lead the IR by 10-20 minutes after analyzing more than 100 hours of coordinated IR and X-ray monitoring. This ensemble-average value is only significant at a 68% confidence interval. The authors conclude additional data are required to constrain the correlation.

One model that attempts to explain the connection between IR, submm, and radio flaring is the adiabatically-expanding synchrotron hotspot model (cite: VDL1966; FYZ2006). It describes the time- and frequency-dependent evolution of an initially optically-thick synchrotron-emitting plasma as it expands. The time delay naturally explains the dynamic expansion as the emission transitions from optically thick to thin. This picture predicts unique continuum and polarimetric light curves, which depend on properties such as the embedded magnetic field, electron spectrum, and expansion speed. In a series of earlier papers, we explored the multiwavelength and polarimetric nature of these hotspots. (cite: Michail2023) tested this picture using a full-radiative transfer prescription to model 235 GHz full-polarization light curves of a detected flare from ALMA. For the first time, we constrained the three-dimensional orientation of the embedded magnetic field. In (cite: Michail2021c), we used this picture to connect the IR and submm variability and predict the resulting radio emission.

In July 2019, we participated in organizing a ground- and space-based campaign to simultaneously monitor Sgr A\* from radio to X-ray energies. Several papers have analyzed these data but do not focus on the complementary radio and Hubble Space Telescope (HST) observations. (cite: Abuter2021) analyzed a remarkable flare on 18 July 2019, which occurred only a few months after the brightest-ever IR flare with a dereddened $2.15~\mu$m peak flux of $\sim60$ mJy (cite: Do2019). Using IR (*Spitzer* *Space Telescope* and GRAVITY) and X-ray (*Chandra* *X-ray Observatory* and NuSTAR) observations, they show its mean and time-resolved spectral energy distributions are consistent with synchrotron self-Compton or a pure synchrotron spectrum with a cooling break. The synchrotron self-Compton model was unable to reproduce any significant submm emission (first reported in ), while the latter produced submm emission at levels consistent with the historic average. However, properties of this model, such as higher-than-inferred electron densities in the accretion flow, were drawbacks. (cite: Boyce2022) reported the remaining two days of ALMA, *Spitzer*, and *Chandra* light curves from the July 2019 campaign and remodeled the first day’s results to include the ALMA data using an adiabatically-expanding source region. Their models rejected the optically-thin case reported in where both the submm and IR flares were produced by a single synchrotron component, as the IR spectral index was not consistent with the observations and could not reproduce the X-ray emission using synchrotron self-Compton. The emission was consistent with an adiabatically-expanding model such that the IR and X-ray emission were both produced by synchrotron self-Compton processes and the submm was produced by synchrotron only. However, such a model predicted similarly high electron densities ($n_e\sim10^{9-10}$ cm$^{-3}$) like those modeled by (cite: Abuter2021).

(cite: Boyce2022) focused only on modeling multiwavelength features on the first day of observation and did not include contemporaneous HST (IR) and VLA (radio) observations during this campaign. Here, we present the remaining two days of monitoring with all participating observatories. We discuss data reduction and calibration for each instrument in Section [2](#sec:data). In Section [3](#sec:analysis), we present the time delay analysis between each pair of instruments and the periodogram analysis of the IR data. In Section [5](#sec:discussion), we use the adiabatic-expansion picture (described in Section [4](#sec:models)) to model the detected features and summarize our conclusions in Section [6](#sec:conclusions). Our adopted mass of Sgr A\* throughout this paper corresponds to a Schwarzschild radius $R_{\text{S}} = 1.23\times10^{12}$ cm.

# Observations and Data Reduction

Here, we describe the observing details and calibration procedures for the data used in this analysis. explained the techniques in greater detail for the ALMA, *Spitzer*, and *Chandra* data; we give summaries for these instruments below. We present detailed explanations for the VLA and HST data.

## Radio: Very Large Array

The VLA observed Sgr A\* on three days: 18 July 2019 (Project ID: 19A-490, PI: Yusef-Zadeh), 21 July 2019, and 26 July 2019 (Project ID: 19A-229, PI: Yusef-Zadeh). Observations on 18 July 2019 were completed in the hybrid BnA array at Q-band (43 GHz). On the 21st and 26th, the VLA was in the A configuration and used the Q and Ka (35 GHz) bands, respectively. The 3-bit correlator was used to observe over 8 GHz bandwidth and is composed of 63 intermediate frequencies (IFs), each with a bandwidth of 128 MHz. Every IF is subdivided into 64 2-MHz wide channels recording full-polarization products.

Observations on 18 and 21 July were not successfully completed owing to several compounding issues. The cycle times between Sgr A\* and the phase calibrator were lengthier than required in the most extended configurations ($\sim20$ minutes used versus the recommended $\sim2$ minutes). Additionally, the pointing calibrations were not completed often enough for high-frequency observing, nominally at a cadence of $45-60$ minutes. Finally, strong winds above the specifications for Q-band observing occurred during these two nights. Despite our best efforts, these data were not salvageable to extract light curves. While the 26 July observations were set up similarly, better weather conditions and the wider primary beam at Ka-band reduced many of the pointing issues. Therefore, we only make use of the Ka-band observations in this analysis.

The two nights of observations follow the same procedure with three calibrators and Sgr A\*. 3C286 is the flux and polarization angle calibrator. J1733-1304 is the bandpass, secondary complex gain, and primary instrumental polarization calibrator, while J1744-3116 (hitherto denoted J1744) is the primary complex gain and secondary instrumental polarization calibrator. Scans of Sgr A\* were interleaved with J1744, and J1733-1304 was observed approximately every hour. The data were reduced in `CASA` (cite: McMullin2007) with the default VLA pipeline. To calibrate the polarization products, we follow the appropriate polarization calibration guide[^1]. The polarization-calibrated visibilities were exported from `CASA` and imported into `AIPS` for additional baseline-based flagging and point-source phase self-calibration. We extract light curves for Sgr A\* and J1744 using `DFTPL` on projected baselines $\geq100~\text{k}\lambda$ at 60-second intervals for each IF. `DFTPL` averages the real portion of the visibilities at the phase center to determine light curves without the need for other (e.g., imaging-based) techniques. The 26 July 2019 light curves at Ka-band are shown in Figure [1](#fig:vla_lcs).

![](VLA.pdf)

![](ALMA_Day2_3_Combined.pdf)

## Submillimeter: ALMA

Three nights of ALMA observations were taken as part of the ALMA Compact Array (ACA) Cycle 6 filler program 2018.A.00050.T in band 7 ($\sim330$ GHz) with projected baselines ranging from $10-55~\text{k}\lambda$. We use the `scriptForPI.py` code to restore the calibrated data from the automatic ALMA pipeline in `CASA` version 5.4.0-70 (Pipeline-CASA54-P1-B, r42254). Four IFs with 2 GHz of bandwidth each were composed of 1024 1.953-MHz channels recording dual polarization products. One IF is centered on the $\approx346$ GHz CO(3-2, v=0) transition. J1337-1257 and J1924-2914 are the bandpass and amplitude calibrators; J1700-2610 (J1700) and J1717-3342 are the phase calibrators for each observation. Like the VLA data, we phase self-calibrated Sgr A\* and J1700, assuming each was a point source to mitigate residual baseline-based phase errors. Finally, we import the data into `AIPS` and use `DFTPL` to extract the light curves with a $1$ minute binning time on baselines $\geq20~\text{k}\lambda$. We chose this limit after viewing the visibility amplitude as a function of projected baseline distance, finding that sizes below this threshold are dominated by the extended emission from the Circumnuclear Disk.

We take additional steps to post-process the light curves. We discarded the last execution block on 21 July 2019 due to amplitude-decorrelation on several antennas caused by the low altitude of our calibrators. The calculated flux of the phase calibrator changed (on the order of a few percent) between execution blocks. We follow to correct this by using the first block as our reference. The phase calibrator’s average flux in subsequent execution blocks was used to calculate multiplicative correction factors. These scale factors are applied to the phase calibrator and Sgr A\*. We show the final ALMA light curves in Figure [2](#fig:alma_lcs).

![](Hubble_Day2_3_Combined.pdf)

## Near-infrared: Hubble Space Telescope

We obtained near-IR observations of Sgr A\* with the HST Wide Field Camera 3 (WFC3) under program 15667 () over two different visits occurring on 21 July (2 orbits) and 26 July (6 orbits). During each visit, Sgr A\* was visible to HST at 40–50 minute intervals per orbit. We give a brief explanation of the data calibration here and refer to (cite: Mossoux2016) for further details.

WFC3 observations were taken with the F153M filter with an effective wavelength of $\lambda_\mathrm{eff}=1.532\ \mu$m taken in continuous accumulation mode. The instantaneous field-of-view is approximately $2\ensuremath{'}{}26$ per side with a pixel size of $\sim0\ensuremath{''}{}13$. The accumulation mode reads out the WFC3 detector every 25 seconds during a total exposure time of 275 seconds. HST was dithered around Sgr A\*’s location to improve WFC3’s point spread function. We calibrate the data with the default STScI `calwf3` calibration pipeline. We corrected the astrometry of each exposure using the radio location of the nearby IRS-16C source. We used the `photutils` package of `astropy` to complete aperture photometry of Sgr A\* using a circular aperture of 4 pixels in diameter centered on this source’s known radio location at 25-second intervals (the cadence of WFC3’s readout mode).

In our initial analysis, the photometry of other stars in the field in each exposure declined by $\sim3\%$, affecting the final light curve of Sgr A\*. Assuming stars near Sgr A\* did not change over a single exposure, we corrected this effect and applied them to Sgr A\*’s light curve. We revalidated the light curves for each star and found that they were constant over each exposure. Finally, we applied an aperture correction using several apertures at different sizes by calculating the curve of growth for isolated stars and applying it to Sgr A\*’s final light curve.

Using a reference star, we estimate a noise level of 0.004 mJy per exposure. We deredden the measured fluxes with the prescription in (cite: Fritz2011). The extinction in the near-IR band is modeled by: $$\begin{equation}
                \text{A}_{\lambda} = 2.62\left(\dfrac{\lambda}{2.166~\ensuremath{\mu}m}\right)^{-2.11}.
            
\end{equation}$$ For $1.53$ $\mu$m, $\text{A}_{1.53~\mu\text{m}} = 5.46$ mag, giving a flux correction factor of $f_{1.53~\mu\text{m}} = 2.512^{5.46} = 152.8$. We show the dereddened photometry for Sgr A\* and the background aperture in Figure [3](#fig:hubble_lcs).

## Mid-infrared: Spitzer Space Telescope

The *Spitzer* observations and calibration were outlined in (cite: Hora2014) and (cite: Witzel2018), while a more detailed explanation of these data was given in (cite: Abuter2021). Three observations of Sgr A\* lasting approximately 16 hours each were taken as part of program ID 14026. In contrast to previous *Spitzer* analyses, we bin the data into 1- and 5-minute averages to obtain higher signal-to-noise light curves by averaging all fluxes within one-half bin width. We converted the barycentric UT timestamps into UTC using an online tool[^2] (cite: Eastman2010). (cite: Fritz2011) listed a $4.5~\ensuremath{\mu}m$ extinction of $1.06$ mag toward the Galactic Center. Therefore, we scale the *Spitzer* light curves by $2.512^{1.06}=2.65$ to deredden the light curves. (cite: Boyce2022) denoted low signal-to-noise-ratio periods in their analysis of these *Spitzer* data, which we incorporate here. The light curves for 21 July 2019 and 26 July 2019 are shown in Figure [4](#fig:spitzer_lcs).

![](Spitzer_Day2_3_Combined.pdf)

## X-ray: Chandra X-Ray Observatory

Three days of simultaneous *Chandra* and *Spitzer* observations were completed on 18, 21, and 26 July 2019. For 21 July 2019 and 26 July 2019, the observation IDs are 20446 and 20447 (PI: Fazio), respectively. Each night’s observation lasted 52 ks in FAINT mode with Sgr A\* centered on the ACIS S3 chip in the 1/8 subarray setting. We reprocessed the data with CIAO version 4.13 and CALDB version 4.9.4. We refine the astrometric accuracy using `wcs_match` and `wcs_update` with three nearby Galactic Center sources from the Chandra Source Catalog (cite: Evans2010).

Following (cite: Capellupo2017), we determine background-subtracted light curves of Sgr A\* by placing a $1.25\ensuremath{''}$ radius aperture at the radio location of Sgr A\* ($17^\text{h}~45^\text{m}~40.04s, -29^\circ~00\ensuremath{'}~28.18\ensuremath{''}$). Our background aperture is centered on $17^\text{h}~45^\text{m}~40.30s, -28\ensuremath{^\circ}~59\ensuremath{'}~52.66\ensuremath{''}$ with a $10.0\ensuremath{''}$ radius. This background aperture contains no known or obvious sources . To minimize photons from the diffuse X-ray background, we only use events within the $2-8$ keV range (cite: Neilsen2013). We used `dmextract` to obtain the light curves of Sgr A\* at a 5-minute binning time and ran the open-source Bayesian block algorithm, `bblocks`[^3], on the light curves (cite: Scargle1998; Scargle2013; BBlocks) with a false positive rate of $p_0=0.05$. The Bayesian blocks method accounts for counting noise in Poissonian-like systems, where the change in count rate must be statistically significant at a level of $1-p_0$. Since every flare requires two changes (cite: Nowak2012), this ensures a flare is significant at a confidence of $1-p_0^2 = 99.75\%$. We show the *Chandra* light curves and the Bayesian block results in Figure [5](#fig:chandra_lcs).

![](Chandra_Day2_3_Combined.pdf)

# Analysis

## 21 July 2019

![](Day2_XCorr_LCs_Combined.pdf)

Sgr A\* was remarkably active on 21 July 2019 in the submm, IR, and X-ray. The Bayesian blocks algorithm (Figure [5](#fig:chandra_lcs)a) detected an increased quiescent plateau and flare in the X-ray light curves, which then decays to a count rate consistent with (cite: Neilsen2015). To detect flaring events in the HST data, we use a root-mean-square-based (RMS-based) calculation. For each orbit, we calculate the RMS flux of Sgr A\* and the background RMS error (RMSE) to quantify the intrinsic scatter in the data. Then, we determine the z-score for each associated flux and error measurement using Sgr A\*’s average flux and the background RMSE in the given orbit. We define a flare-like event when the z-score is $\geq5\sigma$ (the typical HST RMSE per orbit is $\sigma\sim0.2$ mJy). For 21 July 2019, we do not detect any flares in the $1.53$ $\mu$m data. Therefore, we only focus on the ALMA, *Spitzer*, and *Chandra* light curves.

In Figure [6](#fig:july21_xcorr), we show cross-correlations histograms between different pairs of the data (panels a-c) and a subset of these three light curves during the ALMA observations (panel d). We detect several corresponding features that occur in both the *Spitzer* and ALMA light curves following a single X-ray flare. The lack of *Spitzer* data at the peak of the X-ray emission is due to low-SNR data (gray band), so we are unable to definitively conclude if there is an IR flare. Multiwavelength campaigns have shown X-ray flares always appear paired to an IR peak (cite: DE2010). Therefore, we assume a weak IR flare occurs but is not detected.

### Cross Correlations

We complete cross-correlation analyses to check for time-delayed emission using `pyCCF` (cite: Peterson1998; PYCCF). For all cross-correlations in this paper, we use 5000 Monte Carlo realizations that remove a random number of light curve points each time and build a time delay histogram between two light curves. We report the mean delay value and the $95\%$ ($2\sigma$) confidence interval. We consider that the light curves are delayed if zero is not contained within the 95% interval.

We show the three cross-correlation histograms for 21 July in Figure [6](#fig:july21_xcorr)a-c. We report no statistically significant time delay across the ALMA bandwidth ($\sim14$ GHz). (cite: Iwata2020) and (cite: Wielgus2022a) suggest the presence of a small (but detectable) time delay across their lower frequency 230 GHz bandwidth. Using Equation 2 and the values listed in (cite: Iwata2020), we calculate an expected time delay across the 345 GHz ALMA band on the order of $\sim30$ seconds, assuming a range of electron indices ($p$) between $1-3$. Since we average the light curve in 60-second increments, any time delays shorter than this will be washed out.

Cross correlations are sensitive to peaks in emission (i.e., when the correlation coefficient is near $1$) instead of a peak and trough (i.e., when the correlation coefficient is near $-1$). We invert the ALMA light curve before completing the cross-correlation between the submm and X-ray light curves to determine the time delay between the X-ray flare peak and the $\sim0.7$ Jy drop in submm flux. We find the X-ray data lead the submm light curves by approximately $26$ minutes. We mark the X-ray peak flare time with a black dashed line in Figure [6](#fig:july21_xcorr)d to clearly show this detected delay. Such a feature has been detected previously several times (cite: Marrone2008; Meyer2008; FYZ2008; Capellupo2017) and will be further discussed in Section [5.1.2](#ssec:occultation).

Finally, we complete the cross-correlation between the ALMA and *Spitzer* light curves (Figure [6](#fig:july21_xcorr)b); the time delay histogram shows a much different structure than in the other two pairs of light curves. We find three groups of time delay peaks (centered near $\pm35$ and $0$ minutes). The majority of the 5000 realizations prefer the positive time delay where the IR leads the submm. The negative time delay peak (where the submm leads the IR) appears because `pyCCF` is model-agnostic and corresponds to the third IR peak corresponding to the first observed one in the submm. For our analysis, it has no physical meaning.

Due to the lack of ALMA data near 3.5 hr UTC, we cannot rule out the possibility of simultaneity. To determine if peaks in the submm and IR are simultaneous, we follow in using a Gaussian process regression to interpolate the ALMA data between execution blocks. We use the Gaussian process toolkit, part of the `sklearn` Python package, and choose a compound constant + radial-basis kernel. In Figure [7](#fig:alma_spitzer_gp)a,b, we show the Gaussian process-regressed ALMA and *Spitzer* data. The purple band denotes the 95% confidence interval of the Gaussian process fit, and the black marks the mean fit. The red points are the original (non-interpolated) data. We again use `pyCCF` to search for time lags between the interpolated ALMA and *Spitzer*  data; the cross-correlation histogram is shown in Figure [7](#fig:alma_spitzer_gp)c. We utilize the 68% ($1\sigma$) confidence interval as the interpolated data error inputs to `pyCCF` instead of the 95% interval for consistency with Figure [6](#fig:july21_xcorr). From this interpolated analysis, we find the IR data slightly lead the submm peaks by $4.66^{+2.56}_{-2.61}$ minutes and suggests the presence of an ALMA flare near 3.5 hr UTC occurring between execution blocks.

![](Spitzer_ALMA_GP.pdf)

### Periodograms

![](FFT_3_Days.png)

We now focus on the repeating flares present in the mid-IR and submm light curves. The initial cross-correlation results (Figure [6](#fig:july21_xcorr)) between these two wavelengths suggest periodic emission occurring every $\approx40$ minutes. The *Spitzer* data were binned on equal intervals of 1 minute, so we use `numpy` fast Fourier transforms (FFT) to detect evidence for transient periodicity. However, these algorithms have neither error-weighting or significance-testing built in. We discuss the approach to each of these topics below.

To account for the photometric scatter in *Spitzer*’s light curve, we complete a Monte Carlo process to “error weight” the power spectra. To do this, we randomly resample each of the observed points within their (normally distributed) flux uncertainties and redo the FFT on the “new” light curve. Completing this process 35,000 times allows us to probe a probability of $\sim1/35000 \approx4\sigma$; we report the mean and $1\sigma$ CI power spectra as the error-weighted power spectrum.

To determine if any peaks in the power spectrum are significant, we follow the prescription in (cite: Do2009) to compare the measured FFT to a red-noise-dominated power spectrum. We generate 35,000 red-noise light curves (using the `stochastic`[^4] Python package) with a spectral density exponent $\alpha=2.75$ (cite: Weldon2023). These red-noise light curves have the same temporal sampling as our light curves. We scale each of the generated light curves to have the same mean and standard deviation as the Sgr A\* light curve. To account for measurement noise in the light curve, we re-sample each “flux” point with the corresponding uncertainty in the *Spitzer* data. Finally, we calculate the power spectra for each generated light curve and report the $3\sigma$ and $4\sigma$ upper limits on the power. We consider a statistically significant detection in the periodogram when Sgr A\*’s mean spectral power is greater than the $4\sigma$ red-noise spectrum. In Figure [8](#fig:alldata_lomb_scargles), we show the power spectra for Sgr A\* during all three days using all data (outside of the low-SNR ranges) compared to the generated red noise light curves.

On 21 July 2019, we find a significant peak at a $\sim35$ minute period with a similar (but weaker) peak at $\sim40$ minutes on 18 July 2019. These timescales are similar to *Spitzer*’s quasi-periodic pointing wobble with a period of $\sim40$ minutes, which would cause photometric amplitude variations of a couple of percent for a point source (cite: Grillmair2012; Grillmair2014). This effect was present for earlier observations of Sgr A\* but was largely corrected, mitigating the resulting photometric response. Figures 8 and 2 in (cite: Hora2014) show the photometric changes caused by the wobble and the light curve of Sgr A\* after correction, respectively.

There are several key reasons why we trust the validity of this transient periodicity. First, the statistically significant signal only occurs in one of the three days, specifically on the same observation where an identical peaked structure is observed in the ALMA light curves. Second, a more comprehensive catalog of *Spitzer* light curves was published in (cite: Witzel2021), where no quasi-periodicity was detected. A wobble with a sustained period would have been detected in their analysis at higher significance since they used *Spitzer* data beginning in late 2013. Additionally, near the end of *Spitzer*’s mission, the heating duty cycle was changed because it was in a different thermal state where temperature cycling did not occur, rendering this pointing wobble absent. Finally, in the absence the FFT results, the cross correlation plots between ALMA and *Spitzer* (Figure [6](#fig:july21_xcorr)b) and their light curves (Figures [6](#fig:july21_xcorr)d and [7](#fig:alma_spitzer_gp)a,b) still show a similar $35$ minute timescale. Therefore, the sequential peaks observed in *Spitzer* on the 21st may be suggestive of several explanations, such as footprints of flux tubes within the accretion flow (cite: Porth2021) or short-lived, orbiting, transient hotspot within the accretion flow. We discuss the latter model further in Section [5.1.1](#ssec:trans_period).

## 26 July 2019

![](Day3_XCorr_LCs_Combined.pdf)

We use the same RMSE-based analysis in Section [3.1](#ssec:july21) to detect flares in the HST data on this day (Figure [3](#fig:hubble_lcs)b). Aside from two points ($t\approx 11.95, 14.5$ UTC hrs), the variations in the 1.53 $\mu$m light curves are within $5\sigma$ RMSE of the mean flux during each orbit. These data points are below the mean and do not correspond to variations in the *Spitzer* light curves. Therefore, we find no evidence for flaring events at $1.53$ $\mu$m. These non-detections allow us to place an upper limit on the IR flare spectral index using *Spitzer* and HST. Orbits 5 and 6 on this day (Figure [3](#fig:hubble_lcs)b) overlap with moderately weak *Spitzer* flares of $\sim5$ mJy at 4.5 $\mu$m. The upper limits of $1$ mJy from HST (i.e., $\sim5\times$RMSE per orbit) imply a spectral index of $\alpha\lesssim-1.5$ between 1.53 and 4.5 $\mu$m. This value is steeper than the canonical $\alpha=-0.7$ found between 1.6 and 2.2 $\mu$m (cite: Bremer2011), but comparable to the spectral index between 1.6 and 4.5 $\mu$m at the beginning of the bright flare observed on 18 July 2019 (cite: Abuter2021).

We detect no X-ray flaring events in the 2-8 keV energy range from the Bayesian blocks analysis (Figure [5](#fig:chandra_lcs)b). To check for lower significance flares, we test values of $p_0\in\left[0.05, 0.95\right]$ in increments of $0.05$; however, none were detected. This places an upper limit of $1.45$ flares day$^{-1}$ and matches recent published ranges (cite: Neilsen2013; Ponti2015; Yuan2016; Mossoux2017; Bouffard2019).

The *Spitzer* light curves show a great deal of variability, particularly during the latter half of the observation (Figure [4](#fig:spitzer_lcs)b). However, since the radio and submm light curves occur during the first half, we do not focus on these later variations. A flare event in the radio and submm is clearly present (Figures [1](#fig:vla_lcs) and [2](#fig:alma_lcs)b, respectively).

### Cross Correlations

We again use `pyCCF` to check for time-delayed emission in four different frequency pairs: radio-radio, radio-submm, submm-submm, and submm-mid-IR. The histograms for the cross-correlations are shown in Figure [9](#fig:july26_xcorr)a-d. We do not find evidence for a time delay across the radio and submm frequency bandwidths. However, the lowest frequency radio emission lags $\delta t=22.45^{+3.92}_{-4.16}$ minutes behind the highest frequency submm light curve. We further find the submm peak delayed $\delta t=9.02^{+4.98}_{-5.82}$ minutes behind the mid-IR peak. In Figure [9](#fig:july26_xcorr)e, we present the stacked mid-IR, submm, and radio light curves, which clearly show the time delay evolution of the flare.

We examined the lack of time delay across the ALMA bandwidth in Section [3.1.1](#sssec:21jul_cc). However, using the values in (cite: Iwata2020) would suggest a $\sim9$ minute time delay across the VLA bandwidth, which we do not detect (Figure [9](#fig:july26_xcorr)a), but should be measurable. Time delays across a single VLA band have been previously detected, such as the 20-minute lag between 8 and 10 GHz found by (cite: Michail2021b). Recalculating the expected time delay using Equation 2 from (cite: Iwata2020) with the measured 22.5-minute lag between 31.45 GHz and 347.87 GHz (Figure [9](#fig:july26_xcorr)b) yields a theoretical $\sim3$ minute delay across the VLA bandwidth (assuming $p$ ranges from $1-3$). We argue that the absent radio time delay is caused by observational effects in the VLA data rather than a breakdown in the adiabatically-expanding hotspot picture. In Section [2.1](#ssec:vla), we note the numerous weather- and setup-related issues that plagued the VLA observations; these will tend to increase the scatter (noise) in the light curves. Since a 3-minute time delay relies on only three points per light curve (60-second averaging), this, compounded with the increased scatter, restricts our ability to detect delayed emission. The $2\sigma$ scatter of the VLA’s cross correlation histogram (Figure [9](#fig:july26_xcorr)a) matches the expected 3-minute delay, implying the lag may be hidden in the noise.

### Additional Light Curve Features

We note the presence of two additional features (marked with gray dash-dotted lines in Figure [9](#fig:july26_xcorr)e) in the multiwavelength light curves aside from the prominent flare in Figure [9](#fig:july26_xcorr). Near $4.1$ hr UTC, an IR flare occurs, coincident with a slight ($\sim100$ mJy) increase in the submm flux but a drop ($\sim50$ mJy) in the radio flux. It is unclear if the radio feature indicates an occultation-like event (where the flare hides a portion of the accretion flow as seen from the Earth) or an issue with the amplitude scaling between observing blocks.

A tertiary feature appears in the radio light curve near $7.25$ hr UTC, coincident with an increase in the IR. It is unclear if this is another occultation-like event or the beginning of an additional flare. The lack of submm coverage, the proximity of the IR feature to the beginning of a low-SNR part of the light curve (gray band), and not observing the radio peak all blur its final classification. Because of these issues, we do not further consider this feature in our discussion.

# Models of Observed Events in the Light Curves

In this Section, we aim to model the submm flux decrease event observed on 21 July 2019 (Figure [6](#fig:july21_xcorr)) and the time-delayed flare detected in the IR, submm, and radio regimes on 26 July 2019 (Figure [9](#fig:july26_xcorr)). While several interpretations aim to describe the anti-correlation between submm and IR/X-ray light curves, we will focus on the occultation model. Throughout the descriptions below, we assume that Sgr A\* is comprised of two components, namely the variable and background (quiescent) emission. The variable component generates the flares, while the quiescent component is responsible for the non-zero flux offset and low-amplitude, long-timescale variability.

![](Occultation_Figure.pdf)

## Occultation of the Accretion Flow by Adiabatically-Expanding Synchrotron Hotspots

In Figure [6](#fig:july21_xcorr), we document another instance of decreasing submm flux during an IR or X-ray flare. (cite: FYZ2010) models this anti-correlation as a geometric occultation of Sgr A\*’s accretion disk by a flare that is optically thick in the submm. The flaring region is in front of the accretion disk seen from the Earth, eclipsing a fraction of its projected area on the sky, causing a dip in the submm light curve. The general setup for this model is depicted in the top panel of Figure [10](#fig:occultation_diagram). The initial description of the model only accounted for a specific electron power-law index; here, we generalize their model for all values.

### Hotspot Equations

We assume the flare is produced by self-absorbed synchrotron emission from an electron spectrum $n(E)~dE\propto E^{-p}~dE$. We further assume the hotspot is a homogeneous sphere with an initial radius $R$ and contains an initial magnetic field strength $B$. For a power-law electron spectrum, the synchrotron source function, $J_\nu$, is $$\begin{align}
                    J_\nu = \dfrac{\sqrt{2}}{(p+1)} \frac{\Gamma\left(\frac{3p-1}{12}\right)\Gamma\left(\frac{3p+19}{12}\right)}{\Gamma\left(\frac{3p+2}{12}\right)\Gamma\left(\frac{3p+22}{12}\right)}\dfrac{\nu^2}{c^2}E_{\nu},
                    \label{eq:J_nu}
                
\end{align}$$ where $E_\nu$ is the characteristic electron energy $$\begin{align}
                    E_\nu = \left(\dfrac{4\pi m_e c\nu}{3Bq}\right)^{1/2}m_ec^2.
                    \label{eq:e_nu}
                
\end{align}$$ $m_e$, $c$, and $q$ represent the electron mass, speed of light, and (absolute) electron charge, respectively. The hotspot of radius $R$ spans a solid angle $\Omega = \pi\left(R/d\right)^2$, where $d$ is the distance to Sgr A\*.

We define $\tau_\nu$, the frequency-dependent optical depth, as $\tau_\nu = (4/3)\kappa_\nu R$. The $4/3$ prefactor accounts for the “effective” optical depth of all lines of sight through the plasma. This is different than the canonical $\tau_\nu = 2\kappa_\nu R$, which is only true for the optical depth through the plasma’s center. $\kappa_\nu$ is the synchrotron absorption coefficient, $$\begin{align}
                    \kappa_\nu = \dfrac{\sqrt{3}Bq^3}{4\pi m_e\nu^2}\left(2^{p/2-1}\Gamma\left(\dfrac{3p+2}{12}\right)\Gamma\left(\dfrac{3p+22}{12}\right)\right)~n(E).
                    \label{eq:kappa_nu}
                
\end{align}$$ We have set the pitch angles to $90^\circ$ in Equations [\[eq:e_nu\]](#eq:e_nu) and [\[eq:kappa_nu\]](#eq:kappa_nu). To adopt a fixed ratio between the magnetic field energy density ($U_B = B^2/8\pi$) and the electron energy density ($U_e = \int_{E_1}^{E_2} En(E)~dE$), we define the electron number density between initial energies $E_1$ and $E_2$ as $$\begin{align}
                    n(E) = \dfrac{B^2}{8\pi\varphi E_0^2}\left(\dfrac{E}{E_0}\right)^{-p}.
                    \label{eq_nE}
                
\end{align}$$ $\varphi$ is the equipartition factor and controls the ratio of the energy densities between the magnetic and particle fields. We derive $\varphi$ and the prefactor for Equation [\[eq_nE\]](#eq_nE) in Appendix [7](#appendix:a). As the occulting plasma expands, the power-law bounds scale inversely with radius (cite: VDL1966), caused by adiabatic cooling of the ultra-relativistic electron gas. For this analysis, we assume $E_0 = E_1 = 1$ MeV and $E_2 = 1$ GeV. We note the special constraint for the energy bounds where $E \nless 0.5$ MeV (electron rest mass), which we account for in our analysis.

The measured flux of the hotspot at any radius and frequency: $$\begin{equation}
                    S_\nu(R) = \Omega J_\nu\left(1-e^{-\tau_\nu}\right).
                
\end{equation}$$ To convert between radius and UTC time, we assume a linear expansion of the hotspot with expansion speed $v_{\text{exp}}$: $$\begin{equation}
                    \dfrac{R}{R_0} = 1 + v_{\text{exp}}(t - t_0),
                    \label{eq:radius_time_relationship}
                
\end{equation}$$ where $t_0$ is the UTC time when $R=R_0$.

### Quiescent Emission Model

In this geometric model, the fraction of the projected accretion flow’s area occulted by the hotspot is denoted $f$. From previous analyses, the intrinsic area of the accretion flow is modeled by a frequency-dependent power-law, which we define as $A_{q}(\nu)$. We use the results of (cite: Cho2022) to find $A_q(\nu) = 6.1(\nu/300\text{~GHz})^{-2.4}~R_{\text{S}}^2$ assuming a Gaussian profile having area $A_q(\nu) = \left(2\pi/8\ln2\right) \theta_{\text{major}}(\nu)\theta_{\text{minor}}(\nu)$. The choice of $A_q$ will determine if there is an explicit inclination term. The (cite: Cho2022) analysis gave the intrinsic size of Sgr A\* projected on the sky, removing the need for a specific inclination term. Placing the hotspot at the center of the accretion flow lets us define the ratio $f \equiv \pi R^2/A_q$ if $R\leq \sqrt{A_q/\pi}$ and $f=1$ otherwise, measuring the fraction of the accretion flow eclipsed by the hotspot. We note (cite: Cho2022) use only one epoch of data to determine the frequency-dependent size of Sgr A\*. (cite: Cheng2023) observed Sgr A\* over 10 months, finding a variable intrinsic area of $\approx13\%$, while the mean was roughly $10-20\%$ higher than the (cite: Cho2022) single-epoch results. However, this difference would not substantially affect our results.

In addition to the intrinsic size, the accretion flow has a characteristic flux at frequency $\nu$ denoted by $S_{q}(\nu)$. This model could be further generalized to include a time-dependent term, but that is outside the scope of this analysis. We assume the accretion flow is uniformly smooth across the entire projected area.

### Total Intensity Light Curve

There are three sources of flux present in this model: the unobscured and obscured accretion flow and the hotspot. The unobscured flow has flux $\left(1-f\right)S_q$ and the hotspot $\Omega J_\nu\left(1-e^{-\tau_\nu}\right)$. The obscured flow flux passes through the optical depth produced from the hotspot yielding a flux $fS_q e^{-\tau_\nu}$. Altogether, the net sum of these terms yields a total observed flux of $$\begin{align}
                    S(\nu) &= S_{q}(\nu) + \left(\Omega J_\nu - fS_{q}(\nu)\right)\left(1-e^{-\tau_\nu}\right).
                    \label{eq:total}
                
\end{align}$$ We note the parameters $B, \Omega, J_\nu, f, \tau_\nu, \varphi, E_1, \rm{ and } ~E_2$ all vary with radius, and, therefore, time (Equation [\[eq:radius_time_relationship\]](#eq:radius_time_relationship)). When modeling this time-dependent nature of the occultation, the secular changes in these parameters must be accounted for.\

## Flaring Emission Produced by Adiabatically-Expanding Synchrotron Hotspots

We model the multiwavelength flare using an adiabatically-expanding synchrotron hotspot as described by (cite: VDL1966) and (cite: FYZ2006). To characterize both the quiescent and variable emission, we use a joint fit of accounting for secular variations in the accretion flow and the time-dependent nature of the flaring emission.

### Flaring Emission Model

The variable model is characterized by four parameters: $S_0$, $t_0$, $p$, and $v_{\rm{exp}}$. $S_0$ is the peak flux density at frequency $\nu_0$, which is produced by an electron spectrum $n(E)~dE\propto E^{-p}~dE$ between energies $E_{\rm{min}}$ and $E_{\rm{max}}$. The flaring region expands at a (normalized) velocity $v_{\rm{exp}}$. To convert between UTC time and normalized radius, we use Equation [\[eq:radius_time_relationship\]](#eq:radius_time_relationship).

The flux density of the flare at any radius and frequency $\nu$ is given by $$\begin{align}
                    S_\nu(t) = S_0 \left(\dfrac{\nu}{\nu_0}\right)^{2.5}\left(\dfrac{R}{R_0}\right)^3\dfrac{1 - e^{-\tau_\nu}}{1-e^{-\tau_0}},
                
\end{align}$$ where $\tau_\nu$ and $\tau_0$ are the frequency/radius-dependent and critical optical depths, respectively. For a given $p$, the critical optical depth can be determined from the following transcendental relationship: $$\begin{align}
                    e^{\tau_0} - \left(\dfrac{2p}{3}+1\right)\tau_0 - 1 = 0.
                
\end{align}$$ $\tau_\nu$ at any frequency and radius is determined via $$\begin{align}
                    \tau_\nu = \tau_0 \left(\dfrac{R}{R_0}\right)^{-(2p+3)} \left(\dfrac{\nu}{\nu_0}\right)^{-(p+4)/2}.
                    \label{eq:tau_nu}
                
\end{align}$$

### Quiescent Emission Model

To model time-dependent secular and frequency-dependent variations in the accretion flow, we use a linear model of the form $$\begin{align}
                    I_q(\nu, t) = \left(I_0^\nu + \delta I_t^\nu \left(t - t_0\right)\right)\left(\dfrac{\nu}{\nu_0}\right)^{\alpha_{\nu}}.
                    \label{eq:quiescent}
                
\end{align}$$ Here, $I_0^{\nu}$ is the quiescent emission flux density at frequency $\nu_0$ at time $t_0$, $\delta I_t^\nu$ is the time-slope of the quiescent flux, and $\alpha_{\nu}$ is the quiescent emission’s spectral index.

# Discussion

In this Section, we consider the periodic signal detected in the IR and hinted at in the submm in the context of previous analyses. Using the frameworks described in Section [4](#sec:models), we then model the occultation event and the detected multiwavelength flare. Finally, we discuss a caveat in our modeling and quantify how it affects our results.

## 21 July 2019

### Transient Periodicity

![](OrbitalDistance_Periodicity.pdf)

The transient $\sim35$-minute peak (Figure [8](#fig:alldata_lomb_scargles)) corresponds to similar timescale detections in near-IR (cite: Gravity2018) and submm (cite: Iwata2020) analyses of Sgr A\*’s light curves. (cite: Gravity2018) observed a changing polarization angle consistent with an orbiting hotspot having period $P=40\pm8$ minutes. Similarly, (cite: Iwata2020) used several epochs of ALMA light curves ($230$ GHz) and found $\sim35$-minute quasi-periodic variations at $>5\sigma$ statistical significance. In the context of a non-spinning Schwarzschild black hole ($a_{\ast} = 0$), these results are consistent with variability occurring near the ISCO of Sgr A\*. However, there is tension between constraints in Sgr A\*’s spin. (cite: Fragione2020; Fragione2022) argued for a low spin ($\left|a_{\ast}\right| \lesssim 0.1$) using the dynamics of the S-star population orbiting Sgr A\*. The S-stars reside in two orthogonal disks centered on Sgr A\* (cite: Ali2020); on timescales longer than $\sim1$ Myr, the Lense-Thirring Effect should have randomized these orbits if $|a_{\ast}|\approx 0.5$. This is in stark contrast to (cite: EHT2022a; EHT2022e), who preferred $a_{\ast} \gtrsim 0.5$ when comparing event-horizon scale images to general relativistic magnetohydrodynamic (GRMHD) simulations of Sgr A\*.

Due to this discrepancy, we cannot definitively determine the orbital radius where a $\sim35$ minute periodicity would originate. Instead, we calculate the orbital radius corresponding to a $35$-minute period for the full range of $a_{\ast}$ and show it in Figure [11](#fig:isco_plot). We use the period-radius relationship given in (cite: Gravity2018): $$\begin{equation}
                    P~\left[\rm{min}\right] = 2.137~\left(\dfrac{M}{4.14\times10^6~M_\odot}\right)~\left(a_{\ast} + \left(\dfrac{2R}{R_{\rm{S}}}\right)^{3/2}\right).
                
\end{equation}$$ The ISCO radius is given by $$\begin{align}
                        R_{\rm{ISCO}} &= \dfrac{R_{\rm{S}}}{2}\left(3 + z_2 \mp \sqrt{\left(3-z_1\right)\left(3 + z_1 + 2z_2\right)}\right);\\
                        z_1 &=  1 + \sqrt[3]{1 - a_{\ast}^2} \left(\sqrt[3]{1  + a_{\ast}} + \sqrt[3]{1 - a_{\ast}}\right),\\
                        z_2 &= \sqrt{3a_{\ast}^2 + z_1^2},
                    \end{align}$$ where $\mp$ correspond to prograde and retrograde orbits, respectively (cite: Bardeen1972). If this quasi-periodicity is caused by orbital motion, the hotspot is on a stable orbit ($R \geq R_{\rm{ISCO}}$) given $a_{\ast}\gtrsim-0.15$. Viscous timescales are unlikely to be the cause as the accretion flow would require a scale height (H/R) $\sim2.2$ for a 35-minute viscous timescale at $3~R_{\rm{S}}$ (cite: Dexter2014).

Several non-orbital causes may be the origin of this structure. (cite: Boyce2022) noted this periodic structure in their analysis of the *Spitzer* data but argued it may be formed in processes that can be modeled by correlated red noise. (cite: Witzel2012) and (cite: Subroweit2017) found Sgr A\*’s submm variability is also consistent with red noise. If this periodic feature was a statistical product of Sgr A\*’s red noise fluctuations, observing it in the submm and IR strongly indicates the variability at these two frequency regimes originates from a single electron population.

However, physical causes are shown in GRMHD modeling. (cite: Ripperda2020) found magnetic reconnection within magnetically-arrested disks (MAD), such as those around Sgr A\*, can form “plasmoid” hotspots at periodic intervals, and the period of their formation depends on the reconnection rate. Such plasmoids undergo physical expansion, causing a decrease in their average internal magnetic field strength (cite: Nathanail2020). Additionally, (cite: Porth2021) and (cite: Chatterjee2022) studied orbiting flux tubes, regions within the accretion flow with a decreased magnetic field strength compared to the local environment, which could also produce periodic signatures in light curves.

Plasmoids are similar to adiabatically-expanding hotspots, which describe time-delayed emission at different frequencies as the change in optical depth as the hotspot expands. In Figure [7](#fig:alma_spitzer_gp), we detect a $\sim5$ minute time delay detected between the *Spitzer* and ALMA light curves. Taken together, this feature may have been formed by a series of magnetic reconnections within the accretion flow, whose subsequent dynamic expansion caused time-delayed emission between these two frequency regimes. However, plasmoids cause dips in the submm flux from depleted magnetization in the accretion flow rather than a flare occulting it (see Section [5.1.2](#ssec:occultation) below). If such events are recorded at different wavelengths, the predicted multiwavelength signatures may be able to distinguish between the two models.

### Occultation Modeling

![](Occultation_Fits.pdf)

Assuming that there was an IR flare (Figure [9](#fig:july26_xcorr)), Equations [\[eq:J_nu\]](#eq:J_nu)–[\[eq_nE\]](#eq_nE) could be manipulated to solve for the equipartition magnetic field strength, allowing us to directly fit the submm light curve with the occultation model. However, the *Spitzer* data during the period of interest is low SNR, and no discernible flare was detected. While an X-ray flare was detected, the exact mechanism producing this emission is still an open question (cite: Markoff2001; FYZ2006a; DoddsEden2009; Ponti2017; Abuter2021). Therefore, we cannot accurately extrapolate the IR flaring flux. Additionally, there is an insufficient range in bandwidth for us to use all four ALMA light curves to directly fit the data.

Instead, we create a grid of initial physical conditions to determine the IR and submm properties of the plasma. We make grid of $500^3$ realizations linearly sampling the electron energy index ($p\in\left[0.34, 5\right]$), the magnetic field strength ($B\in\left[0.1, 150\right]$ Gauss), and the initial radius ($R\in\left[0.01, 10\right]~\rm{R}_{\rm{S}}$). For each model, we calculate the optically thin IR flux ($S_{\text{IR}}=\Omega J_{\nu} \tau_{\nu}$) and the (absolute) maximum change in the flux at 334 GHz flux (Equation [\[eq:total\]](#eq:total)). For this calculation, we assume $S_q = 4.48$ Jy, which is the average flux before the occultation (Figure [6](#fig:july21_xcorr)d). Determining the maximum change in the submm flux is analytically complicated as most of the parameters vary with the radius of the plasma. Therefore, we numerically simulate the light curve of each realization by varying the plasma size between $1-10\times$ its initial value and determine the radius where the (absolute) maximum submm flux change occurs.

We limit the possible models using several constraints. First, we require the size of the occulting plasma at the maximum change to be larger than its initial size; this constraint stems from the non-zero time delay between the X-ray flare and the submm dip (Figure [6](#fig:july21_xcorr)). Next, we require the change in the submm flux to be negative. Note the submm flux may increase *or* decrease depending on the model conditions. An increase in the submm flux occurs when the plasma’s brightness temperature is greater than the accretion flow’s, producing a normal submm flare (Section [4.2](#ssec:flaring_model)). From Figure [7](#fig:alma_spitzer_gp), we calculate a flux drop of $\sim610$ mJy at 334 GHz but consider models where the flux difference is within $20\%$ of this value ($488-732$ mJy) to account for scatter within the ALMA light curve.

While we do not detect the IR flare, we can place statistical upper- and lower limits on its flux. As an upper limit, we calculate $5\times$RMSE (RMSE $\sim3.2$ mJy) of the *Spitzer* data during the low SNR period (about 1-2.1 hr UTC). The corresponding IR flare hidden within the noise might increase the RMSE, affecting our upper limit. However, since we do not attempt a true fit to the data, we do not revise this upper limit. The lower limit comes from (cite: Witzel2021), who completed a joint-variability analysis of Sgr A\* from submm to X-ray frequencies. They determine each *Spitzer* flux measurement has $\sim0.65$ mJy measurement noise. Since *Spitzer* was unlikely to measure flares dimmer than this, we use $5\times$ this value as our lower limit on the IR flux.

We find only $\sim0.02\%~(27533)$ of our initial conditions are consistent with the data. A corner plot of the initial conditions is shown in Figure [12](#fig:occultation_cp). While we cannot directly fit the light curves, we use the realizations consistent with the data to determine the statistical properties of the flare. We find the drop is consistent with a plasma of initial radius $0.55$ R$_{\rm{S}}$ threaded by a uniform $\sim130$ Gauss magnetic field expanding at $\sim0.6\%$ of the speed of light. This emission is produced by an electron spectrum with index $p\sim2.8$, and we estimate it yields a peak $4.5~\mu$m flare flux $\sim8$ mJy.

The “pseudo-posterior” magnetic field distribution (histograms along the diagonal) is roughly flat, suggesting that we have not probed the best field strengths consistent with the data. This motivates us to test additional models, where we set an unrealistic maximum strength of $500$ Gauss. Even at these strengths, the distribution of values consistent with the data is still flat (not shown). The average magnetic field strength probed by this initial analysis is stronger than typical values found in observation (cite: Ponti2017; Abuter2021; Michail2021c; Michail2021b; Witzel2021) and MHD simulations (cite: Ressler2020a). However, we note (cite: Ressler2020b) have shown that average magnetic field strengths above $200$ Gauss are possible near the event horizon (according to full-GRMHD modeling).

In the context of the given observation, a strong magnetic field and flat distribution is not surprising. Occultations occur when the brightness temperature of the responsible hotspot is lower than that of the accretion flow. The brightness temperature for synchrotron emission scales as $T_B\propto J_\nu / \left(\Omega\nu^2\right)$, where $J_\nu$ is the synchrotron source function. $J_\nu$ itself scales as $J_\nu\propto \nu^{2.5}/\sqrt{B}$ (Equation [\[eq:J_nu\]](#eq:J_nu)); therefore, $T_B \propto \sqrt{\nu / B}$. This necessarily requires high magnetic field strengths to balance the value of $\nu$ at submm frequencies. Additionally, the flat distribution of magnetic field strengths is an artifact of degeneracy since we only used one frequency to model the occultation. For one given frequency, there are an infinite number of magnetic field strengths that will produce a hotspot with a brightness temperature lower than the surrounding accretion flow. Observing the event at a different band constrains the required magnetic field strength to produce this feature at multiple frequencies, where the accretion flow’s brightness temperature is also different.

Additionally, the elevated magnetic field strength may be caused by our choice of the electron energy spectrum’s lower energy bound, which we assume is $1$ MeV. We find a total relativistic electron density of $\sim1.9\times10^{8}$ cm$^{-3}$ between 1-1000 MeV for our parameters. This $\sim40\times$ higher than the electron density found by (cite: Abuter2021) during the flare on 18 July 2019 but similar to the (cite: Boyce2022) value when considering the same flare undergoing adiabatic expansion. We assume magnetic equipartition with the electron energy density while modeling the flare (see Equation [\[eq_nE\]](#eq_nE) and Appendix [7](#appendix:a)). Electrons responsible for the majority of synchrotron emission at frequency $\nu$ and magnetic field strength $B$ have Lorentz factors near: $$\begin{equation}
                    \gamma = \sqrt{~3578\left(\dfrac{\nu}{\text{GHz}}\right)\left(\dfrac{\text{Gauss}}{B}\right)}
                    \label{eq:gamma_likely}
                
\end{equation}$$ (cite: CondonRansom2016). For 334 GHz and 130 Gauss, $\gamma\sim100$ corresponds to an electron energy $\sim50$ MeV. If we grossly underestimate the lower energy bound of the electron spectrum, this overestimates the electron energy density and the magnetic field strength. By way of example, changing the lower energy bound to $\gamma=10$ ($5$ MeV) for an electron spectrum with $p=2.84$ decreases the electron energy density by a factor $\sim4$, reducing the magnetic field strength by a factor $\sim2$ ($B \propto \sqrt{U_e}$).

Obtaining at least one light curve in the radio would constrain the lower energy bound of the electron spectrum ($E_1$). The dip in the radio flux is lessened (cite: Cho2022). However, the time delay of the dip relative to submm depends on the critical optical depth of the plasma, which is solely a function of $p$ (Equation [\[eq:tau_nu\]](#eq:tau_nu)). If the predicted time delay at radio frequencies did not match the value extrapolated from the submm, it could suggest curvature in the electron spectrum between energies probed at the two frequencies, changing the intrinsic optical depth.

### Signatures of Occulting Hotspots Offset from Accretion Flow

Our definition of $f$ implies the occulting hotspot is fully embedded in the accretion flow at any frequency, which is a central assumption in our model and affects the physical parameters. In Figure [10](#fig:occultation_diagram), we show both possibilities where the flare is fully and partially embedded in the accretion flow. In the concentric case, the total observed flux of the system is $S_q(\nu)$ (number 1) before the flare forms. As the plasma expands, it is optically thick and occults part of the accretion flow (number 2) until it reaches the critical optical depth (number 3). The continued expansion causes the emission to become optically thin, lessening the extinction the accretion flow undergoes (number 4) until only the flow remains (number 5).

In the offset model (bottom panels), an interesting feature occurs. As in the previous model, the total emission measured is the accretion flow flux (number 1). However, as the plasma begins to expand, it does not occult any part of the flow, raising the overall flux of the system (number 2). Eventually, the hotspot’s size is large enough, and its optical depth is sufficient to begin shadowing the accretion flow (number 3). As in the previous case, the continuing expansion will cause a dip in the light curve (number 4) and eventually will fade away until only the accretion flow remains (number 5). We note such offset flares require a precise combination of distance from the accretion flow and optical depth for the occultation feature to occur. Additionally, if the hotspot’s distance from the accretion flow is sufficiently far, the hotspot becomes optically thin before it causes an occultation, rendering only a flare in the light curve. Therefore, the offset also explains the lack of occultation events during every flaring event.

The frequency-dependent size of Sgr A\* may also play a role in determining which occultation profile occurs. At radio frequencies, the intrinsic size of this source is larger than the reported hotspot sizes. (cite: Cho2022) found Sgr A\*’s intrinsic extent to be $\sim30~R_{\rm{S}}\times23~R_{\rm{S}}$ at 43 GHz. Using the relationship given in their paper, the 334 GHz size of Sgr A\* is $\sim2.3~R_{\rm{S}}\times1.7~R_{\rm{S}}$, comparable to the hotspot sizes. The Gaussian-process-interpolated ALMA light curve (Figure [7](#fig:alma_spitzer_gp)) suggests this offset profile was detected on 21 July 2019. (cite: Marrone2008) also may have detected a similar case on 17 July 2006 during simultaneous X-ray and submm observations (see their Figure 3). They saw increases in the $850~\mu$m and $1.3$ mm light curves at the beginning of an X-ray flare, then reached a minimum flux near its peak. Future multiwavelength campaigns should observe complementary radio frequencies to test the frequency-dependent nature of this occultation model.\
\

## 26 July 2019

![](RadioSubmmFit.pdf)

Using the adiabatic-cooling model described in Section [4.2](#ssec:flaring_model), we jointly fit the radio and submm light curves shown in Figure [9](#fig:july26_xcorr). Modeling the IR light curve is complicated as synchrotron cooling dominates adiabatic cooling at these high frequencies. For example, the synchrotron cooling timescale at $4.5~\mu$m in a 50 G field is $\sim6$ minutes, while the adiabatic cooling is at $\sim$hourly timescales. Attempting to fit all three frequency light curves simultaneously requires a more substantial model to account for both adiabatic and synchrotron cooling, which is beyond the scope of this analysis. Therefore, we do not model the IR light curve, as the modeled parameters will have little physical meaning. Instead, they will be over-biased such that the “best-fit” adiabatic expansion picture mimics a synchrotron cooling profile.

The VLA and ALMA light curves have sufficient spectral windows to simultaneously fit the flare and quiescent emission. The flaring emission is fit using a single set of hotspot parameters. On the other hand, we use two different sets of quiescent parameters to independently model the radio and submm emission, which is necessary for two reasons. First, the quiescent model includes a phenomenological parameter to model the time-slope of the accretion flow at each frequency range. As each band probes different radii within the accretion flow (cite: Cho2022), there is no guarantee these values will be equivalent. Second, Sgr A\*’s spectral index flattens from radio to submm frequencies (cite: Bower2015), which would require fitting three spectral indices (intra-radio, intra-submm, and radio-submm). By fitting one quiescent model per frequency band, we can determine the intra-radio and intra-submm indices and then infer the one from radio to submm using the quiescent flux densities at each reference frequency (i.e., $I_0^\nu$, Equation [\[eq:quiescent\]](#eq:quiescent)). The result of this joint fit is shown in Figure [13](#fig:plasmon_fits), and the parameter values are given in Table [1](#tab:plasmon_fits).

+---------------------------+----------------------------------------+---------------+--------------------+
| Parameter                 | Description                            | Unit          | Value              |
+:=========================:+:======================================:+:=============:+:==================:+
| Hotspot Parameters                                                                                      |
+---------------------------+----------------------------------------+---------------+--------------------+
| $S_0$                     | Peak Flare Flux at 334 GHz             | mJy           | $686 \pm 6$        |
+---------------------------+----------------------------------------+---------------+--------------------+
| $t_0$                     | Flare UTC Peak Time at 334 GHz         | hr UTC        | $4.58 \pm 0.01$    |
+---------------------------+----------------------------------------+---------------+--------------------+
| $p$                       | Electron Spectrum Index                | –             | $0.59 \pm 0.01$    |
+---------------------------+----------------------------------------+---------------+--------------------+
| $v_\text{exp}$            | Normalized Radial Expansion Speed      | hr$^{-1}$     | $5.36 \pm 0.05$    |
+---------------------------+----------------------------------------+---------------+--------------------+
| Radio Quiescent Parameters                                                                              |
+---------------------------+----------------------------------------+---------------+--------------------+
| $I_0^{\rm{radio}}$        | Quiescent Flux at 37.54 GHz at $t=t_0$ | mJy           | $1305.6\pm0.6$     |
+---------------------------+----------------------------------------+---------------+--------------------+
| $\delta I_t^{\rm{radio}}$ | Quiescent Time-Slope at 37.54 GHz      | mJy hr$^{-1}$ | $-12.2\pm0.3$      |
+---------------------------+----------------------------------------+---------------+--------------------+
| $\alpha_{\rm{radio}}$     | Ka-band Quiescent Spectral Index       | –             | $0.074 \pm 0.003$  |
+---------------------------+----------------------------------------+---------------+--------------------+
| Submm Quiescent Parameters                                                                              |
+---------------------------+----------------------------------------+---------------+--------------------+
| $I_0^{\rm{submm}}$        | Quiescent Flux at 334 GHz at $t=t_0$   | mJy           | $3083\pm2$         |
+---------------------------+----------------------------------------+---------------+--------------------+
| $\delta I_t^{\rm{submm}}$ | Quiescent Time-Slope at 334 GHz        | mJy hr$^{-1}$ | $-79.9 \pm 0.1$    |
+---------------------------+----------------------------------------+---------------+--------------------+
| $\alpha_{\rm{submm}}$     | Band 7 Quiescent Spectral Index        | –             | $-0.099 \pm 0.023$ |
+---------------------------+----------------------------------------+---------------+--------------------+

: Fitted parameters for the joint submm and radio light curve modeling shown in Figure [13](#fig:plasmon_fits). Quoted errors are given at $1\sigma$ significance.

### Quiescent Properties

We find a spectral index that is roughly flat ($\alpha\sim0.07$) at Ka-band. (cite: Herrnstein2004) find a variable spectral index at similar wavelengths that range from $\sim-0.1$ to $0.7$. We note, however, that their observations do not account for flaring emission and are an ensemble average of both the quiescent and variable components. The (ensemble-average) spectral energy distribution of Sgr A\* from (cite: Brinkerink2015) suggested a similarly flat spectrum and comparable flux density at radio frequencies as ours here. Similarly, our fitted submm spectral index and flux are well within the range of those observed (cite: Wielgus2022a). Using the fitted quiescent fluxes, we also determine the average spectral index between 31.54 and 334 GHz is $\alpha\sim0.36$, which is consistent with the canonical value of $\alpha=0.33$ for optically-thick accretion flows (cite: Pringle1981) and those in the literature (cite: Michail2021b).

The consistency between our fitted quiescent emission in 2019 and previous analyses is somewhat shocking. IR variability suggests that Sgr A\* was more variable in 2019 than in the past $\sim20$ years (cite: Do2019; Weldon2023), which they concluded occurs from enhanced accretion onto the event horizon. As flaring events occur within the accretion flow, one would expect similar outliers in the quiescent submm and radio emission. However, this analysis does not show similar drastic changes, even at 334 GHz, where the emission primarily occurs near the event horizon, agreeing with (cite: Murchikova2021), who find no change in either the 230 GHz flux or variability statistics in the aftermath of this bright IR flare. Additional radio observations of Sgr A\* during 2019 should be analyzed to determine if a similar change in the radio continuum properties occurred.

### Hotspot Properties

The first four rows in Table [1](#tab:plasmon_fits) list the fitted parameters for the hotspot. The plasma produces a $686$ mJy flare at 334 GHz from a shallow electron energy spectrum with an index $p=0.59$. The low value of $p$ is caused by neglecting synchrotron cooling in the adiabatically-expanding hotspot model. Values typically range from $p\approx1-3$ (cite: FYZ2009; Eckart2009; Michail2021c; Michail2023; Witzel2021; Boyce2022), where $p=1$ indicates an extremely strong and efficient shock (cite: Bell1978a; Bell1978b). We discuss the low value of $p$ in Section [5.3](#ssec:synch_cool).

Given these values, we can calculate an equipartition magnetic field strength and radius for the observed flare. Once again, we assume the $E^{-0.59}$ electron energy spectrum is valid from energies between 1 to 1000 MeV consistent with Section [5.1.2](#ssec:occultation). We determine the hotspot to have a radius $0.47$ $R_{\text{S}}$ at the time of the peak submm emission, which is threaded by a magnetic field $\sim187$ Gauss. The mass is $3.7\times10^{18}$ grams, and the electron density is $2.82\times10^6$ cm$^{-3}$. Assuming linear expansion of the hotspot yields an expansion velocity of $0.029c$. This combination of magnetic field strength and electron number density is similar to the time-averaged conditions within a few $R_{\text{S}}$ of a strongly-jetted accretion flow around Sgr A\*, as modeled with GRMHD (cite: Chatterjee2021).

(cite: Subroweit2017) complete a statistical analysis of 100 and 345 GHz light curves of Sgr A\*. By relating the flaring flux distribution with the adiabatically expanding hotspot model, they suggest the majority of flares have size $\sim0.67~R_{\text{S}}$ and expand with “intermediate” velocities of order $0.01c$. The expansion velocities have generally been found to lie in the range of $0.001-0.1c$ (cite: FYZ2008). Similarly, the inferred radius of these hotspots are order $\sim R_{\text{S}}$, with most of the GRAVITY IR interferometry results preferring $0.5-1.5~R_{\text{S}}$ (cite: Gravity2020; Gravity2020orbit; Abuter2021).

As with the models consistent with the occultation event, the magnetic field strength here is much stronger than previously observed by a factor $\sim2$. This might be attributed to the incorrect upper energy bound rather than the lower one described during the occultation. The sensitivity of the magnetic field strength on the upper or lower bound depends on the electron energy index. Equation [\[eq:ue\]](#eq:ue) gives the electron energy density as a function of $p$, $E_{2}$, and $E_{1}$ (the maximum and minimum electron energies, respectively). For $p>2$ (in the case of the occultation), the value of $U_e$ is more sensitive to $E_1$ instead of $E_2$ since $E_2^{2-p} < E_1^{2-p}$. For $p\in[0, 2)$, the opposite is true as in our case of $p=0.59$, $U_e\propto E_2^{1.41}-E_1^{1.41}$. Using Equation [\[eq:gamma_likely\]](#eq:gamma_likely) for 334 GHz at 180 Gauss yields $\gamma \approx 80$ (an electron energy of $40$ MeV). Reducing the original upper energy bound to 175 MeV (cite: Boyce2022) yields an equipartition magnetic field strength $94$ Gauss, electron density $3.8\times10^{6}$ cm$^{-3}$, mass $2.9\times10^{18}$ grams, radius $0.39~R_{\text{S}}$, and expansion speed $0.024c$.

## Effects of Synchrotron Cooling

Throughout the models presented in Section [4](#sec:models), we have ignored any contribution of synchrotron cooling to the light curves. However, at the submm frequencies probed here, it somewhat affects the observed profiles. In the occultation modeling (Section [5.1.2](#ssec:occultation)), the adiabatic and synchrotron cooling times are roughly equal. If we define the adiabatic timescale as $t_{\text{ad}}=R_{\text{max}}/v_{\text{exp}}$, we find this value to be $\sim 1$ hour, roughly double the synchrotron cooling timescale at 334 GHz in a 130 Gauss field, $t_{\text{sc}}\sim0.5$ hr. Ignoring this effect will tend to over-predict the magnetic field strength as the electrons will have lower characteristic energies than calculated via adiabatic expansion alone. Since the characteristic electron energy $E_\nu\propto B^{-1/2}$ (Equation [\[eq:e_nu\]](#eq:e_nu)), the fitting results will tend to bias toward higher magnetic field strengths (lower energy) to account for this discrepancy.

Likewise, the effect of synchrotron cooling is visible in the submm light curve in Figure [13](#fig:plasmon_fits), as the predicted adiabatic model peak flux is higher than that of the observed value. This also tends to increase the equipartition magnetic field strength as above; however, it also affects the fitted value of $p$. At the peak submm emission, a sufficient proportion of electrons have cooled faster via adiabatic *and* synchrotron processes, which decreases the optical depth of the plasma, suppressing the peak flux as prescribed by the adiabatic picture.

As mentioned in Section [5.2.2](#ssec:hotspot_properties), the low value of $p$ measured in the joint radio-submm plasmon fit is caused by ignoring synchrotron cooling in the evolution of the submm flare. The relationship between the peak flux of an adiabatically-expanding hotspot at two different frequencies is $S_{\nu_2} = S_{\nu_1}\left(\nu_2/\nu_1\right)^{\frac{7p+3}{4p+6}}$ (cite: VDL1966). As discussed above, synchrotron cooling will tend to decrease the peak flux where it is comparable or dominant to adiabatic cooling. $p$ will be biased towards lower values to fit this dimmer-than-expected submm peak with the radio light curves. To confirm this, we independently fit the radio and submm data with a single adiabatically-cooling hotspot (not shown). We find $p\sim1.3$ for both the radio and submm fits. By way of example, assume a $100$ mJy flare occurs at $31.54$ GHz (as estimated from Figures [9](#fig:july26_xcorr)d and [13](#fig:plasmon_fits)). For $p=0.6$ and $p=1.3$, we find peak $334$ GHz fluxes of $757$ and $1282$ mJy, respectively. The lower value of $p$ better models the observed submm light curve; however, by ignoring synchrotron cooling, we have effectively obtained an unrealistic value of $p$.

Overall, ignoring synchrotron cooling causes a biased value of $p$ and tends to overpredict the calculated equipartition magnetic field strength compared to previous observational and theoretical values. Future analyses using this adiabatic cooling model (especially when synchrotron cooling is dominant to adiabatic cooling) need to account for this additional effect. We note synchrotron cooling is not the only missing process throughout this work. For example, the lack of general relativistic effects, such as lensing, may also affect our results. However, including these additional processes is outside the scope of this current work.

# Summary and Conclusions

We present and analyze the data during the final two days of a multiwavelength campaign to observe Sgr A\*, which occurred in July 2019 and was the last such campaign with the *Spitzer* *Space Telescope*. Analysis of the first day was presented in . The participating instruments ranged in energy from radio to X-ray energies. The observations showed Sgr A\* to be remarkably active. On 26 July, we observed a flare in the IR, submm, and radio, which presents the most evident causal link between the variability mechanisms in these frequency regimes. We model the radio and submm light curves using an adiabatically-expanding synchrotron hotspot. We find a transient $\sim35$ minute periodicity in the *Spitzer* light curve on 21 July, corresponding to slightly time-delayed peaks observed with ALMA, suggesting a hotspot on a stable orbit around Sgr A\*. We detect a drop in the submm flux shortly after an X-ray flare on the same day. We modeled this feature using an adiabatically-expanding synchrotron hotspot, which occults the accretion flow during its dynamic expansion. We present the model in this paper after generalizing it from a specific case for $p=2$ (cite: FYZ2010).

During both days, we find the magnetic field strength estimates are uncertain because of the lack of constraints in the upper and lower energy bounds of the electron spectrum and the omission of synchrotron cooling. The absence of lower frequency radio light curves does not allow for a robust lower energy bound. Synchrotron cooling plays a crucial role in the profiles of the submm light curves. The magnetic field strengths we estimate are uncertain on both days because of the lack of data constraining the bound of the electron energy spectrum and neglecting synchrotron cooling, which will tend to increase the equipartition magnetic field strength required to model the observed features. Modeling flares using adiabatically-expanding synchrotron hotspots with future high-frequency submm and IR observations will require accounting for synchrotron cooling losses during the expansion phase, placing a strong bound on the upper energy limit. Supplementing high-quality radio frequency light curves with such observations will constrain the bounds of the electron spectrum and better bound possible values of the magnetic field strength responsible for the emission.\
\

# Acknowledgments

We are grateful to Sean Carey, Dan Marrone, and Steven Willner for useful comments that strengthened this manuscript. We additionally thank the referee for their very helpful and constructive feedback. This work is partially supported by NSF grant AST-2305857 and through SOSP21A-003 and SOSPADA-026 from the NRAO. SM is grateful for support from the Dutch Research Council (NWO) VICI award (grant 639.043.513) and the European Research Council (ERC) SyG “BlackHolistic” (grant 101071643). GGF, JLH, and HAS acknowledge support for this work from the NASA ADAP program under NASA grant 80NSSC18K0416. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.A.00050.T. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Based on observations made with the NASA/ESA Hubble Space Telescope, obtained from the data archive at the Space Telescope Science Institute. STScI is operated by the Association of Universities for Research in Astronomy, Inc. under NASA contract NAS 5-26555. This work is based on archival data obtained with the Spitzer Space Telescope, which was operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA. The scientific results reported in this article are based in part on data obtained from the Chandra Data Archive. This research has made use of software provided by the Chandra X-ray Center (CXC) in the application packages CIAO. This research has made use of data obtained from the Chandra Source Catalog, provided by the Chandra X-ray Center (CXC) as part of the Chandra Data Archive. This research was supported in part through the computational resources and staff contributions provided for the Quest high-performance computing facility at Northwestern University which is jointly supported by the Office of the Provost, the Office for Research, and Northwestern University Information Technology.

# Facilities

VLA, ALMA, HST (WFC3), Spitzer, CXO (ACIS)

# Software

`AIPS`, `astropy` (cite: astropy:2013; astropy:2018), `BBlocks` (cite: BBlocks), `CASA` (cite: McMullin2007), `CIAO` (cite: Ciao2006), `LMFIT` (cite: LMFIT), `matplotlib` (cite: matplotlib), `numpy` (cite: numpy), `pandas` (cite: pandas), `pyCCF` (cite: Peterson1998; PYCCF), `scipy` (cite: scipy), `sklearn` (cite: sklearn)

# Deriving the Equipartition and Electron Spectrum Factors

For an electron distribution $n(E)\propto E^{-p}$ between energies $E_1$ and $E_2$, the electron energy density is:

$$\begin{align}
        U_e = \int_{E_1}^{E_2} E~n(E)~dE = \int_{E_1}^{E_2} n_0E\left(\dfrac{E}{E_0}\right)^{-p}~dE.
    
\end{align}$$ This integration yields $$\begin{align}
        U_e(p) = \begin{cases}
        \dfrac{n_0E_0^2}{2-p}\left(\left(\dfrac{E_2}{E_0}\right)^{2-p} - \left(\dfrac{E_1}{E_0}\right)^{2-p}\right), & p \geq 0, p\neq2, \\\\
        n_0E_0^2\ln\left(\dfrac{E_2}{E_1}\right), & p=2,
        \label{eq:ue}
        \end{cases}
    
\end{align}$$ where $n_0$ has units of $\rm{erg}^{-1}\rm{ cm}^{-3}$. Writing $U_B$ and $U_e$ as $U_B = \left(U_B/U_e\right)U_e$, plugging in for $U_e$ from Equation [\[eq:ue\]](#eq:ue), and substituting $U_B = B^2/8\pi$: $$\begin{align}
        \dfrac{B^2}{8\pi} = 
        \begin{cases}
        \left(\dfrac{U_B}{U_e}\right) \dfrac{n_0E_0^2}{2-p}\left(\left(\dfrac{E_2}{E_0}\right)^{2-p} - \left(\dfrac{E_1}{E_0}\right)^{2-p}\right), & p \geq 0, p\neq2 \\\\
        \left(\dfrac{U_B}{U_e}\right) n_0E_0^2\ln\left(\dfrac{E_2}{E_1}\right), & p=2.
        \end{cases}
    
\end{align}$$

Solving for $n_0$: $$\begin{align}
        n_0 = \begin{cases}
        \dfrac{B^2}{8\pi E_0^2}\dfrac{2-p}{\left(\dfrac{U_B}{U_e}\right)\left(\left(\dfrac{E_2}{E_0}\right)^{2-p} - \left(\dfrac{E_1}{E_0}\right)^{2-p}\right)}, & p \geq 0, p\neq2
        \\\\
        \dfrac{B^2}{8\pi E_0^2}\dfrac{1}{\left(\dfrac{U_B}{U_e}\right)\ln\left(\dfrac{E_2}{E_1}\right)}, & p=2.
        \end{cases}
    
\end{align}$$

By defining, $$\begin{align}
        \varphi(p) \equiv \begin{cases}
        \left(\dfrac{U_B}{U_e}\right)\dfrac{\left(\dfrac{E_2}{E_0}\right)^{2-p} - \left(\dfrac{E_1}{E_0}\right)^{2-p}}{2-p}, & p \geq 0, p\neq2 \\\\
        \left(\dfrac{U_B}{U_e}\right)\ln\left(\dfrac{E_2}{E_1}\right), & p=2,
        \end{cases}
    
\end{align}$$ we obtain $$\begin{equation}
        n(E) = \dfrac{B^2}{8\pi\varphi E_0^2}\left(\dfrac{E}{E_0}\right)^{-p},
    
\end{equation}$$ which is Equation [\[eq_nE\]](#eq_nE) above. Due to adiabatic cooling of the ultra-relativistic electron gas, $E_1$ and $E_2$ scale inversely with radius. Therefore, $\varphi(p)\propto R^{2-p}$, which must be properly accounted for while modeling the overall occultation light curves.

natexlab

(ref: Ali2020) Ali, B., Paul, D., Eckart, A., et al. 2020, ApJ, 896, 100, doi: [`10.3847/1538-4357/ab93ae`](http://doi.org/10.3847/1538-4357/ab93ae)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Baganoff2001) Baganoff, F. K., Bautz, M. W., Brandt, W. N., et al. 2001, Nature, 413, 45, doi: [`10.1038/35092510`](http://doi.org/10.1038/35092510)

(ref: Bardeen1972) Bardeen, J. M., Press, W. H., & Teukolsky, S. A. 1972, ApJ, 178, 347, doi: [`10.1086/151796`](http://doi.org/10.1086/151796)

(ref: Bell1978a) Bell, A. R. 1978a, MNRAS, 182, 147, doi: [`10.1093/mnras/182.2.147`](http://doi.org/10.1093/mnras/182.2.147)

(ref: Bell1978b) —. 1978b, MNRAS, 182, 443, doi: [`10.1093/mnras/182.3.443`](http://doi.org/10.1093/mnras/182.3.443)

(ref: Boehle2016) Boehle, A., Ghez, A. M., Schödel, R., et al. 2016, ApJ, 830, 17, doi: [`10.3847/0004-637X/830/1/17`](http://doi.org/10.3847/0004-637X/830/1/17)

(ref: Bouffard2019) Bouffard, É., Haggard, D., Nowak, M. A., et al. 2019, ApJ, 884, 148, doi: [`10.3847/1538-4357/ab4266`](http://doi.org/10.3847/1538-4357/ab4266)

(ref: Bower2015) Bower, G. C., Markoff, S., Dexter, J., et al. 2015, ApJ, 802, 69, doi: [`10.1088/0004-637X/802/1/69`](http://doi.org/10.1088/0004-637X/802/1/69)

(ref: Bower2019) Bower, G. C., Dexter, J., Asada, K., et al. 2019, ApJL, 881, L2, doi: [`10.3847/2041-8213/ab3397`](http://doi.org/10.3847/2041-8213/ab3397)

(ref: Boyce2019) Boyce, H., Haggard, D., Witzel, G., et al. 2019, ApJ, 871, 161, doi: [`10.3847/1538-4357/aaf71f`](http://doi.org/10.3847/1538-4357/aaf71f)

(ref: Boyce2022) —. 2022, ApJ, 931, 7, doi: [`10.3847/1538-4357/ac6104`](http://doi.org/10.3847/1538-4357/ac6104)

(ref: Bremer2011) Bremer, M., Witzel, G., Eckart, A., et al. 2011, A&A, 532, A26, doi: [`10.1051/0004-6361/201016134`](http://doi.org/10.1051/0004-6361/201016134)

(ref: Brinkerink2021) Brinkerink, C., Falcke, H., Brunthaler, A., & Law, C. 2021, arXiv e-prints, arXiv:2107.13402, doi: [`10.48550/arXiv.2107.13402`](http://doi.org/10.48550/arXiv.2107.13402)

(ref: Brinkerink2015) Brinkerink, C. D., Falcke, H., Law, C. J., et al. 2015, A&A, 576, A41, doi: [`10.1051/0004-6361/201424783`](http://doi.org/10.1051/0004-6361/201424783)

(ref: Broderick2022) Broderick, A. E., Gold, R., Georgiev, B., et al. 2022, ApJL, 930, L21, doi: [`10.3847/2041-8213/ac6584`](http://doi.org/10.3847/2041-8213/ac6584)

(ref: Capellupo2017) Capellupo, D. M., Haggard, D., Choux, N., et al. 2017, ApJ, 845, 35, doi: [`10.3847/1538-4357/aa7da6`](http://doi.org/10.3847/1538-4357/aa7da6)

(ref: Chatterjee2022) Chatterjee, K., & Narayan, R. 2022, ApJ, 941, 30, doi: [`10.3847/1538-4357/ac9d97`](http://doi.org/10.3847/1538-4357/ac9d97)

(ref: Chatterjee2021) Chatterjee, K., Markoff, S., Neilsen, J., et al. 2021, MNRAS, 507, 5281, doi: [`10.1093/mnras/stab2466`](http://doi.org/10.1093/mnras/stab2466)

(ref: Cheng2023) Cheng, X., Cho, I., Kawashima, T., et al. 2023, Galaxies, 11, 46, doi: [`10.3390/galaxies11020046`](http://doi.org/10.3390/galaxies11020046)

(ref: Cho2022) Cho, I., Zhao, G.-Y., Kawashima, T., et al. 2022, ApJ, 926, 108, doi: [`10.3847/1538-4357/ac4165`](http://doi.org/10.3847/1538-4357/ac4165)

(ref: CondonRansom2016) Condon, J. J., & Ransom, S. M. 2016, Essential Radio Astronomy

(ref: Dexter2014) Dexter, J., Kelly, B., Bower, G. C., et al. 2014, MNRAS, 442, 2797, doi: [`10.1093/mnras/stu1039`](http://doi.org/10.1093/mnras/stu1039)

(ref: Do2009) Do, T., Ghez, A. M., Morris, M. R., et al. 2009, ApJ, 691, 1021, doi: [`10.1088/0004-637X/691/2/1021`](http://doi.org/10.1088/0004-637X/691/2/1021)

(ref: Do2019) Do, T., Witzel, G., Gautam, A. K., et al. 2019, ApJL, 882, L27, doi: [`10.3847/2041-8213/ab38c3`](http://doi.org/10.3847/2041-8213/ab38c3)

(ref: DE2010) Dodds-Eden, K., Sharma, P., Quataert, E., et al. 2010, ApJ, 725, 450, doi: [`10.1088/0004-637X/725/1/450`](http://doi.org/10.1088/0004-637X/725/1/450)

(ref: DoddsEden2009) Dodds-Eden, K., Porquet, D., Trap, G., et al. 2009, ApJ, 698, 676, doi: [`10.1088/0004-637X/698/1/676`](http://doi.org/10.1088/0004-637X/698/1/676)

(ref: Eastman2010) Eastman, J., Siverd, R., & Gaudi, B. S. 2010, PASP, 122, 935, doi: [`10.1086/655938`](http://doi.org/10.1086/655938)

(ref: Eckart2009) Eckart, A., Baganoff, F. K., Morris, M. R., et al. 2009, A&A, 500, 935, doi: [`10.1051/0004-6361/200811354`](http://doi.org/10.1051/0004-6361/200811354)

(ref: Evans2010) Evans, I. N., Primini, F. A., Glotfelty, K. J., et al. 2010, ApJS, 189, 37, doi: [`10.1088/0067-0049/189/1/37`](http://doi.org/10.1088/0067-0049/189/1/37)

(ref: EHT2022a) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2022a, ApJL, 930, L12, doi: [`10.3847/2041-8213/ac6674`](http://doi.org/10.3847/2041-8213/ac6674)

(ref: EHT2022e) —. 2022b, ApJL, 930, L16, doi: [`10.3847/2041-8213/ac6672`](http://doi.org/10.3847/2041-8213/ac6672)

(ref: Fazio2018) Fazio, G. G., Hora, J. L., Witzel, G., et al. 2018, ApJ, 864, 58, doi: [`10.3847/1538-4357/aad4a2`](http://doi.org/10.3847/1538-4357/aad4a2)

(ref: Fragione2020) Fragione, G., & Loeb, A. 2020, ApJL, 901, L32, doi: [`10.3847/2041-8213/abb9b4`](http://doi.org/10.3847/2041-8213/abb9b4)

(ref: Fragione2022) —. 2022, ApJL, 932, L17, doi: [`10.3847/2041-8213/ac76ca`](http://doi.org/10.3847/2041-8213/ac76ca)

(ref: Fritz2011) Fritz, T. K., Gillessen, S., Dodds-Eden, K., et al. 2011, ApJ, 737, 73, doi: [`10.1088/0004-637X/737/2/73`](http://doi.org/10.1088/0004-637X/737/2/73)

(ref: Ciao2006) Fruscione, A., McDowell, J. C., Allen, G. E., et al. 2006, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 6270, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, ed. D. R. Silva & R. E. Doxsey, 62701V, doi: [`10.1117/12.671760`](http://doi.org/10.1117/12.671760)

(ref: Gravity2018) Gravity Collaboration, Abuter, R., Amorim, A., et al. 2018, A&A, 618, L10, doi: [`10.1051/0004-6361/201834294`](http://doi.org/10.1051/0004-6361/201834294)

(ref: Gravity2019) —. 2019, A&A, 625, L10, doi: [`10.1051/0004-6361/201935656`](http://doi.org/10.1051/0004-6361/201935656)

(ref: Gravity2020) GRAVITY Collaboration, Jiménez-Rosales, A., Dexter, J., et al. 2020a, A&A, 643, A56, doi: [`10.1051/0004-6361/202038283`](http://doi.org/10.1051/0004-6361/202038283)

(ref: Gravity2020orbit) GRAVITY Collaboration, Bauböck, M., Dexter, J., et al. 2020b, A&A, 635, A143, doi: [`10.1051/0004-6361/201937233`](http://doi.org/10.1051/0004-6361/201937233)

(ref: Abuter2021) GRAVITY Collaboration, Abuter, R., Amorim, A., et al. 2021, A&A, 654, A22, doi: [`10.1051/0004-6361/202140981`](http://doi.org/10.1051/0004-6361/202140981)

(ref: Grillmair2014) Grillmair, C. J., Carey, S. J., Stauffer, J. R., & Ingalls, J. G. 2014, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9143, Space Telescopes and Instrumentation 2014: Optical, Infrared, and Millimeter Wave, ed. J. Oschmann, Jacobus M., M. Clampin, G. G. Fazio, & H. A. MacEwen, 914359, doi: [`10.1117/12.2057238`](http://doi.org/10.1117/12.2057238)

(ref: Grillmair2012) Grillmair, C. J., Carey, S. J., Stauffer, J. R., et al. 2012, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 8448, Observatory Operations: Strategies, Processes, and Systems IV, ed. A. B. Peck, R. L. Seaman, & F. Comeron, 84481I, doi: [`10.1117/12.927191`](http://doi.org/10.1117/12.927191)

(ref: numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Herrnstein2004) Herrnstein, R. M., Zhao, J.-H., Bower, G. C., & Goss, W. M. 2004, AJ, 127, 3399, doi: [`10.1086/420711`](http://doi.org/10.1086/420711)

(ref: Hora2014) Hora, J. L., Witzel, G., Ashby, M. L. N., et al. 2014, ApJ, 793, 120, doi: [`10.1088/0004-637X/793/2/120`](http://doi.org/10.1088/0004-637X/793/2/120)

(ref: matplotlib) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Iwata2020) Iwata, Y., Oka, T., Tsuboi, M., Miyoshi, M., & Takekawa, S. 2020, ApJL, 892, L30, doi: [`10.3847/2041-8213/ab800d`](http://doi.org/10.3847/2041-8213/ab800d)

(ref: Lu2011) Lu, R. S., Krichbaum, T. P., Eckart, A., et al. 2011, A&A, 525, A76, doi: [`10.1051/0004-6361/200913807`](http://doi.org/10.1051/0004-6361/200913807)

(ref: Markoff2001) Markoff, S., Falcke, H., Yuan, F., & Biermann, P. L. 2001, A&A, 379, L13, doi: [`10.1051/0004-6361:20011346`](http://doi.org/10.1051/0004-6361:20011346)

(ref: Marrone2008) Marrone, D. P., Baganoff, F. K., Morris, M. R., et al. 2008, ApJ, 682, 373, doi: [`10.1086/588806`](http://doi.org/10.1086/588806)

(ref: pandas) McKinney, W. 2010, in Proceedings of the 9th Python in Science Conference, ed. Stéfan van der Walt & Jarrod Millman, 56 – 61, doi: [`10.25080/Majora-92bf1922-00a`](http://doi.org/10.25080/Majora-92bf1922-00a)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meyer2008) Meyer, L., Do, T., Ghez, A., et al. 2008, ApJL, 688, L17, doi: [`10.1086/593147`](http://doi.org/10.1086/593147)

(ref: Michail2021c) Michail, J. M., Wardle, M., Yusef-Zadeh, F., & Kunneriath, D. 2021a, ApJ, 923, 54, doi: [`10.3847/1538-4357/ac2d2c`](http://doi.org/10.3847/1538-4357/ac2d2c)

(ref: Michail2021b) Michail, J. M., Yusef-Zadeh, F., & Wardle, M. 2021b, MNRAS, 505, 3616, doi: [`10.1093/mnras/stab1529`](http://doi.org/10.1093/mnras/stab1529)

(ref: Michail2023) Michail, J. M., Yusef-Zadeh, F., Wardle, M., & Kunneriath, D. 2023, MNRAS, 520, 2644, doi: [`10.1093/mnras/stad291`](http://doi.org/10.1093/mnras/stad291)

(ref: Mossoux2017) Mossoux, E., & Grosso, N. 2017, A&A, 604, A85, doi: [`10.1051/0004-6361/201629778`](http://doi.org/10.1051/0004-6361/201629778)

(ref: Mossoux2016) Mossoux, E., Grosso, N., Bushouse, H., et al. 2016, A&A, 589, A116, doi: [`10.1051/0004-6361/201527554`](http://doi.org/10.1051/0004-6361/201527554)

(ref: Murchikova2021) Murchikova, L., & Witzel, G. 2021, ApJL, 920, L7, doi: [`10.3847/2041-8213/ac2308`](http://doi.org/10.3847/2041-8213/ac2308)

(ref: Nathanail2020) Nathanail, A., Fromm, C. M., Porth, O., et al. 2020, MNRAS, 495, 1549, doi: [`10.1093/mnras/staa1165`](http://doi.org/10.1093/mnras/staa1165)

(ref: Neilsen2013) Neilsen, J., Nowak, M. A., Gammie, C., et al. 2013, ApJ, 774, 42, doi: [`10.1088/0004-637X/774/1/42`](http://doi.org/10.1088/0004-637X/774/1/42)

(ref: Neilsen2015) Neilsen, J., Markoff, S., Nowak, M. A., et al. 2015, ApJ, 799, 199, doi: [`10.1088/0004-637X/799/2/199`](http://doi.org/10.1088/0004-637X/799/2/199)

(ref: LMFIT) Newville, M., Otten, R., Nelson, A., et al. 2023, lmfit/lmfit-py: 1.2.2, 1.2.2, Zenodo, doi: [`10.5281/zenodo.8145703`](http://doi.org/10.5281/zenodo.8145703)

(ref: Nowak2012) Nowak, M. A., Neilsen, J., Markoff, S. B., et al. 2012, ApJ, 759, 95, doi: [`10.1088/0004-637X/759/2/95`](http://doi.org/10.1088/0004-637X/759/2/95)

(ref: sklearn) Pedregosa, F., Varoquaux, G., Gramfort, A., et al. 2011, Journal of Machine Learning Research, 12, 2825

(ref: Peterson1998) Peterson, B. M., Wanders, I., Horne, K., et al. 1998, PASP, 110, 660, doi: [`10.1086/316177`](http://doi.org/10.1086/316177)

(ref: Ponti2015) Ponti, G., De Marco, B., Morris, M. R., et al. 2015, MNRAS, 454, 1525, doi: [`10.1093/mnras/stv1537`](http://doi.org/10.1093/mnras/stv1537)

(ref: Ponti2017) Ponti, G., George, E., Scaringi, S., et al. 2017, MNRAS, 468, 2447, doi: [`10.1093/mnras/stx596`](http://doi.org/10.1093/mnras/stx596)

(ref: Porth2021) Porth, O., Mizuno, Y., Younsi, Z., & Fromm, C. M. 2021, MNRAS, 502, 2023, doi: [`10.1093/mnras/stab163`](http://doi.org/10.1093/mnras/stab163)

(ref: Pringle1981) Pringle, J. E. 1981, ARA&A, 19, 137, doi: [`10.1146/annurev.aa.19.090181.001033`](http://doi.org/10.1146/annurev.aa.19.090181.001033)

(ref: Ressler2020a) Ressler, S. M., Quataert, E., & Stone, J. M. 2020a, MNRAS, 492, 3272, doi: [`10.1093/mnras/stz3605`](http://doi.org/10.1093/mnras/stz3605)

(ref: Ressler2020b) Ressler, S. M., White, C. J., Quataert, E., & Stone, J. M. 2020b, ApJL, 896, L6, doi: [`10.3847/2041-8213/ab9532`](http://doi.org/10.3847/2041-8213/ab9532)

(ref: Ripperda2020) Ripperda, B., Bacchini, F., & Philippov, A. A. 2020, ApJ, 900, 100, doi: [`10.3847/1538-4357/ababab`](http://doi.org/10.3847/1538-4357/ababab)

(ref: Scargle1998) Scargle, J. D. 1998, ApJ, 504, 405, doi: [`10.1086/306064`](http://doi.org/10.1086/306064)

(ref: Scargle2013) Scargle, J. D., Norris, J. P., Jackson, B., & Chiang, J. 2013, ApJ, 764, 167, doi: [`10.1088/0004-637X/764/2/167`](http://doi.org/10.1088/0004-637X/764/2/167)

(ref: Subroweit2017) Subroweit, M., Garcı́a-Marı́n, M., Eckart, A., et al. 2017, A&A, 601, A80, doi: [`10.1051/0004-6361/201628530`](http://doi.org/10.1051/0004-6361/201628530)

(ref: PYCCF) Sun, M., Grier, C. J., & Peterson, B. M. 2018, PyCCF: Python Cross Correlation Function for reverberation mapping studies. [`http://ascl.net/1805.032`](http://ascl.net/1805.032)

(ref: VDL1966) van der Laan, H. 1966, Nature, 211, 1131, doi: [`10.1038/2111131a0`](http://doi.org/10.1038/2111131a0)

(ref: scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Weldon2023) Weldon, G. C., Do, T., Witzel, G., et al. 2023, arXiv e-prints, arXiv:2308.09749, doi: [`10.48550/arXiv.2308.09749`](http://doi.org/10.48550/arXiv.2308.09749)

(ref: Wielgus2022a) Wielgus, M., Marchili, N., Martı́-Vidal, I., et al. 2022, ApJL, 930, L19, doi: [`10.3847/2041-8213/ac6428`](http://doi.org/10.3847/2041-8213/ac6428)

(ref: BBlocks) Williams, P. K. G., Clavel, M., Newton, E., & Ryzhkov, D. 2017, pwkit: Astronomical utilities in Python. [`http://ascl.net/1704.001`](http://ascl.net/1704.001)

(ref: Witzel2012) Witzel, G., Eckart, A., Bremer, M., et al. 2012, ApJS, 203, 18, doi: [`10.1088/0067-0049/203/2/18`](http://doi.org/10.1088/0067-0049/203/2/18)

(ref: Witzel2018) Witzel, G., Martinez, G., Hora, J., et al. 2018, ApJ, 863, 15, doi: [`10.3847/1538-4357/aace62`](http://doi.org/10.3847/1538-4357/aace62)

(ref: Witzel2021) Witzel, G., Martinez, G., Willner, S. P., et al. 2021, ApJ, 917, 73, doi: [`10.3847/1538-4357/ac0891`](http://doi.org/10.3847/1538-4357/ac0891)

(ref: Yuan2016) Yuan, Q., & Wang, Q. D. 2016, MNRAS, 456, 1438, doi: [`10.1093/mnras/stv2778`](http://doi.org/10.1093/mnras/stv2778)

(ref: FYZ2006) Yusef-Zadeh, F., Roberts, D., Wardle, M., Heinke, C. O., & Bower, G. C. 2006a, ApJ, 650, 189, doi: [`10.1086/506375`](http://doi.org/10.1086/506375)

(ref: FYZ2010) Yusef-Zadeh, F., Wardle, M., Bushouse, H., Dowell, C. D., & Roberts, D. A. 2010, ApJL, 724, L9, doi: [`10.1088/2041-8205/724/1/L9`](http://doi.org/10.1088/2041-8205/724/1/L9)

(ref: FYZ2008) Yusef-Zadeh, F., Wardle, M., Heinke, C., et al. 2008, ApJ, 682, 361, doi: [`10.1086/588803`](http://doi.org/10.1086/588803)

(ref: FYZ2011) Yusef-Zadeh, F., Wardle, M., Miller-Jones, J. C. A., et al. 2011, ApJ, 729, 44, doi: [`10.1088/0004-637X/729/1/44`](http://doi.org/10.1088/0004-637X/729/1/44)

(ref: YusefZadeh2006a) Yusef-Zadeh, F., Bushouse, H., Dowell, C. D., et al. 2006b, ApJ, 644, 198, doi: [`10.1086/503287`](http://doi.org/10.1086/503287)

(ref: FYZ2006a) —. 2006c, ApJ, 644, 198, doi: [`10.1086/503287`](http://doi.org/10.1086/503287)

(ref: FYZ2009) Yusef-Zadeh, F., Bushouse, H., Wardle, M., et al. 2009, ApJ, 706, 348, doi: [`10.1088/0004-637X/706/1/348`](http://doi.org/10.1088/0004-637X/706/1/348)

[^1]: <https://casaguides.nrao.edu/index.php?title=CASA_Guides:Polarization_Calibration_based_on_CASA_pipeline_standard_reduction:_The_radio_galaxy_3C75-CASA5.6.2>

[^2]: <https://astroutils.astronomy.osu.edu/time/bjd2utc.html>

[^3]: <https://pwkit.readthedocs.io/en/latest/science/pwkit-bblocks/>

[^4]: <https://stochastic.readthedocs.io/en/stable/index.html>

</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "HST data calibration details",
  "failed_quote": "we refer to (cite: Mossoux2016) for further details."
 }
]
```
