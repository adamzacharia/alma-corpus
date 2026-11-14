# The Ophiuchus DIsk Survey Employing ALMA (ODISEA): Disk Dust Mass Distributions across Protostellar Evolutionary Classes

`2019ApJ...875L...9W` | The Astrophysical Journal Letters 2019 | first author: Williams, Jonathan P. | arXiv: 1904.06471 | DOI: 10.3847/2041-8213/ab1338

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How do disk dust mass distributions vary across protostellar infrared classes (I, Flat, II, III) in Ophiuchus, and how do Class II masses compare with other regions?  
  > "We calculate disk masses and compare their distributions across protostellar classes, revealing their evolution with more clarity than before." (Introduction)
- Target **Ophiuchus ODISEA sample B (142 sources, Class II/III) plus sample A from Paper I**: coordinates not stated (per-source in Table 1)  
  > "The Ophiuchus region is ideally suited on account of its proximity, youth, and size ($\sim 140$ pc, $\sim 1$ Myr, and $\sim 300$ protostars)." (Introduction); "For the 14 sources with larger fractional errors and the 106 with no measurement, we used a mean distance $\bar d = 139.4$ pc." (Observations); z/distance ~140 pc; mean 139.4 pc where no good parallax  
  > "The Ophiuchus region is ideally suited on account of its proximity, youth, and size ($\sim 140$ pc, $\sim 1$ Myr, and $\sim 300$ protostars)." (Introduction); "For the 14 sources with larger fractional errors and the 106 with no measurement, we used a mean distance $\bar d = 139.4$ pc." (Observations); distance from Gaia DR2 parallaxes (d = 1/pi for pi/sigma>10), else mean distance  
  > "The Ophiuchus region is ideally suited on account of its proximity, youth, and size ($\sim 140$ pc, $\sim 1$ Myr, and $\sim 300$ protostars)." (Introduction); "For the 14 sources with larger fractional errors and the 106 with no measurement, we used a mean distance $\bar d = 139.4$ pc." (Observations)

## Data provenance

- ALMA projects: 2016.1.00545.S
- bands: Band 6  
  > "The observations of sample B were carried out in ALMA Band 6 with 40 antennas in the C40-3 array configuration" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.3 GHz centered at 225.4 GHz (1.33 mm)  
  > "with a total continuum bandwidth of 7.3 GHz centered at 225.4 GHz ($\lambda = 1.33$ mm)" (Observations)
- arrays: _not stated_
- configurations: C40-3  
  > "40 antennas in the C40-3 array configuration (15 to 500 m baselines)" (Observations)
- baselines: _not stated_
- angular resolution: ~0.98'' x 0.74'', PA ~88 deg  
  > "$\sim 0.98\ensuremath{''} \times 0.74\ensuremath{''}$ at a position angle of $\sim 88^\circ$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 3 sigma mass sensitivity ~0.3 Earth masses  
  > "despite a $3\sigma$ mass sensitivity of $\sim 0.3\,M_\oplus$" (4.1 Across Protostellar Evolutionary Classes)
- time on source: 54 s per source  
  > "Each of the 142 sources was observed for a total of 54 seconds." (Observations)
- observing dates: 2018 May 2, August 20 and 21  
  > "on 2018 May 2$^{\rm nd}$, and August 20$^{\rm th}$ and 21$^{\rm st}$" (Observations)
- pi or archival as stated: _not stated_
- Line: CO, 13CO, C18O J=2-1 (not stated)
- Other facility **Gaia DR2**: Parallax distances  
  > "169 have parallaxes ($\pi$) in the Data Release 2 catalog" (Observations)
- Other facility **Spitzer c2d**: Source sample and IR classes  
  > "all the protostars identified in the *Spitzer* “Cores to Disks” Legacy project" (Introduction)
- External data: Lupus and Upper Scorpius ALMA flux densities, ages and distances for comparison  
  > "Disk masses were recalculated from the observed flux densities with the same uniform temperature and opacity prescription" (4.2 Across Star-Forming Regions) [from (cite: 2018ApJ...859...21A; 2016ApJ...827..142B)]
- External data: Sample A ALMA observations and sample selection  
  > "Paper I describes the full sample selection and the observations of sample A" (Observations) [from (cite: 2019MNRAS.482..698C)]

## Processing

