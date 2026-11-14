# The discovery of the most UV-Ly α luminous star-forming galaxy: a young, dust- and metal-poor starburst with QSO-like luminosities

`2020MNRAS.499L.105M` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Marques-Chaves, R. | arXiv: 2009.02177 | DOI: 10.1093/mnrasl/slaa160

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What is the nature of BOSS-EUVLG1, an extremely UV/Lya-luminous object at z=2.469: AGN, lensed galaxy, or intense dust-poor starburst?  
  > "is due to an intense burst of star-formation, and not to an AGN or gravitational lensing." (abstract)
- Target **BOSS-EUVLG1 (SDSS J122040.72+084238.1)**: coordinates (185.1697, 8.7106) deg J2000  
  > "located at ($\alpha$, $\delta )_{\rm J2000} = (185.1697^{\circ},8.7106^{\circ}$) with a redshift $z$=2.469" (Introduction); "The systemic redshift $z$=2.4694$\pm$0.0004 is measured from the C iii\] doublet." (Discovery and Follow-up Observations); z/distance z=2.4694±0.0004  
  > "located at ($\alpha$, $\delta )_{\rm J2000} = (185.1697^{\circ},8.7106^{\circ}$) with a redshift $z$=2.469" (Introduction); "The systemic redshift $z$=2.4694$\pm$0.0004 is measured from the C iii\] doublet." (Discovery and Follow-up Observations); distance from C III] doublet in BOSS spectrum  
  > "located at ($\alpha$, $\delta )_{\rm J2000} = (185.1697^{\circ},8.7106^{\circ}$) with a redshift $z$=2.469" (Introduction); "The systemic redshift $z$=2.4694$\pm$0.0004 is measured from the C iii\] doublet." (Discovery and Follow-up Observations)

## Data provenance

- ALMA projects: 2018.1.00932.S
- bands: Band 6 (1.2 mm)  
  > "3$\sigma$ limit of 37 $\mu$Jy at 1.2mm (Band 6)" (Results and Discussion)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.62" x 0.61" beam  
  > "(beam size of $0.62^{\prime \prime} \times 0.61^{\prime \prime}$)" (Discovery and Follow-up Observations)
- max recoverable scale: _not stated_
- sensitivity: 3σ limit 37 μJy  
  > "not detected with a $3\sigma$ limit of 37$\mu$Jy" (Discovery and Follow-up Observations)
- time on source: 5.6 min  
  > "with a total on source time of 5.6 min" (Discovery and Follow-up Observations)
- observing dates: _not stated_
- pi or archival as stated: PI: R. Marques-Chaves  
  > "PI: R. Marques-Chaves" (Discovery and Follow-up Observations)
- Other facility **GTC OSIRIS/EMIR**: Optical and near-IR spectroscopy and near-IR imaging  
  > "Optical and near-IR long-slit spectroscopy were obtained with the Gran Telescopio Canarias (GTC) OSIRIS and EMIR instruments" (Discovery and Follow-up Observations)
- Other facility **SDSS/BOSS**: Discovery spectrum  
  > "Its BOSS spectrum (plate-mjd-fiberid: 5397-55944-626)" (Discovery and Follow-up Observations)
- Other facility **CFHT**: Archival U-Z optical images  
  > "We also used archival Canada France-Hawaii Telescope (CFHT) optical images in $U$ to $Z$ bands" (Discovery and Follow-up Observations)
- Other facility **NEOWISE**: Mid-IR W1, W2 photometry  
  > "detected in the mid-IR in the sixth year NEOWISE 2020 data release" (Discovery and Follow-up Observations)
- External data: Far-IR SED of ALESS galaxies (Tdust ~43 K) used to convert the limit to LIR and Mdust  
  > "Using the far-IR SED of ALESS galaxies ($T_{\rm dust} \simeq 43 K$; (cite: dacunha2015))" (Results and Discussion) [from (cite: dacunha2015)]
