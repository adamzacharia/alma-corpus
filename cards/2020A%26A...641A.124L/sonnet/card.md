# Etching glass in the early Universe: Luminous HF and H<SUB>2</SUB>O emission in a QSO-SMG pair at z = 4.7

`2020A&A...641A.124L` | Astronomy and Astrophysics 2020 | first author: Lehnert, M. D. | arXiv: 2004.04176 | DOI: 10.1051/0004-6361/201935755

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars, astrochemistry
- Question: Do HF J=1-0 and para-H2O (2_20-2_11) trace outflows and energy dissipation in the QSO and SMG of BR 1202-0725 at z=4.7?  
  > "Due to its nature, HF J=1–0 is a good tracer of molecular outflows and H$_{2}$O traces dissipation in molecular gas." (Introduction)
- Target **BR 1202-0725 (QSO and SMG)**: coordinates QSO 12:05:23.134, -07:42:32.76; SMG 12:05:22.980, -07:42:29.680 (Table 1)  
  > "the galaxy group BR 1202-0725 at z=4.69" (Introduction); "we use a luminosity distance of 4.56$\times$10$^4$ Mpc and a physical scale of 6.8 kpc arcsec$^{-1}$." (Introduction); z/distance z=4.69; D_L = 4.56e4 Mpc; 6.8 kpc/arcsec  
  > "the galaxy group BR 1202-0725 at z=4.69" (Introduction); "we use a luminosity distance of 4.56$\times$10$^4$ Mpc and a physical scale of 6.8 kpc arcsec$^{-1}$." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01489.S
- bands: Band 6  
  > "Our ALMA Cycle 3 observations in Band 6 were carried out on 2016 March 5" (2 Observations and data reduction)
- frequencies and spectral setup: four 1.875 GHz spectral windows covering 213-217.4 GHz and 228-232.5 GHz  
  > "The four 1.875 GHz spectral windows were tuned to cover the frequency ranges 213-217.4 GHz and 228-232.5 GHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 36 antennas  
  > "with 36 antennas in the C36-3 configuration" (2 Observations and data reduction)
- configurations: C36-3  
  > "with 36 antennas in the C36-3 configuration" (2 Observations and data reduction)
- baselines: 15 m to 640 m  
  > "baselines with lengths of 15m to 640m" (2 Observations and data reduction)
- angular resolution: 0.56'' x 0.49'', PA=-74 deg  
  > "a beam of 0.56$''$$\times$0.49$''$ with a PA=$-$74$^\circ$" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 77 minutes  
  > "for 77 minutes on-source integration time" (2 Observations and data reduction)
- observing dates: 2016 March 5  
  > "were carried out on 2016 March 5" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: HF J=1-0 (1232.476 GHz)
- Line: para-H2O 2_20-2_11 (1228.789 GHz)
- External data: Herschel HF and H2O line fluxes and LIR for local AGN galaxies  
  > "we extracted the HF emission line fluxes from local galaxies observed with Herschel in the sample of (cite: yang13)" (4.1 HF) [from (cite: yang13)]
- External data: CO(2-1) line widths at various beam sizes (VLA)  
  > "we compare all of the line widths of CO(2–1) with restoring beam sizes of $\ensuremath{\lesssim}$0.6$''$ from (cite: jones16)" (3 Results) [from (cite: jones16)]
- External data: [CII] redshift and line width of the SMG  
  > "we constrained this to the \[CII\] redshift (cite: carilli13)" (Table 1) [from (cite: carilli13)]
- External data: Dust temperature of 43 K, SFR ~1e3 Msun/yr, CO models  
  > "The estimated temperature of the dust continuum is about 43 K (cite: salome12)." (4.1 HF) [from (cite: salome12)]

## Processing

### Calibration

