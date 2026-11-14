# ALMA Reveals Weak [N II] Emission in "Typical" Galaxies and Intense Starbursts at z = 5-6

`2016ApJ...832..151P` | The Astrophysical Journal 2016 | first author: Pavesi, Riccardo | arXiv: 1607.02520 | DOI: 10.3847/0004-637X/832/2/151

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How much ionized gas contributes to [CII] emission in z=5-6 galaxies spanning a wide SFR range, as probed by the [NII] 205 um line and the [CII]/[NII] ratio  
  > "Our results show at least two different regimes of ionized inter-stellar medium properties for galaxies in the first billion years of cosmic time, separated by their $L_{\rm [CII]}/L_{\rm [NII]}$ ratio." (abstract)
- Target **AzTEC-3**: coordinates _not stated_; z/distance z=5.29795  
  > "We detect the [Nii] line (Table [\[table_lines\]](#table_lines)) in AzTEC-3 at 5$\sigma$ confidence in the mosaic of the AzTEC-3 pointing and the LBG-1 pointing" (Results 3.1); distance from [CII] line, Table 1 (this work)  
  > "We detect the [Nii] line (Table [\[table_lines\]](#table_lines)) in AzTEC-3 at 5$\sigma$ confidence in the mosaic of the AzTEC-3 pointing and the LBG-1 pointing" (Results 3.1)
- Target **HZ10**: coordinates _not stated_; z/distance z=5.6543  
  > "We detect the [Nii] line in HZ10 with an integrated significance of $\sim 5.3\sigma$" (Results 3.2); distance from [CII] line, Table 1 (this work)  
  > "We detect the [Nii] line in HZ10 with an integrated significance of $\sim 5.3\sigma$" (Results 3.2)
- Target **LBG-1**: coordinates _not stated_; z/distance z=5.29359  
  > "Our sensitive data on LBG-1 only resulted in a tentative ($2\sigma$) detection of the [Nii] line at $(0.2\pm0.1)\,$mJy peak flux." (Results 3.3); distance from [CII] line, Table 1 (this work)  
  > "Our sensitive data on LBG-1 only resulted in a tentative ($2\sigma$) detection of the [Nii] line at $(0.2\pm0.1)\,$mJy peak flux." (Results 3.3)

## Data provenance

- ALMA projects: 2015.1.00928.S, 2011.0.00064.S, 2012.1.00523.S, 2011.0.00006.SV, 2013.1.00745.S
- bands: Band 6 ([NII], new Cycle 3); Band 7 ([CII], archival Cycles 0/1)  
  > "using ALMA in Band 6" (2.1); "The Cycle-1 observations were taken on 2013 November 15-16 in band 7" (2.2)
- frequencies and spectral setup: 4 spectral windows of 1.875 GHz at 3.9 MHz (~5 km/s) resolution, [NII] centred in one window  
  > "the correlator was set up to cover two spectral windows of 1.875 GHz bandwidth each at $3.9\,$MHz ($\sim5\,$km s$^{-1}$) resolution (dual polarization) in each sideband." (2.1)
- continuum bandwidth: _not stated_
- arrays: 12m array, 32-47 usable antennae  
  > "with 32–47 usable $12\,$m antennae under good weather conditions at 1.3 mm" (2.1)
- configurations: 3 tracks compact (max baseline ~300 m), one LBG-1 track 15 m to 6 km  
  > "using 3 tracks in a compact configuration (max. baseline $\sim300\,$m) and one track on LBG-1 in transition from an extended to a compact configuration" (2.1)
- baselines: _not stated_
- angular resolution: 1.4x1.2 arcsec (mosaic), 1.3x1.1 (LBG-1), 1.7x1.2 (HZ10)  
  > "The mosaic has a synthesized beam size of $1.4^{\prime\prime} \times 1.2^{\prime\prime}$" (2.1)
- max recoverable scale: _not stated_
- sensitivity: line rms ~0.34 (AzTEC-3), 0.21 (LBG-1) mJy/beam in 41 km/s channels; HZ10 ~0.2 mJy/beam in 44 km/s  
  > "the rms noise is $\sim0.34\,$mJy beam$^{-1}$ at the position of AzTEC-3 in $41\,$km s$^{-1}$ wide channels" (2.1)
- time on source: 25 min AzTEC-3, 50 min HZ10, 64 min LBG-1  
  > "total on-source times of $25\,$min for AzTEC-3, $50\,$min for HZ10 and $64\,$min for LBG-1" (2.1)
- observing dates: 2015 Dec 16 to 2016 Jan 14 (Cycle 3)  
  > "for 4 tracks between 2015 December 16 and 2016 January 14" (2.1)
