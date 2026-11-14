# An old disk still capable of forming a planetary system

`2013Natur.493..644B` | Nature 2013 | first author: Bergin, Edwin A. | arXiv: 1303.1107 | DOI: 10.1038/nature11805

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What is the gas mass of the TW Hya disk, and can this old disk still form a planetary system?  
  > "The HD detection, combined with existing observations and detailed models, implies a disk mass $>$0.05 M$_{\odot}$, enough to form a planetary system like our own." (abstract)
- Target **TW Hya**: coordinates RA(2000) 11h01m51.91s, Dec(2000) -34d43m17.0s  
  > "TW Hya ($\alpha(2000)$ = 11$^h$01$^m$51.91$^s$; $\delta(2000)$ = $-34^{\circ}$43$'$17.0$''$)" (1. Herschel Observations); "the closest ($D \sim 55$ pc) and best studied circumstellar disk around TW Hydrae" (main text); z/distance D ~ 55 pc  
  > "TW Hya ($\alpha(2000)$ = 11$^h$01$^m$51.91$^s$; $\delta(2000)$ = $-34^{\circ}$43$'$17.0$''$)" (1. Herschel Observations); "the closest ($D \sim 55$ pc) and best studied circumstellar disk around TW Hydrae" (main text); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00001.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.7'' x 1.5'' beam (47 x 41 AU)  
  > "In Supplementary Figure 1 we show the integrated emission map with a beam size 1.7$''$ $\times 1.5''$, which corresponds to a radius of 47 $\times$ 41 AU." (Supplementary Information)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Science Verification data  
  > "we used the resolved ALMA Science Verification CO $J = 3\rightarrow 2$ data to set a limit on the gas temperature." (Supplementary Information)
- Line: CO J=3-2 (not stated)
- Other facility **Herschel PACS**: HD J=1-0 detection (and J=2-1 upper limit) and CO J=23-22 flux  
  > "Using the Herschel Space Observatory(cite: pilbratt10) PACS Spectrometer(cite: poglitsch10) we robustly detected (9$\sigma$)" (main text)
- External data: CO J=6-5 peak radiation temperature 16.9 +/- 3.2 K  
  > "The observed CO $J = 6\rightarrow 5$ peak intensity is T$_{R} = 16.9 \pm 3.2$ K(cite: qi06)" (Supplementary Information) [from Qi et al. 2006 (cite: qi06)]
- External data: Gorti et al. TW Hya thermochemical model, 0.06 Msun  
  > "The Gorti et al. TW Hya model has a disk gas mass of 0.06 M$_{\odot}$, and we used direct output from the model." (Supplementary Information) [from (cite: gorti11)]
