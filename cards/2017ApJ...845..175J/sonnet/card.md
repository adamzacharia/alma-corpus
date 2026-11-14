# Galaxy Formation through Filamentary Accretion at z = 6.1

`2017ApJ...845..175J` | The Astrophysical Journal 2017 | first author: Jones, G. C. | arXiv: 1706.09968 | DOI: 10.3847/1538-4357/aa7d0d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the detailed spatial and kinematic structure of [C II] and dust emission in the z=6.07 LBG WMH5, and does it indicate galaxy assembly via accretion of satellites along a filament?  
  > "In this paper, we present subarcsecond angular resolution and high sensitivity observations of the [C II] and dust emission from WMH5 using ALMA in Cycle 3." (Introduction)
- Target **WMH5**: coordinates _not stated_; z/distance z = 6.0695  
  > "At this distance, 1 arcsecond corresponds to 5.81 proper kpc at the redshift of WMH5 ($z$=6.0695; (cite: will15))." (Introduction); distance from Willott et al. 2015 (will15)  
  > "At this distance, 1 arcsecond corresponds to 5.81 proper kpc at the redshift of WMH5 ($z$=6.0695; (cite: will15))." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00815.S, 2015.1.00834.S
- bands: Band 6  
  > "spanning 253 to 257 GHz and 268 to 272 GHz (ALMA band 6)" (Observations)
- frequencies and spectral setup: four 2 GHz sub-bands, one centered on [CII] at 268.836 GHz, three for continuum  
  > "One sub-band was centered on the [C II] emission, redshifted to $268.836$ GHz, while the other three were used to measure the rest frame $\sim160\,\mu$m continuum emission." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3 (Cycle 3)  
  > "in configuration C40-3 between 2016 August 3 and 7" (Observations)
- baselines: _not stated_
- angular resolution: 0.30'' x 0.25'', PA 74 deg  
  > "The synthesized beam was $0.30''\times0.25''$, with major axis position angle = $74^{\circ}$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum 9 uJy/beam; line cube 0.1 mJy/beam per 17 km/s channel  
  > "we created a continuum image with an RMS noise level of $9\,\mu$Jy beam$^{-1}$." (Observations)
- time on source: 4 hours (Cycle 3); 95 min (Cycle 2)  
  > "The total time was $\sim6.5$ hours, out of which 4 hours were spent on source." (Observations)
