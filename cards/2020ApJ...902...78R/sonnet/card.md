# The Complete Redshift Distribution of Dusty Star-forming Galaxies from the SPT-SZ Survey

`2020ApJ...902...78R` | The Astrophysical Journal 2020 | first author: Reuter, C. | arXiv: 2006.14060 | DOI: 10.3847/1538-4357/abb599

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What is the complete spectroscopic redshift distribution and the intrinsic properties of the SPT-selected lensed DSFGs, and how do they compare with unlensed DSFGs and galaxy formation models?  
  > "In this paper, we finalize the SPT-selected ALMA redshift survey, which started in (cite: weiss13) and continued in (cite: strandet16)." (1 Introduction)
- Target **81 SPT-selected lensed DSFGs (SPT-SZ 2500 deg^2)**: coordinates Table 2 lists positions from ALMA 3 mm continuum (e.g. SPT0002-52: 0:02:23.76 -52:31:52.7)  
  > "| SPT0002-52 | SPT-S J000223-5232.1  | 0:02:23.76  | -52:31:52.7 |" (Table 2); "The SPT-selected DSFG catalog is a flux-limited sample comprised of 81 bright sources, selected at $1.4\, \mathrm{mm}$ from the $2500\, \mathrm{deg^2}$ of the SPT-SZ survey" (2.1 Sample selection); z/distance 1.9<z<6.9, median 3.9±0.2  
  > "| SPT0002-52 | SPT-S J000223-5232.1  | 0:02:23.76  | -52:31:52.7 |" (Table 2); "The SPT-selected DSFG catalog is a flux-limited sample comprised of 81 bright sources, selected at $1.4\, \mathrm{mm}$ from the $2500\, \mathrm{deg^2}$ of the SPT-SZ survey" (2.1 Sample selection); distance from spectroscopic redshifts from CO/[CI] lines  
  > "| SPT0002-52 | SPT-S J000223-5232.1  | 0:02:23.76  | -52:31:52.7 |" (Table 2); "The SPT-selected DSFG catalog is a flux-limited sample comprised of 81 bright sources, selected at $1.4\, \mathrm{mm}$ from the $2500\, \mathrm{deg^2}$ of the SPT-SZ survey" (2.1 Sample selection)

## Data provenance

- ALMA projects: 2011.0.00957.S, 2012.1.00844.S, 2015.1.00504.S, 2016.1.00672.S, 2018.1.01254.S, 2019.1.00486.S, 2017.1.01340.S
- bands: Band 3 (84-116 GHz) blind scans; Bands 4 and 5 for targeted confirmation  
  > "The blind spectroscopic search was conducted using ALMA’s Band 3 receiver, which operates between $84 - 116\, \mathrm{GHz}$." (2.2.1 ALMA 3 mm blind scans); "using ALMA Bands 4 and 5 ($163$$-$$211\, \mathrm{GHz}$)" (Appendix: ALMA Targeted Line Scans)
- frequencies and spectral setup: Five tunings cover Band 3; 7.5 GHz total bandwidth over two sidebands  
  > "The ALMA Band 3 $3\, \mathrm{mm}$ atmospheric transmission window can be covered in five tunings" (2.2.1 ALMA 3 mm blind scans)
- continuum bandwidth: _not stated_
- arrays: 34-49 antennas depending on cycle  
  > "During Cycle 3, between 34 and 41 antennas were employed" (2.2.1 ALMA 3 mm blind scans)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Cycle 3 beams 3.9"x4.7" to 3.3"x4.1"; Cycle 4 4.1"x5.0" to 3.5"x4.3"; Cycle 7 2.0-4.0"  
  > "resulted in typical synthesized beams of $3.9\ensuremath{''}$$\times$$4.7\ensuremath{''}$ to $3.3\ensuremath{''}$$\times$$4.1\ensuremath{''}$ (FWHM)" (2.2.1 ALMA 3 mm blind scans)
