# Sintering-induced Dust Ring Formation in Protoplanetary Disks: Application to the HL Tau Disk

`2016ApJ...821...82O` | The Astrophysical Journal 2016 | first author: Okuzumi, Satoshi | arXiv: 1510.03556 | DOI: 10.3847/0004-637X/821/2/82

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can aggregate sintering near volatile snow lines explain the multiple bright and dark dust rings seen by ALMA in the HL Tau disk?  
  > "We attempt to explain the multiple ring structure as a consequence of aggregate sintering." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "In accordance with (cite: ALMA+15), we set $d = 140~{\rm pc}$, the standard mean distance to Taurus." (4.6 Dust Thermal Emission); "assuming the disk inclination angle of $46.7^{\circ}$ and the position angle of $138^{\circ}$ (cite: ALMA+15)" (2.1 Temperature Profile); distance from standard mean distance to Taurus, following ALMA Partnership 2015  
  > "In accordance with (cite: ALMA+15), we set $d = 140~{\rm pc}$, the standard mean distance to Taurus." (4.6 Dust Thermal Emission); "assuming the disk inclination angle of $46.7^{\circ}$ and the position angle of $138^{\circ}$ (cite: ALMA+15)" (2.1 Temperature Profile)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: Bands 3, 6, 7 (2.9, 1.3, 0.87 mm)  
  > "We deproject the intensity maps of the disk’s dust continuum at ALMA Bands 3, 6, and 7 into circularly symmetric views" (2.1 Temperature Profile)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: sqrt(85.3x61.1), sqrt(35.1x21.8), sqrt(29.9x19.0) mas at 2.9, 1.3, 0.87 mm  
  > "FWHM angular resolutions of $\sqrt{85.3\times61.1}$, $\sqrt{35.1\times21.8}$, and $\sqrt{29.9\times19.0}$ mas for $\lambda = 2.9$, 1.3, and 0.87 mm" (4.6 Dust Thermal Emission)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: HL Tau ALMA Long Baseline Campaign continuum images/radial profiles at Bands 3, 6, 7 and flux densities 0.0743, 0.744, 2.14 Jy  
  > "the flux densities reported by the ALMA observation are 0.0743, 0.744, and 2.14 Jy at $\lambda = 0.87$, 1.3, and 2.9 mm (Bands 7, 6, and 3), respectively (cite: ALMA+15)" (5.1 Evolution of the Total Dust Mass and Flux Densities) [from (cite: ALMA+15)]
- External data: Cometary volatile abundances relative to H2O  
  > "take their abundances relative to ${\rm H_2O}$ to be consistent with cometary values (cite: MC11)" (3.1 Volatile Composition) [from (cite: MC11)]
