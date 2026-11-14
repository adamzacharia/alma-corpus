# ALMA Detection of a Linearly Polarized Reverse Shock in GRB 190114C

`2019ApJ...878L..26L` | The Astrophysical Journal Letters 2019 | first author: Laskar, Tanmoy | arXiv: 1904.07261 | DOI: 10.3847/2041-8213/ab2247

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: transients
- Question: Is the mm-band afterglow of GRB 190114C linearly polarized, and what does its polarization and temporal evolution imply about the reverse shock and jet magnetic field structure?  
  > "By combining the radio, millimeter, optical, and X-ray observations, we demonstrate that the mm-band flux is dominated by a reverse shock, which allows us to constrain the magnetic field geometry in the outflow powering this burst." (Introduction)
- Target **GRB 190114C**: coordinates _not stated_; z/distance z = 0.4245  
  > "GRB 190114C was discovered by the Burst Alert Telescope (cite: bbc+05) on the *Neil Gehrels Swift Observatory* (cite: gcg+04) on 2019 January 14 at 20:57:03 UT (cite: gcn23688)." (2.1 Gamma-ray, X-ray, and optical); "which was further refined with X-shooter spectroscopy at the European Southern Observatory’s Very Large Telescope to $z=0.4245$ (cite: gcn23710)." (2.1 Gamma-ray, X-ray, and optical); distance from X-shooter/VLT spectroscopy (GCN 23710)  
  > "GRB 190114C was discovered by the Burst Alert Telescope (cite: bbc+05) on the *Neil Gehrels Swift Observatory* (cite: gcg+04) on 2019 January 14 at 20:57:03 UT (cite: gcn23688)." (2.1 Gamma-ray, X-ray, and optical); "which was further refined with X-shooter spectroscopy at the European Southern Observatory’s Very Large Telescope to $z=0.4245$ (cite: gcn23710)." (2.1 Gamma-ray, X-ray, and optical)

## Data provenance

