# Resolving the Nuclear Obscuring Disk in the Compton-thick Seyfert Galaxy NGC 5643 with ALMA

`2018ApJ...859..144A` | The Astrophysical Journal 2018 | first author: Alonso-Herrero, A. | arXiv: 1804.04842 | DOI: 10.3847/1538-4357/aabe30

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Does the nuclear molecular gas of NGC 5643 form a resolved disk that can be identified as the AGN obscuring torus, and how does the circumnuclear gas interact with the AGN outflow?  
  > "We interpret this nuclear molecular gas disk as the obscuring torus of NGC 5643 as well as the collimating structure of the ionization cone." (abstract)
- Target **NGC 5643**: coordinates RA(J2000)=14h32m40.70s, Dec(J2000)=-44d10m27.9s (ALMA continuum peak)  
  > "nearby ($D=16.9\,$Mpc, $1\ensuremath{''} = 81.9\,$pc) Seyfert 2 galaxy NGC 5643" (1 Introduction); "ALMA continuum peak at rest-frame 232 GHz (1.3 mm) RA(J2000) =14$^{\rm h}$ 32$^{\rm m}$ 40.70$^{\rm s}$ and Dec(J2000) = $-44\ensuremath{^\circ}$ 10$\ensuremath{'}$ 27.9$\ensuremath{''}$" (2.2 Archival VLT/MUSE integral field spectroscopy); z/distance D=16.9 Mpc, 1'' = 81.9 pc  
  > "nearby ($D=16.9\,$Mpc, $1\ensuremath{''} = 81.9\,$pc) Seyfert 2 galaxy NGC 5643" (1 Introduction); "ALMA continuum peak at rest-frame 232 GHz (1.3 mm) RA(J2000) =14$^{\rm h}$ 32$^{\rm m}$ 40.70$^{\rm s}$ and Dec(J2000) = $-44\ensuremath{^\circ}$ 10$\ensuremath{'}$ 27.9$\ensuremath{''}$" (2.2 Archival VLT/MUSE integral field spectroscopy); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00254.S
- bands: Band 6  
  > "We obtained Band 6 ALMA observations of NGC 5643" (2.1 ALMA Band 6 observations)