- External data: Vapor pressure parameters L_j, A_j  
  > "we follow (cite: S11b) and take the values from Table 2 of (cite: YNF83)" (3.2 Equilibrium Vapor Pressures) [from (cite: YNF83); (cite: S11b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk inclination, position angle, distance, observed intensity maps and resolutions taken from ALMA Partnership paper  
  > "We use $i = 46.7^\circ$ for the HL Tau disk (cite: ALMA+15)." (4.6 Dust Thermal Emission) [from (cite: ALMA+15)]
- Sintering timescale formula and molecular volumes/surface energies  
  > "we use the same set of $V_{{\rm mol},j}$ and $\gamma_j$ adopted by (cite: S11b)" (3.4 Sintering Zones) [from (cite: S11b)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA image products/deprojection and azimuthal averaging details used to build Figure 1
- Numerical solver and time-stepping scheme for the single-size equations
- Code not released

## Analysis recipe

1. **derive temperature profile**: Deproject ALMA Band 3/6/7 maps, azimuthally average, assume Band 7 optically thick at center, 20 and 40 AU, fit single power law  
  > "we assume that the Band 7 emission is optically thick and hence $T(r) = T_{\rm B}$ at the center, 20 AU, and 40 AU." (2.1 Temperature Profile)
   - parameter: T = 310 (r/1 AU)^-0.57 K  
  > "T(r) = 310 \biggl( {\displaystyle\frac{r}{1~{\rm AU}}} \biggr) ^{-0.57}~{\rm K}," (2.1 Temperature Profile)
   - fitting: _not stated_
   - validation: _not stated_
2. **simulate global dust evolution**: Single-size approach with coagulation, sintering-dependent fragmentation, and radial drift on 300 log radial bins from 1 to 1000 AU  
  > "discretizing the radial direction into 300 logarithmically spaced binds spanning from $r_{\rm in} = 1~{\rm AU}$ and $r_{\rm out} = 1000~{\rm AU}$" (4.1 The Single-size Approach for Global Dust Evolution)
   - parameter: Mdisk=0.2 Msun, rc=150 AU, gamma=1, a0=0.1 um, alpha_t=0.03(r/10AU)^1/2 (fiducial)  
  > "Run Sa0 is our fiducial model and assumes $\gamma = 1$, $a_0 = 0.1~\ensuremath{\mu}m$, and $\alpha_{\rm t} = 0.03(r/10~{\rm AU})^{1/2}$." (4.7 Parameter Sets and Initial Conditions)
   - assumption: Initial dust-to-gas 0.01; aggregate internal density 0.26 g/cm3 (porosity 80%)  
  > "The aggregate internal density is fixed to be $0.26~{\rm g~cm^{-3}}$ assuming a material (monomer) density of $1.3~{\rm g~cm^{-3}}$ and a constant aggregate porosity of 80%." (4 Simulation Method)
   - fitting: _not stated_
   - validation: Snapshot time chosen by minimizing relative errors vs observed flux densities  
  > "search for the time $t =t_{\rm snap}$ at which the sum of the relative errors is minimized." (5.1 Evolution of the Total Dust Mass and Flux Densities)
3. **compute emission and compare with ALMA**: Opacity from Kataoka et al. 2014 analytic expression with a^-3.5 size distribution; intensities I_nu=(1-exp(-tau))B_nu; smooth to ALMA resolutions; compare T_B and spectral index profiles  
  > "We calculate the absorption cross section of porous aggregates using the analytic expression by (cite: KOTN14), which is based on Mie calculations with effective medium theory." (4.5 Aggregate Opacity)
   - fitting: _not stated_
   - validation: Ring radii and brightness temperatures compared with ALMA profiles  
  > "model Sa0-NoSint reproduces the ring radii in the observed image to an accuracy of $\ensuremath{\lesssim} 30\%$" (6.4 Sublimation Energies)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-match snapshot time, fiducial Sa0 | 0.26 | not stated | Myr | 2 | we find that the sum of the relative errors in the flux densities is minimized when $t = 0.26~{\rm Myr}$. |
| Simulated flux densities at 2.9, 1.3, 0.87 mm | 0.070, 0.79, 2.2 | within 6% of observed | Jy | 3 | the flux densities in the simulation are 0.070, 0.79, and 2.2 Jy at $\lambda =$ 2.9, 1.3, and 0.87 mm, respectively |
| Sintering zone locations (Sa0) | 3–6 AU (H2O), 11–23 AU (NH3–CO2–H2S), 24–33 AU (C2H6), 80–106 AU (CH4), 116–160 AU (CO) | not stated | AU | 2 | 3–6 AU (${\rm H_2O}$), 11–23 AU (${\rm NH_3}$–${\rm CO_2}$–${\rm H_2S}$), 24–33 AU (${\rm C_2H_6}$), 80–106 AU (${\rm CH_4}$), and 116–160 AU (${\rm CO}$) |

## Qualitative findings

- Sintering zones appear as optically thick bright rings with spectral index ~2; non-sintering zones are darker with index 2.3–2.5  
  > "these sintering zones appear as bright, optically thick rings with a spectral slope of $\approx 2$" (abstract)

## Claim tuples

- H: Sintering-induced fragmentation produces dust rings matching HL Tau | E: Global dust evolution simulations with sintering, compared with ALMA profiles | R: Bright rings at snow-line-adjacent sintering zones reproduce central peak, brightness temperatures and spectral index | F: Sintering can explain major bright and dark rings | **supported**
- H: Dust settling and ring formation can coexist | E: Runs La0 and LLa0 with larger monomers and weaker turbulence | R: Works only for 1 um ≲ a0 < 4 um and 1e-4 < alpha_t ≲ 1e-3 | F: Monomers micron-sized and turbulence weak | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Ring locations depend on vapor pressure uncertainties; single-size approach and fixed porosity are simplifications  
  > "A probably more critical limitation of the single-size approach is that one has to assume the size distribution of fragments" (7.2 Limitations of the Single Size Approach)
- Caveat (inferred, ours): Temperature profile is tuned to the optically thick assumption
- Caveat (inferred, ours): Many free parameters tuned to match rings
- Caveat (inferred, ours): Ring positions off by up to 30%

## Reproducibility

- Data public (paper): ALMA Science Verification data cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00015.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Simulation code and numerical scheme
- Missing: Exact extracted ALMA profiles
- Data volume (inferred): small (published ALMA images/profiles only)
- Score (inferred): 3/5, Model equations and parameters are given in detail, but code is not released and ALMA data use is minor.
- Rediscovery candidate: no, Main work is a theoretical simulation, not ALMA data reduction.

## Links

- Method: (cite: OTKW12) (collision velocity expressions and drift-limited growth)
- Method: (cite: KOTN14) (aggregate opacity)
- Companion: (cite: ALMA+15) (HL Tau ALMA observations)
- Companion: (cite: ZBB15) (snow-line interpretation of HL Tau rings)
- Related: ALMA Long Baseline Campaign

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 21,
  "rate": 0.339
 },
 "evidence_ok": true
}
```
