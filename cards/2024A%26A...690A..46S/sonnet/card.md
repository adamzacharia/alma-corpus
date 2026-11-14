# Early Planet Formation in Embedded Disks (eDisk): XVI. Asymmetric dust disk driving a multicomponent molecular outflow in the young Class 0 protostar GSS30 IRS3

`2024A&A...690A..46S` | Astronomy and Astrophysics 2024 | first author: Santamaría-Miranda, Alejandro | arXiv: 2407.20885 | DOI: 10.1051/0004-6361/202449981

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the dust disk structure, rotation/stellar mass, and outflow components of the Class 0 protostar GSS30 IRS3 at ~8 au resolution?  
  > "In this paper, we present observations of GSS30 IRS3 at a very high angular resolution (0$.\!\!^{\prime\prime}$056) in the continuum (at 1.3 mm)" (1 Introduction)
- Target **GSS30 IRS3**: coordinates RA=16h26m21.715s, Dec=-24d22m51.09s (Gaussian center)  
  > "located at a distance of $\sim$138.4 $\pm$ 2.6 pc (cite: Ortiz-Leon18) based on the recent Gaia measurements." (1 Introduction); "R.A.=16h26m21.715s" (3.1 Dust emission); z/distance ~138 pc  
  > "located at a distance of $\sim$138.4 $\pm$ 2.6 pc (cite: Ortiz-Leon18) based on the recent Gaia measurements." (1 Introduction); "R.A.=16h26m21.715s" (3.1 Dust emission); distance from Gaia-based distance of L1688 cloud (Ortiz-Leon et al. 2018)  
  > "located at a distance of $\sim$138.4 $\pm$ 2.6 pc (cite: Ortiz-Leon18) based on the recent Gaia measurements." (1 Introduction); "R.A.=16h26m21.715s" (3.1 Dust emission)

## Data provenance

- ALMA projects: 2019.1.00261.L, 2019.A.00034.S
- bands: Band 6 (1.3 mm), 12-m array  
  > "GSS30 IRS3 was observed with the ALMA 12-m array in Band 6" (2 Observation and data reduction)
