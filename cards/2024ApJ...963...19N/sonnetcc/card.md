# On the Evidence for Molecular Outflows in High-redshift Dusty Star-forming Galaxies

`2024ApJ...963...19N` | The Astrophysical Journal 2024 | first author: Nianias, James | arXiv: 2403.09104 | DOI: 10.3847/1538-4357/ad188a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Is the evidence for molecular outflows (OH 119 um absorption more blueshifted than [CII] emission) in five lensed high-z DSFGs robust once atmospheric-correction precision and per-channel noise are properly accounted for, and does searching channel maps reveal separate kinematic components?  
  > "Taking these factors into consideration, we re-analyze OH and \[CII\] data taken with ALMA for the five sources where such data is available, of which four were categorised as exhibiting outflows." (abstract)
- Target **SPT0202-61**: coordinates _not stated_; z/distance z = 5.0180  
  > "SPT0202-61 | 5.0180 | 43 | 54" (Table 1); distance from _not stated_
- Target **SPT0418-47**: coordinates _not stated_; z/distance z = 4.2248  
  > "SPT0418-47 | 4.2248 | 87 | 19" (Table 1); distance from _not stated_
- Target **SPT0441-46**: coordinates _not stated_; z/distance z = 4.4770  
  > "SPT0441-46 | 4.4770 | 28 | 29" (Table 1); distance from _not stated_
- Target **SPT2132-58**: coordinates _not stated_; z/distance z = 4.7677  
  > "SPT2132-58 | 4.7677 | 17 | 25" (Table 1); distance from _not stated_
- Target **SPT2319-55**: coordinates _not stated_; z/distance z = 5.2943  
  > "SPT2319-55 | 5.2943 | 30 | 21" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00191.S, 2016.1.01499.S
- bands: Band 8 for the OH 119 um observations (band of the [CII] observations not stated)  
  > "ALMA band 8, the band in which all the OH observations in and were made" (1 INTRODUCTION)
- frequencies and spectral setup: OH: one sideband with two partially-overlapping SPWs on the OH lines, other sideband with two partially-overlapping continuum SPWs; [CII]: two SPWs on the line in one sideband, two continuum SPWs in the other; each SPW at 1.875 GHz bandwidth; sidebands offset by 12 GHz  
  > "The OH observations were made with one sideband containing two partially-overlapping spectral windows covering the OH lines at the source redshift, and an alternate sideband containing two partially-overlapping spectral windows covering only the dust continuum." (2 ARCHIVAL OBSERVATIONS AND DATA REDUCTION); "In both the OH and \[CII\] observations, each spectral window is configured at its maximal possible bandwidth of $\SI{1.875}{GHz}$." (2 ARCHIVAL OBSERVATIONS AND DATA REDUCTION); "which has a fixed offset of 12 GHz with respect to the OH sideband" (4.3 Improving observing strategies)
- continuum bandwidth: continuum-only sideband made of two SPWs of 1.875 GHz each; for SPT2132-58 no usable continuum sideband data  
  > "The sole exception is the OH observations of SPT2132-58, for which infer OH absorption to cover nearly the entire bandpass, and which has no useable data in the continuum sidebands due to low atmospheric transmission." (2.2 Self-calibration)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Final common beams after convolution (BMAJ x BMIN, BPA): SPT0202-61 0.48 x 0.42 arcsec, 63 deg; SPT0418-47 0.55 x 0.35, 89; SPT0441-46 0.35 x 0.26, 79; SPT2132-58 0.43 x 0.36, 114; SPT2319-55 0.40 x 0.32, 64  
  > "we convolved the OH channel maps, continuum-subtracted \[CII\] channel maps, and dust continuum maps of each target source to the smallest possible common angular resolution (synthesised beam)" (2.3 Channel maps and integrated spectra); "SPT0418-47 | 70 | 0.55 | 0.35 | 89" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Integration time (min), OH / [CII]: SPT0202-61 43/54; SPT0418-47 87/19; SPT0441-46 28/29; SPT2132-58 17/25; SPT2319-55 30/21  
  > "lists the redshifts and integration times of the observations in OH and \[CII\] for each source." (2 ARCHIVAL OBSERVATIONS AND DATA REDUCTION); "SPT0418-47 | 4.2248 | 87 | 19" (Table 1)
