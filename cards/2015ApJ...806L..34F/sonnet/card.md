# Local Instability Signatures in ALMA Observations of Dense Gas in NGC 7469

`2015ApJ...806L..34F` | The Astrophysical Journal Letters 2015 | first author: Fathi, Kambiz | arXiv: 1506.01157 | DOI: 10.1088/2041-8205/806/2/L34

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is the dense gas (HCN/HCO+ J=4-3) in the central kpc of NGC 7469 locally unstable at the star-forming ring, and what is the characteristic instability scale?  
  > "We present an unprecedented measurement of the disc stability and local instability scales in the luminous infrared Seyfert 1 host, NGC 7469" (abstract)
- Target **NGC 7469**: coordinates _not stated_; z/distance 68 Mpc (330 pc/arcsec)  
  > "we assume NGC 7469 to be at an inclination of $45^\circ$ and a distance of 68 Mpc (cite: RC3), implying 330 pc/$''$" (Introduction); distance from RC3 (de Vaucouleurs et al. 1991)  
  > "we assume NGC 7469 to be at an inclination of $45^\circ$ and a distance of 68 Mpc (cite: RC3), implying 330 pc/$''$" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00165.S
- bands: Band 7  
  > "ALMA Band-7 receiver was tuned to cover the redshifted lines of HCN $J(4\to 3)$" (2 Observations, Maps, and Profiles)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 28 antennas  
  > "using 28 antennas in C32-2 configuration" (2 Observations, Maps, and Profiles)
- configurations: C32-2  
  > "using 28 antennas in C32-2 configuration" (2 Observations, Maps, and Profiles)
- baselines: _not stated_
- angular resolution: 0.5"x0.4" synthesized beam (165x132 pc)  
  > "with a synthesized beam of $165\times 132$ pc" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: November 3rd and 4th, 2013  
  > "We observed NGC 7469 with ALMA on November 3rd and 4th, 2013" (2 Observations, Maps, and Profiles)
- pi or archival as stated: PI: Takuma Izumi (project 2012.1.00165.S)  
  > "(Proposal ID 2012.1.00165.S, PI: Takuma Izumi)" (2 Observations, Maps, and Profiles)