- frequencies and spectral setup: BB1: four 58.59 MHz windows at ~0.17 km/s; BB2/3: 1875 MHz continuum at ~1.3 km/s; BB4: 937.5 MHz at 0.64 km/s with 12CO  
  > "The fourth baseband has a bandwidth of 937.5 MHz (0.64 km s$^{-1}$ spectral resolution) to detect the continuum and the $^{12}$CO (2-1) line." (2 Observation and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-8 (Large Program), C43-5 (DDT)  
  > "executed four times in October 2021 in configuration C43-8, while two executions were completed for the DDT program in June 2022 with configuration C43-5" (2 Observation and data reduction)
- baselines: _not stated_
- angular resolution: 0.056 arcsec continuum (7.8 au)  
  > "The angular resolution of the continuum maps is 0$\hbox{$.\!\!^{\prime\prime}$}$056 (7.8 au at a distance of 138 PC)" (2 Observation and data reduction)
- max recoverable scale: 2.9 arcsec  
  > "with a maximum recoverable angular scale of 2$\hbox{$.\!\!^{\prime\prime}$}$9" (2 Observation and data reduction)
- sensitivity: _not stated_
- time on source: 2.75 h (LP), 0.5 h (DDT)  
  > "The time on source for data from the Large Program was 2.75 h, and for the DDT program the time on source was 0.5 h." (2 Observation and data reduction)
- observing dates: _not stated_
- pi or archival as stated: eDisk Large Program (PI Ohashi) plus DDT program (PI Tobin)  
  > "as part of the eDisk ALMA Large Programme (project code: 2019.1.00261.L: PI N. Ohashi)" (2 Observation and data reduction)
- Line: 12CO 2-1 (230.538 GHz)
- Line: 13CO 2-1 (220.398 GHz)
- Line: C18O 2-1 (219.560 GHz)
- Line: H2CO 3_0,3-2_0,2 (218.220 GHz)
- Line: c-C3H2 5_1,4-4_2,3 (217.940 GHz)
- Other facility **JWST NIRCam**: H2 image of rho Oph used to compare with 12CO outflow  
  > "we plot the $^{12}$CO contours overlaid on a recent JWST image of the $\rho$ Ophiuchus region (P.I. Klaus Pontoppidan)" (3.4.1 12CO)
- External data: Distance 138.4 pc to L1688  
  > "located at a distance of $\sim$138.4 $\pm$ 2.6 pc (cite: Ortiz-Leon18) based on the recent Gaia measurements." (1 Introduction) [from (cite: Ortiz-Leon18)]
- External data: Lbol 1.7 Lsun and Tbol 50 K  
  > "with a bolometric luminosity ($L\mathrm{_{bol}}$) of 1.7 L$_{\odot}$, and the bolometric temperature is 50 K (cite: eDisk)" (1 Introduction) [from (cite: eDisk)]
- External data: Dust opacity 2.3 cm2/g at 225 GHz  
  > "$\kappa_{\nu}$(2.3 cm$^{2}$ g$^{-1}$) is the absorption coefficient adopted from (cite: Beckwith+1990)" (3.3 Dust disk mass) [from (cite: Beckwith+1990)]
- External data: Flaring angle 0.02 rad  
  > "$\phi$ corresponds to the assumed flaring angle of 0.02 radian (cite: Huang2018)" (5.2 The origin of the bumps) [from (cite: Huang2018)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration pipeline, then self-calibration  
  > "Calibration of the ALMA data was performed using the standard ALMA calibration pipeline." (2 Observation and data reduction)
- casa version: CASA 6.2.1 (2019.1.00261.L) and 6.4.1 (2019.A.00034.S)  
  > "version 6.2.1 and 6.4.1 for 2019.1.00261.L and 2019.A.00034.S programs, respectively." (2 Observation and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "The absolute flux calibration uncertainty in Band 6 is estimated to be 10$\%$." (2 Observation and data reduction)
- self calibration: Short baselines: 4 phase-only + 2 phase&amp;amp (amp) cycles; then joint 4 phase-only iterations; applied to continuum and lines  
  > "first with four phase-only cycles and two phase and amplitude cycles of the short-baseline data." (2 Observation and data reduction)

### Imaging

- task: tclean after continuum subtraction  
  > "the task *TCLEAN* was used to produce continuum and spectral line images after continuum subtraction." (2 Observation and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0 continuum; 0.5 lines; 2 for H2CO and c-C3H2  
  > "We adopted a Briggs robust parameter equal to 0 for the continuum image and 0.5 for the spectral line data" (2 Observation and data reduction)
- uv taper: 2000 kλ taper on line data  
  > "The spectral line data were tapered at 2000 k$\lambda$ to bring out larger-scale structures." (2 Observation and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied before deriving physical parameters  
  > "Primary beam correction was applied before inferring physical parameters from the images." (2 Observation and data reduction)
- array combination: Short and long configurations combined  
  > "The final image is a combination of the short and long configurations." (2 Observation and data reduction)
- smoothing: _not stated_
- final beam: 0.068x0.045 arcsec, PA 76.61 deg (continuum)  
  > "at an angular resolution of 0$\hbox{$.\!\!^{\prime\prime}$}$068$\times$0$\hbox{$.\!\!^{\prime\prime}$}$045 (Position angle of 76.61$\mathrm{^{o}}$)" (3.1 Dust emission)
- final rms: 18.5 uJy/beam (continuum)  
  > "| 18.5 | 123.6 $\pm$ 1.2 | 3.87 $\pm$ 0.04 |" (Table 3.1)

### Inherited from earlier work

- Detailed baseline, antenna, PWV, calibrator information  
  > "Detailed information about the baseline length, number of antennas, precipitable water vapor, and calibrators are provided in (cite: eDisk)." (2 Observation and data reduction) [from (cite: eDisk)]
- Detailed reduction procedure  
  > "A more detailed explanation of the reduction procedure can be found in (cite: eDisk)." (2 Observation and data reduction) [from (cite: eDisk)]
- SLAM methodology for eDisk papers  
  > "A more detailed explanation of the SLAM methodology for the eDisk papers can be found in (cite: eDisk)." (4.1 Disk rotation) [from (cite: eDisk)]

### Not stated but needed to reproduce (our reading)

- Pipeline version
- Line-free channels and continuum subtraction details
- Clean masks, thresholds, cell/image size, deconvolver
- Self-calibration solution intervals
- Line-wing and SLAM S/N edge thresholds, MCMC settings and priors
- Which 5-sigma contour definition is used for flux

## Analysis recipe

1. **Measure continuum disk size, flux, inclination**: 2D Gaussian fit (imfit) and 5σ contour measurement; inclination from cos i = b/a  
  > "Assuming a geometrically flat and axisymmetric disk, we can estimate the disk inclination as $\cos i = b / a$" (3.1 Dust emission)
   - software: CASA imfit
   - assumption: Flat axisymmetric disk  
  > "Assuming a geometrically flat and axisymmetric disk" (3.1 Dust emission)
   - fitting: _not stated_
   - validation: Gaussian residuals poor; two-Gaussian fit did not converge; adopted 5σ contour values  
  > "a fitting attempt using two (2-D) Gaussian components did not converge" (3.1 Dust emission)
2. **Dust mass**: Optically thin isothermal M = S D^2/(κ B(Td))  
  > "The dust disk mass surrounding GSS30 IRS3 is estimated under the assumption that the emission at 1.3 mm is optically thin and comes entirely from isothermal dust." (3.3 Dust disk mass)
   - parameter: Td = 20 K and 49 K (T=43(L/Lsun)^0.25); κ=2.3 cm2/g; D=138 pc  
  > "this formula provides a temperature of 49 K." (3.3 Dust disk mass)
   - assumption: Optically thin; possibly lower limit  
  > "the derived dust mass might be a lower limit than the actual mass because the inclined disk could be optically thick." (3.3 Dust disk mass)
   - fitting: _not stated_
   - validation: Compared with Friesen et al. 2018, difference attributed to opacity  
  > "so we associate the differences to the adopted absorption coefficient." (3.3 Dust disk mass)
3. **Check reality of bumps**: Frank visibility-space 1D radial profile fit, fixed i=64.3 deg, PA=109 deg, alpha=1.30, wsmooth=1e-4; Gaussians fit to bumps; compare Tb with midplane temperature  
  > "We fixed the hyperparameters to $\alpha$= 1.30 and w$\mathrm{_{smooth}}$=10$^{-4}$ because they present the least noisy results." (12 Radial brightness profile fitting)
   - software: Frank
   - assumption: Passively heated flared disk, flaring angle 0.02 rad, L=1.7 Lsun  
  > "L$_{*}$ is the bolometric luminosity of the central protostar (1.7 L$_{\odot}$)" (5.2 The origin of the bumps)
   - fitting: Fourier-Bessel nonparametric fit  
  > "*Frank* (cite: Jennings2020) first deproject the visibilities to correct the disk inclination and uses the Fourier-Bessel series to reconstruct the radial brightness profile." (Discussion: The origin of the bumps along the major axis)
   - validation: Bump positions match image-plane profile  
  > "The positions of the identified bumps, closely coincide with those obtained from the radial intensity profile in the image plane." (5.2 The origin of the bumps)
4. **Rotation curve and stellar mass**: PV diagram along PA 109 deg (0.17 arcsec width) and SLAM edge/ridge single and double power-law MCMC fits; mass averaged over ridge and edge  
  > "fitting a power-law (single or double) function, that is defined as a positive value, to the derived representative data as a function of velocity or radius using the Markov-Chain Monte Carlo method." (4.1 Disk rotation)
   - software: SLAM
   - parameter: Systemic velocity 2.84 km/s fixed after first fit  
  > "We ran a first test to derive the systemic velocity as 2.84 km s$^{-1}$ for the C$^{18}$O (2-1) emission" (4.1 Disk rotation)
   - assumption: Keplerian inside break radius  
  > "the boundary radius between a Keplerian disk and a rotation/infalling envelope" (4.1 Disk rotation)
   - fitting: MCMC; ridge double power-law with p_in fixed at 0.5  
  > "we fixed it at 0.5 under the assumption that there is a Keplerian disk" (4.1 Disk rotation)
   - validation: Reduced chi-squared compared  
  > "We also derived the reduced chi-squared ($\chi^{2}$) for each fit in order to compare all the results." (4.1 Disk rotation)
5. **Outflow dynamical parameters**: 12CO Tex from peak Tb, optical depth in wings, column density, mass with CO abundance 1e-4; formulas of Santamaria-Miranda 2020 with inclination correction  
  > "Finally, we calculated the outflow mass using the inferred column density, the emission area, and a CO abundance of 10$^{-4}$." (11 Dynamical parameters)
   - parameter: Tex = 25.7 K  
  > "We derived a T$_{\mathrm{ex}}$ for the $^{12}$CO (2-1) of 25.7 K" (11 Dynamical parameters)
   - assumption: Optically thin wings; outflow perpendicular to disk  
  > "Then we assume that the emission is optically thin in the line wings." (11 Dynamical parameters)
   - fitting: _not stated_
   - validation: Treated as lower limits due to interferometric filtering  
  > "Therefore, we conclude that all derived parameters may be treated as lower limits." (11 Dynamical parameters)

## Software

- **CASA** 6.2.1 and 6.4.1: self-calibration, imaging (tclean), fixvis/fixplanets, imfit  
  > "version 6.2.1 and 6.4.1 for 2019.1.00261.L and 2019.A.00034.S programs, respectively." (2 Observation and data reduction)
- **SLAM** : PV rotation-curve fitting  
  > "The SLAM code[^1] (cite: yusuke_aso_2023) is used to analyze the rotation curve of GSS30 IRS3." (4.1 Disk rotation)
- **Frank** : visibility-space radial brightness profile  
  > "we fit the radial intensity profile in the uv plane using *Frank*" (5.2 The origin of the bumps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gaussian flux density | 123.6 | 1.2 | mJy | 1 | / 18.5 / 123.6 $\pm$ 1.2 / 3.87 $\pm$ 0.04 / |
| Flux density above 5σ | 133.7 | not stated | mJy | 1 | the peak intensity and the flux density obtained by this method are 6.38 mJy beam$^{-1}$ and 133.7 mJy, respectively |
| Disk inclination (5σ contour) | 64.3 | 1.5 | deg | 1 | we obtained 64.3 $\pm$ 1.5$\mathrm{^{o}}$ |
| Dust mass (5σ flux, 20 K) | 75.1 | 2.9 | Earth masses | 2 | provides values of 75.1 $\pm$ 2.9 M$_{\Earth}$ and 25.80 $\pm$ 0.99 M$_{\Earth}$ |
| Dust mass (5σ flux, 49 K) | 25.80 | 0.99 | Earth masses | 2 | provides values of 75.1 $\pm$ 2.9 M$_{\Earth}$ and 25.80 $\pm$ 0.99 M$_{\Earth}$ |
| Bump radii | ~26 and ~50 | not stated | au | 3 | The bumps are located at a radius of $\sim$0$.\!\!^{\prime\prime}$19 ($\sim$26 au) and the other located at $\sim$0$.\!\!^{\prime\prime}$36 ($\sim$50 au) |
| Brightness temperature at bumps | 18.9 K and 9.6 K (vs 27.8 K and 20.2 K midplane) | not stated | K | 3 | the observed brightness temperature at 0$.\!\!^{\prime\prime}$19 and 0$.\!\!^{\prime\prime}$36 are 18.9 K and 9.6 K, respectively |
| Protostellar dynamical mass | 0.35 | 0.09 | Msun | 4 | Therefore, we adopt a mass of GSS30 IRS3 is 0.35$\pm$0.09 M$_{\odot}$. |
| Systemic velocity | 2.84 | not stated | km/s | 4 | The systemic velocity is 2.84 km s$^{-1}$ |
| C18O double power-law break radius (edge) | 107 | +26/-19 | au | 4 | with r$\mathrm{_{b}}$ of 107$^{+26}_{-19}$ au |
| Total outflow mass | 6.1e-5 | not stated | Msun | 5 | The total outflow mass of the molecular outflow is 6.1$\times10^{-5}$ M$_{\odot}$ |

## Qualitative findings

- 12CO outflow has three components: collimated jet, hourglass intermediate, wide-angle low-velocity wind  
  > "The $^{12}$CO emission reveals a molecular outflow consisting of three distinct components" (abstract)

## Claim tuples

- H: Does the dust disk show substructure? | E: Image and Frank visibility fit of 1.3 mm continuum | R: Two bumps at 26 and 50 au plus minor-axis asymmetry | F: Minor-axis asymmetry from optically thick flared disk; bump origin uncertain | **partially**
- H: Is C18O rotation Keplerian, giving stellar mass? | E: SLAM PV fits | R: 0.35±0.09 Msun with Keplerian disk plus infalling envelope | F: Disk is Keplerian inside ~47-107 au, infall outside | **supported**
- H: Do a jet and wide-angle wind coexist? | E: 12CO channel/moment maps | R: Three components with distinct velocities and opening angles | F: Jet and disk wind coexist in a Class 0 source | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: C18O single-power ridge fit discarded because p_in not Keplerian  
  > "however the p$\mathrm{_{in}}$ is not close to the expected value of a Keplerian disk, so we should discard this value." (4.1 Disk rotation)
- How they decided it was enough: _not stated_
- Limitation (authors): Observations not designed for outflows; large-scale emission filtered, parameters are lower limits  
  > "we are likely filtering structures larger than $\sim$2$.\!\!^{\prime\prime}$0" (4.2 Characterization of the molecular outflow)
- Caveat (inferred, ours): Dust mass assumes optically thin emission yet the disk appears optically thick
- Caveat (inferred, ours): Mass is the average of edge and ridge methods with poorly converged fits
- Caveat (inferred, ours): Distance assumed from host cloud

## Reproducibility

- Data public (paper): Project codes given; eDisk data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2019.1.00261.L, 2019.A.00034.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Pipeline version
- Missing: Clean parameters
- Missing: SLAM thresholds and priors
- Missing: Line-free channels
- Data volume (inferred): ~100-300 GB raw for six executions
- Score (inferred): 3/5, Data identified and many key parameters given, but heavy reliance on eDisk overview paper for reduction.
- Rediscovery candidate: yes, Public data, numeric results (flux, inclination, dust mass, SLAM mass) with fairly complete recipe.

## Links

- Method: (cite: eDisk) (Reduction and SLAM methodology)
- Method: (cite: yusuke_aso_2023) (SLAM code)
- Method: (cite: Jennings2020) (Frank)
- Companion: (cite: eDisk) (eDisk overview)
- Related: eDisk ALMA Large Program

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 57,
  "rate": 0.713
 },
 "evidence_ok": true
}
```
