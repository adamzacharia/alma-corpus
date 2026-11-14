# The Molecular Gas Reservoirs of z ∼ 2 Galaxies: A Comparison of CO(1-0) and Dust-based Molecular Gas Masses

`2019ApJ...880...15K` | The Astrophysical Journal 2019 | first author: Kaasinen, M. | arXiv: 1905.11417 | DOI: 10.3847/1538-4357/ab253b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do molecular gas masses from single-band long-wavelength (Rayleigh-Jeans) dust continuum agree with CO(1-0)-derived masses for massive z~2 star-forming galaxies?  
  > "We hereby test whether this method is valid for the types of high-redshift, star-forming galaxies to which it has been applied." (abstract)
- Target **16 COSMOS z~2 massive star-forming galaxies (12 in final sample)**: coordinates COSMOS field, per-source positions in source table (e.g. source 1: 10h00m35.29s +2d43m53.2s)  
  > "Because of our selection criteria, our sample spans a wide redshift range of $1.6<z<2.9$." (2.1 Sample Selection); z/distance 1.6<z<2.9; CO(1-0) or optical-line spectroscopic redshifts  
  > "Because of our selection criteria, our sample spans a wide redshift range of $1.6<z<2.9$." (2.1 Sample Selection); distance from CO(1-0) redshifts or COSMOS spectroscopic catalogue  
  > "Because of our selection criteria, our sample spans a wide redshift range of $1.6<z<2.9$." (2.1 Sample Selection)

## Data provenance

