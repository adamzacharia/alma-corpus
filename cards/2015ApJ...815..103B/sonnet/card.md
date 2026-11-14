# Dense Gas Fraction and Star-formation Efficiency Variations in the Antennae Galaxies

`2015ApJ...815..103B` | The Astrophysical Journal 2015 | first author: Bigiel, F. | arXiv: 1510.05680 | DOI: 10.1088/0004-637X/815/2/103

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do the dense gas fraction (HCN/CO) and dense gas star formation efficiency (IR/HCN) vary among regions within the Antennae merger?  
  > "how does the fraction of gas that is dense depend on the host galaxy and local conditions within an individual galaxy?" (Introduction)
- Target **Antennae galaxies (NGC 4038/39)**: coordinates _not stated_; z/distance 22 Mpc  
  > "The Antennae are the nearest major galaxy merger, at a distance of $\approx 22$ Mpc (cite: schweizer08)." (Introduction); distance from Schweizer et al. 2008  
  > "The Antennae are the nearest major galaxy merger, at a distance of $\approx 22$ Mpc (cite: schweizer08)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00003.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ALMA minimum projected baseline ~12 kλ (CO 2-1) and ~17 kλ (CO 3-2)  
  > "for ALMA it is $\sim 12 k\lambda$ for CO (2-1) and $\sim 17 k\lambda$ for CO (3-2)" (3.3 Ratios Among Molecular Transitions)
- angular resolution: _not stated_
- max recoverable scale: ~18'' for CO(2-1), ~12'' for CO(3-2) (ALMA); ~100'' for CO(1-0) (CARMA)  
  > "These correspond to maximum recoverable spatial scales of $\sim100\ensuremath{''}$, $\sim18\ensuremath{''}$ and $\sim12\ensuremath{''}$ for CO (1-0), (2-1), and (3-2), respectively." (3.3 Ratios Among Molecular Transitions)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Science Verification data  
  > "From ALMA, we use science verification observations[^2] of $^{12}{\rm CO(2-1)}$ and $^{12}{\rm CO(3-2)}$." (Data)
- Line: 12CO 2-1 (not stated)
- Line: 12CO 3-2 (not stated)
- Other facility **CARMA**: 12CO(1-0), HCN(1-0), HCO+(1-0), CS(2-1), HNC(1-0) maps  
  > "We used CARMA to observe HCN(1-0), HCO$^+$(1-0), HNC(1-0) and CS(2-1) emission from the Antennae galaxies during 2011." (Data)
- Other facility **Herschel PACS (SHINING Survey)**: 70 micron intensity map as star formation indicator  
  > "we use the publicly available *Herschel* (PACS) 70$\mu$m intensity map obtained as part of the SHINING Survey (P.I.: E. Sturm)." (Data)
- External data: HCN-IR luminosity sample of 65 (U)LIRGs and spiral galaxies for comparison  
  > "we compare our measurements to the 65 (U)LIRGS and spiral galaxies from (cite: gao04b) (black points)." (3.2) [from (cite: gao04b)]
