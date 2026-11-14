# Radio Linear Polarization of GRB Afterglows: Instrumental Systematics in ALMA Observations of GRB 171205A

`2020ApJ...895...64L` | The Astrophysical Journal 2020 | first author: Laskar, Tanmoy | arXiv: 2004.06730 | DOI: 10.3847/1538-4357/ab88cc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: transients
- Question: Is the linear polarization of the GRB 171205A radio afterglow claimed by Urata et al. detected, or is it an ALMA instrumental systematic?  
  > "Using these tests to re-analyze and evaluate the archival ALMA data, we uncover systematics in the polarization calibration at the $\approx0.09\%$ level." (abstract)
- Target **GRB 171205A**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00801.T
- bands: Band 3 (3 mm, 97.5 GHz), full-Stokes  
  > "full-Stokes ALMA Band 3 (3mm) observations of GRB 171205A" (2.1 QA2 calibration)
- frequencies and spectral setup: LSB 89.5–93.5 GHz, USB 101.5–105.5 GHz; four spectral windows  
  > "lower sideband (LSB; $89.5$–$93.5$ GHz) and upper sideband (USB; $101.5$–$105.5$ GHz)" (2.1 QA2 calibration)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.28'' x 0.20'' at PA 85 deg  
  > "The clean beam is $0.28\ensuremath{''}$ $\times$ $0.20\ensuremath{''}$ at a position angle of $85^\circ$" (2.3 Imaging)
- max recoverable scale: _not stated_
- sensitivity: rms ≈7.3 uJy in Q, U, V (full data)  
  > "The rms noise near the center of the $Q$, $U$, and $V$ images is ${\approx7.3}~\mu$Jy" (2.1 QA2 calibration)
- time on source: ≈9.4×10^3 s on source; 43 antennas  
  > "$t_{\rm int}\approx9.4\times10^3$ s is the total integration time on source, $N=43$ is the number of antennas in the array" (2.3 Imaging)
- observing dates: 2017 December 10; three SB executions at 5.135–5.245 days after burst  
  > "The times of the three SB executions (considering target and gain calibrator scans only) are: 5.135–5.169, 5.174–5.208, and 5.211–5.245 days, respectively." (Table 3)
- pi or archival as stated: Archival, PI Urata  
  > "project 2017.1.00801.T (PI: Urata) from the ALMA archive" (2.1 QA2 calibration)
- Other facility **Swift XRT**: X-ray light curve used to constrain jet break time  
  > "The X-ray light curve for the afterglow of GRB 171205A exhibits a shallow, unbroken power law decay with $\alpha\approx-1.06$ to $\gtrsim35$ days" (4.2 Constraints on magnetic field geometry)
- External data: Previously claimed ALMA linear polarization (0.27±0.04)% and VLA cm spectral index 1.46±0.03  
  > "claimed a detection of $(0.27\pm0.04)\%$ linear polarization in the radio afterglow of GRB 171205A" (Introduction) [from Urata et al. 2019 (cite: uth+19)]
- External data: Compilation of radio polarization limits of other GRBs  
  > "Our compiled sample of radio linear polarization observations includes one detection (cite: lag+19), and several upper limits" (4.3 Radio Polarization of GRB Afterglows) [from (cite: tfk+98; fyb+03; gt05; tfbk04; vdhpdb+14; lag+19)]
- Simulation/model as data: Granot & Taylor 2005 polarization models compared with the limit  
  > "we compare the models of (cite: gt05) together with the data in Fig. [7]" (4.2 Constraints on magnetic field geometry)

## Processing

### Calibration

- pipeline or manual: Regenerated QA2 with archive scripts, then full independent manual reduction  
  > "we perform a full independent reduction of the data." (2.2 Detailed data analysis)
