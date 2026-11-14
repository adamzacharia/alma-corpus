# Molecular Outflow in the Reionization-epoch Quasar J2054-0005 Revealed by OH 119 μm Observations

`2024ApJ...962....1S` | The Astrophysical Journal 2024 | first author: Salak, Dragan | arXiv: 2307.02104 | DOI: 10.3847/1538-4357/ad0df5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Does the z=6.04 quasar J2054-0005 host a molecular outflow traced by OH 119 μm, and how strong is it relative to star formation?  
  > "It is therefore of great interest, and motivation of this work, to investigate whether the 119 $\ensuremath{\mu}m$ line can provide a good probe of outflows at the EoR." (Introduction)
- Target **J2054-0005**: coordinates 20h54m06.503s, -00d05m14.43s (ICRS, pointing center)  
  > "centered at $(\alpha,\delta)_\mathrm{ICRS}=(\mathrm{20^h54^m06.503s,-00\ensuremath{^\circ}05\ensuremath{'}14.43\ensuremath{''}})$" (Observations and data reduction); "The measurements of these lines have determined its redshift to be $z=6.0391\pm0.0002$." (Introduction); z/distance z=6.0391±0.0002  
  > "centered at $(\alpha,\delta)_\mathrm{ICRS}=(\mathrm{20^h54^m06.503s,-00\ensuremath{^\circ}05\ensuremath{'}14.43\ensuremath{''}})$" (Observations and data reduction); "The measurements of these lines have determined its redshift to be $z=6.0391\pm0.0002$." (Introduction); distance from previous ALMA [CII], [OIII], CO line measurements  
  > "centered at $(\alpha,\delta)_\mathrm{ICRS}=(\mathrm{20^h54^m06.503s,-00\ensuremath{^\circ}05\ensuremath{'}14.43\ensuremath{''}})$" (Observations and data reduction); "The measurements of these lines have determined its redshift to be $z=6.0391\pm0.0002$." (Introduction)

## Data provenance

- ALMA projects: 2021.1.01305.S, 2019.1.00672.S
- bands: Band 7  
  > "The Band 7 receivers were tuned to cover the OH doublet at an observing frequency for the adopted redshift $z=6.0391$." (Observations and data reduction)
- frequencies and spectral setup: USB SPWs at 356.315 and 358.090 GHz (1.875 GHz each); LSB continuum SPWs at 344.2 and 346.1 GHz (2 GHz each)  
  > "Two spectral windows (upper sideband; USB) were centered at the observing frequencies 356.315 GHz and 358.090 GHz for the line observations." (Observations and data reduction); "The central observing frequencies were 344.2 GHz and 346.1 GHz, and the bandwidth of each of them was 2 GHz." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 41-46 antennas  
  > "In most observing runs, 44 antennas were used, but the number ranged from 41 to 46." (Observations and data reduction)
- configurations: C-5, baselines 15 m to 1301 m  
  > "The array was in configuration C-5 with baselines from 15 m to 1301 m." (Observations and data reduction)
- baselines: _not stated_
- angular resolution: 0.205"x0.176" continuum; 0.204"x0.174" OH cube (~1 kpc)  
  > "FWHM $b_\mathrm{maj}$ (arcsec)                  |   0.205   |  0.204" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 13 μJy/beam continuum; 0.13 mJy/beam per 35 km/s channel  
  > "The mean sensitivity over two spectral windows is $\sigma=0.13~\mathrm{mJy~beam^{-1}}$ in a channel of $35~\mathrm{km~s}^{-1}$" (Observations and data reduction)
- time on source: 7.3 hours on source (12.7 h total)  
  > "The total on-source time was 7.3 hours, whereas the total time including calibrator observations and other overheads was 12.7 hours." (Observations and data reduction)
