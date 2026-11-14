# The ALMA Spectroscopic Survey in the HUDF: Nature and Physical Properties of Gas-mass Selected Galaxies Using MUSE Spectroscopy

`2019ApJ...882..140B` | The Astrophysical Journal 2019 | first author: Boogaard, Leindert A. | arXiv: 1903.09167 | DOI: 10.3847/1538-4357/ab3102

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: In what kind of galaxies, and with what physical properties, is molecular gas detected in the flux-limited ASPECS-LP Band 3 line scan, using MUSE redshifts to identify the CO lines?  
  > "By doing a survey of molecular gas, in what kind of galaxies do we detect molecular gas emission at different redshifts, and what are the physical properties of these galaxies?" (Introduction)
- Target **Hubble Ultra Deep Field (ASPECS-LP Band 3 mosaic)**: coordinates _not stated_; z/distance CO emitters at 1 < z < 4 (MUSE spectroscopic redshifts)  
  > "The final mosaic covers a 4.6 arcmin$^{2}$ area in the HUDF (where the primary beam response is $>50\%$ of the peak sensitivity)." (2.1 ALMA Spectroscopic Survey); distance from MUSE HUDF spectroscopy (Inami2017) and photometric redshifts  
  > "The final mosaic covers a 4.6 arcmin$^{2}$ area in the HUDF (where the primary beam response is $>50\%$ of the peak sensitivity)." (2.1 ALMA Spectroscopic Survey)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 3 (84-115 GHz; 3.6-2.6 mm)  
  > "Here we use the results from the spectral scan of Band 3 (84-115 GHz; 3.6-2.6 mm)" (Introduction)
- frequencies and spectral setup: single cube, 7.813 MHz channels (~23.5 km/s at 99.5 GHz)  
  > "a spectral resolution of 7.813 MHz, corresponding to $\Delta v \approx 23.5$ km s$^{-1}$ at 99.5 GHz" (2.1 ALMA Spectroscopic Survey)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≈1.75'' x 1.49'' (natural weighting at 99.5 GHz)  
  > "a spatial resolution of $\approx 1.75\ensuremath{''} \times 1.49\ensuremath{''}$ (synthesized beam with natural weighting at 99.5 GHz)" (2.1 ALMA Spectroscopic Survey)
- max recoverable scale: _not stated_
- sensitivity: average rms ≈0.2 mJy/beam, deepest ≈0.13 mJy/beam around 100 GHz  
  > "The average root mean square (rms) sensitivity is $\approx 0.2$ mJy beam$^{-1}$ but varies across the frequency range, being deepest ($\approx 0.13$ mJy beam$^{-1}$) around 100 GHz" (2.1 ALMA Spectroscopic Survey)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.54 GHz)
- Line: CO 3-2 (345.80 GHz)
- Line: CO 4-3 (461.04 GHz)
- Other facility **VLT/MUSE**: HUDF integral-field spectroscopy giving redshifts and [OII], [NeIII] fluxes  
  > "The HUDF was observed with the MUSE as part of the MUSE *Hubble* Ultra Deep Field survey (cite: Bacon2017)." (2.2 MUSE HUDF Survey)
- Other facility **Chandra 7 Ms**: X-ray AGN identification  
  > "we use the *Chandra* X-ray data available over the GOODS-S region from (cite: Luo2017), which reaches the full depth of 7 Ms over the HUDF area." (2.4 X-ray photometry)
- Other facility **HST, Spitzer, Herschel photometry**: UV-FIR photometry for SED fitting  
  > "We use the photometric compilation by (cite: Skelton2014), which includes UV, optical and near-IR photometry from the *Hubble* Space Telescope (*HST*) and ground-based facilities" (2.3 Multi-wavelength data (UV–radio) and MAGPHYS)
- External data: MUSE HUDF redshift catalog  
  > "Redshifts were identified semi-automatically and the full spectroscopic catalog is presented in (cite: Inami2017)." (2.2 MUSE HUDF Survey) [from (cite: Inami2017)]
- External data: Chandra 7 Ms X-ray catalog and AGN criteria  
  > "(cite: Luo2017) adopt the following 6 criteria to distinguish X-ray AGN from other sources of X-ray emission" (2.4 X-ray photometry) [from (cite: Luo2017)]
