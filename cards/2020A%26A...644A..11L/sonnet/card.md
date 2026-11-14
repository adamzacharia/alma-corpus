# A statistical analysis of dust polarization properties in ALMA observations of Class 0 protostellar cores

`2020A&A...644A..11L` | Astronomy and Astrophysics 2020 | first author: Le Gouellec, V. J. M. | arXiv: 2009.07186 | DOI: 10.1051/0004-6361/202038404

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Do the statistics of polarization fraction and polarization angle dispersion (S, Pfrac, S x Pfrac) in ALMA maps of Class 0 protostellar envelopes constrain dust grain alignment efficiency, and how do they compare with Planck results and MHD simulations with RATs or perfect alignment?  
  > "we have gathered a dozen ALMA maps of (sub)millimeter-wavelength polarized dust emission from Class 0 protostars, and carried out a comprehensive statistical analysis of dust polarization quantities." (abstract)
- Target **Serpens Emb 6, Emb 8, Emb 8(N), BHR71 IRS1/IRS2, B335, IRAS 16293A/B, VLA 1623A/B, L1448 IRS2, OMC3 MMS6, NGC1333 IRAS4A**: coordinates per-source J2000 coordinates in the ALMA cores table (e.g. Serpens Emb 6 18:29:49.81 +01:15:20.41)  
  > "a sample of fifteen ALMA observations toward eleven Class 0 protostellar cores" (Conclusions); "| Serpens Emb 6    | 18:29:49.81               | 01:15:20.41               | 27.2                 | 134.6                  | 111.3$^*$              | 484       | C,E          |   |" (Table 6); z/distance 165-484 pc (e.g. B335 165 pc, BHR71 200 pc, IRAS 16293 144 pc, L1448 IRS2 294 pc, OMC3 MMS6 432 pc, Serpens 484 pc)  
  > "a sample of fifteen ALMA observations toward eleven Class 0 protostellar cores" (Conclusions); "| Serpens Emb 6    | 18:29:49.81               | 01:15:20.41               | 27.2                 | 134.6                  | 111.3$^*$              | 484       | C,E          |   |" (Table 6); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00726.S, 2017.1.00655.S, 2013.1.01380.S, 2017.1.01392.S, 2018.1.01873.S, 2015.1.01112.S, 2016.1.00604.S, 2015.1.00341.S, 2016.1.01089.S, 2015.1.00546.S
- bands: 0.87, 1.3, 1.5 and 3.0 mm continuum polarization  
  > "at wavelengths ranging from 870 $\mu$m to 3 mm" (Conclusions)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: publicly available archival data; Stokes maps provided by authors of the original publications  
  > "We use the three Stokes maps provided by the authors of the corresponding publications" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- Other facility **Herschel (Gould Belt survey, PACS 70 um)**: internal luminosities and archival 70 um fluxes for dust temperature  
  > "we derived the internal luminosities using archival fluxes at 70 $\mu$m from *Herschel* PACS using the relation from (cite: Dunham2008)" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- Other facility **Planck**: comparison statistics (S proportional to Pfrac^-1) from literature  
  > "shallower than the $\mathcal{S} \propto \mathcal{P_{\rm{frac}}}^{-1}$ relationship found at larger scales in the *Planck* observations" (4.1)
- External data: Stokes I, Q, U maps for all sources except NGC1333 IRAS4A  
  > "We use the three Stokes maps provided by the authors of the corresponding publications" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores) [from Hull2017a; Hull2017b; Maury2018; Sadavoy2018a; Sadavoy2018b; Kwon2019; LeGouellec2019a; Takahashi2019; Hull2020a; Ko2019]
- External data: dust opacity kappa_nu  
  > "$\kappa_\nu$ is the opacity at a specific wavelength taken from (cite: Ossenkopf1994)" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores) [from (cite: Ossenkopf1994)]
- External data: internal luminosities for some sources  
  > "the internal luminosities are known from the *Herschel* Gould Belt survey (cite: Andre2010)" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores) [from (cite: Andre2010)]