- observing dates: 2016 Aug 3-7 (Cycle 3); June 2014 (Cycle 2)  
  > "they observed in June 2014 with 29-32 antennas, 7.5 GHz of bandwidth, and had 95 minutes of on-source integration time." (Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um fine-structure (not stated)
- Other facility **Ground-based near-IR imaging**: near-IR image overlaid with [CII] contours  
  > "overlaid on the ground-based near-IR image." (Results)
- External data: Cycle 2 ALMA observations of WMH5 combined with Cycle 3 data  
  > "we combined these data with the Cycle 2 observations of (cite: will15)." (Observations) [from Willott et al. 2015 (cite: will15)]
- External data: SFR_SED and SFR_FIR summed to total SFR 76+-11 Msun/yr  
  > "we add SFR$_{SED}$ and SFR$_{FIR}$ of (cite: will15), yielding $76\pm11$ M$_{\odot}$ year$^{-1}$." (Analysis) [from Willott et al. 2015 (cite: will15)]
- External data: [CII]/continuum ratios of z~5.5 galaxies HZ4, HZ6, HZ9, HZ10  
  > "These four give ratios of $(6\pm2)\times10^3$ km s$^{-1}$ (HZ4)[^2]" (Analysis) [from Capak et al. 2015 (cite: capa15)]
- Simulation/model as data: Pallottini et al. 2017 'Dahlia' zoom simulation compared qualitatively  
  > "(cite: pall17) studied in detail *Dahlia*, a typical $z\approx 6$ LBG with a SFR $\approx 100\,M_{\odot} \mathrm{yr}^{-1}$" (Discussion)

## Processing

### Calibration

- pipeline or manual: standard calibration script from JAO staff (Cycle 3)  
  > "The Cycle 3 data were calibrated using the standard calibration script prepared by the Joint ALMA Observatory staff." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "When using the CASA task *clean* to combine these two datasets" (Observations)
- deconvolver: _not stated_
- weighting robust: natural (robust 2.0); also tried 1.5, 1.0  
  > "the best results were found for natural (robust 2.0) weighting." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 2 + Cycle 3 uv data, reweighted with statwt  
  > "Since the *statwt* image had the lowest rms noise level and had weights based on properties of the data, we will use this weighting method" (Observations)
- smoothing: _not stated_
- final beam: 0.30'' x 0.25'', PA 74 deg  
  > "The synthesized beam was $0.30''\times0.25''$, with major axis position angle = $74^{\circ}$." (Observations)
- final rms: 9 uJy/beam continuum; 0.1 mJy/beam line  
  > "an RMS noise level of 0.1 mJy beam$^{-1}$." (Observations)

### Inherited from earlier work

- Greybody for FIR luminosity: T_dust=30 K, beta=1.6, 42.5-122.5 um  
  > "A greybody spectrum identical to that used by (cite: will15) was adopted" (Analysis) [from Willott et al. 2015 (cite: will15)]
- Zero velocity at [CII] redshift z=6.0695  
  > "we adopt zero velocity as [C II] emission redshifted to $z=6.0695$, consistent with (cite: will15)." (Results) [from Willott et al. 2015 (cite: will15)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, clean threshold and masks
- Continuum/line channel selection and continuum subtraction method
- Flux calibrators and CASA version used for Cycle 3
- Velocity ranges and fitting details for Gaussian fits; exact Cycle 2 data processing
- Metallicity-SFR calculation details from Vallini eq. 8
- Moment map clipping thresholds

## Analysis recipe

1. **Combine and reweight Cycle 2 and 3 data, image**: Reweight uv data with statwt, then clean with natural weighting to make continuum image and [CII] cube  
  > "The other used the CASA task *statwt*, which resets weights based on the intrinsic scatter of the data." (Observations)
   - software: CASA
   - parameter: 15.6 MHz ~17 km/s channels; natural weighting  
  > "line emission cube with $15.6\,\mathrm{MHz}\sim17$ km s$^{-1}$ channels" (Observations)
   - fitting: _not stated_
   - validation: Compared images from original weights, unit weights and statwt; chose lowest rms  
  > "Both re-weighting methods resulted in images with lower rms noise levels than the original image, and similar channel maps." (Observations)
2. **Fit spectra of core and tail components**: 1D Gaussian fits to single-pixel spectra at core and tail positions  
  > "We performed Gaussian fitting to the apparent three components of the tail." (Results)
   - fitting: Gaussian components; sampler/priors not stated  
  > "We performed Gaussian fitting to the apparent three components of the tail." (Results)
   - validation: _not stated_
3. **Measure [CII] luminosities and SFRs**: 2D Gaussian fits to moment-0 maps of core and sub-galaxy velocity ranges; SFR from Vallini et al. eq. 8  
  > "assuming the relationship given in equation 8 of (cite: vall15) and a metallicity." (Analysis)
   - parameter: core 169 to -77 km/s; sub-galaxies -94 to -305 km/s  
  > "core galaxy (169 to -77 km s$^{-1}$)" (Analysis)
   - assumption: Metallicity 1.0 or 0.1 Zsun; flat cosmology (0.692,0.308,0.678)  
  > "Assuming a solar metallicity, the implied star formation rates for the core and sub-galaxies are $\sim20\,M_{\odot}$ year$^{-1}$." (Analysis)
   - fitting: _not stated_
   - validation: Noted core/sub-galaxy separation not clean, so sub-galaxy flux may be overestimated  
  > "so the flux densities of the sub-galaxy complex may be overestimated." (Analysis)
4. **Derive [CII]/continuum ratios and L_CII/L_FIR**: Ratio of line to continuum surface brightness at core and tail; L_CII via Solomon+92 eq.1; FIR from greybody  
  > "The integrated [C II] flux density was converted to a luminosity using equation 1 of (cite: solo92)." (Analysis)
   - assumption: T_dust=30 K, beta=1.6, FIR 42.5-122.5 um, uniform across source  
  > "Note that we assume that these parameters are uniform across the source." (Analysis)
   - fitting: _not stated_
   - validation: Compared with Capak et al. z~5.5 sample  
  > "Thus, the ratios of both segments of WMH5 fall within the scatter of the Capak et al. sample." (Analysis)
5. **Dust mass**: Bianchi 2013 eq. 1 with 160 um flux density  
  > "By using equation 1 of (cite: bian13), our $\sim160\,\mu$m continuum flux density ($0.15\pm0.03\,$mJy)" (Analysis)
   - assumption: kappa0=1.88 m2/kg at 2.4 THz; T=25-100 K, beta=1.2-2.0 range  
  > "$T_{\rm dust}=25-100$ K and $\beta=1.2-2.0$" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : clean imaging and statwt reweighting  
  > "The other used the CASA task *statwt*" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] core flux (moment 0) | 0.32 | 0.03 | Jy km/s | 3 | a velocity integrated flux density of $0.32\pm0.03$ Jy km s$^{-1}$ |
| L_[CII],CORE | 3.2e8 | 0.3e8 | Lsun | 3 | $L_{\rm [C\,II],CORE}=(3.2\pm0.3)\times10^8\,L_{\odot}$ |
| L_[CII],SG | 3.0e8 | 0.4e8 | Lsun | 3 | $L_{\rm [C\,II],SG}=(3.0\pm0.4)\times10^8\,L_{\odot}$ |
| Continuum integrated flux density | 0.15 | 0.03 | mJy | 1 | an integrated flux density of $0.15\pm0.03\,$mJy |
| [CII]/continuum ratio core | 4.3e3 | 0.8e3 | km/s | 4 | The line to continuum ratio for the core is then: $(4.3\pm0.8)\times10^3$ km s$^{-1}$. |
| Dust mass | 4.0e8 | 0.8e8 | Msun | 5 | we find a dust mass of $(4.0\pm0.8)\times10^8\,M_{\odot}$ |
| SG-1 velocity / FWHM | -249 / 94 | 5 / 12 | km/s | 2 | / SG-1 / $0.50\pm0.05$ / $-249\pm5$ / $94\pm12$ / $0.05\pm0.01$ / |

## Qualitative findings

- Core velocity field shows a gradient but is not a clear rotating disk  
  > "the core galaxy is not highly reminiscent of either a solid-body rotator or a classic rotating disk, but does show an identifiable velocity gradient." (Velocity Behavior)

## Claim tuples

- H: WMH5 is assembling via accretion of satellite sub-galaxies along a filament | E: High-resolution [CII] and continuum imaging, spectral decomposition, comparison with Pallottini simulation | R: Two narrow velocity sub-components in the eastern tail, joining the core velocity field | F: Consistent with accretion of satellites along a possibly filamentary structure | **partially**
- H: [CII]/continuum ratios of WMH5 are similar to other z~5.5 LBGs | E: Ratio at core and tail positions compared with Capak et al. | R: Ratios (4.3+-0.8)e3 and (4+-2)e3 km/s | F: Within the scatter of the comparison sample | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outflow cannot be ruled out but judged less likely given narrow velocity dispersion  
  > "While we cannot rule-out outflow, we find that notion less likely" (Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Comparison against a single simulated system only  
  > "the comparison with observations is here performed only against a single, although very similar, simulated system." (Discussion)
- Caveat (inferred, ours): Filament geometry is inferred, not directly observed
- Caveat (inferred, ours): Metallicity constrained only to 0.1-1 Zsun
- Caveat (inferred, ours): Dust mass depends on assumed T and beta
- Caveat (inferred, ours): Weight rescaling between cycles may bias flux scale

## Reproducibility

- Data public (paper): Project codes cited in acknowledgement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00815.S and #2015.1.00834.S." (Conclusion)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Channel selection for continuum
- Missing: Spectral extraction details and velocity ranges for fits
- Missing: CASA version
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Data public and main steps described, but imaging details missing.
- Rediscovery candidate: yes, Public data, numeric results from Gaussian fits and simple derived quantities; some imaging choices unstated.

## Links

- Companion: Willott et al. 2015 (cite: will15) (Cycle 2 ALMA observations of WMH5 combined here)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
