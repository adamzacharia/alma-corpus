# Extremely Low Molecular Gas Content in a Compact, Quiescent Galaxy at z = 1.522

`2019ApJ...873L..19B` | The Astrophysical Journal Letters 2019 | first author: Bezanson, Rachel | arXiv: 1902.09564 | DOI: 10.3847/2041-8213/ab0c9c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How much molecular gas remains in a massive, recently quenched (post-starburst) galaxy at z=1.522, and how do gas fractions vary with stellar surface density across high-z galaxies?  
  > "we quantify the molecular gas reservoir in C21434, a massive and recently quenched galaxy at $z=1.52$" (Introduction)
- Target **C21434**: coordinates _not stated_; z/distance z = 1.522  
  > "fixing to the spectroscopic redshift $z_{spec}=1.522$" (2.1 Multi-Wavelength Photometry and LRIS Spectrum); distance from spectroscopic redshift (LRIS spectrum)  
  > "fixing to the spectroscopic redshift $z_{spec}=1.522$" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)

## Data provenance

- ALMA projects: 2015.1.00853.S
- bands: Band 3  
  > "ALMA Band 3 observations were carried out in two consecutive observing blocks on 2016 January 18" (2.2 ALMA Observations)
- frequencies and spectral setup: CO(2-1) at 91.411 GHz sky frequency; one 1.875 GHz SPW with 7.8 MHz (~25 km/s) channels; two additional 1.875 GHz continuum SPWs  
  > "One 1.875 GHz spectral window was centered around this frequency with 7.8 MHz ($\sim$25 $\rm{km\,s}^{-1}$) channelization" (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: max 330 m, 40 antennas  
  > "A total of 40 antennas were active in the array, reaching maximum baselines of 330 m" (2.2 ALMA Observations)
- angular resolution: ~2"  
  > "yielding a resolution of $\sim$2$''$" (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 9 uJy/beam continuum at 98 GHz; 105 uJy/beam per 100 km/s channel  
  > "continuum sensitivity of 9 $\mu\rm{Jy}$/beam at 98 GHz, and a CO(2–1) line sensitivity of 105 $\mu\rm{Jy}$/beam per 100 $\rm{km\,s}^{-1}$ channel" (2.2 ALMA Observations)
- time on source: 109 min on source (160 min total)  
  > "The total duration of the two blocks was 160 min, with 109 min on source." (2.2 ALMA Observations)
- observing dates: 2016 January 18  
  > "ALMA Band 3 observations were carried out in two consecutive observing blocks on 2016 January 18" (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **NMBS (NEWFIRM Medium Band Survey)**: UV to 24 micron photometry for SED fitting  
  > "The NMBS survey provides extensive multi-wavelength photometry for this object from the UV to 24 $\mu\rm{m}$" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)
- Other facility **Keck LRIS**: deep 18 hour optical spectrum  
  > "A deep (18 hour) optical spectrum was taken in January and April 2010 using the LRIS spectrograph" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)
- Other facility **HST WFC3 F160W**: rest-frame optical imaging for structural parameters  
  > "high-resolution rest-frame optical imaging was obtained using the $F160W$ filter on the HST-WFC3 Camera" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)
- External data: Literature samples of high-z galaxies with molecular gas, SFRs, sizes (PHIBSS, PHIBSS2, Daddi+10, Decarli+16, Spilker+16, Sargent+15, Hayashi+18, Rudnick+17, Gobat+18, Suess+17, Spilker+18)  
  > "we compile a literature sample of high-redshift galaxies with measured molecular gas reservoirs, star formation rates, and stellar sizes measured from rest-frame optical HST imaging." (2.4 Ancillary Datasets) [from (cite: tacconi:18; daddi:10; decarli:16; spilker:16; sargent:15)]
- External data: COLDGASS low-redshift CO(1-0) benchmark  
  > "Finally we include CO(1-0)-based data from the COLDGASS survey" (2.4 Ancillary Datasets) [from (cite: saintonge:11; saintonge:11b; saintonge:12)]
- External data: 3D-HST catalogs, UV+IR SFRs and HST structural parameters for 1<z<2 comparison  
  > "we include galaxies from the 3D-HST photometric catalogs" (2.4 Ancillary Datasets) [from (cite: brammer:11; skelton3dhst; whitaker:14; wel:12)]
- External data: Stellar velocity dispersion line width FWHM ~600 km/s  
  > "which have FWHM $\sim$ 600 $\rm{km\,s}^{-1}$(cite: bezanson:13a)" (2.3 Non-Detection and H2 Gas Mass Limit) [from (cite: bezanson:13a)]

## Processing

### Calibration

