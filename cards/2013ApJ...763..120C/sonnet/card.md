# The Anatomy of an Extreme Starburst within 1.3 Gyr of the Big Bang Revealed by ALMA

`2013ApJ...763..120C` | The Astrophysical Journal 2013 | first author: Carilli, C. L. | arXiv: 1211.6973 | DOI: 10.1088/0004-637X/763/2/120

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What do the [CII] 158um line and dust continuum images of the BRI 1202-0725 group (SMG, quasar, two Lya emitters) reveal about gas dynamics, outflow and the Lya galaxies?  
  > "In this letter, we examine in more detail the imaging results from the ALMA observations, including velocity channel images, position-velocity plots, and line moment images." (abstract)
- Target **BRI 1202-0725**: coordinates Quasar J120523.13-074232.6; SMG J120522.98-074229.5 (Table 1)  
  > "an optically-undetected SMG located 4$"$ (26 kpc) northwest of the quasar at $z= 4.692$" (Introduction); z/distance z = 4.695 (quasar), 4.692 (SMG)  
  > "an optically-undetected SMG located 4$"$ (26 kpc) northwest of the quasar at $z= 4.692$" (Introduction); distance from Omont et al. 1996; Hu, McMahon, Egami 1996  
  > "an optically-undetected SMG located 4$"$ (26 kpc) northwest of the quasar at $z= 4.692$" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00006.SV
- bands: 4 dual-polarization bands of 2 GHz each; one on [CII] (333.960 GHz), three off-line for continuum  
  > "Observations were made with 4 dual-polarization bands of 2GHz bandwidth each." (Observations)
- frequencies and spectral setup: central sky frequency 333.960 GHz; 128 channels per 2 GHz band, Hanning smoothed  
  > "Hanning smoothing was applied on output from the correlator to the 128 channel per 2 GHz band spectral data." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.2'' x 0.8''  
  > "the restoring Gaussian beam was $1.2''\times 0.8''$ resolution (major axis North-South)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 25 minutes, 17 antennas  
  > "These short observations (25 minutes on-source), with only 17 antennas" (Observations)
- observing dates: January 2012  
  > "during science testing and verification in January 2012" (Observations)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um fine structure (1900.539 GHz)
- Other facility **HST**: i-band image for overlay and astrometry  
  > "Figure 1a shows the 340 GHz continuum emission from BRI 1202-0725, overlayed on the HST i-band image." (Results)
- External data: 3C279 flux density at 340 GHz of 17 Jy  
  > "using the flux density at 340GHz of 17Jy derived by Wagg et al. (2012)" (Observations) [from Wagg et al. (2012)]
- External data: Lya image used for overlay  
  > "with the Ly$\alpha$ image of Hu et al. (1996) in color" (Results) [from Hu et al. (1996)]

## Processing

### Calibration

- pipeline or manual: Manual calibration in AIPS  
  > "Calibration of the data was performed using the Astronomical Image Processing System (AIPS)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C279 (17 Jy at 340 GHz), also phase and bandpass  
  > "The source 3C279 was used as a flux density and phase calibrator" (Observations)
- flux scale uncertainty: 15%  
  > "including the 15% uncertainty in absolute gain calibration estimated by Wagg et al. (2012)" (Results)
- self calibration: Amplitude and phase self-cal, 3 min averaging  
  > "Amplitude and phase self-calibration was performed using a 3min averaging time for complex gain solutions." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust R=1  
  > "Imaging was performed using a robust imaging scheme with R=1" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UV-plane subtraction using CLEAN component model from the three off-line bands  
  > "the continuum was subtracted from the UV data using a CLEAN component model derived from the three off-line bands" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channel images at 62.5 MHz (56 km/s); spectra at 31.25 MHz (28 km/s)  
  > "smoothed to a spectral resolution of 62.5 MHz (= 56 km s$^{-1}$)" (Results)
- final beam: 1.2'' x 0.8''  
  > "the restoring Gaussian beam was $1.2''\times 0.8''$ resolution" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Flux scale and observation details  
  > "(see Wagg et al. 2012 for more details)" (Observations) [from Wagg et al. 2012]
- Outflow rate method  
  > "we follow the same approach presented in Maiolino et al. (2012)" (Analysis) [from Maiolino et al. (2012)]
- Optical-radio astrometry alignment  
  > "we follow Carilli et al. (2002) by aligning the quasar position in the HST, Ly$\alpha$, submm continuum, and radio continuum images" (Results) [from Carilli et al. (2002)]

### Not stated but needed to reproduce (our reading)

- Number of CLEAN iterations, masks, cell and image size
- Which channels were line-free and used as continuum
- Self-cal reference model and number of iterations
- Gaussian fitting procedure for spectra
- Conversion factors for FIR luminosity to SFR beyond reference to Carilli & Walter 2013
- CLOUDY model parameters in detail
- Spectrum extraction apertures

## Analysis recipe