- ALMA projects: 2018.1.01405.T
- bands: Band 3 (97.5 GHz), full linear polarization  
  > "in full linear polarization mode in Band 3, with two 4 GHz-wide base-bands centered at 91.5 and 103.5 GHz, respectively." (2.3 ALMA polarization observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: two 4 GHz-wide base-bands at 91.5 and 103.5 GHz  
  > "two 4 GHz-wide base-bands centered at 91.5 and 103.5 GHz, respectively" (2.3 ALMA polarization observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: rms ≈10 µJy in Stokes QUV images  
  > "The rms noise level in the Stokes $QUV$ images is $\approx10\,\mu$Jy." (2.3.2 Measurement of polarization)
- time on source: 10.5 minutes on source per ≈12 minute cycle; 3 hours total, scheduling block repeated three times  
  > "with 10.5 minutes on source, 30 seconds on the gain calibrator, and the remaining time used for slewing between the two." (2.3 ALMA polarization observations)
- observing dates: starting 2.2 hours after the burst (burst on 2019 Jan 14)  
  > "beginning 2.2 hours after the burst through program 2018.1.01405.T" (2.3 ALMA polarization observations)
- pi or archival as stated: PI program (PI: Laskar)  
  > "through program 2018.1.01405.T (PI: Laskar)" (2.3 ALMA polarization observations)
- Other facility **VLA**: 5–38 GHz Stokes I observations at 4.7–6.3 hr (program 18A-088)  
  > "In our first epoch, we obtained a full sequence of observations spanning 5–38 GHz." (2.2 Radio: VLA)
- Other facility **Swift XRT/UVOT**: X-ray light curve and UVOT photometry  
  > "We performed photometry on the UVOT data at $6\times10^{-3}$ days with a 3.5$''$ aperture" (2.1 Gamma-ray, X-ray, and optical)
- Other facility **GCN circulars (NOT, GROND, MASTER)**: optical/NIR afterglow points  
  > "We further include observations of the afterglow reported in GCN circulars, in particular, the NOT observations at $2\times10^{-2}$ days" (2.1 Gamma-ray, X-ray, and optical)
- External data: J0423-012 flux densities of 4.15±0.08 mJy (91.5 GHz) and 3.89±0.06 mJy (103.5 GHz) from ALMA calibrator catalog  
  > "We used flux density values of $(4.15\pm0.08)$ mJy at 91.5 GHz and $(3.89\pm0.06)$ mJy at 103.5 GHz for J0423-012 from the ALMA calibrator catalog" (2.3.1 ALMA Data analysis) [from ALMA calibrator catalog]
- External data: optical and NIR GROND and NOT observations from GCN circulars  
  > "the GROND observations at $\approx0.16$ days (cite: gcn23702)" (2.1 Gamma-ray, X-ray, and optical) [from (cite: gcn23702); (cite: gcn23695)]

## Processing

### Calibration

- pipeline or manual: manual CASA polarization calibration following standard techniques  
  > "We processed the ALMA data using CASA (cite: mws+07), employing standard techniques (cite: nnp+16)." (2.3.1 ALMA Data analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-012 (flux, bandpass, polarization leakage); J0348-274 gain calibrator  
  > "employing J0423-012 as flux density, bandpass, and polarization leakage calibrator, and J0348-274 as complex gain calibrator." (2.3 ALMA polarization observations)
- flux scale uncertainty: calibrator flux uncertainty ~2% (0.08/4.15 mJy)  
  > "$(4.15\pm0.08)$ mJy at 91.5 GHz and $(3.89\pm0.06)$ mJy at 103.5 GHz" (2.3.1 ALMA Data analysis)
- self calibration: _not stated_

### Imaging

- task: Stokes IQUV and P images; imfit for image-plane flux fits  
  > "We fit for the flux density of the source in the image plane using `imfit`." (2.3.1 ALMA Data analysis)
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

- ALMA polarization calibration procedure  
  > "employing standard techniques (cite: nnp+16)" (2.3.1 ALMA Data analysis) [from Nagai et al. 2016 (cite: nnp+16)]
- RS light curve evolution and SED shape  
  > "using the RS light curve evolution from (cite: zwd05) and the SED shape from (cite: lbz+13)" (4.2 Radio and millimeter: RS) [from (cite: zwd05); (cite: lbz+13)]
- full multiwavelength modeling deferred  
  > "we defer a discussion of the full multi-wavelength modeling to a future work (T. Laskar et al. in preparation)" (3 Basic considerations) [from T. Laskar et al. in preparation]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, cell, image size, masking) for the Stokes images
- CASA version
- Whether archive pipeline products or manual calibration were used as the base
- Time-binning of scans for the Stokes I light curve
- Forward-shock model fitting method and priors; how parameters were chosen
- Flagging details
- Polarization calibrator solution settings (solints)

## Analysis recipe

1. **Polarization calibration of ALMA data**: Standard CASA full-polarization calibration using J0423-012 for leakage with ≈90° parallactic angle coverage  
  > "We used these solutions to estimate the intrinsic Stokes parameters of the polarization calibrator, followed by the cross-hand delays, the XY-phase offset, and the calibrator’s intrinsic polarization." (2.3.1 ALMA Data analysis)
   - software: CASA
   - parameter: flux scale from power-law fit to calibrator catalog flux at 91.5 and 103.5 GHz  
  > "to which we fit a power law model to fix the flux density scale for each channel" (2.3.1 ALMA Data analysis)
   - fitting: _not stated_
   - validation: XX/YY gain ratio within ≈2% of unity; D-terms ≈1%  
  > "The leakage (D-terms) were found to be at the $\approx1\%$ level for individual antennas, as expected for the ALMA 12m array (cite: nnp+16)." (2.3.1 ALMA Data analysis)
2. **Measure Stokes I light curve and Q, U**: Split source data by scan, imfit in image plane for Stokes I; Q and U measured with position and beam fixed from Stokes I image, per run  
  > "measured by fixing the position and beam parameters using the Stokes $I$ image" (2.3.2 Measurement of polarization)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive P, chi, Pi with debiasing**: Monte Carlo with 10^5 realizations from Q and U measurements, including Stokes I uncertainty for Pi  
  > "We generate $10^5$ random realizations from the individual $Q$ and $U$ measurements and calculate $P=\sqrt{Q^2+U^2}$" (2.3.2 Measurement of polarization)
   - fitting: _not stated_
   - validation: Checked via gain calibrator polarization stability, secondary peaks, separate base-bands, and independent ALMA reduction  
  > "All three sets of images yield results consistent within measurement uncertainty." (2.3.2 Measurement of polarization)
4. **Broadband SED and forward/reverse shock decomposition**: Optical/X-ray spectral and temporal indices compared with synchrotron closure relations; radio/mm SED fit with broken power law; RS propagated back to match optical  
  > "can be fit with a broken power law model, transitioning from $\beta=2$ (fixed) to $\beta=0.3\pm0.2$ at $\nu_{\rm break}=24\pm4$ GHz." (4.2 Radio and millimeter: RS)
   - assumption: Omega_m=0.31, Omega_Lambda=0.69, H0=68 km/s/Mpc  
  > "We assume $\Omega_m=0.31$, $\Omega_{\lambda}=0.69$, and $H_0=68$ km s$^{-1}$ Mpc$^{-1}$." (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Constrain magnetic field coherence angle**: Random-walk of N incoherent patches with N~(Gamma_ej theta_B)^-2; Pi ~ Pi_0 Gamma_ej theta_B  
  > "The observed polarization is a random walk of $N$ steps in the $QU$ plane, with $\Pi \sim \Pi_0/\sqrt{N} \sim \Pi_0\Gamma_{\rm ej}\theta_B$" (5 Discussion)
   - parameter: Gamma_ej ≈15, Pi_0 ~0.6 (beta~0), t_dec ≈ T90 = 116 s  
  > "Taking $\ensuremath{t_{\rm dec}}\approx T_{90}=116$ s from *Fermi*/GBM[^9]" (5 Discussion)
   - assumption: Newtonian RS with g≈3, k=2  
  > "For $g\approx3$ and $k=2$, we have" (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA and VLA data reduction and imaging  
  > "We processed the ALMA data using CASA (cite: mws+07)" (2.3.1 ALMA Data analysis)
- **pwkit** : VLA data reduction  
  > "We carried out data reduction with CASA (cite: mws+07) using the `pwkit` package (cite: wcnr17)." (2.2 Radio: VLA)
- **imfit** : image-plane flux density fitting  
  > "We fit for the flux density of the source in the image plane using `imfit`." (2.3.1 ALMA Data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fractional linear polarization, first epoch | 0.87 | 0.13 | % | 3 | / 0.114 / 89.5 / 14.6 / 32.0 / 15.3 / 96.3 / 14.6 / 9.8 / 4.6 / 0.87 / 0.13 / |
| Fractional linear polarization, last epoch | 0.60 | 0.19 | % | 3 | / 0.202 / 1.84 / 14.5 / -41.1 / 14.6 / 43.7 / 14.0 / -43.7 / 11.7 / 0.60 / 0.19 / |
| Polarization position angle, first to last | 10 to -44 | ±5 to ±12 | deg | 3 | evolving in polarization position angle from $(10\pm5)^\circ$ to $(-44\pm12)^\circ$ |
| Circular polarization limit | <0.3 (statistical); systematic ≈0.6 | 3 sigma | % | 2 | corresponding to a formal $3\sigma$ limit on circular polarization of $\Pi_{\rm V} < 0.3\%$ (statistical only) |
| Radio SED break frequency | 24 | ±4 | GHz | 4 | $\nu_{\rm break}=24\pm4$ GHz |
| Magnetic coherence angle theta_B | ≈1e-3 | ≈15% statistical | radian | 5 | The uncertainty on this estimate from the signal-to-noise of the measurement of $\Pi$ is $\approx15\%$ |
| Mean intra-band Stokes I spectral index | ≈-0.4 | not stated | dimensionless | 4 | the mean Stokes $I$ intra-band spectral index between the two ALMA base-bands at 91.5 GHz and 103.5 GHz is $\approx-0.4$ |

## Qualitative findings

- Optical and X-ray at 0.03–0.3 d consistent with fast-cooling forward shock in a wind; radio/mm and early optical from a separate reverse-shock component  
  > "the optical observations at $\lesssim0.03$ days, as well as the radio and millimeter observations, arise from a separate component" (abstract)

## Claim tuples

- H: Is the mm-band afterglow of a GRB linearly polarized? | E: ALMA Band 3 full-polarization observations over 2.2–5.2 hr, Monte Carlo of Q,U | R: Pi=0.87±0.13% falling to 0.60±0.19%, ≈5σ | F: First detection of polarized radio/mm GRB emission with temporal evolution | **supported**
- H: Is the radio/mm emission reverse-shock dominated? | E: SED and light-curve decomposition with optical/X-ray | R: mm emission shallow relative to optical extrapolation; separate component | F: mm band arises from reverse-shocked ejecta | **supported**
- H: What is the jet magnetic field structure? | E: Compare Pi and chi evolution to ordered/patchy field models | R: Low Pi and rotating chi; theta_B≈1e-3 rad | F: Rules out large-scale axisymmetric fields such as global toroidal; tangled fields of small coherence scale | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: P images are biased for faint sources, so P measured from Q and U via Monte Carlo  
  > "As images of $P$ are biased for faint sources, we do not measure $P$ from images of polarized intensity" (2.3.2 Measurement of polarization)
- Alternative: Superposition of ordered and random field components disfavored because the chi change requires comparable polarized intensities with a ratio varying on dynamical time  
  > "and thus such scenarios are disfavored." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Systematic uncertainties from RS dynamics approximations and stochastic random walk; forward-shock parameters degenerate since nu_a not located  
  > "larger systematic uncertainties arise from the approximations used in the RS dynamics as well as the stochastic nature of the 2D random walk." (5 Discussion)
- Caveat (inferred, ours): Only ~5σ polarization detection from a single ALMA epoch with 3 time bins
- Caveat (inferred, ours): theta_B estimate relies on approximate RS dynamics
- Caveat (inferred, ours): Forward-shock model parameters (eps_e≈0.9) are degenerate
- Caveat (inferred, ours): Polarization calibration at sub-percent level is demanding

## Reproducibility

- Data public (paper): ADS/JAO.ALMA#2018.1.01405.T cited; public availability not explicitly stated  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01405.T." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: scan binning for light curve
- Missing: forward/reverse shock model fitting details
- Data volume (inferred): ~50-200 GB raw (Band 3 full-polarization, 3 hr)
- Score (inferred): 3/5, Polarization calibration and Monte Carlo are described and tabulated, but imaging parameters and modeling details are missing.
- Rediscovery candidate: no, Data public after proprietary period probably, but the TOO polarization calibration is intricate and recipe lacks imaging details.

## Links

- Method: Nagai et al. 2016 (cite: nnp+16) (ALMA polarization calibration)
- Companion: T. Laskar et al. in preparation (full multi-wavelength modeling)
- Companion: Laskar et al. 2013 (cite: lbz+13) (GRB 130427A RS SED shape)
- Related: VLA program 18A-088

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 40,
  "rate": 0.526
 },
 "evidence_ok": true
}
```
