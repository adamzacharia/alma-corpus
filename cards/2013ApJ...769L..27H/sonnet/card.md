# Faint End of 1.3 mm Number Counts Revealed by ALMA

`2013ApJ...769L..27H` | The Astrophysical Journal Letters 2013 | first author: Hatsukade, Bunyo | arXiv: 1304.6437 | DOI: 10.1088/2041-8205/769/2/L27

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the faint end (sub-mJy) of the 1.3 mm number counts, and how much of the extragalactic background light is resolved into sources?  
  > "In this letter, we present the faint end of number counts at 1.3 mm revealed by ALMA band 6 observations." (Introduction)
- Target **20 star-forming galaxies at z~1.4 in the SXDS field (serendipitous sources in their maps)**: coordinates _not stated_; z/distance z ~ 1.4  
  > "We conducted ALMA band 6 observations toward 20 star-forming galaxies at $z \sim 1.4$ in the Subaru XMM/Newton Deep Survey (SXDS) field" (Observations and Data Reduction); distance from NIR spectroscopy with FMOS on Subaru  
  > "We conducted ALMA band 6 observations toward 20 star-forming galaxies at $z \sim 1.4$ in the Subaru XMM/Newton Deep Survey (SXDS) field" (Observations and Data Reduction)

## Data provenance

- ALMA projects: 2011.0.00648.S
- bands: Band 6 (1.3 mm, 238 GHz)  
  > "We present the faint end of number counts at 1.3 mm (238 GHz) obtained with the Atacama Large Millimeter/submillimeter Array (ALMA)." (abstract)
