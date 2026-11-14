# Evidence of Fast Pebble Growth Near Condensation Fronts in the HL Tau Protoplanetary Disk

`2015ApJ...806L...7Z` | The Astrophysical Journal Letters 2015 | first author: Zhang, Ke | arXiv: 1505.00882 | DOI: 10.1088/2041-8205/806/1/L7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Are the dark rings (emission dips) in the ALMA HL Tau continuum images due to fast pebble growth near condensation fronts of abundant volatiles?  
  > "Here we propose that the dark concentric rings observed in the (sub)mm interferometry of HL Tau are due to fast pebble growth near condensation fronts." (1 Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc (adopted)  
  > "beam sizes of 11.9$\times$8.6 AU, 4.9$\times$3.1 AU and 4.2$\times$2.7 AU at 2.9, 1.3 and 0.87 mm (for an adopted distance of 140 pc)" (2 Observations); distance from adopted, source not stated  
  > "beam sizes of 11.9$\times$8.6 AU, 4.9$\times$3.1 AU and 4.2$\times$2.7 AU at 2.9, 1.3 and 0.87 mm (for an adopted distance of 140 pc)" (2 Observations)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: Band 3, 6, 7 (2.9, 1.3, 0.87 mm)  
  > "The ALMA Band 3, 6 and 7 (or wavelengths of 2.9, 1.3 and 0.87 mm, respectively) HL Tau observations were carried out in 2014" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest baseline 15.2 km  
  > "With longest baselines of 15.2 km, the HL Tau observations achieved exceptional spatial resolution" (2 Observations)
- angular resolution: 11.9x8.6 AU, 4.9x3.1 AU, 4.2x2.7 AU at 2.9, 1.3, 0.87 mm (140 pc)  
  > "beam sizes of 11.9$\times$8.6 AU, 4.9$\times$3.1 AU and 4.2$\times$2.7 AU at 2.9, 1.3 and 0.87 mm" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014, long-baseline commissioning and science verification  
  > "were carried out in 2014, as part of its long-baseline commissioning and science verification (SV) program" (2 Observations)
- pi or archival as stated: _not stated_
- External data: Best-fit inclination 46.72 deg and PA 138.02 deg  
  > "using the best-fit inclination angle $i$ = 46.72$^\circ$ and PA = 138.02$^\circ$ from APR" (2 Observations) [from (cite: Partnership15)]
- External data: Mid-plane temperature T_mid = 665 (r/AU)^-0.6 K from radiative transfer model of HL Tau  
  > "Their best-fit model results in T$_{\rm mid}$ = 665 $(r/{\rm AU})^{-0.6}$ K for the mid-plane temperature distribution." (4 Condensation fronts) [from (cite: Menshchikov99)]
- External data: Clathrate hydrate condensation temperatures  
  > "along with the condensation temperatures of clathrate hydrates from (cite: Lunine85) and (cite: Iro03)" (4 Condensation fronts) [from (cite: Lunine85); (cite: Iro03)]
- External data: Opacity kappa = 0.01 cm2/g (nu/230 GHz)  
  > "$\kappa_\nu$ = 0.01 cm$^2$ g$^{-1}$$(\nu/230 \rm[GHz])$ throughout the disk (cite: Ossenkopf94)." (3 Characterizing the emission dips) [from (cite: Ossenkopf94)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v4.3  
  > "use CASA v4.3 (cite: McMullin07) to deproject the visibility data" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: Started from calibrated measurements (calibration described in APR)  
  > "We thus start with the calibrated measurements, and use CASA v4.3" (2 Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN with nterms=2 for spectral index map from deprojected bands 6 and 7  
  > "This result is computed using the CLEAN task with nterms=2, based on the multi-frequency deconvolution algorithm developed by (cite: Rau11)." (2 Observations)
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

- Data description and calibration  
  > "More detailed descriptions of the data and calibration can be found in APR" (2 Observations) [from (cite: Partnership15)]
- Inclination and PA  
  > "We then deproject the visibility data using the best-fit inclination angle $i$ = 46.72$^\circ$ and PA = 138.02$^\circ$ from APR." (2 Observations) [from (cite: Partnership15)]
- Desorption and accretion rates for condensation temperatures  
  > "are calculated using the treatment outlined in (cite: Woitke09) and (cite: Walsh10)" (4 Condensation fronts) [from (cite: Woitke09); (cite: Walsh10)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters: weighting/robust, cell and image size, masks, threshold, scales
- Whether images for radial profiles were cleaned and how the beam was matched
- Best-fit isothermal model parameters (T0, q, Sigma_c, r_c, gamma) and fitting method
- Radial bin averaging details and spectral index uncertainty handling
- Gas number density/pressure assumptions in detail
- Calibrator and flux scale details (in APR)

## Analysis recipe

1. **Deproject visibilities and image**: Shift phase center to star, deproject visibilities with inclination/PA from APR, synthesize images in each band  
  > "we first shift the phase center of each band to that of HL Tau (by $\Delta_\alpha = -14\,{\rm mas}, \Delta_\delta\ = 196\,{\rm mas}$)" (2 Observations)
   - software: CASA
   - parameter: i = 46.72 deg, PA = 138.02 deg  
  > "best-fit inclination angle $i$ = 46.72$^\circ$ and PA = 138.02$^\circ$ from APR" (2 Observations)
   - assumption: Peak continuum emission marks the star; distance 140 pc  
  > "Assuming the peak continuum emission represents the location of the central star" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Spectral index map**: CLEAN nterms=2 on deprojected band 6 and 7 data  
  > "This result is computed using the CLEAN task with nterms=2" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Azimuthally averaged radial profiles and dip fits**: Radial profile in 0.5 AU steps; fit smooth isothermal model; divide data by model; Gaussian fits to normalized profile give dip center, FWHM, amplitude  
  > "We measure the surface brightness versus radial distance in steps of 0.5 AU" (3 Characterizing the emission dips); "Gaussian fits to the normalized radial brightness profile are listed in Table [1](#tab:dips)." (3 Characterizing the emission dips)
   - assumption: kappa_nu = 0.01 cm2/g (nu/230 GHz); vertically isothermal, power-law T, Sigma of steady accretion disk  
  > "we use $\kappa_\nu$ = 0.01 cm$^2$ g$^{-1}$$(\nu/230 \rm[GHz])$ throughout the disk" (3 Characterizing the emission dips)
   - fitting: smooth model fit; sampler/priors not stated  
  > "Since our goal is to produce a smooth fit to the surface brightness distribution rather than a realistic physical model, we use" (Charactering the emission dips)
   - validation: Dip locations consistent with APR dark rings  
  > "The locations are consistent with those of the dark rings reported in APR." (3 Characterizing the emission dips)
4. **Compare dips with condensation fronts**: Compute condensation temperatures where desorption equals accretion rate, compare with brightness-temperature lower bound and MFH mid-plane temperature  
  > "we define the condensation temperature of species $i$ as that where the thermal desorption and accretion rates are equal" (4 Condensation fronts)
   - parameter: gas number densities 1e10-1e13 cm^-3  
  > "corresponding to gas number densities of 10$^{10}$- 10$^{13}$cm$^{-3}$, suitable for disk mid-planes" (Table 2)
   - assumption: T_mid = 665 (r/AU)^-0.6 K from MFH  
  > "T$_{\rm mid}$ = 665 $(r/{\rm AU})^{-0.6}$ K for the mid-plane temperature distribution" (4 Condensation fronts)
   - fitting: _not stated_
   - validation: Consistent with Pollack91 over same pressure range  
  > "Our condensation temperatures are consistent with the results of (cite: Pollack91) over the same pressure range." (4 Condensation fronts)
5. **Dust properties with two-population opacity model**: Examine alpha(r) in cuts at 0, 45, 90, 135 deg and azimuthal average; model alpha vs mean size of second population with mass fraction f  
  > "crosscuts at $\theta$ = 0, 45, 90 and 135$^{\circ}$ (starting from west) along with the azimuthally averaged $\alpha (r)$" (5 Dust properties inside the dips)
   - parameter: kappa_dust1 = 1 cm2/g (nu/230 GHz); rho = 1 g/cm3; f = 0.9  
  > "We further adopt $f$=0.9, i.e., 90% of the dust mass in the second dust population." (5 Dust properties inside the dips)
   - assumption: Order-of-magnitude estimate; second population a >> lambda with geometric cross section  
  > "A plausible order of magnitude estimate can be found if we assume" (5 Dust properties inside the dips)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3: Deprojecting visibilities, imaging, CLEAN nterms=2 spectral index map  
  > "use CASA v4.3 (cite: McMullin07) to deproject the visibility data and generate synthesized images for all three bands" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 7 dip 1 center | 12.6 | 0.1 | AU | 3 | / 12.6$\pm$0.1 / 7.2$\pm$0.3  / 0.56$\pm$0.02 / |
| Band 7 dip 1 FWHM | 7.2 | 0.3 | AU | 3 | / 12.6$\pm$0.1 / 7.2$\pm$0.3  / 0.56$\pm$0.02 / |
| Band 7 dip 2 center | 32.2 | 0.4 | AU | 3 | 32.2$\pm$0.4  / 5.3$\pm$1.0  / 0.26$\pm$0.05 |
| Band 6 dip 1 center | 12.7 | 0.2 | AU | 3 | 12.7$\pm$0.2  / 7.4$\pm$0.3  / 0.66$\pm$0.03 |
| 63 AU dip FWHM | 17-18 | not stated | AU | 3 | The 63 AU dip is resolved at all bands, with a FWHM of 17-18 AU. |
| Dip minimum relative to smooth continuum | 37% to 78% | not stated | percent | 3 | The minimum surface intensity of the dips range from 37% to 78% that of the smooth continuum from the best-fit models. |
| Spectral index inside 48 AU, peaks at 13 and 32 AU dips | ~2; ~2.6 at 13 AU, ~2.4 at 32 AU | not stated | dimensionless | 5 | inside of 48 AU $\alpha$$\sim$2, except for increases to values of $\sim$2.6 and $\sim$2.4 at the 13 AU and 32 AU dips, respectively |
| Surface density needed for tau_1.3mm = 1 at 48 AU | 100 | not stated | g cm^-2 | 5 | a surface density of $\Sigma_{\rm gas}$=100  g cm$^{-2}$  at 48 AU is needed to reach $\tau_{\rm 1.3\,mm}$ = 1 |

## Qualitative findings

- Water ice water-line is at <4-5 AU from brightness temperature, unresolved; dips overlap condensation fronts of water (13 AU), NH3/hydrates (32 AU), CO2 and CO/N2 clathrates (63 AU) using the MFH profile  
  > "pure water condenses around the 13 AU dip, while pure NH$_3$ or ammonia (and hydrogen sulfide) hydrates condense around the 32 AU dip." (4 Condensation fronts)

## Claim tuples

- H: The three prominent dips coincide with condensation fronts of abundant volatiles | E: Fit dip centers in deprojected profiles and compare to computed condensation temperatures and the MFH mid-plane profile | R: Dips at ~13, 32, 63 AU overlap the fronts of water, ammonia/hydrates, and CO2/CO and N2 clathrates | F: Dip locations are coincident with expected condensation fronts | **supported**
- H: Spectral index variation in the dips indicates rapid pebble growth | E: Spectral index map from bands 6 and 7 and a two-population dust opacity model | R: alpha ~2 inside 48 AU with increases at the 13 and 32 AU dips; model with decimeter-size second population reproduces this | F: Most dust mass resides in decimeter-size pebbles inside the dips | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Deprojected circular images make a one-parameter radial brightness function  
  > "For our purposes, it is much easier to work on deprojected, circular images." (2 Observations)
- Alternative: Optically thick inner disk with optically thin dips rejected: requires massive disk and brightness temperature conflicts with SED-derived temperature  
  > "This explanation faces two difficulties. First, a massive disk is needed to create optically thick mm-continuum with modest grain growth." (5 Dust properties inside the dips)
- Alternative: Single dust size distribution with beta~0 disfavored  
  > "for a single dust size-distribution, $\alpha>2$ within the 13/32 AU dips demands smaller dust (and reduced mass surface densities) at these radii." (5 Dust properties inside the dips)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust model is only an order-of-magnitude estimate; other condensation fronts' growth rates are unmodeled  
  > "It is unclear if pebble growth is sufficiently rapid around other condensation fronts to explain the HL Tau results." (6 Discussion)
- Caveat (inferred, ours): Correlation between dip radii and condensation fronts depends on the adopted MFH temperature profile with large uncertainty
- Caveat (inferred, ours): Coincidence of three dips with many species' fronts is weakly constraining
- Caveat (inferred, ours): Two-population model is not fit and parameters are fixed by hand; alternatives like unresolved optical depth or scattering not explored
- Caveat (inferred, ours): Spectral index relies on unspecified flux calibration accuracy between bands

## Reproducibility

- Data public (paper): ALMA SV data set 2011.0.00015.SV acknowledged  
  > "This paper makes use of the following ALMA data sets: ADS/JAO.ALMA#2011.0.00015.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN imaging parameters
- Missing: Smooth-model fit parameters and fit method
- Missing: Radial profile extraction details
- Data volume (inferred): Large; long-baseline three-band SV visibilities, likely tens to hundreds of GB
- Score (inferred): 3/5, Public data and clear outline, but imaging and fitting parameters are not given and calibrated data come from another paper.
- Rediscovery candidate: yes, Public SV data, numeric dip parameters in Table 1 can be checked, though some imaging details are missing.

## Links

- Method: (cite: Rau11) (Multi-frequency deconvolution used for the spectral index map)
- Companion: (cite: Partnership15) (HL Tau long baseline campaign paper with data, calibration, ring fits and inclination/PA)
- Related: ALMA HL Tau Long Baseline Campaign science verification

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 39,
  "rate": 0.506
 },
 "evidence_ok": true
}
```
