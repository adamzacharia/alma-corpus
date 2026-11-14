# A Potential Link between Nuclear Winds and Cold Gas Outflows on Kiloparsec Scales in Reionization-era Quasars

`2026ApJ..1000..312Z` | The Astrophysical Journal 2026 | first author: Zhu, Yongda | arXiv: 2504.02305 | DOI: 10.3847/1538-4357/ae4ed1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Are nuclear winds (BALs) in z~5.5 quasars connected to kpc-scale cold gas outflows traced by broad [C ii] wings in stacked profiles?  
  > "Investigating whether such small-scale winds are physically connected to larger-scale gas dynamics is crucial for understanding early SMBH–galaxy co-evolution." (Introduction)
- Target **17 quasars at z~5.5 (Table; 16 used in stacks), e.g. J0012+3632**: coordinates see Table (e.g. J0012+3632 00:12:32.88 +36:32:16.10)  
  > "| 1 | J0012$+$3632 | 00:12:32.88 | $+$36:32:16.10 | $5.485 \pm 0.001$ | -27.2 | **5650.9** | 2021-10 |" (Table 1); z/distance z_[CII] = 5.38-5.79  
  > "| 1 | J0012$+$3632 | 00:12:32.88 | $+$36:32:16.10 | $5.485 \pm 0.001$ | -27.2 | **5650.9** | 2021-10 |" (Table 1); distance from systemic redshift from Gaussian fit to [C II]  
  > "| 1 | J0012$+$3632 | 00:12:32.88 | $+$36:32:16.10 | $5.485 \pm 0.001$ | -27.2 | **5650.9** | 2021-10 |" (Table 1)

## Data provenance

- ALMA projects: 2022.1.00662.S
- bands: Band 7  
  > "we conducted ALMA Band 7 observations targeting 21 quasars at $z \sim 5.5$" (2.1 ALMA Observations)
