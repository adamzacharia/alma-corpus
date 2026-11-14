# First detection of the 448 GHz H<SUB>2</SUB>O transition in space

`2017A&A...601L...3P` | Astronomy and Astrophysics 2017 | first author: Pereira-Santaella, M. | arXiv: 1704.05278 | DOI: 10.1051/0004-6361/201730851

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Detect the H2O 4_23-3_30 448 GHz transition in the LIRG ESO 320-G030 and determine whether it is excited by collisions or by far-IR radiative pumping  
  > "the determination of the dominant excitation mechanism, which might vary from source to source, is required to properly interpret the $4_{23}-3_{30}$ emission" (Introduction)
- Target **ESO 320-G030 (IRAS F11506-3851)**: coordinates _not stated_; z/distance D = 48 Mpc; 235 pc/arcsec  
  > "ESO 320-G030 (IRAS F11506-3851; $D = 48$ Mpc; 235 pc arcsec$^{-1}$)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00263.S
- bands: Band 8  
  > "We obtained band 8 ALMA observations of ESO 320-G030 on 2016 November 16" (2 ALMA data reduction)
- frequencies and spectral setup: spectral window centered at 443.0 GHz, 1.875 GHz bandwidth, 1.95 MHz channels  
  > "a spectral window centered at 443.0 GHz (1.875 GHz/1270 km s$^{-1}$ bandwidth and 1.95 MHz/1.3 km s$^{-1}$ channels)" (2 ALMA data reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 42 antennas  
  > "using 42 antennas of the 12-m array" (2 ALMA data reduction)
- configurations: _not stated_
- baselines: 15 m to 920 m  
  > "The baselines ranged from 15 m to 920 m" (2 ALMA data reduction)
- angular resolution: 0.26"x0.24" (~60 pc), PA 58 deg  
  > "beam with a full-width half-maximum (FWHM) of 0.26$''$$\times$0.24$''$ ($\sim$60 pc) and a position angle (PA) of 58$^\circ$" (2 ALMA data reduction)
- max recoverable scale: ~2 arcsec  
  > "maximum recoverable scale of $\sim$2$''$ based on the ALMA Cycle 4 Technical Handbook equations" (2 ALMA data reduction)
- sensitivity: ~4.8 mJy/beam per 20 km/s channel  
  > "The 1$\sigma$ sensitivity is $\sim$4.8 mJy beam$^{-1}$ per channel." (2 ALMA data reduction)
- time on source: 10.5 min  
  > "The total on-source integration time was 10.5 min." (2 ALMA data reduction)
- observing dates: 2016 November 16  
  > "We obtained band 8 ALMA observations of ESO 320-G030 on 2016 November 16" (2 ALMA data reduction)
- pi or archival as stated: _not stated_
- Line: ortho-H2O 4_23-3_30 (448.001 GHz)
- Other facility **Herschel/PACS**: H2O 79 micron absorption line (HerMoLIRG program)  
  > "was observed with *Herschel*/PACS (cite: Pilbratt2010Herschel; Poglitsch2010PACS) within the open time program HerMoLIRG" (4 Modeling)
- External data: Systemic velocity from CO(2-1) and 233 GHz and 244 GHz continuum fluxes, free-free contribution  
  > "using the systemic velocity $v_{\rm radio} = 3049\pm2$ km s$^{-1}$, derived from CO(2–1)" (3 Data analysis) [from Pereira2016b (companion paper, cite: Pereira2016b)]
- External data: Rest frequency of H2O transition and CH2NH lines  
  > "(448001 MHz; (cite: Pickett1998))" (3 Data analysis) [from (cite: Pickett1998)]

## Processing

### Calibration

- pipeline or manual: reduced and calibrated with CASA  
  > "The data were reduced and calibrated using the ALMA reduction software CASA (v4.7.0; (cite: McMullin2007))." (2 ALMA data reduction)
- casa version: CASA 4.7.0  
  > "CASA (v4.7.0; (cite: McMullin2007))" (2 ALMA data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1229+0203 (3C 273), 2.815 Jy at 449.6 GHz, alpha=-0.78  
  > "we used J1229+0203 (3C 273) assuming a flux density of 2.815 Jy at 449.6 GHz and a spectral index $\alpha=-0.78$" (2 ALMA data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, R = 0.5  
  > "we used the Briggs weighting with $R=0.5$" (2 ALMA data reduction)
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "The final data-cube has 300$\times$300 pixels of 0.05$''$" (2 ALMA data reduction)
- image size: 300x300 pixels  
  > "The final data-cube has 300$\times$300 pixels of 0.05$''$" (2 ALMA data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum per pixel from median of line-free channels  
  > "We estimated the continuum level in each pixel from the median flux density in the line-free channels of the spectral window." (3 Data analysis)
- line free channels: _not stated_
- primary beam correction: corrected for mosaic primary beam pattern  
  > "We corrected the data-cube for the primary beam pattern of the mosaic." (2 ALMA data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.26"x0.24", PA 58 deg  
  > "0.26$''$$\times$0.24$''$ ($\sim$60 pc) and a position angle (PA) of 58$^\circ$" (2 ALMA data reduction)
- final rms: ~4.8 mJy/beam per channel  
  > "The 1$\sigma$ sensitivity is $\sim$4.8 mJy beam$^{-1}$ per channel." (2 ALMA data reduction)

### Inherited from earlier work

- H2O excitation models based on earlier models  
  > "The models, based on those reported in , use the observed size ($R=35$ pc)" (4 Modeling) [from GonzalezAlfonso2014 (cite: GonzalezAlfonso2014)]
- Equivalent radius of uniform disk = 0.8 x FWHM  
  > "For a uniform-brightness disk, the equivalent radius is $0.8\times{\rm FWHM}$ (cite: Sakamoto2008)" (3 Data analysis) [from (cite: Sakamoto2008)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum
- Clean threshold, mask and number of iterations
- Phase, bandpass and gain calibrators
- Continuum fluxes at 244 GHz and free-free derivation (in companion paper)
- Model code and grid details for radiative transfer
- Monte Carlo bootstrap details and priors for the gray-body fit

## Analysis recipe

1. **Continuum map and flux**: Per-pixel median of line-free channels; total in central 200 pc  
  > "The measured total continuum emission in the central 200 pc is 183 $\pm$ 4 mJy." (3 Data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract nuclear spectrum and fit line**: 0.8" aperture spectrum from continuum-subtracted cube; Gaussian fit  
  > "we extracted the nuclear spectrum using a $d=0.8\ensuremath{''}$ aperture" (3 Data analysis)
   - fitting: Gaussian profile  
  > "We fitted a Gaussian to the H$_2$O $4_{23}-3_{30}$ profile" (3 Data analysis)
   - validation: Rest frequency compared with expected; Herschel water detections  
  > "This line identification is also supported by the detection of strong far-IR and sub-mm water transitions in the *Herschel* observations of this object" (3 Data analysis)
3. **Sizes and kinematics**: 2D Gaussian fits to continuum and moment-0 maps; pixel-by-pixel Gaussian for velocity field (>3 sigma)  
  > "we measured the sizes of the emitting regions by fitting a 2D Gaussian." (3 Data analysis)
   - fitting: 2D Gaussian; per-pixel Gaussian  
  > "we measured the sizes of the emitting regions by fitting a 2D Gaussian." (Data analysis)
   - validation: _not stated_
4. **Dust temperature and optical depth**: Gray-body fit to 448 and 244 GHz continuum after subtracting free-free, Monte Carlo bootstrap  
  > "we solved the gray-body equation assuming $1.5<\beta<1.85$ and using a Monte Carlo bootstrapping method" (3 Data analysis)
   - assumption: beta between 1.5 and 1.85; free-free ~7 mJy  
  > "we subtracted the free-free contribution at these frequencies ($\sim$7 mJy; )" (3 Data analysis)
   - fitting: Monte Carlo bootstrapping  
  > "using a Monte Carlo bootstrapping method to estimate the confidence intervals" (Data analysis)
   - validation: _not stated_
5. **Radiative transfer modeling of H2O 448 GHz**: Models of L(H2O 448) vs tau for Tdust 50, 65, 80 K; compare with observed luminosity, continuum and Herschel 79 micron absorption  
  > "Figure  shows the model predictions for the H$_2$O 448 GHz luminosity as a function of the continuum optical depth" (4 Modeling)
   - parameter: R = 35 pc; N_H2O = 2e18 or 8e18 x tau100; n_H2 = 3e4 cm-3; Tgas = 150 K  
  > "Collisional excitation (included in the models with $n_{\mathrm{H2}}=3\times10^4$ cm$^{-3}$ and $T_{\mathrm{gas}}=150$ K)" (4 Modeling)
   - assumption: Gas-to-dust ratio 100 by mass  
  > "for a standard gas-to-dust ratio of 100 by mass" (4 Modeling)
   - fitting: _not stated_
   - validation: Compared with Herschel/PACS 79 micron absorption of -920 Jy km/s  
  > "the observed value ($-920$ Jy km s$^{-1}$ between $-150$ and $+150$ km s$^{-1}$" (4 Modeling)

## Software

- **CASA** 4.7.0: data reduction and calibration  
  > "The data were reduced and calibrated using the ALMA reduction software CASA (v4.7.0; (cite: McMullin2007))." (2 ALMA data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux, central 200 pc | 183 | 4 | mJy | 1 | The measured total continuum emission in the central 200 pc is 183 $\pm$ 4 mJy. |
| H2O 448 GHz line flux | 37.0 | 0.7 | Jy km/s | 2 | We obtained a total flux of 37.0 $\pm$ 0.7 Jy km s$^{-1}$, a velocity of 3045 $\pm$ 1 km s$^{-1}$, and a FWHM of 161 $\pm$ 2 km s$^{-1}$. |
| H2O line FWHM | 161 | 2 | km/s | 2 | a FWHM of 161 $\pm$ 2 km s$^{-1}$ |
| Observed line frequency | 443451 | 2 | MHz | 2 | A line is detected at 443451 $\pm$ 2 MHz. |
| Deconvolved H2O emission size | 40 | 3 | pc | 3 | equivalent to a deconvolved FWHM of 40$\pm$3 pc |
| Dust temperature | 25-80 | not stated | K | 4 | We find that $T_{\rm dust}=25-80$ K and $\tau_{\rm 448\,GHz}=0.2-1.3$. |
| H2O 448 GHz luminosity | 3.8e4 | not stated | Lsun | 5 | The horizontal shaded rectangle indicates the measured value of $3.8\times10^4$ $L_{\odot}$ |

## Qualitative findings

- H2O 448 GHz is not masing; excited by radiative far-IR pumping via 78.7 and 132.4 micron lines  
  > "The excitation is dominated in all cases by radiative pumping through the $4_{23}-3_{12}$ and $4_{23}-4_{14}$ lines at $78.7$ and $132.4$ $\mu$m" (4 Modeling)

## Claim tuples

- H: The 448 GHz H2O line is detectable in nearby galaxies with ALMA | E: Band 8 observation of ESO 320-G030 | R: Line at 443451 MHz, 37.0 Jy km/s, matching 448.001 GHz | F: First detection of the transition in space | **supported**
- H: Line is collisionally or radiatively excited | E: Radiative transfer models compared with L, continuum and Herschel 79 micron absorption | R: Radiative pumping dominates; Tdust >~ 60 K | F: Line arises in warm buried nucleus regions and traces far-IR field | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Higher abundance (6e-6) with Tdust=50 K model disfavored by Herschel 79 micron absorption  
  > "While the $T_{\mathrm{dust}}\sim50$ K model underpredicts the pumping H$_2$O 79 $\mu$m absorption" (4 Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): CH2NH blending likely negligible; dust values may be higher in compact region  
  > "These values may be significantly higher in the more compact region sampled by the H$_2$O 448 GHz emission." (3 Data analysis)
- Caveat (inferred, ours): Model details are not given, so the excitation conclusion cannot be checked
- Caveat (inferred, ours): Short 10.5 min observation; CH2NH identification is tentative
- Caveat (inferred, ours): Model degeneracy between abundance and Tdust

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Radiative transfer model code and inputs
- Missing: Companion-paper continuum measurements
- Missing: Cleaning parameters and calibrators
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, The imaging and line-fit steps are specified, but the modeling is not reproducible from the text.
- Rediscovery candidate: no, The imaging and line measurements could be redone, but the modeling step cannot be reproduced and the data are not stated to be public.

## Links

- Method: GonzalezAlfonso2014 (Basis of H2O excitation models)
- Companion: Pereira2016b (cite: Pereira2016b) (CO(2-1) and 1.3 mm continuum data on the same galaxy)
- Related: HerMoLIRG

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 43,
  "rate": 0.614
 },
 "evidence_ok": true
}
```
