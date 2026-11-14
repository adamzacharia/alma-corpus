# Investigating the gas-to-dust ratio in the protoplanetary disk of HD 142527

`2019PASJ...71..124S` | Publications of the Astronomical Society of Japan 2019 | first author: Soon, Kang-Lou | arXiv: 1909.06745 | DOI: 10.1093/pasj/psz112

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How do the gas and dust surface densities, gas-to-dust ratio and dust opacity index vary across the asymmetric outer disk of HD 142527?  
  > "Herein, we extend on previous studies by deriving the spatial distribution of the gas-to-dust ratio across the outer disk of HD 142527." (Introduction)
- Target **HD 142527**: coordinates _not stated_; z/distance 157 pc ± 1 pc  
  > "The distance to HD 142527 derived by (cite: arun2019) based on the *Gaia* observations (cite: gaia2016a; gaia2016b) is $157~\mathrm{pc}\pm1~\mathrm{pc}$." (Introduction); distance from Arun et al. 2019, from Gaia  
  > "The distance to HD 142527 derived by (cite: arun2019) based on the *Gaia* observations (cite: gaia2016a; gaia2016b) is $157~\mathrm{pc}\pm1~\mathrm{pc}$." (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (Cycle 2) and Band 7 (Cycle 0)  
  > "We used the ALMA Cycle 2 Band 3[^1] and Cycle 0 Band 7[^2] observational data of HD 142527" (2 Observations and data reduction)
- frequencies and spectral setup: Two continuum SPWs at 97.50 and 99.50 GHz (1.875 GHz each); line SPWs at 109.78 and 110.19 GHz, 3840 channels, 15.259 kHz  
  > "Two spectral windows were optimally configured for the continuum observation with frequencies centered at $97.50~\mathrm{GHz}$ and $99.50~\mathrm{GHz}$, and both had an effective bandwidth of $1.875~\mathrm{GHz}$." (2.1 ALMA band 3 data)
- continuum bandwidth: 4 GHz centered at 98.5 GHz  
  > "combined the two wide band spectral windows to obtain a continuum centered at $98.5~\mathrm{GHz}$ with a total bandwidth of $4~\mathrm{GHz}$" (2.1 ALMA band 3 data)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 25.05 m to 1566.19 m, 37-40 12 m antennas  
  > "thereby forming a range of baselines between $25.05~\mathrm{m}$ and $1566.19~\mathrm{m}$" (2.1 ALMA band 3 data)
- angular resolution: 0.54'' x 0.44'', P.A. 78.1 deg (Band 3; Band 7 smoothed to match)  
  > "The synthesized beam in full width at half maximum (FWHM) of the final image is $\timeform{0.54''}\times\timeform{0.44''}$, oriented along $\mathrm{P.A.}=  78.1^\circ$." (2.1 ALMA band 3 data)
- max recoverable scale: _not stated_
- sensitivity: Band 3 continuum 9.6 uJy/beam; Band 7 continuum 150 uJy/beam  
  > "a root mean square noise level of $\sigma = 9.6~\mu\mathrm{Jy~beam^{-1}}$ is reached" (2.1 ALMA band 3 data)
- time on source: 2.94 hours (Band 3)  
  > "the total on-source integration time was $2.94$ hours" (2.1 ALMA band 3 data)
- observing dates: 4, 5 and 15 July 2015 (Band 3)  
  > "carried out on the nights of the 4th, 5th, and 15th July 2015" (2.1 ALMA band 3 data)
- pi or archival as stated: _not stated_
- Line: 13CO J=1-0 (not stated)
- Line: C18O J=1-0 (not stated)
- Line: 13CO and C18O J=3-2 (Band 7) (not stated)
- Other facility **ATCA**: 86.3 GHz integrated flux of 47.1 mJy used for flux-recovery check (from Verhoeff et al. 2011)  
  > "the integrated flux at $86.3~\mathrm{GHz}$ (equivalent wavelength $3.476~\mathrm{mm}$) obtained with the Australia Telescope Compact Array (ATCA)" (3.1 98.5 GHz continuum emission)
- External data: Calibrated Band 7 continuum and 13CO/C18O J=3-2 images  
  > "we use the calibrated images of the $336~\mathrm{GHz}$ continuum and the $^{13}$CO $J=3-2$ and C$^{18}$O $J=3-2$ lines produced by (cite: muto2015)" (2.2 ALMA band 7 data) [from (cite: muto2015)]
- External data: Interstellar abundance chi(C18O/H2)=1.79e-7 and 13CO/C18O ratio 8.1  
  > "by assuming the interstellar abundance $\chi(\mathrm{C^{18}O/H_2}) = 1.79 \times 10^{-7}$ (cite: wilson1999)" (4.2 Derivation of gas surface density) [from (cite: wilson1999)]
- External data: Boehler et al. disk model surface densities used for comparison  
  > "the peak dust surface densities are $0.65~\mathrm{g~cm^{-2}}$ in the north sector and $0.012~\mathrm{g~cm^{-2}}$ in the south sector" (4.1 Derivation of dust surface density) [from (cite: boehler2017)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline for Band 3 calibration  
  > "We used CASA pipeline version 4.3.1 to perform the data reduction and calibration" (2.1 ALMA band 3 data)
- casa version: CASA 5.1.0 (imaging)  
  > "We used CASA version 5.1.0 to image the calibrated visibility" (2.1 ALMA band 3 data)
- pipeline version: CASA pipeline 4.3.1  
  > "We used CASA pipeline version 4.3.1 to perform the data reduction and calibration" (2.1 ALMA band 3 data)
- archive products used as is: _not stated_
- flux calibrator: Ceres, Pallas, Titan or J1427-4206 depending on block  
  > "the absolute flux calibrator was either Ceres, Pallas, Titan, or J1427$-$4206" (2.1 ALMA band 3 data)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal with solints scan length (2-7 min), 240 s, 120 s, 60 s, then one amplitude self-cal at scan length  
  > "followed by shorter time intervals in the order of $240~\mathrm{s}$, $120~\mathrm{s}$, and $60~\mathrm{s}$." (2.1 ALMA band 3 data)

### Imaging

- task: _not stated_
- deconvolver: multi-scale CLEAN, scales 0, 1, 2 times average beam size  
  > "deconvolution scale parameters of $0$ (corresponding to a point source), $1$, and $2$ times the average beam size" (2.1 ALMA band 3 data)
- weighting robust: Briggs, robust = 0.5  
  > "multi-scale CLEAN algorithm with Briggs weighting (robust parameter $0.5$)" (2.1 ALMA band 3 data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask (M*=2.4 Msun, i=27 deg) plus 3.5 sigma clip for moment maps  
  > "We adopt a stellar mass of $M_* = 2.4~M_\odot$ and a disk inclination of $i = 27^\circ$ when creating the Keplerian mask." (Channel maps)
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels of the line SPW  
  > "the continuum level is estimated from the line free channels of the spectral window containing the $^{13}$CO line emission" (3.2 13CO J=1-0 line emission)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channels smoothed to 0.30 km/s (and 0.12 km/s cube); imsmooth to common beam  
  > "We then smoothed the frequency channels to an equivalent velocity resolution of $0.30~\mathrm{km~s^{-1}}$." (2.1 ALMA band 3 data)
- final beam: 0.54'' x 0.44'', P.A. 78.1 deg  
  > "i.e., $\timeform{0.54''}\times\timeform{0.44''}$ ($\mathrm{P.A.}=  78.1^\circ$)" (2.1 ALMA band 3 data)
- final rms: continuum 9.6 uJy/beam; 0.30 km/s cube 2.0 mJy/beam; 0.12 km/s cube 2.9 mJy/beam  
  > "The noise level is $\sigma = 2.0~\mathrm{mJy~beam^{-1}}$." (2.1 ALMA band 3 data)

### Inherited from earlier work

- Band 7 observational setup and calibration  
  > "The observational setup and calibration process of the Band 7 data are described in detail by (cite: fukagawa2013) and (cite: muto2015)." (2.2 ALMA band 7 data) [from (cite: fukagawa2013); (cite: muto2015)]
- Canonical dust opacity law  
  > "we adopt the canonical dust opacity (per dust mass) $\kappa_\mathrm{d}$ described by (cite: beckwith1990)" (4.1 Derivation of dust surface density) [from (cite: beckwith1990)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Image size, cell size and CLEAN thresholds/masks
- Exact number of CLEAN iterations and self-cal gain tables per solint
- Method and fitting details for the power-law exponent p (fit type, errors)
- Exact Keplerian-mask line widths
- Which execution blocks were discarded
- Molecular constants (dipole moment, B0) used for N_tot
- Band 7 beam/properties before smoothing

## Analysis recipe

1. **Image Band 3 continuum and lines and match resolution**: Multiscale CLEAN, self-calibration, then imsmooth of all images to a common beam  
  > "we applied a CASA task *imsmooth* to smooth the image cubes of $^{13}$CO and C$^{18}$O so that they had the same angular resolution in the $98.5~\mathrm{GHz}$ continuum image" (2.1 ALMA band 3 data)
   - software: CASA
   - parameter: Briggs robust 0.5; 0.30 km/s channels  
  > "multi-scale CLEAN algorithm with Briggs weighting (robust parameter $0.5$)" (2.1 ALMA band 3 data)
   - fitting: _not stated_
   - validation: Integrated 98.5 GHz flux extrapolated to 86.3 GHz compared with ATCA, indicating all flux recovered  
  > "indicating that the ALMA observation recovers all the flux" (3.1 98.5 GHz continuum emission)
2. **Determine disk temperature**: Use peak brightness temperature of 13CO J=3-2 including continuum, masking region with T_B<30 K  
  > "we mask out the inner region in which the brightness temperature is less than $30~\mathrm{K}$" (4 Analyses)
   - assumption: Td=Tg, LTE, vertically isothermal, well-mixed gas and dust  
  > "We assume the physical temperatures of the gas and dust, $T_\mathrm{d}$ and $T_\mathrm{g}$, to be identical." (4 Analyses)
   - fitting: _not stated_
   - validation: Alternative Td = 80% Tg two-layer model tested  
  > "To evaluate the uncertainties of $\mathrm{G/D}$ and the exponent $p$, we here adopt a two-layer disk model" (Two-layer disk model)
3. **Derive dust optical depth, beta and dust surface density**: Solve radiative transfer for tau_d at 98.5 and 336 GHz; beta from tau ratio; Sigma_d = tau_d/kappa_d  
  > "The dust surface density is derived from $\Sigma_\mathrm{d} = \tau_\mathrm{d}/\kappa_\mathrm{d}$" (4.1 Derivation of dust surface density)
   - parameter: kappa_d = 10 (nu/1e12 Hz)^beta cm2/g  
  > "\kappa_\mathrm{d} = 10 \left(  \frac{\nu}{10^{12}~\mathrm{Hz}}    \right) ^\beta \quad \mathrm{cm^2~g^{-1}}" (4.1 Derivation of dust surface density)
   - assumption: Dust scattering ignored  
  > "Dust scattering can strongly depend on the dust compositions and structures (cite: tazaki2016; tazaki2018), but we have ignored it in this study." (4.1 Derivation of dust surface density)
   - fitting: _not stated_
   - validation: Compared with Boehler et al. 2017 convolved model; mock 700 GHz image compared with Casassus et al. 2015  
  > "This comparison shows that the disk parameters estimated from Bands 3 and 7 are reasonable." (Mock-up dust continuum image at 700 GHz)
4. **Derive gas surface density from C18O**: Line radiative transfer with dust absorption, column density from tau_g, Sigma_g = m_H2 N_tot / chi; J=3-2 used at PA 180-240  
  > "The gas surface density is then calculated by $\Sigma_\mathrm{g} = m_\mathrm{H_2} N_\mathrm{tot} / \chi$" (4.2 Derivation of gas surface density)
   - assumption: Interstellar abundance chi(C18O/H2)=1.79e-7; Tex=Tg  
  > "The excitation temperature $T_\mathrm{ex}$ is equal to $T_\mathrm{g}$ in the LTE analysis." (4.2 Derivation of gas surface density)
   - fitting: _not stated_
   - validation: J=1-0 and J=3-2 derived Sigma_g differ by <10% at PA 180 and 240; comparison with Boehler et al.  
  > "differs by less than $10\%$, indicating a smooth variation of $\Sigma_\mathrm{g}$ derived from the two lines" (4.2 Derivation of gas surface density)
5. **Compute G/D and Sigma_g-Sigma_d relation**: G/D = Sigma_g/Sigma_d; power-law fit of Sigma_g vs Sigma_d on dust ridge  
  > "The plot can be fitted by a power law for which the exponent $p$ (indicated in the top left corner of the plots) is $p = 0.47$." (5.1 G/D and correlation between gas and dust surface densities)
   - fitting: _not stated_
   - validation: Two-layer model gives p=0.44  
  > "we find a power law with an exponent $p = 0.44$ to be a good fit to the results" (Two-layer disk model)

## Software

- **CASA** pipeline 4.3.1 (calibration); 5.1.0 (imaging): Calibration, imaging, self-calibration, imsmooth  
  > "We used CASA version 5.1.0 to image the calibrated visibility" (2.1 ALMA band 3 data)
- **imsmooth** : Smoothing images to common beam  
  > "we applied *imsmooth* to the Band 7 images to obtain a spatial resolution identical to that of the Band 3 images" (2.2 ALMA band 7 data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 98.5 GHz peak continuum S/N | 240 | not stated | dimensionless | 1 | The signal-to-noise ratio of the peak continuum flux at $98.5~\mathrm{GHz}$ is $240$. |
| Integrated flux at 98.5 GHz (>5 sigma) | 72.1 | not stated | mJy | 1 | is $72.1~\mathrm{mJy}$ |
| 98.5 GHz ridge contrast (max/min) | 58.2 | not stated | dimensionless | 1 | Contrast $\equiv \mathrm{Max/Min}$ /   / $58.2$ |
| Spectral index alpha north / south | 2.8 / 3.4 | not stated | dimensionless | 1 | in the northern region $\alpha \approx 2.8$, while in the southern region $\alpha \approx 3.4$ |
| Peak dust tau at 98.5 GHz / 336 GHz | 0.24 / 0.82 | not stated | dimensionless | 3 | The peak $\tau_\mathrm{d}$ at $98.5~\mathrm{GHz}$ is $0.24$ |
| beta north / south | ~1 / ~1.7 | not stated | dimensionless | 3 | in the southern region, $\beta$ is close to the interstellar value of $1.7$ (cite: planck2014), while in the northern region, it is $\approx1$ |
| Sigma_d max / min along ridge | 3.08e-1 / 9.14e-3 | not stated | g cm^-2 | 3 | $\Sigma_\mathrm{d} = 3.08 \times 10^{-1}~\mathrm{g~cm^{-2}}$ |
| Sigma_g max / min along ridge | 9.14e-1 / 1.75e-1 | not stated | g cm^-2 | 4 | $\Sigma_\mathrm{g} = 9.14\times10^{-1}~\mathrm{g~cm^{-2}}$ |
| N_tot(13CO)/N_tot(C18O) in PA 200-240 | 9.99 | 1.67 | dimensionless | 4 | The ratio $N_\mathrm{tot} (^{13}\mathrm{CO})/N_\mathrm{tot} (\mathrm{C^{18}O})$ is derived to be $9.99 \pm 1.67$ |
| G/D north / south | ~3 / ~20 | not stated | dimensionless | 5 | The estimated $\mathrm{G/D}$ is $\sim 3$ and $\sim 20$ in the northern and southern regions, respectively |
| Exponent p in Sigma_g ∝ Sigma_d^p | 0.47 | not stated | dimensionless | 5 | G/D varies approximately with $\propto \Sigma_\mathrm{d}^{-0.53}$ |
| Dust grain size at Sigma_d peak | >~5 | not stated | mm | 5 | $s \gtrsim 5~\mathrm{mm}$ if $\mathrm{St} \gtrsim 1$ |

## Qualitative findings

- Peak Sigma_d (PA~315 deg) lies downstream (ahead) of peak Sigma_g (PA~3 deg), consistent with dust trapped ahead of a vortex  
  > "the peak $\Sigma_\mathrm{d}$ is located at $\mathrm{P.A.} \approx 315^\circ$, which is downstream of the peak $\Sigma_\mathrm{g}$ located at $\mathrm{P.A.} \approx 3^\circ$" (5.2 Relative spatial distribution of gas and dust surface densities)

## Claim tuples

- H: Does G/D vary azimuthally in the HD 142527 outer disk? | E: Derived Sigma_g (C18O) and Sigma_d (Bands 3 and 7) maps | R: G/D ~3 north to ~20 south, with G/D ∝ Sigma_d^-0.53 | F: G/D varies smoothly in azimuth, consistent with dust concentration in the north | **supported**
- H: Does dust size differ between north and south? | E: beta from Band 3 and 7 optical depths | R: beta ≈ 1 north, ≈ 1.7 south | F: Larger grains accumulate in the higher-pressure northern region | **supported**
- H: Is dust trapped ahead of a gas vortex? | E: Compared polar distributions of Sigma_g and Sigma_d | R: Sigma_d peak ahead of Sigma_g peak | F: Consistent with predictions if the gas peak is a vortex | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: LTE with the 13CO J=3-2 peak T_B as disk temperature  
  > "These temperatures are taken from the peak $T_\mathrm{B}$ of $^{13}$CO $J=3-2$ including the continuum emission" (4 Analyses)
- Alternative: Two-layer model with Td=80% Tg gives consistent p (0.44)  
  > "The derived value of exponent $p$ is consistent with that of the one-layer disk model" (Two-layer disk model)
- How they decided it was enough: _not stated_
- Limitation (authors): CO abundance uncertain (depletion, photodissociation); Sigma_g, G/D and grain size may be underestimated  
  > "though $\Sigma_\mathrm{g}$, $\mathrm{G/D}$, and the dust size estimated from equation ([\[eq:stokes\]](#eq:stokes)) may be underestimated" (5.3 Effects of uncertainties in CO abundance)
- Limitation (authors): Dust opacity highly uncertain; scattering ignored  
  > "The dust opacity is highly uncertain and depends on the particle compositions, structures, as well as size distributions" (4.1 Derivation of dust surface density)
- Caveat (inferred, ours): Single assumed opacity law and neglect of scattering strongly affect Sigma_d in optically thick north
- Caveat (inferred, ours): Temperature taken from 13CO peak T_B may not trace dust temperature
- Caveat (inferred, ours): Resolution of ~0.5'' only marginally resolves ring
- Caveat (inferred, ours): Power-law fit has no stated uncertainty

## Reproducibility

- Data public (paper): ALMA project codes cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00318S and ADS/JAO.ALMA#2013.1.00670S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channels, image/cell sizes, CLEAN thresholds
- Missing: Fit procedure and uncertainty for p
- Missing: Band 7 calibrated images from Muto et al. 2015 need to be re-made
- Data volume (inferred): ~200-500 GB for Band 3 and Band 7 raw data
- Score (inferred): 3/5, Data public and equations given, but imaging details and fitting procedure incomplete.
- Rediscovery candidate: no, Recipe lacks some imaging and fitting details, and depends on Band 7 products from earlier work.

## Links

- Method: (cite: muto2015) (Band 7 calibrated images and disk models)
- Method: (cite: beckwith1990) (dust opacity law)
- Companion: (cite: boehler2017) (previous gas and dust surface density modeling for comparison)
- Companion: (cite: fukagawa2013) (Band 7 observations)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00318.S",
  "2013.1.00670.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 52,
  "rate": 0.693
 },
 "evidence_ok": true
}
```
