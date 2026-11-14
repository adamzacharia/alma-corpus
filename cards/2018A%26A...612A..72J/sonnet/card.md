# The ALMA-PILS survey: 3D modeling of the envelope, disks and dust filament of IRAS 16293-2422

`2018A&A...612A..72J` | Astronomy and Astrophysics 2018 | first author: Jacobsen, S. K. | arXiv: 1712.06984 | DOI: 10.1051/0004-6361/201731668

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What do 3D dust and gas radiative transfer models of IRAS 16293 (envelope, disks, filament, two radiation sources) imply about the disk structures and the luminosities of sources A and B, constrained by ALMA-PILS 868 um continuum and CO isotopologue maps?  
  > "The purpose of this paper is to study the environment of the two components of the binary through 3D radiative transfer modeling and to compare with data from the Atacama Large Millimeter/submillimeter Array." (abstract)
- Target **IRAS 16293-2422 (sources A and B)**: coordinates pointing center 16h32m22.72s, -24d28m34.3s (J2000), between A and B  
  > "The pointing center was set between source A and B at $\alpha_{\mathrm{J2000}}$ = 16$^\mathrm{h}$32$^\mathrm{m}$22$s$72; $\delta_\mathrm{J2000}$ = –24$^{\circ}$28$^{\prime}$34$\ensuremath{''}$3." (Observations); "This luminosity assumes a distance of 120 pc, based on recent distance estimates of the bulk of the $\rho$ Oph cloud from extinction measurements" (Dust radiative transfer modeling); z/distance 120 pc  
  > "The pointing center was set between source A and B at $\alpha_{\mathrm{J2000}}$ = 16$^\mathrm{h}$32$^\mathrm{m}$22$s$72; $\delta_\mathrm{J2000}$ = –24$^{\circ}$28$^{\prime}$34$\ensuremath{''}$3." (Observations); "This luminosity assumes a distance of 120 pc, based on recent distance estimates of the bulk of the $\rho$ Oph cloud from extinction measurements" (Dust radiative transfer modeling); distance from rho Oph cloud extinction measurements (Knude & Hog 1998; Lombardi et al. 2008) and VLBI parallax (Loinard et al. 2008)  
  > "The pointing center was set between source A and B at $\alpha_{\mathrm{J2000}}$ = 16$^\mathrm{h}$32$^\mathrm{m}$22$s$72; $\delta_\mathrm{J2000}$ = –24$^{\circ}$28$^{\prime}$34$\ensuremath{''}$3." (Observations); "This luminosity assumes a distance of 120 pc, based on recent distance estimates of the bulk of the $\rho$ Oph cloud from extinction measurements" (Dust radiative transfer modeling)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7 (~0.8 mm; 868 um continuum and CO 3-2) used; Bands 3 and 6 not used  
  > "The dust continuum images from Bands 3 and 6 were not used in this work due to lower spatial resolutions than the Band 7 data" (Observations)
- frequencies and spectral setup: Band 7 covers 329.15 to 362.90 GHz with ~0.2 km/s spectral resolution  
  > "The Band 7 data cover the frequency range from 329.15 to 362.90 GHz with $\sim$0.2 km s$^{-1}$ spectral resolution" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array plus Atacama Compact Array (ACA)  
  > "which include data from both the array of 12 m telescopes and the Atacama Compact Array (ACA)" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5'' (60 AU at 120 pc); beam 0.5''x0.5'' used for comparison  
  > "$\sim$0.5$''$ angular resolution (60 AU beam diameter, assuming $d$=120 pc)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PILS program, PI Jes K. Jørgensen  
  > "The PILS program (PI: Jes K. Jørgensen, project-id: 2013.1.00278.S)" (Observations)
- Line: 13CO J=3-2 (not stated)
- Line: C18O J=3-2 (not stated)
- Line: C17O J=3-2 (not stated)
- External data: Total luminosity 21 +/- 5 Lsun from SED integration  
  > "where the luminosity is estimated to be $21\pm5$ L$_{\ensuremath{\odot}}$ (cite: 2016A&A...595A.117J)" (Dust radiative transfer modeling) [from (cite: 2016A&A...595A.117J)]
- External data: Disk B column density limit N_H2 > 1.2e25 cm-2  
  > "which (cite: 2016A&A...595A.117J) derive to be N$_{\text{H$_2$}}$ \> $\:1.2\times10^{25}$ cm$^{-2}$, was used as well." (4.1 Disk component model constraints) [from (cite: 2016A&A...595A.117J)]
