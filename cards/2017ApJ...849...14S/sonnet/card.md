# Resolved Structure of the Arp 220 Nuclei at λ ≈ 3 mm

`2017ApJ...849...14S` | The Astrophysical Journal 2017 | first author: Sakamoto, Kazushi | arXiv: 1709.08537 | DOI: 10.3847/1538-4357/aa8f4b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the resolved continuum structure of the two Arp 220 nuclei at 3 mm, how much of it is dust vs plasma emission, and what does the compact western core imply about the luminosity source?  
  > "ALMA archival data at $\sim$0.05$''$ resolution are used for extensive visibility fitting and deep imaging of continuum emission." (abstract)
- Target **Arp 220 (E and W nuclei)**: coordinates E: 15h34m57.2917s +23d30m11.337s; W: 15h34m57.2224s +23d30m11.500s (ICRS, 1G fit)  
  > "We adopt an angular size distance of $D_{\rm A} = 85.0$ Mpc (1$''$ = 412 pc), luminosity distance $D_{\rm L} = 87.9$ Mpc" (Introduction); z/distance D_A = 85.0 Mpc, D_L = 87.9 Mpc  
  > "We adopt an angular size distance of $D_{\rm A} = 85.0$ Mpc (1$''$ = 412 pc), luminosity distance $D_{\rm L} = 87.9$ Mpc" (Introduction); distance from adopted to be consistent with Scoville17; L_IR from Armus09  
  > "We adopt an angular size distance of $D_{\rm A} = 85.0$ Mpc (1$''$ = 412 pc), luminosity distance $D_{\rm L} = 87.9$ Mpc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00113.S
