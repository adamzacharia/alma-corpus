# Unveiling a Hidden Bar-like Structure in NGC 1087: Kinematic and Photometric Evidence Using MUSE/VLT, ALMA, and JWST

`2024ApJ...962...65L` | The Astrophysical Journal 2024 | first author: López-Cobá, Carlos | arXiv: 2312.04098 | DOI: 10.3847/1538-4357/ad152a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies
- Question: Is there a hidden bar-like non-axisymmetric structure in NGC 1087, seen in JWST NIR images and in stellar, ionized and CO kinematics, and can its gas inflow feed the observed star formation?  
  > "We report a faint non-axisymmetric structure in NGC 1087 through the use of JWST Near Infrared Camera (NIRCam)" (abstract); "Furthermore the molecular mass inflow rate associated can explain the observed star formation rate in the bar." (abstract)
- Target **NGC 1087**: coordinates _not stated_; z/distance 14 Mpc  
  > "NGC 1087 is an intermediate Sc galaxy located at 14 Mpc (cite: Kourkchi2017)" (Data and Data analysis); distance from (cite: Kourkchi2017)  
  > "NGC 1087 is an intermediate Sc galaxy located at 14 Mpc (cite: Kourkchi2017)" (Data and Data analysis)

## Data provenance

- ALMA projects: 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.60 arcsec FWHM (CO, following Leroy et al. 2021a)  
  > "Finally the spatial resolution of the ALMA data is $1.60\ensuremath{''}$/FWHM following (cite: Leroy2021a)." (Data and Data analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: public PHANGS-ALMA data products (moments 0 and 1)  
  > "This work is based on public data from the Multi-Unit Spectroscopic Explorer (cite: Bacon2010);" (Data and Data analysis); "in particular we used the data products from the PHANGS–ALMA survey (cite: Leroy2021a; Leroy2021b), namely moments 0 and 1." (Data and Data analysis)
- Line: CO J=2-1 (not stated)
- Other facility **MUSE/VLT (PHANGS-MUSE)**: optical IFU datacubes giving stellar and ionized-gas velocity maps, emission-line fluxes and stellar mass  
  > "The MUSE-VLT data was obtained as part of the recent release of the MUSE-PHANGS datacubes (cite: PHANGS_doi; Emsellem2022)." (Data and Data analysis)
- Other facility **JWST NIRCam (PHANGS-JWST)**: F200W near-IR image revealing the bar-like structure, plus F360M and F335M stellar continuum  
  > "Specifically, we made use of the PHANGS-JWST first result products (cite: PHANGS-JWST_doi)" (Data and Data analysis)
- External data: PHANGS-ALMA CO(2-1) moment 0 and moment 1 maps of NGC 1087  
  > "in particular we used the data products from the PHANGS–ALMA survey (cite: Leroy2021a; Leroy2021b), namely moments 0 and 1." (Data and Data analysis) [from (cite: Leroy2021a; Leroy2021b)]
- External data: Distance to NGC 1087 of 14 Mpc  
  > "NGC 1087 is an intermediate Sc galaxy located at 14 Mpc (cite: Kourkchi2017)" (Data and Data analysis) [from (cite: Kourkchi2017)]
- External data: PHANGS-MUSE datacubes  
  > "The MUSE-VLT data was obtained as part of the recent release of the MUSE-PHANGS datacubes (cite: PHANGS_doi; Emsellem2022)." (Data and Data analysis) [from (cite: PHANGS_doi; Emsellem2022)]
- External data: PHANGS-JWST NIRCam products  
  > "Specifically, we made use of the PHANGS-JWST first result products (cite: PHANGS-JWST_doi)" (Data and Data analysis) [from (cite: PHANGS-JWST_doi)]
- Simulation/model as data: MAPPINGS V shock photoionization grids (Alarie & Morisset 2019) at Gutkin et al. 2016 metallicities, compared with observed line ratios  
  > "we used the photoionization grids from MAPPINGS V (cite: mappingsv) computed by (cite: Alarie2019); we adopt the (cite: Gutkin2016) metallicities." (Ionized and molecular gas)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: PHANGS-ALMA moment 0 and 1 data products used as released  
  > "in particular we used the data products from the PHANGS–ALMA survey (cite: Leroy2021a; Leroy2021b), namely moments 0 and 1." (Data and Data analysis)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO(2-1) to surface-density conversion (alpha_CO and 6.7 factor) and ALMA resolution taken from PHANGS-ALMA  
  > "(cite: Leroy2021a), with $i$ being the disk inclination angle estimated in $44.5^{\circ}$." (Data and Data analysis); "Finally the spatial resolution of the ALMA data is $1.60\ensuremath{''}$/FWHM following (cite: Leroy2021a)." (Data and Data analysis) [from (cite: Leroy2021a)]
- MUSE stellar libraries chosen to match the PHANGS-MUSE analysis  
  > "For concordance with (cite: Emsellem2022), we use the same stellar libraries based on the extended MILES (cite: EMILES)" (Data and Data analysis) [from (cite: Emsellem2022)]
- Non-parametric bar light modelling follows the Reese et al. 2007 algorithm, same as used by XS  
  > "The method adopted here is similar to the non-parametric method from (cite: Reese2007)" (Bar light modeling) [from (cite: Reese2007)]
- Kinematic model fitting by the XS code; full description deferred to the code paper  
  > "We refer to (cite: XookSuut) for a thorough description of this analysis." (Kinematic interpretation of the oval distortion) [from (cite: XookSuut)]
- Molecular mass inflow rate expression  
  > "The molecular mass flow rate ($\dot{M}_{mol}$) associated can be computed following the expression (cite: DiTeodoro2021)" (Kinematic interpretation of the oval distortion) [from (cite: DiTeodoro2021)]

### Not stated but needed to reproduce (our reading)

- ALMA band, array configuration, observing dates and sensitivity of the PHANGS-ALMA CO(2-1) cube (only the 1.60 arcsec resolution and project code are given)
- Which PHANGS-ALMA moment-map version and masking (strict or broad) was used
- CO rest frequency and R21 line ratio details beyond the quoted 6.7 factor
- XS fitting settings: ring spacing and width, error velocity map, initial guesses, convergence and fixed parameters for the inflow model
- Definition of the elliptical bar region used to select pixels for the inflow model
- How the average inflow rate profile was computed (annuli, de-projection details, choice of V_inflow from the model)
- Exact PHANGS-ALMA, MUSE and JWST file names and versions

## Analysis recipe

1. **convert CO moment 0 to molecular surface density**: Scale the PHANGS-ALMA CO(2-1) moment 0 map to Sigma_mol with a fixed conversion and a cos i de-projection  
  > "$\mathrm{ \Sigma_{mol}[M_\odot pc^2] = 6.7\, I_{CO(2-1)}[K\,km/s]} \cos i$ (cite: Leroy2021a), with $i$ being the disk inclination angle estimated in $44.5^{\circ}$." (Data and Data analysis)
   - parameter: inclination i = 44.5 deg  
  > "with $i$ being the disk inclination angle estimated in $44.5^{\circ}$." (Data and Data analysis)
   - assumption: standard Milky Way alpha_CO^{1-0} = 4.35 Msun/pc^2 conversion factor  
  > "assuming a standard Milky Way $\mathrm{ \alpha_\mathrm{CO}^{1-0}=4.35\,M_{\odot} /pc^2 }$ conversion factor" (Data and Data analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit circular-rotation model to get disk orientation**: Circular rotation model fit to the H-alpha and stellar velocity maps with XS, giving disk PA, inclination and systemic velocity  
  > "The disk orientation of NGC 1087 was estimated from modeling the H$\alpha$ and stellar velocity maps with circular rotation only" (Kinematic interpretation of the oval distortion)
   - software: XS (XookSuut)
   - parameter: chi^2 minimised over concentric rings evenly spaced r_k, weighted by the error velocity map  
  > "This code derives an interpolated model over a set of concentric rings evenly spaced $r_k$" (Kinematic interpretation of the oval distortion)
   - assumption: no parametric function assumed for the velocity profiles  
  > "It is important to mention that the modeling does not assume any parametric function on the velocity profiles." (Kinematic interpretation of the oval distortion)
   - fitting: chi^2 minimisation of V_obs against interpolated ring velocities with error map sigma  
  > "minimizing the function $\chi^2 = (V_{obs}-V_k(r) w_k(r))^2/\sigma^2$" (Kinematic interpretation of the oval distortion)
   - validation: Residual maps V_obs - V_circular inspected (about 30 km/s large-scale residuals)  
  > "The circular rotation models leave large-scale residual velocities of the order of $30$ km s$^{-1}$ with a mirror symmetry about the nucleus" (Kinematic interpretation of the oval distortion)
3. **fit bisymmetric and inflow models to stellar, H-alpha and CO velocity maps**: Bisymmetric oval-distortion model and a non-axisymmetric inflow model, both with the flow axis fixed at the NIR bar position angle, fitted with XS  
  > "we performed bisymmetric models over the stellar, H$\alpha$ and CO velocity maps, with a fixed orientation of the oval distortion." (Kinematic interpretation of the oval distortion); "We implemented a non-axisymmetric model, with a flow streaming along $\phi_{bar}^{\prime}$." (Kinematic interpretation of the oval distortion)
   - software: XS (XookSuut)
   - parameter: bar PA fixed at 305 deg on the sky  
  > "oriented at $305^{\circ}$ in the sky" (Kinematic interpretation of the oval distortion)
   - parameter: inflow model applied to pixels inside the elliptical bar region  
  > "we consider the elliptical region that better describes the bar-like light distribution" (Kinematic interpretation of the oval distortion)
   - assumption: trailing spiral arms, so galaxy rotates counterclockwise and V_rad < 0 is inflow; gas flows parallel to the bar major axis  
  > "Assuming the spiral arms are trailing" (Kinematic interpretation of the oval distortion); "assuming that the gas flows parallel to the bar major axis." (Kinematic interpretation of the oval distortion)
   - fitting: same XS chi^2 ring minimisation as step 2  
  > "In this case and in the subsequent, we used the $\mathtt{XS}$ code for generating the kinematic models" (Kinematic interpretation of the oval distortion)
   - validation: Compared model rms with circular model; bisymmetric rms about 15 km/s, inflow model gives the lowest rms  
  > "this is reflected in the 15 km s$^{-1}$ rms in the models" (Kinematic interpretation of the oval distortion); "This kinematic model yields the lowest rms despite being the model with the lowest number of free variables." (Discussion and Conclusions)
4. **derive molecular mass inflow rate**: Mdot_mol(r) = 2 pi r Sigma_mol(r) V_inflow(r), using de-projected molecular surface density and CO inflow velocity, then radial averaging  
  > "with $\mathrm{ \Sigma_{mol} }$ being the de-projected molecular mass surface density, $V_{inflow}$ the CO inflow velocity and $r$ the galactocentric distance." (Kinematic interpretation of the oval distortion)
   - fitting: _not stated_
   - validation: Compared with Mdot of about 1 Msun/yr from spiral-arm-induced flows and with the bar SFR  
  > "For comparison, spiral arms induce radial flows and radial velocities of the order of $1\mathrm{M_{\odot}/yr}$ and $10$ km s$^{-1}$ respectively" (Kinematic interpretation of the oval distortion)

## Software

- **XS (XookSuut)** : non-parametric light modelling of the F200W/F300M images and circular, bisymmetric and inflow kinematic models of the velocity maps  
  > "In this case and in the subsequent, we used the $\mathtt{XS}$ code for generating the kinematic models" (Kinematic interpretation of the oval distortion)
- **pypipe3d** : MUSE spectral fitting for stellar populations, stellar kinematics and ionized-gas emission-line maps  
  > "The MUSE data analysis was made with the pypipe3d tool (cite: Lacerda2022)." (Data and Data analysis)
- **JWST Science Calibration Pipeline** 1.10.1: calibration of the JWST NIRCam products used  
  > "We used fully calibrated data products from JWST from the JWST Science Calibration Pipeline version 1.10.1 (cite: bushouse)." (Data and Data analysis)
- **MAPPINGS V** : shock photoionization grids to test whether shocks explain the line ratios  
  > "we used the photoionization grids from MAPPINGS V (cite: mappingsv) computed by (cite: Alarie2019)" (Ionized and molecular gas)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NGC 1087 disk inclination | 44.5 | not stated | deg | 2 | obtaining $\phi_{disk}^{\prime} = 358.9^{\circ}$, $i=44.5^{\circ}$ and $V_{sys}=1526$ km s$^{-1}$. |
| Disk position angle (sky plane) | 358.9 | not stated | deg | 2 | obtaining $\phi_{disk}^{\prime} = 358.9^{\circ}$, $i=44.5^{\circ}$ and $V_{sys}=1526$ km s$^{-1}$. |
| Systemic velocity | 1526 | not stated | km/s | 2 | obtaining $\phi_{disk}^{\prime} = 358.9^{\circ}$, $i=44.5^{\circ}$ and $V_{sys}=1526$ km s$^{-1}$. |
| NIR bar position angle (sky plane) | 305 | not stated | deg | 0 | oriented at $\phi_{bar}^{\prime} = 305^{\circ}$, and the ellipticity of the elongated structure is $\varepsilon^{\prime} = 0.5$, |
| NIR bar ellipticity | 0.5 | not stated | dimensionless | 0 | oriented at $\phi_{bar}^{\prime} = 305^{\circ}$, and the ellipticity of the elongated structure is $\varepsilon^{\prime} = 0.5$, |
| NIR bar half-major axis length (galaxy plane) | ~14 arcsec, ~1.2 kpc | not stated | arcsec; kpc | 0 | with a half-major axis length of $a_{bar}^{\prime}\sim 14\ensuremath{''}$ or $\sim$ 1.2 kpc in the galaxy plane. |
| Stellar mass of NGC 1087 | 9.9 | not stated | log(Msun) | 0 | we estimate the stellar mass of this object in $\mathrm{ \log M_{\star}/M_{\odot} = 9.9}$. |
| H-alpha SFR within the NIR bar | 0.08 | not stated | Msun/yr | 0 | is $\mathrm{SFR(H\alpha)_{bar}} = 0.08~\mathrm{M_{\odot}/yr}$, while the total $\mathrm{SFR(H\alpha)_{total}} = 0.4~\mathrm{M_{\odot}/yr}$. |
| Total H-alpha SFR | 0.4 | not stated | Msun/yr | 0 | is $\mathrm{SFR(H\alpha)_{bar}} = 0.08~\mathrm{M_{\odot}/yr}$, while the total $\mathrm{SFR(H\alpha)_{total}} = 0.4~\mathrm{M_{\odot}/yr}$. |
| Maximum inflow velocity along the bar (inflow model) | ~50 | not stated | km/s | 3 | with maximum inflow velocities of the order of 50 km s$^{-1}$. |
| Average molecular mass inflow rate | ~ -20 | not stated | Msun/yr | 4 | We find an average $\dot{M}_{mol}\sim -20 \mathrm{M_{\odot}/yr}$. |
| rms of bisymmetric models | 15 | not stated | km/s | 3 | this is reflected in the 15 km s$^{-1}$ rms in the models |

## Qualitative findings

- The NIR bar-like structure is not evident in MUSE optical images and is revealed only in the F200W and F300M bands  
  > "This structure is not evident in the MUSE optical continuum images but only revealed in the near-IR" (abstract)
- The oval distortion is enhanced in CO relative to H-alpha because CO is dynamically cold  
  > "The oval distortion is enhanced in CO due to its dynamically cold nature rather than in H$\alpha$." (abstract)

## Claim tuples

- H: NGC 1087 hosts a bar-like non-axisymmetric structure hidden at optical wavelengths | E: Compared MUSE optical images with JWST NIRCam F200W/F300M and fitted an elliptical light model | R: Elongated structure with PA 305 deg, ellipticity 0.5 and half-major axis about 14 arcsec (1.2 kpc) | F: A faint bar-like structure exists, visible only in the near-IR | **supported**
- H: The stellar, ionized and CO velocity fields show an oval distortion tied to the NIR structure | E: Circular and bisymmetric XS models fitted to stellar, H-alpha and CO velocity maps with the bar orientation fixed | R: Circular models leave about 30 km/s residuals; the bisymmetric model reproduces the twisted iso-velocities in all three maps with 15 km/s rms | F: The kinematics in all phases reflect a bar-like perturbation of the potential | **supported**
- H: The non-circular motions are better described by gas inflow along the bar than by a bisymmetric distortion | E: Fitted an inflow model with flow along the bar axis inside the bar region and compared rms with the bisymmetric model | R: Inflow model gives the lowest rms with maximum inflow of about 50 km/s | F: Inflow is statistically favoured, but oval orbits cannot be ruled out | **partially**
- H: Gas inflow along the bar can feed the star formation in the bar | E: Computed Mdot_mol from CO surface density and model inflow velocity and compared with the H-alpha SFR in the bar | R: Average Mdot_mol about -20 Msun/yr versus SFR(H-alpha) in the bar of 0.08 Msun/yr | F: Inflow rate exceeds the bar SFR, so inflow might feed the star formation | **supported**

## Reasoning

- Why this data: High-resolution public MUSE, JWST and ALMA data combined to detect a small bar missed by coarser surveys  
  > "In this work, we make use of the most sophisticated data to unravel the detection of a bar in NGC 1087." (Introduction)
- Why this method: Bisymmetric model chosen because it reproduces velocity fields in bars; inflow model physically motivated by expected inflows along bar dust lanes  
  > "has been shown to successfully reproduce the velocity field in bars (cite: velfit)." (Kinematic interpretation of the oval distortion); "Our implementation of an inflow model is therefore physically motivated." (Discussion and Conclusions)
- Alternative: An elongated bulge was considered but not favoured because of the large molecular gas reservoirs, since bulges tend to be quiescent  
  > "The main reason this is not considered is due to the large reservoirs of molecular gas observed" (Discussion and Conclusions)
- Alternative: Shock ionization from bar dust lanes cannot explain the observed [O I]/H-alpha ratios with MAPPINGS V models  
  > "the predicted emission-line intensities from shock models can not explain the observed \[ O I \]/H$\alpha$ line ratios" (Ionized and molecular gas)
- How they decided it was enough: _not stated_
- Limitation (authors): Bisymmetric model leaves residuals of about 15 km/s at 70 pc resolution, similar to or larger than ISM turbulence  
  > "there are still residual velocities that the bisymmetric model can not account for" (Kinematic interpretation of the oval distortion)
- Limitation (authors): No 2D kinematic model includes both oval-orbit and inflow dynamics of bars  
  > "To date, there is no a 2D-kinematic model that includes such dynamics of bars." (Discussion and Conclusions)
- Caveat (inferred, ours): Inflow model uses fewer free parameters, so lower rms does not by itself prove inflow over oval orbits
- Caveat (inferred, ours): Mdot of about 20 Msun/yr depends on a fixed alpha_CO and large model inflow velocities, with no uncertainty given
- Caveat (inferred, ours): No uncertainties are given on the bar geometry or kinematic parameters
- Caveat (inferred, ours): The bar-like structure is faint and identified in part by eye, so the elliptical fit is not independently validated

## Reproducibility

- Data public (paper): yes, all three data sets are described as public or archival  
  > "This work is based on public data from the Multi-Unit Spectroscopic Explorer (cite: Bacon2010);" (Data and Data analysis); "we have taken the advantage of multiple archival data to reveal a hidden non-axisymmetric structure" (Discussion and Conclusions)
- Products in archive: _not stated_
- Missing: XS configuration files and ring settings for each model
- Missing: Exact bar region definition for the inflow fit and the radial averaging of Mdot
- Missing: ALMA observing and calibration details (PHANGS-ALMA release products are used as given)
- Missing: Versions of XS and pypipe3d
- Data volume (inferred): small: PHANGS-ALMA moment maps (tens of MB) plus MUSE datacube and JWST images (about 1-2 GB)
- Score (inferred): 3/5, Data are public and the model equations are given, but XS settings, bar region and ring choices are unspecified; ALMA is used only as released moment maps.
- Rediscovery candidate: no, ALMA role is minor (released moment maps) and key fitting settings are missing, so the full recipe is not reproducible from the text alone.

## Links

- Method: Lopez-Coba, Lin & Sanchez 2021 (cite: XookSuut) (XS code used for the light and kinematic models)
- Method: Leroy et al. 2021a (cite: Leroy2021a) (PHANGS-ALMA CO(2-1) products, resolution and Sigma_mol conversion)
- Method: Lacerda et al. 2022 (cite: Lacerda2022) (pypipe3d MUSE analysis)
- Companion: Emsellem et al. 2022 (cite: Emsellem2022) (PHANGS-MUSE data release)
- Companion: Lopez-Coba et al. 2022 (cite: LopezCoba2022) (earlier oval-distortion kinematics with XS)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: PHANGS-JWST

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 47,
  "rate": 0.56
 },
 "evidence_ok": true
}
```
