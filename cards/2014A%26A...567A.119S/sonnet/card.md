# ALMA-backed NIR high resolution integral field spectroscopy of the NUGA galaxy NGC 1433

`2014A&A...567A.119S` | Astronomy and Astrophysics 2014 | first author: Smajić, Semir | arXiv: 1404.6562 | DOI: 10.1051/0004-6361/201423642

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the excitation conditions, kinematics, stellar content and gas feeding/feedback in the central 500 pc of NGC 1433, using SINFONI NIR IFS compared with ALMA CO(3-2) and 0.87 mm data?  
  > "We investigate the central 500 pc of this nearby galaxy, concentrating on excitation conditions, morphology, and stellar content." (abstract)
- Target **NGC 1433**: coordinates RA 03h42m01.49s, Dec -47d13'20.2" (J2000, Combes et al. 2013 centre); new centre Dec -47d13'18.8"  
  > "at a redshift of $z\approx 0.003586$ (cite: koribalski_1000_2004)" (2.2 NGC 1433); "Distance | 9.9 Mpc (1$\ensuremath{''}=$ 48 pc) | \(1\)" (Table 1); z/distance z = 0.003586; 9.9 Mpc  
  > "at a redshift of $z\approx 0.003586$ (cite: koribalski_1000_2004)" (2.2 NGC 1433); "Distance | 9.9 Mpc (1$\ensuremath{''}=$ 48 pc) | \(1\)" (Table 1); distance from Combes et al. 2013 (distance); Koribalski et al. 2004 (redshift)  
  > "at a redshift of $z\approx 0.003586$ (cite: koribalski_1000_2004)" (2.2 NGC 1433); "Distance | 9.9 Mpc (1$\ensuremath{''}=$ 48 pc) | \(1\)" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00208.S
