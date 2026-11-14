# ALMA CO Observations of the Host Galaxies of Long-duration Gamma-Ray Bursts. I. Molecular Gas Scaling Relations

`2020ApJ...892...42H` | The Astrophysical Journal 2020 | first author: Hatsukade, Bunyo | arXiv: 2002.09121 | DOI: 10.3847/1538-4357/ab7992

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, nearby_galaxies, star_formation
- Question: Do GRB host galaxies have molecular gas properties (gas fraction, depletion time) that differ from other star-forming galaxies, once selection bias relative to the main sequence is accounted for?  
  > "In order to understand the molecular gas properties in GRB hosts, a larger sample with CO observations is necessary." (1 Introduction)
- Target **14 GRB hosts (GRBs 980703, 021211, 031203, 050826, 051006, 051117B, 060814, 070306, 071021, 081109A, 100621A, 110918A, 130925A, 140301A)**: coordinates _not stated_; z/distance z = 0.1055 (GRB 031203) to 2.452 (GRB 071021); spectroscopic redshifts  
  > "| 050826 | $0.296\pm0.001$ | 4 |" (Table 1); distance from Spectroscopic redshifts from the literature (Table 1 references); luminosity distance from H0=70, Om=0.3, OL=0.7  
  > "| 050826 | $0.296\pm0.001$ | 4 |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00939.S, 2016.1.00455.S
- bands: Band 4, 6 or 7 depending on target redshift  
  > "the CO(3–2) or CO(4–3) line was observed at band 4, 6, or 7 depending on the target redshift." (2.2 Observations and Results)