- observing dates: August 4-12, 2022 (Cycle 8)  
  > "The observations were conducted between August 4 and 12 in 2022 during ALMA cycle 8." (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: OH 2Pi3/2 J=5/2-3/2 doublet (119.23, 119.44 μm) (2514.31640360 GHz (F=3-–2+))
- Other facility **ALMA 2019.1.00672.S**: [CII] 158 μm data for comparison (Fujimoto et al. in prep.)  
  > "the \[C II\] data are from #2019.1.00672; S. Fujimoto, in prep." (4.3 Resolved OH absorption and emission)
- Other facility **SDSS, WISE, Herschel, VLA, ALMA bands 6/7**: photometry for CIGALE SED fitting  
  > "we used the following data: SDSS-z, WISE1, *Herschel* (PACS, SPIRE), ALMA bands 6 and 7" (5.1 Fractional contribution of AGN to IR luminosity)
- External data: Total molecular gas mass (3-6)e10 Msun  
  > "$M_\mathrm{mol}=(3\mathrm{-}6)\times10^{10}M_\ensuremath{\odot}$ by (cite: Dec22)" (5.3 Suppression of star formation) [from (cite: Dec22)]
- External data: Dynamical mass 7.2e10 Msun from [CII], inclination 24 deg  
  > "$M_\mathrm{dyn}\approx7.2\times10^{10}M_\ensuremath{\odot}$ (cite: Wan13)" (5.4 Gas escaping into the IGM) [from (cite: Wan13)]
- External data: OH outflow properties of comparison quasars and DSFGs (radii, continuum sizes, LIR)  
  > "based on Figure 2 in (cite: But23)" (5.4 Mdot-LIR relation) [from (cite: But23); (cite: Spi20a)]
- External data: Dust temperature Td=50±2 K and LIR~1.3e13 Lsun  
  > "$T_\mathrm{d}=50\pm2~\mathrm{K}$; (cite: Has19)" (4.1 Outflow mass) [from (cite: Has19)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline, 9 calibrated MSs  
  > "Basic calibration was performed with a CASA pipeline resulting in 9 calibrated measurement sets." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2253+1608 (8 sets), J1924-2914 (1 set) flux/bandpass; J2101+0341 phase  
  > "J2253+1608 (8 data sets) and J1924-2914 (1 data set) were observed for the flux and bandpass calibration" (Observations and data reduction)
- flux scale uncertainty: 10% absolute flux accuracy in Band 7  
  > "the absolute flux accuracy in Band 7 is reported to be $10\%$ (cite: Bra21)" (Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "The calibrated data were then combined and imaged using the CASA task `tclean`." (Observations and data reduction)
- deconvolver: hogbom, mtmfs-style multi-frequency synthesis for continuum  
  > "using the line-free LSB spectral windows in the multi-frequency synthesis mode with the `hogbom` deconvolver and standard gridding" (Observations and data reduction)
- weighting robust: briggs, robust = 0.5  
  > "The weighting was set to `briggs` with the robust parameter equal to 0.5" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh; threshold 2σ  
  > "The threshold for iterations was set to $2~\sigma$" (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: not subtracted for OH cube; continuum fitted jointly  
  > "The visibilities of two spectral windows were processed by `tclean` separately and continuum was not subtracted." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: applied to final images  
  > "The final images were corrected for the primary beam attenuation." (Observations and data reduction)
- array combination: _not stated_
- smoothing: smoothed to 35 km/s  
  > "we smoothed the data cubes to a resolution of $35~\mathrm{km~s^{-1}}$" (Observations and data reduction)
- final beam: 0.205"x0.176" PA 81.7 (cont); 0.204"x0.174" PA 75.0 (OH)  
  > "Beam position angle (degree)                    |   81.7    |  75.0" (Table 1)
- final rms: 13 μJy/beam continuum; 0.13 mJy/beam OH  
  > "The rms sensitivity in the final continuum image is $\sigma=13~\mathrm{\mu Jy~beam^{-1}}$." (Observations and data reduction)

### Inherited from earlier work

- Empirical mass outflow rate recipe modified by Spilker  
  > "The “recipe” formula from (cite: HC20) modified by (cite: Spi20b) takes the form" (4.2.2 Empirical relation) [from (cite: HC20); (cite: Spi20b)]
- Thin shell outflow mass formula and covering factor f=0.3  
  > "the molecular gas mass in the outflow (including helium and heavier elements) can be expressed as (cite: Vei20)" (4.1 Outflow mass) [from (cite: Vei20); (cite: Spi20b)]
- Mask-based cleaning via auto-multithresh  
  > "we employed the `auto-multitresh` tool (cite: Kep20)" (Observations and data reduction) [from (cite: Kep20)]

### Not stated but needed to reproduce (our reading)

- Line-free channels/velocity ranges and fitting initial guesses for curve_fit
- Exact tclean parameters (cell, image size, niter, automask thresholds)
- Which spectral extraction mask (>3σ continuum) exact definition
- CASA and pipeline versions
- CIGALE module parameter grids and version
- Fitting data for Mdot-LIR relations (values for comparison sources, regression method)
- Self-calibration status

## Analysis recipe

1. **Image continuum and OH cube**: tclean with hogbom, briggs 0.5, auto-multithresh; LSB for continuum, USB for OH without continuum subtraction; cubes smoothed to 35 km/s  
  > "The deconvolver and weighting setups were the same as for the continuum, and the `auto-multitresh` tool was used." (Observations and data reduction)
   - software: CASA, tclean, imageconcat
   - parameter: robust=0.5; 2σ threshold  
  > "The weighting was set to `briggs` with the robust parameter equal to 0.5" (Observations and data reduction)
   - fitting: _not stated_
   - validation: Interactive tclean gave no obvious difference from automasking  
  > "We also tried `tclean` in interactive mode, but there was no obvious difference in the result" (Observations and data reduction)
2. **Measure continuum flux and position**: imfit 2D Gaussian within 0.5" of brightest pixel; flux in r<0.5"  
  > "Using CASA’s `imfit`, we obtained $(\alpha,\delta)_\mathrm{ICRS}=(20^\mathrm{h}54^\mathrm{m}06.501s,-0\ensuremath{^\circ}05\ensuremath{'}14.44\ensuremath{''})$." (3.1 123-μm continuum emission)
   - software: CASA imfit
   - fitting: 2D Gaussian  
  > "We estimated the peak coordinates by two-dimensional gaussian fitting of a region of radius $0.5\ensuremath{''}$ centered at the brightest pixel." (3.1 123-$\mu$m continuum emission)
   - validation: Compared with SDSS z-band and [OIII] peaks  
  > "are thus in agreement within their respective uncertainties" (3.1 123-μm continuum emission)
3. **Fit OH profile**: Least-squares fit of two double-Gaussians (absorption outflow + emission systemic); doublet separation fixed at 521 km/s, equal peaks and FWHMs; constant continuum  
  > "the separation between the doublet lines of a double gaussian is fixed to $521~\mathrm{km~s^{-1}}$, and their peak values and FWHMs are set to be equal" (3.3 OH line fitting)
   - software: Python scipy.optimize.curve_fit
   - fitting: curve_fit least squares; uncertainties from fitting only  
  > "The uncertainties above include only those from fitting." (3.3 OH line fitting)
   - validation: Residuals shown; emission FWHM compared with [CII], [OIII], CO  
  > "the line widths of the two are in agreement with each other" (3.3 OH line fitting)
4. **Derive outflow mass and rate**: Optical depth, LTE OH column density from equivalent width, N_H2 via abundance, thin shell M=mu mH N_H Omega r^2, Mdot=M v/r; empirical relation as check  
  > "Assuming that the outflow is expanding at velocity $v_\mathrm{out}$ as a thin spherical shell, the mass outflow rate averaged over the outflow lifetime can be expressed as" (4.2.1 Optically-thin outflow model)
   - parameter: Tex=50 K, Q≈19, [OH]/[H2]=5e-7, f=0.3, r_out=2 kpc, v_out=669 km/s  
  > "using the covering factor $f=0.3$, outflow radius $r_\mathrm{out}=2~\mathrm{kpc}$, excitation temperature $T_\mathrm{ex}=50~\mathrm{K}$" (Table 3)
   - assumption: OH abundance 5e-7 chosen as compromise and to match the empirical relation  
  > "Choosing this value is also motivated by the fact that it yields an outflow mass and mass outflow rate comparable to those obtained using an empirical relation" (4.1 Outflow mass)
   - fitting: _not stated_
   - validation: Cross-check with empirical relation  
  > "are in agreement with those obtained under LTE and moderate OH abundance" (4.2.2 Empirical relation)
5. **Resolved OH spectra**: Extract spectra from 0.1"x0.1" regions and double-Gaussian fit each  
  > "We extracted OH spectra from adjacent rectangular regions of area $0.1\ensuremath{''}\times0.1\ensuremath{''}$" (4.3 Resolved OH absorption and emission)
   - software: scipy
   - fitting: _not stated_
   - validation: _not stated_
6. **AGN fraction, LIR, SFR via SED**: CIGALE SED fitting with delayed SFH, DL07 dust, Fritz AGN, solar/2 metallicity, two torus inclinations  
  > "we used the following data: SDSS-z, WISE1" (5.1 Fractional contribution of AGN to IR luminosity)
   - software: CIGALE
   - parameter: SFR=1.40e-10 L'IR (Chabrier)  
  > "$\mathrm{SFR}/M_\ensuremath{\odot}~\mathrm{yr}^{-1}=1.40\times10^{-10}L'_\mathrm{IR}/L_\ensuremath{\odot}$" (5.1)
   - assumption: Gas-phase metallicity half solar; AGN torus optical depth 2  
  > "The gas-phase metallicity was fixed to be two times lower than the solar value." (5.1)
   - fitting: CIGALE PDF analysis, likelihood-weighted mean  
  > "yielding the output value as the likelihood-weighted mean of the PDF" (5.1)
   - validation: median reduced chi2=0.52±0.11  
  > "median reduced $\chi^2=0.52\pm0.11$" (5.1)
7. **Mdot-LIR scaling relation with literature sample**: Power-law fit of Mdot vs LIR for 8 DSFGs and 3 quasars  
  > "the power law is $\log{y}=k\log{x}+m$, where $k=1.61\pm0.40$ and $m=-16.4\pm5.2$" (5.4)
   - assumption: Tex=50 K, [OH]/[H2]=5e-7 for all sources  
  > "we assumed $T_\mathrm{ex}=50~\mathrm{K}$ and $[\mathrm{OH}]/[\mathrm{H}_2]=5\times10^{-7}$ for all sources" (5.4)
   - fitting: _not stated_
   - validation: R^2=0.64  
  > "although the scatter is large ($R^2=0.64$)" (5.4)

## Software

- **CASA** : calibration pipeline, tclean imaging, imfit, imstat  
  > "The data were reduced using the Common Astronomy Software Applications (CASA) package (cite: TCT22)." (Observations and data reduction)
- **SciPy (curve_fit)** : least-squares line fitting  
  > "Python (`scipy.optimize.curve_fit`)" (3.3 OH line fitting)
- **CIGALE** : SED fitting for AGN fraction and LIR  
  > "Code Investigating Galaxy Emission (`CIGALE`; (cite: Boq19))" (5.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density (r<0.5") | 5.723 | 0.009 | mJy | 2 | $S_\nu(r<0.5\ensuremath{''})=5.723\pm0.009~\mathrm{mJy}$ |
| Absorption center velocity | -669 | 87 | km/s | 3 | Center velocity $v_\mathrm{cen}$ \[$\mathrm{km~s^{-1}}$\] / $-669\pm87$ / $65\pm15$ |
| Absorption FWHM | 1052 | 234 | km/s | 3 | FWHM line width \[$\mathrm{km~s^{-1}}$\] / $1052\pm234$ / $306\pm55$ |
| v98 | -1574 | 35 | km/s | 3 | $v_{98}=-1574\pm35~\mathrm{km~s^{-1}}$ |
| USB continuum from fit | 6.175 | 0.092 | mJy | 3 | $S_\mathrm{cont}=6.175\pm0.092~\mathrm{mJy}$ |
| Outflow mass (LTE) | 4.9e9 | not stated | Msun | 4 | Mass $M_\mathrm{out}$ \[$M_\odot$\] / $4.9\times10^9$ / $4.5\times10^9$ |
| Mass outflow rate (LTE) | 1700 | not stated | Msun/yr | 4 | Mass outflow rate $\dot{M}_\mathrm{out}$ \[$M_\odot~\mathrm{yr^{-1}}$\] / $1700$ / $1500$ |
| OH column density | 7.5e15 | not stated | cm^-2 | 4 | Column density $N_\mathrm{OH}~[\mathrm{cm^{-2}}]$ / $7.5\times10^{15}$ |
| Mass loading factor | 2.2 | not stated | dimensionless | 4 | Mass loading factor $\eta$ / $2.2$ / $1.9$ |
| LIR | 1.34e13 | 0.17e13 | Lsun | 6 | $L_\mathrm{IR}=(1.34\pm0.17)\times10^{13}~L_\ensuremath{\odot}$ |
| AGN fraction of LIR | 0.59 | 0.08 | dimensionless | 6 | $f_\mathrm{AGN}=0.59\pm0.08$ |
| SFR | 770 | 180 | Msun/yr | 6 | $\mathrm{SFR}=770\pm180~M_\odot~\mathrm{yr}^{-1}$ |
| Mdot-LIR slope k | 1.61 | 0.40 | dimensionless | 7 | $k=1.61\pm0.40$ and $m=-16.4\pm5.2$ |
| Escape velocity | 780 | not stated | km/s | 0 | $v_\mathrm{esc}(R)\approx\sqrt{2GM_\mathrm{dyn}/R}\approx780~\mathrm{km~s^{-1}}$ |

## Qualitative findings

- OH shows a P-Cygni profile with blueshifted absorption, evidence of outflow  
  > "The OH line is detected and exhibits a P-Cygni profile" (abstract)
- OH marginally resolved over central ~2 kpc  
  > "revealing that the outflow extends over the central 2 kpc region" (abstract)
- Companion continuum source 2.4" west at 8.9σ  
  > "We also found an additional continuum source positioned $2.4\ensuremath{''}$ west of the quasar" (3.1)

## Claim tuples

- H: Is there a molecular outflow in J2054-0005? | E: OH 119 μm Band 7 imaging and double-Gaussian fit | R: Blue-shifted absorption at -669±87 km/s, v98=-1574 km/s | F: Fast molecular outflow detected unambiguously | **supported**
- H: Is the outflow strong enough to quench star formation? | E: LTE thin-shell model plus empirical relation compared to AGN-corrected SFR | R: Mdot~1700 Msun/yr, eta~2, tdep (2-4)e7 yr | F: Rapid quenching implied | **supported**
- H: Does Mdot correlate with LIR at 4<z<6.4? | E: Power-law fit to 11 sources | R: k=1.61±0.40, R^2=0.64 | F: Positive correlation with large scatter | **partially**
- H: Can outflowing gas escape the host? | E: Compare v_out with escape velocity from dynamical mass | R: vesc~780 km/s comparable to 670 km/s | F: Up to ~50% may escape | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: OH 119 μm P-Cygni profile unambiguously distinguishes outflow from inflow, unlike CO/[CII] broad wings  
  > "The 119 $\ensuremath{\mu}m$ doublet can unambiguously reveal the presence of cold molecular outflows and/or inflows through its P-Cygni profile" (Introduction)
- Alternative: Interactive tclean tried; no obvious difference vs automasking  
  > "We also tried `tclean` in interactive mode, but there was no obvious difference in the result" (Observations and data reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass outflow rate uncertainty dominated by poorly constrained OH abundance  
  > "Clearly, the uncertainty of the mass outflow rate is dominated by the poorly constrained OH abundance." (4.2.1)
- Limitation (authors): Almost no line-free channels in USB; simple fitting assumptions  
  > "Given the fact that there are almost no line-free channels in the USB spectrum and that fitting was done under simple assumptions" (3.3)
- Caveat (inferred, ours): OH abundance, covering factor and radius were chosen so LTE result matches the empirical relation (partly circular)
- Caveat (inferred, ours): Continuum level fitted simultaneously with a broad line, degenerate with absorption depth
- Caveat (inferred, ours): Marginal spatial resolution; velocity gradients have large uncertainties
- Caveat (inferred, ours): Mdot-LIR fit on 11 sources with heterogeneous methods

## Reproducibility

- Data public (paper): ALMA data from 2021.1.01305.S and 2019.1.00672.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.01305.S, ADS/JAO.ALMA#2019.1.00672.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact tclean parameters and CASA version
- Missing: Line fitting initial conditions and aperture mask
- Missing: CIGALE parameter grids
- Missing: Comparison-sample values for scaling relation
- Data volume (inferred): ~100-300 GB raw for nine EBs in Band 7
- Score (inferred): 4/5, Recipe is mostly clear with numeric tables, but several imaging and fitting details are missing.
- Rediscovery candidate: yes, Cycle 8 data should be archival, the recipe is mostly complete, and the results are numeric (Table 2 and Table 3).

## Links

- Method: (cite: Vei20) (outflow mass and rate formalism)
- Method: (cite: HC20) (empirical OH outflow rate recipe)
- Method: (cite: Spi20b) (modified recipe and f=0.3)
- Method: (cite: Kep20) (auto-multithresh)
- Method: (cite: Boq19) (CIGALE)
- Companion: (cite: But23) (OH detections in z~6 quasars used in comparison sample)
- Companion: (cite: Has19) (previous ALMA data on this quasar)
- Related: Fujimoto et al. in prep. ([CII] 2019.1.00672.S)

## Checks

```json
{
 "quotes": 92,
 "quotes_ok": 92,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 66,
  "rate": 0.75
 },
 "evidence_ok": true
}
```