- observing dates: _not stated_
- pi or archival as stated: Archival data from the ALMA archive (the OH data of the two earlier papers plus ancillary [CII] observations)  
  > "We obtained data for the same OH $\SI{119}{\um}$ observations presented in and , along with data from ancillary observations covering the \[CII\] $\SI{158}{\um}$ line of each target, from the ALMA archive." (2 ARCHIVAL OBSERVATIONS AND DATA REDUCTION)
- Line: OH 119 um doublet (absorption) (not stated)
- Line: [CII] 158 um (emission) (not stated)
- External data: Continuum estimate for SPT2132-58 used to judge that the low-frequency (high-velocity) channels are absorption-free  
  > "These channels are absorption-free according to the continuum estimate provided in ." (2.3 Channel maps and integrated spectra) [from reference stripped in the paper text (earlier OH papers, Spilker et al. 2018 / 2020a)]
- External data: Published OH and [CII] spectra used as a guide to select line-free frequency ranges  
  > "We therefore selected frequency ranges free from any OH absorption or \[CII\] emission, using the spectra shown in and as a guide" (2.2 Self-calibration) [from reference stripped in the paper text (Spilker et al. 2018 / 2020a)]
- External data: Mass outflow rate method (OH abundance from Sgr B2, thin shell, optical-depth correction from a 14-object sample) discussed from earlier work, not re-derived  
  > "the mass outflow rate for each object thought to host an outflow is estimated using the depth of the blueshifted OH absorption." (4.2 Outflow properties) [from Spilker et al. 2020b (cite: spilker20b); (cite: gc02); (cite: rupke05); (cite: ga17)]

## Processing

### Calibration

