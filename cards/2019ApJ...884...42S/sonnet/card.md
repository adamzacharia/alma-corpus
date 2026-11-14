# Masses and Implications for Ages of Low-mass Pre-main-sequence Stars in Taurus and Ophiuchus

`2019ApJ...884...42S` | The Astrophysical Journal 2019 | first author: Simon, M. | arXiv: 1908.10952 | DOI: 10.3847/1538-4357/ab3e3b

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: star_formation, stellar_physics, protoplanetary_disks
- Question: Do PMS evolutionary tracks, with and without internal magnetic fields, reproduce disk-based dynamical masses of single T Tauri stars in Taurus and Ophiuchus, and what ages does this imply?  
  > "The accuracy of masses of pre-main sequence (PMS) stars derived from their locations on the Hertzsprung-Russell Diagram (HRD) can be tested by comparison with accurate and precise masses determined independently." (abstract)
- Target **Taurus SFR PMS stars with disks (e.g., AA Tau, BP Tau, CQ Tau, CW Tau, CX Tau, DE Tau, HK Tau, HV Tau C, FS Tau B)**: coordinates _not stated_; z/distance ~140 pc average; individual Gaia DR2 distances in Table 1  
  > "Most of the stars lie at a distance near 140 pc as expected (Kenyon et al. 1994) but are distributed over distances 100 to 200 pc." (2.1. Overview: The Samples in the Taurus and Ophiuchus SFRs); distance from Gaia DR2 (Bailer-Jones et al. 2018)  
  > "Most of the stars lie at a distance near 140 pc as expected (Kenyon et al. 1994) but are distributed over distances 100 to 200 pc." (2.1. Overview: The Samples in the Taurus and Ophiuchus SFRs)
- Target **Ophiuchus L1688 stars (GSS 39, ROX 25, YLW 58)**: coordinates _not stated_; z/distance ~119 pc adopted; DR2 where available (Table 2)  
  > "DR2 distances are available for only 3 of the stars in our sample." (2.1. Overview: The Samples in the Taurus and Ophiuchus SFRs); distance from Gaia DR2 (Bailer-Jones et al. 2018)  
  > "DR2 distances are available for only 3 of the stars in our sample." (2.1. Overview: The Samples in the Taurus and Ophiuchus SFRs)

## Data provenance

- ALMA projects: 2013.1.01070.S, 2015.1.010017.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: AA Tau 0.25x0.2 arcsec; 2011.0.00320 ~0.7x0.5 arcsec; DE Tau 0.28x0.19 arcsec; 2016.1.00460 ~0.5x0.35 arcsec  
  > "The typical synthesized beam is 0.5 × 0.35′′." (Appendix)
- max recoverable scale: _not stated_
- sensitivity: 2016.1.00460 line sensitivity ~20 mJy/beam (~1.2 K)  
  > "The line sensitivity is about 20 mJy/beam, or about 1.2 K." (Appendix)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data from PIs Loomis, Chapillon, Boehler, Menard  
  > "The archival data were calibrated using the appropriate CASA software for each observation" (2.2. Analysis of ALMA Archival Data)
- Line: CO J=3-2 (not stated)
- Line: 13CO J=2-1 (AA Tau) and J=3-2 (not stated)
- Other facility **Gaia DR2**: Distances to PMS stars  
  > "Precise distances are now available to most PMS stars in the Taurus SFR using the second release (DR2) of the GAIA mission" (1. INTRODUCTION)
- External data: Luminosities from Andrews et al. (2013) (CQ Tau from Villebrun et al. 2019)  
  > "The luminosities in Col. 4 are from Andrews et al. (2013), except that of CQ Tau which is from Villebrun et al. (2019)." (2.3. Fundamental Masses of Stars with Precisions ≤ 10% and their Stellar Parameters) [from Andrews et al. 2013; Villebrun et al. 2019]
