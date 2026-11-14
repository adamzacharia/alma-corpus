# Evidence for the Disruption of a Planetary System During the Formation of the Helix Nebula

`2023AJ....165...22M` | The Astronomical Journal 2023 | first author: Marshall, Jonathan P. | arXiv: 2211.02251 | DOI: 10.3847/1538-3881/ac9d90

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, debris_disks
- Question: What is the origin of the infrared excess around the Helix Nebula central white dwarf WD 2226-210: remnant planetesimal belt, cometary cloud, or post-AGB disc?  
  > "The origin of this excess is ambiguous. It could be a remnant planetesimal belt, a cloud of comets, or the remnants of material shed during the post-asymptotic giant branch phase." (abstract)
- Target **Helix Nebula central white dwarf WD 2226-210 (NGC 7293)**: coordinates _not stated_; z/distance 201 ± 3 pc  
  > "Lying at a distance of 201 $\pm$ 3 pc, the Helix Nebula is one of the closest such systems to the Sun" (Introduction); distance from Gaia (cite: 2016Gaia; 2018Gaia)  
  > "Lying at a distance of 201 $\pm$ 3 pc, the Helix Nebula is one of the closest such systems to the Sun" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00762.S, 2016.1.00608.S
- bands: Band 6 (≃1300 µm)  
  > "ALMA in Band 6 ($\simeq1\,300~\mu$m)" (Observations)
- frequencies and spectral setup: 4 spectral windows, 7.5 GHz total; C3: two continuum windows plus 12CO(2-1) and 29SiO(5-4); C4: three continuum windows plus 12CO(2-1)  
  > "In both cases the setup consists of four spectral windows providing a total of 7.5 GHz bandwidth to study the target emission." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam FWHM 0.25" major axis (50 au at 200 pc)  
  > "with a beam FWHM $0.25\ensuremath{''}$ along the major axis (50 au at 200 pc)" (Observations)
- max recoverable scale: about 4"  
  > "The largest angular scale for the array configuration was about $4\ensuremath{''}$" (Imaging and spectral energy distribution)
- sensitivity: C3 continuum 9 µJy; C4 continuum 11 µJy  
  > "In the C3 data, the measured continuum sensitivity was 9 $\mu$Jy" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI S. Ertel; data obtained from the ESO ALMA Science Archive  
  > "These data sets were obtained from the ESO ALMA Science Archive" (Observations)
- Line: 12CO 2-1 (not stated)
- Line: 29SiO 5-4 (not stated)
- Other facility **SOFIA/HAWC+**: 53 µm imaging, non-detection of point source  
  > "SOFIA/HAWC+ Band A (53 $\mu$m) observations centred on WD 2226-210 were taken on 2017 Oct 17 for program 05_0054" (Observations)
- Other facility **Herschel/PACS**: archival 70 and 160 µm maps; compact and extended components  
  > "Deep *Herschel*/PACS small map observations of the region around the Helix Nebula’s white dwarf (PID: OT1_ksu_2, PI: K. Su)" (Observations)
- Other facility **Spitzer**: 8-70 µm photometry and IRS spectrum  
  > "The *Spitzer* data show a compact source at infrared wavelengths (from $8~\mu$m to 70 $\mu$m)" (Observations)
- External data: Spitzer IRAC/MIPS photometry and IRS spectrum  
  > "4. (cite: 2007Su)" (Table 1) [from (cite: 2007Su)]
- External data: Herschel SPIRE 250 µm and 70 µm photometry  
  > "6. (cite: 2015VandeSteene)" (Table 1) [from (cite: 2015VandeSteene)]
