# Filamentary Accretion Flows in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA

`2019ApJ...875...24C` | The Astrophysical Journal 2019 | first author: Chen, Huei-Ru Vivien | arXiv: 1903.04376 | DOI: 10.3847/1538-4357/ab0f3e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Are the filaments in IRDC G14.2 dynamically stable and do they channel accretion flows into the hubs, and how does the virial parameter vary with scale?  
  > "We present results of dynamical stability analyses for filaments in the infrared dark cloud G14.225$-$0.506" (abstract)
- Target **IRDC G14.225-0.506 (G14.2), hub-N and hub-S**: coordinates _not stated_; z/distance 1.98 kpc  
  > "At a distance of $1.98_{-0.12}^{+0.13} \; \mathrm{kpc}$ (cite: Xu:2011da), the infrared dark cloud (IRDC) G14.225$-$0.506 (hereafter G14.2)" (1 Introduction); distance from Xu et al. 2011 (cite: Xu:2011da)  
  > "At a distance of $1.98_{-0.12}^{+0.13} \; \mathrm{kpc}$ (cite: Xu:2011da), the infrared dark cloud (IRDC) G14.225$-$0.506 (hereafter G14.2)" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00312.S, 2015.1.00418.S
- bands: Band 3  
  > "All observations employed the Band 3 receivers with an instrumental spectral resolution of $31 \; \mathrm{kHz}$" (2 Observations)
- frequencies and spectral setup: N2H+ (1-0) at 93.1738 GHz; 0.2 km/s after smoothing  
  > "centered at the rest frequency of $93.1738 \; \mathrm{GHz}$ for the $\mathrm{N_2H^+} \; (1-0)$ transition" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m, ACA 7-m, and total power  
  > "Observations with the total power (TP) array were conducted from 2016 May 14 to May 20 in multiple sessions." (2 Observations)
- configurations: C34-2/1, 37 antennas (12-m); 10 antennas (ACA)  
  > "in the C34-2/1 configuration with a total of 37 antennas" (2 Observations)
- baselines: 2.6 to 107 kλ (0.85'' to 35'')  
  > "ranged from $2.6$ to $107 \; \mathrm{k \lambda}$, equivalent to $0.85\ensuremath{''}$ to $35\ensuremath{''}$" (2 Observations)
- angular resolution: 3.48'' Field-N, 3.15'' Field-S (~0.034 pc)  
  > "The beam size of the final image is $3.48\ensuremath{''}$ for Field-N and $3.15\ensuremath{''}$ for Field-S" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 27 mJy/beam (0.32 K) Field-N, 23 mJy/beam (0.32 K) Field-S per channel  
  > "The rms noise level per channel is $27 \; \mathrm{mJy \, beam^{-1}}$ ($0.32 \; \mathrm{K}$) in Field-N and $23 \; \mathrm{mJy \, beam^{-1}}$ ($0.32 \; \mathrm{K}$) in Field-S." (2 Observations)
- time on source: 12-m total duration ~1.7 hr including calibration; 57 pointings Field-N, 67 Field-S  
  > "The duration of all the 12-m array observation, including time for calibration, is roughly 1.7 hr." (2 Observations)
- observing dates: 12-m 2015 Apr 25; ACA 2015 Apr 30, May 4, 2016 May 15, Jun 4; TP 2016 May 14-20  
  > "on 2015 April 25 in the C34-2/1 configuration" (2 Observations)
- pi or archival as stated: _not stated_
- Line: N2H+ J=1-0 (seven hyperfine components) (93.1738 GHz)
- External data: Dust temperature and H2 column density maps from iterative SED fits (0.1 pc resolution)  
  > "whose value is adopted from the dust temperature, $T_d$, obtained by the iterative spectral energy distribution (SED) analysis of dust continuum emission (cite: Lin:2017bv)" (4.3 Spectral Fits) [from (cite: Lin:2017bv; Lin:2016fe)]
