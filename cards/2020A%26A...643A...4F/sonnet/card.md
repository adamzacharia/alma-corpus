# The ALPINE-ALMA [CII] survey. Dust attenuation properties and obscured star formation at z ∼ 4.4-5.8

`2020A&A...643A...4F` | Astronomy and Astrophysics 2020 | first author: Fudamoto, Y. | arXiv: 2004.10760 | DOI: 10.1051/0004-6361/202038163

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How do dust attenuation (IRX-beta, IRX-M*) and the obscured fraction of star formation behave in main-sequence galaxies at z~4.4-5.8, using ALPINE 158 um continuum?  
  > "However, the existing studies at $z>4-5$ are based only on a handful ($\sim10$) of sources, and the results need to be confirmed with a larger sample size. This is the goal of the present paper." (Introduction)
- Target **ALPINE sample of 118 star-forming galaxies (COSMOS 105, GOODS-South 13)**: coordinates _not stated_; z/distance z~4.4-5.9  
  > "The targets have secure spectroscopic redshifts from two observation campaigns in the COSMOS (105) and the GOODS-South (13) fields" (2.1 Sample and ancillary data); distance from spectroscopic redshifts from rest-UV lines (Le Fevre 2015; Hasinger 2018)  
  > "The targets have secure spectroscopic redshifts from two observation campaigns in the COSMOS (105) and the GOODS-South (13) fields" (2.1 Sample and ancillary data)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: _not stated_