- frequencies and spectral setup: two overlapping spws covering [C II], two spws for continuum  
  > "Each observation employed two overlapping spectral windows fully covering the [C ii] line at the expected redshift, alongside two additional spectral windows for dust continuum measurements." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-(1, 2, and 3)  
  > "The observations used the C43-(1, 2, and 3) configurations" (2.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: ~1 arcsec  
  > "achieving an angular resolution of $\sim 1''$ across the entire sample." (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: ~0.25 mJy/beam per 30 MHz bin (average RMS)  
  > "The average RMS noise level across the dataset is $\sim 0.25\ {\rm mJy\,beam^{-1}}$ per 30 MHz bin." (2.1 ALMA Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 9, PI Zhu  
  > "In Cycle 9 (2022.1.00662.S; PI: Zhu)" (2.1 ALMA Observations)
- Line: [C II] 158 um fine-structure (not stated)
- Other facility **Keck/ESI**: rest-UV spectra to identify BALs (Si IV, C IV)  
  > "We acquired the Keck/ESI spectra for most quasars in this sample, which we use to identify BAL features in the rest frame UV." (2.2 ESI Spectra)
- Other facility **SSO-2.3m/WiFeS and Palomar P200/DBSP**: existing confirmation spectra for J1006, J1048, J1614  
  > "we used existing confirmation spectra from (cite: yang_discovery_2017; yang_filling_2019)" (2.2 ESI Spectra)
- External data: quasar sample selection and M1450 luminosities  
  > "We use the brightest quasars in the $z$-band ($m_{z} \lesssim 20$) selected by Yang et al." (2 Data) [from (cite: yang_discovery_2017; yang_filling_2019)]
- External data: BAL hydrogen column density N_H = 10^20.1-22.6 cm^-2  
  > "we adopt a hydrogen column density of $N_{\rm H} = 10^{20.1\sim 22.6}\ \rm cm^{-2}$ (cite: xu_vltx-shooter_2019)" (4.2 Energetics) [from (cite: xu_vltx-shooter_2019)]
- External data: BAL covering fraction f_cov = 0.2  
  > "assuming covering fraction of $f_{\rm cov} = 0.2$ (cite: hewett_frequency_2003)" (4.2 Energetics) [from (cite: hewett_frequency_2003)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "Data calibration and reduction were performed using the CASA pipeline (version 6.4.1.12;" (2.1 ALMA Observations)
- casa version: 6.4.1.12  
  > "Data calibration and reduction were performed using the CASA pipeline (version 6.4.1.12;" (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Imaging was performed with `tclean`, using natural weighting to optimize sensitivity." (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Imaging was performed with `tclean`, using natural weighting to optimize sensitivity." (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-domain, first-order polynomial, all line-free channels across four spws  
  > "Continuum subtraction was conducted in the $uv$-domain using all line-free channels across the four spectral windows by fitting a first-order polynomial" (2.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- data cube generation and [C II] imaging procedures  
  > "We generated data cubes and imaged the [C ii] emission following procedures outlined in (cite: eilers_detecting_2020)." (2.1 ALMA Observations) [from (cite: eilers_detecting_2020)]
- ESI reduction pipeline  
  > "following procedures described in (cite: becker_evolution_2019) and (cite: zhu_probing_2023)" (2.2 ESI Spectra) [from (cite: becker_evolution_2019); (cite: zhu_probing_2023)]
- outflow velocity and mass computed following prior work  
  > "The outflow velocity is computed in the standard way following e.g., (cite: bischetti_widespread_2019)" (4.2 Energetics) [from (cite: bischetti_widespread_2019)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, and channel width of cubes
- Line-free channel ranges per source
- Flux calibrators and flux-scale uncertainty
- Exact BAL BI0 continuum fitting details and ESI spectra reduced products
- How peak normalization and significance (mean S/N within FWHM) are computed
- Initial guesses/bounds for the two-Gaussian fit beyond sigma limit
- Details of how L_[CII] of broad component is converted to mass (T and n choices) and how the efficiency range is propagated

## Analysis recipe

1. **Extract [C II] spectra and systemic redshifts**: Single-beam aperture spectra centered on each source; Gaussian fit to line gives systemic redshift  
  > "Spectra were extracted using a single-beam aperture centered on each source to minimize contamination from extended [C ii] emission and complex host galaxy kinematics." (2.1 ALMA Observations)
   - software: CASA
   - fitting: Gaussian profile fit to [C II]  
  > "We determined the systemic redshift for each quasar by fitting a Gaussian profile to the [C ii] emission line." (2.1 ALMA Observations)
   - validation: 2-beam aperture test reduced BAL broad-wing significance from 4.45 to 3.3 sigma  
  > "the broad wing detection significance decreased from 4.45 (Section [3](#sec:results)) to 3.3$\sigma$" (2.1 ALMA Observations)
2. **Classify BAL vs non-BAL quasars**: Compute BI0 from power-law-normalized ESI spectra; BAL if BI0 > 1000 km/s  
  > "we classify only quasars with significant BAL features ($\rm BI_0 > 1000\ \rm km\, s^{-1}$) as BAL quasars." (2.2 ESI Spectra)
   - parameter: power-law continuum fit over rest 1285–1450 A; vmin=0, vmax=64500 km/s  
  > "we normalized observed fluxes by fitting a power-law continuum to each quasar spectrum in the rest-frame wavelength range of 1285–1450 Å" (2.2 ESI Spectra)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stack [C II] spectra**: Normalize by peak flux, shift to systemic redshift, inverse-variance weighted mean in 60 km/s bins; 1000 bootstraps for variance  
  > "we normalize each spectrum by its peak flux, shift the [C ii] emission line to the systemic redshift, and compute the mean stack in velocity space" (3 Stacked [C II] Spectra)
   - parameter: 5 BAL and 11 non-BAL spectra; J0056+2241 excluded  
  > "We create stacked [C ii] spectra for the five strong BAL quasars and eleven non-BAL quasars, respectively." (3 Stacked [C II] Spectra)
   - fitting: _not stated_
   - validation: image-plane cube stacking gives 4.48 sigma for BAL; random 5-quasar non-BAL stacks give <2% chance of S/N>=4.4  
  > "we find that the cumulative probability of randomly obtaining a broad wing with a significance equal to or greater than S/N = 4.4 is less than 2%" (4.3 Intrinsic Properties)
4. **Fit two-component Gaussian to stacks**: Narrow (sigma<500 km/s, center fixed at 0) plus broad (sigma>500 km/s, free center); uncertainties from bootstrap  
  > "The narrow component’s line center is fixed at $\Delta v = 0$, while the broad component’s center is allowed to vary." (3 Stacked [C II] Spectra)
   - fitting: two-Gaussian model; uncertainties from bootstrap realizations; optimizer not stated  
  > "We derive uncertainties in the fit parameters based on the stacked fluxes across the bootstrap realizations." (3 Stacked [C II] Spectra)
   - validation: jackknife, FWHM split, velocity-normalized stacks, M1450 split  
  > "we performed jackknife tests by excluding one BAL quasar at a time and re-stacking the remaining four." (4.4 Robustness)
5. **Estimate outflow energetics and coupling efficiency**: Compute BAL and [C II] outflow kinetic powers, eta = Edot_out/Edot_BAL  
  > "the coupling efficiency between the BAL and [C ii] outflows is" (4.2 Energetics)
   - parameter: R_out([CII]) = 3.0 kpc; BAL R_out 1-100 pc; v_BAL = 2.5e4 km/s; T ~ 100–1000 K; n >> n_crit  
  > "we adopt an outflow radius of 3.0 kpc, matching the mean ALMA beam size" (4.2 Energetics)
   - assumption: X_C+ = 1e-4; mu = 1.4; broad component primarily AGN-driven  
  > "The energetics discussed below therefore represent AGN coupling efficiency, assuming the [C ii] broad component is primarily AGN-driven." (4.1 Nuclear Winds)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.1.12: calibration, imaging (tclean), continuum subtraction  
  > "Data calibration and reduction were performed using the CASA pipeline (version 6.4.1.12;" (2.1 ALMA Observations)
- **IDL/GDL custom pipeline** : ESI spectral reduction  
  > "The data were reduced using a custom IDL/GDL(cite: coulais_status_2010) pipeline" (2.2 ESI Spectra)
- **astropy** : Planck18 cosmology  
  > "we adopt the `Planck18` cosmology (cite: planck_collaboration_planck_2020), implemented in `astropy`" (Introduction)
- **CARTA** : listed in software; use not specified  
  > "`CARTA` (cite: comrie_carta_2021)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| BAL stack broad component velocity offset | -2.1e2 | +1.3/-0.7 e2 | km/s | 4 | $\Delta v_{\rm b} = -2.1_{-0.7}^{+1.3}\times 10^2 \, \rm km\,s^{-1}$ |
| BAL stack broad component FWHM | 1.18e3 | +0.39/-0.35 e3 | km/s | 4 | a FWHM of $1.18_{-0.35}^{+0.39} \times 10^3 \, \rm km\,s^{-1}$ |
| BAL broad wing significance | 4.45 | not stated | sigma | 4 | detected with a mean signal-to-noise ratio of 4.45 within its FWHM |
| Broad flux fraction | 0.32 | 0.11 | dimensionless | 5 | $F_{\rm broad} / F_{\rm total} = 0.32 \pm 0.11$ |
| [C II] outflow velocity | 8.0e2 | 2.1e2 | km/s | 5 | (8.0 \pm 2.1) \times 10^2\ \rm km\,s^{-1} |
| Outflow mass | 9.3e8 | 0.2e8 | Msun | 5 | $M_{\rm out} = (9.3 \pm 0.2) \times 10^8 M_\odot$ |
| Coupling efficiency | 0.025 | +0.23/-0.022 | dimensionless | 5 | \eta = \frac{\dot{E}_{\rm out}}{\dot{E}_{\rm BAL}} = 0.025_{-0.022}^{+0.23} |
| Narrow component FWHM, BAL vs non-BAL stacks | 320 vs 430 | not stated | km/s | 4 | ($\rm FWHM = 3.2\times10^2\,km\,s^{-1}$) than that of the non-BAL case ($\rm FWHM = 4.3\times10^2\,km\,s^{-1}$) |

## Qualitative findings

- Non-BAL stack shows no significant broad component (<2 sigma).  
  > "the non-BAL stack does not exhibit a significant broad component, and the broad residual has a detection significance below $2\sigma$." (3 Stacked [C II] Spectra)

## Claim tuples

- H: BAL quasars show broad [C II] wings not seen in non-BAL quasars | E: Stack [C II] spectra of 5 BAL and 11 non-BAL quasars; fit two Gaussians | R: BAL stack broad component at 4.45 sigma, offset -210 km/s, FWHM 1180 km/s; non-BAL <2 sigma | F: Potential link between nuclear winds and kpc-scale cold outflows, with caveat of small-sample probability ~2% | **partially**
- H: BAL winds transfer energy to cold gas | E: Compare kinetic powers of BAL and [C II] outflows | R: eta = 0.025 (+0.23/-0.022) | F: A few percent to one-quarter of wind energy may couple, assuming AGN-driven | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-beam aperture chosen to avoid dilution; supported by 2-beam test  
  > "This supports our choice of using the single-beam aperture for the fiducial analysis." (2.1 ALMA Observations)
- Alternative: UV-plane stacking deemed unnecessary due to uniform setup; image-plane stacking used as check  
  > "Therefore, UV-plane stacking was unnecessary for our study." (4.4 Robustness)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot disentangle AGN- vs star formation-driven outflows  
  > "we caution that our stacking analysis cannot unambiguously disentangle AGN- and star formation-driven outflows." (4.1 Nuclear Winds)
- Caveat (inferred, ours): Tiny BAL sample (5); significance only ~4.5 sigma and not robust under jackknife/normalization (~2.8 sigma)
- Caveat (inferred, ours): BAL classification uncertain with incomplete ESI coverage
- Caveat (inferred, ours): Orientation/host-property confounds
- Caveat (inferred, ours): Energetics span large assumption ranges

## Reproducibility

- Data public (paper): ALMA project cited by code; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.00662.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, channels)
- Missing: ESI spectra products
- Missing: Fit initialization and significance definition
- Data volume (inferred): ~50-150 GB raw for 21 Band 7 short observations
- Score (inferred): 3/5, Simple stacking recipe with stated data, but several imaging and fitting details missing and ESI data required.
- Rediscovery candidate: no, Needs ESI spectra for BAL classification and unspecified details; results are numeric but recipe is incomplete.

## Links

- Method: (cite: eilers_detecting_2020) (cube imaging procedures)
- Method: (cite: novak_no_2020) (stacking approach and normalization comparison)
- Companion: (cite: zhu_probing_2023) (details of ALMA program and ESI reduction)
- Related: XQR-30

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
