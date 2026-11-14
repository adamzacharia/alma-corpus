# Multimolecule ALMA observations toward the Seyfert 1 galaxy NGC 1097

`2015A&A...573A.116M` | Astronomy and Astrophysics 2015 | first author: Martín, S. | arXiv: 1410.2823 | DOI: 10.1051/0004-6361/201425105

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry, agn_and_quasars
- Question: How do molecular abundances differ between the AGN-surrounding circumnuclear disk and the star forming ring in NGC 1097, and what does this say about AGN-driven chemistry (HCN/HCO+, HCN/CS)?  
  > "Differences in the molecular abundances are observed between the star forming ring and the inner circumnuclear disk." (abstract)
- Target **NGC 1097**: coordinates RA 02h46m19.06s, Dec -30d16m29.7s (J2000, phase center)  
  > "At the distance of 14.5 Mpc, the angular to linear scale is $\sim70~pc/''$" (2 Observations); "The phase center of the observations was $\alpha_{J2000}=02^h46^m19.06^s$, $\delta_{J2000}=-30^\circ16'29.7''$." (2 Observations); z/distance 14.5 Mpc  
  > "At the distance of 14.5 Mpc, the angular to linear scale is $\sim70~pc/''$" (2 Observations); "The phase center of the observations was $\alpha_{J2000}=02^h46^m19.06^s$, $\delta_{J2000}=-30^\circ16'29.7''$." (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00108.S
- bands: Band 3 (3 mm), 2SB receivers, LO1 93.187 GHz  
  > "The dual sideband (2SB) Band 3 receivers were tuned at an LO1 frequency of 93.187 GHz." (2 Observations)
- frequencies and spectral setup: 4x1.875 GHz spectral windows covering 85.8-89.4 and 97.7-101.3 GHz; 488 kHz resolution smoothed by 10 channels to ~17-14.5 km/s  
  > "covering the rest frequency ranges $85.8-89.4$ GHz and $97.7-101.3$ GHz" (2 Observations); "The original frequency resolution of $488$ kHz was degraded by 10 channels down to a velocity resolution of $\sim17-14.5$ $\rm km\,s^{-1}$" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 24 and 31 antennas in the two runs  
  > "The 24 and 31 antennas used on the first and second run, respectively" (2 Observations)
- configurations: _not stated_
- baselines: up to ~250 m; uv range 4.3-132 kλ (14-447 m)  
  > "thus covering uv ranges from 4.3 to 132 $k\lambda$ ($14-447$ m)" (2 Observations)
- angular resolution: ~2.2'' x 1.5'' (150 pc x 100 pc), P.A.=100 deg  
  > "average synthesized beam of $\sim2.2''\times1.5''$ ($150~pc\times 100~pc$) with $P.A.=100^\circ$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: ~0.5 mJy rms in 4.88 MHz channels  
  > "A final rms of $\sim0.5$ mJy in the smoothed 4.88 MHz channels" (2 Observations)
- time on source: ~72 min  
  > "overall on source integration time of $\sim 72$ min" (2 Observations)
- observing dates: 2012 July 29 and October 19  
  > "Data were acquired during 2012 July 29th and October 19th" (2 Observations)
- pi or archival as stated: Cycle 0 early science program, P.I. K. Kohno  
  > "ALMA Cycle 0 early science program 2011.0.00108.S (P.I. K. Kohno)" (2 Observations)
- Line: HCN 1-0 (88.631 GHz)
- Line: HCO+ 1-0 (89.188 GHz)
- Line: CS 2-1 (97.980 GHz)
- Line: HNCO 4_{0,4}-3_{0,3} (87.925 GHz)
- Line: HC3N 11-10 (100.076 GHz)
- Line: SiO 2-1 (86.846 GHz)
- Line: CCH 1-0 (87.316 GHz)
- Other facility **GALEX FUV**: FUV image of the SF ring compared with HCN and CCH  
  > "comparison between the FUV emission from unobscured massive star formation in the SF ring of NGC 1097 (cite: GildePaz2007)" (4.2 Star formation: CCH)
- External data: H2 column densities from CO observations used for fractional abundances  
  > "we used the molecular hydrogen column densities derived from CO observations by (cite: Hsieh2011)" (3.3 Relative molecular abundances) [from (cite: Hsieh2011)]
- External data: Spectral line parameters from JPL catalog  
  > "extracted from JPL spectral line catalog (cite: Pickett1998)" (3 Results) [from (cite: Pickett1998)]
- External data: 12C/13C ratio of ~40  
  > "assuming a $^{12}$C/$^{13}$C isotopic ratio of $\sim 40$ (cite: Henkel2014)" (3.2 Excitation and column density determination) [from (cite: Henkel2014)]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; details not given  
  > "Data were calibrated and cleaned with CASA (cite: McMullin2007)" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (flux); J1924-292 bandpass; J0334-401 phase  
  > "Absolute flux scaled was calibrated through observations towards Neptune." (2 Observations); "The quasars J1924-292 and J0334-401 were used as bandpass and phase calibrator, respectively." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Cleaned with CASA; images produced with GILDAS  
  > "while images were produced with GILDAS" (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.45''/pixel  
  > "(with $0.45''$/pixel)" (3.1 Selected positions)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 10 original channels averaged to 4.88 MHz  
  > "smoothed 4.88 MHz channels (i.e. 10 original channels)" (2 Observations)
- final beam: _not stated_
- final rms: ~0.5 mJy per 4.88 MHz channel  
  > "A final rms of $\sim0.5$ mJy in the smoothed 4.88 MHz channels" (2 Observations)

### Inherited from earlier work

- Excitation temperature ~8 K for HCN/HCO+ taken from earlier ALMA analysis  
  > "The emission can be roughly fitted in LTE by a rotational temperature of $\sim 8$ K." (3.2 Excitation and column density determination) [from (cite: Izumi2013)]
- Kinematics and linewidth discussion deferred to earlier paper  
  > "See (cite: Hsieh2011) for a discussion on the kinematics and the different linewidths" (3.2 Excitation and column density determination) [from (cite: Hsieh2011)]
- MADCUBA_IJ modelling tool  
  > "MADCUBA_IJ package[^2] (Martín et al in prep.)" (3.2 Excitation and column density determination) [from Martín et al in prep.]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/flagging details
- Cleaning parameters (weighting, robust, masks, threshold, deconvolver)
- Continuum subtraction method and line-free channels
- How the two executions were combined and primary beam correction
- Extraction aperture for spectra at selected positions
- MADCUBA_IJ version and fit details (line profile treatment, hyperfine handling, upper-limit definition)
- Moment map clipping thresholds
- Method for deriving HNCO disk length, PA and velocity gradient

## Analysis recipe

1. **Image cubes and moment 0 maps**: Calibrate/clean in CASA, image with GILDAS, integrate 900-1600 km/s (CCH 600-1600 km/s)  
  > "Moment 0 maps were integrated in the velocity range \[$900-1600$\] $\rm km\,s^{-1}$" (3 Results)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra at 9 selected positions**: Spectra at emission peaks of HCN, C2H, CS; position A is brightest HCN peak  
  > "we have selected a sample of 9 positions" (3.1 Selected positions)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit LTE column densities**: LTE spectral modelling with column density, velocity, linewidth free  
  > "The parameters of column density, velocity and linewidth are left as free parameters." (3.2 Excitation and column density determination)
   - software: MADCUBA_IJ
   - parameter: Tex fixed 8 K, source size fixed 1.8''  
  > "excitation temperature and the source size parameters were fixed to $8$ K and $1.8''$, respectively" (3.2 Excitation and column density determination)
   - assumption: LTE; source size equals synthesized beam solid angle  
  > "we assume the emission to be distributed in a region approximately equal to the synthesized beam in solid angle" (3.2 Excitation and column density determination)
   - fitting: not stated beyond free parameters  
  > "The parameters of column density, velocity and linewidth are left as free parameters." (Excitation and column density determination)
   - validation: Checked sensitivity to Tex (HNCO limit T<20 K) and source size (half size raises N by ~5)  
  > "Assuming a source size of half our assumed value would increase the opacities up to $\tau\gtrsim1$ and the derived column densities by a factor of $\sim 5$." (3.2 Excitation and column density determination)
4. **Relative abundances and line ratio maps**: Abundances normalised to HCN and to position A; HCN/HCO+ ratio map with 5 sigma cutoff; HCN/HNCO, HCN/CS, HCN/CCH ratio maps  
  > "we have only included points above a $5~\sigma$ level in the individual images" (4.1.1 AGN irradiation)
   - assumption: HCN as reference baseline species  
  > "We have used the brightest species in our observations, namely HCN, as a reference column density baseline." (3.3 Relative molecular abundances)
   - fitting: _not stated_
   - validation: Compared with CS as reference  
  > "reproducing Fig. [4] with the abundances relative to CS results in an overall underabundances of all species" (3.3 Relative molecular abundances)
5. **Characterise HNCO circumnuclear disk**: Measure extent, PA and velocity gradient from extreme emission peaks in channel maps, accounting for beam smearing  
  > "From the extreme emission peaks in the channel maps and taking into account the beam smearing, we measure a disk structure" (5.2 The CND traced by HNCO)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data calibration and cleaning  
  > "Data were calibrated and cleaned with CASA (cite: McMullin2007)" (2 Observations)
- **GILDAS** : Image production  
  > "while images were produced with GILDAS" (2 Observations)
- **MADCUBA_IJ** : LTE spectral line fitting and column densities  
  > "We have used the spectral line modeling tools within the MADCUBA_IJ package" (3.2 Excitation and column density determination)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| X(HCN/HCO+) at central position A | 2.7 | 0.1 | dimensionless | 4 | we find that the $X(\rm HCN/HCO^+)=2.7\pm0.1$ in the central position |
| X(HCN/HCO+) in SF ring | 2.1-2.7 | not stated | dimensionless | 4 | only marginally larger than the values in the SF ring which range $2.1-2.7$ |
| HNCO disk length | 180 | 40 | pc | 5 | we measure a disk structure of $180\pm40$ pc length and P.A.$=120\pm10^\circ$ |
| HNCO disk position angle | 120 | 10 | deg | 5 | P.A.$=120\pm10^\circ$ |
| HNCO disk velocity gradient | 1.1 | 0.2 | km/s/pc | 5 | The measured velocity gradient of $1.1\pm0.2\rm~ km~s^{-1}~pc^{-1}$ |
| HCN column density at position A | 3.14 | 0.07 | 1e14 cm^-2 | 3 | / A / 3.14 (0.07) / 1.16 (0.03) / 14.4 (0.8) / 1.85 (0.11) |
| HCN opacity at brightest positions | ~0.2 | not stated | dimensionless | 3 | Our fit to the spectra results in an opacity of $\tau\sim0.2$ in the brightest positions (A and B) for HCN. |
| HCN/HCO+ intensity ratio at center | 1.65 (max ~2 outward) | not stated | dimensionless | 4 | The ratio of $1.65$ at the central position is still significantly higher than the average $\sim1.3$ measured in the SF ring |

## Qualitative findings

- HNCO delineates a rotating circumnuclear disk; HC3N and SiO concentrated inside it  
  > "This disk appear to enclose the emission of HC$_3$N and SiO which suggest an stratification of the disk" (6 Summary)

## Claim tuples

- H: Is the HCN enhancement in AGNs due to X-ray irradiation? | E: HCN/HCO+ abundance and ratio maps across the CND and ring | R: HCN/HCO+ rises with distance from the nucleus; central X(HCN/HCO+) only marginally above ring | F: X-ray enhancement discarded; shocked material ~200 pc away favoured | **supported**
- H: Why is HCN/CS lower in starbursts than AGN? | E: Compare low-J and high-J HCN/CS with excitation modelling | R: CS underabundant ~2 in AGN plus excitation differences | F: Combination of small CS underabundance and excitation effects | **partially**
- H: Do the dense gas tracers outline the disk structure? | E: Maps of HNCO, HC3N, SiO | R: HNCO traces disk; HC3N and SiO concentrated within unresolved center | F: Stratified disk structure | **partially**
- H: Is CCH a tracer of star formation? | E: Compare CCH relative abundance with FUV | R: CCH abundance varies 20% below to 70% above center | F: CCH may trace obscured/early star formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Column densities used instead of intensity ratios for more accurate abundances  
  > "we have estimated the column densities of each of the molecular species to have a more accurate determination of the molecular abundances" (3.2)
- Alternative: CS as reference species instead of HCN rejected because all ring species appear underabundant  
  > "we stick to our use of HCN as it does provide abundances less biased towards the AGN position" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Tex and source size fixed; HCN opacity uncertain in center; H13CO+ and SO at edge of detection  
  > "We note that both H$^{13}$CO$^+$ and SO detections are at the edge of detection." (3.2)
- Caveat (inferred, ours): Fixed Tex=8 K for all species and positions may bias HC3N and others
- Caveat (inferred, ours): Modest resolution (~150 pc) limits disk interpretation
- Caveat (inferred, ours): Single-beam source size assumption conflicts with HCN/H13CN opacity estimate
- Caveat (inferred, ours): Differences are often within excitation uncertainties
- Caveat (inferred, ours): Resolved-out flux not assessed

## Reproducibility

- Data public (paper): Cycle 0 ALMA data; project code given and acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00108.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: MADCUBA_IJ fit configuration (paper in prep.)
- Missing: Spectrum extraction apertures
- Data volume (inferred): ~10-50 GB raw (two Cycle 0 executions)
- Score (inferred): 3/5, Public data and clear LTE assumptions, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Imaging and MADCUBA fitting recipes are incomplete, so numeric results are hard to redo exactly.

## Links

- Method: (cite: McMullin2007) (CASA)
- Companion: (cite: Izumi2013) (First paper on the same ALMA project, HCN/HCO+ J=4-3 and 1-0)
- Related: ALMA Cycle 0 early science 2011.0.00108.S

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 74,
  "stated": 44,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
