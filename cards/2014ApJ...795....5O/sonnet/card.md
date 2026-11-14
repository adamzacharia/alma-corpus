# Faint Submillimeter Galaxies Revealed by Multifield Deep ALMA Observations: Number Counts, Spatial Clustering, and a Dark Submillimeter Line Emitter

`2014ApJ...795....5O` | The Astrophysical Journal 2014 | first author: Ono, Yoshiaki | arXiv: 1403.4360 | DOI: 10.1088/0004-637X/795/1/5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the 1.2 mm number counts and clustering (galaxy bias) of faint (0.1-1 mJy) SMGs in multifield deep ALMA maps, and what is a serendipitous line emitter (SLE-1)?  
  > "We identify faint SMGs with flux densities of $0.1-1.0$ mJy in the deep Band 6 and Band 7 maps of $10$ independent fields that reduce cosmic variance effects." (abstract)
- Target **Himiko field (Map 1)**: coordinates _not stated_; z/distance z = 6.595  
  > "who targeted an extremely luminous Ly$\alpha$ blob at $z = 6.595$, Himiko." (2.1 Our Data); distance from _not stated_
- Target **NB921-N-79144 field (Map 2)**: coordinates _not stated_; z/distance z=6.511  
  > "a spectroscopically confirmed Ly$\alpha$ emitter (LAE) at $z=6.511$, NB921-N-79144" (2.1 Our Data); distance from (cite: ouchi2010)  
  > "a spectroscopically confirmed Ly$\alpha$ emitter (LAE) at $z=6.511$, NB921-N-79144" (2.1 Our Data)
- Target **Archival quasar fields (Maps 3-10)**: coordinates _not stated_; z/distance z ~ 5-6  
  > "Their observations were conducted for spectroscopically confirmed quasars at $z \sim 5-6$." (2.2 Archival Data); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00115.S, 2012.1.00602.S, 2011.0.00206.S, 2011.0.00243.S, 2011.0.00268.S
- bands: Band 6 and Band 7 (around 1 mm)  
  > "We analyze continuum maps at around $1$ mm with high sensitivities and high angular resolutions, obtained in ALMA cycle 0 and cycle 1 observations." (2. ALMA Data)
