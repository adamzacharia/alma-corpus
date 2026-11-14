# An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: halo masses for submillimetre galaxies

`2021MNRAS.504..172S` | Monthly Notices of the Royal Astronomical Society 2021 | first author: Stach, S. M. | arXiv: 2102.12510 | DOI: 10.1093/mnras/stab714

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the clustering strength and dark matter halo masses of ALMA-identified SMGs at z=1.5-3, and do they evolve with redshift?  
  > "We measure the projected cross-correlation function of $\sim$ 350 SMGs in the UKIDSS Ultra Deep-Survey Field across a redshift range of $z$ $=$ 1.5–3" (abstract)
- Target **AS2UDS SMGs in the UKIDSS UDS field**: coordinates _not stated_; z/distance z = 1.5–3.0 (median z=2.61±0.08)  
  > "we use as a basis the 707 SMGs in the catalogue from (cite: stach2019alma)’s AS2UDS ALMA survey" (2.1 Sample Selection); distance from MAGPHYS photometric redshifts from Dudzeviciute et al. 2020  
  > "we use as a basis the 707 SMGs in the catalogue from (cite: stach2019alma)’s AS2UDS ALMA survey" (2.1 Sample Selection)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (870 um) continuum  
  > "The AS2UDS survey obtained ALMA Band 7 (870$\mu$m) continuum observations of all $>$ 4-$\sigma$ sources from the S2CLS SCUBA-2 850-$\mu$m map" (2.1 Sample Selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.3 arcsec (maps uv-tapered to 0.5 arcsec for detection)  
  > "we now have robust ALMA interferometric identifications, at 870 $\mu$m and $\sim$ 0.3$''$ resolution" (2.1 Sample Selection)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **SCUBA-2 (S2CLS)**: 850 um parent map  
  > "The S2CLS UDS map reached a median sensitivity of $\sigma_{850}$ $=$ 0.9 mJy over an area of 0.96 deg$^2$" (Introduction)
- Other facility **UKIDSS UDS DR11**: K-band galaxy catalogue for cross-correlation  
  > "The DR11 catalogue contains 296,007 sources extracted from the $K$-band image with a median 5-$\sigma$ depth of $K$ $=$ 25.3 mag" (2.3 K-band Galaxies)
- External data: AS2UDS SMG catalogue (707 SMGs)  
  > "we use as a basis the 707 SMGs in the catalogue from (cite: stach2019alma)’s AS2UDS ALMA survey" (2.1 Sample Selection) [from (cite: stach2019alma)]
- External data: MAGPHYS photometric redshift PDFs and stellar masses  
  > "Photometric redshifts and other physical parameters (as well as their associated probability density functions) were estimated by (cite: dudzevivciute2020alma)" (2.2 Photometric Redshifts) [from (cite: dudzevivciute2020alma)]

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

- ALMA data reduction, source catalogue and photometric redshifts taken from earlier AS2UDS papers  
  > "The properties of the ALMA source catalogue from the AS2UDS survey are described in (cite: stach2018alma; stach2019alma)." (2.1 Sample Selection) [from (cite: stach2018alma; stach2019alma; dudzevivciute2020alma)]
- Cross-correlation method  
  > "Our clustering analysis employs a similar cross-correlation method as used by (cite: hickox2012laboca)." (2.1 Sample Selection) [from (cite: hickox2012laboca)]

### Not stated but needed to reproduce (our reading)

- Exact r_p bin number/edges and random-selection seeds
- K-band catalogue (Almaini et al. in prep.) availability
- HALOMOD code is unpublished (Murray et al. in prep.)
- Redshift matching procedure details for galaxy subsampling

## Analysis recipe

1. **Build SMG, galaxy and random catalogues**: Mask regions, mass-limit K-band galaxies (>10^9.1 Msun), match redshift distribution to SMGs, randoms at ~10x density with redshifts sampled from PDFs  
  > "We therefore apply a uniform 90 per cent mass completeness limit for our $z$ $=$ 1.5–3 comparison galaxies of $M_{\rm lim}$\>$10^{9.1}$ M$_{\odot}$ to all redshift bins" (2.3 K-band Galaxies)
   - fitting: _not stated_
   - validation: _not stated_
2. **Projected SMG-galaxy cross-correlation**: Landy-Szalay estimator with Monte Carlo sampling of redshift PDFs; power-law fit with gamma=1.8 above 0.5 h^-1 Mpc  
  > "resulting 3,000 redshift-sampling iterations" (2.4 Projected Cross-Correlations)
   - parameter: pi_max = 100 h^-1 Mpc; r_p bins 0.05–14 h^-1 Mpc  
  > "For this work we chose a value of $\pi_{max}$ $=$ 100 $h^{-1}$ Mpc" (2.4 Projected Cross-Correlations)
   - assumption: gamma fixed to 1.8  
  > "we choose to fix $\gamma$ $=$ 1.8" (2.4 Projected Cross-Correlations)
   - fitting: Maximum likelihood, single-parameter power law  
  > "using a maximum likelihood estimator with a single parameter, power-law model" (3 Results and Discussion)
   - validation: pi_max=400 test gave ~10% change in r0; Gaussian PDF width tests  
  > "showing only an $\sim$ 10 per cent increase in $r_0$ from $\pi_{max}$ $=$ 100 Mpc h$^{-1}$" (2.4 Projected Cross-Correlations)
3. **Galaxy auto-correlation and bias**: Angular auto-correlation with jackknife errors, Limber deprojection, HaloFit dark matter, Tinker bias function to halo mass  
  > "We convert the absolute bias into a dark matter halo mass by assuming a (cite: tinker2010large) bias function." (2.6 Deriving dark matter halo masses)
   - software: HaloFit, HALOMOD
   - assumption: Planck XIII cosmology, sigma8=0.816  
  > "we assume a *Planck* XIII cosmology with $\Omega_{\rm m}$ $=$ 0.307, H$_{0}$ $=$ 69.3 km s$^{-1}$ Mpc$^{-1}$" (Introduction)
   - fitting: _not stated_
   - validation: Integral constraint correction IC=2.0 h^-1 Mpc  
  > "We find a final integral constraint correction for our field of $\rm{IC}$ $=$ 2.0 $h^{-1}$ Mpc" (2.7 Integral Constraint)

## Software

- **HaloFit** : non-linear dark matter power spectrum  
  > "we use the HaloFit code (cite: smith2003stable), with the updated Halofit fitting parameters from (cite: takahashi2012revising)" (2.6 Deriving dark matter halo masses)
- **HALOMOD** : project power spectrum to angular dark matter correlation  
  > "We use the HALOMOD code (Murray et al. in prep.)" (2.6 Deriving dark matter halo masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMG correlation length r0, z=1.5–3 | 6.6 | +1.9/-1.9 | h^-1 Mpc | 2 | we find an SMG correlation length of $r_0$ $=$ 6.6$^{+1.9}_{-1.9}$ $h^{-1}$ Mpc |
| Absolute SMG bias, full sample | 4.1 | ±0.7 | dimensionless | 3 | we estimate the absolute bias for our ‘full’ sample finding $b_s$ $=$ 4.1$\pm$0.7 |
| log10 halo mass, z=1.5–3 | 12.6 | +0.3/-0.4 | log10(h^-1 Msun) | 3 | $\log_{10}(M_{\rm halo}[{h^{-1}\,\rm M_{\odot}}])$ $=$ 12.6$^{+0.3}_{-0.4}$ |
| Present-day halo mass | ~13.2 | not stated | log10(h^-1 Msun) | 3 | $\log_{10}(M_{\rm halo}[{h^{-1}\,\rm M_{\odot}}])$ $\sim$ 13.2 at $z$ $\sim$ 0 |

## Qualitative findings

- No significant halo mass evolution across z=1.5–3  
  > "no significant evolution in the dark matter halo masses with redshift" (Conclusions)

## Claim tuples

- H: SMG halo masses evolve with redshift | E: Cross-correlation in three redshift bins | R: r0 ~6–7 h^-1 Mpc, log Mhalo ~12.6–12.8 in all bins | F: No evolution; earlier claims likely due to misidentification | **supported**
- H: SMGs are progenitors of local spheroids | E: Evolve halo masses with median growth rates | R: log Mhalo ~13.2 at z~0 | F: Consistent with evolution into massive passive spheroids | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Large uncertainties due to sample size and PDF widths  
  > "although they are consistent within the relatively large uncertainties" (3.2 Clustering evolution with redshift)
- Caveat (inferred, ours): Photometric redshift PDFs dominate the uncertainty
- Caveat (inferred, ours): Blending bias only tested via a flux cut

## Reproducibility

- Data public (paper): Data in JCMT, ALMA and ESO archives  
  > "The data underlying this article are available in the JCMT, ALMA and ESO archives." (Data Availability)
- Products in archive: _not stated_
- Missing: Catalogues with photometric-redshift PDFs and K-band DR11 catalogue
- Missing: HALOMOD code
- Data volume (inferred): Catalogue-level analysis; ALMA raw data not reprocessed
- Score (inferred): 3/5, Catalogue-based method well described but depends on unreleased catalogues and code.
- Rediscovery candidate: no, Requires unpublished K-band catalogue and PDFs; ALMA data themselves are not reanalysed.

## Links

- Method: (cite: hickox2012laboca) (cross-correlation method followed)
- Method: (cite: stach2019alma) (AS2UDS catalogue)
- Companion: (cite: dudzevivciute2020alma) (photometric redshifts and stellar masses)
- Related: AS2UDS
- Related: S2CLS
- Related: UKIDSS UDS

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01528.S",
  "2016.1.00434.S",
  "2017.1.01492.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 25,
  "rate": 0.385
 },
 "evidence_ok": true
}
```