- External data: Thi et al. TW Hya model, 0.003 Msun, reproduced  
  > "For the Thi et al. TW Hya model we use a reproduction." (Supplementary Information) [from (cite: thi10)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ALMA CO data calibration uncertainty 10%  
  > "we note that this data has a calibration uncertainty of 10%" (Supplementary Information)
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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.7'' x 1.5''  
  > "in a 1.7$''$ $\times 1.5''$ beam (radius $\sim 43$  AU)" (main text)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (CASA version, weighting, cell size, continuum handling)
- Whether the SV archive products were used as is
- Spectral setup and channel width of the CO 3-2 data
- Observing dates, configuration and time on source for ALMA
- How the central spectrum was extracted
- Collision-rate and LIME grid settings

## Analysis recipe

1. **Measure HD and CO line fluxes from Herschel PACS**: Gaussian line fit with first-order polynomial continuum; central spaxel scaled to 3x3 extraction  
  > "The line flux was obtained using a Gaussian fit. The continuum was determined by a first-order polynomial simultaneous fit in a fairly tight region around the line, avoiding the CO transition." (1. Herschel Observations)
   - software: HIPE
   - fitting: _not stated_
   - validation: Compared with PSF-corrected pipeline output, matched within 10%  
  > "We compared this to the PSF-corrected output from the pipeline, and the flux levels matched to within 10%." (1. Herschel Observations)
2. **Gas temperature from ALMA CO 3-2**: Peak radiation temperature converted via Planck function to gas kinetic temperature, assuming optically thick thermalized emission  
  > "results in an average gas kinetic temperature of $T_{gas} = 29.7$ K in the beam, assuming optically thick and thermalized emission." (Supplementary Information)
   - assumption: unity filling factor since CO is resolved  
  > "The map demonstrates that the CO emission is resolved, so we assume unity filling factor." (Supplementary Information)
   - fitting: _not stated_
   - validation: CO 6-5 gives 30.6 K  
  > "which corresponds to a gas temperature of 30.6 K." (Supplementary Information)
3. **Lower-limit gas mass from HD flux**: Optically thin HD J=1-0 mass formula with x_HD = 3e-5  
  > "Converting to mass, and assuming all is in H$_2$, $M_{gas\;disk} = 2.37 * m_{\rm H} \mathcal{N_{\rm HD}}/ x_{\rm HD}$" (Supplementary Information)
   - assumption: Deuterium abundance 1.5e-5, all in H2 and HD  
  > "Placing atoms into H$_2$ and HD, which is appropriate for much of the disk mass, provides an HD abundance relative to H$_2$ of $x_{\rm HD} = 3.0 \times 10^{-5}$." (main text)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model HD emission for thermochemical disk models**: Non-LTE radiative transfer of HD in two published disk models; mass scaled to match observed flux  
  > "we calculate the solution of the equations of statistical equilibrium including the effects of line and dust opacity using the LIME code$^{30}$." (Supplementary Information)
   - software: LIME, RADMC
   - fitting: _not stated_
   - validation: Reproduced Thi model SED and CO/13CO 3-2 within factor of two  
  > "found them to be in agreement to within a factor of two." (Supplementary Information)

## Software

- **HIPE** v8.1: Herschel PACS data reduction  
  > "The data were reduced using the Herschel Interactive Processing Environment (HIPE)(cite: hipe) v8.1 pipeline (calibration set 32)." (1. Herschel Observations)
- **LIME** : HD line radiative transfer  
  > "using the LIME code$^{30}$" (Supplementary Information)
- **RADMC** : Dust thermal structure and SED of the Thi model reproduction  
  > "These inputs were placed into RADMC(cite: dd04)" (Supplementary Information)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD J=1-0 line flux | 6.3 | 0.7 | 1e-18 W m^-2 | 1 | $F_l = (6.3 \pm 0.7) \times 10^{-18}$ W m$^{-2}$ for HD $J = 1\rightarrow 0$ (centered at 112.086 $\mu$m) |
| CO J=3-2 peak radiation temperature | 22.2 | 0.1 | K | 2 | the observed peak radiation temperature is $T_R = 22.2\pm 0.1$ K |
| Average gas temperature within 43 AU | 29.7 | not stated | K | 2 | yield an average $\mbox{$T_{gas}$}= 29.7$ K within 43 AU |
| Minimum disk mass from HD and CO T_gas | 3.9e-3 | not stated | Msun | 3 | $M_{gas\;disk} > 3.9 \times 10^{-3}$ M$_{\odot}$. |
| Gas mass within 80 AU | 0.056 | not stated | Msun | 4 | we estimate the disk gas mass within 80 AU, where the majority of HD emissions arise, is $0.056$ M$_{\odot}$. |

## Qualitative findings

- The 0.003 Msun model is ruled out; HD mass is above the low end of earlier estimates  
  > "For this model to reach the observed flux the disk mass must be increased by a factor of 20, ruling out this low disk mass." (main text)

## Claim tuples

- H: TW Hya's disk mass is large enough to form a planetary system | E: Herschel HD detection combined with ALMA CO temperature and disk models | R: Disk gas mass within 80 AU of 0.056 Msun | F: The old disk has >~0.06 Msun, several times the minimum mass solar nebula | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Low-mass model of 0.003 Msun rejected because it predicts HD flux over an order of magnitude too low  
  > "more than an order of magnitude below the detected level." (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Main uncertainty is the gas temperature structure of the disk  
  > "The main uncertainty in the masses derived here is the gas temperature structure of the disk." (main text)
- Caveat (inferred, ours): ALMA data reduction is not described
- Caveat (inferred, ours): Mass depends on the adopted models and on the assumed HD abundance
- Caveat (inferred, ours): The ALMA role is a single temperature estimate

## Reproducibility

- Data public (paper): ALMA Science Verification data acknowledged with a project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.SV." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA imaging recipe
- Missing: Gorti model output
- Missing: Herschel reduction scripts
- Data volume (inferred): Small to moderate (a few GB for ALMA SV plus Herschel data)
- Score (inferred): 3/5, The ALMA part is simple and public, but the models and reduction details are not fully given.
- Rediscovery candidate: no, The key result depends on Herschel data and unreleased model outputs; ALMA is only a minor input.

## Links

- Companion: Thi et al. 2010 (cite: thi10) (Low-mass TW Hya disk model)
- Companion: Gorti et al. 2011 (cite: gorti11) (High-mass TW Hya disk model)
- Related: Herschel OT1_ebergin_4

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 27,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
