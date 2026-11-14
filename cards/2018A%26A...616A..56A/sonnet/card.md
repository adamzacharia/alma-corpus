# Magnetic field in a young circumbinary disk

`2018A&A...616A..56A` | Astronomy and Astrophysics 2018 | first author: Alves, F. O. | arXiv: 1805.00494 | DOI: 10.1051/0004-6361/201832935

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Which mechanism (self-scattering, radiative alignment, or magnetic alignment) produces the multi-band polarization in the BHB07-11 circumbinary disk?  
  > "Our goal is to discern the main mechanism responsible for the polarization through comparison between our observations and model predictions for each of the proposed mechanisms." (abstract)
- Target **BHB07-11**: coordinates not stated (VLA 5a at RA 17:11:23.1057, Dec -27:24:32.818)  
  > "a Class I object embedded in the darkest parts of the Pipe Nebula, a quite quiescent complex of interstellar clouds located at a distance of 145 pc from the Sun" (1 Introduction); z/distance 145 pc  
  > "a Class I object embedded in the darkest parts of the Pipe Nebula, a quite quiescent complex of interstellar clouds located at a distance of 145 pc from the Sun" (1 Introduction); distance from Alves07  
  > "a Class I object embedded in the darkest parts of the Pipe Nebula, a quite quiescent complex of interstellar clouds located at a distance of 145 pc from the Sun" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00291.S, 2016.1.01186.S
- bands: Band 3 (97.5 GHz), Band 6 (233 GHz), Band 7 (343.5 GHz)  
  > "We used the atmospheric windows centered at 97.5 GHz (Band 3), 233 GHz (Band 6) and 343.5 GHz (Band 7)." (2.1 ALMA)
