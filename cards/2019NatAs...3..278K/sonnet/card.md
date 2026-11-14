# Publisher Correction: A circumbinary protoplanetary disk in a polar configuration

`2019NatAs...3..278K` | Nature Astronomy 2019 | first author: Kennedy, Grant M. | arXiv: 1901.05018 | DOI: 10.1038/s41550-019-0715-1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the orientation, size and structure of the circumbinary disc around HD 98800BaBb, and is it a misaligned, polar, planet-forming disc?  
  > "To ascertain the disc orientation, size, structure, and evolutionary status we observed the HD 98800 system with the Atacama Large Millimeter/sub-millimeter Array (ALMA, see Methods)." (main text)
- Target **HD 98800 (BaBb circumbinary disc)**: coordinates BaBb at RA 11 22 05.17437, Dec -24 46 39.5043 (epoch 2017.874)  
  > "The HD 98800 system is a well known hierarchical quadruple star system 44.9 parsecs from Earth (cite: 2007A&A...474..653V)" (main text); "BaBb is centred at $\alpha = 11$ 22 05.17437, $\delta=-24$ 46 39.5043" (Observations and Data Processing); z/distance 44.9 pc  
  > "The HD 98800 system is a well known hierarchical quadruple star system 44.9 parsecs from Earth (cite: 2007A&A...474..653V)" (main text); "BaBb is centred at $\alpha = 11$ 22 05.17437, $\delta=-24$ 46 39.5043" (Observations and Data Processing); distance from van Leeuwen 2007 (Hipparcos)  
  > "The HD 98800 system is a well known hierarchical quadruple star system 44.9 parsecs from Earth (cite: 2007A&A...474..653V)" (main text); "BaBb is centred at $\alpha = 11$ 22 05.17437, $\delta=-24$ 46 39.5043" (Observations and Data Processing)

## Data provenance

- ALMA projects: 2017.1.00350.S
- bands: Band 6 (1.3 mm)  
  > "HD 98800 was observed by ALMA in Band 6 (1.3 mm) in two observing blocks on 2017 November 15 and 19" (Observations and Data Processing)
- frequencies and spectral setup: three 2 GHz continuum windows plus one window on CO J=2-1 with 488 kHz (0.73 km/s) resolution  
  > "The correlator configuration used three broad continuum windows with 2GHz bandwidth, and one centred on the CO J=2-1 line with a spectral resolution of 488kHz (0.73km s$^{-1}$ velocity resolution)." (Observations and Data Processing)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 92 m to 11.8 km  
  > "The shortest and longest baselines were 92 m and 11.8 km." (Observations and Data Processing)
- angular resolution: 46x42 mas (Briggs robust=0.5)  
  > "In the final Briggs-weighted clean image the beam size is $46 \times 42$mas, the rms is 14 $\mu$Jy beam$^{-1}$" (Observations and Data Processing)
- max recoverable scale: _not stated_
- sensitivity: rms 14 uJy/beam (Briggs continuum); 0.8 mJy/beam per channel for CO  
  > "A naturally-weighted clean CO cube has a beam size of $61 \times 54$ mas, an rms of 0.8 mJy beam$^{-1}$ in each 0.73 km s$^{-1}$ channel" (Observations and Data Processing)
- time on source: 34 minutes per block  
  > "The time on-source was 34 minutes for each block." (Observations and Data Processing)
- observing dates: 2017 November 15 and 19; 49 and 45 antennas  
  > "49 antennas were used in the first block and 45 in the second." (Observations and Data Processing)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230 GHz (approx.))
- Other facility **VLA (Ribas et al. 2018 image)**: Continuum image re-modelled for comparison  
  > "We modelled the VLA image using the model described above" (Comparison with VLA)
- External data: BaBb orbit (e=0.785, node 289, i=67 deg) and mass 1.28 Msun  
  > "The binary BaBb is well characterized, with an eccentricity of $0.785 \pm 0.005$" (main text) [from Boden et al. 2005 (cite: 2005ApJ...635..442B)]
- External data: AB astrometry from the Washington Double Star catalogue  
  > "we obtained previous observations of the AB separation and position angle from the Washington Double Star catalogue (WDS)" (Orbits) [from (cite: 2001AJ....122.3466M)]
