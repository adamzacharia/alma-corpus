# Planck's dusty GEMS. IV. Star formation and feedback in a maximum starburst at z = 3 seen at 60-pc resolution

`2017A&A...604A.117C` | Astronomy and Astrophysics 2017 | first author: Cañameras, R. | arXiv: 1704.05853 | DOI: 10.1051/0004-6361/201630186

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How intense can star formation be in a maximal starburst at z=3, and is it self-regulated by feedback (radiation pressure, supernovae and winds) as seen on ~60 pc scales?  
  > "We also present a first discussion of how feedback from star formation leaves its imprint on the resolved star-formation law and kinematic properties of the gas." (Introduction)
- Target **PLCK G244.8+54.9 (the Ruby)**: coordinates clump 1.1 at 10:53:53.137 +05:56:19.65 (J2000)  
  > "At $z=3.005$ this implies a luminosity distance of 26.0 Gpc, and a projected physical scale of 7.85 kpc arcsec$^{-1}$." (Introduction); "1.1 | 10:53:53.137 | +05:56:19.65" (Table 1); z/distance z=3.005, D_L = 26.0 Gpc (lens at z=1.52)  
  > "At $z=3.005$ this implies a luminosity distance of 26.0 Gpc, and a projected physical scale of 7.85 kpc arcsec$^{-1}$." (Introduction); "1.1 | 10:53:53.137 | +05:56:19.65" (Table 1); distance from Planck cosmology (H0=68, Om=0.31); CO redshift  
  > "At $z=3.005$ this implies a luminosity distance of 26.0 Gpc, and a projected physical scale of 7.85 kpc arcsec$^{-1}$." (Introduction); "1.1 | 10:53:53.137 | +05:56:19.65" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01518.S
- bands: Band 3  
  > "ALMA band 3 interferometry of CO(4-3) and dust" (2.1 heading)