- pipeline or manual: standard ALMA Cycle 3 pipeline  
  > "The data were reduced using the standard ALMA Cycle 3 pipeline, and no significant issues with this reduction were found." (2.2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (block 1), Ganymede (block 2); bandpass J1058+0133; gain J0949+0022  
  > "J1058+0133 was also used to calibrate the absolute flux scale in the first observing block, while Ganymede served this purpose in the second block." (2.2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
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

- Sample selection and full analysis (stellar line width, structure) from earlier paper  
  > "The sample and full analysis is described in (cite: bezanson:13a), but we briefly summarize here." (2.1 Multi-Wavelength Photometry and LRIS Spectrum) [from (cite: bezanson:13a)]
- Thermalized CO excitation and alpha_CO motivated by local early-type galaxies  
  > "we assume thermalized line emission, as observed in local early type galaxies from the ATLAS$^{\mathrm{3D}}$ survey (cite: young:11)" (2.3 Non-Detection and H2 Gas Mass Limit) [from (cite: young:11)]

### Not stated but needed to reproduce (our reading)

- Imaging/weighting details (visibility fitting uses 8-channel bins but no imaging parameters)
- Exact optical/NIR position used to fix the point source
- Velocity center and exact integration window for the upper limit
- Conversion details from L'CO to the limit (r21 value and formula)
- CASA version used
- Stellar surface density and SFR values for literature galaxies

## Analysis recipe

1. **Fit stellar properties and structure**: FAST SED fit of NMBS photometry with delayed exponentially declining SFHs; Galfit single Sérsic fit to HST F160W; PPXF spectral age fit  
  > "The NMBS photometry are fit using FAST (cite: kriek:09) with (cite: bc:03) stellar population synthesis models and delayed exponentially declining star formation histories" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)
   - software: FAST, Galfit, PPXF
   - parameter: redshift fixed at z_spec=1.522  
  > "fixing to the spectroscopic redshift $z_{spec}=1.522$" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)
   - assumption: Chabrier IMF; H0=70, Om=0.3, OL=0.7  
  > "We assume a standard concordance cosmology with $\mathrm{H_0=70 km\,s^{-1}Mpc^{-1}}$, $\Omega_M=0.3$, $\Omega_{\Lambda}=0.7$" (Introduction)
   - fitting: _not stated_
   - validation: Age from photometry and spectrum agree at ~0.8 Gyr  
  > "again finding a stellar age of $\sim$0.8 Gyr" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)
2. **Extract spectrum via visibility point-source fit**: Fit point source to visibilities in 8-channel bins (~200 km/s), position fixed to optical/NIR position, flux free  
  > "we fit a point source to the visibilities in bins of 8 channels, or $\sim$200 $\rm{km\,s}^{-1}$." (2.3 Non-Detection and H2 Gas Mass Limit)
   - parameter: position fixed; only flux density free  
  > "leaving only the flux density at each velocity channel as a free parameter" (2.3 Non-Detection and H2 Gas Mass Limit)
   - assumption: Source unresolved since Re=0.23" << 2" beam  
  > "so this unresolved source is expected to be pointlike" (2.3 Non-Detection and H2 Gas Mass Limit)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive CO luminosity and H2 mass upper limits**: 3 sigma limit on integrated CO(2-1) flux with line width 600 km/s; thermalized excitation; alpha_CO=4.4  
  > "we assume that the gas spatial and kinematic distribution traces the stellar continuum and therefore adopt a CO line width equal to the line width determined from the stellar absorption features" (2.3 Non-Detection and H2 Gas Mass Limit)
   - parameter: alpha_CO = 4.4 Msun/(K km/s pc^2)  
  > "We adopt a Milky Way-like CO-H$_2$ conversion factor, $\ensuremath{\alpha_{\rm{CO}}}=4.4$" (2.3 Non-Detection and H2 Gas Mass Limit)
   - assumption: CO(2-1)/CO(1-0) thermalized, accurate to <30%  
  > "our estimate of thermalized excitation should be accurate to $<$30%" (2.3 Non-Detection and H2 Gas Mass Limit)
   - fitting: _not stated_
   - validation: Continuum-based dust mass limit as cross-check (much weaker)  
  > "which is significantly less constraining than the CO(2-1) line flux" (2.3 Non-Detection and H2 Gas Mass Limit)
4. **Dust continuum gas limit**: 3 mm continuum limit converted to gas mass with Dunne+11 emissivity, Td=25 K, M_H2/M_dust=100  
  > "Based on dust emissivity from (cite: dunne:11) with a dust temperature of 25K and $M_{H_2}/M_{dust}$ = 100" (2.3 Non-Detection and H2 Gas Mass Limit)
   - assumption: Td = 25 K; gas-to-dust 100  
  > "dust temperature of 25K and $M_{H_2}/M_{dust}$ = 100" (2.3 Non-Detection and H2 Gas Mass Limit)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with literature gas fractions vs sSFR, size, surface density**: Compile literature samples, compute fH2, sSFR and Sigma_star = Mstar/(2 pi Re^2), compare with 3D-HST relations  
  > "($\Sigma_{\star}\equiv\,\ensuremath{M_{\rm{\star}}}/(2\pi R_e^2)$)" (3 H2 reservoirs across the galaxy population)
   - assumption: Milky Way alpha_CO applied to literature (conservative)  
  > "therefore posit that adopting a Milky Way $\alpha_{\rm{CO}}$ is a conservative assumption" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Galfit** : Sérsic fit to HST image  
  > "The structural parameters of C21434 are measured using *Galfit* (cite: galfit) to fit a single (cite: sersic) profile to the HST image." (2.1 Multi-Wavelength Photometry and LRIS Spectrum)
