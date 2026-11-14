# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026MNRAS.545f2150S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# HD 44892: The youngest (or oldest?) gas-harbouring debris disc around an intermediate mass star

## Abstract

We present the first detections of gas around a 2.1 Myr old debris disc-bearing intermediate-mass star, HD 44892. Gas is detected both in $^{12}$CO (2-1) emission through ALMA Band 6 observations and in absorption in Ca II K and H, seen with high-resolution UVES spectroscopy. $^{13}$CO and C$^{18}$O (2-1) are not detected. The star exhibits a 12 $\mu$m fractional excess of $7.86^{+0.11}_{-2.27}$, placing it in the transition stage between protoplanetary and debris discs. Our detection of 1.3 mm emission yields the dust mass of 0.019 $\pm$ 0.009 M$_{\oplus}$ assuming 115 K temperature. The $^{13}$CO non-detection places an upper limit on CO gas mass of $\sim$10$^{-2}$ $M_{\oplus}$. The $^{12}$CO detection yields a CO gas mass of (7.86 $\pm$ 2.05) $\times$ 10$^{-5}$ $M_{\oplus}$ or (1.62 $\pm$ 0.17) $\times$ 10$^{-4}$ $M_{\oplus}$ assuming a gas temperature of 20 K or 50 K, respectively. These should be considered as lower limits since $^{12}$CO emission may be optically thick. With UVES, we find variability in Ca II K and H lines, which can be interpreted by transiting circumstellar gas, ruling out interstellar absorption as their origin. Both the dust mass, which is within an order of magnitude of HD 141569, and the gas mass derived here indicate a late gas dispersal stage of the protoplanetary disc. Through our analysis we deem the alternative age of 800 Myr unlikely.

protoplanetary discs – submillimetre: planetary systems – stars: pre-main-sequence – circumstellar matter – planets and satellites: formation

# Introduction

While the dust content of debris discs has been extensively studied, less is known about the presence of gas. Numerous papers have searched for and examined this gas presence (cite: Rebollido2022The36546; Moor2017MolecularStars; Cataldi2023PrimordialALMA; Hales2022ALMADisk; Marino2016ExocometaryRing; Moor2019New32297; Iglesias2018DebrisOrigin); however, many questions remain unanswered. Perhaps the biggest question of all is: where does this gas come from? Two main scenarios have been proposed. This gas is either primordial, leftover from the parent protoplanetary disc, or secondary, produced alongside dust, through processes such as planetesimal collisions, volatile sublimation, and photodesorption (cite: Hughes2018DebrisVariability). Recent findings regarding the shielding effects in discs suggest that CO gas may accumulate in relatively high amounts from secondary means alone (cite: Kral2019ImagingDiscs). Nonetheless, the primordial origin has not yet been disproved, especially as the effects of gas mixing complicate the case for the secondary gas scenario, making shielding less efficient (cite: Marino2022VerticalLifetime), and models of (cite: Nakatani2021PhotoevaporationRemnants) suggest that, in case of A-type stars, the gas can survive as a protoplanetary remnant.

![](Plots/histogramSpTgasDebrisDiscs.png)