- External data: Supernova dust yield predictions for the expected dust mass  
  > "formed by supernovae ((cite: gall2018), assuming no dust destruction)" (Results and Discussion) [from (cite: gall2018)]

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

### Not stated but needed to reproduce (our reading)

- Calibrators and pipeline/manual calibration details
- Array configuration and spectral setup
- Imaging parameters (weighting, cell size, continuum bandwidth)
- How the 3σ limit was computed (rms, aperture)
- Exact conversion from flux limit to LIR and Mdust (dust opacity, beta, CMB correction)

## Analysis recipe

1. **ALMA dust continuum upper limit**: Reduce data in CASA and measure 1.2 mm continuum; no detection, 3σ limit  
  > "Data reduction was performed using version 5.4.0 of the Common Astronomy Software Applications (casa) package." (Discovery and Follow-up Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert limit to LIR and Mdust**: Scale far-IR SED template of ALESS galaxies to the flux limit  
  > "this limit yields to an integrated far-IR luminosity log($L_{\rm IR} / L_{\odot}) < 10.91$ (from $8-1000 \mu$m)" (Results and Discussion)
   - assumption: Tdust ~43 K from ALESS SED  
  > "$T_{\rm dust} \simeq 43 K$" (Results and Discussion)
   - fitting: _not stated_
   - validation: Compared with SN dust production expected over 10 Myr  
  > "still compatible with the non-detection of ALMA dust continuum" (Results and Discussion)

## Software

- **CASA** 5.4.0: ALMA data reduction  
  > "Data reduction was performed using version 5.4.0 of the Common Astronomy Software Applications (casa) package." (Discovery and Follow-up Observations)
- **CIGALE** : SED fitting  
  > "We perform SED-fitting with CIGALE (cite: Boquien2019)" (Results and Discussion)
- **Starburst99** : Stellar wind profile modelling for age and metallicity  
  > "spectral synthesis code Starburst99 (cite: leitherer1999)" (Results and Discussion)
- **Galfit** : Sersic fit of CFHT I-band morphology  
  > "Using the CFHT $I$-band (seeing $\simeq 0.55^{\prime \prime}$ FWHM) and Galfit (cite: peng2002)" (Results and Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.2 mm 3σ upper limit | 37 | not stated | μJy | 1 | not detected with a $3\sigma$ limit of 37$\mu$Jy |
| log(LIR/Lsun) | <10.91 | not stated | dex | 2 | log($L_{\rm IR} / L_{\odot}) < 10.91$ |
| Mdust | <1.9e7 | 3σ | Msun | 2 | $M_{\rm dust} / M_{\odot} < 1.9\times 10^{7}$ ($3\sigma$) |
| log(LIR/LUV) | <-1.2 | not stated | dimensionless | 2 | implying a log($L_{\rm IR}$/$L_{\rm UV}) < -1.2$ |

## Qualitative findings


## Claim tuples

- H: Is the extreme luminosity due to a dusty or an un-obscured young starburst? | E: ALMA 1.2 mm continuum observation | R: No detection at 3σ limit of 37 μJy; LIR/LUV < -1.2 | F: The galaxy is dust-poor, consistent with a very young burst | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Upper limit depends on the assumed Tdust of 43 K; a hotter dust would raise the limits
- Caveat (inferred, ours): Only 5.6 min of ALMA data, so the limit is shallow

## Reproducibility

- Data public (paper): Data shared on reasonable request  
  > "The data underlying this article will be shared on reasonable request to the corresponding author." (Data availability)
- Products in archive: _not stated_
- Missing: ALMA calibration and imaging details
- Missing: Conversion recipe from flux limit to LIR and Mdust
- Data volume (inferred): A few GB (single short Band 6 continuum execution)
- Score (inferred): 3/5, Simple ALMA limit, but the recipe details are sparse.
- Rediscovery candidate: no, The ALMA recipe is incomplete and the main results come from optical/NIR data.

## Links

- Companion: Marques-Chaves et al. in prep. (Sample and selection of the ~70 EUVLGs)
- Related: BOSS-EUVLG
- Related: eBOSS

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 24,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