- External data: Luminosities and spectral types from Herczeg & Hillenbrand (2014)  
  > "The second set of parameters uses the luminosities (col. 6) of Herczeg & Hillenbrand" (2.3. Fundamental Masses of Stars with Precisions ≤ 10% and their Stellar Parameters) [from Herczeg & Hillenbrand (2014)]
- External data: Teff from spectral types via look-up table  
  > "Col. 5 lists the effective temperatures, T eff s, corresponding to the spectral types in Col. 3 using Pecaut & Mamajek (2013)’s look-up table." (2.3. Fundamental Masses of Stars with Precisions ≤ 10% and their Stellar Parameters) [from Pecaut & Mamajek (2013)]
- External data: Gaia DR2 distances  
  > "Col. 6 lists Bailer-Jones et al. (2018)’s Gaia DR2 distance estimates of these stars." (2.1. Overview: The Samples in the Taurus and Ophiuchus SFRs) [from Bailer-Jones et al. 2018]
- External data: Previously published dynamical masses  
  > "References: 1) Simon et al. (2017), 2) This paper, 3) Dutrey et al. (2003), 4) Guilloteau et al. (2014), 5) Schaefer et al. (2009)" (Table 1) [from Simon et al. 2017; Dutrey et al. 2003; Guilloteau et al. 2014; Schaefer et al. 2009]
- External data: Ophiuchus luminosities/spectral types  
  > "The luminosities and spectral types in Columns 3 and 4 for GSS 39 and YLW 58 are from Ricci et al. (2010)" (2.3. Fundamental Masses of Stars with Precisions ≤ 10% and their Stellar Parameters) [from Ricci et al. 2010; Erickson et al. 2011; Najita et al. 2015]
- Simulation/model as data: Evolutionary tracks: Baraffe et al. (2015) standard; Feiden (2016) standard and magnetic; MESA (Paxton et al. 2015)  
  > "Figs 3a and b use the standard models of Baraffe et al. (2015)." (3.1. Track Masses from Hertzsprung-Russell Diagrams)

## Processing

### Calibration

- pipeline or manual: Calibrated with appropriate CASA for each observation; 2016.1.00460 with standard pipeline  
  > "Data was calibrated using the standard pipeline in the CASA software package" (Appendix)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: None for 2016.1.00460  
  > "No self-calibration was performed, but the data is of sufficient quality for our analysis." (Appendix)

### Imaging

- task: Exported via UVFITS to GILDAS for imaging and analysis; fits done on visibilities  
  > "exported through UVFITS format to the GILDAS package for imaging and data analysis" (2.2. Analysis of ALMA Archival Data)
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

- DiskFit model fitting procedure  
  > "we used our DiskFit package (Pi´etu et al. 2007) as in Simon et al. (2017)" (2.2. Analysis of ALMA Archival Data) [from Piétu et al. 2007; Simon et al. 2017]
- HK Tau A/B alternate model subtraction  
  > "The same procedure (alternate subtraction of the best fit model of A and B) as in Simon et al. (2017) was used." (Appendix) [from Simon et al. 2017]

### Not stated but needed to reproduce (our reading)

- CASA versions used for each dataset
- Channel range masked for cloud contamination per source
- Flux calibrators and flux scale uncertainty
- Initial parameters, free-parameter list and priors/bounds for DiskFit
- Exact algorithm for reading track masses and ages from HRDs (interpolation)
- Inclination/disk fit details for sources beyond the Appendix table
- Magnetic track grid specifics from Feiden 2016

## Analysis recipe

1. **Calibrate and image archival ALMA data**: Calibrate with CASA, export UVFITS to GILDAS  
  > "The archival data were calibrated using the appropriate CASA software for each observation" (2.2. Analysis of ALMA Archival Data)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: 2011.0.00320 data recalibrated with newer CASA to remove velocity shift  
  > "Re-calibrating the whole data set using a more recent version of CASA suppressed this issue." (Appendix)
