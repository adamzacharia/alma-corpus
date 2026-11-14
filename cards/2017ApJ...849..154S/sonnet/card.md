# ALMA Pinpoints a Strong Overdensity of U/LIRGs in the Massive Cluster XCS J2215 at z = 1.46

`2017ApJ...849..154S` | The Astrophysical Journal 2017 | first author: Stach, Stuart M. | arXiv: 1705.03479 | DOI: 10.3847/1538-4357/aa93f6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Are the submillimetre sources in the core of the z=1.46 cluster XCS J2215 cluster members, and what are their SFRs, gas content and dynamical masses, and are they affected by environment?  
  > "We then use our sensitive new observations to constrain the dust-obscured star formation activity and cold molecular gas within this cluster." (abstract)
- Target **XCS J2215.9-1738**: coordinates _not stated_; z/distance z = 1.46  
  > "which gives an angular scale of 8.5 kpc arcsec$^{-1}$ at $z =$ 1.46" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00575.S, 2013.1.01213.S
- bands: Band 6 (1.25 mm, six-pointing mosaic) and Band 3 (single pointing)  
  > "we also obtained a single pointing in Band 3 centered on the cluster to cover $^{12}$CO(2–1) emission from gas-rich cluster members." (2.3 ALMA Band 3 Observations)
- frequencies and spectral setup: Band 6: line SPWs 232.7–236.4 GHz, continuum SPWs at 248.9 and 251.4 GHz; Band 3: SPWs at 93.246 and 95.121 GHz  
  > "A further two SPWs were centred at 248.9 and 251.4 GHz, where no visible emission lines are expected, for continuum imaging." (2.2 ALMA Band 6 Observations); "Two spectral windows were used centred at observed frequencies 93.246 GHz and 95.121 GHz" (2.3 ALMA Band 3 Observations)
