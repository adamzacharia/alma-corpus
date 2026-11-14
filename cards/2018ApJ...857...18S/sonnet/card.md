# Multiple Gaps in the Disk of the Class I Protostar GY 91

`2018ApJ...857...18S` | The Astrophysical Journal 2018 | first author: Sheehan, Patrick D. | arXiv: 1803.02847 | DOI: 10.3847/1538-4357/aaae65

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Does the Class I protostar GY 91 host gaps in its disk, are they similar to HL Tau's, and how young is it compared to HL Tau?  
  > "We model these features assuming they are gaps in the disk surface density profile and find that their widths are 7 AU, 30 AU, and 10 AU." (abstract)
- Target **GY 91**: coordinates _not stated_; z/distance 137 pc  
  > "GY 91 is a M4 protostar (cite: Doppmann2005) in the L1688 region of the $\rho$ Ophiuchus molecular cloud, located at a distance of 137 pc (cite: OrtizLeon2017)." (1 Introduction); distance from Ortiz-León et al. 2017  
  > "GY 91 is a M4 protostar (cite: Doppmann2005) in the L1688 region of the $\rho$ Ophiuchus molecular cloud, located at a distance of 137 pc (cite: OrtizLeon2017)." (1 Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00761.S
- bands: Band 3 (3 mm) and Band 7 (870 um)  
  > "GY 91 was observed with ALMA Band 3 (100 GHz/3 mm) in three tracks from 31 October 2015 to 17 April 2016" (2.1 ALMA)
- frequencies and spectral setup: Band 3 continuum at 90.5, 92.5, 102.5, 104.5 GHz; Band 7 continuum at 343 and 356.25 GHz  
  > "Two of four basebands were configured for continuum observations centered at 343 GHz and 356.25 GHz, with a total of 4 GHz of continuum bandwidth." (2.1 ALMA)
- continuum bandwidth: 8 GHz (Band 3), 4 GHz (Band 7)  
  > "In all the observations had 8 GHz of total continuum bandwidth." (2.1 ALMA)
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 3: 14 m-15.3 km; Band 7: 15-3140 m  
  > "with baselines ranging from 15 – 3140 m." (2.1 ALMA)
- angular resolution: 3 mm beam 0.06" x 0.05"; 870 um beam 0.134" x 0.129"  
  > "The 3 mm image has a beam of size 0.06" by 0.05" with a P.A. of 81.9$^{\circ}$ and an rms of 36 $\mu$Jy/beam." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 36 uJy/beam (3 mm), 0.31 mJy/beam (870 um)  
  > "an rms of 0.31 mJy/beam" (2.1 ALMA)
- time on source: _not stated_
- observing dates: 31 Oct 2015 - 17 Apr 2016 (Band 3); 19 May and 11 Sep 2016 (Band 7)  
  > "on 19 May 2016 and 11 September 2016" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **Spitzer IRS/IRAC/MIPS and literature photometry**: Broadband SED and IRS spectrum used in the modeling  
  > "We compile a broadband spectral energy distribution (SED) for GY 91 from a thorough literature search." (2.2 SED from the Literature)
- External data: Spitzer IRS spectrum of GY 91 from CASSIS  
  > "we also download the Spitzer IRS spectrum of GY 91 from the CASSIS database" (2.2 SED from the Literature) [from (cite: Lebouteiller2011; Lebouteiller2015)]
- External data: Dust opacities  
  > "We supply the density structure with opacities described in (cite: Sheehan2014)" (3 Results) [from (cite: Sheehan2014)]

## Processing

### Calibration

- pipeline or manual: standard CASA pipeline  
  > "The data were reduced in the standard way with the `CASA` pipeline and the calibrators listed in Table" (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Band 7: four phase-only iterations on compact track, one on extended; none for Band 3  
  > "We ran four iterations of phase-only self-calibration on the compact configuration track and a single iteration of phase-only self-calibration on the extended configuration track." (2.1 ALMA)

### Imaging

- task: CLEAN  
  > "we imaged the data by Fourier transforming the visibilities with the `CLEAN` routine" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Our final images were produced using Briggs weighting with a robust parameter of 0.5" (2.1 ALMA)
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
- final beam: 0.06"x0.05" (3 mm); 0.134"x0.129" (870 um)  
  > "The 870 $\mu$m image nas a beam size of 0.134" by 0.129" with a P.A. of -9.4$^{\circ}$" (2.1 ALMA)
- final rms: 36 uJy/beam; 0.31 mJy/beam  
  > "an rms of 0.31 mJy/beam" (2.1 ALMA)

### Inherited from earlier work

- Radiative transfer modeling procedure  
  > "This modeling procedure is described in further detail in (cite: Sheehan2014) and Sheehan & Eisner (submitted), but we give a brief overview here." (3 Results) [from (cite: Sheehan2014); Sheehan & Eisner (submitted)]

### Not stated but needed to reproduce (our reading)

- MCMC priors, walker count, step count and burn-in length
- Geometric model functional form used for the initial fit
- CASA version, CLEAN parameters (cell, image size, masks, threshold)
- HL Tau data selection and SED for the comparison
- Stellar parameters and fixed values used in the radiative transfer model
- Image-plane centering and continuum-flux calibration uncertainty

## Analysis recipe

1. **Image and examine radial profiles**: Imaged with Briggs weighting; averaged brightness in elliptical annuli set by disk PA and inclination  
  > "averaged in ellipses defined by the position angle and inclination of the disk to be constant radius bins" (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Geometric model fit to visibilities**: Simple geometric model fit to 870 um and 3 mm visibilities for initial guesses  
  > "we make initial estimates of disk properties and the gap widths and depths by fitting a simple geometric model to the $870$ $\mu$m and 3 mm visibilities (see Figure 3)" (Results)
   - software: emcee
   - fitting: emcee MCMC  
  > "using the MCMC code `emcee`" (3 Results)
   - validation: _not stated_
3. **Radiative transfer disk+envelope fit with gaps**: Synthetic visibilities and SEDs fit simultaneously to 870 um, 3 mm and SED; gaps as multiplicative reductions of surface density  
  > "We fit these synthetic observations simultaneously to all three (870 $\mu$m visibilities, 3 mm visibilities, and broadband SED) of our datasets, again using the `emcee` code." (3 Results)
   - software: RADMC-3D, Hyperion, emcee
   - assumption: Lynden-Bell & Pringle surface density, Ulrich envelope, 10% uncertainty on literature photometry and IRS points  
  > "we assume a constant 10% uncertainty on any photometry from the literature" (2.2 SED from the Literature)
   - fitting: emcee; median of walkers after burn-in, 68% range as uncertainty  
  > "We estimate the uncertainty on these parameter values as the range around the median containing 68% of the walkers." (3 Results)
   - validation: Convergence judged by steady state of walkers  
  > "We consider the fit to have converged when the walkers have reached a steady state" (3 Results)
4. **Estimate planet masses and compare with HL Tau**: Gap width vs Hill radius relation for planet mass; same disk+envelope fit to HL Tau (smooth, min baseline 16 kλ); compare Menv/Mdisk  
  > "we have limited the HL Tau visibilities to a minimum baseline of 16 k$\lambda$ to match our GY 91 dataset" (4 Comparison with HL Tau)
   - assumption: Stellar mass ~0.25 Msun at ~0.5 Myr from Baraffe models  
  > "which evolutionary models predict should have a mass of $\sim0.25$ M$_{\odot}$ at $\sim0.5$ Myr (cite: Baraffe2015)" (4.1 Planets Carving Gaps?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration pipeline and CLEAN imaging  
  > "CASA (cite: McMullin2007), RADMC-3D (cite: Dullemond2012), Hyperion (cite: Robitaille2011), emcee (cite: ForemanMackey2013)" (Software)
- **RADMC-3D** : Monte Carlo radiative transfer  
  > "We use the Monte Carlo radiative transfer codes RADMC-3D (cite: Dullemond2012) and Hyperion (cite: Robitaille2011)" (3 Results)
- **Hyperion** : Monte Carlo radiative transfer  
  > "We use the Monte Carlo radiative transfer codes RADMC-3D (cite: Dullemond2012) and Hyperion (cite: Robitaille2011)" (3 Results)
- **emcee** : MCMC fitting  
  > "using the MCMC code `emcee` (cite: ForemanMackey2013)" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gap 1 radius | 10.0 | 0.2 | AU | 3 | $R_{gap,1}$ \[AU\] / $10.0 \pm   0.2$ |
| Gap 2 radius | 40.9 | 0.4 | AU | 3 | $R_{gap,2}$ \[AU\] / $40.9 \pm   0.4$ |
| Gap 3 radius | 69.4 | 0.6 | AU | 3 | $R_{gap,3}$ \[AU\] / $69.4 \pm   0.6$ |
| Gap 2 width | 30.0 | 6.7 | AU | 3 | $w_{gap,2}$ \[AU\] / $30.0 \pm  6.7$ |
| Inclination | 41 | 1 | deg | 3 | $i$ \[$^{\circ}$\] / $41 \pm  1$ |
| Disk radius | 75 | 1 | AU | 3 | $R_{disk}$ \[AU\] / $75 \pm     1$ |
| Disk mass | 0.17 | 0.00 | Msun | 3 | $M_{disk}$ \[$M_{\odot}$\] / $0.17 \pm  0.00$ |
| GY 91 Menv/Mdisk | 0.121 | not stated | dimensionless | 4 | Our model for HL Tau has $M_{env} = 0.106 \, M_{disk}$, similar to what we find for GY 91 ($M_{env} = 0.121 \, M_{disk}$). |
| HL Tau Menv/Mdisk | 0.106 | not stated | dimensionless | 4 | Our model for HL Tau has $M_{env} = 0.106 \, M_{disk}$ |
| Planet masses needed for gaps | ~0.2, ~0.2, ~0.002 | not stated | M_J | 4 | planets of masses $\sim0.2$ M$_J$, $\sim$0.2 M$_J$, and $\sim$0.002 M$_J$ are needed to produce the observed gaps. |

## Qualitative findings

- The outermost gap roughly matches the N2 freeze-out region; no snow line counterparts for the inner two gaps  
  > "The outermost gap does roughly match the freeze out region of $N_2$. However no obvious counterparts are seen for the inner two gaps." (4.2 Other Causes of Dark Lanes)

## Claim tuples

- H: GY 91's disk has multiple gaps | E: 870 um and 3 mm imaging plus visibility modeling | R: Three gaps at ~10, 41, 69 AU with widths 7, 30, 10 AU | F: Disk has three dark lanes resembling HL Tau | **supported**
- H: GY 91 is embedded and similar in age to HL Tau | E: Same disk+envelope fit to both sources | R: Menv/Mdisk 0.121 vs 0.106 | F: Similar ages, GY 91 possibly younger | **partially**
- H: Planets carve the gaps | E: Gap width to planet mass relation | R: ~0.2, 0.2, 0.002 MJ | F: Saturn-mass planets possible, but snow lines and dead zones are alternatives | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Geometric fit first because full radiative transfer is computationally expensive  
  > "Because full radiative transfer modeling is very computationally intensive, we make initial estimates" (3 Results)
- Alternative: Snow lines/sintering and zonal flows as alternative gap origins  
  > "Planets aren’t the only possible cause of these features." (4.2 Other Causes of Dark Lanes)
- How they decided it was enough: _not stated_
- Limitation (authors): Inner and outer gap depths not well constrained; planet mass estimates are crude without gas information  
  > "The gap depths for the inner and outer gaps are not well constrained because they are not resolved well by our observations." (3 Results)
- Caveat (inferred, ours): Very large a_max (~8 cm) fitted suggests degeneracy with opacity assumptions
- Caveat (inferred, ours): Tiny formal uncertainties likely underestimate systematics
- Caveat (inferred, ours): Menv/Mdisk as age indicator is weak
- Caveat (inferred, ours): Table text gives Menv/Mdisk 0.12 but table Menv/Mdisk = 0.020/0.17 inconsistent in rounding

## Reproducibility

- Data public (paper): ALMA project data cited with project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00761.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: MCMC priors and setup
- Missing: Geometric model definition
- Missing: Unpublished Sheehan & Eisner modeling paper details
- Missing: CLEAN parameters
- Data volume (inferred): ~100-300 GB raw for Band 3 long baselines and Band 7
- Score (inferred): 4/5, Public data and a clear outline, but MCMC setup, priors and imaging details are missing.
- Rediscovery candidate: no, Radiative transfer fitting recipe is incomplete and depends on an unpublished companion paper.

## Links

- Method: (cite: Sheehan2014) (Modeling procedure and opacities)
- Companion: Sheehan & Eisner (submitted) (Further details of modeling)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 38,
  "rate": 0.535
 },
 "evidence_ok": true
}
```
