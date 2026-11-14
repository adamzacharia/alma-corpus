# VALES - IV. Exploring the transition of star formation efficiencies between normal and starburst galaxies using APEX/SEPIA Band-5 and ALMA at low redshift

`2018MNRAS.475..248C` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Cheng, C. | arXiv: 1712.04460 | DOI: 10.1093/mnras/stx3183

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: Does the star formation efficiency (SFR/L'CO or SFR/M_H2) transition smoothly between normal star-forming galaxies and ULIRGs, rather than showing a bimodal jump, and what controls its scatter?  
  > "We find the SFE of our sample bridges the gap between normal star-forming galaxies and Ultra-Luminous Infrared Galaxies (ULIRGs), which are thought to be triggered by different star formation modes." (abstract)
- Target **24 Herschel-detected (H-ATLAS/GAMA) galaxies at 0.1<z<0.2 observed with APEX/SEPIA Band-5, plus 17 VALES ALMA CO(1-0) detections**: coordinates not stated (H-ATLAS names given in Table 1)  
  > "we select sources with reliable optical counterpart, spectroscopic redshift at 0.1 <z<0.2, and located at the top of the sSFR distribution" (2.1 Sample selection); z/distance 0.1 < z < 0.2 (spectroscopic, GAMA)  
  > "we select sources with reliable optical counterpart, spectroscopic redshift at 0.1 <z<0.2, and located at the top of the sSFR distribution" (2.1 Sample selection); distance from GAMA spectroscopic redshifts; H0 = 70 km/s/Mpc, Omega_m = 0.3, Omega_Lambda = 0.7  
  > "we select sources with reliable optical counterpart, spectroscopic redshift at 0.1 <z<0.2, and located at the top of the sSFR distribution" (2.1 Sample selection)

## Data provenance

- ALMA projects: 2012.1.01080.S, 2013.1.00530.S
- bands: APEX/SEPIA Band-5 (159-211 GHz); ALMA Band-3 for VALES CO(1-0)  
  > "SEPIA Band-5 is a spectrograph that covers the frequency range 159-211 GHz" (2.2 APEX/SEPIA Band-5 observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: rms about 0.5 mK at 111 km/s channel width  
  > "reaching an rms of about 0.5 mK at 111 km/s channel width." (2.2 APEX/SEPIA Band-5 observations)
- time on source: 21 hr awarded; about 40 min per target  
  > "Each target’s exposure time was about 40min" (2.2 APEX/SEPIA Band-5 observations)
- observing dates: _not stated_
- pi or archival as stated: APEX programs 097.F-9724(A); 098.F-9712(B), PI: E. Ibar; ALMA data from earlier VALES papers  
  > "APEX programs 097.F-9724(A); 098.F-9712(B), PI: E. Ibar" (2.2 APEX/SEPIA Band-5 observations)
- Line: CO J=2-1 (APEX); J=1-0 (ALMA VALES) (not stated)
- Other facility **APEX/SEPIA Band-5**: New CO(2-1) spectra of 24 galaxies  
  > "We were awarded 21hrs of APEX/SEPIA Band-5 observations to target the CO ( J = 2–1) emission of 24 starburst galaxies" (2.2 APEX/SEPIA Band-5 observations)
- Other facility **Herschel H-ATLAS / GAMA**: Sample selection, far-IR photometry, multiwavelength data, spectroscopic redshifts  
  > "We selected targets from the equatorial H -ATLAS fields covered by the Galaxy And Mass Assembly survey" (2.1 Sample selection)
- External data: VALES ALMA CO(1-0) detections (17 galaxies in 0.1<z<0.2) and their properties  
  > "the 17 galaxies previously detected by ALMA and shown by Villanueva et al (2017) in the same redshift range" (2.3 Galaxy Sample over 0.1 < z < 0.2 for this study) [from Villanueva et al. 2017]
- External data: Local ULIRG data  
  > "the local ULIRGs (orange cirlcles; Solomon et al. 1997)" (Figure 3 caption) [from Solomon et al. 1997]
- External data: Local spirals data  
  > "local spirals (green stars; Leroy et al. 2009)" (Figure 3 caption) [from Leroy et al. 2009]

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

- Galaxy property derivation (M*, LIR, SFR) follows VALES I  
  > "We follow the same procedure to derive galaxy properties as Villanueva et al. (2017)." (2.3 Galaxy Sample over 0.1 < z < 0.2 for this study) [from Villanueva et al. 2017]
- alpha_CO choice by morphology (0.8 mergers, 4.6 isolated)  
  > "as in previous papers of the VALES series" (Figure 5 caption) [from Villanueva et al. 2017]
- CO radius for APEX targets from SDSS r-band Petrosian radius/1.6  
  > "R CO ≃ R r / 1 . 6 following Villanueva et al (2017)" (4.1 The origin of the SFE scatter) [from Villanueva et al. 2017]

### Not stated but needed to reproduce (our reading)

- ALMA reduction and CO(1-0) flux measurement (in VALES I)
- SEPIA CLASS calibration, antenna temperature to Jy conversion factor
- Gaussian fit and integration procedure for line flux and uncertainties
- Fit method for Eq. 2
- MAGPHYS setup
- Merger/isolated classification of all galaxies
- How 5-sigma upper limits were computed

## Analysis recipe

1. **Reduce APEX/SEPIA spectra and fit CO line**: Edge trimmed (~3%), first-order polynomial baseline subtracted, single Gaussian fit  
  > "we trimed the edge (about 3%) of the spectrum and subtracted the baseline by using a first-order polynomial." (2.2 APEX/SEPIA Band-5 observations)
   - software: CLASS
   - fitting: single Gaussian profile  
  > "We fit the CO emission by a single Gaussian profile and show the result as a red line." (Figure 2 caption)
   - validation: _not stated_
2. **Derive galaxy properties**: M* from MAGPHYS; SFR = 1e-10 LIR/Lsun; LIR from far-IR photometry fitting  
  > "The stellar masses are derived using MAGPHYS (da Cunha et al. 2008)" (2.3 Galaxy Sample over 0.1 < z < 0.2 for this study)
   - software: MAGPHYS
   - assumption: Chabrier IMF  
  > "assuming a Chabrier IMF" (2.3 Galaxy Sample over 0.1 < z < 0.2 for this study)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute L'CO and molecular gas mass**: L'CO(1-0) from Eq. 1 using CO(2-1)/CO(1-0)=0.85; M_H2 = alpha_CO L'CO, cross-checked with gas-to-dust ratio  
  > "We assume a L CO ( J =2–1) / L CO ( J =1–0) ratio as 0.85" (3 RESULTS)
   - assumption: alpha_CO = 0.8 for mergers, 4.6 for isolated; delta = 100  
  > "We assume a constant gas-to-dust ratio δ = M gas / M dust = 100 (Magdis et al. 2012)" (4.1 The origin of the SFE scatter)
   - fitting: _not stated_
   - validation: Gas-to-dust method agrees with alpha_CO estimates  
  > "the gas-to-dust ratio method shows a good agreement with the α CO L ′ CO estimations" (4.1 The origin of the SFE scatter)
4. **Fit SFE' vs LIR scaling and compare with bimodal models**: Power-law fit for LIR>1e11 Lsun galaxies including local ULIRGs; compare SFE/SFE_ms vs sSFR/sSFR_ms with Sargent et al. 2014  
  > "We fit the scaling relation between SFE ′ and IR luminosity for all the L IR > 10 11 L ⊙ galaxies from the VALES including our new SEPIA band-5 detections and local ULIRGs" (3 RESULTS)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CLASS** Version 1.1: Reduction of APEX/SEPIA Band-5 data  
  > "The APEX/SEPIA Band-5 data were reduced with CLASS software Version 1.1." (2.2 APEX/SEPIA Band-5 observations)
- **MAGPHYS** : Stellar masses and dust masses  
  > "The stellar masses are derived using MAGPHYS (da Cunha et al. 2008)" (2.3 Galaxy Sample over 0.1 < z < 0.2 for this study)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) detections with S/N>3 | 16 of 24 | not stated | galaxies | 1 | 16 galaxies have S/N > 3 and were fitted by single Gaussian profile |
| Non-detections at 5 sigma | 8 | not stated | galaxies | 1 | 8 galaxies have no CO detection down to 5 σ in the APEX spectra. |
| Scatter of SFE' for normal galaxies (2e9<LIR<1e11) | about 0.5 | not stated | dex | 4 | the SFE ′ is roughly constant with scatter of about 0.5 dex |
| Slope of SFE'-LIR relation (LIR>1e11) | 0.71 | 0.01 | dimensionless | 4 | 0 . 71 ± 0 . 01 |
| Normalisation of SFE' at LIR=1e11 Lsun | 2.8 | 0.9 | 1e-9 yr^-1 | 4 | (2 . 8 ± 0 . 9) |

## Qualitative findings

- SFE' increases smoothly with LIR from normal galaxies to ULIRGs, with no bimodal jump  
  > "there is a smooth transition of SFEs as a function of IR luminosities, in contradiction with a bimodal behaviour." (4.2 Confronting the bimodality in star formation efficiencies)

## Claim tuples

- H: SFE shows a bimodal jump between normal SFGs and starbursts | E: Combined VALES ALMA and new APEX/SEPIA LIRG samples, compared SFE vs LIR and sSFR/sSFRms with literature | R: SFE' is constant up to LIR~1e11 then increases smoothly; steep jump at sSFR/sSFRms>3 not seen | F: Smooth transition rather than bimodality | **supported**
- H: Scatter in SFE is controlled by alpha_CO, gas fraction and size | E: Compared SFE with alpha_CO and gas-to-dust, gas radius, and gas fraction scalings | R: SFE anti-correlates with CO radius, slope about -0.6 ± 0.04 for ALMA-resolved galaxies | F: alpha_CO uncertainty, gas fraction and size drive scatter | **partially**

## Reasoning

- Why this data: SEPIA Band-5 is the only southern instrument able to detect CO(2-1) at z=0.1-0.2  
  > "SEPIA Band-5 is the only instrument that is able to detect CO ( J = 2–1) at redshifts from 0.1 to 0.2 in the Southern hemisphere." (2.2 APEX/SEPIA Band-5 observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): APEX beam (~35") may include close counterparts; CO(2-1)/(1-0) ratio and alpha_CO assumptions add systematic uncertainty  
  > "We expect this systematic variation will affect our result by 0.3 dex at most." (3 RESULTS)
- Caveat (inferred, ours): SFE' and LIR are not independent, so the fitted relation is partly circular
- Caveat (inferred, ours): Low-J CO ratio assumed constant at 0.85
- Caveat (inferred, ours): Sample mixes APEX unresolved and ALMA data; selection toward detections
- Caveat (inferred, ours): Slope/normalisation fit details not described

## Reproducibility

- Data public (paper): H-ATLAS DR1 catalog public; ALMA projects cited  
  > "Making use of the public _H_ -ATLAS DR1 [1] catalog," (2.1 Sample selection)
- Products in archive: _not stated_
- Missing: Reduced APEX spectra or flux table beyond Table 1
- Missing: VALES ALMA fluxes (in Villanueva et al. 2017)
- Missing: Fit details for Eq. 2
- Data volume (inferred): small (<1 GB for APEX spectra); ALMA data not reprocessed here
- Score (inferred): 3/5, Simple analysis with a table of derived values, but key inputs are inherited from earlier VALES papers and fit details are sparse.
- Rediscovery candidate: no, ALMA data play a minor role and the APEX reduction/fit details are insufficient.

## Links

- Method: Villanueva et al. 2017 (VALES I) (Source of sample, ALMA data and galaxy property derivation)
- Companion: Hughes et al. 2017a; 2017b (Other VALES papers)
- Related: VALES
- Related: H-ATLAS
- Related: GAMA

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 30,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
