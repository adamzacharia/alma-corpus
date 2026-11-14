# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...673A.116K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
#  Exploring the environment, magnetic fields, and feedback effects of massive high-redshift galaxies with \[C ii\]

Massive galaxies are expected to grow through different transformative evolutionary phases. High-redshift starburst galaxies and quasars are thought to be such phases and thus provide insight into galaxy evolution. Several physical mechanisms are predicted to play an important role in driving these phases; for example, interaction with companion galaxies, active galactic nuclei feedback, and possibly magnetic fields.

Our aim is to characterize the physical properties and the environment of the submillimeter galaxy AzTEC-3 at $z = 5.3$ and the lensed quasar BRI 0952$-0115$ at $z = 4.4$, and to set a limit on the polarization properties of the two sources. We intend to place these two sources in the broader context of galaxy evolution, specifically star formation and mass growth through cosmic time.

We used full polarization, sub-arcsecond-resolution, ALMA band-7 observations of both BRI 0952$-0115$ and AzTEC-3. We detect \[C ii\] () line emission towards both BRI 0952$-0115$ and AzTEC-3, along with companions in each field. We present an updated gravitational lensing model for BRI 0952$-$0115 for correction of gravitational magnification.

We present infrared luminosities, star-formation rates, and \[C ii\] line to infrared luminosity ratios for each source. The \[C ii\] emission line profile for both BRI 0952$-$0115 and AzTEC-3 exhibit a broad, complex morphology, indicating the possible presence of outflows. We present evidence of a "gas bridge" between AzTEC-3 and a companion source. Modified blackbody spectral energy distribution fitting is used to analyze the properties of \[C ii\] detected companion sources in the field of both the submillimeter galaxy and the quasar. We investigated the possible role of the detected companions in outflow signatures. Using a simple dynamical mass estimate for the sources, we suggest that both systems are undergoing minor or major mergers. No polarization is detected for the \[C ii\] , placing an upper limit below that of theoretical predictions.

Our results show that high-velocity wings are detected, indicating possible signs of massive outflows; however, the presence of companion galaxies can affect the final interpretation. Furthermore, the results provide additional evidence in support of the hypothesis that massive galaxies form in overdense regions, growing through minor or major mergers with companion sources. Finally, strong, ordered magnetic fields are unlikely to exist at the kiloparsec scale in the two studied sources.

# Introduction

The discovery of intense starbursts ($100-1000 \rm M_{\odot}$) at high redshift demonstrates the prevalence of short, transformative phases in the evolution of massive galaxies (cite: Smail97; Hughes98; Blain99; Casey14). Furthermore, the discovery of the relation between the mass of super-massive black holes (SMBHs) in the center of local massive galaxies and the velocity dispersion of those galaxies suggests coeval evolution between the SMBH and the host galaxy (cite: Magorrian98; Ferrarese00; Gebhardt00; Haering04; Gultekin09; Beifiori12; Kormendy13; Bennert15; Reines15). The cosmic black hole accretion rate density has been found to follow a similar trend with redshift to that of the cosmic star-formation rate (SFR) density, indicating that a significant part of the evolution takes place during the first few billion years after the big bang (e.g., (cite: Kormendy13) and (cite: Madau14)). Thus, characterizing the physical properties of high-redshift starburst galaxies and quasars is essential for establishing a complete and coherent description of the evolution of massive galaxies.

![](BRI_hst_b7.png)

Many physical mechanisms play a role in massive galaxy evolution. Galaxies are thought to grow through two main mechanisms, namely galaxy mergers and gas accretion from the intergalactic medium (cite: Keres05; Hopkins08; Dekel09; Genzel10; Krumholz10; DiMatteo12; Dubois12). Additionally, the presence of a growing SMBH, as seen in active galactic nuclei (AGNs) and quasars has been found in theoretical modeling to provide a mechanism for regulating star formation (cite: DiMatteo05; Narayanan15; Harrison17). This implies that characterizing the environment of high-redshift quasars and starbursts, as well as understanding the role of AGN feedback, is paramount to understanding the manner in which these galaxies evolve.

Simulations and theoretical predictions from the early universe have demonstrated the likelihood of ubiquitous major and minor mergers occurring at high redshift (cite: Kaviraj13; Kaviraj15; Fogasy17). Cosmological hydrodynamical simulations such as Illustris (cite: Sijacki15) and Horizon-AGN (cite: Dubois14) can shed light on the effects of these interactions. Studies have shown that minor mergers (classified as those with mass-ratios of \>1:4) and the effect of companion galaxy interactions systematically affect the SFRs and evolution of massive starbursting galaxies (cite: Kaviraj15; Sparre16; Pearson19; Patton20).

Previous studies using optical, near-infrared imaging, or Lyman-$\alpha$ emission in the environment of high-redshift starburst galaxies and quasars have yielded conflicting results. Some of these systems show little or no evidence of companion sources (cite: Willott05; Banados13; Mazzucchelli17; Yue19), while others find overdensities (cite: Carilli13_2; Husband15; Fan16). However, in the last decade, an increasing number of companion sources around high-redshift galaxies have been discovered with the Atacama Large Millimeter/Submillimeter Array (ALMA), primarily using \[C ii\] observations (cite: Oteo16; trakhtenbrot17; Decarli17; DiazSantos18; wardlow18; Casey19; Jones19; Litke19; Neeleman19; Fogasy20; Venemans20). (cite: DiazSantos18) studied the hot dust-obscured galaxy [^1](Hot DOG) W2246$-$0526 and found evidence of a "gas-bridge" structure between a companion source and the central source, suggesting interaction-induced gas flow in the system. The system BRI 1202$-$0725 has also been found to host multiple companions to the quasar and exhibits a similar bridge structure (cite: Carilli13_2).

Studies of the effect of AGNs have demonstrated that galactic-scale outflows and feedback can control star formation activity and black hole growth (cite: Fabian12; King15; Ishibashi16). The extent of this phenomena is unknown, but recent studies of both low- and high-redshift galaxies show many of these sources exhibit outflow characteristics (cite: Heckman90; Rupke05; Weiner09; Banerji11; Cicone14; Chisholm15; Spilker20) through, for example, blueshifted absorption lines, P-Cygni line profiles, or broad emission line components typically seen at higher absolute velocities away from a main emission line. However, these findings become increasingly rare at higher redshifts due to the difficulty in detecting and determining outflow signatures in high-redshift galaxies. Although direct observations of individual sources with outflows are still rare at $z>4$ (cite: Maiolino12; Cicone15; Spilker20; Butler21), studies using stacking of the \[C ii\] line have provided an alternative method of searching for outflows in a wider variety and number of sources, though also providing conflicting results (cite: Gallerani18; Decarli18; Bischetti19; Stanley19; Ginolfi20).

The strength of the \[C ii\] line facilitates its ubiquitous use at high redshift. At high redshifts, this line is shifted to the millimeter (mm) or submillimeter (sub-mm) regime where it is observable by ground-based facilities such as ALMA. The \[CII\] ( $\rightarrow$ ) emission is produced primarily in photodissociation regions (PDRs) by gas exposed to ultraviolet (UV) radiation and acts as one of the major coolants in star-forming regions of the interstellar medium (ISM) (cite: Stacey91; Stacey10; Carilli13). For this reason, it has long been utilized to study the ISM of high-redshift galaxies.

![](BRI_mom0.png)

Although magnetic fields are common, their presence and role in galaxy formation and evolution in the early Universe is still unclear. In the local Universe, ordered magnetic fields with a strength of several $\mu$G are revealed from synchrotron and Faraday rotation observations (cite: Beck2015) in normal spiral galaxies. In local starburst galaxies, fields as high as $\sim20$ mG have been measured (cite: Robishaw2008), and ordered magnetic fields have been found using infrared (IR) dust polarization observations (cite: Lopez2021b). Exactly when these fields were generated is unclear, but models show that a strong regular field can quickly be generated from an initial weak seed field as a result of turbulence driven by, for instance supernova explosions (cite: Rieder2017). Since atoms and ions can easily be aligned by radiation and are subsequently very sensitive to realignment under the influence of only a weak magnetic field, the strength of the \[C ii\] line has led to the suggestion that \[C ii\] could be an excellent tracer of magnetic fields (cite: Yan2006; Zhang2015).

In order to better constrain massive galaxy evolution at high redshift, high-sensitivity data is required to find faint emission from companion sources and to resolve the detailed physics ongoing within these systems. In this study, we explored the environment, searched for magnetic-field signatures, and examined possible outflow properties of two galaxies in the early Universe: the quasar BRI 0952-0115 (hereafter BRI0952) at $z=4.433$ and the massive submillimeter galaxy (SMG) AzTEC-3 at $z=5.3,$ utilizing high-resolution ALMA band-7 \[C ii\] observations. These data were obtained through a proposal designed to look for magnetic fields in the early Universe and were selected based on their previously known extremely bright \[C ii\] emission. Due to the nature of the original project, the sources were observed in full polarization mode in an attempt to detect polarized emission from these sources.

The AzTEC-3 protocluster has been extensively studied previously and encompasses the SMG itself (AzTEC-3) along with a quasar 13 Mpc away in projected distance and a number of previously reported Lyman-break galaxies (LBGs) surrounding the SMG (cite: Capak11; Riechers14). BRI0952 is a gravitationally lensed quasar and has previously been studied due to its strong \[C ii\] emission and lensing features (cite: Maiolino09; Gallerani12). Here, we present findings of resolved \[C ii\] emission in both sources, along with an analysis of their surroundings. These findings help shed light on the role both sources have to play in the evolution of massive galaxies in the early Universe.

