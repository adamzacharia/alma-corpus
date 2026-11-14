# The Evolution of Interstellar Medium Mass Probed by Dust Emission: ALMA Observations at z = 0.3-2

`2014ApJ...783...84S` | The Astrophysical Journal 2014 | first author: Scoville, N. | arXiv: 1401.2987 | DOI: 10.1088/0004-637X/783/2/84

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can the Rayleigh-Jeans dust continuum measured with ALMA Band 7 be used to trace ISM mass, and how does ISM mass evolve from z=2 to 0.4 in stellar-mass-selected galaxies?  
  > "Here, we develop an alternative approach – using the long wavelength dust continuum to probe of ISM masses at high redshift" (1. INTRODUCTION)
- Target **107 COSMOS galaxies at z=0.2-2.5 (Low-z 37, Mid-z 33, High-z 31, IR-bright 6)**: coordinates COSMOS field, RA ~149.5-150.8 deg, Dec ~1.7-2.8 deg (Tables A1-A3)  
  > "Our sample of 107 galaxies is taken from the COSMOS 2 deg [2] survey (Scoville et al. 2007)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA); "The photometric redshifts and stellar masses of the galaxies are from Ilbert et al. (2013)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA); z/distance z = 0.22-2.54  
  > "Our sample of 107 galaxies is taken from the COSMOS 2 deg [2] survey (Scoville et al. 2007)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA); "The photometric redshifts and stellar masses of the galaxies are from Ilbert et al. (2013)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA); distance from photometric redshifts from Ilbert et al. (2013); half have spectroscopic redshifts  
  > "Our sample of 107 galaxies is taken from the COSMOS 2 deg [2] survey (Scoville et al. 2007)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA); "The photometric redshifts and stellar masses of the galaxies are from Ilbert et al. (2013)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA)

## Data provenance

- ALMA projects: 2011.0.00097.S
- bands: Band 7 (350 GHz)  
  > "obtained in Mar Oct 2012 in Band 7 at 350 GHz" (4. OBSERVATIONS AND RESULTS)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 8 GHz  
  > "With continuum bandwidths of 8 GHz, the 1σ rms sensitivity was 0.5, 0.4 and 0.3 mJy" (4. OBSERVATIONS AND RESULTS)
- arrays: 15-18 antennas  
  > "with ∼ 15 − 18 telescopes in the array" (1. INTRODUCTION)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.6 arcsec typical beam  
  > "typical synthesized beam sizes were ≃ 0.6 [′′]" (4. OBSERVATIONS AND RESULTS)
- max recoverable scale: _not stated_
- sensitivity: 1σ rms 0.5, 0.4, 0.3 mJy for z=0.3, 0.9, 2  
  > "the 1σ rms sensitivity was 0.5, 0.4 and 0.3 mJy and typical synthesized beam sizes were ≃ 0.6 [′′]" (4. OBSERVATIONS AND RESULTS)
- time on source: 1, 2, 4 min per galaxy at z=0.3, 0.9, 2; ~5 hr total  
  > "On-source integration times were 1, 2 and 4 minutes per galaxy at z = 0.3, 0.9 and 2, respectively." (4. OBSERVATIONS AND RESULTS)
- observing dates: Mar-Oct 2012 (Cycle 0)  
  > "were obtained in Mar Oct 2012 in Band 7 at 350 GHz" (4. OBSERVATIONS AND RESULTS)
- pi or archival as stated: _not stated_
- Other facility **COSMOS (HST/Spitzer/photometry)**: Photometric redshifts, stellar masses for sample selection  
  > "The photometric redshifts and stellar masses of the galaxies are from Ilbert et al. (2013)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA)
- Other facility **Herschel PACS/SPIRE**: IR data used for SFRs  
  > "The SFRs are derived from the rest frame UV continuum and the infrared using Herschel PACS and SPIRE data as detailed in Scoville et al. (2013)." (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA)
- Other facility **Planck**: Galactic dust opacity and beta calibration  
  > "Planck Collaboration (2011a) finds β = 1.8 ± 0.1 with no significant difference between the HI and H 2 -dominant regions." (2.1)
- External data: SCUBA 450/850 um fluxes and ISM masses for 12 local galaxies  
  > "Submm flux measurements and ISM masses from Dale et al. (2005), Clements et al. (2010) and the NASA Extragalactic Database." (Table 1) [from Dale et al. 2005; Clements et al. 2010]
- External data: SMG 850um fluxes and CO(1-0) data  
  > "Submm fluxes and CO(1-0) measurements from references given in the second column" (Table 2) [from Fu et al. 2013; Aravena et al. 2013; Harris et al. 2012; etc.]
- External data: Photometric redshifts and stellar masses  
  > "the galaxy properties are from the latest photometric redshift catalog (Ilbert et al. 2013)" (Appendix A) [from Ilbert et al. 2013]
