# GRB 190114C in the nuclear region of an interacting galaxy. A detailed host analysis using ALMA, the HST, and the VLT

`2020A&A...633A..68D` | Astronomy and Astrophysics 2020 | first author: de Ugarte Postigo, A. | arXiv: 1911.07876 | DOI: 10.1051/0004-6361/201936668

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: transients, nearby_galaxies
- Question: What are the properties of the host galaxy of GRB 190114C (the first GRB with TeV emission), and could its environment have favoured the very-high-energy emission?  
  > "We explore the peculiarities of this event and any distinctive factor that could have favoured the generation of the VHE photons that were observed." (Introduction)
- Target **GRB 190114C host galaxy and companion**: coordinates _not stated_; z/distance z = 0.425  
  > "was found to be at a redshift of $z=0.425$" (Introduction); "At a redshift of $z=0.425$ this is equivalent to a projected distance of $6.8\pm0.6$ kpc." (2.1 Optical and near-infrared imaging from HST with ACS and WFPC3); distance from Selsing2019; Castro-Tirado2019 (GCN redshift)  
  > "was found to be at a redshift of $z=0.425$" (Introduction); "At a redshift of $z=0.425$ this is equivalent to a projected distance of $6.8\pm0.6$ kpc." (2.1 Optical and near-infrared imaging from HST with ACS and WFPC3)

## Data provenance

- ALMA projects: 2018.A.00020.T
- bands: Band 6  
  > "were carried out with the Atacama Large Millimeter Array (ALMA) observatory in Band 6" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- frequencies and spectral setup: central observed frequency 235.0487 GHz; CO(3-2) at 242.663 GHz  
  > "The correlator was configured for a central observed frequency of 235.0487 GHz." (2.5 ALMA CO(3-2) imaging and spectroscopy)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 313 m, 47-48 antennas  
  > "The configuration used 47-48 antennas with baselines ranging from 15 m to 313 m" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- angular resolution: 1.16" x 0.867" (PA -87.9 deg)  
  > "was $1.16\ensuremath{''}\times0.867\ensuremath{''}$ (Position Angle $-87.9^\circ$)" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 43 min per observation, five executions  
  > "Each observation consisted of 43 min integration time on source" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- observing dates: 17-18 January 2019, three epochs  
  > "Five individual executions were performed in three independent epochs ranging between January 17 and 18, 2019." (2.5 ALMA CO(3-2) imaging and spectroscopy)
- pi or archival as stated: DDT programme, PI de Ugarte Postigo  
  > "within the context of DDT programme ADS/JAO.ALMA#2018.A.00020.T (P.I.: de Ugarte Postigo)" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- Line: CO 3-2 (not stated (observed 242.663 GHz at z=0.425))
- Other facility **HST ACS/WFC3**: optical/NIR imaging, host position and photometry  
  > "The field was observed in four optical bands: $F475W$, $F606W$, $F775W$, and $F850LP$." (2.1 Optical and near-infrared imaging from HST with ACS and WFPC3)
- Other facility **VLT/HAWK-I**: JHKs photometry  
  > "the field was observed in the near-infrared (NIR) bands with HAWK-I" (2.2 Near-infrared imaging from VLT/HAWK-I)
- Other facility **VLT/X-shooter**: emission-line spectroscopy  
  > "In this paper we use the second observation to perform emission-line analysis of the host galaxy of GRB 190114C." (2.4 VLT/X-shooter spectroscopy)
- Other facility **GALEX and WISE**: unresolved UV and IR catalogue photometry  
  > "we can only obtain combined photometry of both galaxies." (2.3 Ultraviolet and infrared archival photometry from GALEX and WISE)
- External data: CO(3-2)/CO(1-0) luminosity ratio of 0.56  
  > "Assuming L$^{\prime}_{{\rm CO}(3-2)}$/L$^{\prime}_{{\rm CO}(1-0)}$ = 0.56 (cite: Carilli2013) for star-forming galaxies" (Table 4 notes) [from (cite: Carilli2013)]
- External data: SFR(CO) relation for metal-poor galaxies  
  > "Based on the relation given by (cite: Hunt2015) for metal-poor galaxies" (Table 4 notes) [from (cite: Hunt2015)]