### Calibration

- pipeline or manual: standard data pipeline scripts  
  > "The visibilities were calibrated using the standard data pipeline scripts using version 5.3.0 of the CASA software package." (Observations)
- casa version: CASA 5.3.0  
  > "using version 5.3.0 of the CASA software package" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 and J1517-2422  
  > "The flux scale was referenced to J1733-1304 and J1517-2422 and has an uncertainty of 10%." (Observations)
- flux scale uncertainty: 10%  
  > "has an uncertainty of 10%" (Observations)
- self calibration: _not stated_

### Imaging

- task: tclean for continuum images; uvmodelfit for point-source photometry  
  > "Continuum images were created using the task `tclean` and inspected for multiplicity." (Observations); "fitting a point source to the visibilities using the task `uvmodelfit`" (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Correlator configuration same as sample A  
  > "The correlator was configured in the same way as for sample A" (Observations) [from (cite: 2019MNRAS.482..698C)]
- Use d = 1/pi for pi/sigma_pi > 10  
  > "As in (cite: 2018A&A...618L...3M), we set $d = 1/\pi$ for those sources with $\pi/\sigma_\pi > 10$" (Observations) [from (cite: 2018A&A...618L...3M)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, cell, image size, deconvolver, masking)
- Aperture sizes for resolved/binary sources
- How rms was measured
- Survival analysis implementation and gaussian fitting method/priors
- Sample A fluxes (from Paper I) used in the class comparison
- Exact J-band source selection and the Lupus/Upper Sco flux tables used
- Pipeline calibration flagging details

## Analysis recipe

1. **Measure continuum flux densities**: Point-source fit to visibilities with uvmodelfit; aperture photometry for binary and resolved sources  
  > "Photometry was carried out for the rest of the sample by fitting a point source to the visibilities using the task `uvmodelfit`." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Images inspected for multiplicity  
  > "Continuum images were created using the task `tclean` and inspected for multiplicity." (Observations)
2. **Adopt distances and clean sample**: Gaia DR2 parallax inversion; mean distance otherwise; remove background (pi<2.5 mas) and misclassified sources  
  > "For the 14 sources with larger fractional errors and the 106 with no measurement, we used a mean distance $\bar d = 139.4$ pc." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Convert flux to dust mass**: Optically thin M = F d^2/(kappa B(T))  
  > "under the assumption of optically thin emission throughout, with a uniform temperature, $T_{\rm dust} = 20$ K" (3 Disk Mass Distributions)
   - parameter: detection if flux >= 3 rms and position within 1'' of Spitzer position; upper limits at 3 rms  
  > "A disk was deemed to be detected by ALMA if the measured flux density was at least three times greater than the rms" (3 Disk Mass Distributions)
   - assumption: T_dust = 20 K, kappa_nu = (nu/100 GHz) cm^2/g, optically thin  
  > "$\kappa_\nu = (\nu/100\,{\rm GHz})\,{\rm cm^2~g^{-1}}$" (3 Disk Mass Distributions)
   - fitting: _not stated_
   - validation: Compared with radiative transfer modeling results of Tazzari et al. 2017  
  > "find masses that are very similar to those derived from this equation" (3 Disk Mass Distributions)
4. **Derive cumulative mass distributions and log-normal fits per class and region**: Survival analysis for upper limits; gaussian in log mass fitted to cumulative distributions  
  > "Cumulative mass distributions were then determined using survival analysis, which uses the constraints from upper limits in the data" (3 Disk Mass Distributions)
   - parameter: Region comparison restricted to J-band <= 12 mag (masses >~0.2 Msun)  
  > "we use a $1.2\,\mu$m J-band magnitude cutoff of 12 mag" (4.2 Across Star-Forming Regions)
   - fitting: _not stated_
   - validation: Separation robust to different J/K cutoffs; omitting binaries did not change fits  
  > "omitting them from the disk distributions here did not significantly change the log-normal fits" (4.1 Across Protostellar Evolutionary Classes)

## Software

- **CASA** 5.3.0: Pipeline calibration, tclean imaging, uvmodelfit  
  > "using version 5.3.0 of the CASA software package" (Observations)
- **astropy** : Listed software, use not specified  
  > "astropy (cite: 2013A&A...558A..33A)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Class I mean dust mass | 3.83 | +1.62/-1.31 | Earth masses | 4 | I /  28 /  $3.83^{+1.62}_{-1.31}$ /                $0.86^{+0.06}_{-0.02}$ |
| Flat spectrum mean dust mass | 2.49 | +0.82/-0.82 | Earth masses | 4 | Flat /  50 /  $2.49^{+0.82}_{-0.82}$ |
| Class II mean dust mass | 0.78 | +0.12/-0.11 | Earth masses | 4 | II / 172 /  $0.78^{+0.12}_{-0.11}$ /                $0.97^{+0.06}_{-0.05}$ |
| Ophiuchus Class II mean mass (J<=12) | 2.62 | +0.83/-0.65 | Earth masses | 4 | Ophiuchus / $\sim 1$ / $2.62^{+0.83}_{-0.65}$ |
| Lupus Class II mean mass | 5.08 | +1.78/-1.41 | Earth masses | 4 | Lupus / $\sim 3$ / $5.08^{+1.78}_{-1.41}$ |
| Upper Sco Class II mean mass | 0.36 | +0.10/-0.09 | Earth masses | 4 | Upper Scorpius / $\sim 10$ / $0.36^{+0.10}_{-0.09}$ |
| Final sample size | 265 sources, 279 disks | not stated | count | 2 | final sample of 265 sources (279 disks after allowing for 12 binaries and one triple system) |

## Qualitative findings

- Three Class III sources detected with masses 0.2-0.4 Earth masses  
  > "we detected three Class III sources with dust masses $0.2-0.4\,M_\oplus$" (4.1 Across Protostellar Evolutionary Classes)

## Claim tuples

- H: Disk dust mass declines from Class I through Flat to Class II | E: ALMA 1.3 mm fluxes converted to dust masses; log-normal fits per class | R: Mean masses 3.83, 2.49, 0.78 Earth masses; sigma ~0.8-1 dex | F: Clear decline with class but large overlap | **supported**
- H: Disk masses decrease monotonically with region age | E: Compare Class II fits in Ophiuchus, Lupus, Upper Sco with J<=12 cut | R: Ophiuchus 2.62, Lupus 5.08, Upper Sco 0.36 Earth masses | F: Masses do not decrease monotonically; environment or dust regeneration may matter | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple uniform conversion allows cleanest comparison across and between surveys  
  > "it allows the cleanest comparison of disks both within the large Ophiuchus sample and between surveys of other regions" (3 Disk Mass Distributions)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass conversion limited to grains of size comparable to wavelength; assumed T, opacity, optical depth may bias masses  
  > "any such flux-to-mass conversions are ultimately limited to constraints on the mass of particles with sizes comparable to the observing wavelength" (5 Discussion)
- Caveat (inferred, ours): Fixed 20 K dust temperature ignores luminosity/stellar mass dependence and Class I envelope contamination
- Caveat (inferred, ours): Class II region comparison depends on a J-band proxy for stellar mass
- Caveat (inferred, ours): Gaia distances missing for 106 sources
- Caveat (inferred, ours): Upper limits and binaries handled coarsely

## Reproducibility

- Data public (paper): Cycle 4 program cited with ADS/JAO.ALMA acknowledgement; table of fluxes in online journal  
  > "The full table of 279 disks is available in machine-readable form in the online journal." (Table 1)
- Products in archive: _not stated_
- Missing: tclean imaging parameters
- Missing: Sample A flux values from Paper I
- Missing: Survival analysis and fitting code details
- Missing: Comparison survey flux tables
- Data volume (inferred): ~100-300 GB raw for sample B (3 EBs); continuum only much smaller
- Score (inferred): 3/5, Data public and the mass formula is explicit, but imaging and fitting details are missing and sample A comes from Paper I.
- Rediscovery candidate: yes, Public data, simple numeric recipe (flux to mass, log-normal fit) and numeric results, though some imaging details are absent.

## Links

- Method: (cite: 1985ApJ...293..192F) (Survival analysis for censored data)
- Companion: (cite: 2019MNRAS.482..698C) (Paper I: ODISEA survey, sample A observations)
- Related: Spitzer Cores to Disks
- Related: ALMA Lupus survey
- Related: ALMA Upper Scorpius survey

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 38,
  "rate": 0.559
 },
 "evidence_ok": true
}
```
