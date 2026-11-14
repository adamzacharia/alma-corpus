# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024JApA...45....3M\gpt61sol\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ACA observation and chemical modelling of phosphorus nitride (PN) towards the hot molecular cores G10.47+0.03 and G31.41+0.31

# Introduction

The identification of new interstellar complex organic molecules gives us an idea of the prebiotic chemistry in star-formation regions, which allows us to learn how the building blocks of life may have evolved in the interstellar medium (ISM) (cite: her09). Phosphorus (P) is a fundamental element for the study of the origin of life in the universe. Phosphorus is an important compound in the formation of nucleic acids, phospholipids, adenosine triphosphate (ATP), and deoxyribonucleic acid (DNA) (cite: mac97; pas05). In biotic and prebiotic chemistry, phosphorus gas-phase chemistry is poorly understood because of the minimal observations of its chemical compounds in the ISM. Phosphorus is synthesised in massive stars and injected into the ISM via supernova explosions (cite: ko13; ro14). Phosphorus has a relatively low abundance relative to hydrogen (2.8$\times$10$^{-7}$), which is lower than that of iron, magnesium, sodium, calcium, and aluminium (cite: gre98). The detection of phosphorus is difficult because it is heavily depleted in cold and dense molecular clouds by a factor of 600 (cite: tur90; wak08). In the ISM, only a few P-bearing species, i.e., PN, PO, CP, HCP, C$_{2}$P, and PH$_{3}$ have been detected in the envelopes of evolved stars (cite: ten07; de13; ag14). Among the detected P-bearing molecules, PN and PO are reported to exist in the star-forming regions (see (cite: riv16) and references therein).

![](cont.pdf)

In ISM, P and N-bearing molecule phosphorus nitride (PN) was first detected in three high-mass star-formation regions, i.e., Orion KL, Sgr B2, and W51, with an estimated abundance of $\sim$(1–4)$\times$10$^{-10}$ (cite: tur87; ziu87; riv16). The abundance of PN towards Orion KL, Sgr B2, and W51 was larger than the theoretically expected abundance from a pure low-temperature ion-molecule chemical network (cite: tur87; ziu87; riv16). Previously, the rotational emission lines of PN were identified in several high-mass star-formation regions (cite: tur90; fot16; min18; riv20; ber21), carbon- and oxygen-rich stars (cite: mil08; de13), protostellar shocks (cite: lef16), Galactic Center molecular clouds (cite: riv18), and class I low-mass protostar B1 (cite: ber19). Recently, rotational emission lines of PN were also detected in two giant molecular clouds of the sculptor galaxy NGC 253 (cite: has22). Owing to the limited number of observations of the emission lines of PN and other P-bearing molecules in the ISM, the formation mechanisms of PN and other P-bearing molecules are strongly debated. Previously, three possible formation routes of PN towards the star-formation regions have been proposed: 1. gas-phase chemistry after the shock-induced desorption of P-bearing species (e.g., PH$_{3}$) (cite: aot12; lef16); 2. high-temperature gas-phase formation routes after the thermal desorption of PH$_{3}$ from ice (cite: ch12); and 3. gas-phase chemistry of PN and PO during the cold collapse phase and thermal desorption ($\gtrsim$35 K) due to the heat of the protostellar core (cite: riv16).

