# ALMA Observations of Polarization from Dust Scattering in the IM Lup Protoplanetary Disk

`2018ApJ...860...82H` | The Astrophysical Journal 2018 | first author: Hull, Charles L. H. | arXiv: 1804.06269 | DOI: 10.3847/1538-4357/aabfeb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the 870 um dust polarization morphology of the IM Lup disk, is it consistent with self-scattering, and what maximum grain size does it imply compared with HL Tau?  
  > "To shed more light on the origins of dust polarization in disks, and to investigate the polarization in a Class II source that is more evolved than HL Tau" (Introduction)
- Target **IM Lup**: coordinates 15:56:09.172 -37:56:06.483 (J2000)  
  > "The pointing center was $\alpha_\textrm{J2000}$ = 15:56:09.172, $\delta_\textrm{J2000}$ = –37:56:06.483." (2 Observations); "corresponding to a linear resolution of $\sim$ 72 au at a distance of $161 \pm 10$ pc (cite: Gaia2016)." (2 Observations); z/distance 161 ± 10 pc  
  > "The pointing center was $\alpha_\textrm{J2000}$ = 15:56:09.172, $\delta_\textrm{J2000}$ = –37:56:06.483." (2 Observations); "corresponding to a linear resolution of $\sim$ 72 au at a distance of $161 \pm 10$ pc (cite: Gaia2016)." (2 Observations); distance from Gaia (Gaia2016)  
  > "The pointing center was $\alpha_\textrm{J2000}$ = 15:56:09.172, $\delta_\textrm{J2000}$ = –37:56:06.483." (2 Observations); "corresponding to a linear resolution of $\sim$ 72 au at a distance of $161 \pm 10$ pc (cite: Gaia2016)." (2 Observations)

## Data provenance

- ALMA projects: 2016.1.00712.S
- bands: Band 7 (870 um)  
  > "At Band 7 (870 $\mu$m), ALMA’s flux-calibration accuracy is $\sim$ 10%" (2 Observations)
- frequencies and spectral setup: 8 GHz wide-band continuum, ~336.5–350.5 GHz, mean 343.479 GHz (873 um); four correlator bands  
  > "The ALMA polarization data comprise 8 GHz of wide-band dust continuum ranging in frequency from $\sim$ 336.5–350.5 GHz, with a mean frequency of 343.479 GHz (873 $\ensuremath{\mu}m$)." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.50" x 0.40", PA 76.9 deg (~72 au)  
  > "The observations have a synthesized beam (resolution element) of 0$\ensuremath{''}$50 $\times$ 0$\ensuremath{''}$40 at a position angle of 76.9$\degree$," (2 Observations)
- max recoverable scale: ~4"  
  > "The largest recoverable scale in the data is approximately 4$\ensuremath{''}$" (2 Observations)
- sensitivity: sigma_I = 100 uJy/beam; sigma_P = 22 uJy/beam  
  > "The rms noise level in the final Stokes $I$ dust map is $\sigma_I = 100$ $\mu$Jy beam$^{-1}$" (2 Observations)
- time on source: _not stated_
- observing dates: 2017 April 24 and 26  
  > "on 2017 April 24 and 2017 April 26" (2 Observations)
- pi or archival as stated: _not stated_
- External data: HL Tau 870 um polarization fraction cuts and total polarization fractions for comparison  
  > "the 870 $\ensuremath{\mu}m$ HL Tau data are from (cite: Stephens2017b)" (4.1) [from (cite: Stephens2017b)]
- External data: IM Lup disk model (dust column density, scale height, gamma = 1.0)  
  > "we adopt the IM Lup disk model based on (cite: Cleeves2016), taking into account only millimeter-sized dust grains." (4.2) [from (cite: Cleeves2016)]
- External data: Grain composition (water ice 62%, organics 30%, silicates 8%)  
  > "All fractional abundances are by volume and are taken from (cite: Pollack1994)." (4.2) [from (cite: Pollack1994)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux), J1517-2422 (bandpass), J1610-3958 (phase); polarization calibrator J1549+0237  
  > "The flux, bandpass, and phase calibrators were Titan, J1517-2422, and J1610-3958, respectively" (2 Observations)
- flux scale uncertainty: ~10%  
  > "ALMA’s flux-calibration accuracy is $\sim$ 10%" (2 Observations)
- self calibration: four rounds of phase-only self-cal using Stokes I model; shortest solint 10 s  
  > "The images were improved by performing four rounds of phase-only self-calibration using the total intensity (Stokes $I$) image as a model" (2 Observations)

### Imaging