- pi or archival as stated: _not stated_
- Line: [NII] 3P1-3P0 205 um (1461.131 GHz)
- Line: [CII] 158 um (not stated)
- Other facility **Keck/DEIMOS**: rest-UV spectrum of HZ10 (COSMOS DEIMOS survey)  
  > "taken with Keck/DEIMOS as part of the COSMOS DEIMOS spectroscopic survey (PI: Capak)" (5.2)
- Other facility **Spitzer IRAC**: [3.6]-[4.5] colours from COSMOS2015 catalog  
  > "From the COSMOS2015 catalog (cite: Lcosm16) we calculate a color of $0.48\,$mag" (5.1)
- External data: Archival [CII] ALMA data of AzTEC-3 and LBG-1 (Cycle 0)  
  > "have previously been presented by R14 for the Cycle-0 observations of AzTEC-3 and LBG-1" (2.2) [from (cite: R14)]
- External data: Archival [CII] ALMA data of HZ10 and LBG-1 (Cycle 1)  
  > "by C15 for the Cycle-1 observations of HZ10 and LBG-1 (referred to as HZ6 by C15)" (2.2) [from (cite: C15)]
- External data: Local galaxy and high-z [CII]/[NII] comparison samples  
  > "than observed in local (U)LIRGs (cite: F13; K16; Ro15; DS; Z16)" (5.1) [from (cite: Z16; DS; D14)]
- Simulation/model as data: Cloudy 13.03 grid with Starburst99 input spectra, ages 1 and 10 Myr, varying density and ionization parameter  
  > "we have run a grid of Cloudy models using version 13.03 (cite: cl)." (4)

## Processing

### Calibration

- pipeline or manual: Archive scripted pipelines modified for CASA 4.5 (archival data re-calibrated)  
  > "using the scripted pipelines on the archive after appropriately modifying them to be executed with CASA 4.5" (2.2)
