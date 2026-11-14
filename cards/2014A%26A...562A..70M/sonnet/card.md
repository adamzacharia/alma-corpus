# Spatially-resolved dust properties of the GRB 980425 host galaxy

`2014A&A...562A..70M` | Astronomy and Astrophysics 2014 | first author: Michałowski, M. J. | arXiv: 1311.6466 | DOI: 10.1051/0004-6361/201322843

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the spatially resolved dust properties of the closest GRB host (GRB 980425 host, ESO 184-G82) and the contribution of its Wolf-Rayet region?  
  > "The objective of this paper is to change this situation by determining the dust properties in this closest known GRB host." (1. Introduction)
- Target **GRB 980425 host galaxy (ESO 184-G82) and its WR region**: coordinates _not stated_; z/distance z = 0.0085; 36.5 Mpc  
  > "GRB 980425 at z = 0.0085 is at a luminosity distance of 36.5 Mpc and 1 [′′] corresponds to 175 pc at its redshift" (1. Introduction); distance from redshift with H0 = 70 km/s/Mpc, OmegaL = 0.7, Omegam = 0.3  
  > "GRB 980425 at z = 0.0085 is at a luminosity distance of 36.5 Mpc and 1 [′′] corresponds to 175 pc at its redshift" (1. Introduction)

## Data provenance

- ALMA projects: 2011.0.00046.S
- bands: Band 3  
  > "We performed Band 3 ALMA observations on 1 Sep 2012" (2. Data)
