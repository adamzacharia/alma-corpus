# An ALMA survey of the SCUBA-2 cosmology legacy survey UKIDSS/UDS field: Dust attenuation in high-redshift Lyman-break galaxies

`2020MNRAS.492.4927K` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Koprowski, M. P. | arXiv: 2001.00402 | DOI: 10.1093/mnras/staa160

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do ALMA-detected z~3 Lyman-break galaxies in the UDS field sit on the IRX-beta relation, and how do the dust attenuation curve shape, stellar age, stellar mass and sSFR explain their offset  
  > "In this work, we were able to precisely investigate the dust attenuation properties of high-redshift Lyman-break galaxies, as quantified via the IRX-$\beta$ relation, thanks to the availability of the FIR data." (Introduction)
- Target **41 ALMA-detected z~3 LBGs in the UDS field (AS2UDS IDs, Table 1)**: coordinates _not stated_; z/distance z ~ 2.7-3.5 (quartile range)  
  > "We start by noting that the quartile redshift range spanned by the 41 ALMA-detected LBGs analysed here corresponds to $z\sim 2.7$–3.5" (Results & Discussion (Fraction of obscured star formation)); "In our analysis we adopt the photometric redshifts for the 41 LBGs in our sample from" (SED fitting); distance from photometric redshifts from Dudzeviciute et al. 2019 (magphys)  
  > "We start by noting that the quartile redshift range spanned by the 41 ALMA-detected LBGs analysed here corresponds to $z\sim 2.7$–3.5" (Results & Discussion (Fraction of obscured star formation)); "In our analysis we adopt the photometric redshifts for the 41 LBGs in our sample from" (SED fitting)
- Target **209 ALMA-undetected LBGs in the AS2UDS ALMA coverage (stacked)**: coordinates _not stated_; z/distance _not stated_; distance from eazy photometric redshifts  
  > "for the ALMA-faint sources, in the absence of useful photometric constraints on their FIR emission, redshifts were determined using the eazy template-fitting code." (SED fitting)

## Data provenance

