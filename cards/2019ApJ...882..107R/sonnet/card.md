# ALMA 200 pc Resolution Imaging of Smooth Cold Dusty Disks in Typical z ∼ 3 Star-forming Galaxies

`2019ApJ...882..107R` | The Astrophysical Journal 2019 | first author: Rujopakarn, W. | arXiv: 1904.04507 | DOI: 10.3847/1538-4357/ab3791

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do typical main-sequence z~3 star-forming galaxies show star-forming dust clumps/substructures at 200-pc resolution, and how do they compare with SMGs?  
  > "No dust substructures or clumps are seen down to $\simeq 1- 3$ $M_\odot$yr$^{-1}$ (1$\sigma$) per 200-pc beam." (abstract)
- Target **UDF1**: coordinates RA 53.18347 deg, Dec -27.77666 deg  
  > "| UDF1 | 53.18347 | $-27.77666$ | 2.698 |" (Table 1); z/distance z = 2.698  
  > "| UDF1 | 53.18347 | $-27.77666$ | 2.698 |" (Table 1); distance from spectroscopic z from ASPECS Band 3  
  > "| UDF1 | 53.18347 | $-27.77666$ | 2.698 |" (Table 1)
- Target **UDF2**: coordinates RA 53.18137 deg, Dec -27.77758 deg  
  > "| UDF2 | 53.18137 | $-27.77758$ | 2.696 |" (Table 1); z/distance z = 2.696  
  > "| UDF2 | 53.18137 | $-27.77758$ | 2.696 |" (Table 1); distance from spectroscopic z from ASPECS  
  > "| UDF2 | 53.18137 | $-27.77758$ | 2.696 |" (Table 1)
- Target **UDF7**: coordinates RA 53.18053 deg, Dec -27.77971 deg  
  > "| UDF7 | 53.18053 | $-27.77971$ | 2.59 |" (Table 1); z/distance z = 2.59  
  > "| UDF7 | 53.18053 | $-27.77971$ | 2.59 |" (Table 1); distance from photometric redshift  
  > "| UDF7 | 53.18053 | $-27.77971$ | 2.59 |" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00001.S, 2016.1.00048.S, 2015.1.00948.S, 2012.1.00173.S
- bands: Band 7, 343.5 GHz (870 um)  
  > "We used the ALMA Band 7 receivers in the single-continuum mode, tuned to a central frequency of 343.5 GHz." (2.1 ALMA Observations)