- External data: Single-dish HCN and CO luminosities used for flux recovery check  
  > "we compare our luminosities (Table 2) to the single dish measurements presented in (cite: gao01)." (2.2 Measurements) [from (cite: gao01)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 15% (CARMA)  
  > "The two approaches yield results consistent within 15%, which we adopt as the uncertainty on the flux scale." (Data)
- self calibration: Additional self-calibration applied to ALMA SV data  
  > "We performed some additional self-calibration on these data that moderately improved the dynamic range of the images" (Data)

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
- smoothing: All data convolved to common 6.5'' circular Gaussian beam; 1'' pixels on CARMA HCN grid  
  > "We convolve all data sets to a common circular Gaussian beam with a FWHM of 6.5$''$" (Data); "which has 1$''$ pixels" (Data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- TIR from 70 micron conversion  
  > "The total infrared luminosity estimate from 70$\mu$m intensity follows (cite: galametz13)." (Table 2) [from (cite: galametz13)]
- PACS-to-Gaussian PSF convolution kernel  
  > "For the Herschel PACS map we use the kernel from (cite: aniano11) to convert from the PACS map to a Gaussian PSF." (Data) [from (cite: aniano11)]

### Not stated but needed to reproduce (our reading)

- ALMA SV reprocessing details: CASA version, self-calibration parameters, imaging weighting and cleaning
- How ALMA CO(2-1) and CO(3-2) were convolved/matched to 6.5'' and any uv-range matching
- CARMA MIRIAD imaging parameters (weighting, cleaning, mosaic)
- ALMA flux calibration uncertainty
- Exact TIR-from-70um coefficients

## Analysis recipe

1. **Measure integrated intensities at HCN peaks**: Integrate common-resolution cubes (K) over hand-selected velocity windows, no masking  
  > "We measure the intensities from the $6.5\ensuremath{''}$ common-resolution data cubes by integrating the line emission, in Kelvins, across a velocity window selected by hand" (2.2 Measurements)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure luminosities from masked cubes**: Signal-to-noise masked cubes integrated to moment-0 maps; flux summed in apertures  
  > "we select regions of the cube that have a signal-to-noise ratio greater than 3.5 (5) for the HCN or HCO$^{+}$ (CO) over at lease two adjacent velocity channels." (2.2 Measurements)
   - fitting: _not stated_
   - validation: Compared with single-dish luminosities of Gao et al. 2001; recover ~70% CO and ~50% HCN  
  > "we recover about 70% and 50% of the total $^{12}$CO(1-0) and HCN(1-0) luminosity, respectively" (2.2 Measurements)
3. **Derive masses, SFR and depletion times**: Apply conversion factors to luminosities  
  > "we adopt ${\rm \alpha_{HCN}=10\,M_{\odot}\,(K\,km\,s^{-1}\,pc^{2})^{-1}}$ (cite: gao04b), a Galactic $\alpha_{\rm CO} = 4.35$" (3.2)
   - assumption: alpha_HCN=10, alpha_CO=4.35, Murphy et al. 2011 TIR-to-SFR  
  > "and the TIR-to-star formation rate conversion of (cite: murphy11)" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute line ratios among transitions**: Ratios of integrated intensities in K normalized to CO(1-0)  
  > "show the ratios among the integrated line intensities for these transitions, normalizing all measurements to CO(1-0)" (3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : CARMA data reduction  
  > "The data reduction was carried out using MIRIAD." (Data)
- **RADEX** : Mentioned as a one-zone model that could reproduce CO ratios  
  > "a one-zone model like RADEX (cite: vandertak07)" (3.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dense gas depletion time, whole system | ~40 | not stated | Myr | 3 | is $\sim$40 Myr for the entire (observed) system |
| L_HCN/L_CO(1-0), whole system | ~1.5 | not stated | % | 3 | $\sim1.5\%$ for the system as a whole |
| CO(3-2)/(1-0) ratio | ~0.25 | not stated | dimensionless | 4 | Our observed CO(3-2)/(1-0) ratio of $\sim 0.25$ and CO(2-1)/(1-0) ratio of $\sim 0.5$ |
| CO(2-1)/(1-0) ratio | ~0.5 | not stated | dimensionless | 4 | Our observed CO(3-2)/(1-0) ratio of $\sim 0.25$ and CO(2-1)/(1-0) ratio of $\sim 0.5$ |

## Qualitative findings

- HCO+(1-0) is brighter than HCN(1-0) across the Antennae  
  > "the HCO$^{+}$ (1-0) line is in fact brighter than HCN (1-0) across the Antennae" (3.3)

## Claim tuples

- H: Does HCN/CO predict the IR/CO star formation efficiency within the Antennae? | E: Compared region ratios with Gao & Solomon sample | R: Scatter of about a factor of 3 about constant IR/HCN, comparable to the galaxy sample | F: Dense gas star formation efficiency varies; HCN/CO does not predict IR/CO within the Antennae | **supported**
- H: Is the dense gas fraction in the Antennae elevated like in (U)LIRGs? | E: Computed HCN/CO luminosity ratios | R: A few percent, ~1.5% for whole system | F: Dense gas fraction is small, similar to Milky Way clouds | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Different uv coverage between CARMA and ALMA makes CO line ratios uncertain; CARMA may resolve out flux  
  > "the CO line ratios should be treated with some caution because the data come from different telescopes with different $u-v$ coverage" (3.3)
- Caveat (inferred, ours): ALMA SV data are only a minor part, with no processing details
- Caveat (inferred, ours): Uncertainties are large and correlated (35%)
- Caveat (inferred, ours): Flux recovery for HCN only ~50%

## Reproducibility

- Data public (paper): ALMA SV and Herschel data public  
  > "we use the publicly available *Herschel* (PACS) 70$\mu$m intensity map" (Data)
- Products in archive: _not stated_
- Missing: CARMA imaging parameters
- Missing: ALMA reprocessing details
- Missing: Exact TIR calibration
- Data volume (inferred): ~10-50 GB for ALMA SV plus CARMA data
- Score (inferred): 3/5, Main data are CARMA; ALMA part poorly described, but simple measurements.
- Rediscovery candidate: no, Key CARMA data may not be easily available and the recipe is incomplete.

## Links

- Companion: Usero et al., accepted (Related resolved HCN studies in galaxy disks)
- Related: SHINING Survey
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
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
  "stated": 26,
  "rate": 0.394
 },
 "evidence_ok": true
}
```