- casa version: CASA 4.5  
  > "The Common Astronomy Software Application (CASA) version 4.5 was used for data reduction and analysis." (2.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Cycle 3: J1058+0133, J0854+2006, Ganymede; flux scheme Butler-JPL-Horizons 2012  
  > "J1058+0133 and J0854+2006 were observed for bandpass and flux calibration, and Ganymede was also used for flux calibration of two tracks." (2.1)
- flux scale uncertainty: ~10%  
  > "We estimate the overall accuracy of the flux calibration to be within $\sim10\%$." (2.1)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA 4.5; mosaic for AzTEC-3+LBG-1  
  > "All images and mosaics were produced with the CLEAN algorithm, using natural weighting for maximal sensitivity." (2.1)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting for maximal sensitivity" (2.1)
- uv taper: 300 kλ outer taper for LBG-1  
  > "We also apply an outer taper of $300\,$k$\lambda$ to the LBG-1 observations" (2.1)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.4x1.2'' mosaic; 1.3x1.1'' LBG-1; 1.7x1.2'' HZ10  
  > "For HZ10, the imaging results in a synthesized beam size of $1.7^{\prime\prime} \times 1.2^{\prime\prime}$" (2.1)
- final rms: continuum ~20 and ~15 uJy/beam (mosaic), ~16 (LBG-1), ~35 (HZ10)  
  > "The rms noise in the continuum maps are $\sim 20\,\mu$Jy beam$^{-1}$ and $\sim 15\,\mu$Jy beam$^{-1}$ at the positions of AzTEC-3 and LBG-1 in the mosaic" (2.1)

### Inherited from earlier work

- Cycle-0 [CII] data and AzTEC-3/LBG-1 properties (SED, dust mass, alpha_CO limit)  
  > "The ALMA data targeting the [Cii] lines for our sample galaxies have previously been presented by R14" (2.2) [from (cite: R14)]
- Cycle-1 HZ10/LBG-1 [CII] data and FIR luminosity comparisons  
  > "we here provide a brief description of the data that we have re-analyzed from C15" (2.2) [from (cite: C15)]
- Ionized-gas [CII]/[NII] ratio ~3.5 and C+/N+ abundance 1.8  
  > "Following (cite: O06), we assume a C$^+$/N$^+$ abundance ratio of $\sim1.8$ (cite: S96)" (5.1) [from (cite: O06; S96)]

### Not stated but needed to reproduce (our reading)

- Source coordinates / phase centres
- Line-free channels and continuum subtraction method
- CLEAN threshold, masks, cell and image size
- Exact aperture definitions and the x2 aperture correction implementation for each source
- MCMC sampler and likelihood details for the modified blackbody fit
- Cloudy grid values (densities, U) and inner-radius parameters
- Archive scheduling blocks / member IDs for each project

## Analysis recipe

1. **Calibrate and image data**: Re-calibrated archival Cycle 0/1 data with modified archive scripts; imaged all with CLEAN, natural weighting  
  > "We have produced image cubes and continuum maps using the CLEAN task with natural weighting in CASA 4.5." (2.2)
   - software: CASA
   - parameter: 300 kλ taper for LBG-1; mosaic of AzTEC-3 and LBG-1 pointings  
  > "We also apply an outer taper of $300\,$k$\lambda$ to the LBG-1 observations" (2.1)
   - fitting: _not stated_
   - validation: Mosaic vs single pointing results confirmed equivalent  
  > "after confirming that the results were equivalent in both cases" (2.1)
2. **Extract line spectra and fluxes**: Aperture spectra (apertures from [CII] size or [NII] Gaussian FWHM) with x2 correction; Gaussian line fits  
  > "all aperture spectra are extracted in apertures fitted to the FWHM of the spatial emission, and then corrected by a factor of $\times 2$" (Footnote 1)
   - parameter: AzTEC-3 aperture 1.5''x1.3''  
  > "we extract the [Nii] line spectrum using an aperture of $1.5^{\prime\prime} \times1.3^{\prime\prime}$" (3.1)
   - assumption: Gaussian spatial profiles  
  > "based on the assumption of Gaussian spatial profiles" (Footnote 1)
   - fitting: Gaussian line profile chi^2 fitting  
  > "Determined through $\chi^2$ fitting of a Gaussian line profile without imposing any priors on the line position or width." (Footnote 2)
   - validation: 2D Gaussian flux compared with aperture flux (~25% higher, within 1 sigma)  
  > "would result in [Nii] line flux which is $\sim$25% higher, compatible with our measurement to within $\sim1\sigma$" (3.1)
3. **Fit FIR SED of HZ10 and LBG-1**: MCMC modified blackbody fit to continuum measurements  
  > "we explore the parameter space of modified black-body models with a Markov chain Monte Carlo (MCMC) routine to fit the continuum measurements" (3.4)
   - parameter: FIR luminosity integrated over 42.5-122.5 um  
  > "The resulting FIR luminosities (between 42.5 and $122.5\,\mu$m)" (3.4)
   - assumption: Optically thin; Gaussian priors Td 30±20 K, beta 1.7±0.5  
  > "impose weak Gaussian priors on the dust temperature ($30\pm20\,$K) and $\beta$ ($1.7\pm0.5$)" (3.4)
   - fitting: MCMC; also tested uniform Td prior 10-100 K  
  > "If we relax the prior on the dust temperature to a uniform prior between 10–$100\,$K" (3.4)
   - validation: Compared with previous FIR estimates (C15)  
  > "compatible with previous estimates (C15)" (3.4)
4. **Model [CII]/[NII] with Cloudy**: Grid of constant-pressure spherical clouds to A_V=10, Starburst99 input, ages 1 and 10 Myr  
  > "We simulate constant pressure clouds with spherical geometry" (4)
   - software: Cloudy, Starburst99
   - parameter: Cloudy 13.03; inner radius 3 kpc; B field 1e-5 G  
  > "intensity of $10^{-5}\,$G at the inner edge" (4)
   - assumption: Solar abundances (N11), Orion-like dust  
  > "We adopt all gas element abundances for solar metallicity from (cite: N11) and include Orion-like dust" (4)
   - fitting: _not stated_
   - validation: Models used for trends only, not direct comparison  
  > "the precise values are model-dependent and should not be directly compared to the measured values" (4)
5. **Infer ionized fraction of [CII]**: Assume [CII]/[NII]=3.5 for ionized gas to derive fraction of [CII] from ionized gas  
  > "to infer a line luminosity ratio [Cii]$_{\rm ionized}$/[Nii]$\simeq$3.5, for ionized gas density in the range $\sim$10–$1000\,$cm$^{-3}$" (5.1)
   - assumption: Optically thin lines; C+/N+ ~1.8  
  > "The line emission needs to be optically thin in order to be additive." (Footnote 6)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5: Calibration, CLEAN imaging, analysis  
  > "The Common Astronomy Software Application (CASA) version 4.5 was used for data reduction and analysis." (2.1)
- **Cloudy** 13.03: Photoionization/PDR models of [CII]/[NII]  
  > "we have run a grid of Cloudy models using version 13.03" (4)
- **Starburst99** : Input stellar spectra for Cloudy  
  > "The input spectrum is taken from Starburst99 models (cite: stb99)" (4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L[CII]/L[NII] AzTEC-3 | 22 | ±8 | dimensionless | 2 | $22\pm8$ |
| L[CII]/L[NII] HZ10 | 19 | ±6 | dimensionless | 2 | The global [Cii] to [Nii] luminosity ratio obtained from the integrated line fluxes is $19\pm6$ for HZ10 |
| L[CII]/L[NII] LBG-1 | 68 | +200/-28 | dimensionless | 2 | $L_{\rm [CII]}/L_{\rm [NII]}=68^{+200}_{-28}$ |
| [NII] integrated flux AzTEC-3 | 0.46 | ±0.16 | Jy km/s | 2 | we measure an integrated line flux of $(0.46\pm0.16)\,$Jy km s$^{-1}$ |
| HZ10 dust temperature (Gaussian prior) | 33 | +12/-8 | K | 3 | to obtain dust temperatures of $33^{+12}_{-8}\,$K for HZ10 |
| LFIR HZ10 | 6.5e11 | +9.1/-3.8 e11 | Lsun | 3 | $6.5^{+9.1}_{-3.8} \times 10^{11} \,L_\odot$ for HZ10 |
| [CII] ionized fraction AzTEC-3 and HZ10 | 10-25 | not stated | % | 5 | the measured fraction of [Cii] emission from ionized gas in AzTEC-3 lies in the range 10–25% |

## Qualitative findings

- LBG-1 shows very weak [NII], suggesting little ionized-gas [CII] (~5%) possibly from low dust/metallicity or high ionization  
  > "we find a fraction of [Cii] emission from ionized gas in LBG-1 that is only about $\sim5\%$" (5.3)

## Claim tuples

- H: Typical z~5-6 galaxies have a lower ionized-gas contribution to [CII] than local galaxies | E: ALMA [NII] 205um in LBG-1 vs [CII] | R: L[CII]/L[NII]=68 (+200/-28), tentative 2σ detection | F: Extremely low [NII] relative to [CII] in LBG-1 | **partially**
- H: The starburst AzTEC-3 should show a high [CII]/[NII] ratio given its SFR surface density | E: [NII] detection in AzTEC-3 compared to Cloudy | R: ratio 22±8 | F: [NII] traces a diffuse ionized medium rather than star-forming HII regions | **partially**
- H: Ionized fraction varies spatially in HZ10 | E: Compared [NII] and [CII] positions and velocities | R: [NII] offset ~0.8'' and red-shifted; local ratios 14±5 and 8±3 | F: Tentative spatial variation of ionized fraction | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: [NII] 205um used with [CII] to separate ionized and neutral gas  
  > "suggested that the [Nii] $205\,\mu$m line could be used in conjunction with [Cii] $158\,\mu$m to separate the ionized from neutral fraction of the ISM" (1)
- Alternative: 2D Gaussian-fit flux rejected for AzTEC-3 in favor of [CII]-based aperture flux due to uncertain size  
  > "This leads us to adopt the [Cii]-based aperture flux in the following." (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): AzTEC-3 [NII] size and width poorly constrained; LBG-1 only 2σ  
  > "Because of the moderate signal-to-noise ratio and consequently poorly constrained spatial extent of the emission" (3.1)
- Caveat (inferred, ours): LBG-1 result rests on a 2σ detection with large asymmetric errors
- Caveat (inferred, ours): Aperture x2 correction assumes Gaussian profiles
- Caveat (inferred, ours): FIR luminosities depend on weak temperature priors
- Caveat (inferred, ours): Cloudy models are qualitative and solar-metallicity

## Reproducibility

- Data public (paper): Projects cited as archival; Cycle 3 data used via ADS/JAO.ALMA  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00928.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: Aperture positions/sizes in detail
- Missing: Cloudy input files
- Missing: MCMC code details
- Data volume (inferred): ~50-150 GB raw across five projects
- Score (inferred): 3/5, Data are public and the workflow is outlined, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Recipe lacks details; low-S/N results are sensitive to aperture choices.

## Links

- Method: (cite: O06) ([NII]/[CII] ionized-gas diagnostic)
- Companion: (cite: R14) (Cycle-0 [CII] data on AzTEC-3 and LBG-1)
- Companion: (cite: C15) (Cycle-1 [CII] data on HZ10 and HZ6/LBG-1)
- Related: COSMOS DEIMOS spectroscopic survey
- Related: COSMOS2015

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 60,
  "rate": 0.69
 },
 "evidence_ok": true
}
```
