# ALMA [C I]<SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Observations of NGC 6240: A Puzzling Molecular Outflow, and the Role of Outflows in the Global α <SUB>CO</SUB> Factor of (U)LIRGs

`2018ApJ...863..143C` | The Astrophysical Journal 2018 | first author: Cicone, Claudia | arXiv: 1807.06015 | DOI: 10.3847/1538-4357/aad32a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, milky_way_ism
- Question: What are the physical properties and energetics of the molecular outflow in NGC 6240, and what is the CO-to-H2 conversion factor in the outflow and quiescent gas, as derived by combining [CI](1-0) with CO(1-0)?  
  > "We combine the [CI](1-0) and CO(1-0) data to constrain the CO-to-H$_2$ conversion factor ($\alpha_{\rm CO}$) in the outflow" (abstract)
- Target **NGC 6240**: coordinates _not stated_; z/distance z=0.02448, D_L = 110.3 Mpc  
  > "At the distance of NGC 6240 (redshift $z=0.02448$, luminosity distance $D_L = 110.3$ Mpc), the physical scale is 0.509 kpc arcsec$^{-1}$." (1 Introduction); distance from Planck2016 cosmology (H0=67.8) applied to redshift  
  > "At the distance of NGC 6240 (redshift $z=0.02448$, luminosity distance $D_L = 110.3$ Mpc), the physical scale is 0.509 kpc arcsec$^{-1}$." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00717.S, 2015.1.00370.S
- bands: Band 8 ([CI](1-0)); Band 6 (CO(2-1))  
  > "The Band 8 observations of the [CI](1-0)" (2 Observations); "ALMA Band 6 (programme 2015.1.00370.S, PI: Treister)" (2 Observations)
- frequencies and spectral setup: two spectral windows, total bandwidth 3.675 GHz (2293 km/s) centred at 480.40045 GHz  
  > "yielding a total bandwidth of 3.675 GHz (2293 km s$^{-1}$) centred at $\nu_{obs}^{\rm [CI]}=480.40045$ GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m and ACA 7 m for [CI]; ALMA compact configuration for CO(2-1)  
  > "in May 2016 with the 12 m-diameter antennas of ALMA and in August 2016 with the 7 m-diameter antennas of the Atacama Compact Array (ACA)" (2 Observations)
- configurations: _not stated_
- baselines: ALMA 15-640 m; ACA 9-45 m  
  > "minimum and maximum baselines, $b_{min}=15$ m, $b_{max}=640$ m" (2 Observations); "nine antennas with $b_{min}=9$ m and $b_{max}=45$ m" (2 Observations)
- angular resolution: ALMA [CI] 0.24'' (MRS 2.48''); ACA 2.4'' (MRS 14''); CO(2-1) 1.2'' (MRS 10'')  
  > "yielding an angular resolution (AR) of $0.24\ensuremath{''}$ and a maximum recoverable scale (MRS) of $2.48\ensuremath{''}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: [CI] 1.4 mJy/beam (high-res) and 5 mJy/beam (tapered) per 50 km/s channel at phase centre  
  > "are 1.4 mJy beam$^{-1}$ and 5 mJy beam$^{-1}$ per $dv=50$ km s$^{-1}$spectral channel" (2 Observations)
- time on source: ALMA [CI] 0.12 h; ACA 0.7 h; CO(2-1) one minute  
  > "Only one of the two planned 0.7 h-long scheduling blocks was executed, and the total on-source time was 0.12 h." (2 Observations); "of which 0.7 h on source" (2 Observations)
- observing dates: ALMA May 2016, ACA Aug 2016, CO(2-1) Jan 2016  
  > "which were performed in January 2016 (PWV=1.2 mm)" (2 Observations)
- pi or archival as stated: _not stated_
- Line: [CI] 3P1-3P0 (492.16065 GHz)
- Line: CO 2-1 (not stated)
- Line: CO 1-0 (IRAM PdBI) (not stated)
- Other facility **IRAM PdBI**: CO(1-0) data cube previously published  
  > "we make use of the IRAM PdBI CO(1-0) data previously presented by (cite: Feruglio+13a; Feruglio+13b)" (2 Observations)
- External data: IRAM PdBI CO(1-0) data cube  
  > "IRAM PdBI CO(1-0) data previously presented by (cite: Feruglio+13a; Feruglio+13b)" (2 Observations) [from (cite: Feruglio+13a; Feruglio+13b)]