- Simulation/model as data: six RAMSES non-ideal MHD collapse simulations, post-processed with POLARIS (RATs or perfect alignment) and filtered with the CASA simulator  
  > "We use six different setups for the simulations performed with the RAMSES code" (Appendix MHD simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.4  
  > "using the task `tclean` in version 5.4 of CASA" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: four rounds of phase-only self-calibration (NGC1333 IRAS4A only)  
  > "We applied four rounds of consecutive phase-only self-calibration, using the total intensity (Stokes $I$) solutions as the model" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)

### Imaging

- task: tclean (NGC1333 IRAS4A)  
  > "We produced the polarized dust continuum images using the task `tclean` in version 5.4 of CASA" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- deconvolver: _not stated_
- weighting robust: robust = 1  
  > "with a Briggs weighting parameter of `robust` = 1" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- uv taper: _not stated_
- cell size: regridded to Nyquist, 4 pixels per beam area  
  > "We regrid the maps of the three Stokes parameters $I$, $Q$, and $U$ to a Nyquist sampling, with exactly 4 pixels per beam in terms of area." (3.1)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not applied to Q/U/I for statistics; Stokes I corrected only for column density  
  > "we do not perform any primary beam correction at this step of the analysis" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- S and Pfrac statistical method, 5-sigma S/N pixel-selection and analytical model  
  > "We follow the method introduced in (cite: Planck2018XII) to compute a pixel-selection criterion" (3.1) [from (cite: Planck2018XII)]
- debiasing of polarized intensity  
  > "we follow the method from (cite: WardleKronberg1974)" (3.1) [from (cite: WardleKronberg1974); (cite: Hull2015b)]
- dust temperature profile  
  > "following (cite: Terebey1993) and (cite: Motte2001)" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores) [from (cite: Terebey1993); (cite: Motte2001)]
