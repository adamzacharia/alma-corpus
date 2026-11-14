# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Search for [CII] Line and Dust Emission in 6

`2016ApJ...833...71A` | The Astrophysical Journal 2016 | first author: Aravena, M. | arXiv: 1607.06772 | DOI: 10.3847/1538-4357/833/1/71

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Can [CII] line and dust continuum emission be detected from z>6 optical dropout galaxies in the ALMA 1-mm spectral scan of the HUDF, and what do they imply for the L[CII]-SFR relation and the [CII] luminosity function at 6<z<8?  
  > "We identify fourteen [CII] line emitting candidates in this redshift range with significances $>$4.5 $\sigma$, two of which correspond to blind detections with no optical counterparts." (abstract)
- Target **Hubble Ultra Deep Field (ASPECS ~1 arcmin^2 region), 58 optical dropout galaxies at z_phot=5.5-8.5**: coordinates Source positions in Table 1 (e.g. ID02 3:32:39.39 -27:46:11.1)  
  > "we use a sample of 58 $z>5.5$ optical dropout galaxies that were located within the 1 arcmin$^2$ region covered by our 1-mm mosaic in the *Hubble* UDF." (2.3 Multi-wavelength ancillary data); z/distance z_phot 5.5-8.5; [CII] candidates at z~6.0-7.9  
  > "we use a sample of 58 $z>5.5$ optical dropout galaxies that were located within the 1 arcmin$^2$ region covered by our 1-mm mosaic in the *Hubble* UDF." (2.3 Multi-wavelength ancillary data); distance from EAZY photometric redshifts; [CII] line redshift  
  > "we use a sample of 58 $z>5.5$ optical dropout galaxies that were located within the 1 arcmin$^2$ region covered by our 1-mm mosaic in the *Hubble* UDF." (2.3 Multi-wavelength ancillary data)

## Data provenance

- ALMA projects: 2013.1.00146.S, 2013.1.00718.S
- bands: Band 3 (single pointing) and Band 6 (7-point mosaic)  
  > "Observations were performed in a single pointing in band 3, and using a 7-point mosaic in band 6" (2.1 ALMA UDF survey overview)