- frequencies and spectral setup: two 1.875 GHz spectral windows, ~228 GHz (CO 2-1) and ~230 GHz (continuum); 3.9 MHz (~5 km/s) channels  
  > "We defined two spectral windows of 1.875 GHz bandwidth (3.9 MHz $\sim$ 5 km/s channels)" (2.1 ALMA Band 6 observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "using the 12-m array in compact (baselines between 15 and 492 m) and extended (baselines between 17 and 3700 m) configurations" (2.1 ALMA Band 6 observations)
- configurations: _not stated_
- baselines: 15-492 m (compact); 17-3700 m (extended)  
  > "compact (baselines between 15 and 492 m) and extended (baselines between 17 and 3700 m) configurations" (2.1 ALMA Band 6 observations)
- angular resolution: 0.11-0.26'' (9-21 pc)  
  > "angular resolutions $0.11-0.26\ensuremath{''}$   ($9-21\,$pc)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: CO cubes ~1.2 and ~0.5 mJy/beam/channel; continuum ~76 and ~37 uJy/beam for b=-0.5 and b=0.8  
  > "The achieved 1$\sigma$ sensitivities are $\sim$1.2 and $\sim$0.5 mJy beam$^{\rm -1}$ channel$^{-1}$ in the CO(2–1) cubes" (2.1 ALMA Band 6 observations)
- time on source: 11 and 36 min  
  > "The on-source integrations times were 11 and 36 min, respectively." (2.1 ALMA Band 6 observations)
- observing dates: 24 December 2016 and 18 July 2017  
  > "on 24 December 2016 and 18 July 2017" (2.1 ALMA Band 6 observations)
- pi or archival as stated: Own program, PI A. Alonso-Herrero  
  > "through the project 2016.1.00254.S (PI: A. Alonso-Herrero)" (2.1 ALMA Band 6 observations)
- Line: 12CO J=2-1 (not stated)
- Other facility **VLT/MUSE**: Archival IFU data (program 095.B-0532(A)) giving [OIII] and Halpha maps  
  > "These observations were part of the program 095.B-0532(A) (PI: Carollo)." (2.2 Archival VLT/MUSE integral field spectroscopy)
- External data: Single-dish CO(2-1) flux 912±60 Jy km/s for a 30'' beam  
  > "the single-dish measurement for a beam size of $30\ensuremath{''}$ is $912
\pm 60\,$ Jy km s$^{-1}$" (2.1 ALMA Band 6 observations) [from (cite: Monje2011)]
- External data: Disk PA and inclination from near-IR stellar kinematics used as starting values  
  > "using the disk PA and inclination derived from the near-infrared stellar kinematics by (cite: Davies2014)" (3.2 Kinematics) [from (cite: Davies2014)]
- External data: Ionization cone inclination i_cone=25 deg and bicone modelling  
  > "inclination of ionization cone derived by (cite: Fischer2013) from the modelling of the narrow line region (NLR) kinematics, $i_{\rm cone} = 25\ensuremath{^\circ}$" (4.2 Kinematics) [from (cite: Fischer2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v.4.7  
  > "We calibrated the data using the ALMA reduction software CASA (v.4.7; (cite: McMullin2007))." (2.1 ALMA Band 6 observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (1.92 Jy at 228.6 GHz, index -0.59) for extended; Callisto (Butler-JPL-Horizons 2012) for compact  
  > "The amplitude was calibrated using J1427-4206 for the extended configuration assuming a flux density of 1.92 Jy at 228.6 GHz and a spectral index of –0.59." (2.1 ALMA Band 6 observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, two configurations combined  
  > "Then, we combined and cleaned the data from the two configurations using the CASA *clean* task." (2.1 ALMA Band 6 observations)
- deconvolver: _not stated_
- weighting robust: natural; Briggs b=0.8 and b=-0.5  
  > "with robustness parameters of $b=0.8$ and $b=-0.5$ to increase sequentially the angular resolution" (2.1 ALMA Band 6 observations)
- uv taper: _not stated_
- cell size: 0.03'' (b=-0.5) and 0.04'' (b=0.8)  
  > "The pixel sizes were set to 0.03$''$ and 0.04$''$" (2.1 ALMA Band 6 observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane constant fit to line-free channels  
  > "we subtracted the continuum (rest-frame 232 GHz) in the $uv$ plane by fitting the continuum with a constant in the line free channels." (2.1 ALMA Band 6 observations)
- line free channels: _not stated_
- primary beam correction: applied, FWHM=27''  
  > "We applied the primary beam (FWHM=27$''$) correction to the data." (2.1 ALMA Band 6 observations)
- array combination: _not stated_
- smoothing: b=0.8 data rebinned by 3 in frequency (~15 km/s)  
  > "for the $b=0.8$ set we rebinned the data by a factor of 3 in frequency to increase the signal-to-noise ratio" (2.1 ALMA Band 6 observations)
- final beam: CO: 0.16x0.11'' PA -67 (b=-0.5); 0.26x0.17'' PA -58 (b=0.8)  
  > "CO(2–1) full-width half-maximum (FWHM) of 0.16$''$$\times$0.11$''$ with beam position angle (${\rm PA}_{\rm beam}$) of –67$^\circ$ for the $b=-0.5$ data set" (Observations (ALMA Band 6 observations))
- final rms: _not stated_

### Inherited from earlier work

- Disk PA/inclination starting values and comparison from SINFONI H2 study  
  > "which are compatible with those inferred from the stellar kinematics (cite: Davies2014)" (3.2 Kinematics) [from (cite: Davies2014)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Clean threshold, masks, niter, deconvolver
- 3DBAROLO ring geometry, radial sampling, masks and parameter settings
- 3DBAROLO version
- Exact CO(2-1) rest frequency and velocity range for moment maps
- Details of how the radial-velocity component was parameterized
- Sakamoto1999 conversion implementation (aperture, brightness-temperature handling)

## Analysis recipe

1. **Image CO(2-1) and continuum**: Combine configurations, uv continuum subtraction, clean with natural and Briggs weights, moment maps with >3 sigma pixels  
  > "For all these maps we used pixels at all frequencies with detections $>3\sigma$." (2.1 ALMA Band 6 observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Recovered ~50% of single-dish flux  
  > "Thus we recovered approximately 50% of the single-dish observation flux" (2.1 ALMA Band 6 observations)
2. **Fit circumnuclear disk kinematics**: 3DBAROLO tilted-ring fit of b=0.8 cube over 8''x8'', residual velocity map, line profiles at three positions  
  > "We used the $^{\rm 3D}$BAROLO code (cite: DiTeodoro2015) to model the CO(2–1) kinematics of the central $8\ensuremath{''} \times 8\ensuremath{''}$ region" (3.2 Kinematics)
   - software: 3DBarolo
   - parameter: PA=320 deg, i=35 deg, vsys=1194 km/s fixed after first run  
  > "${\rm PA}_{\rm disk}= 320\ensuremath{^\circ}$ and $i=35\ensuremath{^\circ}$" (3.2 Kinematics)
   - fitting: Two-step 3D tilted ring fit  
  > "The fit is done in two steps." (3.2 Kinematics)
   - validation: Compared with H2 2.12um kinematics of Davies2014  
  > "These can be compared directly with the H$_2$ $2.12\,\mu$m hot molecular gas maps in Figure 8" (3.2 Kinematics)
3. **Measure nuclear continuum**: uv-plane Gaussian fit  
  > "we modeled the continuum in the $uv$ plane using the UVMULTIFIT library (cite: MartiVidal2014) with a Gaussian function" (4.1 Morphology)
   - software: UVMULTIFIT
   - fitting: Single Gaussian  
  > "We fitted a single Gaussian profile to each of these transitions in each spaxel." (Archival VLT/MUSE integral field spectroscopy)
   - validation: _not stated_
4. **Model nuclear disk kinematics with radial component**: ellipse isophote fit for initial PA/i, then 3DBAROLO on b=-0.5 cube with kinematic center at continuum peak, then with added radial velocity; p-v diagrams  
  > "we rerun $^{\rm 3D}$BAROLO including a radial velocity component with the same assumptions for the rotating disk as above" (4.2 Kinematics)
   - software: 3DBarolo, IRAF ellipse
   - parameter: PA=355 deg, i=60 deg, vsys=1198 km/s  
  > "we fixed the nuclear disk geometry to ${\rm PA}=355\ensuremath{^\circ}$ and $i=60\ensuremath{^\circ}$" (4.2 Kinematics)
   - fitting: _not stated_
   - validation: Residuals ±30 km/s or less with radial component; inclination agrees with ionization cone  
  > "the residuals in the region of the nuclear disk being of the order of $\pm 30\,{\rm km\,s}^{-1}$ or less" (4.2 Kinematics)
5. **Derive gas mass, dynamical mass and column density**: CO(2-1) intensity converted via Sakamoto1999 with Galactic X; spheroid dynamical mass; column density from mass and size  
  > "using the relation of (cite: Sakamoto1999) with a Galactic CO-to-H$_2$ conversion factor" (4.3 Molecular gas mass)
   - assumption: CO(1-0)/CO(2-1) brightness temperature ratio of one; X=2e20 cm-2 (K km/s)-1  
  > "Assuming a CO(1–0)/CO(2–1) brightness temperature ratio of one" (4.3 Molecular gas mass)
   - fitting: _not stated_
   - validation: Compared with X-ray column and gas fraction  
  > "The derived H$_2$ column density is short of the value derived from X-ray observations which provides a lower limit for the obscuring column density toward the AGN in NGC 5643" (Column Density)

## Software

- **CASA** 4.7: Calibration and imaging  
  > "We calibrated the data using the ALMA reduction software CASA (v.4.7; (cite: McMullin2007))." (2.1 ALMA Band 6 observations)
- **3DBarolo** : Tilted-ring kinematic modelling  
  > "$^{\rm 3D}$BAROLO was designed to fit simple disk models using 3D tilted rings" (3.2 Kinematics)
- **UVMULTIFIT** : uv-plane continuum fit  
  > "we modeled the continuum in the $uv$ plane using the UVMULTIFIT library" (4.1 Morphology)
- **IRAF ellipse** : Isophotal fit of nuclear CO emission  
  > "We first fitted a simple isophotal model with the iraf *ellipse* task" (4.2 Kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Nuclear continuum flux (232 GHz) | 1.8 | 0.2 | mJy | 3 | The best fit produced a continuum flux of $1.8\pm0.2\,$mJy |
| Continuum deconvolved FWHM major axis | 0.20 | 0.04 | arcsec | 3 | deconvolved size (FWHM) along the major axis of $0.20\pm0.04$$''$ |
| Nuclear disk H2 mass | 1.1e7 | not stated | Msun | 5 | we derived a molecular gas mass in the nuclear disk of $M({\rm H}_2)=1.1\times 10^7\,M_\odot$ |
| H2 column density at AGN position | 5e23 | not stated | cm-2 | 5 | we would derive a column density of $N({\rm H}_2)\sim 5 \times 10^{23}\,{\rm cm}^{-2}$ |
| Dynamical mass of nuclear disk | 5e7 | not stated | Msun | 5 | This leads to a dynamical mass of approximately $5\times
  10^7\,M_\odot$ |
| CO(2-1) flux over 40''x40'' | 480 | not stated | Jy km/s | 1 | We measure a CO(2–1) line intensity over a region $40\ensuremath{''} \times 40\ensuremath{''}$ of 480  Jy km s$^{-1}$. |
| Nuclear disk FWHM (N-S x E-W) | 0.32'' x 0.24'' (26 x 20 pc) | not stated | arcsec | 1 | measured FWHM of $0.32\ensuremath{''}$ in the approximate north-south direction and $0.24\ensuremath{''}$ in the east-west direction |

## Qualitative findings

- CO(2-1) avoids the [OIII] ionization cone region and shows redshifted second components NE of the nucleus interpreted as gas pushed outward by the AGN outflow  
  > "most of the CO(2–1) bright emission seems to *avoid* the regions of ionized \[O iii\] gas" (3.1 Morphology)

## Claim tuples

- H: Is there a resolved nuclear molecular disk consistent with the obscuring torus? | E: Band 6 CO(2-1) at 0.16x0.11'' and 3DBAROLO modelling | R: Disk of 26 pc FWHM, M(H2)=1.1e7 Msun, N(H2)~5e23 cm-2, inclined ~60 deg | F: Nuclear disk is interpreted as the obscuring torus and collimator of the ionization cone | **supported**
- H: Does the AGN outflow affect circumnuclear molecular gas? | E: CO line profiles and residual velocity map compared to MUSE [OIII] | R: Two velocity components with ~30-45 km/s redshift NE of nucleus | F: Molecular gas is pushed outward in the disk by the outflow | **supported**
- H: Are there non-circular motions in the nuclear disk? | E: 3DBAROLO with radial velocity term and p-v diagrams | R: Deviations up to ±100 km/s | F: Radial outflow in the nuclear disk is possible if there is no nuclear bar | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Nuclear bar with elliptical streamlines could explain non-circular motions  
  > "In this scenario the radial motions seen in the inner 1$''$   could be interpreted as gas elliptical stream lines in a nuclear bar." (5.2 Nuclear scales)
- How they decided it was enough: _not stated_
- Limitation (authors): CO-to-H2 conversion factor uncertain (could be 5-10 higher near AGN), X-ray column is a lower limit exceeding the ALMA value  
  > "Another source of uncertainty in this comparison is the assumed CO-to-H$_2$ conversion factor." (4.4 Column Density)
- Caveat (inferred, ours): Only ~50% of single-dish flux recovered; no short-spacing correction
- Caveat (inferred, ours): Kinematic models fixed to few parameters with no uncertainties
- Caveat (inferred, ours): Nuclear disk is only ~1-2 beams, so size and inclination are weakly constrained
- Caveat (inferred, ours): Torus identification relies on a Galactic X factor

## Reproducibility

- Data public (paper): ALMA project 2016.1.00254.S acknowledged; MUSE data from ESO archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00254.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: 3DBAROLO configuration
- Missing: Line-free channels
- Missing: Velocity-integration ranges
- Data volume (inferred): ~100-200 GB raw for two Band 6 executions
- Score (inferred): 3/5, Data and tools are named, but clean and 3DBAROLO settings are largely missing.
- Rediscovery candidate: no, Key imaging and fitting settings are not given, though the headline numbers are quantitative.

## Links

- Method: (cite: DiTeodoro2015) (3DBAROLO tilted-ring code)
- Method: (cite: MartiVidal2014) (UVMULTIFIT)
- Method: (cite: Sakamoto1999) (CO to H2 mass relation)
- Companion: (cite: Davies2014) (SINFONI H2 kinematics of NGC 5643)
- Companion: (cite: Cresci2015) (MUSE study of NGC 5643 outflow and positive feedback)
- Related: Swift/BAT 70 month catalog

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 48,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