- External data: Dust opacities (thin ice mantles and bare grains, n=1e6 cm-3)  
  > "We used dust opacities from (cite: 1994A&A...291..943O)" (Dust opacity & temperature) [from (cite: 1994A&A...291..943O)]
- External data: Envelope power-law index p = 1.7 and 1D envelope model  
  > "We fixed $p$ = 1.7, taken from (cite: 2002A&A...390.1001S)." (Dust envelope model) [from (cite: 2002A&A...390.1001S)]
- External data: CO isotopologue abundances  
  > "were found by using the C and O isotopologue abundances given by (cite: 1994ARA&A..32..191W)" (Abundance modeling) [from (cite: 1994ARA&A..32..191W)]
- External data: Collisional rate coefficients from LAMDA  
  > "The CO isotopologue data files containing collisional rate coefficients (cite: 2010ApJ...718.1062Y) were downloaded from the LAMDA" (Gas line emission modeling) [from (cite: 2010ApJ...718.1062Y)]

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
- final beam: 0.5''x0.5''  
  > "after convolution with a 0.5$^{\prime\prime}\times0.5^{\prime\prime}$ beam using `MIRIAD`" (4.5 Disk component models)
- final rms: _not stated_

### Inherited from earlier work

- Survey details, data reduction and observation overview  
  > "Further details about the survey, data reduction and an overview of the observations can be found in (cite: 2016A&A...595A.117J)." (Observations) [from (cite: 2016A&A...595A.117J)]
- Continuum image as average of Band 7 continuum channels  
  > "The continuum image was taken as an average of the Band 7 continuum in each channel (cite: 2016A&A...595A.117J)." (Observations) [from (cite: 2016A&A...595A.117J)]
- Blackbody 5000 K stellar spectra  
  > "following (cite: 2002A&A...390.1001S)" (Table notes) [from (cite: 2002A&A...390.1001S)]
- Source A LSR velocity 3.1 km/s  
  > "The source A LSR velocity of 3.1 km s$^{-1}$ (cite: 2011A&A...534A.100J) was used for all lines." (Observations) [from (cite: 2011A&A...534A.100J)]

### Not stated but needed to reproduce (our reading)

- Calibration, imaging parameters (robust, deconvolver, clean masks) and combination of 12m and ACA data are only in Jørgensen et al. 2016
- Which PILS data products/cubes were used and their final rms
- Exact stellar/disk parameters for models in full (model grids not fully listed); no code released
- Exact moment-0 velocity ranges/line frequencies and noise thresholds
- Image-plane comparison of models with data is qualitative; no beam-matching/uv-sampling details of model comparison

## Analysis recipe