- External data: Photometric compilation  
  > "We use the photometric compilation by (cite: Skelton2014)" (2.3 Multi-wavelength data (UV–radio) and MAGPHYS) [from (cite: Skelton2014)]
- External data: CO excitation ladder r21=0.76, r31=0.42, r41=0.31 for MS galaxies  
  > "We use the excitation ladder as estimated by (cite: Daddi2015) for galaxies on the MS, where $r_{21} = 0.76 \pm 0.09$, $r_{31} = 0.42 \pm 0.07$ and $r_{41} = 0.31 \pm 0.06$" (4.3 Molecular gas properties) [from (cite: Daddi2015)]
- External data: Main sequence relations  
  > "We show the MS relations from (cite: Whitaker2014) and (cite: Schreiber2015) at the average redshift of the sample." (6.2 Molecular gas across the galaxy main sequence) [from (cite: Whitaker2014; Schreiber2015)]

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
- weighting robust: natural weighting  
  > "synthesized beam with natural weighting at 99.5 GHz" (2.1 ALMA Spectroscopic Survey)
- uv taper: 3'' tapered cube used for prior-based spectra  
  > "We extract a single-pixel spectrum from the 3$''$ tapered cube at the position of each MUSE source in the redshift range" (3.2 Additional sources with MUSE redshift priors at z < 2.9)
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

- ALMA Band 3 data acquisition and reduction  
  > "The acquisition and reduction of the Band 3 data are described in detail in (cite: DecarliALP)." (2.1 ALMA Spectroscopic Survey) [from (cite: DecarliALP)]
- CO line search and fidelity/completeness  
  > "An extensive description of the line search is provided in (cite: Gonzalez-LopezALP)." (3.1 Identification of the line search sample) [from (cite: Gonzalez-LopezALP)]
- Molecular gas mass derivation  
  > "The derivation of the molecular gas properties of our sources is detailed in (cite: AravenaALP)." (4.3 Molecular gas properties) [from (cite: AravenaALP)]
- 1.2 mm continuum combination  
  > "as detailed in (cite: AravenaALP)" (2.3 Multi-wavelength data (UV–radio) and MAGPHYS) [from (cite: AravenaALP)]

### Not stated but needed to reproduce (our reading)

- Exact MCMC implementation (custom code, not released) and number of walkers/steps for the prior-based line fits
- MAGPHYS version, library and fitting setup beyond the high-z extension
- Which ALMA execution blocks or pipeline version produced the cube
- Details of PLATEFIT modifications
- Aperture/tapering parameters of the 3'' tapered cube

## Analysis recipe

1. **Identify CO redshifts of line-search sources**: Cross-match 16 line-search candidates (fidelity>=0.9) with MUSE redshifts, extract MUSE spectra for the rest, and use photometric redshifts  
  > "First, we correlate the spatial position and potential redshifts of the CO lines with known spectroscopic redshifts from MUSE (cite: Inami2017)." (3.1 Identification of the line search sample)
   - fitting: _not stated_
   - validation: Cross-correlation with templates and stacking of absorption features for 3mm.12  
  > "which is detected at $\mathrm{S/N} > 4$ both via cross-correlation with a $z\approx2.5$ spectral template and by stacking absorption features" (3.1 Identification of the line search sample)