As of August 2025, 45 debris discs containing gas have been discovered either through gas emission or absorption. Over 20 of them have been observed with ALMA to search for CO and other gas emission, a full list of which can be found in Table [\[tab:allCOGasDetections\]](#tab:allCOGasDetections). Interestingly, the majority of all gas detections in debris discs have been around A-type stars (see Figure [1](#fig:histogramAllDetections)). For most of these systems, secondary origin models can readily explain the observed low CO gas masses. However, a few systems, such as 49 Cet (cite: Moor2019New32297; Pearce2022PlanetDiscs), HD 21997 (cite: Kospal2013ALMA21997; Moor2013ALMA21997), HD 141569 (cite: Miley2018Unlocking141569), and HD 32297 (cite: Moor2019New32297), which are intermediate-mass stars, exhibit significantly higher CO gas masses, which the current secondary models are not able to fully explain. In these cases, the origin of the gas is proposed to be primordial or a mixture of primordial and secondary (cite: Cataldi2023PrimordialALMA). Secondary origin is most certain around older systems, such as the 440 Myr Fomalhaut (cite: Matra2017ExocometaryObservations) or the 1-2 Gyr $\eta$ Crv (cite: Marino2017ALMAPlanets), where primordial gas cannot survive over such long timescales. $\beta$ Pic, despite its younger age of $\sim$20 Myr, is another example of a system with secondary gas, in which gas produced in planetesimal collisions and the destruction of volatile bodies has been observed (cite: Dent2014MolecularDisk; Matra2017DetectionComets).

The primordial origin has been suggested for discs where the gas is present in substantial amounts - quantities that are not yet fully explainable by models of secondary origin - and where the parent star is very young (cite: Nakatani2021PhotoevaporationRemnants), hence the gas might not have yet been fully cleared from the system (cite: Smirnov-Pinchukov2022LackGas). Such is the case for HD 141569 (cite: Miley2018Unlocking141569), a 5 Myr star harbouring a ‘hybrid’ disc, name used for gas-bearing discs with protoplanetary disc levels of likely primordial gas, but debris-disc levels of secondary dust. These discs are similar to dusty debris discs but retain some primordial gas from the earlier evolutionary stage, hence are hybrid between protoplanetary and debris discs (cite: Pericaud2017TheDisks). The dissipation of primordial gas is still ongoing in these systems, placing them just at the end of protoplanetary disc dispersal. In the case of HD 141569, the dust is of secondary origin or mixed, with a relatively low dust mass and IR excess for a protoplanetary disc but high for a debris disc (Figure [2](#fig:DustAgeEvolution)), while the gas is suspected to be primordial and at a mass comparable to the least-massive protoplanetary discs (PPDs). HD 141569 is thus the only known gas-harbouring debris disc found around a pre-main-sequence (pre-MS) intermediate-mass star (IMS) with a measured CO mass to date.

![](Plots/DustMassExcessVsAgeTogether.png)

# HD 44892

In this paper, we present ALMA observations of HD 44892 (also known as HIP 30414), an A9/F0IV type star (cite: Wenger2000TheDatabase) located 191 $\pm$ 1 pc away (cite: Vallenari2023iGaia/i3; Prusti2016TheMission). HD 44892 has a temperature of 7500 $\pm$ 500K, a luminosity of 60.0 $\pm$ 20.0 $L_{\odot}$, stellar mass of 2.87 $^{+0.67}_{-0.41}$ $M_{\odot}$, and an age of 2.1 $^{+1.2}_{-1.0}$ Myr (cite: Iglesias2023X-shooterEvolution). The pre-MS star HD 44892 has undergone the transition from convective to radiative structure at $\sim$1 Myr. (cite: Gontcharov2006PulkovoSystem) have calculated the radial velocity of the star to be 20.9 $\pm$ 0.6 km s$^{-1}$, which is the value adopted in this study. A more recent estimate yields a value of 20.88 $\pm$ 1.85 km s$^{-1}$ (D. Iglesias, priv. comm.), which is consistent with previous findings. There are no mentions in the literature suggesting HD 44892 is part of a binary or multiple star system; it is also a field star (cite: Gagne2018BANYAN.Pc).

(cite: Ishihara2017FaintIRSF) identified it as a warm debris disc candidate based on its IR excess at 18 $\mu$m found through spectral energy distribution (SED) fitting, and it was first identified as a hybrid disc candidate in (cite: Iglesias2023X-shooterEvolution). HD 44892 has a fractional IR excess at 12 $\mu$m of 7.86 $^{+0.11}_{-2.27}$ (cite: Iglesias2023X-shooterEvolution), placing it between debris ($3<F_{12\mu m}/F_{star}$) and protoplanetary ($F_{12\mu m}/F_{star}>25$) discs (cite: Wyatt2015FiveDisk; Iglesias2023X-shooterEvolution), where also a number of gas-bearing debris discs have been found (Figure [2](#fig:DustAgeEvolution), right).

There is a disagreement in the literature regarding the stellar parameters of HD 44892, particularly about its age. Its location on the HR diagram can be fit by either pre- or post-MS tracks. Past studies, such as (cite: Zorec2012RotationalStars) and (cite: Bochanski2018FundamentalGaia), have classified it as a post-MS object ($\sim$570-580 Myr with a mass of 2.50-2.60 $M_{\odot}$). (cite: Iglesias2023X-shooterEvolution) present the fit to the pre-MS tracks yielding the 2.1 Myr and an alternative fit to the post-MS tracks with 800 Myr, with a mass of 2.29 $M_{\odot}$. They conclude that the possibility of the older age is less likely. In this paper, we adopt the pre-MS age of 2.1 Myr and present arguments against the alternative age of 800 Myr in later sections.

# ALMA

## ALMA observations and data reduction

HD 44892 was observed using the ALMA (Atacama Large Millimeter/submillimeter Array) 12 m array on 15th January 2023 (PI Panić, ID 2022.1.01686.S). Observations were taken across four spectral windows (SPWs) in Band 6, searching for both continuum and gas emission. The target was observed for a total of 34 minutes and 25 seconds using 46 operational antennas, with minimum and maximum baselines of 15.3 m and 783.5 m, respectively. J0423-0120 was used as the flux calibrator and J0609-1542 as the phase calibrator.

Band 6 transitions of CO were observed, including the 2-1 transitions of ${}^{12}\text{CO}$ in a SPW of 1920 channels of width 244.141 kHz and a central frequency of 230 517 MHz, resulting in a resolution of 0.32 km s$^{-1}$. ${}^{13}\text{CO}$ and $\text{C}^{18}\text{O}$ SPW has 1920 channels of width 976.562 kHz and a central frequency of 219 980 MHz, which gives a spectral resolution of 1.33 km s$^{-1}$. The remaining two spectral windows, of central frequencies 216 980 MHz and 232 979 MHz, were dedicated to continuum emission. Each of these windows contains 128 channels of width 15 625 kHz.

We processed all of the data using CASA 6.5.4-9 (cite: McMullin2007CASAApplications) and CARTA 4.0.0 (cite: Comrie2018CARTA:Astronomy). Continuum emission of HD 44892 was imaged using the task ‘tclean’ with Briggs weighting and a robust parameter set to 0.3, which we found to provide the highest signal-to-noise ratio and source emission over the range of -2 to 2 explored. Our target’s emission fits entirely in the region where primary beam is maximum, hence no primary beam correction was applied. No self-calibration was applied to the data as the source is too weak in continuum to provide reliable phase or amplitude solutions.

For line data, we used the CASA task ‘uvcontsub’ to subtract the continuum from the line emission data. Using the ‘plotms’ task (amplitude vs channel), we identified SPWs and frequencies at which line emission was potentially present. We imaged both SPWs using the ‘tclean’ task with Briggs weighting and a robust parameter set to 0.3, which produced the highest signal-to-noise ratio for the $^{12}$CO detection. We did not detect any emission in the individual channels of the SPW containing ${}^{13}$CO and C$^{18}$O.

## ALMA results

### Continuum

![](Plots/HD44892cont3sigma.png)

![](Plots/ContMargResolved.png)

For continuum of HD 44892 our data reduction resulted in a synthesised beam size of 0.44$''$ (84 au) $\times$ 0.38$''$ (72 au) at a position angle (PA) of $-70.7\degree$. We detected continuum emission of 0.136 $\pm$ 0.016 mJy ($\sim$9 $\sigma$), shown in Figure [3](#fig:HD44892dust). The continuum flux was measured only from inside the 3 $\sigma$ contour. Using task ‘imfit’, which is part of the CASA package, we found that the continuum emission of HD 44892 is marginally resolved, as the fitted Gaussian component has a FWHM of major axis of 0.58$''$ $\pm$ 0.08$''$, 110 au, which extends beyond that of the beam (0.43$''$, 82 au, measured in the same direction). The drop in amplitude at longest UV distances (Figure [4](#fig:ContMargResolved)), confirms that the most extended emission from the source is being resolved.

The continuum emission appears to be offset from the position of HD 44892 (see Figure [3](#fig:HD44892dust)). To determine the underlying cause of this apparent offset, we calculated the astrometric accuracy of ALMA[^2] using Equation [\[eq:PosAcc\]](#eq:PosAcc):

$$\begin{equation}
 \label{eq:PosAcc}

\sigma_{\mathrm{pos}} = \frac{\theta_{\mathrm{FWHM}}}{0.9 \times \mathrm{SNR}}
\end{equation}$$

where $\theta_{\mathrm{FWHM}}$ is the full width at half maximum (FWHM) of the synthesized beam, and SNR is the signal-to-noise ratio of the peak target flux. For our data we found $\sigma_{\mathrm{pos}}$ = 45 milliarcseconds. The apparent offset of the continuum emission from the stellar position is 34 milliarcseconds, which is less than the calculated $\sigma_{\mathrm{pos}}$, suggesting that it is most likely due to the limited astrometric accuracy rather than physical displacement.

### Gas

![](Plots/HD44892finalProfileGaussianSum.png)

For ${}^{12}$CO emission, the resulting synthesized beam size is 0.46$''$ (88 au) $\times$ 0.40$''$ (76 au), at a PA of -80.6$\degree$. Figure [5](#fig:HD44892velStructure) shows the spectrum of the detected gas emission, which has the typical double-peaked profile associated with gas rotating in a Keplerian disc. Fitting a double-peaked Gaussian curve to this spectrum reveals a midpoint at $v={\sim}0$ km s$^{-1}$. The first peak is at -5.45 km s$^{-1}$ and the second at 6.75 km s$^{-1}$. This x-axis of this plot has been corrected for the star’s radial velocity in the LSR frame of ${\sim}1.5km\,s^{-1}$.

From moment 0 (Figure [6](#fig:HD44892gas), integrated intensity made using the CASA task ‘immoments’ within range -8.49-15.33 km s$^{-1}$) we found an integrated line flux of 96.92 $\pm$16.22 mJy km s$^{-1}$ ($\sim$6.0 $\sigma$). Therefore, we decided to re-image the data, this time binning three channels together during tclean (nchan = 3). This reduced the noise in our image and made the emission more prominent. The moment 0 map was made using the same velocity range as in the non-binned case, resulting in a slightly lower noise of 14.10 mJy km s$^{-1}$, and the integrated line flux of 93.06 mJy km s$^{-1}$, improving the signal-to-noise (6.6 $\sigma$).

We then also used the Keplerian Mask tool[^3], which produces a rotating mask based on the system’s parameters that a Keplerian disc should follow. To search the parameter space to be used in the tool, we are guided by the aspect ratio of the deconvolved disc size. We used the ‘imfit’ task and obtained the deconvolved Gaussian parameters: 0.34$''$ $\pm$ 0.10$''$ for the major axis and 0.19$''$ $\pm$ 0.08$''$ for the minor axis (PA of 76.2 $\pm$ 63.4$\degree$). This suggests an inclination of 56.1 $\pm$ 19.9$\degree$. We therefore varied the inclination from 36$\degree$ to 76$\degree$ in the Keplerian Mask tool. The stellar mass range was adopted from (cite: Iglesias2023X-shooterEvolution) as 2.87 $^{+0.67}_{-0.41}M_{\odot}$ and Keplerian rotation computed accordingly in the tool. Using these values as initial constraints, we explored combinations of the parameters (within their uncertainty ranges) to best match the $^{12}$CO emission of HD 44892. The parameters that resulted in the best fit were an inclination of 40$\degree$, PA of 17.2$\degree$, stellar mass of 3.27 $M_{\odot}$, and an outer radius of 0.4$''$ (76 au). The $^{12}$CO emission follows this rotation, indicating that the emission lines up with theoretical positions and confirming it is from a disc rotating around the parent star (Figure [7](#fig:KeplerianMask)). Using the Keplerian Mask during cleaning has improved the signal-to-noise once more, in moment 0 this resulted in an integrated line flux ($F_{21}$) of 95.47 $\pm$ 13.49 mJy km s$^{-1}$ (7.1 $\sigma$, Figure [6](#fig:HD44892gas)). Here we used channels where gas emission was most prominent, corresponding to the frequency range of 230.5262 GHz (15.33 km s$^{-1}$) to 230.5445 GHz (-8.49 km s$^{-1}$).

Knowing the channels (velocities) at which $^{12}$CO emission is present, we created a moment 0 map for the SPW containing $^{13}$CO and C$^{18}$O. The emission from these isotopes would allow for a more precise CO gas mass calculation, as they are likely optically thin, ensuring the $^{12}$CO emission traces molecular density, rather than being convoluted with temperature effects. Since no emission was visible in the individual channels of this spectral window, we used the same velocity range as for $^{12}$CO. However, this has resulted in a non-detection of both $^{13}$CO and C$^{18}$O.

![](Plots/Mom0contounsOnMom1.png)

![](Plots/KeplerianMask.png)

Figure [6](#fig:HD44892gas) shows the full extent of ${}^{12}$CO gas emission (contour levels) overlaid on the velocity distribution of the disc. The visible velocity gradient, from red- to blue-shifted, indicates gas rotation. This, along with the disc being located around the star’s position, confirms the gas is rotating around the star and the emission is not from a different source. The gas emission appears compact and follows the beam shape, with the highest intensity near the centre, as expected for a spatially unresolved source.

# UVES

![](Plots/finalHD44892AllLines.png)

## UVES observations and data reduction

We obtained high-resolution observations of HD 44892 using UVES (Ultraviolet and Visual Echelle Spectrograph; (cite: Dekker2000DesignObservatory)) at the VLT (Very Large Telescope), on 13th and 27th September 2023 (PI Iglesias, ID 112.262P.001). VLT is part of the European Southern Observatory and is located in Cerro Paranal in Chile. Data was taken in both Blue and Red arms, centred at 390 nm and 580 nm, respectively. We used the 0.5$''$ for these observations to achieve high resolution (R$\sim$74000 for the Red arm and R$\sim$65000 for the Blue arm). HD 44892 was observed each time for 1 minute 48 seconds. Data of one of the comparison stars used, HIP 28877, is part of the same observing programme. The observations were reduced using the UVES EsoReflex pipeline (cite: Ballester2000ThePipeline; Freudling2013AutomatedAstronomy) version 6.4.1.

Additional spectra from the ESO archive[^4] were obtained for two other comparison stars (HD 43544, HD 46035), using high-resolution spectrographs HARPS (cite: Mayor2003SettingHARPS) and FEROS (cite: Kaufer1999CommissioningLa-Silla.) at the La Silla Observatory. These were science-ready products from the ESO archive and reduced with each instrument standard pipeline. We used Molecfit (cite: Smette2015Molecfit:Correction; Kausch2015Molecfit:Correction) to correct for telluric contamination as the region around the Na I doublet is highly affected by the Earth’s atmosphere. Barycentric radial velocity corrections were also applied to the spectra.

## UVES results

Using data from the UVES spectrograph, we also searched for gas absorption towards HD 44892, particularly in the Ca II K & H, and Na I D1 & D2 lines. By fitting Kurucz model spectra to the stellar spectrum of our target, we identified a narrow absorption feature, located at 22.5 km s$^{-1}$ (36 $\sigma$, Figure [8](#fig:AbsAndSkyMap)). Although this feature does not correlate with the radial velocity of any known gas clouds in the line of sight and falls within the stellar radial velocity range of 20.88 $\pm$ 1.85 km s$^{-1}$, it is matched well by several of the nearby comparison stars. Interstellar origin of this feature is further supported by its strength in both of the sodium lines, which are a strong indication of interstellar medium (ISM) gas presence. The detailed description of methods used and analysis of the absorption features of this and other objects will be published in Szewczyk et al. (in prep).

There is, however, some variability in the residual flux present in both Ca II K and H lines (Figure [8](#fig:AbsAndSkyMap)), which is not present in the sodium lines. This variability does not match with any of the clouds in the line of sight nor the nearby comparison stars. While not at the radial velocity of the parent star, this variability in the residual absorption might be caused by secondary gas released from volatile bodies like in case of $\beta$ Pic (cite: Dent2014MolecularDisk) or a gas wind-disc, like the one found around NO Lup (cite: Lovell2021RapidDisc), although this cannot be confirmed with the data we currently have. Thus, it is possible we have detected variable, circumstellar gas around HD 44892.

Following the methods described in (cite: Fairlamb2017ALines) we calculated the mass accretion rate of HD 44892 from the H$\alpha$ spectrum. We found accretion rates of $\log\dot{M}_{acc}$ = -7.64$^{+0.11}_{-0.07}$$\,M_{\odot}\,yr^{-1}$ and $\log\dot{M}_{acc}$ = -7.69$^{+0.11}_{-0.07}$ $M_{\odot}\,yr^{-1}$ for the two observed epochs, which are consistent with those of other Herbig Ae/Be stars (cite: Wichittanakom2020TheStars). This further suggests that HD 44892 is a pre-MS star, with an estimated age of 2.1 Myr, as accretion is characteristic of young stellar objects. Variability is also observed in the H$\alpha$ line (Szewczyk et al., in prep), similar to that seen in the Ca II K & H lines. Hence, the derived accretion rate may correspond to a temporary phase of high accretion and should therefore be regarded as an approximate estimate.

# Analysis & discussion

## ALMA

### Continuum

The continuum emission we have detected around HD 44892 is only marginally resolved along the major axis. Because of this, we are unable to estimate the orbital distance to the debris disc using our current data, and hence cannot determine the dust temperature, on which dust mass depends. To provide a more reliable estimate of the dust mass, we have utilised the ‘simalma’ task, which is part of CASA package. We first created models, each containing a circular dust ring at various disc inclinations, located at a range of orbital distances from the star (with disc radii extending to 20-100 au along the major axis), which we then input into ‘simalma’. Because the continuum emission is only marginally resolved, we did not consider the ring width as a free parameter and fixed it to 1 px (0.2 au), small enough to not influence the fit. The aim of our approach was to determine the dust ring size that would best mimic our observations - effectively, the maximum radius at which the dust can be placed without the belt becoming resolved. The simulations were carried out using the exact same observational setup as our real continuum observations - including observing time, precipitable water vapour (pwv), frequency, antenna setup, and other parameters - in order to accurately replicate the noise, resolution, and observed flux.

We used the CASA task ‘imfit’ to compare the simulated images to the actual data, and found that a ring located approximately 40-45 au from the star best reproduced the observed emission. Since the minor axis is not resolved, we cannot give an estimate to its size. Based on this distance, assuming the dust particles behave as black bodies, we estimated the dust temperature using Equation [\[eq:Distance\]](#eq:Distance):

$$\begin{equation}
\label{eq:Distance}
    R=\sqrt{\frac{L_{\odot}}{16\pi\sigma T^{4}}}
\end{equation}$$

where R is the distance from the parent star to the debris belt, $L_{\odot}$ is the stellar luminosity, $\sigma$ is the Stefan-Boltzmann constant, and $T$ is the dust belt temperature. A debris belt distance of 40-45 au corresponds to a dust temperature of $\sim$115 K.

We calculated the minimum dust mass of HD 44892 assuming optically thin, thermal emission, with Equation [\[eq:DustMass\]](#eq:DustMass):

$$\begin{equation}
 \label{eq:DustMass}
M_{dust} = \frac{F_{\nu} \times D^{2}}{B_{\nu}(T) \times \kappa_{\nu}}
\end{equation}$$

where $F_{\nu}$ is the source emission, $D$ is the distance to the source, $B_{\nu}(T)$ is the Planck function (dependent on dust temperature, $T$), and $\kappa_{\nu}$ is the dust opacity, which is very uncertain. Here, we assume $\kappa=0.1\times2.3\times(\frac{\nu}{230\times10^9})^{0.7}$ \[cm$^{2}$ g$^{-1}$\] (cite: Beckwith1990), where $\nu$ is the frequency of observations \[Hz\]. This results in a minimum dust mass at the dust temperature of 115 K of 0.019 $\pm$ 0.009 M$_{\oplus}$. This mass is highly dependent on the dust temperature, which is uncertain given the emission is only marginally resolved along the major axis. For comparison, a lower dust temperature of 50 K would yield a higher dust mass estimate of 0.05 $\pm$ 0.03$M_{\oplus}$.

Based on the expected lifetime of the observed dust, we can estimate whether it is primordial (left over from system formation) or secondary (released in planetesimal collisions). In the absence of gas, the lifetime of millimetre dust would be dominated by grain-grain collisions. The longest timescale at which this amount of millimetre dust can be destroyed, assuming collisions with dust of the same size, is if we distribute it in the entire region up to 40-45 au. In this scenario, following (cite: Pearce2021Fomalhaut) (cite: Wyatt2002Collisions) we obtain the dust lifetime of order $10^{-2}$ Myr, which is much smaller than the estimated age of HD 44892. Whilst the derived lifetime could be extended in the presence of gas, which can damp grains and reduce their impact velocities, very significant damping would be required to extend the lifetime up the the ${2\text{\,Myr}}$ star age. Hence the estimated lifetime, combined with the relatively low dust mass compared to protoplanetary discs (Figure [2](#fig:DustAgeEvolution)), leads us to believe that at least some of the dust is secondary in nature. This is typical for hybrid discs, which are thought to comprise primordial gas and second-generation dust (e.g. (cite: Kospal2013ALMA21997; Moor2013ALMA21997)).

### Gas

To calculate the CO gas mass in this disc we follow methods described in (cite: Miley2019Asymmetric100546) and (cite: Matra2015COALMA). Since our detection is in ${}^{12}$CO (2-1) only, we use Equation [\[eq:GasMass\]](#eq:GasMass) to calculate the minimum CO gas mass, assuming local thermodynamic equilibrium:

$$\begin{equation}
 \label{eq:GasMass}
M_{CO}=\frac{4\pi m d^{2}}{h\nu_{21}A_{21}}\frac{F_{21}}{x_{2}}
\end{equation}$$

where $F_{21}$ is the integrated flux of gas emission, $d$ is the distance to the star, $m$ is the mass of the emitting molecule (${}^{12}$CO), $\nu_{21}$ is the rest frequency of the transition, $h$ is Planck’s constant, $A_{21}$ is the appropriate Einstein coefficient, and $x_{2}$ is the fraction of the population found in the upper level of the transition (in this case ‘2’), estimated using a Boltzmann distribution. Since the gas emission is spatially unresolved, we cannot estimate its temperature. Using the flux measured for $^{12}$CO emission, for 20 K gas we obtain a minimum CO gas mass of (7.86 $\pm$ 2.05) $\times$ 10$^{-5}$ $M_{\oplus}$ or (1.62 $\pm$ 0.17) $\times$ 10$^{-4}$ $M_{\oplus}$ assuming warmer gas at 50 K.

Given the young age of HD 44892 and its transitional stage from a protoplanetary to a debris disc, the primordial origin of gas cannot be ruled out (cite: Nakatani2021PhotoevaporationRemnants). Primordial gas is leftover from the protoplanetary stage, where it is dominated by the ISM-like abundances of molecular hydrogen (H$_{2}$), with carbon monoxide (CO) along other gases contributing to the total gas mass. Assuming the disc is hybrid, we use the ISM ratio of ${}^{12}\text{CO}$/H$_{2}$=$10^{-4}$ to estimate the total gas mass in this disc, under the assumption of a substantial hydrogen presence in the disc. If the gas is indeed primordial, we estimate the H$_{2}$ mass, and hence total disc gas mass, to be 0.06 $\pm$ 0.02 $M_{\oplus}$ for 20 K gas and 0.12 $\pm$ 0.01 $M_{\oplus}$ for 50 K gas. These estimates are based on the lower limit of CO gas mass (estimated from ${}^{12}\text{CO}$ emission), hence the total gas mass in this disc may be higher.

From the moment 0 map made for the two non-detections, ${}^{13}$CO and C$^{18}$O, we derived upper limits to the CO gas mass. By overlaying the 3 $\sigma$ contours of ${}^{12}$CO emission on this map, we derived the RMS within this region to be 30.28 mJy km s$^{-1}$, with 3$\sigma=90.84$ mJy km s$^{-1}$, which we use as $^{13}$CO and C$^{18}$O flux for the purpose of gas mass calculations, since the dataset is common between them. We adopt the ISM-like relative ratios of CO/$^{13}$CO and CO/C$^{18}$O as 77 and 550, respectively (cite: Wilson1994AbundancesMedium). Using Equation [\[eq:GasMass\]](#eq:GasMass) with adjusted values for $m$ and $x_{2}$, we obtained the upper limits to the CO gas mass as presented in Table [1](#tab:UpperLimits). However, since in debris discs $^{13}$CO is typically more abundant than C$^{18}$O (cite: Miley2018Unlocking141569), the upper limit on the CO gas mass derived from $^{13}$CO is more stringent. The total CO gas mass in the debris disc of HD 44892 should hence be contained between the lower limits from the $^{12}$CO emission and upper limits from $^{13}$CO non-detection.

| In units of $M_{\oplus}$: | $^{13}$CO | C$^{18}$O | $^{12}$CO |
|:---|:---|:---|:---|
| $M_{CO}$ (20K) | \<7.09 $\times$ 10$^{-3}$ | \<5.27 $\times$ 10$^{-2}$ | (7.86 $\pm$ 2.05) $\times$ 10$^{-5}$ |
| $M_{CO}$ (50K) | \<1.47 $\times$ 10$^{-2}$ | \<1.10 $\times$ 10$^{-1}$ | (1.62 $\pm$ 0.17) $\times$ 10$^{-4}$ |
| $M_{H_{2}}$ (20K) | \<5.06 | \<37.67 | 0.06 $\pm$ 0.02 |
| $M_{H_{2}}$ (50K) | \<10.51 | \<78.30 | 0.12 $\pm$ 0.01 |

: Upper limits to CO and total gas mass derived from $^{13}$CO and C$^{18}$O non-detections, and lower limits from $^{12}$CO emission.

### Gas and dust emission morphology

![](Plots/GasDustOverlay.png)

Examining the structure of both the continuum and $^{12}$CO emission (Figure [9](#fig:HD44892gasCont)), we can see that the dust emission clearly has a different morphology than the $^{12}$CO emission. This direct comparison in their morphology is possible because of the similar signal-to-noise ratio of both dust and $^{12}$CO emission. The $^{12}$CO integrated emission is not spatially resolved, therefore it follows the beam distribution. As mentioned in Section [3.2.1](#sec:dustFlux), the continuum emission is marginally resolved, which can be further seen in Figure [4](#fig:ContMargResolved). Here, the longest UV-distance baselines, at $\sim$800 m, deviate from a flat profile, which indicates the continuum emission is not unresolved, since a point-like source would have a constant amplitude across all baselines. The extended continuum emission is only marginally resolved with an apparent asymmetry at a level of 4.5 $\sigma$, which may or may not indicate asymmetry in the dust disc. The larger extent of continuum emission with respect to CO emission is atypical in protoplanetary discs, and more common in debris discs (cite: PPVII2023; Moor2019New32297; DiFolco2020). Higher resolution observations are necessary to ascertain the distribution of dust and CO gas in the HD 44892 system.

## SED

![](Plots/SEDs7000K7500K8000K.png)

Figure [10](#fig:SED) shows the SED of the HD 44892 debris disc, assuming optically thin dust. The excess emission is best modelled with a single-temperature belt structure, fitted using a blackbody model. Due to the uncertainties in the temperature of the parent star T$_{eff}$ = 7500 $\pm$ 500 K, we present the SED fit to the stellar temperature of 7500 K along with the alternative minimum and maximum values of 7000 K and 8000 K. The fit to the excess is highly dependent on the assumed stellar temperature, changing the resultant dust-belt temperatures. The best-fit SED (left plot of Figure [10](#fig:SED), 7000 K) suggests that the debris disc is composed of a warm belt at 739 K, based on which we estimate the location of this component belt using Equation [\[eq:Distance\]](#eq:Distance).

We estimate the distance of the 739 K dust belt to be 1.1 au from the parent star. The two higher-temperature fits produce additional excess points that cannot be fitted with the existing blackbody component and would hence require an additional, even hotter belt fit. However, at such high temperatures, around A-type stars, it would be physically impossible for the dust to survive, suggesting the stellar fit might not be accurate. Carbon grains $\sim$0.1 au away from A-type stars sublimate at $\sim$2000 K (cite: Lebreton2013; Pearce2020). Silicates sublimate at comparatively cooler temperatures of $\sim$1200 K (cite: Sezestre2019). In addition to the SED data shown in Figure [10](#fig:SED), there exists a 100$\mu$m upper limit listed in the IRAS catalogue, which we did not include in the SED fit, as it is very large and does not represent a meaningful constraint.

## IRS

Using data from the IRS spectrograph[^5] (the Infrared Spectrograph on the Spitzer Space Telescope), in Figure [11](#fig:IRS) we examined and compared the mid-IR spectrum of HD 44892 (PI Bouwman, ID 3470) to that of protoplanetary discs HD 97048 (PI Houck, ID 2) and HD 36112 (PI Bouwman, ID 3470), and debris discs with gas HD 138813 (PI Carpenter, ID 30091) and HD 131835 (PI Houck, ID 40651). The spectrum of HD 44892 is quite complex and looks very different to those of both protoplanetary and debris discs, and it shows a distinctive feature at the wavelength of $\sim$ 12 $\mu$m, which is not present in the spectra of other objects. The comparison shows that HD 44892 is unique and likely caught at the transition from protoplanetary to debris disc stage.

![](Plots/IRS.png)

# HD 44892 in the context of known gas-harbouring debris discs

![](Plots/ComparisonWithOthers.png)

In Figure [12](#fig:MassComparison) we compare the dust and CO gas masses we calculated for HD 44892 with Herbig star discs (cite: Moor2017MolecularStars) and all other debris discs with CO gas mass measurements to date (see Table [\[tab:allCOGasDetections\]](#tab:allCOGasDetections) for detailed list), highlighting the discs HD 141569 (cite: Miley2018Unlocking141569), NO Lup (cite: Lovell2021ALMADispersal), Fomalhaut (cite: Matra2017DetectionComets; MacGregor2017ADisk), and $\eta$ Crv (cite: Marino2017ALMAPlanets). HD 44892, due to its probable very young age, populates an area where we would expect protoplanetary discs to reside, but both its dust and CO gas masses are much lower than expected for PPDs.

Since HD 44892 is younger than almost all of debris discs from Figure [12](#fig:MassComparison), we would expect it to contain more both dust and gas, as less time has passed for collisional evolution and subsequent dispersal of material from the system. While the CO gas mass of our target may be quite high and comparable to the most massive debris discs with gas, the dust mass is lower in comparison. Like HD 141569, HD 44892 is also a pre-main sequence star. Both these discs seem to represent the missing link between protoplanetary discs and the older planetary systems we observe around other stars. They are both at an evolutionary stage following PPDs, suggesting their gas is potentially inherited from this earlier stage, hence is primordial. This does not, however, entirely rule out the possibility of secondary or mixed origin gas.

The accretion rate we derived for HD 44892 (see Section [4.2](#sec:UVESresults)) is very similar to that measured for HD 141569 (cite: Fairlamb2015) and is orders of magnitude higher than expected for CO-rich debris discs (cite: Kral2017PredictionsPlanetesimals; Borthakur2025). If we assume a secondary origin for the gas, where the gas is H-poor with no significant H$_2$ reservoir, and adopting the upper limit on the total CO gas mass (based on the $^{13}$CO emission) of 10$^{-2}$ $M_{\oplus}$, the CO in the disc would be depleted within just a few years. It is highly unlikely that a mechanism capable of replenishing such a large amount of secondary gas exists, thus the high accretion rate suggests that at least the inner disc is of primordial origin and dominated by H$_{2}$ gas. However, given the accretion variability discussed in Section [4.2](#sec:UVESresults), this value may represent a phase of enhanced accretion. A more detailed discussion will be presented in Szewczyk et al. (in prep).

At the young age of HD 44892, apart from HD 141569, only one other comparable $^{12}$CO detection in a debris disc exists - that in the disc around NO Lup, a 0.7 $M_{\odot}$ star with an age estimate of 1-3 Myr. The two other possible $^{12}$CO detections presented in (cite: Lovell2021ALMADispersal), around Sz 108B and Lup 818s, are likely caused by CO cloud (ISM) gas instead. For NO Lup, using continuum and $^{12}$CO fluxes from (cite: Lovell2021ALMADispersal), we derive the CO gas mass, assuming gas temperature of 50 K, of (5.03 $\pm$ 1.13) $\times$ 10$^{-5}$ $M_{\oplus}$. At the reported dust temperature of 20 K, we estimate the dust mass in the disc to be (4.00 $\pm$ 1.38) $\times$ 10$^{-2}$ $M_{\oplus}$. These values are comparable to those we derive for HD 44892. HD 44892, similarly to NO Lup, has lost its protoplanetary disc, but retains some gas and dust. However, given their very different stellar masses and structure, the mechanisms responsible for dispersal are very likely different, i.e., FUV/EUV photoevaporation for the radiative A-type star HD 44892, and X-ray photoevaporation for the convective low mass star NO Lup (cite: Kunitomo2021PhotoevaporativeStars).

The probable age of 2.1 Myr makes HD 44892 the youngest known gas-bearing debris disc around an IMS to date. There are several reasons why we trust this age determination the most. First, this object has a relatively high level of fractional IR excess (particularly at 12 $\mu$m), putting it in the ‘hybrid’ category. Such excess is observed to decrease with age, as shown in Figure [2](#fig:DustAgeEvolution), and stars older than 100 Myr are expected to have $F_{12\mu m}/F_{star}<3$. Given HD 44892 has a fractional excess of 7.86 at this wavelength, it is unlikely to be very old, as no debris disc with such a high excess has been found at such an advanced age (see Figure [2](#fig:DustAgeEvolution)).

Only three debris discs with gas have been found around stars older than 100 Myr: HD 23642 (V\* V1229 Tau) at 170 Myr (cite: Pericaud2017TheDisks; Southworth2022ScutiHD23642), Fomalhaut (HD 216956) at 440 Myr (cite: Matra2017DetectionComets), and the 1-2 Gyr $\eta$ Crv (cite: Marino2017ALMAPlanets). The older age possibility of HD 44892, at 800 Myr, would make it comparable to the latter two of these objects. For Fomalhaut, using data from (cite: Matra2017DetectionComets) and (cite: MacGregor2017ADisk), we derive a 50 K dust mass of $(1.49\pm0.38)\times10^{-2}$$M_{\oplus}$ and a CO gas mass of $(1.89\pm0.55)\times10^{-7}$$M_{\oplus}$. For $\eta$ Crv we derive a dust mass at 50 K of $(1.07\pm0.87)\times10^{-2}$$M_{\oplus}$ and a CO gas mass of $(5.92\pm0.78)\times10^{-7}$$M_{\oplus}$ (cite: Marino2017ALMAPlanets). Both systems contain at least three orders of magnitude less CO gas mass than HD 44892 (see Figure [12](#fig:MassComparison)). This further shows that if HD 44892 was 800 Myr, it would be an outlier, containing significantly high amounts of CO gas.

It is worth noting that discs exist around post-asymptotic giant branch (AGB) binary star systems, with dust masses even up to 1 $M_{J}$ (cite: Kluska2022APlanets). These, however, are created from the mass-loss of primary object during the last stages of its evolution. HD 44892, at the age of 2.1 Myr, is approaching the zero-age main sequence (ZAMS) or, at the alternative age of 800 Myr, is crossing the Hertzsprung-Russell (HR) gap after leaving the MS. Both its stellar temperature and luminosity are inconsistent with the star being on the AGB. Moreover, there is no evidence to suggest that HD 44892 is a binary system, hence this scenario is inapplicable here.

# Summary and future prospects

Using ALMA, we have detected CO emission in a debris disc around a young, pre-MS intermediate-mass star HD 44892 with a fractional IR excess of 7.86 $^{+0.11}_{-2.27}$ at 12 $\mu$m (cite: Iglesias2023X-shooterEvolution), which falls within a range ($3<F_{12\mu m}/F_{star}<25$) where only one such object, HD 141569, has been previously identified with a measured CO gas mass. This provides a rare glimpse into the very stage of transition from protoplanetary to debris discs. HD 44892 is hence also one of the youngest known hybrid discs, along with the lower-mass (0.7 $M_{\odot}$) star NO Lup, with an age 1-3 Myr (cite: Lovell2021ALMADispersal). For gas temperature in the range 20-50 K, the CO detection yields an estimate of CO gas mass of around 10$^{-4}$ $M_{\oplus}$. On the other hand, the non-detections of $^{13}$CO and C$^{18}$O lines provide upper limits on gas mass of around 10$^{-2}$ $M_{\oplus}$. Since we do not know whether the $^{12}$CO emission we detected is optically thin or thick, the CO gas mass we derived from $^{12}$CO emission should be treated as a lower limit, and may be up to $\sim$10$^{-2}$ $M_{\oplus}$, which is the upper limit derived from $^{13}$CO non-detection.

Given the possibility of the primordial origin of gas, we also report the total gas mass values, calculated assuming an ISM ratio of ${}^{12}\text{CO}$$/$H$_{2}$=$10^{-4}$ in the disc. This results in total H$_2$ gas mass of 0.06 $\pm$ 0.02 $M_{\oplus}$ for 20 K gas and 0.12 $\pm$ 0.01 $M_{\oplus}$ for 50 K gas, yielding a gas-to-dust mass ratio of $\sim$3 at 20 K or $\sim$6 at 50 K. The H$_2$ masses presented are based on $^{12}$CO emission, which may be optically thick, and hence represent lower limits to the total disc gas mass. However, if this gas is of secondary rather than primordial origin, this ratio does not apply, since secondary gas is hydrogen-depleted (cite: Smirnov-Pinchukov2022LackGas). In such a case, the gas is most likely CO dominated, making the CO gas mass a better representative of the total disc gas mass.

Presence of circumstellar gas is further confirmed in our UVES observations of gas absorption, for which we were able to rule out interstellar origin. From the UVES data we also derived an accretion rate for HD 44892 of $\log\dot{M}_{acc}$ = -7.64$^{+0.11}_{-0.07}$$\,M_{\odot}\,yr^{-1}$ and $\log\dot{M}_{acc}$ = -7.69$^{+0.11}_{-0.07}$ $M_{\odot}\,yr^{-1}$ for the two observed epochs. This value is comparable to that of HD 141569 exceeding the level expected for CO-rich debris discs and is similar to values found in protoplanetary discs. If the gas was secondary, then based on the $\sim10^{-2}$ M$_{\oplus}$ CO gas mass upper limit, from our $^{13}$CO non-detection, it would be depleted on very short timescales, and replenishment at the required rate seems unlikely. This strongly suggests that at least the inner disc retains primordial, $H_2$-rich gas.

We also detect 1.3 mm continuum emission in HD 44892 in our ALMA observations. We report the dust mass of HD 44892, assuming a dust temperature of 115 K, of 0.019 $\pm$ 0.009 M$_{\oplus}$. Millimetre dust in this young disc is likely to originate from collisional evolution, given the collisional dust lifetime we estimate at $\sim$10$^{-2}$ . With the detected 1.3 mm flux and known shorter-wavelength photometric measurements of HD 44892, along with the stellar spectrum models, we attempt to characterise the SED in the context of single-temperature ring models. This approach suggests that almost all of the excess emission comes from hot material, over 700 K, thus close to the star. Indeed, most of the millimetre flux in HD 44892 is unresolved and may originate from a point source.

If this is correct, then the marginally resolved dust and gas extending at $\sim$40-45 au are very cold and vertically thin enough not to intercept stellar light - the only scenario to explain the lack of significant infrared emission from these spatial scales. Such flattened disc structures (and low-excess SEDs) may arise at late stages of protoplanetary disc evolution due to gas loss but also when all the very small, sub-micron dust has been removed (cite: Panic2017EffectsLocation). Important to note is that removal of such dust creates conditions for gas survival beyond protoplanetary disc phase suggested by (cite: Nakatani2021PhotoevaporationRemnants). Assuming HD 44892 is an example of this scenario, future studies could involve scattered-light observations using telescopes such as the VLT/SPHERE, to verify if such small grains are indeed absent from its debris disc by, for example, if scattered light is absent, or has a colour indicative of scattering by larger grains (cite: Mulders2013WhyHD100546).

The dust mass in the disc of HD 44892 is within an order of magnitude less than that of the hybrid disc HD 141569. The CO gas mass may be comparable to that of known gas-rich debris discs, depending on the optical thickness of $^{12}$CO emission. Given the very young age of HD 44892, primordial origin gas is likely (cite: Nakatani2021PhotoevaporationRemnants; Smirnov-Pinchukov2022LackGas). Hence, it is possible that we have caught this disc just at the end of its primordial gas contents, which may explain the relatively low CO mass. This suggests HD 44892 is the next evolutionary stage following HD 141569, helping us understand the evolution of planetary systems better. Nonetheless, the young age of this object alone does not allow to make definitive conclusions about the origin of gas in this disc.

It is important to note that from the CO gas mass alone, of (1.62 $\pm$ 0.17) $\times$ 10$^{-4}$$M_{\oplus}$, it is impossible to fully rule out the secondary origin scenario. According to (cite: Cataldi2023PrimordialALMA), only CO-rich debris discs, which they classify as having M$_{CO}\gtrsim10^{-3}$$M_{\oplus}$, cannot be solely explained by the current secondary models (cite: Kral2017PredictionsPlanetesimals). A solution may be either an improvement of secondary models of gas production or presence of primordial gas. On the other hand, they state that it is the debris discs with low CO gas masses, $\lesssim10^{-5}$$M_{\oplus}$ that are easily explainable by secondary means alone. Since the CO gas mass of HD 44892 is between the two, secondary or mixed origin is still possible. It is worth noting, however, that while models introduced in (cite: Kral2019ImagingDiscs) can explain the high CO gas masses in CO-rich debris discs, by introducing neutral carbon shielding and self-shielding of CO, more recent work of (cite: Marino2022VerticalLifetime) discusses the limitations of this scenario. In particular, they show that vertical mixing of gas in the debris disc reduces the effectiveness of shielding, limiting the accumulation of CO. Hence, for the most CO-rich systems secondary models alone are not yet able to explain this gas presence, and primordial origin remains the best available explanation (cite: Cataldi2023PrimordialALMA; Marino2022VerticalLifetime). (cite: Cataldi2023PrimordialALMA) propose that observations of C I in debris discs where CO was found are needed to improve current models of gas, which might help answer questions regarding its origin. Since HD 44892 has a CO gas mass comparable to some of the debris discs with detected C I in their sample, it is possible that HD 44892 may also have detectable C I emission in higher sensitivity observations.

If the alternative age of 800 Myr is considered, HD 44892 would be an outlier in terms of its dust mass (temperature-dependent), 12 $\mu$m excess, and CO gas mass, strongly suggesting that this is the case of a young pre-main sequence star. The two proposed age scenarios, of 2.1 Myr and 800 Myr, correspond to different stellar mass estimates of 2.87 $M_{\odot}$ and 2.29 $M_{\odot}$, respectively. Future, higher spatial and spectral resolution studies of CO emission with ALMA, could remove any remaining uncertainties, allowing for a dynamical mass estimation of the star.

# Acknowledgements

KS acknowledges funding from the Bell Burnell Graduate Scholarship Fund (BB0023). OP and DPI acknowledge support from the Science and Technology Facilities Council via grant number ST/X001016/1. TDP is supported by a UKRI Stephen Hawking Fellowship and a Warwick Prize Fellowship, the latter made possible by a generous philanthropic donation. JM acknowledges support from FONDECYT de Postdoctorado 2024 #3240612 and ANID – Millennium Science Initiative Program – Center Code NCN2024_001.

We thank Lionell Siess, Sebastian Marino, Rens Waters, and Till Käufer for fruitful discussions.

We thank the anonymous referee for their insightful comments and suggestions, which provided valuable perspectives on the nature of this system.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01686.S ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan). It includes NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

Based on observations collected at the European Southern Observatory under ESO programmes 112.262.P.001, 094.A-9029(D), 082.D-0499(A), and 085.D-0395(A).

This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement.

This publication makes use of VOSA, developed under the Spanish Virtual Observatory (<https://svo.cab.inta-csic.es>) project funded by MCIN/AEI/10.13039/501100011033/ through grant PID2020-112949GB-I00. VOSA has been partially updated by using funding from the European Union’s Horizon 2020 Research and Innovation Programme, under Grant Agreement n$\degree$ 776403 (EXOPLANETS-A).

This work is based \[in part\] on observations made with the Spitzer Space Telescope, which was operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA.

# Data Availability

All data underlying this article are available at the ALMA, ESO, and GAIA archives. ALMA data is found under project 2022.1.01686.S at <https://almascience.eso.org/aq/>. ESO data are found under projects 112.262.P.001, 094.A-9029(D), 082.D-0499(A), and 085.D-0395(A) at <http://archive.eso.org/cms.html>. GAIA archive can be browsed at <https://gea.esac.esa.int/archive>. Spitzer IRS spectra can be found at <https://cassis.sirtf.com>.

# Debris discs with gas found through emission

| Name | Age \[Myr\] | Stellar Mass \[$M_{\odot}$\] | Spectral Type | Distance \[pc\] | Dust mass \[$M_{\oplus}$\] | CO gas mass \[$M_{\oplus}$\] | Reference |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| V\* NO Lup | 1-3 | 0.7 | K7 | 132.90 | 4.00 $\times$ 10$^{-2}$ | 5.03 $\times$ 10$^{-5}$ | (cite: Lovell2021ALMADispersal)$^{e}$ |  |
| HD 44892 | 2.1 | 2.87 | A9/F0IV | 191.00 | 1.91 $\times$ 10$^{-2}$ | 1.62 $\times$ 10$^{-4}$ | This study |  |
| HD 141569 | 5 | 2.04$^{[1]}$ | A2VekB9mB9(\_lB) | 111.61 | 2.00 $\times$ 10$^{-1}$ | 3.01 $\times$ 10$^{-1}$ |  |  |
| (cite: Malamut2014THEPc)$^{a}$ |  |  |  |  |  |  |  |  |
| HD 36546 | 3-10 | 1.87$^{[2]}$ | B8 | 100.18 | 7.40 $\times$ 10$^{-2}$ | 6.69 $\times$ 10$^{-3}$ |  |  |
| (cite: Rebollido2020Exocomets:Survey)$^{a}$ |  |  |  |  |  |  |  |  |
| V\* CE Ant | 10 | 0.31$^{[1]}$ | M2Ve | 34.10 | 2.13 $\times$ 10$^{-2}$ | 1.68 $\times$ 10$^{-6}$ | (cite: Matra2019On7)$^{e}$ |  |
| HD 138813 | 10$^{[3]}$ | 2.15$^{[3]}$ | A0V | 136.60 | 1.30 $\times$ 10$^{-1}$ | 1.23 $\times$ 10$^{-3}$ | (cite: Lieman-Sifry2016DebrisALMA)$^{e}$ |  |
| HD 146897 | 10$^{[3]}$ | 1.32$^{[3]}$ | F2/3V | 132.19 | 2.14 $\times$ 10$^{-1}$ | 2.90 $\times$ 10$^{-6}$ | (cite: Lieman-Sifry2016DebrisALMA)$^{e}$ |  |
| HD 172555 | 24$^{[3]}$ | 1.71$^{[3]}$ | A7V | 28.79 | 1.79 $\times$ 10$^{-4}$ | 4.56 $\times$ 10$^{-6}$ |  |  |
| (cite: Kiefer2014ExocometsHD172555)$^{a}$ |  |  |  |  |  |  |  |  |
| HD 110058 | 15$^{[3]}$ | 1.53$^{[3]}$ | A0V | 130.08 | 3.23 $\times$ 10$^{-2}$ | 5.40 $\times$ 10$^{-3}$ |  |  |
| (cite: Iglesias2018DebrisOrigin)$^{a}$ |  |  |  |  |  |  |  |  |
| HD 121191 | 16$^{[3]}$ | 1.63$^{[3]}$ | A5IV/V | 132.29 | 9.02 $\times$ 10$^{-3}$ | 5.83 $\times$ 10$^{-3}$ | (cite: Moor2017MolecularStars)$^{e}$ |  |
| HD 121617 | 16$^{[3]}$ | 1.90$^{[3]}$ | A1V | 117.89 | 1.30 $\times$ 10$^{-1}$ | 3.86 $\times$ 10$^{-2}$ | (cite: Moor2017MolecularStars)$^{e}$ |  |
| HD 131488 | 16$^{[4]}$ | 1.8$^{[6]}$ | A1V | 152.24 | 3.21 $\times$ 10$^{-1}$ | 4.75 $\times$ 10$^{-2}$ | (cite: Moor2017MolecularStars)$^{e}$ |  |
| HD 131835 | 16$^{[3]}$ | 1.81$^{[3]}$ | A2IV | 129.74 | 2.81 $\times$ 10$^{-1}$ | 2.14 $\times$ 10$^{-2}$ | (cite: Lieman-Sifry2016DebrisALMA)$^{e}$ |  |
| HD 156623 | 16$^{[3]}$ | 1.91$^{[3]}$ | A0V | 108.33 | 3.62 $\times$ 10$^{-2}$ | 6.48 $\times$ 10$^{-4}$ |  |  |
| (cite: Rebollido2018TheDiscs)$^{a}$ |  |  |  |  |  |  |  |  |
| HD 181327 | 24 | 1.36 | F6V | 47.78 | 2.41 $\times$ 10$^{-1}$ | 2.70 $\times$ 10$^{-6}$ | (cite: Marino2016ExocometaryRing)$^{e}$ |  |
| \* bet Pic | 24$^{[7]}$ | 1.73$^{[1]}$ | A6V | 19.63 | 4.13 $\times$ 10$^{-2}$ | 2.41 $\times$ 10$^{-5}$ |  |  |
| (cite: Kiefer2014TwoSystem)$^{a}$ |  |  |  |  |  |  |  |  |
| \* eta Tel | 24$^{[3]}$ | 2.21$^{[3]}$ | A0V | 48.54 | 1.33 $\times$ 10$^{-2}$ | \- |  |  |
| (cite: Rebollido2018TheDiscs)$^{a}$ |  |  |  |  |  |  |  |  |
| HD 32297 | \<30 | 1.69$^{[1]}$ | A0V | 129.73 | 6.04 $\times$ 10$^{-1}$ | 1.56 $\times$ 10$^{-1}$ |  |  |
| (cite: Redfield2007Gas32297)$^{a}$ |  |  |  |  |  |  |  |  |
| \* 49 Cet | 45$^{[3]}$ | 1.98$^{[3]}$ | A1V | 57.23 | 1.44 $\times$ 10$^{-1}$ | 2.42 $\times$ 10$^{-2}$ |  |  |
| (cite: Roberge2014VOLATILE-RICHDISK)$^{a}$ |  |  |  |  |  |  |  |  |
| HD 21997 | 42$^{[3]}$ | 1.83$^{[3]}$ | A3IV/V | 69.69 | 2.64 $\times$ 10$^{-1}$ | 6.17 $\times$ 10$^{-2}$ | (cite: Kospal2013ALMA21997)$^{e}$ |  |
| V\* V1229 Tau | 170$^{[5]}$ | \- | A0VpSi+Am | 138.31 | \- | 6.33 $\times$ 10$^{-4}$ | (cite: Pericaud2017TheDisks)$^{e}$ |  |
| HD 216956 | 440 | 1.9$^{[6]}$ | A4V | 7.70 | 1.49 $\times$ 10$^{-2}$ | 1.89 $\times$ 10$^{-7}$ | (cite: Matra2017DetectionComets)$^{e}$ |  |
| \* eta Crv | 1000-2000 | 1.39$^{[3]}$ | F2V | 18.24 | 1.07 $\times$ 10$^{-2}$ | 5.92 $\times$ 10$^{-7}$ | (cite: Marino2017ALMAPlanets)$^{e}$ |  |

[^1]: E-mail: py19k2ms@leeds.ac.uk

[^2]: <https://help.almascience.org/kb/articles/what-is-the-absolute-astrometric-accuracy-of-alma>

[^3]: <https://github.com/richteague/keplerian_mask>

[^4]: <http://archive.eso.org>

[^5]: With reduced spectra obtained from <https://cassis.sirtf.com>

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].method.evidence[2]",
  "value": "Generate circular dust ring models (radii 20-100 au, width 1 px / 0.2 au) at various inclinations, simulate ALMA observations with CASA simalma, compare to data with imfit to find best-fit radius, compute blackbody temperature and optically thin dust mass, and estimate collisional lifetime.",
  "failed_quote": "We calculated the minimum dust mass of HD 44892 assuming optically thin, thermal emission, with Equation [eq:DustMass]"
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Blackbody dust grains; optically thin thermal emission; distance D = 191 pc; stellar luminosity L = 60.0 L_odot; dust opacity kappa = 0.1 * 2.3 * (nu / 230e9)^0.7 cm^2 g^-1 (Beckwith 1990)",
  "failed_quote": "Based on this distance, assuming the dust particles behave as black bodies, we estimated the dust temperature using Equation [eq:Distance]"
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Calculate minimum CO gas mass from 12CO (2-1) integrated flux assuming LTE and optically thin emission at 20 K and 50 K; derive 3-sigma upper limits from 13CO and C18O moment 0 RMS inside the 3-sigma 12CO contour; convert to total H2 mass assuming ISM abundance ratios.",
  "failed_quote": "Since our detection is in ${}^{12}$CO (2-1) only, we use Equation [eq:GasMass] to calculate the minimum CO gas mass, assuming local thermodynamic equilibrium"
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "CO gas mass upper limit from 13CO (at 20 K) = <7.09e-3 M_oplus",
  "failed_quote": "$M_{CO}$ (20K) | <7.09 $\\times$ 10$^{-3}$ | <5.27 $\\times$ 10$^{-2}$ | (7.86 ± 2.05) $\\times$ 10$^{-5}$"
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "CO gas mass upper limit from 13CO (at 50 K) = <1.47e-2 M_oplus",
  "failed_quote": "$M_{CO}$ (50K) | <1.47 $\\times$ 10$^{-2}$ | <1.10 $\\times$ 10$^{-1}$ | (1.62 ± 0.17) $\\times$ 10$^{-4}$"
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "CO gas mass upper limit from C18O (at 20 K) = <5.27e-2 M_oplus",
  "failed_quote": "$M_{CO}$ (20K) | <7.09 $\\times$ 10$^{-3}$ | <5.27 $\\times$ 10$^{-2}$ | (7.86 ± 2.05) $\\times$ 10$^{-5}$"
 },
 {
  "path": "results_numeric[20].evidence[0]",
  "value": "CO gas mass upper limit from C18O (at 50 K) = <1.10e-1 M_oplus",
  "failed_quote": "$M_{CO}$ (50K) | <1.47 $\\times$ 10$^{-2}$ | <1.10 $\\times$ 10$^{-1}$ | (1.62 ± 0.17) $\\times$ 10$^{-4}$"
 },
 {
  "path": "results_numeric[21].evidence[0]",
  "value": "H2 gas mass upper limit from 13CO (at 20 K) = <5.06 M_oplus",
  "failed_quote": "$M_{H_{2}}$ (20K) | <5.06 | <37.67 | 0.06 ± 0.02"
 },
 {
  "path": "results_numeric[22].evidence[0]",
  "value": "H2 gas mass upper limit from 13CO (at 50 K) = <10.51 M_oplus",
  "failed_quote": "$M_{H_{2}}$ (50K) | <10.51 | <78.30 | 0.12 ± 0.01"
 },
 {
  "path": "results_numeric[25].evidence[0]",
  "value": "Warm belt temperature and radius from SED fit (for T_eff = 7000 K) = 739 K at 1.1 au K, au",
  "failed_quote": "The best-fit SED (left plot of Figure 10, 7000 K) suggests that the debris disc is composed of a warm belt at 739 K, based on which we estimate the location of this component belt using Equation [eq:Distance]."
 }
]
```