1. **Extract continuum and CO isotopologue moment-0 maps**: Channels within +/-5 km/s of each line combined into moment-0 maps; continuum from Band 7 channel average  
  > "Channels within $\pm$ 5 km s$^{-1}$ of each line were combined into an integrated intensity (moment zero) map for each isotopologue, using the image analysis software `MIRIAD`." (Observations)
   - software: MIRIAD
   - parameter: LSR velocity 3.1 km/s  
  > "The source A LSR velocity of 3.1 km s$^{-1}$ (cite: 2011A&A...534A.100J) was used for all lines." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare envelope temperature for one vs two sources**: RADMC-3D Monte Carlo dust temperature for 1D envelope with density plateau; volumes above 30, 50, 90 K for one or two sources  
  > "we used the dust envelope model from Eq. [\[eq:rhoplat\]](#eq:rhoplat) with one or two radiation sources in `RADMC-3D`, without including the filament and disk component models." (Envelope temperature structure)
   - software: RADMC-3D
   - parameter: rplat = 600 AU, p = 1.7, L = 21 Lsun total, L1 = 10.5, 14.0 or 18.0  
  > "$r_{\mathrm{plat}}$ = 600 AU, $L_*$ = 21 L$_{\ensuremath{\odot}}$ (if one source) and $L_1$ = 10.5, 14.0 or 18.0 L$_{\ensuremath{\odot}}$" (Envelope temperature structure)
   - assumption: Sublimation temperatures 30 K (CO), 50 K (H2CO), 90 K (H2O)  
  > "as these temperatures roughly correspond to the sublimation temperatures of CO, H$_2$CO and H$_2$O, respectively" (Envelope temperature structure)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model 3D dust density (envelope, filament, PP-disk or rotating toroid disks) and compare to 868 um continuum**: RADMC-3D dust temperature and ray tracing at 868 um, convolved to 0.5'' beam, compared with peak fluxes (within 10%), aspect ratio of disk A (1.64, within 10%) and N_H2 limit; coarse parameter-space exclusion  
  > "which we required the model to match within 10 % along with the peak central flux density of source A within 10 %." (4.1 Disk component model constraints)
   - software: RADMC-3D, MIRIAD
   - parameter: PP-disk p = 0.5, flaring Psi = 0.25 fixed; Sigma0, H0, i, LA free  
  > "while $p$ and $\varPsi$ were fixed to 0.5 and 0.25, respectively" (4.6 Model analysis)
   - parameter: Disk radii 150 AU (A) and 50 AU (B); MA = 1 Msun, MB = 0.1 Msun  
  > "The disk component models were fixed to 150 and 50 AU around source A and B, respectively" (4 Dust density structures of IRAS 16293)
   - assumption: Dust-to-gas mass ratio 100; bare-grain opacities above 90 K, iterated twice  
  > "Therefore, two recursions of the bare-grain opacity allocation, that is, three Monte Carlo dust temperature estimations in total were performed" (Dust opacity & temperature)
   - fitting: No MCMC or chi2; coarse grid and parameter exclusion; no confidence intervals  
  > "standard model optimization approaches such as a Markov Chain Monte Carlo (MCMC) or a $\chi^2$ analysis of a large, uniform grid of model parameters were not feasible in this work and no parameter confidence intervals were derived." (4.5 Disk component models)
   - validation: SED sanity check; filament column density check against 0.056 Jy/beam gives 9.9 vs model 9.7 g cm-2  
  > "The dust column density of the filament was derived to be 9.9 g cm$^{-2}$, while the model column density was 9.7 g cm$^{-2}$" (4.3 Dust filament)
4. **Model CO isotopologue emission and constrain luminosity ratio**: LIME non-LTE line radiative transfer on RADMC-3D dust temperatures; abundance jump at 30 K; synthetic moment-0 maps compared qualitatively with observations at different LA  
  > "the $J$=3–2 line emission from $^{13}$CO, C$^{17}$O and C$^{18}$O of select dust models were modeled in `LIME`" (Gas line emission modeling)
   - software: LIME, RADMC-3D
   - parameter: Freeze-out factor 0.01 below 30 K; abundances lowered by factor 5 for matching C18O  
  > "a drop factor of 10$^{-2}$ was used in regions with $T$ $<$ 30 K, to imitate freeze-out" (Abundance modeling)
   - assumption: Gas and dust temperatures coupled; Keplerian rotation (PP-disk), Terebey et al. velocities (toroid), free-fall elsewhere; LIME model radius 2000 AU  
  > "we assumed that the dust and gas temperatures are coupled" (Gas line emission modeling)
   - fitting: _not stated_
   - validation: Qualitative comparison of synthetic and observed moment maps  
  > "Optimally, the absorption features around each source and the major features of the interbinary CO isotopologue emission seen in Fig. [2](#fig:co_obs) were recreated in the synthetic moment zero maps" (Gas line emission modeling)

## Software

- **MIRIAD** : Moment-0 maps and convolution of model images  
  > "using the image analysis software `MIRIAD`" (Observations)
- **RADMC-3D** : Dust temperature, continuum images and SED  
  > "To determine the dust temperature and to produce continuum images, the radiative transfer code `RADMC-3D`" (RADMC-3D)
- **LIME** v. 1.5 (with custom changes): Non-LTE CO isotopologue line radiative transfer  
  > "`LIME` performs non-LTE (Local Thermodynamic Equilibrium) line radiative transfer modeling" (Gas line emission modeling)