- External data: NH3 filament data, 870 um clump and 3 mm core properties for comparison  
  > "hubs and dense clumps identified in the $870 \; \mu\mathrm{m}$ continuum emission (cite: Ohashi:2016iz)" (5.3 Comparison) [from (cite: Busquet:2013ko; Ohashi:2016iz)]
- External data: Magnetic field strength 0.32-0.55 mG  
  > "The magnetic field strength in IRDC G14.2 reported by (cite: Santos:2016cg) is in the range $0.32$–$0.55 \; \mathrm{mG}$" (5.5 Dynamical Stability) [from (cite: Santos:2016cg)]

## Processing

### Calibration

- pipeline or manual: standard CASA procedures; data delivered from the East Asian ARC  
  > "using the standard procedures, and the data were delivered from the East Asian ALMA Regional Center" (2 Observations)
- casa version: CASA 4.3.1, 4.5.3, 4.7.0  
  > "The reduction and calibration of the data were done with CASA version 4.3.1, 4.5.3, and 4.7.0" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Ceres; bandpass/phase J1733-1304, J1924-2914  
  > "Flux calibration was performed using Neptune and Ceres." (2 Observations)
- flux scale uncertainty: 5% in Band 3  
  > "The uncertainty of absolute flux calibration is 5% in Band 3" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: MIRIAD imaging after FITS export  
  > "exported in FITS format to the MIRIAD package for imaging reconstruction with the robust parameter equal to zero" (2 Observations)
- deconvolver: maximum entropy, TP cubes as default images  
  > "The TP image cubes were used as default images when performing the maximum entropy deconvolution." (2 Observations)
- weighting robust: robust = 0  
  > "imaging reconstruction with the robust parameter equal to zero" (2 Observations)
