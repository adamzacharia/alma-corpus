# Ongoing and Fossil Large-scale Outflows Detected in a High-redshift Radio Galaxy: [C II] Observations of TN J0924-2201 at z = 5.174

`2024ApJ...972..111L` | The Astrophysical Journal 2024 | first author: Lee, Kianhong | arXiv: 2407.00977 | DOI: 10.3847/1538-4357/ad5be5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the kinematics of the [C II] gas in the z=5.17 radio galaxy TN J0924-2201, and are the three CO(1-0) companions outflows from the host or unrelated dwarf galaxies?  
  > "it is important to obtain the kinematic properties of the interstellar medium (ISM) in both the host galaxy and the companions." (1 Introduction)
- Target **TN J0924-2201**: coordinates _not stated_; z/distance z_[CII] = 5.1736 ± 0.0002  
  > "At $z\sim5$, TN J0924$-$2201 is one of the most distant known radio galaxies" (1 Introduction); "we derived the redshift $z_{\rm [C\,{\sc II}]}=5.1736\pm0.0002$, which is the systemic redshift of TN J0924$-$2201" (3.2 [C II] line emission); distance from Gaussian fit of the ALMA [C II] line (this work)  
  > "At $z\sim5$, TN J0924$-$2201 is one of the most distant known radio galaxies" (1 Introduction); "we derived the redshift $z_{\rm [C\,{\sc II}]}=5.1736\pm0.0002$, which is the systemic redshift of TN J0924$-$2201" (3.2 [C II] line emission)

## Data provenance

- ALMA projects: 2021.1.00219.S
- bands: Band 7 (~1 mm)  
  > "the ALMA Band-7 observations (ID: 2021.1.00219.S; Principal Investigator: K. Lee) were conducted on 2022 Jan 02 and 03." (2 ALMA Observations)
- frequencies and spectral setup: 4 spectral windows of 1.875 GHz, 240 channels each; LSB 293.59–297.23 GHz, USB 305.41–309.11 GHz  
  > "The lower sideband covers 293.59–297.23 GHz, and the upper sideband covers 305.41–309.11 GHz, corresponding to wavelength $\sim1\,$mm." (2 ALMA Observations)