- **FAST** : SED fitting for stellar mass and age  
  > "The NMBS photometry are fit using FAST (cite: kriek:09)" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)
- **PPXF** : spectroscopic stellar age fit  
  > "using PPXF (cite: cappellari:04) to fit a linear, non-negative sum of (cite: vazdekis:99) single stellar population models" (2.1 Multi-Wavelength Photometry and LRIS Spectrum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass | 11.2 | not stated | log Msun | 1 | The best-fitting model finds a stellar mass of $\log \ensuremath{M_{\rm{\star}}}/\ensuremath{\rm{M}_\odot}= 11.2$. |
| Stellar age | ~0.8 | not stated | Gyr | 1 | The photometric fit yields a stellar age of $\sim$0.8 Gyr. |
| 3sigma upper limit L'CO(2-1) | <2.4e9 | not stated | K km/s pc^2 | 3 | This yields a 3$\sigma$ upper limit to the CO(2–1) luminosity of $\ensuremath{\rm{L}_{\rm{CO}}'}< 2.4 \times 10^{9}$ K $\rm{km\,s}^{-1}$ pc$^2$. |
| 3sigma upper limit M_H2 (CO) | <1.1e10 | not stated | Msun | 3 | final 3$\sigma$ upper limit on the molecular gas mass of C21434 of $\ensuremath{M_{\rm{H_2}}}< 1.1\times10^{10}$ $\rm{M}_\odot$ |
| Gas fraction upper limit | <7% | not stated | percent | 3 | The implied gas fraction is $\ensuremath{f_{\rm{H_2}}}{\equiv M_{H_2}/M_{\star}}<7\%$ |
| 3 mm continuum gas mass limit | <4.5e10 | not stated | Msun | 4 | the 3-$\sigma$ gas mass limit from the 3 mm continuum is $M_{H_2}<4.5\times10^{10} M_{\odot}$ |
| alpha_CO limit from continuum | <19 | not stated | Msun/(K km/s pc^2) | 4 | This places a very weak limit on $\alpha_{CO} < 19$ |

## Qualitative findings

- Galaxies with high stellar surface density have low gas fractions at each epoch, separating cleanly from extended galaxies in fH2.  
  > "they separate relatively cleanly in gas fraction (Figure [5](#fig:sigmastar)b)" (3 H2 reservoirs across the galaxy population)

## Claim tuples

- H: Is molecular gas substantially retained in a recently quenched z>1 massive galaxy? | E: ALMA Band 3 CO(2-1) observation of C21434 with visibility-plane point-source spectrum extraction | R: No CO(2-1) detection; M_H2<1.1e10 Msun, fH2<7% | F: Gas depletion in quenched galaxies can be efficient and nearly complete | **supported**
- H: Does gas fraction correlate with stellar surface density across high-z galaxies? | E: Compile literature galaxies and compare fH2 versus Sigma_star | R: High-Sigma_star galaxies have lower fH2 at each epoch | F: Gas fraction is correlated with stellar surface density; causality unclear | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Milky Way alpha_CO adopted as conservative and motivated by local quiescent galaxies  
  > "Aside from being a conservative choice, this value is motivated by observations of local quiescent galaxies (cite: young:11)" (2.3 Non-Detection and H2 Gas Mass Limit)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO is a systematic uncertainty  
  > "however this assumption will always introduce a source of systematic uncertainty" (2.3 Non-Detection and H2 Gas Mass Limit)
- Limitation (authors): Sparse sampling of dense high-z galaxies limits interpretation to speculation  
  > "given the sparse sampling of very dense galaxies at high redshift we are limited to speculation" (Discussion)
- Caveat (inferred, ours): Single non-detected object; upper limit depends on assumed 600 km/s line width and alpha_CO
- Caveat (inferred, ours): Heterogeneous literature sample with different methods, IMFs, alpha_CO corrections
- Caveat (inferred, ours): Surface density correlation is qualitative with no statistical test

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00853.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact upper-limit calculation details and r21
- Missing: Position of source
- Missing: Literature tables compiled values
- Missing: Imaging parameters
- Data volume (inferred): ~10-20 GB raw for a short Band 3 track
- Score (inferred): 3/5, Simple data and clear final numbers, but visibility fitting details and literature compilation are underspecified.
- Rediscovery candidate: yes, Short single-project dataset; main result is a numeric upper limit that can be recomputed from the visibilities.

## Links

- Method: (cite: bezanson:13a) (sample selection, stellar line width and analysis)
- Companion: (cite: suess:17) (gas-rich post-starburst galaxies comparison)
- Companion: (cite: spilker:18) (quiescent galaxy CO sample at z~0.8)
- Related: NMBS
- Related: 3D-HST
- Related: PHIBSS
- Related: PHIBSS2
- Related: COLDGASS

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 44,
  "rate": 0.543
 },
 "evidence_ok": true
}
```