- bands: around 100 GHz (3 mm), two tunings  
  > "The dataset consists of two tunings around 100 GHz consecutively observed on 2015 Oct. 27 in a long-baseline configuration" (ALMA Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 0.24–10.38 km (tuning 1, 12CO); 0.22–11.10 km (tuning 2, 13CO)  
  > "The projected baseline lengths for Arp 220 ranged 0.24–10.38 km for the first tuning with $^{12}$CO and 0.22–11.10 km for the second with $^{13}$CO." (ALMA Data)
- angular resolution: ~0.05'' (uniform weighting)  
  > "ALMA archival data at $\sim$0.05$''$ resolution" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 Oct. 27  
  > "consecutively observed on 2015 Oct. 27 in a long-baseline configuration" (ALMA Data)
- pi or archival as stated: archival, P.I. Scoville  
  > "We analyzed archival data of the ALMA project 2015.1.00113.S (P.I. Scoville)." (ALMA Data)
- Line: 12CO 1-0 (not stated)
- Other facility **VLA 33 GHz (Barcos-Munoz15)**: exponential-disk plasma models and 6–33 GHz spectral indices  
  > "Parameters for the exponential disks E$_2$$'$ and W$_2$$'$, in italics, are from (cite: Barcos-Munoz15) and fixed." (Visibility Fitting)
- Other facility **VLBI (Varenius17)**: compact radio supernova source distribution for comparison  
  > "compares the 3 mm continuum emission with the distribution of compact ($< 2$ pc) radio (18–2 cm) sources" (Images)
- External data: 33 GHz exponential-disk parameters and 6–33 GHz plasma spectral indices (-0.59 E, -0.61 W)  
  > "$\mbox{$\alpha_{\rm p}$}= -0.59 \pm 0.08$ for E and $-0.61\pm 0.07$ for W from the 6–33 GHz measurements by (cite: Barcos-Munoz15)" (Fractional Contribution of Dust Emission) [from (cite: Barcos-Munoz15)]
- External data: Dust emissivity index beta = 1.8±0.1 (alpha_d = 3.8)  
  > "using the dust emissivity index $\beta$ of $1.8\pm0.1$ in the Galactic plane (cite: Planck21)" (Fractional Contribution of Dust Emission) [from (cite: Planck21)]

## Processing

### Calibration

- pipeline or manual: observatory-provided calibration steps re-run from raw data with revised flux model and extra flagging  
  > "starting from the raw data and following the steps of the observatory-provided calibration except the revised calibrator flux model and the additional flagging of DA65 and DV20." (ALMA Data)
- casa version: CASA 4.7.2  
  > "We used CASA 4.7.2 for our data reduction (cite: CASA07)" (ALMA Data)
- pipeline version: _not stated_
- archive products used as is: No; re-calibrated  
  > "starting from the raw data and following the steps of the observatory-provided calibration" (ALMA Data)
- flux calibrator: J1550+0527, S = 1.000 (nu/104.0 GHz)^-0.602 Jy  
  > "Both used J1550$+$0527 for flux and bandpass calibration." (ALMA Data); "$(S_\nu / {\rm Jy}) = 1.000 \times (\nu/{\rm 104.0\; GHz})^{-0.602}$" (ALMA Data)
- flux scale uncertainty: ~5%  
  > "subject to the flux calibration uncertainty on the order of 5% in this ALMA band" (Visibility Fitting)
- self calibration: phase-only, per tuning for visibility fitting; again after combining for images  
  > "We made phase-only self calibration using continuum." (ALMA Data)

### Imaging

- task: multi-frequency synthesis, two terms, from CDC1  
  > "Multi-frequency synthesis was made with two terms (i.e., the spectrum at each position is assumed to follow a power law)" (Images)
- deconvolver: _not stated_
- weighting robust: Briggs robust; one example robust=0.5 at 0.07'' (three robust values in Fig. 4)  
  > "a 0.07$''$ resolution image made with `robust=0.5`" (1G fit)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: CDC1 total 9.5 GHz; CDC2 subset (nine segments)  
  > "The total bandwidth of CDC$_1$ is 9.5 GHz." (3 mm Spectra of the Two Nuclei)
- primary beam correction: _not stated_
- array combination: two tunings combined for imaging  
  > "Another round was made after combining the two datasets and before making the images presented in this paper." (ALMA Data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Plasma exponential-disk shapes and spectral indices fixed from 33 GHz fits  
  > "We adopt their deconvolved shapes, place the plasma disks in our 1G fit positions" (Distribution of Dust Emission in the Nuclei) [from (cite: Barcos-Munoz15)]
- Distance and L_IR adopted to be consistent  
  > "to be consistent with (cite: Scoville17)" (Introduction) [from (cite: Armus09); (cite: Scoville17)]

### Not stated but needed to reproduce (our reading)

- Image sizes, cell sizes, cleaning thresholds and masks
- Exact CDC1/CDC2 channel ranges and the nine segment boundaries
- Initial guesses and weighting scheme in mpfit visibility fits
- Robust values of the three images in Fig. 4
- Self-calibration solution intervals
- Continuum subtraction approach for line-contaminated data
- How the fitting code treats visibility weights

## Analysis recipe

1. **Recalibrate and self-calibrate**: Standard observatory calibration re-run with revised J1550+0527 flux model, extra flagging, phase-only self-cal  
  > "We made phase-only self calibration using continuum." (ALMA Data)
   - software: CASA
   - parameter: flagged DA45, DA65, DV20; 37 antennas remain  
  > "We flagged three poorly performing antennas, DA45, DA65, and DV20, and used the remaining 37." (ALMA Data)
   - fitting: _not stated_
   - validation: 2G fits repeated before self-cal; sizes changed within uncertainties  
  > "Finally, we verified our 2G fitting by using data before any self-calibration." (2G fit)
2. **Spectra and continuum channel selection**: Power-law fit to off-line channels; define CDC1 and CDC2  
  > "Continuum was first estimated by visually finding regions with least lines in each spectrum and fitting a power-law curve" (3 mm Spectra of the Two Nuclei)
   - fitting: power law S ∝ nu^alpha  
  > "fitting a power-law curve $S_\nu \propto \nu^\alpha$" (3 mm Spectra of the Two Nuclei)
   - validation: _not stated_
3. **Visibility model fitting (1G, r2G, 2G)**: Non-linear fits of complex visibilities per 30 MHz channel, averaged over nine CDC2 segments with inverse-variance weights  
  > "The whole data set was fitted in each and every 30 MHz channel." (1G fit)
   - software: mpfit, IDL
   - parameter: r2G: baselines <0.2 Mlambda flagged  
  > "baselines shorter than 0.2 M$\lambda$ were flagged to suppress any subtraction residuals" (r2G fit)
   - fitting: Levenberg-Marquardt least squares; reduced chi2 1.4–2.1 for 2G  
  > "The fits easily converged with reduced $\chi^2$ of 1.4–2.1." (2G fit)
   - validation: consistency among nine CDC2 segments from two sessions  
  > "This assures that our spatial decomposition is robust and not limited to the r2G model." (2G fit)
4. **Dust fraction from spectral indices**: alpha = f_d alpha_d + (1-f_d) alpha_p solved for f_d  
  > "$\alpha = \mbox{$f_{\rm d}$}\mbox{$\alpha_{\rm d}$}+ (1 - \mbox{$f_{\rm d}$}) \mbox{$\alpha_{\rm p}$}$" (Fractional Contribution of Dust Emission)
   - assumption: alpha_d = 3.8 (optically thin dust, beta=1.8); alpha_p from 6–33 GHz  
  > "We use $\mbox{$\alpha_{\rm d}$}= 3.8$ for optically thin dust emission" (Fractional Contribution of Dust Emission)
   - fitting: _not stated_
   - validation: compared with direct subtraction and with Scoville17 (0.11, 0.45)  
  > "Our adopted estimates agree with theirs." (Fractional Contribution of Dust Emission)
5. **1G+1E fit and dust map**: Fix plasma exponential disks scaled by (1-f_d), fit Gaussian dust component; image-domain subtraction for dust map  
  > "Each nucleus is therefore described as an exponential disk of fixed parameters plus a Gaussian (1G+1E fit)." (1G+1E fit)
   - software: mpfit
   - assumption: all emission optically thin for subtraction  
  > "We also caution about an underlying assumption in this subtraction that all emission is optically thin." (Distribution of Dust Emission in the Nuclei)
   - fitting: _not stated_
   - validation: visibility and image-domain results consistent  
  > "The results for the Gaussian (dust) components are consistent with our image-domain estimate" (Distribution of Dust Emission in the Nuclei)
6. **Bolometric luminosity of W1'**: Optically thick Gaussian-temperature disk, L = pi r^2 sigma T^4 /(2 ln2), T_b = T_dust  
  > "Here brightness temperature of the dust emission is equated with dust physical temperature." (Bolometric Luminosity of the Compact Core in the Western Nucleus)
   - assumption: thin axisymmetric disk, two faces  
  > "where the factor of 2 before the integral is for the two faces of the disk" (Bolometric Luminosity of the Compact Core in the Western Nucleus)
   - fitting: _not stated_
   - validation: caveats and alternative cases (optically thick W1, r_maj r_min, flat-topped)  
  > "Removing the assumption, the lowest disk luminosity can be obtained by replacing $r_{\rm maj}^2$ with $r_{\rm maj}r_{\rm min}$" (Bolometric Luminosity of the Compact Core in the Western Nucleus)

## Software

- **CASA** 4.7.2: data reduction and imaging  
  > "We used CASA 4.7.2 for our data reduction (cite: CASA07)" (ALMA Data)
- **mpfit** : Levenberg-Marquardt visibility fitting in IDL  
  > "We made our non-linear visibility fitting in IDL using an implementation of the Levenberg-Marquardt algorithm called `mpfit`" (Visibility Fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| W1 major-axis FWHM (2G) | 50.0 | not stated | mas | 3 | E$_1$ and W$_1$ have major axis FWHM of 88 mas (36 pc) and 50 mas (21 pc), respectively. |
| W1 peak Tb (2G) | 640 | not stated | K | 3 | Their peak brightness temperatures are as high as 73 K in E$_1$ and 640 K in W$_1$. |
| W1 spectral index | 1.94 | ±0.16 | dimensionless | 3 | the spectral index of W$_1$, $1.94\pm0.16$ |
| Dust fraction at 3 mm, E and W | 0.13 (E), 0.41 (W) | ±0.04, ±0.05 | dimensionless | 4 | we obtain $\mbox{$f_{\rm d}$}= 0.13 \pm 0.04$ and $0.41 \pm 0.05$ for Arp 220 E and W, respectively. |
| W1' peak Tb (dust) | 529 | ±20 | K | 5 | $T_{\rm p}$= $529 \pm 20$ K |
| L_bol of W1' | 3.3e12 | ±0.8e12 | Lsun | 6 | we obtain $L_{\rm bol}$= $(3.3 \pm 0.8) \times 10^{12}$ $L_\odot$ |
| L_bol of W1 (optically thick) | 5.7e12 | ±1.2e12 | Lsun | 6 | is calculated to be $(5.7\pm1.2)\times 10^{12}$ $L_\odot$ |
| 3 mm spectral index W / E | +1.2 (W), 0.0 (E) | ±0.2 | dimensionless | 2 | of $+1.2$ for the western nucleus and $0.0$ for the eastern nucleus with uncertainties about $\pm 0.2$ |

## Qualitative findings

- Faint bipolar spurs along P.A. ~170 deg perpendicular to the W disk major axis, attributed to an outflow  
  > "the western nucleus has faint bipolar features that extend from the central region along P.A. $\sim 170$$^\circ$" (Images)

## Claim tuples

- H: Each nucleus has more than one structural component at 3 mm | E: 1G, r2G and 2G visibility fits | R: Single Gaussian is a poor fit; two concentric components fit well | F: Compact cores plus extended nuclear disks | **supported**
- H: The compact component is dust emission | E: Spectral-index decomposition and plasma subtraction using 33 GHz data | R: f_d = 13% E, 41% W; dust centrally concentrated | F: Compact cores correspond to dust | **supported**
- H: The W core luminosity source is AGN or extreme starburst | E: Luminosity surface density comparison with Seyferts and SSCs | R: ~10^15.5 Lsun/kpc^2, order of magnitude above Seyferts | F: A luminous AGN is plausible but not proven | **partially**
- H: W nucleus drives a bipolar outflow from a highly inclined disk | E: Deep continuum imaging and axial ratio inclination | R: Faint spurs perpendicular to disk; i≈60 deg | F: Outflow from inclined disk, not face-on disk | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility fitting is more direct for simple marginally resolved structure  
  > "it is far more straightforward to fit visibilities than to make a dirty image first, deconvolve it next" (Visibility Fitting)
- Alternative: Single elliptical exponential disk fits worse than r2G at 3 mm  
  > "neither nucleus is fitted by a single elliptical exponential disk" (r2G fit)
- How they decided it was enough: _not stated_
- Limitation (authors): Luminosity uncertain by at least ±0.2 dex due to assumptions (optical depth, disk geometry, Tb=Tdust)  
  > "with at least $\pm$0.2 dex uncertainty due to various assumptions" (Bolometric Luminosity of the Compact Core in the Western Nucleus)
- Caveat (inferred, ours): Dust Tb equated with physical temperature despite possible partial opacity
- Caveat (inferred, ours): Results depend on assumed alpha_d and fixed 33 GHz plasma disks
- Caveat (inferred, ours): Missing flux and calibrator model changes not fully quantified

## Reproducibility

- Data public (paper): archival data  
  > "We analyzed archival data of the ALMA project 2015.1.00113.S (P.I. Scoville)." (ALMA Data)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom IDL fitting code not released
- Missing: Channel lists and imaging parameters
- Missing: Self-cal details
- Data volume (inferred): ~100s GB raw (long-baseline, two tunings, 37 antennas)
- Score (inferred): 3/5, Public data and well-described fitting models with tables, but custom code, channel lists and imaging details are missing.
- Rediscovery candidate: yes, Public data, numeric results, and recipe mostly clear, though some settings are missing.

## Links

- Method: (cite: Barcos-Munoz15) (33 GHz exponential-disk plasma models)
- Method: (cite: Scoville17) (earlier analysis of same dataset)
- Companion: Sakamoto et al. in prep. (1 and 0.8 mm structural fits of Arp 220)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 50,
  "rate": 0.641
 },
 "evidence_ok": true
}
```
