# Complex molecular gas kinematics in the inner 5 kpc of 4C12.50 as seen by ALMA

`2019A&A...629A..30F` | Astronomy and Astrophysics 2019 | first author: Fotopoulou, C. M. | arXiv: 1908.01011 | DOI: 10.1051/0004-6361/201834416

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Where is the molecular gas wind in the radio galaxy 4C12.50 located, and what are its mass, excitation and driving mechanism?  
  > "To further investigate the physical conditions of the low-temperature molecular gas in the wind of 4C12.50 (including its location, mass, and excitation), we acquired new millimeter interferometric data of CO (1$-$0), (3$-$2), and (4$-$3)." (Introduction)
- Target **4C12.50 (IRAS 13451+1217, PKS 1345+12)**: coordinates _not stated_; z/distance z = 0.122; D_L = 570 Mpc  
  > "which yields 2.2kpc per arcsecond and a luminosity distance of $D_L=570$ Mpc (cite: wright06) at the redshift of the source." (Introduction); "provided an average redshift $z$ of 0.122($\pm$0.001) when fitted by Gaussian profiles." (3.1 Line fluxes); distance from LCDM (H0=70, OmegaM=0.3, OmegaL=0.7) via Wright 2006 calculator  
  > "which yields 2.2kpc per arcsecond and a luminosity distance of $D_L=570$ Mpc (cite: wright06) at the redshift of the source." (Introduction); "provided an average redshift $z$ of 0.122($\pm$0.001) when fitted by Gaussian profiles." (3.1 Line fluxes)

## Data provenance

- ALMA projects: 2013.1.00180.S, 2013.1.00976.S, 2012.1.00797.S
- bands: Bands 3, 7, 8  
  > "in band 3 (July 2015), and in bands 7 and 8 (May 2015)" (2 The ALMA data and their reduction)
