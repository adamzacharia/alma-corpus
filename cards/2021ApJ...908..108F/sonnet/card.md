# Physical and Chemical Structure of the Disk and Envelope of the Class 0/I Protostar L1527

`2021ApJ...908..108F` | The Astrophysical Journal 2021 | first author: Flores-Rivera, Lizxandra | arXiv: 2012.05553 | DOI: 10.3847/1538-4357/abd1db

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, protoplanetary_disks
- Question: Can a coupled dynamical, radiative-transfer and gas-grain chemical model (RadChemT) reproduce the observed C18O, 12CO and N2H+ line emission, PV diagrams and SED of the Class 0/I protostar L1527?  
  > "RadChemT combines dynamics, radiative transfer, gas chemistry and gas-grain reactions to generate models which can be directly compared with observations for individual protostars." (abstract)
- Target **L1527 IRS**: coordinates RA(J2000)=4h39m53.9s, Dec=26d03m10s  
  > "classified as a class 0/I protostar with an edge-on disk orientation located 140 parsecs away in Taurus molecular cloud" (Introduction); "Dec.(J2000)=26$^\mathrm{\circ}$03$^\mathrm{'}$10$^\mathrm{"}.000$" (Table 2); z/distance 140 pc  
  > "classified as a class 0/I protostar with an edge-on disk orientation located 140 parsecs away in Taurus molecular cloud" (Introduction); "Dec.(J2000)=26$^\mathrm{\circ}$03$^\mathrm{'}$10$^\mathrm{"}.000$" (Table 2); distance from literature (Beichman 1986; Torres 2007; Tobin 2008; Kristensen 2012)  
  > "classified as a class 0/I protostar with an edge-on disk orientation located 140 parsecs away in Taurus molecular cloud" (Introduction); "Dec.(J2000)=26$^\mathrm{\circ}$03$^\mathrm{'}$10$^\mathrm{"}.000$" (Table 2)

## Data provenance

- ALMA projects: 2011.0.00210.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.96'' x 0.73'' (geometric ~0.8'')  
  > "having ${0.96\ensuremath{''} \times 0.73\ensuremath{''}}$ (that is the geometric beam) spatial resolution" (3.2 ALMA data)
- max recoverable scale: ~15'' (15.7'')  
  > "Maximum recoverable scale | 15.7$\ensuremath{''}$" (ALMA observational parameters)
- sensitivity: 8.0 mJy/beam per detected channel; velocity resolution 0.17 km/s  
  > "Noise level (detected channel) | 8.0mJy beam$^{-1}$" (ALMA observational parameters)
- time on source: _not stated_
- observing dates: 2012 August 26 (Cycle 0)  
  > "taken during cycle 0 on 2012 August 26" (3.2 ALMA data)
- pi or archival as stated: ALMA archive data  
  > "are based on data from the ALMA archive" (3.2 ALMA data)
- Line: C18O 2-1 (219.5603 GHz)
- Other facility **CARMA**: 12CO(1-0) and N2H+(1-0) maps, 2.66 mm continuum  
  > "The CARMA correlator was set to observe the $^{12}$CO (1-0) emission line ($\nu$ = 115.271 GHz)" (3.1 CARMA data)
- Other facility **Herschel**: PACS photometry and spectrum for SED  
  > "The *Herschel* data were downloaded from the IRSA/IPAC archive." (4.1 L1527 SED fits)
