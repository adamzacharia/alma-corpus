# Anatomy of a blazar in the (sub-)millimeter: ALMA observations of PKS 0521-365

`2016A&A...586A..70L` | Astronomy and Astrophysics 2016 | first author: Leon, S. | arXiv: 1510.07536 | DOI: 10.1051/0004-6361/201527146

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars
- Question: What are the synchrotron and thermal (sub-)millimeter emission properties of the components of the blazar PKS 0521-365 (core, jet, counter-jet, hot spot, perpendicular structure), and how do they vary in time and frequency?  
  > "We aim at analyzing the (sub-)millimeter emission in a nearby blazar, *PKS 0521-365*, to study the synchrotron and thermal emission in the different components detected at low frequency." (abstract)
- Target **PKS 0521-365 (J0522-364)**: coordinates _not stated_; z/distance z = 0.0565; 236 Mpc comoving radial distance  
  > "At $z = 0.0565$, *PKS 0521-365*  is at a comoving radial distance of 236 Mpc, and have a linear scale size of 1.15 kpc/arcsec." (Introduction); distance from redshift with cosmology Omega_m=0.27, Omega_Lambda=0.73, H0=71 (Spergel et al. 2003)  
  > "At $z = 0.0565$, *PKS 0521-365*  is at a comoving radial distance of 236 Mpc, and have a linear scale size of 1.15 kpc/arcsec." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00099.S, 2011.0.00131.S, 2011.0.00467.S, 2011.0.00108.S, 2011.0.00268.S, 2011.0.00210.S, 2011.0.00397.S, 2011.0.00124.S, 2011.0.00768.S, 2011.0.00083.S, 2011.0.00208.S, 2011.0.00223.S, 2011.0.00340.S
- bands: Bands 3, 6 and 7 (87.3-372.5 GHz)  
  > "The observed frequencies go from 87.3 GHz up to 372.5 GHz, which covers bands 3, 6 and 7." (2 Observations and data reduction)
- frequencies and spectral setup: Four spectral windows per EB, generally 2 GHz bandwidth each, two in USB and two in LSB  
  > "Each EB has four spectral windows of, generally, 2 GHz bandwidth distributed over 4 basebands, two in the USB window and two in the LSB window." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: band 3+6+7: 0.53x0.71 arcsec (natural weighting)  
  > "The final spatial resolution with a natural weighting is of $0.53\ensuremath{''}\times 0.71\ensuremath{''}$." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: RMS 158 uJy (3+6+7, no wavelet), 90 uJy after wavelet; band 7 91 uJy  
  > "RMS noise of 158 $\mu$Jy for the band 3+6+7 with a dynamic range (SNR) of 27100 without wavelet filtering" (2 Observations and data reduction)
- time on source: 2 to 4 minutes per execution; total 1.55 hours for combined set  
  > "observed between 2 to 4 minutes per execution" (2 Observations and data reduction); "The total integration time is of 1.55 hours with an equivalent of 66 pad positions and 2145 baselines." (2 Observations and data reduction)
- observing dates: 2011/11/05 to 2012/11/19 (Table)  
  > "the observations span a period of about 1 year from 2012/01/10 to 2012/11/19" (2 Observations and data reduction)
- pi or archival as stated: Public archival Cycle 0 data where the source was a calibrator  
  > "Publicly available data from ALMA Cycle 0 observations were used to analyze the sub-millimeter properties of the blazar *PKS 0521-365*." (2 Observations and data reduction)
- External data: 15 GHz VLA map of PKS 0521-365 used for comparison (RMS 200 uJy)  
  > "The 15 GHz VLA map shown in Falomo et al. (2009) has a similar angular resolution ($\sim 0.5\ensuremath{''}$) to the ALMA data and a RMS noise of 200 $\mu$Jy" (6.2 Double jet, dust or free-free emission) [from Falomo et al. 2009]
- External data: R-band isophote fitting giving host major axis PA~75 deg  
  > "The isophote fitting of the R-band image (Falomo, 1994) indicates that this feature is aligned with the major axis of the host galaxy (PA$\approx 75^\circ$)." (6.2 Double jet, dust or free-free emission) [from Falomo 1994]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration of each dataset before combining within a band  
  > "Before combining the different dataset in each band, a self-calibration was performed on each of them to improve the phase/amplitude gain solutions thanks to the strong continuum emission." (2 Observations and data reduction)

### Imaging