- max recoverable scale: _not stated_
- sensitivity: Noise per channel 0.5-0.8 (Cy3), 0.4-0.6 (Cy4), 0.2-0.3 mJy/beam (Cy7); continuum 50, 40, 10-70 uJy/beam  
  > "Observations from Cycle 3 had a typical noise per channel of $0.5-0.8\, \mathrm{mJy/beam}$ over the $37\, \mathrm{GHz}$ bandwidth." (2.2.1 ALMA 3 mm blind scans)
- time on source: ~6 min (Cy3), 12-15 min (Cy4), 45-91 min (Cy7) per source  
  > "Each target was observed for roughly 6 minutes on-source." (2.2.1 ALMA 3 mm blind scans)
- observing dates: Cy3 Dec 2015-Aug 2016; Cy4 Nov 2016-May 2017; Cy7 Nov 2019-Jan 2020  
  > "The Cycle 4 observations were conducted from November 2016 - May 2017" (2.2.1 ALMA 3 mm blind scans)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 through 8-7 (mostly 3-2 to 7-6) (spaced every 115 GHz)
- Line: [CI] 1-0 (not stated)
- Other facility **SPT**: 1.4 and 2.0 mm flux densities, source selection  
  > "The SPT $1.4\, \mathrm{mm}$ and $2.0\, \mathrm{mm}$ flux densities were extracted from CMB maps acquired from the first survey, SPT-SZ." (2.3.1 SPT)
- Other facility **APEX/LABOCA**: 870 um photometry  
  > "The sources were observed at $870\, \mathrm{\mu m}$ with LABOCA at APEX and the flux densities were extracted." (2.3.1 APEX)
- Other facility **Herschel SPIRE/PACS**: 100-500 um photometry  
  > "Additional *Herschel*/PACS $160\, \mathrm{\mu m}$ and $100\, \mathrm{\mu m}$ observations were obtained for a subset of 65 sources." (2.3.1 Photometry)
- Other facility **APEX/FLASH**: [CII] redshift confirmations  
  > "The \[CII\] emission line survey was conducted using the First Light APEX Submillimetre Heterodyne receiver" (2.2.2)
- Other facility **ATCA**: CO(1-0)/CO(2-1) follow-up  
  > "The Australia Telescope Compact Array (ATCA) was used to conduct a survey of CO(1-0) and CO(2-1)" (2.2.2)
- External data: Lens models and magnifications for 39 sources (median mu=5.5 adopted for others)  
  > "the magnifications presented in (cite: spilker16) are used when available." (2.3.3) [from (cite: spilker16)]
- External data: ALESS comparison sample properties (MAGPHYS values)  
  > "The `MAGPHYS` SED modeling code was used to obtain photometric properties (cite: dacunha15)." (3.2.2) [from (cite: dacunha15)]
- External data: Cycle 0 and 1 redshifts and spectra  
  > "The Cycle 0 data was published in (cite: weiss13) and Cycle 1 data was published in (cite: strandet16)." (Appendix Table 4) [from (cite: weiss13); (cite: strandet16)]
- External data: Deboosted SPT 1.4 and 2 mm flux densities  
  > "the $2\, \mathrm{mm}$ and $1.4\, \mathrm{mm}$ SPT flux densities are deboosted and were presented in (cite: everett20)." (Table 3 notes) [from (cite: everett20)]
- Simulation/model as data: Béthermin et al. 2015 empirical model mock catalogs compared via KS test; Hayward13, Béthermin17, Shark (Lagos), Lovell20 predictions compared to number densities  
  > "In this section, we compare the model of (cite: bethermin15b) with our observed distribution." (4.1.2 Selection Effects)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Cy3: Uranus, Neptune, Ganymede, J0519-4546, J0538-4405  
  > "Flux calibration was performed on Uranus, Neptune, Ganymede, J0519-4546, and J0538-4405." (2.2.1)