2. **Fit disk Keplerian model to derive dynamical mass**: DiskFit fit of vertically isothermal power-law disk with CO depletion zone, chi2 minimization on visibilities  
  > "The fit is performed by minimizing the χ2 between the modeled and the observed visibilities." (2.2. Analysis of ALMA Archival Data)
   - software: DiskFit, GILDAS
   - parameter: Channels around cloud systemic velocity ignored; scale height free; a_dep typically <0.1  
  > "a range of channels around the cloud systemic velocity was ignored in the fitting process." (2.2. Analysis of ALMA Archival Data)
   - assumption: Gaia DR2 distances; power-law temperature and column density  
  > "In this paper we apply the distances in DR2 to the PMS stars with masses measured by the circumstellar disk technique." (1. INTRODUCTION)
   - fitting: chi2 minimization; no sampler stated  
  > "The fit is performed by minimizing the χ2 between the modeled and the observed visibilities." (2.2. Analysis of ALMA Archival Data)
   - validation: Masses insensitive to avoided channel range; T by 20% or column density by factor 2 would not change velocities; continuum checked for consistency  
  > "We verified that our derived masses were not sensitive to the precise range of the avoided channels." (2.2. Analysis of ALMA Archival Data)
3. **Select precise masses**: Keep stars with Mdyn relative uncertainty <10%  
  > "We selected for further analysis only the 32 stars with fundamental dynamical masses determined to relative uncertainty less than 10%" (2.3. Fundamental Masses of Stars with Precisions ≤ 10% and their Stellar Parameters)
   - fitting: _not stated_
   - validation: _not stated_
4. **Place stars on HRDs and derive track masses and ages**: Locate (Teff, L) on standard (Baraffe, Feiden, MESA) and magnetic (Feiden 2016) tracks; uncertainty from ellipse  
  > "The uncertainty is derived by drawing an ellipse centered at (logTeff, logL) with shape given by uncertainties in luminosities scaled to DR2 distances." (3.1. Track Masses from Hertzsprung-Russell Diagrams)
   - parameter: Magnetic models used for ages 1 to 10 MY  
  > "here we use them only in the age range 1 to 10 MY." (3.1. Track Masses from Hertzsprung-Russell Diagrams)
   - assumption: Luminosities scaled to DR2 distances; Teff from spectral types  
  > "The table presents two sets of parameters with the published luminosities scaled to DR2 distances." (2.3. Fundamental Masses of Stars with Precisions ≤ 10% and their Stellar Parameters)
   - fitting: _not stated_
   - validation: Standard-model results said same for Feiden 2016 and MESA as Baraffe  
  > "they would have been the same if we had used the standard models of Feiden (2016) or those calculated using MESA (Paxton et al. 2015)" (3.1. Track Masses from Hertzsprung-Russell Diagrams)

## Software

- **CASA** : Calibration of archival data  
  > "The archival data were calibrated using the appropriate CASA software for each observation" (2.2. Analysis of ALMA Archival Data)
- **GILDAS** : Imaging and data analysis  
  > "exported through UVFITS format to the GILDAS package for imaging and data analysis" (2.2. Analysis of ALMA Archival Data)