- ALMA projects: 2013.1.00034.S, 2015.1.00137.S, 2013.1.00118.S, 2013.1.00151.S
- bands: ALMA Band 7 (343.5 GHz) continuum  
  > "we selected the 16 galaxies with the highest ALMA Band 7 (343.5 GHz) fluxes." (2.1 Sample Selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: VLA beams ~2-4 arcsec (Table); ALMA beam at least 6x smaller than VLA beam  
  > "the FWHM of the synthesized ALMA beam is at least $6\times$ smaller than that of the VLA beam" (2.3 Dust Continuum Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: VLA: four hours per target including calibrators  
  > "Each target was observed for a total of four hours, including the time spent on bandpass, phase and amplitude calibration sources." (2.2 CO(1-0) Observations and Data Reduction)
- observing dates: VLA: February and March 2017; Q band (4 sources) and Ka band (12 sources)  
  > "The VLA observations analysed here were taken during February and March 2017." (2.2 CO(1-0) Observations and Data Reduction)
- pi or archival as stated: ALMA continuum from the parent sample of Scoville et al. 2017; VLA CO(1-0) from the authors' program VLA/17A-251  
  > "Our sample was selected from the ALMA-detected, IR-bright sample of (cite: 2017ApJ...837..150S)." (2.1 Sample Selection); "This paper makes use of the VLA data: VLA/17A-251" (Acknowledgments)
- Line: CO J=1-0 (not stated)
- Other facility **VLA**: CO(1-0) line observations (Ka and Q bands)  
  > "four were observed in the Q band ($40 - 50 \mathrm{GHz}$) and 12 in the Ka band ($26.5 - 40 \mathrm{GHz}$)" (2.2 CO(1-0) Observations and Data Reduction)
- Other facility **Keck I MOSFIRE**: Rest-frame optical redshifts for several sources  
  > "reobserved sources 1, 2, 4, 6, 9, 11 and 12 with the Multi-Object Spectrometer For Infra-Red Exploration (MOSFIRE, on Keck I)" (2.2 CO(1-0) Observations and Data Reduction)
- Other facility **Herschel PACS/SPIRE and COSMOS photometry**: FIR and UV-to-IR photometry for SED fitting  
  > "We fit the available COSMOS photometry, from the GALEX far-ultraviolet to Herschel PACS 500 $\mu$m filters" (3.3.1 Application of MAGPHYS)
- External data: COSMOS2015 photometry and stellar masses/redshifts  
  > "taken from the 2016 catalogue of (cite: 2016ApJS..224...24L)" (3.3.1 Application of MAGPHYS) [from (cite: 2016ApJS..224...24L)]
- External data: alpha_850 calibration (mean 6.7±1.7e19 erg/s/Hz/Msun) and best-fit relation  
  > "$\left<\alpha_\mathrm{850\mu m}\right>  = 6.7\pm 1.7 \times 10^{19} \mathrm{erg \, s^{-1}\, Hz^{-1}\, \ensuremath{\rm{M}_{\odot}}^{-1}}$ derived for the (cite: 2016ApJ...820...83S) calibration sample" (4.1 Comparison) [from (cite: 2016ApJ...820...83S)]
- External data: Herschel data for source 16 via private correspondence  
  > "Instead, we use the Herschel data described in (cite: 2013ApJ...778..131L)[^3]." (3.3.1 Application of MAGPHYS) [from (cite: 2013ApJ...778..131L)]

## Processing

### Calibration

- pipeline or manual: VLA calibration pipeline without Hanning smoothing  
  > "we applied the VLA calibration pipeline[^2] without Hanning smoothing." (2.2 CO(1-0) Observations and Data Reduction)
- casa version: CASA 4.7.2 (VLA data)  
  > "Common Astronomy Software Application (CASA)[^1], version 4.7.2." (2.2 CO(1-0) Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA TCLEAN (VLA cubes)  
  > "We created the initial dirty images using CASA’s `TCLEAN` algorithm." (2.2 CO(1-0) Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "applying a natural weighting scheme, a cleaning threshold of twice the root-mean-square (rms) noise level ($2\sigma$)" (2.2 CO(1-0) Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: circular mask radius 5 arcsec centred on source  
  > "a circular mask with a radius of 5”, centred at the position of the source" (2.2 CO(1-0) Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectral resolution optimised for S/N; native ~16 km/s for sources 8 and 16  
  > "For sources 8 and 16 it was necessary to use the native resolution ($\sim 16 \ensuremath{\rm{km}\, \rm{s}^{-1}}$) to extract the spectra" (2.2 CO(1-0) Observations and Data Reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Single-band L850 prescription (T=25 K, beta=1.8, Gamma_RJ correction)  
  > "follows the prescription described in detail in Appendix A.1 of (cite: 2016ApJ...820...83S; 2017ApJ...837..150S)." (3.2.1 Single-band Derived L850) [from (cite: 2016ApJ...820...83S; 2017ApJ...837..150S)]
- Main sequence definition  
  > "We define the MS using the best fit from (cite: 2014ApJS..214...15S)" (3.3.2 Main Sequence Offset) [from (cite: 2014ApJS..214...15S)]
- MAGPHYS high-z framework details  
  > "The details of the SED-fitting framework, stellar model libraries and treatment of dust are described in (cite: 2008MNRAS.388.1595D; 2015ApJ...806..110D)." (3.3.1 Application of MAGPHYS) [from (cite: 2008MNRAS.388.1595D; 2015ApJ...806..110D)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and continuum measurement details (reduction path, CASA version, beams, uv coverage) for the Band 7 data
- VLA CLEAN iteration limits, channel widths for each source and which channels were used for velocity-integrated maps
- Dust opacity normalization kappa(850um) and Gamma_RJ implementation
- MAGPHYS prior and library settings and exact photometry used
- Velocity ranges per source for moment maps

## Analysis recipe

1. **Image VLA CO(1-0) cubes and detect line**: Pipeline calibration, TCLEAN natural-weighted cubes, detection if spectrum peak and moment-0 peak >=3 sigma  
  > "we require the peak flux of the spectrum, extracted at the source position, and the peak flux in the moment zero map to be detected at $\geq 3\sigma$." (2.2 CO(1-0) Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Moment-0 fluxes consistent with Gaussian-fit fluxes  
  > "These values are consistent, within uncertainties, with the integrated line fluxes extracted from the moment zero maps" (2.2 CO(1-0) Observations and Data Reduction)
2. **Fit CO line flux and redshift; upper limits**: Single Gaussian fit; 3 sigma upper limits from 500 km/s channel maps  
  > "We create each map using `TCLEAN`, with a channel width of $500\, \ensuremath{\rm{km}\, \rm{s}^{-1}}$" (2.2 CO(1-0) Observations and Data Reduction)
   - software: scipy.optimize.curvefit
   - fitting: 1/sigma^2 weighting with rms per channel; 1 sigma fit errors  
  > "We use a $1/\sigma^2$ weighting scheme, where $\sigma$ is the rms noise per channel" (2.2 CO(1-0) Observations and Data Reduction)
   - validation: Double Gaussian fits consistent within uncertainties  
  > "The fluxes derived from the double Gaussian line profiles are consistent, within uncertainties, with the single Gaussian fits" (2.2 CO(1-0) Observations and Data Reduction)
3. **Measure ALMA Band 7 continuum flux**: Elliptical Gaussian fits within 5 arcsec; two Gaussians for source 16  
  > "We fit two Gaussians to the emission of source 16 but fit all other sources with a single Gaussian element." (2.3 Dust Continuum Data)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Compared with Scoville et al. 2017 automated fluxes; source 5 is 20% lower  
  > "Our derived fluxes are mostly consistent with those predicted by the automated procedure of (cite: 2017ApJ...837..150S), except for source 5" (2.3 Dust Continuum Data)
4. **CO-based molecular gas mass**: L'CO via Solomon et al. 1992 Eq.; Mmol = alpha_CO L'CO  
  > "$L_\mathrm{CO}^{\prime} = 3.25 \times 10^7 S_\mathrm{CO} \Delta v \, \nu_\mathrm{obs}^{-2}  D_\mathrm{L}^2  (1+z)^{-3}$" (3.1 CO(1-0)-based Molecular Gas Masses)
   - assumption: alpha_CO = 6.5 Msun/(K km/s pc^2) incl. factor 1.36 for heavy elements  
  > "includes a factor of 1.36 to account for the associated mass of heavy elements (mostly He at 8% by number)" (3.1 CO(1-0)-based Molecular Gas Masses)
   - assumption: Flat LCDM H0=70, OmegaM=0.3, OmegaL=0.7  
  > "$H_0 = 70 \ensuremath{\rm{km}\, \rm{s}^{-1}}\mathrm{Mpc}^{-1}$, $\Omega_M = 0.3$ and $\Omega_\Lambda = 0.7$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Single-band L850 and RJ gas mass**: Modified blackbody extrapolation to rest 850um then divide by alpha_850  
  > "the reference luminosity can be calulated from the measured, RJ flux via" (3.2.1 Single-band Derived L850)
   - assumption: T_dust = 25 K mass-weighted  
  > "The mean, mass-weighted dust temperature, used to describe the modified blackbody emission, is assumed to be 25 K" (3.2.1 Single-band Derived L850)
   - assumption: beta = 1.8, constant gas-to-dust ratio  
  > "with a dust emissivity index of $\beta=1.8$" (3.2.1 Single-band Derived L850)
   - fitting: _not stated_
   - validation: Compared with MAGPHYS SED-derived L850  
  > "We compare the values of $L_\mathrm{850\mu m,rest}$ derived via these two methods" (3.2 RJ-based Molecular Gas Masses)
6. **SED fitting for L850, stellar mass, SFR**: MAGPHYS high-z on GALEX-to-Herschel photometry plus ALMA Band 7; four beta/T_cold variants; medians with 16-84 percent errors  
  > "To assess what impact variations in $\beta$ and $T_\mathrm{dust}$ have on the derived $L_\mathrm{850\mu m,rest}$ we apply `MAGPHYS` with four sets of assumptions:" (3.2.2 SED-derived L850)
   - software: MAGPHYS
   - fitting: MAGPHYS likelihood marginalised over model library  
  > "builds a likelihood distribution for $L_\mathrm{850\mu m,rest}$ by marginalising over a library of models" (3.2.2 SED-derived L850)
   - validation: Stellar masses and SFRs compared with LePhare and previous values  
  > "The stellar masses derived via `MAGPHYS` and `LePhare` are consistent within a factor of two (with no systematic offset)" (3.3 Stellar Masses and SFRs)
7. **Compare CO and dust luminosities / gas masses**: Standardized residuals e/sigma_e of L'CO vs predicted from L850 with mean and best-fit alpha_850; Spearman correlations of Mmol ratio with properties  
  > "To quantify the scatter and the goodness of fit compared to the predictions from the mean and best-fit $\alpha_\mathrm{850 \mu m}$, we compute the standardized residuals." (4.2 CO(1-0) vs. Dust Continuum Luminosity)
   - fitting: _not stated_
   - validation: Comparison with Scoville et al. 2016 calibration sample scatter  
  > "Our sample exhibits the same level of scatter as the calibration sample of (cite: 2016ApJ...820...83S)" (4.2 CO(1-0) vs. Dust Continuum Luminosity)

## Software

- **CASA** 4.7.2: VLA reduction, TCLEAN imaging, imfit  
  > "Common Astronomy Software Application (CASA)[^1], version 4.7.2." (2.2 CO(1-0) Observations and Data Reduction)
- **MAGPHYS** high-z version: SED fitting for L850, stellar mass, SFR  
  > "we apply the updated version of the SED-fitting algorithm `MAGPHYS` high-z" (3.2.2 SED-derived L850)
- **scipy.optimize.curvefit** : Gaussian line fits  
  > "via `Python`’s `scipy.optimize.curvefit` algorithm" (2.2 CO(1-0) Observations and Data Reduction)
- **LePhare** : Catalogue stellar masses (COSMOS) for comparison  
  > "The stellar masses, determined with the SED-fitting algorithm `LePhare`" (3.3 Stellar Masses and SFRs)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO-detected sources | 10 of 16 | not stated | sources | 1 | We detect CO(1-0) emission in 10 of the 16 sources in our sample. |
| M_mol range from single-band RJ method | 1.7-7.1e11 | mean uncertainty 0.9e11 | Msun | 5 | we find a range of $\rm{M}_{\rm{mol}}$ of $1.7-7.1 \times 10^{11}\ensuremath{\rm{M}_{\odot}}$ with a mean uncertainty of $0.9\times 10^{11}\ensuremath{\rm{M}_{\odot}}$ |
| Pearson correlation of 343.5 GHz luminosity with L'CO | 0.78 | not stated | dimensionless | 7 | correlates strongly (Pearson rank correlation coefficient of 0.78) with the CO(1-0) luminosity |
| Mean alpha_850 of this sample | 7.7e19 | ±2.3e19 | erg/s/Hz/Msun | 7 | the mean $\alpha_\mathrm{850 \mu m}$ of our sample, $7.7\pm2.3 \times 10^{19} |
| Median L850 SED(standard MAGPHYS)/single-band | 78% | not stated | percent | 6 | i.e. centred at 78% of the single-band values |
| Mmol RJ vs CO agreement for CO detections | within factor 1.7 | not stated | factor | 7 | for all CO-detected sources, the values of $\rm{M}_{\rm{mol}}$ are consistent to within a factor of 1.7 |
| MS offset range | 1-7 | not stated | dimensionless | 6 | spanning $1< \mathrm{sSFR/sSFR_{MS}} <7$ |

## Qualitative findings

- No significant correlation of the RJ/CO gas mass ratio with stellar mass, SFR or MS offset  
  > "We find no statistically significant correlation with the stellar mass, SFR or main sequence offset within our sample" (4.3 Accuracy of Mmol)

## Claim tuples

- H: Does the L850-CO(1-0) calibration hold for z~2 massive star-forming galaxies? | E: Compared L850 and L'CO and standardized residuals with the Scoville et al. calibration sample | R: Strong correlation; scatter matches calibration sample, residuals within |2| | F: Calibration is valid for this sample | **supported**
- H: Do RJ and CO(1-0) gas masses agree? | E: Compared M_mol,RJ and M_mol,CO with same alpha_CO | R: Consistent within factor 1.7 | F: Single-band dust continuum constrains gas mass as reliably as CO(1-0) to within a factor of two | **supported**
- H: What drives the scatter? | E: Varied beta and T_cold in MAGPHYS | R: Factor ~2 changes in L850 | F: beta/T extrapolation uncertainty is smaller than alpha_CO uncertainty | **supported**

## Reasoning

- Why this data: Sources chosen with highest Band 7 fluxes to maximise CO(1-0) detection  
  > "To maximise the chances of detecting CO(1-0) emission, we selected the 16 galaxies with the highest ALMA Band 7 (343.5 GHz) fluxes." (2.1 Sample Selection)
- Why this method: _not stated_
- Alternative: Double Gaussian fits for sources 3 and 8 not adopted as unphysical  
  > "We do not consider the double Gaussian profiles to be physical given the relative strengths of the rms and dip in flux." (2.2 CO(1-0) Observations and Data Reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample biased to high SFR; alpha_CO uncertainty up to factor ~8 dominates absolute masses  
  > "Our sample is therefore intentionally biased to the types of high SFR ($\mathrm{SFR}>300\ensuremath{\rm{M}_{\odot}}\ensuremath{\rm{yr}^{-1}}$) sources" (2.1 Sample Selection)
- Caveat (inferred, ours): Small sample (12) with CO detections only for 10; selection by brightest Band 7 biases toward high-gas-mass sources
- Caveat (inferred, ours): Common alpha_CO built into calibration makes agreement partly circular
- Caveat (inferred, ours): Source 12 non-detection unexplained

## Reproducibility

- Data public (paper): ALMA and VLA project IDs given in acknowledgments  
  > "This paper makes use of the VLA data: VLA/17A-251, and, the ALMA data: 2013.1.00034.S, 2015.1.00137.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA Band 7 reduction details
- Missing: VLA per-source channel/velocity settings
- Missing: Private Herschel data for source 16
- Data volume (inferred): ~50-200 GB (VLA 16 targets plus ALMA Band 7 continuum)
- Score (inferred): 3/5, Data identifiable and equations explicit, but ALMA processing and several settings are unstated or inherited.
- Rediscovery candidate: no, ALMA continuum processing is not described and part of the photometry is private.

## Links

- Method: (cite: 2016ApJ...820...83S) (RJ method and alpha_850 calibration)
- Method: (cite: 2015ApJ...806..110D) (MAGPHYS high-z)
- Companion: (cite: 2017ApJ...837..150S) (Parent ALMA-detected sample)
- Related: COSMOS
- Related: Herschel

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00118.S",
  "2013.1.00151.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 52,
  "rate": 0.619
 },
 "evidence_ok": true
}
```
