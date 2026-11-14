# A Massive Molecular Torus inside a Gas-poor Circumnuclear Disk in the Radio Galaxy NGC 1052 Discovered with ALMA

`2020ApJ...895...73K` | The Astrophysical Journal 2020 | first author: Kameno, Seiji | arXiv: 2004.09369 | DOI: 10.3847/1538-4357/ab8bd6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies, astrochemistry
- Question: How does mass accretion work in the gas-poor radio galaxy NGC 1052: what are the gas content and kinematics of the circumnuclear disk and of a molecular torus seen in absorption?  
  > "We report ALMA observations of NGC 1052 to quest mass accretion in a gas-poor active galactic nucleus (AGN)." (abstract)
- Target **NGC 1052**: coordinates _not stated_; z/distance D_A = 17.5 Mpc, D_L = 17.6 Mpc, 85 pc/arcsec; V_LSR = 1492 km/s  
  > "Thanks to the proximity with the angular distance of 17.5 Mpc ($1^{\prime \prime}$ corresponds to 85 pc)" (1 Introduction); "We employ the systemic velocity of $V_{\rm LSR, radio} = 1492$ km s$^{-1}$ based on our measurements" (1 Introduction); distance from derived from the measured systemic velocity with H0 = 73 km/s/Mpc, Omega_M = 0.27, Omega_Lambda = 0.73, V_CMB = 371 km/s  
  > "Thanks to the proximity with the angular distance of 17.5 Mpc ($1^{\prime \prime}$ corresponds to 85 pc)" (1 Introduction); "We employ the systemic velocity of $V_{\rm LSR, radio} = 1492$ km s$^{-1}$ based on our measurements" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.01225.S
- bands: Bands 6 and 7 (CO J=2-1 at 230 GHz; CO J=3-2 and HCN J=4-3 near 345-355 GHz); three frequency setups  
  > "consisting of five executions at three different frequency setups" (2 Observations and data reduction); "a_06 | Xa76868/X2423 | 2015-08-05 | 229.407" (Table 1)