- frequencies and spectral setup: Four groups with LO 231.198, 236.168, 240.380, 244.166 GHz; 3-4 spectral windows of 1875 MHz each  
  > "The local oscillator frequencies for the four groups were 231.198 GHz, 236.168 GHz, 240.380 GHz, and 244.166 GHz (typical frequency of 238 GHz)." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, 23-25 antennas, Cycle 0  
  > "with 23–25 antennas in the extended configuration during the ALMA Cycle 0 session" (Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 8-15 minutes per pointing  
  > "each with on-source observing time of 8–15 minutes" (Observations and Data Reduction)
- observing dates: August 9, 11, 15, 26, 2012  
  > "The observations were carried out in August 9th, 11th, 15th, and 26th, 2012" (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO 5-4 (not stated)
- Other facility **Subaru/FMOS**: NIR spectroscopic redshifts of targets  
  > "whose redshifts were obtained by near-infrared (NIR) spectroscopy with the Fibre Multi-Object Spectro-graph (cite: kimu10) on the Subaru telescope" (Observations and Data Reduction)
- External data: Literature number counts (SCUBA 850um, LABOCA 870um, AzTEC 1.1mm, ALMA 870um) for comparison  
  > "we plot number counts obtained by SCUBA 850 $\mu$m (cite: knud08), LABOCA 870 $\mu$m (cite: joha11), AzTEC 1.1 mm (cite: scot12)" (Comparisons with Previous Results) [from knud08; joha11; scot12; kari13]
- External data: EBL at 1.3 mm of 14-18 Jy deg^-2 from COBE  
  > "The EBL at 1.3 mm based on the measurements by the *Cosmic Background Explorer* satellite is 14–18 Jy deg$^{-2}$ (cite: puge96; fixs98)." (Contribution to the Extragalactic Background Light) [from puge96; fixs98]
- Simulation/model as data: Model counts from shim12, beth12, dacu13 compared with ALMA counts  
  > "We compare the 1.3 mm counts with recent model predictions with different approaches by (cite: shim12), (cite: beth12), and (cite: dacu13)." (Comparisons with Model Predictions)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Callisto, Uranus  
  > "Ganymede, Callisto, and Uranus were observed as a flux calibrator." (Observations and Data Reduction)
- flux scale uncertainty: _not stated_
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
- primary beam correction: Source extraction in maps uncorrected for primary beam; flux corrected afterwards; primary beam FWHM 26"  
  > "Because the source extraction is conducted in the maps uncorrected for primary beam attenuation" (Completeness)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Flux scaling to 1.3 mm uses modified blackbody with beta=1.5, T=35 K at z=2.5  
  > "spectral index of $\beta = 1.5$ and dust temperature of 35 K (cite: kova06; copp08) located at $z = 2.5$ (cite: chap05; yun12)" (Comparisons with Previous Results) [from kova06; copp08; chap05; yun12]

### Not stated but needed to reproduce (our reading)

- CASA version and reduction procedure (done with ARC staff)
- Imaging parameters: weighting, cell size, image size, deconvolution, continuum channels
- Source-finding algorithm and how spurious detection rate was derived
- Synthesized beam and rms per map
- Phase calibrator/flux-scale uncertainty

## Analysis recipe

1. **Extract serendipitous sources**: Detect sources at >=3.8 sigma in 20 maps uncorrected for primary beam, excluding targets  
  > "We detect 15 sources (excluding the target sources) in the 20 maps with the raw flux density (uncorrected for the primary beam attenuation)" (Source and Spurious Detection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Completeness and flux boosting simulation**: Subtract >=3.5 sigma sources, inject flux-scaled synthesized beam at random positions, recover within 1.0" at >=3.8 sigma; 1000 repeats per source  
  > "We repeat this 1000 times for the raw flux density of each source." (Completeness)
   - fitting: _not stated_
   - validation: _not stated_
3. **Effective area**: Per map, find radius within which source is detected at >=3.8 sigma given PB-corrected rms  
  > "we find a distance from the map center within which the source is detected at $\ge$$3.8 \sigma$ in the raw map uncorrected for primary beam attenuation" (Effective Area)
   - fitting: _not stated_
   - validation: _not stated_
4. **Cumulative number counts**: Weight each source by (1 - C_spurious)/completeness/effective area; Poisson errors at 84.13% confidence  
  > "The upper and lower errors are calculated for each source from Poisson confidence limits of 84.13%, which correspond to $1 \sigma$ for Gaussian statistics (cite: gehr86)" (Number Counts)
   - fitting: _not stated_
   - validation: Compared counts from 4.0 sigma subsample; consistent  
  > "We also plot the number counts created by using 6 $\ge$$4.0 \sigma$ sources to see the effect of the detection threshold." (Number Counts)
5. **EBL fraction resolved**: Sum corrected flux of >=3.8 sigma sources and divide by COBE EBL  
  > "Therefore, we have resolved $\sim$80% of the EBL into discrete sources" (Contribution to the Extragalactic Background Light)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of serendipitous sources (>=3.8 sigma) | 15 | not stated | sources | 1 | we serendipitously detect 15 sources ($\ge$$3.8 \sigma$, $S_{\rm 1.3\ mm} = 0.15$–0.61 mJy) |
| Completeness range | 77%–100% | not stated | percent | 2 | The completeness for the 15 sources ranges from 77% to 100%. |
| Flux ratio input/output | 1.00–1.14 | not stated | dimensionless | 2 | The flux ratio calculated for each source in this simulation is 1.00–1.14. |
| Total flux density of sources | ~13 | not stated | Jy deg^-2 | 5 | is $\sim$13 Jy deg$^{-2}$ |
| EBL fraction resolved | ~80% | not stated | percent | 5 | we have resolved $\sim$80% of the EBL into discrete sources |
| N(>S) at 0.59 mJy | 2.10e3 (+4.57/-1.64e3) | +4.57/-1.64 | deg^-2 | 4 | 0.59  /        2         /   $2.10^{+4.57}_{-1.64}$ |

## Qualitative findings

- Counts consistent with flux-scaled 850/870 um lensing-cluster counts and with three models; no turnover seen at faint end  
  > "However, our data points at fainter flux range do not show such turnover." (Comparisons with Previous Results)

## Claim tuples

- H: Sub-mJy 1.3 mm counts match lensing-cluster counts at submm | E: Compare flux-scaled counts | R: Consistent | F: Both wavelengths trace the same faint population | **supported**
- H: Sub-mJy sources are normal star-forming galaxies rather than classical SMGs | E: Compare counts with models | R: Models agree well | F: Sources more like normal star-forming galaxies | **supported**
- H: Faint sources resolve much of the EBL | E: Sum corrected fluxes vs COBE EBL | R: ~13 Jy/deg2 of 14-18 | F: ~80% resolved | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Counts from targeted fields may show excess; comparison with 870 um counts not quantitative  
  > "We note that number counts derived from targeted observations may show an excess of source counts." (Comparisons with Previous Results)
- Caveat (inferred, ours): Only 15 sources, large Poisson errors
- Caveat (inferred, ours): Fields targeted at z~1.4 galaxies may bias counts via clustering
- Caveat (inferred, ours): Some sources may be line-dominated
- Caveat (inferred, ours): Flux scaling from 850/870 um assumes single SED

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00648.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Source finder and spurious-rate procedure
- Missing: Source positions/flux table
- Data volume (inferred): ~20-50 GB (Cycle 0, 20 short pointings)
- Score (inferred): 4/5, Simple recipe and public-era Cycle 0 data, but imaging and spurious-rate details missing.
- Rediscovery candidate: yes, Single known project, simple numeric counts, though imaging details are missing.

## Links

- Companion: yabe12; yabe13 (Source of the target sample)
- Related: Subaru/XMM-Newton Deep Survey (SXDS)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
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
  "facts": 65,
  "stated": 24,
  "rate": 0.369
 },
 "evidence_ok": true
}
```