- **DiskFit** : Disk model fitting to visibilities for dynamical masses  
  > "we used our DiskFit package (Pi´etu et al. 2007)" (2.2. Analysis of ALMA Archival Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean (Mdyn - MC_hrd), magnetic tracks | 0.01 | 0.02 | Msun | 4 | the average difference (M dyn MC hrd ) is 0.01 ± 0.02 M ⊙ |
| Mean (Mdyn - MA_hrd), standard Baraffe tracks | 0.11 | 0.04 | Msun | 4 | The average difference (M dyn - MA hrd ) is 0.11 ± 0.04 M ⊙ |
| Mean (Mdyn - MB_hrd) | 0.19 | 0.02 | Msun | 4 | for MB hrd the average difference is 0.19 ± 0.02 M ⊙ |
| Mdyn of CW Tau | 0.64 | 0.01 | Msun | 2 | CW Tau, despite its value of M dyn = 0.64 ± 0.01 |
| Teff offset below non-magnetic theory | 200-300 | not stated | K | 4 | the stars’ T eff values lie about 200-300 K below the theoretical values indicated by the non-magnetic model. |
| Ages on magnetic tracks | 3 to 10 | not stated | MY | 4 | Ages of the stars in the Taurus SFR evaluated using isochrones of the magnetic models are older, ∼ 3 to 10 MY |

## Qualitative findings

- Standard models underestimate actual stellar mass by ~30% for 0.4–1.4 Msun  
  > "underestimate the actual stellar mass by about 30%." (4. SUMMARY)
- Large scatter of observed Teff around magnetic model Teff exceeds uncertainties  
  > "the scatter of the observed T eff s around the theoretical T eff, in the plausible age range 1-10 MY, far exceeds their uncertainties." (3.1. Track Masses from Hertzsprung-Russell Diagrams)

## Claim tuples

- H: Non-magnetic PMS tracks give accurate masses | E: Compare Mdyn with track masses from HRDs for 25 Taurus stars | R: Track masses smaller than Mdyn for 20 of 25; mean differences 0.11 and 0.19 Msun | F: Standard models underestimate mass by ~30% | **supported**
- H: Magnetic tracks reproduce dynamical masses | E: Place stars on Feiden (2016) magnetic HRD | R: Mean Mdyn-MC_hrd = 0.01±0.02 Msun | F: Magnetic models are more consistent with Mdyn | **supported**
- H: PMS stars are older than standard 1-3 MY | E: Read isochrone ages on magnetic HRD | R: Ages ~3-10 MY | F: Older ages indirectly supported, lengthening disk and planet formation time | **partially**

## Reasoning

- Why this data: Archival ALMA disk data give dynamical masses independent of other stellar properties  
  > "These masses are fundamental because they are independent of any other stellar property." (1. INTRODUCTION)
- Why this method: _not stated_
- Alternative: Stars with poor data excluded from mass determination (MWC 758, IRAS04302+2247, IRAS I04158+2805)  
  > "Hence, no dynamical mass determination was performed on this object." (Appendix)
- How they decided it was enough: _not stated_
- Limitation (authors): Few stars with Mdyn<0.4 Msun  
  > "The sample with which worked has very few stars with M dyn < 0.4 M ⊙ ." (4. SUMMARY)
- Limitation (authors): Ophiuchus luminosities/track masses unreliable due to extinction  
  > "We do not regard these track masses as reliable owing to the uncertainties of determining luminosities and spectral types of these very obscured stars." (3.1. Track Masses from Hertzsprung-Russell Diagrams)
- Caveat (inferred, ours): Track masses read graphically from figures; reproducibility is limited
- Caveat (inferred, ours): Luminosity systematics (0.3 dex between catalogs) dominate age uncertainty
- Caveat (inferred, ours): Alternative explanations for Teff offsets (spots, accretion) not disentangled
- Caveat (inferred, ours): Only magnetic tracks of one code (Feiden 2016) tested

## Reproducibility

- Data public (paper): Archival ALMA data, with project codes given  
  > "Our work has also used ALMA archival data as specified in the text." (Acknowledgments)
- Products in archive: _not stated_
- Missing: DiskFit settings and masking velocity ranges per source
- Missing: CASA versions
- Missing: HRD mass/age reading procedure
- Data volume (inferred): ~100-300 GB raw for five ALMA projects
- Score (inferred): 3/5, Data are public and the methodology is described, but fit settings are sparse and the HRD analysis is graphical.
- Rediscovery candidate: no, Recipe incomplete (mass fits rely on unreleased DiskFit configuration; HRD mass reading is graphical).

## Links

- Method: Piétu et al. 2007 (DiskFit package)
- Method: Simon et al. 2017 (Same disk-fitting procedure and earlier masses)
- Companion: Simon et al. 2017, ApJ (Earlier dynamical masses for Taurus and Ophiuchus)
- Related: Gaia DR2

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.010017.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00320.S",
  "2013.1.00426.S",
  "2015.1.01017.S",
  "2016.1.00460.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 43,
  "rate": 0.537
 },
 "evidence_ok": true
}
```