- frequencies and spectral setup: Band 6: 212.0-272.0 GHz with 8 tunings; Band 3: 84.2-114.9 GHz with 5 tunings  
  > "We scanned the band 6 using eight frequency tunings, covering the frequency range $212.0-272.0$ GHz." (2.2 ALMA data and reduction); "using 5 frequency tunings to cover the frequency range $84.2-114.9$ GHz" (2.2 ALMA data and reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-2 (band 3) and C34-1 (band 6)  
  > "Observations in bands 3 and 6 were taken with ALMA’s compact array configurations, C34-2 and C34-1, respectively." (2.2 ALMA data and reduction)
- baselines: _not stated_
- angular resolution: 3.5''x2.0'' (band 3) and 1.5''x1.0'' (band 6)  
  > "resulting in synthesized beam sizes of $3.5''\times2.0''$ and $1.5''\times1.0''$ from the low to high frequency ends of bands 3 and 6, respectively." (2.2 ALMA data and reduction)
- max recoverable scale: _not stated_
- sensitivity: average rms 0.53 mJy/beam per 31.25 MHz channel in 1-mm cube; continuum 12.7 uJy in central region  
  > "We find an average rms of 0.53 mJy beam$^{-1}$ in the 1-mm cube at 31.25 MHz channel$^{-1}$ resolution (no PB corrected)." (2.2 ALMA data and reduction); "reaching down to 12.7 $\mu$Jy in the central regions of the mosaic" (3.6 Continuum emission: Individual sources and stack)
- time on source: _not stated_
- observing dates: Band 6: Dec 12, 2014 to Apr 21, 2015; Band 3: Jul 1, 2014 to Jan 5, 2015  
  > "observations were conducted between December 12, 2014 to April 21, 2015 under good weather conditions" (2.2 ALMA data and reduction)
- pi or archival as stated: Cycle-2 projects, PIs F. Walter and M. Aravena  
  > "projects 2013.1.00146.S (PI: F. Walter) and 2013.1.00718.S (PI: M. Aravena)" (2.2 ALMA data and reduction)
- Line: [CII] 158 um (not stated)
- Line: CO J=6-5, 7-6, 8-7 (not stated)
- Other facility **HST (ACS, WFC3, HUDF09/12, CANDELS)**: Dropout galaxy catalogs and photometry for photo-z  
  > "This includes all available *HST* Advanced Camera for Surveys (ACS) optical and Wide Field Camera 3 (WFC3) IR data from the HUDF09, HUDF12 and from the Cosmic Assembly Near-infrared Deep Extragalactic Legacy Survey (CANDELS) programs." (2.3 Multi-wavelength ancillary data)
- Other facility **VLT/MUSE**: Optical IFU spectroscopy 4650-9200 A to check Ly-alpha and interlopers  
  > "comprising the wavelength range between 4650-9200 Å." (2.3 Multi-wavelength ancillary data)
- External data: Dropout galaxy catalogs with photometric redshifts 5.5-8.5  
  > "we use the most complete catalog of galaxies selected to have photometric redshifts in the range $5.5-8.5$ compiled by (cite: schenker13), (cite: mclure13) and (cite: bouwens15)." (2.3 Multi-wavelength ancillary data) [from (cite: schenker13); (cite: mclure13); (cite: bouwens15)]
- External data: Local L[CII]-SFR relation, high-z [CII] detections and [CII] luminosity function comparisons  
  > "We compare our measurements with the recent constraints obtained by (cite: swinbank14) based on the serendipitous detection of two [CII] line emitters at $z=4.4$." (4.2 Constraints on luminosity function) [from (cite: swinbank14); (cite: delooze14); (cite: popping16)]
- External data: MUSE UDF spectroscopy  
  > "deep Multi Unit Spectroscopic Explorer (MUSE) integrations taken with the Very Large Telescope (VLT) as part of the Guaranteed Time Observations (GTO) on the *Hubble* UDF (Bacon et al., in preparation)" (2.3 Multi-wavelength ancillary data) [from Bacon et al., in preparation]

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

- task: CASA CLEAN used to make dirty cube (no clean deconvolution)  
  > "we used a data cube that had been de-convolved using a natural weighting scheme, without primary beam correction using the CASA task `CLEAN`." (3.1 Line search procedure)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using a natural weighting scheme, without primary beam correction" (3.1 Line search procedure)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: not subtracted for line search  
  > "We do not subtract the continuum, as this requires a specific frequency range to subtract on" (3.1 Line search procedure)
- line free channels: _not stated_
- primary beam correction: not applied for search; applied for later quantitative analysis  
  > "Primary beam correction is later on taken into account for all subsequent quantitative analysis." (3.1 Line search procedure)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Survey setup and data reduction  
  > "The survey setup and data reduction steps are described in detail in (cite: walter16)." (2.2 ALMA data and reduction) [from (cite: walter16) Paper I]
- Completeness simulation procedure for fake sources  
  > "We use the same procedure as in Walter et al. (2016; Paper I) to insert sources, and we refer the reader to this paper for details." (3.2 Purity and completeness) [from Walter et al. (2016; Paper I)]
- Continuum map  
  > "reaching down to 12.7 $\mu$Jy in the central regions of the mosaic (cite: aravena16b)" (3.6 Continuum emission: Individual sources and stack) [from (cite: aravena16b)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version and flux calibrators
- Exact cell size, image size and channelization of the dirty cube
- Mosaic combination details and primary-beam model
- Which continuum channels/mask used for collapsed continuum map and stacking cutout size
- Conversion from UV to SFR (UV SFR calibration) not given
- Details of the source selection in SERCH (pixel/beam handling)

## Analysis recipe

1. **Blind line search in dirty 1-mm cube**: Convolve cube along frequency with Gaussian kernels with AIPS SERCH, identify peaks with CLUMPFIND, S/N>3.5  
  > "We performed a line search using the Astronomical Image Processing System (AIPS) task `SERCH`." (3.1 Line search procedure)
   - software: AIPS SERCH, CLUMPFIND, CASA
   - parameter: Gaussian kernels 180-500 km/s; S/N>3.5  
  > "we used a set of different Gaussian kernels, from 180 to 500 km s$^{-1}$" (3.1 Line search procedure)
   - fitting: _not stated_
   - validation: Compared with independent search in Paper I; similar fidelity and completeness  
  > "Both searches were performed to provide independent checks on the reliability of our algorithms" (3.1 Line search procedure)
2. **Fidelity and completeness**: Fidelity P=1-Nneg/Npos from negative peaks; completeness from 200 injected fake lines  
  > "We check the *completeness* level of our sample by inserting 200 fake sources into the 1-mm data cube." (3.2 Purity and completeness)
   - parameter: thresholds: S/N=5.3 (70% fidelity) for blind; S/N=4.5 (40%) for optical-matched within 1''  
  > "we set a threshold at the 70% fidelity level or S/N$=5.3$ for considering a *blind* candidate line detection" (3.2 Purity and completeness)
   - fitting: _not stated_
   - validation: Negative peaks as contamination measure  
  > "We quantify the *fidelity* level of our sample based on the number of negative peaks in our 1-mm cube, using the same line search procedure." (Purity and completeness)
3. **Select candidates and measure line properties**: Blind selection plus cross-match to dropouts within 1''; single Gaussian fit to spectra; moment-0 map 2D Gaussian  
  > "For each spectrum we fit a single Gaussian to the candidate line emission, thereby deriving an integrated intensity ($I_{\rm [CII]}$) and line full width at half maximum (FWHM)." (3.3 Blind [CII] line candidates)
   - fitting: single Gaussian per spectrum  
  > "For each spectrum we fit a single Gaussian to the candidate line emission, thereby deriving an integrated intensity ($I_{\rm [CII]}$) and line full width at half maximum (FWHM)." (Blind [CII] line candidates)
   - validation: Checked against MUSE spectra, 3-mm CO lines, photo-z probability distributions, SPW edges and atmospheric lines  
  > "We have thus used two important sources of information to reject other redshift possibilities and assess the reality of our \[CII\] line candidates, as described below." (Other redshift possibilities)
4. **Photometric redshifts**: EAZY with EAZY_v1.0 plus GALEV templates, flat prior  
  > "A flat redshift prior is assumed." (2.4 Photometric redshifts)
   - software: EAZY
   - fitting: chi-square fitting  
  > "computed based using the best-fit chi-square at a given redshift derived from the full set of *HST* optical and NIR photometry for a source using the `EAZY` photometric redshift code" (Photometric redshifts)
   - validation: _not stated_
5. **Continuum stacking and IR SFR**: Weighted average of cutouts at candidate or dropout positions; modified blackbody to derive LFIR and SFR  
  > "we compute a weighted average of the individual cutout images, using the sensitivity pattern of the mosaic as weight." (3.6 Continuum emission: Individual sources and stack)
   - parameter: Td=50 K, beta=1.8, kappa0=0.4 cm^2/g at 250 GHz, optically thick at 100 um  
  > "We assume a typical dust temperature $T_{\rm d}=50$ K at $z\sim6-8$" (3.6 Continuum emission: Individual sources and stack)
   - assumption: Chabrier IMF; CMB contrast included  
  > "For a (cite: chabrier03) initial mass function, this translates into an average IR-derived SFR of $3\pm1$ $M_\ensuremath{\odot}$ yr$^{-1}$." (3.6 Continuum emission: Individual sources and stack)
   - fitting: _not stated_
   - validation: Td=25 K alternative gives factor 2.5-3 lower  
  > "Assuming lower dust temperatures in our calculations, $T_{\rm d}=25$ K, yield FIR luminosity and SFR$_{\rm IR}$ estimates a factor $(2.5-3.0)$ lower." (Continuum emission: Individual sources and stack)
6. **L[CII]-SFR and luminosity function**: Compare with local relations; count candidates in 4678 Mpc^3 corrected for purity and completeness  
  > "For the $\sim$1 arcmin$^2$ area of the sky covered by our survey this volume corresponds to 4678 Mpc$^3$." (4.2 Constraints on luminosity function)
   - assumption: Factor 2 correction to UV SFR to get total SFR  
  > "we simply apply a factor of 2 correction to each individual UV–derived SFR value in our sample." (4.1 L[CII] vs SFR)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN task to make dirty cube  
  > "using the CASA task `CLEAN`" (3.1 Line search procedure)
- **AIPS SERCH** : line search  
  > "We performed a line search using the Astronomical Image Processing System (AIPS) task `SERCH`." (3.1 Line search procedure)
- **CLUMPFIND (IDL)** : isolating line peaks  
  > "we used the IDL routine `CLUMPFIND` (cite: williams11) to isolate individual line peaks" (3.1 Line search procedure)
- **EAZY** EAZY_v1.0 templates: photometric redshifts  
  > "using the `EAZY` photometric redshift code (cite: brammer08)" (2.4 Photometric redshifts)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of [CII] candidates | 14 (2 blind, 12 optically matched) | not stated | dimensionless | 3 | We find a total of 14 [CII] line candidates, two of which are blindly detected |
| Positive vs negative line peaks | 2875 vs 2771 | not stated | dimensionless | 2 | We find 2875 positive versus 2771 negative line peaks identified within the HPBW or PB of our data |
| Stacked 1.2 mm flux of [CII] candidates | 14 | 5 | uJy | 5 | yields a tentative detection at the $\sim3\sigma$ level with a measured peak flux density of $14\pm5\,\mu$Jy |
| Stacked dropouts 3sigma upper limit | 6 | not stated | uJy | 5 | No detection is found in the stack of the optical dropout galaxies yielding a $3\sigma$ upper limit of 6$\mu$Jy at 1.2-mm. |
| LFIR of stack (40-500 um) | 2.7e10 | 0.9e10 | Lsun | 5 | $L_{\rm FIR}=(2.7\pm0.9)\times10^{10}\ L_\ensuremath{\odot}$ |
| IR-derived SFR of stack | 3 | 1 | Msun/yr | 5 | average IR-derived SFR of $3\pm1$ $M_\ensuremath{\odot}$ yr$^{-1}$ |
| 3sigma [CII] luminosity limit | (1.6-2.5)e8 | not stated | Lsun | 1 | the $3\sigma$ detection limit for the [CII] luminosity varies between $L_{\rm [CII]}=(1.6-2.5)\times10^8\ L_\ensuremath{\odot}$ |
| IDX25 redshift | 6.3568 (CO(6-5) tentative) | not stated | dimensionless | 3 | placing this blind line detection at $z=6.3568$ |
| Comoving volume 6<z<8 | 4678 | not stated | Mpc^3 | 6 | this volume corresponds to 4678 Mpc$^3$ |

## Qualitative findings

- Most candidates have [CII] luminosities well above those expected from UV-based SFR; about 60% expected spurious.  
  > "The other candidates have significantly higher [CII] luminosities than expected from their UV–based SFR." (abstract)

## Claim tuples

- H: Can [CII] emitters at 6<z<8 be found in the ASPECS 1-mm scan? | E: Blind and dropout-guided line search with fidelity/completeness assessment | R: 14 candidates with S/N>4.5, ~60% expected spurious | F: Candidates exist but most are likely spurious; only IDX25 has tentative CO(6-5) confirmation | **partially**
- H: Are candidates detected in dust continuum? | E: Individual and stacked 1.2mm continuum | R: Stack of candidates 14±5 uJy; no individual detection | F: Tentative dust detection, SFR_IR ~3 Msun/yr | **partially**
- H: Do candidates follow the local L[CII]-SFR relation? | E: Compare L[CII] with UV SFR (x2 correction) | R: Only highest-SFR objects consistent; others far more luminous | F: Unclear whether intrinsically bright or spurious | **partially**
- H: Is the [CII] source density consistent with models? | E: Number counts in 4678 Mpc^3 assuming one real source or all corrected | R: Higher than models by over an order of magnitude | F: Less abrupt fall in [CII] counts than models if confirmed | **partially**

## Reasoning

- Why this data: UDF has deepest multiwavelength data and many dropouts at 6<z<8  
  > "The UDF is an ideal field to perform such a study, as this field contains a high density of dropout galaxies in this redshift range" (1 Introduction)
- Why this method: _not stated_
- Alternative: Lower-redshift CO interlopers tested with MUSE and 3-mm scan; ID52 rejected as z=2.379  
  > "except in the case of ID52 where MUSE confirms $z=2.379$." (3.5.1 MUSE complementary information)
- How they decided it was enough: _not stated_
- Limitation (authors): Candidates unconfirmed; blind IDX25 lies on atmospheric features  
  > "the 1-mm line falls right at the location of two atmospheric features making this detection uncertain despite its high significance." (3.5.2 ALMA 3-mm scan constraints)
- Caveat (inferred, ours): Low-S/N candidates with ~60% spurious fraction make L-SFR and luminosity function conclusions weak
- Caveat (inferred, ours): Luminosity function text refers to 'IDX04' inconsistent with source names
- Caveat (inferred, ours): Stack uncertainty only reflects image noise; assumed Td=50 K drives SFR_IR

## Reproducibility

- Data public (paper): Data from Cycle-2 projects cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00146.S and ADS/JAO.ALMA#2013.1.00718.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration/imaging parameters (in Paper I)
- Missing: MUSE data unpublished
- Missing: SERCH/CLUMPFIND settings beyond kernels and S/N
- Data volume (inferred): Large: 7-pointing mosaic band 6 plus band 3 scans, likely hundreds of GB raw
- Score (inferred): 3/5, Search method and thresholds described but calibration and cube making deferred to Paper I; MUSE data unpublished.
- Rediscovery candidate: no, Recipe depends on Paper I and AIPS-based search with unspecified parameters; results are low-significance candidates.

## Links

- Method: Walter et al. 2016 (cite: walter16) (Survey setup, data reduction, line search and completeness procedure)
- Companion: (cite: aravena16b) (1.2 mm continuum map)
- Related: ASPECS
- Related: HUDF
- Related: CANDELS
- Related: MUSE UDF GTO

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 81,
  "stated": 49,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