- continuum bandwidth: _not stated_
- arrays: Band 6: forty-two 12 m antennae; Band 3: thirty-nine 12 m antennae  
  > "The observations were conducted with forty-two 12 m antennae" (2.2 ALMA Band 6 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 6 beam ~0.66" x 0.47" (PA ~78 deg)  
  > "synthesised beam in Band 6 for the six pointings of $\sim$ 0$\ensuremath{''}$66$\times$ 0$\ensuremath{''}$47 (PA $\sim$ 78 deg.)" (2.2 ALMA Band 6 Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 6 rms 48 uJy/beam at deepest point; Band 3 channel noise 0.3-0.8 mJy/beam at 50 km/s  
  > "rms $\sigma_{\rm 1.25mm} =$ 48 $\mu$Jy beam$^{-1}$ at its deepest point" (2.2 ALMA Band 6 Observations); "a noise level in each channel of 0.3–0.8 mJy beam$^{-1}$" (2.3 ALMA Band 3 Observations)
- time on source: Band 6: 244 s per pointing; Band 3: 37.5 minutes  
  > "with an on-source integration time of 244 s for each pointing" (2.2 ALMA Band 6 Observations); "on-science target integration time of 37.5 minutes" (2.3 ALMA Band 3 Observations)
- observing dates: Band 6: 2016 June 19; Band 3: 2015 August 7  
  > "These observations were carried out on 2015 August 7" (2.3 ALMA Band 3 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 12CO J=5-4 (not stated)
- Other facility **VLT/MUSE-GALACSI**: [OII] redshifts for the millimetre sources  
  > "We fit the \[Oii\] emission doublet and derive redshifts that agree with the CO (within their 1 $\sigma$ error) in all cases." (2.5 MUSE AO Observations)
- Other facility **SCUBA-2 and Herschel PACS**: 450/850 um and 100/160 um photometry for SED fitting  
  > "fluxes from the lower resolution single-dish observations from SCUBA-2 at 450 and 850 $\mu$m (cite: ma2015dusty) and archival *Herschel* PACS data at 100 and 160 $\mu$m" (3.1 SED Fitting)
- Other facility **Spitzer IRAC**: 3.6 um magnitudes for stellar masses  
  > "we exploit the archival IRAC imaging of XCS J2215 to measure IRAC 3.6 $\mu$m magnitudes for our sources" (3.2 CO Line Properties)
- External data: Spectroscopic and photometric redshift catalogues of cluster members (H10, H09)  
  > "the 25 spectroscopic members from H10, the 46 sources from H09 with photometric redshifts indicating possible cluster membership" (2.4 Source Detection) [from (cite: hilton2010xmm; hilton2009xmm)]
- External data: Archival CO(2-1) detections for five further sources  
  > "we match the remaining fainter continuum sources to the (cite: hayashi2017evolutionary) $^{12}$CO(2–1) catalog, finding five further matches: IDs 1, 5, 10, 13, 14." (3 Analysis and Results) [from (cite: hayashi2017evolutionary)]
- External data: Median rest-frame H-band mass-to-light ratio of ECDFS SMGs  
  > "apply their median rest-frame $H$-band mass-to-light ratio to our sample" (3.2 CO Line Properties) [from (cite: da2015alma)]

## Processing

### Calibration

- pipeline or manual: Calibration and imaging in CASA  
  > "Calibration and imaging was carried out with the COMMON ASTRONOMY SOFTWARE APPLICATION (CASA v4.6.0 (cite: mcmullin2007casa))." (2.2 ALMA Band 6 Observations)
- casa version: CASA v4.6.0  
  > "CASA v4.6.0 (cite: mcmullin2007casa)" (2.2 ALMA Band 6 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 6: Titan; Band 3: Ceres  
  > "the flux calibrator used was Titan" (2.2 ALMA Band 6 Observations); "Ceres as the flux calibrations" (2.3 ALMA Band 3 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN, multi-frequency synthesis  
  > "The resulting continuum maps were created with the CLEAN algorithm using multi-frequency synthesis mode with a natural weighting to maximise sensitivity." (2.2 ALMA Band 6 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with a natural weighting to maximise sensitivity" (2.2 ALMA Band 6 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: clean to 3 sigma, then boxes on >4 sigma sources cleaned to 1.5 sigma  
  > "masking boxes are placed on sources $>$ 4$\sigma$ and the sources cleaned to 1.5$\sigma$" (2.2 ALMA Band 6 Observations)
- multiscale scales: _not stated_
- continuum subtraction: UVCONSTSUB in CASA for CO(5-4)  
  > "we subtracted the continuum emission in the $uv$ data using the UVCONSTSUB task in CASA" (2.4 Source Detection)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel maps at 50 km/s  
  > "created continuum-subtracted channel maps at a velocity resolution of 50 km s$^{-1}$ with an rms of 0.3–0.4 mJy beam$^{-1}$" (2.4 Source Detection)
- final beam: _not stated_
- final rms: 48 uJy/beam deepest (Band 6 continuum)  
  > "rms $\sigma_{\rm 1.25mm} =$ 48 $\mu$Jy beam$^{-1}$ at its deepest point" (2.2 ALMA Band 6 Observations)

### Inherited from earlier work

- alpha_CO=1, R=7 kpc, r21/10=0.84 and disk dynamical mass with average inclination  
  > "we adopted the same values for the constants $\alpha_{\rm CO}=1$, radius of galaxy $R_{kpc} =
  7$ kpc" (3.2 CO Line Properties) [from (cite: bothwell2013survey)]
- SCUBA-2/Herschel deblending method with ALMA positional priors  
  > "deblending these maps using the method detailed in (cite: swinbank2013alma) using the ALMA detections as positional priors as described in Ma15" (3.1 SED Fitting) [from (cite: swinbank2013alma); Ma15]
- Band 3 reduction same as Band 6  
  > "The same reduction approach was taken for the Band 3 observations as used for the Band 6 data" (2.3 ALMA Band 3 Observations) [from Section 2.2 of this paper]

### Not stated but needed to reproduce (our reading)

- Band 3 beam size and clean thresholds
- Cell size and image size
- Line-free channels used for continuum subtraction
- Deblended SCUBA-2/Herschel flux values and SED template choice per source
- Details of the CO(5-4)/CO(2-1) brightness ratio conversion
- Aegean parameters beyond the 4 sigma threshold
- Spectral binning used in Gaussian fitting

## Analysis recipe

1. **Detect 1.25 mm continuum sources**: Aegean source finder on mosaic with local noise map, >4 sigma; negative map used for reliability  
  > "we used AEGEAN (cite: hancock2012compact) to identify $>$ 4$\sigma$ detections" (2.4 Source Detection)
   - software: AEGEAN
   - fitting: _not stated_
   - validation: Negative map gives zero >4 sigma detections  
  > "we perform the same detection routine in the negative source map which yields zero detections at $>$ 4$\sigma$" (2.4 Source Detection)
2. **Search and measure CO lines**: Targeted spectra extraction at known positions plus blind search in collapsed 300 km/s bins; Gaussian fits  
  > "Line widths are derived from fitting Gaussian profiles to the binned spectra using scipy.curve_fit in Python weighted by the uncertainty in the spectra." (2.4 Source Detection)
   - software: scipy.curve_fit, AEGEAN, CASA
   - parameter: bins of 300 km/s stepped by 100 km/s, >4 sigma  
  > "collapsing them in 300 km s$^{-1}$ wide bins" (2.4 Source Detection)
   - fitting: single Gaussian, weighted least squares  
  > "we fit single Gaussians to each of the Band 3 and 6 emission spectra" (3.2 CO Line Properties)
   - validation: CO redshifts agree between transitions and with MUSE [OII]  
  > "derive redshifts that agree with the CO (within their 1 $\sigma$ error) in all cases" (2.5 MUSE AO Observations)
3. **Derive FIR luminosities and SFRs**: Fit template SEDs to 100-1250 um photometry, integrate 8-1000 um, Kennicutt relation  
  > "We calculate the infrared luminosity from integrating the best-fitting SEDs for each galaxy in the wavelength range 8–1000 $\mu$m" (3.1 SED Fitting)
   - assumption: sources at cluster redshift; Chabrier IMF  
  > "assuming the sources lie at the cluster redshift" (3.1 SED Fitting)
   - fitting: template library fits (Chary & Elbaz, Draine, Rieke)  
  > "using a library of galaxy template SEDs from (cite: chary2001interpreting; draine2007dust; rieke2009determining)" (3.1 SED Fitting)
   - validation: _not stated_
4. **Derive CO luminosities, gas and dynamical masses**: Solomon & Vanden Bout L'CO relation; Mgas with alpha_CO=1; Mdyn disk model with R=7 kpc  
  > "the $^{12}$CO luminosities were calculated using the relation given in (cite: solomon2005molecular)" (3.2 CO Line Properties)
   - assumption: alpha_CO=1 (4.36 as alternative), R=7 kpc, random-disk inclination, r21/10=0.84  
  > "We also list the dynamical masses ($M_{\rm dyn}$) for a disk-like dynamical model with a 7 kpc radius" (3.2 CO Line Properties)
   - fitting: _not stated_
   - validation: Gas fractions from Mdyn agree with those from IRAC-based stellar masses  
  > "which is in excellent agreement with the gas fractions derived from the dynamical masses" (3.2 CO Line Properties)

## Software

- **CASA** 4.6.0: calibration, imaging, uvcontsub  
  > "CASA v4.6.0 (cite: mcmullin2007casa)" (2.2 ALMA Band 6 Observations)
- **AEGEAN** : continuum and blind line source detection  
  > "we used AEGEAN (cite: hancock2012compact) to identify $>$ 4$\sigma$ detections" (2.4 Source Detection)
- **scipy.curve_fit** : Gaussian line fits  
  > "using scipy.curve_fit in Python weighted by the uncertainty in the spectra" (2.4 Source Detection)
- **esorex MUSE pipeline** : MUSE data reduction  
  > "we use the MUSE esorex pipeline" (2.5 MUSE AO Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of S/N>4 1.25 mm sources | 14 | not stated | sources | 1 | we detect 14 S/N $>$ 4.0$\sigma$ candidate sources from the Band 6 continuum map |
| Overdensity relative to blank field | ~7 | not stated | dimensionless | 1 | we appear to be detecting a $\sim$ 7$\times$ overdensity of millimetre sources |
| Velocity dispersion of 11 mm-selected members | 1040 | 100 | km/s | 2 | we derive a rest-frame velocity dispersion of $\sigma=$ 1040$\pm$100 km s$^{-1}$ |
| Median gas mass (alpha_CO=1) | 1.6e10 | 0.2e10 | Msun | 4 | $M_{\rm
  gas}=1.6\pm0.2\times 10^{10}$ $M_\odot$ |
| r54/21 | 0.37 | 0.06 | dimensionless | 4 | $r_{54/21}=0.37\pm 0.06$ |
| Median gas consumption timescale | 200 | 100 | Myr | 4 | we estimate a median gas consumption timescale of 200$\pm$100 Myrs |
| Median FWHM21/FWHM54 | 0.7 | 0.2 | dimensionless | 2 | FWHM$_{21}$/FWHM$_{54}$ = 0.7 $\pm$ 0.2 |

## Qualitative findings

- Most millimetre sources are cluster members; dust-obscured SFR in the core is >~700 Msun/yr  
  > "we derive a total SFR in the central $\sim$ 500 kpc of the cluster of $\mathrel{\raise 0.35ex\hbox{$\scriptstyle >$}\kern-0.6em
\lower 0.40ex\hbox{{$\scriptstyle \sim$}}}$ 700 $M_\odot$ yr$^{-1}$" (3.1 SED Fitting)

## Claim tuples

- H: The submm sources in the XCS J2215 core are cluster members | E: ALMA 1.25 mm mosaic plus CO and MUSE [OII] redshifts | R: 14 sources; 11 spectroscopically confirmed members, 1 interloper, 2 photo-z consistent | F: The bulk (>=11/14) are U/LIRGs in the cluster | **supported**
- H: Environment has reduced the cool gas and dust in cluster LIRGs | E: Compare CO luminosities, FWHM and LIR with field galaxies | R: Lower CO(2-1) luminosity at fixed FWHM; narrower CO(2-1) than CO(5-4) | F: Tentative hints of stripping of cool gas | **partially**
- H: These LIRGs are progenitors of massive local early-type cluster galaxies | E: Compare dynamical masses and expected ages with local cluster early types | R: Five of six have similar properties | F: Plausible link | **supported**

## Reasoning

- Why this data: High resolution needed to identify counterparts of single-dish submm sources  
  > "uncertainties in reliably identifying the counterparts of far-infrared/submillimetre sources at other wavelengths, due to the typically poor spatial resolution" (1 Introduction)
- Why this method: _not stated_
- Alternative: Milky Way-like alpha_CO~4.4 rejected for at least IDs 6 and 7 as it gives gas fractions >1  
  > "a Milky Way-like $\alpha_{\rm CO}\sim 4.4$ is an inappropriate conversion factor to use" (3.2 CO Line Properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas and dynamical masses depend strongly on alpha_CO and assumed radius/inclination; comparison samples are small  
  > "We note that the derived values are highly dependant on the value of $\alpha_{\rm CO}$" (3.2 CO Line Properties)
- Limitation (authors): FIR luminosities may be unreliable and driven by 1.25 mm flux  
  > "This may indicate that the far-infrared luminosities may be less reliable" (3.1 SED Fitting)
- Caveat (inferred, ours): Environmental stripping claim rests on six galaxies and few comparison sources
- Caveat (inferred, ours): Gas masses use a fixed R=7 kpc and unresolved CO
- Caveat (inferred, ours): CO(2-1) detections are low S/N (some about 2-3 sigma in flux)
- Caveat (inferred, ours): Template SEDs may bias LIR

## Reproducibility

- Data public (paper): All data available through ESO, ALMA and HST archives or published papers  
  > "All of the data used here is available through the ESO, ALMA and *HST* archives or in published papers." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Cell/image size and Band 3 imaging details
- Missing: Deblended single-dish fluxes
- Missing: Exact SED fitting setup
- Missing: Stellar mass derivation details
- Data volume (inferred): ~20-50 GB for two ALMA datasets
- Score (inferred): 3/5, Public data and clear outline, but several imaging and SED fitting details are missing.
- Rediscovery candidate: yes, Public ALMA data; numeric results such as source count, CO fluxes and line ratios are reproducible, though some settings are missing.

## Links

- Method: (cite: bothwell2013survey) (Source of alpha_CO, R and Mdyn recipe)
- Method: (cite: swinbank2013alma) (Deblending method for single-dish maps)
- Companion: (cite: hayashi2017evolutionary) (Independent ALMA Band 3 CO(2-1) study of the same cluster)
- Companion: (cite: ma2015dusty) (SCUBA-2 survey of the cluster)
- Related: SCUBA-2 survey of XCS J2215

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 49,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
