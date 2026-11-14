# Witnessing Galaxy Assembly at the Edge of the Reionization Epoch

`2018ApJ...863L..29D` | The Astrophysical Journal Letters 2018 | first author: D'Odorico, V. | arXiv: 1808.01146 | DOI: 10.3847/2041-8213/aad7b7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Is there a CO(6-5)-emitting galaxy associated with a metal-poor proximate DLA at z~5.939 along the sightline to quasar J2310, and what are its molecular gas content and the DLA abundances?  
  > "We report the discovery of Serenity-18, a galaxy at $z\simeq5.939$ for which we could measure the content of molecular gas" (abstract)
- Target **Serenity-18 / DLA toward SDSS J2310+1855**: coordinates 23:10:38.44 +18:55:21.95 (J2000)  
  > "Redshift of CO(6-5) emission | 5.93957" (Table 2); "R.A., decl. ($23:10:38.437, 18:55:22.00$), or about ($-6.3,+2.2$) arcsec offset from the quasar position" (Emission line and sub-mm continuum); z/distance z=5.93957 (CO); DLA z=5.938646  
  > "Redshift of CO(6-5) emission | 5.93957" (Table 2); "R.A., decl. ($23:10:38.437, 18:55:22.00$), or about ($-6.3,+2.2$) arcsec offset from the quasar position" (Emission line and sub-mm continuum); distance from CO emission line redshift; DLA from XSHOOTER Voigt fits  
  > "Redshift of CO(6-5) emission | 5.93957" (Table 2); "R.A., decl. ($23:10:38.437, 18:55:22.00$), or about ($-6.3,+2.2$) arcsec offset from the quasar position" (Emission line and sub-mm continuum)
- Target **Quasar J231038.88+185519.7 (J2310)**: coordinates J231038.88+185519.7  
  > "the quasar J231038.88+185519.7 ($z_{\rm em}=6.0025$, J2310 hereafter)" (Introduction); z/distance z_em=6.0025  
  > "the quasar J231038.88+185519.7 ($z_{\rm em}=6.0025$, J2310 hereafter)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00584.S, 2015.1.00997.S
- bands: Band 3 and a Cycle 3 higher-frequency (band 6) dataset  
  > "ALMA band 3 receivers tuned to cover the frequency ranges $[84.56-87.94]$, and $[96.56-99.69]$ GHz" (Observations)