- bands: _not stated_
- frequencies and spectral setup: 350 GHz; 4 spectral windows (7 GHz line-free continuum); line cube of 72 channels of 5 km/s  
  > "The line cube comprises 72 channels of 5 km/s width, centered on the systemic velocity, i.e. $1076\pm180$ km s$^{-1}$." (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA cycle 0  
  > "observations carried out with ALMA in cycle 0" (footnote 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Other facility **VLT SINFONI**: H- and K-band integral field spectroscopy (main data)  
  > "In this paper we present the results of our ESO SINFONI observations of NGC 1433 with the Unit Telescope 4 of the Very Large Telescope in Chile." (Observation and Data Reduction)
- Other facility **HST**: optical images (F450W, F660W, F810W) for overlays and torque computation  
  > "HST images from F450W, F660W and F810W filters" (3.3 Continuum)
- Other facility **2MASS**: flux calibration of the standard star  
  > "to the flux given by the 2MASS All-sky Point Source Catalog" (Observation and Data Reduction)
- External data: Calibrated 350 GHz ALMA data of NGC 1433 (line cube, continuum)  
  > "we use calibrated 350 GHz ALMA data (cite: combes_ALMA_2013)" (Observation and Data Reduction) [from (cite: combes_ALMA_2013)]
- External data: Cold-to-warm H2 mass ratio (0.3-1.6)e6  
  > "The conversion factor detemined by (cite: mazzalay_molecular_2013)" (3.2.1 H2 mass estimation) [from (cite: mazzalay_molecular_2013)]
- External data: M-sigma relation for black hole mass  
  > "Following (cite: gultekin_m-\_2009)" (3.3 Continuum) [from (cite: gultekin_m-\_2009)]
- External data: Stellar templates for CO(2-0) bandhead fitting  
  > "Stellar templates from (cite: winge_gemini_2009) were used as input for the fitting routine." (3.3 Continuum) [from (cite: winge_gemini_2009)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: calibrated ALMA data taken from Combes et al. 2013  
  > "we use calibrated 350 GHz ALMA data (cite: combes_ALMA_2013)" (Observation and Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA imaging and cleaning  
  > "Imaging, cleaning and parts of the analysis have been conducted with the CASA software" (Observation and Data Reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "The map sizes are $720\times720$ pixels with a pixel size of 0$\ensuremath{''}$05." (Observation and Data Reduction)
- image size: 720x720 pixels  
  > "The map sizes are $720\times720$ pixels with a pixel size of 0$\ensuremath{''}$05." (Observation and Data Reduction)
- masking: clean masks at 50, 30 and 10 mJy emission levels  
  > "For cleaning we used a mask at 50mJy, 30 mJy and 10mJy emission level." (Observation and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to integrated intensity and continuum maps  
  > "were corrected for primary beam attenuation" (Observation and Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibrated ALMA data and outflow interpretation  
  > "we use calibrated 350 GHz ALMA data (cite: combes_ALMA_2013)" (Observation and Data Reduction) [from (cite: combes_ALMA_2013)]
- Continuum decomposition method  
  > "a decomposition as described in (cite: smajic_unveiling_2012) was used" (3.3 Continuum) [from (cite: smajic_unveiling_2012)]
- Fourier decomposition of the potential  
  > "The potential has been decomposed into its different Fourier components, as in (cite: combes_ALMA_2014)." (4.4 Computation of the torques) [from (cite: combes_ALMA_2014)]
- Torque computation  
  > "we derive the torques at each pixel, as described in (cite: garcia-burillo_molecular_2005)" (4.4 Computation of the torques) [from (cite: garcia-burillo_molecular_2005)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version, calibration and flux scale details (in Combes et al. 2013)
- Beam size, weighting/robust, rms and cleaning threshold of the ALMA images
- Line-free channels and continuum subtraction method
- ALMA array configuration and time on source
- CO-to-H2 conversion factor used for the CO(3-2) mass
- Details of the CO(3-2) mass derivation and the dynamical mass fits
- Code for IDL routines (not released)

## Analysis recipe

1. **Reduce SINFONI cubes and correct detector/OH problems**: SINFONI pipeline to single-exposure cubes, own IDL routines for detector pattern, OH correction, wavelength refinement  
  > "The data reduction was performed by the SINFONI pipeline up to single-exposure-cube reconstruction." (Observation and Data Reduction)
   - software: SINFONI pipeline, IDL
   - fitting: _not stated_
   - validation: _not stated_
2. **Image ALMA CO(3-2) and 0.87 mm continuum**: CASA cleaning with masks, primary beam correction, moment maps  
  > "Imaging, cleaning and parts of the analysis have been conducted with the CASA software" (Observation and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Align NIR and ALMA maps to fix nuclear position**: Overlay of H2(1-0)S(1) on CO(3-2) and HST maps, cross-correlation of emission spots  
  > "By shifting the CO maps with respect to the H$_2$ emission line map a cross-correlation of the strongest $^{12}$CO(3-2) emission spots" (4.1 The nucleus of NGC 1433)
   - fitting: _not stated_
   - validation: centre position error 0.2 arcsec  
  > "The error estimate of the center positioning, using the described method, turns out to be 0$\ensuremath{''}$2." (4.1 The nucleus of NGC 1433)
4. **Gaussian line fits, masses, SFR, SNR, M-sigma**: Gaussian line fitting, CO bandhead stellar fitting, M-sigma relation, H2 mass formula  
  > "The emission lines properties were determined from Gaussian profile fits." (3 Results)
   - software: IDL
   - assumption: galaxy lies on the M-sigma relation  
  > "assuming that NGC 1433 lies on the M-$\sigma$ relation" (3.3 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model central kinematics and compute gravity torques**: Simple disk/outflow/combined toy models convolved with PSF; HST F814W potential torques  
  > "three simple models for the central velocity gradients were derived" (4.2.1 A simple model approach)
   - parameter: M/L = 0.5 Msun/Lsun in I-band, i=33 deg, PA=199 deg  
  > "constant mass-to-light ratio of M/L = 0.5 M$_{\odot}$/L$_{\odot}$ in the I-band" (4.4 Computation of the torques)
   - fitting: _not stated_
   - validation: torque uncertainty about 20% from centre shifts of 0.2 arcsec  
  > "This resulted in an uncertainty on torques of about 20%." (4.4 Computation of the torques)

## Software

- **CASA** : ALMA imaging, cleaning and parts of analysis  
  > "Imaging, cleaning and parts of the analysis have been conducted with the CASA software" (Observation and Data Reduction)
- **SINFONI pipeline** 2.3.2: SINFONI data reduction  
  > "We used the SINFONI pipeline version 2.3.2 for data reduction, except for the OH correction." (Appendix)
- **IDL** : own routines for detector correction, OH, line maps, spectra  
  > "as well as the linemap and spectra extraction using our own IDL routines" (Observation and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Black hole mass from central sigma=100 km/s | 7e6 | not stated | Msun | 4 | we determine a black hole mass of M$_{\bullet}$ = 7 $\times$ 10$^6 M_{\odot}$ |
| Black hole mass from mean sigma 125 km/s | 1.8e7 | 0.8e7 | Msun | 4 | M$_{\bullet}=(1.8\pm0.8)\times10^7M_{\odot}$ |
| Warm H2 mass within 1 arcsec | 4.89 | not stated | Msun | 4 | A warm H$_2$ gas mass of 4.89 $M_{\odot}$ can be estimated at the central 1$\ensuremath{''}$ |
| H2 mass from CO(3-2), 1 arcsec radius | 2.1e5 | not stated | Msun | 4 | we estimate an H$_2$ gas mass of $2.1\times10^5 M_{\odot}$ for a 1$\ensuremath{''}$ radius |
| CO(3-2) line of nodes PA | 155 | not stated | deg | 5 | For $^{12}$CO(3-2) we measure a line of nodes PA of 155$\ensuremath{^\circ}$ |
| Central mass from H2 velocities | 7.3e6 | not stated | Msun | 5 | we determine a central mass to be $M_{cent}$ of 7.3 $\times$ 10$^{6} M_{\odot}$ |
| Upper limit SFR within 1 arcsec | 1.4e-3 | not stated | Msun/yr | 4 | upper limit for the SFR within a 1$\ensuremath{''}$ radius around the nucleus of $1.4 \times 10^{-3} M_{\odot}$yr$^{-1}$ |

## Qualitative findings

- Nuclear gradient in H2 and CO is consistent with an outflow, a small circumnuclear disk, or a combination; the new centre lies about 1.5 arcsec from the Combes et al. centre  
  > "propose three interpretations of the results: gaseous disk, molecular outflow or a combination of both" (Conclusion and summary)

## Claim tuples

- H: Where is the nucleus/SMBH of NGC 1433? | E: Aligned SINFONI H2 and stellar continuum with ALMA CO(3-2) and 0.87 mm maps | R: New centre about 1.5 arcsec from Combes et al. centre, error 0.2 arcsec | F: The outflow originates at the SMBH position | **supported**
- H: Does the nuclear bar drive gas inwards? | E: Gravity torques from HST I-band potential | R: Positive torque at R<200 pc, negative at R>200 pc | F: Gas accumulates at the 200 pc ring; other mechanisms needed further in | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Star formation as outflow driver rejected due to very low SFR  
  > "An outflow inferred from strong star formation in the center can be excluded due to a very low SFR." (Conclusion and summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk and outflow models cannot be distinguished at the available resolution  
  > "the convolved models of disk and outflow look very similar and cannot unambiguously be traced back to their underlying model" (4.2.1 A simple model approach)
- Caveat (inferred, ours): ALMA processing is minimally described and relies on a previous paper
- Caveat (inferred, ours): Alignment of NIR and ALMA maps is done by eye, with no formal fit
- Caveat (inferred, ours): Warm H2 mass of 4.89 Msun looks inconsistent with the quoted cold masses
- Caveat (inferred, ours): Toy models were tuned by hand without a fit

## Reproducibility

- Data public (paper): ALMA data acknowledged with project code; SINFONI from ESO proposal 090.B-0657(A)  
  > "Based on the ESO-VLT proposal ID: 090.B-0657(A)" (footnote 1)
- Products in archive: _not stated_
- Missing: IDL routines not released
- Missing: ALMA calibration details only in Combes et al. 2013
- Missing: imaging parameters beyond masks and pixel size
- Data volume (inferred): ALMA cycle 0 band 7 data of one target, a few GB; SINFONI cubes small
- Score (inferred): 2/5, The ALMA part is minor and thinly described; the SINFONI analysis relies on custom code.
- Rediscovery candidate: no, ALMA is secondary, the recipe is incomplete, and the main results are mostly from SINFONI.

## Links

- Method: (cite: smajic_unveiling_2012) (continuum decomposition)
- Method: (cite: garcia-burillo_molecular_2005) (torque computation)
- Companion: (cite: combes_ALMA_2013) (source of the ALMA data and outflow interpretation)
- Related: NUGA

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 77,
  "stated": 39,
  "rate": 0.506
 },
 "evidence_ok": true
}
```