- External data: SED flux densities and physical model parameters for L1527  
  > "We re-generate SEDs for L1527 by including the flux density values from (cite: Tobin_2008)" (4.1 L1527 SED fits) [from (cite: Tobin_2008; Tobin_2010; tobin_2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (gain calibrator J0510+180)  
  > "Flux calibrator | Callisto" (ALMA observational parameters)
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
- primary beam correction: Model multiplied by 28'' FWHM Gaussian primary beam  
  > "The model is also multiplied by the ALMA primary beam, which was taken to be a smooth $28\ensuremath{''}$ FWHM Gaussian image." (3.2 ALMA data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation and calibration details  
  > "More information about the observations and calibration is given in Table 1. in (cite: Ohashi_2014)." (3.2 ALMA data) [from (cite: Ohashi_2014)]
- Physical model parameters (initial)  
  > "use what has been previously determined by (cite: tobin_2012) as initial parameters" (1 Introduction) [from (cite: tobin_2012)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration/CASA version and imaging recipe (robust, deconvolver)
- Continuum subtraction and line-free channels
- How the PV cut was extracted and model offset/normalization
- Chemistry code name/version and HOCHUNK3D setup files

## Analysis recipe

1. **Dust temperature via MCRT**: HOCHUNK3D MCRT on 2D TSC/UCM density structure with outflow cavity  
  > "Step 1 carries out MCRT using HOCHUNK3D" (2.1 RadChemT overview)
   - software: HOCHUNK3D
   - fitting: _not stated_
   - validation: SED comparison at 1000 and 10,000 au apertures  
  > "Panel (a) and (b) show the model SEDs computed for a 1000 au (7.14$\ensuremath{''}$) aperture and a larger 10,000 au (71.4$\ensuremath{''}$) aperture, respectively." (Results and discussions: L1527 SED fits)
2. **Time-dependent chemistry**: Point-model UMIST RATE12 network with gas-grain reactions per cell  
  > "Our chemical network is taken from the UMIST database, RATE12" (2.3 Chemical model)
   - fitting: _not stated_
   - validation: _not stated_
3. **Synthetic line cubes and comparison**: RADMC-3D LTE line transfer, then primary and synthesized beam convolution, PV diagrams vs ALMA  
  > "we selected RADMC-3D, version 0.41 (cite: dullemond_2012) , to generate synthetic spectral line emission assuming LTE" (2.4)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: visual comparison of PV diagrams and integrated spectra  
  > "Comparison of the PV diagrams in Fig. [7](#fig:pv) shows an overall correspondence of the data with the RadChemT models that is encouraging." (Results and discussions: C$^{18}$O ALMA)

## Software

- **RADMC-3D** 0.41: synthetic LTE line images  
  > "RADMC-3D, version 0.41" (2.4)
- **HOCHUNK3D** : MCRT dust temperature  
  > "Step 1 carries out MCRT using HOCHUNK3D" (2.1)
- **MIRIAD** : CARMA data reduction  
  > "The data reduction and the image reconstruction were obtained using the MIRIAD software package." (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C18O line strength offset (data/TSC model) | 3.0 | not stated | dimensionless | 3 | The strength of the observed C$^{18}$O(2-1) emission is about a factor of 3.0 higher than the model prediction for the TSC model. |
| CO snowline radius | ~225 | not stated | au | 1 | until $T = 25$ K at $\sim$225 au, where the CO snowline lies |

## Qualitative findings

- TSC model reproduces PV diagrams better than UCM  
  > "the TSC model better corresponds to the observed PV diagrams" (Summary)

## Claim tuples

- H: RadChemT reproduces C18O and N2H+ line strengths | E: Synthetic cubes compared with ALMA and CARMA | R: Within factor 3.0 | F: Encouraging agreement without tuning | **supported**
- H: N2H+ anti-correlates with CO | E: Chemistry model vs CARMA maps | R: N2H+ enhanced 400-2000 au | F: Anti-correlation confirmed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Model does not reproduce C18O self-absorption at the protostar  
  > "our model does not currently reproduce the self-absorption feature" (4.5.2)
- Caveat (inferred, ours): Model is not fitted; agreement judged visually
- Caveat (inferred, ours): Only one ALMA line used

## Reproducibility

- Data public (paper): ALMA data from archive  
  > "are based on data from the ALMA archive" (3.2 ALMA data)
- Products in archive: _not stated_
- Missing: RadChemT code
- Missing: Calibration/imaging parameters
- Data volume (inferred): ~10 GB
- Score (inferred): 2/5, Code not released, ALMA is minor validation data
- Rediscovery candidate: no, Requires proprietary modeling code and results are not simple numeric measurements

## Links

- Method: (cite: Whitney_2013) (HOCHUNK3D)
- Companion: (cite: Ohashi_2014) (ALMA data)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 27,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
