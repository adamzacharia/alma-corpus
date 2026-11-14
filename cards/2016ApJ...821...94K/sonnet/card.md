# The Deuterium Fraction in Massive Starless Cores and Dynamical Implications

`2016ApJ...821...94K` | The Astrophysical Journal 2016 | first author: Kong, Shuo | arXiv: 1509.08684 | DOI: 10.3847/0004-637X/821/2/94

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: What are the deuterium fractions of N2H+ in two massive starless cores, and what collapse rate relative to free-fall do they imply via chemodynamical modeling?  
  > "We then present chemodynamical modeling of the two cores, exploring especially the implications for the collapse rate relative to free-fall, $\alpha_{\rm ff}$." (abstract)
- Target **C1-N**: coordinates RA 18h42m46.89s, Dec -04d04m06.28s  
  > "C1-N | $\rm 18^h42^m46.89s$" (Table 1); "core physical radius at a distance of 5 kpc" (Table 1); z/distance 5 kpc  
  > "C1-N | $\rm 18^h42^m46.89s$" (Table 1); "core physical radius at a distance of 5 kpc" (Table 1); distance from _not stated_
- Target **C1-S**: coordinates RA 18h42m46.50s, Dec -04d04m15.96s  
  > "C1-S | $\rm 18^h42^m46.50s$" (Table 1); z/distance 5 kpc  
  > "C1-S | $\rm 18^h42^m46.50s$" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00236.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA N2D+(3-2) 2''  
  > "*ALMA*$^{2}$ | 231.32183 | 2 | 0.08" (Table 2)