- **Astropy** : Python package acknowledged as used  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Luminosity of source A | ~18 | coarse parameter steps; not stated | Lsun | 4 | $L_\mathrm{A}$ $\sim$ 18 L$_\ensuremath{\odot}$ and $L_\mathrm{B}$ $\sim$ 3 L$_\ensuremath{\odot}$ |
| Luminosity of source B | ~3 | not stated | Lsun | 4 | $L_\mathrm{A}$ $\sim$ 18 L$_\ensuremath{\odot}$ and $L_\mathrm{B}$ $\sim$ 3 L$_\ensuremath{\odot}$ |
| Observed aspect ratio of 868 um continuum around source A | 1.64 | not stated | dimensionless | 3 | The observed 868 $\upmu$m continuum emission in a 2$^{\prime\prime} \times 2^{\prime\prime}$ box around source A was found to have an aspect ratio of 1.64 |
| Disk B PP-disk scale height at 100 AU needed for LB = 3 Lsun | >53 | not stated | AU | 3 | the PP-disk model around source B needs a scale-height of more than 53 AU at 100 AU, when $L_\mathrm{B}$ = 3 L$_{\ensuremath{\odot}}$ |
| Relative difference in 90 K volume, single star vs binary | up to ~40% | not stated | percent | 2 | This is more pronounced for the 90 K volumes, where the relative difference is almost up to $40~\%$. |
| Filament dust column density, observed vs model | 9.9 vs 9.7 | not stated | g cm-2 | 3 | The dust column density of the filament was derived to be 9.9 g cm$^{-2}$, while the model column density was 9.7 g cm$^{-2}$ |

## Qualitative findings

- Disk B must be vertically extended (puffed up); disk A structure unconstrained  
  > "the disk around source B has to be vertically extended" (abstract)
- Single-source approximation overestimates volume of warm sublimated regions unless one source dominates  
  > "as the total amount of sublimated gas will otherwise be overestimated" (Envelope temperature structure)

## Claim tuples

- H: Are the disks of IRAS 16293 A and B consistent with a PP-disk or a rotating toroid density structure? | E: 3D RADMC-3D models compared with the 868 um continuum and CO isotopologue maps | R: PP-disk B needs H0 > 3 AU at 10 AU; the rotating toroid matches naturally; disk A not constrained | F: Disk B is vertically extended; A unconstrained | **supported**
- H: What is the luminosity ratio of sources A and B? | E: Synthetic CO maps and continuum at varying LA (total 21 Lsun) | R: LA >= 18 Lsun reproduces emission concentrated toward A | F: LA ~ 18 and LB ~ 3 Lsun | **partially**
- H: Does a single-source approximation affect hot-corino temperature volumes? | E: One- vs two-source RADMC-3D envelope models | R: Single star has larger 50-90 K volumes, up to ~25-40% | F: Two sources should be included unless one dominates | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: MCMC or chi2 grids infeasible because single models take days  
  > "the thermal Monte Carlo calculation execution time, on the available computing facilities, for a single model was very long, sometimes on the order of days." (4.5 Disk component models)
- Alternative: Bands 3 and 6 continuum not used due to lower resolution confusing disks with filament  
  > "The dust continuum images from Bands 3 and 6 were not used in this work due to lower spatial resolutions than the Band 7 data" (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Match is qualitative; no confidence intervals; parameters coarse; CO abundance result may be model dependent  
  > "This result needs to be investigated further, as the low abundances could be model dependent." (Conclusions)
- Caveat (inferred, ours): Luminosity constraint rests on qualitative visual comparison of maps, not quantitative fit
- Caveat (inferred, ours): Degeneracies between density, luminosity, opacity and abundance; fixed p and Psi, single dust opacity
- Caveat (inferred, ours): Filament in plane of sky and equal-distance sources assumed
- Caveat (inferred, ours): Nonstandard abundances (factor 5) required

## Reproducibility

- Data public (paper): ALMA data acknowledged as 2013.1.00278.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Custom LIME modifications not released
- Missing: Calibrated PILS cubes/reduction from companion paper
- Missing: Full set of tested models and exact fixed parameters
- Data volume (inferred): Large (hundreds of GB for full PILS dataset; only Band 7 CO and continuum needed, tens of GB)
- Score (inferred): 3/5, Data public, models described with tables, but comparison qualitative, long runtimes and custom code unreleased
- Rediscovery candidate: no, Results are qualitative model comparisons with very expensive custom radiative transfer and no confidence intervals.

## Links

- Method: (cite: 2016A&A...595A.117J) (PILS survey, data reduction and observations)
- Companion: Van der Wiel et al. in prep. (Gas kinematics analysis)
- Related: ALMA Protostellar Interferometric Line Survey (PILS)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 45,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