- casa version: CASA 5.6.1 (imaging)  
  > "with CASA version 5.6.1 using a robust parameter of 0.0" (2.1 QA2 calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1127-1857 (≈1.05 Jy at 91.5 GHz, β=-0.51) from ALMA calibrator catalog  
  > "We set the flux density of J1127-1857 using measurements near the time of the GRB observations listed the ALMA calibrator catalog" (2.2 Detailed data analysis)
- flux scale uncertainty: Systematic polarization uncertainty 0.09% (1σ) estimated from gain calibrator variability  
  > "we estimate an additional $1\sigma$ systematic calibration uncertainty of $\approx0.16\%/1.69\approx0.09\%$" (2.5 Systematic calibration uncertainty)
- self calibration: Phase-only 10 min then 2 min, then amp+phase 20 min, gain mode T, refant strict, per sideband  
  > "We correct for these by performing two rounds of phase-only self-calibration with solution intervals of 10 min and 2 min" (2.3 Imaging)

### Imaging

- task: tclean, nterms=1  
  > "using `tclean` in CASA with a robust parameter of 0.0 and one Taylor term (i.e. nterms=1)" (2.3 Imaging)
- deconvolver: _not stated_
- weighting robust: robust = 0.0  
  > "with a robust parameter of 0.0" (2.3 Imaging)
- uv taper: _not stated_
- cell size: 0.05'' cell, 25''x25'' image  
  > "across the $25\ensuremath{''}\times25\ensuremath{''}$ image is $\approx0.02\ensuremath{''}$, which is a fraction of the $0.05\ensuremath{''}$ cell size" (footnote 6)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.28'' x 0.20'' PA 85 deg  
  > "The clean beam is $0.28\ensuremath{''}$ $\times$ $0.20\ensuremath{''}$ at a position angle of $85^\circ$" (2.3 Imaging)
- final rms: _not stated_

### Inherited from earlier work

- Time splitting by scheduling block execution to test polarization stability  
  > "We tested for stability of polarization calibration by dividing the data in time by each execution of the scheduling block (SB), as described in (cite: lag+19)." (2.1 QA2 calibration) [from (cite: lag+19)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, threshold and masks for tclean
- Exact flagging selections beyond DV22 and the specific spectral window
- Targeted source coordinates
- Spectral windows' channelization
- Whether the reduction scripts and CASA version for the manual reduction match 5.6.1

## Analysis recipe

1. **Regenerate QA2 data and test stability**: Run archive calibration scripts, image Stokes IQUV, fit point source with imfit, split by sideband and by SB execution  
  > "we used the CASA (cite: mws+07) calibration scripts, associated with the data set and also available from the ALMA archive, to regenerate the calibrated Quality Assurance 2 (QA2) measurement set." (2.1 QA2 calibration)
   - software: CASA, imfit
   - parameter: robust 0.0  
  > "using a robust parameter of 0.0" (2.1 QA2 calibration)
   - fitting: Point source fit with position fixed to Stokes I  
  > "Fitting for the linearly polarized flux density with the position fixed to that derived from the Stokes $I$ image" (2.1 QA2 calibration)
   - validation: Compared Q,U with Urata et al.; sidebands differ by 32 uJy in Q  
  > "we find that the Stokes $Q$ measurements differ between the two sidebands by $32~\mu$Jy" (2.1 QA2 calibration)
2. **Independent polarization calibration**: Tsys/wvr, bandpass, qufromgain, XYf+QU in gaincal, xyamb, polcal for D-terms, repeated with two reference antennas  
  > "We use DV06 as reference antenna, and validate our calibration by repeating the entire analysis separately using a nearby antenna with a different architecture, DA64." (2.2 Detailed data analysis)
   - software: CASA, qufromgain, xyamb, gaincal, polcal
   - parameter: cross-hand delays from scan 61 on polarization calibrator  
  > "we use scan 61 on the polarization calibrator as the scan with the strongest polarization signal" (2.2 Detailed data analysis)
   - assumption: Stokes V of polarization calibrator negligible  
  > "Standard polarization calibration assumes negligible $V$ in the polarization calibrator." (2.4 Polarization measurements)
   - fitting: _not stated_
   - validation: Residual polarization of calibrator ≈0.1%  
  > "the final residual polarization, determined by running `qufromgain` on the calibrated calibrator data, is $\approx0.1\%$" (2.2 Detailed data analysis)
3. **Self-calibration and imaging**: Phase-only then amp+phase self-cal per sideband, tclean imaging, imfit point source fits to IQUVP  
  > "We, therefore, perform one round of amplitude and phase self calibration, applying the pre-derived phase solutions on the fly." (2.3 Imaging)
   - software: CASA, gaincal, tclean, imfit
   - parameter: amp solint 20 min, 14 solutions per pol per antenna, cross-hand phase fixed  
  > "we solve for one solution per 20 min, for a total of 14 solutions per polarization per antenna" (2.3 Imaging)
   - fitting: Point source model with imfit  
  > "We fit the Stokes $I$ image with a point source model using CASA `imfit`" (2.3 Imaging)
   - validation: Compared with 30 s self-cal as in Urata et al.; minimum solint ≳35 s  
  > "yields $t_{\rm solint}\gtrsim35$ s" (2.3 Imaging)
4. **Quantify systematic uncertainty and upper limit**: Use gain calibrator polarization variation across SB executions; range of three Gaussian draws gives 1σ systematic, combined with statistical error; Rician bias  
  > "Thus, we estimate an additional $1\sigma$ systematic calibration uncertainty of $\approx0.16\%/1.69\approx0.09\%$ for these observations." (2.5 Systematic calibration uncertainty)
   - assumption: Gain calibrator intrinsic polarization constant over observations; systematic is Gaussian  
  > "assume that the calibrator’s intrinsic polarization is constant with time over our observations" (2.5 Systematic calibration uncertainty)
   - fitting: _not stated_
   - validation: _not stated_
5. **Interpret limit with jet magnetic field models**: Compare with Granot & Taylor 2005 toroidal models and patch-coherence estimate  
  > "The low degree of polarization disfavors models of polarization produced by toroidal magnetic fields in GRB jets." (4.2 Constraints on magnetic field geometry)
   - assumption: β≈-0.43 from Urata et al.  
  > "for $\beta\approx-0.43$ (cite: uth+19)" (4.2 Constraints on magnetic field geometry)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.1: Calibration, tclean imaging, imfit, gaincal, polcal  
  > "with CASA version 5.6.1" (2.1 QA2 calibration)
- **almapolhelpers (qufromgain, xyamb)** : Estimating Q,U from gains and resolving QU phase ambiguity  
  > "using the python utility `qufromgain` from the ALMA polarization helpers module (`almapolhelpers.py`" (2.2 Detailed data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3σ upper limit on linearly polarized intensity | 97.2 | not stated | uJy | 4 | We derive a 3$\sigma$ upper limit on the linearly polarized intensity of $P<97.2~\mu$Jy |
| 3σ upper limit on fractional linear polarization | <0.30 | not stated | % | 4 | $\Pi_{\rm L}<0.30\%$ |
| Additional 1σ systematic calibration uncertainty | 0.09 | not stated | % of Stokes I | 4 | $\approx0.16\%/1.69\approx0.09\%$ |
| Combined-data linear polarized flux (undebiased) | 41.7 | ±32.4 | uJy | 4 | This yields a linear polarization measurement of $41.7\pm32.4~\mu$Jy (undebiased) |
| Stokes I flux density (all data, self-calibrated) | 32.44 | ±0.03 | mJy | 3 | for which we derive a value of $32.44\pm0.03$ mJy (statistical error) |
| Stokes V (all data) | -73.4 | ±7.3 | uJy | 3 | / All / amp & phase / 20 min / $32.44\pm0.03$ / 7.7 / $-31.5\pm7.3$ / $9.6\pm7.7$ / $-73.4\pm7.3$ / $41.7\pm10.6$ / |
| Magnetic patch scale limit | 4e-3 Gamma^-1 | not stated | rad | 5 | $\theta_{\rm B}\lesssim \Pi_{\rm L,lim}\Gamma^{-1}\Pi_{\rm max}^{-1}\approx4\times10^{-3}\Gamma^{-1}$ rad |
| mm spectral index | -0.51 | ±0.04 | dimensionless | 5 | for which we calculate $\beta_{\rm mm}=-0.51\pm0.04$ |

## Qualitative findings

- Polarization calibration varies with time and sideband for both GRB and gain calibrator, indicating instrumental systematics; spurious Stokes V ≈0.23% appears  
  > "we find that the polarization measurements exhibit significant time variability." (2.4 Polarization measurements)

## Claim tuples

- H: Is the 0.27% linear polarization of GRB 171205A real? | E: Independent re-reduction with time/frequency splitting and gain calibrator checks | R: Q,U not reproduced; time variable; significance ≈1.3σ with systematics | F: No detection; 3σ limit Π<0.30% | **supported**
- H: Does the polarization imply thermal electrons? | E: Compare limit with optical polarization measurements and upper limits | R: As many as 27% of optical observations lie below the limit | F: No strong evidence for non-accelerated electrons | **supported**
- H: Does the limit constrain jet magnetic geometry? | E: Compare with Granot & Taylor models | R: Toroidal field gives too high polarization for most viewing angles | F: Toroidal field disfavored for reverse shock | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Time and frequency splitting and gain calibrator checks quantify stability of polarization calibration  
  > "we recommend basic sanity checks of (i) dividing the data in time and frequency to test for calibration stability" (Conclusions)
- Alternative: 30 s amp+phase self-cal with independent X,Y gains (Urata et al.) rejected as shorter than minimum solution interval  
  > "the 30 s solution interval used by (cite: uth+19) is shorter than the minimum possible $t_{\rm solint}$ where stable solutions may be expected." (2.3 Imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): Origin of time-varying systematics (e.g. XY phase) not investigated; second-order corrections beyond scope  
  > "investigating this requires second-order calibration corrections, which are beyond the scope of this work." (2.4 Polarization measurements)
- Caveat (inferred, ours): Systematic estimate rests on only three time bins of one gain calibrator
- Caveat (inferred, ours): Assumes calibrator polarization is constant
- Caveat (inferred, ours): Single dataset, no independent confirmation

## Reproducibility

- Data public (paper): Raw data downloaded from ALMA archive  
  > "We downloaded the raw data for full-Stokes ALMA Band 3 (3mm) observations of GRB 171205A" (2.1 QA2 calibration)
- Products in archive: _not stated_
- Missing: Clean parameters beyond robust
- Missing: Exact flagging and spw details
- Missing: Scripts not released
- Data volume (inferred): tens of GB raw
- Score (inferred): 4/5, Public data, detailed recipe and numeric tables; some tclean/flagging details missing.
- Rediscovery candidate: yes, Public archival data, step-by-step recipe, numeric results in tables.

## Links

- Method: Nagai et al. 2016 (cite: nnp+16) (ALMA polarization commissioning)
- Companion: Urata et al. 2019 (cite: uth+19) (Original claim being re-analyzed)
- Companion: Laskar et al. 2019 (cite: lag+19) (GRB 190114C ALMA polarization, time-splitting method)
- Related: ALMA calibrator catalog
- Related: AMAPOLA

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 74,
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