2. **Prior-based CO(2-1) search at MUSE positions and redshifts**: Gaussian line fits to single-pixel spectra from the 3'' tapered cube using a Bayesian MCMC  
  > "We then fit the lines with a Gaussian curve, using a custom-made Bayesian Markov chain Monte Carlo routine with the following priors:" (3.2 Additional sources with MUSE redshift priors at z < 2.9)
   - software: custom MCMC
   - parameter: Priors: velocity Gaussian sigma=100 km/s; width Maxwellian 100 km/s; flux Gaussian sigma=0.5 Jy km/s  
  > "*line flux*: a Gaussian distribution centered at zero, with $\sigma = 0.5$ Jy km s$^{-1}$, allowing both positive and negative line fluxes to be fitted." (3.2 Additional sources with MUSE redshift priors at z < 2.9)
   - parameter: Selection: S/N>3 in all three fits, |dv|<80 km/s, width>100 km/s  
  > "we select only the objects that have a velocity offset of $<80$ km s$^{-1}$ from the MUSE systemic redshift" (3.2 Additional sources with MUSE redshift priors at z < 2.9)
   - fitting: Uncertainties from 16th and 84th percentiles of posteriors  
  > "The uncertainties are computed from the 16th and 84th percentiles of the posterior distributions of each parameter." (3.2 Additional sources with MUSE redshift priors at z < 2.9)
   - validation: Refit with broader width prior (200 km/s) and with uniform frequency prior over ±1 GHz  
  > "we rerun the fit with a broader prior on the line width of 200 km s$^{-1}$." (3.2 Additional sources with MUSE redshift priors at z < 2.9)
3. **Derive stellar mass, SFR, A_V from SED fitting**: MAGPHYS high-z extension on UV-FIR photometry including ASPECS 1.2 and 3.0 mm  
  > "we derive the SFR (and $M_{*}$ and $A_{V}$) from the UV-FIR data (including 24$\mu$m–160$\mu$m and ASPECS-LP 1.2 mm and 3.0 mm) using MAGPHYS" (4.1 Star formation rates from MAGPHYS & [OII])
   - software: MAGPHYS
   - parameter: Zero-point errors added in quadrature, 5% error floor  
  > "include a 5% error-floor to further account for systematic errors in the physical models (following (cite: Leja2018))" (2.3 Multi-wavelength data (UV–radio) and MAGPHYS)
   - assumption: Chabrier IMF; systematic uncertainties ~0.3 dex  
  > "systematic uncertainties can be of order $\sim 0.3$ dex (cite: Conroy2013)" (2.3 Multi-wavelength data (UV–radio) and MAGPHYS)
   - fitting: Bayesian inference of posterior  
  > "The code performs a Bayesian inference of the posterior likelihood distribution of the fitted parameter" (2.3 Multi-wavelength data (UV–radio) and MAGPHYS)
   - validation: _not stated_
4. **Unobscured SFR and metallicity from MUSE lines**: SFR([OII]) following Kewley2004 without dust correction; metallicity from [NeIII]/[OII] following Maiolino2008  
  > "We derive SFRs from $\mathrm{[O\,\textsc{ii}]}\ \lambda 3726,3729$ following (cite: Kewley2004), adopting a (cite: Chabrier2003) IMF." (4.1 Star formation rates from MAGPHYS & [OII])
   - software: PLATEFIT
   - assumption: [OII]/Halpha = 1.0 at 12+log(O/H)~8.8; X-ray AGN excluded  
  > "we instead adopt an average $\mathrm{[O\,\textsc{ii}]}\ \lambda 3726,3729$/$\mathrm{H}\alpha$ ratio of unity" (4.1 Star formation rates from MAGPHYS & [OII])
   - fitting: _not stated_
   - validation: Compared with mass-metallicity relations of Maiolino2008 and Zahid2014  
  > "They are all metal-rich and consistent with a solar or super-solar metallicity, in line with the expectations from the mass-metallicity relation." (5.4 Metallicities at 1.0 < z < 1.42)
5. **Convert CO flux to molecular gas mass**: M_mol = (alpha_CO/r_J1) L'_CO  
  > "$\ensuremath{M_{\mathrm{mol}}}/\ensuremath{\mathrm{M}_{\odot}}= \left(\alpha_{\mathrm{CO}}/r_{J1}\right)" (Molecular gas properties)
   - assumption: alpha_CO = 3.6 Msun (K km/s pc^2)^-1; MS excitation ladder  
  > "we use an $\ensuremath{\alpha_{\mathrm{CO}}}= 3.6$ $\mathrm{M}_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$, appropriate for star-forming galaxies" (4.3 Molecular gas properties)
   - fitting: _not stated_
   - validation: Supported by near-solar metallicities  
  > "This choice of $\alpha_{\mathrm{CO}}$ is supported by our finding that the ASPECS-LP sources are mostly on the MS and have (near-)solar metallicity" (4.3 Molecular gas properties)
