# Resolved ALMA observations of water in the inner astronomical units of the HL Tau disk

`2024NatAs...8..587F` | Nature Astronomy 2024 | first author: Facchini, Stefano | arXiv: 2403.00647 | DOI: 10.1038/s41550-024-02207-w

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can ALMA detect and spatially resolve thermal emission from the main water isotopologue (H2O) in the inner disk of HL Tau, and what do the lines say about the water extent, excitation and column density?  
  > "With this article, we report the detection of three rotational water lines in the inner regions of the HL Tau protoplanetary disk obtained with ALMA." (Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "At a distance of 140 pc, this corresponds to $\sigma_{\rm G}=16.8\pm1.4\,$au." (The spatial distribution of water vapour); "with the lines being centered on the systemic velocity of the system (7.1 km s$^{-1}$; (cite: Garufi_ea_2021; Garufi_ea_2022))" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01178.S, 2022.1.00905.S
- bands: Band 5 and Band 7  
  > "HL Tau was observed in both Band 5 and Band 7 with the ALMA Program 2017.1.01178.S (PI: Humphreys)" (Methods)
- frequencies and spectral setup: Band 5: 6 spws, one 1.875 GHz continuum spw at 170.004 GHz; Band 7: 4 spws in FDM mode, one with 1920 244 kHz channels on the water line  
  > "The Band 5 spectral setup had 6 spectral windows (spws), five of which targeting different molecular transitions, including the 183 GHz water line, and a 1.875 GHz-wide spw for continuum observations at 170.004 GHz." (Methods); "one with 1920 244 kHz channels, targeting the water 325 GHz line" (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m-1.4 km (Band 5); 41 m-3.6 km and up to 8500 m (Band 7, 2017.1.01178.S); 15-500 m (2022.1.00905.S)  
  > "with 43 antennas and baselines ranging between 15 m and 1.4 km" (Methods); "with baselines ranging between 15 and 500 m, and a total on-source time of 100 min" (Methods)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 46 min (Band 5); 31 and 33 min (Band 7, 2017.1.01178.S); 100 min (2022.1.00905.S)  
  > "| 2022.1.00905.S | p-H$_2$O 5$_{15}$–4$_{22}$ | 100 | 0.3 | J0423-0120 | J0431+1731 | 500 |" (Table 2)
- observing dates: 21 Sep 2018 (Band 5); 12 Aug 2019 and 24 Nov 2017 (Band 7); Oct 2022  
  > "the source was observed in Band 5 on September 21, 2018" (Methods); "new data were taken in October 2022" (Methods)
- pi or archival as stated: 2017.1.01178.S PI Humphreys; 2022.1.00905.S PI Facchini  
  > "Program 2022.1.00905.S (PI: Facchini)" (Methods)
- Line: p-H2O 3_13-2_20 (183.31009 GHz)
- Line: p-H2O 5_15-4_22 (325.15290 GHz)
- Line: o-H2O 10_29-9_36 (321.22569 GHz)
- Line: p-H2(18)O 5_15-4_22 (322.46517 GHz)
- External data: Inclination 46.7 deg and PA 138.0 deg from high-resolution continuum  
  > "after fixing the inclination and position angle to $46.7\deg$ and $138.0\deg$, respectively, as derived from high angular resolution continuum observations (cite: HL_Tau_SV_2015)" (The spatial distribution of water vapour) [from (cite: HL_Tau_SV_2015)]
- External data: Dust mass and surface density, optical depths from multiwavelength continuum analysis  
  > "By using the dust surface density from this study, we obtain $M_{\rm dust}\sim13M_{\rm Earth}$" (Water column density) [from (cite: Carrasco_ea_2019)]
- External data: Partition function of water  
  > "the partition function was determined with a cubic spline interpolation across the rotational temperatures listed in (cite: Polyansky2018)" (Rotational diagram and optical depth constraints) [from (cite: Polyansky2018)]
- External data: Oxygen isotope ratio 530 from solar wind  
  > "Assuming that $\tau_{\rm{H}_{2}\rm{O}}=530\,\tau_{\rm{H}_{2}^{18}\rm{O}}$ (using the oxygen isotope ratio measured in the solar wind (cite: McKeegan11))" (Water column density) [from (cite: McKeegan11)]
- External data: Systemic velocity 7.1 km/s  
  > "systemic velocity of the system (7.1 km s$^{-1}$; (cite: Garufi_ea_2021; Garufi_ea_2022))" (Observations) [from (cite: Garufi_ea_2021; Garufi_ea_2022)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, then self-calibration  
  > "The Cycle 6 (9) data were calibrated by the ALMA pipeline using `CASA` v5.4 (v6.4)" (Methods)
- casa version: CASA v5.4 (Cycle 6), v6.4 (Cycle 9) for pipeline; CASA 6.2.1 for imaging  
  > "The Cycle 6 (9) data were calibrated by the ALMA pipeline using `CASA` v5.4 (v6.4)" (Methods); "imaged with `CASA` 6.2.1 with natural weighting" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120, J0538-4405, J0519-4546 (per execution block)  
  > "| 2017.1.01178.S | p-H$_2$O 5$_{15}$–4$_{22}$ | 31 | 0.4 | J0538-4405 | J0431+1731 | 3637 |" (Table 2)
- flux scale uncertainty: 10% absolute flux systematic uncertainty  
  > "We accounted for 10% absolute flux systematic uncertainties in the line fluxes." (Water column density)
- self calibration: Phase self-cal per EB on line-free combined spws, alignment, then phase+amplitude on short-baseline EBs, then combined with long baseline and re-self-calibrated; models by CLEAN robust=0.5; solutions applied to full spectral data  
  > "We then self-calibrated the two short-baselines (in the case of band 5, only one set of baselines is available) execution blocks in both phase and amplitude, reaching a peak snr of 9950" (Methods); "The models for self-calibration were constructed with `CLEAN` with Briggs weighting (`robust`=0.5). The gain solutions were then applied to the full spectral data." (Methods)

### Imaging

- task: CASA 6.2.1 imaging of continuum-subtracted lines  
  > "we imaged both the continuum and the continuum-subtracted lines with the CASA software" (Observations)
- deconvolver: _not stated_
- weighting robust: Lines: natural weighting; Band 5 continuum robust=0.0; Band 7 continuum robust=-1.0  
  > "All the H$_2$O lines and the H$_2^{18}$O line were imaged with `CASA` 6.2.1 with natural weighting, to maximise point source sensitivity." (Observations); "The band 7 (0.94 mm) data were imaged with `robust`=$-1.0$." (Methods)
- uv taper: Several uv-tapers tried, no new features vs natural weighting  
  > "several additional attempts with a range of uv-tapers were performed to increase the sensitivity to extended emission" (Methods)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Band 7 data from two cycles combined; 321 GHz line from a single long-baseline EB  
  > "For the band 7 data, we combined the data from the two cycles." (Methods)
- smoothing: Channel widths 0.8, 1, 5 km/s for 183, 325, 321 GHz lines  
  > "with a 5 km s$^{-1}$ channel spacing" (Observations)
- final beam: 183 GHz: 0.500x0.442" (PA -3.0); 325 GHz: 0.640x0.491" (PA -42.1); 321 GHz: 0.067x0.061" (PA 12.2); H2 18O: 0.779x0.626"  
  > "The 183 GHz line presents a synthesized beam of $0.500''\times0.442''$ (PA $-3.0$ deg), and was imaged with a channel width of $0.8\,$km s$^{-1}$." (Observations)
- final rms: Continuum: 33 uJy (Band 5), 36 uJy (Band 7); line rms in Table 1  
  > "the Band 5 (1.70 mm) continuum presents an rms of $33\,\mu$Jy, with a peak snr of 2457" (Methods)

### Inherited from earlier work

- Alignment of data by fitting a Gaussian to the continuum and shifting phase center (fixvis, fixplanet)  
  > "Following (cite: Andrews_ea_2018), we then aligned the data by fitting a Gaussian to the continuum" (Methods) [from (cite: Andrews_ea_2018)]
- Keplerian disk spectrum model  
  > "we fitted its spectrum by analytically computing model spectra of a geometrically thin Keplerian disk, similarly to (cite: Zagaria2023)" (Methods) [from (cite: Zagaria2023)]
- Rotational diagram approach  
  > "we use the same approach as in e.g., (cite: Loomis18; Facchini21)" (Methods) [from (cite: Loomis18; Facchini21)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum subtraction and self-calibration
- Self-calibration solution intervals other than 'scan-length' for amplitude, and number of iterations
- Image size, cell size, masks and clean threshold for line cubes
- Continuum subtraction method
- Which execution blocks go into each line cube and how line cubes were weighted/combined
- Primary beam correction details
- Uvrange/weights for galario fit and how visibilities were averaged
- Fixed parameters in rotational diagram beyond Table 3 (partition function values for higher-energy lines)
- Spectrum extraction center position

## Analysis recipe

1. **Calibrate and self-calibrate**: ALMA pipeline, then phase and amplitude self-calibration, alignment, and combination of EBs; gains applied to line data  
  > "For both bands, we first self-calibrated each of the three execution blocks in phase, combining all spectral windows after flagging spectral ranges associated to line emission" (Methods)
   - software: CASA
   - parameter: self-cal model CLEAN robust=0.5  
  > "The models for self-calibration were constructed with `CLEAN` with Briggs weighting (`robust`=0.5)." (Methods)
   - fitting: _not stated_
   - validation: Peak SNR improvements 9950 (Band 5) and 5300 (Band 7)  
  > "reaching a peak snr of 5300 (a $210\%$ improvement)" (Methods)
2. **Image continuum and lines, extract spectra and fluxes**: Natural-weighted line cubes; spectra over 0.7" radius (0.06" for 321 GHz); moment 0 and 1 maps; fluxes in circular apertures with bootstrapped uncertainties  
  > "The uncertainties on the line fluxes were computed by bootstrapping over 100 circular apertures in emission free regions of the map" (Methods)
   - software: CASA, bettermoments
   - parameter: Moment 0 integration ranges -2 to 16, -6.4 to 20.6, -10.4 to 24.6 km/s for 183, 325, 321 GHz lines  
  > "between $-6.4$ and $20.6\,$km s$^{-1}$ for the 325 GHz line, and between $-10.4$ and $24.6\,$km s$^{-1}$ for the 321 GHz line" (Methods)
   - parameter: Moment 1 clipping 4 sigma (183 GHz) and 3 sigma (325 GHz)  
  > "after applying $4$ and $3$ $\sigma$ clipping to individual channels, respectively" (Methods)
   - assumption: 325 GHz flux corrected for red-shifted absorption by doubling the blue-shifted side  
  > "we also computed the underlying flux by considering the blue-shifted side only, and multiplying it by a factor of two" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit 183 GHz integrated intensity profile in the visibility plane**: Gaussian radial profile Fourier-transformed and fitted to visibilities  
  > "we fitted the visibility data by Fourier transforming a projected integrated intensity profile in the same $uv$-points sampled during the observations" (Methods)
   - software: galario, emcee
   - parameter: Free: J0, sigma_G, delta RA, delta Dec; inclination 46.7 deg and PA 138.0 deg fixed  
  > "where we considered four free parameters: $J_0$, $\sigma_{\rm G}$, and the disk center ($\Delta$RA and $\Delta$Dec)" (Methods)
   - assumption: Distance 140 pc  
  > "At a distance of 140 pc, this corresponds to $\sigma_{\rm G}=16.8\pm1.4\,$au." (The spatial distribution of water vapour)
   - fitting: emcee; 50 walkers, 1000 burn-in + 1000 steps; flat priors log10(J0/sr) in [1,20], sigma_G in [0,1.5]", dRA, dDec in [-0.4,0.4]"  
  > "The posterior distribution was sampled with 50 walkers and 1000 steps, after 1000 steps of burn-in." (Methods)
   - validation: MCMC convergence shown in Extended Data figure  
  > "The MCMC exploration of the posterior space well converges, as shown in Extended Data Figure 7." (Methods)
4. **Radial profile of 321 GHz line**: De-project and azimuthally average the moment zero map  
  > "by azimuthally averaging the moment zero map, after de-projecting it by the known inclination (using the `GoFish` package (cite: gofish))" (The spatial distribution of water vapour)
   - software: GoFish
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit 183 GHz spectrum with Keplerian disk with brightness temperature gradient**: Thin Keplerian disk model, T(R)=T0 (R/10au)^-q, optically thick limit, convolved to channel width  
  > "We kept three free parameters in the fitting procedure: $T_0$, $q$ and $R_{\rm out}$." (Methods)
   - software: emcee
   - parameter: R_in = 0.1 au; 150 radial and 550 azimuthal points  
  > "We fixed $R_{\rm in}$ to $0.1\,$ au (but the model is not sensitive to this value for reasonably small radii), and sampled the disk with 150 points in radius, and 550 in azimuth." (Methods)
   - assumption: Stellar mass fixed to 1 Msun in the equation, i=46.7 deg, d=140 pc  
  > "$d$ is the distance of HL Tau (140 pc)" (Methods)
   - fitting: emcee, 30 walkers, 1000 burn-in + 1000 steps; flat priors T0 [10,1500] K, q [0,3], Rout [2,200] au  
  > "using flat priors on the three free parameters: $[10,1500]$ K, $[0,3]$, $[2,200]$ au, respectively." (Methods)
   - validation: Best fit and 100 posterior draws shown; Rout unconstrained  
  > "While the fit does not manage to constrain the outer radius of the emission" (Methods)
6. **Rotational diagram: excitation temperature and column density**: Linear regression in ln(Nu/gu) vs Eu assuming optically thin emission, uniform Trot, 3:1 ortho-to-para ratio  
  > "In the rotational diagram, we used degeneracy quantum numbers that account for a 3:1 ortho-to-para ratio" (Water column density)
   - software: emcee
   - parameter: 128 walkers, 2000 steps after 1000 burn-in  
  > "we used 128 walkers, and 2000 steps (after 1000 steps of burn-in)" (Methods)
   - assumption: Optically thin, LTE, 10% flux systematics  
  > "under the assumption of optically thin emission and uniform excitation temperature across the energy range" (Water column density)
   - fitting: emcee linear regression; partition function by cubic spline of Polyansky2018 values  
  > "We performed a linear regression using the `emcee` sampler (cite: Foreman-Mackey+13)" (Methods)
   - validation: Separate fits to the two lower and two higher energy lines  
  > "Fitting either the two lower energy lines or the two higher energy lines separately" (Water column density)
7. **Optical depth upper limit and water-to-dust ratio**: Use H2 18O non-detection (3 sigma) with tau ratio 530 to solve flux ratio equation; compare water mass to dust mass from literature  
  > "a numerical solution of the equations leads to $\tau_{\rm{H}_{2}\rm{O}}<14$, as reported in the main text." (Methods)
   - assumption: H2O/H2 18O optical depth ratio 530  
  > "is equal to $530\times\tau_{\rm{H}_{2}^{18}\rm{O}}$ (cite: McKeegan11)" (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4, 6.4 (pipeline); 6.2.1 (imaging): calibration, self-calibration, imaging  
  > "All the H$_2$O lines and the H$_2^{18}$O line were imaged with `CASA` 6.2.1 with natural weighting" (Observations)
- **galario** : visibility-plane fit of the 183 GHz integrated intensity  
  > "We then fitted the line integrated intensity visibilities with a simple Gaussian model using the `galario` package" (The spatial distribution of water vapour)
- **GoFish** : radial profile of 321 GHz moment 0 map  
  > "using the `GoFish` package (cite: gofish)" (The spatial distribution of water vapour)
- **bettermoments** : moment one maps  
  > "intensity weighted velocity maps were generated using the `bettermoments` package (cite: bettermoments)" (Methods)
- **emcee** : MCMC fits of spectrum, visibilities and rotational diagram  
  > "We fitted the spectrum shown in Figure 2 with the `emcee` package" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 183 GHz Gaussian sigma_G | 0.12 | 0.01 | arcsec | 3 | The fit converges well to a Gaussian with $\sigma_{\rm G}=0.12\pm0.01''$ |
| 183 GHz sigma_G in au | 16.8 | 1.4 | au | 3 | $\sigma_{\rm G}=16.8\pm1.4\,$au |
| Upper limit on water snowline radius | 17 | not stated | au | 3 | These findings set a stringent upper limit on the radius of the water snowline at 17 au. |
| Line flux 183 GHz | 973 | 89 | mJy km/s | 2 | / p-H$_2$O 3$_{13}$–2$_{20}$ / 183.31009 / 204.7 / 0.8 / 6.90 / $973\pm89$ / 0.70 / |
| Line flux 325 GHz (absorption-corrected) | 1332 | 89 | mJy km/s | 2 | The resulting flux is $1332\pm89$ mJy km s$^{-1}$. |
| Line flux 321 GHz | 679 | 135 | mJy km/s | 2 | The resulting flux is $679\pm135\,$mJy km s$^{-1}$. |
| H2 18O 3-sigma flux upper limit | <33.6 | not stated | mJy km/s | 2 | $<33.6^d$ |
| Peak SNR of 183 GHz spectrum | ~9.6 (rms 13.2 mJy) | not stated | dimensionless | 2 | The 183 GHz line spectrum exhibits a peak signal-to-noise ratio (snr) of $\sim9.6$, with an rms of $13.2\,$mJy |
| Brightness temperature T0 | 287 | +180/-154 | K | 5 | we obtain $T_0=287_{-154}^{+180}$, and $q=0.92^{+0.30}_{-0.47}$ |
| Brightness temperature power-law index q | 0.92 | +0.30/-0.47 | dimensionless | 5 | we obtain $T_0=287_{-154}^{+180}$, and $q=0.92^{+0.30}_{-0.47}$ |
| Excitation temperature, two lower-energy lines | 214 | +42/-29 | K | 6 | excitation temperatures of $214_{-29}^{+42}$ and $789_{-110}^{+127}$ K, respectively |
| Excitation temperature, two higher-energy lines | 789 | +127/-110 | K | 6 | excitation temperatures of $214_{-29}^{+42}$ and $789_{-110}^{+127}$ K, respectively |
| Total water column density within 0.7" (log10 N_thin) | 16.41 | +0.06/-0.09 | log10 cm^-2 | 6 | $\log_{10}{(N_{\rm thin}/{\rm cm}^2)} = 16.41^{+0.06}_{-0.09}$ within $0.7''$ |
| Average column density within 17 au (log10) | ~18.10 | +0.06/-0.09 | log10 cm^-2 | 6 | $\log_{10}{(N_{\rm thin}/{\rm cm}^2)} \sim18.10^{+0.06}_{-0.09}$ |
| Water vapour mass | ~3.7 Earth oceans (7.1e-2 lunar masses) | not stated | Earth oceans | 6 | This corresponds to $\sim3.7$ Earth oceans ($7.1\times10^{-2}$ lunar masses) of water vapour. |
| Optical depth upper limit of 325 GHz H2O line | <14 | not stated | dimensionless | 7 | we obtain that $\tau_{\rm{H}_{2}\rm{O}}<14$ |
| N(H2O)/N(H2 18O) upper limit | 40 | not stated | dimensionless | 7 | provides an upper limit of $N$(H$_{2}$O)/$N$(H$_{2}^{18}$O)$=40$ in HL Tau |
| Water-to-dust mass ratio | ~6e-5 | not stated | dimensionless | 7 | water-to-dust mass ratio of $M_{{\rm H}_2{\rm O}}/M_{\rm dust}\sim6\times10^{-5}$ |
| Continuum flux density at 0.94 mm | 1677.7 | 0.6 | mJy | 2 | we obtain a flux density of $323.0\pm1.4\,$mJy and $1677.7\pm0.6\,$mJy at 1.70 and 0.94 mm, respectively |

## Qualitative findings

- Water emission is centrally peaked and confined within a prominent continuum gap; the lower-excitation line is more extended, implying radially decreasing excitation temperature.  
  > "The lower excitation line is significantly more extended, showing that the water emission has a radially decreasing temperature (excitation)" (The spatial distribution of water vapour)
- The lines trace warm gas in disk upper layers above optically thick dust.  
  > "jointly indicate that the (sub-)mm lines are probing warm gas in the disk upper layers above the water snow surface" (Conclusions)

## Claim tuples

- H: Can ALMA detect thermal H2O emission from a quiescent protoplanetary disk? | E: Band 5 and 7 observations of three H2O lines in HL Tau | R: Peak SNR in moment 0 maps of 21.4, 19.8 and 8.1 for 183, 325 and 321 GHz | F: Three rotational H2O lines detected and spatially resolved in the inner HL Tau disk | **supported**
- H: Where does the water emission originate and what limits the snowline? | E: visibility Gaussian fit of the 183 GHz line and radial profile of the 321 GHz line | R: sigma_G = 0.12" (16.8 au); 321 GHz emission out to 0.3" | F: Emission confined within ~17 au, an upper limit on snowline radius | **supported**
- H: Is the water emission optically thin and tracing the full water reservoir? | E: H2 18O non-detection and water-to-dust ratio | R: tau(H2O)<14; water-to-dust ~6e-5 vs ~1e-2 expected | F: ALMA probes marginally optically thick gas above opaque dust, so column is a lower limit | **supported**
- H: Does the water excitation show a temperature gradient? | E: Rotational diagram and Keplerian spectrum fit | R: Two Trot solutions of 214 and 789 K; q=0.92 | F: Continuous gradient in excitation temperature | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting used to maximise point source sensitivity.  
  > "with natural weighting, to maximise point source sensitivity" (Observations)
- Alternative: Several uv-tapers tried but showed no feature undetected with natural weighting.  
  > "but they did not show any feature undetected with natural weighting" (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Column density is a lower limit given the optically thin assumption.  
  > "Given the optically thin assumption, this has to be considered as a tight lower limit." (Water column density)
- Limitation (authors): Accurate snowline determination needs thermo-chemical forward modelling.  
  > "A more accurate determination will require simultaneous forward-modelling of the radial and spectral profiles of all three (sub-)mm lines with the aid of thermo-chemical codes." (The spatial distribution of water vapour)
- Caveat (inferred, ours): Rotational diagram with LTE, uniform Trot and optical thin assumptions is inconsistent with the stated partial thickness
- Caveat (inferred, ours): Masing not strictly excluded
- Caveat (inferred, ours): Doubling blue side to correct absorption in 325 GHz line is ad hoc
- Caveat (inferred, ours): 321 GHz detection is marginal (SNR ~4 in spectrum)
- Caveat (inferred, ours): Stellar mass in the Keplerian model is fixed to 1 Msun while cited mass is 2.1 Msun

## Reproducibility

- Data public (paper): All ALMA data publicly available in the ALMA archive  
  > "All the ALMA data are publicly available on the ALMA archive (https://almascience.nrao.edu/aq/), with program IDs #2017.1.01178.S and #2022.1.00905.S." (Data availability)
- Products in archive: _not stated_
- Code: Calibration and fitting scripts available only on request from the first author  
  > "The calibration and fitting scripts can be obtained by SF upon reasonable requests." (Code availability)
- Missing: Self-calibration scripts and solution intervals
- Missing: Line-free channels and continuum subtraction details
- Missing: Imaging parameters (size, cell, masks, thresholds)
- Missing: Partition function values at all needed temperatures
- Data volume (inferred): ~100-300 GB raw across 5-6 execution blocks in Bands 5 and 7
- Score (inferred): 3/5, Public data and well-described fitting, but self-calibration and imaging details are missing and scripts are only available on request.
- Rediscovery candidate: no, Data are public and results numeric, but self-calibration and imaging recipe are incomplete.

## Links

- Method: (cite: Andrews_ea_2018) (alignment of execution blocks)
- Method: (cite: Zagaria2023) (Keplerian spectrum model)
- Method: (cite: galario) (visibility fitting)
- Companion: (cite: Garufi_ea_2022) (other lines in the same Band 5/7 dataset)
- Companion: (cite: Carrasco_ea_2019) (dust mass and optical depth of HL Tau)
- Related: ALMA HL Tau Science Verification

## Checks

```json
{
 "quotes": 103,
 "quotes_ok": 103,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 66,
  "rate": 0.702
 },
 "evidence_ok": true
}
```
