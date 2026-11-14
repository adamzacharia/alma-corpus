# Environmental Effect on the Interstellar Medium in Galaxies across the Cosmic Web at z = 0.73

`2019ApJ...874...53B` | The Astrophysical Journal 2019 | first author: Betti, S. K. | arXiv: 1902.08216 | DOI: 10.3847/1538-4357/ab07b3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: How does local galaxy environment (density) affect the ISM mass, gas fraction and depletion time of star-forming galaxies at z~0.73 in the COSMOS large-scale structure?  
  > "Using the ALMA observations, we calculate the total ISM mass ($\mathrm{M}_{\mathrm{ISM}}$) and look for depletion as a function of galaxy density" (abstract)
- Target **101 COSMOS galaxies at z=0.72-0.76 (zCOSMOS spectroscopic, Herschel-detected)**: coordinates individual RA/Dec in Table 2 (e.g. 150.7695, 2.4400 deg for ID 65511)  
  > "the spectroscopic redshift range $z = 0.72-0.76$ was selected as it shows a known large scale structure (LSS) in COSMOS" (2 Sample); "| 65511        | 2            | 150.76950070 | 2.44000006   | 0.746" (Table 2); z/distance z_spec = 0.72-0.76  
  > "the spectroscopic redshift range $z = 0.72-0.76$ was selected as it shows a known large scale structure (LSS) in COSMOS" (2 Sample); "| 65511        | 2            | 150.76950070 | 2.44000006   | 0.746" (Table 2); distance from zCOSMOS spectroscopic redshifts (Lilly2007)  
  > "the spectroscopic redshift range $z = 0.72-0.76$ was selected as it shows a known large scale structure (LSS) in COSMOS" (2 Sample); "| 65511        | 2            | 150.76950070 | 2.44000006   | 0.746" (Table 2)

## Data provenance

- ALMA projects: 2015.1.00055.S
- bands: Band 7  
  > "Both science goals were observed in Band 7" (3 Observations)
- frequencies and spectral setup: SG1 345.7 GHz, bandwidth 7.475 GHz; SG2 342.3 GHz, bandwidth 7.425 GHz  
  > "SG1 observations taken between January $2 - 5$, 2016 ($\nu=345.7\,$GHz, bandwidth of 7.475 GHz)" (3 Observations); "($\nu=342.3\,$GHz, bandwidth of 7.425 GHz)" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.9"x0.5" (SG1), 1.0"x0.8" (SG2)  
  > "0.21 mJy/beam with a beam size of $1.0\ensuremath{''} \times 0.8\ensuremath{''}$ for SG2" (3 Observations)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma rms 0.15 mJy/beam (SG1), 0.21 mJy/beam (SG2)  
  > "The average 1$\sigma$ rms sensitivity achieved is 0.15 mJy/beam with a beam size of $0.9\ensuremath{''} \times 0.5\ensuremath{''}$ for SG1" (3 Observations)
- time on source: 3 minutes per galaxy  
  > "On source integration time for both science goals was 3 minutes per galaxy." (3 Observations)
- observing dates: SG1 Jan 2-5 2016; SG2 Jan 26-Apr 27 2016  
  > "SG2 observations taken between January 26 $-$ April 27, 2016" (3 Observations)
- pi or archival as stated: Cycle 3, PI Pope  
  > "ALMA Cycle 3 observations (2015.1.00055.S; PI Pope)" (3 Observations)
- Other facility **Herschel PACS/SPIRE and Spitzer MIPS**: 100 um/24 um photometry for L_IR and sample selection  
  > "which includes fluxes at 24 $\mu$m (Spitzer/MIPS) and 100 $\mu$m (*Herschel*/PACS)" (2 Sample)
- Other facility **zCOSMOS (VLT-VIMOS)**: spectroscopic redshifts  
  > "spectroscopic redshifts obtained from the VLT-VIMOS zCOSMOS survey" (2 Sample)
