# First ALMA Light Curve Constrains Refreshed Reverse Shocks and Jet Magnetization in GRB 161219B

`2018ApJ...862...94L` | The Astrophysical Journal 2018 | first author: Laskar, Tanmoy | arXiv: 1808.09476 | DOI: 10.3847/1538-4357/aacbcc

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients
- Question: What do multi-wavelength (radio to X-ray) observations, including the first ALMA light curve, reveal about the forward and reverse shocks, energetics, circumburst density and jet magnetization of GRB 161219B?  
  > "Comparing the RS and FS emission, we show that the ejecta are only weakly magnetized, with relative magnetization, $\ensuremath{R_{\rm B}}\approx1$, compared to the FS." (abstract)
- Target **GRB 161219B**: coordinates RA = 06h 06m 51.37s, Dec = -26 47 29.7 (J2000), X-ray position  
  > "Spectroscopic observations 36 hr after the burst with the X-shooter instrument on the ESO VLT 8.2 m telescope provided a redshift of $z = 0.1475$" (2 GRB Properties and Observations); "The X-ray afterglow was localized to RA = 06h 06m 51.37s, Dec = -26$^\circ$ 47$'$ 29.7$''$ (J2000)" (X-ray: Swift/XRT); z/distance z = 0.1475  
  > "Spectroscopic observations 36 hr after the burst with the X-shooter instrument on the ESO VLT 8.2 m telescope provided a redshift of $z = 0.1475$" (2 GRB Properties and Observations); "The X-ray afterglow was localized to RA = 06h 06m 51.37s, Dec = -26$^\circ$ 47$'$ 29.7$''$ (J2000)" (X-ray: Swift/XRT); distance from X-shooter/VLT spectroscopy (GCN circular)  
  > "Spectroscopic observations 36 hr after the burst with the X-shooter instrument on the ESO VLT 8.2 m telescope provided a redshift of $z = 0.1475$" (2 GRB Properties and Observations); "The X-ray afterglow was localized to RA = 06h 06m 51.37s, Dec = -26$^\circ$ 47$'$ 29.7$''$ (J2000)" (X-ray: Swift/XRT)

## Data provenance

- ALMA projects: 2016.1.00819.T, 2016.A.00015.S
- bands: Band 3  
  > "in Band 3, with two 4 GHz-wide base-bands centered at 91.5 and 103.5 GHz, respectively." (Millimeter: ALMA)