- task: CASA tclean; Stokes I, Q, U cleaned independently  
  > "The Stokes $I$, $Q$, and $U$ maps (where the $Q$ and $U$ maps show the polarized emission) were each cleaned independently" (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with a Briggs weighting parameter of robust = 0.5" (2 Observations)
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
- final beam: 0.50" x 0.40", PA 76.9 deg  
  > "0$\ensuremath{''}$50 $\times$ 0$\ensuremath{''}$40 at a position angle of 76.9$\degree$," (2 Observations)
- final rms: I: 100 uJy/beam; P: 22 uJy/beam  
  > "whereas the rms noise level in the map of polarized intensity $P$" (2 Observations)

### Inherited from earlier work

- Polarized intensity debiasing method  
  > "we do debias the polarized intensity map as described in (cite: Vaillancourt2006) and (cite: Hull2015b)" (2 Observations) [from (cite: Vaillancourt2006); (cite: Hull2015b)]
- Grain model and scattering model setup  
  > "For the dust grain model, we adopted the one used by (cite: Kataoka2015) and (cite: Yang2016a)" (4.2) [from (cite: Kataoka2015); (cite: Yang2016a)]
- Total polarization fraction metric versus grain size  
  > "we repeat the exercise of (cite: Kataoka2017), who analyzed the polarization of HL Tau" (4.2) [from (cite: Kataoka2017)]

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean image size, cell size, niter, threshold and masks
- self-calibration solution intervals beyond the shortest (10 s), and the order of intervals
- how Stokes I/Q/U were derived from the polarization calibration (CASA polcal steps)
- RADMC-3D settings: number of photons, grid, inclination and position angle, stellar parameters, observation simulation/beam convolution
- how the model best fit was judged (no quantitative metric)
- bin width of the polarization-angle histogram

## Analysis recipe

1. **Image Stokes I, Q, U with self-calibration**: tclean with robust 0.5, four rounds of phase-only self-cal from Stokes I model, then independent cleaning of I, Q, U  
  > "The images were improved by performing four rounds of phase-only self-calibration using the total intensity (Stokes $I$) image as a model" (2 Observations)
   - software: CASA
   - parameter: robust = 0.5; shortest solint 10 s  
  > "the shortest interval for determining the gain solutions was 10 s" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive P, Pfrac and position angle maps**: P = sqrt(Q^2+U^2), Pfrac = P/I, chi = 0.5 arctan(U/Q); P debiased  
  > "Note that while we do debias the polarized intensity map as described in (cite: Vaillancourt2006) and (cite: Hull2015b)" (2 Observations)
   - parameter: detections where P > 3 sigma_P; I > 3 sigma_I  
  > "$P$ is the polarized intensity, reported where $P > 3\,\sigma_P$." (Table 1)
   - fitting: _not stated_
   - validation: Checked frequency dependence across the four correlator bands; no change found  
  > "We found no significant changes in polarized intensity, polarization fraction, or polarization angle as a function of frequency" (3 Results)
3. **Histogram of polarization angles**: Each angle binned as a Gaussian PDF with its mean and sigma; compared with 48 deg minor axis  
  > "each individual polarization angle measurement was binned presuming it had a Gaussian probability distribution function (PDF)" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate maximum grain size with scattering models**: Mie opacities and scattering matrix, RADMC-3D Monte Carlo radiative transfer, varying a_max; compare polarization fraction cuts and angle histogram  
  > "We then calculate polarization by varying the maximum grain size $a_{\rm max}$ with the Monte Carlo Radiative Transfer code RADMC-3D (cite: Dullemond2012)." (4.2)
   - software: RADMC-3D
   - parameter: a_max = 61 um best; 50 and 70 um tested  
  > "We tested slightly larger (70 $\ensuremath{\mu}m$) and smaller (50 $\ensuremath{\mu}m$) maximum grain sizes, and found that they do not reproduce the observations" (4.2)
   - assumption: MRN n(a) ∝ a^-3.5, a_min = 0.25 um; spherical grains of ice 62%, organics 30%, silicates 8%; Sigma_c = 0.25 g cm^-2 at 100 au, H_c = 3 au, gamma = 1.0  
  > "The grain size distribution follows the Mathis, Rumpl & Nordsieck (MRN)-type power-law $n(a) \propto a^{-3.5}$ (cite: Mathis1977), with a fixed minimum grain size $a_{\rm min}=0.25\rm\, \mu m$." (4.2)
   - fitting: Visual comparison of model and observed cuts and histogram (no formal fit stated)  
  > "the predicted distributions of the polarization fraction along the major and minor axes agree well with observations, peaking at $\sim$ 1.1% when the maximum grain size is set to be 61 $\ensuremath{\mu}m$" (4.2 Maximum grain-size estimate for IM Lup)
   - validation: Total polarization fraction P/I ~0.50% compared with Kataoka2017 curves, roughly consistent with ~70 um  
  > "we find all of the above values of the total polarization fraction (at their respective wavelengths) are roughly consistent with a maximum size of $\sim$ 70 $\ensuremath{\mu}m$" (4.2)

## Software

- **CASA** : calibration/imaging with tclean and self-calibration  
  > "Common Astronomy Software Applications (CASA, (cite: McMullin2007)) task **TCLEAN**" (2 Observations)
- **RADMC-3D** : Monte Carlo radiative transfer for scattering polarization  
  > "Monte Carlo Radiative Transfer code RADMC-3D (cite: Dullemond2012)" (4.2)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak polarization fraction | ~1.1 | not stated | % | 2 | reaching a peak value of $\sim$ 1.1% |
| Integrated 870 um flux | 580 | not stated | mJy | 1 | The integrated 870 $\mu$m flux of IM Lup from our observations is 580 mJy |
| Total polarization fraction P/I | 0.50 | not stated | % | 4 | We find that the total polarization fraction of IM Lup in our 870 $\ensuremath{\mu}m$ observations is $P/I \approx 0.50\%$ |
| Maximum grain size | 61 | not stated | um | 4 | We can reproduce the observed polarization in our 870 $\ensuremath{\mu}m$ IM Lup observations with $a_{\rm max}$ of 61 $\ensuremath{\mu}m$. |
| Mean polarization angle uncertainty | 3.6 | not stated | deg | 3 | 3.6$\degree$ is the mean of the statistical uncertainties in all of the polarization angles detected toward IM Lup. |
| Circular polarization fraction | ~0.17 | not stated | % | 2 | the circular polarization fraction is only $\sim$ 0.17% of the total intensity |

## Qualitative findings

- Polarization is oriented along the disk minor axis with polarization fraction rising toward the center, consistent with self-scattering.  
  > "We find that the orientation of the polarized emission is along the minor axis of the disk" (abstract)
- No obvious near/far-side asymmetry, suggesting settled ~60 um grains if marginally optically thick.  
  > "There is no obvious near/far-side asymmetry detected in our observations" (4.3)

## Claim tuples

- H: IM Lup polarization at 870 um arises from dust self-scattering | E: Mapped Stokes I, Q, U and compared orientation and fraction with scattering models | R: Polarization along the minor axis, Pfrac rising to ~1.1% at the center, with angle spread | F: Consistent with self-scattering from an inclined disk | **supported**
- H: IM Lup has a higher polarization fraction than HL Tau | E: Compared major and minor axis cuts of Pfrac | R: IM Lup is substantially higher at the center | F: Higher HL Tau optical depth or larger grains in IM Lup are possible causes | **partially**
- H: Scattering models give maximum grain sizes that differ between the disks | E: RADMC-3D models varying a_max | R: 61 um for IM Lup, versus 72 um for HL Tau | F: Similar sizes, in tension with mm/cm grains from the emission spectrum | **supported**

## Reasoning

- Why this data: IM Lup is massive, large, has no envelope, is azimuthally symmetric with intermediate inclination, and is more evolved than HL Tau  
  > "IM Lup has a number of other features that make it ideally suited for studying scattering-induced disk polarization." (Introduction)
- Why this method: _not stated_
- Alternative: Alignment with the dust emission gradient judged not significant, since angle curvature is smaller than in HL Tau at 1.3 mm  
  > "suggesting that alignment of dust grains with the dust emission gradient is not contributing significantly to our 870 $\ensuremath{\mu}m$ polarization observations" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot draw firm quantitative conclusions about dust settling since the optical depth across the polarized region is uncertain  
  > "we cannot currently draw firm quantitative conclusions about dust settling" (4.3)
- Caveat (inferred, ours): Grain-size estimate relies on a single-band comparison with no quantitative goodness-of-fit
- Caveat (inferred, ours): Only three a_max values were tested; the uncertainty on 61 um is not given
- Caveat (inferred, ours): Disk model is taken from Cleeves2016 and not refit; Mie spherical grains assumed
- Caveat (inferred, ours): Single 870 um band cannot separate scattering from other mechanisms

## Reproducibility

- Data public (paper): Project code is given in the acknowledgments; public status is not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00712.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and polarization calibration commands
- Missing: imaging grid parameters and masks
- Missing: RADMC-3D model inputs and the exact comparison method
- Data volume (inferred): ~20-50 GB raw for two Band 7 polarization execution blocks
- Score (inferred): 5/5, Data and main imaging parameters are given and the table of results is published, but CASA version, polarization calibration details and the RADMC-3D setup are missing.
- Rediscovery candidate: no, The model comparison recipe is incomplete and the grain size result is not strictly numerical-fit based, although the polarization maps could be redone.

## Links

- Method: (cite: Nagai2016) (ALMA polarization system)
- Method: (cite: Hull2015b) (polarization debiasing)
- Companion: (cite: Stephens2017b) (HL Tau ALMA polarization comparison)
- Companion: (cite: Cleeves2016) (IM Lup disk model)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 43,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
