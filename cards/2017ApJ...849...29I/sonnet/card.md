# ALMA Multiple-transition Molecular Line Observations of the Ultraluminous Infrared Galaxy IRAS 20551-4250: Different HCN, HCO<SUP>+</SUP>, and HNC Excitation, and Implications for Infrared Radiative Pumping

`2017ApJ...849...29I` | The Astrophysical Journal 2017 | first author: Imanishi, Masatoshi | arXiv: 1708.08073 | DOI: 10.3847/1538-4357/aa7ff9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: How do HCN, HCO+ and HNC excite and differ in abundance in the buried-AGN ULIRG IRAS 20551-4250, and does infrared radiative pumping affect their rotational excitation?  
  > "infrared radiative pumping plays a role in rotational excitation at v=0, at least for HCN and HNC, and (2) HCN abundance is higher than HCO$^{+}$ and HNC." (abstract)
- Target **IRAS 20551-4250**: coordinates continuum peak RA,Dec J2000 = 20 58 26.80, -42 39 00.3  
  > "with infrared luminosity L$_{\rm IR}$ $\sim$ 10$^{12}$L$_{\odot}$ at z=0.043 (Table 1)" (Introduction); "(20 58 26.80, $-$42 39 00.3)" (Table 3); z/distance z = 0.043; 187 Mpc  
  > "with infrared luminosity L$_{\rm IR}$ $\sim$ 10$^{12}$L$_{\odot}$ at z=0.043 (Table 1)" (Introduction); "(20 58 26.80, $-$42 39 00.3)" (Table 3); distance from redshift with H0=71, OmegaM=0.27, OmegaL=0.73 (Komatsu et al. 2009)  
  > "with infrared luminosity L$_{\rm IR}$ $\sim$ 10$^{12}$L$_{\odot}$ at z=0.043 (Table 1)" (Introduction); "(20 58 26.80, $-$42 39 00.3)" (Table 3)

## Data provenance

- ALMA projects: 2013.1.00033.S, 2015.1.00028.S, 2016.1.00051.S
- bands: Bands 3, 6, 7, 9  
  > "our new ALMA observational results in bands 3 (84–116 GHz), 7 (275–373 GHz), and 9 (602–720 GHz)" (Introduction)
