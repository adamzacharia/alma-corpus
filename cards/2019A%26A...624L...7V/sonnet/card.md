# Stringent limits on the magnetic field strength in the disc of TW Hya. ALMA observations of CN polarisation

`2019A&A...624L...7V` | Astronomy and Astrophysics 2019 | first author: Vlemmings, W. H. T. | arXiv: 1904.01632 | DOI: 10.1051/0004-6361/201935459

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What limits can CN (N=2-1) circular polarisation (Zeeman effect) place on the magnetic field strength in the TW Hya disc?  
  > "One of the best probes of disc magnetic fields is the CN radical, which is very sensitive to the Zeeman effect." (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 60 pc  
  > "TW Hya, at $d = 60$ pc (cite: Gaia18), is a star of type K7 with an age of $\sim8-10$ Myr." (TW Hya); distance from Gaia Collaboration 2018 (Gaia18)  
  > "TW Hya, at $d = 60$ pc (cite: Gaia18), is a star of type K7 with an age of $\sim8-10$ Myr." (TW Hya)

## Data provenance

- ALMA projects: 2018.1.00167.S
- bands: Band 6 (CN N=2-1 near 226 GHz)  
  > "produce a linear polarisation image of the dust continuum emission at 226 GHz" (Results)
- frequencies and spectral setup: three 58.59 MHz spws with 1920 channels covering 11 CN N=2-1 hyperfine components (0.093 km/s after Hanning smoothing); fourth 1.875 GHz spw with 1920 channels (~3 km/s) for calibration  
  > "we tuned three spectral windows (spws) with a width of $58.59$ MHz and $1920$ channels to cover 11 CN $(N=2-1)$ hyperfine components" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.44x0.52 arcsec  
  > "The resulting beam size was $0.44\times0.52\ensuremath{''}$." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: channel rms 1.3 mJy/beam in narrow spws; continuum sigma (I,Q,U,V) = (46,22,22,23) uJy/beam  
  > "We reach a channel rms in the narrow spws of $\sigma=1.3$ mJy beam$^{-1}$ for all four Stokes parameters I, Q, U, and V." (2 Observations and data reduction)
- time on source: 8.8 hr total in full polarisation mode, ~3.6 hr on TW Hya  
  > "The total observing time in full polarisation mode was $8.8$ hr, of which $\sim3.6$ hr were spent on TW Hya." (2 Observations and data reduction)
- observing dates: 2018 December 11, 12, and 13  
  > "on 2018 December 11, 12, and 13" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CN N=2-1 hyperfine components (11 observed) (226.33-226.89 GHz)
- External data: CN emission model (ring, emitting height) used to estimate scale height ~18 au at 42 au  
  > "According to the model of CN emission from (cite: Cazzoletti18), at this radius, we are most sensitive to the magnetic field at a disc scale height of $|z|\sim18$ au." (Discussion and conclusions) [from Cazzoletti18]
- External data: Disc model for plasma beta  
  > "$\beta\gtrsim4\times10^3$ when we adopt the disc model used in (cite: Bai15)" (Discussion and conclusions) [from Bai15]
- External data: CN molecular constants for Zeeman calculation  
  > "using the molecular constants of (cite: dixon:77)" (Zeeman-splitting coefficients of CN) [from dixon:77]

## Processing

### Calibration

- pipeline or manual: standard ALMA polarisation calibration scripts  
  > "The initial calibration was performed using the standard ALMA polarisation calibration scripts in CASA 5.4.0." (2 Observations and data reduction)
- casa version: CASA 5.4.0  
  > "The initial calibration was performed using the standard ALMA polarisation calibration scripts in CASA 5.4.0." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449 (bandpass, flux); assumed 0.72 Jy at 226.64 GHz, spectral index -0.8; J1037-2934 gain; J1256-0547 polarisation  
  > "which was assumed to have a constant flux of 0.72 Jy at $226.64$ GHz with a spectral index of $-0.8$" (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: two rounds phase and one round amplitude self-cal on continuum in the 1.875 GHz spw (lines flagged), applied to all spws; I S/N ~400 to ~2000  
  > "we performed two rounds of phase and one round of amplitude self-calibration using the continuum dust emission of TW Hya in the 1.875 GHz spectral window" (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting and a robust parameter of $0.5$" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted using the broad spw, extrapolated to narrow spws  
  > "Subsequently, the continuum was subtracted using the broad spw, which was extrapolated to the narrow spws." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.44x0.52 arcsec  
  > "The resulting beam size was $0.44\times0.52\ensuremath{''}$." (2 Observations and data reduction)
- final rms: 1.3 mJy/beam channel rms  
  > "We reach a channel rms in the narrow spws of $\sigma=1.3$ mJy beam$^{-1}$" (2 Observations and data reduction)

### Inherited from earlier work

- Turbulent line width of TW Hya CN/molecular lines  
  > "some line broadening remains in excess of the turbulent line width derived by (cite: Teague16)" (3.1 CN polarisation) [from Teague16]
- Maximum vertical field relation B_z,max=(R_out/R)^2 B_inf  
  > "$B_{z, {\rm max}}=(R_{\rm out}/R)^2
B_{\infty}$" (Discussion and conclusions) [from Okuzumi14]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection for continuum
- Exact conversion from Stokes V/I limit to B_z (derivative of I, Zeeman coefficients used in stacking)
- Spectral window frequency tunings and kinematic parameters (inclination, PA, stellar mass) for the Keplerian correction
- Self-calibration solution intervals
- Image size and cell size
- Hanning smoothing and masking details
- Disc model parameters for beta and accretion-rate limits

## Analysis recipe

1. **Calibrate and image all Stokes**: Standard polarisation calibration, self-calibration on continuum, continuum subtraction, cubes in I,Q,U,V  
  > "image cubes were created for all spws at the native spectral resolution in all four Stokes parameters I, Q, U, and V" (2 Observations and data reduction)
   - software: CASA
   - parameter: robust 0.5  
  > "Briggs weighting and a robust parameter of $0.5$" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Limits per hyperfine component at CN peak**: Stokes V limits relative to peak I at emission peak (-0.09,-0.78) arcsec offset  
  > "We first analysed the strongest CN emission peak at $(-0.09\ensuremath{''}, -0.78\ensuremath{''})$ offset from the continuum peak" (3.1 CN polarisation)
   - assumption: Low inclination so sensitive mostly to vertical field B_z  
  > "Because the inclination of the disc around TW Hya is low, we are mostly sensitive to the vertical component of the magnetic field $|B_z|$." (3.1 CN polarisation)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stack hyperfine components**: Stack all but two weakest components, scaled by relative Stokes I peak and Zeeman coefficient relative to strongest component  
  > "the stacked Stokes V spectrum was produced by scaling Stokes V spectra of the individual components by the relative Stokes I peak intensity" (3.1 CN polarisation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Azimuthally averaged Keplerian-corrected stack**: Ring of beam width at radius 0.72 arcsec (~42 au), pixel-by-pixel Keplerian correction, stack two strongest unblended components; line width 0.45 km/s  
  > "we produced an azimuthally averaged spectrum that was corrected on a pixel-by-pixel basis for the Keplerian rotation of the disc" (3.1 CN polarisation)
   - fitting: _not stated_
   - validation: _not stated_
5. **Line-of-nodes stack for toroidal field**: Stack east and west parts with sign flip; B_phi=B_z/sin i  
  > "toroidal field strength of $|B_\phi|=|B_z|/\sin{i}<30$ mG" (3.1 CN polarisation)
   - assumption: inclination i~5 deg  
  > "$i\sim5^\circ$ (cite: Huang18)" (TW Hya)
   - fitting: _not stated_
   - validation: _not stated_
6. **Debiased linear continuum polarisation map**: P_l=sqrt(Q^2+U^2-sigma_P^2) using line-free channels of the wide spw  
  > "$P_l=\sqrt{{\rm Q}^2+{\rm U}^2 - \sigma_P^2}$" (3.2 Continuum polarisation)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare limits with disc field models**: Compute beta, B_inf, D(R), accretion-rate limits from limit on B_z  
  > "our limit would thus imply $B_{\infty}<25~\mu$G" (Discussion and conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: calibration and imaging  
  > "standard ALMA polarisation calibration scripts in CASA 5.4.0" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| |B_z| limit, stacked hyperfine components | <2.7 | 1 sigma | mG | 3 | we reach a fractional limit ($1\sigma$) of $/B_z/<2.7$ mG |
| |B_z| limit, azimuthally averaged | <0.8 | 1 sigma | mG | 4 | reaches a $1\sigma$ limit of $/B_z/<0.8$ mG |
| |B_phi| limit, line of nodes | <30 | not stated | mG | 5 | $/B_z/<2.6$ mG or a toroidal field strength of $/B_\phi/=/B_z//\sin{i}<30$ mG |
| plasma beta | >~4e3 | not stated | dimensionless | 7 | $\beta\gtrsim4\times10^3$ |
| B_infinity | <25 | not stated | uG | 7 | $B_{\infty}<25~\mu$G |
| accretion rate limit (Ohmic) | <~3e-7 | not stated | Msun/yr | 7 | $\dot{M}\lesssim3\times10^{-7}$ M$_\odot$ yr$^{-1}$ |
| continuum polarised rms | 22 | not stated | uJy/beam | 6 | We find $\sigma_P\approx22~\mu$Jy beam$^{-1}$. |

## Qualitative findings

- Continuum polarisation vectors are almost purely toroidal, consistent with radiatively aligned grains  
  > "The polarisation vectors are almost purely toroidal, which is the signature of radiatively aligned grains dominating the polarised emission" (3.2 Continuum polarisation)

## Claim tuples

- H: Is circular polarisation of CN detectable in the TW Hya disc, giving B_z? | E: Stokes V analysis of CN N=2-1 hyperfine components with stacking | R: No detection; |B_z|<0.8 mG (1 sigma) at ~42 au | F: Tight upper limit on vertical field, well below Shu07 predictions | **supported**
- H: Does the limit constrain disc advection/diffusion models? | E: Compare with Okuzumi14 maximum field | R: B_inf<25 uG; D(42 au)<0.025/B_inf | F: First observational constraint on advection in an accretion disc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: ~2 sigma line-of-nodes V signal (~5 mG) not classified as detection due to low significance  
  > "considering the low significance of the circular polarisation signal ($\sim2\sigma$), we do not classify it as a detection" (3.1 CN polarisation)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum polarisation low S/N and no other wavelengths, so nature is beyond scope  
  > "because of the low S/N of the polarisation and the lack of data at other wavelengths" (3.2 Continuum polarisation)
- Caveat (inferred, ours): Limit conversion depends on Zeeman coefficients and assumed line width; systematic leakage not quantified
- Caveat (inferred, ours): Stacking of overlapping hyperfine components may bias
- Caveat (inferred, ours): Flux calibrator variability handled by self-cal only

## Reproducibility

- Data public (paper): ALMA project 2018.1.00167.S cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00167.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Custom stacking and Keplerian-correction code
- Missing: Line-free channel ranges
- Missing: Imaging parameters beyond robust
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data are archival-accessible and basic calibration is described, but stacking and Keplerian correction details are incomplete.
- Rediscovery candidate: no, Main results are upper limits and the stacking recipe lacks detail.

## Links

- Method: Okuzumi14 (disc field model)
- Method: larsson:19 (Zeeman calculation notation)
- Companion: Cazzoletti18 (CN emission model for TW Hya)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "stated": 37,
  "rate": 0.487
 },
 "evidence_ok": true
}
```