- flux scale uncertainty: 10% for ALMA absolute calibration  
  > "$7\%$ for SPT, and $10\%$ for ALMA data added in quadrature to the errors quoted in Ap. [9](#ap:fml)." (2.3.1 Photometry)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Calibrated data cubes were constructed using `CASA`’s `TCLEAN` package." (2.2.1)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with the full observed bandwidth ($84.2$$-$$114.9\, \mathrm{GHz}$) with natural weighting in order to optimize sensitivity" (2.3.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel width 62.5 MHz (~220 km/s) for 3 mm cubes; 16 MHz for targeted scans  
  > "The cubes have a channel width of $62.5\, \mathrm{MHz}$ ($\sim$$220\, \mathrm{km s^{-1}}$)." (2.2.1)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SED fit: lambda0-Tdust empirical relation  
  > "we use the empirical relationship between $\lambda_{0}$ and $\mathrm{T_{\rm dust}}$ given in Eq. 2 of (cite: spilker16) to constrain $\lambda_{0}$" (2.3.2) [from (cite: spilker16)]
- LABOCA reduction and noise removal  
  > "The resulting time-ordered data undergo various calibration, noise removal, and flagging procedures detailed fully in (cite: greve12)." (2.3.1 APEX) [from (cite: greve12)]
- SPT flux extraction/deboosting  
  > "The data were extracted and deboosted according to the procedure described in (cite: everett20)." (2.3.1 SPT) [from (cite: everett20)]
- [CII] APEX/FLASH observation and processing  
  > "A full detail of the observation scheme and data processing procedure is detailed in (cite: gullberg15)." (Appendix A) [from (cite: gullberg15)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration was used
- tclean cell size, image size, cleaning threshold and masks
- Line fitting details (MCMC priors, line-free channels, line widths) for redshift determination
- emcee settings (walkers, steps, priors on Tdust and redshift)
- Lens magnifications for the 42 unmodeled sources beyond the median 5.5
- Exact ALESS data used and SED fitting adjustments
- Photometric redshift prior construction details

## Analysis recipe

1. **Image 3 mm cubes and continuum**: CASA tclean cubes (62.5 MHz channels) and natural-weighted continuum over full bandwidth  
  > "The continuum images were created using `CASA`’s `TCLEAN` procedure with the full observed bandwidth ($84.2$$-$$114.9\, \mathrm{GHz}$) with natural weighting" (2.3.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and determine redshifts**: Brightest-pixel spectrum for unresolved sources; imfit 2D Gaussian per channel for marginally resolved; line profiles fitted by MCMC; redshifts averaged over lines  
  > "`CASA`’s `imfit` routine is used to fit a 2D Gaussian to the source in each datacube slice and extract the flux and associated error." (2.3.1 ALMA); "The redshifts are derived by averaging the redshifts for individual line detections" (3.1.1)
   - software: CASA
   - fitting: MCMC line profile fits  
  > "Because these line profiles were fitted using a Markov-Chain Monte Carlo (MCMC) to sample to posterior probability" (3.1.1)
   - validation: Single-line sources confirmed with APEX/ATCA/ALMA follow-up; compared with previously published values (<0.1%)  
  > "the redshifts with previously published values also differ at the $< .1\%$ level and agree within their stated error bars" (3.1.1)
3. **Fit SEDs**: Modified blackbody (beta=2, lambda0 tied to Tdust) with CMB term; second fit with added mid-IR power law; data shortward of 50 um rest masked for MBB  
  > "The only free parameters in this SED fit are the overall SED normalization, dust temperature, and redshift." (2.3.2)
   - software: emcee
   - parameter: beta = 2; mask lambda_rest < 50 um  
  > "we mask data shortward of $\lambda_{\mathrm{rest}}$$=$$50\, \mathrm{\mu m}$ (cite: greve12) for the modified blackbody fits" (2.3.2)
   - fitting: MCMC with emcee  
  > "we employ a Markov Chain Monte Carlo (MCMC) algorithm using the `emcee` package (cite: foremanmackey13) to sample the posterior probability function" (2.3.2)
   - validation: Median reduced chi2 1.8 (MBB), 0.7 (with power law)  
  > "with a median reduced ${\mathpalette\irchi\relax}^2$ value of 1.8" (3.2.1)
4. **Derive intrinsic properties**: LFIR 42.5-122.5 um, LIR 8-1000 um; dust mass from rest 345 GHz flux; SFR from Murphy+11 conversion; demagnify with lens models or median mu=5.5  
  > "The apparent FIR luminosity ($L_{\rm FIR}$) is calculated by integrating the fitted SED over the wavelength range $42.5-122.5\, \mathrm{\mu m}$" (2.3.3)
   - assumption: kappa = 0.015 (nu/250 GHz)^beta m^2/kg, beta=2; gas-to-dust ratio 100; Kroupa IMF; flat LCDM H0=68.1  
  > "We adopt $\kappa(\nu)/\, \mathrm{m^2 kg^{-1}} = 0.015 \times
(\nu_r/250\, \mathrm{GHz})^{\beta}$" (2.3.3); "Molecular gas mass was obtained by assuming a constant gas-to-dust ratio (taken to be $100$; e.g. (cite: casey14))." (4.3)
   - fitting: _not stated_
   - validation: Compared with MAGPHYS where direct SED fit possible  
  > "When a direct SED fit is possible, the two methods produce results that agree within the stated errors, with no bias." (4.3)
5. **Test Tdust-z evolution and compare distributions and models**: Maximum likelihood linear fit with intrinsic scatter; binned medians with bootstrap; KS tests vs Bethermin15 model; space density by scaling to ALESS in 2.5<z<4.5  
  > "we perform a maximum likelihood estimation assuming a linear model with an extra Gaussian variance term to account for intrinsic scatter" (4.2)
   - assumption: SPT and ALESS have equal source density at 2.5<z<4.5 above 3e12 Lsun  
  > "We assume the two surveys have equal source density in the region $2.5$$<$$z$$<$$4.5$ for $>$$3$$\times$$10^{12}\, \mathrm{{L_{\odot}}{}}$." (4.4)
   - fitting: _not stated_
   - validation: Bootstrapping gave similar errors  
  > "Error estimation using bootstrapping produced similar results to the errors shown." (4.4)

## Software

- **CASA** : Calibration, tclean imaging, imfit  
  > "The data were processed using the Common Astronomy Software Application (`CASA`; (cite: mcmullin07; petry12))." (2.2.1)
- **emcee** : MCMC SED fitting  
  > "using the `emcee` package (cite: foremanmackey13)" (2.3.2)
- **Miriad** : ATCA data editing, calibration, imaging  
  > "The software packages `Miriad` (cite: sault95) and `CASA` were used for editing, calibration and imaging." (Appendix ATCA)
- **BoA** : LABOCA map making  
  > "APEX/LABOCA maps were created for each source using the Bolometer Array analysis software (`BoA`; (cite: schuller10))." (2.3.1 APEX)
- **HIPE** v9.0: Herschel SPIRE reduction  
  > "The maps were produced using the standard reduction pipeline `HIPE` v9.0" (2.3.1 Herschel/SPIRE)
- **MAGPHYS** : ALESS SED-derived properties (from literature)  
  > "The `MAGPHYS` SED modeling code was used to obtain photometric properties (cite: dacunha15)." (3.2.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median spectroscopic redshift | 3.9 | 0.2 | dimensionless | 2 | The median of this distribution is $z_{\mathrm{median}} = 3.9 \pm 0.2$ |
| Median dust temperature | 52.4 | 2.3 | K | 3 | the median of the distribution is significantly higher at $T_{\mathrm{dust}}$$=$$52.4\pm2.3$K |
| Median intrinsic dust mass | 1.4e9 | 0.1e9 | Msun | 4 | the SPT sources have a median intrinsic dust mass of $1.4(1)$$\times$$10^{9}\, \mathrm{M_\odot}$ |
| Median SFR | 2.3e3 | 0.2e3 | Msun/yr | 4 | which corresponds to a median SFR of $2.3(2)\times 10^3\, \mathrm{{{\rm M}_{\odot} }yr^{-1}}$ for the SPT sample |
| Median intrinsic LFIR | 7.1e12 | 0.5e12 | Lsun | 4 | The median SPT intrinsic FIR luminosity is $7.1(5)$$\times$$10^{12}\, \mathrm{L_\odot}$ |
| Tdust-z slope | 4.7 | 1.5 | K per unit z | 5 | with a slope of $4.7$$\pm$$1.5\, \mathrm{K/z}$ |
| Number density z>4, LIR>3e12 Lsun | 2.6e-6 | 0.7e-6 | Mpc^-3 | 5 | the expected number of DSFGs above $z$$>$$4$ is $2.6(7)$$\times$$10^{-6}\, \mathrm{/Mpc^3}$ |
| Number density z>6 | 0.95e-7 | 1.0e-7 | Mpc^-3 | 5 | which we take to be $0.95(1.0)$$\times$$10^{-7}\, \mathrm{/Mpc^3}$ |

## Qualitative findings

- All 81 sources have spectroscopic redshifts; two rely on a single line (CO(3-2) most probable).  
  > "Only two of the redshifts are based on a single line, but they have no other possible redshift solution" (3.1.5)

## Claim tuples

- H: Do selection wavelength and lensing explain the SPT redshift distribution? | E: KS tests against Bethermin15 model with 1.4 mm selection and lensing | R: Model still ruled out at 3.2 sigma; median z~3.2 vs 3.9 | F: Observed SPT distribution sits at higher z than the model | **supported**
- H: Are SPT DSFGs intrinsically more extreme than unlensed DSFGs? | E: Compare demagnified LFIR and dust mass with ALESS | R: Median LFIR 7.1e12 vs 2.3e12 Lsun; Mdust 1.4e9 vs 7.3e8 | F: SPT sources are more extreme even after lensing correction | **supported**
- H: Does Tdust evolve with redshift? | E: ML linear fit and binned analysis | R: Slope 4.7±1.5 K/z with 8.4 K scatter; binned slope not significant | F: Mild evidence, not statistically significant | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lens models exist for only 39 sources; median magnification adopted for rest, so intrinsic properties are estimates  
  > "given that the median magnifications are merely an estimate, the intrinsic properties for these sources should be also treated as estimates" (3.2.2)
- Caveat (inferred, ours): Median magnification assumed for 42 sources may bias intrinsic properties
- Caveat (inferred, ours): Space density depends on assumed equal density with ALESS
- Caveat (inferred, ours): Multiplicity systems treated as single sources

## Reproducibility

- Data public (paper): Machine-readable tables on GitHub; ALMA project IDs listed  
  > "This table is available in machine-readable format at: <https://github.com/spt-smg/publicdata>" (Table 3 notes)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: MCMC line-fit and SED prior details
- Missing: Full lens model catalog
- Data volume (inferred): Several hundred GB across ~60 ALMA execution blocks and 7 projects
- Score (inferred): 3/5, Data are public and the SED recipe is mostly given, but imaging and line fitting details are sparse.
- Rediscovery candidate: no, Needs many projects and external lens models, and line-fit details are missing.

## Links

- Method: (cite: spilker16) (Lens models and lambda0-Tdust relation)
- Method: (cite: greve12) (SED fitting and LABOCA reduction)
- Companion: (cite: weiss13) (Cycle 0 redshift survey)
- Companion: (cite: strandet16) (Cycle 1 redshift survey)
- Related: SPT-SZ
- Related: ALESS
- Related: LESS

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 53,
  "rate": 0.639
 },
 "evidence_ok": true
}
```
