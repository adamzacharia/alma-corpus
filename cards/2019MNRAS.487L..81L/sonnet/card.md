# The absence of [C II] 158 μm emission in spectroscopically confirmed galaxies at z &gt; 8

`2019MNRAS.487L..81L` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Laporte, N. | arXiv: 1906.01937 | DOI: 10.1093/mnrasl/slz094

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do the two most distant spectroscopically-confirmed galaxies (z=8.38 and z=9.11), both bright in [OIII]88um, show [CII]158um emission, and what does this imply for the [CII] deficit at high redshift?  
  > "we exploit the newly-available band 5 receiver to present new observations targeting \[C II\] 158$\mu$m in each source" (Introduction)
- Target **A2744_YD4**: coordinates _not stated_; z/distance z=8.38 (z_OIII = 8.382)  
  > "A2744_YD4 at $z=8.38$ for which a dust continuum detection was also secured (cite: Laporte2017)" (Introduction); distance from [OIII]88um, Laporte2017  
  > "A2744_YD4 at $z=8.38$ for which a dust continuum detection was also secured (cite: Laporte2017)" (Introduction)
- Target **MACS1149_JD1**: coordinates _not stated_; z/distance z=9.11 (z_OIII = 9.1096)  
  > "MACS1149_JD1 at $z=9.11$ (cite: Hashimoto2018)" (Introduction); distance from [OIII]88um, Hashimoto2018  
  > "MACS1149_JD1 at $z=9.11$ (cite: Hashimoto2018)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00463.S
- bands: Band 5 (new); Band 7 for YD4 re-reduced; Band 6 archival for YD4  
  > "Observations were carried out in band 5 during ALMA Cycles 5 and 6" (Observations)
- frequencies and spectral setup: Lower spectral window covers [CII] at z=8.26-8.43 (YD4) and 8.96-9.16 (JD1)  
  > "its width covers the redshift range 8.26 $< z <$ 8.43." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-2 (YD4), C43-4 (JD1)  
  > "Observations of A2744_YD4 were made with the C43-2 configuration yielding a beam size of 1.3”$\times$0.79”." (Observations)
- baselines: _not stated_
- angular resolution: YD4 1.3"x0.79"; JD1 0.75"x0.63"  
  > "For MACS1149_JD1, we used the configuration C43-4 to achieve a beam size of 0.75”$\times$0.63”." (Observations)
- max recoverable scale: _not stated_
- sensitivity: 3sigma continuum < 21 uJy/beam (YD4), < 15 uJy/beam (JD1), not corrected for magnification  
  > "$f_{\nu}^{158\mu m}$\< 21 $\mu$Jy/beam for A2744_YD4 and $f_{\nu}^{158\mu m}$\< 15 $\mu$Jy/beam for MACS1149_JD1" (Observations)