- pipeline or manual: Supplied calibration script with CASA  
  > "We used the supplied calibration script and Common Astronomy Software Applications (CASA; (cite: mcmullin07)) to reduce the data." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "To image both the continuum and line emission, we used natural weighting" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum model subtracted from visibilities, then straight-line fit to line-free channels in uv  
  > "We then subtracted the low-level residuals of the continuum by fitting a straight line to the line-free channels in the visibility data." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.56'' x 0.49'', PA=-74 deg  
  > "a beam of 0.56$''$$\times$0.49$''$ with a PA=$-$74$^\circ$" (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- SMG H2O redshift fixed to [CII] value; [CII] width used for constrained fit  
  > "we constrained this to the \[CII\] redshift (cite: carilli13)" (Table 1) [from (cite: carilli13)]
- Column density from HF absorption optical depth  
  > "Using the relation from (cite: neufeld10), we estimated the integrated column density for each realization." (4.2 HF absorption) [from (cite: neufeld10)]
- HF abundance 3.5e-8 from Orion Bar  
  > "we assumed an abundance of HF as inferred in the Orion Bar, 3.5$\times$10$^{-8}$ (cite: vandertak12a)" (4.2 HF absorption) [from (cite: vandertak12a)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum fitting
- Image size, cell size, and CLEAN threshold/masking
- CASA version
- Flux calibrator and flux scale uncertainty
- Spectral resolution/channel width of line cubes
- Exact LIR values and adopted sources for the L_HF/L_IR plot
- Full RADEX grid and fit procedure for brightness temperature matching

## Analysis recipe

1. **Reduce and image data**: Supplied calibration script in CASA; continuum model subtraction then linear fit of line-free channels; natural weighting  
  > "We used the supplied calibration script and Common Astronomy Software Applications (CASA; (cite: mcmullin07)) to reduce the data." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Phase calibrator imaged; bandpass stability ~0.1%  
  > "We imaged the phase calibrator and determined that the bandpass stability is accurate to $\sim$0.1$\%$" (Observations and data reduction)
2. **Measure continuum and line properties**: Point-source fit to continuum; Gaussian fit to H2O and HF lines  
  > "The continuum properties are derived by fitting a point source to the unresolved 216 GHz continuum of both the QSO and SMG." (3 Results); "The line properties are derived by fitting a Gaussian function to the H$_{2}$O (2$_{20}$-2$_{11})$ and HF J=1–0 lines." (3 Results)
   - fitting: Gaussian line fit; SMG H2O also fit with [CII] redshift and width  
  > "When we constrain the fit of the H$_{2}$O (2$_{20}$-2$_{11})$ in the SMG to the redshift and width of the \[CII\] line from (cite: carilli13)" (3 Results)
   - validation: _not stated_
3. **Model HF excitation in QSO**: RADEX models to match HF brightness temperature, source size = beam  
  > "we assumed that the source size was that of the beam of the ALMA observations of BR 1202-0725" (4.1 HF)
   - software: RADEX
   - parameter: N(HF)=1e15 cm-2, n_H2=1e5 cm-3, Tgas=43 K, Tbg=15.5 K, ne=10 cm-3, turbulent dispersion 5 km/s  
  > "N(HF)=10$^{15}$ cm$^{-2}$, the number density of molecular hydrogen, n$_{\rm H_2}$=10$^{5}$ cm$^{-3}$" (4.1 HF)
   - assumption: Turbulent velocity dispersion of 5 km/s as in Orion Bar  
  > "we assume a turbulent velocity dispersion of 5 km s$^{-1}$ as observed in the Orion Bar" (4.1 HF)
   - fitting: manual parameter matching to brightness temperature  
  > "We tried a variety of models to explain the brightness temperature of the HF emission, including ones used previously to model the CO emission in BR 1202-0725" (HF: Molecular gas irradiated by AGN and young stars)
   - validation: RADEX model of [CII] checks electron fraction  
  > "we used RADEX to model the brightness temperature of the \[CII\]$\lambda$ 158$\mu$m line" (4.1 HF)
4. **Bootstrap HF absorption in SMG and outflow rate limit**: 1000 realizations of data binned by 10 to 60 km/s; optical depth integrated over 0 to -400 km/s; Neufeld relation for N(HF); wind rate Mdot=pi m_H2 N(H2) V R  
  > "We did 1000 realizations of the data by binning the unsmoothed data by a factor of ten to a velocity sampling of 60 km s$^{-1}$." (4.2 HF absorption)
   - parameter: V_wind=400 km/s; R_wind=half beam size  
  > "V$_{\rm wind}$ is the terminal velocity of the wind (which we assume to be 400 km s$^{-1}$)" (4.2 HF absorption)
   - assumption: All HF in ground state; HF abundance 3.5e-8  
  > "we assumed that all of the HF was in the ground state" (4.2 HF absorption)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging  
  > "Common Astronomy Software Applications (CASA; (cite: mcmullin07)) to reduce the data" (2 Observations and data reduction)
- **RADEX** : Radiative transfer modelling of HF and [CII]  
  > "we used the code RADEX (cite: vandertak07)" (4.1 HF)
- **Starburst99** : UV flux density for radiation field estimates  
  > "estimated using Starburst99 (cite: leitherer99)" (4.1 HF)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| QSO HF J=1-0 integrated flux | 0.25 | 0.03 | Jy km/s | 2 | $S\Delta$v (Jy beam$^{-1}$ km s$^{-1}$) / 0.25$\pm$0.03 |
| QSO HF FWHM | 285 | 45 | km/s | 2 | FWHM (km s$^{-1}$) / 285$\pm$45 |
| QSO H2O FWHM | 340 | 15 | km/s | 2 | FWHM (km s$^{-1}$) / 340$\pm$15 |
| SMG H2O FWHM | 1020 | 50 | km/s | 2 | FWHM (km s$^{-1}$) / 340$\pm$15 / 1020$\pm$50 |
| QSO H2O integrated flux | 0.80 | 0.03 | Jy km/s | 2 | $S\Delta$v (Jy beam$^{-1}$ km s$^{-1}$) / 0.80$\pm$0.03 / 1.1$\pm$0.2 |
| QSO 216 GHz continuum | 4.9 | 0.2 | mJy | 2 | $S_{\textrm{216\,GHz}}$ (mJy) / 4.9$\pm$0.2 / 5.1$\pm$0.2 |
| QSO H2O redshift | 4.6948 | 0.0001 | dimensionless | 2 | $z$ / 4.6948$\pm$0.0001 |
| SMG HF-absorption N(HF) 95% limit | <=4e13 | not stated | cm-2 | 4 | N(HF)$\ensuremath{\lesssim}$4$\times$10$^{13}$ cm$^{-2}$ |
| SMG outflow rate upper limit | <=45 | not stated | Msun/yr | 4 | $\dot{\rm M}_{\rm wind}\ensuremath{\lesssim}$45 M$_{\odot}$ yr$^{-1}$ |
| Total molecular column from HF assuming solar F | ~1e22 | not stated | cm-2 | 3 | then the total molecular column is $\sim$10$^{22}$ cm$^{-2}$ |

## Qualitative findings

- HF J=1-0 is detected in emission in the QSO; L_HF/L_IR is roughly constant across AGN and the QSO.  
  > "have an approximately constant ratio of L$_\mathrm{HF}$/L$_\mathrm{IR}$ irrespective of L$_\mathrm{IR}$" (4.1 HF)
- H2O in both QSO and SMG is among the most luminous known relative to L_IR; SMG line is anomalously broad.  
  > "they are among the most, if not the most, luminous emitters of H$_{2}$O (2$_{20}$-2$_{11})$ currently known" (4.3 H2O)

## Claim tuples

- H: Is HF J=1-0 emitted by the QSO, and why? | E: Gaussian fit of HF line, RADEX modelling, comparison with Orion Bar and local AGN | R: HF emission detected, L_HF/L_IR similar to AGN and Orion Bar | F: Excitation by collisions with electrons/H2 in AGN- and star formation-irradiated gas | **partially**
- H: Does the SMG drive a molecular outflow traced by HF absorption? | E: Bootstrap of weak absorption feature | R: Mdot <~45 Msun/yr, wind efficiency <~5% | F: No strong outflow; absorption weak | **supported**
- H: Is H2O excitation consistent with IR pumping and does the SMG show dissipation? | E: Compare L_H2O/L_IR vs L_IR to local sample; compare line widths | R: Both lie above relation; SMG H2O broader than other tracers | F: IR pumping consistent, possible dissipation contribution in SMG | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Chemical pumping of HF ruled out because required N_H2 >~1e24 cm-2 exceeds CO-based estimates  
  > "Thus we can rule out a significant contribution by chemical pumping to the excitation of HF." (4.1 HF)
- How they decided it was enough: _not stated_
- Limitation (authors): The HF absorption feature is of low significance.  
  > "The significance of this feature is not high" (4.2 HF absorption)
- Limitation (authors): Part of the SMG H2O profile falls outside the frequency coverage.  
  > "the low frequency part of the profile falls past the edge of our bandpass and some of the emission is missing" (3 Results)
- Caveat (inferred, ours): Single short observation; low S/N on HF
- Caveat (inferred, ours): SMG H2O width biased by truncated bandpass
- Caveat (inferred, ours): Radiation field and RADEX estimates crude and degenerate
- Caveat (inferred, ours): L_IR choice affects slope

## Reproducibility

- Data public (paper): ALMA project 2015.1.01489.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.01489.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Cube/image parameters
- Missing: Literature L_IR values and HF fluxes for comparison sample
- Data volume (inferred): ~10-50 GB
- Score (inferred): 5/5, Public data and simple fits, but imaging and modelling details are sparse.
- Rediscovery candidate: yes, Public data, simple Gaussian fits and numeric results in Table 1; imaging details partly missing.

## Links

- Method: (cite: vandertak07) (RADEX code)
- Method: (cite: neufeld10) (HF column density relation)
- Companion: (cite: carilli13) ([CII] observations of BR 1202-0725)
- Companion: (cite: salome12) (CO modelling of BR 1202-0725)
- Companion: (cite: jones16) (VLA CO(2-1))

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
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
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