1. **Calibrate and self-calibrate**: AIPS calibration with 3C279, then amp+phase self-cal  
  > "Amplitude and phase self-calibration was performed using a 3min averaging time for complex gain solutions." (Observations)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and line cubes**: Robust R=1 imaging, UV continuum subtraction, channel/moment/PV products  
  > "Imaging was performed using a robust imaging scheme with R=1" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Gaussians to spectra**: Gaussian models fit to spectra of each source; double Gaussian for quasar  
  > "For reference, we have fit Gaussian models to the spectra, although admittedly the SMG spectrum is decidedly non-Gaussian." (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive quasar outflow rate and power**: [CII] wing luminosity (+220 to +500 km/s) converted to atomic mass, conical outflow, size 1.5''  
  > "assuming an abundance ratio of $\rm [CII]/H = 1.4\times 10^{-4}$ (Savage & Sembach 1996)" (Analysis)
   - assumption: [CII]/H = 1.4e-4; conical or bi-conical geometry; n >> n_c  
  > "Assuming a simplified conical or bi-conical outflow geometry and a size of 1.5$''$ (=10 kpc)" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
5. **SFR and photoionization test for Lya emitters**: FIR luminosity and Sargsyan [CII]-SFR relation; CLOUDY models of gas 15 kpc from quasar  
  > "We ran a series of simple CLOUDY models (Ferland et al 1998)" (Analysis)
   - software: CLOUDY
   - fitting: _not stated_
   - validation: Predicted UV lines compared to upper limits of Ohyama et al. (2004)  
  > "predicted at luminosities more than a factor of 10 higher than the upper limits placed by Ohyama etal. (2004)" (Analysis)

## Software

- **AIPS** : calibration (and presumably imaging)  
  > "Calibration of the data was performed using the Astronomical Image Processing System (AIPS)." (Observations)
- **CLOUDY** : photoionization models of Lya-1  
  > "We ran a series of simple CLOUDY models (Ferland et al 1998)" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMG 340 GHz flux density | 17 | 2.5 | mJy | 2 | / SMG / J120522.98-074229.5 / $17\pm 2.5$ / 4.6915 / $16 \pm 2.4$ / 712 / |
| Quasar 340 GHz flux density | 18 | 2.7 | mJy | 2 | with flux densities of $17\pm 2.5$mJy and $18\pm 2.7$mJy, respectively |
| Lya-2 continuum flux density | 1.4 | 0.2 | mJy | 2 | is unresolved with a flux density $1.4\pm 0.2$ mJy |
| Lya-1 [CII] FWHM | 56 | not stated | km/s | 3 | The \[CII\] emission from Ly$\alpha$-1 is narrow, with a FWHM $\sim 56$ km s$^{-1}$, centered at $z = 4.6950$. |
| SMG dynamical mass | 3.6e11 [sin(i)/sin(45)]^-2 | not stated | Msun | 0 | this would imply a dynamical mass of $3.6\times 10^{11}$ \[sin(i)/sin(45)\]$^{-2}$ M$_\odot$ to a radius of 5.5 kpc |
| Outflow rate lower limit | >80 | not stated | Msun/yr | 4 | we infer a lower limit on the outflow rate of $\rm \dot{M}_{outfl} > 80 M_{\odot}~ yr^{-1}$ |
| Outflowing atomic gas mass | >2.9e8 | not stated | Msun | 4 | M_{outfl}(atomic) > 2.9\times 10^8 M_{\odot} |
| Lya-2 [CII]/FIR | 0.0005 | not stated | dimensionless | 5 | The \[CII\]/FIR ratio is 0.0005 for Ly$\alpha$-2. |
| Lya-1 [CII] luminosity | 1.9e8 | not stated | Lsun | 5 | the \[CII\] line luminosity is $1.9\times 10^8$ L$_\odot$ |

## Qualitative findings

- Both Lya emitters detected in [CII]; SMG shows east-west velocity gradient; possible quasar outflow and bridge  
  > "We present detections of \[CII\] emission from two Ly$\alpha$-selected galaxies in the group" (abstract)

## Claim tuples

- H: Can ALMA detect [CII] from lower-SFR Lya galaxies easily? | E: 25 min test observation with 17 antennas | R: Lya-1 and Lya-2 detected in [CII] | F: ALMA readily detects [CII] in Lya-selected galaxies | **supported**
- H: Does the quasar drive an outflow? | E: Double Gaussian fit of quasar [CII] and wing luminosity | R: Rate >80 Msun/yr, modest | F: Possible outflow, not dominating gas depletion; energetics cannot distinguish quasar vs starburst | **partially**
- H: Is the quasar the heating source for Lya-1? | E: CLOUDY models | R: Predicted UV lines exceed limits | F: Quasar unlikely to heat and ionize Lya-1 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SMG velocity gradient may not be rotation; could be end-stage merger  
  > "Perhaps the simplest conclusion is that the velocity gradient in the SMG is not due to rotation." (4.1 SMG dynamics)
- How they decided it was enough: _not stated_
- Limitation (authors): Lya-2 line truncated by spectral coverage; luminosity and redshift uncertain  
  > "Hence, we do not know the full velocity extent nor total luminosity of the \[CII\] emission for Ly$\alpha$-2" (Results)
- Limitation (authors): Resolution insufficient to distinguish bridge from blending  
  > "Unfortunately, the current resolution is insufficient to distinguish between a true bridge, or simply blurring" (Discussion)
- Caveat (inferred, ours): Outflow wing is weak and poorly constrained
- Caveat (inferred, ours): Manual imaging details sparse
- Caveat (inferred, ours): Dynamical mass depends on unknown inclination

## Reproducibility

- Data public (paper): ALMA SV data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00006.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, clean depth)
- Missing: Line-free channel definitions
- Missing: Details of Gaussian fitting and aperture choices
- Data volume (inferred): Small, a few GB
- Score (inferred): 3/5, Public SV data and the main steps are described, but the imaging details are sparse and the AIPS-based workflow is old.
- Rediscovery candidate: no, Imaging recipe incomplete and the data are an old SV dataset in an unusual format.

## Links

- Method: Maiolino et al. (2012) (outflow rate method)
- Companion: Wagg et al. (2012) (initial analysis of same ALMA data)
- Companion: Salome et al. (2012) (CO observations of the system)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 37,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
