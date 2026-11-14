# The most distant, luminous, dusty star-forming galaxies: redshifts from NOEMA and ALMA spectral scans

`2017MNRAS.472.2028F` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Fudamoto, Y. | arXiv: 1707.08967 | DOI: 10.1093/mnras/stx1956

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Determine robust spectroscopic redshifts of ultrared Herschel-selected DSFGs via 3-mm spectral scans, and derive their physical properties (SFR, gas and dust mass, depletion time)  
  > "Our primary objective here is to determine robust spectroscopic redshifts for these DSFGs, via the detection of multiple molecular and/or atomic emission lines." (Introduction)
- Target **21 ultrared H-ATLAS DSFGs (e.g. SGP-196076, G09-83808, NGP-190387)**: coordinates Table 2 lists J2000 positions (e.g. G09-83808 09:00:45.79 +00:41:22.9); not available for G15-26675, G15-82684, NGP-63663  
  > "G09-83808$^{\rm a,b}$                | 09:00:45.79 |  +00:41:22.9" (Table 2); "| G09-83808$^{\rm a,b}$                | 09:00:45.79 |  +00:41:22.9  |" (Table 2); z/distance z_spec 3.847-6.027 for 8 galaxies; z_phot 3.08-5.66 for the rest  
  > "G09-83808$^{\rm a,b}$                | 09:00:45.79 |  +00:41:22.9" (Table 2); "| G09-83808 | $9.7\pm5.4$ | $24.6\pm 7.9$ | $44.0\pm 8.2$ | $36.2\pm9.1$ | $19.4\pm 2.0$ | $0.66\pm 0.12$ | $5.66^{+0.06}_{-0.74}$ | $6.027\pm 0.001$ | (cite: zavala17) |" (Table 1 (flux densities and redshifts)); distance from CO line detections in this work; photometric redshifts from Ivison et al. 2016  
  > "G09-83808$^{\rm a,b}$                | 09:00:45.79 |  +00:41:22.9" (Table 2); "Photometric redshift estimated by template SED fits to 250-, 350-, 500-, and 850- or 870-$\mu$m flux densities (cite: ivison16)." (Table 1 footnote b)

## Data provenance

- ALMA projects: 2013.1.00499.S
- bands: 3 mm spectral scans (NOEMA and ALMA); NOEMA 1.3 mm continuum  
  > "Four ultrared galaxies were observed using ALMA (see Table 1), with five separate tunings to cover the 3-mm window" (3.2 ALMA 3-mm spectral scans)
- frequencies and spectral setup: NOEMA WideX, 3.6 GHz per tuning, covering 80-101.6 GHz; ALMA five tunings  
  > "together with the WideX correlator – which provides 3.6 GHz of instantaneous dual-polarization bandwidth – to cover the 80–101.6-GHz part of the 3-mm atmospheric window" (3.1 NOEMA 3-mm spectral scans)
- continuum bandwidth: _not stated_
- arrays: NOEMA five or six antennas, compact D configuration; ALMA  
  > "Both projects acquired data using five or six antennas in NOEMA’s most compact (D) configuration." (3.1 NOEMA 3-mm spectral scans)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: NOEMA 3 mm ~5 arcsec; ALMA 0.6-1.2 arcsec; NOEMA 1.3 mm ~1.5 arcsec  
  > "the resulting synthesized beamsizes varied between 0.6 and 1.2$''$ fwhm." (3.2 ALMA 3-mm spectral scans)
- max recoverable scale: _not stated_
- sensitivity: NOEMA 2.7 and 1.1 mJy/beam; ALMA 0.73-0.80 mJy/beam in 100 km/s channels  
  > "The resulting r.m.s. noise levels ranged between 0.73 and 0.80 mJy beam$^{-1}$ in channels binned to 100 km s$^{-1}$." (3.2 ALMA 3-mm spectral scans)
- time on source: ALMA typically 8.6-9.7 min per tuning  
  > "with typically 8.6–9.7 min spent on-source for each tuning" (3.2 ALMA 3-mm spectral scans)
- observing dates: ALMA 2014 July 02-03 and August 28  
  > "Data were acquired during 2014 July 02–03 and August 28" (3.2 ALMA 3-mm spectral scans)
- pi or archival as stated: _not stated_
- Line: 12CO J=4-3 to 7-6 (not stated)
- Other facility **NOEMA**: 3-mm spectral scans of 17 targets and 1.3-mm continuum  
  > "We observed 17 of these galaxies with NOEMA and four with ALMA, scanning through the 3-mm atmospheric window." (abstract)
