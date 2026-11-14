# CO, H<SUB>2</SUB>O, H<SUB>2</SUB>O<SUP>+</SUP> line and dust emission in a z = 3.63 strongly lensed starburst merger at sub-kiloparsec scales

`2019A&A...624A.138Y` | Astronomy and Astrophysics 2019 | first author: Yang, C. | arXiv: 1903.00273 | DOI: 10.1051/0004-6361/201833876

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the spatial and kinematic structure, dust and gas content (CO, H2O, H2O+) of the lensed SMG G09v1.97 at sub-kpc scales in the source plane, and is it a merger?  
  > "Here we present ALMA observations of the dust continuum, CO, H~2~O, and H$_2$O$^+$ line emission in G09v1.97 at spatial resolutions of $\lesssim$ 0.4$''$." (1 Introduction)
- Target **G09v1.97 (H-ATLAS J083051.0+013224)**: coordinates RA 08:30:51.156, Dec +01:32:24.35 (Band 4 phase center)  
  > "The central observing coordinates (J2000) are RA 08:30:51.156 and DEC $+$01:32:24.35 for the Band 4 observations" (Observations and Data Reduction); "The redshift $z$ = 3.632 corresponds to a luminosity distance of $D_\mathrm{L}$ = 32724 Mpc." (Observations and Data Reduction); z/distance z = 3.632  
  > "The central observing coordinates (J2000) are RA 08:30:51.156 and DEC $+$01:32:24.35 for the Band 4 observations" (Observations and Data Reduction); "The redshift $z$ = 3.632 corresponds to a luminosity distance of $D_\mathrm{L}$ = 32724 Mpc." (Observations and Data Reduction); distance from CO(6-5) central frequency from this work  
  > "The central observing coordinates (J2000) are RA 08:30:51.156 and DEC $+$01:32:24.35 for the Band 4 observations" (Observations and Data Reduction); "The redshift $z$ = 3.632 corresponds to a luminosity distance of $D_\mathrm{L}$ = 32724 Mpc." (Observations and Data Reduction)

## Data provenance

- ALMA projects: 2015.1.01320.S, 2013.1.00358.S
- bands: Band 4 (2 mm) and Band 7 (0.87 mm continuum)  
  > "was observed in the 2 mm atmospheric window (Band 4) with the Atacama Large Millimeter/submillimeter Array (ALMA)" (2 Observations)
- frequencies and spectral setup: Band 4: four SPWs of 1875 MHz, 147.146–150.064 and 159.278–162.819 GHz; 128 channels of 15.6 MHz (~30 km/s)  
  > "In each spectral window, there are 128 frequency channels giving a resolution of 15.6 MHz ($\sim$ 30  km s$^{-1}$)." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-5, baselines 15 m to ~1462 m (Band 4)  
  > "The observations were performed with the ALMA C36-5 configuration, which provides baselines from 15 m up to about 1462 m" (2 Observations)
- baselines: _not stated_
- angular resolution: 0.3''–0.4'' Band 4; 0.19''x0.12'' Band 7  
  > "yielding a synthesis beam of 0.19$''$$\times$0.12$''$ (PA = 60$^\circ$)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.21 mJy/beam in 50 km/s channel (Band 4)  
  > "The root mean square (RMS) of the data reaches 0.21 mJy beam$^{-1}$ in a 50  km s$^{-1}$ channel width." (2 Observations)
- time on source: 73.8 min Band 4 (36.8 min x2); 3.1 min Band 7  
  > "amounting to a total of 73.8 min on-source time" (2 Observations)
- observing dates: 04-Aug-2016 and 25-Aug-2016 (Band 4); 01-Sep-2015 (Band 7)  
  > "The observations were performed on 01-Sep-2015 in good weather conditions" (2 Observations)
- pi or archival as stated: Band 4 PI A. Omont; Band 7 archival, PI S. Eales  
  > "We have also included in this study ALMA Band 7 continuum archive data of G09v1.97" (2 Observations)
- Line: CO 6-5 (149.207 GHz (sky))
- Line: para-H2O 2_11-2_02 (161.946 GHz (sky))
- Line: H2O+ 2_02-1_11 and 2_11-2_02 (742.1 and 742.3 GHz (rest))
- Line: H2(18)O 2_11-2_02 (745.320 GHz (rest))
- Other facility **Keck-II/NIRC2**: Ks-band image to locate foreground deflectors  
  > "superimposed on the *Keck*-II/NIRC2 $\mathit{Ks}$-band image" (3.1 Continuum and Emission Line Images)