- internal luminosity from 70 um flux  
  > "using the relation from (cite: Dunham2008)" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores) [from (cite: Dunham2008)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging parameters (robust, masks, thresholds) for the other datasets, which are only referenced to earlier papers
- Exact fitting method (least-squares vs other) and weights for the log-log S vs Pfrac fit
- How the S x Pfrac mean and asymmetric uncertainties were computed (bins, running mean)
- IRAS4A project code, beam and noise values
- Outflow cavity geometry fitted by eye
- Epoch and parameters of the CASA simulator inputs (beyond configurations C-3, C-5, C-6, 6000 s)
- Simulation outputs and POLARIS setup files

## Analysis recipe

1. **Image NGC1333 IRAS4A**: self-calibrate and clean Stokes I, Q, U separately  
  > "The three Stokes parameters $I$, $Q$, and $U$ were cleaned separately after the last round of self-calibration" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
   - software: CASA
   - parameter: robust = 1, four phase-only selfcal rounds  
  > "with a Briggs weighting parameter of `robust` = 1" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive column density and temperature**: optically thin dust emission with radial T_d(r) from central heating  
  > "assuming the dust emission recovered in the ALMA observations (at scales of 10–2000 au) is optically thin, we calculate the column density" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
   - parameter: T_d = 38 K (r/100 au)^-0.4 (Lint/Lsun)^0.2  
  > "T_d(r) = 38\,K\,\left(\frac{r}{100\,\textrm{au}}\right)^{-0.4} \left(\frac{L_\textrm{int}}{1 L_\odot}\right)^{0.2}" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
   - assumption: gas-to-dust ratio 100, mu_H2 = 2.8, Ossenkopf & Henning opacity; pixels with scattering or optically thick emission excluded  
  > "We assume a gas-to-dust ratio of 100." (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute P, Pfrac, S per pixel with noise cutoff**: debiased P, S from 8 nearest neighbours, Stokes I cutoff where mean P/sigma_P = 5 (min 5 sigma_I)  
  > "Note that if this method provides a threshold limit of Stokes $I$ below $5\,\sigma_I$, we chose $5\,\sigma_I$ as the cutoff for the dataset." (3.1)
   - software: Python
   - parameter: n = 8 neighbours, 4 pixels per beam, lag about half a beam  
  > "the equivalent $\delta$ parameter (see also Equation [\[equ:S_def\]](#equ:S_def)) is approximately $1/2$ of a beam width" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit S vs Pfrac power law**: linear fit in log-log space per dataset and merged, excluding Pfrac < 1.3% saturated region  
  > "we establish a threshold in $\mathcal{P_{\rm{frac}}}$ of $1.3\%$" (3.2)
   - fitting: S = f / Pfrac^alpha; fitting algorithm not stated  
  > "which is defined by the two parameters $\alpha$ and $f$ such that $S\,=\,f/{\mathcal{P_{\rm{frac}}}^{\alpha}}$" (3.2)
   - validation: threshold chosen where alpha stops changing  
  > "determining where the $\alpha$ value from the linear fit would no longer have changed if we had moved the threshold up in polarization fraction" (3.2)
5. **S x Pfrac versus column density**: merged distribution versus N_H2 and normalized N_H2; split by luminosity (10 Lsun) and outflow cavity vs envelope  
  > "First, we separate the “low” and “high” luminosity cores" (4.2.2)
   - assumption: isotropic turbulent field component so S x Pfrac traces alignment efficiency  
  > "it is reasonable to assume that $\mathcal{S}\times\mathcal{P_{\rm{frac}}}$ traces the intrinsic capability of dust grains to align themselves" (4.2.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **Synthetic observations of MHD models and filtering test**: POLARIS radiative transfer (RATs or PA) at 870 um, then CASA simulator with C-3, C-5, C-6, 6000 s each, same statistics  
  > "we combine synthetic observations from ALMA configurations C-3, C-5, and C-6, with an exposure time of 6000 s per antenna configuration" (Appendix MHD simulations)
   - software: RAMSES, POLARIS, CASA
   - parameter: grains 62.5% silicate/37.5% graphite, MRN, a_min 2 nm, a_max 10 um, aspect ratio 0.5, G0=1, 400 pc, 80 au beam  
  > "cutoff sizes of $a_\textrm{min}\,=\,2\,\textrm{nm}$ and $a_\textrm{max}\,=\,10\,\mu\textrm{m}$" (Appendix MHD simulations)
   - fitting: _not stated_
   - validation: Planck maps placed at ALMA scales and filtered as test: index 0.94 to 0.48  
  > "from an initial 0.94 before filtering to 0.48 after filtering" (4.1.3)
7. **Power spectra of Stokes I, Q, U**: 2D FFT, normalized magnitude, azimuthal average  
  > "we perform 2D Fourier transforms of the Stokes $I$, $Q$, and $U$ maps and take their normalized absolute magnitude" (Appendix Power spectra)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4: tclean imaging of IRAS4A; simulator for synthetic filtering  
  > "using the task `tclean` in version 5.4 of CASA" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- **POLARIS** : radiative transfer and Stokes maps of MHD simulations  
  > "We perform radiative transfer on these models using the POLARIS code" (4.1.3)
- **RAMSES** : non-ideal MHD collapse simulations  
  > "computed with RAMSES" (4.1.3)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)
- **Astropy** : listed software  
  > "Astropy (cite: Astropy2018)" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Merged power-law index alpha of S vs Pfrac | 0.79 | 0.03 | dimensionless | 4 | We obtain a power law index $\alpha\,=\,0.79\,\pm\,0.03$ |
| Pfrac threshold for fit | 1.3 | not stated | % | 4 | we establish a threshold in $\mathcal{P_{\rm{frac}}}$ of $1.3\%$ |
| Mean S x Pfrac | 0.36 | +0.10/-0.17 | dimensionless | 5 | with a mean value of $0.36^{+0.10}_{-0.17}$ |
| Per-core alpha range | 0.523 to 0.866 | 0.094 and 0.040 | dimensionless | 4 | These values range from $\alpha =0.523 \pm 0.094$ to $\alpha = 0.866 \pm 0.040$. |
| Alpha for Planck maps before/after ALMA-like filtering | 0.94 / 0.48 | not stated | dimensionless | 6 | from an initial 0.94 before filtering to 0.48 after filtering |

## Qualitative findings

- Observed S x Pfrac exceeds RAT model predictions and is consistent with perfect alignment  
  > "the observed $\mathcal{S}\times\mathcal{P_{\rm{frac}}}$ values are overall larger than those predicted by models with dust grains aligned via RATs" (4.2.3)
- Low-luminosity cores show S x Pfrac decreasing with column density; high-luminosity cores flat  
  > "the distribution from the low-luminosity cores shows a clear decrease in $\mathcal{S}\times\mathcal{P_{\rm{frac}}}$ as a function of column density" (4.2.2)

## Claim tuples

- H: Core-scale S-Pfrac correlation matches Planck cloud-scale relation | E: Fit S vs Pfrac in 15 ALMA maps | R: alpha = 0.79 +/- 0.03 vs -1 for Planck | F: Shallower correlation; possible causes are different turbulence, filtering and local alignment | **supported**
- H: Grain alignment efficiency varies with column density | E: S x Pfrac versus N_H2 | R: approximately constant at 0.36 | F: Alignment mechanism not systematically dependent on local density | **supported**
- H: Standard RATs reproduce observed alignment efficiency | E: Compare ALMA with POLARIS synthetic observations | R: ALMA S x Pfrac higher than RATs, near PA | F: Alignment more efficient than standard RATs | **supported**
- H: Low-luminosity cores have less efficient alignment at high column density | E: Split sample at 10 Lsun | R: decrease in low-luminosity cores | F: only a hint | **partially**
- H: Interferometric filtering and differing scales of I vs Q/U bias Pfrac | E: Power spectra and filtered synthetic maps | R: Q/U have more power at large scales; filtering raises S and Pfrac | F: artificially high Pfrac | **partially**

## Reasoning

- Why this data: Class 0 envelopes dominate dust emission and give most polarization detections; selected extended polarized emission  
  > "we selected observations with the most extended polarized dust emission" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- Why this method: _not stated_
- Alternative: New estimator Pi gives only marginally different results so not adopted  
  > "These plots show that the results are only marginally different, and thus we do not recompute our results using this new estimator." (Appendix Pi)
- How they decided it was enough: _not stated_
- Limitation (authors): Significant uncertainty in reliability of Pfrac due to filtering and different scales  
  > "there is significant uncertainty in the reliability of the calculated values of $\mathcal{P_{\rm{frac}}}$" (4.1.3)
- Limitation (authors): Simulations do not reproduce the observed morphologies, and massive ones are axisymmetric and unturbulent  
  > "these simulations do not have initial turbulence, and are quite axisymmetric at the time steps we choose" (4.2.3)
- Caveat (inferred, ours): Heterogeneous datasets with unequal weights and different resolutions
- Caveat (inferred, ours): Isotropic turbulence assumption for S x Pfrac may fail in collapsing cores
- Caveat (inferred, ours): Only six simulation outputs, with sink masses larger than observed
- Caveat (inferred, ours): Self-scattering and optically thick pixels removed only approximately
- Caveat (inferred, ours): Fit uncertainties likely ignore correlated pixels

## Reproducibility

- Data public (paper): publicly available ALMA data  
  > "We gathered publicly available ALMA dust polarization observations" (2.2 ALMA observations of polarized dust emission in Class 0 protostellar cores)
- Products in archive: _not stated_
- Missing: Stokes maps from original authors or full re-reduction
- Missing: Simulation snapshots and POLARIS configuration
- Missing: Fitting code
- Data volume (inferred): Tens to hundreds of GB raw if re-reducing; small if using published Stokes maps
- Score (inferred): 3/5, Public data and clear statistical recipe, but Stokes maps come from other papers, most imaging details are not given, and the simulations are not available.
- Rediscovery candidate: no, Requires many externally produced Stokes maps and unreleased simulations, so the recipe is incomplete.

## Links

- Method: (cite: Planck2018XII) (statistical method and analytical model)
- Method: (cite: WardleKronberg1974) (debiasing P)
- Method: (cite: Reissl2016) (POLARIS code)
- Companion: (cite: Hull2020a) (BHR71 data and analysis)
- Companion: (cite: LeGouellec2019a) (Serpens data)
- Related: Herschel Gould Belt survey

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 49,
  "rate": 0.544
 },
 "evidence_ok": true
}
```