- External data: Dust temperature of 160 K from multiwavelength photometry  
  > "assuming a dust temperature of 160K derived from photometry over a range of wavelengths (cite: 1993ApJ...406L..25Z)" (Continuum modelling results) [from Zuckerman & Becklin 1993 (cite: 1993ApJ...406L..25Z)]

## Processing

### Calibration

- pipeline or manual: observatory pipeline  
  > "The raw data were calibrated using the observatory pipeline with CASA v5.1." (Observations and Data Processing)
- casa version: CASA v5.1  
  > "The raw data were calibrated using the observatory pipeline with CASA v5.1." (Observations and Data Processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1127-1857 (also bandpass)  
  > "J1127-1857 was used as the bandpass and flux calibrator." (Observations and Data Processing)
- flux scale uncertainty: 10%  
  > "Including an absolute calibration uncertainty of 10% yields a final flux measurement of $47 \pm 5$ mJy." (Observations and Data Processing)
- self calibration: one cycle phase self-cal, all spws combined, solint 20-40 min  
  > "All spectral windows were combined, and the averaging time (‘solint’) was chosen to be relatively long (20-40min)" (Observations and Data Processing)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5 (also natural and uniform images)  
  > "clean images before self-cal with Briggs weighting (robust=0.5)" (Observations and Data Processing)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub; observations merged with mstransform  
  > "The continuum was subtracted using the CASA `uvcontsub` task, the two observations merged using the `mstransform` task" (Observations and Data Processing)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 46x42 mas Briggs; 64x56 natural; 32x25 uniform  
  > "In a uniformly weighted image the beam size is $32 \times 25$mas, the rms is 43 $\mu$Jy beam$^{-1}$" (Observations and Data Processing)
- final rms: 14 uJy/beam (Briggs)  
  > "the rms is 14 $\mu$Jy beam$^{-1}$, and the peak s/n is 280" (Observations and Data Processing)

### Inherited from earlier work

- Visibility re-weighting so a null model gives chi2 of 1  
  > "The weights associated with each visibility were divided by a re-weighting factor such that a null model produces a $\chi^2$ value of 1" (Observations and Data Processing) [from (cite: 2011A&A...529A.105G)]
- SPH parameters same as earlier polar-disc simulations  
  > "the simulations used the same SPH parameters as ref (cite: 2017ApJ...835L..28M) and 300,000 particles" (Simulations) [from Martin & Lubow 2017 (cite: 2017ApJ...835L..28M)]

### Not stated but needed to reproduce (our reading)

- Exact CLEAN parameters (cell, image size, masks, niter, threshold)
- Self-cal reference antenna and per-block solint
- Prior ranges for MCMC model parameters
- Line-free channels used for uvcontsub
- Phantom viscosity, disc mass and radii setup
- Flux of AA/Ab and AaAb orbit parameters used in n-body

## Analysis recipe

1. **Calibrate and self-calibrate, combine blocks**: Pipeline calibration, one cycle of phase self-cal, concatenate two blocks  
  > "The data were further processed using one cycle of phase self-calibration (self-cal) to improve the signal to noise ratio (s/n)." (Observations and Data Processing)
   - software: CASA
   - fitting: _not stated_
   - validation: Separate continuum fits of each block agree in offset within 0.0002 arcsec and flux within 1%  
  > "The difference in integrated flux densities was consistent to within 1%." (Observations and Data Processing)
2. **Fit continuum and CO visibilities with a power-law disc model**: Line-of-sight integration disc model fit in visibility plane; ring with r_in, r_out, power law, eccentric inner edge for continuum  
  > "Modelling of the continuum and CO data was done in the visibility plane using an optically thin line of sight integration code." (Visibility Modelling)
   - software: emcee, GALARIO
   - parameter: 64 walkers, 1000 steps after 1000 step burn-in; scale height 0.05r; 2048 pixels of 4.6 mas  
  > "The best fitting continuum model was found using 64 ‘walkers’ (parallel MCMC chains) run for 1000 steps" (Continuum modelling results)
   - assumption: CO orbits a point mass of 1.28 Msun  
  > "We assume the CO orbits a single point mass with the combined mass of HD 98800BaBb of 1.28$M_\odot$" (Visibility Modelling)
   - fitting: Likelihood -chi2/2 via GALARIO, sampled with emcee  
  > "The log likelihood $-\chi^2/2$ of each model is computed given the visibility data using GALARIO" (Visibility Modelling)
   - validation: Residual images; optical depth parameter consistent with 0  
  > "the residuals are at most only 1% of the peak" (Continuum modelling results)
3. **Estimate dust and CO gas masses**: Optically thin dust mass from flux; CO mass assuming tau=1, Tex=70 K, H2/CO=1e4  
  > "If we assume that the disc is primordial and has a standard H$_2$/$^{12}$CO ratio of 10$^4$, then the total gas mass is roughly 0.28$M_\oplus$" (CO modelling results)
   - assumption: Opacity 1.7 cm2/g, dust T=160 K  
  > "which assumes an opacity of 1.7 cm$^2$ g$^{-1}$" (Continuum modelling results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit AB orbit**: MCMC orbit fit to WDS astrometry plus two radial velocity constraints  
  > "we use the python `emcee` package to find the best-fitting orbits" (Orbits)
   - software: emcee
   - assumption: Mass of A 1.3±0.15 Msun prior; B 1.28 Msun  
  > "The mass of A is estimated as $1.3 \pm 0.15 M_\odot$" (Orbits)
   - fitting: chi2 of position angles, separations and radial velocities  
  > "we compute the position angles, separations, and 1991.96 and 2017.874 radial velocities, from which we derive a $\chi^2$" (Orbits)
   - validation: _not stated_
5. **Test disc stability with dynamics**: Gas-free n-body (1 Myr) and SPH simulations of both inclination solutions  
  > "We used the ‘whfast’ integrator (cite: 2015MNRAS.452..376R) with a time step of 1/20th of the BaBb orbital period." (Simulations)
   - software: REBOUND, Phantom, splash
   - parameter: 300,000 SPH particles  
  > "the simulations used the same SPH parameters as ref (cite: 2017ApJ...835L..28M) and 300,000 particles" (Simulations)
   - fitting: _not stated_
   - validation: _not stated_
6. **Population estimate of polar fraction**: Monte Carlo of 1e6 random orientations at 16 eccentricities, separatrix c=e^2  
  > "we populate the $i \cos{\Omega}$, $i \sin{\Omega}$ plane with $N=10^6$ orbits." (Population estimate of disc orientations)
   - assumption: Uniform initial orientations, uniform e in 0-0.8  
  > "discs initially have uniformly distributed orientations with respect to the binary" (Population estimate of disc orientations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1: calibration, uvcontsub, mstransform, statwt  
  > "The raw data were calibrated using the observatory pipeline with CASA v5.1." (Observations and Data Processing)
- **emcee** : MCMC for visibility and orbit fits  
  > "Markov-Chain Monte-Carlo (MCMC) package `emcee`" (Visibility Modelling)
- **GALARIO** : visibility likelihood  
  > "computed given the visibility data using GALARIO" (Visibility Modelling)
- **REBOUND** : gas-free n-body simulations  
  > "We simulated the system as gas-free using the REBOUND code" (Simulations)
- **Phantom** : SPH simulations  
  > "We used Phantom (cite: 2018PASA...35...31P) to simulate the response of the two possible disc configurations" (Simulations)
- **splash** : SPH visualisation  
  > "the images were created using `splash`" (Simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust inner/outer edge | 2.5 / 4.6 | ±0.02 / ±0.01 | au | 2 | the inner edges of the dust and CO are at $2.5 \pm 0.02$ and $1.6 \pm 0.3$ au respectively, while the outer edges are at $4.6 \pm 0.01$ and $6.4 \pm 0.5$ au |
| CO inner/outer edge | 1.6 / 6.4 | ±0.3 / ±0.5 | au | 2 | the inner edges of the dust and CO are at $2.5 \pm 0.02$ and $1.6 \pm 0.3$ au respectively, while the outer edges are at $4.6 \pm 0.01$ and $6.4 \pm 0.5$ au |
| Disc position angle | 16 | ±1 | deg | 2 | the disc has a position angle of $16 \pm 1^\circ$ (measured anti-clockwise from North) |
| Total disc flux | 47 | ±5 | mJy | 2 | Including an absolute calibration uncertainty of 10% yields a final flux measurement of $47 \pm 5$ mJy. |
| Dust mass | 0.33 | not stated | Earth masses | 3 | the result is $0.33M_\oplus$ |
| Total gas mass (minimum CO-based) | 0.28 | not stated | Earth masses | 3 | then the total gas mass is roughly 0.28$M_\oplus$ |
| AB orbit eccentricity | 0.52 | ±0.01 | dimensionless | 4 | which has an eccentricity of $0.52 \pm 0.01$ and a period of $246 \pm 5$ years |
| Fraction of discs evolving to polar | 46% | not stated | percent | 6 | found to be 46% |

## Qualitative findings

- The disc is in a polar configuration; the moderately misaligned alternative is reoriented within hundreds of years.  
  > "the moderately misaligned configuration is reoriented on a timescale that is very short relative to the ten million-year old age of the system" (main text)

## Claim tuples

- H: Is the HD 98800BaBb disc strongly misaligned and polar? | E: Visibility modelling of ALMA data plus SPH simulations of both inclination solutions | R: Inclination 26 or 154 deg; 154 deg is 4 deg from polar; the 26 deg case reorients to polar in hundreds of years | F: The disc is in a stable polar configuration | **supported**
- H: Is the disc gas-rich and planet-forming? | E: n-body test particles plus CO and dust masses | R: Particles are ejected within 1 Myr without gas; gas mass comparable to dust | F: Disc is likely gas-rich and protoplanetary, with gas more extended than dust | **partially**
- H: Are polar discs common? | E: Monte Carlo population estimate | R: About 46% of discs evolve to polar | F: Polar circumbinary planets may be common | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Moderately misaligned (26 deg) configuration rejected because it reorients on short timescales.  
  > "the lifetime of the disc in the moderately misaligned case is very short relative to the stellar age of ten million years" (Simulations)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas and dust mass estimates have large systematic uncertainties from optical depth, temperature and H2/CO.  
  > "the empirical evidence for which dominates remains uncertain" (CO modelling results)
- Caveat (inferred, ours): Inclination ambiguity resolved only by dynamical argument
- Caveat (inferred, ours): Simple power-law ring model; optically thick emission ignored
- Caveat (inferred, ours): SPH simulations exclude the outer binary and have no stated resolution tests
- Caveat (inferred, ours): Population estimate assumes uniform initial orientations

## Reproducibility

- Data public (paper): ALMA data available from the ALMA Science Archive  
  > "The ALMA data used in this study are available in the ALMA Science Archive at <http://almascience.eso.org/aq/>." (Data and code availability)
- Products in archive: _not stated_
- Code: Post-processing and modelling scripts on github (drgmk)  
  > "The post-processing, modelling, and other scripts used in this study are available on github at <https://github.com/drgmk>." (Data and code availability)
- Missing: MCMC priors
- Missing: tclean imaging settings
- Missing: Phantom setup details
- Data volume (inferred): about 10-30 GB for two Band 6 execution blocks
- Score (inferred): 4/5, Public data, code on github, and most modelling settings stated; some imaging and SPH details missing.
- Rediscovery candidate: yes, Public data, a clear visibility-modelling recipe and numeric edges, angles and fluxes.

## Links

- Method: Tazzari et al. 2018 (cite: 2018MNRAS.476.4527T) (GALARIO visibility modelling)
- Method: Foreman-Mackey et al. 2013 (cite: 2013PASP..125..306F) (emcee sampler)
- Companion: Ribas et al. 2018 (cite: 2018ApJ...865...77R) (VLA imaging of the HD 98800B disc)
- Companion: Martin & Lubow 2017 (cite: 2017ApJ...835L..28M) (Polar alignment theory and SPH setup)
- Related: TW Hydrae Association

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 53,
  "rate": 0.639
 },
 "evidence_ok": true
}
```
