# ALMA Observations toward the Starburst Dwarf Galaxy NGC 5253. I. Molecular Cloud Properties and Scaling Relations

`2018ApJ...864..120M` | The Astrophysical Journal 2018 | first author: Miura, Rie E. | arXiv: 1808.10089 | DOI: 10.3847/1538-4357/aad69f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the properties of parsec-scale molecular clouds in the starburst dwarf galaxy NGC 5253, how do they compare with scaling relations, and what is the origin of the starburst?  
  > "The main goal of this paper is to study the gas distribution and cloud properties in NGC 5253 with parsec-scale resolution" (Introduction)
- Target **NGC 5253**: coordinates pointings at 13h39m55.87s, -31d38m25.9s and 13h39m56.77s, -31d38m32.4s (ICRS)  
  > "The spatial resolution of the final images is $0.2\ensuremath{''}$ (corresponding to 3.1 pc at a distance of 3.15 Mpc)." (Observations); "We adopt a distance to NGC 5253 of 3.15 Mpc (cite: 2001ApJ...553...47F; 2007AJ....134.1799D) throughout this paper." (Footnote 2); z/distance 3.15 Mpc  
  > "The spatial resolution of the final images is $0.2\ensuremath{''}$ (corresponding to 3.1 pc at a distance of 3.15 Mpc)." (Observations); "We adopt a distance to NGC 5253 of 3.15 Mpc (cite: 2001ApJ...553...47F; 2007AJ....134.1799D) throughout this paper." (Footnote 2); distance from Freedman et al. 2001; Davidge 2007  
  > "The spatial resolution of the final images is $0.2\ensuremath{''}$ (corresponding to 3.1 pc at a distance of 3.15 Mpc)." (Observations); "We adopt a distance to NGC 5253 of 3.15 Mpc (cite: 2001ApJ...553...47F; 2007AJ....134.1799D) throughout this paper." (Footnote 2)

## Data provenance

- ALMA projects: 2013.1.00210.S
- bands: Band 6  
  > "using Band 6 (project code: 2013.1.00210.S; PI: R. E. Miura)" (Observations)
- frequencies and spectral setup: Each spw 1875 MHz bandwidth, 1.129 MHz resolution (1.470 km/s at CO(2-1)); CO(2-1) and H30a in LSB, CS(5-4) in USB  
  > "Each spectral window has a bandwidth of 1875 MHz with a resolution of 1.129 MHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m, ACA 7 m and Total Power  
  > "two ACA 7 m array datasets, three 12 m array data sets and seven Total Power (TP) array datasets" (Observations)
- configurations: C34-2/1 and C34-7/6 (12 m), ACA/7m, ACA/TP  
  > "C34-7/6" (Table 2)
- baselines: longest baseline 349 m (compact 12 m), 1.6 km (extended 12 m)  
  > "compact 12 m array data (C34-2/1, longest baseline of 349 m)" (Observations)
- angular resolution: 0.2 arcsec (3.1 pc)  
  > "The spatial resolution of the final images is $0.2\ensuremath{''}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 1.3 mJy/beam at 1.5 km/s (combined CO cube)  
  > "The combined CO image has a typical noise level of 1.3 mJy beam$^{-1}$ for a velocity resolution of 1.5 km s$^{-1}$ resolution." (Observations)
