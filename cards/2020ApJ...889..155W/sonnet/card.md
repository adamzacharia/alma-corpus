# Observations of the Orion Source I Disk and Outflow Interface

`2020ApJ...889..155W` | The Astrophysical Journal 2020 | first author: Wright, Melvyn | arXiv: 1912.08862 | DOI: 10.3847/1538-4357/ab5864

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the dust opacity structure of the Orion SrcI disk and the molecular distributions (NaCl, H2O, AlO, SiO, SiS, SO, SO2) in the disk and outflow, and what chemistry do they imply?  
  > "We use continuum images with 30 mas (12 AU) resolution to probe the dust opacity across the disk." (Introduction)
- Target **Orion Source I (SrcI)**: coordinates RA = 05:35:14.513, DEC = -05:22:30.576 (image center)  
  > "The Kleinmann-Low Nebula in Orion, at a distance 415 pc (cite: Menten2007; Kim2008; Kounkel2018)" (Introduction); "to an image center at RA = 05:35:14.513, DEC = -05:22:30.576 used in the following figures." (3 THE SRC I DISK); z/distance 415 pc  
  > "The Kleinmann-Low Nebula in Orion, at a distance 415 pc (cite: Menten2007; Kim2008; Kounkel2018)" (Introduction); "to an image center at RA = 05:35:14.513, DEC = -05:22:30.576 used in the following figures." (3 THE SRC I DISK); distance from Menten2007; Kim2008; Kounkel2018  
  > "The Kleinmann-Low Nebula in Orion, at a distance 415 pc (cite: Menten2007; Kim2008; Kounkel2018)" (Introduction); "to an image center at RA = 05:35:14.513, DEC = -05:22:30.576 used in the following figures." (3 THE SRC I DISK)

## Data provenance

- ALMA projects: 2017.1.00497.S, 2016.1.00165.S, 2013.1.00546.S, 2012.1.00123.S
- bands: Band 3 (99 GHz), Band 6 (223 GHz), Band 7 (340 GHz) plus JVLA 43 GHz  
  > "The 223 GHz (ALMA Band 6; B6) and 340 GHz (ALMA Band 7; B7) observations and calibration are described in (cite: Ginsburg2018)." (Observations and Data Reduction)
- frequencies and spectral setup: 99 GHz: 4 spectral windows, each 1.875 GHz bandwidth, 960 channels  
  > "included 4 spectral windows, each with a bandwidth of 1.875 GHz and 960 spectral channels" (99 GHz)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 99 GHz beam 45x36 mas; 223 GHz 39x19 mas; 340 GHz 26x11 mas  
  > "| 340 | 2016.1.00165.S | 2017-11-08 | 45 | 26$\times$11 at PA 58 | 90 - 12900 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 99 GHz 158 min; 224 GHz 44 min; 340 GHz 45 min  
  > "| 99 | 2017.1.00497.S | 2017-10-12 | 158 | 45$\times$36 at PA 47 | 40 - 16200 |" (Table 1)
- observing dates: 99 GHz on 2017 Oct 12 and 17  
  > "ALMA observations at 99 GHz (Band 3; B3) on 2017 Oct 12 and 17" (99 GHz)
- pi or archival as stated: _not stated_
- Line: NaCl v=1, J=18-17 (232.51 GHz)
- Line: AlO N=6-5 (229.69387 GHz)
- Line: SiS not stated (217.817 GHz)
- Line: SiO v=0, J=5-4 (217.10498 GHz)
- Other facility **JVLA**: 43 GHz continuum and SiO maser self-calibration data  
  > "The spectral setup for the 43 GHz JVLA observations included 16 wideband windows" (43 GHz)
- External data: Observations and calibration of 223 and 340 GHz data  
  > "observations and calibration are described in (cite: Ginsburg2018)" (223 and 340 GHz) [from Ginsburg2018]
