# ALMA and GMRT Constraints on the Off-axis Gamma-Ray Burst 170817A from the Binary Neutron Star Merger GW170817

`2017ApJ...850L..21K` | The Astrophysical Journal Letters 2017 | first author: Kim, S. | arXiv: 1710.05847 | DOI: 10.3847/2041-8213/aa970b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: transients, other
- Question: Can ALMA and GMRT non-detections plus public X-ray/radio data constrain the afterglow of GRB 170817A/GW170817 and the jet geometry (off-axis)?  
  > "In this letter, we examine the afterglow properties of AT2017gfo." (Introduction)
- Target **AT2017gfo / GW170817 / GRB 170817A**: coordinates RA 13h09m48.09s, Dec -23d22'53.3" (J2000)  
  > "$10.3\ensuremath{''}$ from NGC 4993 at 43.9 Mpc (cite: Levan2017a)" (Introduction); z/distance 43.9 Mpc; z=0.009854 adopted in modeling  
  > "$10.3\ensuremath{''}$ from NGC 4993 at 43.9 Mpc (cite: Levan2017a)" (Introduction); distance from Levan et al. 2017 (cite: Levan2017a)  
  > "$10.3\ensuremath{''}$ from NGC 4993 at 43.9 Mpc (cite: Levan2017a)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00862.T