- frequencies and spectral setup: four spectral windows in TDM, 64 channels of 31.5 kHz, full polarization  
  > "The spectral setup have four spectral windows in Time Domain Mode (TDM, 64 channels with a width of 31.5 kHz)" (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: mean ~28.3 AU; beams 0.22x0.17, 0.26x0.15, 0.21x0.18 arcsec  
  > "This corresponds to a mean spatial resolution of $\sim28.3$ AU." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: Stokes I rms 0.012, 0.15, 0.52 mJy/beam (Bands 3, 6, 7)  
  > "The total intensity (Stokes I) maps have a *rms* noise level of 0.012, 0.15 and 0.52 mJy beam$^{-1}$ for bands 3, 6 and 7, respectively." (2.1 ALMA)
- time on source: Band 6 total 3 hours in three EBs  
  > "The total observing time was 3 hours divided in three EBs of 1 hour each." (2.1 ALMA)
- observing dates: Band 3: 14 Nov 2017; Band 6: 19 Sep 2015; Band 7: 17 May 2017  
  > "The Band 3 observations were performed in two Execution Blocks (EBs) on November 14, 2017." (2.1 ALMA); "The Band 7 observations were carried out on the 17$^{\mathrm{th}}$ May of 2017" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 34.5 GHz continuum resolving VLA 5 into a binary (VLA 5a, 5b)  
  > "The new observations resolved VLA 5 in a binary system, VLA 5a" (2.2 VLA)
- External data: Disk inclination/PA, H2CO kinematics and 1.3 mm continuum from earlier non-polarimetric study  
  > "consistent with the 1.3 mm continuum map obtained in non- polarimetric mode by (cite: Alves17)" (3 Polarization properties) [from (cite: Alves17)]
- External data: Self-scattering plus radiative alignment model predictions (a_max=150 um)  
  > "predicted by self-scattering plus radiative alignment in a protoplanetary disk with $a_{\mathrm{max}} = 150$ $\mu$m" (6.1 Self-scattering) [from (cite: Kataoka17)]
- Simulation/model as data: DustPol/ARTIST synthetic polarization maps of Shu07 magnetized disk, passed through CASA simobserve/simanalyze  
  > "we used the DustPol module of the ARTIST software (cite: Padovani12; Jorgensen14) to build a disk model" (7.2 Alignment with magnetic field)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 3 J1733-1304; Band 6 Titan; Band 7 J1733-1304  
  > "The absolute flux calibration was obtained with observing scans on Titan" (2.1 ALMA)
- flux scale uncertainty: ~10% (Band 3)  
  > "the uncertainty on the absolute flux density scale is expected to be $\sim 10$%" (2.1 ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: common uv range 27-1310 klambda for all bands  
  > "we produced cleaned maps using a *uv* range that is common for all bands, from 27 to 1310 k$\lambda$" (2.1 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "We applied primary beam correction to account for the decreasing instrument sensitivity away from the center of the primary beam." (2.1 ALMA)
- array combination: _not stated_
- smoothing: Band 3 and 7 Stokes I smoothed to common beam for spectral index  
  > "we have smoothed the corresponding Stokes I maps to a common beam" (4 Spectral properties)
- final beam: 0.22x0.17 (PA -61.46), 0.26x0.15 (PA -85.65), 0.21x0.18 (PA -72.79) arcsec  
  > "synthesized beams of $0.22\ensuremath{''} \times 0.17\ensuremath{''}$ (position angle = $-61.46\ensuremath{^\circ}$)" (2.1 ALMA)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and whether ALMA pipeline or manual calibration was used
- tclean parameters (weighting/robust, deconvolver, cell, image size, masks, niter, threshold)
- polarization calibration details (leakage solutions, calibration of polarization angle)
- DustPol input parameters (density, temperature, grain properties, disk size)
- how model maps were compared (pixel selection, error on PA)
- how the Bands 3 and 7 spectral index maps were aligned and noise-clipped

## Analysis recipe

1. **Image Stokes I, Q, U in common uv range**: cleaned maps with common uv range 27-1310 klambda, primary beam corrected  
  > "we produced cleaned maps using a *uv* range that is common for all bands, from 27 to 1310 k$\lambda$" (2.1 ALMA)
   - software: CASA
   - parameter: vectors drawn at S/N=5 in polarized intensity  
  > "we adopt a signal-to-noise ratio of 5 in polarized intensity for all bands in order to produce vector maps" (2.1 ALMA)
   - fitting: _not stated_
   - validation: calibrator polarization compared to ALMA Calibrator Catalogue  
  > "The mean polarization fraction of $2.4$% is consistent with earlier measurements of this object according to the ALMA Calibrator Source Catalogue." (2.1 ALMA)
2. **Derive spectral index and beta**: Smooth Band 3 and 7 Stokes I to common beam, compute alpha from flux difference, beta = alpha - 2  
  > "We computed the dust opacity index $\beta$ assuming an optically thin and Rayleigh-Jeans regime for the disk edge ($\beta = \alpha - 2$)" (4 Spectral properties)
   - assumption: optically thin, Rayleigh-Jeans  
  > "assuming an optically thin and Rayleigh-Jeans regime for the disk edge" (4 Spectral properties)
   - fitting: _not stated_
   - validation: caveats on optical depth and RJ departure discussed  
  > "An accurate estimation of maximum grain size is affected by departures from the Rayleigh-Jeans regime and changes in optical depth through the disk." (4 Spectral properties)
3. **Test radiative alignment model**: synthetic polarization maps for VLA 5a, 5b, and 1/d^2 combination; inclination and PA free; compare mean deltaPA  
  > "We used the disk inclination and position angle in the plane-of-sky as free parameters." (7.1 Alignment with radiation field)
   - fitting: free inclination and PA; best fit VLA 5a: i=48 deg, PA=138 deg  
  > "from which a disk inclination of 48$^\circ$ and position angle of 138$^\circ$ were derived (fit error of $\pm 15\ensuremath{^\circ}$)" (7.1 Alignment with radiation field)
   - validation: residual deltaPA histogram  
  > "The histogram in Fig. [7](#fig:rf) shows the distribution of residuals ($\delta$PA)" (7.1 Alignment with radiation field)
4. **Fit magnetic field model**: DustPol models of Shu07 disk at 343 GHz, i=52 deg, rotated 138 deg, varying k=Bp/Bphi, processed with simobserve/simanalyze with Band 7 configuration; compared to 90-deg rotated PA  
  > "We ran DustPol assuming a frequency of 343 GHz as in Band 7 observations." (7.2 Alignment with magnetic field)
   - software: ARTIST DustPol, CASA simobserve/simanalyze
   - parameter: field inclination 55 deg; k free  
  > "we adopted $i=55$$^\circ$ and considered $k$ as a free parameter" (7.2 Alignment with magnetic field)
   - assumption: Shu et al. 2007 viscously accreting disk with advected, twisted field  
  > "we assumed the model by (cite: Shu07) of a viscously accreting disk surrounding a low-mass protostar" (7.2 Alignment with magnetic field)
   - fitting: grid in k from 1 to infinity; best k=3 by mean residual deltaPA  
  > "The best fit is represented by the $k=3$ case, with mean residual $\delta$PA$= 23.4\ensuremath{^\circ}$" (7.2 Alignment with magnetic field)
   - validation: consistency with sense of rotation from molecular line maps  
  > "Our results are consistent with the rotation seen in our molecular line maps" (7.2 Alignment with magnetic field)

## Software

- **CASA** : VLA pipeline calibration; simobserve/simanalyze of models  
  > "The calibration was performed using the standard CASA VLA pipeline." (2.2 VLA)
- **ARTIST (DustPol)** : synthetic polarization maps of magnetized disk  
  > "we used the DustPol module of the ARTIST software (cite: Padovani12; Jorgensen14)" (7.2 Alignment with magnetic field)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean polarization fraction Band 3 | 7.9 | 0.8 | % | 1 | the mean polarization fraction is 7.9$\pm$0.8, 5.3$\pm$0.3 and 3.5$\pm$0.1% for bands 3, 6 and 7, respectively |
| Mean polarization fraction Band 6 | 5.3 | 0.3 | % | 1 | the mean polarization fraction is 7.9$\pm$0.8, 5.3$\pm$0.3 and 3.5$\pm$0.1% for bands 3, 6 and 7, respectively |
| Mean polarization fraction Band 7 | 3.5 | 0.1 | % | 1 | the mean polarization fraction is 7.9$\pm$0.8, 5.3$\pm$0.3 and 3.5$\pm$0.1% for bands 3, 6 and 7, respectively |
| Mean spectral index Band 3-7 | 3.01 | 0.02 | dimensionless | 2 | The spectral index has a mean value of $3.01 
\pm 0.02$ with a minimum $2.67 \pm 0.01$ near the center of the disk. |
| Mean dust opacity index beta | ~1.0 | not stated | dimensionless | 2 | found $\langle\beta\rangle \sim 1.0$ |
| VLA 5a flux density (34.5 GHz) | 0.32 | 0.03 | mJy | 0 | Their flux densities are $0.32\pm0.03$ and $0.23\pm0.03$ mJy, respectively. |
| Best magnetic model mean residual deltaPA (k=3) | 23.4 | sigma = 7.5 deg | deg | 4 | The best fit is represented by the $k=3$ case, with mean residual $\delta$PA$= 23.4\ensuremath{^\circ}$ and standard deviation $\sigma=7.5\ensuremath{^\circ}$. |
| Radiative alignment (VLA 5a) mean deltaPA | 20.2 | sigma = 6.9 deg | deg | 3 | with mean $\delta$PA$= 20.2\ensuremath{^\circ}$ and $\sigma = 6.9\ensuremath{^\circ}$ |

## Qualitative findings

- Polarization morphology is a horseshoe peaking in the southwest and is very similar across all three bands  
  > "The polarization properties of the three bands are remarkably similar" (3 Polarization properties)

## Claim tuples

- H: Is the polarization due to self-scattering? | E: Compare observed PA pattern, polarization degree and frequency dependence with self-scattering predictions | R: Pattern inconsistent; polarization at least ~4 times higher than predicted; degree varies by 2.0 over a frequency factor 3.5 | F: Self-scattering ruled out | **supported**
- H: Is the polarization due to radiative alignment by the binary? | E: Synthetic maps for VLA 5a, 5b and combined | R: VLA 5a best, mean deltaPA 20.2 deg, but pattern and levels inconsistent with Tazaki17 | F: Cannot be ruled out but unlikely | **partially**
- H: Is the polarization due to magnetically aligned grains? | E: DustPol models with varying Bp/Btor | R: k=3 best, deltaPA 23.4 deg | F: Data consistent with magnetic alignment with poloidal about 3 times toroidal | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Compare multi-band maps to disentangle mechanisms with different wavelength dependence  
  > "This example stresses the importance of comparing maps at different wavelengths in order to disentangle the possible different contributions to the observed polarization." (1 Introduction)
- Alternative: Self-scattering rejected; radiative alignment not ruled out but disfavored  
  > "Although we cannot rule out alignment with the radiation field, our analysis shows that the observed polarization is consistent with being produced by magnetically aligned grains." (7.3 Interpreting the modelling results)
- How they decided it was enough: _not stated_
- Limitation (authors): Residuals likely from binary-induced field twisting not in the model; optical depth affects grain size estimate  
  > "The residual is likely due to the internal twisting of the magnetic field due to the binary system dynamics, which is not considered in our model." (abstract)
- Caveat (inferred, ours): Magnetic and radiative models fit about equally (23.4 vs 20.2 deg), so discrimination is weak
- Caveat (inferred, ours): Only Band 7 compared with models; no formal fit statistics
- Caveat (inferred, ours): Optical depth could bias beta
- Caveat (inferred, ours): Band 7 model compared only at one frequency

## Reproducibility

- Data public (paper): data archived in ALMA Science Archive  
  > "The data reported in this paper are archived in the ALMA Science Archive." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: DustPol model parameters
- Missing: Polarization calibration details
- Missing: VLA data project code
- Data volume (inferred): ~100-300 GB raw for three bands
- Score (inferred): 3/5, Public data and clear workflow, but imaging and model parameters are largely unstated.
- Rediscovery candidate: no, Imaging and model settings are incomplete, and the model comparison is not fully specified.

## Links

- Method: (cite: Shu07) (magnetized accretion disk model used)
- Method: (cite: Padovani12; Jorgensen14) (ARTIST/DustPol radiative transfer)
- Companion: (cite: Alves17) (earlier non-polarimetric study of BHB07-11)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 68,
  "stated": 41,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