- External data: SrcI proper motion Dx=6.3, Dy=-4.2 mas/yr  
  > "Src I is moving at Dx=6.3, Dy=-4.2 mas/yr (cite: Goddi2011)" (3 THE SRC I DISK) [from Goddi2011]

## Processing

### Calibration

- pipeline or manual: Observatory-supplied scripts; 223/340 GHz not self-calibrated  
  > "The data were calibrated using observatory supplied scripts." (99 GHz)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% per band  
  > "Uncertainties in the spectral indices are dominated by the absolute flux calibration accuracy of $\sim$10% for each frequency band." (Spectral Index Distribution)
- self calibration: 43 GHz self-calibrated on SiO v=1 maser; 99, 223, 340 GHz not self-calibrated  
  > "The data were self-calibrated using a strong SiO $v=1$, $J=1-0$ maser feature" (43 GHz)

### Imaging

- task: MIRIAD; CLEAN and Maximum Entropy  
  > "We used both CLEAN and Maximum Entropy algorithms to image the JVLA and ALMA data." (3 THE SRC I DISK)
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
- array combination: Only 12m array data used for mosaics  
  > "We used only the ALMA 12m array data in these images to filter out the large scale structure" (223 and 340 GHz)
- smoothing: Convolved to 30 and 50 mas  
  > "We convolved the continuum images to a common resolution of 30 mas and 50 mas resolution" (3 THE SRC I DISK)
- final beam: 99 GHz 45x36 mas  
  > "We made images with the synthesized beam width 45 $\times$ 36 mas" (99 GHz)
- final rms: Continuum rms 4 K, 3 K, 7 K, 6 K  
  > "The RMS noise levels on the continuum images are 4 K, 3 K, 7 K, and 6 K, respectively" (Spectral Index Distribution)

### Inherited from earlier work

- 223 and 340 GHz observations and calibration  
  > "observations and calibration are described in (cite: Ginsburg2018)" (223 and 340 GHz) [from Ginsburg2018]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (robust, niter, masks, cell and image size)
- Maximum Entropy settings
- Continuum channel selection / line-free channels
- Gaussian fit procedure for Table 2
- CASA version of observatory scripts
- Whether the 43 GHz image shift was applied uniformly

## Analysis recipe

1. **Image and align continuum**: CLEAN/MaxEnt imaging in MIRIAD, convolve to 30/50 mas, align 43 GHz image to 99 GHz with imdiff  
  > "We aligned the 43 GHz image with the 99 GHz image using MIRIAD task *imdiff*" (3 THE SRC I DISK)
   - software: MIRIAD
   - parameter: shifts 9 mas in RA and -2 mas in DEC  
  > "The parameters adjusted were shifts 9 mas in RA and -2 mas in DEC" (3 THE SRC I DISK)
   - fitting: _not stated_
   - validation: _not stated_
2. **Spectral index maps**: Spectral index from continuum brightness ratios, clipped at 5% of peak  
  > "the images were clipped at 5% of the peak for the spectral index calculation" (Spectral Index Distribution)
   - software: MIRIAD
   - fitting: Least squares fit 43-340 GHz at selected positions  
  > "A least squares fit from 43 to 340 Ghz to the spectral index at the central position gives 1.6 +/- 0.1" (Spectral Index Distribution)
   - validation: Flux-scale error propagated into spectral index  
  > "A multiplicative error in the flux ratio is an additive error in the spectral index of +0.15 and -0.18 in the 340/99 GHz spectral index image" (Spectral Index Distribution)
3. **Disk size and inclination**: Gaussian fits to continuum images; inclination lower limit from axis ratio assuming thin circular disk  
  > "If we assume that the disk is circular and infinitesimally thin, we can set a lower limit on its inclination angle." (Disk Structure)
   - software: MIRIAD
   - assumption: Disk circular and infinitesimally thin  
  > "If we assume that the disk is circular and infinitesimally thin" (Disk Structure)
   - fitting: _not stated_
   - validation: _not stated_