- time on source: _not stated_
- observing dates: 2014 June to 2015 July  
  > "The ALMA data were obtained during 2014 June and 2015 July" (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: H30alpha recombination line (231.900 GHz)
- Line: CS 5-4 (244.936 GHz)
- Other facility **HST**: Halpha image and star cluster catalogs for cross-matching  
  > "Figure [2](#mom)b indicates the locations of the CO(2–1) distributions over an *HST* H$\alpha$ image." (3 Results)
- Other facility **SEST 15 m**: single-dish CO(1-0) used for R21/10  
  > "Since the half-power beam size (HPBW = 44$\ensuremath{''}$) of the SEST telescope matches the field of view of our observations" (3.2.2)
- External data: Star cluster catalogs (ages, masses) for cloud association  
  > "We also used the catalog in (cite: 2013MNRAS.431.2917D) to cover other star clusters." (4.1) [from (cite: 2015ApJ...811...75C; 2013MNRAS.431.2917D; 2004ApJ...603..503H)]
- External data: CO(1-0) integrated intensity 1.3 K km/s, width 43 km/s  
  > "reported a CO(1–0) integrated intensity of 1.3 K $\mbox{km s$^{-1}$}$ with a velocity width of 43 km s$^{-1}$" (3.2.2) [from (cite: 1989A&A...225....1W)]
- External data: Dust mass 1.2e5 Msun within 120 arcsec  
  > "estimated a dust mass $M_{\rm dust}=1.2^{+1.1}_{-0.6}\times10^5$ $M_{\ensuremath{\odot}}$" (3.2.2) [from (cite: 2013A&A...557A..95R)]
- External data: Gas-to-dust ratio vs metallicity relation  
  > "Using the correlation between gas-to-dust mass ratio (GTD) and metallicity in (cite: 2014A&A...563A..31R)" (3.2.2) [from (cite: 2014A&A...563A..31R)]
- External data: Gas density and temperature for N5253-D and C  
  > "using the molecular gas density and kinetic temperature for N5253-D and N5253-C in (cite: 2015Natur.519..331T)" (3.2.3) [from (cite: 2015Natur.519..331T)]
- External data: Metallicity 12+log(O/H) ~8.18 and 8.30  
  > "$12+\log({\rm O/H})\sim 8.18 \pm 0.03$" (3.2.2) [from (cite: 2007ApJ...656..168L)]
- Simulation/model as data: Comparison with gas-infall simulations of dwarf galaxies, and a simple disk-rotation model (30 km/s) for PVDs  
  > "(cite: 2014MNRAS.442.1830V) showed that external gas infall can trigger a starburst in dwarf galaxies." (4.2)

## Processing

### Calibration

- pipeline or manual: Interferometric data manual; TP with Pipeline  
  > "Data calibration and imaging were manually done using the Common Astronomy Software Applications (cite: 2007ASPC..376..127M) version 4.7.0 for all of the interferometric datasets." (Observations)
- casa version: CASA 4.7.0  
  > "version 4.7.0 for all of the interferometric datasets" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Bandpass calibrator J1427-4206 used as flux calibrator for one ACA execution instead of Ceres  
  > "we used the bandpass calibrator J1427-4206 also as flux calibrator, instead of using Ceres" (Observations)
- flux scale uncertainty: <10%  
  > "All executions have flux calibration uncertainty of less than 10 %." (Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "with 1.5 km s$^{-1}$ resolution using clean task in CASA" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "we used Briggs weighting with the parameter robust=0.5" (Observations)
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "The pixel size of the image was set to about one-fourth of the synthesized beam, 0.05$''$." (Observations)
- image size: _not stated_
- masking: Moment map mask: >4 sigma plus adjacent pixels down to 2 sigma  
  > "The mask only includes pixels whose intensities are over $4\,\sigma$ and adjacent ones down to $2\,\sigma$ level." (3 Results)
- multiscale scales: _not stated_
- continuum subtraction: Done in uv-plane before concatenation, excluding CO, H30a lines and band edges  
  > "We excluded the CO(2–1) and H30$\alpha$ lines, as well as the band edges, for continuum subtraction." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+7m mosaic feathered with TP image  
  > "the mosaicked $^{12}$CO(2–1) interferometric 12 m and 7 m data cube was combined with the TP image using the feathering algorithm" (Observations)
- smoothing: _not stated_
- final beam: 0.2 arcsec  
  > "The spatial resolution of the final images is $0.2\ensuremath{''}$" (Observations)
- final rms: 1.3 mJy/beam at 1.5 km/s  
  > "typical noise level of 1.3 mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Cloud identification algorithm and property definitions follow CPROPS  
  > "For details about the algorithm to identify clouds and the definition of the derived cloud properties, please refer to (cite: 2006PASP..118..590R)." (3.2) [from (cite: 2006PASP..118..590R)]
- Radius conversion factor 1.91 following Solomon et al.  
  > "using the factor $3.4/\pi^{1/2}$, following (cite: 1987ApJ...319..730S)" (3.2) [from (cite: 1987ApJ...319..730S)]
- Pressure plot convention  
  > "calculated following the convention in (cite: 2011MNRAS.416..710F)" (3.2.3) [from (cite: 2011MNRAS.416..710F)]
- Radiation force and gravity estimates  
  > "Following (cite: 2011ApJ...729..133M), we estimate $F_{\rm rad}$ for five clouds" (4.1) [from (cite: 2011ApJ...729..133M)]

### Not stated but needed to reproduce (our reading)

- CPROPS non-default parameter values and exact masking/merge settings
- Line-free channel ranges for continuum subtraction
- Feathering parameters (SD scaling factor, uv-range)
- Clean threshold, masks, niter, image size and mosaic setup
- Calibrator names other than J1427-4206
- Fitting method and uncertainties for the virial-luminosity intercept
- Self-calibration status
- Details of the cluster astrometry correction

## Analysis recipe

1. **Calibrate and image CO(2-1) cube**: Manual CASA calibration of 12m/7m, pipeline TP, clean with Briggs weighting, then feather with TP  
  > "Finally, the mosaicked $^{12}$CO(2–1) interferometric 12 m and 7 m data cube was combined with the TP image using the feathering algorithm." (Observations)
   - software: CASA
   - parameter: robust=0.5, 1.5 km/s channels, 0.05 arcsec pixel  
  > "we used Briggs weighting with the parameter robust=0.5" (Observations)
   - fitting: _not stated_
   - validation: Compared integrated fluxes: TP 96.6 Jy km/s vs combined 92.6 Jy km/s  
  > "The integrated flux of the combined image within a 22$\ensuremath{''}$ radius is $92.6\pm0.1$ Jy km s$^{-1}$." (Observations)
2. **Identify clouds and measure properties**: CPROPS with 5 sigma masking, extrapolation to zero intensity, beam and channel deconvolution; bootstrap uncertainties  
  > "We used default values for most of the parameters in the algorithm, and we masked emission below five $\sigma$." (3.2)
   - software: CPROPS
   - parameter: Bootstrap 10,000 resamplings per cloud  
  > "We repeated this resampling and remeasuring step 10,000 times for each cloud" (3.2)
   - assumption: Spherical virialized clouds with rho ∝ r^-1; Mvir = 189 dV^2 R  
  > "We compute the virial mass using $M_{\rm vir}=189\,\Delta V^2\,R$ \[$M_\odot$\]" (3.2)
   - fitting: _not stated_
   - validation: Excluded clouds near the primary beam edge (60% level), S/N<5, and sizes near resolution  
  > "We also excluded clouds with low signal-to-noise ratio of less than 5" (3.2)
3. **Derive XCO from virial mass vs CO luminosity**: Fit log-log relation with slope fixed to unity; Mgas = 4.3 (XCO/2) L'CO(2-1)/R21  
  > "The intercept of the best fit in the log–log space is $9.2^{+13.2}_{-5.4}$, where the slope has been constrained to be unity" (3.2.2)
   - assumption: R2-1/1-0 = 1 (measured 0.96 from TP vs SEST); factor 1.36 for helium; D=3.15 Mpc  
  > "We use unity for $R_{2-1/1-0}$ throughout this paper" (3.2.2)
   - fitting: _not stated_
   - validation: Compared with metallicity-based XCO and dust-based estimate (XCO = 6-19)  
  > "it yields a range of $X_{\rm CO} = 6-19$" (3.2.2)
4. **Scaling relations, surface density and pressure**: Compare line-width-size, Mgas-R and sigma^2/R vs Sigma with literature CPROPS samples  
  > "Figure [10](#pressure) shows the correlation between the scaling coefficient $\sigma_v^2/R$ and the gas mass surface density" (3.2.3)
   - assumption: XCO = 4.1 for gas mass  
  > "The gas mass was derived assuming $X_{\rm CO}=4.1$." (3.2.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Cross-match clouds with star clusters and compute SFE and forces**: Positional overlap at 3 sigma extent after astrometry correction; SFE = M*/(Mgas+M*); Frad = L/c; Fgrav = G Mgas^2/R^2  
  > "SFE is defined as $M_{\ast}/(M_{\rm gas}+M_{\ast})$" (4.1)
   - assumption: xi = 8e-11 erg; M* = 1.6e4 (Q/1e51) Msun  
  > "$M_{\ast}=1.6\times10^4 (Q/10^{51}\,{\rm s}^{-1})\,\mbox{$M_\odot$}$" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **PVDs, disk-rotation model and gas inflow rates**: PV cuts at several PAs, compared to a disk model with Vrot ~30 km/s; inflow rate = 1.0e-6 Mgas Vgrad/tan i  
  > "$V_{\rm grad,corr}  =V_{\rm grad}/\tan i$, where $i$ is an inclination of the flow along the line of sight, and we assume $i=45$$^\circ$" (4.2)
   - assumption: inclination of flow 45 deg  
  > "we assume $i=45$$^\circ$" (4.2)
   - fitting: 2D Gaussian fit to optical disk; best-fit rotation velocity ~30 km/s  
  > "We then determine the best-fit rotation velocity to be about 30 km s$^{-1}$" (Disk Rotation)
   - validation: _not stated_

## Software

- **CASA** 4.7.0: Calibration and imaging of interferometric data; TP pipeline  
  > "version 4.7.0 for all of the interferometric datasets" (Observations)
- **CPROPS** : Cloud identification and property measurement  
  > "We identified molecular gas clouds using the package CPROPS in IDL" (3.2)
- **analysisUtils getJyPerK** : K to Jy conversion for TP data  
  > "using the command in analysisUtils getJyPerK" (Observations)
- **Astropy** : Used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of molecular clouds | 118 | not stated | clouds | 2 | we have identified a total of 118 molecular clouds |
| Mean cloud radius | 4.3 | not stated | pc | 2 | with average values of 2.2 km s$^{-1}$  and 4.3 pc |
| Mean velocity dispersion | 2.2 | not stated | km/s | 2 | with average values of 2.2 km s$^{-1}$  and 4.3 pc |
| XCO | 4.1e20 | +5.9/-2.4 e20 | cm^-2 (K km/s)^-1 | 3 | $X$ = $4.1^{+5.9}_{-2.4}\times10^{20}$ cm$^{-2}$(K km s$^{-1}$)$^{-1}$ |
| R2-1/1-0 | 0.96 | ~20% | dimensionless | 3 | We then obtain $R_{2-1/1-0}$ of 0.96 with an uncertainty of $\sim20$ % |
| Offset from Galactic line-width-size relation | ~0.2 (average); ~0.5 for central clouds | not stated | dex | 4 | have on average a slight offset of $\sim$0.2 dex from the general line-width - size relation |
| Typical gas surface density | 400 (10^3 near central SB) | not stated | Msun/pc^2 | 4 | aligned along the line of a surface density of $\Sigma_{\rm  H_2}$ = 400 $M_\odot$ pc$^{-2}$ |
| SFE range of associated clouds | 5 to 64 (up to 80 for cloud 8) | not stated | % | 5 | The SFEs we obtain for NGC 5253 range from 5 % to 64 %. |
| Gas inflow rate via dust lane | ~2 | not stated | Msun/yr | 6 | we obtained a gas inflow rate via the dust lane of $\dot{M}_{\rm flow}$ $\simeq$2 $M_\odot$yr$^{-1}$ |
| Clouds associated with star clusters | 6 (with 10 clusters) | not stated | clouds | 5 | we found that six clouds appear spatially associated with 10 star clusters |

## Qualitative findings

- Clouds near the central starburst have larger line widths and higher surface densities but are gravitationally bound.  
  > "These central clouds are gravitationally bound despite the high internal pressure." (abstract)
- Molecular gas kinematics are not dominated by galaxy rotation; consistent with infall.  
  > "We showed that the kinematics of the molecular gas is not likely dominated by the galaxy rotation of NGC 5253" (Summary)

## Claim tuples

- H: Do NGC 5253 clouds follow the Galactic line-width-size relation? | E: CPROPS cloud catalog compared with literature samples | R: ~0.2 dex mean offset, ~0.5 dex for central clouds | F: Starburst environment raises line widths, especially near the center | **supported**
- H: What is XCO in this low-metallicity starburst? | E: Virial mass vs CO luminosity fit | R: XCO = 4.1e20 (+5.9/-2.4) | F: Slightly larger than Galactic; a lower limit if CO-dark H2 exists | **supported**
- H: Do SSC-forming clouds disperse rapidly after cluster formation? | E: Cloud-cluster cross-match, SFE and Frad vs Fgrav | R: Clouds 5 and 8 have high SFE and Frad exceeding Fgrav | F: Parent clouds are dispersed by stellar feedback | **partially**
- H: Was the starburst triggered by gas infall? | E: PVDs, disk model and inflow rates compared with simulations | R: No clear rotation; inflow rate exceeds SFR | F: Gas falling toward the center is compatible with an early infall phase | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: CPROPS used so that properties are comparable with literature samples  
  > "All of the samples used in this comparison are identified using CPROPS" (3.2.1)
- Alternative: Gas infall in dust lane may instead be outflow; net inflow remains positive even then  
  > "Even if these small components were all outflows rather than inflows, a positive net inflow rate is likely preserved" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): R21/10 may vary cloud to cloud; XCO virial value may miss CO-dark gas; distance uncertain 2.8-5.2 Mpc  
  > "with the caveat that the ratio can change considerably from cloud to cloud depending on the environment" (3.2.2)
- Caveat (inferred, ours): XCO fit method and uncertainty derivation are vague
- Caveat (inferred, ours): Cluster-cloud association depends on 0.1-0.3 arcsec astrometry
- Caveat (inferred, ours): SFE and force estimates depend strongly on assumed XCO and cluster ages
- Caveat (inferred, ours): Inflow rates rely on an assumed 45 deg inclination

## Reproducibility

- Data public (paper): Project code and acknowledgment given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00210.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CPROPS parameters beyond defaults
- Missing: Feathering and clean details
- Missing: Line-free channels
- Missing: Calibrator list
- Data volume (inferred): ~100-300 GB raw (12m, 7m, TP in one project); a few GB for the cube
- Score (inferred): 3/5, Data and main steps given, but several processing and fitting details are missing.
- Rediscovery candidate: yes, Project code is stated, the pipeline is mostly described, and results are numeric (118 clouds, XCO).

## Links

- Method: (cite: 2006PASP..118..590R) (CPROPS cloud identification algorithm)
- Companion: (cite: 2017MNRAS.472.1239B) (H30alpha star formation rate from same observations)
- Related: Paper ii and Paper iii (in preparation)

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 64,
  "rate": 0.719
 },
 "evidence_ok": true
}
```
