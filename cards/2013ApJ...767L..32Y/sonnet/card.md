# ALMA Observations of the Galactic Center: SiO Outflows and High-mass Star Formation near Sgr A*

`2013ApJ...767L..32Y` | The Astrophysical Journal Letters 2013 | first author: Yusef-Zadeh, F. | arXiv: 1303.3403 | DOI: 10.1088/2041-8205/767/2/L32

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, star_formation
- Question: Do SiO (5-4) clumps inside the circumnuclear ring around Sgr A* trace protostellar outflows, indicating ongoing massive star formation near the black hole?  
  > "The SiO clumps are interpreted as highly embedded protostellar outflows, signifying an early stage of massive star formation near Sgr A\* in the last $10^4-10^5$ years." (abstract)
- Target **Sgr A* region (inner ~1', 7-point mosaic)**: coordinates 17h45m40.04s, -29d00m28.12s (J2000)  
  > "the observations consisted of a 7-point mosaic at the position of Sgr A\*: $(\alpha, \delta)= 17^h 45^m 40^s.04, -29^{\circ} 0' 28''.12$." (Observations and Data Reduction); "assuming that the distance to the Galactic center is 8.5 kpc" (Introduction); z/distance 8.5 kpc (assumed)  
  > "the observations consisted of a 7-point mosaic at the position of Sgr A\*: $(\alpha, \delta)= 17^h 45^m 40^s.04, -29^{\circ} 0' 28''.12$." (Observations and Data Reduction); "assuming that the distance to the Galactic center is 8.5 kpc" (Introduction); distance from assumed in text  
  > "the observations consisted of a 7-point mosaic at the position of Sgr A\*: $(\alpha, \delta)= 17^h 45^m 40^s.04, -29^{\circ} 0' 28''.12$." (Observations and Data Reduction); "assuming that the distance to the Galactic center is 8.5 kpc" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: 4 basebands, 1.875 GHz each, 3840 channels each; centered ~216.2, 218.0, 231.9, 233.7 GHz  
  > "Four basebands of total width 1.875 GHz were used with the high spectral resolution, which contained 3840 channels each." (Observations and Data Reduction); "The spectral windows were centered at roughly: 216.2 GHz, 218.0 GHz, 231.9 GHz, and 233.7 GHz." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: twelve 12 m antennas only  
  > "Utilizing only twelve of the 12 m antennas, the observations consisted of a 7-point mosaic" (Observations and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.61'' x 0.97''  
  > "ALMA observations of the Galactic center with spatial resolution $2.61''\times0.97''$" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: June 26, 2011  
  > "The data were obtained through the ALMA Science Verification process on June 26, 2011." (Observations and Data Reduction)
- pi or archival as stated: ALMA Science Verification data  
  > "The data were obtained through the ALMA Science Verification process on June 26, 2011." (Observations and Data Reduction)
- Line: SiO 5-4 (217.105 GHz)
- Other facility **CARMA**: SiO (2-1) mosaic data, 8.87''x4.56'' and 6.74 km/s resolution, for LVG modeling  
  > "The spatial resolution and spectral resolutions of the final maps are $8.87\ensuremath{''}\times 4.56\ensuremath{''}$ and 6.74 km s$^{-1}$, respectively." (Observations and Data Reduction)
- Other facility **VLT**: 3.6 micron and K-band images (provided by S. Gillessen) used for IR comparison  
  > "Figure 1c shows the positions of these highly redshifted velocity clumps on a 3.6$\mu$m image taken with the VLT." (Results and Discussion)
- External data: SiO (5-4) luminosities and widths of low- and high-mass YSO outflows, rescaled by factors of 1500 and 170  
  > "have been corrected by multiplying by 1500 and 170, respectively (A. Gibb, private communication)." (Results and Discussion) [from Gibb 2004, 2007]
- External data: YSO candidate positions (8 micron) used for SED fitting  
  > "positional uncertainty of 1.18$''$ at 8$\mu$m (Ramirez )" (Results and Discussion) [from Ramirez et al. 2008]
- External data: 3.6 cm continuum, HCN CNR map and 3 cm continuum images used as context  
  > "surrounded by the CNR as traced by HCN line emission (Christopher )." (Results and Discussion) [from Christopher et al. 2005]
- Simulation/model as data: Grid of YSO SED models  
  > "comparing a set of SEDs enhanced by a large grid of YSO models (Whitney ; Robitaille )" (Results and Discussion)

## Processing

### Calibration

- pipeline or manual: Calibration by Science Verification team in CASA  
  > "The editing and calibration of the data was carried out by the Science Verification team in CASA." (Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan flux; 3C279 bandpass/phase; NRAO 530 periodic  
  > "Titan was initially used as the flux calibrator and 3C279 as the initial bandpass and phase calibrator." (Observations and Data Reduction)
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
- continuum subtraction: linear continuum fitted to line-free channels and subtracted before CLEAN  
  > "A linear continuum was fitted and subtracted from the line-free channels before CLEANing." (Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: averaged by factor 5 to 3.371 km/s (2.441 MHz) from 0.674 km/s raw  
  > "The data was averaged by a factor of five to achieve a spectral resolution of 3.371 km s$^{-1}$  (2.441 MHz)" (Observations and Data Reduction)
- final beam: 2.61'' x 0.97''  
  > "ALMA observations of the Galactic center with spatial resolution $2.61''\times0.97''$" (abstract)
- final rms: _not stated_

### Inherited from earlier work

- Imaging done by modifying the supplied SV imaging script  
  > "The imaging was completed by modifying the supplied imaging script." (Observations and Data Reduction) [from ALMA Science Verification team script]

### Not stated but needed to reproduce (our reading)

- CASA version
- Weighting/robust, cell size, image size, CLEAN threshold and masks
- Line-free channel ranges and continuum fit details
- Modifications made to the SV imaging script
- How clumps were identified and spectra extracted (apertures)
- LVG code, abundance and collision-rate inputs
- CARMA calibration, imaging, and how it was matched to ALMA resolution
- Details of SED fitting setup (extinction, distance, apertures, photometry)
- Flux scale uncertainty

## Analysis recipe

1. **image SiO (5-4) cube**: Continuum subtraction, CLEAN, spectral averaging by 5 from SV data  
  > "A linear continuum was fitted and subtracted from the line-free channels before CLEANing." (Observations and Data Reduction)
   - software: CASA
   - parameter: 3.371 km/s channels  
  > "The data was averaged by a factor of five to achieve a spectral resolution of 3.371 km s$^{-1}$  (2.441 MHz)" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Checked amplitude/phase at edge channels when combining first two basebands  
  > "care was taken to note any changes in amplitude and phase at the edge channels in combining the two windows." (Observations and Data Reduction)
2. **fit clump line profiles**: Gaussian fits for peak, center velocity, FWHM; FWZI listed  
  > "Gaussian fitted central velocity, FWHM linewidths, and FWZI of the 11 sources labeled in Figure 2." (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
3. **constrain density and column density with LVG**: LVG modeling of SiO (5-4)/(2-1) for clumps 1 and 11 with CARMA data  
  > "We used the Large Velocity Gradient (LVG) model to constrain the density and column density." (Results and Discussion)
   - parameter: beam filling factor 0.5; 1 mJy = 20.5 mK (5-4) and 7.96 mK (2-1)  
  > "Assuming that the beam filling factor is 0.5, thus, 1 mJy is equivalent to T$_{\rm MB}=20.5$ and 7.96 mK for SiO (5-4) and SiO (2-1) data, respectively" (Results and Discussion)
   - assumption: kinetic temperature 100-200 K  
  > "Multi-transition CO and NH$_3$ studies of the inner 2pc derive kinetic temperature 100-200K" (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **test boundedness and compare with YSO outflows**: Velocity gradients and dynamical vs collapse timescales; SiO luminosity vs FWZI compared with Gibb YSO samples  
  > "Figure 4 compares the SiO (5-4) luminosity and FWZI for the detected sources inside the molecular ring, to those for samples of low-mass and high-mass YSOs" (Results and Discussion)
   - parameter: clump radius 0.03 pc, n_H2 = 1e6 cm^-3 for mass  
  > "using clump radius 0.03pc (0.79$''$) for an unresolved sources and n$_{\rm 
H_2}=10^6$ cm$^{-3}$." (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **SED fitting of YSO candidates**: Fit candidate SEDs with YSO model grid  
  > "The SEDs of these sources are analyzed by comparing a set of SEDs enhanced by a large grid of YSO models (Whitney ; Robitaille )" (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration (by SV team), imaging and CLEAN  
  > "The editing and calibration of the data was carried out by the Science Verification team in CASA." (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of SiO (5-4) clumps within 0.6 pc of Sgr A* | 11 | not stated | clumps | 2 | detection of 11 SiO (5-4) clumps of molecular gas within 0.6pc (15$''$) of Sgr A\* |
| Clump 1 center velocity | 147.81 | 1.35 | km/s | 2 | / 1 / 17:45:40.51 / -29.0.28.78 / 38.91 $\pm$ 2.28 / 147.81 $\pm$ 1.35 / 47.42 $\pm$ 3.29 / 110 $\pm$ 40 / |
| Clump 11 FWZI | 147 | 39 | km/s | 2 | / 11 / 17:45:39.51 / -29.0.36.96 / 50.43 $\pm$ 1.81 / 136.16 $\pm$ 0.96 / 55.51 $\pm$ 2.43 / 147 $\pm$39 / |
| N(SiO) clumps 1 and 11 | 8.6e13 and 1.3e14 | not stated | cm^-2 | 3 | The column densities of SiO for Clumps 1 and 11 are estimated to be N(SiO)$\sim8.6\times10^{13}$ and $\sim1.3\times10^{14}$ cm$^{-2}$, respectively. |
| n_H2 from LVG | (3-9)e5 | not stated | cm^-3 | 3 | the gas density of hydrogen nuclei is constrained to n$_{\rm H_2}\sim (3-9)\times10^5$ cm$^{-3}$ within a temperature range 100-200K. |
| SiO abundance | 5.6e-10 | not stated | dimensionless | 4 | SiO abundance of 5.6$\times10^{-10}$ which is clearly much higher than is expected in quiescent molecular clouds. |
| Velocity gradient, broad/narrow clumps | 833 and 165 | not stated | km/s/pc | 4 | the velocity gradient is estimated to be 833 and 165 km s$^{-1}$  pc$^{-1}$ for clumps with broad ($\sim50$ km s$^{-1}$) and narrow ($\sim10$ km s$^{-1}$) linewidths respectively. |
| YSO candidate masses (clumps 1 and 5) | 34.3 and 19.4 | 5.9 and 2.5 | Msun | 5 | we derive masses of $34.3\pm5.9$ and 19.4$\pm2.5$ |

## Qualitative findings

- Three SiO clumps nearest Sgr A* have the broadest, most asymmetric lines; others lie mainly NE of the mini-spiral with narrow lines  
  > "The remaining clumps, distributed mainly to the NE of the ionized mini-spiral, have narrow FWZI ($\sim18-56$ km s$^{-1}$)." (abstract)

## Claim tuples

- H: SiO clumps inside the ring are protostellar outflows | E: Gaussian line fits, LVG with CARMA SiO (2-1), boundedness test, luminosity-FWZI comparison with YSO samples | R: Clumps unbound by self-gravity; luminosities between low- and high-mass YSOs; abundance high | F: Clumps trace YSO outflows, i.e. ongoing massive star formation near Sgr A* | **supported**
- H: YSO candidates are associated with SiO clumps | E: SED fits of IR sources near clumps 1 and 3 | R: Two YSO candidates with masses ~34 and ~19 Msun | F: Supports in-situ star formation | **partially**
- H: Radiation pressure or clump collisions can trigger star formation here | E: Analytic estimates | R: Radiation pressure gives n~4e8 cm^-3; collisions need ~60 clumps | F: Both possible; collisions struggle with the number of sources | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Interaction of molecular clumps with N-arm ionized gas considered but kinematics inconsistent  
  > "the kinematics of the molecular and ionized gas are inconsistent with the interaction picture." (Results and Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Synthesized beam highly elongated, so a filling factor of 0.5 was chosen  
  > "The synthesized beam is highly elongated in one direction, thus we chose a beam filling factor of 0.5." (Results and Discussion)
- Caveat (inferred, ours): SiO outflow interpretation is not tested against shocks from cloud collisions or the radiation field
- Caveat (inferred, ours): LVG constraints depend on assumed filling factor, temperature and CARMA/ALMA resolution mismatch
- Caveat (inferred, ours): Velocity range limited to 440 km/s; line contamination possible
- Caveat (inferred, ours): Gibb luminosity rescaling is a private communication
- Caveat (inferred, ours): The YSO candidate labels are inconsistent in the text

## Reproducibility

- Data public (paper): ALMA Science Verification data, project 2011.0.00005.SV  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00005.SVProject code." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: LVG code and inputs
- Missing: CARMA data
- Missing: SED photometry
- Data volume (inferred): ~10-50 GB
- Score (inferred): 4/5, Public SV data and an identifiable line, but imaging, clump finding and LVG/SED details are sparse.
- Rediscovery candidate: no, Imaging and LVG recipes are incomplete, and the LVG and SED inputs need external CARMA and IR data.

## Links

- Companion: Yusef-Zadeh 2012, ApJ, 759, 8 (radio dark clouds in the N arm region)
- Related: ALMA Science Verification Sgr A*

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00005.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 36,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