- uv taper: _not stated_
- cell size: 0.3''  
  > "the pixel size is $0.3\ensuremath{''}$" (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m + ACA + TP combined  
  > "using the ALMA 12-m Array, the ACA, and the TP array" (6 Conclusion)
- smoothing: 0.1 to 0.2 km/s spectral smoothing  
  > "visibility data were smoothed from an instrumental spectral resolution of $0.1 \; \mathrm{km \, s^{-1}}$ to $0.2 \; \mathrm{km \, s^{-1}}$ before making images" (2 Observations)
- final beam: circular 3.48'' (N), 3.15'' (S)  
  > "restored with a circular beam size equal to the solid angle of the Gaussian synthesized beam" (2 Observations)
- final rms: 27 and 23 mJy/beam per channel  
  > "The rms noise level per channel is $27 \; \mathrm{mJy \, beam^{-1}}$ ($0.32 \; \mathrm{K}$) in Field-N" (2 Observations)

### Inherited from earlier work

- Fitting algorithm built on earlier hyperfine fitting work  
  > "The fitting procedure in the current work uses an improved algorithm to handle a large amount of spectral data based on our previous studies (cite: Chen:2010hn; Chen:2011bo)." (Appendix) [from (cite: Chen:2010hn; Chen:2011bo)]
- Accretion rate geometry/inclination method  
  > "Following the method used by (cite: Kirk:2013gq), one may express the observed quantities" (5.1 Mass Accretion Rates) [from (cite: Kirk:2013gq)]
- Dust opacity and gas-to-dust uncertainties  
  > "Following the discussion by (cite: Sanhueza:2017bd), we adopt uncertainties of 28% and 23% for the dust opacity and gas-to dust mass ratio." (5.4 Uncertainties) [from (cite: Sanhueza:2017bd)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / baseline handling for N2H+ cubes
- MIRIAD task parameters (invert/mosaic, maxen settings, iterations)
- FilFinder remaining parameters (e.g. smoothing size, adapt_thresh)
- RadFil fit settings beyond samp_int and background range
- Dust opacity and gas-to-dust ratio values used for the column density maps
- Excitation temperature map values used per pixel (need Lin et al. 2017 data)
- Bootstrap sampling details beyond 50,000 sets

## Analysis recipe

1. **Image N2H+ cubes**: MIRIAD maximum entropy mosaic imaging of 12-m+ACA with TP as default image, robust 0, 0.2 km/s channels, circular beam  
  > "The TP image cubes were used as default images when performing the maximum entropy deconvolution." (2 Observations)
   - software: CASA, MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify filaments**: FilFinder skeletons on integrated maps of the isolated hyperfine component, pruning branches <1 pc, spines terminated at hubs  
  > "The mask is prepared with a flatten percentage of 90% and a minimum intensity to be included (glob_thresh) at 60% for field-N and 40% for field-S." (4.1 Filament Identification)
   - software: FilFinder
   - parameter: aspect ratio > 5; glob_thresh 60% (N), 40% (S)  
  > "An object also need to have an aspect ratio larger than 5 to be considered as a branch or filament." (4.1 Filament Identification)
   - fitting: _not stated_
   - validation: parameter robustness checked qualitatively  
  > "The spine identification does not vary drastically unless the parameters are deviated far from the default values." (4.1 Filament Identification)
3. **Measure filament widths**: RadFil radial profiles fitted with Plummer-like function, background removed by first-order polynomial  
  > "Cuts are taken every $12$ pixels (samp_int=12), which are roughly equal to the beam size." (4.2 Filament Width)
   - software: RadFil
   - parameter: background fit region 0.2-0.8 pc from spine; 0.1 pc peak-search mask  
  > "The background model is obtained with data in regions between $0.2 - 0.8 \; \mathrm{pc}$ from the spine." (4.2 Filament Width)
   - assumption: cylindrical filament, w = 2 R_flat  
  > "The filament width is given by $w = 2 R_\mathrm{flat}$." (4.2 Filament Width)
   - fitting: Plummer profile fit to mean profile  
  > "RadFil fits a given profile function, such as the Plummer function, on the average profile of the entire ensemble of cuts." (4.2 Filament Width)
   - validation: _not stated_
4. **Fit hyperfine spectra pixel by pixel**: Multi-component 7-hyperfine radiative transfer model with Levenberg-Marquardt minimisation of reduced chi2, up to 4 components, Tex=Td  
  > "minimization of the reduced $\chi^2$ value, $\overline{\chi^2}$, using the Levenberg-Marquardt method" (Appendix)
   - parameter: components rejected if peak <3.5 sigma; separation >2 channels (0.4 km/s)  
  > "Further rejection of velocity components with spectral peaks below $3.5\sigma$ is applied to avoid poorly constrained fits" (4.3 Spectral Fits)
   - assumption: single excitation temperature equal to dust temperature; single beam filling factor  
  > "All the velocity components are assumed to be in full thermalization for the $\mathrm{N_2H^+} \; (1-0)$ line at a single excitation temperature" (4.3 Spectral Fits)
   - fitting: Levenberg-Marquardt chi2 minimization; best of up to 56 initial-guess combinations from cross-correlation  
  > "the maximum number of all the available combinations for an initial set of six will be 56" (Appendix)
   - validation: reduced chi2 maps; hub fits excluded  
  > "Note that we do not use spectral fits in hub-N nor hub-S for later analysis." (4.3 Spectral Fits)
5. **Assign velocity components to filaments**: Friends-of-friends in PPV space seeded from spine pixels; linking length half beam and 0.4 km/s  
  > "their angular separation is within half a beam and their velocity difference is less than two channels, i.e. $0.4 \; \mathrm{km \, s^{-1}}$" (4.4 Velocity Components)
   - fitting: _not stated_
   - validation: compared with averaged position-velocity plots of isolated component  
  > "In general, the derived velocity distribution agrees very well with the observed velocity pattern." (4.4 Velocity Components)
6. **Velocity gradients and accretion rates**: PCA of PPV distribution gives gradient; Mdot = M grad_v tan i with i=45 deg; mass from Lin et al. column density within 0.1 pc of spine  
  > "Assuming a moderate inclination angle of $i = 45^\circ$, we list in Table [\[tab:flm\]](#tab:flm) the mass accretion rate" (5.1 Mass Accretion Rates)
   - assumption: cylindrical geometry, i = 45 deg  
  > "Assuming a moderate inclination angle of $i = 45^\circ$, we list in Table [\[tab:flm\]](#tab:flm) the mass accretion rate" (5.1 Mass Accretion Rates)
   - fitting: PCA first component  
  > "PCA allows a fit for general orientation and velocity gradient with the full ensemble of PPV components." (4.5 Inflow Motion along Filaments)
   - validation: first PC significance >96.6%  
  > "The first principal component has significance higher than 96.6% in all filaments." (4.6 Inflow Motion)
7. **Virial parameters and scale trends**: alpha_vir = M_l,vir/(M_l/N_sub) with effective sound speed; bootstrap linear regression of 50,000 synthetic sets vs scale and sigma_nt/cs  
  > "we perform linear regression for a bootstrapping statistical sample of 50,000 synthetic data sets" (5.5 Dynamical Stability)
   - assumption: mu = 2.33; uniform inclination distribution with max length 5-8 pc  
  > "where $\mu = 2.33$ is the mean molecular weight" (4.7 Transonic Turbulent Motions)
   - fitting: linear regression on bootstrap samples, normal uncertainties  
  > "we perform linear regression for a bootstrapping statistical sample of 50,000 synthetic data sets." (5.5 Dynamical Stability and Virial Parameters)
   - validation: slope varied with l_max  
  > "We vary $\ell_\mathrm{max}$ to examine how the slope and intercept depend on $\ell_\mathrm{max}$." (5.5 Dynamical Stability and Virial Parameters)

## Software

- **CASA** 4.3.1, 4.5.3, 4.7.0: calibration  
  > "The reduction and calibration of the data were done with CASA version 4.3.1, 4.5.3, and 4.7.0" (2 Observations)
- **MIRIAD** : imaging reconstruction  
  > "exported in FITS format to the MIRIAD package for imaging reconstruction" (2 Observations)
- **FilFinder** : filament spine identification  
  > "We use the publicly available filament finding package FilFinder" (4.1 Filament Identification)
- **RadFil** : filament radial profiles and widths  
  > "we apply the publicly available filament profile builder package RadFil" (4.2 Filament Width)
- **TOPCAT** : listed in software section  
  > "TOPCAT (cite: Taylor:2005wq)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Filament length range | 1.02-3.22 (mean 2.0) | not stated | pc | 2 | is in the range of $1.02$ to $3.22 \; \mathrm{pc}$ with a mean value of $2.0 \; \mathrm{pc}$ |
| Filament width | 0.05-0.09 (mean 0.07) | not stated | pc | 3 | The filament widths are in the range of $0.05$ to $0.09 \; \mathrm{pc}$ with a mean value of $0.07 \; \mathrm{pc}$ |
| Velocity gradient | 0.3-0.6 (mean 0.5) | not stated | km/s/pc | 6 | The derived velocity gradient is in the range of $0.3 - 0.6 \; \mathrm{km \, s^{-1} \, pc^{-1}}$ with a mean value of $0.5 |
| Linear mass | 75-116 (mean 92) | ~45% | Msun/pc | 6 | The linear mass of our observed filaments is in the range of $75$ to $116 |
| Mass accretion rate (i=45 deg) | (0.2-1.3)e-4 | not stated | Msun/yr | 6 | mass accretion rates along filaments are in the range of $(0.2 - 1.3) \times 10^{-4} \; M_\odot \, \mathrm{yr^{-1}}$ |
| Virial parameter of N2H+ filaments | 0.6-1.8 (mean 1.2) | not stated | dimensionless | 7 | The value of $\alpha_\mathrm{vir}$ in the $\mathrm{N_2H^+}$ filaments is in the range of $0.6 -1.8$ with a mean value of $1.2$ |
| alpha_vir vs scale slope | 0.23 | 0.06 | dimensionless | 7 | $\log \alpha_\mathrm{vir} = (0.23 \pm 0.06) \log s + (0.03 \pm 0.07)$ |
| Fraction subsonic non-thermal motions | 60% | not stated | percent | 4 | 60% have subsonic non-thermal motions and 96% include subsonic and transonic motions altogether |
| Free-fall time hub-N / hub-S | 8.4e4 / 1.1e5 | not stated | yr | 6 | $t_\mathrm{ff} = 8.4 \times 10^4 \; \mathrm{yr}$ in hub-N and $1.1 \times 10^5 \; \mathrm{yr}$ in hub-S |

## Qualitative findings

- About 1/3 of spectra show multiple velocity components.  
  > "In total, $\sim 1/3$ of the spectra display multiple velocity components." (4.3 Spectral Fits)

## Claim tuples

- H: Do filaments feed the hubs fast enough to affect hub dynamics? | E: PCA velocity gradients and cylindrical accretion estimate | R: Mdot up to ~1e-4 Msun/yr, 16-20% of hub mass per free-fall time | F: Filamentary accretion can alter hub dynamics within one free-fall time | **supported**
- H: Are N2H+ filaments in virial equilibrium? | E: Virial parameter with effective sound speed and substructure correction | R: alpha_vir 0.6-1.8, mean 1.2 | F: Marginally virialized, in equilibrium | **supported**
- H: Does alpha_vir decrease toward smaller scales? | E: Compare NH3 filaments, N2H+ filaments, clumps, cores with bootstrap regression | R: slope 0.23±0.06 | F: Gravity increasingly important at small scales, consistent with global hierarchical collapse | **supported**

## Reasoning

- Why this data: N2H+ has higher critical density and lower upper-level energy than NH3, tracing quiescent dense gas  
  > "To trace quiescent gas kinematics in G14.2, we choose to map emission of the molecular ion, $\mathrm{N_2H^+}$" (1 Introduction)
- Why this method: _not stated_
- Alternative: Filament expansion rather than inflow judged less favorable  
  > "Hence the expansion scenario seems less favorable in IRDC G14.2." (5.6 Alternative Dynamical Interpretation)
- How they decided it was enough: _not stated_
- Limitation (authors): Unknown inclination biases filament identification and accretion rates  
  > "The unknown inclination introduces an unavoidable bias in identifying a filament and a fairly large uncertainty in the estimates of the accretion rate along the axis." (5.6 Alternative Dynamical Interpretation)
- Limitation (authors): Single temperature and filling factor assumptions fail in hubs  
  > "Our spectral model assumes single temperature for all velocity components along line of sight, which is not valid in regions with significant internal heating" (4.3 Spectral Fits)
- Caveat (inferred, ours): Accretion rates depend on assumed i=45 deg
- Caveat (inferred, ours): Virial parameter excludes magnetic fields and relative substructure motions
- Caveat (inferred, ours): Only five filaments; regression mixes heterogeneous tracers

## Reproducibility

- Data public (paper): ALMA project codes given; public availability not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00312.S, #2015.1.00418.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: Own spectral fitting code not released; FilFinder and RadFil are public  
  > "FilFinder available online at [ https://github.com/e-koch/FilFinder]" (4.1 Filament Identification)
- Missing: Custom hyperfine fitting code
- Missing: Dust temperature and column density maps from Lin et al.
- Missing: MIRIAD maxen parameters
- Data volume (inferred): ~50-150 GB (12-m + ACA mosaics, two fields, plus TP)
- Score (inferred): 3/5, Data identified, many parameters given, but custom fitting code and external maps are needed.
- Rediscovery candidate: no, Requires unreleased fitting code and external temperature/column density maps.

## Links

- Method: Koch & Rosolowsky 2015 (cite: Koch:2015dc) (FilFinder)
- Method: Zucker & Chen 2018 (cite: Zucker:2018eg) (RadFil)
- Method: Chen et al. 2010, 2011 (cite: Chen:2010hn; Chen:2011bo) (hyperfine fitting basis)
- Companion: Ohashi et al. 2016 (cite: Ohashi:2016iz) (3 mm continuum cores in same fields)
- Companion: Busquet et al. 2013 (cite: Busquet:2013ko) (NH3 filaments)
- Related: M17 SWex
- Related: Herschel filament surveys

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 65,
  "rate": 0.747
 },
 "evidence_ok": true
}
```