- frequencies and spectral setup: Four spectral windows, 1875 MHz each (488.28 kHz x 3840 channels), total 7.5 GHz  
  > "The correlator was used in the frequency domain mode with a bandwidth of 1875 MHz (488.28 kHz $\times$ 3840 channels). Four spectral windows were used, providing a total bandwidth of 7.5 GHz." (2.2 Observations and Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-2/3, C36-3, C40-4, C40-5, C40-6 (per target in observation table)  
  > "| 980703 | 4–3 | 6 | 234.507 | 2016-05-22 | C36-3 | 30 | 37 | 16.5–640.0 |" (Table 2)
- baselines: _not stated_
- angular resolution: Natural-weighted beams 0.19–1.52 arcsec; tapered (0.8 arcsec) 0.85–1.07 arcsec  
  > "| 050826 | 3–2 | 6 | 266.818 | 2016-10-19 | C40-6 | 81 | 44 | 16.7–1800 | $0.19 \times 0.18$ | $0.88 \times 0.74$ |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 11–90 min per execution  
  > "| 051117B | 4–3 | 6 | 233.567 | 2016-10-19 | C40-6 | 90 | 44 | 16.7–1800 |" (Table 2)
- observing dates: March–November 2016 (Cycle 3 and 4)  
  > "ALMA observations of the targets were conducted in March–November, 2016, for the Cycle 3 and Cycle 4 programs" (2.2 Observations and Results)
- pi or archival as stated: _not stated_
- Line: CO J=3–2 (not stated)
- Line: CO J=4–3 (not stated)
- Other facility **GHostS database, Perley et al. compilations, Dark Energy Survey**: UV-to-radio photometry for SED fitting  
  > "The photometry data of our targets are taken from the GHostS database ([www.grbhosts.org](www.grbhosts.org) and references therein), (cite: perl16), and (cite: perl17a)." (3 SED Fit)
- Other facility **Hubble Legacy Archive / DES**: optical images for comparison with CO maps  
  > "along with optical images taken from the Hubble Legacy Archive[^1] and the public data of the Dark Energy Survey" (2.2 Observations and Results)
- External data: CO observations, SFR, M*, metallicity of 11 literature GRB hosts (Appendix table)  
  > "Six hosts with CO detection (GRBs 980425, 051022, 080207, 080517, 111005A, and 190114C) and five hosts with upper limits (GRBs 000418, 030329, 060505, 060814, and 100316D)." (2.1 GRB Hosts) [from mich18; hats14; arab18; hats19; stan15; deug19 etc.]
- External data: Comparison star-forming galaxy sample and scaling relations (1444 galaxies, z=0–4)  
  > "the distribution of star-forming galaxies compiled by (cite: tacc18) is shown as a color distribution." (5.3 Gas Fraction, Depletion Timescale, and Scaling Relation) [from (cite: tacc18)]
- External data: Main-sequence relation for star-forming galaxies  
  > "MS star-forming galaxies at $z = 0.1$–2.5, taken from (cite: spea14)" (2.1 GRB Hosts) [from (cite: spea14)]
- External data: Metallicity-dependent alpha_CO relation  
  > "We adopted the relation between metallicity and $\alpha_{\rm CO}$ of (cite: genz15)" (4.2 Molecular Gas Mass) [from (cite: genz15); (cite: genz12); (cite: bola13); (cite: tacc18)]

## Processing

### Calibration

- pipeline or manual: ALMA QA2 data; QA2 PASS except GRB 031203 (SEMIPASS)  
  > "The second level of Quality Assurance (QA2) performed by the ALMA data reduction team was “PASS” except for the data set of the GRB 031203 host" (2.2 Observations and Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "created with natural weighting without tapering the $uv$ data." (Table 2)
- uv taper: 0.8 arcsec taper for tapered maps  
  > "created with natural weighting and $0.8\ensuremath{''}$ taper." (Table 2)
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

- CO line luminosity formula  
  > "The CO luminosity was calculated as follows (cite: solo05)" (4.2 Molecular Gas Mass) [from (cite: solo05)]
- alpha_CO(Z) with harmonic mean for low-metallicity hosts  
  > "we adopted the harmonic mean of the two relations by following (cite: tacc18)." (4.2 Molecular Gas Mass) [from (cite: tacc18)]
- Dust mass and L_FIR formalism  
  > "The FIR luminosity and dust mass were derived as (cite: debr03)" (4.3 Dust Mass, FIR Luminosity, and SFR) [from (cite: debr03)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration scripts/pipeline version
- Imaging details: tclean parameters, cell/image size, deconvolver, masks, line-free channels, continuum subtraction
- Channel width/velocity resolution used for integrated maps and spectrum extraction aperture
- How CO flux, line width and S/N were measured (fitting method)
- CIGALE parameter grid (tau, ages, burst, attenuation, etc.)
- Which flux calibrator and flux uncertainty
- How δMS was computed for each host and error handling for Pearson r

## Analysis recipe

1. **Measure CO line fluxes and continuum**: Velocity-integrated CO maps and continuum maps; 3 sigma upper limits for non-detections assuming 180 km/s line width  
  > "For non-detection hosts, we derived 3$\sigma$ upper limits by assuming a line width of 180 km s$^{-1}$" (4.2 Molecular Gas Mass)
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting for SFR and stellar mass**: CIGALE with delayed SFH, BC03 SSP, Chabrier IMF, nebular emission, modified starburst attenuation, dl2014 dust emission, radio module  
  > "We adopt a SFH of the delayed SFH with an optional exponential burst (`sfhdelayed`)" (3 SED Fit)
   - software: CIGALE, CLOUDY
   - fitting: Likelihood analysis of model grid  
  > "The models are fitted to the data and physical properties are estimated through the analysis of the likelihood distribution." (3 SED Fit)
   - validation: Stellar masses compared with previous studies  
  > "The stellar masses are overall consistent with previous studies" (3 SED Fit)
3. **Derive molecular gas mass**: L'CO from Solomon & Vanden Bout formula, converted to CO(1–0) with r31=0.6, r41=0.4, times metallicity-dependent alpha_CO  
  > "we adopted the line ratios of CO(3–2)/CO(1–0) $=r_{31}$ $=0.6$ and CO(4–3)/CO(1–0) $=r_{41}$ $=0.4$" (2.1 CO Line Luminosity Ratios)
   - assumption: alpha_CO(Z) of Genzel+15 (harmonic mean of Genzel+12 and Bolatto+13 at low metallicity), metallicity on Pettini & Pagel scale  
  > "The adopted metallicity-dependent conversion factor $\alpha_{\rm CO}(Z)$ is 4–15 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (4.2 Molecular Gas Mass)
   - fitting: _not stated_
   - validation: Compared with Galactic alpha_CO=4.4 (mass smaller by up to factor 3)  
  > "derived molecular gas mass would be smaller at most by a factor of 3 for hosts with a larger $\alpha_{\rm CO}(Z)$" (4.2 Molecular Gas Mass)
4. **Derive dust mass, L_FIR and FIR SFR**: Optically thin modified blackbody from single continuum flux  
  > "adopt $\kappa_d(125\ \mu m) = 2.64 \pm 0.29$ m$^2$ kg$^{-1}$ (cite: dunn03) and $\beta = 1.5$." (4.3 Dust Mass, FIR Luminosity, and SFR)
   - assumption: T_dust = 40 K; SFR = 1.72e-10 L_FIR (Kennicutt98) scaled to Chabrier  
  > "In this study, we adopted $T_{\rm dust} = 40$ K" (4.3 Dust Mass, FIR Luminosity, and SFR)
   - fitting: _not stated_
   - validation: Sensitivity to T_dust 30 or 50 K tested  
  > "If we adopt $T_{\rm dust} = 30$ or 50 K, the dust mass would change by a factor of 1.5 and 0.8, and SFR would change by a factor of 0.3 and 2.6." (4.3 Dust Mass, FIR Luminosity, and SFR)
5. **Compare with scaling relations vs. delta MS**: Plot mu_gas and t_depl vs redshift and δMS against Tacconi+18 relations; Pearson correlation  
  > "The Pearson’s correlation coefficients estimated for the CO-detected hosts are $r = 0.79$ and $r = -0.59$" (5.3 Gas Fraction, Depletion Timescale, and Scaling Relation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CIGALE** : SED fitting for SFR and stellar mass  
  > "We adopt a SED modeling code of Code Investigating GALaxy Emission" (3 SED Fit)
- **CLOUDY** : nebular emission modelling within CIGALE  
  > "where `CLOUDY` (cite: ferl98; ferl13) is used" (3 SED Fit)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO-detected hosts | 8 of 14 | not stated | hosts | 1 | We detected CO emission in eight hosts at $z = 0.3$–2 |
| Molecular gas mass range of detected hosts | (0.2–6)e10 | not stated | Msun | 3 | The derived molecular gas mass is $M_{\rm gas} =$ (0.2–$6) \times 10^{10}$$M_{\odot}$ |
| alpha_CO(Z) range | 4–15 | not stated | Msun (K km/s pc^2)^-1 | 3 | The adopted metallicity-dependent conversion factor $\alpha_{\rm CO}(Z)$ is 4–15 |
| M_gas, GRB 051006 host | 3.6e10 | 0.4e10 | Msun | 3 | / 051006 / 1.057 / $263\pm39$ / $0.69\pm0.07$ / 10 / $2.7\pm0.3\times10^9$ / $(3.6\pm0.4)\times10^{10}$ |
| M_gas/M_dust, GRB 051006 / 051117B / 110918A | 1730 / 640 / 840 | 560 / 260 / 210 | dimensionless | 4 | $M_{\rm gas}/M_{\rm dust} = 1730\pm560$, $640\pm260$, and $840\pm210$ for the hosts of GRBs 051006, 051117B, and 110918A |
| Pearson r, mu_gas vs δMS | 0.79 | not stated | dimensionless | 5 | $r = 0.79$ and $r = -0.59$ for the distribution of $\mu_{\rm gas}$ and $t_{\rm depl}$ |
| Pearson r, t_depl vs δMS | -0.59 | not stated | dimensionless | 5 | $r = 0.79$ and $r = -0.59$ for the distribution of $\mu_{\rm gas}$ and $t_{\rm depl}$ |
| CO(3–2)/CO(2–1) lower limit, GRB 060814 host | > 0.32 | 3 sigma | dimensionless | 3 | The obtained lower limit for the line luminosity ratio was CO(3–2)/CO(2–1) $> 0.32$ (3$\sigma$). |

## Qualitative findings

- Two hosts (110918A, 140301A) show rotation-consistent velocity gradients; others more disturbed  
  > "Two GRB hosts (GRBs 110918A and 140301A) show velocity gradient consistent with rotation" (2.2 Observations and Results)

## Claim tuples

- H: GRB hosts have higher gas fraction and shorter depletion time than other SFGs | E: Compare mu_gas and t_depl vs redshift with Tacconi+18 sample | R: GRB hosts tend to have higher mu_gas and shorter t_depl, especially z<~1 | F: Could be a common property or selection effect from being above the MS | **partially**
- H: GRB hosts follow the same δMS scaling relations as other SFGs | E: mu_gas and t_depl vs δMS | R: mu_gas increases and t_depl decreases with δMS; r=0.79, -0.59 | F: No molecular gas deficit at given SFR and stellar mass | **supported**
- H: GRB hosts share dynamics with other SFGs | E: L'CO vs FWHM comparison | R: Hosts overlap MS and local galaxies | F: Similar geometry and kinematics | **supported**

## Reasoning

- Why this data: Needed a larger CO sample; targets chosen with spectroscopic z, observable lines, high SFR, z<=2.5  
  > "(iv) located at moderate redshifts ($z \le 2.5$) to ensure a significant constraint on the molecular gas mass." (2.1 GRB Hosts)
- Why this method: _not stated_
- Alternative: Galactic alpha_CO=4.4 would give masses lower by up to 3; ULIRG alpha_CO rejected since hosts are not ULIRGs  
  > "our targets are not categorized as ULIRGs" (4.2 Molecular Gas Mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Targets biased toward high SFR; CO line ratio uncertain (mass could vary by factor of a few)  
  > "Because our targets for CO observations in this study were biased toward higher SFRs, it is important to construct an “unbiased” sample" (6 Conclusions)
- Limitation (authors): Gas mass uncertain by factor of a few from line ratios  
  > "We note that the derived molecular gas mass could vary by a factor of a few due to the uncertainty of CO line ratios." (2.1 CO Line Luminosity Ratios)
- Caveat (inferred, ours): Assumed r31/r41 and single T_dust=40 K drive results
- Caveat (inferred, ours): Many gas-fraction points are upper limits
- Caveat (inferred, ours): Heterogeneous comparison samples and alpha_CO choices
- Caveat (inferred, ours): Small sample with correlation from only detected hosts

## Reproducibility

- Data public (paper): ALMA project codes given; data presumably public via archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00939.S and #2016.1.00455.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: CIGALE module parameter grids
- Missing: Spectrum extraction apertures and line fitting method
- Data volume (inferred): ~100–300 GB raw for 14 targets (Band 4/6/7, 7.5 GHz bandwidth)
- Score (inferred): 5/5, Data identifiable and formulae for derived quantities are given, but imaging and SED parameters are missing.
- Rediscovery candidate: no, Imaging/extraction settings and SED setup incomplete, and the comparison relies on external compiled samples.

## Links

- Method: (cite: tacc18) (scaling relations and alpha_CO prescription)
- Method: (cite: boqu19) (CIGALE SED code)
- Method: (cite: solo05) (CO luminosity formula)
- Companion: (cite: hats19) (detailed study of GRB 080207 host with ALMA/VLA)
- Related: GHostS database
- Related: ALLSMOG
- Related: xCOLD GASS
- Related: Dark Energy Survey

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 75,
  "stated": 40,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