- External data: L_TIR from IRAS Revised Bright Galaxy Sample  
  > "From the IRAS Revised Bright Galaxy Sample (cite: Sanders+03)" (Table 3) [from (cite: Sanders+03)]
- External data: L_AGN from X-ray data  
  > "Total bolometric luminosity of the dual AGN system estimated from X-ray data by (cite: Puccetti+16)" (Table 3) [from (cite: Puccetti+16)]

## Processing

### Calibration

- pipeline or manual: Data calibrated with the scripts delivered to the PI  
  > "After calibrating separately the ALMA and ACA datasets with the respective scripts delivered to the PI" (2 Observations)
- casa version: CASA v4.6.0  
  > "CASA v4.6.0" (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939 and Titan (flux); J1924-2914 bandpass; J1658+0741, J1651+0129 phase  
  > "J1751+0939 and Titan were used for flux calibration, J1924-2914 for bandpass calibration" (2 Observations)
- flux scale uncertainty: 15% Band 8; 10% for CO(1-0) and CO(2-1)  
  > "which are 10% for the IRAM PdBI CO(1-0) and ALMA CO(2-1) data, and 15% for the ALMA [CI](1-0) line observations" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: clean (uvcontsub for continuum; feather for combination)  
  > "The line visibilities were then deconvolved using `clean` with Briggs weighting and robust parameter equal to 0.5." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The line visibilities were then deconvolved using `clean` with Briggs weighting and robust parameter equal to 0.5." (2 Observations)
- uv taper: outer taper of 1.4'' for low-res cube  
  > "applying a tapering (outer taper of $1.4\ensuremath{''}$)" (2 Observations)
- cell size: 0.01'' (high-res), 0.2'' (low-res)  
  > "set equal to $0.01\ensuremath{''}$ and $0.2\ensuremath{''}$ respectively for the higher and lower resolution data" (2 Observations)
- image size: _not stated_
- masking: interactive cleaning masks  
  > "the cleaning masks were chosen interactively" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, zeroth-order polynomial  
  > "by using a zeroth-order polynomial for the fit" (2 Observations)
- line free channels: [CI]: 478.568-478.988 and 481.517-482.230 GHz; CO(2-1): 224.106-224.279 and 225.780-225.971 GHz  
  > "478.568$<\nu_{obs} [\rm GHz]<$478.988 and 481.517$<\nu_{obs}[\rm GHz]<$482.230" (2 Observations)
- primary beam correction: applied to all datasets  
  > "Primary beam correction was applied to all datasets." (2 Observations)
- array combination: ACA cleaned cube used as modelimage for ALMA clean, then feather of ALMA and ACA images  
  > "we combined the (tapered and non) ALMA image data cubes with the ACA one using the task `feather`." (2 Observations)
- smoothing: spectral binning 9.77 MHz (6 km/s)  
  > "A spectral binning of $\Delta \nu=9.77$ MHz (6 km s$^{-1}$) was applied" (2 Observations)
- final beam: ALMA 0.29''x0.24''; tapered 1.28''x1.02''; ACA 4.55''x2.98''; CO(2-1) 1.54''x0.92''  
  > "$0.29\ensuremath{''}\times0.24\ensuremath{''}$ (PA= 113.18 deg), respectively" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Strategy of using ACA cube as source model to initialise ALMA clean  
  > "following the strategy adopted by (cite: Hacar+18), we used the cleaned ACA data cube corrected for primary beam as a source model" (2 Observations) [from (cite: Hacar+18)]
- CO(1-0) PdBI data reduction  
  > "IRAM PdBI CO(1-0) data previously presented by (cite: Feruglio+13a; Feruglio+13b)" (2 Observations) [from (cite: Feruglio+13a; Feruglio+13b)]
- Line luminosities computed following Solomon+97  
  > "the corresponding line luminosities calculated from the integrated fluxes following (cite: Solomon+97)" (3.2) [from (cite: Solomon+97)]
- Bayesian linear regression  
  > "we conduct a Bayesian linear regression analysis of the relations in Fig. [6](#fig:plots) following (cite: Kelly07)" (3.5) [from (cite: Kelly07)]
- SFR = (1-alpha_AGN) x 1e-10 L_TIR  
  > "$\rm SFR = (1-\alpha_{AGN})\times 10^{-10}$ $\rm L_{TIR}$, following (cite: Sturm+11)" (Table 3) [from (cite: Sturm+11)]

### Not stated but needed to reproduce (our reading)

- CO(2-1) clean parameters beyond robust (masks, image size)
- Image size for [CI] cubes
- Gaussian fitting procedure details (optimizer, initial guesses, how number of components chosen, errors)
- Exact feather parameters (SD scaling, uv overlap)
- Which CASA version used for which dataset, PdBI cube reduction details
- Box positions/centre coordinates for the 13-box grid
- Rest frequencies of CO lines
- Aperture/SNR determination for each box components

## Analysis recipe

1. **Calibrate and image line cubes**: Calibrate with PI scripts, uvcontsub, clean ACA, clean ALMA with ACA model, feather, primary beam correct  
  > "(i) `clean` of ACA visibilities followed by primary beam correction, (ii) `clean` of ALMA visibilities by using the ACA images as a source model followed by primary beam correction, and (iii) `feather` of the ACA and ALMA images." (2 Observations)
   - software: CASA
   - parameter: robust = 0.5; 6 km/s binning; taper 1.4''  
  > "Briggs weighting and robust parameter equal to 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: ALMA and ACA flux scales consistent within 15% in overlapping spatial scales  
  > "found that they are consistent within the Band 8 calibration uncertainty of 15%" (2 Observations)
2. **Map outflow wings and moment maps**: Image blue (-650,-200) and red (250,800) km/s wings of CO(1-0), CO(2-1), [CI]; moment maps of [CI] within -200<v<250 km/s  
  > "integrated respectively within $v\in(-650, -200)$ km s$^{-1}$and $v\in(250, 800)$ km s$^{-1}$" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: Blue and red CO(2-1) wings compared for spatial overlap  
  > "In Figure [2](#fig:CO21wings_overlap) we directly compare the blue and red line wings using the ALMA CO(2-1) data." (3.1)
3. **Fit integrated spectra and derive alpha_CO and r21**: Simultaneous two-Gaussian fit to CO(1-0), CO(2-1), [CI] spectra from 12''x6'' aperture with tied v and sigma; M_mol from [CI] LTE optically thin formula; alpha_CO = M_mol/L'CO(1-0)  
  > "The spectra in Fig. [4](#fig:tot_region_fit) were fitted simultaneously using two Gaussians to account for the narrow core and broad wings" (3.2)
   - parameter: T_ex = 30 K, X_CI = (3.0±1.5)e-5, alpha_[CI] = 9.43  
  > "We adopt $T_{ex} = 30$ K and $X_{\rm CI} = (3.0\pm1.5) \times10^{-5}$" (3.2)
   - assumption: LTE, optically thin [CI], CO and [CI] trace the same gas  
  > "The fundamental underlying assumption is that [CI](1-0) and CO(1-0) trace the same material." (4.1.2)
   - fitting: Simultaneous Gaussian fit; sampler/priors not stated  
  > "For each box, the CO(1-0), CO(2-1), and \[CI\](1-0) spectra are fitted simultaneously with a combination of Gaussian functions tied to have the same line centres and widths for all three transitions." (3.3 Spatially-resolved analysis: the average alpha_CO of the quiescent and outflowing gas)
   - validation: Total CO fluxes consistent with single-dish measurements; alpha_CO consistent with Papadopoulos+14  
  > "the total CO(1-0) and CO(2-1) line fluxes are consistent with previous single-dish measurements" (2 Observations)
4. **Spatially-resolved decomposition into quiescent/outflow**: 13 boxes (nine 2''x2'' and four 3''x3''); up to four Gaussians per box fitted simultaneously; components with -200<v<250 km/s and FWHM<400 km/s are quiescent, others outflow; mean alpha_CO, r21 from components with S/N>=3  
  > "we assume that all components with $-200<v[km~s^{-1}]<250$ *and* FWHM$<400$ km s$^{-1}$trace quiescent gas that is not involved in the outflow." (3.3)
   - fitting: Up to four tied Gaussians per box, minimal number of components  
  > "we minimise the number of spectral components required to reproduce the line profiles, up to a maximum of four Gaussians per box" (3.3)
   - validation: Box-by-box examination in Appendix; removing uncertain boxes C5, C9 leaves results consistent  
  > "without `C5` and `C9`, we derive $M_{out}=1.1\times10^{10}$ M$_{\odot}$ and $dM_{out}/dt = 2350$ $M_{\odot}~yr^{-1}$" (Box spectra and outflow identification)
5. **Compute outflow energetics**: Per box: M_out = L'CO(1-0) x alpha_CO; tau_dyn=R/v_out; Mdot=M_out/tau_dyn; summed over 12 boxes; errors by propagation  
  > "The mass-loss rate $\dot{M}_{out,i}$, equal to $M_{out,i}/\tau_{dyn,i}$. All uncertainties are derived by error propagation." (3.4)
   - parameter: R from RA=16:52:58.900, Dec=02.24.03.950; R=0.5 kpc for C1; sigma_R = 0.3 kpc  
  > "for box `C1`, we conservatively assume that most of the outflow emission comes from a radius of $1\ensuremath{''}$, hence we set $R=0.5$ kpc" (3.4)
   - assumption: Outflow alpha_CO of 2.1±1.2 used where [CI] not detected  
  > "we adopt the galaxy-averaged outflow $\alpha_{\rm CO}$ of $2.1\pm1.2$" (3.4)
   - fitting: _not stated_
   - validation: Optically thin alpha_CO ~0.34 gives lower limits  
  > "Very stringent lower limits on the outflow energetics can be derived by assuming that its CO(1-0) emission is fully optically thin." (3.4)
6. **Trends of alpha_CO and r21 with sigma_v and distance**: Bayesian linear regression  
  > "we conduct a Bayesian linear regression analysis of the relations in Fig. [6](#fig:plots) following (cite: Kelly07)" (3.5)
   - software: linmix_err.pro
   - fitting: linmix_err.pro (Kelly 2007); priors not stated  
  > "We used the IDL routine `linmix_err.pro`" (3.5)
   - validation: _not stated_

## Software

- **CASA** 4.6.0: calibration, uvcontsub, clean, feather  
  > "CASA v4.6.0" (Software)
- **GILDAS** : listed in software  
  > "GILDAS(cite: Pety05)" (Software)
- **linmix_err.pro** : Bayesian linear regression  
  > "We used the IDL routine `linmix_err.pro`" (3.5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean alpha_CO outflow | 2.1 | ±1.2 | Msun (K km/s pc^2)^-1 | 4 | Mean$^\ddag$ outflow comp / $2.1 \pm 1.2$ / $1.4\pm 0.3$ |
| mean alpha_CO systemic | 3.2 | ±1.8 | Msun (K km/s pc^2)^-1 | 4 | Mean$^\ddag$ systemic comp / $3.2\pm 1.8$ / $1.0\pm 0.2$ |
| mean r21 outflow | 1.4 | ±0.3 | dimensionless | 4 | Mean$^\ddag$ outflow comp / $2.1 \pm 1.2$ / $1.4\pm 0.3$ |
| total molecular mass (boxes) | 2.1e10 | ±0.5e10 | Msun | 4 | ${M}_{mol}^{tot} = (2.1\pm 0.5)\times10^{10}~\rm M_{\odot}$ |
| outflow mass | 1.2e10 | ±0.3e10 | Msun | 5 | $M_{out} = (1.2\pm0.3)\times 10^{10}~M_{\odot}$ |
| mass-loss rate | 2500 | ±1200 | Msun/yr | 5 | $dM_{out}/dt = 2500\pm1200$ $M_{\odot}~yr^{-1}$ |
| outflow kinetic power | 0.033 | ±0.019 | L_AGN | 5 | $1/2\dot{M}_{out}v_{out}^2\equiv \sum_i 1/2\dot{M}_{out,i}v_{out,i}^2 = (0.033\pm0.019)~L_{AGN}$ |
| momentum rate | 80 | ±50 | L_AGN/c | 5 | $v \dot{M}_{out} \equiv \sum_i v_i\dot{M}_{out,i} = (80\pm50)~L_{AGN}/c$ |
| depletion time | 8 | ±4 | Myr | 5 | $\tau_{dep} = 8\pm4$ Myr |
| mass loading eta | 50 | ±30 | dimensionless | 5 | $\eta \equiv \dot{M}_{out}$/SFR / $50\pm30$ |
| blue-red [CI] wing peak separation | 0.65 | ±0.02 | arcsec | 2 | The [CI](1-0) red and blue wing peaks are separated by $0.65\ensuremath{''}\pm0.02\ensuremath{''}$. |
| total alpha_CO from integrated spectra | 2.1 | ±1.1 | Msun (K km/s pc^2)^-1 | 3 | Total$^\dag$ / $2.1\pm 1.1$ / $1.22\pm 0.14$ |

## Qualitative findings

- Outflow exceeds 10 kpc, with both east and west sides detected in blue and red components  
  > "The molecular outflow extends by more than 10 kpc along the east-west direction" (Summary and conclusions)
- High-resolution [CI] wing emission peaks between the two AGNs, and the outflow dominates the nuclear velocity field with an hourglass-shaped dispersion structure  
  > "Its emission peaks between the two AGNs, rather than on either of the two." (Summary and conclusions)

## Claim tuples

- H: Does the molecular outflow in NGC 6240 emerge from either AGN? | E: High-resolution [CI](1-0) wing maps and moment maps | R: Blue and red wing peaks offset from AGNs, red wing ~0.8'' from both; no butterfly rotation pattern | F: Outflow launch region lies between the two AGNs and dominates nuclear kinematics | **supported**
- H: What fraction of the gas is in outflow and how powerful is it? | E: Box-by-box simultaneous fits using [CI]-derived alpha_CO | R: M_out=1.2e10 Msun, Mdot=2500 Msun/yr, 60±20% of gas | F: Energetics rule out solely star-formation-driven wind | **supported**
- H: Is alpha_CO lower in outflow than in quiescent gas and below ULIRG value? | E: Compare [CI]-based alpha_CO for components | R: Quiescent 3.2±1.8, outflow 2.1±1.2 (difference only 1.2 sigma) | F: Quiescent alpha_CO at least twice the ULIRG value; outflows may drive down global alpha_CO | **partially**
- H: Does r21 vary with velocity dispersion and between outflow and quiescent gas? | E: Regression of r21 versus sigma_v and distance | R: Weak correlation with sigma_v (rho=0.4±0.2); r21 1.4±0.3 in outflow vs 1.0±0.2 | F: Tentative trend; r21>1 attributed to optical depth effects in non-virial outflow | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: [CI](1-0) is optically thin and expected to coexist with H2, so combining with CO(1-0) yields alpha_CO  
  > "by combining the information from CO(1-0) and [CI](1-0) it is possible to derive an estimate of the $\alpha_{\rm CO}$ value" (1 Introduction)
- Alternative: Rotating disk, nuclear inflows and tidal tails rejected as origin of high-v/sigma emission  
  > "other mechanisms such as rotating disks or gravity-induced dynamical motions, possibly also coexisting in NGC 6240, are unlikely to significantly affect our outflow energetics estimates." (4.1.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Some extended [CI] emission resolved out; flux 34±15% lower than Herschel  
  > "lower by $34\pm15$% than the flux measured by the *Herschel* space observatory" (2 Observations)
- Limitation (authors): Outflow environment unprecedented; [CI]-based assumptions (X_CI, same gas as CO) uncertain  
  > "Further investigation is needed, and our work constitutes just a starting point." (4.1.2)
- Caveat (inferred, ours): Outflow/quiescent split relies on a hard FWHM-velocity cut; central box C1 dominates Mdot and its uncertainty
- Caveat (inferred, ours): Fixed X_CI and T_ex across components may bias alpha_CO
- Caveat (inferred, ours): Only 0.12 h on source; negative artefacts in CO cubes
- Caveat (inferred, ours): Differences in alpha_CO between components only ~1 sigma

## Reproducibility

- Data public (paper): ALMA programmes cited with codes; PdBI data from earlier papers  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00717.S and #2015.1.00370.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Gaussian fitting code and initial conditions
- Missing: PdBI CO(1-0) cube not obviously public
- Missing: Box grid centre and exact box positions
- Missing: Feather and clean image sizes
- Data volume (inferred): ~20-50 GB for ALMA+ACA Band 8 and Band 6 raw data
- Score (inferred): 3/5, ALMA data are public with clear imaging recipe, but the multi-Gaussian fit details are missing and CO(1-0) comes from a prior paper.
- Rediscovery candidate: no, The PdBI CO(1-0) cube is required but not an ALMA archive item, and the fitting procedure is under-specified.

## Links

- Method: (cite: Hacar+18) (ACA cube as source model for ALMA clean)
- Method: (cite: Papadopoulos+04) ([CI] mass formula and X_CI)
- Method: (cite: Kelly07) (Bayesian linear regression)
- Companion: (cite: Feruglio+13a) (Original PdBI CO(1-0) detection of outflow in NGC 6240)
- Companion: (cite: Feruglio+13b) (PdBI CO(1-0) data presentation)
- Related: Treister et al. long baseline ALMA campaign on NGC 6240 (in prep)

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 64,
  "rate": 0.771
 },
 "evidence_ok": true
}
```
