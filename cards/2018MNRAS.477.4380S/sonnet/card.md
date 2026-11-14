# Testing star formation laws in a starburst galaxy at redshift 3 resolved with ALMA

`2018MNRAS.477.4380S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Sharda, P. | arXiv: 1712.03661 | DOI: 10.1093/mnras/sty886

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, star_formation
- Question: Do existing star formation laws (KS, KDM12, SFK15) reproduce the SFR surface density of the brightest clump in lensed starburst SDP 81, and what is the role of turbulence?  
  > "Our measurements of gas surface density, freefall time and turbulent Mach number allow us to compare the theoretical SFR from various star formation models with that observed" (abstract)
- Target **SDP 81 (J090311.6+003906), clump A**: coordinates RA = 09h03m11.57s, Dec = +00d39m06.6s  
  > "ALMA observations of SDP 81 (RA = $09^\mathrm{h}03^\mathrm{m}11.57^\mathrm{s}$, Dec = $+00^{\circ}39'06.6''$)" (2 Data Reduction and Analysis); "the redshift was measured as $z = 3.042\pm0.001$ through ground based CO measurements" (1 Introduction); z/distance z = 3.042; D_L = 25.9 Gpc  
  > "ALMA observations of SDP 81 (RA = $09^\mathrm{h}03^\mathrm{m}11.57^\mathrm{s}$, Dec = $+00^{\circ}39'06.6''$)" (2 Data Reduction and Analysis); "the redshift was measured as $z = 3.042\pm0.001$ through ground based CO measurements" (1 Introduction); distance from CO redshift from Negrello et al. 2010; luminosity distance from cosmology (Wright 2006 calculator)  
  > "ALMA observations of SDP 81 (RA = $09^\mathrm{h}03^\mathrm{m}11.57^\mathrm{s}$, Dec = $+00^{\circ}39'06.6''$)" (2 Data Reduction and Analysis); "the redshift was measured as $z = 3.042\pm0.001$ through ground based CO measurements" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Bands 4, 6, 7 (2.0, 1.3, 1.0 mm)  
  > "in ALMA Bands 4, 6 and 7, corresponding to $\lambda_{\mathrm{obs}}=2.0,1.3$ and $1.0$ mm, respectively" (2 Data Reduction and Analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~150x120 mas via uv tapering  
  > "Through $u\nu$ tapering, a resolution of $\sim150\times120\,\mathrm{mas}$ was achieved in the three bands" (2 Data Reduction and Analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: October 2014, Science Verification  
  > "were taken during Science Verification cycle in October 2014" (2 Data Reduction and Analysis)
- pi or archival as stated: _not stated_
- Line: CO 5-4 (observed at 142.57 GHz (Band 4))
- Other facility **Herschel SPIRE**: 350 um flux used in SED fit  
  > "from SPIRE observations" (3 Measurement of the Star Formation Rate)
- Other facility **VLA**: CO(1-0) data at lower resolution (not used for kinematics)  
  > "the CO$\,$(1-0) data was obtained by the Karl G. Jansky Very Large Array (VLA) at a lower resolution than ALMA" (5 Gas Mass and Freefall Time From CO (5-4))
- External data: Additional IR fluxes (350-2000 um) of SDP 81  
  > "reported in Table 2 of (cite: 2014MNRAS.440.1999N)" (3 Measurement of the Star Formation Rate) [from Negrello et al. 2014 (cite: 2014MNRAS.440.1999N)]
- External data: CO(5-4)/CO(1-0) line ratio r54 = 0.28±0.05 for clump A  
  > "This value was derived for $\mathrm{clump\,A}$ by S15" (5 Gas Mass and Freefall Time From CO (5-4)) [from Swinbank et al. 2015 (cite: 2015ApJ...806L..17S)]
- External data: Source-plane lens model and magnification factors (15.8±0.7, 16.0±0.7)  
  > "The average luminosity weighted magnification factors derived by (cite: 2015MNRAS.452.2258D) for the continuum in band 6 and 7 are $15.8 \pm 0.7$ and $16.0 \pm 0.7$ respectively." (2 Data Reduction and Analysis) [from Dye et al. 2015 (cite: 2015MNRAS.452.2258D)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated Science Verification data used  
  > "In the calibrated data[^2], the lensed galaxy is seen in the form of an Einstein ring" (2 Data Reduction and Analysis)
- flux calibrator: _not stated_
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
- smoothing: uv tapering; CO(5-4) cubes binned to 21 km/s  
  > "The CO$\,$(5-4) velocity cubes were binned to a velocity resolution of $21\,\mathrm{km}\,\mathrm{s}^{-1}$" (2 Data Reduction and Analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Source-plane reconstructed continuum and CO(5-4) flux/velocity maps and clump identification  
  > "created by S15, using the lensing model by (cite: 2015MNRAS.452.2258D)" (2 Data Reduction and Analysis) [from S15 (cite: 2015ApJ...806L..17S); Dye et al. 2015 (cite: 2015MNRAS.452.2258D)]
- Observed fluxes and noise levels  
  > "see Tables 1 and 3 of (cite: 2015ApJ...808L...4A) for observed fluxes and noise levels" (2 Data Reduction and Analysis) [from ALMA Partnership 2015 (cite: 2015ApJ...808L...4A)]
- Turbulent velocity gradient-subtraction approach  
  > "similar to the analysis of turbulent velocity dispersion done on the central molecular zone (CMZ) cloud Brick by (cite: 2016ApJ...832..143F)" (4 Mach Number Estimation) [from Federrath et al. 2016 (cite: 2016ApJ...832..143F)]

### Not stated but needed to reproduce (our reading)

- Source-plane reconstructed maps (S15) are not provided; need the lens model and the S15 reconstruction procedure
- Clump A pixel mask and the kernel sizes used for background subtraction
- Flux values for clump A in each band
- Derivation of the Toomre freefall time inputs for KDM12/SFK15 (galaxy-scale parameters)
- Number of MC iterations for SED fit and the fitting code details
- Data used for comparison sample of local regions in Fig 8

## Analysis recipe

1. **Background-subtract continuum and fit SED**: Mask clump A, smooth with large Gaussian, subtract; fit modified blackbody with fixed beta to galaxy-integrated then clump fluxes; MC error propagation  
  > "we fit the galaxy-integrated fluxes to constrain $T$ and $\beta_{\mathrm{em}}$; 2) we then adopt the 'galaxy-wide' $T$ and $\beta_{\mathrm{em}}$ to fit $\mathrm{clump\,A}$" (3 Measurement of the Star Formation Rate)
   - parameter: beta_em = 1.5, 2.0, 2.5 fixed; best fit beta=2.5, T=39±2 K  
  > "we fix $\beta_{\mathrm{em}}= 1.5, 2.0$ and $2.5$" (3 Measurement of the Star Formation Rate)
   - assumption: Clump A conditions identical to galaxy-wide T and beta  
  > "assume that the clump conditions (of $\mathrm{clump\,A}$) are identical to the galaxy-wide properties" (3 Measurement of the Star Formation Rate)
   - fitting: Monte Carlo with Gaussian flux uncertainties  
  > "we use Monte Carlo (MC) simulations (by modeling the uncertainties in the observed fluxes according to a Gaussian distribution) to find the bestfit MBB" (3 Measurement of the Star Formation Rate)
   - validation: Pixel-by-pixel vs whole-clump fits agree within 3%; Sersic+Gaussian model fluxes agree within 12%  
  > "The SFRs we obtain from both the methods agree well with each other, within $\pm\,3$%." (3 Measurement of the Star Formation Rate)
2. **Derive L_FIR and SFR surface density**: Integrate MBB 8-1000 um; apply Kennicutt 1998 L_FIR-SFR with factor 1.6 reduction for Chabrier IMF  
  > "we adjust its coefficient by a factor of 1.6 downward to adopt to "the Chabrier IMF"" (3 Measurement of the Star Formation Rate)
   - assumption: Chabrier IMF; H0=72, Om=0.27  
  > "We adopt the $\Lambda$CDM cosmology with H$_0 = 72\,\mathrm{km\,s}^{-1}\,\mathrm{Mpc}^{-1}$, $\Omega_\mathrm{m}$ = 0.27" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure turbulent velocity dispersion and Mach number**: Fit plane to CO(5-4) velocity map of clump A, subtract, take std of residuals; Mach number = sigma/c_s with c_s 0.2-0.6 km/s  
  > "we fit a large-scale gradient to the clump and subtract it" (4 Mach Number Estimation)
   - software: IDL PLANEFIT
   - parameter: Gas temperature assumed 10-100 K, mean molecular weight 2.33  
  > "for a mean molecular weight of 2.33" (4 Mach Number Estimation)
   - fitting: Least-squares plane fit; error from analytical formula and MC  
  > "performs a least-squares fit of a plane to set of ($x,y,z$) points" (4 Mach Number Estimation)
   - validation: Resolution degradation with superpixels (1/4, 1/16) changes dispersion by <20%  
  > "Since decreasing the resolution by $(1/4)$ does not alter the velocity dispersion by $\gtrsim\,20$%" (4.1 Resolution Check for Gradient Fit and Subtraction Algorithm)
4. **Derive gas mass, density, virial parameter, freefall time**: CO(5-4) luminosity via Solomon relation, r54, alpha_CO, +36% He; spherical clump; virial parameter and t_ff formulas  
  > "we assume $\alpha_{\mathrm{CO}} \approx 0.9\pm0.2\,$ $\mbox{$\mathrm{M}_{\ensuremath{\odot}}$}$ per ($\mathrm{K\,km}\,\mathrm{s}^{-1} \mathrm{pc}^2$)" (5 Gas Mass and Freefall Time From CO (5-4))
   - parameter: r54 = 0.28±0.05; alpha_CO = 0.9±0.2  
  > "$\alpha_{_{\mathrm{CO}}}$ | $0.9\pm0.2" (Table 1)
   - assumption: Clump spherical; sigma_tot ≈ sigma_bgs  
  > "Assuming $\mathrm{clump\,A}$ to be spherical" (5 Gas Mass and Freefall Time From CO (5-4))
   - fitting: _not stated_
   - validation: Compared to dust-based gas mass (2.3-4.9)e8 Msun  
  > "the gas masses we thereby obtain are $M_{\mathrm{gas}} = (2.3-4.9)\times10^8\,\mbox{$\mathrm{M}_{\ensuremath{\odot}}$}$" (3.1 Gas Mass and Clump Size from Continuum Emission)
5. **Compare observed SFR with KS, KDM12, SFK15 predictions**: Evaluate relations with MC (100,000 samples) and compare PDFs; reduced chi2 scatter vs local regions  
  > "These PDFs were calculated using Monte Carlo simulations with a sample size of 100,000" (6 Comparison of observed SFR surface density with theoretical predictions by K98, KDM12 and SFK15)
   - parameter: b = 0.4, beta_mag -> infinity, eps_ff = 0.015  
  > "We use a mixed driving mode with $b=0.4$" (6 Comparison of observed SFR surface density with theoretical predictions by K98, KDM12 and SFK15)
   - assumption: Magnetic fields neglected  
  > "we neglect magnetic fields and set $\beta_{\mathrm{mag}}\to \infty$" (6 Comparison of observed SFR surface density with theoretical predictions by K98, KDM12 and SFK15)
   - fitting: No fit; chi2 minimization scatter only  
  > "We emphasize that we do not fit any relations to compute the scatter" (6 Comparison of observed SFR surface density with theoretical predictions by K98, KDM12 and SFK15)
   - validation: _not stated_

## Software

- **IDL PLANEFIT** : Plane fit to velocity field  
  > "we use the `PLANEFIT` routine in IDL" (4 Mach Number Estimation)
- **WebPlot Digitizer** : Extracting literature data from figures  
  > "The authors also acknowledge the use of WebPlot Digitizer" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sigma_SFR observed (Chabrier) | 357 | +135/-85 | Msun/yr/kpc^2 | 2 | $357^{+135}_{-85}\,\mbox{$\mathrm{M}_{\ensuremath{\odot}}$}\,\mathrm{yr}^{-1}\,\mathrm{kpc}^{-2}$ |
| Dust temperature (beta=2.5) | 39 | 2 | K | 1 | We derive a best-fit temperature $T = 39\pm2\,\mathrm{K}$ for $\beta_{\mathrm{em}}= 2.5$ |
| L_FIR clump A | 2.25e11 | +0.95/-0.47 e11 | Lsun | 2 | $L_{\mathrm{FIR}} = \big(2.25^{+0.95}_{-0.47}\big)\times10^{11}\,\mbox{$\mathrm{L}_{\ensuremath{\odot}}$}$ |
| sigma_v,turb | 37 | 5 | km/s | 3 | $\sigma_{\mathrm{v,turb}} = 37\pm5\,\mathrm{km\,s}^{-1}$ |
| Mach number | 96 | 28 | dimensionless | 3 | we obtain a turbulent Mach number $\mathcal{M}= 96\pm28$ |
| Gas mass | 6.2e8 | 1.4e8 | Msun | 4 | $M_{\mathrm{gas}}$ / $(6.2\pm1.4)\times10^8\,\mbox{$\mathrm{M}_{\ensuremath{\odot}}$}$ |
| Virial parameter | 0.63 | 0.13 | dimensionless | 4 | $\alpha_{\mathrm{vir}} = 0.63\pm0.13$ |
| Freefall time | 1.3 | 0.1 | Myr | 4 | we obtain a freefall time of $1.3\pm0.1\,\mathrm{Myr}$ |
| Sigma_SFR KS | 52 | 17 | Msun/yr/kpc^2 | 5 | $\Sigma_{\mathrm{SFR,KS}} = 52\pm17 |
| Sigma_SFR KDM12 | 106 | 37 | Msun/yr/kpc^2 | 5 | $\Sigma_{\mathrm{SFR,KDM}} = 106\pm37 |
| Sigma_SFR SFK15 | 491 | +139/-194 | Msun/yr/kpc^2 | 5 | $\Sigma_{\mathrm{SFR,SFK}} = 491^{+139 |
| Reduced chi2 scatter (KS, KDM12, SFK15) | 50.1, 7.27, 1.25 | not stated | dimensionless | 5 | $\chi^2_{\mathrm{red}} = 50.1$ and $7.27$ for the KS and KDM12 relations, respectively |

## Qualitative findings

- Turbulence-based SFK15 gives the best SFR prediction though it overestimates, plausibly because magnetic fields are neglected  
  > "Although the SFK relation overestimates the SFR in this clump (possibly due to the negligence of magnetic fields), it provides the best prediction among the available models." (abstract)

## Claim tuples

- H: Do KS and KDM12 predict the observed SFR surface density of clump A? | E: Compare SED-derived SFR surface density with relation predictions | R: KS 52±17 and KDM12 106±37 vs observed 357 | F: Both underestimate; KS by factor ≳3.3 | **supported**
- H: Does turbulence matter for SFR in this clump? | E: Mach number from CO(5-4) velocity field fed into SFK15 | R: SFK15 gives 491, scatter 1.25 vs 50.1 (KS) and 7.27 (KDM12) | F: Turbulence crucial; SFK15 best among models | **supported**
- H: Is plane-of-sky turbulent dispersion consistent with line-of-sight estimate? | E: Gradient subtraction vs S15 second-moment dispersion | R: 37±5 vs 30±9 km/s | F: Agreement; clump approximately isotropic | **supported**

## Reasoning

- Why this data: Lensing plus ALMA gives sub-kpc resolution for a high-z starburst, ideal to test SF relations  
  > "Thus, SDP 81 falls under the category of extreme starburst galaxies and is an ideal candidate to test star formation relations." (1 Introduction)
- Why this method: _not stated_
- Alternative: Clump B excluded: elongated structure and poor correlation with CO(5-4) flux  
  > "The horizontally elongated structure of clump B rules out the possibility of a spherical approximation to its volume" (2 Data Reduction and Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust parameters cannot be simultaneously constrained; clump conditions assumed equal to galaxy-wide  
  > "the available ALMA observations are insufficient to simultaneously constrain the dust parameters" (3 Measurement of the Star Formation Rate)
- Limitation (authors): Magnetic fields unavailable and neglected  
  > "We do not have any estimates of magnetic field strength in this galaxy" (6 Comparison of observed SFR surface density with theoretical predictions by K98, KDM12 and SFK15)
- Caveat (inferred, ours): Only one clump (32 pixels) analysed; low-number statistics
- Caveat (inferred, ours): alpha_CO and r54 uncertain and drive gas mass
- Caveat (inferred, ours): Lens model uncertainty and source-plane reconstruction not propagated
- Caveat (inferred, ours): Gas temperature range wide, Mach number sensitive to c_s
- Caveat (inferred, ours): Single-object test of relations

## Reproducibility

- Data public (paper): ALMA Science Verification data publicly available  
  > "In the calibrated data[^2], the lensed galaxy is seen in the form of an Einstein ring" (2 Data Reduction and Analysis)
- Products in archive: _not stated_
- Missing: Source-plane reconstructed maps and lens model code/parameters
- Missing: Clump A mask and band fluxes
- Missing: Code for MC and SED fitting
- Missing: Comparison sample data
- Data volume (inferred): ~10-50 GB for SV calibrated data, though only reconstructed maps are needed
- Score (inferred): 3/5, Public data and clear formulae, but depends on S15 source-plane maps and unspecified clump fluxes.
- Rediscovery candidate: no, Key inputs come from lens reconstruction by earlier work not reproduced here.

## Links

- Method: Federrath et al. 2016 (cite: 2016ApJ...832..143F) (Gradient subtraction turbulence method)
- Method: Salim, Federrath & Kewley 2015 (cite: 2015ApJ...806L..36S) (SFK15 relation)
- Companion: Swinbank et al. 2015 (cite: 2015ApJ...806L..17S) (Clump identification and source-plane maps)
- Companion: Dye et al. 2015 (cite: 2015MNRAS.452.2258D) (Lens model)
- Companion: ALMA Partnership 2015 (cite: 2015ApJ...808L...4A) (SDP 81 SV observations)
- Related: H-ATLAS
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