6. **X-ray AGN fraction and detection fractions vs main sequence**: Cross-match to Chandra within 1'' and count AGN; compare CO detections to MUSE/photometric galaxy populations in M*-SFR bins  
  > "We spatially cross-match the X-ray catalog to the closest source within 1$''$ in our MUSE and multi-wavelength catalog over the ASPECS-LP area" (2.4 X-ray photometry)
   - assumption: MS scatter 0.3 dex; MS reference from polynomial fit to rolling median at low z  
  > "we show $\pm0.3$ dex scatter around a second order polynomial fit to the rolling median of the SFRs all the galaxies" (6.2.1 Systematic offsets in the MS)
   - fitting: _not stated_
   - validation: Compared with AGN fractions of Wang2017 and Haggard2010  
  > "The AGN fractions found in ASPECS-LP are broadly consistent with these ranges given the limited numbers and considerable Poisson error." (5.2 AGN fraction)

## Software

- **LINESEEKER** : line search (in Gonzalez-Lopez et al.)  
  > "LINESEEKER (cite: Gonzalez-Lopez2017b), FINDCLUMP (cite: Decarli2014; Walter2016) and MF3D (cite: Pavesi2018)" (3.1 Identification of the line search sample)
- **FINDCLUMP** : line search  
  > "FINDCLUMP (cite: Decarli2014; Walter2016)" (3.1 Identification of the line search sample)
- **MF3D** : line search  
  > "MF3D (cite: Pavesi2018)" (3.1 Identification of the line search sample)
- **MAGPHYS** high-z extension: SED fitting for M*, SFR, A_V  
  > "We use the high-$z$ extension of the SED-fitting code MAGPHYS to infer physical parameters" (2.3 Multi-wavelength data (UV–radio) and MAGPHYS)
- **PLATEFIT** modified: MUSE line fluxes and equivalent widths  
  > "The spectra are modeled with a modified version of PLATEFIT (cite: Tremonti2004; Brinchmann2004; Brinchmann2008)" (2.2 MUSE HUDF Survey)
- **GNUASTRO, ASTROPY, NUMPY, TOPCAT** : general analysis tools  
  > "TOPCAT (cite: Taylor2005), GNUASTRO (cite: Akhlaghi2015), IPYTHON (cite: Perez2007), NUMPY (cite: VanDerWalt2011), MATPLOTLIB (cite: Hunter2007), ASTROPY" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of line-search CO emitters | 16 | not stated | sources | 1 | In total, there are 16 emission line candidates for which the fidelity is $\ge0.9$. |
| Total CO sample including prior-based | 18 | not stated | sources | 2 | The full ASPECS-LP CO line sample consists of 18 galaxies with a CO detection in the HUDF; 16 detections without preselection and 2 MUSE redshift prior based detections. |
| X-ray AGN fraction among CO emitters | 20% at 1.0<z<1.7; 60% at 2.0<z<3.1 | not stated | percent | 6 | The AGN fraction among the ASPECS-LP sources is thus $2/10 = 20\%$ at $1.0<z<1.7$ and $3/5 = 60\%$ at $2.0<z<3.1$ |
| Median obscured/unobscured SFR ratio (line search) | 10.8 | +3.0/-5.1 | dimensionless | 4 | The median ratio (bootstrapped errors) of obscured/unobscured SFR is $10.8^{+3.0}_{-5.1}$ for the ASPECS-LP sources from the line search |
| Median depletion time at z~1.4 | ≈1.2 | not stated | Gyr | 5 | with a median depletion time of $\approx 1.2$ Gyr |
| Median Mmol/M* at z~1.4 | ≈0.6 | not stated | dimensionless | 5 | with a median of $\ensuremath{M_{\mathrm{mol}}}/M_{*} \ensuremath{\approx 0.6}$ |
| Detection completeness for M*>1e10 at 1<z<1.7 | ≈40% | not stated | percent | 6 | At $M_{*} > 10^{10}$ $\mathrm{M}_{\odot}$, we are $\approx40\%$ complete at $1.0 < z < 1.7$ |
| Limiting gas mass at 1.0<z<1.7 (5 sigma, FWHM 100 km/s) | ~10^9.5 | not stated | Msun | 5 | the lowest gas mass we can detect at $5 \sigma$ (using the above assumptions and a FWHM for CO(2-1) of 100 km s$^{-1}$) is $\ensuremath{M_{\mathrm{mol}}}\sim 10^{9.5}$ $\mathrm{M}_{\odot}$ |