- frequencies and spectral setup: 1.875 GHz band mode, 3840 channels; online spectral averaging by 2 or 4 for some observations  
  > "The widest 1.875 GHz band mode and 3840 total channel number were employed for all observations." (2 Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 3248 m depending on band; 34-44 antennas  
  > "2016 October 1   | 41      | 15–3248" (Table 2)
- angular resolution: Beams ~0.16'' (band 6) to ~1.2'' (band 3)  
  > "0.16$\times$0.15 (35$^{\circ}$)" (Table 4)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 15-47 min per execution (H13CN: 36 min Cycle 2, 129 min Cycle 4)  
  > "observed in ALMA Cycle 2 (36 min integration) and Cycle 4 (129 min integration)" (3 Result)
- observing dates: 2014 June to 2016 October  
  > "Band 9 (HCN, HCO$^{+}$, HNC J=8–7)                      | 2016 May 18" (Table 2)
- pi or archival as stated: Authors' own programs (PI M. Imanishi)  
  > "Cycle 2 program 2013.1.00033.S (PI = M. Imanishi)" (2 Observations and Data Analysis)
- Line: HCN J=1-0 (88.632 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: HNC J=8-7 (725.107 GHz)
- Line: CO J=3-2 (345.796 GHz)
- Line: H13CN J=3-2 (259.012 GHz)
- Other facility **Spitzer IRS**: 5-35 micron spectrum used for pumping calculation  
  > "infrared 5–35 $\mu$m spectrum of IRAS 20551$-$4250 obtained with Spitzer IRS" (4.3)
- Other facility **XMM-Newton**: X-ray N_H  
  > "The XMM-Newton 2–10 keV X-ray observation of IRAS 20551$-$4250 shows" (4.4)
- External data: ALMA Cycle 0 HCN J=4-3 flux 9.5 Jy km/s and HCO+, HNC J=4-3 fluxes  
  > "derived in our Cycle 0 observations (9.5$\pm$0.2 Jy km s$^{-1}$) (cite: ima13b)" (3 Result) [from (cite: ima13b)]
- External data: J=3-2 fluxes of HCN, HCO+, HNC and v2=1f lines  
  > "$^{a}$ Taken from (cite: ima16b)." (Table 6) [from (cite: ima16b)]
- External data: X-ray N_H = 7.9e23 cm-2  
  > "N$_{\rm H}$ = 7.9$^{+6.9}_{-1.9}$ $\times$ 10$^{23}$ cm$^{-2}$ (cite: fra03)" (4.4) [from (cite: fra03)]
- External data: Einstein A and energy levels from CDMS  
  > "are from the Cologne Database of Molecular Spectroscopy (CDMS) (cite: mul05)" (Table 7) [from (cite: mul05)]

## Processing

### Calibration

- pipeline or manual: Retrieved ALMA-calibrated data; self-calibration only for CO J=3-2 spectral window  
  > "We retrieved data calibrated by ALMA and used CASA (https://casa.nrao.edu) for further data reduction." (2 Observations and Data Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA-provided calibration (phase calibrators) used  
  > "we adopted results produced with a standard phase calibration using phase calibrators, which were provided by ALMA" (2 Observations and Data Analysis)
- flux calibrator: Titan, Pallas, J2056-4714 (varies)  
  > "Band 9 (HCN, HCO$^{+}$, HNC J=8–7)                      | 2016 May 18      | 42      | 15–640   | 39          | J2253$+$1608 | Pallas" (Table 2)
- flux scale uncertainty: maximum ~10% per observation  
  > "supporting the quoted $<$10% absolute flux calibration uncertainty in individual ALMA observations" (3 Result)
- self calibration: Phase self-cal on CO J=3-2 line in that spectral window  
  > "we employed self-calibration, using the CO J=3–2 emission line itself for phase calibration" (2 Observations and Data Analysis)

### Imaging

- task: CASA clean; imfit for sizes  
  > "The task “clean” was then applied for the molecular line data" (2 Observations and Data Analysis)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1'' for bands 3,7; 0.03'' for bands 9,6  
  > "Pixel scale was set as 0$\ensuremath{''}$1 pixel$^{-1}$ for band 3 and 7 data" (2 Observations and Data Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels, subtracted  
  > "We then subtracted the derived continuum levels, to extract only molecular line data." (2 Observations and Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels binned to 20-40 km/s  
  > "by binning spectral channels to make the velocity resolution 20–40 km s$^{-1}$" (2 Observations and Data Analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data analysis performed same way as earlier ALMA data of this galaxy  
  > "We performed data analysis in the same way as for our previously obtained ALMA data of IRAS 20551$-$4250 (cite: ima13b; ima16b)." (2 Observations and Data Analysis) [from (cite: ima13b; ima16b)]
- Vibrational excitation temperature and abundance-ratio logic follow J=3-2 analysis  
  > "follow the same logical steps as those made by (cite: ima16b) for J=3–2 data" (4.3) [from (cite: ima16b)]
- Cosmology adopted for consistency  
  > "We adopt H$_{0}$ $=$ 71 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}$ = 0.27, and $\Omega_{\rm \Lambda}$ = 0.73 (cite: kom09)" (Introduction) [from (cite: kom09)]

### Not stated but needed to reproduce (our reading)

- clean weighting/robust, deconvolver, threshold and masks
- line-free channel ranges per spectral window
- CASA version
- moment-map integration channel ranges
- spectrum extraction aperture details
- RADEX collisional rate files and grid sampling
- how Gaussian fits were done (fitting code)

## Analysis recipe

1. **Image continuum and lines**: Continuum subtraction from line-free channels, clean to 20-40 km/s channels, extract spectra at continuum peak  
  > "To estimate the continuum flux levels, we removed channels that contained discernible emission lines." (2 Observations and Data Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Checked line-free spectra fluctuate around zero; redefined channels if over-subtracted  
  > "After confirming that the extracted spectra at line-free channels at the continuum peak position show flux density fluctuating around zero level with noise" (2 Observations and Data Analysis)
2. **Measure line fluxes and sizes**: Gaussian fits to spectra, moment 0/1/2 maps, imfit deconvolved sizes  
  > "Peak flux values in the moment 0 maps and emission line fluxes estimated from the best Gaussian fits are summarized in Table 4." (3 Result)
   - software: CASA imfit
   - fitting: Single Gaussian per line  
  > "In Figure 4, although we fit emission lines with single Gaussian component, when we examine the line profiles of the very bright CO J=3–2 and HCO$^{+}$ J=4–3 emission lines in more detail, skew patterns are recognizable." (Discussion, Molecular gas morphology and dynamics)
   - validation: Compared Cycle 0 vs 2 fluxes; rescaled HCN J=4-3 by 1.22  
  > "We thus multiplied the HCN J=4–3 (v=0) flux derived in our Cycle 0 observations (9.5$\pm$0.2 Jy km s$^{-1}$) (cite: ima13b) by a factor of 1.22" (3 Result)
3. **Line opacity from isotopologues**: HCN/H13CN etc. flux ratios vs 12C/13C = 50-100 give flux attenuation and tau  
  > "Adopting the $^{12}$C-to-$^{13}$C abundance ratios in ULIRGs with 50–100" (4.2)
   - assumption: Isotopologue lines optically thin; well-mixed geometry tau/(1-exp(-tau))  
  > "In a geometry where radiation sources and molecular gas are spatially well mixed" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test IR pumping and abundance ratios**: Compare v2=1f excitation temperature to threshold T0/ln(A_vib/A_rot); column density ratios from flux/A_ul  
  > "Infrared radiative pumping is estimated to play a significant role if the following condition is met" (4.3)
   - assumption: J=4 level fraction same across molecules; v2=1f optically thin  
  > "and that v$_{2}$=1f J-transition emission is optically thin (cite: ima16b)" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Collisional excitation modelling**: RADEX LVG grid in n_H2, T_kin to reproduce flux ratios  
  > "we use the RADEX software (cite: van07), which treats the non-LTE analysis" (4.4)
   - software: RADEX
   - parameter: n_H2 10^3-10^8 cm-3; T_kin 10-500 K; dv=300 km/s; N_mol=1e16 cm-2; T_bak 3 K  
  > "We vary the H$_{2}$ number density (n$_{\rm H2}$) between 10$^{3}$ and 10$^{8}$ cm$^{-3}$" (4.4)
   - fitting: Grid comparison, no sampler  
  > "The parameter ranges that can reproduce the observed flux ratios of individual J-transitions are shown as thick lines." (Discussion, Molecular gas properties)
   - validation: tau~3 from RADEX matches isotopologue-derived tau  
  > "roughly comparable to the observationally derived values from isotopologue line data" (4.4)
6. **IR pumping radiative transfer**: MOLPOP LVG with 5-30 micron power-law IR field at 30 and 100 pc, plane-parallel  
  > "the infrared 5–30 $\mu$m radiation source is placed at 30 pc and 100 pc from the molecular gas" (4.6)
   - software: MOLPOP
   - parameter: n_H2=1e5, T_kin=100 K, dv=300 km/s, N=1e16; F_nu=0.0024 lambda^2.0 Jy  
  > "F$_{\nu}$ (Jy) = 0.0024 $\times$ $\lambda$($\mu$m) $^{2.0}$" (4.6)
   - fitting: _not stated_
   - validation: MOLPOP and RADEX agree within 20-30% under LVG  
  > "agree within 20–30% for various H$_{2}$ number density" (4.6)
7. **CO J=3-2 outflow**: Broad Gaussian wing, blue-wing flux doubled, mass from L'CO with alpha=0.8, rate = 3 M V/R  
  > "we adopt the relation of Ṁ$_{\rm outf}$ = 3 $\times$ M$_{\rm outf}$ $\times$ V/R" (4.1)
   - parameter: R~60 pc, V=500 km/s  
  > "R $\sim$ 60 (pc) from the nucleus and outflow velocity with V = 500 km s$^{-1}$" (4.1)
   - assumption: CO J=3-2 optically thick and thermalized; ULIRG-like alpha ~0.8  
  > "Assuming that CO J=3–2 emission is optically thick and thermalized" (4.1)
   - fitting: _not stated_
   - validation: Outflow rate compared with ULIRG relation within factor ~2  
  > "agrees within a factor of $\sim$2 with the relation seen in other ULIRGs" (4.1)

## Software

- **CASA** : data reduction, clean, imfit  
  > "used CASA (https://casa.nrao.edu) for further data reduction" (2 Observations and Data Analysis)
- **RADEX** : non-LTE LVG collisional excitation  
  > "we use the RADEX software (cite: van07)" (4.4)
- **MOLPOP** : IR radiative pumping calculations  
  > "We use MOLPOP (cite: eli06)" (4.6)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO J=3-2 flux | 162 | 3 | Jy km/s | 2 | 12886$\pm$1   / 717$\pm$7     / 221$\pm$3     / 162$\pm$3 |
| HCN v2=1f J=4-3 flux | 0.60 | 0.13 | Jy km/s | 2 | 0.60$\pm$0.13 |
| HCN J=4-3 recalibrated flux | 11.6 | 0.2 | Jy km/s | 2 | adopted the re-calibrated HCN J=4–3 flux with 11.6$\pm$0.2 (Jy km s$^{-1}$) |
| HCN-to-H13CN J=3-2 ratio | 22 | 3 | dimensionless | 3 | HCN-to-H$^{13}$CN J=3–2 flux in (Jy km s$^{-1}$) to be $\sim$22$\pm$3 |
| HCN J=3-2 opacity tau | 2-5 | not stated | dimensionless | 3 | we obtain $\tau$ = 2–5 for HCN J=3–2 |
| T_ex-vib HCN, HNC | ~360 | not stated | K | 4 | are $\sim$360 (K), $<$280 (K), and $\sim$360 (K) for HCN, HCO$^{+}$, and HNC |
| abundance ratio HCN:HCO+:HNC | 1:<0.4:0.1 | not stated | dimensionless | 4 | HCN:HCO^{+}:HNC (abundance) & = & 1:<0.4:0.1 |
| molecular outflow rate | ~150 | not stated | Msun/yr | 7 | we obtain a molecular outflow rate with Ṁ$_{\rm outf}$ $\sim$ 150 (M$_{\odot}$ yr$^{-1}$) |
| outflow mass | 5.8e6 | not stated | Msun | 7 | M$_{\rm outf}$ $\sim$ 5.8 $\times$ 10$^{6}$ M$_{\odot}$ |
| dense molecular mass | ~2e9 | not stated | Msun | 5 | is estimated to be $\sim$2 $\times$ 10$^{9}$ M$_{\odot}$ |

## Qualitative findings

- HNC shows higher high-J/low-J ratios than HCN, hard to explain by collisions alone but reproduced by IR pumping with source at 30-100 pc  
  > "find that our observational results are well explained if the radiation source is located at 30–100 pc from the molecular gas" (abstract)

## Claim tuples

- H: Does IR radiative pumping contribute to v=0 rotational excitation? | E: J=4-3 v2=1f vs v=0 fluxes and Tex-vib criterion | R: T_ex-vib ~360 K for HCN and HNC exceeds threshold ~160-210 K | F: IR pumping matters at least for HCN and HNC | **supported**
- H: Is HCN more abundant than HCO+ and HNC? | E: v2=1f column-density ratios and isotopologue ratios | R: abundance ratio 1:<0.4:0.1; HCN opacity higher | F: HCN abundance higher by a few times | **supported**
- H: Can collisional excitation explain higher HNC excitation? | E: RADEX and MOLPOP models | R: collision alone fails; pumping with source at 30-100 pc reproduces trend | F: IR pumping needed | **partially**
- H: Is there a molecular outflow? | E: broad wing in CO J=3-2 | R: ~150 Msun/yr | F: outflow interpreted | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Multiple J lines and isotopologues needed to separate abundance and excitation  
  > "Multiple rotational J-transition line observations are required to disentangle the abundance and excitation effects" (Introduction)
- Alternative: Extreme compact starburst as alternative to buried AGN as IR source  
  > "However, an extreme starburst with a very compact size remains another possibility" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Flux ratios, emitting volume differences and IR pumping cannot be separated reliably; HNC v2=1f only upper limit; HN13C only ~3 sigma  
  > "separating the contributions from collisional excitation and infrared radiative pumping with sufficient reliability is not easy" (4.4)
- Caveat (inferred, ours): Single-zone assumptions with identical emitting volume across J
- Caveat (inferred, ours): Outflow rate depends on factor-10 choice of wing flux and uncertain geometry
- Caveat (inferred, ours): HNC v2=1f possibly contaminated
- Caveat (inferred, ours): Beams differ between bands and are not corrected

## Reproducibility

- Data public (paper): Projects listed by code and acknowledgement of ADS/JAO.ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00033.S, #2015.1.00028.S, and #2016.1.00051.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: line-free channels
- Missing: CASA version
- Missing: MOLPOP/RADEX input setup details
- Data volume (inferred): ~100-300 GB raw for four bands
- Score (inferred): 3/5, Public data and clear numeric tables, but imaging parameters and fitting details are missing.
- Rediscovery candidate: yes, Public archive data, line fluxes tabulated numerically, though some processing details unstated.

## Links

- Method: (cite: ima16b) (previous J=3-2 analysis with the same methodology)
- Method: (cite: ima13b) (Cycle 0 data and analysis)
- Companion: (cite: ima16b) (J=3-2 ALMA observations of the same galaxy)

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 57,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