- continuum bandwidth: Total bandwidth 7.5 GHz  
  > "The total bandwidth 7.5 GHz consists of four spectral windows of 1.875 GHz." (2 ALMA Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Continuum beam 0.38"x0.28"; cube beam 0.48"x0.36"  
  > "The synthesized beam size is 0$''$.48 $\times$ 0$''$.36 with P.A. = $-$79$^{\circ}$.5." (2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1.8 hours  
  > "The on-source integration time is 1.8 hours." (2 ALMA Observations)
- observing dates: 2022 Jan 02 and 03  
  > "were conducted on 2022 Jan 02 and 03." (2 ALMA Observations)
- pi or archival as stated: PI K. Lee  
  > "Principal Investigator: K. Lee" (2 ALMA Observations)
- Line: [C II] 158 um fine structure (not stated)
- Other facility **VLA**: CO(1-0) detections of three companions and 19 GHz image (Lee23)  
  > "we marked the positions where CO(1–0) line is detected (cite: Lee23) in letters A, B and C." (3.1 1-mm continuum emission)
- Other facility **HST/ACS**: F775W image, optical peak position  
  > "TN J0924$-$2201 is detected in all of the HST/ACS F775W ($i$-band), IRAC 3.6 $\mu$m and VLA 19 GHz images." (3.1 1-mm continuum emission)
- External data: Ly-alpha and C IV redshifts/spectra  
  > "The detection of Ly$\alpha$ line ($z_{\rm Ly\alpha}=5.195$) and C iv 1549 Å emission line ($z_{\rm C\,{\sc IV}}=5.184$)" (1 Introduction) [from (cite: Matsuoka11)]
- External data: CO(1-0) detections, ALMA Band 6 photometry, radio fluxes  
  > "ALMA Band 6 (cite: Falkendal19; Lee23) and ALMA Band 7 (this work)." (3.1 1-mm continuum emission) [from (cite: Lee23)]
- External data: Stellar mass M*=1.3e11 Msun from SED fitting  
  > "consistent with the SED-derived stellar mass $M_{*}=1.3\times10^{11}\,M_{\odot}$ (cite: DeBreuck10)" (3.2 [C II] line emission) [from (cite: DeBreuck10)]
- External data: Lya emitters velocities in overdense region  
  > "the velocities of six Ly$\alpha$ emitters in the overdense region around TN J0924$-$2201 reported by (cite: Venemans04)" (3.2 [C II] line emission) [from (cite: Venemans04)]

## Processing

### Calibration

- pipeline or manual: Standard manner in CASA  
  > "Data reduction was performed with Common Astronomy Software Applications (cite: CASA22) version 6.5.1 in the standard manner." (2 ALMA Observations)
- casa version: CASA 6.5.1  
  > "Data reduction was performed with Common Astronomy Software Applications (cite: CASA22) version 6.5.1 in the standard manner." (2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We applied `tclean` with deconvolver `mtmfs` and Briggs weighting `robust=0.5`." (2 ALMA Observations)
- deconvolver: continuum: mtmfs; cube: hogbom  
  > "we applied `tclean` with deconvolver `hogbom` and Briggs weighting `robust=2.0`." (2 ALMA Observations)
- weighting robust: continuum robust=0.5; cube robust=2.0  
  > "we applied `tclean` with deconvolver `hogbom` and Briggs weighting `robust=2.0`." (2 ALMA Observations)
- uv taper: _not stated_
- cell size: 0.1"  
  > "The pixel scale is set to $0''.1$." (2 ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, fitorder=1  
  > "firstly we used CASA task `uvcontsub` to subtract the continuum." (2 ALMA Observations)
- line free channels: Continuum image from 293.59–306.62 GHz; cube fit uses two LSB spws and about half of one USB spw  
  > "the continuum image was produced with line-emission-free spectral windows and channels (293.59–306.62 GHz)." (2 ALMA Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cubes made at 91.2 and 60.8 km/s by channel binning  
  > "we made data cubes in two velocity resolutions, 91.2 and 60.8 $\rm km\,s^{-1}$" (2 ALMA Observations)
- final beam: Continuum 0.38"x0.28", PA -78.4 deg; cube 0.48"x0.36", PA -79.5 deg  
  > "The synthesized beam size is 0$''$.38 $\times$ 0$''$.28 with Position Angle (P.A.) = $-$78$^{\circ}$.4." (2 ALMA Observations)
- final rms: Continuum 19 uJy/beam; cube 74.5 (91.2 km/s) and 91.2 (60.8 km/s) uJy/beam/channel  
  > "The rms noise level is 19 $\rm \mu Jy\,beam^{-1}$." (2 ALMA Observations)

### Inherited from earlier work

- Modified blackbody form  
  > "Following (cite: Casey12) and (cite: Falkendal19), the modified blackbody (i.e., a “graybody”) is:" (3.1 1-mm continuum emission) [from (cite: Casey12); (cite: Falkendal19)]
- nu_0 = 1.5 THz  
  > "being assumed to be 1.5 THz (cite: Conley11)" (3.1 1-mm continuum emission) [from (cite: Conley11)]
- Virial dynamical mass formula  
  > "Following (cite: Bothwell13), the virial dynamical mass is:" (3.2 [C II] line emission) [from (cite: Bothwell13)]
- Escape velocity with truncated isothermal sphere  
  > "we derived the escape velocity $v_{\rm esc}$ following (cite: Veilleux20)" (4.2 Outflowing molecular clouds) [from (cite: Veilleux20)]
- Outflow kinetic power  
  > "We derived the kinetic power of outflows ($\dot{E_{\rm out}}$) following (cite: Rose18)" (4.3 Kinetic power of radio jets) [from (cite: Rose18)]
- Jet kinetic luminosity relation  
  > "We also derived the kinetic power (kinetic luminosity $L_{\rm kin}$) of radio jets following (cite: Smolcic17)" (4.3 Kinetic power of radio jets) [from (cite: Smolcic17)]

### Not stated but needed to reproduce (our reading)

- Continuum-fit channel selection for uvcontsub exactly
- Clean mask, threshold and iteration settings
- Image size and spectral-line fitting method details
- Aperture centre for the ~0.8" spectrum and how the deconvolved sizes were measured
- Spectral cube channel start/frequency and rest frequency used
- Gray-body fitting method, priors/fitter and photometry used
- Inputs to PDR model and L_IR scaling
- M_out inputs for outflow power
- Pipeline version

## Analysis recipe

1. **Continuum imaging and flux measurement**: tclean mtmfs on line-free channels; peak and integrated flux  
  > "We applied `tclean` with deconvolver `mtmfs` and Briggs weighting `robust=0.5`." (2 ALMA Observations)
   - software: CASA
   - parameter: robust=0.5, cell 0.1"  
  > "The pixel scale is set to $0''.1$." (2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Modified blackbody SED fit for T_dust, beta, L_IR**: Graybody fit to ALMA Band 6 and 7 data  
  > "With ALMA Band-6 (1.3$\,$mm) and Band-7 (1$\,$mm) data, we applied modified blackbody fitting on TN J0924$-$2201." (3.1 1-mm continuum emission)
   - assumption: Optically thin above nu_0 = 1.5 THz; synchrotron negligible at 1 mm  
  > "Given the extrapolation of the power law, the contribution of synchrotron emission is negligible at observed 1$\,$mm (cite: Lee23)." (3.1 1-mm continuum emission)
   - fitting: _not stated_
   - validation: Compared T_dust with local (U)LIRGs  
  > "This $T_{\rm dust}$ is consistent with the mean value of local luminous and ultra-luminous infrared galaxies (ULIRGs) (cite: U12)." (3.1 1-mm continuum emission)
3. **Build [C II] cube and fit line**: uvcontsub, tclean hogbom; spectra; single and double 1-D Gaussian fits  
  > "We applied double-component 1-D Gaussian fit on the spectrum and found a redshifted substructure" (3.2 [C II] line emission)
   - software: CASA
   - parameter: ~0.8" aperture and peak pixel 0.1"  
  > "The upper left panel shows the spectrum extracted with aperture $\sim0''.8$, which covers the whole galaxy" (3.2 [C II] line emission)
   - fitting: Gaussian fit  
  > "We applied double-component 1-D Gaussian fit on the spectrum and found a redshifted substructure, which is shown in red dashed line, with a velocity offset of $702\pm17\,\rm km\,s^{-1}$, relative to the main component." (3.2 [C II] line emission)
   - validation: Checked cube without uvcontsub; substructure persists  
  > "It is clear that the redshifted substructure does still appear." (3.2 [C II] line emission)
4. **Moment maps, flux, luminosity, inclination, dynamical mass**: Moment 0/1/2; 2-D Gaussian fit on moment-0; virial mass M=1.56e6 sigma^2 R  
  > "Applying the 2-D Gaussian fitting on the moment-0 map, the integrated flux of [C ii] is $3.34\pm0.31\,\rm Jy\,km\,s^{-1}$" (3.2 [C II] line emission)
   - assumption: Symmetric circular disk for inclination; virialized system  
  > "Assuming a symmetric circular disk, we derived its inclination angle of $52.8\pm7.6$ degree." (3.2 [C II] line emission)
   - fitting: _not stated_
   - validation: M_dyn consistent with stellar mass  
  > "we derived $M_{\rm dyn}^{\rm vir}=(1.9\pm0.2)\times10^{11}\,M_{\odot}$, which is consistent with the SED-derived stellar mass $M_{*}=1.3\times10^{11}\,M_{\odot}$" (3.2 [C II] line emission)
5. **Test companions with PDR model and escape velocity**: Upper limits on L_[CII] (500 km/s width) and L_IR (scaled gray-body); PDRT density/G0; escape velocity of 1e13 Msun halo  
  > "we derived the upper limit of $L_{\rm [C\,{\sc II}]}$ with $3\sigma$ upper limit of [C ii] and assuming its velocity width as $500\,\rm km\,s^{-1}$" (4.2 Outflowing molecular clouds)
   - software: PDRT
   - assumption: Companions at 12–33 kpc projected distance with ~1500 km/s velocity  
  > "Assuming the CO(1–0) emitting outflows move through the distance of 12–33 kpc with the velocity of $\sim1500\,\rm km\,s^{-1}$" (4.2 Outflowing molecular clouds)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.1: Data reduction, uvcontsub, tclean  
  > "Data reduction was performed with Common Astronomy Software Applications (cite: CASA22) version 6.5.1 in the standard manner." (2 ALMA Observations)
- **PDRT** : PDR model of density and radiation field  
  > "by using PDRT (cite: Kaufman06; Pound08; Pound11; Pound23)" (4.2 Outflowing molecular clouds)
- **Astropy** : Listed in Software section  
  > "Astropy (cite: astropy13; astropy18; astropy22), CASA (cite: CASA22), PDRT (cite: Kaufman06; Pound08; Pound11; Pound23), SciPy (cite: SciPy20)" (Software)
- **SciPy** : Listed in Software section  
  > "Astropy (cite: astropy13; astropy18; astropy22), CASA (cite: CASA22), PDRT (cite: Kaufman06; Pound08; Pound11; Pound23), SciPy (cite: SciPy20)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum integrated flux of TN J0924-2201 | 829 | 57 | uJy | 1 | The peak flux of TN J0924$-$2201 is $392\pm19\,\mu$Jy and the integrated flux is $829\pm57\,\mu$Jy. |
| T_dust | 29.3 | 0.4 | K | 2 | We obtained $T_{\rm dust}=29.3\pm0.4\,\rm K$ and $\beta=1.51\pm0.46$. |
| beta | 1.51 | 0.46 | dimensionless | 2 | We obtained $T_{\rm dust}=29.3\pm0.4\,\rm K$ and $\beta=1.51\pm0.46$. |
| L_IR (8–1000 um) | 1.72e12 | +0.13/-0.14 e12 | Lsun | 2 | $L_{\rm IR}=1.72^{+0.13}_{-0.14}\times10^{12}\,L_{\odot}$ |
| [C II] systemic redshift | 5.1736 | 0.0002 | dimensionless | 3 | $z_{\rm [C\,{\sc II}]}=5.1736\pm0.0002$ |
| Ly-alpha velocity offset from [C II] | 1035 | 10 | km/s | 3 | redshifted by a velocity of $1035\pm10$ km s$^{-1}$ |
| Redshifted [C II] component velocity | 702 | 17 | km/s | 3 | Mean (km$\,$s$^{-1}$) / $\pm6$$\ensuremath{^{a}}$ / $702\pm17$ |
| C IV velocity offset | 500 | 10 | km/s | 3 | C iv line with a velocity of $500\pm10$ km s$^{-1}$ |
| Main component velocity dispersion | 270 | 6 | km/s | 3 | Velocity dispersion (km$\,$s$^{-1}$) / $270\pm6$ / $47\pm16$ |
| [C II] integrated flux | 3.34 | 0.31 | Jy km/s | 4 | the integrated flux of [C ii] is $3.34\pm0.31\,\rm Jy\,km\,s^{-1}$ |
| L_[CII] | 2.52e9 | 0.23e9 | Lsun | 4 | $L_{\rm [C\,{\sc II}]}=(2.52\pm0.23)\times10^{9}\,L_{\odot}$ |
| Inclination | 52.8 | 7.6 | degree | 4 | we derived its inclination angle of $52.8\pm7.6$ degree. |
| Virial dynamical mass | 1.9e11 | 0.2e11 | Msun | 4 | we derived $M_{\rm dyn}^{\rm vir}=(1.9\pm0.2)\times10^{11}\,M_{\odot}$ |
| Continuum 3-sigma upper limit at companions | 57 | not stated | uJy/beam | 1 | The $3\sigma$ upper limit of non-detection is $57\,\mu$Jy with beam $\sim0''.4$. |
| Outflow kinetic power (ULIRG alpha_CO) | 3.3e45 | not stated | erg/s | 5 | we estimated $\dot{E_{\rm out}}\sim3.3\times10^{45}\,\rm erg\,s^{-1}$ |

## Qualitative findings

- No [C II] or 1-mm continuum at the three CO(1-0) companions.  
  > "However, there are no detection at three CO(1–0) detected regions." (3.2 [C II] line emission)

## Claim tuples

- H: Does the large Lya velocity offset reflect an outflowing shell? | E: Double Gaussian fit to [C II] and comparison with C IV and Lya velocities | R: Redshifted [C II] at 702 km/s and C IV at 500 km/s, about half of the 1035 km/s Lya offset; redshifted [C II] concentrated centrally | F: Consistent with an AGN-driven expanding shell outflow | **supported**
- H: Are the CO(1-0) companions dwarf galaxies or outflows? | E: [C II]/L_IR vs CO/L_IR PDR diagram with upper limits | R: Companions lie in the [C II]-dark region, unlike CO-dark dwarfs | F: Different nature from dwarf galaxies; likely outflowing molecular clouds | **partially**
- H: Can the outflows escape the halo? | E: Compare ~1500 km/s with escape velocity of 1e13 Msun halo | R: Two of three exceed escape velocity at projected distances | F: May exceed escape velocity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: [C II] chosen as best kinematic tracer of ISM  
  > "[C ii] 158 $\mu$m fine structure line has been known as the best kinematic tracer of the global ISM properties in high-redshift galaxies" (1 Introduction)
- Alternative: Companions at a different redshift as dwarf galaxies; dusty H I absorber for the Lya offset  
  > "an alternative interpretation is that the velocity offset is caused by a dusty H i absorber." (4.4 Neutral hydrogen absorber)
- How they decided it was enough: _not stated_
- Limitation (authors): Only projected distances and radial velocities known; spatial offset of redshifted [C II] smaller than beam  
  > "Although we only have the information of the projected distances and the radial velocities instead of the actual distances and velocities" (4.2 Outflowing molecular clouds)
- Caveat (inferred, ours): Redshifted [C II] component is low significance (amplitude 0.15±0.05 mJy) and spatially offset by less than the beam
- Caveat (inferred, ours): Outflow interpretation for CO companions relies on assumed association and projected distances
- Caveat (inferred, ours): Dusty HI absorber alternative not excluded

## Reproducibility

- Data public (paper): Project ID given; public status not stated  
  > "the ALMA Band-7 observations (ID: 2021.1.00219.S; Principal Investigator: K. Lee) were conducted on 2022 Jan 02 and 03." (2 ALMA Observations)
- Products in archive: _not stated_
- Missing: CLEAN masks and thresholds
- Missing: Exact gray-body fitting procedure and input photometry
- Missing: PDR model inputs and companion line ratio details
- Data volume (inferred): ~10-50 GB (single Band 7 execution set)
- Score (inferred): 6/5, Imaging parameters and many numbers given, but fitting, masks, and several model inputs are not specified.
- Rediscovery candidate: yes, Single ALMA project, clear imaging settings and numeric results (flux, redshift, Gaussian fit).

## Links

- Method: (cite: Casey12) (Modified blackbody form)
- Method: (cite: Bothwell13) (Virial mass formula)
- Companion: (cite: Lee23) (VLA CO(1-0) detection of companions and ALMA Band 6 data)
- Related: ALPINE
- Related: REBELS

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 56,
  "rate": 0.683
 },
 "evidence_ok": true
}
```
