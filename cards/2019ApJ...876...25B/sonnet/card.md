# A Survey of C<SUB>2</SUB>H, HCN, and C<SUP>18</SUP>O in Protoplanetary Disks

`2019ApJ...876...25B` | The Astrophysical Journal 2019 | first author: Bergner, Jennifer B. | arXiv: 1904.09315 | DOI: 10.3847/1538-4357/ab141e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How do C2H, HCN and C18O emission, excitation, optical depth and morphology relate to each other and to disk properties (age, luminosity, mass) across 14 protoplanetary disks?  
  > "To this end, we present a survey of C$^{18}$O, C$_2$H, and HCN in 14 protoplanetary disks." (Introduction)
- Target **14 protoplanetary disks (AS 209, CI Tau, DM Tau, DO Tau, HD 143006, HD 163296, IM Lup, J1604-2130, J1609-1908, J1612-1859, J1614-1906, LkCa 15, MWC 480, V4046 Sgr)**: coordinates _not stated_; z/distance 72.4-166.1 pc (e.g. AS 209 121.0 pc, V4046 Sgr 72.4 pc)  
  > "From *Gaia* Data Release 2" (Table 1); distance from Gaia DR2  
  > "From *Gaia* Data Release 2" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00226.S, 2015.1.00964.S, 2015.1.00671.S, 2016.1.00627.S
- bands: Band 6 (ALMA), C2H/HCN near 262-266 GHz  
  > "We present ALMA Band 6 observations of C$_2$H, HCN, and C$^{18}$O" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-705 m for most ALMA programs (21-558 m for 2013.1.00226.S); SMA 16-226 m  
  > "| V4046 Sgr         | 38       | 15 – 705      | 9               | 2016 06 20 |" (Table 7)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data from various ALMA and SMA programs; C18O described in Huang2017 and J. Pegues (in prep.)  
  > "This project makes use of data from various ALMA and SMA programs, summarized in Table [2](#tab:obsdat)." (2.1 Observational details)
- Line: C2H N=3-2, J=7/2-5/2, F=4-3 and 3-2 (262.00422660 GHz)
- Line: HCN J=3-2 (265.88643390 GHz)
- Line: C18O J=2-1 (not stated)
- Line: H13CN J=3-2 (not stated)
- Other facility **SMA**: HCN J=3-2 for CI Tau, DM Tau, DO Tau, LkCa 15, MWC 480 (project 2017B-S036)  
  > "CI Tau, DM Tau, DO Tau, LkCa 15, and MWC 480 were observed with the SMA and the remaining disks with ALMA." (2.1 Observational details)
- External data: Stellar ages, masses, luminosities of sample  
  > "References: \[1\] (cite: Andrews2009), \[2\] (cite: Guilloteau2014), \[3\] (cite: Andrews2013)" (Table 1) [from Andrews2009; Guilloteau2014; Andrews2013; Vioque2018 and others (Table 1)]
- External data: Disk inclinations and PAs from Keplerian mask fitting to CO  
  > "Derived from Keplerian mask fitting to CO emission (J. Pegues, in preparation)" (Table 1) [from J. Pegues (in preparation)]
- External data: 12C/13C = 68 ± 15 for local ISM  
  > "We adopt a $^{12}$C/$^{13}$C value of 68 $\pm$ 15 appropriate for the local ISM (cite: Milam2005)." (4.2 Isotopologue ratios) [from Milam2005]
- External data: Source-specific disk structure parameters for toy models  
  > "The physical structure for each of these disks has been modeled previously in the literature, and we use these constraints to produce toy models for each disk" (5.3 C2H morphologies in our disk sample) [from Table 6 refs (Andrews2009, Oberg2015, Cleeves2016, Andrews2011, Rosenfeld2013a)]
