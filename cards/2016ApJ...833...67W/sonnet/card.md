# ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Survey Description

`2016ApJ...833...67W` | The Astrophysical Journal 2016 | first author: Walter, Fabian | arXiv: 1607.06768 | DOI: 10.3847/1538-4357/833/1/67

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Obtain an unbiased census of molecular gas (CO, [CII]) and dust continuum emission in high-redshift galaxies via full band 3 and band 6 frequency scans of the Hubble Ultra Deep Field, and characterize the line candidates.  
  > "Our overarching goal is to obtain an unbiased census of molecular gas and dust continuum emission in high–redshift (z$>$0.5) galaxies." (abstract)
- Target **Hubble Ultra Deep Field (XDF region)**: coordinates RA=03:32:37.90 Dec=-27:46:25.0 (J2000.0)  
  > "The 3mm scan consisted of a single pointing (RA=03:32:37.90 Dec=–27:46:25.0, J2000.0) and 5 frequency settings" (4 Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00146.S, 2013.1.00718.S
- bands: Band 3 (84-115 GHz) and Band 6 (212-272 GHz)  
  > "full frequency scans in band 3 (84–115 GHz) and band 6 (212–272 GHz)" (abstract)
- frequencies and spectral setup: Band 3: 5 settings, 4x1.875 GHz spectral windows each, native channel 3.9025 MHz; Band 6: 8 settings per pointing, continuous 212-272 GHz  
  > "Each setting had $4\times1.875$ GHz spectral windows (two in the upper side band, and two in the lower side band), and was observed in three execution blocks." (2.4 Observations); "For each pointing position, eight frequency settings were needed to cover the entire band" (2.4 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array, C34-2 (band 3) and C34-1 (band 6)  
  > "Our observations were taken in the C34-2 and C34-1 configurations, resulting in beam sizes of $3.6''\times 2.1''$ (band 3) and $1.7''\times 0.9''$ (band 6)" (2.3 Choice of Array Configuration)
- configurations: _not stated_
- baselines: Band 3: 12-612 m; Band 6: 12-350 kλ  
  > "with 29–41 antennas, with baselines ranging between 12 and 612 m." (2.4 Observations); "Baselines ranged between 12 and 350 k$\lambda$." (2.4 Observations)
- angular resolution: Band 3: 3.5''x2.0'' PA=84 deg; Band 6: 1.5''x1.0'' PA=-79 deg  
  > "The restored synthesized beam size is $3.5''\times 2.0''$ (FWHM) with PA=84$^\circ$." (2.4 Observations); "yielding a synthesized beam of $1.5''\times 1.0''$ with PA=-79$^\circ$" (2.4 Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 3 rms 0.1-0.25 mJy/beam per 19.5 MHz channel; continuum 3.8 uJy/beam (band 3), 12.7 uJy/beam (band 6)  
  > "reaches an rms of $0.1-0.25$ mJy beam$^{-1}$ per 19.5 MHz channel" (2.4 Observations); "noise levels at their center of 3.8 $\mu$Jy beam$^{-1}$ (band 3) and 12.7 $\mu$Jy beam$^{-1}$ (band 6)" (3.4 Continuum emission)
- time on source: ~40 hours total including overheads, split ~50-50 between bands  
  > "The time allocated for both projects amounts to a total of $\sim$40 hours including overheads (split approximately 50–50 between band 3 and band 6)." (2.4 Observations)
- observing dates: Band 3: 1 Jul 2014-6 Jan 2015; Band 6: 12 Dec 2014-21 Apr 2015  
  > "were carried out between July $1^{\rm st}$, 2014 and January $6^{\rm th}$, 2015." (2.4 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 to 7-6 (ladder) (115.271 GHz (J=1-0), spacing ~115 GHz)
- Line: [CII] 2P3/2-2P1/2 (1900.548 GHz)
- Other facility **HST**: Deep optical/NIR imaging for counterparts and SED fitting  
  > "The $\sim$1$'$ region covered within the UDF was chosen to overlap with the deepest available imaging from *HST*." (abstract)
- External data: UDF photometric catalog used for SED fits and counterpart matching  
  > "by fitting the optical/NIR photometry provided by (cite: coe06), using the MAGPHYS spectral energy fitting code" (4 Comparison with expectations) [from (cite: coe06)]
- External data: Predicted CO and [CII] line counts from MAGPHYS SED modelling of UDF galaxies  
  > "(cite: dacunha13) estimated stellar masses, SFRs, IR luminosities, and expected CO and \[C ii\] fluxes and luminosities" (4 Comparison with expectations) [from (cite: dacunha13)]
- External data: Spectroscopic redshifts from longslit and HST grism  
  > "spectroscopic redshifts are available for the optical/NIR counterparts, either through longslit spectroscopy (cite: lefevre05; kurk13; skelton14; morris15), or *HST* grism observations (cite: morris15; momcheva16)" (3.2.3 Optical/NIR spectroscopic redshifts) [from (cite: lefevre05; kurk13; skelton14; morris15; momcheva16)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Data were calibrated and imaged with the *Common Astronomy Software Applications* package (CASA) version 4.2.2 of the ALMA pipeline." (2.4 Observations)
- casa version: CASA 4.2.2  
  > "Data were calibrated and imaged with the *Common Astronomy Software Applications* package (CASA) version 4.2.2 of the ALMA pipeline." (2.4 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus and quasars J0334-4010, J0334-4008 (band 3); Uranus and J0334-4008 (band 6)  
  > "while Uranus and the quasars J0334–4010 and J0334–4008 were used as flux and bandpass calibrators." (2.4 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We adopted natural weighting, yielding a synthesized beam of $1.5''\times 1.0''$ with PA=-79$^\circ$." (2.4 Observations)
- uv taper: _not stated_
- cell size: 0.5'' (band 3), 0.3'' (band 6)  
  > "We thus adopted a pixel scale of $0.5''$ pixel$^{-1}$, and an image size of $90''\times90''$." (2.4 Observations)
- image size: 90''x90'' (band 3); ~75''x70'' mosaic to half-sensitivity (band 6)  
  > "The final mosaic covers a region of approximately $75''\times 70''$ to the half–sensitivity point." (2.4 Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum map made by collapsing cubes after removing channels with significant line emission  
  > "by collapsing the two data cubes along the frequency axis, after removing the few channels that contain significant line emission." (3.4 Continuum emission)
- line free channels: _not stated_
- primary beam correction: applied for all quantitative analysis  
  > "A primary beam correction has been applied for all quantitative analysis." (2.4 Observations)
- array combination: _not stated_
- smoothing: Band 3 averaged over 2 and 5 channels (7.8, 19.5 MHz); band 6 over 4, 8, 12 channels (15.6, 31.2, 46.8 MHz)  
  > "We imaged the 3mm cube after averaging over two and five native channels (7.8 MHz and 19.5 MHz respectively) using natural weighting." (2.4 Observations)
- final beam: 3.5''x2.0'' (band 3), 1.5''x1.0'' (band 6)  
  > "The restored synthesized beam size is $3.5''\times 2.0''$ (FWHM) with PA=84$^\circ$." (2.4 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Continuum map analysis deferred to Paper II  
  > "are shown in Fig. [6](#fig_continuum) and will be discussed in detail in *Paper II*." (3.4 Continuum emission) [from Paper II (Aravena et al. 2016a)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channels used for continuum maps
- S/N threshold used in findclumps/daofind before fidelity cut
- Cleaning (deconvolution) parameters, thresholds and masks for cubes
- Flux calibration scale uncertainty
- Band 6 CASA/pipeline version
- findclumps code is not released
- Execution block selection/flagging beyond pipeline
- Spectral line fitting method for flux, FWHM and uncertainties

## Analysis recipe

1. **Combine band 3 setups into a cube**: Split ranges per execution block, cvel overlap regions, concat, statwt to homogenize weights, concat all  
  > "We therefore ran statwt in order to homogenize the weighting system in the concatenated data. 5) We combined all the frequency ranges using the task concat again." (2.4 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image cubes and continuum**: Natural-weighted imaging at several channel samplings; primary beam correction  
  > "The cube was imaged in spectral samplings of 4, 8 and 12 native channels, corresponding to $15.6$ MHz, $31.2$ MHz, and $46.8$ MHz respectively, as well as in a continuum image." (2.4 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Blind line search for positive and negative peaks**: findclumps: floating averages over 3,5,7,9-channel windows on 7.8 MHz (3mm) and 31.2 MHz (1mm) cubes, peak finding with daofind, trimmed by primary beam radius, duplicates removed, bright continuum sources masked  
  > "we ran our search over 3, 5, 7, and 9–channel windows, i.e., kernel line widths of $\sim$50–300 km s$^{-1}$" (3.1 The blind line search)
   - software: IRAF daofind, findclumps
   - parameter: Candidates kept within sqrt2 x primary beam radius at 3mm (53'' at 84 GHz, 39'' at 115 GHz) and 30.9'' radius at 1mm  
  > "within a fixed radius of $30.9''$ at 1mm (given that the latter is a mosaic)" (3.1 The blind line search)
   - assumption: Negative candidates are all noise peaks; no absorption expected  
  > "all the ‘negative’ line candidates will be noise peaks, while the ‘positive’ line candidates will be a mixture of noise peaks and genuine lines" (3.1.1 Fidelity)
   - fitting: _not stated_
   - validation: Fidelity from negative vs positive counts; completeness via simulated sources  
  > "We address this by inserting artificial line sources of various strengths and widths in our data cubes, then calculating our ability to recover them in our line search." (Completeness)
4. **Compute fidelity**: fidelity = 1 - N_neg/N_pos; fitted with error function; require fidelity >=60% and >2 sigma in consecutive channels  
  > "For the analysis of our blind search, we request a fidelity level of 60% or higher." (3.1.1 Fidelity)
   - software: findclumps
   - parameter: C_3mm=5.1, C_1mm=5.0, sigma_3mm=0.4, sigma_1mm=0.8  
  > "where $C_{\rm 3mm}$=5.1, $C_{\rm 1mm}$=5.0, $\sigma_{\rm 3mm}$=0.4, $\sigma_{\rm 1mm}$=0.8" (3.1.1 Fidelity)
   - fitting: error-function parameterization of fidelity vs S/N, not physically motivated  
  > "While not physically motivated, the following error function provides a good description of the observed trend, with the following parameterization:" (Fidelity)
   - validation: _not stated_
5. **Measure completeness**: Inject 2500 Gaussian artificial lines with random position, frequency, flux and width; rerun search  
  > "adding 2500 artificial line sources to the data cube, re–running our line searching algorithm, and comparing the number of recovered sources with the input catalog" (3.1.2 Completeness)
   - software: findclumps
   - parameter: Peak flux 0.22-1.00 mJy (3mm), 0.5-2.0 mJy (1mm); widths 50-500 km/s  
  > "The line widths span the range 50–500 km s$^{-1}$." (3.1.2 Completeness)
   - fitting: _not stated_
   - validation: _not stated_
6. **Identify redshifts of candidates**: Use multiple CO lines, spectroscopic redshifts, and optical/NIR counterpart presence (no counterpart implies z>2 at 3mm; J<4 ruled out at 1mm)  
  > "we assume that line candidates selected in band 3 and lacking an optical/NIR counterpart are at $z>2$" (3.2.3 Lack of optical/NIR counterparts)
   - software: MAGPHYS
   - assumption: No significant dust reddening; no CO detectable in galaxies with M* << 1e9 Msun  
  > "we do not expect to detect CO in galaxies with $M_*\ll 10^9$ M$_\odot$" (3.2.3 Lack of optical/NIR counterparts)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare detected line counts with MAGPHYS expectations**: Scale da Cunha et al. predicted line number counts to survey area and compare with observed counts, no completeness/fidelity correction  
  > "For this back–of–the envelope calculation, we do not correct our measurements for completeness or fidelity" (4 Comparison with expectations)
   - software: MAGPHYS
   - assumption: Low (Milky Way) and high (M82) excitation bounds  
  > "the low–excitation case of the global Milky Way disk, and the high–excitation case of the nucleus of the local starburst galaxy M82" (4 Comparison with expectations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: calibration, concat/cvel/statwt, imaging  
  > "Data were calibrated and imaged with the *Common Astronomy Software Applications* package (CASA) version 4.2.2 of the ALMA pipeline." (2.4 Observations)
- **findclumps (IRAF-based)** : blind line search in cubes  
  > "we developed an IRAF–based routine, findclumps, which operates directly on the imaged data cubes." (3.1 The blind line search)
- **daofind (IRAF)** : peak finding  
  > "searches for peaks exceeding a certain S/N threshold using the IRAF task daofind" (3.1 The blind line search)
- **MAGPHYS** : SED fitting for stellar masses and expected line fluxes  
  > "using the MAGPHYS spectral energy fitting code (cite: dacunha08)" (4 Comparison with expectations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 line candidates | 10 | <4 spurious | count | 4 | Our blind search resulted in 10 line candidates from the 3 mm search, and 11 line candidates from the 1 mm search |
| Band 6 line candidates | 11 | <4 spurious | count | 4 | Our blind search resulted in 10 line candidates from the 3 mm search, and 11 line candidates from the 1 mm search |
| 3mm fidelity 60/80/95% S/N | 5.17, 5.34, 5.57 | not stated | dimensionless | 4 | This implies that we reach 60, 80, and 95% fidelity levels at $S/N$=$5.17$, $5.34$, and $5.57$ at 3mm |
| 1mm fidelity 60/80/95% S/N | 5.15, 5.50, 5.97 | not stated | dimensionless | 4 | and at $S/N$=$5.15$, $5.50$, and $5.97$ at 1mm |
| 3mm 50% completeness peak flux | >0.45 for widths >100 | not stated | mJy (km/s for width) | 5 | At 3mm, the completeness is $>50$% for peak flux densities $F_\nu^{\rm line}>0.45$ mJy, and for line widths $\Delta v>100$ km s$^{-1}$. |
| 1mm 50% completeness peak flux | >0.8 for widths >100 | not stated | mJy (km/s for width) | 5 | The line search in the 1mm mosaic shows a completeness $>50$% for peak flux densities $>$0.8 mJy and widths $>100$ km s$^{-1}$. |
| Total CO flux of candidates | 2.55 | not stated | Jy km/s | 6 | The total CO flux of all line candidates is 2.55 Jy km s$^{-1}$ |
| Flux of candidates without counterpart | 0.83 (~33%) | not stated | Jy km/s | 6 | whereas the total flux of the candidates that have no optical/NIR counterpart is 0.83 Jy km s$^{-1}$ |
| Continuum noise band 3 | 3.8 | not stated | uJy/beam | 2 | noise levels at their center of 3.8 $\mu$Jy beam$^{-1}$ (band 3) and 12.7 $\mu$Jy beam$^{-1}$ (band 6) |
| Continuum noise band 6 | 12.7 | not stated | uJy/beam | 2 | noise levels at their center of 3.8 $\mu$Jy beam$^{-1}$ (band 3) and 12.7 $\mu$Jy beam$^{-1}$ (band 6) |

## Qualitative findings

- Observed CO line counts broadly agree with MAGPHYS-based expectations, with possible excess in highest 1mm flux bin  
  > "Overall, we conclude that within the large uncertainties, there is reasonable agreement between the observations and previous expectations." (4 Comparison with expectations)

## Claim tuples

- H: Do blind scans yield statistically reliable CO line candidates? | E: Positive vs negative peak search with fidelity cut at 60% | R: 10 (3mm) and 11 (1mm) candidates, <4 spurious per band | F: Candidate lists are reliable enough for statistical use | **supported**
- H: Do many CO sources lack optical/NIR counterparts (dark galaxies)? | E: Cross-match line candidates with HST/NIR catalogs and sum fluxes | R: ~33% of total flux in candidates without counterpart | F: Counterpart-less sources contribute a small fraction, likely less after removing spurious | **supported**
- H: Are observed line counts consistent with SED-based predictions? | E: Compare counts to scaled da Cunha et al. 2013 predictions | R: Reasonable agreement, excess in highest 1mm bin | F: Agreement within large uncertainties | **supported**

## Reasoning

- Why this data: Band 3 gives lowest CO transitions; band 6 completes redshift coverage and [CII] at 6<z<8; UDF has deepest multiwavelength data  
  > "With ALMA, the lowest frequencies are accessible in band 3, which therefore is the primary band of choice." (2.1 Choice of Frequencies)
- Why this method: Compact configurations chosen so extended CO emission is not resolved out per beam  
  > "observations in a compact array configuration are essential to ensure that no extended CO emission is missed by the interferometer" (2.3 Choice of Array Configuration)
- Alternative: Band 7 rejected: only high-J transitions, smaller field of view, more than 13 tunings  
  > "For all of these reasons, band 6 is preferred over band 7 to complement the band 3 observations." (2.1 Choice of Frequencies)
- How they decided it was enough: _not stated_
- Limitation (authors): Survey area small, limited by ALMA early-science time  
  > "The current size of the survey is admittedly small, limited by the amount of time available in ALMA ‘early science’." (5 Summary)
- Caveat (inferred, ours): Fidelity assumes negative peaks mirror positive noise peaks, which may not hold for non-Gaussian interferometric noise
- Caveat (inferred, ours): Search assumes spatially unresolved lines
- Caveat (inferred, ours): Redshift assignments rely on counterpart absence and are partly ambiguous
- Caveat (inferred, ours): Small number statistics for counts comparison

## Reproducibility

- Data public (paper): Project codes given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: 2013.1.00146.S and 2013.1.00718.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: findclumps source code and S/N thresholds
- Missing: Cleaning parameters
- Missing: Line-free channel selection for continuum
- Missing: Line fit procedure for catalog fluxes
- Data volume (inferred): Large: 13 frequency tunings, multi-execution blocks, ~40 h; likely several hundred GB raw
- Score (inferred): 3/5, Data and general recipe given, but the custom search code and key thresholds are unreleased
- Rediscovery candidate: no, Custom findclumps code and clean parameters not provided; reproduction would approximate the catalog only.

## Links

- Companion: Aravena et al. 2016a (Paper II) (continuum analysis)
- Companion: Decarli et al. 2016a (Paper III) (CO luminosity functions, uses completeness corrections)
- Companion: Decarli et al. 2016b (Paper IV) (properties of CO-bright galaxies)
- Companion: Aravena et al. 2016b (Paper V) ([CII] emitters)
- Companion: Bouwens et al. 2016 (Paper VI) (IRX-beta relations)
- Companion: Carilli et al. 2016 (Paper VII) (intensity mapping)
- Related: ASPECS
- Related: HST UDF/XDF
- Related: PdBI spectral scan of Hubble Deep Field North

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 50,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