- max recoverable scale: ALMA 9''; CARMA ~50'' (also ~30'' in Observations)  
  > "The angular resolution of *ALMA* observation is 2$''$, and the maximum recoverable scale is 9$''$." (Discussion)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA Cycle 0  
  > "The two cores were first detected by $\rm N_2D^+$(3-2) emission in *ALMA* Cycle 0 observations (T13)." (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: N2D+ 3-2 (231.32183 GHz)
- Line: N2H+ 1-0 (93.17340 GHz)
- Line: N2H+ 4-3 (372.67249 GHz)
- Line: o-H2D+ 1(1,0)-1(1,1) (372.42138 GHz)
- Other facility **CARMA**: N2H+(1-0) maps  
  > "We observed the cores in $\rm N_2H^+$(1-0) at 93 GHz with the *CARMA* 15-element array" (CARMA)
- Other facility **JCMT**: N2H+(4-3) and o-H2D+  
  > "We observed ortho-H$_2$D$^+$ J$_{k^+,k^-}$ = 1$_{1,0}$ $\rightarrow$ 1$_{1,1}$ and $\rm N_2H^+$(4-3) lines" (JCMT)
- Other facility **NRO 45m**: N2D+(1-0) toward C1-S  
  > "We observed $\rm N_2D^+$(1-0) at 77 GHz, with a beam size of $\sim$22$''$." (Nobeyama 45m)
- Other facility **IRAM 30m**: N2D+(2-1), N2H+(3-2) from literature  
  > "The *IRAM 30m* data of $\rm N_2D^+$(2-1) and $\rm N_2H^+$(3-2) presented in this paper are taken from (cite: 2011A&A...529L...7F)." (IRAM 30m)
- Other facility **SMA**: N2H+(3-2) sub-compact data  
  > "SMA observations were made as part of the “SMA survey of high-mass starless cores” in the most compact configuration (sub-compact)" (SMA)
- External data: Core properties (radii, LSR velocities, dispersions, mass surface density, densities, masses) from ALMA N2D+(3-2) and 1.3 mm continuum  
  > "Core properties defined by *ALMA* observations of $\rm N_2D^+$(3-2) by T13" (Table 1) [from (cite: 2013ApJ...779...96T)]
- External data: IRAM 30m N2D+(2-1) and N2H+(3-2) spectra  
  > "The *IRAM 30m* data of $\rm N_2D^+$(2-1) and $\rm N_2H^+$(3-2) presented in this paper are taken from (cite: 2011A&A...529L...7F)." (IRAM 30m) [from (cite: 2011A&A...529L...7F)]
- Simulation/model as data: Astrochemical collapse models from K15 compared with observed abundances  
  > "We run astrochemical models developed by (cite: 2015ApJ...804...98K) to compare with the above observational results." (Chemodynamical Modeling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ALMA ≲20%; CARMA ~15%; JCMT ≲20%; NRO ~10%; IRAM ~20%; SMA ~15%  
  > "we note also that the calibration uncertainties of these data are estimated to be $\lesssim 20\%$" (Observations and Data Reduction); "Overall flux calibration uncertainties are estimate to be $\sim 15\%$." (CARMA)
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
- primary beam correction: efficiency correction, roughly factor of 2.0 for C1-S, not done in T13  
  > "so we applied a primary beam efficiency correction (roughly a factor of 2.0, depending on distance from phase center) to the observed fluxes" (Observations and Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: CARMA 5.5'' x 4.7'' PA 4 deg  
  > "The synthesized beam is 5.5$''$ $\times$ 4.7$''$ with P.A. = 4$^\circ$." (CARMA)
- final rms: CARMA 0.050 Jy/beam at map center  
  > "The final 1$\sigma$ rms at the map center for C1 is 0.050 Jy beam$^{-1}$ (combined CDE-configuration)." (CARMA)

### Inherited from earlier work

- ALMA observations, calibration and imaging  
  > "In this paper we use the *ALMA* data from T13 (see their paper for more details of these observations)." (Observations and Data Reduction) [from (cite: 2013ApJ...779...96T)]
- Astrochemical model and other parameters  
  > "Other parameters of the modeling are the same as those listed in Tables 1 and 2 of K15." (The Fiducial Case) [from (cite: 2015ApJ...804...98K)]
- o-H2D+ column density method  
  > "We follow (cite: 2003A&A...403L..37C) to calculate the column density." (o-H2D+ Abundance) [from (cite: 2003A&A...403L..37C)]
- SMA observing and imaging details  
  > "Further details on the observing and imaging will be reported in a separate publication on the survey (Pillai et al. in prep.)." (SMA) [from Pillai et al. in prep.]

### Not stated but needed to reproduce (our reading)

- ALMA calibration/imaging details (CASA version, weighting, cell size) deferred to T13
- Hyperfine line list and exact fitting code for multi-transition N2D+/N2H+ model
- Aperture definitions and spectral extraction for CARMA/SMA
- SMA data not public (in prep.)
- Full K15 chemical network and its code
- Exact RADEX collision data and inputs for line ratio grid
- CARMA calibration/imaging parameters

## Analysis recipe

1. **Extract core spectra**: Extract ALMA, CARMA, SMA spectra from core apertures; convert single-dish Tmb to flux density  
  > "For the *ALMA*, *CARMA* and *SMA* data, the fluxes are directly extracted from the cores, since they are resolved." (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
   - software: CLASS
   - parameter: S = Tmb 2k Omega_mb / lambda^2  
  > "S_\nu = T_{\rm mb} \frac{2k\Omega_{\rm mb}}{\lambda^2}," (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit N2D+ Tex and column density**: Hyperfine model normalized to ALMA N2D+(3-2); vary Tex to match N2D+(2-1) and (1-0) without exceeding observed  
  > "We vary $T_{\rm ex}~$to reproduce the flux in $\rm N_2D^+$(2-1) and $\rm N_2D^+$(1-0) from the single dish observations as closely as possible" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
   - parameter: Case 2 uses Tex = 7 K  
  > "We will use this value of $T_{\rm ex}~$for the Case 2 models" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
   - assumption: Optically thin hyperfine components with same velocity dispersion  
  > "(1) all hyperfine components are optically thin (this will be checked by radiative transfer modeling, below); (2) all hyperfine components have the same Gaussian profile velocity dispersion" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
   - fitting: Model range allowed by 1 sigma rms noise gives errors  
  > "we consider a range of models about the best-fit value that is allowed by the 1$\sigma$ RMS noise of the spectra" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
   - validation: RADEX optical depth check  
  > "we calculate the optical depth of line emission from the model cores using RADEX" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
3. **Derive N2H+ column and Dfrac**: Assume same Tex as N2D+; scale model to ~50% (25-100%) of CARMA N2H+(1-0) isolated component flux; SMA (3-2) consistency check  
  > "we expect only $\sim 50\%$ of the flux of the observed $\rm N_2H^+$(1-0) spectra to come from the $\rm N_2D^+~$core" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
   - software: RADEX
   - assumption: N2H+ Tex equals N2D+ Tex  
  > "we assume this species has the same value of $T_{\rm ex}~$as $\rm N_2D^+$" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
   - fitting: _not stated_
   - validation: Optical depth correction would reduce Dfrac by ~0.6 (C1-N), 0.8 (C1-S)  
  > "a correction for $\rm N_2H^+$(1-0) optical depth would lead to smaller estimates of $D_{\rm frac}^{\rm N_2H^+}$ by a factor of about 0.6 for C1-N and 0.8 for C1-S" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
4. **o-H2D+ upper limits**: Column density following Caselli 2003, divided by NH from mm continuum; Tex 4-10 K, fiducial 7 K  
  > "Here we adopt a range of $T_{\rm ex}~$from 4 K (allowing for subthermal excitation) to 10 K and set $T_{\rm ex}~$= 7 K as a fiducial value." (o-H2D+ Abundance)
   - assumption: LTE  
  > "(cite: 2003A&A...403L..37C) assumed LTE and adopted $T_{\rm ex}$=7 K" (o-H2D+ Abundance)
   - fitting: _not stated_
   - validation: _not stated_
5. **Chemodynamical model grid and best-fit alpha_ff**: Run K15 models over alpha_ff, zeta, n0/n1, fD0, OPR0; compute mean log-space distance to observed [N2D+], Dfrac, [o-H2D+]  
  > "we calculate its total (summed in quadrature) “distance,” $\Delta$, in the three dimensional log-scale parameter space" (Best Fit alpha_ff)
   - parameter: Fiducial T=10 K, zeta=2.5e-17 s^-1, n_H0=0.1 n_H1, fD0=3, OPR0=1  
  > "a fixed kinetic temperature of 10 K (c.f., the fiducial value of 15 K in K15); a cosmic ray ionization rate of $2.5\times10^{-17}\:{\rm s^{-1}}$" (The Fiducial Case)
   - assumption: All parameters equally weighted; factor-of-two systematic in abundances allowed  
  > "we assume that all parameters are equally important" (Best Fit alpha_ff)
   - fitting: Grid averaging of distances; no sampler  
  > "we average the total distances from each specific model \[$\zeta$, $f_{D,0}$, OPR$^{\rm H_2}_0$\] to have a likelihood parameter $\bar{\Delta}(\alpha_{\rm ff},\delta n_{\rm H})$" (Chemodynamical Modeling – Best Fit $\alpha_{\rm ff}~$)
   - validation: Theory uncertainty ~ factor of two (K15)  
  > "which for the abundances and abundance ratios of interest are at approximately the factor of two level (K15)" (The Fiducial Case)

## Software

- **MIRIAD** : CARMA data reduction  
  > "The data were reduced with the MIRIAD software package." (CARMA)
- **Starlink** : JCMT cube construction  
  > "used the Starlink software package to co-add and re-grid the data to construct the cube" (JCMT)
- **CLASS** : HFS fits and velocity component removal  
  > "using the HFS method in CLASS" (Spectra of N2D+ and N2H+ Emission Towards the Cores)
- **RADEX** : Optical depths and N2H+ (3-2)/(4-3) ratio grid  
  > "we calculate the optical depth of line emission from the model cores using RADEX" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N2D+ excitation temperature C1-N (Case 1) | 3.50 | 0.16 | K | 2 | Case 1 / C1-N / 3.50(0.16) |
| N2D+ excitation temperature C1-S (Case 1) | 4.12 | 0.22 | K | 2 | C1-S / 4.12(0.22) |
| Dfrac C1-N Case 1 | 0.44 (range 0.22-0.88) | 0.10 | dimensionless | 3 | 0.22 – 0.44(0.10) – 0.88 |
| Dfrac C1-S Case 1 | 0.72 (range 0.36-1.4) | 0.15 | dimensionless | 3 | 0.36 – 0.72(0.15) – 1.4 |
| o-H2D+ abundance upper limit band C1-N | 2.4e-11 to 7.3e-10 | not stated | relative to H | 4 | For C1-N, this band is from 2.4$\times$10$^{-11}$ to 7.3$\times$10$^{-10}$. |
| Core age for C1-S (n0/n1=0.1) | 2.4e5/alpha_ff | not stated | yr | 5 | $t_{\rm past,0}$ = (2.4, 10.0)$\times$10$^5$/$\alpha_{\rm ff}~$yr |

## Qualitative findings

- N2H+ emission has a significant, warm, extended envelope component, so core N2H+ is uncertain  
  > "indicate the presence of significant $\rm N_2H^+~$emission from the clump envelope, including a relatively warm component" (Conclusions)

## Claim tuples

- H: Are the cores highly deuterated? | E: Multi-transition fitting of N2D+ and N2H+ spectra | R: Dfrac ~0.2-0.7 | F: Dfrac orders of magnitude above cosmic D/H | **supported**
- H: What collapse rate explains the deuteration? | E: Compare K15 chemodynamical models with observations | R: alpha_ff ≳0.3 disfavored; best fits alpha_ff ≪1 | F: Cores collapse slowly, ≲1/10 free-fall | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dfrac of N2H+ is a chemical clock/best tracer of pre-stellar cores  
  > "Indeed, it is probably the best tracer of pre-stellar cores" (Introduction)
- Alternative: Tex=10 K rejected as inconsistent with NRO N2D+(1-0)  
  > "adopting $T_{\rm ex}$$= 10$ K results in a negligible amount of flux in the $\rm N_2D^+~$(1-0) line" (Excitation Temperatures, Column Densities and Deuterium Fractions of the N2D+ Cores)
- How they decided it was enough: _not stated_
- Limitation (authors): Unknown fraction of N2H+ flux from the cores dominates Dfrac uncertainty  
  > "it is quite uncertain what fraction of $\rm N_2H^+~$line flux is emitted from the $\rm N_2D^+~$cores" (Discussion)
- Caveat (inferred, ours): 50% N2H+ core fraction is an assumption
- Caveat (inferred, ours): Heterogeneous beams and unresolved single-dish data
- Caveat (inferred, ours): Simple unweighted distance metric, no formal likelihood
- Caveat (inferred, ours): Optically thin assumption
- Caveat (inferred, ours): ALMA data reused from T13 with a only an ad hoc primary-beam correction

## Reproducibility

- Data public (paper): ALMA project code cited; other data not stated as public  
  > "This paper makes use of the following *ALMA* data: ADS/JAO.ALMA#2011.0.00236.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: SMA, CARMA, JCMT, NRO data access
- Missing: Exact spectral fitting code
- Missing: K15 model code and settings
- Data volume (inferred): ~10-50 GB for ALMA Cycle 0 data; other data small
- Score (inferred): 3/5, ALMA data public but processing deferred to T13; multi-telescope data and custom models limit reproduction.
- Rediscovery candidate: no, Requires non-public multi-telescope data and custom chemical models.

## Links

- Method: (cite: 2015ApJ...804...98K) (Astrochemical model used)
- Method: (cite: 2003A&A...403L..37C) (o-H2D+ column density method)
- Companion: (cite: 2013ApJ...779...96T) (ALMA observations and core properties)
- Companion: (cite: 2011A&A...529L...7F) (IRAM 30m data)
- Related: SMA survey of high-mass starless cores

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 50,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