- External data: Projected 2D local galaxy density maps  
  > "The local galaxy densities were determined from projected 2D density maps published by (cite: Scoville2013)" (2 Sample) [from (cite: Scoville2013)]
- External data: Stellar masses and photometric catalog (COSMOS2015)  
  > "We show the distribution of stellar mass and local galaxy density of these targets compared to the overall COSMOS sample from (cite: Laigle2016)" (2 Sample) [from (cite: Laigle2016)]
- External data: SFR_UV and comparison L_IR  
  > "All 101 target galaxies have corresponding SFR$_\mathrm{UV}$ from (cite: Lee2015)." (2 Sample) [from (cite: Lee2015)]
- External data: Herschel PACS fluxes  
  > "We used the IR photometry for our 101 sources from the PEP PACS catalogs (cite: Lutz2011)" (2 Sample) [from (cite: Lutz2011)]
- External data: Visual morphological classifications  
  > "Using the visual morphological classifications from (cite: Kartaltepe2015) for our galaxies" (6.4.2 Mergers and Morphology) [from (cite: Kartaltepe2015)]

## Processing

### Calibration

- pipeline or manual: SG1 delivered calibrated data used; SG2 manually recalibrated in CASA due to pipeline flagging issues  
  > "We used the delivered calibrated data for SG1, but had to manually recalibrate SG2 with the Common Astronomy Software Application (cite: McMullin2007) due to issued flagged by the pipeline reduction." (3 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: SG1 delivered calibrated data used as is  
  > "We used the delivered calibrated data for SG1" (3 Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "we made continuum maps and primary beam corrected continuum maps with the CASA task CLEAN using natural weighting and a threshold of 0.4 mJy ($2-3\sigma$)" (3 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting and a threshold of 0.4 mJy" (3 Observations)
- uv taper: Gaussian uv-taper on SG1 to match SG2 beam  
  > "with a Gaussian uv-taper for the higher resolution SG1 in order to match the beam size of SG2" (3 Observations)
- cell size: 0.12 arcsec  
  > "The maps have a pixel scale of $0.12\ensuremath{''}$." (3 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: primary beam corrected maps made  
  > "continuum maps and primary beam corrected continuum maps" (3 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: SG1 tapered to match SG2 (~1.0"x0.8")  
  > "in order to match the beam size of SG2" (3 Observations)
- final rms: SG1 tapered average 0.16 mJy/beam  
  > "The average rms of the SG1 tapered images is 0.16 mJy/beam." (3 Observations)

### Inherited from earlier work

- ISM mass from RJ dust continuum, calibration alpha_850 and T_d = 25 K  
  > "Following (cite: Scoville2014; Scoville2016), we assume the temperature to be $T_d = 25$ K" (4.2 ISM Mass) [from (cite: Scoville2014; Scoville2016)]
- Detection criterion (>2 sigma integrated or 3 sigma peak)  
  > "Similar to (cite: Scoville2014), a detection requires a $> 2\sigma$ integrated aperture flux measurement" (4.1 Flux Measurements) [from (cite: Scoville2014)]
- SFR_IR conversion  
  > "we calculate SFR$_{\mathrm{IR}}$ using the relation from (cite: Arnouts2013), who adopted the relation from (cite: Bell2005)" (2 Sample) [from (cite: Arnouts2013)]

### Not stated but needed to reproduce (our reading)

- CASA version used for recalibration and imaging
- Details of the SG2 manual recalibration (flags, calibrators)
- Flux calibrator and flux scale uncertainty
- Number of clean iterations and masking
- Exact uv-taper size
- Rule for choosing density-bin boundaries from the boxcar average
- How stellar masses and uncertainties were assigned per bin
- Gamma_0 definition used in the ISM mass equation

## Analysis recipe

1. **Select sample and derive L_IR/SFR**: Select zCOSMOS galaxies z=0.72-0.76 with S100>5 mJy; fit Kirkpatrick2015 SFG template to 24/100 um photometry; SFR_IR=8.6e-11 L_IR plus SFR_UV  
  > "we fit the available IR photometry to the (cite: Kirkpatrick2015) spectral energy distribution (SED) templates" (2 Sample)
   - assumption: Chabrier IMF; flat LCDM Om=0.307, H0=67.7  
  > "$H_0 = 67.7$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)
   - fitting: _not stated_
   - validation: Compared L_IR with Lee2015: 15% mean difference, no density dependence  
  > "The average percent difference in L$_\mathrm{IR}$ for the 80 matches was 15$\%$" (2 Sample)
2. **Image continuum**: CLEAN natural weighting, 0.4 mJy threshold; taper SG1 to SG2 beam  
  > "using natural weighting and a threshold of 0.4 mJy ($2-3\sigma$)" (3 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure aperture and peak fluxes**: Integrated flux in 0.54" radius aperture on primary-beam-corrected map, divided by pixels/beam (~66.14); noise from 100 random apertures; detection >2 sigma integrated or 3 sigma peak  
  > "We find an optimal aperture with radius $0.54\ensuremath{''}$, which is used for all individual flux measurements." (4.1 Flux Measurements)
   - software: CASA
   - parameter: aperture radius 0.54"; 100 random apertures  
  > "taking the standard deviation of integrated flux measurements in 100 random apertures of the same size offset from the source" (4.1 Flux Measurements)
   - fitting: _not stated_
   - validation: Aperture radius chosen by maximizing S/N per annulus  
  > "we calculate the S/N per annuli for increasing aperture radii in order to determine the aperture radius which encloses the maximum signal and least noise" (4.1 Flux Measurements)
4. **Convert flux to ISM mass**: Scoville RJ dust-continuum formula with alpha_850=6.7e19 erg/s/Hz/Msun, Gamma_RJ correction  
  > "$$\alpha_{850 \mu m} = \frac{L_{\nu 850\ \mu m}}{M_{ISM}} = 6.7 \times 10^{19} \ \mathrm{erg} \ \mathrm{s}^{-1} \ \mathrm{Hz}^{-1}  \ M_{\odot}^{-1}.$$" (4.2 ISM Mass)
   - assumption: T_d = 25 K; optically thin RJ tail; lambda_rest > 250 um  
  > "we assume the temperature to be $T_d = 25$ K" (4.2 ISM Mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **Stack by density bin**: Weighted-mean (inverse-variance) and median stacks in three density bins chosen via sliding boxcar average of 8 samples; M_ISM from bin mean z, nu, d_L  
  > "In Figure [5](#boxcarStacks), we plot a sliding box average of 8 samples; the sample separates into three 3 groups: $0.16-1.2$, $1.2-2.6$, $2.6-10.5$ galaxies Mpc$^{-2}$." (4.3 Stacking Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Bootstrap with 5000 realizations; comparable uncertainties to map-based; 2D Anderson-Darling tests between bins  
  > "We repeated the stacking process and total aperture flux measurement for $N = 5000$ realizations using randomly selected sources in each density bin with replacement." (4.4 Stacking Noise Estimates)
6. **Derive gas fraction and depletion time**: f_gas = M_ISM/(M_ISM+M*); tau = M_ISM/SFR; compare with Tacconi2018/Carilli2013 redshift evolution  
  > "the depletion time ($\tau=1/ {\rm SFE} =  \mathrm{M}_\mathrm{ISM} / \mathrm{SFR}$)" (5.2.2 Depletion time)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : manual recalibration of SG2, cleaning and imaging  
  > "The data was then cleaned and imaged with CASA." (3 Observations)
- **astropy** : listed in Software section  
  > "astropy (cite: Astropy-CollaborationRobitaille:2013), CASA (cite: McMullin2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of significant detections | 68 of 101 | not stated | galaxies | 3 | Of the 101 galaxies, 68 are significantly detected in our ALMA band 7 data. |
| Optimal aperture radius | 0.54 | not stated | arcsec | 3 | We find an optimal aperture with radius $0.54\ensuremath{''}$ |
| M_ISM ratio intermediate/low density | 1.5 | 0.2 | dimensionless | 5 | galaxies at intermediate densities have ISM masses higher by a factor of $1.5 \pm 0.2$ |
| M_ISM ratio high/low density | 0.7 | 0.2 | dimensionless | 5 | galaxies in the highest density bin have ISM masses lower by a factor of $0.7 \pm 0.2$ |
| M_ISM decrease intermediate to high | 2.1 | 0.6 | dimensionless | 5 | the ISM mass decreases by a factor of $2.1 \pm 0.6$ ($\sim 2\sigma$) |
| Weighted-mean stacked M_ISM, low/intermediate/high density | 0.78 / 1.16 / 0.55 | 0.07 / 0.11 / 0.15 | 1e10 Msun | 5 | / 0.78 $\pm$ 0.07                    / 0.17 $\pm$ 0.02 |
| Depletion time | 210 | 71 | Myr | 6 | $\tau = 210 \pm 71$ Myr |
| Anderson-Darling statistic intermediate vs high | 2.5 | not stated | dimensionless | 5 | we find a AD statistic of 2.5 between the mm fluxes in the intermediate and high densities bins |

## Qualitative findings

- Gas fraction change from intermediate to high density at fixed z equals 2-3 Gyr of cosmic evolution  
  > "at $z=0.73$ it takes a galaxy $2-3$ Gyrs to experience a decrease in the gas fraction by a factor of 1.8" (6.2)

## Claim tuples

- H: ISM mass depends on environment at z~0.73 | E: Stack ALMA Band 7 continuum in three density bins; convert to M_ISM | R: M_ISM elevated at intermediate density (1.5x, ~2.5 sigma), lower at high density (0.7x) | F: ISM mass has a modest dependence on environment | **partially**
- H: Depletion time varies with environment | E: tau = M_ISM/SFR for stacks | R: tau ~ 210 Myr across all densities | F: Depletion time constant | **supported**
- H: Environmental processes drive gas loss at high density | E: Compare gas fraction drop with evolution with redshift | R: Drop by factor 1.8 equals 2-3 Gyr of evolution | F: Mergers and ram pressure stripping/strangulation likely play a role | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust continuum avoids poorly constrained CO-to-H2 conversion and is cheaper than CO  
  > "estimating the ISM mass from CO lines is expensive and uncertain due to the poorly constrained conversion from CO to H$_{2}$" (4.2 ISM Mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Large stellar mass uncertainties reduce significance of f_gas trend; merger fraction differences not significant  
  > "though the uncertainties in stellar mass decrease the significance of this trend" (5.2.1)
- Caveat (inferred, ours): Only ~2.5 sigma significance for key trends; density bin boundaries chosen from data
- Caveat (inferred, ours): Single T_d=25 K and alpha_850 calibration assumed for all densities
- Caveat (inferred, ours): Projected 2D density used as proxy for true environment
- Caveat (inferred, ours): Many non-detections stacked; sample selected by 100 um flux

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA $\#$2015.1.00055.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and recalibration details
- Missing: Gamma_0 definition
- Missing: Stellar masses per galaxy (from Laigle2016 catalog)
- Data volume (inferred): ~10-50 GB (101 short Band 7 pointings, continuum)
- Score (inferred): 3/5, Data and aperture/stacking recipe largely specified, but calibration details and CASA version missing.
- Rediscovery candidate: yes, Data are an ALMA project with stated code, aperture photometry and stacking recipe are numeric and fairly complete, with the Table 2 values as answer keys.

## Links

- Method: (cite: Scoville2014; Scoville2016) (ISM mass from RJ dust continuum calibration)
- Companion: (cite: Darvish2018b) (Environment dependence of gas fraction using Scoville2017 sample)
- Related: COSMOS
- Related: zCOSMOS
- Related: PEP (Herschel)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