- frequencies and spectral setup: lower sidebands: continuum + [CII]; upper sidebands: continuum only  
  > "The lower side bands were used for both continuum measurements and the \[CII\] $158\,\rm{\mu m}$ emission line expected from the redshifts, and the upper side bands covered the dust continuum only." (2.2 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: antenna configurations C43-1 and C43-2  
  > "using antenna configurations C43-1 and C43-2" (2.2 ALMA observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median 1.1" (0.9-1.6")  
  > "1.1$^{\prime\prime}$($0.9-1.6^{\prime\prime}$), respectively." (2.2 ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: median 41 uJy/beam (16.8-72.1)  
  > "$41\, \rm{\mu Jy/beam}$ ($16.8-72.1\, \rm{\mu Jy/beam}$)" (2.2 ALMA observations and data reduction)
- time on source: 15-45 min, average 22 min  
  > "The integration times ranged from 15 to 45 minutes, with an average of 22 minutes." (2.2 ALMA observations and data reduction)
- observing dates: 07 May 2018 (Cycle 5) to 10 January 2019 (Cycle 6)  
  > "ALMA observed our sample between 07 May, 2018 (Cycle 5) and 10 January, 2019 (Cycle 6)" (2.2 ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- Other facility **Herschel, AzTEC/ASTE, SCUBA2 (COSMOS)**: multiwavelength data used by Bethermin+2020 to build stacked FIR SED/template  
  > "This includes deep *Herschel* (cite: Lutz2011; Oliver2012), AzTEC/ASTE (cite: Aretxaga2011), and SCUBA2 data (cite: Casey2013)." (4.1)
- External data: SED-based SFR, M*, L_UV, beta from ancillary data  
  > "We adopt these SED-based quantities from (cite: Faisst2019) for this paper." (2.1 Sample and ancillary data) [from (cite: Faisst2019)]
- External data: L158um to L_IR conversion nu L_nu/L_IR=0.13 (FIR template)  
  > "$\nu_{158\,\rm{\mu m}}\,L_{\nu_{158\,\rm{\mu m}}}/L_{\rm{IR}}=0.13$ (cite: Bethermin2019)" (4.1) [from (cite: Bethermin2019)]
- External data: Serendipitous source catalog (>5 sigma) used for masking  
  > "based on the serendipitous detection catalog from (cite: Bethermin2019)" (3.2 Stacking analysis) [from (cite: Bethermin2019)]
- External data: Morpho-kinematic classification of [CII]  
  > "our sample was classified as rotators (9 galaxies), mergers (31 galaxies), extended dispersion dominated (15 galaxies), and compact dispersion dominated (8 galaxies)" (4.1.3) [from (cite: Lefevre2019)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline basic calibration plus extra flagging of bad antennae  
  > "After a basic calibration using the pipeline of the Common Astronomy Software Applications package (cite: Mcmullin2007), and additional flagging for bad antennae" (2.2 ALMA observations and data reduction)
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
  > "we imaged continuum maps using the CASA task with the natural weighting scheme to maximise sensitivity." (2.2 ALMA observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: exclude channels within ±3 sigma of [CII] width; extend masks by ~0.1-0.2 GHz for complex lines  
  > "we excluded channels within the $\pm3\,\sigma$ width of the detected \[CII\] emission lines" (2.2 ALMA observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction and detection criteria (3.5 sigma, fidelity >95%)  
  > "The details of the ALMA observations and the data reduction are presented in (cite: Bethermin2019)." (2.2 ALMA observations and data reduction) [from (cite: Bethermin2019)]
- Image-based stacking method  
  > "We used image based stacking as described in Khusanova (in preparation)" (3.2 Stacking analysis) [from Khusanova (in preparation)]
- beta0=-2.62 baseline  
  > "(cite: Reddy2018) derived a more appropriate value of $\beta_0=-2.62$ for early galaxies" (4.1.2) [from (cite: Reddy2018)]

### Not stated but needed to reproduce (our reading)

- Imaging details (cell size, image size, tclean parameters, line-mask channel lists per source)
- Custom 2D Gaussian fitting routine not released
- Fitting method for dA_FUV/dbeta (likelihood, handling of upper limits) not described
- Bootstrap settings for stack uncertainties
- Number of stacks' weighting details beyond formula; Khusanova stacking code unavailable

## Analysis recipe

1. **Measure continuum fluxes and upper limits**: 2D Gaussian fitting at UV position; 3.5 sigma detection within 2" ; 3 sigma upper limits from max flux in 2" plus 3x RMS  
  > "We determined $3\,\sigma$ upper limits by searching the maximum flux within 2$^{\prime\prime}$ diameter of the UV counterpart position, and by adding three times the background RMS to that maximum value." (2.3)
   - software: CASA
   - fitting: Uncertainties following Condon 1997  
  > "Flux measurement uncertainties were estimated using a method provided by (cite: Condon1997)" (2.3)
   - validation: _not stated_
2. **Convert 158um flux to L_IR, IRX, SFR**: Normalise Bethermin+2017 template (<U>=50, Td~41 K) to 158um flux, integrate 8-1000 um; SFR_IR=2.64e-44 L_IR  
  > "our template was normalised to the continuum fluxes or $3\,\sigma$ upper limits measured at rest-frame $158\,\rm{\mu m}$, and then integrated over the wavelength range $8-1000\,{\rm \mu m}$." (4.1)
   - assumption: Single mean FIR template, Td~41 K, Chabrier IMF, cosmology (0.3,0.7,0.7)  
  > "we do not have constraints on the FIR SEDs of individual galaxies." (4.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stack continuum images in bins**: Weighted median stacking (weights L_UV,median/L_UV,i), serendipitous sources >5 sigma masked, aperture r=1.5"; bins by z (<5, >5), beta and M*  
  > "Flux densities were measured from the stacks using aperture photometry ($r=1.5^{\prime\prime}$), and the measurement uncertainties were estimated by boot strapping." (3.2 Stacking analysis)
   - fitting: _not stated_
   - validation: Compared with unweighted median stacks and FIR-centred stacks; results consistent  
  > "For testing purposes, we also computed unweighted median stacks, which did not differ significantly from our weighted medians." (3.2 Stacking analysis)
4. **Fit IRX-beta attenuation slope**: Fit stacked IRX with IRX=1.75(10^{0.4 dA/dbeta (beta-beta0)}-1) at fixed beta0=-2.62 (and -2.23)  
  > "IRX} =  1.75 \times \left( 10^{0.4\frac{d\,A_{\rm FUV}}{d\beta}(\beta - \beta_0)} -1 \right)" (4.1)
   - assumption: BC_UV=1.75; SMC-like 1.1, Meurer 1.99  
  > "here we used $BC_{\rm UV}=1.75$" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute obscured fraction**: f_obs=SFR_IR/(SFR_UV+SFR_IR) and compare with Whitaker+2017  
  > "$f_{\rm obs}={\rm SFR_{IR}/SFR_{tot}}$" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : pipeline calibration and continuum imaging  
  > "Common Astronomy Software Applications package (cite: Mcmullin2007)" (2.2 ALMA observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of continuum detections | 23 | not stated | galaxies | 1 | In total, 23 of our galaxies have continuum detections at this level. |
| dA_FUV/dbeta (beta0=-2.62), z~4.5 | 0.71 | 0.15 | dimensionless | 4 | $d\,A_{\rm FUV}/d\beta = 0.71\pm0.15$ at $z\sim4.5$ |
| dA_FUV/dbeta (beta0=-2.62), z~5.5 | 0.48 | 0.13 | dimensionless | 4 | $d\,A_{\rm FUV}/d\beta = 0.48\pm0.13$ at $z\sim5.5$ |
| dA_FUV/dbeta (beta0=-2.23), z~4.5 and 5.5 | 1.01 and 0.74 | 0.20 and 0.24 | dimensionless | 4 | 4.5 / $0.71\pm0.15$ / $1.01\pm0.20$ |
| f_obs, M*>1e10, z~4.5 | 0.67 | +0.05/-0.07 | dimensionless | 5 | $f_{\rm obs}=0.67^{+0.05}_{-0.07}$ at $z\sim4.5$ |
| f_obs, M*>1e10, z~5.5 | 0.44 | ±0.11 | dimensionless | 5 | only $f_{\rm obs}=0.44^{+0.11}_{-0.11}$ at $z\sim5.5$ |
| f_obs, M*<1e10, z~4.5 | 0.36 | +0.13/-0.19 | dimensionless | 5 | $f_{\rm obs}=0.36^{+0.13}_{-0.19}$ at $z\sim4.5$ |

## Qualitative findings

- IRX-beta at z>4 favours SMC-like or steeper attenuation than Meurer; IRX-M* lower by up to ~1 dex at z~5.5  
  > "The attenuation curve is similar to or even steeper than that of the extinction curve of the Small Magellanic Cloud (SMC)." (abstract)

## Claim tuples

- H: The IRX-beta relation at z~4.4-5.8 follows the Meurer relation | E: Individual detections, upper limits and stacks fitted with IRX-beta relation | R: dA/dbeta=0.71±0.15 (z~4.5), 0.48±0.13 (z~5.5) | F: Attenuation curve is SMC-like or steeper; Meurer rejected | **supported**
- H: IRX-M* relation does not evolve to z~5.5 | E: Stacks in two mass bins compared with z<4 relations | R: IRX lower by ~0.6 dex at z~4.5 and ~1 dex at z~5.5 for massive bin | F: Rapid evolution of IRX-M* at z>4 | **supported**
- H: Obscured fraction is constant with redshift | E: f_obs from SFR_IR and SFR_UV in stacks | R: ~65% at z~4.5 to ~45% at z~5.5 for massive galaxies | F: Obscured fraction decreases rapidly at z>4 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Stacking of detections and nondetections to get population averages since individual constraints are limited  
  > "we performed a stacking analysis of all ALMA continuum images, including both individual detections and nondetections." (3.2 Stacking analysis)
- Alternative: Classical beta0=-2.23 tested as alternative to -2.62; conclusion unchanged  
  > "even if we change $\beta_0$ to the classical value from M99 of $\beta_0=-2.23$, we still derive a best-fit" (4.1.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample not mass complete, UV-selected; dusty massive galaxies missing; single FIR template for all galaxies  
  > "One likely caveat of our analysis is that our sample is not perfectly mass complete." (4.3)
- Caveat (inferred, ours): L_IR depends on one assumed FIR template (Td~41 K); IRX conclusions sensitive to it
- Caveat (inferred, ours): Fit procedure and treatment of upper limits not specified
- Caveat (inferred, ours): Stacking in coarse bins with few sources

## Reproducibility

- Data public (paper): ALMA data acknowledged as ADS/JAO.ALMA#2017.1.00428.L  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00428.L." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Khusanova stacking method
- Missing: Faisst+2019 SED quantities and Bethermin+2020 catalog needed
- Missing: Custom flux-fitting routine
- Missing: Fit details
- Data volume (inferred): ~100-200 GB raw for 118 pointings (reduced products much smaller)
- Score (inferred): 3/5, Public data and clear equations, but relies on companion-paper catalogs and unreleased stacking code.
- Rediscovery candidate: no, Requires external catalogs and unpublished stacking/fit details.

## Links

- Method: (cite: Bethermin2019) (ALPINE data reduction, continuum catalog, L_IR conversion)
- Method: (cite: Faisst2019) (SED fitting and ancillary data)
- Method: (cite: Lefevre2019) (Survey description)
- Companion: (cite: Schaerer2020) (uses the fiducial L_IR for total SFRs)
- Companion: (cite: Fujimoto2020) (UV vs FIR positional offsets)
- Related: ALPINE
- Related: COSMOS
- Related: GOODS-South

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "stated": 35,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