- Other facility **HST**: F110W image confirming compound lens  
  > "also confirms such a compound lens configuration" (3.1 Continuum and Emission Line Images)
- Other facility **WHT ACAM**: deflector redshifts  
  > "redshifts obtained from the William Herschel Telescope (WHT) ACAM spectroscopy" (3.1 Continuum and Emission Line Images)
- External data: Previous SMA 880 um lens model magnification mu = 6.9±0.6 and structure  
  > "With a magnification factor of $\mu$ = $6.9\pm0.6$, estimated from 880 $\mu$m dust continuum observations with the SMA" (1 Introduction) [from (cite: 2013ApJ...779...25B)]
- External data: IRAM 30m/NOEMA line fluxes and CO(1-0) based gas mass, CO excitation  
  > "comparable to those obtained with the IRAM 30-meter telescope and NOEMA" (3.2 Integrated Spectra) [from (cite: 2016A&A...595A..80Y; 2017A&A...608A.144Y)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipelines with minor flagging  
  > "Both datasets were calibrated using the ALMA calibration pipelines, with only minor flagging required." (2 Observations)
- casa version: CASA 5.1.1  
  > "using `tclean` within `CASA`[^3] version 5.1.1" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 4: J0750+1231 and J0854+2006; Band 7: J0510+1800  
  > "The flux calibrators were J0750+1231 and J0854+2006." (2 Observations)
- flux scale uncertainty: 5% Band 4; 10% Band 7  
  > "The absolute flux calibration uncertainty in Band 7 is 10%." (2 Observations)
- self calibration: Iterative phase-only self-calibration until S/N stopped improving; similar for Band 7  
  > "We then performed several iterations of phase-only self-calibration until the S/N stopped improving." (2 Observations)

### Imaging

- task: tclean in CASA  
  > "imaged and `CLEAN`ed using `tclean` within `CASA`[^3] version 5.1.1" (2 Observations)
- deconvolver: MS-MFS, nterms=2  
  > "combined by using the `MS-MFS` algorithm (cite: 2011A&A...532A..71R) with multiple Taylor terms `nterms=2`" (2 Observations)
- weighting robust: robust −0.5 continuum; −0.2 CO; 0.5 H2O and H2O+  
  > "$-$ 0.2 for the CO emission, and  0.5 for the H~2~O and H$_2$O$^+$ emission" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels subtracted from cubes  
  > "After subtracting the dust continuum for the line emission data cube" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: CO 0.37x0.35'' PA64; H2O 0.38x0.36''; H2O+ 0.40x0.36''; 2mm cont 0.32x0.28''; 0.87mm 0.19x0.12''  
  > "0.32$\times$0.28" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Lens model approach: SIE deflectors as in earlier SMA parametric model  
  > "Similar to the parametric lens model in (cite: 2013ApJ...779...25B), the two foreground deflectors (G1 and G2, see Fig. [1](#fig:g09-image)) are assumed to be singular isothermal ellipsoid (SIE)" (4 Lens Modeling) [from (cite: 2013ApJ...779...25B)]
- sl_fit lens inversion method incl. treatment of beam and correlated noise  
  > "The lens model is based on the `sl_fit` lens inversion code, following the method described in (cite: 2011ApJ...738..125G)." (4 Lens Modeling) [from (cite: 2011ApJ...738..125G)]
- CO(6-5)/CO(1-0) ratio assumed for gas masses  
  > "taking the same ${\mathrm{CO}}(6\text{--}5)$ to ${\mathrm{CO}}(1\text{--}0)$ ratio for R and B as in (cite: 2017A&A...608A.144Y)" (5.4 Intrinsic properties) [from (cite: 2017A&A...608A.144Y)]
- SFR calibration from LIR  
  > "the calibration of the far-IR star formation rate ($\mathit{SFR}$) from (cite: 2012ARA&A..50..531K)" (1 Introduction) [from (cite: 2012ARA&A..50..531K; 2011ApJ...737...67M)]

### Not stated but needed to reproduce (our reading)

- Number of tclean iterations, thresholds, masks and cell/image sizes
- Self-calibration solution intervals and number of rounds
- Line-free channel selection
- Uv-range or taper settings
- Source-plane flux-binning details and MCMC chain length/convergence
- Details of the modified blackbody SED fit (fitted data points, priors, two-temperature split)
- Deflector optical positions used for priors
- Exact PyAutoLens and 3DBarolo settings

## Analysis recipe

1. **Image continuum and line cubes**: Pipeline-calibrated data cleaned with tclean, MS-MFS continuum, phase-only self-cal, continuum subtraction  
  > "The calibrated data were then imaged and `CLEAN`ed using `tclean` within `CASA`[^3] version 5.1.1" (2 Observations)
   - software: CASA
   - parameter: robust −0.5 / −0.2 / 0.5; nterms=2  
  > "$-$ 0.2 for the CO emission, and  0.5 for the H~2~O and H$_2$O$^+$ emission" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit integrated line spectra**: Multi-Gaussian (B, Rb, Rr) fit of spectra; H2O and H2O+ widths fixed to CO values  
  > "we fix the linewidths of the B, Rb, and Rr components to be that found for the components of the ${\mathrm{CO}}(6\text{--}5)$ line" (3.2 Integrated Spectra)
   - software: MPFIT
   - fitting: Levenberg-Marquardt least squares; three Gaussians since two left residuals  
  > "Therefore, we fitted the lines with three Gaussian components." (3.2 Integrated Spectra)
   - validation: Compared total fluxes with IRAM 30m/NOEMA; no missing flux  
  > "indicating that there is no missing flux in the ALMA data of G09v1.97" (3.2 Integrated Spectra)
3. **Lens model from dust continuum**: Joint fit of 1.94 and 0.87 mm images with two SIE deflectors and two exponential-profile source components; image-plane fit  
  > "we used the 1.94 and 0.87 mm dust continuum images (Fig. [1](#fig:g09-image)) to constrain simultaneously the mass distribution (SIE model) of G1 and G2 and the dust emission" (4.1 Fitting the dust continuum emission)
   - software: sl_fit
   - parameter: Priors: Einstein radii uniform [0.1,1.1'']; axis ratios Normal(0.5,0.2); source positions uniform ±0.2''; source axis ratio uniform [0.1,0.9]; Reff Normal(0.1'',0.03'') in [0,0.2'']  
  > "The prior on both Einstein radii is uniform in the range $[0.1\ensuremath{''},1.1\ensuremath{''}]$." (4.1 Fitting the dust continuum emission)
   - assumption: Both source components have constant magnification across SED; deflectors at z=0.626 and 1.002  
  > "each of the two background components has a constant magnification across its entire far-IR spectral energy distribution (SED)" (4.1 Fitting the dust continuum emission)
   - fitting: MCMC Metropolis-Hastings; median and 68% intervals  
  > "implementing the standard Metropolis-Hastings algorithm" (4 Lens Modeling)
   - validation: Residuals <2.5 sigma; PyAutoLens pixelized reconstruction converged to same model  
  > "The analysis converges to the same lens model and reconstructs a source galaxy with the same global structure as the double-disk model" (4.1 Fitting the dust continuum emission)
4. **Source-plane line cube reconstruction**: Cube binned into 10 velocity bins of 105 km/s (−478 to 467); fixed mass model; one elliptical exponential per bin; H2O+ in 2 bins  
  > "the data cube was binned into 10 velocity channel bins of 105  km s$^{-1}$ from $-$478 to 467 km s$^{-1}$" (4.2 Fitting the CO and H2O Line Emission)
   - software: sl_fit
   - assumption: CO and H2O emission identical up to flux normalization  
  > "we assume that, up to a normalizing flux constant, the emission is identical between the ${\mathrm{CO}}(6\text{--}5)$ and H~2~O($2_{11}\text{--}2_{02}$) lines" (4.2 Fitting the CO and H2O Line Emission)
   - fitting: Same priors as continuum model; 10x7 parameters  
  > "We thus fit for the 10$\times$7 parameters defining the source emission" (4.2 Fitting the CO and H2O Line Emission)
   - validation: Image-plane moment maps and per-channel residuals; image vs source-plane moment maps match  
  > "The moment maps from the image and source plane match very well, suggesting that our lens model is robust." (5.2 Kinematic structure)
5. **Morphology and kinematics in source plane**: Three-disk IMFIT of CO moment-0 map; inclination from axis ratio with q0=0.2; 3DBarolo tilted-ring test; PV diagrams  
  > "we performed a fit to the 0$^{\rm th}$ moment map of ${\mathrm{CO}}(6\text{--}5)$ in the source plane with a disk model using `IMFIT`" (5.1 Morphology)
   - software: IMFIT, 3DBarolo
   - parameter: q0 = 0.2  
  > "Choosing a typical value of $q_0=0.2$ for disk galaxies" (5.1 Morphology)
   - assumption: R and B are thin disks  
  > "Assuming that both R and B are thin disks, the inclination angle can be derived" (5.1 Morphology)
   - fitting: chi2 minimization; bootstrap uncertainties of 10%  
  > "Using bootstrap resampling, the uncertainties from the fit are determined with uncertainties of 10%." (5.1 Morphology)
   - validation: Residuals <1% of emission  
  > "maximum differences are less than 1% of the emission" (5.1 Morphology)
6. **Derive LIR, SFR, gas mass**: Split total LIR among B, G, R with modified blackbody (beta=2), LIR proportional to CO(6-5) luminosity for R and B; 50% extra uncertainty; SFR = 1.4e-10 LIR; gas mass from CO(6-5)/CO(1-0)  
  > "We can decompose the total $L_{\mathrm{IR}}$ into three parts using a modified black-body model ($\beta$ = 2), for B, G, and R" (5.4 Intrinsic properties)
   - assumption: S0.87/S1.94 = 26 for R and B; 5.4 for bridge  
  > "for which we assume a similar ratio, $S_\mathrm{0.87}$/$S_\mathrm{1.94}$ = 26" (5.4 Intrinsic properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: calibration pipeline, tclean imaging, gaincal self-cal  
  > "using `tclean` within `CASA`[^3] version 5.1.1" (2 Observations)
- **MPFIT** : Gaussian fits of line spectra  
  > "Levenberg-Marquardt least-square minimization code `MPFIT`" (3.2 Integrated Spectra)
- **sl_fit** : MCMC lens inversion  
  > "The lens model is based on the `sl_fit` lens inversion code" (4 Lens Modeling)
- **PyAutoLens** : pixelized source reconstruction as a test  
  > "This has been further tested with `PyAutoLens`" (4.1 Fitting the dust continuum emission)
- **IMFIT** : disk fits to source-plane moment-0  
  > "with a disk model using `IMFIT`" (5.1 Morphology)
- **3DBarolo** : tilted-ring fit to source-plane CO cube  
  > "using $^\mathrm{3D}$`Barolo`" (5.1 Morphology)
- **GALFIT** : subtracting foreground galaxies in Ks and F110W  
  > "after subtracting the foreground galaxies with `GALFIT`" (3.1 Continuum and Emission Line Images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total magnification (dust) | 10.3 | 0.5 | dimensionless | 3 | $\mu_{\rm tot}$ = $10.3\pm 0.5$ |
| Compact dust Reff | 0.63 | 0.15 | kpc | 3 | $R_{\rm eff,\,1}$ = $0.63 \pm 0.15\, {\rm kpc}$ |
| Extended dust Reff | 1.37 | 0.05 | kpc | 3 | $R_{\rm eff,\,2}$ = $1.37 \pm 0.05\, {\rm kpc}$ |
| Einstein radius G1 | 0.39 | ±0.01 | arcsec | 3 | Einstein radius of $0.39\ensuremath{''} ^{+0.01}_{-0.01}$ for G1 |
| Einstein radius G2 | 0.63 | ±0.01 | arcsec | 3 | $0.63\ensuremath{''}^{+0.01}_{-0.01}$ for the more distant G2 |
| CO(6-5) total line flux components B/Rb/Rr | 2.2 / 6.0 / 4.8 | 0.2 / 1.3 / 1.2 | Jy km/s | 2 | $2.2\pm0.2$ |
| H2(18)O line flux | 0.5 | 0.1 | Jy km/s | 2 | we observe a 5-$\sigma$ emission line with an integrated flux of $0.5\pm0.1$ Jy  km s$^{-1}$ |
| Band 4 continuum flux | 8.8 | 0.5 | mJy | 1 | $8.8\pm0.5$ mJy |
| Band 7 continuum flux | 106.6 | 10.7 | mJy | 1 | $106.6\pm10.7$ mJy |
| Semi-major half-light radius R and B | 1.2 and 0.4 | 10% | kpc | 5 | of 1.2 kpc and 0.4 kpc, are separated by a projected distance of 0.18$''$ (1.3 kpc) |
| Inclinations R, B | 82, 66 | not stated | deg | 5 | we infer inclinations for R and B of 82$^\circ$ and 66$^\circ$, respectively |
| LIR of B | (4.0±2.0)e12 | 2.0e12 | Lsun | 6 | $L_{\mathrm{IR}}$$_\mathrm{,\,B}$ = (4.0$\pm$2.0)$\times$10$^{12}$ $L_\odot$ |
| LIR of R | (6.3±3.1)e12 | 3.1e12 | Lsun | 6 | $L_{\mathrm{IR}}$$_\mathrm{,\,R}$ = (6.3$\pm$3.1)$\times$10$^{12}$ $L_\odot$ |
| SFR B and R | 600 and 900 | ±300 / ±400 | Msun/yr | 6 | $\mathit{SFR}_\mathrm{B}$ = (6$\pm$3)$\times$10$^{2}$ $M_\odot$ yr$^{-1}$ |
| Gas mass R and B | 5e10 and 4e10 | not stated | Msun | 6 | about 5$\times$10$^{10}$ and 4$\times$10$^{10}$ $M_\odot$, respectively |
| Bridge dust temperature | 17 (+9/−4) | +9/-4 | K | 6 | $T_{\mathrm{d}}$ = $17^{+9}_{-4}$ K |

## Qualitative findings

- CO(6-5), H2O and H2O+ line profiles and spatial distributions are strikingly similar  
  > "The observed line profiles of the ${\mathrm{CO}}(6\text{--}5)$, H~2~O($2_{11}\text{--}2_{02}$), and $J_\mathrm{up}$ = 2 H$_2$O$^+$ lines are strikingly similar." (abstract)
- First detection at high z of H2(18)O(2_11-2_02) at 5 sigma  
  > "we also present the first 5-$\sigma$ detection of H$_2^{18}$O($2_{11}\text{--}2_{02}$)" (6 Summary)

## Claim tuples

- H: Is G09v1.97 a merger or a single clumpy rotating disk? | E: Source-plane reconstruction, PV diagrams, 3DBarolo rotating-disk fit | R: Rotating disk model fails; R and B overlap spatially in PV; bridge gas | F: Two gas-rich merging galaxies in pre-coalescence | **supported**
- H: Do dust and gas differ in structure? | E: Two-component dust model vs CO/H2O reconstruction | R: Compact + extended dust disks; cold dust peaks between two gas components | F: Cold ISM concentrated in the interaction region | **partially**
- H: Does the LIR–line luminosity correlation hold at sub-kpc scales? | E: Compare L_CO/L_IR and L_H2O/L_IR for B and R | R: Ratios consistent with SMGs and local ULIRGs | F: H2O lines trace SFR down to sub-kpc scales | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-plane fit used because sl_fit lacks uv-plane fitting; high uv coverage assumed sufficient  
  > "Since our ALMA data has such sufficiently high uv-plane coverage and S/N, we safely assume that any information loss in the source plane as a result of our image-plane analysis is negligible." (4 Lens Modeling)
- Alternative: N2H+(8-7) identification of 745 GHz line rejected in favor of H2(18)O  
  > "However, we rule out this identification for the following reasons." (3.2 Integrated Spectra)
- How they decided it was enough: _not stated_
- Limitation (authors): Source-plane uncertainties may be underestimated; mass-sheet degeneracy not explored  
  > "the uncertainties of $\mu$ (and on the intrinsic source flux and size) do not account for the effect of mass-sheet degeneracy" (Appendix)
- Limitation (authors): No spatially resolved photometry for B, G, R so large LIR uncertainties  
  > "We acknowledge that there could be large uncertainties because there is no spatially resolved photometry for B, G, and R." (5.4)
- Caveat (inferred, ours): Image-plane lens fitting with CLEANed images rather than visibilities
- Caveat (inferred, ours): Parametric one-exponential source per velocity bin may miss structure
- Caveat (inferred, ours): LIR split among B, G, R relies on assumed CO-LIR proportionality and SED ratios
- Caveat (inferred, ours): Mass model from continuum only; deflector profile fixed isothermal

## Reproducibility

- Data public (paper): Band 7 described as archive data; both projects cited by code  
  > "We have also included in this study ALMA Band 7 continuum archive data of G09v1.97" (2 Observations)
- Products in archive: _not stated_
- Missing: sl_fit code availability not stated
- Missing: Clean parameters and masks
- Missing: Self-cal details
- Missing: Lens model posterior chains
- Data volume (inferred): ~50–150 GB raw for two Band 4 and one Band 7 execution
- Score (inferred): 3/5, Public data and clear lens priors, but imaging details, self-cal settings and code access are missing.
- Rediscovery candidate: no, Results rely on specialised unreleased lens code and incomplete processing details.

## Links

- Method: (cite: 2011ApJ...738..125G) (sl_fit lens inversion method)
- Method: (cite: 2013ApJ...779...25B) (earlier SMA lens model of G09v1.97)
- Companion: (cite: 2017A&A...608A.144Y) (CO excitation and gas properties of G09v1.97)
- Companion: (cite: 2016A&A...595A..80Y) (H2O and H2O+ in H-ATLAS lensed SMGs)
- Related: H-ATLAS
- Related: SMA 880 um observations of G09v1.97

## Checks

```json
{
 "quotes": 95,
 "quotes_ok": 95,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 66,
  "rate": 0.742
 },
 "evidence_ok": true
}
```