4. **Line maps of molecules**: Channel maps of NaCl, H2O, AlO, SiO, SiS, SO, SO2 compared with continuum and spectral index  
  > "Figure 14 compares the 217.817 GHz SiS line with SiO and emission in 2 $\rm km~s^{-1}$ velocity channels." (SiS)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : Imaging and analysis of all data  
  > "The MIRIAD software package (cite: Sault1995) was used to image and analyze all the data in this paper." (Observations and Data Reduction)
- **CASA** : Observatory-supplied calibration scripts  
  > "The data were calibrated using the observatory-supplied CASA scripts." (223 and 340 GHz)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index at disk center (43-340 GHz fit) | 1.6 | 0.1 | dimensionless | 2 | gives 1.6 +/- 0.1, whereas at the ends of the disk the fitted spectral index is 3.4 +/- 0.3. |
| Spectral index at disk ends | 3.4 | 0.3 | dimensionless | 2 | gives 1.6 +/- 0.1, whereas at the ends of the disk the fitted spectral index is 3.4 +/- 0.3. |
| Inclination lower limit, 400 K contour | 79 | 1 | deg | 3 | 79$\pm$1$^{\circ}$ measured at the 400 K contour (99 $\times$ 19 AU) |
| U-line rest frequency | 354.4945 | not stated | GHz | 4 | the rest frequency of the U-line is 354.4945 GHz |
| Integrated continuum flux at 340 GHz | 630 | not stated | mJy | 3 | 340 & 0.03 , 58$^\circ$ & 0.234 , -37.4$^\circ$ $^\circ$ & 630 |

## Qualitative findings

- Salt emission is found where dust is optically thin; molecules other than NaCl originate primarily in the bipolar outflow, whose base corotates with the disk.  
  > "All other molecules that we have mapped – H$_2$O, AlO, SiO, SiS, SO, and SO$_2$ – appear to originate primarily in the bipolar outflow." (abstract)

## Claim tuples

- H: Dust opacity varies across the SrcI disk | E: Spectral index maps from 43-340 GHz at 30 mas | R: Spectral index ~2 in the midplane, ~3 at edges | F: Midplane optically thick, edges optically thin | **supported**
- H: Salt traces the disk velocity field where dust is thin | E: NaCl line maps compared with spectral index images | R: NaCl lies in the surface layers with large spectral index gradient | F: NaCl is a tracer of the disk velocity field; rotational temperatures may be underestimated | **supported**
- H: Outflow chemistry is shaped by grain destruction and gas-phase reactions | E: Maps of H2O, AlO, SiO, SiS, SO, SO2 | R: SiS filamentary at outflow edges; others in outflow | F: Si and Al released from grains form SiO and AlO; SiS forms via SO and SO2 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): SO and SO2 distributions are over-resolved; the U-line remains unidentified.  
  > "The SO and distributions are over-resolved in these ALMA observations." (SO and SO2)
- Caveat (inferred, ours): Chemical interpretation is qualitative, with no modeling
- Caveat (inferred, ours): Imaging parameters not given
- Caveat (inferred, ours): Optical depth and temperature assumptions are loosely stated

## Reproducibility

- Data public (paper): ALMA project codes listed, but public status not stated  
  > "Table 1 provides a summary of the observations, including project codes." (Table 1)
- Products in archive: _not stated_
- Missing: CLEAN and MaxEnt parameters
- Missing: Line-free channels
- Missing: JVLA calibration details
- Missing: Gaussian fit details
- Data volume (inferred): Several hundred GB across four ALMA projects plus JVLA
- Score (inferred): 3/5, Data are identified, but imaging parameters are missing and results are largely qualitative.
- Rediscovery candidate: no, Imaging recipe incomplete and main results mostly qualitative.

## Links

- Method: Sault1995 (MIRIAD software)
- Companion: Ginsburg2018 (Observations and calibration of 223/340 GHz data)
- Companion: Ginsburg2019 (NaCl and KCl lines identified in the disk)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.1.005446.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 34,
  "rate": 0.523
 },
 "evidence_ok": true
}
```
