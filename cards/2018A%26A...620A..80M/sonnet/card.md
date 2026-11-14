# ALMA observations of the young protostellar system Barnard 1b: Signatures of an incipient hot corino in B1b-S

`2018A&A...620A..80M` | Astronomy and Astrophysics 2018 | first author: Marcelino, N. | arXiv: 1809.08014 | DOI: 10.1051/0004-6361/201731955

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Do the young protostars B1b-N and B1b-S show complex organic molecule emission, and what are the physical conditions and abundances of the emitting gas (is a hot corino forming in B1b-S)?  
  > "this core is an ideal target to study the structure and chemistry of the first objects formed in the collapse of prestellar cores." (abstract)
- Target **Barnard 1b (B1b-N, B1b-S)**: coordinates mosaic centre 03h33m21.3s, +31d07m34.0s (J2000)  
  > "We performed a 7-point mosaic centered at α J2000 = 03 h 33 m 21.3 s and δ J2000 = 31 ◦ 07 ′ 34.0 ′′" (2. Observations); "The Barnard 1 cloud is a moderately active star forming region in the Perseus molecular complex, at a distance of 230 pc (Hirota et al. 2008)." (1. Introduction); z/distance 230 pc  
  > "We performed a 7-point mosaic centered at α J2000 = 03 h 33 m 21.3 s and δ J2000 = 31 ◦ 07 ′ 34.0 ′′" (2. Observations); "The Barnard 1 cloud is a moderately active star forming region in the Perseus molecular complex, at a distance of 230 pc (Hirota et al. 2008)." (1. Introduction); distance from Hirota et al. 2008  
  > "We performed a 7-point mosaic centered at α J2000 = 03 h 33 m 21.3 s and δ J2000 = 31 ◦ 07 ′ 34.0 ′′" (2. Observations); "The Barnard 1 cloud is a moderately active star forming region in the Perseus molecular complex, at a distance of 230 pc (Hirota et al. 2008)." (1. Introduction)

## Data provenance

- ALMA projects: 2015.1.00025.S
- bands: Band 6, centred at 218 and 233 GHz (LSB/USB)  
  > "We used the Band 6 receiver centered at 218 and 233 GHz in the lower and upper side band, respectively" (2. Observations)