- External data: SFRs  
  > "The SFRs in Column 9 are from Scoville et al. (2013)" (Appendix A) [from Scoville et al. 2013]
- External data: Planck tau250/NH values  
  > "In the following, we adopt τ 250µm /N H ≃ 1.0 × 10 [−][25]" (2.3) [from Planck Collaboration 2011a,b]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA (details not given)  
  > "The data were calibrated and imaged with natural weighting using CASA." (4. OBSERVATIONS AND RESULTS)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The data were calibrated and imaged with natural weighting using CASA." (4. OBSERVATIONS AND RESULTS)
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

- Photometric redshifts and stellar masses  
  > "The photometric redshifts and stellar masses of the galaxies are from Ilbert et al. (2013)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA) [from Ilbert et al. (2013)]
- SFR derivation  
  > "as detailed in Scoville et al. (2013)" (3. COSMOS MASS-SELECTED GALAXY SAMPLE FOR ALMA) [from Scoville et al. (2013)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrator/flux scale details
- Image size, cell size, and flux-scale uncertainty
- How apertures were centered (positions from COSMOS) and pixel treatment
- Exact stacking procedure (alignment, weights) and how uncertainties on stacked masses were computed
- Primary beam correction not stated

## Analysis recipe

1. **Calibrate empirical alpha850 (L_nu/M_ISM)**: Ratio of 850um specific luminosity to ISM mass for local galaxies, Planck Galactic data, and SMGs with CO(1-0)  
  > "Based on the data shown in Fig. 1, we find a constant of proportionality between the 850µm specific luminosity and the ISM mass" (2.2)
   - parameter: beta = 1.8, Td = 25 K  
  > "In the following, we assume T d = 25 K to characterize the bulk of the ISM mass." (2.4)
   - assumption: alpha_CO = 4.6 Msun (K km/s pc^2)^-1 for SMGs; HI set to 50% of H2 for local sample  
  > "a standard α CO = M ISM /L CO = 4.6 M ⊙ (K km sec [−][1] pc [2] ) [−][1]" (2.5)
   - fitting: _not stated_
   - validation: Three independent calibrations agree within ~20%  
  > "The value of the constant of proportionality between the 850µm flux and the ISM mass in the Galaxy found by the Planck Mission is therefore within 20% of that found earlier" (2.3)
2. **Measure continuum fluxes of individual galaxies**: Integrated aperture flux and peak pixel in 3" (low-z) or 2" (mid/high-z) apertures; noise from 100 displaced apertures; detection at 2σ integrated or 3.6σ peak  
  > "A significant detection required a 2σ SNR in the integrated aperture flux (S tot in the tables) or a 3.6 σ detection of a high single pixel" (4.1)
   - software: CASA
   - fitting: _not stated_
   - validation: Thresholds chosen so fewer than one spurious detection in sample  
  > "These different nσ limits were chosen such that there would be less than one spurious detection by either technique in the entire sample." (4.1)
3. **Stack images per subsample and derive ISM mass**: Average, median, and rms-weighted average stacks; convert flux to M_ISM via Eq. 12 with Gamma_RJ correction  
  > "The individual galaxy images were stacked in three ways: an average, a median stack and an average weighted by the square of the rms noise." (5. STACKED SAMPLES)
   - assumption: alpha850 = 1.0e20 erg/s/Hz/Msun, beta=1.8, Td=25 K  
  > "where we have used α 850µm given by Eq. 7." (2.4)
   - fitting: _not stated_
   - validation: Simple average not significantly different from weighted  
  > "The simple average was not significantly different except that it has higher noise than the rms-weighted average." (5. STACKED SAMPLES)
4. **Derive gas fractions and depletion times**: M_ISM/(M*+M_ISM) and tau_SF = M_ISM/<SFR>  
  > "The depletion timescales for the ISM via star formation are given by τ SF = M ISM / < SFR >" (5. STACKED SAMPLES)
   - fitting: _not stated_
   - validation: Compared with Tacconi et al. 2013 CO gas fractions  
  > "Tacconi et al. (2013) surveyed 52 galaxies at z = 1 - 3 in CO(3-2) and found mean gas mass fractions of 0.33 and 0.47" (5. STACKED SAMPLES)

## Software

- **CASA** : calibration and imaging with natural weighting  
  > "The data were calibrated and imaged with natural weighting using CASA." (4. OBSERVATIONS AND RESULTS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha850 local galaxies | 1.0 | ±0.23 | 1e20 erg s^-1 Hz^-1 Msun^-1 | 1 | = 1.0 ± 0.23 × 10 [20] ergs sec [−][1] Hz [−][1] M ⊙−1 . (7) |
| alpha850 from Planck | 0.79 | not stated | 1e20 erg s^-1 Hz^-1 Msun^-1 | 1 | = 0.79 × 10 [20] ergs/sec/Hz/M ⊙ (9) |
| alpha850 SMGs | 1.01 | ±0.52 | 1e20 erg s^-1 Hz^-1 Msun^-1 | 1 | The average value of the luminosity-tomass ratio = 1.01 ± 0.52 × 10 [20] |
| Individual detection fraction | 28 of 107 (26%) | not stated | dimensionless | 2 | Twenty-eight of the 107 galaxies (26%) were significantly detected |
| Gas mass fractions (low-z, mid-z, high-z, IR bright) | 2, 12, 14, 53 % | ±0.5, 3, 3, 5 | % | 4 | ∼ 2 ± 0.5, 12 ± 3, 14 ± 3 and 53 ± 5 % for the low-z, mid-z, high-z and IR bright samples, respectively. |
| Stacked M_ISM weighted average (low-z, mid-z, high-z, IR bright) | 0.50, 1.06, 0.26... see Table 4: 0.21, 2.19, 2.43, 10.48 | ±0.07, 0.47, 0.24, 0.57 | 1e10 Msun | 3 | weighted average 0.18 0.057 0.240 3.23 0.39 1.30±0.57 0.63±1.72 0.21±0.07 0.50±0.16 0.02±0.005 |
| Depletion time range | 0.2-1.2 | not stated | Gyr | 4 | This depletion timescale is similar for the subsamples (0.2 - 1.2 Gyr). |

## Qualitative findings

- ISM mass roughly constant from z=2 to 0.9 and drops by ~6 to z=0.4; IR-bright z=2 galaxies have ~4-5 times more ISM.  
  > "the ISM content has decreased a factor ∼ 6 from 1 − 2 × 10 [10] M ⊙ at both z = 2 and 0.9 down to ∼ 2 × 10 [9] M ⊙ at z = 0.4." (abstract)

## Claim tuples

- H: RJ dust emission is a calibrated probe of ISM mass | E: Compare L850/M_ISM in local galaxies, Planck Milky Way, and z<3 SMGs | R: alpha850 = 1.0, 0.79, 1.01 e20 | F: A constant RJ mass-to-light ratio is usable at all redshifts | **supported**
- H: ISM content of massive galaxies evolves strongly with redshift | E: Stack ALMA Band 7 images of 3 mass-selected samples | R: M_ISM ~2e10 at z=2,0.9 and ~2e9 at z=0.4 | F: Strong decline in ISM mass fraction at low z | **supported**
- H: IR-bright galaxies differ from mass-selected ones | E: Compare stacked IR-bright sample at z=2 | R: ~4-5 times more ISM, similar depletion time | F: IR-bright galaxies simply have more ISM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust continuum is much faster than CO and avoids excitation and CO-to-H2 uncertainties  
  > "This approach is much faster (∼ 30×) than molecular line observations and more reliably calibrated" (1. INTRODUCTION)
- Alternative: SED fitting for dust temperature rejected as unreliable for mass  
  > "Fitting the observed SED to derive an effective dust temperature is not a reliable approach" (2.7)
- How they decided it was enough: _not stated_
- Limitation (authors): Pathfinder, small samples, only most massive galaxies; results preliminary  
  > "Thus the evolutionary trends mentioned above are very preliminary and much larger samples are warranted." (6. SUMMARY)
- Caveat (inferred, ours): Single dust temperature (25 K) and alpha850 assumed constant across redshift
- Caveat (inferred, ours): Low-z stack detection only ~3σ and from peak pixel
- Caveat (inferred, ours): Calibration relies on assumed CO-to-H2 conversion factors
- Caveat (inferred, ours): Stack uncertainties are sample dispersions, not clearly propagated
- Caveat (inferred, ours): Sample dominated by massive galaxies, possibly passive

## Reproducibility

- Data public (paper): ALMA project cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2011.0.00097.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and calibration details
- Missing: Imaging parameters (cell, size, masking)
- Missing: Stacking details
- Missing: Table 4 low-z flux handling details
- Data volume (inferred): ~tens of GB (Cycle 0 Band 7, ~5 hr, 107 short pointings)
- Score (inferred): 3/5, Photometry and stacking are simple and tables are given, but processing details and stacking specifics are missing.
- Rediscovery candidate: no, Imaging and stacking recipes are incomplete, though the flux-to-mass conversion is fully given.

## Links

- Method: Scoville 2012 (ArXiv:1210.6990) (Physical basis of dust-based ISM mass)
- Companion: Scoville et al. 2013, ApJS, 206, 3 (SFRs of COSMOS galaxies)
- Related: COSMOS
- Related: Herschel-ATLAS

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 72,
  "stated": 40,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