- ALMA projects: 2012.1.00090.S, 2015.1.01528.S, 2016.1.00434.S, 2017.1.01492.S
- bands: Band 7 (870 um)  
  > "(Band-7) imaging between November 2013 and May 2017, with an initial pilot study of 30 of the brightest SCUBA-2 sources in Cycle 1" (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: average 870 um depths 0.25, 0.34, 0.23 and 0.09 mJy/beam (Cycles 1, 3, 4, 5)  
  > "with average depths of $\sigma_{870}=0.25, 0.34, 0.23$ and 0.09 mJy beam$^{-1}$ (Cycles 1, 3, 4 and 5, respectively)" (Data)
- time on source: _not stated_
- observing dates: November 2013 to May 2017 (Cycles 1, 3, 4, 5)  
  > "(Band-7) imaging between November 2013 and May 2017, with an initial pilot study of 30 of the brightest SCUBA-2 sources in Cycle 1" (Data)
- pi or archival as stated: _not stated_
- Other facility **SCUBA-2 Cosmology Legacy Survey (S2CLS) 850 um map**: Parent catalogue of 716 submm sources that ALMA followed up  
  > "The starting point for our analysis is the catalogue of 716 sub-millimetre sources detected in the 850-${\rm \mu m}$ map of the UDS field from the SCUBA-2 Cosmology Legacy Survey" (Data)
- Other facility **UKIDSS UDS DR11 UV/optical/near-IR catalogue**: Parent photometric catalogue used to select LBGs and for SED fitting  
  > "We start by updating the LBG selection using the new UV/optical/near-IR DR11 UDS catalogue (from the DR8 used previously)." (Data)
- Other facility **Herschel (HerMES SPIRE, PEP PACS)**: Far-IR photometry used in the magphys SED modelling of the AS2UDS sources  
  > "as provided by the public releases of the HerMES" (Data)
- Other facility **HST CANDELS**: High-resolution optical imaging for five IR-bright LBGs (morphology check)  
  > "This work is based on observations taken by the CANDELS Multi-Cycle Treasury Program with the NASA/ESA HST" (Acknowledgements); "Based on this small sample we can see no clear correlation between $\delta$ and the level of disturbance." (Results & Discussion (Scatter from the attenuation curves))
- External data: AS2UDS ALMA 870 um catalogue of 708 SMGs (S870 >~ 1 mJy, 4.3 sigma) used for detections  
  > "catalogued 708 sub-millimetre galaxies (SMGs) brighter than $S_{870}\gtrsim 1$ mJy (4.3$\sigma$, or a false-positive rate of 2%) in the full sample." (Data) [from Stach et al. 2019 (cite: Stach_2019)]
- External data: SCUBA-2 S2CLS 850 um source catalogue of 716 sources  
  > "The starting point for our analysis is the catalogue of 716 sub-millimetre sources detected in the 850-${\rm \mu m}$ map of the UDS field from the SCUBA-2 Cosmology Legacy Survey" (Data) [from Geach et al. 2017 (cite: Geach_2017)]
- External data: Photometric redshifts and magphys properties (stellar masses, L_IR) for the AS2UDS SMGs  
  > "Photometric redshifts and multi-wavelength properties for the SMGs in the AS2UDS sample are presented in" (Data) [from Dudzeviciute et al. 2019 (cite: Dudzeviciute_2019)]
- External data: Earlier UDS LBG sample, updated here with DR11  
  > "We matched the SMGs from the ALMA Band-7 $>4.3\,\sigma$ catalogue with the UDS LBG sample from" (Data) [from Koprowski et al. 2018 (cite: Koprowski_2018)]
- External data: 185 FIR SED templates (local and high-z starburst, 19-60 K) used to fit L_IR  
  > "we fit the dust emission SEDs, using 185 FIR SED templates compiled by" (Physical properties); "with a range of dust temperatures spanning 19–60 K" (Physical properties) [from Swinbank et al. 2014 (cite: Swinbank_2014)]
- External data: z~3 best-fit FIR SED used to convert the stacked 870 um flux to L_IR  
  > "To translate the stacked flux to the IR luminosity, we adopt the $z \simeq 3$ best-fit FIR SED from" (Physical properties) [from Koprowski et al. 2018 (cite: Koprowski_2018)]
- External data: Best-fit f_obs versus stellar mass relation compared against  
  > "The solid line shows the best-fit function of" (Results & Discussion (Fraction of obscured star formation)) [from Whitaker et al. 2017 (cite: Whitaker_2017)]
- External data: UV and IR SFR conversion factors (2.5e-10 and 1.73e-10 Msun/yr/Lsun, Salpeter, x0.63 to Chabrier)  
  > "In order to find the values for the SFRs, we follow" (Results & Discussion (IRX-M* scatter)); "we also multiply both SFRs by a factor of 0.63 to convert to" (Results & Discussion (IRX-M* scatter)) [from Madau & Dickinson 2014 (cite: Madau_2014)]
- External data: SMG V-band obscuration A_V ~ 500 mag with gas-to-dust ratio 90+-25  
  > "the SMGs in the UDS field have, on average, a $V$-band obscuration of $A_V\sim 500$ mag towards the FIR-bright component" (Results & Discussion (Scatter from the attenuation curves)) [from Swinbank et al. 2014 and Simpson et al. 2017 (cite: Swinbank_2014; Simpson_2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 0.5 arcsec FWHM taper for the AS2UDS source-identification maps (cleaned continuum)  
  > "using cleaned, 0.5 arcsec FWHM-tapered continuum maps" (Data)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA calibration, analysis and source catalogue follow the AS2UDS papers  
  > "For more details of the calibration, analysis and catalogue see" (Data) [from (cite: Stach_2019)]
- Photometry and magphys SED analysis taken from earlier AS2UDS paper  
  > "for more details of the photometry and magphys analysis." (Data) [from (cite: Dudzeviciute_2019)]
- Star-formation histories (single/double burst, instantaneous, exponentially declining, continuous)  
  > "A range of different star-formation histories (SFHs) was assumed, including both single- and double-burst, instantaneous, exponentially declining and continuous models (see" (SED fitting) [from (cite: Koprowski_2018)]
- Dust emission prescription in cigale  
  > "and the dust emission is modeled following the prescriptions of" (SED fitting) [from (cite: Casey_2012c)]
- IR luminosity as a single constraint in cigale energy balance  
  > "modified cigale to include the IR luminosity as a single constraint in the energy-balance calculation." (Physical properties) [from (cite: Salim_2018)]
- LBG colour selection with UGR/BVR filters, shifted to higher redshifts  
  > "We identify galaxies at $z$$\simeq$3 using UGR, or BVR, filters" (Data); "extending to higher redshifts by simply shifting the colour space to longer wavelengths, as described by" (Data) [from (cite: Steidel_1996; Ouchi_2004)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging recipe (CASA version, calibrators, robust/weighting, cleaning, masks, primary-beam correction) is only given by reference to Stach et al. 2019
- Photometric catalogue (UDS DR11 UV/optical/NIR and IRAC photometry) is 'in prep', so the input fluxes for the cigale fits cannot be rebuilt from the paper
- cigale version and full parameter grid: ranges and steps for delta, B, tau1, tau2, f_m, ages, dust-emission parameters
- Which average local IRX-beta relation defines the zero point of Delta log(IRX) and how the 'offset' is computed
- Stacking details for the 209 ALMA-undetected LBGs (positions, weights, noise estimate, treatment of primary beam)
- How the ALMA-undetected LBGs' L_IR and attenuation were entered into the SED fit and which redshift/filters were used for eazy
- Exact photometric filters and aperture corrections used for the 11-band photometry
- Meaning of the 'bad UV fit' flag used for starred IDs in Table 1

## Analysis recipe

1. **Select z~3-5 LBG sample**: Colour-select LBGs from the updated K-selected UDS DR11 catalogue using UGR/BVR-like filter combinations, shifted for higher redshift; finds 8494 LBGs  
  > "We identify galaxies at $z$$\simeq$3 using UGR, or BVR, filters" (Data); "finding 8494 3$\lesssim$$z$$\lesssim$5 LBGs." (Data)
   - parameter: K < 25.3 parent catalogue, mass complete to log(M*/Msun) >~ 9.5  
  > "Since the parent optical catalogue is selected at $K$-band ($K<25.3$)" (Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Cross-match ALMA detections with LBGs**: Match AS2UDS >=4.3 sigma detections to LBGs within 0.7 arcsec radius; radius chosen from Monte Carlo of randomly shifted LBG catalogues  
  > "Out of 250 3$\lesssim$$z$$\lesssim$5 LBGs in the UDS field which fall within the primary beam coverage of the AS2UDS ALMA maps, 41 were found to have ALMA Band-7 detections ($\geq 4.3\sigma$) within a 0.7 arcsec search radius" (Data)
   - parameter: 1000 realizations, random shifts over 10 arcsec  
  > "In each of 1,000 realizations, an artificial LBG catalogue was constructed by shifting all the individual sources in the original catalogue in random directions over a distance of 10 arcsec." (Data)
   - parameter: search radius 0.7 arcsec  
  > "we found a false association rate of $\sim 3\%$ for a search radius of 0.7  arcsec, rising to $\sim 10\%$ at 1.5  arcsec" (Data)
   - fitting: _not stated_
   - validation: False association rate ~3% at 0.7 arcsec; about one false association expected among the 41  
  > "where only one of our optical counterparts is statistically expected to be a false association." (Data)
3. **Measure L_IR of ALMA-detected LBGs**: chi-squared fit of 185 FIR templates to the dust emission SEDs, L_IR integrated over rest-frame 8-1000 um  
  > "We find the best-fitting SEDs using a $\chi^2$ minimization approach and determine the $L_{\rm IR}$ by integrating between the rest-frame 8–1000 ${\rm \mu m}$ emission." (Physical properties)
   - parameter: templates span dust temperatures 19-60 K  
  > "with a range of dust temperatures spanning 19–60 K" (Physical properties)
   - fitting: chi-squared minimisation over templates  
  > "We find the best-fitting SEDs using a $\chi^2$ minimization approach" (Physical properties)
   - validation: Compared with magphys L_IR of Dudzeviciute et al. 2019 (5.0 vs 5.5 x 10^12 Lsun mean); difference attributed to the FIR libraries  
  > "where the small difference can be attributed to the variation in the FIR libraries used." (Physical properties)
4. **Stack ALMA-undetected LBGs**: Inverse-variance stacking of the ALMA 870 um maps at the LBG positions, then conversion of stacked flux to L_IR with the z~3 FIR SED of Koprowski et al. 2018  
  > "For the ALMA-undetected sources we measure their average ALMA Band-7 flux by inverse-variance stacking in the ALMA maps." (Physical properties); "To translate the stacked flux to the IR luminosity, we adopt the $z \simeq 3$ best-fit FIR SED from" (Physical properties)
   - fitting: _not stated_
   - validation: Stack consistent with Koprowski et al. 2016 non-detection stack, lower than Coppin 2015 and Koprowski 2018 stacks, explained by sample differences  
  > "This latter discrepancy is due to two main factors." (Physical properties)
5. **SED fit with variable attenuation curve**: Energy-balance SED fitting with cigale using Calzetti curve modified by slope delta and UV-bump amplitude B, with L_IR as a single constraint; stellar mass, L_UV and intrinsic SED from the best fit  
  > "we have chosen to refit the UV and IR parts of the SEDs using a code which allows us to easily vary the attenuation curve." (SED fitting); "with two free parameters: the relative slope of the attenuation curve, $\delta$, and the magnitude of the UV bump, $B$." (Attenuation curves)
   - software: cigale
   - parameter: four stellar metallicities 0.004, 0.008, 0.02, 0.05  
  > "four values of stellar metallicity (0.004, 0.008, 0.02 and 0.05)." (SED fitting)
   - parameter: Double-burst SFH with tau1, tau2 and late-burst mass fraction f_m free  
  > "with the star forming timescale, $\tau$, for both bursts of the star formation and the mass fraction of the late burst population, $f_{\rm m}$, being kept as free parameters." (Results & Discussion (IRX-beta scatter))
   - parameter: Error bars from Monte Carlo varying redshifts and photometry within Gaussian errors  
  > "we have performed a simple Monte Carlo simulation, where we have varied the redshifts and the photometry of each source by a random offset sampled from a Gaussian distribution with $1\sigma$ equal to the corresponding errors." (Physical properties)
   - assumption: Chabrier IMF, flat cosmology Omega_m=0.3, Omega_Lambda=0.7, H0=70  
  > "stellar IMF with assumed flat cosmology with $\Omega_{\rm m} = 0.3$, $\Omega_\Lambda = 0.7$ and H$_0 = 70$ km s$^{-1}$ Mpc$^{-1}$." (Introduction)
   - fitting: _not stated_
   - validation: Fixing the Calzetti curve gives statistically higher chi-squared; mean cigale stellar mass 5.3+-1.7e10 Msun consistent with magphys 6.4+-1.4e10 Msun  
  > "However, fixing the attenuation curve to that of Calzetti will produce SED fits which have statistically higher values of $\chi^2$ (worse fits) than when the attenuation laws are allowed to vary." (Values of IRX & beta); "To check for consistency, we compare the estimated stellar masses from our cigale analysis to those derived using magphys by" (Physical properties)
6. **Derive IRX and UV slope beta**: IRX = L_IR/L_UV; beta from a power-law fit to the best-fit SED between rest-frame 125 and 250 nm  
  > "To calculate IRX, we simply divided $L_{\rm IR}$ by $L_{\rm UV}$" (Values of IRX & beta); "In this work we decided to fit the power-law slope to the best-fitting SED between the rest-frame 125 and 250 nm." (Values of IRX & beta)
   - parameter: L_UV at rest-frame 1600 A taken from the best-fit SED  
  > "was determined from the best-fit SED" (Physical properties)
   - assumption: UV bump amplitude set to 0 when measuring beta  
  > "since it falls within the UV slope range (central rest-frame wavelength of 217.5 nm and FWHM of 35 nm)" (Values of IRX & beta)
   - fitting: Power-law fit to best-fit SED, not to photometry (about 4 photometric points in rest-frame UV)  
  > "and therefore the UV slopes calculated directly from the photometry, as oppose to the best-fit SEDs, have larger uncertainties." (Values of IRX & beta)
   - validation: _not stated_
7. **Relate IRX offset to attenuation slope**: Spearman correlation and linear fit between the offset of log(IRX) from the average relation and the relative attenuation slope delta  
  > "It can be seen that the two quantities do correlate, with the Spearman correlation of $0.89$ and the two-sided $p$-value of $\ll 0.001$." (Results & Discussion (Scatter from the attenuation curves))
   - fitting: Linear fit, Delta log(IRX) = (2.79+-0.22) x delta + (0.48+-0.06); fitting method not stated  
  > "We find the relation to be of a linear form with $\Delta{\rm log(IRX)}=(2.79\pm 0.22)\times \delta + (0.48\pm 0.06)$." (Summary)
   - validation: _not stated_
8. **Compute SFRs, sSFR and obscured fraction**: SFR_UV = 2.5e-10 x L_UV and SFR_IR = 1.73e-10 x L_IR (Msun/yr per Lsun), both x0.63 for Chabrier IMF; f_obs = SFR_IR/SFR_(UV+IR) compared to Whitaker et al. 2017  
  > "For UV SFRs we multiply $L_{\rm UV}$ by $2.5\times 10^{-10} \,{\rm M_\odot\,yr^{-1}\,L_\odot^{-1}}$" (Results & Discussion (IRX-M* scatter)); "we also multiply both SFRs by a factor of 0.63 to convert to" (Results & Discussion (IRX-M* scatter)); "the fraction of obscured star formation, $f_{\rm obs}\equiv {\rm SFR_{IR}/SFR_{UV+IR}}$" (Results & Discussion (Fraction of obscured star formation))
   - assumption: Salpeter-IMF conversions rescaled to Chabrier  
  > "we also multiply both SFRs by a factor of 0.63 to convert to" (Results & Discussion (IRX-M* scatter))
   - fitting: _not stated_
   - validation: Stacked LBG samples consistent with Whitaker et al. 2017 relation  
  > "It is clear that both stacked LBG samples are consistent with the findings of" (Results & Discussion (Fraction of obscured star formation))
9. **Compare stellar masses for varying vs Calzetti attenuation**: Compare cigale stellar masses from fits with variable attenuation curves to fits fixed at the Calzetti shape, as a function of delta  
  > "it is clear that galaxies with the greyest curves (largest $\delta$) will tend to have their stellar masses underestimated by a factor 2$-$3$\times$, when Calzetti curve is incorrectly assumed." (Stellar masses)
   - software: cigale
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **cigale** : Energy-balance SED fitting with variable attenuation curve to get stellar mass, L_UV, beta, intrinsic beta  
  > "we repeat the SED fitting using the energy-balance code cigale" (SED fitting)
- **magphys** : High-redshift magphys SED fits of the AS2UDS SMGs (photometric redshifts, comparison masses and L_IR) from Dudzeviciute et al. 2019  
  > "using the high-redshift version of the magphys code" (Data)
- **eazy** : Photometric redshifts of the ALMA-faint LBGs  
  > "redshifts were determined using the eazy template-fitting code." (SED fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA-detected LBGs among 3<z<5 LBGs in ALMA coverage | 41 of 250 | not stated | galaxies | 2 | Out of 250 3$\lesssim$$z$$\lesssim$5 LBGs in the UDS field which fall within the primary beam coverage of the AS2UDS ALMA maps, 41 were found to have ALMA Band-7 detections |
| False association rate at 0.7 arcsec search radius | ~3% | not stated | percent | 2 | we found a false association rate of $\sim 3\%$ for a search radius of 0.7  arcsec |
| Mean stellar mass of the 41 LBGs (cigale) | 5.3e10 | 1.7e10 | Msun | 5 | The mean mass for the 41 LBGs from cigale is ${M_\ast= 5.3\pm 1.7 \times 10^{10} {\rm M_\odot}}$ |
| Mean L_IR of the 41 LBGs (template fit) | 5.0e12 | +2.6/-1.5 e12 (standard deviation) | Lsun | 3 | with the mean value of ${L_{\rm IR}= 5.0^{+2.6}_{-1.5}\times 10^{12} {\rm L_\odot}}$ |
| Stacked 870 um flux of ALMA-undetected LBGs | 65 | 20 (3.2 sigma) | microJy | 4 | We acquire a $3.2\sigma$ detection of $S_{870}=65\pm 20\,{\rm \mu Jy}$ |
| Bluest intrinsic UV slope possible in the models (1 Myr population) | -2.7 | not stated | dimensionless | 5 | For the stellar population age of 1 Myr, the bluest UV slope possible within the models is about $-2.7$. |
| Mean age of the young burst | 25 | 6 | Myr | 5 | the mean age of the young burst in our sample, responsible for the slope of the rest-frame UV part of the stellar SED, is $25\pm 6$ Myr |
| Spearman correlation of Delta log(IRX) with delta | 0.89 | two-sided p << 0.001 | dimensionless | 7 | It can be seen that the two quantities do correlate, with the Spearman correlation of $0.89$ and the two-sided $p$-value of $\ll 0.001$. |
| Slope of Delta log(IRX) vs delta | 2.79 | 0.22 | dimensionless | 7 | We find the relation to be of a linear form with $\Delta{\rm log(IRX)}=(2.79\pm 0.22)\times \delta + (0.48\pm 0.06)$. |
| Intercept of Delta log(IRX) vs delta | 0.48 | 0.06 | dimensionless | 7 | We find the relation to be of a linear form with $\Delta{\rm log(IRX)}=(2.79\pm 0.22)\times \delta + (0.48\pm 0.06)$. |
| Fraction of AS2UDS ALMA-detected population in z~2.7-3.5 that are these LBGs | 16 | 2 | percent | 2 | these LBGs comprise only $16\pm 2$% (41 of 250) |
| Obscured star-formation fraction of ALMA-bright LBGs | >~0.95 | not stated | dimensionless | 8 | having their SFRs dominated by the IR-luminous dust component ($f_{\rm obs}\gtrsim 0.95$) |
| Stellar mass underestimate when Calzetti curve is wrongly assumed (greyest curves) | factor 2-3 | not stated | dimensionless | 9 | it is clear that galaxies with the greyest curves (largest $\delta$) will tend to have their stellar masses underestimated by a factor 2$-$3$\times$, when Calzetti curve is incorrectly assumed. |

## Qualitative findings

- ALMA-bright LBGs lie above and to the left of the local IRX-beta relation (bluer beta at given IRX)  
  > "We find that our ALMA-bright LBGs lie significantly off the locally calibrated IRX-$\beta$ relation and tend to have relatively bluer rest-frame UV slopes" (abstract)
- Intrinsic UV slope and stellar age do not correlate clearly with offset from the local relation  
  > "However, no clear correlation between the intrinsic UV slope and the offset between a given source and the local, average relation can be seen" (Results & Discussion (Scatter from the intrinsic UV slopes))
- FIR-bright LBGs are more massive than FIR-faint LBGs and have high sSFR (starburst regime)  
  > "We find that the FIR-bright LBGs are on average significantly more massive than their FIR-faint analogues" (Summary)

## Claim tuples

- H: Do ALMA-detected LBGs follow the local IRX-beta relation? | E: Measure IRX and beta from cigale best-fit SEDs for the 41 ALMA-detected LBGs and compare with the local relation | R: They lie well above the average relation with bluer beta at given IRX | F: Local IRX-beta cannot be used to infer L_IR for these FIR-bright LBGs | **supported**
- H: Is the IRX-beta scatter driven by attenuation curve shape rather than stellar age or intrinsic slope? | E: Colour-code IRX-beta by intrinsic beta, mass-weighted age and delta; correlate Delta log(IRX) with delta | R: Spearman 0.89 with delta; no clear correlation with intrinsic beta or age | F: Scatter mainly due to shallow attenuation curves, with age playing some role | **supported**
- H: Does fixing a Calzetti-like attenuation curve bias stellar masses? | E: Compare cigale stellar masses with variable vs fixed Calzetti curves | R: Greyest-curve galaxies have masses underestimated by a factor 2-3 under Calzetti | F: Attenuation curves must be allowed to vary when deriving masses of IR-bright galaxies | **supported**
- H: Are the ALMA-bright LBGs massive starbursts? | E: Compare IRX-M* and f_obs-M* with average relations and main-sequence offsets | R: Unusually high IRX at given mass, large sSFR and f_obs >~ 0.95 | F: ALMA-bright LBGs are massive galaxies undergoing a burst of star formation | **supported**
- H: Do shallow attenuation curves arise from geometric disconnection of dust and stars (disturbed morphology)? | E: Inspect HST CANDELS stamps of five IR-bright LBGs ordered by delta | R: No clear correlation between delta and level of disturbance in five sources | F: Cannot test the morphology link quantitatively; larger sample needed | **partially**

## Reasoning

- Why this data: FIR constraints are needed to measure dust-absorbed UV light and derive robust SFRs of LBGs  
  > "Hence, it is important to try to constrain the far-infrared (FIR) luminosities of LBGs to derive more robust estimates of their SFRs." (Introduction)
- Why this method: L_IR as a single constraint in cigale lets them sample many SFHs and attenuation laws, since the focus is on rest-frame UV not dust temperature  
  > "This approach is ideal for our analysis as we are not interested in details of the IR emission, such as characteristic dust temperature, instead our focus is on the rest-frame UV properties." (Physical properties)
- Alternative: Fixed Calzetti attenuation curve gives worse fits (higher chi-squared) for ALMA-bright LBGs  
  > "However, fixing the attenuation curve to that of Calzetti will produce SED fits which have statistically higher values of $\chi^2$ (worse fits) than when the attenuation laws are allowed to vary." (Values of IRX & beta)
- Alternative: Measuring beta directly from photometry rejected in favour of best-fit SED  
  > "and therefore the UV slopes calculated directly from the photometry, as oppose to the best-fit SEDs, have larger uncertainties." (Values of IRX & beta)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot reach quantitative conclusions on dust-star morphology due to lack of high-resolution UV and IR data  
  > "However, due to the lack of high-resolution UV and IR data, we cannot reach any quantitative statements." (Summary)
- Limitation (authors): Sample is a small UV-bright subset, not representative of the bulk of highly star-forming galaxies  
  > "this UV-bright subset is far from representative of the bulk of highly star-forming galaxies at these redshifts" (Results & Discussion (Fraction of obscured star formation))
- Limitation (authors): Attenuation curve slope and SFH are degenerate  
  > "It is important to note, that the attenuation curve slopes and the star-formation histories (with the resulting intrinsic UV slopes) are degenerate." (Values of IRX & beta)
- Caveat (inferred, ours): Attenuation curve slope delta is degenerate with SFH and with the L_IR constraint; no posterior or prior sensitivity shown
- Caveat (inferred, ours): ALMA-selected LBGs are selected by both UV and FIR brightness, so the offset from the local relation is partly a selection effect
- Caveat (inferred, ours): L_IR comes from template fits to a single ALMA 870 um point plus Herschel; dust temperature assumptions drive IRX
- Caveat (inferred, ours): Stellar mass differences between curves depend on the cigale model grid, which is not specified
- Caveat (inferred, ours): Only five sources have HST data, so the morphology interpretation is untested

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: UDS DR11 photometry catalogue (in prep) and the exact LBG list beyond Table 1
- Missing: cigale configuration files (parameter grid, version)
- Missing: ALMA calibration and imaging parameters (only by reference to Stach et al. 2019)
- Missing: Stacking procedure details for ALMA-undetected LBGs
- Missing: Definition of the reference IRX-beta relation for Delta log(IRX)
- Data volume (inferred): Reprocessing the four ALMA projects from raw data would be hundreds of GB; using published AS2UDS maps/catalogue and the photometry catalogue would need only a few GB
- Score (inferred): 2/5, Numeric results and Table 1 are given, and ALMA project codes are listed, but the photometric catalogue is unpublished, the cigale grid is not specified and ALMA processing is deferred to another paper
- Rediscovery candidate: no, The input photometric catalogue is 'in prep' and the SED fitting grid and ALMA imaging recipe are incomplete, so the main results cannot be redone from the paper alone

## Links

- Method: Stach et al. 2019 (cite: Stach_2019) (AS2UDS ALMA calibration, imaging, source catalogue)
- Method: Dudzeviciute et al. 2019 (cite: Dudzeviciute_2019) (Photometry, magphys SED fits and redshifts of AS2UDS SMGs)
- Method: Koprowski et al. 2018 (cite: Koprowski_2018) (LBG sample, SFH details, FIR SED for stacking)
- Method: Salim et al. 2018 (cite: Salim_2018) (cigale with L_IR as single constraint)
- Method: Swinbank et al. 2014 (cite: Swinbank_2014) (FIR SED template library and Herschel deblending)
- Companion: Simpson et al. 2017 (cite: Simpson_2017) (Cycle 1 pilot ALMA follow-up of SCUBA-2 sources in UDS)
- Companion: Geach et al. 2017 (cite: Geach_2017) (SCUBA-2 Cosmology Legacy Survey catalogue)
- Related: AS2UDS
- Related: SCUBA-2 Cosmology Legacy Survey (S2CLS)
- Related: UKIDSS UDS
- Related: HST CANDELS
- Related: HerMES
- Related: PEP

## Checks

```json
{
 "quotes": 104,
 "quotes_ok": 104,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 114,
  "stated": 68,
  "rate": 0.596
 },
 "evidence_ok": true
}
```
