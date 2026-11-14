# Shock-induced HCNH<SUP>+</SUP> abundance enhancement in the heart of the starburst galaxy NGC 253 unveiled by ALCHEMI

`2025A&A...696A..31G` | Astronomy and Astrophysics 2025 | first author: Gong, Y. | arXiv: 2502.20894 | DOI: 10.1051/0004-6361/202452835

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the physical conditions and HCNH+ abundances in the CMZ of NGC 253 from multiple HCNH+ transitions, and what chemistry explains the abundances?  
  > "We aim to reveal the physical and chemical properties of the CMZ in the starburst galaxy NGC 253 with multiple HCNH$^{+}$ transitions" (abstract)
- Target **NGC 253 CMZ**: coordinates 00h47m33.28s, -25d17m17.6s (phase center)  
  > "At a distance of $\sim$3.5 Mpc (cite: 2003A&A...404...93K; 2005MNRAS.361..330R), the Sculptor galaxy NGC 253" (1 Introduction); "The phase center of these observations is ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$)=(00$^{\rm h}$47$^{\rm m}$33$^{\rm s}$28, $-$25$^{\circ}$17$^{\prime}$17$^{\prime\prime}$6)." (2 Observations and data reduction); z/distance ~3.5 Mpc  
  > "At a distance of $\sim$3.5 Mpc (cite: 2003A&A...404...93K; 2005MNRAS.361..330R), the Sculptor galaxy NGC 253" (1 Introduction); "The phase center of these observations is ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$)=(00$^{\rm h}$47$^{\rm m}$33$^{\rm s}$28, $-$25$^{\circ}$17$^{\prime}$17$^{\prime\prime}$6)." (2 Observations and data reduction); distance from Karachentsev et al. 2003; Rekola et al. 2005  
  > "At a distance of $\sim$3.5 Mpc (cite: 2003A&A...404...93K; 2005MNRAS.361..330R), the Sculptor galaxy NGC 253" (1 Introduction); "The phase center of these observations is ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$)=(00$^{\rm h}$47$^{\rm m}$33$^{\rm s}$28, $-$25$^{\circ}$17$^{\prime}$17$^{\prime\prime}$6)." (2 Observations and data reduction)

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: Bands 3–7 (84–375 GHz) survey  
  > "spans ALMA Bands 3–7, covering frequencies from 84 to 375 GHz" (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m Array and ACA combined  
  > "was achieved by combining the 12 m Array and Atacama Compact Array data" (2 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: common circular beam of 1.6" (27 pc)  
  > "All data products have been convolved to a common circular beam of 1$''$6 (i.e., 27 pc)." (2 Observations and data reduction)
- max recoverable scale: ≳11"  
  > "their maximum recoverable scales of $\gtrsim$11$''$ was achieved" (2 Observations and data reduction)
- sensitivity: rms about 4–20 mK at 10 km/s channel width  
  > "The typical rms noise levels are about 4–20 mK at a channel width of 10 km s$^{-1}$." (2 Observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCNH+ 2–1 (148221.450(17) MHz)
- Line: HCNH+ 3–2 (222329.277(8) MHz)
- Line: HCNH+ 4–3 (296433.652(17) MHz)
- Line: HCNH+ 5–4 (370533.375(23) MHz)
- External data: Beam-averaged H2 column densities (1.6" beam) for each GMC  
  > "we directly utilized values for $N_{\rm H_{2}}$ from the low-density hierarchical Bayesian analysis of the ALCHEMI data at a circular beam of 1$''$6 (cite: 2024ApJ...961...18T)" (3.2 LTE analysis) [from (cite: 2024ApJ...961...18T)]
- External data: Spectroscopic data for HCNH+ from CDMS  
  > "The spectroscopic information was taken from the entry in the Cologne Database for Molecular Spectroscopy (cite: 2016JMoSp.327...95E)" (2 Observations and data reduction) [from (cite: 2016JMoSp.327...95E)]
- External data: HCNH+ HCN-HCN and HCN-H2O binding energies from experiments  
  > "we adopted HCN–HCN and HCN-H$_{2}$O binding energies of $E_{\rm D}=3207\pm 197$ K and $E_{\rm D}=4192\pm 68$ K" (4.1 Static clouds) [from (cite: 2022ApJ...933..206B)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Data taken directly from ALCHEMI products (continuum-subtracted cubes)  
  > "The data cubes were extracted from the ALCHEMI continuum-subtracted FITS cubes using the SpectralCube[^1] python package." (2 Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: ≲10%  
  > "The absolute flux calibration uncertainties were found to be $\lesssim 10$% (cite: 2021A&A...656A..46M)." (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 3σ connected components (26-connected) in HCNH+ (2–1) cube used as mask for all transitions, expanded spatially/spectrally  
  > "We labeled the connected components above the 3$\sigma$ threshold in the three-dimensional ($\alpha_{2000}, \delta_{2000}$, $\varv_{\rm LSR}$) data cube of HCNH$^{+}$ (2–1) using a 26-connected neighborhood" (3.1 Spatial distribution and spectra)
- multiscale scales: _not stated_
- continuum subtraction: ALCHEMI continuum-subtracted cubes used  
  > "extracted from the ALCHEMI continuum-subtracted FITS cubes" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m + ACA  
  > "combining the 12 m Array and Atacama Compact Array data" (2 Observations and data reduction)
- smoothing: convolved to 4" FWHM for integrated intensity map Fig. 1b  
  > "Fig. [1](#Fig:hcnh+_m0)b shows the integrated intensity map convolved to a circular beam of 4$''$ FWHM,without sigma clipping." (3.1 Spatial distribution and spectra)
- final beam: 1.6" circular (4" for smoothed Fig. 1b)  
  > "All data products have been convolved to a common circular beam of 1$''$6 (i.e., 27 pc)." (2 Observations and data reduction)
- final rms: 4–20 mK at 10 km/s  
  > "The typical rms noise levels are about 4–20 mK at a channel width of 10 km s$^{-1}$." (2 Observations and data reduction)

### Inherited from earlier work

- Data reduction/imaging of the ALCHEMI survey  
  > "A comprehensive description of the survey has already been provided in (cite: 2021A&A...656A..46M), so we only offer a brief summary here." (2 Observations and data reduction) [from (cite: 2021A&A...656A..46M)]
- Masking method is a modified version of earlier method  
  > "Our masking method[^2] is a modified version of that previously adopted by (cite: 2024ApJS..271...38H)." (3.1 Spatial distribution and spectra) [from (cite: 2024ApJS..271...38H)]
- H2 ortho-to-para ratio of 0.25  
  > "we adopted an H$_{2}$ ortho-to-para ratio of 0.25, following the values reported in previous studies (cite: 2006ApJ...649..816N)" (3.3.2 Non-LTE modeling) [from (cite: 2006ApJ...649..816N)]
- Chemical network UMIST RATE12 with updated reactions  
  > "employing the UMIST RATE12 chemical network (cite: 2013A&A...550A..36M) enhanced with updated chemical reactions as described by (cite: 2023A&A...679A..39G)" (4.1 Static clouds) [from (cite: 2013A&A...550A..36M; 2023A&A...679A..39G)]
- C-type shock parameterization  
  > "we adopted C-type shocks for our calculations, parameterized according to (cite: 2008A&A...482..549J), similar to the approach in (cite: 2023A&A...675A.151H)" (4.3 Shocks) [from (cite: 2008A&A...482..549J; 2023A&A...675A.151H)]

### Not stated but needed to reproduce (our reading)

- Exact ALCHEMI cube versions and file names, and channel velocity resolution used
- Mask expansion sizes in spatial and spectral dimensions
- Spectral extraction apertures for the GMC spectra
- MCMC prior on line width and how line widths/integrated-intensity ratios enter the likelihood; RADEX background temperature
- Chempl/UCLCHEM input parameter grids and run times
- Convergence diagnostics for MCMC
- Velocity ranges for Gaussian fit windows

## Analysis recipe

1. **extract and mask cubes**: Extract continuum-subtracted cubes, convert to brightness temperature (Rayleigh-Jeans), build 3σ 26-connected mask from HCNH+ (2–1), apply to all transitions  
  > "These labeled components were subsequently utilized as masks for all the HCNH$^{+}$ transitions." (3.1 Spatial distribution and spectra)
   - software: SpectralCube, connected-components-3d
   - parameter: 3σ threshold; integrate 100–400 km/s  
  > "we derived the integrated intensity distributions of the four HCNH$^{+}$ transitions over a range from 100 km s$^{-1}$ to 400 km s$^{-1}$." (3.1 Spatial distribution and spectra)
   - fitting: _not stated_
   - validation: Integrated intensities of masked map consistent with Harada et al. map within uncertainties  
  > "The integrated intensities of Fig. [1](#Fig:hcnh+_m0)a and Fig. [3](#Fig:4m0)a are consistent within uncertainties" (3.1 Spatial distribution and spectra)
2. **fit line profiles**: Single-component Gaussian fit to HCNH+ spectra of GMCs  
  > "We fit the observed HCNH$^{+}$ transitions from the selected GMCs using a single-component Gaussian model" (3.1 Spatial distribution and spectra)
   - assumption: Optically thin (tau<0.1; <0.3 with dilution 0.1) assuming Tex=15 K  
  > "Assuming an excitation temperature of 15 K (as discussed below) and neglecting beam dilution effects, we find that the low peak intensities correspond to optical depths of $<$0.1." (3.1 Spatial distribution and spectra)
   - fitting: _not stated_
   - validation: Velocities agree with other tracers  
  > "The peak velocities of HCNH$^{+}$ transitions agree well with those of all other molecular species" (3.1 Spatial distribution and spectra)
3. **LTE rotational diagram**: Rotational diagram with linear fits; Monte Carlo with 10,000 realizations for uncertainties; abundances using N(H2) from Tanaka et al.  
  > "Specifically, 10,000 realizations were generated by sampling Gaussian distributions of the integrated intensities" (3.2 LTE analysis)
   - assumption: LTE; beam dilution not corrected  
  > "we did not correct for the beam dilution effects, which may be negligible (see above)" (3.2 LTE analysis)
   - fitting: Linear fit; Gaussian-resampled intensities with combined uncertainties and 10% flux calibration  
  > "Linear fits were applied to these diagrams, with uncertainties quantified using a Monte Carlo approach. Specifically, 10,000 realizations were generated by sampling Gaussian distributions of the integrated intensities" (Results, LTE analysis)
   - validation: _not stated_
4. **compute collisional rate coefficients**: Coupled states approximation with MOLSCAT using the 4D PES of Bop & Lique 2023, for p-H2 and o-H2 up to 500 K; compared with CC data via WMEF  
  > "we implemented the four-dimensional potential energy surface calculated by (cite: 2023JChPh.158g4304B) in the `MOLSCAT` molecular scattering code" (3.3.1 Collisional rate coefficients)
   - software: MOLSCAT
   - parameter: 30 lowest levels of HCNH+, j1 = 0–48; H2 j2=0–2 (p) and 1–3 (o); total energies up to 3500/3620 cm-1  
  > "The calculations were performed for total energies up to 3500 cm$^{-1}$ and 3620 cm$^{-1}$ using *p*-H$_2$ and *o*-H$_2$ as colliders, respectively." (3.3.1 Collisional rate coefficients)
   - fitting: _not stated_
   - validation: CS rates compared with CC rates; WMEF decreases with T, good for T>50 K, excellent above 80 K  
  > "The WMEF decreases with increasing temperature, suggesting that the agreement is expected to be reasonable above 30 K, good for $T > 50$ K, and excellent above 80 K." (3.3.1 Collisional rate coefficients)
5. **non-LTE MCMC fit with RADEX**: RADEX (LVG) models fit to integrated intensities with emcee; uniform priors on TK, nH2, N(HCNH+)  
  > "We minimize our modeling results using the emcee[^12] code (cite: 2013PASP..125..306F) and the affine-invariant ensemble sampler" (3.3.2 Non-LTE modeling)
   - software: RADEX, emcee
   - parameter: Priors: TK 50–500 K, nH2 10^2–10^7 cm-3, N 10^13–10^17 cm-2; 20 walkers, 4500 steps after burn-in  
  > "The MCMC simulations were conducted using 20 walkers for 4500 steps following a burn-in period to ensure that the walkers achieved convergence." (3.3.2 Non-LTE modeling)
   - assumption: OPR 0.25, beam dilution factor unity, same emitting region for all transitions, line width averaged over transitions  
  > "For simplicity, we neglected the beam dilution effects (i.e., the beam dilution factor is set to be unity)." (3.3.2 Non-LTE modeling)
   - fitting: Likelihood exp(-chi2/2); 16th and 84th percentiles for 1σ  
  > "The likelihood function is assumed to be e$^{-\chi^{2}/2}$" (3.3.2 Non-LTE modeling)
   - validation: Compared densities with low-density component of Tanaka et al. 2024  
  > "aligning with the values of the low-density component in the CMZ of NGC 253 (cite: 2024ApJ...961...18T)" (3.3.2 Non-LTE modeling)
6. **astrochemical modeling (static, PDR, shock)**: Chempl static and PDR models; UCLCHEM two-phase C-type shock models, varying T, density, Av, G0, zeta, shock velocity  
  > "we employed the UCLCHEM[^14] code (cite: 2017AJ....154...38H) to run shock models." (4.3 Shocks)
   - software: Chempl, UCLCHEM
   - parameter: PDR fiducial T=500 K, n=10^3 cm-3; shock preshock density 10^3 cm-3  
  > "we used $T_{\rm k}=$500 K and a gas density of 10$^{3}$ cm$^{-3}$ as our fiducial parameters in the PDR models" (4.2 PDRs)
   - assumption: Dust temperature equal to gas temperature in static models  
  > "In these models, dust temperatures are assumed to be equal to gas temperatures." (4.1 Static clouds)
   - fitting: _not stated_
   - validation: Compared with observed abundances and HCN/HNC abundances from Behrens et al. 2024  
  > "We also compared the HCN and HNC abundances derived from (cite: 2024ApJ...977...38B) with our shock models." (4.3 Shocks)

## Software

- **SpectralCube** : Extract data cubes from ALCHEMI FITS  
  > "using the SpectralCube[^1] python package" (2 Observations and data reduction)
- **connected-components-3d** : 26-connected labeling for masks  
  > "using a 26-connected neighborhood[^3] algorithm[^4]" (3.1 Spatial distribution and spectra)
- **MOLSCAT** : Inelastic cross sections for HCNH+ + H2  
  > "to compute state-to-state inelastic cross sections" (3.3.1 Collisional rate coefficients)
- **RADEX** : Non-LTE radiative transfer  
  > "we used the non-LTE radiative transfer code RADEX[^11] for statistical equilibrium calculations" (3.3.2 Non-LTE modeling)
- **emcee** : MCMC sampling  
  > "We minimize our modeling results using the emcee[^12] code" (3.3.2 Non-LTE modeling)
- **Chempl** : Static cloud and PDR chemical models  
  > "We first used the gas-grain astrochemical code, *Chempl[^13]*" (4.1 Static clouds)
- **UCLCHEM** : Shock models  
  > "we employed the UCLCHEM[^14] code (cite: 2017AJ....154...38H) to run shock models" (4.3 Shocks)
- **CARTA** : Cube visualization  
  > "made use of the Cube Analysis and Rendering Tool for Astronomy (CARTA) software" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCNH+ radial extent in CMZ | ~300 | not stated | pc | 1 | with a radial extent of $\sim$300 pc in the CMZ |
| Rotational temperatures | 12–21 | not stated | K | 3 | The derived rotational temperatures are in the range of 12–21 K |
| LTE HCNH+ column densities | 8.3e14–4.0e15 | not stated | cm^-2 | 3 | range from $8.3\times 10^{14}$ cm$^{-2}$ to $4.0\times 10^{15}$ cm$^{-2}$ |
| LTE HCNH+ abundances | 6.3e-9 to 2.0e-8 | not stated | dimensionless | 3 | ranging from $6.3\times 10^{-9}$ to $2.0\times 10^{-8}$ |
| Non-LTE HCNH+ column densities | (0.3–1.2)e15 | not stated | cm^-2 | 5 | The beam-averaged HCNH$^+$ column densities of $(0.3-1.2) \times 10^{15}$ cm$^{-2}$ |
| Non-LTE HCNH+ abundances | (1.8–9.4)e-9 | not stated | dimensionless | 5 | the HCNH$^+$ abundances are revised to (1.8–9.4)$\times 10^{-9}$ in the CMZ of NGC 253 |
| H2 number density | 10^2.80–10^3.55 | ~0.2 dex typical | cm^-3 | 5 | H$_2$ number densities of $\sim 10^{2.80}-10^{3.55}$ cm$^{-3}$ with typical errors of $\sim$0.2 dex |
| Critical densities at 100 K for (2–1),(3–2),(4–3),(5–4) | 1.0e3, 3.6e3, 8.6e3, 1.7e4 | not stated | cm^-3 | 4 | are $1.0\times 10^{3}$ cm$^{-3}$, $3.6\times 10^{3}$ cm$^{-3}$, $8.6\times 10^{3}$ cm$^{-3}$, and $1.7\times 10^{4}$ cm$^{-3}$, respectively |

## Qualitative findings

- HCNH+ emission is widespread and four transitions have nearly identical spatial distributions, peaking at GMC6  
  > "the four HCNH$^{+}$ transitions exhibit nearly identical spatial distributions, with emission peaking at GMC6" (3.1 Spatial distribution and spectra)
- HCNH+ abundance decreases toward the CMZ center and anti-correlates with N(H2)  
  > "we observe a trend of decreasing HCNH$^{+}$ abundances in GMCs as they approach the center of the CMZ" (3.2 LTE analysis)
- Static and PDR models fail at high cosmic-ray rates; C-type shocks with v_s ≳10 km/s reproduce abundances  
  > "our C-type shock models can reproduce the high HCNH$^{+}$ abundances at such extreme physical conditions with shock velocities of $\varv_{\rm s}\gtrsim$10 km s$^{-1}$" (4.3 Shocks)

## Claim tuples

- H: HCNH+ traces low-density gas in the NGC 253 CMZ | E: RADEX+emcee non-LTE modeling with new CS collisional rates | R: nH2 ~10^2.80–10^3.55 cm-3 | F: HCNH+ is a tracer of low-density environments | **supported**
- H: HCNH+ abundances in NGC 253 CMZ exceed Milky Way values | E: Non-LTE abundances using N(H2) from Tanaka et al. | R: (1.8–9.4)e-9 vs ≲2e-9 in Milky Way | F: Most abundances exceed all Galactic values | **supported**
- H: Shocks can explain elevated HCNH+ abundances | E: Static, PDR and UCLCHEM C-type shock models | R: Only shock models match at high zeta; single shock insufficient | F: Recurrent shocks could account for the enhancement | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: CS approximation used to extend rates to high T at lower computational cost than CC  
  > "To address the computational cost of the CC method, we employ the quantum mechanical coupled states (CS) approximation" (3.3.1 Collisional rate coefficients)
- Alternative: Static and PDR models rejected as they fail at zeta ≳10^3 zeta0  
  > "PDR models fail to match the observed values at the expected high cosmic-ray ionization rates" (4.2 PDRs)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas temperatures poorly constrained by HCNH+; large-scale emission filtered; beam dilution neglected  
  > "whereas the gas temperatures are less precisely determined" (3.3.2 Non-LTE modeling)
- Caveat (inferred, ours): Abundances depend on external N(H2) from a different model
- Caveat (inferred, ours): Single-shock chemical models are illustrative; recurrent shocks not modelled
- Caveat (inferred, ours): Likelihood chi2 formula lacks square
- Caveat (inferred, ours): CS rates underestimate CC by up to a factor 2 at low T
- Caveat (inferred, ours): Beam dilution set to unity may bias column densities

## Reproducibility

- Data public (paper): ALCHEMI data public; trimmed cubes to be made public  
  > "The data cubes will be made public online via [this link](https://gongyan2444.github.io/)." (footnote 5)
- Products in archive: _not stated_
- Code: Masking script on GitHub  
  > "The masking script is available from [this link](https://github.com/shbzhang/MaskingNGC253)." (footnote 2)
- Missing: Chempl/UCLCHEM input files
- Missing: Exact mask expansion parameters
- Missing: N(H2) values require Tanaka et al. table
- Data volume (inferred): tens of GB (ALCHEMI cubes for four lines)
- Score (inferred): 3/5, Public data and many parameters given, with codes mostly public, but model inputs and mask details are incomplete.
- Rediscovery candidate: yes, Public data, numeric tables of fitted parameters and abundances, recipe mostly specified.

## Links

- Method: (cite: 2021A&A...656A..46M) (ALCHEMI survey description and calibration)
- Method: (cite: 2024ApJS..271...38H) (Masking method and GMC definitions)
- Companion: (cite: 2024ApJ...961...18T) (H2 column densities and low-density component)
- Companion: (cite: 2023A&A...679A..39G) (HCNH+ chemistry in Galactic clouds)
- Related: ALCHEMI

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 62,
  "rate": 0.681
 },
 "evidence_ok": true
}
```