- frequencies and spectral setup: 4 basebands of 2 GHz, dual linear polarization; 15.625 MHz channels with Hanning window (40.8, 27.3, 26.6 km/s for CO 2-1, CO 3-2, HCN 4-3)  
  > "We used 4 basebands (BBs) of 2-GHz bandwidth in dual linear polarization." (2 Observations and data reduction); "channel spacing of 2 GHz/128 ch $= 15.625$ MHz and the Hanning window" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 36-42 antennas per execution  
  > "a_07 | Xa7c533/X1dc7 | 2015-08-11 | 344.100 | 42" (Table 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.298x0.212 arcsec (a_06), 0.209x0.145 arcsec (a_07), 0.184x0.145 arcsec (b_07), natural weighting  
  > "a_07 | $0^{\prime \prime}.209$ | $0^{\prime \prime}.145$ | $58^{\circ}.3$" (Table 2)
- max recoverable scale: 1.8, 1.5, 1.1 arcsec for a_06, a_07, b_07  
  > "b_07 | $0^{\prime \prime}.184$ | $0^{\prime \prime}.145$ | $59^{\circ}.8$ | $1^{\prime \prime}.1$" (Table 2)
- sensitivity: continuum rms 11.8-21.3 uJy/beam; per-channel rms 273.9-327.7 uJy/beam  
  > "a_06 | $0^{\prime \prime}.298$ | $0^{\prime \prime}.212$ | $55^{\circ}.4$ | $1^{\prime \prime}.8$ | $11.8$ | $273.9$ | 0.101" (Table 2)
- time on source: 22.7 to 47.4 min per execution plus 2.5-5.6 min as phase calibrator  
  > "b_07 | Xa830fc/X1a2f | 2015-08-16 | 352.767 | 36 | $47.4 + 5.6$" (Table 1)
- observing dates: 2015-08-05 to 2015-08-16  
  > "b_07 | Xa830fc/X16e2 | 2015-08-16 | 352.767" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Line: CO J=3-2 (345.796 GHz)
- Line: HCN J=4-3 v=0 (354.505 GHz)
- Line: HCO+ J=4-3 v=0 (356.734 GHz)
- Line: H13CN J=4-3 v=0 (345.340 GHz)
- Other facility **HST 1.6 micron image**: dust absorption feature compared with the CND  
  > "The CND structure coincides with the dust absorption feature identified in the Hubble Space Telescope (HST) 1.6 $\mu$m image" (3.2 CO emission)
- External data: Black-hole mass 1.5e8 Msun from stellar velocity dispersion  
  > "black-hole mass of $1.5 \times 10^8$ M$_{\odot}$ derived with stellar velocity dispersion" (4.2 Circum-Nuclear Disk) [from Woo & Urry 2002 (cite: 2002ApJ...579..530W)]
- External data: HCN-to-H2 abundance (0.2-4.1)e-9  
  > "Applying abundance ratios of $(0.2-4.1) \times 10^{-9}$ in HCN-to-H$_2$" (4.5.3 Molecular gas mass of the torus) [from Smith & Wardle 2014 (cite: 2014MNRAS.437.3159S)]
- External data: HCO+-to-H2 abundance (2-3)e-9  
  > "$(2 - 3) \times 10^{-9}$ in HCO$^{+}$-to-H$_2$" (4.5.3 Molecular gas mass of the torus) [from Liszt, Pety & Lucas 2010 (cite: 2010A&A...518A..45L)]
- External data: CO-to-H2 abundance ~1e-4  
  > "$\sim 10^{-4}$ in CO-to-H$_2$" (4.5.3 Molecular gas mass of the torus) [from Bolatto et al. 2013 (cite: 2013ARA&A..51..207B)]
- External data: CO luminosity conversion formula  
  > "using the conversion formula described by (cite: 2005ARA&A..43..677S)" (3.2 CO emission) [from Solomon & Vanden Bout 2005 (cite: 2005ARA&A..43..677S)]

## Processing

### Calibration

- pipeline or manual: standard calibration procedures in CASA, plus phase self-calibration on NGC 1052 itself  
  > "following standard calibration procedures except phase calibration toward the target source of NGC 1052 itself (i.e. self calibration)" (2 Observations and data reduction)
- casa version: CASA 5.6.0  
  > "We used CASA 5.6.0 for calibration and imaging" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120, J0238+1636, J0339-0146, J0244+0659 with assumed flux densities of 1.129, 3.110, 2.051, 0.882, 3.391 Jy  
  > "assuming the flux densities of 1.129 Jy, 3.110 Jy, 2.051 Jy, 0.882 Jy, 3.391 Jy" (2 Observations and data reduction)
- flux scale uncertainty: 4.4% systematic  
  > "we estimated systematic errors in flux scaling by 4.4%" (2 Observations and data reduction)
- self calibration: phase self-calibration on NGC 1052 (J0241-0815 also used as phase calibrator in some scans)  
  > "The control software chose J0241-0815, which is NGC 1052 itself, as the phase calibrator in some scans" (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used natural weighting for synthesis imaging to maximize the signal-to-noise ratio (SNR)" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: visibility-domain subtraction before CO emission imaging  
  > "The CO emission-line images were processed after continuum subtraction in the visibility domain." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: two executions combined each for a_07 and b_07 after calibration  
  > "two executions were combined after the calibration processes" (2 Observations and data reduction)
- smoothing: _not stated_
- final beam: 0.209x0.145 arcsec (a_07)  
  > "a_07 | $0^{\prime \prime}.209$ | $0^{\prime \prime}.145$ | $58^{\circ}.3$" (Table 2)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- tclean parameters (cell size, image size, niter, threshold, mask)
- line-free channels used for continuum subtraction
- self-calibration solution intervals and reference
- pixel/aperture used for the extracted core absorption spectra
- fitting details (sampler, weights, errors) for Gaussian and covering-factor solutions
- how the CND gas mass was integrated (aperture, masks)
- line identification catalog usage (beyond CDMS/JPL mention)
- how the R = 2.4 +/- 1.3 pc range was combined from the grid

## Analysis recipe

1. **Calibrate and image**: CASA standard calibration with phase self-calibration on the target, natural-weight imaging, visibility-domain continuum subtraction  
  > "We used natural weighting for synthesis imaging to maximize the signal-to-noise ratio (SNR) targeting absorption spectra toward the compact core." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: flux scale compared between executions and spectral windows (4.4%)  
  > "By comparing flux densities of flux calibrators between different observations and spectral windows" (2 Observations and data reduction)
2. **Identify CO clouds and CND, derive luminosities and gas mass**: Threshold detection in CO 3-2 and 2-1 channel maps; L'CO from Solomon & Vanden Bout formula; mass via L'CO(3-2) with alpha_CO  
  > "peak intensity of CO ($J=3-2$) emission exceeds a threshold of $1.94$ mJy beam$^{-1}$, 7 times as high as the spectral rms" (3.2 CO emission)
   - software: CASA
   - parameter: alpha_CO(1-0) = 0.8 Msun (K km/s pc^2)^-1, thermalized CO transitions  
  > "with the CO conversion factor of $\alpha_{\rm CO (1-0)} = 0.8$ M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (4.2 Circum-Nuclear Disk)
   - assumption: alternative Cen A-like X_CO = 5e20 gives 4.8e6 Msun  
  > "$M_{\rm H_2} = 4.8\times 10^6$ M$_{\odot}$" (4.2 Circum-Nuclear Disk)
   - fitting: _not stated_
   - validation: comparison with Seyfert CND masses and Circinus  
  > "comparable to the Circinus galaxy" (4.2 Circum-Nuclear Disk)
3. **Measure CND kinematics and enclosed mass**: Linear regression on P-V diagram, terminal velocity, M_enc = R V^2 / G; Gaussian decomposition of rotation-subtracted profile  
  > "$\displaystyle M_{\rm enc} = \frac{RV^2}{G} = (2.13 \pm 0.09) \times 10^9$ M$_{\odot}$" (4.2 Circum-Nuclear Disk)
   - assumption: CND rotationally supported ring seen edge-on  
  > "If we assume the CND is rotationally supported without significant radial motions" (4.2 Circum-Nuclear Disk)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit absorption lines**: Single (or multi) Gaussian fits in optical depth to the core spectrum  
  > "together with single Gaussian fitting to characterize the optical depth, LSR velocity, and line width" (3.3 Absorption features)
   - software: R
   - fitting: _not stated_
   - validation: _not stated_
5. **Column densities of absorbers**: LTE column density formula with equivalent width  
  > "derived assuming local thermodynamic equilibrium (LTE) as" (4.4 Column densities of absorption lines)
   - parameter: T_ex = 230 K  
  > "Total molecular column densities assuming $T_{\rm ex}=230$ K" (Table 6)
   - fitting: _not stated_
   - validation: _not stated_
6. **Solve covering factor and optical depth with clumpy torus**: Radiative transfer constraint on H12CN and H13CN line-bottom flux with tau ratio 50, over a grid of Theta (0.4-1.0) and T_ex (50-500 K)  
  > "$\tau_{\ell}($H$^{12}$CN$)/ \tau_{\ell}($H$^{13}$CN) $= 50$" (4.5.1 Covering factor and optical depth)
   - assumption: 12C/13C ~ 50; torus larger than plasma torus (R >= 1 pc)  
  > "If we assume that the typical C$^{12}$-to-C$^{13}$ abundance ratio of $\sim 50$" (4.5.1 Covering factor and optical depth)
   - fitting: _not stated_
   - validation: consistency with KVN covering factor 0.17 and with CO and HCO+ line-bottom fluxes  
  > "Those meet with the observed flux densities of $0.386 \pm 0.015$ Jy and $0.399 \pm 0.016$ Jy, respectively." (4.5.1 Covering factor and optical depth)
7. **Torus gas mass and densities**: N_H2 from HCO+ with abundance ratio; M_torus = 2 pi Theta R^2 N_H2 mu; clump density via f_cov^{3/2}  
  > "$M_{\rm torus} = 2\pi \Theta R^2 N_{\rm H_2} \mu_{\rm H_2} = (1.3 \pm 0.3) \times 10^7$ M$_{\odot}$" (4.5.3 Molecular gas mass of the torus)
   - assumption: HCO+/H2 = (2-3)e-9 chosen for smaller uncertainty  
  > "we adopt the H$_2$ column density estimated by HCO$^{+}$ because of relatively small uncertainty in the abundance ratio" (4.5.3 Molecular gas mass of the torus)
   - fitting: _not stated_
   - validation: _not stated_
8. **Specific angular momentum and sphere of influence**: SAM = V_R R for torus, CND and clouds; Keplerian extrapolation crosses flat rotation at 14.4 pc  
  > "it crosses the inward flat-rotation at $R=14.4$ pc" (4.6 Angular momentum of the CND and the torus)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.0: calibration and imaging  
  > "We used CASA 5.6.0 for calibration and imaging" (2 Observations and data reduction)
- **R** 3.6.1: named in the software list; use not specified  
  > "CASA 5.6.0 (McMullin et al. 2007), R 3.6.1 (The R Foundation)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 222 GHz | 0.487 | 0.02 | Jy | 1 | flux densities of $0.487 \pm 0.02$ Jy and $0.442 \pm 0.02$ Jy at 222 GHz and 350 GHz |
| Core spectral index | -0.22 | 0.01 | dimensionless | 1 | $\alpha = -0.22 \pm 0.01$ |
| CND molecular gas mass | 5.3e5 | not stated | Msun | 2 | $M_{\rm H_2} = 5.3\times 10^5$ M$_{\odot}$ |
| Enclosed mass inside CND | 2.13e9 | 0.09e9 | Msun | 3 | $(2.13 \pm 0.09) \times 10^9$ M$_{\odot}$ |
| CND terminal velocity | 245 | 4.9 | km/s | 3 | $245 \pm 4.9$ km s$^{-1}$ at the radius of 153 pc |
| H12CN peak optical depth | 0.1508 | 0.0018 | dimensionless | 4 | / HCN / $J=4-3, \ {\rm v}=0$ / 354.505 / $0.1508 \pm 0.0018$ |
| Covering factor | 0.17 | +0.06/-0.03 | dimensionless | 6 | $f_{\rm cov} = 0.17^{+0.06}_{-0.03}$ |
| Torus radius | 2.4 | 1.3 | pc | 6 | a radius of $2.4 \pm 1.3$ pc and a thickness ratio of $0.7 \pm 0.3$ |
| Torus H2 column density | 3.3e25 | 0.7e25 | cm^-2 | 7 | $(3.3 \pm 0.7) \times 10^{25}$ cm$^{-2}$ |
| Torus gas mass | 1.3e7 | 0.3e7 | Msun | 7 | $(1.3 \pm 0.3) \times 10^7$ M$_{\odot}$ |
| Clump H2 density | 6.4e7 | 1.3e7 | cm^-3 | 7 | $(6.4 \pm 1.3) \times 10^7$ cm$^{-3}$ |
| Sphere of influence radius | 14.4 | not stated | pc | 8 | it crosses the inward flat-rotation at $R=14.4$ pc |

## Qualitative findings

- CND is a ring with a central void, edge-on, asymmetric (north brighter)  
  > "This indicates that CND structure is ring-like with a void, unlike a filled disk" (4.2 Circum-Nuclear Disk)
- Vibrationally excited HCN and HCO+ detected in absorption; first vib-excited HCO+ outside the Galaxy  
  > "this is the first time vibrationally excited HCO$^+$ is reported outside the Galaxy" (4.5.2 Vibrationally-excited absorption lines)

## Claim tuples

- H: Is the CND gas-rich enough to drive accretion via star formation? | E: CO 2-1/3-2 emission mapping, gas mass and Toomre Q | R: M_H2 = 5.3e5 Msun; Q ~ 500 | F: CND is too gas-poor to drive accretion | **supported**
- H: Do the absorption features arise in a geometrically thick molecular torus rather than the CND? | E: Compare absorption widths to CND emission widths | R: CO FWHM ~167 km/s vs CND 123.7 km/s; HCN wings | F: A thick torus with R=2.4 pc, Theta=0.7 | **supported**
- H: Is the torus massive and clumpy? | E: H12CN/H13CN radiative transfer and HCO+ column density | R: f_cov=0.17; M_torus=1.3e7 Msun | F: Massive clumpy torus inside a gas-poor CND, density meeting H2O maser conditions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CO-based and HCN-based H2 column densities differ; HCO+ adopted for lower abundance uncertainty  
  > "we adopt the H$_2$ column density estimated by HCO$^{+}$ because of relatively small uncertainty in the abundance ratio" (4.5.3 Molecular gas mass of the torus)
- How they decided it was enough: _not stated_
- Limitation (authors): Degeneracy between optical depth and torus thickness remains; needs emission-line measurement with longer baselines  
  > "a degeneracy between the optical depths and the torus thickness still remain." (4.5.1 Covering factor and optical depth)
- Limitation (authors): CO conversion factor may underestimate CND mass by ~10  
  > "then the molecular mass would be underestimated by a factor of $\sim 10$" (4.2 Circum-Nuclear Disk)
- Caveat (inferred, ours): Torus parameters depend on assumed 12C/13C, abundance ratios and T_ex
- Caveat (inferred, ours): Torus geometry is unresolved; R from virial argument with literature BH mass
- Caveat (inferred, ours): Gaussian blend decompositions are uncertain

## Reproducibility

- Data public (paper): Data come from ALMA project 2013.1.01225.S, cited as ADS/JAO.ALMA#2013.1.01225.S; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01225.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean imaging parameters
- Missing: continuum channel selection
- Missing: spectrum extraction aperture
- Missing: assumed fit setups for blended lines
- Data volume (inferred): ~50-150 GB raw for five executions, three Band 6/7 setups
- Score (inferred): 3/5, Data and general recipe given with many numeric results, but imaging parameters and fit details are missing.
- Rediscovery candidate: yes, Archival project code is given, CASA 5.6.0 used, and results are numeric (line optical depths, CND mass, torus parameters).

## Links

- Method: Solomon & Vanden Bout 2005 (cite: 2005ARA&A..43..677S) (CO luminosity conversion)
- Method: Izumi et al. 2018 (cite: 2018ApJ...867...48I) (gas mass from CO 3-2 luminosity)
- Companion: Sawada-Satoh et al. 2016 (cite: 2016ApJ...830L...3S) (KVN HCN absorption and covering factor comparison)
- Companion: Sawada-Satoh et al. 2019 (cite: 2019ApJ...872L..21S) (KVN HCO+ absorption comparison)
- Related: KVN observations of NGC 1052
- Related: PdBI absorption observations (Liszt & Lucas 2004)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
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
  "facts": 86,
  "stated": 51,
  "rate": 0.593
 },
 "evidence_ok": true
}
```
