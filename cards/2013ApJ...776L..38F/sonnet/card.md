# A Significantly Low CO Abundance toward the TW Hya Protoplanetary Disk: A Path to Active Carbon Chemistry?

`2013ApJ...776L..38F` | The Astrophysical Journal Letters 2013 | first author: Favre, Cécile | arXiv: 1309.5370 | DOI: 10.1088/2041-8205/776/2/L38

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the disk-averaged gas-phase CO abundance relative to H2 in the TW Hya disk, derived from HD (1-0) and C18O (2-1)?  
  > "we report the CO abundance relative to H$_{2}$ derived toward the circumstellar disk of the T-Tauri star TW Hya from the HD ($1-0$) and C$^{18}$O ($2-1$) emission lines." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 51 pc  
  > "towards the closest T-Tauri system, TW Hya, at 51 pc (cite: Mamajek:2005)" (Introduction); distance from Mamajek 2005  
  > "towards the closest T-Tauri system, TW Hya, at 51 pc (cite: Mamajek:2005)" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 6 (12CO 2-1) science verification data; main C18O data from SMA  
  > "Using the resolved Band 6 TW Hya ALMA Science Verification (S.V.) observations of $^{12}$CO ($2-1$)" (Analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA 12CO beam 2.83'' x 2.39'' (PA=44 deg)  
  > "within a 2$\ensuremath{''}83\times2\ensuremath{''}$39 ($\rm{P.A.}=44\ensuremath{^\circ}$) beam" (Analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C18O 2-1 (219.560 GHz)
- Line: HD 1-0 (2674.986 GHz)
- Other facility **SMA**: C18O and 13CO (2-1) spectra, integrated fluxes  
  > "The resulting synthesized beam sizes were $2.8\ensuremath{''}\times1.9\ensuremath{''}$" (Observations and data reduction)
- Other facility **Herschel PACS**: HD (1-0) line  
  > "The HD ($1-0$) line was observed by the Herschel Space Observatory Photodetector Array Camera and Spectrometer" (abstract)
- External data: Disk physical structure model of TW Hya  
  > "with the (cite: Gorti:2011) physical structure employed in the original modeling effort of (cite: Bergin:2013)" (Hints from Disk Models) [from Gorti et al. 2011 (cite: Gorti:2011)]
- External data: HD reduction, flux and excitation models  
  > "Further informations concerning both reduction and line analysis are presented in B13." (Observations and data reduction) [from Bergin et al. 2013 (cite: Bergin:2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Callisto (SMA)  
  > "Flux calibration was done using observations of Titan and Callisto." (Observations and data reduction)
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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.8''x1.9'' (PA=-1.3 deg) for C18O  
  > "The resulting synthesized beam sizes were $2.8\ensuremath{''}\times1.9\ensuremath{''}$ ($\rm{PA=-1.3\ensuremath{^\circ}}$)" (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- HD data reduction and line analysis  
  > "Further informations concerning both reduction and line analysis are presented in B13." (Observations and data reduction) [from B13 = Bergin et al. 2013 (cite: Bergin:2013)]

### Not stated but needed to reproduce (our reading)

- Herschel HD flux extraction details
- Exact f_u values used per temperature
- Details of ALMA Band 6 data processing

## Analysis recipe

1. **Line opacity of C18O**: Compare 13CO and C18O flux ratio with assumed isotope ratios  
  > "we compare C$^{18}$O ($2-1$) to $^{13}$CO ($2-1$) and find the disk-averaged $^{13}$CO/C$^{18}$O flux ratio is $\sim$3.3 $\pm$ 0.9." (Line Opacity)
   - assumption: 12C/13C=70, 16O/18O=557  
  > "assuming isotope ratios of $\rm{^{12}C/^{13}C=70}$ and $\rm{^{16}O/^{18}O=557}$ for the local ISM" (Line Opacity)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive chi(CO) from LTE flux ratio**: Ratio of upper-state populations of C18O and HD, with chi(HD)=3e-5, varying HD temperature 20-60 K and C18O at 20 K  
  > "we compute the $\chi$(CO) from Eq. [\[eq:abu\]](#eq:abu) assuming a C$^{18}$O gas temperature of $T_g=20$ K and varying the HD emitting temperature" (Mass and Model Independent chi(CO) Determination)
   - software: LIME
   - assumption: LTE, optically thin lines, co-spatial emission  
  > "assuming the emission is co-spatial and in LTE" (Analysis)
   - fitting: _not stated_
   - validation: Compared with LIME disk-model prediction and 12CO peak beam temperature  
  > "to match the observed flux, $\chi$(C$^{18}$O) needs to be reduced to $\sim7\times10^{-9}$" (Hints from Disk Models)

## Software

- **MIRIAD** : imaging and deconvolution of SMA data  
  > "imaging and deconvolution were accomplished in the MIRIAD software package" (Observations and data reduction)
- **MIR** : SMA calibration  
  > "Routine calibration tasks were performed using the MIR software package" (Observations and data reduction)
- **LIME** : non-LTE modeling of C18O emission in disk model  
  > "we adopt the non-LTE code *LIME* (cite: Brinch:2010)" (Hints from Disk Models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk-averaged chi(CO) | (0.1-3)e-5 | not stated | dimensionless | 2 | we measure a disk-averaged gas-phase CO abundance relative to H$_2$ of $\chi{\rm(CO)}=(0.1-3)\times10^{-5}$ |
| chi(CO) for T_g(HD)~40 K | 7e-6 | not stated | dimensionless | 2 | the resulting CO abundance is only ${\rm{\chi(CO)=7\times10^{-6}}}$ |
| 13CO/C18O flux ratio | 3.3 | 0.9 | dimensionless | 1 | the disk-averaged $^{13}$CO/C$^{18}$O flux ratio is $\sim$3.3 $\pm$ 0.9 |
| tau(C18O) | ~0.36 | not stated | dimensionless | 1 | $\rm{\tau(C^{18}O)\sim0.36}$ |

## Qualitative findings

- CO is likely an unreliable H2 mass tracer  
  > "CO may be an unreliable tracer of H$_2$ gas mass." (abstract)

## Claim tuples

- H: TW Hya warm layer has the canonical CO abundance of 1e-4 | E: Compare C18O (2-1) and HD (1-0) fluxes under LTE | R: chi(CO)=(0.1-3)e-5 | F: CO is depleted by at least an order of magnitude, perhaps via chemical carbon sink | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Freeze-out, photodissociation and different emitting regions considered and judged unlikely to explain low chi(CO)  
  > "the reduced measured $\chi$(CO) in the gas-phase is unlikely to be the result of freeze-out" (Freeze-out)
- How they decided it was enough: _not stated_
- Limitation (authors): HD may be optically thick, so chi(CO) would be an upper limit  
  > "the possibility of optically thick HD emission still remains" (Opacity)
- Caveat (inferred, ours): Disk-averaged LTE analysis with large temperature uncertainty
- Caveat (inferred, ours): Results depend on the HD abundance and the Gorti model

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Herschel HD data reduction
- Missing: SMA flux details beyond Table 1
- Data volume (inferred): small (<10 GB)
- Score (inferred): 3/5, The main data are SMA and Herschel; ALMA is used only for a supporting 12CO temperature, and the recipe leans on B13.
- Rediscovery candidate: no, The ALMA role is minor and the key data are SMA and Herschel.

## Links

- Method: Bergin et al. 2013 (cite: Bergin:2013) (HD reduction and line analysis)
- Companion: Qi et al. 2006 (cite: Qi:2006) (earlier SMA CO data)
- Related: ALMA Science Verification TW Hya

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00001.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 23,
  "rate": 0.371
 },
 "evidence_ok": true
}
```