- frequencies and spectral setup: Band 3: 84.56-87.94 and 96.56-99.69 GHz; second dataset 254-257.65 and 269.65-273.15 GHz; SPW1 at 98.75 GHz  
  > "covering the frequency ranges \[254–257.65\] GHz and \[269.65–273.15\] GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array (Cycle 3) for the second dataset  
  > "observations obtained with the ALMA 12 m array in Cycle 3" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3: 0.6x0.4 arcsec PA -6 deg; second dataset: 0.9x0.6 arcsec PA 49 deg  
  > "we obtain a synthesized beam of $0.6 \times 0.4$ arcsec$^2$ at a PA $=-6$ deg" (Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 3: 5.4 uJy/beam continuum, 0.13 mJy/beam per 23.7 km/s channel; second: 50 uJy/beam continuum, 0.20 mJy/beam per 100 km/s  
  > "The noise levels are 5.4 $\mu$Jy/beam in the continuum in the aggregated bandwidth, and 0.13 mJy/beam in 23.7 ${\rm km~s}^{-1}$ wide channels" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 6-5 (not stated)
- Other facility **VLT/XSHOOTER**: Optical/NIR spectrum of J2310 for DLA identification and abundances  
  > "Quasar J2310 was also observed with XSHOOTER with a nominal resolving power of $R\simeq 8800$ and $8100$" (Observations)
- External data: Solar abundances  
  > "Solar abundances and corresponding uncertainties from Asplund et al. (2009)." (Table 1) [from Asplund et al. (2009)]
- External data: XQ-100 PCA quasar continua  
  > "We considered all of the Principal Component Analysis continua computed for the quasars in the XQ-100 sample (López et al. 2016)." (A proximate DLA at z≈5.939) [from López et al. 2016]
- External data: CO excitation ratio r61=20  
  > "We adopt in the following, $S_{\rm CO}(6-5)/(1-0)=r_{61}=20$" (Serenity-18 properties) [from Carilli & Walter 2013]
- External data: alpha_CO=1.5  
  > "We therefore adopt a lower value based on Vallini et al. (2018), $\alpha_{\rm CO}=1.5$" (Serenity-18 properties) [from Vallini et al. (2018)]
- Simulation/model as data: Althaea simulated z~6 galaxy HI column density and metallicity maps (Pallottini et al. 2017; Vallini et al. 2018)  
  > "In Fig. [3](#Fig:sim), we show the H I column density and metallicity maps for the filament embedding Althæa." (The system Serenity-18 + DLA)

## Processing

### Calibration

- pipeline or manual: calibration in CASA  
  > "We performed calibration in the CASA environment (McMullin et al. 2007)." (Observations)
- casa version: CASA v4.7 (second dataset)  
  > "The data were calibrated and imaged in CASA v4.7 by applying a natural weighting." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "By adopting a natural weighting scheme with detection threshold 0.5 times the noise per channel" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: corrected for primary beam efficiency  
  > "All data were corrected for the primary beam efficiency." (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.6x0.4 arcsec PA -6 deg  
  > "synthesized beam of $0.6 \times 0.4$ arcsec$^2$ at a PA $=-6$ deg" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- XSHOOTER spectrum characteristics and reduction  
  > "The characteristics of the spectrum and the reduction process were described in Feruglio et al. (2018)." (Observations) [from Feruglio et al. (2018)]
- Dynamical mass relation  
  > "(Wang et al. 2013, Feruglio et al. 2018)" (Serenity-18 properties) [from Wang et al. 2013, Feruglio et al. 2018]

### Not stated but needed to reproduce (our reading)

- Continuum-subtraction method and line-free channels
- CASA version and calibrators for the band 3 data
- Exact line integration window and spectral baseline for the Gaussian fit
- Band 6 observation dates/configurations
- Which PCA continua were selected
- Details of the conversion from L_FIR to SFR

## Analysis recipe

1. **Fit DLA absorption lines**: Voigt profile fits to XSHOOTER absorption lines; HI from damping wing using PCA continua  
  > "Absorption lines were identified and then fit with Voigt profiles using the context LYMAN of the ESO MIDAS software package" (A proximate DLA at z≈5.939)
   - software: ESO MIDAS LYMAN
   - parameter: b=8.0±0.4 km/s for O I, C II, Si II; b=10.5±1.5 km/s for Fe II  
  > "adopting the same Doppler parameter, $b=8.0\pm0.4$ km s$^{-1}$" (A proximate DLA at z≈5.939)
   - assumption: No ionization corrections, dust-free gas  
  > "we are computing abundances assuming a dust-free gas" (DLA properties)
   - fitting: Two continua fit separately; adopted average and half-width of range  
  > "We fit the DLA H I Ly$\alpha$ and Ly$\beta$ absorption lines using the two continua separately" (A proximate DLA at z≈5.939)
   - validation: _not stated_
2. **Detect and measure CO(6-5) emission**: Gaussian fit to spectrum; point-source fit to visibilities averaged over line width  
  > "A fit with a point source gives a zero spacing flux density of $251\pm51\rm ~\mu Jy$" (Emission line and sub-mm continuum)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Chance coincidence probability ~1-2% using Walter et al. 2016 line counts  
  > "we obtain a probability of chance alignment of $\sim1$  % $-2$ %." (Emission line and sub-mm continuum)
3. **Derive dynamical and molecular gas mass**: Mdyn sin^2 i relation with D<=beam; M(H2) from L'CO(6-5) with r61 and alpha_CO  
  > "$M_{\rm dyn} \sin^2(i) = 1.16~ 10^5 \times (0.75\times$FWHM$_{\rm CO})^2 \times D$" (Serenity-18 properties)
   - assumption: r61=20; alpha_CO=1.5  
  > "$\alpha_{\rm CO}=1.5$ K ${\rm km~s}^{-1}$ pc$^{-2}$ M$_{\ensuremath{\odot}}^{-1}$" (Serenity-18 properties)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate FIR luminosity and SFR**: L_FIR from L'CO(6-5) (Greve et al. 2014), SFR via Kennicutt 1998 with Kroupa IMF; compared with band 6 upper limit  
  > "From the calibration of Greve et al. (2014) between $L_{\rm FIR}$ and $L^{\prime}$ CO(6-5), we derive a far-infrared luminosity of $L_{\rm FIR} \approx 10^{12}~L_{\ensuremath{\odot}}$." (Serenity-18 properties)
   - assumption: T_dust=30-50 K  
  > "dust temperature in the range $T_{dust}=30-50~ K$" (Emission line and sub-mm continuum)
   - fitting: _not stated_
   - validation: Consistent with band 6 3-sigma upper limit  
  > "This value is consistent with the upper limit on the 150 $\mu$m continuum estimated from band 6 data." (Serenity-18 properties)

## Software

- **CASA** v4.7 (second dataset): calibration, imaging  
  > "We performed calibration in the CASA environment (McMullin et al. 2007)." (Observations)
- **GILDAS** : mapping and data analysis  
  > "Mapping and data analysis were performed both in the CASA and in the GILDAS (Guilloteau et al. 2000) environments." (Observations)
- **ESO MIDAS (LYMAN)** : Voigt profile fitting  
  > "using the context LYMAN of the ESO MIDAS software package (Fontana & Ballester 1995)" (A proximate DLA at z≈5.939)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(6-5) FWHM | 155 | 30 | km/s | 2 | $\rm FWHM_{CO(6-5)}$ \[km s$^{-1}$\] / $155 \pm  30$ |
| CO(6-5) integrated flux | 0.06 | 0.012 | Jy km/s | 2 | $\int S_{{\rm CO}(6-5)}dv$ \[Jy  km s$^{-1}$\] / $0.06\pm0.012$ |
| M(H2) | 5.4e9 | 0.5e9 | Msun | 3 | $M({\rm H}_2)~[M_\odot]$ / $(5.4\pm0.5) \times 10^{9}$ |
| Mdyn sin^2 i | <=5.6e9 | not stated | Msun | 3 | $M_{\rm dyn}sin^2(i)~[M_\odot]$ / $\leq 5.6\times 10^9$ |
| log N(HI) | 21.05 | 0.10 | log cm^-2 | 1 | H I / $21.05\pm0.10$ |
| [Fe/H] | -3.08 | 0.12 | dex | 1 | \[Fe/H\] $=-3.08 \pm 0.12$ |
| [Si/H] | -2.86 | 0.14 | dex | 1 | \[Si/H\] $=-2.86\pm0.14$ |
| SFR | ~115 | ~1 dex in L_FIR | Msun/yr | 4 | SFR \[$M_\odot {\rm yr}^{-1}$\] / $\approx 115$ |

## Qualitative findings

- CO-emitting galaxy lies at 6.7 arcsec (~40 kpc) from the quasar sightline, ~50 km/s from the DLA redshift, unresolved  
  > "Their angular separation is of $6.7$ arcsec, corresponding to an impact parameter of $\approx 40$ kpc at the DLA redshift" (The system Serenity-18 + DLA)

## Claim tuples

- H: The proximate DLA is associated with a CO-emitting galaxy | E: Searched ALMA band 3 data at DLA redshift | R: 5 sigma CO(6-5) line at DLA redshift, 6.7 arcsec from quasar, chance alignment ~1-2% | F: Serenity-18 is associated with the metal-poor DLA | **supported**
- H: The DLA is very metal poor | E: Voigt fits to XSHOOTER | R: [Fe/H]=-3.08, [Si/H]=-2.86 | F: Consistent with other z~6 DLAs and PopII enrichment | **supported**
- H: Serenity-18 is a typical main sequence galaxy with substantial molecular gas | E: CO luminosity to gas mass and SFR | R: M(H2)~5e9 Msun, SFR~100 | F: First molecular gas detection in typical main sequence galaxy at end of reionization | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Foreground CO(3-2) at z~2.47 or CO(4-3) at z~3.63 as chance alignment, rejected at ~1-2% probability  
  > "a foreground CO emitter (CO(3-2) at $z\simeq2.47$ or CO(4-3) at $z\simeq3.63$)" (Emission line and sub-mm continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Line at band edge so flux and derived masses may be lower limits  
  > "the integrated flux of the emission line and its derived quantities might be lower limits" (Emission line and sub-mm continuum)
- Limitation (authors): L_FIR uncertain by ~1 dex  
  > "This is a very rough estimate with an uncertainty of $\sim1$ dex due to the scatter of the correlation." (Serenity-18 properties)
- Caveat (inferred, ours): Gas mass depends strongly on assumed r61 and alpha_CO
- Caveat (inferred, ours): Single 5 sigma line truncated at band edge
- Caveat (inferred, ours): SFR derived indirectly from CO, not independently measured
- Caveat (inferred, ours): Unresolved source so Mdyn is only an upper limit

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details and scripts
- Missing: Line-fit and integration window
- Missing: Chosen PCA continua
- Data volume (inferred): ~50-100 GB raw for two ALMA projects
- Score (inferred): 4/5, Short letter; few processing details, but data codes given and results are numeric.
- Rediscovery candidate: no, Processing details (calibration, line window) are insufficient and the XSHOOTER analysis requires non-ALMA data.

## Links

- Method: Feruglio et al. 2018 (Describes XSHOOTER spectrum and reduction and the ALMA quasar observations)
- Companion: Feruglio et al. 2018 (Quasar host galaxy results from the same ALMA data)
- Related: XQ-100

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 42,
  "rate": 0.545
 },
 "evidence_ok": true
}
```