- bands: 338.5 GHz (ALMA); 1.39 GHz L band (GMRT)  
  > "In total, we obtained six epochs at 338.5 GHz" (2.1 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-7 initially; C40-8/9 at 44 days  
  > "The initial ALMA observations were performed in the C40-7 configuration" (2.1 ALMA observations)
- baselines: _not stated_
- angular resolution: ~0.13"x0.07" (C40-7); 0.026"x0.016" (C40-8/9)  
  > "yielding a synthesized beam of $0.026\ensuremath{''}\times0.016\ensuremath{''}$" (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: nominal rms ~40 uJy/beam; 3sigma limits 90-150 uJy (ALMA)  
  > "set to reach a nominal r.m.s. of $\sim40$ $\mu$Jy/beam" (2.1 ALMA observations)
- time on source: GMRT ~1.5 hr per epoch; ALMA 1724-2238 s  
  > "The observing time was $\sim1.5$ hr for each observation." (2.2 GMRT Observations)
- observing dates: ALMA from 18 Aug 2017 (1.4 d) to 30 Sep 2017 (44.1 d)  
  > "started on 18 August 2017 at 22:50:40 UTC (1.4 days after GW170817)" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Other facility **GMRT**: 1.39 GHz upper limits at three epochs  
  > "We secured three epochs in the L band, centered at 1.39 GHz" (2.2 GMRT Observations)
- Other facility **VLA/ATCA, Swift, Chandra, HST, VLT**: public radio, X-ray and optical data used in modeling  
  > "obtained with the Australia Telescope Compact Array (ATCA) and the Very Large Array (VLA)" (2.3 Other Observations)
- External data: Radio measurements (VLA/ATCA)  
  > "we incorporated radio measurements from (cite: Corsi2017e; Corsi2017f; Corsi2017b; Corsi2017c; Corsi2017d)" (2.3 Other Observations) [from Corsi2017; Hallinan2017a; Kaplan2017a; Mooley2017]
- External data: X-ray constraints from Swift and Chandra  
  > "We also included the X-ray constraints of (cite: Evans2017b), (cite: Haggard2017b) and (cite: Troja:nature)" (2.3 Other Observations) [from Evans2017b; Haggard2017b; Troja:nature]
- External data: Optical HST/VLT photometry  
  > "optical photometry obtained with the *Hubble Space Telescope* and ESO’s 8.2-m Very Large Telescope (VLT) by (cite: Tanvir2017b)" (2.3 Other Observations) [from Tanvir2017b]
- External data: Prompt gamma-ray energy and Epeak of GRB 170817A  
  > "reported an exceptionally low isotropic-equivalent energy of only $E_{\gamma,\,\rm iso}=(3.08\pm0.72)\times10^{46}$ erg" (3.1) [from GRB2017a; Goldstein2017b]
- Simulation/model as data: BOXFIT v2 templates from 2D relativistic hydrodynamical jet simulations  
  > "we model the observed evolution from X-rays to radio with templates from two-dimensional relativistic hydrodynamical jet simulations using BOXFIT version 2" (3.2 Modeling the broadband afterglow)

## Processing

### Calibration

- pipeline or manual: scripts provided by ALMA, CASA  
  > "The ALMA data were reduced with scripts provided by ALMA" (2.1 ALMA observations)
- casa version: CASA 4.7.2  
  > "version 4.7.2" (2.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1337-1257 and J1427-4206 (ALMA); 3C286 (GMRT)  
  > "The quasars J1337$-$1257 and J1427$-$4206 were used for band and flux calibration" (2.1 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "we created images using TCLEAN, with a pixel size of $0.01\ensuremath{''}$/px" (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.01"/px  
  > "with a pixel size of $0.01\ensuremath{''}$/px" (2.1 ALMA observations)
- image size: _not stated_
- masking: interactive cleaning regions around detected sources  
  > "We interactively selected cleaning regions around detected sources" (2.1 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: measured in 10" box around center in images without primary beam correction  
  > "The r.m.s. was measured in a $10''$-width box around the central position in the images without primary beam correction." (2.1 ALMA observations)

### Inherited from earlier work

- Modeling method for BOXFIT templates  
  > "using BOXFIT version 2 with the methods described in (cite: vanEerten2012)" (3.2) [from vanEerten2012]
- Rest-frame X-ray light curve computation  
  > "Identical to (cite: Schulze2014a), we computed the rest-frame light curves" (3.1) [from Schulze2014a]

### Not stated but needed to reproduce (our reading)

- tclean weighting/robust, deconvolver, threshold
- ALMA flux scale uncertainty and QA details
- GMRT AIPS calibration and imaging parameters
- Fit likelihood/optimizer for matching BOXFIT templates to data; how best models were chosen
- epsilon_B, n and other parameter grid sampling and goodness-of-fit
- Epeak/Egamma parameter-study grid sampling
- Fixed values for the unlisted eighth frequency (21 GHz listed, only 7 named)

## Analysis recipe

1. **Image ALMA data and derive limits**: tclean imaging per epoch; rms in 10" box; 3 sigma limits at AT2017gfo position  
  > "The cleaning process was repeated until no clear emission was left." (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **GMRT reduction and limits**: AIPS standard reduction; rms from source-free regions with TVSTAT  
  > "the r.m.s. level is estimated from source-free regions using the task TVSTAT" (2.2 GMRT Observations)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with GRB samples**: Compare luminosity limits to sub-mm/radio GRB samples and Swift X-ray light curves; compute Eiso distribution median/dispersion  
  > "computed with (PY)MULTINEST" (3.1)
   - software: PyMultiNest, Swift Burst Analyser
   - fitting: _not stated_
   - validation: _not stated_
4. **Broadband off-axis afterglow modeling**: BOXFIT 9-parameter templates in homogeneous ISM across 1.4 GHz-X-ray  
  > "We fix the fractions of $\epsilon_e$ and $\xi_N$ at 0.1 and 1, respectively, and $p$ to 2.43 and the redshift to 0.009854." (3.2)
   - software: BOXFIT
   - parameter: theta_jet 5-45 deg, E_AG,iso 1e47-1e53 erg, eps_B 1e-5-1e-2, n 1e-4-1e-1, theta_obs 0-45 deg  
  > "E$_{\rm AG,\,iso} = 10^{47}$–$10^{53}$ erg, $\epsilon_B = 10^{-5}$–$10^{-2}$" (3.2)
   - assumption: epsilon_e=0.1, xi_N=1, p=2.43, z=0.009854  
  > "and $p$ to 2.43 and the redshift to 0.009854" (3.2)
   - fitting: best-matching templates identified; method not stated  
  > "The best-matching templates (colored curves in Fig. [3](#fig:lc)) strongly argue for a GRB seen off-axis" (Results and discussion, Modeling the broadband afterglow)
   - validation: Azimuthal resolution 20/30 compared with 70: flux within 20%  
  > "able to recover the absolute flux scale at maximum to within 20%" (3.2)
5. **Infer Gamma0 and true energetics**: Top-hat jet finite-size analytic Egamma,off and Epeak,off vs Gamma0 parameter study  
  > "we assume a top-hat jet, similar to (cite: Troja:nature) and (cite: GRB2017a), but we take into account the finite size of the jet" (3.3)
   - parameter: Epeak varied 123-8400 keV; Egamma/EAG 0.05-40  
  > "Hence, we vary $E_{\rm peak}$ between 123 keV and 8400 keV." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
6. **Merger ejecta radio emission**: Nakar & Piran 2011 scaling for non-relativistic ejecta  
  > "we estimate the brightness at $1.4$ GHz to be $\sim60~\mu\rm Jy$ for a deceleration time scale of 55 years" (3.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: ALMA reduction and imaging  
  > "CASA) version 4.7.2" (2.1 ALMA observations)
- **AIPS** : GMRT data reduction  
  > "Data reduction was carried out with the NRAO ASTRONOMICAL IMAGE PROCESSING SOFTWARE" (2.2 GMRT Observations)
- **BOXFIT** 2: off-axis afterglow templates  
  > "using BOXFIT version 2" (3.2)
- **PyMultiNest** : SGRB Eiso distribution median and dispersion  
  > "computed with (PY)MULTINEST" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 338.5 GHz 3sigma limit at 1.4 d | <126 | not stated | uJy | 1 | $F_{\rm 338.5\,{\rm GHz}}<$126 $\mu$Jy at 1.4 days |
| Luminosity limit | 3e26 | not stated | erg/s/Hz | 1 | corresponds to a luminosity of $3\times10^{26}~{\rm erg\,s}^{-1}\,{\rm Hz}^{-1}$ |
| NGC 4993 nucleus flux at 338.5 GHz | 1.07 | 0.21 | mJy | 1 | We measure $1.07\pm0.21$ mJy at 338.5 GHz. |
| Model 1 theta_obs | 41 | not stated | deg | 4 | The jet axis and the line of sight are misaligned by $41^\circ$. |
| Gamma0 upper limits | <15 (Model 1), <43 (Model 2) | not stated | dimensionless | 5 | $\Gamma_0<15$ and $\Gamma_0<43$ for *Model 1* and *Model 2* |
| Optical afterglow contamination of kilonova | <1 | not stated | % | 4 | The contamination by the afterglow in the optical is negligible ($<1\%$) |

## Qualitative findings

- Afterglow undetected in ALMA/GMRT; emergence of X-ray/radio after a week requires off-axis jet; consistent with SGRB population  
  > "The afterglow evaded detection at all epochs." (4 Summary)

## Claim tuples

- H: Is GRB 170817A's afterglow consistent with an on-axis GRB? | E: Compare limits and light curves with on-axis and off-axis BOXFIT templates | R: On-axis models fail; off-axis models with theta_obs>theta_jet match | F: Off-axis afterglow of an SGRB associated with GW170817 | **supported**
- H: Can two jet geometries explain the data? | E: Fit wide and narrow jet templates | R: Wide: ~20 deg, 41 deg view; narrow: ~5 deg, 17 deg view | F: Degenerate parameters; more data needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: On-axis afterglow models rejected  
  > "This evolution is in stark contrast to observations of AT2017gfo." (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Degeneracy due to few detections and large Epeak uncertainty  
  > "Limiting this parameter study is the degeneracy in the afterglow parameters" (4 Summary)
- Caveat (inferred, ours): Fit procedure and goodness-of-fit not described
- Caveat (inferred, ours): Narrow-jet viewing angle quoted inconsistently (17 vs ~20 deg)
- Caveat (inferred, ours): Radio flux conversions from relative measurements are approximate

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model-fit procedure
- Missing: tclean parameters
- Missing: Data table of public points used
- Data volume (inferred): ~tens of GB (six ALMA epochs)
- Score (inferred): 3/5, ALMA limits straightforward, but modeling selection of best templates not specified.
- Rediscovery candidate: no, Main results depend on a non-specified modeling choice; ALMA part is only non-detections.

## Links

- Method: van Eerten et al. 2012 (cite: vanEerten2012) (BOXFIT method)
- Companion: Troja et al. 2017 (cite: Troja:nature) (X-ray afterglow detection)
- Related: Swift GRB sample

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