- pipeline or manual: Archive calibration scripts (pipeline of the observing cycle), run by authors or by the East Asia ALMA helpdesk; OH data of SPT0441-46 and [CII] data of SPT2132-58 re-calibrated manually  
  > "We calibrated each visibility set in the same manner as reported in and , using the calibration script either executed by us (for SPT0418-47 and SPT2132-58) or by the East Asia ALMA helpdesk" (2.1 Calibration); "which we re-calibrated manually, though excluding the data flagged in the initial automatic pipeline as for the other sources" (2.1 Calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-calibration on a continuum image CLEANed to 3x thermal noise; no amplitude self-calibration  
  > "We then used these CLEAN continuum maps to perform phase-only self-calibration of the target visibilities" (2.2 Self-calibration); "we did not perform any self-calibration in amplitude, as deriving robust amplitude corrections would require images having much higher signal-to-noise ratios." (2.2 Self-calibration)

### Imaging

- task: CLEAN deconvolution (task name not stated); continuum maps CLEANed to 3x thermal noise, channel maps to 1.5x thermal noise  
  > "the resulting continuum maps to three times the thermal noise level" (2.2 Self-calibration); "For each source, we CLEANed the channel maps to $1.5$ times the thermal noise level as measured in the channel map corresponding to the central velocity of the higher-frequency (lower-velocity) component of the OH doublet." (2.3 Channel maps and integrated spectra)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane continuum subtraction using the same line-free channels as used for the continuum maps (applied to [CII] and OH visibilities for the channel maps; continuum retained in integrated OH spectra)  
  > "we performed continuum subtraction on the \[CII\] visibilities in the uv-plane, fitting the continuum level using the same channels in the \[CII\]-containing spectral windows as were used to make continuum maps" (2.3 Channel maps and integrated spectra); "when presenting the spatially-integrated spectra in OH, however, we retain the continuum" (2.3 Channel maps and integrated spectra)
- line free channels: Chosen by eye from the earlier papers' spectra as free of OH absorption or [CII] emission (ranges not listed); SPT2132-58 OH: all channels of both OH SPWs used for the continuum image  
  > "We therefore selected frequency ranges free from any OH absorption or \[CII\] emission, using the spectra shown in and as a guide" (2.2 Self-calibration); "we used all channels in both OH-containing spectral windows to make the continuum image" (2.2 Self-calibration)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: OH channel maps, continuum-subtracted [CII] channel maps and continuum maps convolved to the smallest possible common beam; [CII] channel maps made with the same channel widths as OH (50, 70, 75, 150, 75 km/s)  
  > "To make a proper comparison of the OH and \[CII\] spectral profiles, we used the same widths when making \[CII\] channel maps for each source." (2.3 Channel maps and integrated spectra); "SPT2132-58 | 150 | 0.43 | 0.36 | 114" (Table 2)
- final beam: SPT0202-61 0.48 x 0.42 arcsec PA 63; SPT0418-47 0.55 x 0.35 PA 89; SPT0441-46 0.35 x 0.26 PA 79; SPT2132-58 0.43 x 0.36 PA 114; SPT2319-55 0.40 x 0.32 PA 64  
  > "After convolution, the final beam sizes are only slightly larger than the beam sizes reported in and for the OH observations." (2.3 Channel maps and integrated spectra); "SPT0441-46 | 75 | 0.35 | 0.26 | 79" (Table 2)
- final rms: _not stated_

### Inherited from earlier work

- Calibration performed in the same manner as the earlier OH papers  
  > "We calibrated each visibility set in the same manner as reported in and" (2.1 Calibration) [from Spilker et al. 2018 (cite: spilker18) and Spilker et al. 2020a (cite: spilker20a), as written 'in and ']
- Further details of the OH observations (setup) are in the earlier papers  
  > "Further details of the OH observations can be found in and ." (2 ARCHIVAL OBSERVATIONS AND DATA REDUCTION) [from Spilker et al. 2018 (cite: spilker18) and Spilker et al. 2020a (cite: spilker20a)]
- Continuum subtraction approach follows the earlier papers  
  > "like in and , we performed continuum subtraction on the \[CII\] visibilities in the uv-plane" (2.3 Channel maps and integrated spectra) [from Spilker et al. 2018 (cite: spilker18) and Spilker et al. 2020a (cite: spilker20a)]
- Integration region for spatially-integrated spectra (continuum above 3 sigma) follows the earlier papers  
  > "integrating over regions where continuum is detected above $3\sigma$ following the same procedure as used in and" (2.3 Channel maps and integrated spectra) [from Spilker et al. 2018 (cite: spilker18) and Spilker et al. 2020a (cite: spilker20a)]
- SPT2132-58 OH continuum image made from all channels in both OH SPWs  
  > "following , we used all channels in both OH-containing spectral windows to make the continuum image" (2.2 Self-calibration) [from earlier OH paper (reference stripped in text)]
- Channel widths chosen to be approximately the same as in the earlier papers  
  > "chosen to be approximately the same as those in and" (2.3 Channel maps and integrated spectra) [from Spilker et al. 2018 (cite: spilker18) and Spilker et al. 2020a (cite: spilker20a)]
- No amplitude self-calibration, as in the earlier papers  
  > "Like and , we did not perform any self-calibration in amplitude" (2.2 Self-calibration) [from Spilker et al. 2018 (cite: spilker18) and Spilker et al. 2020a (cite: spilker20a)]

### Not stated but needed to reproduce (our reading)

- CASA version and ALMA pipeline version for each project
- Flux, bandpass and phase calibrator names used for each execution block, and the flux-scale accuracy
- Exact flagging applied in the manual re-calibrations of SPT0441-46 (OH) and SPT2132-58 ([CII])
- CASA imaging task and parameters: weighting and robust, cell size, image size, masks, deconvolver, uv-range, primary-beam correction
- Explicit line-free channel ranges (velocity or frequency) used for continuum images, continuum subtraction and continuum level for each source
- Self-calibration solution intervals, number of iterations, reference antenna and the S/N reached
- Integration regions (continuum above 3 sigma mask) and the exact continuum image used to define them
- Procedure for finding the S/N-maximising velocity range, and the lowest detectable [CII] velocity per source
- ESSENCE configuration (masking of the source when measuring the noise autocorrelation function) and version
- Definition of the annulus used for the rms check and of the spatial-pattern criteria used to call a separate kinematic component
- Archive MOUS identifiers or execution blocks mapped to each source and line

## Analysis recipe

1. **calibrate archive visibilities**: Archive pipeline calibration scripts run by the authors or the East Asia ALMA helpdesk, with manual re-calibration for OH of SPT0441-46 and [CII] of SPT2132-58  
  > "We calibrated each visibility set in the same manner as reported in and , using the calibration script either executed by us (for SPT0418-47 and SPT2132-58) or by the East Asia ALMA helpdesk" (2.1 Calibration); "which we re-calibrated manually, though excluding the data flagged in the initial automatic pipeline as for the other sources" (2.1 Calibration)
   - software: ALMA calibration pipeline, CASA
   - parameter: Re-calibration of SPT0441-46 OH motivated by high noise in images from the original calibration; for SPT2132-58 [CII], a discontinuous noise jump between adjacent SPWs from an issue in the original script  
  > "Our re-calibration of the OH observations of SPT0441-46 was motivated by concerns about the high noise level found in the images made with the original calibration" (footnote 2)
   - fitting: _not stated_
   - validation: Continuum maps and integrated OH spectra compared with the earlier papers and found consistent within noise  
  > "the dust continuum maps that we produced for all sources have morphologies and signal-to-noise ratios in close agreement with those reported in and" (2.1 Calibration)
2. **continuum imaging and phase-only self-calibration**: Line-free frequency ranges of the line SPWs combined with the continuum sideband to image the continuum; CLEAN to 3x thermal noise; phase-only self-calibration applied to target visibilities  
  > "combined these with the continuum-only sidebands when making continuum images." (2.2 Self-calibration); "We then used these CLEAN continuum maps to perform phase-only self-calibration of the target visibilities" (2.2 Self-calibration)
   - software: CASA
   - parameter: Thermal noise determined from maps with large phase-center shifts relative to the source positions  
  > "We determined the thermal noise level by making maps with large shifts in phase center relative to the source positions." (footnote 4)
   - parameter: SPT2132-58 OH: all channels of both OH SPWs used for the continuum image  
  > "we used all channels in both OH-containing spectral windows to make the continuum image" (2.2 Self-calibration)
   - assumption: No amplitude self-calibration because robust amplitude corrections would need higher S/N images  
  > "we did not perform any self-calibration in amplitude, as deriving robust amplitude corrections would require images having much higher signal-to-noise ratios." (2.2 Self-calibration)
   - fitting: _not stated_
   - validation: Self-calibration gave smaller residual phase errors and improved S/N in final continuum maps, which agree with earlier papers  
  > "which resulted in smaller residual phase errors and hence significantly improved signal-to-noise in the final CLEAN continuum maps." (2.2 Self-calibration)
3. **make continuum-subtracted channel maps at a common resolution**: Channel maps CLEANed to 1.5x thermal noise from the self-calibrated visibilities, uv-plane continuum subtraction, convolution of OH, [CII] and continuum maps to a common beam  
  > "The channel maps used in our study as presented in Section [3.2](#section:chanmaps) were generated from the self-calibrated visibilites." (2.3 Channel maps and integrated spectra); "we convolved the OH channel maps, continuum-subtracted \[CII\] channel maps, and dust continuum maps of each target source to the smallest possible common angular resolution (synthesised beam)" (2.3 Channel maps and integrated spectra)
   - software: CASA
   - parameter: Channel widths (km/s): SPT0202-61 50, SPT0418-47 70, SPT0441-46 75, SPT2132-58 150, SPT2319-55 75; same widths for [CII]  
  > "SPT0202-61 | 50 | 0.48 | 0.42 | 63" (Table 2); "SPT2319-55 | 75 | 0.40 | 0.32 | 64" (Table 2)
   - parameter: CLEAN threshold 1.5x thermal noise measured in the channel map at the central velocity of the higher-frequency OH doublet component  
  > "we CLEANed the channel maps to $1.5$ times the thermal noise level as measured in the channel map corresponding to the central velocity of the higher-frequency (lower-velocity) component of the OH doublet." (2.3 Channel maps and integrated spectra)
   - fitting: _not stated_
   - validation: rms in an annulus around the source in each channel map is only about 10% to 30% above thermal noise  
  > "finding it to be only $\sim 10\%$ to $30\%$ higher than the thermal noise level" (2.3 Channel maps and integrated spectra)
4. **extract spatially-integrated spectra with per-channel uncertainties**: Integrate OH and [CII] over regions with continuum above 3 sigma; per-channel 1 sigma uncertainty from the noise autocorrelation function of each channel map with the source masked, using ESSENCE; continuum level and uncertainty from line-free channels (SPT2132-58: channels at the low-frequency end of the bandpass)  
  > "ESSENCE derives uncertainties in spatially-integrated flux density using the noise autocorrelation function, as measured from each channel map with the target source masked out." (2.3 Channel maps and integrated spectra); "we estimated the continuum level using the channels at the low-frequency (i.e. high-velocity) end of the bandpass." (2.3 Channel maps and integrated spectra)
   - software: ESSENCE
   - parameter: Integration regions where continuum is detected above 3 sigma  
  > "integrating over regions where continuum is detected above $3\sigma$ following the same procedure as used in and" (2.3 Channel maps and integrated spectra)
   - fitting: _not stated_
   - validation: Noise agrees with the rms times square root of number of beams approximation to within 5 to 15%  
  > "(to within 5 – 15%, varying from source to source and channel to channel)" (footnote 5)
5. **measure significance of blueshifted OH absorption**: Integrate the OH spectrum bluewards of the lowest detectable [CII] velocity over the range that maximises the S/N of the putative absorption; divide by the per-channel uncertainties  
  > "we integrate the OH spectrum of each source over velocities bluewards of the lowest detectable \[CII\] velocity until the signal-to-noise level of this putative absorption is maximised" (3.1 Integrated spectra)
   - software: ESSENCE
   - parameter: 3 sigma threshold for a statistically significant detection  
  > "we find statistically significant ($\geq 3 \sigma$) evidence for blueshifted absorption in the spatially-integrated spectrum of only one source, SPT2319-55, at $6.1 \sigma$." (3.1 Integrated spectra)
   - fitting: _not stated_
   - validation: Nominal absorption depths agree with the earlier papers within measurement uncertainties  
  > "the nominal absorption depth in these channels is the same as that in and to within measurement uncertainties" (3.1 Integrated spectra)
6. **bound residual atmospheric and bandpass errors**: Apply each target's blueshifted velocity range to its secondary-calibrator spectrum (after atmospheric and bandpass calibration) and compute 3 sigma upper bounds on residual features as a fraction of continuum; compare with the OH absorption strength  
  > "we compute $3\sigma$ upper bounds for any residual bandpass features as a fraction of the continuum" (3.1 Integrated spectra)
   - assumption: Secondary calibrators observed at similar elevation to the target and with higher continuum S/N, so their residuals bound those in the target  
  > "These calibrators were observed at a similar elevation but have a higher signal-to-noise in the continuum compared to the target sources." (3.1 Integrated spectra)
   - fitting: _not stated_
   - validation: None of the secondary-calibrator spectra show statistically significant residual features; absorption is about an order of magnitude above the bound in most sources, except SPT0418-47  
  > "none of the secondary calibrator spectra exhibit statistically significant residual features." (3.1 Integrated spectra)
7. **compare OH and [CII] spatio-kinematics in channel maps**: Inspect OH and [CII] channel maps and velocity-integrated maps for OH more blueshifted than [CII], and for OH features moving in a different direction around the Einstein ring than [CII]  
  > "we searched the channel maps for features in OH absorption that show a different spatio-kinematic pattern than \[CII\] emission." (3.2 Channel maps)
   - parameter: Absorption patches counted as genuine only if coincident with dust continuum and deeper than any patch not coincident with the continuum (spurious patches seen at 4 sigma or more)  
  > "We therefore only consider as genuine those absorption patches that are not only spatially-coincident with the dust continuum, but that are also deeper than any apparent absorption patches that are not spatially-coincident with the dust continuum." (3.2 Channel maps)
   - assumption: [CII] emission traces the rotating disc; OH absorption strength also depends on the background continuum brightness, so morphologies need not match exactly  
  > "we should not expect the morphology of the OH absorption to perfectly match that of the \[CII\] emission in individual channels even if both lines trace the same gas in the disc." (3.2 Channel maps)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging of ALMA data (specific tasks not named); listed in the Software section  
  > "CASA (cite: casaref), Astropy (cite: astropy:2013; astropy:2018; astropy:2022), Matplotlib (cite: mplref), ESSENCE (cite: tsukui23)" (Software)
- **ALMA calibration pipeline** : Archive pipeline for the corresponding ALMA cycle used for calibration scripts  
  > "The ALMA Science Archive provides uncalibrated visibilities along with scripts that allow users to calibrate the visibilities using the corresponding pipeline for the ALMA cycle in which the observations were made." (2.1 Calibration)
- **ESSENCE** : Per-channel 1 sigma uncertainties of spatially-integrated spectra from the noise autocorrelation function  
  > "To determine the $1\sigma$ uncertainties in individual channels of the integrated OH or \[CII\] spectra, we use the ESSENCE software package" (2.3 Channel maps and integrated spectra)
- **Astropy** : Listed in the Software section; specific use not stated  
  > "CASA (cite: casaref), Astropy (cite: astropy:2013; astropy:2018; astropy:2022), Matplotlib (cite: mplref), ESSENCE (cite: tsukui23)" (Software)
- **Matplotlib** : Listed in the Software section; specific use not stated (presumably plotting)  
  > "CASA (cite: casaref), Astropy (cite: astropy:2013; astropy:2018; astropy:2022), Matplotlib (cite: mplref), ESSENCE (cite: tsukui23)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SPT2319-55 blueshifted OH absorption strength (velocity range -712 to -262 km/s) | 2890 | 470 (6.1 sigma) | mJy km/s | 5 | SPT2319-55 / 75 / 0.40 / 0.32 / 64 / $[-712, -262]$ / $2890 \pm 470$ ($6.1 \sigma$) / 130 |
| SPT0441-46 blueshifted OH absorption strength (velocity range -462 to -187 km/s) | 1690 | 620 (2.7 sigma) | mJy km/s | 5 | SPT0441-46 / 75 / 0.35 / 0.26 / 79 / $[-462, -187]$ / $1690 \pm 620$ ($2.7 \sigma$) / 200 |
| SPT0418-47 blueshifted OH absorption strength (velocity range -525 to -245 km/s) | 2320 | 980 (2.4 sigma) | mJy km/s | 5 | SPT0418-47 / 70 / 0.55 / 0.35 / 89 / $[-525, -245]$ / $2320 \pm 980$ ($2.4 \sigma$) / 890 |
| SPT2132-58 blueshifted OH absorption strength (velocity range -675 to -375 km/s) | 2820 | 1170 (2.2 sigma) | mJy km/s | 5 | SPT2132-58 / 150 / 0.43 / 0.36 / 114 / $[-675, -375]$ / $2820 \pm 1170$ ($2.2 \sigma$) / 380 |
| Bandpass/atmospheric correction accuracy (3 sigma upper bound), SPT2319-55 | 130 | not stated | mJy km/s | 6 | SPT2319-55 / 75 / 0.40 / 0.32 / 64 / $[-712, -262]$ / $2890 \pm 470$ ($6.1 \sigma$) / 130 |
| Bandpass/atmospheric correction accuracy (3 sigma upper bound), SPT0441-46 | 200 | not stated | mJy km/s | 6 | SPT0441-46 / 75 / 0.35 / 0.26 / 79 / $[-462, -187]$ / $1690 \pm 620$ ($2.7 \sigma$) / 200 |
| Bandpass/atmospheric correction accuracy (3 sigma upper bound), SPT0418-47 | 890 | not stated | mJy km/s | 6 | SPT0418-47 / 70 / 0.55 / 0.35 / 89 / $[-525, -245]$ / $2320 \pm 980$ ($2.4 \sigma$) / 890 |
| Bandpass/atmospheric correction accuracy (3 sigma upper bound), SPT2132-58 | 380 | not stated | mJy km/s | 6 | SPT2132-58 / 150 / 0.43 / 0.36 / 114 / $[-675, -375]$ / $2820 \pm 1170$ ($2.2 \sigma$) / 380 |
| Bandpass correction precision relative to measurement uncertainty | within about 0.3 sigma for all sources except SPT0418-47 (about 1 sigma) | not stated | dimensionless | 6 | we found the bandpass to have been corrected to within $\lesssim 0.3 \sigma$ for all sources except SPT0418-47, for which the bandpass is corrected to $\sim 1\sigma$. |
| Number of sources with significant (>= 3 sigma) blueshifted OH absorption in integrated spectra | 1 of 5 (SPT2319-55); the others 2.7, 2.4, 2.2 sigma, SPT0202-61 none | not stated | dimensionless | 5 | The source that shows the next strongest putative blueshifted OH absortion is SPT0441-46, at a significance level of $2.7 \sigma$, followed by SPT0418-47 at $2.4 \sigma$ and SPT2132-58 at $2.2 \sigma$. |
| Sources with OH more blueshifted than [CII] in channel maps vs integrated spectra | 3 in channel maps vs 1 in integrated spectra | not stated | dimensionless | 7 | three sources exhibit more blueshifted OH absorption than \[CII\] emission in channel maps, compared with only one (of the same three) in spatially-integrated spectra |

## Qualitative findings

- SPT2319-55 shows the strongest evidence for an outflow: OH moves clockwise at the most blueshifted velocities while [CII] does not  
  > "making a strong case for a molecular outflow in SPT2319-55" (3.2 Channel maps)
- All five sources show evidence for a separate OH kinematic component plausibly associated with outflows  
  > "In brief, we find evidence of separate kinematic components plausibly associated with molecular outflows in all five of the sources included in our study." (5 SUMMARY AND CONCLUSION)
- Mass outflow rates of the earlier work have substantially higher uncertainties, in some cases consistent with zero  
  > "the putative mass-outflow rates – derived solely from the spatially-integrated spectra – must have substantially higher uncertainties than presented in" (4.2 Outflow properties)

## Claim tuples

- H: Do spatially-integrated OH and [CII] spectra show statistically significant OH absorption blueshifted beyond [CII] in the sources previously classed as outflows? | E: Recomputed per-channel uncertainties with ESSENCE and integrated OH over the S/N-maximising blueshifted range | R: Only SPT2319-55 exceeds 3 sigma (6.1 sigma); the other three tentative sources are 2.2 to 2.7 sigma | F: The integrated-spectrum evidence for outflows is significant in 1 of 5 sources, not 4 | **supported**
- H: Could residual atmospheric or bandpass errors produce the apparent blueshifted OH absorption? | E: Applied each target's velocity range to its secondary-calibrator spectrum and computed 3 sigma upper bounds | R: Absorption is roughly an order of magnitude above the bound in most sources; SPT0418-47 bound is comparable to the 1 sigma uncertainty | F: Calibration residuals cannot explain the absorption in most sources, but may contribute in SPT0418-47 | **partially**
- H: Do channel maps reveal outflow evidence diluted in the integrated spectra? | E: Compared OH and [CII] channel maps for blueshifted extent and spatio-kinematic pattern | R: Three sources show OH more blueshifted than [CII] in channel maps (vs one in integrated spectra); all five show an OH component with a different spatio-kinematic pattern | F: All five sources show evidence for a separate kinematic component plausibly tied to outflows | **supported**
- H: Are the earlier mass outflow rates reliable given the significance of the OH absorption? | E: Compared nominal absorption depths with the earlier work and assessed their significance | R: Nominal depths match the earlier results within uncertainties but significance is low | F: Mass outflow rates derived solely from integrated spectra have larger uncertainties, in some cases consistent with zero | **supported**

## Reasoning

- Why this data: Sources with high-resolution [CII] data as well as OH data (five of eleven) permit the channel-map checks  
  > "for which high-resolution \[CII\] $\SI{158}{\um}$ observations have been made with ALMA – five out of eleven in total" (1 INTRODUCTION)
- Why this method: Check bandpass precision to define the minimum level at which OH absorption can be considered genuine, and compute per-channel uncertainties  
  > "we check the precision of the overall bandpass calibration to define the minimum level whereby OH absorption features can be considered genuine." (1 INTRODUCTION)
- Alternative: Remaining six sources excluded because only low-resolution CO data exist for the checks  
  > "only have available observations in CO at angular resolutions far too low to permit the checks described above, and are therefore excluded from our study." (1 INTRODUCTION)
- How they decided it was enough: _not stated_
- Limitation (authors): For SPT0418-47 a nearby atmospheric O3 line means residual calibration errors may contribute to the measured absorption  
  > "we cannot rule out the possibility that residual calibration errors contribute in part to the measured absorption." (3.1 Integrated spectra)
- Limitation (authors): For SPT2132-58 no usable continuum sideband data exist, so the continuum level is uncertain  
  > "so no useable continuum spectrum can be produced at all given the restrictions on the ALMA correlator set-up." (4.3 Improving observing strategies)
- Caveat (inferred, ours): The 'different spatio-kinematic pattern' criterion is assessed by eye in channel maps with no quantitative test or false-positive rate
- Caveat (inferred, ours): Significance of the integrated absorption depends on the velocity range chosen to maximise S/N, which biases it upward without a trials correction
- Caveat (inferred, ours): Continuum level uncertainty, especially for SPT2132-58, may affect absorption depths and significances
- Caveat (inferred, ours): Secondary-calibrator test assumes similar elevation and atmosphere to the target, which is not quantified
- Caveat (inferred, ours): No simulations or injection tests are used to validate the channel-map evidence

## Reproducibility

- Data public (paper): Data obtained from the public ALMA archive; project codes 2016.1.01499.S and 2018.1.00191.S  
  > "from the ALMA archive." (2 ARCHIVAL OBSERVATIONS AND DATA REDUCTION)
- Products in archive: Archive provides uncalibrated visibilities and calibration scripts  
  > "The ALMA Science Archive provides uncalibrated visibilities along with scripts that allow users to calibrate the visibilities using the corresponding pipeline for the ALMA cycle in which the observations were made." (2.1 Calibration)
- Missing: Imaging parameters (weighting, cell, image size, masks) and CASA version
- Missing: Line-free channel ranges and the exact integration regions
- Missing: Details of the manual re-calibrations
- Missing: ESSENCE settings and the velocity-range selection procedure
- Missing: Quantitative criteria behind the channel-map judgements
- Data volume (inferred): Ten archive datasets (OH and [CII] for five sources) with four 1.875 GHz SPWs each plus calibrators; likely tens to a few hundred GB raw
- Score (inferred): 3/5, Data are public and the analysis outline plus Table 2 numbers are given, but imaging parameters, channel selections, regions and the ESSENCE setup are missing, and channel-map conclusions are qualitative.
- Rediscovery candidate: no, Public data and numeric absorption strengths exist, but key imaging, region and line-free choices are unstated and the main channel-map claims are qualitative.

## Links

- Method: Spilker et al. 2018 (cite: spilker18) (Original Band 8 OH survey whose data and calibration/analysis are followed)
- Method: Spilker et al. 2020a (cite: spilker20a) (Companion OH survey paper whose data and calibration/analysis are followed)
- Method: (cite: tsukui23) (ESSENCE software for per-channel uncertainties of integrated spectra)
- Method: (cite: he22) (Description of ALMA atmospheric (T_atm) calibration)
- Companion: Spilker et al. 2020b (cite: spilker20b) (Derived mass outflow rates from the OH absorption depths discussed here)
- Related: Band 8 OH 119 um survey of eleven lensed DSFGs of Spilker et al. 2018 and 2020a

## Checks

```json
{
 "quotes": 104,
 "quotes_ok": 104,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 68,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