- frequencies and spectral setup: two 4 GHz-wide base-bands centered at 91.5 and 103.5 GHz  
  > "two 4 GHz-wide base-bands centered at 91.5 and 103.5 GHz, respectively." (Millimeter: ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 31 min scheduling block, 16 min on source (first epoch)  
  > "in our 31 min scheduling block, with 16 min on source" (Millimeter: ALMA)
- observing dates: _not stated_
- pi or archival as stated: PI Laskar program plus Director's Discretionary Time  
  > "through program 2016.1.00819.T (PI: Laskar)" (Millimeter: ALMA)
- Other facility **Swift XRT/UVOT/BAT**: X-ray and UV/optical light curves, prompt emission  
  > "XRT continued observing the afterglow for $123$ d in photon counting mode." (X-ray: Swift/XRT)
- Other facility **VLA**: 1.2-37 GHz radio SEDs over 9 epochs (program 15A-235)  
  > "We detected and tracked the flux density of the afterglow from 1.2 GHz to 37 GHz over 9 epochs until $\approx159$ d after the burst." (Centimeter: VLA)
- Other facility **LCOGT, Liverpool Telescope, Swope, Keck, UKIRT**: optical and near-IR photometry  
  > "We obtained 7 epochs of near-IR observations in the $JHK$-bands with the Wide-field Camera (WFCAM; (cite: caado+07)) mounted on the United Kingdom Infrared Telescope (UKIRT)" (UV, optical, and near-IR)
- External data: GROND, GTC, NOT and PS1 light curves  
  > "We include the GROND, Gran Telescopio Canarias (GTC), Nordic Optical Telescope (NOT), and Pan-STARRS1 (PS1) light curves presented by (cite: cidup+17)" (UV, optical, and near-IR) [from (cite: cidup+17)]
- External data: VLT, TNG, LT, Keck observations  
  > "the 3.6 m Telescopio Nazionale Galileo (TNG), LT, and Keck observations presented by (cite: apm+17) in our modeling." (UV, optical, and near-IR) [from (cite: apm+17)]
- Simulation/model as data: SN 1998bw template used for SN 2016jca contribution  
  > "We include the contribution of the supernova using a template constructed from the extinction-corrected spectra of SN 1998bw" (4 Multi-wavelength modeling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: pipeline products imaged with CASA  
  > "We imaged the pipeline products using the Common Astronomy Software Application" (Millimeter: ALMA)
- flux calibrator: J0522-3627 bandpass and flux calibrator; J0614-2536 phase calibrator  
  > "All observations utilized J0522-3627 as bandpass and flux density calibrator, and J0614-2536 as phase calibrator." (Millimeter: ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
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

- Cm-band spectro-temporal variability analysis deferred to companion paper  
  > "which we discuss in detail in a separate work (Alexander et el., in prep; henceforth ALB18)" (Introduction) [from ALB18 (Alexander et al., in prep)]
- MCMC procedure follows earlier work  
  > "following the procedure described in (cite: lbt+14) and (cite: lbm+15)" (4 Multi-wavelength modeling) [from (cite: lbt+14); (cite: lbm+15)]
- Synchrotron spectra from Granot & Sari with weighting schemes of Laskar 2014  
  > "smoothly connected power-law synchrotron spectra described by (cite: gs02) modified using the weighting schemes presented in (cite: lbt+14)" (4 Multi-wavelength modeling) [from (cite: gs02); (cite: lbt+14)]

### Not stated but needed to reproduce (our reading)

- ALMA imaging parameters (tclean weighting, cell, masking) and how flux densities were measured
- CASA version and pipeline version
- ALMA flux calibrator flux scale uncertainty
- Full multi-frequency data tables (only samples printed)
- Exact MCMC burn-in length and convergence criteria (deferred to earlier papers)

## Analysis recipe

1. **Fit X-ray and UV/optical light curves with broken power laws**: smoothly broken power laws with smoothness fixed y=5  
  > "We fix the smoothness parameters here and in equation [\[eq:bpl\]](#eq:bpl) at $y_1=y_2=y=5$" (Footnote 11)
   - software: Xspec
   - fitting: _not stated_
   - validation: _not stated_
2. **Model forward shock with SN and host in all bands**: Synchrotron FS model with jet break, SN 1998bw template, SMC extinction, MCMC  
  > "we carry out a Markov Chain Monte Carlo (MCMC) analysis using the Python-based code EMCEE" (4 Multi-wavelength modeling)
   - software: emcee
   - parameter: 128 chains, 10^4 posterior samples, 10% uncertainty floor  
  > "We initialized 128 Markov chains with parameters clustered around their best fit values (with a 3% dispersion)." (4 Multi-wavelength modeling)
   - assumption: ISM environment; uniform priors, log-uniform for scale parameters  
  > "Priors for all scale parameters ($\epsilon_{\rm e}$, $\epsilon_{\rm B}$, $n_{0}$, $E_{\rm K,iso}$, $t_{\rm jet}$, and $\Upsilon_{\rm SN}$) are uniform in logarithmic space" (4 Multi-wavelength modeling)
   - fitting: emcee MCMC with uniform priors  
  > "We assume uninformative, uniform priors on all free parameters." (4 Multi-wavelength modeling)
   - validation: _not stated_
3. **Model reverse shock from energy injection and compare to FS**: Analytic RS scaling relations anchored to cm and ALMA bands; compare with FS scaled by Lorentz factor  
  > "We present a comparison between the observed RS parameters and the values expected by scaling the FS parameters by $\Gamma_{\rm E}$" (6.3 self-consistency)
   - assumption: pressure behind RS equals that at FS; same p; constant microphysical parameters  
  > "make the simplifying assumption that the pressure behind the RS is equal to that at the FS" (6.1)
   - fitting: _not stated_
   - validation: Peak flux matches within 5%  
  > "We find the peak flux density to match within 5%(!), suggesting that the RS is not magnetized relative to the FS." (6.3)

## Software

- **CASA** : imaging ALMA pipeline products and VLA reduction  
  > "We imaged the pipeline products using the Common Astronomy Software Application" (Millimeter: ALMA)
- **emcee** : MCMC fitting of afterglow model  
  > "using the Python-based code EMCEE" (4 Multi-wavelength modeling)
- **HEASOFT** v6.19: XRT and UVOT analysis  
  > "fit them using the HEASOFT (v6.19) software package" (X-ray: Swift/XRT)
- **FAST** : host galaxy SED fitting  
  > "We fit a set of galaxy templates from (cite: bc03) using `FAST`" (Host galaxy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA light curve decline index 1.3-24.5 d | -0.52 | 0.02 | dimensionless | 0 | The ALMA light curve can be fit with a single power law with $\alpha_1 = -0.52\pm0.02$ |
| circumburst density n0 | 3.2e-4 | +1.4/-1.2 e-4 | cm^-3 | 2 | $(3.2^{+1.4}_{-1.2})\times10^{-4}$ |
| jet break time | 33.0 | +1.5/-1.4 | d | 2 | $33.0^{+1.5}_{-1.4}$ |
| jet opening angle | 13.44 | 0.35 | deg | 2 | $13.44\pm0.35$ |
| beaming-corrected kinetic energy | 1.27e50 | +0.36/-0.25 e50 | erg | 2 | $(1.27^{+0.36}_{-0.25})\times10^{50}$ |
| electron index p | 2.079 | +0.009/-0.006 | dimensionless | 2 | $2.079^{+0.009}_{-0.006}$ |
| injection index m | 0.35 | 0.09 | dimensionless | 3 | $m=(4\alpha_{\rm X}+3p-3)/(p+3) = 0.35\pm0.09$ |

## Qualitative findings

- Early cm/mm excess is consistent with a Newtonian reverse shock from energy injection ending at ~0.25 d, with low ejecta magnetization  
  > "The peak frequency and peak flux of the two shocks are fully self-consistent at the deceleration time, indicating low ejecta magnetization." (7 Discussion)

## Claim tuples

- H: Does early cm/mm and optical excess arise from a refreshed reverse shock? | E: FS plus RS modeling of radio-to-X-ray data | R: RS with g~2.8, tE~0.25 d fits the excess | F: First direct detection of energy injection RS; ejecta weakly magnetized (RB~1) | **supported**
- H: What are the jet geometry and energetics? | E: Joint modeling with ALMA, X-ray and VLA light curves constraining jet break | R: t_jet~32 d, theta~13 deg, E_K~1.3e50 erg | F: Wide jet, low radiative efficiency ~4% | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Relativistic RS models and other cooling-frequency orderings were ruled out  
  > "Upon detailed consideration, no relativistic RS models are able to reproduce the observations" (6.2)
- How they decided it was enough: _not stated_
- Limitation (authors): nu_a not constrained, causing parameter degeneracies; epsilon_e~0.9 problematic  
  > "We note that $\ensuremath{\nu_{\rm a}}$ is not constrained by the data, resulting in some degeneracies between the physical parameters" (4.1 Afterglow)
- Caveat (inferred, ours): Radio variability from scintillation leaves cm data excluded from fits, affecting RS inference
- Caveat (inferred, ours): RS analytic scalings may over-predict flux
- Caveat (inferred, ours): ALMA treated as one of many datasets; RB depends on assumptions

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; no explicit public statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00819.T and ADS/JAO.ALMA#2016.A.00015.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters for ALMA
- Missing: Full photometry tables (only samples in text)
- Missing: MCMC model code (deferred to previous papers)
- Data volume (inferred): ALMA: ~tens of GB for 5 small Band 3 epochs; plus VLA and Swift
- Score (inferred): 3/5, ALMA flux densities are tabulated but imaging details are missing and the modeling relies on external papers.
- Rediscovery candidate: no, The main results depend on a multi-facility model with incomplete recipe; ALMA data are a minor part.

## Links

- Method: (cite: lbt+14) (MCMC afterglow modeling procedure)
- Method: (cite: gs02) (synchrotron spectra)
- Companion: Alexander et al., in prep (ALB18) (cm-band variability and scintillation)
- Related: VLA 15A-235

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