In this article, we present the study of the rotational emission line of PN towards the well-known chemically rich hot molecular cores G10.47+0.03 (hereafter G10) and G31.41+0.31 (hereafter G31). The hot molecular cores G10 and G31 are located at a distance of 8.6 kpc (cite: san14) and 7.9 kpc (cite: chu90) from Earth. These hot molecular cores are known to be nurseries of complex organic molecules, including the possible precursors of the simplest amino acid glycine (NH$_{2}$CH$_{2}$COOH) in their warm inner regions (cite: suz16; oh19; man22a). Earlier, (cite: man22a; man22b), (cite: man23), and (cite: min20) discussed the physical and chemical properties of G10 and G31 at millimeter wavelengths. The observations and data reduction are presented in Section [2](#obs) The result of the detection of rotational emission lines of PN is shown in Section [3](#res) The discussion and conclusion of the detection of PN towards the G10 and G31 are shown in Section [4](#dis) and  [5](#con)

![](spectrum.pdf)

# Observations and data reductions

We used the archival data of hot molecular cores G10 and G31, which were observed using the Atacama Compact Array (ACA) with 7-metre array antennas (PI: Rivilla, Victor). ACA is the heart of the Atacama Large Millimeter/Submillimeter Array (ALMA). The observation was performed to detect the emission lines of PN with transition J = 3–2 and the spatial distribution of PN towards the G10, G31, and nine other hot molecular cores. We chose only G10 and G31 from that survey data because the luminosities of G10 and G31 are higher than those of other observed sources. The phase center of G10 and G31 were ($\alpha,\delta$)$_{\rm J2000}$ = 18:08:38.232, –19:51:50.400 and 18:47:34.000, –01:12:45.000 respectively. The observation of hot core G10 was carried out on September 16, 2017, using 11 antennas. Similarly, G31 was observed on August 29, 2017, using ten antennas. The observations were made with spectral ranges of 127.47–128.47 GHz, 129.74–130.74 GHz, 139.07–140.07 GHz, and 140.44–141.44 GHz. For the observation of G10, the flux and bandpass calibrator were J1924–2914, and the phase calibrator was J1833–210 B. For the observation of G31, the flux calibrator was taken as Neptune, the bandpass calibrator was taken as J1924–2914, and the phase calibrator was taken as J1851+0035.

For data reduction and spectral imaging, we used the Common Astronomy Software Application (CASA 5.4.1) with an ALMA data reduction pipeline (cite: mc07). For flux calibration of G10 and G31 using the flux calibrators J1924–2914 and Neptune, we used the Perley–Butler 2017 (for J1924–2914) and Butler-JPL-Horizons 2012 (for Neptune) flux calibrator models for each baseline to scale the continuum flux density of the flux calibrators using the CASA task `SETJY` with 5% accuracy (cite: per17; but12). We made the flux and bandpass calibration after the flagging of the bad channels and antenna data using the CASA pipeline with tasks `hifa_bandpassflag` and `hifa_flagdata`. We used task `MSTRANSFORM` with all available rest frequencies to separate the target data of G10 and G31 after the initial data reduction. We used the task `UVCONTSUB` in the UV plane of the separated calibrated data of G10 and G31 for continuum subtraction. We created a continuum emission map of G10 and G31 using the CASA task `TCLEAN` with `HOGBOM` deconvolver. To create the spectral data cubes of G10 and G31, we used task `TCLEAN` with cube spectral definition mode `SPECMODE`. Finally, we used the CASA task `IMPBCOR` to correct the primary beam pattern for both the continuum and spectral data cubes.

# Result

## Continuum emission towards the G10 and G31

We have shown the millimeter-wavelength continuum emission images of hot core G10 and G31 at frequencies of 140.92 GHz and 140.90 GHz in Figure [1](#fig:continuum), where the surface brightness colour scale has the unit of Jy beam$^{-1}$. After creating the continuum emission map of G10 and G31, we fitted the 2D Gaussian over the continuum emission images of G10 and G31 using the CASA task `IMFIT`. We estimate the peak flux density in Jy beam$^{-1}$, integrated flux density in Jy, synthesized beam size in arcsec ($^{\prime\prime}$), deconvolved beam size in arcsec ($^{\prime\prime}$), position angle in degree ($^{\circ}$), and RMS in mJy of the G10 and G31. For G10, the peak flux density and integrated flux density are 1.78$\pm$0.01 Jy beam$^{-1}$ and 1.99$\pm$0.02 Jy with RMS 12.27 mJy and position angle 89.79$^{\circ}$. The deconvolved source size of the continuum emission map of G10 is 2.72$^{\prime\prime}$$\times$2.31$^{\prime\prime}$ while the synthesized beam of the continuum image of G10 is 10.86$^{\prime\prime}$$\times$6.82$^{\prime\prime}$. Similarly, for G31, the peak flux density and integrated flux density are 1.67$\pm$0.02 Jy beam$^{-1}$ and 2.24$\pm$0.04 Jy with RMS 20.98 mJy and position angle –74.44$^{\circ}$. The deconvolved source size of the continuum emission map of G31 is 6.62$^{\prime\prime}$$\times$5.10$^{\prime\prime}$ while the synthesized beam of the continuum image of G31 is 17.89$^{\prime\prime}$$\times$8.77$^{\prime\prime}$. We find that the continuum emission regions of G10 and G31 are smaller than the synthesized beam size, which is estimated after fitting the 2D Gaussian over the continuum emission regions of G10 and G31. It indicates that the continuum emission maps of G10 and G31 are not resolved at frequencies of 140.92 GHz and 140.90 GHz, respectively.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Frequency |  | Transition$^{*}$ |  |  | $E_{u}$ | log$_{10}$($A_{ij}$) | $S\mu^{2}$ |  |  |  |  |
| (MHz) | ($J^{\prime}$ | $F^{\prime}$ | $J^{\prime\prime}$ | $F^{\prime\prime}$) | \(K\) |  | (Debye$^{2}$) |  |  |  |  |
| 140966.005 | 3 | 3 | 2 | 3 | 13.530 | –5.408 | 0.8383 |  |  |  |  |
| 140967.684 | 3 | 2 | 2 | 1 | 13.530 | –4.526 | 4.5268 |  |  |  |  |
| 140967.684 | 3 | 3 | 2 | 2 | 13.530 | –3.977 | 22.635 |  |  |  |  |
| 140967.684 | 3 | 4 | 2 | 3 | 13.530 | –4.454 | 9.700 |  |  |  |  |
| 140970.005 | 3 | 2 | 2 | 2 | 13.530 | –5.262 | 0.838 |  |  |  |  |

: Observed hyperfine lines of PN.

\* The J = 3–2 frequency without the hyperfine structure is 140967.684 MHz (cite: caz06). The hyperfine spectroscopic line parameters of PN are taken from the [Splatalogue](https://splatalogue.online/advanced1.php) and (cite: caz06).\

## Identification of PN towards the G10 and G31

At first, we extract the molecular spectra of G10 and G31 from the spectral data cubes to create 23.55$^{\prime\prime}$ and 34.02$^{\prime\prime}$ diameter circular regions over G10 and G31. The synthesized beam sizes of the spectral data cubes of G10 and G31 are 10.78$^{\prime\prime}$$\times$6.28$^{\prime\prime}$ and 17.03$^{\prime\prime}$$\times$7.06$^{\prime\prime}$. The systematic velocity ($V_{LSR}$) of the G10 and G31 is 68.50 km s$^{-1}$ and 97.0 km s$^{-1}$ (cite: rof11; suz16). To detect the rotational emission line of PN in the spectra of G10 and G31, we used the local thermodynamic equilibrium (LTE) model spectra with the Cologne Database for Molecular Spectroscopy (CDMS) (cite: mu05). We used the CASSIS software for LTE spectral modelling of PN (cite: vas15). The LTE assumptions are valid in the inner regions of G10 and G31 because the gas density of the warm inner regions of G10 and G31 is $\sim$1.2$\times$10$^{^7}$ cm$^{-3}$ (cite: rof11; suz16; min20). After LTE spectral analysis, we identify the rotational emission line of PN (J = 3–2) and its hyperfine transitions in the spectra of G10 and G31. For fitting the LTE model over the observed spectra of PN, we use Markov chain Monte Carlo (MCMC) in CASSIS. The MCMC technique uses a random walk to iteratively go over all of the parameters and move into the solution space, making it the ultimate outcome by $\chi^{2}$ minimization. The MCMC method considers choosing an initial value in a five-dimensional parameter space, which we call the X$_{0}$ state. Subsequently, it chooses an arbitrary closest neighbour, which is referred to as the X$_{1}$ state. This state is based on a variable step size that is estimated for each iteration. Using this method, $\chi^{2}$ of the new state is estimated, and if $p = \chi^{2}$(X$_{0}$)/$\chi^{2}$(X$_{1}$) $>$1 then the new state is accepted. If $p = \chi^{2}$(X$_{0}$)/$\chi^{2}$(X$_{1}$) $<$ 1 then the new state may be accepted with a certain acceptance probability. If the new state is rejected, the existing X$_{0}$ state will remain, and the X$_{1}$ state will be chosen randomly from among the neighbouring states. This algorithm runs with several initial random states, and it is typically deemed to have reached the correct solution when the variation between different groups of states is less than the variance of each group. All spectral parameters, such as excitation temperature, column density, source size, FWHM, and V$_{LSR}$, can be varied. The partition functions are computed using CASSIS for temperatures lower than 9.375 K, which is the lowest temperature provided by the CDMS database for some molecules. The partition function can be computed as:

$$\begin{equation}
Q(T) = \sum g_{i}\times exp(-E_{i}/kT)
\end{equation}$$ where $E_{i}$ and $g_{i}$ are the energy and degeneracy of level $i$, respectively.

![](INTMP.pdf)

.

The J = 3–2 transition line of PN splits into five hyperfine components ($F^{\prime}$ and $F^{\prime\prime}$) owing to the nuclear quadrupole interaction of the N nucleus ($I$ = 1), as shown in Table [1](#tab:MOLECULAR DATA). Here, we use the rest frequency of the PN (J = 3–2) line without the hyperfine structure at a frequency of 140967.684 MHz taken from the CDMS and (cite: caz06). After the LTE analysis, we find that the hyperfine transitions of PN towards G10 and G31 do not resolve due to insufficient spectral resolution to resolve the hyperfine lines of PN. Additionally, we also check for the possible blending effect in the PN emission spectra with nearby molecular transitions using CDMS databases, but we find that the identified emission spectra of PN do not blend with nearby molecular lines. The full-width half maximum (FWHM) of the LTE-fitted rotational emission spectra of PN towards the G10 and G31 are 8.50 km s$^{-1}$ and 5.80 km s$^{-1}$, respectively. The best-fit column density of PN towards G10, using the LTE modelled spectra, is (3.60$\pm$0.2)$\times$10$^{13}$ cm$^{-2}$ with an excitation temperature of 150$\pm$25 K and a source size of 10.78$^{\prime\prime}$. Similarly, for G31, the best-fit column density is (9.10$\pm$0.1)$\times$10$^{12}$ cm$^{-2}$ with an excitation temperature of 150$\pm$25 K. Our estimated excitation temperature indicates that the detected emission line of PN originates from the inner region of the hot core because the temperature of the hot molecular core is above 100 K (cite: her09; man23a). During the estimation of the column density, we assume an excitation temperature of 150$\pm$25 K to estimate the column density of the single transition line of PN. We use the same excitation temperature for the two hot cores because the gas densities of G10 and G31 are nearly similar (cite: suz16). The LTE-fitted rotational emission spectra of PN towards G10 and G31 are shown in Figure [2](#fig:ltespec). The estimated fractional abundances of PN towards G10 and G31 with respect to H$_{2}$ are 2.76$\times$10$^{-10}$ and 5.68$\times$10$^{-11}$ respectively, whereas the column densities of H$_{2}$ towards G10 and G31 are 1.3$\times$ 10$^{23}$ cm$^{-2}$ and 1.6$\times$ 10$^{23}$ cm$^{-2}$, respectively, (cite: ik01). Earlier, (cite: fot19) first detected the emission line of PN towards G10 and G31 using IRAM with lower excitation temperatures of 16 K and 10 K. The low excitation temperature of PN estimated by (cite: fot19) does not truly represent hot molecular cores because the temperatures of the hot cores are above 100 K (cite: her09). (cite: fot19) also does not create the emission map of PN due to the restriction of the IRAM resolution. Our ACA observation of PN indicates that the emission line of PN is emitted from the warm-inner regions of G10 and G31.

## Spatial distribution of PN towards the G10 and G31

After detecting the rotational emission line of PN, we produce an integrated emission map of PN with transition J = 3–2 using the CASA task `IMMOMENTS` towards G10 and G31. The integrated emission maps of PN towards G10 and G31 are produced by integrating the spectral data cubes in the velocity range in which the emission lines of PN are detected. The integrated emission maps of PN for G10 and G31 are shown in Figure [3](#fig:emissionmap). The velocity ranges of the integrated emission maps of PN towards G10 and G31 are 60 to 75 km s$^{-1}$ and 90 to 105 km s$^{-1}$, respectively. The resultant integrated emission maps of PN towards G10 and G31 are overlaid with the 140.92 GHz and 140.90 GHz continuum emission maps of G10 and G31. We observe that the integrated emission maps of PN towards G10 and G31 had a peak at the continuum position. From the integrated emission maps, it is evident that PN originate from the warm inner part of the hot core regions of G10 and G31. After producing the integrated emission maps of PN, we estimate the emitting regions of PN towards G10 and G31 by fitting the 2D Gaussian over the integrated emission maps of PN using the CASA task `IMFIT`. The deconvolved beam size of the emitting region of PN is estimated by the following equation, $$\begin{equation}
    \theta_{S}=\sqrt{\theta^2_{50}-\theta^2_{beam}}
    
\end{equation}$$ where $\theta_{50} = 2\sqrt{A/\pi}$ indicates the diameter of the circle whose area ($A$) encloses the 5% line peak of PN, and $\theta_{beam}$ is the half-power width of the synthesized beam (cite: man22a). The estimated emitting regions of PN towards the G10 and G31 are 0.44 pc and 0.65 pc, respectively. We noticed that the emitting regions of PN towards G10 and G31 are similar or small with respect to the synthesized beam size. This indicates that the J = 3–2 transition line of PN is not spatially resolved or, at best, marginally resolved. Therefore, we cannot draw any conclusions about the morphology of the integrated emission maps of PN towards G10 and G31. The higher spatial and spectral resolution observation of PN using the ALMA 12-m array is needed to draw any conclusions about the chemical morphology of PN towards G10 and G31.

![](model.jpeg)

# Discussion

## Previous chemical modelling of PN in the high-mass star-forming regions

Previously, (cite: riv16) and (cite: jim18) computed the two-phase warm-up chemical model of PN using the gas-grain chemical kinetics code UCLCHEM (cite: hol17) in the environment of high-mass star-formation regions. During chemical modelling, (cite: riv16) and (cite: jim18) assumed the formation of a dark, dense clump from the translucent cloud during free-fall collapse. In the first phase of chemical modelling, the gas density increased from 10$^{2}$ to 10$^{6}$ cm$^{-3}$ and the visual extinction (A$_{v}$) increased from 2 to 100 mag. Similarly, the dust and gas temperatures decreased from 20 to 10 K. In the second phase, the dense dark clump warms up to 10 K to 200 K during 2$\times$10$^{5}$ yr. The second phase is known as the warm-up protostellar phase, where the hot core was developed during 2$\times$10$^{5}$ yr. After chemical modelling, (cite: riv16) and (cite: jim18) observed that the abundance of PN varies from 10$^{-12}$ to almost 10$^{-9}$. To estimate the modelled abundance of PN, (cite: riv16) and (cite: jim18) used the gas-phase neutral-neutral reaction between PO and N at 1.2$\times$10$^{5}$ yr (warm-up phase). (cite: riv16) and (cite: jim18) claim that the abundances of the PO and PN become almost equal until 1.2$\times$10$^{5}$ yr. In the warm-up phase, the gas temperature gradually increased from 10 to 200 K, and the species evaporated to the gas phase, while PN and PO were desorbed when the temperature reached $\sim$35 K. The possible gas-phase reactions are as follows.\
\
PO + N $\rightarrow$ PN + O                (1)\
\
Recently, (cite: sil21) claimed that reaction 1 is the most efficient pathway for the formation of PN in high-mass star-formation regions and hot molecular cores. Similarly, (cite: riv16) claimed that PO can be efficiently created during the cold collapse phase in the star-formation regions in a sequence of gas-phase ion-molecule reactions.\
\
H$_{3}$O$^{+}$ + P $\rightarrow$ HPO$^{+}$ + H$_{2}$      (2)\
\
HPO$^{+}$ + e$^{-}$ $\rightarrow$ PO + H           (3)\
\
and\
\
P$^{+}$ + H$_{2}$ $\rightarrow$ PH$_{2}$$^{+}$                  (4)\
\
PH$_{2}$$^{+}$ + e$^{-}$ $\rightarrow$ PH + H          (5)\
\
PH + O $\rightarrow$ PO + H               (6)\
\
Similarly, (cite: riv16) claimed that the PN would be destroyed when protonated water (H$_{3}$O$^{+}$) reacts with the PN in the gas phase via the following reaction\
\
H$_{3}$O$^{+}$ + PN $\rightarrow$ HPN$^{+}$ + H$_{2}$O               (7)\
\
where after the dissociative recombination of HPN$^{+}$, two equally probable reactions were created (cite: riv16).\
\
HPN$^{+}$ + e$^{-}$ $\rightarrow$ PN + H           (8)\
\
and\
\
HPN$^{+}$ + e$^{-}$ $\rightarrow$ PH + N           (9)\
\
Since the fractional abundance of oxygen is higher than the abundance of nitrogen, PH is converted to PO instead of PN. Therefore, PN is gradually destroyed, but PO is produced significantly, which increases the PO/PN ratio in the star-formation regions (see Figure 7(d) in (cite: riv16)).

|  | Reaction | Types | $\alpha$ | $\beta$ | $\gamma$ |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Formation | N + PO $\rightarrow$ PN + O | Neutral-neutral reaction between N and PO | 3.01$\times$10$^{-11}$ | -0.60 | 0.00 |  |  |  |  |  |  |
|  | HPN$^{+}$ + e$^{-}$ $\rightarrow$ PN + H | Dissociative recombination of HPN$^{+}$ | 1.00$\times$10$^{-7}$ | -0.50 | 0.00 |  |  |  |  |  |  |
|  | N + PH $\rightarrow$ PN + H | Neutral-neutral reaction between N and PH | 5.00$\times$10$^{-11}$ | 0.00 | 0.00 |  |  |  |  |  |  |
| Destruction | H$_{3}$O$^{+}$ + PN $\rightarrow$ HPN+ + H$_{2}$O | Ion-neutral reaction between H$_{3}$O$^{+}$ and PN | 1.00$\times$10$^{-9}$ | -0.50 | 0.00 |  |  |  |  |  |  |
|  | H$_{3}$$^{+}$ + PN $\rightarrow$ HPN+ + H$_{2}$ | Ion-neutral reaction between H$_{3}$$^{+}$ and PN | 1.00$\times$10$^{-9}$ | -0.50 | 0.00 |  |  |  |  |  |  |
|  | HCO$^{+}$ + PN $\rightarrow$ HPN+ + CO | Ion-neutral reaction between HCO$^{+}$ and PN | 1.00$\times$10$^{-9}$ | -0.50 | 0.00 |  |  |  |  |  |  |
|  | H$^{+}$ + PN $\rightarrow$ PN$^{+}$ + H | Charge exchange of PN | 1.00$\times$10$^{-9}$ | -0.50 | 0.00 |  |  |  |  |  |  |
|  | He$^{+}$ + PN $\rightarrow$ P$^{+}$ + N + He | Ion-neutral reaction between He$^{+}$ and PN | 1.00$\times$10$^{-9}$ | -0.50 | 0.00 |  |  |  |  |  |  |

The chemical modelling of (cite: riv16) and (cite: jim18) is not valid for G10 and G31 because the gas densities of G10 and G31 are $\sim$1$\times$10$^{7}$ cm$^{-3}$ and during the warm up stage (cite: riv16) and (cite: jim18) increase the gas density upto 10$^{6}$ cm$^{-3}$. To understand the formation mechanism of PN towards G10 and G31, new chemical modelling is needed with the gas density of 1$\times$10$^{7}$ cm$^{-3}$ and gas temperature 300 K (typical hot core temperature).

## New chemical modelling of PN towards hot molecular cores

We made the two-phase warm-up chemical modelling of PN to estimate the modelled abundance from the reactions and uncover the proper formation mechanism of PN towards the hot molecular cores. We use the gas-grain chemical code GGCHEMPY for chemical modelling (cite: ge22). During warm-up chemical modelling, the free-fall collapse of the cloud (Phase I) is followed by a warm-up phase (Phase II). Our two-phase warm-up chemical model is similar to that of (cite: vi04). In phase I, the gas density rapidly increase from $n_{H}$ = 300 cm$^{-3}$ to 1$\times$10$^{7}$ cm$^{-3}$ and the dust temperature remained constant at 10 K. During modelling, the initial visual extinction ($A_{V}$) is assumed to be 2, and the cosmic ray ionization rate is assumed to be 1.3$\times$10$^{-17}$ s$^{-1}$ (cite: vi04). During this time, atoms and molecules are accreted on the grain surface of the hot molecular cores. The accretion rate depends on the gas density of the hot cores. At this stage, the chemical species may hydrogenate or rapidly react with other compounds on the grain surface. In our chemical model, the abundances of oxygen (O), carbon (C), nitrogen (N), and helium (He) corresponding to the solar values are obtained from (cite: as09). Other atomic compounds, such as sulphur (S), silicon (Si), magnesium (Mg), chlorine (Cl), fluorine (F), and phosphorus (P) are depleted by factors of 100. In phase II, the gas density remains constant at 1$\times$10$^{7}$ cm$^{-3}$ and the gas temperature increases from 10 to 300 K during 1$\times$10$^{5}$ yr, which develops into a hot molecular core (“warm-up protostellar phase"). The following trends are discussed in (cite: vi04). In phase II, the molecules no longer freeze, and the frozen molecules on the grains are removed in the gas phase by both non-thermal and thermal desorption mechanisms. In our chemical model, we use thermal evaporation analysis as detailed in (cite: vi04). In our chemical model, we also include co-desorption with H$_{2}$O, volcano desorption, and mono-molecular desorption, which are described in detail in (cite: col04).

During chemical modelling, we add three formation pathways for the production of PN in the chemical network of GGCHEMPY. Similarly, we add five destruction pathways to the PN. The chemical reactions and reaction coefficients which obtained by the Arrhenius equation are presented in Table [\[tab:reactions\]](#tab:reactions). The formation and destruction pathways and the reaction coefficients are obtained from the UMIST 2012 astrochemistry chemical network (cite: mce13). The computed chemical model is shown in Figure. [4](#fig:chemical model). After chemical modelling, the modelled abundance of PN in the hot molecular cores varies from 8.20$\times$10$^{-12}$ to 3.90$\times$10$^{-10}$ during the warm-up phase. In our modelling, we see that the neutral-neutral reaction between N and PO produces a sufficient amount of PN in the gas phase of the hot molecular cores. The other two reactions, the dissociative recombination of HPN$^{+}$ and neutral-neutral reactions between N and PH, do not produce a sufficient amount of PN. We also compute the formation and destruction rates with respect to time, corresponding to three formation pathways and five destruction pathways of PN. We notice that the neutral-neutral reaction between N and PO in the gas phase has a 51% ability to produce PN in hot molecular cores. Similarly, we confirm that the ion-neutral reaction between H$_{3}$O$^{+}$ and PN is the most likely pathway for the destruction of PN.

## Comparision between observed and modelled abundance of PN

We compared our estimated abundance of PN towards G10 and G31 with our computed two-phase warm-up chemical model abundance of PN. Our two-phase warm-up chemical model of PN is suitable with G10 and G31 because the gas densities of both hot cores are $\sim$1$\times$10$^{7}$ cm$^{-3}$ and the temperatures of both sources are above 150 K (cite: rof11; min20; man22a). We estimate that the fractional abundances of PN towards G10 and G31 are 2.76$\times$10$^{-10}$ and 5.68$\times$10$^{-11}$. From the two-phase warm-up chemical modelling, we see that the modelled abundance of PN varies between 8.20$\times$10$^{-12}$ to 3.90$\times$10$^{-10}$ in the warm-up phase. This indicates an estimated abundance of PN towards G10 and G31, which is nearly similar to the range of the modelled abundance of PN. This result clearly indicates that PN is created towards G10 and G31 via the neutral-neutral reaction between PO and N in the gas phase. Earlier, (cite: tur87) detected the rotational emission lines of PN from Orion (KL), W51-M, and Sgr B2 with fractional abundances of 1.7$\times$10$^{-10}$, 1.1$\times$10$^{-11}$, and 1.7$\times$10$^{-12}$. The abundance of PN towards Orion (KL), W51-M, and Sgr B2 is similar to our range of modelled abundances of PN. That indicates that except for G10 and G31, the P and N-bearing molecule PN is created via the neutral-neutral reaction between PO and N in the gas phase towards other hot cores, Orion (KL), W51-M, and Sgr B2.

# Summary and conclusion

In this article, we present the detection of the rotational emission line of PN with transition J = 3–2 towards the hot molecular cores G10 and G31 using ACA. The estimated column densities of PN towards G10 and G31.41 are (3.60$\pm$0.2)$\times$10$^{13}$ cm$^{-2}$ and (9.10$\pm$0.1)$\times$10$^{12}$ cm$^{-2}$, respectively, with an excitation temperature of 150$\pm$25 K. The abundance of PN towards G10 is 2.76$\times$10$^{-10}$. Similarly, the abundance of PN in G31 is 5.68$\times$10$^{-11}$. We create the integrated emission map of PN towards G10.47 and G31.41, and we observe that the PN arises from the warm inner regions of both hot cores with emitting regions of 0.44 pc and 0.65 pc respectively. We also compute a two-phase warm-up chemical model to understand the formation mechanism of PN. We derive the modelled abundance of PN from chemical modelling. After chemical modelling, we compared our estimated abundance of PN with the modelled abundance of PN and observed that the observed and modelled abundances are nearly similar. After this comparison, we claim that PN is created in the gas phase via the neutral-neutral reaction between PO and N in the warm-up stage of G10 and G31. Except for G10 and G31, we also observe that our modelled abundance is similar to the observed abundance of PN towards Orion (KL), W51-M, and Sgr B2. This result also concludes that the PN is formed towards Orion (KL), W51-M, and Sgr B2 via the neutral-neutral reaction between PO and N. We also search for emission lines of PO towards G10 and G31 to estimate the PO/PN ratio, which will be carried out in our follow-up study.

# Acknowledgement

We thank the anonymous referee for the helpful comments that improved the manuscript. A.M. acknowledges the Swami Vivekananda Merit cum Means Scholarship (SVMCM), Government of West Bengal, India, for financial support for this research. The plots within this paper and other findings of this study are available from the corresponding author upon reasonable request. This paper makes use of the following ALMA data: ADS /JAO.ALMA#2016.2.00005.S. ALMA is a partnership of ESO, NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

natexlab

(ref: aot12) Aota, T., & Aikawa, Y., 2012, [ApJ](https://iopscience.iop.org/article/10.1088/0004-637X/761/1/74/meta), 761, 74

(ref: as09) Asplund M., Grevesse N., Sauval A. J., Scott P., 2009, ARA&A, 47, 481

(ref: ag14) Agúndez, M., Cernicharo, J., Decin, L., Encrenaz, P., Teyssier, D., 2014, [ApJ](https://iopscience.iop.org/article/10.1088/2041-8205/790/2/L27/meta), 790, L27

(ref: ber19) Bergner, J. B., $\ddot{O}$berg, K. I., Walker, S., et al. 2019, [ApJ](https://iopscience.iop.org/article/10.3847/2041-8213/ab48f9/meta), 884, L36

(ref: ber21) Bernal, J. J., Koelemay, L. A., & Ziurys, L. M. 2021, [ApJ](https://iopscience.iop.org/article/10.3847/1538-4357/abc87b/meta), 906, 55

(ref: but12) Butler, B., 2012, [ALMA Memo 594](https://library.nrao.edu/public/memos/alma/memo594.pdf), ALMA Memo Series, NRAO

(ref: caz06) Cazzoli, G., Cludi, L., & Puzzarini, C. 2006, [J. Mol. Struct](https://www.sciencedirect.com/science/article/abs/pii/S0022286005005387)., 780, 260

(ref: chu90) Cesaroni, R., Olmi, L., Walmsley, C. M., Churchwell, E., Hofner, P., 1994, [ApJL](https://ui.adsabs.harvard.edu/abs/1994ApJ...435L.137C/abstract), 435, L137

(ref: ch12) Charnley S. B., & Millar, T. J., 1994, [MNRAS](https://academic.oup.com/mnras/article-abstract/270/3/570/1025818), 270, 570

(ref: col04) Collings M. P., Anderson M. A., Chen R., Dever J. W., Viti S., Williams D. A., McCoustra M. R. S., 2004, MNRAS, 354, 1133

(ref: de13) De Beck, E., Kami$\acute{n}$ski, T., Patel, N. A., Young, K. H., Gottlieb, C. A., Menten, K. M., Decin, L., 2013, [A&A](https://doi.org/10.1051/0004-6361/201321349), 558, A132

(ref: fot16) Fontani, F., Rivilla, V. M., Caselli, P., Vasyunin, A., Palau, A., 2016, [ApJ](https://iopscience.iop.org/article/10.3847/2041-8205/822/2/L30/meta), 822, L30

(ref: fot19) Fontani, F., Rivilla, V. M., van der Tak, F. F. S., et al., 2019, [MNRAS](https://doi.org/10.1093/mnras/stz2446), 489, 4530-4542,

(ref: gre98) Grevesse, N., & Sauval, A. J. 1998, [SSRv](https://doi.org/10.1023/A:1005161325181), 85, 161

(ref: ge22) Ge, J., 2022, RAA, 22, 015004

(ref: has22) Haasler, D. et al., 2022, [A&A](https://www.aanda.org/articles/aa/abs/2022/03/aa42032-21/aa42032-21.html), 659, A158

(ref: her09) Herbst, E., & van Dishoeck, E. F. 2009, [ARA&A](https://doi.org/10.1146/annurev-astro-082708-101654), 47, 427

(ref: hol17) Holdship, J., Viti, S., Jiménez-Serra, I., Makrymallis, A., & Priestley, F. 2017, [AJ](https://doi.org/10.3847/1538-3881/aa773f), 154, 38H

(ref: ik01) Ikeda, M., Ohishi, M., Nummelin, A., et al. 2001, [ApJ](https://iopscience.iop.org/article/10.1086/322957/meta), 560, 792

(ref: jim18) Jiménez-Serra, I., Viti, S., Quénard, D., Holdship, J., 2018, [ApJ](https://iopscience.iop.org/article/10.3847/1538-4357/aacdf2/meta), 862, 2

(ref: ko13) Koo, B.-C., Lee, Y.-H., Moon, D.-S., Yoon, S.-C., & Raymond, J. C. 2013, [Sci](https://doi.org/10.1126/science.1243823), 342, 1346

(ref: lef16) Lefloch, B. et al., 2016, [MNRAS](https://academic.oup.com/mnras/article-abstract/462/4/3937/2589897), 462, 3937

(ref: mac97) Maciá, E., Hernández, M. V., Oró, J., 1997, [Orig. Life Evol. Biosph](https://doi.org/10.1023/A:1006523226472), 27, 459

(ref: mil08) Milam, S. N., Halfen, D. T., Tenenbaum, E. D., Apponi, A. J., Woolf, N. J., Ziurys, L. M., 2008, [ApJ](https://iopscience.iop.org/article/10.1086/589135/meta), 684, 618

(ref: min18) Mininni, C., Fontani, F., Rivilla, V. M., et al. 2018, [MNRAS](https://academic.oup.com/mnrasl/article/476/1/L39/4893720), 476, L39

(ref: man22a) Manna, A., & Pal, S., 2022, [Life Sciences in Space Research](https://doi.org/10.1016/j.lssr.2022.04.002), 34, 9

(ref: man22b) Manna, A., and Pal, S., 2022, [Journal of Astrophysics and Astronomy](https://doi.org/10.1007/s12036-022-09868-x), 43, 83

(ref: man23) Manna, A., and Pal, S., 2023, [Astrophys Space Sci](https://doi.org/10.1007/s10509-023-04202-5), 368, 44

(ref: man23a) Manna, A., Pal, S., Viti, S., Sinha, S., 2023, [MNRAS](https://doi.org/10.1093/mnras/stad2185), 525, 2229–2240

(ref: min20) Mininni, C. et al., 2020, [A&A](https://doi.org/10.1051/0004-6361/202038966), 644, A84

(ref: mu05) Müller, H. S. P., SchlM$\ddot{o}$der, F., Stutzki, J. Winnewisser, G., 2005, [Journal of Molecular Structure](https://ui.adsabs.harvard.edu/abs/2005JMoSt.742..215M/abstract), 742, 215

(ref: mc07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, [Astronomical Data Analysis Software and Systems XVI](https://ui.adsabs.harvard.edu/abs/2007ASPC..376..127M/abstract), ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mce13) McElroy, D., Walsh, C., Markwick, A. J., Cordiner, M. A., Smith, K., Millar, T. J., 2013, A&A, 550, A36

(ref: oh19) Ohishi, M., Suzuki, T., Hirota, T., Saito, M. Kaifu, N., 2019, [PASJ](https://doi.org/10.1093/pasj/psz068), 71, 86

(ref: pas05) Pasek, M. A., & Lauretta, D. S. 2005, [AsBio](https://doi.org/10.1089/ast.2005.5.515), 5, 515

(ref: per17) Perley, R. A., Butler, B. J. 2017, [ApJ](https://ui.adsabs.harvard.edu/link_gateway/2017ApJS..230....7P/doi:10.3847/1538-4365/aa6df9), 230, 1538

(ref: riv16) Rivilla, V. M., Fontani, F., Beltr$\acute{a}$n, M. T., Vasyunin, A., Caselli, P., Marti$\acute{n}$, Pintado J., Cesaroni, R., 2016, [ApJ](https://iopscience.iop.org/article/10.3847/0004-637X/826/2/161/meta), 826, 2

(ref: riv18) Rivilla, V. M., Jim$\acute{e}$nez-Serra, I., Zeng, S., et al. 2018, [MNRAS](https://academic.oup.com/mnrasl/article/475/1/L30/4791563), 475, L30

(ref: riv20) Rivilla, V. M., Drozdovskaya, M. N., Altwegg, K., et al. 2020, [MNRAS](https://academic.oup.com/mnras/article/492/1/1180/5699695), 492, 1180

(ref: rof11) Rolffs, R., Schilke, P., Zhang, Q., & Zapata, L. 2011, [A&A](https://doi.org/10.1051/0004-6361/201117112), 536, A33

(ref: ro14) Roederer, I. U., Jacobson, H. R., Thanathibodee, T., Frebel, A., & Toller, E. 2014, [ApJ](https://iopscience.iop.org/article/10.1088/0004-637X/797/1/69/meta), 797, 69

(ref: san14) Sanna, A., Reid, M. J., Menten, K. M., et al. 2014, [ApJ](https://iopscience.iop.org/article/10.1088/0004-637X/781/2/108/meta), 781, 108

(ref: suz16) Suzuki, T., Ohishi, M., Hirota, T., Saito, M., Majumdar, L., Wakelam, V., 2016, [ApJ](https://ui.adsabs.harvard.edu/link_gateway/2016ApJ...825...79S/doi:10.3847/0004-637X/825/1/79), 825, 79

(ref: sil21) Sil, M., Srivastav, S., Bhat, B., 2021, AJ, 162, 119

(ref: tur90) Turner, B. E., Tsuji, T., Bally, J., Guelin, M., Cernicharo, J., 1990, [ApJ](https://adsabs.harvard.edu/pdf/1990ApJ...365..569T), 365, 569

(ref: ten07) Tenenbaum, E. D., Woolf, N. J., Ziurys, L. M., 2007, [ApJ](https://iopscience.iop.org/article/10.1086/521361/meta), 666, L29

(ref: tur87) Turner, B. E., Bally, J., 1987, [ApJ](https://legacy.adsabs.harvard.edu/full/1987ApJ...321L..75T), 321, L75

(ref: vas15) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. -M., Boiziot, M., 2015, [Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics](https://ui.adsabs.harvard.edu/abs/2015sf2a.conf..313V/abstract), 313-316

(ref: vi04) Viti, S., Collings, M. P., Dever, J. W., McCoustra, M. R. S., & Williams, D. A. 2004, MNRAS, 354, 1141

(ref: wak08) Wakelam, V., Herbst, E., 2008, [ApJ](https://iopscience.iop.org/article/10.1086/587734/meta), 680, 371

(ref: ziu87) Ziurys, L. M., 1987, [ApJ](https://adsabs.harvard.edu/pdf/1987ApJ...321L..81Z), 321, L81

</paper>

## Items to check

```json
[
 {
  "path": "software[13].used_for.evidence[0]",
  "value": "PN hyperfine spectroscopic line parameters",
  "failed_quote": "The hyperfine spectroscopic line parameters of PN are taken from the Splatalogue and (cite: caz06)."
 }
]
```
