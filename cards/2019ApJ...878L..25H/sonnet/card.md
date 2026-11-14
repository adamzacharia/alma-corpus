# ALMA Polarimetry of AT2018cow

`2019ApJ...878L..25H` | The Astrophysical Journal Letters 2019 | first author: Huang, Kuiyun | arXiv: 1905.09785 | DOI: 10.3847/2041-8213/ab23fd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: transients
- Question: Is linear polarization detectable in AT2018cow at 100 and 230 GHz, and what does it imply for the circumburst environment and progenitor (stellar explosion vs tidal disruption)?  
  > "Based on two epochs of ALMA observations, the scenarios of a progenitor accompanied by a dense circumstellar medium are examined." (Introduction)
- Target **AT2018cow**: coordinates _not stated_; z/distance z = 0.0141 (host CGCG 137-068); D = 60 Mpc used in scaling equations  
  > "A luminous transient, AT2018cow, was discovered near the galaxy CGCG 137-068 ($z$ =0.0141) at 2018-06-16 10:35:02 UT (cite: smartt18)." (Introduction); distance from smartt18 for discovery/host; 60 Mpc scaling follows ho19  
  > "A luminous transient, AT2018cow, was discovered near the galaxy CGCG 137-068 ($z$ =0.0141) at 2018-06-16 10:35:02 UT (cite: smartt18)." (Introduction)

## Data provenance

- ALMA projects: 2017.A.00046.T
- bands: Band 3 (97.5 GHz) and Band 6 (230 GHz)  
  > "using the Atacama Large Millimeter/submillimeter Array (ALMA) in the 100 GHz and 230 GHz bands." (Introduction)
- frequencies and spectral setup: Band 3 SPWs centered 90.5, 92.5, 102.5, 104.5 GHz; Band 6 SPWs 224, 226, 240, 242 GHz  
  > "| 12m         | 0,1,2,3   | 232.9        | $<0.15$    | $-$         | 48.755$\pm$0.047 | 0.016 (rms)    | 0.018 (rms)    |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12-m array and ACA  
  > "using both the 12-m antenna array and Atacama Compact Array (ACA)." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Epoch1 27 June 2018 (T0=11.1 d); Epoch2 3 July 2018 (T0=17.1 d)  
  > "starting at 27 June 2018 01:04 UT (midpoint $T_{0}$=11.1 d, here after epoch1)." (Observations)
- pi or archival as stated: DDT, PI K. Huang  
  > "Director’s Discretionary Time (DDT) during Cycle 5 (2017.A.00046.T; PI K. Huang)" (Observations)
- Other facility **ATCA, SMA**: Published ATCA data at similar epochs and SMA 230-GHz monitoring from Ho et al. used in SED fits and light curve  
  > "The smooth broken power-law fitting was performed, including ATCA data taken at the similar epochs" (Discussion)
- External data: ATCA data and SMA 230-GHz monitoring data  
  > "together with the 230-GHz monitoring data (cite: ho19)" (Analysis and Results) [from (cite: ho19)]
- External data: Low-frequency spectral index beta_low = 2.5  
  > "the spectral index of the lower-frequency side was fixed as $\beta_{low}=2.5$ (reported by (cite: ho19))" (Discussion) [from (cite: ho19)]

## Processing

### Calibration

- pipeline or manual: Raw data reduced at EA-ARC with CASA  
  > "The raw data of ALMA were reduced at the East Asian ALMA Regional Center (EA-ARC) using CASA (version 5.1.1)" (Analysis and Results)
- casa version: 5.1.1  
  > "using CASA (version 5.1.1)" (Analysis and Results)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 12m: J1550+0527 (bandpass and flux); ACA: J1337-1257 and J1517-2422  
  > "the bandpass and flux were calibrated using observations of J1550+0527, and J1606+1814 was used for the phase calibration." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Applied to 12-m data before final CLEAN  
  > "We further performed interactive CLEAN deconvolution imaging (cite: clean1; clean2) with self-calibration for the data obtained by the 12-m antenna array." (Analysis and Results)

### Imaging

- task: Interactive CLEAN with Stokes I, Q, U maps  
  > "The Stokes $I$, $Q$, and $U$ maps were CLEANed with an appropriate number of CLEAN iterations after the final round of self-calibration." (Analysis and Results)
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

