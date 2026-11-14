# Diagnosing 0.1-10 au Scale Morphology of the FU Ori Disk Using ALMA and VLTI/GRAVITY

`2019ApJ...884...97L` | The Astrophysical Journal 2019 | first author: Liu, Hauyu Baobab | arXiv: 1908.02981 | DOI: 10.3847/1538-4357/ab391c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the 0.1-10 au scale morphology and thermal structure of the FU Ori disk (and companion FU Ori S), as constrained by new ALMA Band 3/4 continuum and VLTI/GRAVITY data plus the broadband SED?  
  > "We find that the emission in both FU Ori and FU Ori S at (sub)millimeter and near infrared bands is dominated by structures inward of $\sim$10 au radii." (abstract)
- Target **FU Ori**: coordinates pointing center R.A. 05h45m22.375s, Decl. +09d04m12.400s (J2000)  
  > "we assume the distance of FU Ori to be $d\sim$416 pc, according to the parallax measurement published in the second data release of the Gaia space telescope" (Introduction); z/distance ~416 pc  
  > "we assume the distance of FU Ori to be $d\sim$416 pc, according to the parallax measurement published in the second data release of the Gaia space telescope" (Introduction); distance from Gaia DR2 parallax  
  > "we assume the distance of FU Ori to be $d\sim$416 pc, according to the parallax measurement published in the second data release of the Gaia space telescope" (Introduction)
- Target **FU Ori S**: coordinates _not stated_; z/distance ~416 pc (assumed same as FU Ori)  
  > "which also covered its $\sim$0$\ensuremath{''}$5 separation companion, FU Ori S" (2.3 ALMA observations); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00388.S
- bands: Band 3 (86-100 GHz) and Band 4 (146-160 GHz)  
  > "Band 3 (86-100 GHz; $\sim$80 mas angular resolution) and Band 4 (146-160 GHz; $\sim$50 mas angular resolution)" (abstract)