- task: CLEAN in CASA with mfs mode  
  > "computed using the deconvolution CLEAN task in CASA with the multi-frequency synthesis (mfs) mode" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting (uniform weighting for counter-jet search in band 3)  
  > "The final spatial resolution with a natural weighting is of $0.53\ensuremath{''}\times 0.71\ensuremath{''}$." (2 Observations and data reduction); "we searched for the counter-jet emission by using uniform weights during the imaging step" (3 (Sub-)millimeter distribution)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Self-calibrated datasets combined per band, then all into band 3+6+7 superset  
  > "The self-calibrated datasets were combined in each band and imaged." (2 Observations and data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 90 uJy for band 3+6+7 after wavelet filtering  
  > "A final equivalent RMS noise of 90 $\mu$Jy can be achieved for the band 3+6+7." (2.1 Wavelet filtering)

### Inherited from earlier work

- Multi-frequency synthesis details  
  > "see Rau & Cornwell (2011) for details" (2 Observations and data reduction) [from Rau & Cornwell (2011)]
- Wavelet a trous method and scale-to-size relation  
  > "As described in Leon et al. (2000) we use the "A trous" algorithm (see Bijaoui 1991)." (2.1 Wavelet filtering) [from Leon et al. (2000); Bijaoui 1991]
- Jet/counter-jet ratio formula  
  > "can be estimated as following (e.g. in Ghisellini et al. 1993):" (3 (Sub-)millimeter distribution) [from Ghisellini et al. 1993]
- Variability index definition  
  > "The variability index VI (Ciaramella et al., 2004) was introduced to parametrize the flux variation of a source" (4 (Sub-)millimeter variability) [from Ciaramella et al. 2004]

### Not stated but needed to reproduce (our reading)

- CASA version and whether archive calibration or manual scripts were used
- Flux calibrator and flux scale uncertainty
- Self-calibration solution intervals and iterations
- CLEAN parameters (cell, image size, threshold, masks)
- Wavelet pixel size and per-scale noise estimation method
- Region definitions (polygons) for jet and counter-jet
- Method of stacking datasets for the counter-jet
- Spectral index fitting procedure

## Analysis recipe

1. **Self-calibrate and image each dataset**: Self-calibration of each dataset, CLEAN mfs imaging; core and HS fluxes measured  
  > "The HS flux was measured including the pixels above 3-$\sigma$ of the RMS in the HS area." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: HS flux in band 3 with band 7 uv-coverage is 5% lower  
  > "The HS flux is in that case lower by 5% compared to the measured flux with the full uv-coverage." (2 Observations and data reduction)
2. **Combine datasets and wavelet filter**: A trous wavelet transform with B3 spline, coefficients thresholded at 4.5 sigma, 7 scales  
  > "In this study the wavelet coefficients are filtered at the 4.5-$\sigma$ level." (2.1 Wavelet filtering)
   - parameter: threshold 4.5 sigma per scale  
  > "In this study the wavelet coefficients are filtered at the 4.5-$\sigma$ level." (2.1 Wavelet filtering)
   - fitting: _not stated_
   - validation: _not stated_
3. **Detect point sources**: SExtractor on WT-filtered band 3+6+7 at 4.5 sigma, minimum 5 pixels  
  > "using the SExtractor software (Bertin & Arnouts, 1996) at a 4.5-$\sigma$ level with a minimum of 5 pixels per sources" (3 (Sub-)millimeter distribution)
   - software: SExtractor
   - fitting: _not stated_
   - validation: Counts compared with Hatsukade et al. (2013)  
  > "this estimation is similar, but lower, to the one derived by Hatsukade et al. (2013) using ALMA fields at 238 GHz" (3 (Sub-)millimeter distribution)
4. **Derive jet geometry from jet/counter-jet ratio**: Subtract Gaussian nucleus, measure jet and counter-jet in polygons; compare ratio to J=((1+b cos t)/(1-b cos t))^p  
  > "The jet and counter-jet flux was estimated by subtracting to the image a Gaussian source fitting the nucleus and selecting a polygonal area on the jet and the counter-jet." (3 (Sub-)millimeter distribution)
   - parameter: p = 2.5  
  > "taking an intermediate exponent $p = 2.5$ which is used for the analysis" (3 (Sub-)millimeter distribution)
   - assumption: equal intrinsic emission in jet and counter-jet  
  > "Assuming an equal intrinsic emission between the jet and the counter-jet" (3 (Sub-)millimeter distribution)
   - fitting: _not stated_
   - validation: Compared with Pian et al. 1996 and Tingay et al. 2002  
  > "These results are similar to the values obtained by Pian et al. (1996)" (3 (Sub-)millimeter distribution)
5. **Variability and spectral index**: VI=(Smax-Smin)/(Smax+Smin) per band; spectral index from core flux in the 4 basebands; A/B fluxes in 1 arcsec aperture  
  > "The spectral index was computed measuring the core flux at the 4 basebands of a given dataset" (5 Spectral index)
   - parameter: 1 arcsec circular aperture for A and B  
  > "we take a fixed circular aperture of 1$''$ around the peak emission to estimate the flux" (5 Spectral index)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN mfs imaging  
  > "computed using the deconvolution CLEAN task in CASA with the multi-frequency synthesis (mfs) mode" (2 Observations and data reduction)
- **SExtractor** : point-source extraction  
  > "The list of the point sources was obtained by using the SExtractor software (Bertin & Arnouts, 1996)" (3 (Sub-)millimeter distribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dynamic range band 3+6+7 after wavelet filtering | 47000 | not stated | dimensionless | 2 | band 3+6+7 / 221.02 / $0.53\times 0.71$ (PA=90$^\circ$) / 90 / 47000 / 43 |
| Jet/counter-jet ratio | 10.2 | not stated | dimensionless | 4 | The emission ratio between the jet and the counter-jet was found to be $\Re = 10.2$. |
| Viewing angle range | 16-38 deg | not stated | deg | 4 | the viewing angle must be in the range $\theta \subset [16^\circ,38^\circ]$ with a moderate bulk velocity $\beta \subset [0.45, 0.55]$ |
| Doppler factor range | 1.3-1.7 | not stated | dimensionless | 4 | These values give us a Lorentz factor $\Gamma \subset [1.1,1.2]$ and a Doppler factor $\delta \subset [1.3,1.7]$. |
| Variability index B3, B6, B7 | 0.33, 0.06, 0.40 (text); Table lists 0.40, 0.23, 0.48 | not stated | dimensionless | 5 | $VI_{B3} = 0.33$, $VI_{B6} =  0.06$ and $VI_{B7} = 0.40$ |
| Mean core spectral index band 7 / band 3 | -0.43 / -0.08 | not stated | dimensionless | 5 | $-0.43$ in band 7 versus $-0.08$ in band 3 |
| Hot spot spectral index | -1.6 | not stated | dimensionless | 5 | The HS discloses a steep distribution with a spectral index of $-1.6$ |
| Counter-jet spectral index | -2.9 | not stated | dimensionless | 5 | The very low value, $-2.9$, of the spectral index of the counter-jet |
| Hot spot deprojected distance | 19.8 | not stated | kpc | 4 | Assuming a viewing angle of $30^\circ$ for the jet we estimate the distance from the center to be 19.8 kpc. |
| Detected point sources in 1'x1' box | 16 | not stated | sources | 3 | A total of 16 sources are detected in a $1\ensuremath{'}\times1\ensuremath{'}$ box |

## Qualitative findings

- A new elongated structure roughly perpendicular to the jet is detected; thermal origin favoured.  
  > "Finally a new structure is detected roughly perpendicular to the radio jet and a thermal emission origin is currently favoured." (abstract)

## Claim tuples

- H: Is the jet strongly beamed? | E: Jet/counter-jet ratio compared with beaming model | R: R = 10.2; theta 16-38 deg, beta 0.45-0.55, delta 1.3-1.7 | F: Emission is not highly beamed; consistent with VLBI constraints | **supported**
- H: Does the mm flux vary and how does the SED differ across components? | E: Flux and spectral index per dataset over ~1 year | R: Large variations, core steepens to band 7, A/B flat, HS -1.6, counter-jet -2.9 | F: SED differs by component and time | **supported**
- H: Is the perpendicular structure thermal or synchrotron? | E: Morphology plus comparison with 15 GHz VLA map | R: Not seen at 15 GHz | F: Dust emission favoured, needs confirmation | **partially**

## Reasoning

- Why this data: Calibrator observations in many projects give multi-epoch, multi-band data of the source.  
  > "using calibration data of several unrelated scientific projects" (4 (Sub-)millimeter variability)
- Why this method: _not stated_
- Alternative: Synchrotron origin of the perpendicular feature disfavoured by non-detection at 15 GHz.  
  > "No hint of an elongated feature along the major axis is visible on the 15 GHz map" (6.2 Double jet, dust or free-free emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Irregular, sparse time sampling prevents robust variability analysis; VI are lower limits.  
  > "These values of the VI must be considered as lower limit during the year 2012 since the sampling is sparser than the variability" (4 (Sub-)millimeter variability)
- Caveat (inferred, ours): Text and table VI values disagree
- Caveat (inferred, ours): Flux calibration of calibrator-quality data and absolute scale uncertainties not given
- Caveat (inferred, ours): Counter-jet ratio depends on assumed p and equal intrinsic emission
- Caveat (inferred, ours): Text refers to source #36 though only 16 sources are listed

## Reproducibility

- Data public (paper): Public ALMA Cycle 0 archive data  
  > "Here we present archival ALMA observations of the radio source *PKS 0521-365*." (Introduction)
- Products in archive: _not stated_
- Missing: CASA version and calibration details
- Missing: Self-calibration parameters
- Missing: Wavelet noise estimation and code
- Missing: Region definitions
- Data volume (inferred): Tens of GB across 13 Cycle 0 projects (continuum calibrator scans)
- Score (inferred): 5/5, Data public and steps outlined, but many processing parameters missing.
- Rediscovery candidate: no, Recipe lacks key imaging and self-calibration parameters and requires custom wavelet code.

## Links

- Method: Leon et al. (2000) (Wavelet a trous analysis method)
- Method: Rau & Cornwell (2011) (Multi-frequency synthesis)
- Companion: Tingay & Edwards (2002) (VLBI beaming constraints compared)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 13,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 40,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
