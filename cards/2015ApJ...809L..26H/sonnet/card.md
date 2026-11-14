# Detection of N<SUB>2</SUB>D<SUP>+</SUP> in a Protoplanetary Disk

`2015ApJ...809L..26H` | The Astrophysical Journal Letters 2015 | first author: Huang, Jane | arXiv: 1508.03637 | DOI: 10.1088/2041-8205/809/2/L26

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is N2D+ detectable in a protoplanetary disk, and what disk-averaged N2D+/N2H+ (D/H) ratio does it imply?  
  > "In this letter, we present the first detection of N$_2$D$^+$ in a protoplanetary disk." (Introduction)
- Target **AS 209**: coordinates RA 16h49m15.29s, Dec -14d22m08.6s (J2000)  
  > "AS 209 (J2000.0 R.A. $16^{\textup{h}}49^{\textup{m}}15^{\textup{s}}.29$, decl. $-14^{\circ}22'08''.6$)" (Observations); "a 1.6 Myr old K5 T Tauri star in $\rho$ Ophiuchi located 130$\pm$ 50 pc away" (Introduction); z/distance 130±50 pc  
  > "AS 209 (J2000.0 R.A. $16^{\textup{h}}49^{\textup{m}}15^{\textup{s}}.29$, decl. $-14^{\circ}22'08''.6$)" (Observations); "a 1.6 Myr old K5 T Tauri star in $\rho$ Ophiuchi located 130$\pm$ 50 pc away" (Introduction); distance from cite: 1988cels.book.....H; 2007A&A...474..653V  
  > "AS 209 (J2000.0 R.A. $16^{\textup{h}}49^{\textup{m}}15^{\textup{s}}.29$, decl. $-14^{\circ}22'08''.6$)" (Observations); "a 1.6 Myr old K5 T Tauri star in $\rho$ Ophiuchi located 130$\pm$ 50 pc away" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6  
  > "Thirteen spectral windows (SPWs) were observed in Band 6, each with 61.04 kHz resolution." (Observations)
- frequencies and spectral setup: N2D+ 3-2 in SPW 9 centered 231.32183 GHz; 13CO 2-1 in SPW 7 centered 220.39868 GHz; 61.04 kHz resolution  
  > "The N$_2$D$^+$ J=3-2 line was in SPW 9, centered on 231.32183 GHz" (Observations)
- continuum bandwidth: five line-free SPWs, each 59 MHz wide  
  > "The 1.4 mm dust continuum flux was extracted by averaging the channels in five line-free SPWs. Each of these windows was 59 MHz wide." (Observations)
- arrays: Thirty-four 12 m antennae  
  > "Thirty-four 12 m antennae were used for the observations, with a maximum baseline of 650.3 m." (Observations)
- configurations: _not stated_
- baselines: maximum 650.3 m  
  > "Thirty-four 12 m antennae were used for the observations, with a maximum baseline of 650.3 m." (Observations)
- angular resolution: N2D+ beam 1.05"x0.99"; 13CO 1.02"x0.74"  
  > "1.$''$05$\times$ 0.$''$99 (87$^{\circ}$.83)" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.3 mJy/beam; channel rms 17 mJy/beam (13CO), 8.5 mJy/beam (N2D+)  
  > "The channel rms for $^{13}$CO 2-1 was 17 mJy beam$^{-1}$, while the rms for N$_2$D$^+$ 3-2 was 8.5 mJy beam$^{-1}$." (Observations)
- time on source: 21 minutes  
  > "was observed 2014 July 2 during ALMA Cycle 2 with 21 minutes of on-source integration time." (Observations)
- observing dates: 2014 July 2, ALMA Cycle 2  
  > "was observed 2014 July 2 during ALMA Cycle 2 with 21 minutes of on-source integration time." (Observations)
- pi or archival as stated: _not stated_
- Line: N2D+ J=3-2 (231.32183 GHz)
- Line: 13CO J=2-1 (220.39868 GHz)
- Line: N2H+ J=3-2 (SMA) (279.51173 GHz)
- Other facility **SMA**: N2H+ 3-2 and 1.4 mm continuum data from the Öberg et al. 2011 survey  
  > "this paper also uses AS 209 data originally published in Öberg et al.’s Submillimeter Array protoplanetary disk survey (cite: 2011ApJ...734...98O)." (Observations)