- frequencies and spectral setup: Map 1: four spectral windows of 1875 MHz at 250.24, 252.11, 265.90, 267.78 GHz  
  > "The central frequency of the four spectral bands is $250.24$ GHz, $252.11$ GHz, $265.90$ GHz, and $267.78$ GHz." (2.1 Our Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Map 1: 16 12-m antennas, extended configuration, 36-400 m baselines  
  > "with a $16$ 12-m antenna array under the extended configuration of $36-400$ m baseline." (2.1 Our Data)
- baselines: _not stated_
- angular resolution: ~0.6-0.8'' (own maps); ~0.6-1.5'' (archival)  
  > "The final synthesized beam sizes of the maps are $\sim 0.6\ensuremath{''} - 0.8\ensuremath{''}$." (2.1 Our Data)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma 17 (Map 1), 52 (Map 2) uJy/beam; archival 21-88 uJy/beam  
  > "The $1 \sigma$ noises of the maps uncorrected for primary beam attenuations are $\simeq 21 - 88$ $\mu$Jy beam$^{-1}$." (2.2 Archival Data)
- time on source: Map 1: 3.17 h; Map 2: 1.22 h  
  > "The total on-source integration time was $3.17$ hours." (2.1 Our Data); "The total on-source integration time was $1.22$ hours." (2.1 Our Data)
- observing dates: Map 1: 2012 July 15, 18, 28, 31; Map 2: 2013 June 18, 19  
  > "Deep ALMA Band 6 observations were carried out in 2012 July 15, 18, 28, and 31" (2.1 Our Data)
- pi or archival as stated: _not stated_
- Line: [CII] (serendipitous SLE-1 candidate) 3P3/2-3P1/2 (1900.5 GHz)
- Other facility **Subaru, UKIRT, HST, Spitzer, Herschel, GALEX, XMM**: Multiwavelength upper limits for SLE-1  
  > "we find no detectable source at the position of SLE–1 in the multiwavelength images." (6)
- External data: Bright SMG ALMA catalog (91 sources, SNR>4) for >1 mJy counts  
  > "We use $91$ sources whose SNRs are higher than $4.0$ in Table 3 and Table 4 of (cite: hodge2013)." (4.2) [from (cite: hodge2013); (cite: karim2013)]
- External data: Faint SMG counts from SXDS ALMA catalog  
  > "We also construct the differential number counts using the source catalog of (cite: hatsukade2013)" (4.2) [from (cite: hatsukade2013)]
- External data: EBL at 1.2 mm from COBE FIRAS: 21.1 Jy/deg2  
  > "the EBL at 1.2 mm has been estimated to be $21.1^{+4.4}_{-4.6}$ Jy deg$^{-2}$" (4.3) [from (cite: fixsen1998)]
- External data: SMG redshift distribution (mean z~2.5)  
  > "we use a redshift distribution of SMGs obtained by follow-up spectroscopic observations (cite: chapman2005)." (5) [from (cite: chapman2005)]
- Simulation/model as data: Model number counts from Shimizu+2012, Hayward+2013, Cai+2013 compared with observations  
  > "Next we compare the observed number counts to theoretical predictions." (4.2)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Map 1: Neptune and Callisto; Map 2: J0238+166 and J2258-279  
  > "Neptune and Callisto were observed as a flux calibrator." (2.1 Our Data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA, standard manner  
  > "The data were reduced with the Common Astronomy Software Applications (cite: mcmullin2007) package in a standard manner." (2.1 Our Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Source extraction before PB correction; maps used within primary beam model  
  > "Source extractions are conducted on the ALMA maps before primary beam correction with SExtractor version 2.5" (3.1 Source Extraction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Number-count method (extraction, completeness, flux boosting, spurious fraction)  
  > "basically following the method described in (cite: hatsukade2013)." (3. Data Analysis) [from (cite: hatsukade2013)]
- Scaling to 1.2 mm via modified blackbody  
  > "Following the method by (cite: hatsukade2013), we scale the flux density of a source observed at a wavelength different from $1.2$ mm" (1) [from (cite: hatsukade2013)]
- Map 1 and Map 2 data details/calibration  
  > "Further details of the ALMA observations and sensitivities are summarized in (cite: ouchi2013) and will be presented in R. Momose et al. in preparation." (2.1 Our Data) [from (cite: ouchi2013); R. Momose et al. in preparation]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, robust, cell, size, cleaning)
- Continuum channel selection and line-free channels
- Flux calibration accuracy
- Map 2 reduction details (unpublished)
- Archival project-to-map mapping and details of archival reductions
- Number of artificial sources and trials in completeness simulations
- Priors/optimization for chi2 fits
- Line search algorithm for the cube

## Analysis recipe

1. **Extract sources and apply SNR cut**: SExtractor on maps before PB correction; negative maps for spurious fraction; keep peak SNR>4  
  > "A collection of at least six contiguous pixels above the $1.8 \sigma$ noise level are identified as an object." (3.1 Source Extraction)
   - software: SExtractor
   - parameter: 6 contiguous pixels above 1.8 sigma; final SNR>4.0  
  > "We limit the catalogs to objects whose peak SNR is higher than $4.0$." (3.1 Source Extraction)
   - fitting: _not stated_
   - validation: Negative-map extraction  
  > "The number of spurious sources is obtained by extracting sources from the negative map in the same manner as that for the positive map." (3.1 Source Extraction)
2. **Completeness and flux deboosting**: Inject flux-scaled synthesized beams (SNR 2-9) at random positions, re-extract; deboost by S_out/S_in  
  > "To obtain the de-boosted flux density, we divide the observed flux density of a detected source by the ratio $S_{\rm out} / S_{\rm in}$" (3.2)
   - software: SExtractor
   - fitting: _not stated_
   - validation: _not stated_
3. **Differential number counts**: xi(S)=(1-fc)/(C Aeff), summed in bins of dlogS=0.2, scaled to 1; Poisson errors  
  > "we calculate a sum of the contributions, $n(S) = \sum \xi(S) / \Delta \log S$ in each logarithmic flux density bin" (4.1)
   - assumption: Modified blackbody beta=1.5, Td=35 K at z=2.5 for flux/SFR scaling  
  > "spectral index of $\beta_{\rm d} = 1.5$ and dust temperature of $T_{\rm d} = 35$ K" (1)
   - fitting: _not stated_
   - validation: Compared with Hatsukade+2013, Knudsen+2008, models  
  > "are broadly consistent with our results within the $1 \sigma$ uncertainties." (4.2)
4. **Fit Schechter and double power law; integrate EBL**: chi2 minimization to counts (this work, Hatsukade, Hodge/Karim), integrate S*phi  
  > "we search for the best-fitting set of ($\phi_\ast$, $S_\ast$, $\alpha$) that minimizes $\chi^2$." (4.3)
   - fitting: chi2 minimization  
  > "Varying the four parameters, we search for the best-fitting DPL function that minimizes $\chi^2$." (4.3)
   - validation: _not stated_
5. **Galaxy bias via counts-in-cells**: b_g^2 ≈ (sigma_N^2 - Nbar)/(Nbar^2 sigma_V^2) from field-to-field scatter; halo mass from Sheth-Tormen bias  
  > "From the field-to-field scatter in their number counts, we estimate the galaxy bias of the faint SMGs." (5)
   - parameter: flux limit 0.25 mJy with factor-2 flux uncertainty  
  > "If we take a flux density limit of $0.25$ mJy with an uncertainty of a factor of two in flux density measurements" (5)
   - assumption: Redshift distribution of Chapman+2005 (mean z~2.5); one-to-one galaxy-halo  
  > "its mean is $\mbox{$\left\langle z \right\rangle$} \simeq 2.5$." (5)
   - fitting: _not stated_
   - validation: _not stated_
6. **Blind line search and interpretation of SLE-1**: 100 km/s binned cube of Map 1 SPW; negative-source check; compare expected 1.2 mm continuum from line-derived LIR to upper limit; SED templates and multiwavelength limits  
  > "We create a data cube with $\Delta v =$ $100$ km s$^{-1}$ binning, to search for serendipitous emission lines within the primary beam." (6)
   - assumption: M82 CO ladder; Iono+2009 L'CO-LIR relation; Td=35 K, beta=1.5  
  > "we obtain CO(3–2) line fluxes in units of Jy km s$^{-1}$ by adopting the CO excitation ladder found in M82" (6)
   - fitting: _not stated_
   - validation: Negative sources SNR; multi-binning check  
  > "we also conduct blind line emitter searches in data cubes with smaller binnings, $\Delta v = 50$ and $20$ km s$^{-1}$" (6)

## Software

- **CASA** : Data reduction  
  > "The data were reduced with the Common Astronomy Software Applications (cite: mcmullin2007) package in a standard manner." (2.1 Our Data)
- **SExtractor** 2.5: Source extraction  
  > "Source extractions are conducted on the ALMA maps before primary beam correction with SExtractor version 2.5" (3.1 Source Extraction)
- **cloudy** : Line emissivity model of [OIII]88 (Inoue+2014)  
  > "with the photoionization code cloudy (cite: ferland2013)" (6)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of faint SMGs detected (SNR>4) | 11 | not stated | sources | 1 | In the $10$ ALMA maps, we detect eleven SMGs with SNRs of $4.1-6.1$. |
| Differential count at 0.13 mJy | log n = 4.83 | +0.37/-0.45 | deg^-2 per dlogS | 3 | $0.13$ / $4.83^{+0.37}_{-0.45}$ |
| Integrated flux density down to 0.1 mJy | ≃ 11 | not stated | Jy deg^-2 | 4 | The integrated flux density down to the survey limit, $S_{\rm limit} = 0.1$ mJy, is calculated to be $\simeq 11$ Jy deg$^{-2}$ |
| Schechter S* | 2.3 | +2.3/-0.9 | mJy | 4 | Schechter / $2.3^{+2.3}_{-0.9}$ / $9.0^{+20.2}_{-7.3}$ / $-2.4^{+0.3}_{-0.3}$ |
| Galaxy bias of faint SMGs | < 4 | 1 sigma upper limit | dimensionless | 5 | we obtain an $1\sigma$ upper limit of the galaxy bias of $b_{\rm g} < 4$. |
| Dark halo mass of faint SMGs | ≲ 7e12 | not stated | Msun | 5 | we estimate the dark halo mass of the faint SMGs to be roughly $\lesssim 7 \times 10^{12} M_\odot$. |
| SLE-1 line flux | (1.36 ± 0.19)e-1 | 0.19e-1 | Jy km/s | 6 | The flux of the detected line is calculated to be $(1.36 \pm 0.19) \times 10^{-1}$ Jy km s$^{-1}$ |
| SLE-1 3 sigma 1.2 mm continuum upper limit | 64 | not stated | uJy | 6 | The $3 \sigma$ upper limit on the $1.2$ mm continuum flux density of SLE–1 is estimated to be $64$ $\mu$Jy. |

## Qualitative findings

- Faint SMGs (0.1-1 mJy) contribute nearly half of the 1.2 mm EBL; the rest from <0.1 mJy sources  
  > "contribute nearly a half of the extragalactic background light (EBL)" (abstract)

## Claim tuples

- H: Do sub-mJy 1.2 mm number counts keep rising to 0.1 mJy? | E: Counts from 10 ALMA fields combined with bright ALMA counts | R: Counts increase to 0.1 mJy with shallower slope than bright end | F: Faint SMGs contribute ~half the EBL | **supported**
- H: Are faint SMGs less clustered than bright SMGs? | E: Counts-in-cells across 10 fields | R: b_g < 4, Mh ≲ 7e12 Msun | F: Faint SMG halos are less massive, consistent with sBzKs/LBGs/LAEs | **partially**
- H: What is the nature of the continuum-less line emitter SLE-1? | E: Line search plus multiwavelength upper-limit/SED tests | R: CO and [CI](2-1), H2O, [OI] excluded | F: [CII] at z=6.60 or [OIII] at z=12.6 if real | **partially**

## Reasoning

- Why this data: Multiple independent fields reduce cosmic variance  
  > "10$ independent fields that reduce cosmic variance effects" (abstract)
- Why this method: _not stated_
- Alternative: Two extra SNR>4 sources in Map 9 removed as possible side-lobes of bright quasar  
  > "Thus, we remove the two sources from our sample." (3.1 Source Extraction)
- How they decided it was enough: _not stated_
- Limitation (authors): Small number of fields and unknown redshift distribution of faint SMGs give large bias uncertainties; SLE-1 could be systematic noise  
  > "Since the number of the pencil-beam survey fields is small, our estimates on galaxy biases have relatively large uncertainties." (5)
- Caveat (inferred, ours): Only 11 sources; Poisson errors dominate
- Caveat (inferred, ours): Archival fields are quasar fields, possible bias
- Caveat (inferred, ours): SLE-1 significance relies on non-uniform noise
- Caveat (inferred, ours): Bias depends on assumed redshift distribution of bright SMGs

## Reproducibility

- Data public (paper): Archival data public in ALMA archive; Map 2 data newly obtained  
  > "archival ALMA data that have been already public on the ALMA science archive." (2.2 Archival Data)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Map 2 reduction details
- Missing: Mapping of project codes to maps
- Missing: Fit uncertainty procedure
- Data volume (inferred): ~100-300 GB raw for 10 datasets
- Score (inferred): 3/5, Public data and clear counting recipe, but imaging parameters missing and some data unpublished.
- Rediscovery candidate: yes, Public data, numeric counts, but imaging details are partly missing.

## Links

- Method: (cite: hatsukade2013) (Number count method followed)
- Companion: (cite: ouchi2013) (Himiko ALMA data origin)
- Related: ALMA Cycle 0/1 quasar-field observations
- Related: LESS ALMA follow-up (Hodge+2013, Karim+2013)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 47,
  "rate": 0.54
 },
 "evidence_ok": true
}
```