## Qualitative findings

- CO detections include galaxies below the main sequence at z~1.4 with substantial gas reservoirs  
  > "we also detect a number of galaxies that lie significantly below the main sequence (e.g., ASPECS-LP.3mm.02)" (6.2.2 Normal galaxies at 1.01 < z < 1.74)

## Claim tuples

- H: Can MUSE spectroscopy uniquely identify all ALMA line-search emitters as CO transitions? | E: Cross-matching 16 candidates with MUSE spectra and photometric redshifts | R: Redshift solutions for 16/16; 12 directly confirmed by MUSE | F: 10 CO(2-1), 5 CO(3-2), 1 CO(4-3) | **supported**
- H: CO-detected galaxies at z<=1.5 have metallicities consistent with a Galactic alpha_CO | E: [NeIII]/[OII] metallicities from MUSE | R: AGN-free sources are consistent with solar or super-solar | F: Galactic conversion factor is justified | **supported**
- H: Does the flux-limited survey preferentially detect AGN? | E: Chandra cross-match of CO emitters | R: 20% and 60% AGN fraction at z~1.4 and z~2.6 | F: No preferential AGN detection at z<2 | **partially**
- H: What part of the galaxy population is detected in CO? | E: Compare detections to MUSE/photometric galaxy distributions in M*-SFR | R: ~40% (50%) of galaxies with M*>=1e10 (1e10.5) detected at 1<z<2 (2<z<3) | F: CO detections span galaxies on, above, and below the MS | **supported**

## Reasoning

- Why this data: MUSE gives redshifts for all galaxies in the field without preselection, complementing the unbiased ALMA line scan  
  > "The MUSE HUDF is a natural complement to the ASPECS-LP in the same area on the sky, providing optical spectroscopy for all galaxies within the field of view, also without any preselection." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Prior-based selection is deliberately incomplete; MAGPHYS SFRs lie below MS literature relations; some redshifts rely on indirect evidence  
  > "we do not attempt to be complete." (3.2 Additional sources with MUSE redshift priors at z < 2.9)
- Caveat (inferred, ours): Four of 16 redshifts rest on photometric redshifts and absence of features
- Caveat (inferred, ours): Single alpha_CO and fixed excitation ladder applied to all sources including AGN and starbursts
- Caveat (inferred, ours): Small-number statistics for AGN fractions and detection fractions
- Caveat (inferred, ours): MS reference defined ad hoc due to SFR offsets between methods

## Reproducibility

- Data public (paper): ALMA project code printed; MUSE HUDF data from published release  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00324.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-search catalog and cube details live in companion papers
- Missing: Custom MCMC code not released
- Missing: MAGPHYS configuration details
- Missing: 1.2 mm continuum combination described elsewhere
- Data volume (inferred): ~50-200 GB for the Band 3 ASPECS-LP cube and raw data; MUSE and ancillary catalogs are small
- Score (inferred): 3/5, Main numbers are tabulated, but the ALMA reduction, line search and gas masses are in companion papers and the prior-search code is custom.
- Rediscovery candidate: no, Recipe depends heavily on companion papers (cube production, line search) and a non-released MCMC routine.

## Links

- Method: (cite: Gonzalez-LopezALP) (Line search, fidelity and completeness)
- Method: (cite: DecarliALP) (ALMA Band 3 observations and reduction)
- Method: (cite: AravenaALP) (Molecular gas derivation and 1.2 mm continuum)
- Companion: (cite: PoppingALP) (ASPECS-LP theory paper)
- Companion: (cite: Decarli2016) (ASPECS-Pilot results)
- Related: ASPECS-LP
- Related: MUSE HUDF Survey
- Related: ASPECS-Pilot

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 51,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
