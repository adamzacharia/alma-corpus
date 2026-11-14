# A triple protostar system formed via fragmentation of a gravitationally unstable disk

`2016Natur.538..483T` | Nature 2016 | first author: Tobin, John J. | arXiv: 1610.08524 | DOI: 10.1038/nature20094

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Does the disk around the triple protostar system L1448 IRS3B show evidence of gravitational instability and fragmentation forming the tertiary companion?  
  > "The triple protostar system L1448 IRS3B is an ideal candidate to search for evidence of disk fragmentation." (main text)
- Target **L1448 IRS3B**: coordinates _not stated_; z/distance ~230 pc  
  > "L1448 IRS3B is located in the Perseus molecular cloud at a distance of $\sim$230 pc(cite: hirota2011)" (main text); distance from Hirota et al. 2011 (Perseus distance)  
  > "L1448 IRS3B is located in the Perseus molecular cloud at a distance of $\sim$230 pc(cite: hirota2011)" (main text)

## Data provenance

- ALMA projects: 2013.1.00031.S
- bands: Band 6 (1.3 mm)  
  > "provide images at 1.3 mm of the dust and gas emission surrounding the three protostars" (main text)
- frequencies and spectral setup: 2 GHz continuum band centered at 232.5 GHz; 60 MHz bands on 12CO, 13CO, C18O (2-1), SO 6_5-5_4, H2CO 3_03-2_02  
  > "The correlator was configured to observe a 2 GHz continuum band centered at 232.5 GHz, and with 60 MHz bands centered on the following molecular transitions" (1. Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 32 - 2000 m, 33 antennas  
  > "with 33 antennas sampling baselines between 32 - 2000 meters" (1. Observations)
- angular resolution: continuum 0.27x0.16 arcsec; lines 0.36x0.25 arcsec  
  > "the beam size of the molecular line data is 0$.\!\!^{\prime\prime}$36$\times$0$.\!\!^{\prime\prime}$25 (83 AU $\times$ 58 AU)" (1. Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.14 mJy/beam continuum; 15 mJy/beam per 0.25 km/s channel  
  > "The resultant noise in the 1.3 mm continuum was 0.14 mJy/beam and 15 mJy/beam in 0.25 km s$^{-1}$ channels" (1. Observations)
- time on source: ~2.9 minutes  
  > "the total time spent on L1448 IRS3B was $\sim$2.9 minutes" (1. Observations)
- observing dates: 27 September 2015, Cycle 2  
  > "during Cycle 2 on 27 September 2015 with 33 antennas" (1. Observations)
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: 12CO J=2-1 (not stated)
- Line: H2CO 3_03-2_02 (not stated)
- Line: SO 6_5-5_4 (not detected) (not stated)
- Other facility **VLA**: 8 mm image and earlier detection of the three protostars  
  > "A VLA 8 mm image is also shown in Figure 1, having comparable resolution to the ALMA data." (main text)
- External data: Bolometric luminosity 3.2 Lsun  
  > "bolometric luminosity of 3.2 L$_{\odot}$(cite: sadavoy2014)" (6. Stability Analysis) [from (cite: sadavoy2014)]
- External data: Distance to Perseus 230 pc  
  > "$D$ = 230 pc(cite: hirota2011) is the distance to the Perseus molecular cloud" (3. Disk Mass) [from (cite: hirota2011)]
- External data: Dust opacity 0.899 cm2/g at 1.3 mm  
  > "$\kappa_{1.3mm}$ = 0.899 cm$^2$ g$^{-1}$\[(cite: ossenkopf1994)\]" (3. Disk Mass) [from (cite: ossenkopf1994)]
- Simulation/model as data: Baraffe et al. models (1 Myr) for stellar radii and intrinsic luminosity  
  > "We use the youngest age available from the Baraffe et al. models(cite: baraffe2015) (1 Myr) to calculate the stellar radii and intrinsic luminosity." (6. Stability Analysis)

## Processing

### Calibration

- pipeline or manual: manual reduction by NA ARC staff  
  > "The raw data were manually reduced by the North American ALMA Regional Center staff using CASA(cite: mcmullin2007) version 4.5.0." (1. Observations)
- casa version: CASA 4.5.0  
  > "The data were reduced and processed using the Common Astronomy Software Applications (CASA) version 4.5.0." (Code Availability)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+166  
  > "the amplitude and absolute flux calibrator was the monitored quasar J0238+166" (1. Observations)
- flux scale uncertainty: better than 10%  
  > "The flux calibration accuracy is expected to be better than 10%." (1. Observations)
- self calibration: continuum phase and amplitude self-cal, applied to line bands  
  > "The phase and amplitude solutions from the continuum self-calibration were also applied to the spectral line bands." (1. Observations)

### Imaging

- task: CASA clean  
  > "The data were imaged using the *clean* task within CASA 4.5.0" (1. Observations)
- deconvolver: _not stated_
- weighting robust: continuum Briggs robust 0.5; lines natural weighting  
  > "generated using Briggs weighting with a robust parameter of 0.5" (1. Observations)
- uv taper: lines tapered at 500 klambda; uv>50 klambda  
  > "imaged with natural weighting, tapering at 500 k$\lambda$, and with data having $uv$-distances $>$ 50 k$\lambda$" (1. Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.27x0.16 arcsec continuum; 0.36x0.25 arcsec lines  
  > "The beam size of the continuum image is 0$.\!\!^{\prime\prime}$27$\times$0$.\!\!^{\prime\prime}$16 (62 AU $\times$37 AU)" (1. Observations)
- final rms: 0.14 mJy/beam continuum  
  > "The resultant noise in the 1.3 mm continuum was 0.14 mJy/beam" (1. Observations)

### Inherited from earlier work

- Deprojection of uv data using standard methods  
  > "The uv-data are deprojected using standard methods(cite: persson2016) that adjust the $u$ and $v$ coordinates based on the geometric projection." (4. Disk Surface Density) [from (cite: persson2016)]
- Two-component disk temperature model  
  > "a two component temperature model is used(cite: kratter2008; kratter2010)" (6. Stability Analysis) [from (cite: kratter2008; kratter2010)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, reference antenna and number of iterations
- Cell size, image size, clean masks, threshold and iteration count
- Whether Gaussian-fit region/initial guesses for IRS3B-c are reproducible
- Line-free channels / continuum subtraction for line cubes
- Details of the Keplerian curve drawn on the PV diagram (width of cut, position angle choice)
- Exact annulus-by-annulus surface density and temperature profile data
- Source coordinates

## Analysis recipe

1. **Image continuum and lines**: CASA clean after manual calibration and self-calibration; continuum Briggs robust 0.5, lines natural with 500 klambda taper; uv>50 klambda  
  > "we only include data at $uv$-distances $>$ 50 k$\lambda$ to mitigate striping in the images" (1. Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract tertiary IRS3B-c in uv plane**: Fit point source plus extended Gaussian with constant offset in 0.7x0.6 arcsec ellipse using imfit; model Fourier transformed with setjy and subtracted with uvsub  
  > "we fit a two-component Gaussian with a constant zero-level offset." (2. Subtracting the Tertiary, IRS3B-c)
   - software: CASA
   - fitting: imfit two-component Gaussian  
  > "We used the *imfit* task in CASA 4.5.0 to fit the Gaussian components." (2. Subtracting the Tertiary, IRS3B-c)
   - validation: _not stated_
3. **Derive disk inclination and position angle**: Single Gaussian fit to image tapered to 0.43x0.36 arcsec with center fixed on IRS3B-a; inclination = arccos(minor/major)  
  > "We use the *imfit* task in CASA to fit a single Gaussian, with the center position fixed at the location of IRS3B-a" (2. Subtracting the Tertiary, IRS3B-c)
   - software: CASA
   - assumption: Disk is intrinsically symmetric  
  > "Assuming symmetry, this corresponds to an inclination angle of 45.4" (2. Subtracting the Tertiary, IRS3B-c)
   - fitting: imfit Gaussian  
  > "We use the *imfit* task in CASA to fit a single Gaussian, with the center position fixed at the location of IRS3B-a, which appears to be the most centrally-located source in the system." (Methods 2. Subtracting the Tertiary, IRS3B-c)
   - validation: _not stated_
4. **Estimate disk and IRS3B-c masses from dust**: Optically thin isothermal dust mass equation, M=D^2 F/(kappa B(T))  
  > "Assuming that the dust around L1448 IRS3B is optically thin, isothermal, and that the gas and dust are well-mixed" (3. Disk Mass)
   - parameter: T_dust = 30 K disk, 40 K for IRS3B-c; kappa 0.899 or 2.3 cm2/g  
  > "we adopt $T_{dust}$ = 40 K for IRS3B-c" (3. Disk Mass)
   - assumption: Gas-to-dust 100:1, constant  
  > "We then adopt a standard dust to gas mass ratio of 1:100" (3. Disk Mass)
   - fitting: _not stated_
   - validation: Compared two limiting opacity values  
  > "While there are a multitude of possible models to consider(cite: testi2014); we adopt two limiting cases for simplicity." (Methods 3. Disk Mass)
5. **Surface density profile**: Deproject visibilities, image, measure flux in annuli of half-beam width centered on IRS3B-a, convert to surface density  
  > "each annulus has a width of half the beam-size" (4. Disk Surface Density)
   - software: CASA
   - assumption: Radial temperature profile from Section 6 model  
  > "assuming a radial temperature profile that is described in Section 6." (Methods 4. Disk Surface Density)
   - fitting: _not stated_
   - validation: _not stated_
6. **Dynamical mass of central pair**: Draw Keplerian curve on C18O PV diagram along major axis at 45.4 deg inclination; compare with thin-disk model  
  > "we can estimate the protostar mass by drawing a Keplerian curve on the PV diagram, accounting for the 45.4$^\circ$ system inclination." (5. Protostar Masses)
   - software: Maret 2015 thin disk model code
   - fitting: by eye, no formal fit  
  > "Nevertheless, we can estimate the protostar mass by drawing a Keplerian curve on the PV diagram, accounting for the 45.4$^\circ$ system inclination." (Methods 5. Protostar Masses)
   - validation: Comparison to thin rotating disk model  
  > "The thin disk model occupies a very similar domain in PV space as the data." (5. Protostar Masses)
7. **Toomre Q and cooling time analysis**: 1D analytic disk models: Q, t_cool, radiative-equilibrium temperature with irradiation and accretion heating, for a range of accretion rates  
  > "we generate a set of one-dimensional analytic disk models." (6. Stability Analysis)
   - parameter: Each protostar 0.5 Msun; f≈0.1; opacity 0.24 cm2/g or ~T^2; 1 Myr Baraffe radii  
  > "treat IRS3B-a and IRS3B-b as equal mass 0.5 M$_{\odot}$ protostars (see Section 5). We use the youngest age available from the Baraffe et al. models(cite: baraffe2015) (1 Myr)" (Methods 6. Stability Analysis)
   - assumption: Accretion rate benchmark 1e-7 Msun/yr from L=3.2 Lsun  
  > "This implies an accretion rate of $\sim$10$^{-7}$ M$_{\odot}$ yr$^{-1}$" (6. Stability Analysis)
   - fitting: _not stated_
   - validation: Cooling time well below 10 Omega^-1 threshold  
  > "We find that the cooling time is well below the critical threshold of $\sim10\Omega^{-1}$ throughout the entire disk." (6. Stability Analysis)

## Software

- **CASA** 4.5.0: Reduction, self-calibration, clean imaging, imfit, setjy, uvsub  
  > "The data were reduced and processed using the Common Astronomy Software Applications (CASA) version 4.5.0." (Code Availability)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)
- **Astropy** : Python astronomy package  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination | 45.4 | +10.4/-12.8 | deg | 3 | inclination angle of 45.4$^\circ$$^{+10.4}_{-12.8}$ |
| Disk position angle | 29.5 | not stated | deg east of north | 3 | the position angle is 29.5$^\circ$ east of north |
| Disk mass (IRS3B-c removed), kappa=0.899 | 0.30 | not stated | Msun | 4 | we find $M_{\rm disk}=0.30~M_{\odot}$ using the integrated 1.3 mm flux density of 0.52 $\pm$ 0.002 Jy |
| IRS3B-c mass | 0.085 | lower limit | Msun | 4 | the mass of IRS3B-c in the outer disk is estimated to be 0.085 $M_{\odot}$ from the 1.3 mm flux density of 0.19 $\pm$ 0.003 Jy |
| Combined mass IRS3B-a+b | ~1.0 | not stated | Msun | 6 | We find that the combined mass for both IRS3B-a and IRS3B-b is likely $\sim$1.0 M$_{\odot}$. |
| Deprojected separations of b and c from a | 78 and 254 | not stated | AU | 3 | The deprojected separations of IRS3B-b and IRS3B-c from IRS3B-a are 78 AU and 254 AU, respectively. |
| Radii of marginal instability (Q≈1) | 150-320 | not stated | AU | 7 | the disk around IRS3B is marginally unstable ($Q\approx1$) at radii between 150 AU and 320 AU |
| Initial fragment mass | 0.005-0.015 | not stated | Msun | 7 | the fragment mass ranges from $0.005-0.015\mbox{M$_{\odot}$}$ between $150-320$ AU |

## Qualitative findings

- Disk with spiral structure surrounds all three protostars, extending to ~400 AU; C18O rotation centered on IRS3B-a/b.  
  > "The ALMA images also reveal a disk with substructure surrounding the entire system, extending to a radius of $\sim$400 AU." (main text)

## Claim tuples

- H: The IRS3B disk is gravitationally unstable and formed IRS3B-c by fragmentation | E: Derived disk mass, surface density, central mass and Toomre Q/cooling time models | R: Q≈1 at 150-320 AU, cooling time short, fragment mass ~0.01 Msun | F: Disk likely recently fragmented to form IRS3B-c | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: IRS3B-b may have formed via earlier fragmentation, possibly in the outer disk and migrated inward.  
  > "It could also have formed in the outer disk prior to IRS3B-c and migrated inward" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust mass estimates are lower limits because of optical depth; SNR insufficient for quantitative kinematic mass fitting.  
  > "The signal-to-noise ratio of the data is not high enough to employ the techniques that have been used to quantitatively measure protostellar masses" (5. Protostar Masses)
- Caveat (inferred, ours): Mass depends strongly on assumed opacity and temperature
- Caveat (inferred, ours): Keplerian mass drawn by eye without formal uncertainty
- Caveat (inferred, ours): Only 2.9 min on source; spatial filtering removes envelope and low-velocity gas
- Caveat (inferred, ours): Inclination uncertain because disk is asymmetric

## Reproducibility

- Data public (paper): Data to be available in ALMA archive and from corresponding author  
  > "These data will be available in the ALMA archive and from the corresponding author upon request." (Data Availability Statement)
- Products in archive: _not stated_
- Code: No new code; thin-disk model code of Maret 2015 is public  
  > "involve no significant code development." (Code Availability)
- Missing: Self-calibration parameters
- Missing: Cleaning parameters (cell, image size, masks)
- Missing: Details of PV diagram extraction and Keplerian curve
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 3/5, Public single-EB data and clear mass recipe, but clean/selfcal and Keplerian-mass details missing.
- Rediscovery candidate: yes, Public data, numeric results (inclination, masses, flux densities) reproducible with described steps.

## Links

- Method: (cite: kratter2016) (Analytic disk fragmentation model)
- Method: (cite: persson2016) (uv-plane deprojection)
- Companion: (cite: tobin2016) (VLA detection of the three protostars)
- Related: VANDAM VLA survey of Perseus

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
  "facts": 84,
  "stated": 54,
  "rate": 0.643
 },
 "evidence_ok": true
}
```