- External data: White dwarf Teff and log g  
  > "we have adopted the values of (cite: 1999Napiwotzki) and (cite: 2005Traulsen) to model the white dwarf spectrum" (Introduction) [from (cite: 1999Napiwotzki); (cite: 2005Traulsen)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3 (C3), 4.7.6 (C4)  
  > "using the appropriate CASA version (4.5.3 in C3 and 4.7.6 in C4)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust value not stated)  
  > "adopting Briggs weighting as a compromise between signal-to-noise and resolution" (Observations)
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

- Imaging scripts supplied by the observatory  
  > "Image reconstruction was carried out using scripts supplied by the observatory" (Observations) [from ALMA observatory scripts]
- Debris disc modelling tools for SED fitting and simulated observations  
  > "We used standard debris disc modelling tools to fit the far-infrared SED of the compact excess (cite: 2012Ertel) and simulate spatially resolved observations (cite: 2011Ertel)." (Radiative transfer modelling) [from (cite: 2012Ertel); (cite: 2011Ertel)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, masking
- Dust optical constants and composition for the radiative transfer model
- How the ALMA upper limits were measured (aperture, beam)
- Details of the radiative transfer code and its public availability
- Exact ALMA image products used (scripts are only in GitHub)

## Analysis recipe

1. **Measure compact/extended components in imaging**: Compact component fitted with wavelength-appropriate PSF, extended as 2D Gaussian; convolved model subtracted and residuals examined  
  > "The compact component is modelled as a point source using a wavelength appropriate PSF model, whilst the extended component is modelled as a 2D Gaussian profile." (Image analysis and modified blackbody fitting)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit SED with modified blackbodies**: 10,000 random parameter sets of Tbb, lambda0, beta; models violating upper limits discarded; error-weighted least squares on remainder  
  > "we create 10,000 sets of values drawn from the appropriate ranges for each parameter ($T_{bb}$, $\lambda_{0}$, $\beta$)" (Image analysis and modified blackbody fitting)
   - parameter: Compact temperature fixed at 102 K; beta between 0 and 4  
  > "is fixed as 102 K and the temperature of the extended component must be lower than the compact component." (Image analysis and modified blackbody fitting)
   - fitting: Monte Carlo draw plus error-weighted least squares  
  > "we calculated the best-fit values for the two components in combination through error weighted least-squares fitting" (Image analysis and modified blackbody fitting)
   - validation: _not stated_
3. **Derive gas mass upper limits from CO and SiO non-detections**: 5-sigma integrated line flux limits assuming optically thin LTE  
  > "Assuming a line width of 10 km/s (typical for debris discs), optically thin emission, and local thermodynamic equilibrium for the gas ($T_{\rm gas} = 100~K$)" (Imaging and spectral energy distribution)
   - assumption: line width 10 km/s, Tgas = 100 K  
  > "Assuming a line width of 10 km/s (typical for debris discs)" (Imaging and spectral energy distribution)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radiative transfer modelling of dust grain size and distribution**: Optically thin disc models with power-law size distribution; simulated ALMA image compared to upper limit  
  > "For each model fit to the SED, a spatially resolved ALMA image of the emission was simulated and compared to the ALMA upper limit." (Radiative transfer modelling)
   - parameter: Models A-D with Rin 30-60 au, Rout 50-90 au, amin 2-60 µm, gamma 3.5, Mdust 8-10e-3 Mearth  
  > "| Minimum grain size, $a_{\rm min}$ ($\mu$m) | 2 | 60 | 60 | 10 |" (Table 3)
   - assumption: optically thin dust; power-law size distribution  
  > "We assume the dust emission is optically thin" (Radiative transfer modelling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3 (C3), 4.7.6 (C4): ALMA calibration and reduction  
  > "Calibration and reduction of the ALMA observations were carried out in CASA" (Observations)
- **astropy** : Python analysis  
  > "This paper has made use of the Python packages astropy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.3 mm compact 3-sigma upper limit | <0.030 | not stated | mJy | 0 | / 1300.0     / $<$ 0.030         / ALMA Band 6       / 5    / |
| Herschel 70 µm compact flux density | 36.0 | 4.5 | mJy | 1 | with a flux density of 36 $\pm$ 4.5 mJy |
| Herschel 70 µm extended flux density | 222 | 12 | mJy | 1 | with a flux density of 222 $\pm$ 12 mJy |
| CO gas mass upper limit | 1.2e-4 | not stated | Earth masses | 3 | gas masses of 1.2$\times10^{-4}~M_{\oplus}$ in CO |
| Extended component temperature | 50 | 6 | K | 2 | / Temperature (K)        /      102      /  50 $\pm$ 6   / |
| Observed dust mass | 0.13 | not stated | Earth masses | 4 | given the observed dust mass of 0.13 $M_{\oplus}$ |
| Hale-Bopp equivalent comets disrupted per year | 5,000 | not stated | per year | 0 | therefore requires 5,000 Hale-Bopp equivalent comets per year being completely disrupted |

## Qualitative findings

- ALMA continuum and CO/SiO line emission are non-detections  
  > "The ALMA millimetre-wavelength observations are likewise non-detections in both continuum and line emission." (Observations)

## Claim tuples

- H: The excess is a remnant post-AGB circumbinary disc | E: CO/SiO limits plus SED grain-size constraint | R: No gas detected; grains too small compared to the 60 µm blow-out size | F: Post-AGB disc discarded | **supported**
- H: The excess is a compact remnant planetesimal belt | E: SED and radiative transfer models compared to ALMA upper limit | R: Steep SED needs small grains well below blow-out size | F: Debris disc disfavoured | **supported**
- H: The dust is delivered by a cometary cloud | E: Dust mass and lifetime arguments | R: About 5,000 Hale-Bopp equivalent comets per year | F: Disrupted planetary system is the preferred origin | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Post-AGB disc and in-situ planetesimal belt destruction rejected  
  > "The observed dust emission is inconsistent with either a remnant of the post-AGB envelope or the in-situ collisional destruction, or sublimation, of remnant planetesimals" (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Nature of the extended component is unconstrained  
  > "The available data offer no real constraint on the nature of the extended component seen in the *Herschel* 70 $\mu$m map" (Imaging and spectral energy distribution)
- Caveat (inferred, ours): Cometary scenario is argued from order-of-magnitude estimates without a formal model comparison
- Caveat (inferred, ours): Radiative transfer fits are by-eye models with no uncertainties
- Caveat (inferred, ours): The ALMA data are only upper limits and blind to extended emission
- Caveat (inferred, ours): Inconsistent numbers (SiO listed twice, line sensitivities differ between sections)

## Reproducibility

- Data public (paper): ALMA, Herschel and SOFIA data from public archives; scripts and models on GitHub  
  > "The exact reduction steps used can be inferred from the scripts available, along with the reduced data, analysis scripts, and models, in a GitHub repository" (Observations)
- Products in archive: _not stated_
- Code: GitHub repository with scripts, reduced data and models  
  > "in a GitHub repository" (Observations)
- Missing: Dust opacity and composition
- Missing: Imaging parameters for ALMA
- Missing: Radiative transfer code details
- Data volume (inferred): ~20-50 GB for the two ALMA datasets
- Score (inferred): 4/5, Public data and a GitHub repository, but the paper gives few modelling and imaging details; ALMA is non-detection only.
- Rediscovery candidate: no, ALMA yields only upper limits and the main conclusions are qualitative modelling inferences.

## Links

- Method: (cite: 2012Ertel) (SED modelling tool)
- Method: (cite: 2011Ertel) (simulating spatially resolved observations)
- Companion: (cite: 2007Su) (Spitzer discovery of the excess)
- Companion: (cite: 2015VandeSteene) (Herschel observations of the nebula)
- Related: FEARLESS collaboration

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 35,
  "rate": 0.479
 },
 "evidence_ok": true
}
```