- time on source: 3.8 hr (YD4), 6.2 hr (JD1)  
  > "The total exposure time on source was 3.8hrs." (Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- External data: [OIII] luminosity, z, L_FIR, SFR, Mstar, 88um flux for A2744_YD4 and magnification mu=2  
  > "$^a$ (cite: Laporte2017)" (Table 1) [from (cite: Laporte2017)]
- External data: [OIII] luminosity, z, L_FIR, SFR, Mstar for MACS1149_JD1 and mu=10  
  > "$^b$ (cite: Hashimoto2018)" (Table 1) [from (cite: Hashimoto2018)]
- External data: [CII] non-detection measurements of Lyman-alpha emitter at z=7.2  
  > "A similar non-detection of \[Cii\]158$\mu$m was reported by (cite: Inoue2016) for a Lyman-$\alpha$ emitter at $z$ = 7.2" (Observations) [from (cite: Inoue2016)]
- External data: Local metal-poor dwarf [OIII]/[CII] ratios  
  > "lower redshift metal-poor dwarf galaxies (cite: Madden2013)" (Analysis) [from (cite: Madden2013)]
- Simulation/model as data: Katz2019 hydrodynamical simulations (0.1 solar metallicity) and Lagache2018 semi-analytical model (>10^3 objects at z~8)  
  > "Examining a recent semi-analytical model of galaxy evolution (cite: Lagache2018) in over 10$^3$ simulated objects at $z\simeq$8" (Analysis)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "Data were reduced using the version 5.4.0 of the CASA pipeline ((cite: CASA))" (Observations)
- casa version: 5.4.0  
  > "Data were reduced using the version 5.4.0 of the CASA pipeline ((cite: CASA))" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean with Briggs weighting  
  > "a Briggs weighting was applied in the *tclean* task in both cases" (Observations)
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

- Magnification factors and source properties  
  > "see (cite: Laporte2017) and (cite: Hashimoto2018) for details" (Observations) [from (cite: Laporte2017), (cite: Hashimoto2018)]
- Velocity offset search window of +/-500 km/s  
  > "ranging from -500 km/s to 500km/s (e.g. (cite: Hashimoto2019))" (Observations) [from (cite: Hashimoto2019)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, niter and threshold
- Spectral window frequencies and channel widths
- Continuum-subtraction approach and line-free channels
- Flux calibrator and flux scale uncertainty
- Exact positions for the apertures and the UV-rest-frame centres
- MAGPHYS setup (priors, library, photometry used)
- Selection details for the Lagache2018 comparison

## Analysis recipe

1. **Reduce data and image**: CASA 5.4.0 pipeline and tclean with Briggs weighting; Band 7 data for YD4 re-reduced the same way  
  > "we re-reduced ALMA band 7 data for A2744_YD4 following the same procedures" (Observations)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: _not stated_
2. **Continuum upper limits**: 3sigma limits from several beam-size apertures at the field centre  
  > "We measure 3$\sigma$ upper limits using several beam-size apertures distributed at the centre of the field" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Search for [CII] line and derive luminosity limits**: Search in 1.5" radius circle around UV position, velocity offset ±500 km/s relative to [OIII] z, rebin to FWHM=100 km/s (also 50 km/s); rms in beam-size apertures; 3sigma L_CII limits corrected for magnification  
  > "We rebinned the data assuming a FWHM of 100km/s for \[Cii\]158$\mu$m" (Observations)
   - parameter: mu=2 (YD4), mu=10 (JD1)  
  > "taking into account the best magnification for the two targets ($\mu$=2 and $\mu$=10 respectively for YD4 and JD1" (Observations)
   - assumption: Line FWHM=100 km/s  
  > "assuming a FWHM=100km/s" (Observations)
   - fitting: _not stated_
   - validation: Repeated with 50 km/s FWHM; no line found  
  > "but no emission line was found on either dataset" (Observations)
4. **Compare with relations and simulations**: Place sources on [CII]-SFR relation, compare [OIII]/[CII] with Katz2019 simulations and local dwarfs; select Lagache2018 analogues by SFR, L_CII and Mstar ranges  
  > "we find 75 simulated objects that have extreme properties similar to A2744_YD4" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
5. **Constrain dust temperature of YD4**: SED fit with MAGPHYS including Band 5 limit and Band 6 2sigma limit of 30 uJy/beam  
  > "Using *MAGPHYS* (cite: MAGPHYS), we can give a first constraint on the dust temperature in this object $T_{dust}$ \> 55 K." (Analysis)
   - software: MAGPHYS
   - fitting: _not stated_
   - validation: Using 3sigma limits gives T>43 K  
  > "Using the 3$\sigma$ upper limits for both band 5 and 6 observations decreases the minimum dust temperature to T$>$43 K." (Analysis)

## Software

- **CASA** 5.4.0: Data reduction (pipeline) and imaging  
  > "Data were reduced using the version 5.4.0 of the CASA pipeline ((cite: CASA))" (Observations)
- **MAGPHYS** : SED fitting for dust temperature  
  > "Using *MAGPHYS* (cite: MAGPHYS), we can give a first constraint on the dust temperature" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_CII upper limit A2744_YD4 (3sigma) | <2.0e7 x (2/mu) | not stated | Lsun | 3 | $L_{CII}^{YD4}$\< 2.0$\times$10$^7$$\times$(2/$\mu$)L$_{\odot}$ |
| L_CII upper limit MACS1149_JD1 (3sigma) | <3.98e6 x (10/mu) | not stated | Lsun | 3 | $L_{CII}^{JD1}$\< 3.98$\times$10$^6$$\times$(10/$\mu$)L$_{\odot}$ |
| Band 5 continuum 3sigma limit YD4 | <21 | not stated | uJy/beam | 2 | $f_{\nu}^{158\mu m}$\< 21 $\mu$Jy/beam for A2744_YD4 |
| Band 5 continuum 3sigma limit JD1 | <15 | not stated | uJy/beam | 2 | $f_{\nu}^{158\mu m}$\< 15 $\mu$Jy/beam for MACS1149_JD1 |
| YD4 dust temperature lower limit | >55 | not stated | K | 5 | $T_{dust}$ \> 55 K |
| Simulated analogues of YD4 | 75 | not stated | objects | 4 | we find 75 simulated objects that have extreme properties similar to A2744_YD4 |
| Simulated analogues of JD1 | 8 | not stated | objects | 4 | only 8 simulated sources have \[C II\]158$\mu$m properties similar to MACS1149_JD1 |

## Qualitative findings

- Neither target shows [CII] or Band 5 continuum; [OIII]/[CII] ratios are anomalously high.  
  > "Likewise when studying the \[Oiii\]88$\mu$m/ \[Cii\]158$\mu$m line ratio, we find anomalously high values." (Summary)

## Claim tuples

- H: Do z>8 galaxies with strong [OIII] show [CII] consistent with the local [CII]-SFR relation? | E: Band 5 ALMA search for [CII] in YD4 and JD1 | R: No detection; stringent upper limits well below local relation | F: A redshift-dependent [CII] deficit exists at z>8 | **supported**
- H: Is low metallicity alone sufficient to explain the deficit? | E: Compare [OIII]/[CII] with Katz2019 simulations at 0.1 solar | R: Metallicity would need to drop by ×10, which also reduces [OIII] | F: Low metallicity may be insufficient | **partially**
- H: Are such faint [CII] luminosities expected in models? | E: Search Lagache2018 semi-analytic objects at z~8 | R: Only 75 and 8 analogues out of >10^3 | F: Such faint [CII] is rarely expected | **supported**
- H: Is YD4 dust warmer than the typical 30 K? | E: MAGPHYS SED fit with Band 5 and Band 6 limits | R: T_dust>55 K (>43 K with 3sigma limits) | F: Consistent with simulations predicting higher dust temperature | **supported**

## Reasoning

- Why this data: Band 5 receiver newly available, allows [CII] search in the two most distant ALMA-accessible confirmed sources  
  > "The two sources represent the highest redshift spectroscopically-confirmed sources accessible to ALMA" (Introduction)
- Why this method: _not stated_
- Alternative: CMB attenuation and low metallicity considered but seem unable to fully explain the deficit; high ionisation parameter and feedback suggested  
  > "seems unable to explain the size of the discrepancy" (Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Non-detections in sparse high-z data may be due to inadequate sensitivity in some cases  
  > "some non-detections are likely due to inadequate sensitivity" (Introduction)
- Caveat (inferred, ours): Upper limits depend on the assumed 100 km/s line FWHM and the magnification
- Caveat (inferred, ours): Possible spatial offset of [CII] beyond the 1.5" search radius not fully excluded
- Caveat (inferred, ours): Inconsistent numbers between text and Table 1 for continuum limits (21 vs 10.5 uJy/beam)
- Caveat (inferred, ours): Dust temperature limit depends on unstated MAGPHYS priors

## Reproducibility

- Data public (paper): ADS/JAO.ALMA data codes are listed in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.A.00463, ADS/JAO.ALMA#2017.1.00697" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, cell, image size)
- Missing: Frequency setup and channelization
- Missing: MAGPHYS configuration
- Data volume (inferred): ~50-150 GB raw for Band 5 plus Band 6/7
- Score (inferred): 3/5, Public data and simple upper-limit procedure, but imaging and SED parameters are not given.
- Rediscovery candidate: yes, Public data, numeric upper limits; the recipe is simple though imaging details are missing.

## Links

- Companion: (cite: Laporte2017) (Original [OIII] and dust detection in A2744_YD4)
- Companion: (cite: Hashimoto2018) (Original [OIII] detection in MACS1149_JD1)
- Related: 2018.A.0004

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00594.S",
  "2017.1.00697.S",
  "2017.A.00026.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