- frequencies and spectral setup: baseband 1 on CO(4-3) at 114.888 GHz; continuum windows at 100.908, 102.783, 112.897 GHz  
  > "We had centered baseband 1 on the redshifted CO(4–3) line at 114.888 GHz, and the remaining three spectral windows onto the continuum at frequencies of 100.908 GHz, 102.783 GHz, and 112.897 GHz" (2.1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: long baseline C36-8, max baselines over 10 km  
  > "in the long baseline configuration C36-8 with maximum baselines of over 10 km" (2.1)
- baselines: _not stated_
- angular resolution: 0.14'' x 0.06'' at PA=55 deg  
  > "The beam size is 0.14$''$$\times$0.06$''$ along ${\rm PA}=55^\circ$." (2.1)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.014 mJy/beam; CO cube 0.34 mJy/beam per 24.4 MHz (63.7 km/s) channel  
  > "The rms in the final continuum image is 0.014 mJy beam$^{-1}$, and 0.34 mJy beam$^{-1}$ in the CO(4–3) cube" (2.1)
- time on source: 58 min with 35 antennas  
  > "The target was observed for 58 min with 35 antennas" (2.1)
- observing dates: October 23 2015  
  > "were taken on October 23 2015" (2.1)
- pi or archival as stated: PI Nesvadba, Cycle 3 program  
  > "These ALMA Cycle 3 data (2015.1.01518.S, PI Nesvadba)" (2.1)
- Line: CO 4-3 (redshifted to 114.888 GHz)
- Other facility **Herschel/SPIRE**: FIR photometry and modified blackbody fits (from earlier paper)  
  > "The modified blackbody fits to the *Herschel*/SPIRE photometry of (cite: canameras15)" (Introduction)
- Other facility **SMA / ALMA 3 mm (C17)**: Einstein ring imaging and lens model  
  > "SMA-850 $\mu$m and ALMA-3 mm interferometry show a near-complete Einstein ring with 1.4$''$ diameter" (Introduction)
- External data: Lens model, source-plane reconstruction and magnifications from LENSTOOL  
  > "Detailed lens modeling with `LENSTOOL` (cite: jullo07) suggests typical gravitational magnification factors between 10 and 40" (Introduction) [from C17 (cite: canameras17)]
- External data: Dust SED (T=50 K, beta=2.0) and FIR luminosity  
  > "with a global temperature, $T=50$ K, and $\beta=2.0$ (cite: canameras15)" (5.1 Schmidt-Kennicutt law) [from (cite: canameras15)]
- Simulation/model as data: Starburst99 energy/momentum injection; Andrews & Thompson 2011, Ostriker & Shetty 2011, Faucher-Giguere 2013 feedback models compared with data  
  > "We compare the star-formation intensity with the models of (cite: andrews11) and (cite: ostriker11)" (5.2)

## Processing

### Calibration

- pipeline or manual: standard manual scripts in CASA  
  > "we used the standard manual scripts with the Common Astronomy Software Application (CASA)" (2.1)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN, channel and velocity modes  
  > "The data were imaged into cubes using the “channel” and “velocity” modes" (2.1)
- deconvolver: _not stated_
- weighting robust: briggs, robust=0.5  
  > "“briggs” weighting with robust$=0.5$" (2.1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: custom cleaning masks, 1000 iterations  
  > "custom cleaning masks using 1000 iterations" (2.1)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.14'' x 0.06'', PA=55 deg  
  > "The beam size is 0.14$''$$\times$0.06$''$ along ${\rm PA}=55^\circ$." (2.1)
- final rms: 0.014 mJy/beam continuum; 0.34 mJy/beam in CO cube  
  > "The rms in the final continuum image is 0.014 mJy beam$^{-1}$" (2.1)

### Inherited from earlier work

- Lens model and image-system identification  
  > "The source-plane reconstruction of C17 obtained with `LENSTOOL` suggests that these two image systems trace two independent regions" (4) [from C17 (cite: canameras17)]
- Star formation rate calibration SFR=4.5e-44 L_FIR, with factor 1.8 for Chabrier  
  > "We follow (cite: kennicutt89) in estimating the star-formation rates by setting ${\rm SFR}=4.5\times 10^{-44} L_{\rm FIR}$" (5.1) [from (cite: kennicutt89)]
- Gas mass from CO line flux  
  > "We follow (cite: solomon97) to estimate molecular gas masses from the CO line flux of each spatial pixel" (5.1) [from (cite: solomon97)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method for the cube
- Image size, cell size and clean threshold
- Flux calibrator and calibration pipeline/CASA version
- Details of per-pixel Gaussian fitting (S/N cut, initial guesses)
- Lens model files and magnification maps
- How pixel-by-pixel SFR and gas surface densities were mapped to source plane
- Averaging/masking used for Clumpfind beyond threshold levels

## Analysis recipe

1. **Reduce and image ALMA data**: Manual CASA calibration, CLEAN imaging of cubes and continuum  
  > "using CLEAN to construct the synthesized beam de-convolved images of the frequency data cubes and continuum images" (2.1)
   - software: CASA
   - parameter: briggs robust=0.5, 1000 iterations, 63.7 km/s channels  
  > "“briggs” weighting with robust$=0.5$, and custom cleaning masks using 1000 iterations" (2.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Map CO(4-3) moments per pixel**: Single Gaussian fit to each spatial pixel for flux, velocity, width  
  > "by fitting single Gaussian profiles to each spatial pixel with a custom IDL routine based on the MPFIT algorithm" (3.1)
   - software: IDL, MPFIT
   - fitting: Gaussian least squares (MPFIT)  
  > "MPFIT algorithm of (cite: markwardt09)" (3.1)
   - validation: _not stated_
3. **Identify clumps and image systems**: Clumpfind in 3D cube; reassemble clumps into lens images  
  > "we analyzed the CO(4–3) data cube with the Clumpfind algorithm (cite: williams94)" (3.2)
   - software: Clumpfind
   - parameter: steps of 2 sigma starting at 2 sigma; sigma=2 mJy from cube smoothed 3 pixels spatially and 5 spectrally; clumps >=5 sigma  
  > "We ran Clumpfind in steps of $2\sigma$, starting at $2\sigma$" (3.2)
   - fitting: _not stated_
   - validation: Inverted cube found no spurious clumps >4 sigma; compared with C17 image assignment  
  > "We also inverted the cube, to provide another constraint on the potential number of spurious clumps, finding none with $>4\sigma$ significance." (3.2)
4. **Dynamical mass and Toomre Q**: M_dyn = v^2 R/G with v = dv/2 sin i; Toomre Q from Genzel+14 parametrization  
  > "we can provide dynamical mass estimates by setting $M_{dyn}= v^2 R / G$" (4.1)
   - parameter: R1=700 pc, R2=600 pc; Sigma_gas=1e4 Msun/pc2; a=2  
  > "with intrinsic sizes $R_1 = 700$ pc and $R_2 =600$ pc for regions 1 and 2" (4.1)
   - assumption: velocity gradients trace rotation of a disk; inclination not corrected  
  > "If these gradients approximately sample gravitational motion within a rotating disk" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Resolved Schmidt-Kennicutt law**: Per-pixel (0.04'') continuum extrapolated with modified blackbody to L_FIR then SFR; gas mass from CO via alpha_CO and r43/10  
  > "we measured the average continuum flux density in each 0.04$''$$\times$0.04$''$ pixel in our line-free ALMA spectral windows 1 and 2" (5.1)
   - parameter: T=50 K, beta=2.0; alpha_CO=0.8; r43/10=0.6; SFR divided by 1.8 for Chabrier  
  > "we therefore adopt r$_{43/10}=0.6$" (5.1)
   - assumption: alpha_CO=0.8 Msun (K km/s pc2)^-1  
  > "adopt a CO-to-H$_2$ conversion factor of $\alpha_{\rm CO}=0.8$" (5.1)
   - fitting: _not stated_
   - validation: Compared with feedback models and other lensed galaxies  
  > "Fig. [6](#fig:sklaw) shows that the Ruby falls into the regime expected from a self-regulated starburst for all these approaches." (5.2)
6. **Feedback energetics, SF efficiency, virial parameter**: Kinetic energy and momentum per pixel vs Starburst99 and radiation pressure injection; free-fall time efficiency; alpha_vir  
  > "by setting $E_{\rm kin,turb}=3/2\ \Sigma\ m_{\rm i}\ \sigma_{\rm i}^2$ and $p=\Sigma\ m_{\rm i}\ \sigma_{\rm i}$" (6.1)
   - software: Starburst99
   - parameter: starburst age lower limit 10 Myr; cloud sizes 50-100 pc  
  > "Adopting a lower limit on the starburst age in the Ruby of 10 Myrs" (6.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and CLEAN imaging  
  > "Common Astronomy Software Application (CASA)" (2.1)
- **Clumpfind** : 3D clump identification in CO cube  
  > "Clumpfind algorithm (cite: williams94)" (3.2)
- **MPFIT (IDL)** : per-pixel Gaussian fits  
  > "custom IDL routine based on the MPFIT algorithm" (3.1)
- **LENSTOOL** : lens model and source-plane reconstruction (CleanLens)  
  > "determined through the CleanLens algorithm within `LENSTOOL`" (4)
- **Starburst99** : energy and momentum injection rates  
  > "We use Starburst99 (cite: leitherer99) to estimate the energy and momentum injection rates" (5.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Intensity-weighted continuum flux recovered | 2.00 | 0.05 | mJy | 1 | we recover 73% of this flux density, that is, 2.00$\pm0.05$ mJy |
| Clumps found by Clumpfind | 12 (11 real) | not stated | dimensionless | 3 | With Clumpfind we identified a total of 12 clumps at $\ge 5
\sigma$. |
| Toomre Q | 1.0 | 0.3 | dimensionless | 4 | This gives $Q=1.0\pm0.3$. |
| Star-formation intensity range | 220-2200 | not stated | Msun/yr/kpc2 | 5 | local star-formation intensities of $220-2200$ M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| Gas surface density range | 10^3.7-10^4.7 | not stated | Msun/pc2 | 5 | resulting gas-mass surface densities are within $10^{3.7-4.7}$ M$_{\odot}$ pc$^{-2}$ |
| Star-formation efficiency per free-fall time | 1-9% | not stated | percent | 6 | corresponding to a range of approximately $1-9$% of the available gas-mass |
| Luminosity-weighted magnification (continuum, CO) | 33.8 and 43.6 | 6.4, 8.2 | dimensionless | 0 | $33.8\pm6.4$ and $43.6\pm8.2$ for the FIR continuum luminosity and CO(4–3) line luminosity |
| Intrinsic SFR of image 1.1 | 335 | 2 | Msun/yr | 5 | ${\rm SFR}=335\pm2$ M$_{\odot}$ yr$^{-1}$ |

## Qualitative findings

- Ruby sits in the self-regulated, feedback-dominated regime; no clear outflows detected; differential lensing effect ~10-30%.  
  > "the location of the Ruby in the Schmidt-Kennicutt diagram suggests that star formation is self-regulated" (7 Summary)

## Claim tuples

- H: Does the Ruby reach maximal-starburst star-formation intensities? | E: Pixel-by-pixel SFR from 3 mm continuum and gas from CO(4-3) | R: SFR intensity up to 2200 Msun/yr/kpc2 | F: Ruby is a maximal starburst consistent with Eddington-limited models | **supported**
- H: Is differential lensing a major bias? | E: Compared luminosity-weighted magnifications of CO and dust | R: differences ~10-22% | F: Differential lensing small | **supported**
- H: Can SF feedback power the turbulence and keep clouds marginally bound? | E: Compared kinetic energy/momentum to injection and alpha_vir | R: both mechanical and radiation feedback sufficient | F: Feedback sustains marginal stability; efficiency 1-10% | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Clumpfind used for robust, reproducible clump identification; direct velocity range instead of kinemetry due to few resolution elements  
  > "in a robust, reproducible way, we analyzed the CO(4–3) data cube with the Clumpfind algorithm" (3.2)
- Alternative: Kinemetry rejected, needs up to 15 free parameters.  
  > "rely on fitting up to 15 free parameters internally, which we cannot provide with our data set" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO and r43/10 make gas surface densities uncertain by a few tenths of a dex.  
  > "make gas mass surface density estimates uncertain by a few tenths of a dex" (5.2)
- Limitation (authors): 27% of expected continuum flux missed.  
  > "Most of the missing flux is likely to be in the extended diffuse regions" (3.1)
- Caveat (inferred, ours): Dynamical masses assume disk rotation and no inclination correction
- Caveat (inferred, ours): Energetics rely on assumed starburst age and alpha_CO
- Caveat (inferred, ours): Lens model uncertainties propagate to source-plane sizes and magnifications

## Reproducibility

- Data public (paper): ALMA program 2015.1.01518.S acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01518.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Lens model/magnification maps from C17
- Missing: Custom IDL fitting code
- Missing: Reduction script details
- Data volume (inferred): ~100 GB raw for a 58 min long-baseline Band 3 execution
- Score (inferred): 3/5, Data is archival and the recipe is outlined, but lens model, imaging parameters and calibrations are incomplete.
- Rediscovery candidate: no, Depends on external lens model and unreleased custom code; imaging details missing.

## Links

- Method: (cite: williams94) (Clumpfind algorithm)
- Method: (cite: jullo07) (LENSTOOL lens modeling)
- Companion: (cite: canameras17) (C17: lens model and image identification for the Ruby)
- Companion: (cite: canameras15) (Planck's dusty GEMS SED and FIR properties)
- Related: Planck's Dusty GEMS

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
  "facts": 85,
  "stated": 53,
  "rate": 0.624
 },
 "evidence_ok": true
}
```