- Simulation/model as data: Toy disk models with RADMC-3D UV flux and atomic carbon distributions (generic and for 6 source-specific disks)  
  > "We use the radiative transfer code RADMC-3D (cite: Dullemond2012) mctherm task to solve for dust temperatures in the disk." (5 Disk modeling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% calibration uncertainty  
  > "added in quadrature with a 10% calibration uncertainty" (2.2 Data analysis)
- self calibration: Phase self-cal on continuum of individual spws, one or two rounds, applied to line data  
  > "One or two rounds of phase self-calibration were performed depending on the continuum brightness." (2.1 Observational details)

### Imaging

- task: CLEAN in CASA 4.6  
  > "calibrated and continuum-subtracted data were CLEANed to a 3$\sigma$ noise threshold in CASA 4.6" (2.1 Observational details)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 1.0 for line cubes (0.5 for continuum)  
  > "using Briggs weighting with a robust factor of 1.0." (2.1 Observational details)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Hand-drawn masks for strong emission; 5σ continuum contour for weak lines  
  > "CLEAN masks were drawn by hand for strong emission; for weak lines the 5$\sigma$ continuum contour was used as the CLEAN mask." (2.1 Observational details)
- multiscale scales: _not stated_
- continuum subtraction: In the uv plane  
  > "The self-calibration solutions were applied to the spectral line data followed by continuum subtraction in the uv plane." (2.1 Observational details)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channels 0.5 km/s generally; 0.14 km/s for hyperfine fitting cubes  
  > "To produce image cubes for hyperfine fitting a higher spectral resolution of 0.14 km/s was used." (2.1 Observational details)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Keplerian masking method for moment maps, spectra and fluxes  
  > "Our methodology is described in detail in (cite: Bergner2018) and J. Pegues (in preparation)." (2.2 Data analysis) [from Salinas2017; Bergner2018; J. Pegues (in preparation)]
- C18O observational details  
  > "C$^{18}$O observational details are described in (cite: Huang2017) and J. Pegues (in preparation)." (2.1 Observational details) [from Huang2017; J. Pegues (in preparation)]
- Hyperfine fitting procedure  
  > "Our fitting procedure is adapted from (cite: Estalella2017) and (cite: Mangum2015)." (4.1 Hyperfine fitting) [from Estalella2017; Mangum2015]
- Disk structure formalism  
  > "Our physical model is based on the formalism presented in (cite: Andrews2011) and (cite: Rosenfeld2013)" (5.1 Disk model setup) [from Andrews2011; Rosenfeld2013]

### Not stated but needed to reproduce (our reading)

- Exact outer radii used for Keplerian masks per line
- Spectral window/line-free channels used for continuum subtraction
- Self-calibration solution intervals
- emcee settings (walkers, steps, priors)
- CASA version used for calibration
- Details of SMA tapering for H13CN
- UV spectrum scaling and RADMC-3D photon numbers
- Filling factor assumption details for HCN beam dilution

## Analysis recipe

1. **Extract line moment maps, spectra and fluxes**: Keplerian masking of cubes with disk geometry; bootstrapping of uncertainties with 1000 synthetic emission-free cubes  
  > "the same Keplerian mask used to extract line emission is applied to 1000 synthetic image cubes composed of randomly drawn emission-free channels neighboring the target line." (2.2 Data analysis)
   - software: CASA
   - parameter: Detection: flux >3σ and at least 3 channels >3×rms  
  > "at least 3 channels show emission $>3\times$ rms within the Keplerian mask" (3.1 Molecule detections)
   - fitting: _not stated_
   - validation: _not stated_
2. **Hyperfine fitting of C2H and HCN spectra per pixel**: Fit hyperfine model spectra in pixels along the major axis to get tau, Tex, column density  
  > "we extract spectra from each pixel within a slice along the disk major axis the width of the beam major axis." (4.1 Hyperfine fitting)
   - software: emcee
   - parameter: Pixels with peak SNR <6 excluded; widths >2.5 km/s and tau outside 0.15-30 excluded  
  > "we exclude pixels with derived optical depths outside the range of 0.15 to 30" (4.1 Hyperfine fitting)
   - assumption: LTE; filling factor 1; Tbg from local continuum brightness temperature  
  > "We note that this fitting assumes LTE conditions" (4.1 Hyperfine fitting)
   - fitting: emcee affine-invariant MCMC sampling four parameters ΔV_i, V_lsr, A_m*, tau_m*  
  > "We use the affine-invariant MCMC package emcee (cite: Foreman-Mackey2013) to sample posterior distributions of the four fit parameters." (4.1 Hyperfine fitting)
   - validation: Compared HCN hyperfine result in J1604-2130 with isotopologue results  
  > "this agreement points to the robustness of both methods" (4.2 Isotopologue ratios)
3. **HCN optical depth from HCN/H13CN ratio**: Radially binned integrated intensity ratios with 12C/13C=68  
  > "we instead use the ratio of velocity-integrated intensities, making the assumption that HCN and H$^{13}$CN have similar line profiles" (4.2 Isotopologue ratios)
   - parameter: Only pixels with H13CN SNR >2.5; H13CN tapered to SMA beam for LkCa 15 and MWC 480  
  > "including only pixels in which the H$^{13}$CN signal to noise ratio is greater than 2.5" (4.2 Isotopologue ratios)
   - assumption: Co-spatial emission; molecular 12C/13C equals atomic ratio  
  > "assuming co-spatial emission of both molecules and that the molecular $^{12}$C/$^{13}$C ratio is the same as the atomic ratio" (4.2 Isotopologue ratios)
   - fitting: _not stated_
   - validation: _not stated_
4. **Disk-averaged column densities**: Column density from integrated flux for Tex = 10 and 30 K, with and without optical depth correction (tau=2 C2H, 8 HCN), using radius containing 50% of emission  
  > "we calculate column densities for 10K and 30K excitation temperatures" (4.3)
   - assumption: tau = 2 for C2H and 8 for HCN  
  > "corrected for an assumed optical depth of 2 for C$_2$H and 8 for HCN" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Toy disk models of UV flux and atomic carbon to explain C2H morphology**: RADMC-3D dust temperature and mcmono UV field; parametrized gas temperature; atomic C where column < f_pen N_diss; overlap profile integral of n_C × F_UV dz compared with observed radial profiles  
  > "we also plot the vertically-integrated convolution of both factors: $\int n_c \times F_{UV} dz$, hereafter referred to as overlap profiles." (5.3)
   - software: RADMC-3D
   - parameter: N_diss = 1.3e21 H2 cm-2; f_pen = f_dep = 1, 10, 100; G0 = 5; dust-to-gas 0.01  
  > "we evaluate atomic carbon abundances for $f_{\mathrm{pen}}$ = $f_{\mathrm{dep}}$ = 1, 10, and 100" (5.3)
   - fitting: _not stated_
   - validation: Qualitative comparison of overlap profile shapes to observed C2H profiles  
  > "The shapes of the modeled overlap profiles and the observed C$_2$H emission profiles generally match well." (5.3)
6. **Excitation check and flux correlations**: Radex grid for T Tauri and Herbig Ae conditions; Spearman correlation of continuum-normalized fluxes  
  > "We normalize each disk-integrated line flux to the continuum flux in order to cancel out any dependency on the disk angular size." (6.4)
   - software: Radex
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.6 (imaging): Self-calibration, continuum subtraction, CLEAN imaging  
  > "CLEANed to a 3$\sigma$ noise threshold in CASA 4.6" (2.1 Observational details)
- **MIR** : SMA data calibration  
  > "SMA data were calibrated using the `MIR ` software package" (2.1 Observational details)
- **emcee** : MCMC for hyperfine fits  
  > "We use the affine-invariant MCMC package emcee (cite: Foreman-Mackey2013)" (4.1 Hyperfine fitting)
- **RADMC-3D** : Dust temperature (mctherm) and UV field (mcmono) in toy models  
  > "We use the radiative transfer code RADMC-3D (cite: Dullemond2012) mctherm task to solve for dust temperatures in the disk." (5.1)
- **Radex** : Excitation and optical depth grid  
  > "we run Radex models (cite: Vandertak2007) for a grid of densities and temperatures" (6.1)
- **DIANA Opacity-Tool** : Dust opacities  
  > "calculated using the DIANA project Opacity-Tool (cite: Woitke2016)" (5.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C2H optical depth range | ~1-5 | not stated | dimensionless | 2 | C$_2$H is marginally optically thick ($\tau$ $\sim$1–5) |
| HCN optical depth range | ~5-10 (abstract); 3-10 (text) | not stated | dimensionless | 3 | HCN is quite optically thick ($\tau$ $\sim$ 5–10) in the inner 200 AU |
| C2H excitation temperature range | 10-40 | not stated | K | 2 | Excitation temperatures range from 10 – 40K for C$_2$H, and 5 – 20K for HCN. |
| Spearman coefficient C2H vs HCN normalized flux | 0.8 (p=0.003) | not stated | dimensionless | 6 | for C$_2$H with HCN the coefficient is 0.8 with a p-value of 0.003 |
| Disk-averaged N(C2H) at 10 K, tau-corrected, sample range | 5-37 | not stated | 1e12 cm-2 | 4 | range from 5 – 37 $\times$ 10$^{12}$ cm$^{-2}$ for C$_2$H |
| Disk-averaged N(HCN) at 10 K, tau-corrected, sample range | 1-10 | not stated | 1e12 cm-2 | 4 | from 1 – 10 $\times$ 10$^{12}$ cm$^{-2}$ for HCN |
| HCN integrated flux, HD 163296 | 9174 ± 920 | ±920 | mJy km/s | 1 | / HD 163296    / 0.53 $\times$ 0.47 / 84.3          / 2.3               / 6.1                           / 9174 $\pm$ 920        / |

## Qualitative findings

- C2H and HCN fluxes correlate positively; neither correlates with C18O; no age trend  
  > "find a positive correlation between C$_2$H and HCN fluxes, but no relationship between C$_2$H or HCN with C$^{18}$O fluxes." (abstract)
- HD 163296 C2H column density local minima coincide with planet locations of Teague2018  
  > "the locations of local minima in the column density profile coincide nearly exactly with the locations of planets identified by (cite: Teague2018)" (6.3)

## Claim tuples

- H: Are C2H and HCN optically thick and cold in disks? | E: Hyperfine fitting and HCN/H13CN ratios | R: tau ~1-5 (C2H), 3-10 (HCN); Tex 10-40 K and 5-20 K | F: Low temperatures indicate sub-thermal emission from warm atmosphere or beam dilution | **supported**
- H: Does overlap of UV flux and atomic carbon explain C2H morphology diversity? | E: Toy models for 6 disks, overlap profiles vs observed profiles | R: Overlap profile shapes generally match observations, best with high depletion inner and low outer | F: UV-atomic C interplay explains compact/extended, ringed/ringless C2H | **supported**
- H: Do C2H, HCN and C18O share a common oxygen-depletion driver? | E: Spearman correlations of continuum-normalized fluxes and age comparison | R: C2H-HCN correlated; none with C18O; no age trend | F: Common driver for C2H and HCN, but oxygen depletion as driver is questioned | **partially**
- H: Can C2H column density profiles trace planets? | E: Compare HD 163296 C2H column profile to planet locations | R: Minima coincide with planets | F: Possible planet tracer, needs more tests | **partially**

## Reasoning

- Why this data: Disks chosen to span ages, stellar masses and luminosities  
  > "The target disks were chosen to span a range of ages ($<$1 to $\sim$10 Myr)" (2.1 Observational details)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Fluxes may not trace abundances due to optical depth and excitation effects  
  > "an important caveat to this analysis is that fluxes may not be reliable tracers of molecular abundances." (6.4)
- Limitation (authors): SMA HCN data poorly resolved, beam dilution  
  > "HCN observations taken with the SMA are not well resolved" (3.2 Emission morphologies)
- Caveat (inferred, ours): LTE hyperfine fitting with unresolved structure may bias Tex
- Caveat (inferred, ours): Only 14 disks, so correlation significance is limited
- Caveat (inferred, ours): Toy models are not full chemistry and parameters are partly adopted from literature
- Caveat (inferred, ours): Heterogeneous beams between ALMA and SMA complicate flux comparisons

## Reproducibility

- Data public (paper): ALMA project codes listed; public status not stated  
  > "This paper makes use of ALMA data, project codes: 2013.1.00226, 2015.1.00671.S, 2015.1.00964.S, and 2016.1.00627.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Pegues in-prep Keplerian mask details and outer radii
- Missing: emcee priors and settings
- Missing: Spectral setups and line-free channels
- Missing: SMA data may not be public
- Data volume (inferred): ~100-300 GB raw for four ALMA programs (14 disks, multiple EBs)
- Score (inferred): 3/5, Data identified and methods largely described, but key details deferred to in-prep work and fitting priors not stated; SMA data adds complexity.
- Rediscovery candidate: no, Recipe relies on unpublished Keplerian masking details and hyperfine fit settings are incomplete.

## Links

- Method: Salinas2017 (Keplerian masking)
- Method: Estalella2017 (Hyperfine fitting procedure)
- Method: Mangum2015 (Column density and isotopologue ratio formalism)
- Companion: Bergner2018 (Keplerian masking methodology)
- Companion: Huang2017 (C18O observations)
- Companion: J. Pegues (in preparation) (CO/C18O data and Keplerian mask parameters)
- Related: DSHARP

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 51,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