- Line: HCN J=4-3 (354.505 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- External data: HCN J(4-3)/HCN J(1-0) ratio = 0.6  
  > "Combined with the ratio HCN $J(4\to 3)$ / HCN $J(1\to 0)$= $0.6$ (cite: Viti2014)" (3.2 Surface Density of the Dense Gas Phase) [from (cite: Viti2014)]
- External data: Conversion factor formula X_HCN = 2.1 sqrt(n)/T_b  
  > "we calculate the conversion factor $X_{\rm HCN}$ $=2.1 \times \sqrt{n_\mathrm{(H_2)}}/T_b \sim 27\ M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: Kripsetal2008)" (3.2 Surface Density of the Dense Gas Phase) [from (cite: Kripsetal2008)]

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
- smoothing: Data binned to 20.2 km/s velocity resolution (from 0.43 km/s)  
  > "we binned the data at an effective resolution of 20.2 km s$^{-1}$ (cite: Izumi1)" (2 Observations, Maps, and Profiles)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and maps/cube follow Izumi et al. (cube binning, moment-map comparison)  
  > "are all reliable and fully consistent with the maps presented in (cite: Izumi1)" (2 Observations, Maps, and Profiles) [from (cite: Izumi1)]
- Rotation curve harmonic decomposition method  
  > "We then use the method described in (cite: Schoenmakers1997; Fathietal2005; vdVF2010) to derive the best representation of the rotation curve." (2 Observations, Maps, and Profiles) [from (cite: Schoenmakers1997; Fathietal2005; vdVF2010)]
- Stability parameter Q with disc thickness  
  > "we derive the Toomre-like stability parameter $\mathcal{Q}$ for the HCN, taking into account also the disc thickness (cite: RomeoWiegert2011; RomeoFalstad2013)" (3.3 Disc Stability Analysis) [from (cite: RomeoWiegert2011; RomeoFalstad2013)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, weighting, cleaning, continuum subtraction); the cube is from Izumi et al.
- Spectral resolution and cube specifics used for Gaussian fitting
- Amplitude-to-noise cut details and fit initial guesses
- Exact conversion of flux to Sigma including the line luminosity step and T_b
- Rotation curve fitting order n of the harmonic series
- Method of derivative for kappa

## Analysis recipe

1. **Fit line profiles to derive maps**: Single Gaussian fit to each spectrum in the cube, keeping positive-amplitude fits, giving flux, velocity and sigma maps  
  > "we applied single Gaussian fits to each individual spectrum in the data cube, keeping only the positive-amplitude fits." (2 Observations, Maps, and Profiles)
   - fitting: _not stated_
   - validation: Compared with moment maps; side-lobe contribution <15% at R<3"  
  > "We further estimated the contribution of the side-lobes to $< 15\%$ at $R<3\ensuremath{''}$" (2 Observations, Maps, and Profiles)
2. **Radial profiles of flux and sigma**: Median in projected circular rings with robust statistics, errors per Huber & Ronchetti  
  > "At each radius (in the plane of the galaxy) we derive the median value for the flux and $\sigma$" (2 Observations, Maps, and Profiles)
   - parameter: ring step 0.25 arcsec (82.5 pc)  
  > "The smallest reliable step is thus $0\hbox{$.\!\!^{\prime\prime}$}25$, corresponding to an increment value of 82.5 pc" (2 Observations, Maps, and Profiles)
   - assumption: inclination 45 deg, distance 68 Mpc  
  > "we assume NGC 7469 to be at an inclination of $45^\circ$ and a distance of 68 Mpc" (Introduction)
   - fitting: _not stated_
   - validation: Tests with varying ring widths and radii  
  > "Numerous tests with varying ring widths and ring radii confirm that the exceptional quality and broad dynamical range of the ALMA data allows a stable median and error estimation" (2 Observations, Maps, and Profiles)
3. **Derive rotation curve, Omega and kappa**: Harmonic series decomposition of line-of-sight velocity; Omega=k1/R, kappa=sqrt(R dOmega^2/dR+4Omega^2)  
  > "we calculate the angular frequency $\Omega = k_1/R$ and the epicyclic frequency $\kappa = \sqrt{R d\Omega^2/dR + 4\Omega^2}$ curves" (2 Observations, Maps, and Profiles)
   - assumption: circular rotation dominant, single inclined disc  
  > "assuming that the circular rotation is the dominant kinematic feature and that our measurements refer to positions on a single inclined disk" (2 Observations, Maps, and Profiles)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dynamical mass**: M = R(k1^2+3 sigma^2)/G  
  > "applying the equation $M = R(k^{2}_{1}+3\sigma^2)/G$ (cite: Benderetal1992)" (3.1 Dynamical Mass)
   - assumption: HCN sigma rises due to symmetric macroscopic motions  
  > "We assume that the HCN $\sigma$ rises due to symmetric macroscopic motions" (3.1 Dynamical Mass)
   - fitting: _not stated_
   - validation: Compared with Genzel et al. 1995 and Hicks et al. 2009 masses  
  > "The mass curve shown in Fig. [3](#fig:vsigma) is in full agreement with the measurements listed in (cite: Genzeletal1995) and (cite: Hicksetal2009)" (3.1 Dynamical Mass)
5. **Gas surface density from HCN**: Convert HCN flux with X_HCN and HCN(4-3)/(1-0)=0.6  
  > "we convert the HCN flux into molecular gas surface density $\Sigma$ (in $M_\odot$ pc$^{-2}$)" (3.2 Surface Density of the Dense Gas Phase)
   - parameter: n(H2)~1e5 cm^-3, T_k=25 K, X_HCN~27 Msun/(K km/s pc^2)  
  > "we find it reasonable to assume $T_k=25$ K in NGC 7469" (3.2 Surface Density of the Dense Gas Phase)
   - assumption: Beam dilution up to factor 5 as upper error; temperature twice higher as lower Sigma limit  
  > "using a factor 5 as upper value, and a factor two higher kinetic temperature (cite: ScovilleALMA2015) as lower $\Sigma$ limit" (3.2 Surface Density of the Dense Gas Phase)
   - fitting: _not stated_
   - validation: _not stated_
6. **Stability parameter and instability scale**: Q=3 kappa sigma/(2 pi G Sigma); lambda_c=2 pi sigma/kappa  
  > "$\mathcal{Q}=3\kappa\sigma/2\pi G\Sigma$" (3.3 Disc Stability Analysis); "It is defined as $\lambda_c = 2\pi \sigma/\kappa$" (3.3 Disc Stability Analysis)
   - assumption: isotropic velocity dispersion  
  > "we assume that the velocity dispersion is isotropic" (3.3 Disc Stability Analysis)
   - fitting: _not stated_
   - validation: Compared lambda_c with sizes of star-forming complexes from HST images  
  > "our measured $\sim 180$ pc scale (median $\lambda_c = 0.18$ kpc) is fully comparable to the measured sizes for the star forming complexes" (3.3 Disc Stability Analysis)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean systemic velocity | 4860 | not stated | km/s | 3 | we find that the mean systemic velocity is $4860$ km s$^{-1}$ and the kinematic position angle is $132^\circ$ |
| kinematic position angle | 132 | not stated | deg | 3 | the kinematic position angle is $132^\circ$ |
| median velocity error | 5.5 | not stated | km/s | 2 | the median velocity error across the field is 5.5 km s$^{-1}$ |
| X_HCN | ~27 | not stated | Msun (K km/s pc^2)^-1 | 5 | $X_{\rm HCN}$ $=2.1 \times \sqrt{n_\mathrm{(H_2)}}/T_b \sim 27\ M_\odot$ |
| median lambda_c at ring | 0.18 | not stated | kpc | 6 | (median $\lambda_c = 0.18$ kpc) |

## Qualitative findings

- Q falls below unity at the radii of the star-forming ring and is above unity elsewhere  
  > "this parameter decreases below unity at the region of the ring-like structure in NGC 7469" (3.3 Disc Stability Analysis)
- Non-circular motions not significant  
  > "we confirm that non-circular motions are not significant in redistributing the dense interstellar gas in this galaxy" (abstract)

## Claim tuples

- H: Local gravitational instability of dense gas explains the star-forming ring | E: Compute Toomre-like Q from HCN kinematics and surface density | R: Q<1 at the ring, >1 elsewhere | F: Dense gas is locally unstable at the ring | **supported**
- H: The instability scale matches star cluster complex sizes | E: Derive lambda_c=2 pi sigma/kappa | R: median ~180 pc | F: Agrees with sizes of star-forming complexes | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Sigma and Q depend strongly on assumed temperature and density; beam dilution up to factor 5  
  > "Bothe $\Sigma$ and disc stability parameter (as described in section [3.3](#sec:stability)) depend highly on the assumed temperature and number density." (3.2 Surface Density of the Dense Gas Phase)
- Caveat (inferred, ours): Single assumed density and temperature across the whole disc dominate Q uncertainty
- Caveat (inferred, ours): Conversion factor and line ratio taken from other environments
- Caveat (inferred, ours): No CO comparison
- Caveat (inferred, ours): Error budget is rough

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration/imaging parameters
- Missing: Rotation curve fit details
- Missing: Flux-to-Sigma conversion steps
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple formulae, but processing details and conversion steps are sparse and inherited from a submitted paper.
- Rediscovery candidate: no, Recipe incomplete; assumptions strongly set results, cube preparation deferred to Izumi et al.

## Links

- Method: (cite: RomeoFalstad2013) (Q and lambda_c prescription)
- Method: (cite: vdVF2010) (Rotation curve harmonic decomposition)
- Companion: (cite: Izumi1) (Original ALMA data presentation)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 35,
  "rate": 0.461
 },
 "evidence_ok": true
}
```