- frequencies and spectral setup: Four 1.875 GHz spectral windows centred at 100.6, 102.4, 112.5, and 114.3 GHz  
  > "Four 1.875 GHz spectral windows were centred at 100.6, 102.4, 112.5, and 114.3 GHz." (2. Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 24 to 384 m, 23 antennas  
  > "Twenty three antennas and baselines ranging between 24 and 384 m were available." (2. Data)
- angular resolution: 1.9x1.8 arcsec  
  > "2790.5 < 0.43 0.123±0.025  - 29 1.9×1.8 ALMA" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 67.4 min  
  > "A total of 67.4 min of on-source data were obtained." (2. Data)
- observing dates: 1 Sep 2012  
  > "We performed Band 3 ALMA observations on 1 Sep 2012" (2. Data)
- pi or archival as stated: _not stated_
- Other facility **Herschel PACS/SPIRE**: 100-500 um photometry  
  > "We obtained Herschel observations of the GRB 980425 host (project no. OT1 lhunt 2, PI: L. Hunt) using the Photodetector Array Camera and Spectrometer" (2. Data)
- Other facility **APEX/LABOCA**: 870 um photometry  
  > "We also performed submillimetre (870 µm) observations of the GRB 980425 host on 4–5 Aug 2007" (2. Data)
- Other facility **ATCA**: radio 1.3-2.9 GHz photometry  
  > "We performed radio 2.1 GHz observations with the Australia Telescope Compact Array (ATCA) on 12 Apr 2012" (2. Data)
- Other facility **Swift UVOT and WISE**: UV and mid-IR photometry  
  > "We also obtained Ultraviolet/Optical Telescope (UVOT; Roming et al. 2005) data from the Swift" (2. Data)
- External data: UV-to-radio SED compilation of the host  
  > "we also used the compilation of the data presented in Micha�lowski et al. (2009, their Table 1) covering ultraviolet (UV) to radio wavelengths" (2. Data) [from Micha�lowski et al. (2009)]
- External data: Halpha flux of WR region for free-free estimate  
  > "using the Hα flux measured by Christensen et al. (2008) corrected for Galactic extinction" (3. SED fitting) [from Christensen et al. (2008)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (flux), J1733-130 (bandpass), J1945-552 (phase)  
  > "Neptune, J1733-130, and J1945-552 were used as flux, bandpass, and phase calibrators, respectively." (2. Data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting, multifrequency synthesis  
  > "The map was created by multifrequency synthesis with ‘natural’ weighting, giving the best signal-to-noise ratio." (2. Data)
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

- CASA version and calibration procedure
- clean threshold, cell and image size
- ALMA flux scale uncertainty
- aperture-flux handling of non-detection of the whole host (2σ limit derivation)
- Magphys priors/settings details

## Analysis recipe

1. **measure ALMA 2.8 mm fluxes**: Gaussian fit at WR region position; 50 arcsec diameter aperture for whole galaxy  
  > "We measured its flux by fitting a Gaussian at its position, whereas the flux for the entire galaxy was again measured in the 50 [′′] diameter aperture." (2. Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **remove free-free emission at 2.8 mm**: estimate free-free from Halpha flux; subtract from ALMA flux  
  > "The estimated free-free flux at 2.8 mm is 0.054 mJy, ∼45% of the total observed WR flux." (3. SED fitting)
   - fitting: _not stated_
   - validation: _not stated_
3. **SED modelling of host and WR region**: Magphys and Grasil fits to UV-radio photometry  
  > "We also used Magphys [8] (Multi-wavelength Analysis of Galaxy Physical Properties; da Cunha et al. 2008), an empirical but physically-motived SED model" (3. SED fitting)
   - software: Magphys, Grasil
   - assumption: Bruzual & Charlot (2003) stellar models, Chabrier IMF, kappa(850um)=0.77 cm2/g  
  > "We used the Bruzual & Charlot (2003) stellar models and adopted the Chabrier (2003) initial mass function (IMF)." (3. SED fitting)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data reduction and analysis  
  > "The data reduction and analysis were done using the Casa package" (2. Data)
- **Magphys** : SED fitting  
  > "We also used Magphys" (3. SED fitting)
- **Grasil** : SED templates  
  > "all developed in Grasil" (3. SED fitting)
- **Miriad** : ATCA and LABOCA analysis  
  > "The data reduction and analysis were done using Miriad." (2. Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 2.8 mm flux of WR region | 0.123 | 0.025 | mJy | 1 | 2790.5 < 0.43 0.123±0.025  - 29 1.9×1.8 ALMA |
| Free-free-subtracted WR 2.8 mm flux | 0.069 | 0.028 | mJy | 2 | 2790.5  - · · 0.069 [a] ±0.028  - · · 1.9×1.8 ALMA |
| WR contribution to dust mass of host | ~5 | not stated | % | 3 | we found that it contributes only ∼ 5% to the dust mass of the host |
| Dust mass (Bianchi 2013 method) | 6.57 | 0.05 | log(Md/Msun) | 3 | log(M d /M ⊙ ) = 6.57 ± 0.05 |

## Qualitative findings

- Host has low dust content and high fraction of UV-visible star formation, similar to dwarf galaxies  
  > "The host is characterised by low dust content and a high fraction of UV-visible star formation, similar to other dwarf galaxies." (abstract)

## Claim tuples

- H: Is the host a typical star-forming dwarf? | E: SED modelling and flux-ratio comparison with local samples | R: low 100um/NUV ratio, Md/M* consistent with dwarfs | F: host resembles local dwarf irregulars | **supported**
- H: Does the WR region's high gas density explain its far-IR, mm and radio prominence? | E: electron densities, dust growth timescales, ALMA detection | R: WR region dense and old enough to build dust | F: high density likely responsible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Submillimetre excess explained by very cold dust or by shallow beta=1 dust slope  
  > "We present two hypotheses to explain this excess: very cold dust and unusual dust properties." (5.3. Submillimetre excess and gas-to-dust ratio)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA flux has large free-free contamination; dust-only detection is ~2.5 sigma  
  > "The dust-only emission is a ∼ 2.5σ detection" (5.2. Dust and star formation in the WR region: high density)
- Caveat (inferred, ours): ALMA detection marginal after free-free subtraction
- Caveat (inferred, ours): free-free estimate relies on single Halpha measurement
- Caveat (inferred, ours): dust mass depends on assumed opacity

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Reduced images available at CDS  
  > "Reduced images as FITS files are only available at the CDS" (abstract footnote)
- Missing: CASA version and imaging parameters
- Missing: Magphys configuration
- Data volume (inferred): ~ a few GB for ALMA Band 3 (plus Herschel/ATCA/APEX)
- Score (inferred): 3/5, Data public and multi-facility, but ALMA processing details sparse.
- Rediscovery candidate: no, Multi-facility data and incomplete ALMA recipe; ALMA role minor.

## Links

- Method: da Cunha et al. (2008) (Magphys SED model)
- Companion: Hunt et al. (2014) (Herschel observations of whole GRB host sample)
- Companion: Micha�lowski et al. (2009) (earlier SED study of host)
- Related: KINGFISH
- Related: HRS

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
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
  "facts": 66,
  "stated": 29,
  "rate": 0.439
 },
 "evidence_ok": true
}
```
