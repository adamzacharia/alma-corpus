# Submillimetre dust polarization and opacity in the HD163296 protoplanetary ring system

`2019MNRAS.482L..29D` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Dent, W. R. F. | arXiv: 1809.09185 | DOI: 10.1093/mnrasl/sly181

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the polarisation fraction and angle structure and the 870/1300 um spectral index of the HD163296 ringed disk, and can self-scattering explain them?  
  > "We present ALMA images of the sub-mm continuum polarisation and spectral index of the protoplanetary ringed disk HD163296." (abstract)
- Target **HD163296**: coordinates _not stated_; z/distance 105 pc  
  > "Lying at a distance of 105pc[^2], it is classified as spectral type A2Ve, of age 5Myr (cite: Montesinos2009)." (Introduction); "Sizes and luminosities in this paper have been revised based on the GAIA DR2 parallax" (Introduction); distance from GAIA DR2 parallax (per footnote)  
  > "Lying at a distance of 105pc[^2], it is classified as spectral type A2Ve, of age 5Myr (cite: Montesinos2009)." (Introduction); "Sizes and luminosities in this paper have been revised based on the GAIA DR2 parallax" (Introduction)

## Data provenance

- ALMA projects: 2015.0.00616.S, 2013.0.00601.S
- bands: Band 7 (343.5 GHz mean) polarisation; archival Band 6 for spectral index  
  > "The system was set up to observe continuum in band 7 at a mean frequency of 343.5GHz" (Observations)
- frequencies and spectral setup: SPWs at 336.494, 338.432, 348.494, 350.494 GHz; 31.25 MHz channels, 2 GHz nominal bandwidth each  
  > "with spectral windows at 336.494, 338.432, 348.494 and 350.494GHz, each having 31.25MHz channel spacing and 2GHz nominal bandwidth" (Observations)