- External data: SMA N2H+ 3-2 line data and 219±22 mJy 1.4 mm continuum for AS 209  
  > "is 219 $\pm$ 22 mJy." (Observations) [from Öberg et al. 2011 (cite: 2011ApJ...734...98O)]
- External data: Molecular parameters (Qrot, Eu, S, mu) from CDMS  
  > "were all obtained from the Cologne Database for Molecular Spectroscopy (cite: 2001A&A...370L..49M; 2005JMoSt.742..215M)." (Results) [from (cite: 2001A&A...370L..49M; 2005JMoSt.742..215M)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2  
  > "CASA software package (version 4.2.2)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan; bandpass and phase with J1733-1304  
  > "ALMA/NAASC staff performed bandpass and phase calibration with the quasar J1733-1304, and the flux was calibrated with Titan." (Observations)
- flux scale uncertainty: ~10%  
  > "The uncertainty in the absolute flux is $\sim$10$\%$." (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: N2D+ visibilities tapered to 1"  
  > "the visibilities for the N$_2$D$^+$ J=3-2 line were tapered to 1$''$." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian rotation mask based on 13CO 2-1 emission  
  > "CLEANing for both N$_2$D$^+$ and $^{13}$CO was performed using a Keplerian rotation mask based on the emission patterns of the stronger line" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: in the uv-plane  
  > "After continuum subtraction in the uv-plane, the data cubes for the SPWs were rebinned to 0.4 km/s." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: N2D+ 1.05"x0.99" PA 87.83°  
  > "1.$''$05$\times$ 0.$''$99 (87$^{\circ}$.83)" (Table 1)
- final rms: 8.5 mJy/beam per channel (N2D+)  
  > "the rms for N$_2$D$^+$ 3-2 was 8.5 mJy beam$^{-1}$." (Observations)

### Inherited from earlier work

- LTE optically thin column density formula  
  > "Column densities were derived from the integrated intensities using the LTE formula from (cite: 2003ApJ...590..314R)" (Results) [from (cite: 2003ApJ...590..314R)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, weighting/robust, cell and image size
- Keplerian mask parameters (stellar mass, inclination, PA)
- Line-free channels used for continuum subtraction
- Exact spectrum extraction details and FWHM value
- Whether SMA N2H+ beam differences were corrected
- Whether pipeline or manual calibration was used

## Analysis recipe

1. **Image continuum and lines**: Continuum from 5 line-free SPWs; uv continuum subtraction; rebin to 0.4 km/s; N2D+ tapered to 1"; CLEAN with Keplerian mask from 13CO  
  > "CLEANing for both N$_2$D$^+$ and $^{13}$CO was performed using a Keplerian rotation mask based on the emission patterns of the stronger line" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Velocity channel progression consistent with disk rotation  
  > "The progression of emission from west to east of the pointing center is consistent with disk rotation" (Results)
2. **Measure integrated fluxes**: Spectra extracted with Keplerian masks; uncertainty = rms x FWHM/sqrt(n_ch)  
  > "The uncertainty on the integrated flux was calculated using the formula $\sigma = \textup{rms} \times \textup{FWHM}/\sqrt{n_{ch}}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive column densities and D/H**: Optically thin LTE; N2H+ averaged over 5"x5" circle, N2D+ over 4"x4" circle; Tex 10-25 K; molecules assumed co-spatial  
  > "Hence we assume that the molecules are co-spatial in the disk based on their similar formation and destruction chemistry." (Results); "The excitation temperature is expected to be between 10 and 25 K in the outer regions of the disk" (Results)
   - software: CDMS
   - assumption: Tex 10-25 K, optically thin, co-spatial N2D+ and N2H+  
  > "The excitation temperature is expected to be between 10 and 25 K in the outer regions of the disk" (Results)
   - fitting: _not stated_
   - validation: RADEX non-LTE grid (Tkin 10-25 K, n(H2) 1e6-1e10 cm-3) gave similar N2H+ columns of 1.7-7.8e11 cm-2  
  > "The resulting column densities ranged from 1.7 to 7.8$\times 10^{11}$ cm$^{-2}$, similar to the column density range estimated through LTE calculations." (Results)

## Software

- **CASA** 4.2.2: calibrated visibility deconvolution and CLEAN  
  > "The calibrated visibilities were deconvolved and CLEANed with the CASA software package (version 4.2.2)." (Observations)
- **RADEX** : non-LTE check of column densities  
  > "column densities for N$_2$H$^+$ were also calculated with RADEX, a 1D non-LTE radiative transfer code" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.4 mm continuum flux density (ALMA) | 242 | 24 | mJy | 1 | The integrated flux density of the 1.4 mm dust continuum is 242$\pm$24 mJy. |
| N2D+ 3-2 integrated flux | 80 | 18 | mJy km/s | 2 | 80\[18\] |
| N2D+ peak integrated intensity significance | 3.3 | not stated | sigma | 1 | The peak intensity of N$_2$D$^+$ is 3.3$\sigma$ |
| N2D+ column density (10-25 K) | 2.1e11 to 1.4e11 | ±0.5e11 / ±0.3e11 | cm^-2 | 3 | At 10 K, the disk-averaged column density of N$_2$D$^+$ is $2.1\pm 0.5\times 10^{11}$ cm$^{-2}$ |
| N2H+ column density (10-25 K) | 6.3e11 to 3.1e11 | ±0.8e11 / ±0.4e11 | cm^-2 | 3 | At 10 K, the disk-averaged column density of N$_2$D$^+$ is $2.1\pm 0.5\times 10^{11}$ cm$^{-2}$ and that of N$_2$H$^+$ is $6.3\pm 0.8\times 10^{11}$ cm$^{-2}$. |
| Disk-averaged N2D+/N2H+ ratio | 0.3-0.5 | not stated | dimensionless | 3 | The resulting D/H ratio is estimated to be between 0.3 and 0.5. |

## Qualitative findings

- N2D+ emission is asymmetric, mostly redshifted, east of phase center; tentative  
  > "but no blueshifted emission is observed for N$_2$D$^+$ above the 2$\sigma$ level." (Results)

## Claim tuples

- H: Is N2D+ present in a protoplanetary disk? | E: ALMA Band 6 N2D+ 3-2 observation of AS 209 | R: 3.3 sigma integrated peak; emission follows disk rotation in channel maps | F: First detection of N2D+ in a protoplanetary disk | **supported**
- H: How high is deuterium fractionation of N2H+ in AS 209? | E: LTE column densities from ALMA N2D+ and SMA N2H+ | R: N2D+/N2H+ = 0.3-0.5 | F: An order of magnitude above DCN/HCN and DCO+/HCO+ disk-averaged ratios, consistent with models | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low SNR; spatial distributions not constrained; asymmetry needs higher SNR confirmation  
  > "Because the SNR is low for both molecules, their spatial distributions are not well-constrained by the current set of observations." (Results)
- Caveat (inferred, ours): Detection only 3.3 sigma
- Caveat (inferred, ours): Co-spatiality assumed; SMA beam (3.7") much larger than ALMA beam
- Caveat (inferred, ours): Tex range not fitted
- Caveat (inferred, ours): Only 10-25 K LTE; distance uncertainty large

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CLEAN parameters and mask definition
- Missing: SMA N2H+ visibilities processing details
- Data volume (inferred): ~10-50 GB for the single ALMA execution
- Score (inferred): 3/5, Public ALMA data and simple analysis, but imaging parameters and mask are unspecified.
- Rediscovery candidate: yes, Single public dataset, short recipe, numeric results (flux, columns, ratio), though imaging details are missing.

## Links

- Method: (cite: 2003ApJ...590..314R) (LTE column density formula)
- Companion: (cite: 2011ApJ...734...98O) (SMA N2H+ and continuum data for AS 209)
- Related: ALMA Cycle 2 disk survey of deuterated molecules

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00226.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 35,
  "rate": 0.574
 },
 "evidence_ok": true
}
```