- Theoretical analysis for R, B, v, n_e followed Ho et al.  
  > "the theoretical analysis of (cite: ho19) is followed for the estimated values of the radius of the shock" (Discussion) [from (cite: ho19)]
- T0 = MJD 58285  
  > "The date is the same $T_{0}$ used in (cite: perley19; ho19)." (Introduction) [from (cite: perley19; ho19)]

### Not stated but needed to reproduce (our reading)

- CLEAN weighting, robust, cell size, image size, masks, iteration thresholds
- Self-calibration solution intervals and rounds
- Polarization calibration details (D-terms, angle calibrator model)
- Synthesized beams and rms of images
- Photometry method (point-source fit vs aperture)
- Values of epsilon_e, epsilon_B, f used
- Exact ν_p fit function form and the fitted smoothness parameter

## Analysis recipe

1. **Reduce and image**: CASA reduction at EA-ARC, interactive CLEAN with self-calibration of 12-m data; Stokes I, Q, U maps  
  > "We further performed interactive CLEAN deconvolution imaging (cite: clean1; clean2) with self-calibration for the data obtained by the 12-m antenna array." (Analysis and Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Polarization upper limits**: 3-sigma upper limits from non-detections in Q and U maps  
  > "the 3-$\sigma$ upper limits were derived based on the non-detections in Q and U maps." (Analysis and Results)
   - software: CASA
   - assumption: Negligible depolarization between source and observer for point source at mm wavelengths  
  > "the depolarization between the source and observation site is negligible for the point source (i.e., transients) in this millimeter band (cite: brentjens05)" (Analysis and Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit per-SPW power-law spectral indices**: Fit f_nu ∝ nu^beta to SPW fluxes in each band and epoch  
  > "The photometric measurements in each of the spectral windows (SPWs) of Band3 and Band6 were fitted with a simple power-law function (i.e. $f_{\nu}\propto\nu^{\beta}$)." (Analysis and Results)
   - fitting: chi-square power-law fit; 242 GHz point excluded in a second epoch2 Band6 fit  
  > "The same fitting was therefore performed by excluding the data, and $\beta_{E2B6}=-0.65\pm0.02$ ($\chi^2/ndf$=1.25 with $ndf$=1) was obtained." (Analysis and Results)
   - validation: reduced chi^2 reported  
  > "These fittings yield $\beta_{E1B3}=1.080\pm0.007$ ($\chi^2/ndf$=1.39 with number of degree of freedom, $ndf$=2) for epoch1 with Band3" (Analysis and Results)
4. **Fit spectral peak frequency**: Smooth broken power-law fit including ATCA data, excluding SMA  
  > "we excluded the data taken by the Submillimeter Array (SMA)." (Discussion)
   - parameter: beta_low=2.5 fixed; beta_high=-1.15 (epoch1), -0.86 (epoch2) fixed  
  > "the higher-frequency side was fixed as $\beta_{high}=-1.15$ for epoch1 and $\beta_{high}=-0.86$ for epoch2." (Discussion)
   - fitting: smooth broken power law (Band-function-like)  
  > "The smooth fitting with wider spectral frequency coverage is also reasonable to characterize the spectral peak frequency as the method is applied for various analyses such as GRB prompt emissions" (Discussion, Spectral Flux Distribution)
   - validation: nu_p ∝ t^-1.1 consistent with SSA model of Chevalier 1998  
  > "$\nu_{p} \propto t^{-1.1}$, which is consistent with that of the theoretical model for the synchrotron self-absorption frequency (cite: chevalier98)." (Discussion)
5. **Estimate shock parameters and Faraday depth, E_max limit**: Scaling relations of Ho et al. for R, B, v, n_e; Faraday depth with turbulent field coherence length gives lower limits on l_M and E_max  
  > "The lower limit on $\ell_M$ leads to the lower limit on the maximum energy of accelerating particles at the shock." (Discussion)
   - assumption: l_M ~ R/10 as in Tycho's SNR; D = 60 Mpc; first-order Fermi acceleration  
  > "The observation of Tycho’s SNR indicates $\ell_M \sim R/10$ (cite: shimoda18)." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: Data reduction, imaging, self-calibration  
  > "using CASA (version 5.1.1)" (Analysis and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Linear polarization upper limit, 97.5 GHz epoch1 | <0.10 | 3-sigma | % | 2 | the values of $<0.10\%$ in the 97.5-GHz band and $<0.15\%$ in the 233-GHz band |
| Linear polarization upper limit, 233 GHz epoch2 | <0.15 | 3-sigma | % | 2 | the values of $<0.10\%$ in the 97.5-GHz band and $<0.15\%$ in the 233-GHz band |
| beta epoch1 Band3 | 1.080 | 0.007 | dimensionless | 3 | $\beta_{E1B3}=1.080\pm0.007$ |
| beta epoch1 Band6 | -1.15 | 0.16 | dimensionless | 3 | $\beta_{E1B6}=-1.15\pm0.16$ |
| beta epoch2 Band3 | 0.44 | 0.05 | dimensionless | 3 | $\beta_{E2B3}=0.44\pm0.05$ |
| beta epoch2 Band6 (excluding 242 GHz) | -0.65 | 0.02 | dimensionless | 3 | $\beta_{E2B6}=-0.65\pm0.02$ ($\chi^2/ndf$=1.25 with $ndf$=1) |
| Peak frequency epoch1 | 109.8 | 0.5 | GHz | 4 | $\nu_{p}$ =109.8$\pm$0.5 GHz ($\chi^2/ndf$=7.3 with $ndf=$7) at epoch1 |
| Peak frequency epoch2 | 67.4 | 1.6 | GHz | 4 | $\nu_{p}$ = 67.4$\pm$1.6 GHz ($\chi^2/ndf$=7.6 with $ndf=6$) at epoch2 |
| Lower limit on E_max | ~3 (scaled) | not stated | GeV | 5 | \right)^4 \;{\rm GeV}. |

## Qualitative findings

- Non-detection of polarization explained by internal Faraday depolarization with dense medium and strong B, favoring stellar explosion over tidal disruption  
  > "The result supports the stellar explosion scenario rather than the tidal disruption scenario" (Discussion)

## Claim tuples

- H: Spectral peak traces synchrotron self-absorption | E: Broken power-law fits to ALMA+ATCA SEDs at two epochs | R: nu_p 109.8 GHz to 67.4 GHz, ∝ t^-1.1 | F: Peak is the SSA frequency, consistent with Ho et al. model | **supported**
- H: Polarization is detectable if progenitor is a stellar explosion in dense medium or TDE | E: ALMA polarimetry at 97.5 and 233 GHz | R: <0.10% and <0.15% (3-sigma) | F: Internal Faraday depolarization explains non-detection; supports stellar explosion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Millimeter band has weaker Faraday effect than cm band  
  > "In this millimeter wavelength range, the Faraday effect is weaker than the centimeter radio band." (Introduction)
- Alternative: Tidal disruption scenario gives tau_V<<1 so sizable polarization would be expected  
  > "These lead to $\tau_{V} < 3\times10^{-7} \ll 1$ in Eq. (5) even for $N=1$" (footnote 3)
- How they decided it was enough: _not stated_
- Limitation (authors): Large reduced chi^2 in SED fits possibly due to differing epochs; significant variability at 242 GHz  
  > "The larger reduced $\chi^2$ may be caused by the epoch differences." (Discussion)
- Caveat (inferred, ours): Non-detection interpretation depends on assumed epsilon_e, epsilon_B, f and l_M~R/10 borrowed from Tycho
- Caveat (inferred, ours): Spectral peak in text inconsistent: ~140 GHz vs 110 GHz
- Caveat (inferred, ours): Variability within observation windows not treated
- Caveat (inferred, ours): Upper-limit method for polarization (bias) not described

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Polarization calibration details
- Missing: ATCA and SMA data from Ho et al.
- Data volume (inferred): ~50-200 GB raw for two epochs 12m+ACA
- Score (inferred): 3/5, Data identified and CASA version given, but imaging and polarization calibration details sparse; results mostly simple numbers.
- Rediscovery candidate: no, Imaging and polarization-calibration recipe incomplete, and the fits need external ATCA data.

## Links

- Companion: Ho, A. Y. Q., et al. 2019, ApJ, 871, 73 (cite: ho19) (Radio model, SMA/ATCA data and theory followed)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 35,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