- External data: metallicity-dependent alpha_CO = 18.2  
  > "Assuming a metallicity-dependent CO-to-H$_2$ conversion factor (cite: Amorin2016) of $\alpha_{CO}=18.2$" (Table 4 notes) [from (cite: Amorin2016)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline calibration  
  > "using the pipeline calibration" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- casa version: CASA 5.4.0  
  > "Common Astronomy Software Applications, version 5.4.0" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (first two epochs), J0423-0120 (last)  
  > "The flux calibration was performed using the quasar J0522-3627 in the first two epochs and with J0423-0120 for the last one." (2.5 ALMA CO(3-2) imaging and spectroscopy)
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
- continuum subtraction: in the uv plane using line-free channels on both sides of CO(3-2)  
  > "continuum subtraction was performed in the UV visibilities using line free channels on both sides of CO(3-2)" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- line free channels: 241.839-242.433 and 242.800-243.574 GHz  
  > "The spectral ranges used to fit the continuum were $241.839-242.433$ and $242.800-243.574$ GHz" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- primary beam correction: _not stated_
- array combination: pipeline cube combining all five executions  
  > "spectral data cube obtained by the pipeline products that combined all five executions" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- smoothing: _not stated_
- final beam: 1.16" x 0.867", PA -87.9 deg  
  > "was $1.16\ensuremath{''}\times0.867\ensuremath{''}$ (Position Angle $-87.9^\circ$)" (2.5 ALMA CO(3-2) imaging and spectroscopy)
- final rms: _not stated_

### Inherited from earlier work

- Continuum/afterglow analysis deferred to other papers  
  > "for a detailed analysis of the continuum emission see Acciari et al. 2019, in press, and Misra et al. in prep." (3.2 Molecular analysis) [from Acciari et al. 2019; Misra et al. in prep.]
- Half-light radii method  
  > "These radii have been determined using the method described by (cite: Blanchard2016)." (2.1 Optical and near-infrared imaging from HST with ACS and WFPC3) [from (cite: Blanchard2016)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, cell, image size, deconvolver, masking, threshold)
- channel width of the cube
- aperture definitions for spectral extraction and fitting procedure for CO lines
- how the afterglow continuum was removed given its dominance
- CO line luminosity conversion formulas
- LePhare configuration (grid, priors)
- phase and bandpass calibrators

## Analysis recipe

1. **Image CO(3-2) and subtract continuum**: Pipeline-calibrated data, uv continuum subtraction, zero-moment map  
  > "The CO(3-2) zero-moment image is shown in Fig. [2](#Fig:alma)." (2.5 ALMA CO(3-2) imaging and spectroscopy)
   - software: CASA
   - parameter: line-free ranges 241.839-242.433 and 242.800-243.574 GHz  
  > "The spectral ranges used to fit the continuum were $241.839-242.433$ and $242.800-243.574$ GHz" (2.5 ALMA CO(3-2) imaging and spectroscopy)
   - fitting: _not stated_
   - validation: Integrated random velocity ranges in line-free regions; no residual continuum  
  > "No significant residual continuum was detected on those verification maps." (2.5 ALMA CO(3-2) imaging and spectroscopy)
2. **Extract CO spectra of host, companion, combined; derive line properties and H2 masses**: Spectra from apertures; flux, centre, FWHM; luminosity; SFR and M_H2 with two alpha_CO  
  > "Using the apertures shown in Fig. [2](#Fig:alma) we extracted the spectra of the GRB host, the companion galaxy, and the combined system." (3.2 Molecular analysis)
   - software: CASA
   - assumption: alpha_CO = 5 and 18.2; L'CO(3-2)/L'CO(1-0)=0.56  
  > "First we used $\alpha_{CO}=5$ M$_{\odot}$/(K·km/s·pc$^2$)" (3.2 Molecular analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **SED fitting for stellar mass and SFR**: Iterative fit including blended GALEX/WISE photometry, BC03 templates, Calzetti law, exponentially declining SFH, Chabrier IMF  
  > "The process was iterated until it converged." (3.1 SED fits)
   - software: LePhare
   - assumption: Galactic E(B-V)=0.011  
  > "corrected for Galactic extinction ($\textnormal{E}(B-V)=0.011$, (cite: Schlafly2011))" (3.1 SED fits)
   - fitting: _not stated_
   - validation: Compared with HST+VLT-only fit  
  > "the results differ only slightly from those obtained just with the *HST*/ACS and VLT/HAWK-I data" (3.1 SED fits)
4. **X-shooter emission-line analysis (attenuation, SFR, metallicity)**: Gaussian fits/integration, MC errors, Balmer decrement, Kennicutt SFR, O3N2 and N2 metallicity  
  > "For 1000 simulated events we repeatedly added random Gaussian noise" (3.3 Host emission-line analysis)
   - fitting: _not stated_
   - validation: Errors cross-checked with continuum r.m.s.  
  > "cross-checked with the r.m.s. of the spectral continuum" (3.3 Host emission-line analysis)

## Software

- **CASA** 5.4.0: ALMA calibration and spectroscopic analysis  
  > "The spectroscopic measurements were also analysed within CASA." (2.5 ALMA CO(3-2) imaging and spectroscopy)
- **LePhare** : SED fitting  
  > "We used `LePhare` (cite: Arnouts1999; Ilbert2006) to fit these photometric data" (3.1 SED fits)
- **SExtractor** : HST photometry  
  > "The photometry was performed with SExtractor (cite: Bertin1996)" (2.1 Optical and near-infrared imaging from HST with ACS and WFPC3)
- **astrodrizzle** : HST image combination  
  > "Processed images were then reduced and combined via `astrodrizzle`" (2.1 Optical and near-infrared imaging from HST with ACS and WFPC3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Host CO(3-2) line flux | 150 | 25 | mJy km/s | 2 | Line Flux (mJy·km/s) / $150\pm25$ / $336\pm26$ / $512\pm41$ |
| Companion CO(3-2) line flux | 336 | 26 | mJy km/s | 2 | Line Flux (mJy·km/s) / $150\pm25$ / $336\pm26$ / $512\pm41$ |
| Host M_H2 (alpha_CO=5) | 1.38e9 | 0.23e9 | Msun | 2 | $(1.38\pm0.23)\times10^9$ |
| Velocity difference host-companion | 50 | 20 | km/s | 2 | The centres of the emission lines differ by only $50\pm20$ km/s |
| Host stellar mass log | 9.27 | +0.28/-0.25 | log Msun | 3 | log(Mass (M$_{\odot}$))     / $9.27_{-0.25}^{+0.28}$ |
| Host SFR from SED | 9.4 | +12.8/-6.4 | Msun/yr | 3 | $9.4_{-6.4}^{+12.8}$ |
| GRB offset from host centre (HST) | 170 | 60 | pc | 0 | or a projected distance of $170\pm60$ pc |
| Metallicity (N2) | 8.38 | 0.02 | 12+log(O/H) | 4 | for N2 we get $12+\log\mathrm{(O/H)}=8.38\pm0.02$ |

## Qualitative findings

- Both galaxies are detected in CO(3-2) and are an interacting pair at the same redshift; the companion is more CO-luminous.  
  > "the companion galaxy is more luminous in the CO(3-2) transition, in contrast to the optical emission" (3.2 Molecular analysis)

## Claim tuples

- H: Are host and companion physically interacting? | E: CO(3-2) redshifts from ALMA, HST separation | R: Velocity difference 50±20 km/s, projected separation 6.8±0.6 kpc | F: Close interacting pair | **supported**
- H: Do the galaxies have high molecular gas fractions? | E: CO luminosity to M_H2 with two alpha_CO | R: f_gas 0.7 (host), 0.35 (companion) for alpha_CO=5 | F: High gas fraction, likely interaction induced | **supported**
- H: Was the GRB environment unusually dense? | E: HST offset, extinction, gas content | R: Offset 170 pc, Offset/r50=0.09 | F: Indicative of dense environment that could favour VHE emission | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Submm continuum dominated by afterglow so host continuum cannot be studied.  
  > "This implies that we cannot study the continuum emission of the host galaxy." (3.2 Molecular analysis)
- Caveat (inferred, ours): Dense-environment/VHE link is speculative from a single event
- Caveat (inferred, ours): alpha_CO uncertain by a factor of ~3.6
- Caveat (inferred, ours): Large SED uncertainties
- Caveat (inferred, ours): Low ALMA resolution barely separates galaxies

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean imaging parameters
- Missing: aperture definitions
- Missing: LePhare settings
- Data volume (inferred): ~10-30 GB for ALMA (five executions, Band 6)
- Score (inferred): 3/5, ALMA data identified and calibration basic settings given, but imaging and extraction details are missing.
- Rediscovery candidate: no, Imaging and spectral extraction details are insufficient and public status is not stated.

## Links

- Method: (cite: Blanchard2016) (half-light radius method)
- Companion: Acciari et al. 2019 (afterglow continuum analysis)
- Companion: Thöne et al. in prep. (X-shooter details)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