- Other facility **SCUBA-2/JCMT**: 850 um imaging used to localize emission  
  > "overlaying the 3-mm continuum images with contours from the deep SCUBA-2 850-$\mu$m imaging of (cite: ivison16)" (4.1 Continuum emission)
- External data: SPIRE, SCUBA-2 flux densities and photometric redshifts  
  > "The SPIRE flux densities and photometric redshifts determined by (cite: ivison16) are listed in Table" (2 Sample selection) [from (cite: ivison16)]
- External data: Average CO line ratios for SMGs  
  > "$L^{\prime}_{\text{CO(7-6)}}/L^{\prime}_{\text{CO(1-0)}} = 0.18$" (4.6 Molecular gas masses) [from (cite: bothwell13)]
- External data: Lens magnification of G09-83808 (8.2±0.3)  
  > "predicts a gravitional amplification of $8.2\pm 0.3$ (cite: oteo17morph)" (4.3 Unambiguous redshifts) [from (cite: oteo17morph)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline for ALMA; gildas for NOEMA  
  > "Data were calibrated using the ALMA pipeline, with only minor flagging required." (3.2 ALMA 3-mm spectral scans)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (ALMA)  
  > "pointing, phase, flux density (Neptune) and bandpass" (3.2 ALMA 3-mm spectral scans)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Calibrated data were imaged using clean within casa, using the natural weighting scheme to maximize sensitivity." (3.2 ALMA 3-mm spectral scans)
- deconvolver: _not stated_
- weighting robust: natural weighting (ALMA)  
  > "using the natural weighting scheme to maximize sensitivity" (3.2 ALMA 3-mm spectral scans)
- uv taper: _not stated_
- cell size: _not stated_
- image size: 1'x1' map  
  > "with a map size of $1^{\prime}\times 1^{\prime}$" (3.2 ALMA 3-mm spectral scans)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB using all channels except near lines  
  > "Continuum emission was subtracted with the UVCONTSUB task in casa, using all available channels except those close to emission lines." (4.2 Searching for emission lines)
- line free channels: _not stated_
- primary beam correction: continuum flux densities corrected for primary beam attenuation  
  > "corrected for primary beam attenuation" (4.1 Continuum emission)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Sample selection method  
  > "we briefly summarize the selection method used, referring readers to (cite: ivison16) for more details." (2 Sample selection) [from (cite: ivison16)]
- SED template fits repeated as in earlier work  
  > "it is worth repeating the SED fits performed by (cite: ivison16)" (4.5 Spectral energy distributions) [from (cite: ivison16)]
- Rest-frame stacking approach  
  > "following (cite: spilker15) and (cite: zhang17)" (4.4 Rest-frame stacking) [from (cite: spilker15); (cite: zhang17)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (cell size, threshold, masks, robust for NOEMA)
- ALMA pipeline and CASA versions
- Line-free channels used for continuum subtraction
- Stacking weights and procedure details
- IR luminosity integration and chi2 fitting details
- Gildas calibrators for NOEMA

## Analysis recipe

1. **Measure continuum and positions**: Integrate over all frequencies, image with clean, make SNR maps, overlay SCUBA-2 contours  
  > "we integrated our data over all observed frequencies, imaging with the clean task in casa" (3.1 NOEMA 3-mm spectral scans)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with SCUBA-2 850 um positions  
  > "We then searched for faint 3-mm continuum sources coincident with SCUBA-2 850-$\mu$m emission, finding eight plausible sites." (4.1 Continuum emission)
2. **Search and fit emission lines**: Extract spectra at continuum positions; blind search with box-car convolved cubes (3, 4, 7 channels) for >5 sigma peaks; Gaussian fits; IMFIT on moment-0 maps  
  > "We convolved these data cubes along their frequency axis with box-car kernels of width 3, 4 and 7 channels" (4.2 Searching for emission lines)
   - software: CASA
   - fitting: single-component Gaussians  
  > "we have fitted single-component Gaussians, measuring the frequency of the line center, and its fwhm." (4.2 Searching for emission lines)
   - validation: _not stated_
3. **SED and modified blackbody fits**: Template SED fits and optically thin single-T MBB fits by chi2 minimisation at known z  
  > "we have performed SED fits using modified blackbody (MBB) spectra, again by minimizing $\chi^2$." (4.5.1 Modified blackbody fits)
   - assumption: nu_c = 1.5 THz, kappa_850 = 0.15 m^2/kg, beta fixed 1.5/2.0/2.5  
  > "We fixed $\nu_{\rm c}$ to 1.5 THz (cite: conley11; rangwala11) and adopted $\kappa_{850\,{\rm \mu m}} = 0.15\,{\rm m^2\,kg^{-1}}$" (4.5.1 Modified blackbody fits)
   - fitting: chi2 minimisation  
  > "To better quantify the thermal dust emission we have performed SED fits using modified blackbody (MBB) spectra, again by minimizing $\chi^2$." (Modified blackbody fits)
   - validation: _not stated_
4. **Derive SFR and molecular gas masses**: SFR from L_IR; gas mass from average L'CO(1-0) inferred from high-J lines with Bothwell ratios and alpha_CO  
  > "calculated the molecular gas masses using $\alpha_{\rm CO}=0.8\,{\rm M_{\odot}\,(K\,km\,s^{-1}\,pc^{2})^{-1}}$" (4.6 Molecular gas masses)
   - assumption: alpha_CO = 0.8, Salpeter IMF, SFR = L_IR/2.21e43  
  > "${\rm SFR}=L_{\rm IR}/2.21\times10^{43}\,{\rm M_{\odot}\,yr^{-1}}$" (Table 6)
   - fitting: _not stated_
   - validation: L_IR-L'CO from different transitions consistent  
  > "We find that $L_{\rm IR}-L^{\prime}_{\rm CO}$ as derived from different – usually neighbouring – transitions are consistent." (4.6 Molecular gas masses)

## Software

- **CASA** : imaging, UVCONTSUB, IMFIT  
  > "to be imaged by casa (cite: mcmullin07)" (3.1 NOEMA 3-mm spectral scans)
- **GILDAS** : NOEMA calibration  
  > "Calibration of the data was carried out by using the gildas package" (3.1 NOEMA 3-mm spectral scans)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| z of G09-83808 | 6.027 | 0.001 | dimensionless | 2 | so an average of $6.027\pm0.001$ |
| Slope of L_IR-L'CO | 1.14 | 0.02 | dimensionless | 4 | slope close to unity, $1.14\pm0.02$ |
| Average SFR of confirmed sample | 2900 | not stated | Msun/yr | 4 | with an average SFR of $\approx 2900$ M$_{\odot}$ yr$^{-1}$ |
| Gas depletion timescale | ~50 | not stated | Myr | 4 | is around 50 Myr |

## Qualitative findings

- Non-detections are 0.3-0.4 dex less luminous in the far-IR than line-detected galaxies  
  > "the galaxies are generally less luminous by 0.3–0.4 dex" (abstract)

## Claim tuples

- H: Ultrared DSFGs lie at z>~4 and can be confirmed with 3-mm scans | E: NOEMA and ALMA 3-mm scans of 21 galaxies | R: Multiple lines in seven galaxies (z=3.85-6.03); single lines in four more | F: Secure redshifts for a third of the sample; others need follow-up | **partially**
- H: The galaxies are progenitors of red-and-dead ellipticals | E: Gas depletion time from gas mass and SFR | R: t_depl ~50 Myr | F: They consume gas rapidly, consistent with being progenitors | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO and high-J CO assumptions make gas masses uncertain; alpha_CO~3 would give ~3.5x higher masses  
  > "we arrive at a value $\sim 3.5\times$ higher, the equivalent of $\alpha_{\rm CO}\approx 3$" (4.7 L_IR-L'CO correlation)
- Caveat (inferred, ours): Gas masses rely on assumed CO ratios and low alpha_CO
- Caveat (inferred, ours): Lensing magnifications unknown for most
- Caveat (inferred, ours): Single-line redshifts ambiguous

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; NOEMA programs listed  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00499.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Detailed imaging parameters
- Missing: NOEMA data access
- Missing: Stacking details
- Data volume (inferred): ~50-100 GB for ALMA (4 sources, 5 tunings); NOEMA data separate
- Score (inferred): 4/5, ALMA data public and steps described qualitatively, but imaging and fitting parameters sparse and NOEMA data needed.
- Rediscovery candidate: no, Recipe incomplete and most of the data come from NOEMA.

## Links

- Method: (cite: ivison16) (Sample selection and photometric redshift method)
- Companion: (cite: oteo17morph) (High-resolution ALMA imaging of the sample)
- Companion: (cite: oteo17grh) (Follow-up of SGP-354388)
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00499.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00449.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 41,
  "rate": 0.594
 },
 "evidence_ok": true
}
```