- continuum bandwidth: 7.5 GHz usable  
  > "with a total usable bandwidth of 7.5GHz" (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.21x0.19 arcsec at 81 deg (natural); 0.18x0.17 arcsec for combined B6+B7  
  > "giving a beam of 0.21x0.19$\ensuremath{''}$ at 81$\ensuremath{^\circ}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: ~50 uJy rms Stokes images; 55 uJy for combined I/alpha image  
  > "resulting in a final rms of $\sim$50$\mu$Jy in the Stokes images" (Observations)
- time on source: 2 hours (about 15 min flagged)  
  > "The total time on-source was 2 hours, although some 15 minutes of data were flagged in the second session" (Observations)
- observing dates: 23 Jul and 13 Aug 2016 (Band 7); 2015 Aug (Band 6)  
  > "The observations were conducted in sessions on two nights: 23 Jul and 13 Aug 2016" (Observations)
- pi or archival as stated: _not stated_
- External data: Archival ALMA Band 6 data taken in 2015 Aug  
  > "together with ALMA archive data taken in 2015 Aug in band 6 (cite: Isella2016)" (Observations) [from (cite: Isella2016)]
- External data: Scale height of 10 au at 100 au used in model  
  > "a Gaussian scale height of 10 au at 100 au (cite: deGregorio2013)" (Discussion and modeling) [from (cite: deGregorio2013)]
- External data: Literature alpha_mm of 2.7±0.4 for comparison  
  > "This is in reasonable agreement with that measured by (cite: Pinilla2014) (2.7$\pm0.4$)" (Results) [from (cite: Pinilla2014)]
- Simulation/model as data: mcfost radiative transfer model with DHS astrosilicate grains, a_max ~100 um  
  > "The model presented in Fig. [4](#fig:model) corresponds to compact astrosilicates (cite: Draine2003), with a maximum grain size a$_{max} \sim$ 100$\,\mu$m" (Discussion and modeling)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline data, extra flagging, per-execution self-cal (phase and amplitude), polarisation calibrated per day  
  > "The calibrated data from the ALMA pipeline was examined, further flagging applied, and the individual executions were used to create self-calibrated solutions for the antenna phase and amplitude." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304, 1.52 and 1.67 Jy at 343.5 GHz  
  > "J1733-1304 was used as a flux calibrator with assumed fluxes of 1.52 and 1.67 Jy at 343.5 GHz on the two observing nights" (Observations)
- flux scale uncertainty: relative <=1%; conservative absolute 7%  
  > "A conservative calibration error is 7%, which would correspond to a spectral index offset of 0.3" (Results)
- self calibration: phase and amplitude per execution  
  > "used to create self-calibrated solutions for the antenna phase and amplitude" (Observations)

### Imaging

- task: CLEAN in CASA; Stokes I,Q,U,V  
  > "imaged using CLEAN in CASA (cite: 2007ASPC..376..127M), producing separate images of Stokes I, Q, U and V" (Observations)
- deconvolver: _not stated_
- weighting robust: natural for polarisation; Briggs robustness=0.5 for combined I/alpha  
  > "natural uv weighting was applied" (Observations); "CLEAN with Briggs robustness=0.5 uv weighting" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Band 6 + Band 7 combined with multi-frequency synthesis; pointing offset -11,-73 mas corrected  
  > "Data were combined using the multi-frequency synthesis method (cite: Rau2011)" (Observations)
- smoothing: _not stated_
- final beam: 0.21x0.19 arcsec at 81 deg  
  > "giving a beam of 0.21x0.19$\ensuremath{''}$ at 81$\ensuremath{^\circ}$" (Observations)
- final rms: ~50 uJy (Stokes); 55 uJy (combined)  
  > "and an rms of 55$\mu$Jy at an effective central frequency of 291 GHz" (Observations)

### Inherited from earlier work

- Disk model setup details  
  > "Details are outlined in (cite: Pinte2016) for HL Tau." (Discussion and modeling) [from (cite: Pinte2016)]

### Not stated but needed to reproduce (our reading)

- CLEAN cell size, image size, masks, threshold and iterations
- Band 6 project code details and exact calibration of archival data
- Pointing offset correction method
- Surface density inversion details and dust grain size distribution/ mass/ opacity in mcfost
- Polarisation calibration procedure details

## Analysis recipe

1. **Image Stokes I,Q,U,V and derive debiased polarisation**: CLEAN imaging, P% = 100 sqrt(Q^2+U^2-rms^2)/I  
  > "$P\% = 100\sqrt{{Q}^2 +{U}^2- {rms}^2} / I$" (Observations)
   - software: CASA
   - parameter: natural weighting  
  > "natural uv weighting was applied" (Observations)
   - fitting: _not stated_
   - validation: calibrator fluxes agree with calibrator database to better than 5%  
  > "agreed with the measured values at that time from the ALMA online calibrator database to better than 5%" (Observations)
2. **Spectral index map**: Combine Band 7 and Band 6 with MFS CLEAN  
  > "Data were combined using the multi-frequency synthesis method (cite: Rau2011)" (Observations)
   - software: CASA
   - parameter: Briggs robust 0.5  
  > "CLEAN with Briggs robustness=0.5 uv weighting" (Observations)
   - fitting: _not stated_
   - validation: relative calibration <=1%, absolute 7% giving 0.3 offset  
  > "The relative flux calibrations across each of the images are accurate to $\leq1\%$" (Results)
3. **Self-scattering radiative transfer model**: mcfost with density from inverting uniform-weighted intensity image, passive disk, DHS astrosilicates  
  > "building a disk density model by inverting the intensity image with uniform CLEAN weighting into a surface density profile" (Discussion and modeling)
   - software: mcfost
   - parameter: L*=28 Lsun, scale height 10 au at 100 au, DHS max void fraction 0.8, a_max ~100 um  
  > "We calculate dust optical properties using a distribution of hollow spheres (DHS) with a maximum void fraction of 0.8." (Discussion and modeling)
   - assumption: spherical grains, scattering only source of polarisation, multiple scattering included  
  > "Spherically symmetric dust grains are used, where the only source of polarisation is scattering (multiple scattering is included)." (Discussion and modeling)
   - fitting: _not stated_
   - validation: qualitative comparison of model Stokes Q,U convolved to observed resolution  
  > "The corresponding Stokes Q and U maps are computed, and then convolved to the observed resolution" (Discussion and modeling)

## Software

- **CASA** : CLEAN imaging  
  > "imaged using CLEAN in CASA (cite: 2007ASPC..376..127M)" (Observations)
- **mcfost** : radiative transfer scattering model  
  > "we use the radiative transfer code mcfost (cite: Pinte2006; Pinte2009)" (Discussion and modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| central polarisation fraction | 0.9 | not stated | % | 1 | The percentage polarisation (Fig.1b) ranges from 0.9% in the centre |
| median central polarisation angle (inner 30 au) | 44.1 | 1.5 | deg | 1 | with a median of 44.1$\pm1.5\ensuremath{^\circ}$ over the inner 30 au |
| total disk spectral index | 2.1 | 0.3 | dimensionless | 2 | giving $\alpha_{mm}$ of $2.1\pm0.3$ |
| total flux Band 7 / Band 6 | 1.68 / 0.70 | not stated | Jy | 2 | The total disk fluxes are 1.68Jy at band 7 and 0.70Jy at band 6 |
| model alpha_mm | ~3.5 | not stated | dimensionless | 3 | This gives $\alpha_{mm}$ $\sim$ 3.5 |

## Qualitative findings

- Polarisation fraction peaks (~4%) in gaps, anticorrelated with intensity; vectors become azimuthal in gaps  
  > "It peaks in the gaps between the dust rings, and the largest value ($\sim\,$4$\%$) is found between rings 1 and 2." (abstract)

## Claim tuples

- H: Self-scattering alone explains the polarisation pattern | E: mcfost scattering model of ringed disk compared with ALMA 870 um polarisation | R: Model reproduces major-axis enhancement, anticorrelation with intensity, minor-axis alignment and azimuthal twist in gaps | F: Consistent with self-scattering without additional alignment | **supported**
- H: Low alpha_mm in the inner disk is consistent with the polarisation-derived grain size | E: Compare model alpha_mm with observed | R: Model alpha ~3.5 vs observed lows | F: Dust/disk model needs refinement to match both | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Magnetic or radiative-torque aligned grains do not predict minor-axis alignment in inclined disks  
  > "for inclined disks like HD163296, they do not predict the same vector orientation along the minor axis in the centre" (Discussion and modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Ring widths unresolved so optical depth only a lower limit; absolute flux calibration may offset alpha by 0.3  
  > "the ring brightness temperature only provides a lower limit to the optical depth, so we cannot discriminate between these possibilities" (Results)
- Caveat (inferred, ours): Model comparison is qualitative, no fit or quantitative goodness
- Caveat (inferred, ours): Single grain model explored
- Caveat (inferred, ours): Band 6 and 7 epochs differ by a year, possible variability

## Reproducibility

- Data public (paper): Band 6 described as ALMA archive data  
  > "together with ALMA archive data taken in 2015 Aug in band 6" (Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: mcfost model inputs
- Missing: Polarisation calibration details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identifiable and main steps described, but imaging and modeling parameters are missing.
- Rediscovery candidate: no, Key imaging and model details are not given, and model comparison is qualitative.

## Links

- Method: (cite: Rau2011) (Multi-frequency synthesis)
- Method: (cite: Pinte2016) (Disk model details)
- Companion: (cite: Isella2016) (Source of the Band 6 data)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.0.00616.S",
  "2013.0.00601.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00601.S",
  "2015.1.00616.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 40,
  "rate": 0.606
 },
 "evidence_ok": true
}
```