- frequencies and spectral setup: 13 spectral windows: one 2 GHz continuum window (~40 km/s) and 12 windows of 58.5 MHz with ~0.16–0.2 km/s resolution  
  > "13 spectral windows were used, one at low resolution (∼40 km s −1 and 2 GHz of bandwidth) for the continuum, and 12 windows with spectral resolutions of ∼0.16–0.2 km s −1" (2. Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array  
  > "The ALMA 12m array was used in the C40-4 configuration" (2. Observations)
- configurations: C40-4, 36–40 antennas  
  > "C40-4 configuration, with 36–40 antennas and baselines between 15.1 and 704.1 m" (2. Observations)
- baselines: 15.1–704.1 m  
  > "baselines between 15.1 and 704.1 m" (2. Observations)
- angular resolution: ~0.7×0.55 arcsec (160×126 au)  
  > "∼0.7×0.55 ′′ (160×126 au)" (2. Observations)
- max recoverable scale: ~4 arcsec  
  > "the largest scales to which we are sensitive are ∼4 ′′" (2. Observations)
- sensitivity: image rms 3.3–6.2 mJy/beam; 128–414 mK in B1b-S spectra (Table B.1)  
  > "215811 – 215869 0.74×0.57 23 3.29 128" (Table B.1)
- time on source: 44 min per track, four tracks  
  > "Total time on-source is 44 min per track." (2. Observations)
- observing dates: 2016 June 21-24  
  > "ALMA Cycle 3 observations were performed on 2016 June 2124, in four different tracks of about 1 hr each." (2. Observations)
- pi or archival as stated: _not stated_
- Other facility **IRAM 30m**: Envelope abundances from 3 mm survey for comparison  
  > "Table B.3 shows the abundances derived from the ALMA data, together with those obtained in the envelope from the IRAM 30m survey at 3mm." (5. Discussion)
- External data: Compact continuum size 0.35 arcsec for hot component (ALMA Band 7)  
  > "a size of 0.35 ′′ (that of the continuum compact emission obtained by ALMA Band 7 observations, Gerin et al. 2017)" (4. Column densities and abundances) [from Gerin et al. 2017]
- External data: Envelope N(H2)=7.6e22 cm-2 and envelope abundances from IRAM 30m  
  > "Abundances for the envelope are from Marcelino et al. (2009), Cernicharo et al. (2012), and Marcelino et al. (in prep.)." (Table B.3) [from Daniel et al. 2013; Marcelino et al. 2009; Cernicharo et al. 2012]
- External data: Previous dust continuum (ALMA 850 um, JVLA 8-10 cm) used for N(H2)  
  > "Based on previous observations of dust continuum emission with ALMA at 850 µm and JVLA at 8-10 cm (those with the best angular resolution, see appendix A)" (4. Column densities and abundances) [from Table A.1 refs (Gerin et al. 2017; Tobin et al. 2016)]

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline  
  > "Calibration was performed by the ALMA Pipeline in CASA [1] 4.5.3." (2. Observations)
- casa version: CASA 4.5.3  
  > "Calibration was performed by the ALMA Pipeline in CASA [1] 4.5.3." (2. Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636, flux density set to ~1.14–1.22 Jy  
  > "Flux density for J0238+1636 was set to ∼1.14–1.22 Jy, depending on the day and frequency, based on close flux measurements." (2. Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Images produced in CASA, 0.2 km/s resolution  
  > "Images of all spectral windows were also produced in CASA, with a spectral resolution of 0.2 km s −1 and Briggs weighting." (2. Observations)
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust not stated)  
  > "with a spectral resolution of 0.2 km s −1 and Briggs weighting" (2. Observations)
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
- final beam: ~0.59–0.74 x 0.44–0.58 arcsec per window  
  > "231293 – 231351 0.59×0.44 16 6.17 414" (Table B.1)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell and image size, deconvolver, cleaning masks and thresholds
- Continuum subtraction method and line-free channels
- Exact MADEX LTE inputs: linewidths, source-size/beam-dilution treatment, spectroscopic catalogs per species
- Fitting procedure and uncertainties for column densities (by-eye?)
- How N(H2) of 1.4e25 and 1.1e25 cm-2 was computed (opacity law, fluxes used)
- Gaussian line-fit procedure details; the conversion factor per window used
- Whether pipeline products were manually refined

## Analysis recipe

1. **Image spectral windows and extract spectra**: Imaged in CASA at 0.2 km/s; spectra extracted within one synthesized beam toward B1b-N and B1b-S with GILDAS, converted Jy to K (K/Jy ~63)  
  > "We have extracted the spectra, within one synthesized beam size, towards the positions of the B1b-N and B1b-S cores." (2. Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and fit Gaussians**: Line identification with MADEX; Gaussian fits; 3 sigma threshold (4 sigma for unidentified)  
  > "Line identification was carried out using MADEX [3] (Cernicharo 2012)." (3. Results); "All transitions listed in Table B.2 are above the 3σ level" (3. Results)
   - software: MADEX
   - fitting: Gaussian line fits  
  > "with line parameters obtained from Gaussian line fits" (3. Results)
   - validation: _not stated_
3. **LTE two-component source model for COMs**: Fit CH3OCOH and CH3CHO with LTE models; two components: 200 K, 0.35 arcsec and 60 K, 0.6 arcsec; applied to other species  
  > "we built a model of the source with two components. One warm and compact component at 200 K and a size of 0.35 ′′" (4. Column densities and abundances)
   - software: MADEX
   - parameter: Temperatures between 50–250 K tested in one-component models  
  > "using other temperatures (between 50–250 K) in the one component models does not reproduce satisfactorily the observations" (4. Column densities and abundances)
   - assumption: LTE  
  > "We assume local thermodynamic equilibrium (LTE) conditions" (4. Column densities and abundances)
   - fitting: Models adjusted in temperature and column density to match spectra (apparently by comparison with observations)  
  > "we modified the temperature and column density to fit the observed spectra." (4. Column densities and abundances)
   - validation: Fit error estimated ~50%; compared with one-component models  
  > "We estimate the error in the fit to be ∼50%." (4. Column densities and abundances)
4. **Derive H2 column densities and abundances**: N(H2) from dust continuum assuming dust temperatures 12–50 K; abundances X/H2  
  > "assuming dust temperatures from 12 to 50 K, we have computed mean column densities of N(H2)=1.4 10 25 cm −2 and 1.1 10 25 cm −2" (4. Column densities and abundances)
   - assumption: Standard dust opacity law; uncertainties up to factor 2  
  > "All these factors could result in uncertainties in the column density estimates up to a factor 2." (4. Column densities and abundances)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: Pipeline calibration and imaging  
  > "Calibration was performed by the ALMA Pipeline in CASA [1] 4.5.3. Images of all spectral windows were also produced in CASA" (2. Observations)
- **GILDAS** : Spectra extraction and analysis  
  > "For analysis purposes we used the GILDAS [2] software. We have extracted the spectra, within one synthesized beam size, towards the positions of the B1b-N and B1b-S cores." (2. Observations)
- **MADEX** : Line identification and LTE modelling  
  > "We have used MADEX (Cernicharo 2012) to reproduce the observed spectra of COMs in B1b-S" (4. Column densities and abundances)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lines detected toward B1b-S | 190 | not stated | lines | 2 | In total, we have detected 190 lines towards B1b-S. |
| CH3OCOH column density (hot; cold) | 1.5e16; 0.5e16 | ~50% fit error | cm-2 | 3 | CH 3 OCOH 1.5 ; 0.5 10 [16] 1.1 ; 0.4 10 [−][9] |
| CH3OCOH abundance (hot; cold) | 1.1e-9; 0.4e-9 | factor ~2 | X/H2 | 4 | CH 3 OCOH 1.5 ; 0.5 10 [16] 1.1 ; 0.4 10 [−][9] |
| t-CH3CH2OCOH abundance (hot; cold) | 3.3e-11; 0.7e-11 | not stated | X/H2 | 4 | t -CH 3 CH 2 OCOH 4.6 ; 0.8 10 [14] 3.3 ; 0.7 10 [−][11] |
| N(H2) at 0.35 and 0.60 arcsec | 1.4e25; 1.1e25 | up to factor 2 | cm-2 | 4 | N(H2)=1.4 10 25 cm −2 and 1.1 10 25 cm −2 for source sizes of 0.35 ′′ and 0.6 ′′ |
| NH2CN/NH2CHO ratio | 0.25 | not stated | dimensionless | 4 | We obtain in B1b-S an abundance ratio of 0.25, similar to IRAS 16293-2422. |

## Qualitative findings

- B1b-N spectra are free of COM emission; B1b-S shows rich COM spectra with narrow (~1 km/s) lines  
  > "while B1b-S shows intense and rich spectra, B1b-N is mostly free of line emission." (3. Results)

## Claim tuples

- H: Is a hot corino forming in the very young Class 0 source B1b-S? | E: ALMA Band 6 spectra and two-component LTE model | R: Compact 200 K component with moderate COM abundances; COM abundances enhanced vs envelope | F: A hot corino is being formed in B1b-S | **supported**
- H: Does the FHSC candidate B1b-N show COM emission? | E: Spectra extracted toward B1b-N | R: No COM emission | F: B1b-N likely at an earlier evolutionary stage | **supported**
- H: Are new COMs, including ethyl formate, present in a low-mass protostar? | E: Line identification with MADEX | R: Tentative detections of several species; ethyl formate with 3 unblended lines | F: First detection of ethyl formate toward a low-mass star-forming region | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Two components needed because one component could not fit all lines, notably deuterated vs vibrationally excited ones  
  > "However, it was difficult to fit all the lines with only" (4. Column densities and abundances)
- Alternative: One-component models at 50–250 K rejected  
  > "We have checked that using other temperatures (between 50–250 K) in the one component models does not reproduce satisfactorily the observations." (4. Column densities and abundances)
- How they decided it was enough: _not stated_
- Limitation (authors): Emission unresolved; origin of COMs unclear; resolution and S/N insufficient to constrain model  
  > "the limited angular resolution and signal-to-noise ratio of the current observations do not allow a well-constrained model." (4. Column densities and abundances)
- Caveat (inferred, ours): Two-component model is degenerate; not a formal fit with uncertainties
- Caveat (inferred, ours): Many tentative detections based on a single unblended line
- Caveat (inferred, ours): LTE assumption and dust-derived N(H2) uncertain
- Caveat (inferred, ours): Optically thick lines and flux filtering affect extended species

## Reproducibility

- Data public (paper): ALMA project 2015.1.00025.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00025.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MADEX line catalogs and model inputs
- Missing: Imaging parameters beyond Briggs weighting
- Missing: Details of N(H2) derivation
- Data volume (inferred): ~100-200 GB raw for four tracks, 13 spws
- Score (inferred): 3/5, Data are archival and the processing is outlined, but LTE model details and imaging parameters are incompletely given.
- Rediscovery candidate: no, The LTE modelling relies on MADEX and by-eye fitting not fully specified.

## Links

- Method: Cernicharo 2012 (MADEX code used for line identification and LTE modelling)
- Companion: Gerin et al. 2017 (ALMA Band 7 continuum, source sizes)
- Companion: Gerin et al. 2015 (Outflows of B1b-N and B1b-S)
- Related: PILS (IRAS 16293-2422)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 68,
  "stated": 42,
  "rate": 0.618
 },
 "evidence_ok": true
}
```