- frequencies and spectral setup: four 1.875 GHz spectral windows per band; ~5 km/s line channels  
  > "In all bands, four spectral windows of 1.875 GHz bandwidth were employed." (2 The ALMA data and their reduction); "we typically chose a velocity bin of 5($\pm$1) km s$^{-1}$" (2 The ALMA data and their reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.62x0.56'' (B3), 0.61x0.47'' (B7), 0.43x0.36'' (B8); common 0.63'' convolved  
  > "The beam was 0.62$''$ $\times$ 0.56$''$ at a position angle (PA) of 14$\ensuremath{^\circ}$ in band 3" (2 The ALMA data and their reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.40, 1.1, 1.2 mJy/beam at 20 km/s for CO(1-0), (3-2), (4-3)  
  > "the noise level is at 0.40 mJy/beam for $\rm CO(1$-$0)$, at 1.1 mJy/beam for $\rm CO(3$-$2)$, and at 1.2 mJy/beam for $\rm CO(4$-$3)$" (2 The ALMA data and their reduction)
- time on source: 24.4, 5.2, 24 min in bands 3, 7, 8  
  > "4C12.50 was observed for 24.4, 5.2, and 24 minutes" (2 The ALMA data and their reduction)
- observing dates: Band 3 July 2015; bands 7, 8 May 2015  
  > "in band 3 (July 2015), and in bands 7 and 8 (May 2015)" (2 The ALMA data and their reduction)
- pi or archival as stated: Own program (PI Dasyra) plus archival calibrator observations from two other programs  
  > "we also looked into the archive for additional CO line data from observations of 4C12.50 as a calibrator for other programs." (2 The ALMA data and their reduction)
- Line: CO 1-0 (not stated)
- Line: CO 3-2 (not stated)
- Line: CO 4-3 (not stated)
- Line: H2O nu=0 4[2,3]-3[3,0] (448.00108 GHz)
- Line: HCO+ 5-4 (not stated)
- Other facility **HST**: [OIII] and continuum optical images  
  > "as derived from the subtraction of two *Hubble Space Telescope* images" (Introduction)
- Other facility **IRAM Plateau de Bure / 30m**: earlier CO fluxes for comparison  
  > "the IRAM 30m single dish telescope: 50($\pm$8) Jy km s$^{-1}$ (cite: dasyra_combes12)" (3.1 Line fluxes)
- External data: Warm H2 outflow mass 5.2e7 Msun and disk 1.4e8 Msun (Spitzer)  
  > "the outflow has a mass of 5.2$\times$10$^7$ $M_{\odot}$(cite: dasyra11)" (3.5 Gas excitation) [from (cite: dasyra11)]
- External data: CO(1-0) flux 14 +/-4 Jy km/s  
  > "yielding a $\rm CO(1$-$0)$ flux of 14($\pm$4) Jy km s$^{-1}$" (3.1 Line fluxes) [from (cite: evans99)]

## Processing

### Calibration

- pipeline or manual: Pipeline reran; restored for bands 3 and 7; band 8 fine-tuned (DA34, DV02 flagged)  
  > "The automated pipeline results were restored for bands 3 and 7. For band 8, the calibrations were fine tuned" (2 The ALMA data and their reduction)
- casa version: Calibration 4.3.1/4.2.2/4.3.1 (bands 3/7/8); imaging CASA 5.4  
  > "The calibration routines were run with CASA version 4.3.1, 4.2.2, and 4.3.1 for bands 3, 7, and 8, respectively." (2 The ALMA data and their reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C273 (band 7); Titan (bands 3, 8)  
  > "The flux calibration solution was found using 3C273 in band 7, and using Titan in bands 3 and 8." (2 The ALMA data and their reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibrated on 4C12.50 using additional dedicated observations  
  > "The phase was self-calibrated on 4C12.50 using additional observations dedicated for this purpose." (2 The ALMA data and their reduction)

### Imaging

- task: tclean (CASA 5.4)  
  > "The image reconstruction was executed with the routine tclean that also performs the beam cleaning." (2 The ALMA data and their reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust=2 band 3; robust=1 bands 7, 8  
  > "we used Briggs weighting of the visibilities with robustness parameter of 2 for band 3, and 1 for bands 7 and 8." (2 The ALMA data and their reduction)
- uv taper: _not stated_
- cell size: 0.08''  
  > "At a common pixel scale of 0.08$''$ and at a common velocity resolution of 20 km s$^{-1}$" (2 The ALMA data and their reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first-order polynomial; zero-order in band 8  
  > "First-order polynomials were employed for the modeling and the subtraction of the continuum in all spectral windows with one exception" (2 The ALMA data and their reduction)
- line free channels: _not stated_
- primary beam correction: applied during image reconstruction  
  > "During the image reconstruction, a primary beam correction was also applied." (2 The ALMA data and their reduction)
- array combination: Calibration-intended 4C12.50 data merged; archival CO(1-0), CO(3-2) concatenated with concat to make deep cubes  
  > "we merged the calibrated measurement set with ours using the routine concat in CASA 5.4" (2 The ALMA data and their reduction)
- smoothing: convolved to common 0.63''x0.63'' beam with ia.convolve2d  
  > "by convolving the data to a common beam of 0.63$''$ $\times$0.63$''$ using the routine ia.convolve2d" (2 The ALMA data and their reduction)
- final beam: Deep CO(1-0) 0.81x0.74'' PA -22; deep CO(3-2) 0.63x0.48'' PA 51  
  > "which has a new (common) beam of 0.81$''$ $\times$0.74$''$ at a PA of -22$\ensuremath{^\circ}$" (2 The ALMA data and their reduction)
- final rms: 0.41, 1.2, 1.4 mJy/beam in homogenized cubes  
  > "the noise level is at 0.41 mJy/beam, 1.2 mJy/beam, and 1.4 mJy/beam" (2 The ALMA data and their reduction)

### Inherited from earlier work

- H2 mass computed with Solomon et al. 1997 formula  
  > "The  $\rm{H_ 2}$ mass is computed as in (cite: solomon97)." (3.2 Disk and ambient gas emission) [from (cite: solomon97)]
- alpha = 0.8 Msun/(K km/s pc^2), ULIRG value  
  > "we adopted an $\alpha$ value of 0.8 $M_{\odot}$/(K km s$^{-1}$pc$^2$) for consistency with the literature" (3.2 Disk and ambient gas emission) [from (cite: downes98)]
- Half of L_IR ascribed to AGN  
  > "Following (cite: veilleux09), we ascribe half the  $L_{\rm IR}$ to the AGN." (4.1 Energy output) [from (cite: veilleux09)]
- SFR from Kennicutt formula  
  > "computed from the (cite: kennicutt98) formula for  $L_{\rm IR}$/2" (4.1 Energy output) [from (cite: kennicutt98)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Clean threshold, masking, niter and number of channels/imaging of the cubes
- Mask regions/ellipses used to extract fluxes of F1, F2, disk-wide and extended components
- Gaussian fit details for the nuclear wind residual
- Self-calibration solution details
- Line rest frequencies and velocity definitions
- Exact derivation of d and V_mean per region
- SED fit data points and priors

## Analysis recipe

1. **Reduce and image cubes**: Rerun CASA calibration, tclean imaging, uvcontsub, concat archival data into deep cubes, convolve to common beam  
  > "For the imaging part of the pipeline, CASA version 5.4 was used." (2 The ALMA data and their reduction)
   - software: CASA, tclean, uvcontsub, concat, ia.convolve2d
   - parameter: robust 2 (B3), 1 (B7, B8); pixel 0.08''  
  > "robustness parameter of 2 for band 3, and 1 for bands 7 and 8" (2 The ALMA data and their reduction)
   - fitting: _not stated_
   - validation: Compared fluxes of high-res and deep cubes and with IRAM/30m values  
  > "As in both bands the high-resolution data reach comparable flux levels to the deep and the ancillary data, we perform all of our calculations with them." (3.1 Line fluxes)
2. **Measure line fluxes and moment maps**: Gaussian line profile fit per spatial pixel; integrated fluxes  
  > "The disk rotation pattern is best revealed by the fitting of a Gaussian line profile in every spatial pixel of the ALMA data" (3.2 Disk and ambient gas emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive H2 masses**: M_H2=3.25e7 alpha S dV nu_obs^-2 D_L^2/(1+z)  
  > "M_{H_2}=3.25\times10^7 \alpha S _{CO(1-0)} \Delta V \nu_{obs}^{-2}D_L^2/(1+z)" (3.2 Disk and ambient gas emission)
   - assumption: alpha = 0.8; D_L = 570 Mpc  
  > "we adopted an $\alpha$ value of 0.8" (3.2 Disk and ambient gas emission)
   - fitting: _not stated_
   - validation: Wind detection tested against altering continuum fit order and spw ranges  
  > "the wind detection survives the test of altering pipeline parameter values" (3.4.1 Nuclear wind in CO)
4. **Wind energetics**: Mdot = M V/d; L_kin = 0.5 M V^3/d; momentum rate Mdot V; compare to jet, AGN radiation pressure and SN  
  > "computed as $(1/2) MV^{3}d^{-1}$" (4.2 Extended wind energetics)
   - assumption: One SN per 100 Msun formed, 1e51 erg each; AGN = half of L_IR  
  > "We assume that for every 100 $M_{\odot}$ formed, there is one SN." (4.1 Energy output)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit SED for jet power and L_IR**: Simultaneous chi2 fit of jet synchrotron (broken power law with exponential cutoff) and dust (modified blackbody plus power law)  
  > "we simultaneously fitted their SEDs using a standard $\chi ^2$ minimization method (cite: lmfit)" (4.1 Energy output)
   - software: lmfit
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.1, 4.2.2, 4.3.1, 4.7.0 (calibration); 5.4 (imaging): calibration, tclean, uvcontsub, concat  
  > "For the imaging part of the pipeline, CASA version 5.4 was used." (2 The ALMA data and their reduction)
- **lmfit** : SED chi2 fitting  
  > "standard $\chi ^2$ minimization method (cite: lmfit)" (4.1 Energy output)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean redshift from CO | 0.122 | 0.001 | dimensionless | 2 | average redshift $z$ of 0.122($\pm$0.001) |
| CO(1-0) flux (high-res) | 13.6 | 1.5 | Jy km/s | 2 | 13.6($\pm$1.5) Jy km s$^{-1}$, 66($\pm$2) Jy km s$^{-1}$  and 70($\pm$2) Jy km s$^{-1}$ |
| Total H2 mass from CO(1-0) | 7.7e9 | 0.8e9 | Msun | 3 | 7.7($\pm$0.8)$\times$10$^9$  $M_{\odot}$ |
| Nuclear wind mass | 5.3e8 | 0.7e8 | Msun | 3 | nuclear wind mass of 5.3($\pm$0.7)$\times$10$^8$  $M_{\odot}$ |
| Extended wind mass | 1.0e9 | 0.1e9 | Msun | 3 | total mass of the extended wind reaches 1.0($\pm$0.1)$\times$10$^9$ $M_{\odot}$ |
| Jet power range | 1e44 to 8e44 | not stated | erg/s | 5 | we find the jet power to be in the range $10^{44}-8\times10^{44}\,\mathrm{erg}/\mathrm{s}$ |
| Total wind kinetic luminosity | 5.1e44 | not stated | erg/s | 4 | reach 5.1$\times$10$^{44}$ ergs$^{-1}$ and 7.7$\times$10$^{36}$ erg cm$^{-1}$ |
| Dust temperature | 55 | not stated | K | 5 | We found the dust temperature to be $55 \, \mathrm{K}$ |

## Qualitative findings

- Gas out of dynamical equilibrium includes a southern tidal tail; CO disk cut along an [OIII] ridge  
  > "The CO emission is abruptly cut along an  \[O III\] ridge north of the main nucleus, where no CO is detected." (5 Conclusions)

## Claim tuples

- H: A molecular wind exists in 4C12.50 detectable in CO emission | E: ALMA CO(1-0),(3-2),(4-3) cubes | R: Nuclear wind mass 5.3e8 Msun; extended tentative wind 1.0e9 Msun | F: Wind components detected, though extended ones are low S/N | **partially**
- H: The accelerated gas is heated | E: Compare cold wind fraction in CO with warm H2 fraction | R: Cold wind fraction <20% versus warm >30% | F: Confirms heating of accelerated gas | **supported**
- H: What drives the wind | E: Energetics compared to jet, AGN radiation, SN | R: Starburst insufficient; jet most powerful | F: Wind mainly sustained by the jet, assisted by radiation pressure | **partially**

## Reasoning

- Why this data: To study the low-temperature molecular gas in the wind, including location, mass, excitation  
  > "To further investigate the physical conditions of the low-temperature molecular gas in the wind of 4C12.50" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO(2-3) absorption could not be tested due to spw concatenation continuum uncertainty  
  > "Unfortunately, we were unable to test the CO(2$-$3) absorption previously reported" (3.1 Line fluxes)
- Limitation (authors): Some cold wind mass may be unaccounted for due to overlap of structures  
  > "some of the cold gas mass in the wind may be unaccounted for" (3.5 Gas excitation)
- Caveat (inferred, ours): Extended wind detections are 3-5 sigma and sensitive to continuum subtraction
- Caveat (inferred, ours): Single alpha=0.8 assumed; mass scales linearly
- Caveat (inferred, ours): Energetics depend on adopted d and projected, uncorrected velocities
- Caveat (inferred, ours): Jet power uncertain by an order of magnitude

## Reproducibility

- Data public (paper): ALMA data from archive programs acknowledged  
  > "This paper makes use of the ALMA data ADS/JAO.ALMA 2013.1.00180.S, 2013.1.00976.S, 2012.1.00797.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Line-free channels
- Missing: Region definitions for wind components
- Missing: SED data compilation
- Data volume (inferred): ~50-150 GB across three bands plus two archival datasets
- Score (inferred): 5/5, Data public and core steps described, but masks, regions and clean settings missing.
- Rediscovery candidate: no, Key wind results are low S/N and depend on unstated region and fit choices.

## Links

- Method: (cite: solomon97) (H2 mass formula)
- Companion: (cite: dasyra14) (Earlier PdB CO study of 4C12.50 wind)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 48,
  "rate": 0.649
 },
 "evidence_ok": true
}
```
