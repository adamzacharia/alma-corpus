# Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II. Complex organic molecules and heavy water in shocks around a young high-mass protostar

`2019A&A...632A..57C` | Astronomy and Astrophysics 2019 | first author: Csengeri, T. | arXiv: - | DOI: 10.1051/0004-6361/201935226

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Where in a resolved single high-mass protostellar envelope (accretion shocks, inner envelope, protostar/disk) do complex organic molecules and HDO reside, and how does their composition differ?  
  > "We put observational constraints on the physical location of COMs in a resolved high-mass protostellar envelope associated with the G328.2551−0.5321 clump." (abstract)
- Target **G328.2551-0.5321**: coordinates phase centre (J2000) 15h58m00.05s, −53°57′57.8″  
  > "The phase centre was (α, δ) J2000 = (15 [h] 58 [m] 00.05 [s], −53 [◦] 57 [′] 57. [′′] 8)" (2. Observations and data reduction); "The phase centre was (α, δ) J2000 = (15 [h] 58 [m] 00.05 [s], −53 [◦] 57 [′] 57. [′′] 8)" (2. Observations and data reduction); z/distance 2.5 (+0.7/-0.5) kpc  
  > "cloud that is located at a distance of 2.5" (1. Introduction); "cloud that is located at a distance of 2.5" (1. Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00960.S
- bands: Band 7, ~345 GHz  
  > "We used four basebands in Band 7 centred on 347.331, 345.796, 337.061, and 333.900 GHz, respectively." (2. Observations and data reduction)
- frequencies and spectral setup: 4 basebands, 4 × 1.75 GHz, 0.977 MHz (~0.9 km/s) resolution  
  > "This gives a 4 × 1.75 GHz effective bandwidth with a spectral resolution of 0.977 MHz corresponding to ∼0.9 km s−1 velocity resolution." (2. Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m, 35 antennas, Cycle 2 (7 m data not used for this work)  
  > "The observations have been carried out with ALMA in Cycle 2 using 35 of the 12 m antennas on 2015 May 3, and 2015 September 1." (2. Observations and data reduction); "We have therefore not used information from the more compact 7 m array." (2. Observations and data reduction)
- configurations: _not stated_
- baselines: 15 m (17 kλ) to 1574 m (1809 kλ)  
  > "the baseline range is 15 m (17 kλ) to 1574 m (1809 kλ)" (2. Observations and data reduction)
- angular resolution: 0.30″ × 0.17″, PA 88.37°, geometric mean 0.23″ (~575 au)  
  > "synthesised half-power beam width (HPBW) of 0.″30 × 0.″17 and a position angle of 88.37 degrees." (2. Observations and data reduction)
- max recoverable scale: ~7″  
  > "largest angular scales of ∼7″, beyond which the sensitivity of our 12 m array observations drops" (2. Observations and data reduction)
- sensitivity: 1σ rms ~3 K in Tb at 0.977 MHz resolution  
  > "We measure a 1σ rms noise level of ∼3 K in brightness temperature (Tb) scales in a spectral resolution of" (2. Observations and data reduction)
- time on source: 7.4 min  
  > "The total time on source was 7.4 min" (2. Observations and data reduction)
- observing dates: 2015 May 3 and 2015 September 1  
  > "on 2015 May 3, and 2015 September 1." (2. Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: HDO 3(3,1)-4(2,2) (335.396 GHz)
- Line: CH3OH vt=1 3_0-2_1 E (shock tracer) (334.427 GHz)
- Other facility **APEX/ATLASGAL**: 870 µm survey that identified the source  
  > "based on the APEX Telescope Large Area Survey of the Galaxy (ATLASGAL) (Schuller et al. 2009; Csengeri et al. 2014, 2017) at 870 µm" (1. Introduction)
- External data: Dust opacity κν = 0.0185 cm2 g−1 at 345 GHz including gas-to-dust ratio 100  
  > "κ ν = 0.0185 cm [2] g [−][1] from Ossenkopf & Henning (1994) at 345 GHz including the gas-to-dust ratio, _R_, of 100" (3.1 Line fitting and LTE modelling) [from Ossenkopf & Henning (1994)]
- External data: Spectroscopic line catalogues CDMS and JPL  
  > "using the CDMS (Müller et al. 2005; Endres et al. 2016) and JPL (Pickett et al. 1998) molecular databases" (3.1 Line fitting and LTE modelling) [from Müller et al. 2005; Endres et al. 2016; Pickett et al. 1998]
- External data: Source vlsr and linewidth from Gaussian fits to CH3OH lines  
  > "The � lsr and ∆� are measured using a Gaussian fit to the CH 3 OH lines and these values are reported in Paper I." (3.1 Line fitting and LTE modelling) [from Csengeri et al. 2018 (Paper I)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data have been calibrated in CASA 4.3.1 with the pipeline (version 34 044)." (2. Observations and data reduction)
- casa version: CASA 4.3.1  
  > "The data have been calibrated in CASA 4.3.1 with the pipeline (version 34 044)." (2. Observations and data reduction)
- pipeline version: 34 044  
  > "The data have been calibrated in CASA 4.3.1 with the pipeline (version 34 044)." (2. Observations and data reduction)
- archive products used as is: _not stated_
- flux calibrator: Titan and Ceres; bandpass J1517−2422, phase J1617−5848  
  > "the absolute flux scale has been calibrated based on observations of Titan and Ceres." (2. Observations and data reduction)
- flux scale uncertainty: ~10% (max discrepancy up to 12%)  
  > "We estimate an absolute flux uncertainty around ∼10%" (2. Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CLEAN with Briggs weighting  
  > "We imaged and cleaned the data using Briggs weighting and used the CLEAN algorithm for deconvolution." (2. Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "In this work we used a robust parameter of 0.5 for the imaging" (2. Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Spectra: zero-order baseline in CLASS; line images: uv-plane subtraction using emission-free channels  
  > "We subtracted the continuum emission from these spectra by selecting line emission free channels, and using a zero order baseline." (2. Observations and data reduction); "We then subtracted the continuum emission in the _uv_ -data" (2. Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m only; 7 m not used  
  > "We have therefore not used information from the more compact 7 m array." (2. Observations and data reduction)
- smoothing: _not stated_
- final beam: 0.30″ × 0.17″ (geometric mean 0.23″)  
  > "The geometric mean of the major and minor axes corresponds to a beam size of 0.″23 (∼575 au)." (2. Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Spectral setup and data reduction  
  > "The spectral setup and data reduction for our target is described in more details in Paper I." (2. Observations and data reduction) [from Csengeri et al. 2018 (Paper I)]
- R90% size estimate formulation  
  > "Following the formulation in Paper I, we estimate a radius ( _R_ 90% ) of 0.″58 corresponding to a size of 1450 au." (3.3 Spatial distribution of various molecules) [from Csengeri et al. 2018 (Paper I)]
- vlsr and linewidth of CH3OH  
  > "these values are reported in Paper I." (3.1 Line fitting and LTE modelling) [from Paper I]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Clean threshold, mask, image size and cell size
- Exact line widths and vlsr values (in Paper I)
- Positions and extraction apertures of spectra beyond the figure
- Fit goodness criterion is visual only; no numeric chi2
- Bad-data flagging details

## Analysis recipe

1. **Image the 12 m data cube and extract spectra**: CLEAN with Briggs weighting; extract spectra at shock A, shock B, inner envelope and centre; continuum subtract in CLASS  
  > "We then extracted spectra of the entire frequency coverage towards representative positions corresponding to the two accretion shock spots, and a position representing the inner envelope (Fig. 1)." (2. Observations and data reduction)
   - software: CASA, GILDAS/CLASS
   - parameter: robust 0.5; conversion Jy/beam to K factor 198  
  > "we used a factor of 198 based on the geometric mean of the synthesized HPBW" (2. Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit CH3OH column density and Tkin**: Grid of LTE models with Weeds, N(CH3OH)=1e17-1e20 cm-2, Tkin=50-300 K; best fit chosen by residuals and visual inspection  
  > "To select the best fit, we computed the residuals of each fit, and visually inspected the results with a particular emphasis on the optically thin lines" (3.1 Line fitting and LTE modelling)
   - software: Weeds
   - parameter: source size fixed to 0.4″  
  > "We fixed the source size to 0.″4 which is larger than the beam." (3.1 Line fitting and LTE modelling)
   - assumption: LTE, since n ≳ 1e7 cm-3  
  > "we model the spectra assuming that local thermodynamic equilibrium (LTE) conditions apply" (3.1 Line fitting and LTE modelling)
   - fitting: grid search, visual selection; 3σ-consistent range given  
  > "In Table 2 we give the range of values that are consistent with the data within 3σ" (3.1 Line fitting and LTE modelling)
   - validation: Composite model compared with the full spectrum  
  > "As our composite final model shows, these parameters give a good agreement with the spectra." (3.1 Line fitting and LTE modelling)
3. **Derive N(H2) from dust continuum**: N(H2)=Fν/(Bν(Td) Ω κν R μ mH) with Td=Tkin  
  > "assuming that the gas and the dust are thermalised at these high densities, hence _T_ d = _T_ kin" (3.1 Line fitting and LTE modelling)
   - parameter: mu_H2 = 2.8; Omega = 1.13 Θ²  
  > "µ H 2 is the mean molecular weight per hydrogen molecule and is equal to 2.8" (3.1 Line fitting and LTE modelling)
   - assumption: Ossenkopf & Henning κ with gas-to-dust 100  
  > "including the gas-to-dust ratio, _R_, of 100" (3.1 Line fitting and LTE modelling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit other COMs and HDO relative to methanol**: Same vlsr, Δv, Tkin and source size as CH3OH; vary column density of each species iteratively and inspect the composite model  
  > "After fitting the CH 3 OH transitions, we created the models for other molecules using the same parameters (v lsr, ∆�, _T_ kin and source size) as for CH 3 OH" (3.1 Line fitting and LTE modelling)
   - software: Weeds
   - assumption: All COMs share Tkin of methanol  
  > "our initial assumption that all COMs originate from gas with the same physical conditions (i.e. _T_ kin ), may not hold" (3.2 Detection of COMs)
   - fitting: manual iterative fitting  
  > "We used the Weeds package (Maret et al. 2011), and fitted the spectra in an iterative process." (3.1. Line fitting and LTE modelling)
   - validation: Visual inspection of the full model with all species  
  > "visually inspected the full model including all identified species" (3.1 Line fitting and LTE modelling)
5. **Map spatial distribution and measure sizes**: Zeroth/first moment maps over −55 to −35 km/s; 2D Gaussian fits to moment-0 maps; R90% sizes  
  > "We show zeroth moment maps calculated over a velocity range of −55 to −35 km s−1 for some unblended transitions of COMs" (3.3 Spatial distribution of various molecules)
   - fitting: 2D Gaussian  
  > "Using a 2D Gaussian fit to the 0th moment map shown in Fig. 4," (3.3. Spatial distribution of various molecules)
   - validation: _not stated_

## Software

- **CASA** 4.3.1: calibration (pipeline) and imaging  
  > "The data have been calibrated in CASA 4.3.1 with the pipeline (version 34 044)." (2. Observations and data reduction)
- **GILDAS/CLASS** : spectra processing and continuum subtraction  
  > "The spectra were then exported to GILDAS/CLASS [2] for further processing. We subtracted the continuum emission from these spectra by selecting line emission free channels" (2. Observations and data reduction)
- **Weeds** : LTE spectral modelling  
  > "We used the Weeds package (Maret et al. 2011), and fitted the spectra in an iterative process." (3.1 Line fitting and LTE modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(CH3OH) at shocks | up to 2e19 (shock A 1.6e19, B 2e19) | range 1.2-1.6e19 (A), 1.6-2.4e19 (B) | cm-2 | 2 | Shock _B_ [−2.″50;−2.″88] 144 28.5 1.6 × 10 [19] − 2.4 × 10 [19] ( **2** × **10** **[19]** ) 170–200 ( **180** ) 1.89 × 10 [24] |
| Tkin shocks | 180 | 170-190 (A), 170-200 (B) | K | 2 | 170–190 ( **180** ) |
| Tkin inner envelope | 110 | 90-110 range | K | 2 | a considerably lower kinetic temperature of 110 K |
| N(H2) shock A / B / envelope | 2.04e24 / 1.89e24 / 1.90e24 | not stated | cm-2 | 3 | Inner envelope [−2.″43;−2.″47] 86 17.0 **4** . **1** × **10** **[18]** − 8.1 × 10 [18] 90–110 1.90 × 10 [24] |
| N(CH3OCHO) at shock B | 1.0e18 | not stated | cm-2 | 4 | CH 3 OCHO 1 0.05 1.0 × 10 [18] 5.3 × 10 [−][7] 180 +4.55 |
| N(HDO) | 2.1-4.0e17 | not stated | cm-2 | 4 | requires a high column density of 2.1–4.0 × 10 [17] cm [−][2] to fit the observed line intensity |
| HDO abundance | 1.1e-7 to 2.1e-7 | not stated | relative to H2 | 4 | The estimated HDO abundance is between 1.1 × 10 [−][7] and 2.1 × 10 [−][7] for all three positions |
| C2H5CN/C2H3CN abundance ratio | 2.4-3.4 | not stated | dimensionless | 4 | The C 2 H 5 CN/C 2 H 3 CN abundance ratio is 2.4−3.4 towards all positions |
| R90% of methyl formate | 0.58″ (1450 au) | not stated | arcsec | 5 | we estimate a radius ( _R_ 90% ) of 0.″58 corresponding to a size of 1450 au |
| R90% of HDO | 0.53″ (~1325 au) | not stated | arcsec | 5 | corresponding to an _R_ 90% radius of 0.″53 that is ∼1325 au |

## Qualitative findings

- O-bearing COMs (ethanol, acetone, ethylene glycol) peak at accretion shocks; CN-bearing N-COMs peak on the protostar  
  > "O-bearing COMs, such as ethanol, acetone, and ethylene glycol are almost exclusively found and show a higher abundance towards the accretion shocks with _T_ kin ∼ 180 K." (abstract)

## Claim tuples

- H: COMs are enhanced at accretion shocks relative to the inner envelope | E: LTE modelling at two shock positions and an envelope position | R: O-bearing COM abundances an order of magnitude higher at the shocks | F: Accretion shocks enrich O-bearing COMs | **supported**
- H: The source is a precursor of a classical hot core | E: Compare radiatively heated region size with other hot cores | R: Heated region <1000 au, inner envelope Tkin ~110 K | F: Source is a hot core precursor | **supported**
- H: HDO traces sublimated ice in the inner envelope | E: Image the HDO 335.396 GHz line and model it | R: Extended HDO with similar abundance at shocks and envelope | F: HDO destruction has not been efficient yet | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Blending and single-transition identifications make some column densities (formamide, HDO, acetone) less robust  
  > "the estimated column density is less robust compared to the other species" (3.2 Detection of COMs)
- Caveat (inferred, ours): Visual fitting without uncertainties on abundances
- Caveat (inferred, ours): Single Tkin assumed for all species
- Caveat (inferred, ours): HDO blended with ethylene glycol and methyl formate, one transition only
- Caveat (inferred, ours): Short integration, one tuning

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Reduced datacubes available at CDS  
  > "A copy of the reduced datacubes is available at the CDS via anonymous ftp" (abstract footnote)
- Missing: Exact spectrum extraction positions/apertures and line-free channels
- Missing: Weeds model files and per-line fitting choices
- Missing: Parameters in Paper I
- Data volume (inferred): ~tens of GB (single Band 7 12 m project, two execution blocks)
- Score (inferred): 3/5, Data public and main setup stated, but fitting is by eye and details are deferred to Paper I.
- Rediscovery candidate: no, LTE fits were selected visually and key settings are in Paper I, so exact numbers are hard to redo.

## Links

- Method: Maret et al. 2011 (Weeds LTE modelling package)
- Companion: Csengeri et al. 2018 (Paper I) (Source structure, shock detection, data reduction details)
- Related: SPARKS
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 76,
  "stated": 51,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