- frequencies and spectral setup: four 1.875 GHz wide spectral windows, 976.562 kHz channel spacing; Band 3 centered 86.000, 87.863, 98.196, 100.001 GHz; Band 4 146.001, 147.863, 158.196, 160.001 GHz  
  > "The correlators were configured to cover four 1.875 GHz wide spectral windows with a 976.562 kHz channel spacing." (2.3 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: uv distances ~100 m - 13 km  
  > "The *uv* distance ranges covered by these observations are $\sim$100 m – 13 km." (2.3 ALMA observations)
- angular resolution: Band 3 100 GHz: 0.082x0.075 arcsec; Band 4 160 GHz: 0.047x0.043 arcsec  
  > "At Band 3, the spectral window centered at 100 GHz achieved a $\theta_{\mbox{\scriptsize maj}}\times\theta_{\mbox{\scriptsize min}}$=0$''$.082$\times$0$''$.075 (P.A.=-79$^{\circ}$) synthesized beam" (2.3 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 69 uJy/beam (Band 3, 100 GHz); 72 uJy/beam (Band 4, 160 GHz)  
  > "a 69 $\mu$Jy beam$^{-1}$ RMS noise level" (2.3 ALMA observations)
- time on source: _not stated_
- observing dates: Band 3: 2017 Nov 08; Band 4: 2017 Nov 07  
  > "The Band 3 observations were carried out on 2017 November 08." (2.3 ALMA observations)
- pi or archival as stated: PI Hauyu Baobab Liu (new observations)  
  > "(Project code: 2017.1.00388.S, PI: Hauyu Baobab Liu)" (2.3 ALMA observations)
- Other facility **VLTI/GRAVITY**: K-band (2-2.45 um) visibilities and closure phases, medium resolution, ATs, baselines 40-100 m  
  > "FU Ori was observed by VLTI/GRAVITY (cite: 2017A&A...602A..94G) on 2016 November 25 and 26." (2.2 VLTI/GRAVITY observations)
- Other facility **Spitzer and Herschel**: archival infrared spectra for SED (Herschel from COPS-DIGIT-FOOSH archive)  
  > "The *Herschel*/PACS and SPIRE spectra were taken from the COPS-DIGIT-FOOSH (CDF) archive" (2.1 Spitzer and Herschel spectra)
- Other facility **JVLA, SMA, earlier ALMA**: previous (sub)mm and cm fluxes for the SED  
  > "previous (sub)millimeter observations of the ALMA, the Submillimeter Aray (SMA)[^1] and the NRAO[^2] Karl G. Jansky Very Large Array (JVLA)" (Introduction)
- External data: JVLA 29-37 GHz fluxes  
  > "By quoting the previous JVLA observations at 29-37 GHz (cite: Liu2017A&A)" (3.2 ALMA data) [from (cite: Liu2017A&A)]
- External data: ALMA ~225 GHz fluxes  
  > "the ALMA observations at $\sim$225 GHz (Pérez et al. submitted)" (3.2 ALMA data) [from Pérez et al. submitted]
- External data: ALMA ~346 GHz fluxes  
  > "at $\sim$346 GHz (cite: Hales2015ApJ)" (3.2 ALMA data) [from (cite: Hales2015ApJ)]
- External data: DSHARP dust optical constants and analytic radiative transfer solutions  
  > "we utilized the DSHARP dust optical constants published in (cite: Birnstield2018ApJ)" (4.2 Individual emission components) [from (cite: Birnstield2018ApJ)]
- External data: calibrator diameter HD 38494 from JSDC  
  > "estimated to be $\theta_\mathrm{UD}=0.71\pm0.06$ mas according to the Jean-Marie Mariotti Center Stellar Diameters Catalogue" (2.2 VLTI/GRAVITY observations) [from (cite: 2017yCat.2346....0B)]

## Processing

### Calibration

- pipeline or manual: manual calibration and phase self-calibration  
  > "We manually calibrated and phase self-calibrated these data using the CASA software package (cite: McMullin2007) version 5.4.0." (2.3 ALMA observations)
- casa version: CASA 5.4.0  
  > "We manually calibrated and phase self-calibrated these data using the CASA software package (cite: McMullin2007) version 5.4.0." (2.3 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800: 2.0 Jy, alpha -0.30 at 93.015 GHz; 1.6 Jy, alpha -0.4 at 153.016 GHz  
  > "we assumed that J0510+1800 has a 2.0 Jy absolute flux and a $-$0.30 spectral index at the reference frequency 93.015 GHz" (2.3 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: phase self-calibration (details not given)  
  > "We manually calibrated and phase self-calibrated these data" (2.3 ALMA observations)

### Imaging

- task: CASA clean, MFS, nterm=1, each spectral window imaged separately  
  > "we created images for each of the four spectral windows separately using the multi-frequency synthesis (MFS) method, setting the parameter *nterm*=1." (2.3 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs Robust = 0  
  > "We produced the Briggs Robust = 0 weighted continuum images from line-free spectral channels using the CASA task `clean`." (2.3 ALMA observations)
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
- final beam: 0.082x0.075 arcsec (100 GHz); 0.047x0.043 arcsec (160 GHz)  
  > "at Band 4, the spectral window centered at 160 GHz achieved a $\theta_{\mbox{\scriptsize maj}}\times\theta_{\mbox{\scriptsize min}}$=0$''$.047$\times$0$''$.043 (P.A.=57$^{\circ}$) synthesized beam" (2.3 ALMA observations)
- final rms: 69 uJy/beam (Band 3), 72 uJy/beam (Band 4)  
  > "a 72 $\mu$Jy beam$^{-1}$ RMS noise level" (2.3 ALMA observations)

### Inherited from earlier work

- Herschel/SPIRE semi-extended source correction and data reduction  
  > "We refer to Section 2.2 of (cite: Green2016AJ) for a complete description of the data reduction." (2.1 Spitzer and Herschel spectra) [from (cite: Green2016AJ)]
- dust radiative transfer and opacity framework  
  > "were evaluated based on the analytic radiative transfer solutions published in (cite: Birnstield2018ApJ)" (4.2 Individual emission components) [from (cite: Birnstield2018ApJ)]
- free-free optical depth formula  
  > "Following (cite: Mezger1967) and (cite: Keto2003), we approximated the optical depth of the free-free emission components" (4.2 Individual emission components) [from (cite: Mezger1967); (cite: Keto2003)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection and masks for clean
- Image size, cell size, number of clean iterations/threshold
- Self-calibration solution intervals and number of rounds
- Gaussian fit regions/procedure for flux extraction
- Initial parameter values for MCMC and the full likelihood form
- Stated GRAVITY reduction/calibration details beyond pipeline version
- Pérez et al. 225 GHz fluxes and other SED data values (JVLA, SMA, Herschel, Spitzer) not tabulated
- Radius used for converting solid angles/grain size distribution upper limit handling

## Analysis recipe

1. **Calibrate and image ALMA continuum**: Manual CASA calibration, phase self-cal, per-spw MFS clean images  
  > "We manually calibrated and phase self-calibrated these data using the CASA software package (cite: McMullin2007) version 5.4.0." (2.3 ALMA observations)
   - software: CASA
   - parameter: Briggs robust=0, nterm=1  
  > "We produced the Briggs Robust = 0 weighted continuum images from line-free spectral channels using the CASA task `clean`." (2.3 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure ALMA fluxes and spectral indices**: Two-dimensional Gaussian fits; spectral indices over frequency ranges combined with literature fluxes  
  > "Their fluxes determined by fitting two-dimensional Gaussians are summarized in Table" (3.2 ALMA data)
   - assumption: F_nu = F0 (nu/nu0)^alpha  
  > "$F_{\nu}=F_{0}(\nu/\nu_{0})^{\alpha}$" (footnote 5)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit geometric model to GRAVITY visibilities**: Chi-squared fits of uniform disk (compact) plus 2D Gaussian (extended) with flux ratios interpolated at eight wavelengths from 2.0 to 2.45 um  
  > "We then performed chi-squared fits to determine the sizes of the two components, and to determine the flux ratios as a linear interpolation between eight equally spaced wavelengths between 2.0 and 2.45 $\mu$m (R$\sim$40)." (4.1 Interpreting VLTI/GRAVITY data)
   - assumption: constant component sizes with wavelength; concentric in most trials  
  > "we assumed that the VLTI-compact and the VLTI-extended components have constant sizes over the wavelength range covered by the VLTI/GRAVITY observations." (4.1 Interpreting VLTI/GRAVITY data)
   - fitting: chi-squared minimization  
  > "We then performed chi-squared fits to determine the sizes of the two components, and to determine the flux ratios as a linear interpolation between eight equally spaced wavelengths" (4.1 Interpreting VLTI/GRAVITY data)
   - validation: Compared with viscous accretion disk model of Calvet et al. 1991  
  > "appears fully consistent with the viscous accretion disk model of (cite: Calvet1991ApJ)" (4.1 Interpreting VLTI/GRAVITY data)
4. **Multi-component SED model with MCMC**: Sum of dust slab and free-free components with mutual obscuration, fit to SED with MCMC  
  > "After we obtained an approximate fit, we used MCMC to simultaneously optimize all free parameters" (4.3 Abstracted geometric model and integrated SEDs)
   - software: emcee
   - parameter: 84 walkers, 1500 steps, first 500 discarded  
  > "The MCMC fittings were initialized with 84 walkers with 1500 iterative steps each; in the end, the results from the first 500 steps were discarded." (4.3 Abstracted geometric model and integrated SEDs)
   - parameter: Herschel/SPIRE, PACS, Spitzer/IRS errors set to 1000, 10, 1 times the fluxes  
  > "artificially assigning the flux errors of the *Herschel*/SPIRE, *Herschel*/PACS, and *Spitzer*/IRS to be 1000, 10, and 1 times the detected fluxes" (4.3 Abstracted geometric model and integrated SEDs)
   - assumption: DSHARP opacities, 170 K ice sublimation, power-law grain size q=3.5, amin=1e-4 mm, face-on slabs  
  > "we simply assumed the typical power-law grain size distribution with a power-law index $q=$3.5, the minimum grain size $a_{\mbox{\scriptsize min}}=$10$^{-4}$ mm" (4.2 Individual emission components)
   - fitting: flat priors from 0.5x to 2x initial value; likelihood set to -inf if FU Ori S 9 GHz flux exceeds 3 sigma  
  > "We assumed flat priors, which permitted each parameter to vary from half of its initial value to two times of the initial value." (4.3 Abstracted geometric model and integrated SEDs)
   - validation: Monitored likelihood contributions; model also close to unfitted Spitzer/Herschel spectra  
  > "We have monitored how the likelihood evolved over the MCMC iterations to make sure that the contribution of the *Herschel* and *Spitzer* data are on the same order with the rest of the data." (4.3 Abstracted geometric model and integrated SEDs)
5. **Compare dust temperatures with heating models**: Compare fitted temperatures to steady viscous disk T(r) (Pringle 1981) and radiative equilibrium disk (Chiang & Goldreich 1997)  
  > "we compare our fits of dust temperatures (Table [\[tab:components\]](#tab:components)) with the simplest analytic models of the dust temperature profiles (c.f., (cite: Chiang1997ApJ) and references therein)" (4.4.3 Outbursting versus quiescent disks?)
   - parameter: M*=0.5 Msun, Mdot=1e-8,1e-6,1e-4 Msun/yr, R*=2 Rsun  
  > "$M_{*}=$0.5 $M_{\odot}$ is the assumed host protostellar mass" (4.4.3 Outbursting versus quiescent disks?)
   - assumption: T*=4000 K for irradiated disk  
  > "We assumed an effective stellar temperature $T_{*}=$4000 K and stellar radius $R_{*}=$2 $R_{\odot}$" (4.4.3 Outbursting versus quiescent disks?)
   - fitting: _not stated_
   - validation: Order-of-magnitude sanity check only  
  > "Such a comparison can serve as a sanity check for whether or not a certain heating mechanism can potentially provide a sufficiently high heating rate" (4.4.3 Outbursting versus quiescent disks?)

## Software

- **CASA** 5.4.0: calibration, self-calibration, imaging of ALMA data  
  > "using the CASA software package (cite: McMullin2007) version 5.4.0" (2.3 ALMA observations)
- **GRAVITY pipeline** 1.0.11: reduction of VLTI/GRAVITY data  
  > "We reduced the data using the GRAVITY pipeline (cite: 2014SPIE.9146E..2DL) version 1.0.11." (2.2 VLTI/GRAVITY observations)
- **emcee** : MCMC (listed in software section)  
  > "CASA (cite: McMullin2007), Numpy (cite: VanDerWalt2011), emcee (cite: Foreman-Mackey2013PASP)" (Software)
- **HIPE** : Semi-Extended Correction Tool for SPIRE spectra  
  > "apply the Semi-Extended Correction Tool in HIPE (cite: Ott2010; Wu2013)" (2.1 Spitzer and Herschel spectra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 100 GHz flux FU Ori | 3.0 | 0.11 | mJy | 2 | 100.001 & 3.0 & 0.11 & 1.6 & 0.14 |
| Band 4 160 GHz flux FU Ori | 7.4 | 0.20 | mJy | 2 | 160.002 & 7.4 & 0.20 & 4.0 & 0.19 |
| Spectral index 86-160 GHz FU Ori | 2.0 | 0.07 | dimensionless | 2 | 86-160 GHz & 2.0$\pm$0.07 & 1.9$\pm$0.07 |
| Spectral index 29-100 GHz FU Ori | 2.5 | 0.05 | dimensionless | 2 | 29-100 GHz & 2.5$\pm$0.05 & 2.7$\pm$0.05 |
| GRAVITY closure phases | smaller than 2.5 | not stated | degrees | 3 | The closure phases (CP) are smaller than $\pm$2.5 degrees. |
| VLTI-compact uniform disk diameter (best fit) | 1.06 | 0.01 | mas | 3 | / **4** / $1.06\pm0.01$ / $7.9\pm0.1$ / $0.6\pm0.1$ / $1.0\pm0.1$ / 1.03 / |
| VLTI-extended Gaussian FWHM (best fit) | 7.9 | 0.1 | mas | 3 | / **4** / $1.06\pm0.01$ / $7.9\pm0.1$ / $0.6\pm0.1$ / $1.0\pm0.1$ / 1.03 / |
| FUOri_dust1 temperature | 370 | +63/-49 | K | 4 | 370$^{+63}_{-49}$ & 45$^{+10}_{-12}$ |
| FUOri_dust1 amax | 2.4 | +0.40/-0.32 | mm | 4 | 2.4$^{+0.40}_{-0.32}$ & Comp. 2 |
| FUOri_dust2 temperature | 140 | +20/-26 | K | 4 | 2 & 140$^{+20}_{-26}$ & 0.63$^{+0.12}_{-0.099}$ |
| FUOri_dust4 temperature | 690 | +18/-12 | K | 4 | 4 & 690$^{+18}_{-12}$ & 0.0095$^{+0.0019}_{-0.0018}$ |
| FUOri_dust1 dust mass | 510 | +210/-190 | Earth masses | 4 | 510$^{+210}_{-190}$ |

## Qualitative findings

- Emission from both FU Ori and FU Ori S at (sub)mm and NIR is dominated by structures inside ~10 au; small closure phases imply approximately face-on, centrally symmetric.  
  > "We detected closure phases close to zero from FU Ori with VLTI/GRAVITY, which indicate the source is approximately centrally symmetric and therefore is likely viewed nearly face-on." (abstract)
- Tentative evidence for vertical dust settling in inner 10 au of FU Ori  
  > "we tentatively detect evidence of vertical dust settling in the inner 10 au of the FU Ori disk" (abstract)

## Claim tuples

- H: Is FU Ori's inner disk viewed face-on and centro-symmetric? | E: VLTI/GRAVITY closure phases and visibilities | R: Closure phases <2.5 deg, scatter <1 deg | F: Approximately centro-symmetric, likely nearly face-on | **supported**
- H: Can viscous heating with ~1e-4 Msun/yr explain inner disk emission from 0.1 to 10 au? | E: Geometric fits to GRAVITY plus SED MCMC and comparison to T_viscous | R: Compact component matches viscous disk spectrum; dust1 temperature consistent with viscous heating | F: Constant ~1e-4 Msun/yr inflow replenishes hot inner disk | **supported**
- H: Is there vertical dust settling in FU Ori? | E: Compare amax of dust1 and dust2 components in SED fit | R: dust1 (mm-size, hotter) obscured by dust2 (0.2 mm) | F: Tentative evidence only | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Multi-component SED fitting chosen since disks have substructures and the sources are unresolved; MCMC needed because components switch opacity tables  
  > "Because of this mid-routine shift, it is very difficult to implement fitting methods other than MCMC." (4.3 Abstracted geometric model and integrated SEDs)
- Alternative: Allowing small temperature range per dust component rejected as not meaningful given SPIRE aperture limits  
  > "we do not consider it to be meaningful to use a further detailed parameterization for dust temperature profiles" (4.3 Abstracted geometric model and integrated SEDs)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust masses uncertain due to opacity; analytic heating comparison not conclusive  
  > "We cannot accurately determine the dust masses of these two components due to the uncertainties of the dust mass opacities." (4.4.1 FU Ori model)
- Caveat (inferred, ours): SED model is non-unique; components and obscuration geometry chosen by hand
- Caveat (inferred, ours): Down-weighting Herschel/Spitzer by arbitrary factors affects fit
- Caveat (inferred, ours): Sources only marginally resolved by ALMA
- Caveat (inferred, ours): Face-on assumption drives results
- Caveat (inferred, ours): 9 GHz data uncertain

## Reproducibility

- Data public (paper): ALMA project code given; GRAVITY from ESO archive  
  > "This paper is based on data obtained from the ESO Science Archive Facility under request number AMERAND384481." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Tabulated literature SED fluxes
- Missing: MCMC code and initial parameters
- Missing: Imaging parameters
- Missing: GRAVITY calibrated data products
- Data volume (inferred): ~50-150 GB raw ALMA for two long-baseline EBs; GRAVITY small
- Score (inferred): 3/5, Data public and key steps described, but SED model inputs and imaging parameters incomplete
- Rediscovery candidate: no, Main results depend on multi-facility data and hand-tuned SED model with unspecified inputs.

## Links

- Method: (cite: Birnstield2018ApJ) (dust opacities and radiative transfer solutions)
- Method: (cite: Green2016AJ) (Herschel spectra reduction)
- Companion: (cite: Liu2017A&A) (previous JVLA observations of FU Ori)
- Companion: Pérez et al. submitted (ALMA 225 GHz data)
- Related: COPS-DIGIT-FOOSH
- Related: DSHARP

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00548.S",
  "2016.1.01228.S"
 ],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 59,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