In Section [2](#sec:obs), we describe the ALMA observations and analysis utilized in this paper. In Section [3](#sec:results), we describe the results from the \[C ii\] line and continuum analysis and the polarization of both AzTEC-3 and BRI0952. Section [4](#sec:discussion) provides a discussion of the properties of both sources as well as the environment these sources reside in. Finally, we present our conclusions in Section [5](#sec:conclusions). Throughout this paper, we adopt the term "outflows" to describe the high-velocity flow of gas away from central regions typically associated with energy-driven winds by central AGNs or through starburst activity. Similarly, the term "gas-bridge" is used to describe structures of gas connecting components within galaxy systems thought to be caused by physical interactions between these components. Furthermore, we utilized a flat $\Lambda$CDM cosmology with $H_{0}$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M} = 0.3$, and $\Omega_{\Lambda}= 0.7$.

# Observations and analysis

We obtained ALMA band-7 data for BRI0952 and AzTEC-3 as part of a program originally designed to search for magnetic field lines in the early Universe (2018.1.01536.S, P.I. Vlemmings). The setup for both galaxies was tuned to the \[C ii\] 1900.5369 GHz line, and the "time domain mode" was used. Observation details are listed in Table [\[tab:obs\]](#tab:obs).

The data calibration steps were performed following the ALMA polarization calibration scripts using CASA 5.4.0. (CASA [^2]). This includes calibration of the phase, bandpass, flux, and gain. The phase calibrators used for BRI0952 were J0948+002, J0854+2006, and J0725-0054, and for AzTEC-3 these were J0854-2006 and J0948+0022. The quasar J0854+2006 was used for polarization calibration. The uncertainty on the absolute flux calibration is conservatively estimated to be 10%.

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Source | Date | $N_{\rm ant}$ | $\nu_{\mathrm{spw, central}}$ | Synthesized Beam | Image RMS |
|  | \[yyyy mm dd\] | \[GHz\] | \[ $''\times''$ \] | \[mJy/beam\] | \[km/s\] |
| BRI0952$_{\rm [CII]}$ | 2019 04 06 | 41 | 349.8 | 0.48 $\times$ 0.35 | 0.5 |
| BRI0952$_{\rm Cont}$ |  |  | 336.0,338.0,348.0 | $0.53 \times 0.41$ | 0.05 |
| AzTEC-3 | 2019 03 22 | 48 | 301.7 | 0.80 $\times$ 0.56 | 0.2 |
| AzTEC-3$_{\rm Cont}$ |  |  | 288.0,289.9,299.9 | $0.91 \times 0.65$ | 0.02 |

| Source | $P_{l, {\rm peak}}$ (\[C ii\] ) | $P_{l, {\rm int}}$ (\[C ii\] ) | $P_{l, {\rm dust}}$ |
|:---|:---|:---|:---|
| BRI0952 | $<4.8\%$ | $<0.7\%$ | $<2.7\%$ |
| AzTEC-3 | $<2.1\%$ | $<0.2\%$ | $<2.1\%$ |

: Linear polarization $3\sigma$-limits.

To analyze the Stokes-$I$ data, imaging was done using the task tclean. All sources in the field were masked during cleaning. An initial search for line emission was done using "dirty" images to identify the line-free channels available for use in continuum subtraction, which was subsequently performed using the uvcontsub task with a polynomial fit of the order of one for both AzTEC-3 and BRI0952 (see Figures [12](#fig:Az3_contsub) and [13](#fig:BRI_contsub)). The continuum subtraction for BRI0952 was complicated by the appearance of unexpected lines in spectral windows adjacent to that of the \[C ii\] line. [^3]

In the case of AzTEC-3, we used the frequency range of the observations up to 300 GHz due to the possible additional \[C ii\] wing feature seen in the 300.5-301 GHz range and the width of the \[C ii\] line (see Figures [7](#fig:Az3_spec) and [12](#fig:Az3_contsub)). In the case of BRI0952, we used the frequency ranges 335.3-336.9, 347.1-347.7, 348.97-348.98, and 350.45-350.67 GHz. Line emission images were created from the continuum-subtracted data, and continuum images were made from line-free channels. We used Briggs weighting with a robust factor of 0.5 initially for both AzTEC-3 and BRI0925. However, for further analysis of the companion sources surrounding both primary targets, a robust factor of 0.0 was utilized to increase the angular resolution of the \[C ii\] emission cubes; these images were subsequently used for the analyses described in this paper. The continuum images were created using a robust factor of 0.5. For BRI0952, the spectral window centered on the \[C ii\] emission had a bandwidth of 1.8 GHz with a spectral resolution of 31 MHz. The adjacent spectral windows had bandwidths of 2.0 GHz with spectral resolutions of 15.625 MHz. For AzTEC-3, the spectral window centered on the \[C ii\] emission and the adjacent spectral windows had bandwidths of 2.0 GHz with a spectral resolution of 31.25 MHz. Angular resolution and sensitivity is listed in Table [\[tab:obs\]](#tab:obs).

Polarization image cubes were created at native spectral resolutions of $15.625$ MHz and $31.25$ MHz channels for BRI0952 and AzTEC-3, respectively, using Briggs weighting with a robust factor of $0.5$. For BRI0952, the resulting beam size was $0.51''\times0.40''$ with a position angle of $81^{\circ}$. For AzTEC-3, the mean was $0.91''\times0.64''$ (at $82^\circ$). The different observing conditions and channel width resulted in a channel rms noise in the Stokes Q and U maps of $0.46$ mJy beam$^{-1}$ and $0.14$ mJy beam$^{-1}$ for BRI0952 and AzTEC-3, respectively.

For further analysis, including spectral energy distribution (SED) fitting, additional photometry was extracted from archival resources for both AzTEC-3 and BRI0952. *Hubble Space Telescope (HST)* data were extracted from the *HST* archive for both sources. For AzTEC-3, we used the ACS F606W, ACS F814W, WFC3 F105W, WFC3 F125W, and WFC3 F160W bands from the following project codes: 13641 (PI Capak), 9822 (PI COSMOS24-21), and 13384 (PI Riechers). For BRI0952, we used the WFPC2 F814W band with project code 8268 (PI Impey), cross-checked the astrometry with the Gaia2 catalog (cite: Gaia2), and used photometry from the WISE All-Sky Data Release (cite: Cutri12). We performed an archive search for the MIPS 24$\mu$m data. We used archival data of ALMA bands 3, 4, and 6 (2017.1.01081.S P.I. Leung and 2015.1.00388.S P.I. Lu).

# Results

## Polarization

Our full polarization observations did not reveal any polarized emission, neither from emission lines nor from the source continuum. In Table [1](#polres), we indicate the $3\sigma$ upper linear polarization ($P_l$) limits that we derive for both sources at the peak for the \[C ii\] line, both for the total integrated line and for the continuum.

The linear polarization spectra and continuum values were extracted in a single beam (see Section [3.1](#sec:pol) for the size) towards the peak of the lines and continuum, respectively. The linear polarization spectrum was produced from the Q and U spectra using $I_p=\sqrt{Q^2+U^2-\sigma_p^2}$, where $\sigma_p=\sqrt{\sigma_Q^2+\sigma_U^2}$ corresponds to the rms error on the linear polarization and $\sigma_{Q,U}$ are the rms errors in Q and U, respectively. Since we detect no polarization, the derived limits include any potential remaining calibration uncertainty. According to ALMA specifications, this $3\sigma$ limit corresponds to $0.1\%$. Thus, the derived upper limits on the \[C ii\] lines are significantly below values that could be expected if the level of polarization in our sources is similar to that predicted around Galactic star-forming regions (cite: Zhang2018).

![image](FO1_spw3_spec.png) ![image](CompSW_spec.png) ![image](CompN_spec.png)

.

![](BRI_mosaic.png)

![](Aztec3_hst_b7.png)

![](Az3_mom0.png)

## BRI 0952-0115

### Lensing magnification

The quasar BRI0952 is lensed by a single galaxy, with the lensing source at $z = 0.632$. Although previous lensing models have been constructed for BRI0952 (cite: Lehar00; Eigenbrod07; Gallerani12; Momcheva15), the wing-like structures we observe in the \[C ii\] emission suggested differential lensing across the apparent surface of BRI0952 (seen in Figure [14](#fig:img_model_lensing)), prompting us to create an updated lensing model using our high-resolution data. Additionally, the presence of two companion sources in close proximity to the quasar were also a factor as it was necessary to determine if these represented one double-imaged object or two or more separate sources.

We determined the lensing parameters of both the source and the lens by utilizing Visilens (cite: Spilker16). This code is designed specifically to model observations of gravitationally lensed sources at radio and millimeter wavelengths. Visilens calculates the magnification factor by directly modeling the *uv* data rather than introducing bias by using images produced from algorithms such as CASA’s CLEAN. We modeled the lens as a single isothermal ellipsoid parameterized by its location relative to the ALMA image phase center ($x_L$, $y_L$), the ellipticity ($e_L$), and position angle of the major axis ($\phi_L$) in degrees east of north. We modeled the source as a Sérsic source parameterized by position relative to the lens ($x_S$, $y_S$), flux density, Sérsic index, half-light radius, axis-ratio, and position angle. These parameters are then run through a Markov chain Monte Carlo (MCMC) fitting procedure, and the best models were output using a deviance information criterion as described in (cite: Spilker16).

Initially, we ran Visilens on band-7 continuum data in order to determine the best-fit parameters for the lens. Although lens parameters have been previously reported (cite: Lehar00; Eigenbrod07; Gallerani12; Momcheva15), lens fitting was improved when we allowed the parameters to vary outside of previous values. During the lens optimization, we also allowed the source to vary in position and flux density. Once the lens was optimized, we reran the continuum fit with fixed lens parameters but still allowed the Sérsic source profile to vary. Similarly, for the band-7 \[C ii\] emission data, we ran Visilens with the previously optimized lens parameters on the *uv* line emission data while allowing the source to vary in an attempt to increase the quality of our lensing model. The model produced by Visilens is a good fit for our data with minimal to no residual emission, and this is shown in Figure [14](#fig:img_model_lensing). The best-fit parameters are provided in Table [\[tab:lensing_params\]](#tab:lensing_params). Furthermore, the magnification factor produced from this model is similar to those previously reported ($\mu \sim {3.92} \pm 1.3$).

The presence of wing-like structures across the \[C ii\] frequency range of our BRI0952 observations, as seen in the \[C ii\] line emission map (see Figure [14](#fig:img_model_lensing), panels 1 and 3 for observed \[C ii\] data and model output of Visilens), prompted consideration of the effect of different lensing factors across the line (i.e., differential magnification). To investigate this, we split the \[C ii\] line into five bins constituting five different frequency ranges across the line (these can be seen in Figure [14](#fig:img_model_lensing)) and ran Visilens, with the source and lens parameters as specified above, on these bins. The results of this are shown in Figure [14](#fig:img_model_lensing). We determine that it is likely that some amount of differential lensing across the surface of BRI0952 is occurring, and thus we caution that conclusions drawn that correlate strength of emission with location will be affected by this. However, we conclude that based on the low lensing-magnification factor, this effect will not drastically change the extent or strength of the \[C ii\] or continuum emission studied in this paper.

We also note that images of both the data and residuals, as seen in Figures [14](#fig:img_model_lensing) and [15](#fig:comp_lensing) are produced by Visilens rather than by CASA. Although the imaging process in itself is similar to the procedure that CASA performs, it lacks the ability to change weighting schemes and does not clean images. Thus, images produced in Visilens are dirty images with natural weighting and therefore will look slightly different than those created by CASA. As a consequence of this, faint sources in close proximity to BRI0952 are not clearly resolved and distinguishable in images produced by Visilens. This is in contrast with images produced in CASA, which are cleaned with a Briggs weighting scheme using a robust factor of 0.0. The latter are those used throughout the spectral analysis in this paper.

![image](Sub3_spec.png) ![image](GB_spec.png) ![image](GBR_spec.png) ![image](LBG3_spec.png)

### \[C ii\] emission

We detect \[C ii\] ( $\rightarrow$ ) line emission toward both images of the lensed quasar BRI0952. We refer to the two images of the quasar as the "north" and "south" images (names and locations shown in Figure [1](#fig:bri_info)). We confirm the detection of a southern companion source (henceforth termed Comp-SW) tentatively detected by (cite: Gallerani12); we note that our detection is located in the same region as that of the source reported by (cite: Gallerani12), but at a significantly lower signal-to-noise ratio (S/N) and a smaller emitting region. Furthermore, we tentatively detect a second companion (termed Comp-N) north of the top image of the quasar. Higher resolution data and a source plane reconstruction of this system would be required to come to a robust conclusion about the nature of this emission. For the purposes of this paper, we treated both sources as additional companion galaxies as the emission is not seen in our lensing model produced by Visilens, which suggests it is not simply an affect of the lensing magnification. We isolated our lensing model to only those velocities in which the companions manifest and demonstrate in Figure [15](#fig:comp_lensing) that "residual" emission remains in the regions of the companions, lending further weight to the conclusion that the emission has a separate origin to that of the quasar. Given the relatively lower S/N of Comp-N and Comp-SW in relation to BRI0952, combined with the fact that the lensing model reproduces the flux of BRI0952 using a single Sérsic brightness distribution, we treated Comp-SW and Comp-N as not sufficiently lensed to affect conclusions drawn in this analysis (in effect $\rm \mu_{comp-N} = \mu_{comp-SW} = 1$).

We note that including additional faint sources in the lensing analysis with Visilens did not enable a good fit for the two companion sources; however, given their location, they are likely to be magnified by a factor close to $\mu \sim 1$. Furthermore, based on the close spatial proximity of Comp-SW and Comp-N to BRI0952, we assume the emission is \[C ii\] and find spectroscopic redshifts of $z_{\mathrm{Comp-SW}} = 4.4323$ and $z_{\mathrm{Comp-N}} = 4.432$.

To extract the spectra of BRI0952, Comp-N, and Comp-SW we defined a region around each from which to extract the \[C ii\] spectra individually for each component [^4]. For BRI0952, we used an elliptical region of $2.1'' \times 1.45''$ encompassing $\sim 18$ beams[^5], containing both Img-S and Img-N of the quasar. For Comp-SW, we used an elliptical region of $1.13'' \times 0.57''$ encompassing $\sim 4$ beams, and for Comp-N we used an elliptical region of $1.3'' \times 0.62''$ encompassing $\sim 5$ beams. These regions are shown in Figure [2](#fig:BRI_mom0) along with moment-0 and moment-1 maps, and extracted spectra are shown in Figure [3](#fig:BRI_spec). Both companions are faint compared to the emission from BRI0952; both are $\leq 10\%$ of the flux from BRI0952 (see Figure [9](#fig:comb_spec)). The gray plotted rms in Figure [3](#fig:BRI_spec) is calculated in each channel by sampling the spectra in 25 different emission-free regions of the cube extracted from regions the same size as those described above for each individual source.

Due to the presence of high-velocity wings at an $\sim 14 \sigma$ level in the spectra of BRI0952, we find that a double-Gaussian fit was more appropriate (see Figure [3](#fig:BRI_spec), top panel), yielding an improvement to the reduced $\chi^2$ of more than a factor of four. To investigate the impact of differential magnification on the broad wings and attempt to determine if this feature is simply an artifact from lensing, we calculated the ratio of the flux in the blue and red wings of the line profile. If the ratio of the blue to red wing is more than the error on the lensing factor, we suggest that the broad wings could be due to differential magnification predominantly affecting one side of the line. We define these wings to be between $\pm500$ km/s and $1/4\times \rm F_{peak}$, where $\rm F_{peak}$ is the peak of the flux. We find the ratio of the red-to-blue wing to be $\sim1.09$, which is less than the error on the magnification factor (1.3). This suggests that while the observed broad velocity wings may be slightly affected by lensing magnification, it is not solely responsible for them. As an additional test, we extracted the spectra from a region only corresponding to Img-N of BRI0952 to determine if the double Gaussian remained a better fit to the data (shown in Figure [16](#fig:BRI_top_spec)). Indeed, the broad wings remain, and a double Gaussian provides an improved fit to the data. We further discuss the implications of this in Section [4.5](#subsec:outflows).

We compare the line intensities of each component to those found by (cite: Gallerani12). We find that our values are lower, both for the intensity of BRI0952 and for Comp-SW (their Comp-C). However, we note a significant discrepancy between their decomposition and ours. (cite: Gallerani12) find that Comp-SW is significantly brighter than either of the individual images of the quasar BRI0952 (here Img-N and Img-S), while we find the opposite to be true. We attribute this to the increased spectral resolution and baseline coverage possible with ALMA over the IRAM Plateau de Bure Interferometer (PdBI).

The observations from (cite: Gallerani12) were carried out with the IRAM Plateau de Bure Interferometer with six antennas in the extended B configuration during three observing runs and the compact C configuration during two observing runs. They obtained a sensitivity level of 0.5 Jy km s$^{-1}$ beam$^{-1}$ in a 300 km s$^{-1}$ channel, which corresponds to a 1$\sigma$ rms of 1.7 mJy beam$^{-1}$. For comparison, our ALMA data for a similar channel width would be $\sim0.1$ mJy beam$^{-1}$, which is about 15-17 times better in terms of sensitivity. We note that the BRI0952 field is near equatorial, meaning that many antennas possibly in combination with several antenna configurations are needed to achieve a good *uv*-coverage in the $v$ direction. Given the higher sensitivity combined with the improved *uv* coverage thanks to the larger number of ALMA antennas, it is likely that the calibration and image reconstruction of the ALMA data is more robust. As a further comparison between the previous PdBI observations from (cite: Gallerani12) and the new ALMA observations, the spatial resolution is $1.08''\times 0.66''$ and $0.54''\times0.40''$, respectively, and the absolute flux calibration is $\sim20\%$ and $\sim10\%$, respectively.

We used CASA’s imfit task to fit the source size for both images of the quasar and companions. We provide \[C ii\] line parameters and deconvolved source sizes in Table [\[tab:CII_line_params\]](#tab:CII_line_params). We note that, due to the lensed nature of BRI0952, this source has a more complex morphology than those typically handled in this way. The source size provided from imfit is an indication of the extent of the emission in the image plane and is not necessarily well fit by a Gaussian profile. We added an additional 30% on the error of the spatial extent of the emission reported for Img-S and Img-N corresponding to the uncertainty on the lensing magnification factor.

We note the presence of a complex velocity structure between the images of the lensed quasar and the companions. The northern companion exhibits a faint velocity gradient, and the same is present for the south-western companion (see Figure [4](#fig:BRI_mosaic)). The implications of this are further discussed in Section [4.6](#subsec:environment).

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| RA | DEC | $x_L$ | $y_L$ | M | $e_{\rm L}$ | $\phi_{L}$ | $\gamma$ | $\phi_{\gamma}$ | $\mu$ |
| $\rm [J2000]$ | \[J2000\] | $\rm ['']$ | $\rm ['']$ | \[M$_{\odot}$\] |  | (deg. E of N) |  | (deg. E of N) |  |
| 09:55:00.1 | -01:30:07.1 | $0.446$ | $0.003$ | $0.619 \times 10^{11}$ | 0.055 | 191 | 0.011 | 63 | $3.92 \pm 1.3$ |

### Continuum

We detect strong continuum emission toward both north and south images of BRI0952. Using CASA’s imfit, we fit both the north and south images of the quasar and report strong continuum emission totaling $1.96 \pm 0.43$ mJy, which is corrected for lensing. Continuum fluxes from individual images of the quasar are provided in Table [2](#tab:cont) and images are shown in Figure [1](#fig:bri_info). We do not detect the companion sources in continuum and report a $3\sigma$ upper limit of $0.13$ mJy for each. Due to the non-detection of the companions in the continuum, we defined a region corresponding to the quasar from which to extract the continuum flux. As for the line emission, the source sizes of BRI0952 reported in Table [2](#tab:cont) are reported with an additional 30% error added to account for the complex morphology and lensing uncertainties.

Since we do not detect the companions in continuum emission, we estimated their flux using relations from their $L_{\rm{[C\,{\sc II}]}}$ to determine if they should be detectable in our ALMA observations. We estimated their SFR’s using the relation $\rm log(SFR)\,[M_{\odot}/yr] = 1.0 -7.06\times log(L_{[CII]})\,[L_{\odot}]$ from (cite: DeLooze14) for starburst galaxies, computed their $L_{\rm{IR}}$ using the relation in Section [4.3](#subsec:sfr) (cite: Carilli13), and used a modified blackbody approximation (cite: Knudsen03) to recover their $S_{350 \rm{GHz}}$. This results in $S_{350 \rm{GHz}} = 0.21$ mJy for the northern companion and $S_{350 \rm{GHz}} = 0.10$ mJy for the south-western companion. This would correspond to an $\sim4\sigma$ detection for the northern companion and an $\sim 2\sigma$ detection for the southern companion. Thus, in the case of the southern companion with the current data a continuum emission detection is unfeasible. This may also be the case for the northern companion. However, it is also possible that without the velocity information encoded in emission line spectra (and thus without the ability to severely isolate the frequency or velocity range from which to attempt to extract information about the emission from the companions), our observations are simply insufficient to resolve any continuum emission from the companions.

### SED fitting

We performed IR SED fitting and decomposition of the AGN and star formation contributions, using DecompIR (cite: Mullaney11) following the methods of (cite: Stanley18). We used photometry from an archival search for WISE bands and MIPS 24 $\mu m$. We also used ALMA archival data from bands 3, 4, and 6. We performed two sets of fits, one with only the star formation templates and one with both AGN and star formation templates. We find that the photometry of BRI0952 is best fit by a combination of AGN and star formation emission in the IR. The decomposition of the IR SED allows for a calculation of the SFR without contamination from the AGN emission, using the $L_{\rm IR_{SF}}$ integrated from 8-1000 $\mu$m. IR luminosities are reported in Table [\[tab:derived_props\]](#tab:derived_props) and discussed further in Section [4.2](#subsec:LIR).

## Aztec-3

### \[C ii\] emission

We detect \[C ii\] ( $\rightarrow$ ) emission toward the SMG AzTEC-3. We report three sources (LBG-3, Gal-S, and Gal-SW) of the same emission in the region shown in Figure [5](#fig:Az3_info). LBG-3 was initially detected as an Lyman-break galaxy with the COSMOS survey (cite: Ilbert09) but was undetected in \[C ii\] in (cite: Riechers14) and the authors presented a $3\sigma$ upper limit on its \[C ii\] emission. An additional companion, LBG-2 - not shown in Figure [5](#fig:Az3_info), was also originally detected by COSMOS as an LBG but was also undetected in \[C ii\] by (cite: Riechers14). Similarly, we do not detect the source in \[C ii\] emission, and thus do not investigate this source further. Gal-S and Gal-SW are first detections.

The data of (cite: Riechers14) were obtained during Cycle-0 with 16-24 antennas, with a total observing near 7000 seconds spread evenly over two pointings. As a result, the sensitivity of the data in the region around AzTEC-3 is lower by about a factor of two compared to the new data presented here; however, it is important to note that the beam area of our data is 1.7$\times$ larger. We note that the $3\sigma$ limit from (cite: Riechers14) appears to be for a single beam, while we obtain a detection over a more extended region corresponding to $2.8\times$ the size of beam used in this analysis. Furthermore, we note that if converting their $3\sigma$ upper limit to a $5\sigma$ upper limit, the resulting $I_{\rm [CII]}$ is consistent with our detection, though it is important to keep in mind that in this comparison we do not take into account the integration over an extended area.

We assume that the emission from the companions is \[C ii\] based on their close proximity to AzTEC-3, and find a spectroscopic redshift of $z_{\rm LBG-3} = 5.284$, which is in relative agreement with the previous spectroscopic redshift of $z = 5.3$ (cite: Riechers14). We report spectroscopic redshifts for the additional companions, $z_{\rm Gal-S} = 5.2919$ and $z_{\rm Gal-SW} = 5.2942,$ respectively. Figure [9](#fig:comb_spec) shows the combined spectra of the companions and AzTEC-3.

|                   |                                          |                 |
|:------------------|:----------------------------------------:|:---------------:|
| Galaxy            |                  Region                  |    $S_{\nu}$    |
|                   |             ($'' \times ''$)             |     \[mJy\]     |
| $\rm BRI0952_{N}$ | (\[$0.35\pm0.15] \times [0.20\pm0.13$\]) |  $1.44\pm0.4$   |
| $\rm BRI0952_{S}$ | (\[$0.31\pm0.15] \times [0.26\pm0.13$\]) |  $0.52\pm0.14$  |
| Comp-N            |                    \-                    |     $<0.13$     |
| Comp-SW           |                    \-                    |     $<0.13$     |
| AzTEC-3           | (\[$0.38\pm0.03] \times [0.27\pm0.07$\]) | $6.06 \pm 0.13$ |
| LBG-3             | (\[$0.59\pm0.07] \times [0.35\pm0.07$\]) | $0.19 \pm 0.02$ |
| Gal-SW            |          ($<0.91 \times <0.66$)          | $0.07 \pm 0.02$ |
| Gal-S             |                    \-                    |    $<0.056$     |
| ES                | (\[$1.09\pm0.38] \times [0.37\pm0.36$\]) | $0.21 \pm 0.05$ |

: Continuum fluxes for both systems. The continuum fluxes are provided for both images of BRI0952 and are corrected for lensing. However, we do not correct the sizes for lensing. We note that the error on the companions of AzTEC-3 includes an additional 10% due to the additional uncertainty introduced from the deblending process and the errors on the size of both images of BRI0952 include an additional 30% to account for lensing uncertainty.

We followed the same procedure as described for BRI0952 and individually extracted the spectra for the sources in this system from a region with a very limited velocity range [^6]. We used a circular region with a radius of $2.4''$ to extract the spectra of AzTEC-3 encompassing $\sim 13$ beams. We used elliptical regions for the following companions: $1.2'' \times 1.5''$ for LBG-3 encompassing $\sim 4$ beams, $2.6'' \times 1.7''$ for Gal-S encompassing $\sim 10$ beams, and $1.3'' \times 0.90''$ for Gal-SW encompassing $\sim 3$ beams. These regions are shown in Figure [6](#fig:Az3_mom0). We were able to minimize the source blending of the companions with AzTEC-3 since the spectra of the companions are extracted over a very limited velocity range, as shown in Figure [6](#fig:Az3_mom0). We calculated the rms in the same way as described in Section [3.2.2](#subsec:BRI_cii). Additionally, we include the atmospheric transmission in the top subplot for every source in Figure [7](#fig:Az3_spec) to show where the atmospheric absorption line is (shown in Figure [12](#fig:Az3_contsub)), specifically in relation to the companion spectra.

![image](Az3_mosaic.png)

The \[C ii\] spectral line profile of AzTEC-3 shows the presence of high-velocity wings at a $\sim 24 \sigma$ level -and the profile is better fit with a double Gaussian to account for this (Figure [7](#fig:Az3_spec))- where the reduced $\chi^2$ is improved by more than a factor of four using a double-Gaussian fit. We note that the blue wing is wider compared to that of the red wing, as reported in (cite: Riechers14). We used CASA’s imfit to determine deconvolved source sizes. We report source sizes and Gaussian line parameters for AzTEC-3 and companions in Table [\[tab:CII_line_params\]](#tab:CII_line_params). The \[C ii\] emission from the central source is emitted over a compact region with an extent of $4.2 \pm 0.4$ kpc along the major axis, which is consistent with the emitting region of $3.9$ kpc reported by (cite: Riechers14). We do not detect a strong velocity gradient, which is also in good agreement with (cite: Riechers14).

We note an additional feature: a possible velocity gradient between AzTEC-3 and LBG-3. We show this in Figure [8](#fig:Az3_mosaic) and Figure [17](#fig:lbg3_velgrad). This is a tentative feature as it only appears in a few spectral elements and could simply be emission associated with AzTEC-3. (cite: Guaita22) detected a bridge of Lyman-$\alpha$ emission extending between these two components, indicating that tidal forces could be at work between LBG-3 and AzTEC-3. The detection of Lyman-$\alpha$ in both AzTEC-3 and LBG-3 further supports the likelihood of an interacting system. This is further discussed in Section [4.6](#subsec:environment).

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | R.A. | Dec. | Distance | $z_{\rm [CII]}$ | $I_{\rm [CII]}$ | $\rm FWHM_{[CII]}$ | $A_{\rm [CII]}$ |
|  | \[J2000\] | \[J2000\] | \[$''$\] |  | \[Jy km $\rm s^{-1}$\] | \[km $\rm s^{-1}$\] | \[$''\times ''$\] |
| BRI0952 | N: 09:55:00.10 | $-$01:30:06.61 |  | $4.433$ | $15.45 \pm 1.5$ | $182 \pm 5$ | (\[$0.51 \pm 0.19] \times [(0.285 \pm 0.12$\]) |
|  | S: 09:55:00.06 | $-$01:30:07.29 | 1.0 |  |  | $410 \pm 21$ | (\[$0.36 \pm 0.13] \times [0.29 \pm 0.21]$\]) |
| Comp-N | 09:55:00.09 | $-$01:30:05.89 | 0.75 | $4.432$ | $0.62 \pm 0.06$ | $130 \pm 10$ | (\[$0.79 \pm 0.32] \times [0.23 \pm 0.11$\]) |
| Comp-SW | 09:55:00.00 | $-$01:30:08.05 | 2.2 | $4.432$ | $0.30 \pm 0.04$ | $122 \pm 13$ | (\[$0.76 \pm 0.30] \times [0.23 \pm 0.13]$\]) |
| AzTEC-3 | 10:00:20.696 | +02:35:20.35 |  | $5.2988$ | $11.34 \pm 1.0$ | $320 \pm 12$ | (\[$0.69 \pm 0.06] \times [0.42 \pm 0.10$\]) |
|  |  |  |  |  |  | $660 \pm 20$ |  |
| LBG-3 | 10:00:20.766 | +02:35:21.39 | 1.5 | $5.2841$ | $0.78 \pm 0.07$ | $630 \pm 36$ | (\[$0.8 \pm 0.02] \times [0.46 \pm 0.02$\]) |
|  |  |  |  |  |  | $165 \pm 24$ |  |
| Gal-S | 10:00:20.68 | +02:35:18.07 | 2.3 | $5.2919$ | $0.52 \pm 0.05$ | $190 \pm 10$ | (\[$0.53 \pm 0.10] \times [0.41 \pm 0.15$\]) |
|  |  |  |  |  |  | $92 \pm 23$ |  |
| Gal-SW | 10:00:20.60 | +02:35:19.28 | 1.8 | $5.2942$ | $0.15\pm0.01$ | $325 \pm 24$ | (\[$0.36 \pm 0.04] \times [0.08 \pm 0.10$\]) |

### Continuum

We obtain continuum emission from imaging line-free channels in the band-7 ALMA data. Due to the lower angular resolution combined with the lack of velocity information provided in the spectral emission, we were unable to isolate the emission from the companions by restricting the velocity range from which they were extracted as we did for the \[C ii\] emission. Hence, we extracted the continuum flux using three different methods.

The first was to use CASA’s imfit routine on the marginally resolved continuum image. From this we obtain a continuum flux of $6.06 \pm 0.13$ mJy for AzTEC-3, which is in good agreement with (cite: Riechers14), $0.071 \pm 0.018$ mJy for Gal-SW, and $0.18 \pm 0.023$ mJy for LBG-3.

Secondly, we used the imfit residual image with the continuum emission from AzTEC-3 removed to obtain the continuum flux of the companions. Using this method, we obtain a continuum flux of $0.082 \pm 0.02$ mJy for Gal-SW and $0.19 \pm 0.024$ mJy for LBG-3.

Finally, we attempted to isolate the origin of the continuum flux for the companions by creating a continuum image corresponding only to the flux from AzTEC-3, which we were then able to subtract from the original continuum image. To model the flux from AzTEC-3, we selected emission that was at levels higher than $9\sigma$. This emission was then subtracted from the continuum image. The original continuum image and the subtracted image are shown in Figure [5](#fig:Az3_info). This resulted in a continuum flux of $0.06 \pm 0.017$ mJy for Gal-SW and $0.22 \pm 0.025$ mJy for LBG-3. Due to the similarity of the results from various methods, we conclude that the intrinsic value of the continuum for each is in the range provided for the continuum for LBG-3 and Gal-SW.

We do not detect Gal-S in continuum, and we report a $3 \sigma$ upper limit of $0.05$ mJy. The companion sources are faint compared to AzTEC-3 ($\sim3\%$ for LBG-3 and $\sim1\%$ for Gal-SW), and their flux contribution to the central source is negligible. Flux measurements and deconvolved source sizes for the field are provided in Table [2](#tab:cont), where average values are provided for LBG-3 and Gal-SW for both continuum flux and size estimates.

We note an offset between the ALMA continuum, *HST*, and \[C ii\] emission for LBG-3. This is shown in Figure [18](#fig:cont_offset). We suggest that this offset between the three types of emission is likely linked to spatial offset between different types of emission in this source. The offset of this emission also affects the subtraction we performed above due to the possibility that we have in fact subtracted some flux pertaining to LBG-3 that could be included in our model of the emission from AzTEC-3. Thus, we suggest that the continuum flux reported in this paper for LBG-3 be treated as a lower limit. Without additional higher resolution data, a robust conclusion about the nature of this offset is not possible.

We detect an additional continuum source at $\sim10.5$ significance, referred to extra source (ES), in the AzTEC-3 field at the position 10:00:21.066, +02:35:16.975, which is shown in Figure [5](#fig:Az3_info). This source is bright across the *HST* WFC3 filters, but it is undetected in \[C ii\] emission, indicating that it is at a different redshift. Continuum flux measurements and source size are provided in Table [2](#tab:cont).

### SED Fitting

We fit the SED of AzTEC-3 using photometry extracted from *HST* imaging utilizing the source extraction algorithm SExtractor (cite: Sextractor) and our ALMA photometry (see Table [3](#tab:az3_phot)). We matched the resolution of the *HST* images to the lowest resolution filter; we note that the companion sources are not blended with the emission from AzTEC-3 in the *HST* imaging. We fit the SED using Bagpipes (cite: Carnall18), assuming a constant star formation history, a Calzetti reddening law to describe the dust attenuation, and a Chabrier initial mass function (cite: Chabrier03). The mass of the central source was allowed to vary from $10^8 - 10^{14} \rm M_{\odot,}$ and the metallicity was allowed to vary from 0.01-1.0 $\rm Z_{\odot}$. We used the SED fit from Bagpipes to calculate the $L_{\rm IR}$ (integrated from 8-1000 $\mu$m) of AzTEC-3, which is subsequently utilized below in determination of the SMG’s properties.

![image](Az3_allspec.png)

 

![](BRI_allspec.png)

|        |                    |
|:-------|:-------------------|
| Filter | Magnitude          |
|        | \[$\rm mag_{AB}$\] |
| F606W  | $28.89 \pm 0.30$   |
| F814W  | $27.17 \pm 0.10$   |
| F105W  | $24.92 \pm 0.03$   |
| F125W  | $24.68 \pm 0.02$   |
| F160W  | $24.52 \pm 0.02$   |

: Photometry for AzTEC-3 extracted from *HST* images using SExtractor.

# Discussion

## Magnetic fields

The mechanisms for the predicted polarization of the \[C ii\] fine structure line has been named ground state alignment (GSA) (cite: Yan2006; Yan2012; Zhang2015). GSA occurs due to the interaction of an anisotropic radiation field with atoms or ions with fine- or hyperfine-structures. A magnetic field induces precession, which causes the atom or ion to align with the magnetic field. As a result, the emission or absorption of the spectral lines becomes polarized and the polarization direction reflects the direction of the magnetic field. The atoms align predominantly at their ground state level. Due to the low emission and absorption rates involved in these transitions, and hence their long life spans, already weak fields ($B>10^{-15}$ G) can cause alignment.

Predictions for the level of \[C ii\] polarization based on the GSA effect have been made for \[C ii\] emission near galactic star-forming regions (cite: Zhang2018). Near the strong anisotropic radiation field produced from the regions, \[C ii\] polarization up to $\sim30\%$ could be expected. Since the radiation field in starburst galaxies and AGN hosts are similarly energetic, comparable levels of polarization could have been expected in early star-forming galaxies and AGNs (cite: Zhang2018). Our observations do not reveal any linear polarization of \[C ii\] with $3\sigma$ limits to the polarization percentages at the peak of emission \<5% and for the integrated emission \<1%.

There are two possible explanations for such low or non-existent levels of polarization. Firstly, the GSA prediction might not be relevant in conditions where the \[C ii\] emission originates in the observed SMG and quasar, because the anisotropic radiation field is not sufficient to cause significant polarization. Alternatively, if the magnetic field is sufficiently irregular or has a large turbulent component within our resolution elements, beam depolarization will reduce the polarization fraction. Our angular resolution corresponds to $\sim3.1$ kpc and $\sim4.7$ kpc for BRI0952 and AzTEC-3, respectively. These scales are not significantly larger than those where structured fields are observed in nearby galaxies (cite: Beck2015; Lopez2021b), but if the magnetic field follows spiral arms or warped disks, like in the case of Centaurus A (cite: Lopez2021a), depolarization could still be large. Without a better estimate of the expected linear polarization fraction in SMGs and around quasars, we cannot use our limits to provide meaningful constraints on the level of depolarization, and thus the level of structure in the magnetic field. However, unless the GSA mechanism is much less effective than expected, it appears unlikely that a strong ordered magnetic field exists at the kiloparsec scale in the two sources in this paper.

## Infrared luminosity

We obtain an $L_{\rm IR}$ estimate for AzTEC-3 by integrating our SED from Bagpipes from 8-1000 $\mu$m of $L_{\rm IR} = (7.3 \pm 0.2) \times 10^{13}\,\rm L_{\odot}$. Although the central source is blended with surrounding companions, we anticipate that the uncertainty caused by the companion’s IR luminosity will be small and we do not add additional errors to the $L_{\rm{IR}}$ of AzTEC-3. This value is consistent with that reported by (cite: Capak11), as they provide a wide range of possible $L_{\rm IR}$ values ranging from $(2.2-11) \times 10^{13}\,\rm L_{\odot}$ for the 8-1000 $\mu$m wavelength range. (cite: Riechers14) reported a $L_{\rm FIR}$ that is a factor of $\sim6.5$ times lower than our reported $L_{\rm IR}$, which is outside the range of error typically ascribed to differences between $L_{\rm IR}$ and $L_{\rm FIR}$ [^7] (cite: Carilli13). We suggest that discrepancies between these two reported values, apart from the utilized wavelength range, derive from the number of data points used for each fit. (cite: Riechers14) used a higher number of data points than in our SED fitting; however, both analyses lack IR coverage, making it difficult to obtain high levels of accuracy, and thus $L_{\rm FIR}$ or $L_{\rm IR}$, from the SED fit.

To determine a lower limit on the IR luminosity of the companions of AzTEC-3, we used a modified blackbody approximation (e.g., (cite: Knudsen03), Equation 2), assuming a temperature of 45 K and $\beta = 1.7$ (cite: Beelen06; Dunne11; Carniani19). We utilized this approach rather than an SED fit as the SED of the companions is poorly sampled, especially in the far-IR, and the accuracy of sub-mm photometry is affected by the blending of the continuum emission from the central SMG. Calculated lower limits are provided in Table [\[tab:derived_props\]](#tab:derived_props).

A similar fit for the IR luminosity was performed for BRI0952, integrating the SED between 8 and 1000 $\mu$m. We assume the same approximation as for AzTEC-3: the effect of the companion sources on the SED and $L_{\rm{IR}}$ will be negligible due to their faintness in comparison to the quasar. Specifically, we find that the IR luminosity due to star formation is $L_{\rm{IR_{SF}}} = (7.66 \pm 2.49) \times 10^{12} \,\rm L_{\odot}$ and the IR luminosity due to AGN is $L_{\rm{IR_{AGN}}} = (2.23 \pm 0.72) \times 10^{14} \,\rm L_{\odot}$. We note that the error on the IR luminosity comes from the uncertainty on the lensing factor. We find that $L_{\rm{IR_{SF}}}$ is a factor of $\sim 5$ higher than that reported by (cite: Gallerani12). We suggest that this is for two main reasons: (i) the methodology used for fitting - (cite: Gallerani12) scaled a template SED to the 870$\mu m$ continuum flux, while our model fits based on a number of photometric values, increasing the accuracy of the fit - and (ii) the wavelength range used in fitting (cite: Gallerani12).

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | $L_{\rm [CII]}$ | $L_{\rm IR}$ | $\rm SFR_{IR}$ | $\rm SFR_{\rm [CII]}$ | $L_{\rm [CII]}/L_{\rm IR}$ | $\dot{M}_{\rm out}$ | $M_{\rm dyn,[CII]}$ |
|  | \[$10^{9}$ L$_\odot$\] | \[$10^{12}$ L$_\odot$\] | \[M$_{\odot}$ yr$^{-1}$\] | \[M$_{\odot}$ yr$^{-1}$\] | $10^{-3}$ | \[M$_{\odot}$ yr$^{-1}$\] | \[$10^{10}$ M$_{\odot}$\] |
| BRI0952 | $2.46 \pm 0.23$ | $7.66 \pm 2.49$ | 770 | 247 | 0.37 | $98 \pm 19$ | 0.90 |
| Comp-N | $0.39 \pm 0.04$ | \<0.2 | \<21 | 34 | \<2.0 | \- | 0.5 |
| Comp-SW | $0.19 \pm 0.03$ | \<0.2 | \<21 | 16 | \<1.0 | \- | 0.4 |
| AzTEC-3 | $9.3 \pm 0.80$ | $73.4\pm 2$ | 7340 | 809 | $0.12 \pm 0.01$ | $238 \pm 30$ | 6.5 |
| LBG-3 | $0.63 \pm 0.05$ | $0.40 \pm 0.5$ | $40 \pm 46$ | 55 | $1.6 \pm 0.14$ | \- | 0.95 |
| Gal-S | $0.43 \pm 0.04$ | $<0.1$ | $<12.0$ | 37 | $<3$ | \- | 0.83 |
| Gal-SW | $0.12 \pm 0.01$ | $0.15 \pm 0.2$ | $15 \pm 23$ | 11 | $0.85 \pm 0.13$ | \- | 1.6 |

## Star-formation rate

We calculated the SFR of BRI0952 and AzTEC-3, along with their surrounding sources, using different methods. By assuming a Chabrier IMF we can infer the SFR of each source via the following relation: SFR $\sim 10^{-10} L_{\rm{IR,}}$ where $L_{\rm IR}$ is given in $L_{\odot}$ (cite: Carilli13). This yields an SFR of 770 M$_{\odot}$ yr$^{-1}$ for the quasar BRI0952 using $L_{\rm{IR_{SF}}}$ and $\sim 7340$ M$_{\odot}$ yr$^{-1}$ for AzTEC-3 (significantly higher than that reported by (cite: Riechers14) of 1100 M$_{\odot}$ yr$^{-1}$).

These extremely high values are similar to those reported for other peculiar sources in the high-redshift universe. (cite: Daddi09) reported an SFR of $> 1000 \rm M_{\odot}/yr$ in the SMGs GN20 and GN20.2 and notes that there is no evidence of AGN activity. Similarly, SFRs of $\geq 1000$ M$_{\odot}$ yr$^{-1}$ have been reported in HDF850.1 (cite: Walter12), AzTEC-1 (cite: Yun15; Sharda19), HFLS3 (cite: Robson14; Cooray14), and BRI1202 (cite: Carilli13_2).

Following the same procedure we infer the SFRs of the companions of AzTEC-3 from the modified blackbody $L_{\rm{IR}}$ fit, reported in Table [\[tab:derived_props\]](#tab:derived_props). The companions exhibit significantly lower SFRs than AzTEC-3, although we assume that these values provide a lower limit for the companions. We find comparable SFRs to those reported for the quasar companions in (cite: Neeleman19).

We derive SFRs through an additional method using the \[C ii\] -SFR relation for starburst galaxies from (cite: DeLooze14) (provided in Section [3.2.2](#subsec:BRI_cii)), which are given in Table [\[tab:derived_props\]](#tab:derived_props). This results in a similar distribution to the above method, demonstrating the significant discrepancy between the SFR of the companions and that of the central sources in both fields.

We caution that using \[C ii\] as a means of inferring SFR may be inaccurate as the \[C ii\] emission is likely tracing other processes in addition to star formation within the galaxies. The \[C ii\] emission could be tracing more extreme processes or neutral gas (cite: Pavesi18) within the galaxy. If this is the case in AzTEC-3 or BRI0952, this could also contaminate the measurement of the SFR from the \[C ii\] emission. We further note the degeneracy inherently present in determining a SFR from a galaxy’s \[C ii\] luminosity due to the \[C ii\] versus FIR deficit, which is explored below.

## \[CII\] Deficit

The \[C ii\] line is well known to exhibit a deficit with increasing IR luminosity (cite: DiazSantos13; Gullberg15; DiazSantos17; Gullberg18; Lagache18). This has been heavily investigated at high redshift (cite: Stacey10; Wang13; Gullberg15; Decarli17; Gullberg18; Lagache18; Neeleman19), with many proposed explanations including the physical scale of star formation, \[C ii\] saturation, optical depth effects, increased dust grain charge in PDRs and the ISM, and AGN activity (cite: Casey14). Some studies at high redshift have suggested that the lowest ratios occur preferentially in AGN host galaxies (cite: Stacey10). This may not be exclusively limited to \[C ii\] emission, as other fine structure lines such as \[O i\], \[O iii\], \[N ii\], and \[N iii\] have been found to exhibit this deficit as well (cite: GarciaCarpio11; Decarli12; Farrah13). We plot the $L_{\rm [CII]}/L_{\rm{IR}}$ ratios as a function of the IR luminosity for the sources in our sample, as well as other low- and high-redshift galaxies in Figure [10](#fig:CII_FIR). The ratios we find for BRI0952 and AzTEC-3 are similar to those found in HFSL3 (cite: Riechers13) and the ratios reported for two of the four quasars studied in (cite: Decarli17).

For the companion galaxies, we also investigated the $L_{\rm [CII]}/L_{\rm{IR}}$ ratio, though we note that the errors are very large due to the additional uncertainty caused by the deblending of emission from the central bright source. As the IR luminosity is seen as a lower limit (see Section  [4.2](#subsec:LIR)), the ratio can be treated as an upper limit. The resulting values are consistent with those of local star-forming galaxies (cite: DiazSantos13) and are higher than those reported for high-redshift companion sources detected in \[C ii\] (cite: Carilli13_2; Decarli17; Neeleman19).

A possible explanation for the ratios observed in AzTEC-3 and BRI0952 is that of \[C ii\] saturation (cite: Munoz16; Gullberg18). These sources are both hosts to extreme star formation and, in the case of BRI0952, AGN activity. If the temperatures in the majority of the environments in which \[C ii\] is produced exceed the ground state temperature (92 K), we can expect this line to saturate and other fine structure lines to become the primary coolants of the ISM. If this is the case for these two sources, it could explain the deficits observed in both. Observations of other fine structure lines in these sources could provide further clues to the origin of the deficit.

## Outflows and turbulence

As shown in Sections [3.3.1](#subsec:Az3_cii) and [3.2.2](#subsec:BRI_cii), the \[C ii\] emission line profiles of the bright target sources, namely BRI0952 and AzTEC-3, are better fit when including an additional broad Gaussian function. The presence of broad, higher velocity wings in the line profiles are often interpreted as an indication of high-velocity outflows. We note that this need not be a unique interpretation; however, as this is a common analysis that has been done in many previous works (cite: Feruglio10; Aalto12; Maiolino12; Cicone14; Cicone15; Gallerani18; Bischetti19; Stanley19; Ginolfi20). We pursue this below.

We used the luminosity of the broad component of the \[C ii\] line in both AzTEC-3 and BRI0952 to infer a mass outflow rate using the equation from (cite: HaileyDunsheath10) to calculate the mass of the outflow. Similarly to the method employed by (cite: Maiolino12), (cite: Cicone15), and (cite: Stanley19), we assumed $\mathrm{X_{C^+} = 1.4 \times 10^{-4}}$, $T = 200$ K, and $n \gg n_{\rm crit}$ - typical values for PDRs. We estimated the velocity of the outflow by assuming a constant outflow rate of $v_{\rm outf} = 0.5 \times \mathrm{FWHM_{broad}}$ over a region with a radius of $\mathrm{R_{out}}$, allowing us to calculate the outflow rate using $\dot{M}_{\rm out} = M_{\rm out} \times v_{\rm out}/R_{\rm out}$.

We determined the outflow radius as the major axis of the extent of the \[C ii\] emission for AzTEC-3 ($\sim 7.5$ kpc) and BRI0952 ($\sim 2.3$ kpc); for BRI0952, this measurement was taken using the major axis through both the image plane top and bottom images combined, and corrected for lensing magnification [^8]. We investigated alternative methods for determining the mass outflow rate below. We find outflow rates of $\dot{M}_{\rm out} = 238 \pm 30 \mathrm{M_{\odot}/yr}$ for AzTEC-3 and $\dot{M}_{\rm out} = 98 \pm 19 \mathrm{M_{\odot}/yr}$ for BRI0952. Although these values are lower than those found for other individual detections of quasar-driven outflows (cite: Feruglio10; Sturm11; CanoDiaz12; Maiolino12; Cicone14; Feruglio15), they are in good agreement with outflow rates estimates through stacking analyses (cite: Gallerani18; Stanley19; Ginolfi20). The latter samples are comprised of more ‘normal’ high-redshift sources, so the validity of the comparison is tenuous and the methodology used is discussed at the end of this section.

As noted above, there are different methods for disentangling a potential contribution of a high-velocity outflow to the line profile, and we note that the velocity profile of the outflow need not be described by a single Gaussian. As an alternative, we determined the strength of the outflow by utilizing only the flux not accounted for in a single Gaussian fit to the \[C ii\] emission; effectively subtracting the single component from the broad one. This yields a significantly lower mass outflow rate, which we treated as a lower limit for BRI0952 and AzTEC-3. Using this method, we find mass outflow rates of $28 \pm 8 \rm M_{\odot}/yr$ for AzTEC-3 and $12 \pm 4 \rm M_{\odot}/yr$ for BRI0952. We attribute the discrepancy between the two methods, at least in part, to be the effect of the companion sources on the \[C ii\] line emission profile. If the emission from the central source is blended with that of the companions, it is possible that the double-Gaussian fit (and thus the broad complex emission line profiles) are simply an artifact caused by this blending.

![](CII_vs_FIR_corrected.png)

We caution that the differential lensing of the quasar may be contributing to the high-velocity wings. To this end, for an additional investigation into the mass outflow rate of BRI0952 we used the spectra extracted from Img-N (as mentioned in Section [3.2.2](#subsec:BRI_cii) and shown in Figure [3](#fig:BRI_spec)). We use a radius of $0.35''$ ($\sim2.38$kpc), corrected using the same lensing factor as described above), $\rm FWHM_{broad}$ = $543$ km s$^{-1}$, and $L_{[\rm C\,{\sc II}]_{broad}} = 0.22 \times 10^{9}$ L$_{\odot}$, resulting in an outflow of $\dot{M}_{\rm out} = 74 \pm 19\,\mathrm{M_{\odot}/yr}$. The exact impact of the gravitational lensing, and in particular differential lensing, is challenging to estimate, and further modeling based on higher resolution and higher sensitivity data across multiple wavelengths would be needed. We note that systematic errors on the mass outflow rate estimates, along with the systematic errors on other quantities used for comparison (e.g., SFR), are likely to dominate over the effect of the differential lensing. An additional important consideration is the origin of this broad component, which we interpret as an outflow above; for example, we ask ourselves whether the broad component is tracing high-velocity gas outflowing from AzTEC-3 or an interaction between the SMG and the companion Gal-S. This is further discussed in section [4.6](#subsec:environment).

We show the mass outflow rate estimates as a function of SFR in Figure [11](#fig:sfr_mout), together with similar estimates for low- and high-redshift sources. With star-formation-rate estimates that are $\sim \rm or > 1000$ M$_\odot$ yr$^{-1}$ for both BRI0952 and AzTEC-3, both sources are seen in a similar region to other results for high-redshift galaxies. For both sources, the mass outflow rate estimates are on the lower side of the average; however, we note that the large uncertainties in the $\dot{M}_{\rm out}$ and SFR do not allow for additional interpretation.

Outflows are generally studied through different probes, including both emission from high-velocity outflows as well as absorption line studies. In terms of high-velocity outflows, detections have been published using different lines, including CO, \[C ii\], and \[O iii\]$\lambda\,5007$ at low and high redshift (cite: Cicone14; Cicone15; Carniani16; Brusa18). So far, only a few robust detections from single $z>4$ quasars using \[C ii\] have been published (cite: Maiolino12; Carilli13_2). Studies using stacking analyses for larger samples of $z\sim 6$ quasars provide conflicting results (cite: Decarli18; Stanley19; Bischetti19), ranging from non-detection to claimed detections. In terms of star-forming galaxies, stacking of \[C ii\] for $z=4-6$ galaxies in the ALPINE survey revealed a high-velocity outflow component, finding mass outflow rates that are consistent with our results (cite: Ginolfi20). The use of broad \[C ii\] emission as a means of detecting outflows was called into question by (cite: Spilker20) following their non-detection of broad wings associated with a sample of dusty star-forming galaxies with clear OH outflow absorption features. It is thus possible that the broad wings we detect are dominated by emission from the companion sources around AzTEC-3 and BRI0952, where the latter could also be affected by differential lensing magnification. In addition, recent studies have reexamined previous results, indicating the need for a broad component in the fitting of \[C ii\] spectra and found these components superfluous (cite: Meyer22); therefore, we caution that the true nature of the broad component cannot be confirmed as an outflow in BRI0952 and AzTEC-3 without additional outflow tracers detected in these galaxies.

## Environment

The impact of the environment in which massive galaxies evolve at high-redshift remains an open question. These two systems present extreme situations in which to study the effects of faint companion sources in the early universe.

The AzTEC-3 system, with the presence of multiple close companions, detected either in \[C ii\] or in optical or continuum observations, provide an exceptional laboratory to study the effect of close companions near intense starbursts in the early Universe. There are three companion galaxies within a projected distance of $\sim18$ kpc from the central SMG, and an additional system of possibly merging galaxies located at a projected distance of $\sim 95$ kpc from the central source (cite: Riechers14), though the latter is not covered by our observations. We detect a bridge-like structure between the companion galaxy Gal-S and AzTEC-3, suggesting the possible occurrence of a gas-exchange between the two galaxies extending over $\sim 12$ kpc. This "gas bridge" between Gal-S and AzTEC-3 is very similar to that observed by (cite: DiazSantos18) between the Hot DOG W2246 and a companion, although only about half as large in spatial extent. Further investigation of this requires higher resolution ALMA data and an improved method for isolating and subtracting the emission from the central source. As mentioned in Section [3.3](#subsec:aztec3), we detect a velocity gradient between LBG-3 and AzTEC-3, indicating an additional possible interaction. The detections of Lyman-$\alpha$ between these two galaxies in (cite: Guaita22) also indicate an interacting system.

In the field of BRI0952, Comp-N and Comp-SW are detected in \[C ii\] with no further sources detected out to a projected distance of 62 kpc (corresponding to the radius of the primary beam). Also, no additional companions are seen at other wavelengths, most notably the archival *HST* data. Due to the non-detection of the companions in current *HST* and *Herschel* imaging, an analysis of comparable level to that of AzTEC-3 is currently not feasible. We note the possibility that one or both of Comp-N and Comp-SW could be in the process of merging with BRI0952. If this is the case, it may suggest that we are observing the quasar in a post-starburst state in which recent galaxy interactions and ongoing mergers have triggered extreme star formation and AGN activity. In order to investigate this possibility, higher-resolution data of multiple emission lines combined with a robust source plane reconstruction would be needed; this is beyond the scope of this paper. For the BRI0952 companion sources, we see no clear signs of gas-bridge-like structures (as were seen for the AzTEC-3 companion galaxies). We also note that an alternative interpretation of either of the companions Comp-N and Comp-SW could be that they represent an extended substructure in the gas distribution. If that is the case, it would likely indicate the presence of merger activity, as the gravitational forces from minor or major merger interactions could cause a more complex gas distribution (cite: Konig14; Harada18; Konig18; Young21).

These two systems seem to be examples of long-sought-after, theorized, typical, over-dense environments of massive sources with numerous faint companions in the high-redshift Universe. The companion sources of both systems contribute less than 10% to the total \[C ii\] emission, and even less to the total IR luminosity between 8-1000 $\mu m$. Other systems observed in recent years have also been found to have companion sources; however, most of these companions have luminosities comparable to that of the central SMG or quasar host galaxy (cite: Clements09; Carilli13_2; Robson14; Fogasy17; trakhtenbrot17; wardlow18; DiazSantos18; Neeleman19; Fogasy21; Bischetti21). The detection of faint companion sources in these two fields, together with the results of W2246$-$0526 and BRI1202$-$0725 (cite: Carilli13_2; DiazSantos18) and other such systems, are increasing the sample enabling investigation of the role of less massive companion sources on massive galaxy evolution.

Theoretical predictions from semi-analytical model simulations suggest that $22\%$ of quasars should have at least one companion galaxy with stellar masses $>10^8$ $\mathrm{M_{\odot}}$ (cite: Fogasy17). Additionally, studies show that minor mergers, especially in the high-redshift Universe, are common. (cite: Kaviraj15) utilized the Horizon-AGN hydrodynamical cosmological simulation to show that by $z \sim 1$ all massive galaxies ($>10^{10}\,\rm M_{\odot}$) have undergone a major or minor merger, and that minor mergers (those with a mass ratio \> 4:1) are around $2.5\times$ more frequent than major mergers between $1 < z < 4$. Their work also suggests that major mergers are not the dominant source of star-formation enhancement at high redshift (cite: Kaviraj15). This is indicative of the need for minor mergers as fuel providers for high-redshift galaxies and is especially important for extreme SMGs hosting maximum starbursts such as AzTEC-3. The lack of current detections of smaller companion sources is likely due, in part, to the long integration time required to observe them.

In order to categorize these systems as possible minor mergers (be it progenitors or ongoing processes), we calculated the mass of the central source using a virial mass estimator following the procedure used by (cite: Riechers14). We find the dynamical mass inferred from the \[C ii\] emission to be $\sim 6.5\times10^{10}$ M$_{\odot}$ for AzTEC-3 and $\sim 0.90 \times10^{10}$ M$_{\odot}$ for BRI0952 (lensing corrected). We used the same method to compute the masses of the companions, reported in Table [\[tab:derived_props\]](#tab:derived_props). In the AzTEC-3 system, we find that the companions have dynamical masses of $\leq 4 \times$ that of AzTEC-3. This would classify these companions as minor mergers should they interact with the central source; we already observe signs of this for AzTEC-3 and its companions in the form of the gas bridge between these objects. These companion sources are significantly less massive than those reported by (cite: Neeleman19). For the companions of BRI0952 we find the companions have masses $\sim1.5 -2 \times$ smaller than that of the quasar. These values for the companions are closer to the values found for the quasar companions in (cite: Neeleman19). We note that the companion masses are likely overestimated as we do not correct for lensing along the major axis of the companions used for the virial mass estimates due to uncertainties in our lensing model, and therefore the above estimate can be seen as an upper limit.

![](SFR_Mout.png)

The effect of the companions on massive sources remains to be seen. If these faint companions are dynamically interacting in some manner, such as providing gas to the central sources, this could supply the needed materials for the extreme star formation occurring in these systems. Additionally, as suggested by (cite: McGreer14), the possibility of mergers occurring on a relatively fast timescale as a short transitional phase could drastically limit our ability to obtain high number density observations of similar systems. We further suggest that the increased resolution now possible with ALMA will allow for increased detections of SMG and quasar systems with numerous and faint surrounding objects.

# Conclusions

In this paper, we present observational results of \[C ii\] emission from BRI0952 and AzTEC-3, along with respective companion sources. Our results lend credibility to the paradigm of major and minor mergers in the early Universe as progenitors for the massive galaxies we see in studies of the local Universe. We summarize our conclusions below.

1.  We detect \[C ii\] emission in the lensed quasar BRI0952 at $z \sim 4.433$ and the SMG AzTEC-3 at $z \sim 5.3$. We report serendipitous detections of \[C ii\] emission from two previously unreported companion sources around BRI0952 and new detections of \[C ii\] emission from three companions surrounding AzTEC-3. These companions are each located within 3$\,''$ (18 kpc) of the central source.

2.  We present a full-polarization analysis of the \[C ii\] emission lines for both main targets. No polarization was detected, and upper limits are provided. The results suggest that strong ordered magnetic fields are unlikely to exists at the kiloparsec scale in the two studied sources, unless ground state alignment is a less effective mechanism than expected.

3.  We constructed a new lensing model for BRI0952 using Visilens (cite: Spilker16), yielding a lensing magnification factor of $\mu \sim 4$ for the quasar and insignificant lensing magnification of the two companion sources. Our model suggests that differential lensing is occurring across the surface of BRI0952 in both \[C ii\] and continuum emission. This difference is likely insubstantial (or within errors) for our purposes, but it is important to keep it in mind when considering the physical properties of the lensed images.

4.  The inferred SFR from the IR luminosity of both the central SMG AzTEC-3 and the quasar BRI0952 suggest that both sources harbor starbursts of $\sim \rm or > 1000$ solar masses per year.

5.  The central SMG AzTEC-3 and a companion galaxy (Gal-S) in the field show evidence of an interlinking gas bridge. Although we do not find a strong velocity gradient across the central source, we suggest that this bridge may be indicative of an ongoing gas-exchange process or merger.

6.  The \[C ii\] line profiles for both central sources exhibit complex broad features indicating the possible presence of outflows. The mass outflow rates of both BRI0952 and AzTEC-3 are similar to results for high-redshift galaxies; any discrepancies we find are likely symptomatic of large uncertainties on both the mass outflow rate and the SFR.

7.  The outflow features, combined with the observed gas-bridge structure between AzTEC-3 and its southern companion (and possibly others) and velocity-gradients between BRI0952 and companions, suggest both are interacting systems. The extent of this interaction is unknown, but if both systems are either entering or exiting a merger phase, this could explain the extreme star formation events occurring in both.

Growing evidence in recent years suggests that overdense regions leading to major and minor mergers are the progenitors of the massive galaxies we see in the local Universe. The improved resolution possible with ALMA will allow for the increased detection of companion galaxies in high-redshift environments, allowing us to explore the credibility of mergers as means of creating the extreme SFRs observed in these objects.

# Acknowledgements

We thank the anonymous referee for their helpful comments and insights. Kiana Kade acknowledges support from the Nordic ALMA Regional Centre (ARC) node based at Onsala Space Observatory. The Nordic ARC node is funded through Swedish Research Council grant No 2017-00648. Kirsten Knudsen acknowledges support from the Swedish Research Council and the Knut and Alice Wallenberg Foundation. BG acknowledges support from the Carlsberg Foundation Research Grant CF20-0644 ‘Physical pRoperties of the InterStellar Medium in Luminous Infrared Galaxies at High redshifT: PRISMLIGHT’. Sabine König gratefully acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No 789410). This paper makes use of the following ALMA data: 2018.1.01536.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. This paper makes use of the following *HST* projects: 13641 (PI Capak), 9822 (PI COSMOS24-21), and 13384 (PI Riechers), 8268 (PI Impey). Based on observations made with the NASA/ESA Hubble Space Telescope, and obtained from the Hubble Legacy Archive, which is a collaboration between the Space Telescope Science Institute (STScI/NASA), the Space Telescope European Coordinating Facility (ST-ECF/ESA) and the Canadian Astronomy Data Centre (CADC/NRC/CSA) This research made use of APLpy, an open-source plotting package for Python (Robitaille & Bressert 2012).

144 natexlab

(ref: Aalto12) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2012, A&A, 537, A44

(ref: Banados13) Bañados, E., Venemans, B., Walter, F., et al. 2013, ApJ, 773, 178

(ref: Banerji11) Banerji, M., Chapman, S. C., Smail, I., et al. 2011, MNRAS, 418, 1071

(ref: Beck2015) Beck, R. 2015, A&ARv, 24, 4

(ref: Beelen06) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694

(ref: Beifiori12) Beifiori, A., Courteau, S., Corsini, E. M., & Zhu, Y. 2012, MNRAS, 419, 2497

(ref: Bennert15) Bennert, V. N., Treu, T., Auger, M. W., et al. 2015, ApJ, 809, 20

(ref: Sextractor) Bertin, E. & Arnouts, S. 1996, A&AS, 117, 393

(ref: Bischetti21) Bischetti, M., Feruglio, C., Piconcelli, E., et al. 2021, A&A, 645, A33

(ref: Bischetti19) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019, A&A, 630, A59

(ref: Blain99) Blain, A. W., Smail, I., Ivison, R. J., & Kneib, J. P. 1999, MNRAS, 302, 632

(ref: Brusa18) Brusa, M., Cresci, G., Daddi, E., et al. 2018, A&A, 612, A29

(ref: Butler21) Butler, K. M., van der Werf, P. P., Rybak, M., et al. 2021, arXiv e-prints, arXiv:2104.10077

(ref: CanoDiaz12) Cano-Dı́az, M., Maiolino, R., Marconi, A., et al. 2012, A&A, 537, L8

(ref: Capak11) Capak, P. L., Riechers, D., Scoville, N. Z., et al. 2011, Nature, 470, 233

(ref: Carilli13_2) Carilli, C. L., Riechers, D., Walter, F., et al. 2013, ApJ, 763, 120

(ref: Carilli13) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Carnall18) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379

(ref: Carniani19) Carniani, S., Gallerani, S., Vallini, L., et al. 2019, MNRAS, 489, 3939

(ref: Carniani16) Carniani, S., Marconi, A., Maiolino, R., et al. 2016, A&A, 591, A28

(ref: Casey14) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45

(ref: Casey19) Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ, 887, 55

(ref: Chabrier03) Chabrier, G. 2003, PASP, 115, 763

(ref: Chisholm15) Chisholm, J., Tremonti, C. A., Leitherer, C., et al. 2015, ApJ, 811, 149

(ref: Cicone15) Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, A&A, 574, A14

(ref: Cicone14) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21

(ref: Clements09) Clements, D. L., Petitpas, G., Farrah, D., et al. 2009, ApJL, 698, L188

(ref: Cooray14) Cooray, A., Calanog, J., Wardlow, J. L., et al. 2014, ApJ, 790, 40

(ref: Cutri12) Cutri, R. M. & et al. 2012, VizieR Online Data Catalog, II/311

(ref: Daddi09) Daddi, E., Dannerbauer, H., Stern, D., et al. 2009, ApJ, 694, 1517

(ref: DeLooze14) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: Decarli12) Decarli, R., Walter, F., Neri, R., et al. 2012, ApJ, 752, 2

(ref: Decarli17) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457

(ref: Decarli18) Decarli, R., Walter, F., Venemans, B. P., et al. 2018, ApJ, 854, 97

(ref: Dekel09) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: DiMatteo12) Di Matteo, T., Khandai, N., DeGraf, C., et al. 2012, ApJL, 745, L29

(ref: DiMatteo05) Di Matteo, T., Springel, V., & Hernquist, L. 2005, Nature, 433, 604

(ref: DiazSantos17) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32

(ref: DiazSantos13) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68

(ref: DiazSantos18) Dı́az-Santos, T., Assef, R. J., Blain, A. W., et al. 2018, Science, 362, 1034

(ref: Dubois12) Dubois, Y., Devriendt, J., Slyz, A., & Teyssier, R. 2012, MNRAS, 420, 2662

(ref: Dubois14) Dubois, Y., Pichon, C., Welker, C., et al. 2014, MNRAS, 444, 1453

(ref: Dunne11) Dunne, L., Gomez, H. L., da Cunha, E., et al. 2011, MNRAS, 417, 1510

(ref: Eigenbrod07) Eigenbrod, A., Courbin, F., & Meylan, G. 2007, A&A, 465, 51

(ref: Fabian12) Fabian, A. C. 2012, ARA&A, 50, 455

(ref: Fan16) Fan, L., Han, Y., Fang, G., et al. 2016, ApJL, 822, L32

(ref: Farrah13) Farrah, D., Lebouteiller, V., Spoon, H. W. W., et al. 2013, ApJ, 776, 38

(ref: Ferrarese00) Ferrarese, L. & Merritt, D. 2000, ApJL, 539, L9

(ref: Feruglio17) Feruglio, C., Ferrara, A., Bischetti, M., et al. 2017, A&A, 608, A30

(ref: Feruglio15) Feruglio, C., Fiore, F., Carniani, S., et al. 2015, A&A, 583, A99

(ref: Feruglio10) Feruglio, C., Maiolino, R., Piconcelli, E., et al. 2010, A&A, 518, L155

(ref: Fluetsch19) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: Fogasy21) Fogasy, J., Knudsen, K. K., Drouart, G., & Gullberg, B. 2021, MNRAS, 501, 5973

(ref: Fogasy20) Fogasy, J., Knudsen, K. K., Drouart, G., Lagos, C. D. P., & Fan, L. 2020, MNRAS, 493, 3744

(ref: Fogasy17) Fogasy, J., Knudsen, K. K., Lagos, C. D. P., Drouart, G., & Gonzalez-Perez, V. 2017, A&A, 597, A123

(ref: Gaia2) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1

(ref: Gallerani12) Gallerani, S., Neri, R., Maiolino, R., et al. 2012, A&A, 543, A114

(ref: Gallerani18) Gallerani, S., Pallottini, A., Feruglio, C., et al. 2018, MNRAS, 473, 1909

(ref: Gebhardt00) Gebhardt, K., Bender, R., Bower, G., et al. 2000, ApJL, 539, L13

(ref: Genzel10) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091

(ref: George14) George, R. D., Ivison, R. J., Smail, I., et al. 2014, MNRAS, 442, 1877

(ref: Ginolfi20) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 633, A90

(ref: GarciaCarpio11) Graciá-Carpio, J., Sturm, E., Hailey-Dunsheath, S., et al. 2011, ApJL, 728, L7

(ref: Guaita22) Guaita, L., Aravena, M., Gurung-Lopez, S., et al. 2022, A&A, 660, A137

(ref: Gullberg15) Gullberg, B., De Breuck, C., Vieira, J. D., et al. 2015, MNRAS, 449, 2883

(ref: Gullberg18) Gullberg, B., Swinbank, A. M., Smail, I., et al. 2018, ApJ, 859, 12

(ref: Gultekin09) Gültekin, K., Richstone, D. O., Gebhardt, K., et al. 2009, ApJ, 698, 198

(ref: HaileyDunsheath10) Hailey-Dunsheath, S., Nikola, T., Stacey, G. J., et al. 2010, ApJL, 714, L162

(ref: Harada18) Harada, N., Sakamoto, K., Martı́n, S., et al. 2018, ApJ, 855, 49

(ref: Haering04) Häring, N. & Rix, H.-W. 2004, ApJL, 604, L89

(ref: Harrison17) Harrison, C. M. 2017, Nature Astronomy, 1, 0165

(ref: Heckman90) Heckman, T. M., Armus, L., & Miley, G. K. 1990, ApJS, 74, 833

(ref: HerreraCamus19) Herrera-Camus, R., Tacconi, L., Genzel, R., et al. 2019, ApJ, 871, 37

(ref: Hopkins08) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, ApJS, 175, 356

(ref: Hughes98) Hughes, D. H., Serjeant, S., Dunlop, J., et al. 1998, Nature, 394, 241

(ref: Husband15) Husband, K., Bremer, M. N., Stanway, E. R., & Lehnert, M. D. 2015, MNRAS, 452, 2388

(ref: Ilbert09) Ilbert, O., Capak, P., Salvato, M., et al. 2009, ApJ, 690, 1236

(ref: Ishibashi16) Ishibashi, W. & Fabian, A. C. 2016, MNRAS, 463, 1291

(ref: Jones19) Jones, G. C., Maiolino, R., Caselli, P., & Carniani, S. 2019, A&A, 632, L7

(ref: Kaviraj13) Kaviraj, S., Cohen, S., Windhorst, R. A., et al. 2013, MNRAS, 429, L40

(ref: Kaviraj15) Kaviraj, S., Devriendt, J., Dubois, Y., et al. 2015, MNRAS, 452, 2845

(ref: Keres05) Kereš, D., Katz, N., Weinberg, D. H., & Davé, R. 2005, MNRAS, 363, 2

(ref: King15) King, A. & Pounds, K. 2015, ARA&A, 53, 115

(ref: Knudsen03) Knudsen, K. K., van der Werf, P. P., & Jaffe, W. 2003, A&A, 411, 343

(ref: Konig14) König, S., Aalto, S., Lindroos, L., et al. 2014, A&A, 569, A6

(ref: Konig18) König, S., Aalto, S., Muller, S., et al. 2018, A&A, 615, A122

(ref: Kormendy13) Kormendy, J. & Ho, L. C. 2013, ARA&A, 51, 511

(ref: Krumholz10) Krumholz, M. R. & Dekel, A. 2010, MNRAS, 406, 112

(ref: Lagache18) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130

(ref: Lehar00) Lehár, J., Falco, E. E., Kochanek, C. S., et al. 2000, ApJ, 536, 584

(ref: Litke19) Litke, K. C., Marrone, D. P., Spilker, J. S., et al. 2019, ApJ, 870, 80

(ref: Lopez2021a) Lopez-Rodriguez, E. 2021, Nature Astronomy \[\]

(ref: Lopez2021b) Lopez-Rodriguez, E., Guerra, J., Asgari-Targhi, M., & Schmelz, J. T. 2021, arXiv e-prints, arXiv:2102.03362

(ref: Madau14) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Magorrian98) Magorrian, J., Tremaine, S., Richstone, D., et al. 1998, AJ, 115, 2285

(ref: Maiolino09) Maiolino, R., Caselli, P., Nagao, T., et al. 2009, A&A, 500, L1

(ref: Maiolino12) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66

(ref: Mazzucchelli17) Mazzucchelli, C., Bañados, E., Decarli, R., et al. 2017, ApJ, 834, 83

(ref: McGreer14) McGreer, I. D., Fan, X., Strauss, M. A., et al. 2014, AJ, 148, 73

(ref: mcmullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meyer22) Meyer, R. A., Walter, F., Cicone, C., et al. 2022, ApJ, 927, 152

(ref: Momcheva15) Momcheva, I. G., Williams, K. A., Cool, R. J., Keeton, C. R., & Zabludoff, A. I. 2015, ApJS, 219, 29

(ref: Munoz16) Muñoz, J. A. & Oh, S. P. 2016, MNRAS, 463, 2085

(ref: Mullaney11) Mullaney, J. R., Alexander, D. M., Goulding, A. D., & Hickox, R. C. 2011, MNRAS, 414, 1082

(ref: Narayanan15) Narayanan, D., Turk, M., Feldmann, R., et al. 2015, Nature, 525, 496

(ref: Neeleman19) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10

(ref: Oteo16) Oteo, I., Ivison, R. J., Dunne, L., et al. 2016, ApJ, 827, 34

(ref: Patton20) Patton, D. R., Wilson, K. D., Metrow, C. J., et al. 2020, MNRAS, 494, 4969

(ref: Pavesi18) Pavesi, R., Riechers, D. A., Sharon, C. E., et al. 2018, ApJ, 861, 43

(ref: Pearson19) Pearson, W. J., Wang, L., Alpaslan, M., et al. 2019, A&A, 631, A51

(ref: Reines15) Reines, A. E. & Volonteri, M. 2015, ApJ, 813, 82

(ref: Riechers13) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329

(ref: Riechers14) Riechers, D. A., Carilli, C. L., Capak, P. L., et al. 2014, ApJ, 796, 84

(ref: Rieder2017) Rieder, M. & Teyssier, R. 2017, MNRAS, 471, 2674

(ref: Robishaw2008) Robishaw, T., Quataert, E., & Heiles, C. 2008, ApJ, 680, 981

(ref: Robson14) Robson, E. I., Ivison, R. J., Smail, I., et al. 2014, ApJ, 793, 11

(ref: Rupke05) Rupke, D. S., Veilleux, S., & Sanders, D. B. 2005, ApJ, 632, 751

(ref: statcont18) Sánchez-Monge, Á., Schilke, P., Ginsburg, A., Cesaroni, R., & Schmiedeke, A. 2018, A&A, 609, A101

(ref: Sharda19) Sharda, P., da Cunha, E., Federrath, C., et al. 2019, MNRAS, 487, 4305

(ref: Sijacki15) Sijacki, D., Vogelsberger, M., Genel, S., et al. 2015, MNRAS, 452, 575

(ref: Smail97) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5

(ref: Sparre16) Sparre, M. & Springel, V. 2016, MNRAS, 462, 2418

(ref: Spilker20) Spilker, J. S., Aravena, M., Phadke, K. A., et al. 2020a, ApJ, 905, 86

(ref: Spilker20_b) Spilker, J. S., Aravena, M., Phadke, K. A., et al. 2020b, ApJ, 905, 86

(ref: Spilker16) Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016, ApJ, 826, 112

(ref: Stacey91) Stacey, G. J., Geis, N., Genzel, R., et al. 1991, ApJ, 373, 423

(ref: Stacey10) Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al. 2010, ApJ, 724, 957

(ref: Stanley18) Stanley, F., Harrison, C. M., Alexander, D. M., et al. 2018, MNRAS, 478, 3721

(ref: Stanley19) Stanley, F., Jolly, J. B., König, S., & Knudsen, K. K. 2019, A&A, 631, A78

(ref: Sturm11) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJL, 733, L16

(ref: trakhtenbrot17) Trakhtenbrot, B., Lira, P., Netzer, H., et al. 2017, ApJ, 836, 8

(ref: Venemans20) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130

(ref: Walter12) Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233

(ref: Wang13) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44

(ref: wardlow18) Wardlow, J. L., Simpson, J. M., Smail, I., et al. 2018, MNRAS, 479, 3879

(ref: Weiner09) Weiner, B. J., Coil, A. L., Prochaska, J. X., et al. 2009, ApJ, 692, 187

(ref: Willott05) Willott, C. J., Percival, W. J., McLure, R. J., et al. 2005, ApJ, 626, 657

(ref: Yan2006) Yan, H. & Lazarian, A. 2006, ApJ, 653, 1292

(ref: Yan2012) Yan, H. & Lazarian, A. 2012, JQSRT, 113, 1409

(ref: Young21) Young, L. M., Meier, D. S., Bureau, M., et al. 2021, ApJ, 909, 98

(ref: Yue19) Yue, M., Fan, X., Schindler, J.-T., McGreer, I. D., & Huang, Y.-H. 2019, ApJ, 883, 141

(ref: Yun15) Yun, M. S., Aretxaga, I., Gurwell, M. A., et al. 2015, MNRAS, 454, 3485

(ref: Zhang2018) Zhang, H. & Yan, H. 2018, MNRAS, 475, 2415

(ref: Zhang2015) Zhang, H., Yan, H., & Dong, L. 2015, ApJ, 804, 142

# Continuum-subtracted spectra

Presented in this appendix are the figures showing the total spectra compared with the continuum-subtracted spectra for each source (see Figures [12](#fig:Az3_contsub) and [13](#fig:BRI_contsub)).

![](Az3_allspw_trunc_lesschans_spectralreg.png)

![](Bri_allspw_trunc_ciifo1.png)

# Lensing model for BRI0952

This appendix includes the figures detailing the Visilens lensing model results, which are given in Fig. [14](#fig:img_model_lensing).

![](img_model_2.png)

# Lensing model for companions to BRI0952

Appendix includes the figures detailing the Visilens lensing model results for the companions of BRI0952, which are given in Fig. [15](#fig:comp_lensing).

![](img_model_comps.png)

# BRI0952 Img-N \[C ii\] spectra

Appendix includes the \[C ii\] spectra from Img-N of the quasar BRI0952 used in analysis of outflow properties as described in Section [4.5](#subsec:outflows).

![](BRI0952_top_spec.png)

# Velocity gradient of LBG-3

This appendix includes a velocity map showing the velocity gradient detected in \[C ii\] between LBG-3 and AzTEC-3.

![](LBG3_velgrad.png)

# \[CII\] and continuum offset of LBG-3

This appendix includes figures showing the \[C ii\] and continuum offset for LBG-3.

![image](Az3_cont_CII.png)

[^1]: Hot dust-obscured galaxies are a class of high-redshift, dust-obscured, AGN-dominated galaxies.

[^2]: http://casa.nrao.edu/ (cite: mcmullin07)

[^3]: We note that the results of this paper do not change when using other tools such as imcontsub or statcont (cite: statcont18).

[^4]: This extraction could be done through a number of different methods; however, we find that the outcomes of these methods remain consistent with the method employed in this paper. We also note that methods such as *uv*-plane fitting introduce bias in a similar way to image-plane fitting through base-assumptions of, e.g., a model to describe the source, boundary conditions, and so on.

[^5]: We define $N_{beams} = A_{extraction}/A_{beam}$.

[^6]: Again, similar to BRI0952; if other methods are used, the results remain consistent with the regional spectral extraction used here.

[^7]: In this analysis, we assume $L_{\rm FIR} \sim 0.75 \times L_{\rm IR,}$ following (cite: Decarli17).

[^8]: The lensing magnification factor we utilized to correct the extent was $\mu = 3$.

</paper>

## Items to check

```json
[
 {
  "path": "processing.imaging.line_free_channels.evidence[0]",
  "value": "AzTEC-3: frequency range up to 300 GHz; BRI0952: 335.3-336.9, 347.1-347.7, 348.97-348.98, and 350.45-350.67 GHz",
  "failed_quote": "In the case of AzTEC-3, we used the frequency range of the observations up to 300 GHz due to the possible additional [C ii] wing feature seen in the 300.5-301 GHz range and the width of the [C ii] line (see Figures 7 and 12)."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[1]",
  "value": "Lens parameters: (x_L, y_L), ellipticity e_L, position angle phi_L; Source parameters: Sersic profile with (x_S, y_S), flux density, Sersic index, half-light radius, axis-ratio, position angle; 5 frequency bins across [C II]",
  "failed_quote": "To investigate this, we split the [C ii] line into five bins constituting five different frequency ranges across the line (these can be seen in Figure 14) and ran Visilens, with the source and lens parameters as specified above, on these bins."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Single and double Gaussian fits evaluated via reduced chi^2; 2D Gaussian image fitting via CASA imfit",
  "failed_quote": "The [C ii] spectral line profile of AzTEC-3 shows the presence of high-velocity wings at a $\\sim 24 \\sigma$ level -and the profile is better fit with a double Gaussian to account for this (Figure 7)- where the reduced $\\chi^2$ is improved by more than a factor of four using a double-Gaussian fit."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[2]",
  "value": "Flat LambdaCDM cosmology with H0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7; Chabrier IMF; Constant star formation history and Calzetti reddening law for AzTEC-3; SFR ~ 10^-10 L_IR [L_sun]; De Looze et al. (2014) starburst relation for SFR_[CII]",
  "failed_quote": "We estimated their SFR's using the relation $\\rm log(SFR)\\,[M_{\\odot}/yr] = 1.0 -7.06\\times log(L_{[CII]})\\,[L_{\\odot}]$ from (cite: DeLooze14) for starburst galaxies, computed their $L_{\\rm{IR}}$ using the relation in Section 4.3 (cite: Carilli13), and used a modified blackbody approximation (cite: Knudsen03) to recover their $S_{350 \\rm{GHz}}$."
 },
 {
  "path": "analysis_steps[4].validation.evidence[1]",
  "value": "Compared SF-only and AGN+SF fits in DecompIR; compared SFR_IR with SFR_[CII]",
  "failed_quote": "We derive SFRs through an additional method using the [C ii] -SFR relation for starburst galaxies from (cite: DeLooze14) (provided in Section 3.2.2), which are given in Table [tab:derived_props]."
 },
 {
  "path": "analysis_steps[5].key_parameters[0].evidence[0]",
  "value": "R_out = 7.5 kpc (AzTEC-3), R_out = 2.3 kpc (BRI0952, lensing corrected with mu = 3); v_outf = 0.5 x FWHM_broad",
  "failed_quote": "We determined the outflow radius as the major axis of the extent of the [C ii] emission for AzTEC-3 ($\\sim 7.5$ kpc) and BRI0952 ($\\sim 2.3$ kpc); for BRI0952, this measurement was taken using the major axis through both the image plane top and bottom images combined, and corrected for lensing magnification."
 }
]
```