- frequencies and spectral setup: 4 SPWs, 128 channels, 1875 MHz each, 7.5 GHz total  
  > "each SPW comprises 128 channels and covers 1875 MHz, resulting in 7.5 GHz of aggregate bandwidth" (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 43 antennas, extended configuration, baselines 92-8548 m  
  > "The observations were carried out using 43 antennas in an extended configuration with baselines ranging from 92 to 8548 m" (2.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: nominal 31 mas; final beam 42 x 30 mas  
  > "is 31 mas, corresponding to 240 pc at $z = 3$" (2.1 ALMA Observations)
- max recoverable scale: 0.60 arcsec  
  > "is 0.60$''$ for the array" (2.1 ALMA Observations)
- sensitivity: 11 uJy/beam rms  
  > "well fit by a Gaussian with a rms of 11 $\mu$Jy beam$^{-1}$" (2.2)
- time on source: 3.2 hr on source, 5.2 hr total  
  > "the observations took 5.2 hr, with 3.2 hr being on-source integration" (2.1 ALMA Observations)
- observing dates: 2017 November 23-24, four observing blocks  
  > "taken in four observing blocks during 2017 November $23-24$" (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **HST**: 0.4-1.6 um imaging (HUDF12/XDF) for optical morphology  
  > "The *HST* images at $0.4-1.6$ $\mu$m that reach $29.8-30.3$ mag (5$\sigma$, AB) are from the HUDF12 and XDF data releases" (2.5 Ancillary Data)
- Other facility **Spitzer/Herschel**: 3.6-500 um photometry for SED fitting  
  > "*Spitzer* and *Herschel* catalogs at $3.6-500$ $\mu$m" (2.5 Ancillary Data)
- Other facility **VLA**: 6 GHz imaging, radio luminosities  
  > "Ultra-deep VLA observations at 6 GHz reach 0.32 $\mu$Jy beam$^{-1}$ rms" (2.5 Ancillary Data)
- Other facility **Chandra**: 7 Ms X-ray survey for AGN identification  
  > "The *Chandra* 7 Ms X-ray survey (cite: Luo17) is used to identify X-ray AGNs." (2.5 Ancillary Data)
- External data: ALMA 1.3 mm HUDF survey source catalog/fluxes (sample selection)  
  > "The three galaxies in this sample were selected from the ALMA HUDF Survey at 1.3 mm (cite: Dunlop17)." (2 Observations) [from (cite: Dunlop17)]
- External data: Deblended far-IR photometric catalog  
  > "a new, deblended far-IR photometric catalog described by (cite: Elbaz18) is used in this work" (2.5 Ancillary Data) [from (cite: Elbaz18)]
- External data: HST astrometric offsets  
  > "We have corrected all *HST* images for the astrometric offsets reported by (cite: Rujopakarn16)" (2.5 Ancillary Data) [from (cite: Rujopakarn16)]
- External data: Photometric compilation for stellar masses  
  > "utilizing the most recent revision of the (cite: Barro11) photometric compilation" (2.5 Ancillary Data) [from (cite: Barro11)]
- External data: H19 SMG stellar masses (MAGPHYS) and redshifts  
  > "those from H19 based on the energy-balancing `MAGPHYS` tabulated" (Table 3 notes) [from (cite: Hodge19)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline  
  > "We processed the raw visibilities using the ALMA calibration pipeline in CASA (version 5.1.1-5)" (2.2)
- casa version: CASA 5.1.1-5  
  > "ALMA calibration pipeline in CASA (version 5.1.1-5)" (2.2)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (bandpass and flux scale); J0348-2749 phase  
  > "J0522$-$3627 for bandpass and flux density scale calibrations; J0348$-$2749 for phase" (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "imaged the calibrated visibilities with the CASA task `tclean`" (2.2)
- deconvolver: Hogbom minor cycle, MFS  
  > "`MFS` spectral definition mode, and the Högbom minor cycle algorithm" (2.2)
- weighting robust: Briggs robust = 0.5  
  > "Briggs weighting with the `robust` parameter of 0.5" (2.2)
- uv taper: _not stated_
- cell size: 6 mas  
  > "The final CASA image was made with a cell size of 6 mas" (2.2)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: done within tclean  
  > "The primary beam attenuation correction is done with `tclean` during this step." (2.2)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 42 x 30 mas, PA 77.8 deg  
  > "The final image has a synthesized beam FWHM of $42 \times 30$ mas" (2.2)
- final rms: 11 uJy/beam  
  > "rms of 11 $\mu$Jy beam$^{-1}$" (2.2)

### Inherited from earlier work

- Mixture-of-Gaussians representation of Sersic profiles in uv-plane  
  > "(cite: HoggLang13) have shown that linear superposition of Gaussians (“mixture-of-Gaussian” in the Hogg & Lang nomenclature) can accurately describe" (2.3) [from (cite: HoggLang13)]
- L_IR and M_dust from SED fitting following Magdis12 with Draine & Li models; gas mass via GDR(Z)  
  > "We estimate total IR luminosities, $L_{\rm IR}$, and dust masses, $M_{\rm dust}$, following (cite: Magdis12)" (2.5 Ancillary Data) [from (cite: Magdis12)]
- SFR from L_IR via Kennicutt relation with 0.66 Chabrier factor  
  > "The $L_{\rm IR}$ is used to estimate the SFR via the (cite: Kennicutt98) relation, with a factor of 0.66 adjustment" (2.5 Ancillary Data) [from (cite: Kennicutt98)]

### Not stated but needed to reproduce (our reading)

- Exact tclean niter, threshold, image size and masking used for the final image
- Line-free channel handling (none needed, but spectral window flagging not stated)
- Multiscale scales used for final image
- GILDAS uv_fit starting guesses and model-selection details
- SED-fitting photometry values and priors for L_IR, M_dust
- GALFIT setup details (PSF, masks, initial guesses)
- Flux scale uncertainty

## Analysis recipe

1. **Calibrate and image**: ALMA pipeline calibration then tclean with Briggs robust 0.5, Hogbom, cell 6 mas  
  > "We processed the raw visibilities using the ALMA calibration pipeline in CASA (version 5.1.1-5) and imaged the calibrated visibilities with the CASA task `tclean`." (2.2)
   - software: CASA, tclean
   - parameter: robust = 0.5, cell 6 mas  
  > "Briggs weighting with the `robust` parameter of 0.5" (2.2)
   - fitting: _not stated_
   - validation: Tested gridder wproject, niter/threshold, masking; images insensitive  
  > "The resulting images are insensitive to whether source masking is employed during deconvolution." (2.2)
2. **uv-plane morphological fitting**: Fit point, circular and elliptical Gaussians to visibilities simultaneously for all components, until residuals show no peaks >=3 sigma  
  > "We fitted source models to the visibilities using the task `uv_fit`, fitting all components of all three galaxies simultaneously, and subtracted the models from the data." (2.3)
   - software: GILDAS, CASA
   - parameter: all parameters free; fluxes corrected with tclean primary beam  
  > "We allow all parameters to be free (i.e., no parameter fixing) in the modeling." (2.3)
   - fitting: uv_fit least squares; two nested Gaussians approximate Sersic  
  > "We found that good fits were obtained with two nested Gaussians" (2.3)
   - validation: Residual rms 10 uJy/beam consistent with tclean image noise  
  > "has rms noise of 10 $\mu$Jy beam$^{-1}$, consistent with that of the source-free region" (2.3)
3. **Assess astrometric and morphological fidelity**: uv fits of check source and phase/flux calibrators  
  > "we measured the positional offset of the ‘check source’ that is observed as a part of each schedule block, J0336$-$2644" (2.4)
   - software: GILDAS
   - fitting: _not stated_
   - validation: Phase calibrator FWHM 2.30 mas  
  > "is well described by a circular Gaussian with FWHM of $2.30 \pm 0.02$ mas" (2.4)
4. **Ancillary SED/stellar mass/HST morphology**: Stellar mass from HYPERZ and PPG08 averaged; GALFIT of H160; L_IR, M_dust from Draine&Li SED fit; SFR via Kennicutt  
  > "We estimate the spatially-integrated stellar mass ($M_*$) using `HYPERZ` (cite: Bolzonella00) and the (cite: PPG08) SED fitting codes" (2.5 Ancillary Data)
   - software: HYPERZ, GALFIT, EAZY
   - assumption: solar metallicity, GDR(Zsun) ~ 90; Chabrier IMF; Calzetti law, A_V up to 5  
  > "we adopt a solar metallicity that corresponds to GDR($Z_{\odot}$) $\approx 90$" (2.5 Ancillary Data)
   - fitting: _not stated_
   - validation: Two codes agree within 0.1-0.2 dex; EAZY check  
  > "The stellar mass estimates from the two codes agreed within $0.1-0.2$ dex" (2.5 Ancillary Data)
5. **Limits on substructure SFR and SFR surface density maps**: Scale local 870 um residual noise per beam to total flux and total SED SFR; build Sigma_SFR from noise-free Gaussian models  
  > "We quantify the upper SFR limit of substructures by scaling the local 870 $\mu$m residual noise per beam to the total 870 $\mu$m flux" (3.2)
   - assumption: dust temperature and IMF do not vary within each source  
  > "this approach assumes that the dust temperature and IMF do not vary within each source" (3.2)
   - fitting: _not stated_
   - validation: Expected ~3 stochastic 3-sigma peaks per ~10^3 beams; fewer found  
  > "Given that each cutout contains $\approx 10^3$ beams, we expect up to $\simeq3$ stochastic $3\sigma$ peaks from ideal Gaussian noise." (3.2)
6. **Compare with H19 SMGs**: Same GILDAS uv-plane procedure applied to archival 2016.1.00048.S pipeline products; identify substructures by subtracting dominant components  
  > "analyzed the calibrated visibilities in the $uv$ plane with GILDAS using the identical procedure as for our data" (4.2.3)
   - software: GILDAS, MAGPHYS, HYPERZ
   - assumption: SFR linear with rest 150-350 um dust emission (constant T_dust and IMF)  
  > "Assuming a constant dust temperature and IMF, i.e., that the SFR varies linearly with the rest-frame $150-350$ $\mu$m dust emission" (4.2.3)
   - fitting: _not stated_
   - validation: Agrees with H19 image-plane results qualitatively  
  > "Our images are similar to those in H19 from modeling in the image plane" (4.2.3)

## Software

- **CASA** 5.1.1-5: pipeline calibration, tclean imaging, exportuvfits  
  > "ALMA calibration pipeline in CASA (version 5.1.1-5)" (2.2)
- **GILDAS** jul18a: uv-plane model fitting (uv_fit)  
  > "We carried out the $uv$-based morphological analysis using GILDAS (version `jul18a`" (2.3)
- **GALFIT** : HST H160 morphology  
  > "We use GALFIT (cite: Peng10) to model and decompose the *HST* $H_{160}$ images" (2.5 Ancillary Data)
- **HYPERZ** : stellar mass SED fitting  
  > "using `HYPERZ` (cite: Bolzonella00)" (2.5 Ancillary Data)
- **EAZY** : cross-check of stellar masses  
  > "estimated with EAZY (cite: Brammer08) using the (cite: Conroy09) Flexible Stellar Population Synthesis" (2.5 Ancillary Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| UDF1 component 1 flux | 1.84 | 0.16 | mJy | 2 | integrated fluxes of 1.56 $\pm$ 0.16 mJy and 1.84 $\pm$ 0.16 mJy |
| UDF2 disk flux | 2.0 | 0.1 | mJy | 2 | with an integrated flux of $2.0 \pm 0.1$ mJy |
| UDF2 total flux | 2.80 | 0.1 | mJy | 2 | yielding a combined flux of $2.80 \pm 0.1$ mJy |
| UDF7 Gaussian flux | 0.58 | 0.05 | mJy | 2 | containing $0.58 \pm 0.05$ mJy of integrated flux |
| 1-sigma SFR sensitivity per 200-pc beam (UDF1, 2, 7) | 1.9, 0.9, 2.8 | not stated | Msun/yr | 5 | are 1.9, 0.9, 2.8 $M_\odot$yr$^{-1}$, respectively |
| Max clump fraction of total SFR (3 sigma) | 1, 1, 7 | not stated | percent | 5 | no more than $\simeq$ 1, 1, and 7% respectively (3$\sigma$ upper limits |
| Astrometric offset of check source (RA, Dec) | 1.07, 1.65 | 0.05, 0.04 | mas | 3 | $1.07 \pm 0.05$ and $1.65 \pm 0.04$ mas |
| Total SFR UDF1, UDF2, UDF7 | 444, 257, 116 | 5, 4, 1 | Msun/yr | 4 | $444 \pm 5$ |
| H19 SMG substructure SFR fractions | 4-10 (two up to 30-36) | not stated | percent | 6 | the typical fractional SFRs in substructures in the H19 SMGs range from 4 to 10%, with two substructures being as large as $30-36$% |

## Qualitative findings

- Cold dust is smooth, well fit by two concentric Gaussians, with no emission at UV clump positions  
  > "We find the distributions of cold dust emission at this physical resolution to be remarkably smooth, showing no sign of clumpy star formation." (3 Results)

## Claim tuples

- H: Typical z~3 SFGs host star-forming dust clumps at 200 pc scale | E: 30 mas ALMA 870 um imaging and uv-plane modeling of three HUDF SFGs | R: Residuals show no >=3 sigma peaks; clump upper limits 1-7% of SFR | F: Dust disks are smooth; no substructures | **supported**
- H: UV-bright clumps are sites of significant obscured star formation | E: Compare ALMA with HST maps | R: No dust emission at UV clumps 2-10 kpc away | F: UV clumps are not dust-obscured star-forming sites | **supported**
- H: SMG substructures differ from those in typical SFGs | E: Same uv analysis on H19 data | R: SMGs need multiple extra components containing 10-30% SFR | F: SMGs may arise from more disruptive events involving multiple objects | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane analysis uses information from long baselines and is not susceptible to imaging parameters  
  > "While this analysis is not susceptible to imaging parameters and has the potential to utilize information from the longest baselines" (2.3)
- Alternative: wproject gridder and multiscale cleaning tested; no improvement or biases morphology  
  > "found no significant improvement between the gridder choice of standard versus `wproject`" (2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited by surface brightness sensitivity for clumps larger than the beam; small sample  
  > "we are limited by the surface brightness sensitivity of our observations" (3.2)
- Limitation (authors): Assumes constant dust temperature and IMF within each galaxy  
  > "the implicit assumptions that the dust temperature and IMF do not vary spatially within each galaxy are likely to be challenged" (3.3)
- Caveat (inferred, ours): Only three galaxies; conclusions about typical SFGs not statistically robust
- Caveat (inferred, ours): Model-dependent substructure limits (Gaussian decomposition)
- Caveat (inferred, ours): H19 stellar masses disagree with own; SMG/SFG comparison uncertain
- Caveat (inferred, ours): Imaging details (multiscale) alter structure but uv fits mitigate

## Reproducibility

- Data public (paper): Archival ALMA data used for H19 comparison; project codes listed  
  > "we took the pipeline product of the H19 archival data (ALMA#2016.1.00048.S)" (4.2.3)
- Products in archive: _not stated_
- Missing: Full tclean parameters (niter, threshold, imsize)
- Missing: uv_fit starting models
- Missing: SED photometry tables and fitting priors
- Missing: GALFIT configuration
- Data volume (inferred): ~100-300 GB raw for 4 EBs of extended Band 7 plus H19 data
- Score (inferred): 3/5, Public data and clear uv-fit procedure, but many imaging and SED fitting details missing.
- Rediscovery candidate: yes, Public data, main results numeric (component fluxes/sizes), recipe mostly specified via pipeline plus GILDAS uv_fit.

## Links

- Method: (cite: HoggLang13) (Mixture-of-Gaussians for Sersic profiles)
- Method: (cite: Magdis12) (Dust mass and gas mass method)
- Companion: (cite: Hodge19) (Comparison SMG sample and data)
- Companion: (cite: Dunlop17) (Parent HUDF 1.3 mm survey)
- Companion: (cite: Rujopakarn16) (Earlier ALMA/VLA HUDF imaging)
- Related: ALMA HUDF 1.3 mm survey
- Related: ASPECS
- Related: ALESS

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 69,
  "rate": 0.742
 },
 "evidence_ok": true
}
```
