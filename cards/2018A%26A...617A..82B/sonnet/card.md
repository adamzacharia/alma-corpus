# The WISSH quasars project. V. ALMA reveals the assembly of a giant galaxy around a z = 4.4 hyper-luminous QSO

`2018A&A...617A..82B` | Astronomy and Astrophysics 2018 | first author: Bischetti, M. | arXiv: 1804.06399 | DOI: 10.1051/0004-6361/201833249

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the host galaxy and environment properties of the hyper-luminous QSO J1015+0020 at z~4.4, and how do SMBH and host galaxy growth compare?  
  > "we selected the QSO J1015$+$0020 at $z=4.4$ for a pilot ALMA observing programme aimed to characterise the host galaxy and environment properties of hyper-luminous QSOs." (Introduction)
- Target **SDSS J1015+0020**: coordinates RA 10:15:49.00, Dec +00:20:20.03  
  > "WISSH QSO SDSS J1015$+$0020 (celestial coordinates RA 10:15:49.00, Dec +00:20:20.03)" (2 ALMA observation and data analysis); "given the SDSS DR10 redshift $z_{\rm SDSS} = 4.400$ (cite: Paris14)" (2 ALMA observation and data analysis); z/distance z_SDSS = 4.400; z_[CII] = 4.407  
  > "WISSH QSO SDSS J1015$+$0020 (celestial coordinates RA 10:15:49.00, Dec +00:20:20.03)" (2 ALMA observation and data analysis); "given the SDSS DR10 redshift $z_{\rm SDSS} = 4.400$ (cite: Paris14)" (2 ALMA observation and data analysis); distance from SDSS DR10 (Paris14); [CII] line centroid  
  > "WISSH QSO SDSS J1015$+$0020 (celestial coordinates RA 10:15:49.00, Dec +00:20:20.03)" (2 ALMA observation and data analysis); "given the SDSS DR10 redshift $z_{\rm SDSS} = 4.400$ (cite: Paris14)" (2 ALMA observation and data analysis)

## Data provenance

- ALMA projects: 2016.1.00718.S
- bands: Band 7  
  > "We used the ALMA band 7 receiver and the frequency division mode of the ALMA correlator." (2 ALMA observation and data analysis)
- frequencies and spectral setup: four 1.875 GHz spws (7.5 GHz total), 31.25 MHz resolution; one centred at ~352 GHz on [CII]  
  > "This provided us with four spectral windows of 1.875 GHz width, for a total spectral coverage of 7.5 GHz, with a spectral resolution of 31.25 MHz." (2 ALMA observation and data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-5  
  > "in C36-5 configuration with a maximum projected baseline of 1396 m" (2 ALMA observation and data analysis)
- baselines: maximum projected baseline 1396 m  
  > "in C36-5 configuration with a maximum projected baseline of 1396 m" (2 ALMA observation and data analysis)
- angular resolution: 0.18'' x 0.21''  
  > "ALMA high-resolution ($0.18''\times0.21''$) observation" (abstract)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.04 mJy/beam  
  > "with a rms sensitivity of 0.04 mJy beam$^{-1}$" (3.1 Continuum and [CII] emission maps)
- time on source: 0.6 hours  
  > "for a 0.6 hours on-source integration time" (2 ALMA observation and data analysis)
- observing dates: 5 March 2016  
  > "The observation was carried out on 5 March 2016" (2 ALMA observation and data analysis)
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2-2P1/2 fine structure (157.74 um (wavelength as stated))
- Other facility **Herschel/SPIRE, WISE, SDSS, UKIDSS**: Photometry and SDSS spectrum for SED fitting and CIV black hole mass  
  > "We added the ALMA data to the SDSS DR10 (cite: Paris14), WISE (cite: Wright10), and *Herschel*/SPIRE (cite: Pilbratt10; Griffin10) photometry, presented in (cite: Duras17)." (4.2)
- External data: 850 um Log(N)-Log(S) number counts  
  > "By using the Log(N)$-$Log(S) at 850 $\mu$m derived by (cite: Simpson2015c)" (4.1) [from (cite: Simpson2015c)]
- External data: L_[CII] and L_FIR for 42 z~4-7 QSOs  
  > "we collected $L_{\rm [CII]}$ and $L_{\rm FIR}$ for 42 sources from the works of (cite: Wang13; Wang16; Venemans16; Venemans17" (4.2) [from (cite: Wang13; Wang16; Venemans16; Venemans17; Willott13; Willott15; Willott17; Kimball15; Diaz-Santos16; Decarli17; Decarli18)]
- External data: Herschel/SDSS/WISE photometry of J1015+0020  
  > "photometry, presented in (cite: Duras17)" (4.2) [from (cite: Duras17)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline mode with default calibrators  
  > "calibrated with the CASA 4.7.0 software (cite: McMullin07) in pipeline mode by applying the default phase, bandpass, and flux calibrators provided" (2 ALMA observation and data analysis)
- casa version: CASA 4.7.0  
  > "calibrated with the CASA 4.7.0 software" (2 ALMA observation and data analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Images were produced using the CASA task clean with natural weights, a 0.03 arcsec pixel size and a 30 km s$^{-1}$ channel width" (2 ALMA observation and data analysis)
- deconvolver: _not stated_
- weighting robust: natural weights  
  > "clean with natural weights" (2 ALMA observation and data analysis)
- uv taper: _not stated_
- cell size: 0.03 arcsec  
  > "a 0.03 arcsec pixel size" (2 ALMA observation and data analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: first-degree polynomial fit in uv plane to first two spws  
  > "fitting the UV plane of the first two spectral windows by a first degree polynomial and then subtracted to the visibilities" (2 ALMA observation and data analysis)
- line free channels: continuum map averages all spws excluding 1.2 GHz around [CII]  
  > "averaging over all the spectral windows and excluding 1.2 GHz around the \[CII\] emission" (2 ALMA observation and data analysis)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.18'' x 0.22''  
  > "a final beam size of $0.18''\times0.22''$" (2 ALMA observation and data analysis)
- final rms: _not stated_

### Inherited from earlier work

- Dynamical mass disk formula, D=1.5x deconvolved major axis, v_circ=0.75 FWHM/sin i  
  > "computed as 1.5 times the deconvolved major axis (cite: Wang13)" (5.1) [from (cite: Wang13)]
- SFR from L_FIR  
  > "the SFR derived by following (cite: Kennicutt12)" (4.2) [from (cite: Kennicutt12)]
- AGN contributes ~50% of FIR luminosity for Lbol>10^47  
  > "who found that in hyper-luminous QSOs with Log($L_{\rm Bol}$/erg s$^{-1}$)$> 47.0$ the AGN contributes to about 50% of the total FIR luminosity" (4.2) [from (cite: Duras17)]

### Not stated but needed to reproduce (our reading)

- Which spw/channels define the line-free continuum and cleaning threshold/mask
- Primary beam correction details and flux scale uncertainty
- SED fitting code, templates and priors
- Aperture/region definitions and fitting software for 2D Gaussians
- Orthogonal regression implementation
- Whether self-calibration was applied

## Analysis recipe

1. **Calibrate and image continuum and [CII] cube**: CASA pipeline calibration; clean with natural weights; uv continuum subtraction  
  > "Images were produced using the CASA task clean with natural weights, a 0.03 arcsec pixel size and a 30 km s$^{-1}$ channel width" (2 ALMA observation and data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure source fluxes and sizes**: 2D Gaussian fits in image plane for sources with S/N>5; one or two Gaussian components for [CII] spectra  
  > "continuum and \[CII\] flux densities were measured by fitting a 2D Gaussian model to the final map in the image plane" (2 ALMA observation and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Assess overdensity of continuum sources**: Poisson probability using 850 um Log(N)-Log(S) over a 4''x4'' region  
  > "assuming a Poissonian distribution with average number of successes equal to the expected number counts, the probability of having two detections is $\sim2\times10^{-4}$" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fit and SFR**: SED fit of QSO with SPIRE fluxes rescaled by 3.76 to remove Cont1/Cont2 contamination; SFR via Kennicutt12 and halved for AGN contribution; [CII]-SFR from Sargsyan14  
  > "we rescaled the SPIRE fluxes by a factor $r_{\rm cont}=3.76$" (4.2)
   - fitting: _not stated_
   - validation: Residual SPIRE excess reduced in SED B  
  > "This feature is significantly reduced in SED B, indicating that the main contributors to this excess have been removed." (4.2)
5. **Black hole mass from CIV**: Fit 1300-1700 A with power law plus two Gaussians; single-epoch relation of Vestergaard06 with Coatman17 blueshift correction  
  > "we fit the spectral region between 1300 Å and 1700 Å with a model consisting of a power law to reproduce the continuum emission" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **Dynamical masses**: Disk formula with inclination from axis ratio i=arccos(amin/amaj)  
  > "the inclination of the disk can be estimated from the ratio of semi-minor to semi-major axes as $i=arcos(a_{\rm min}/a_{\rm maj})$" (5.1)
   - assumption: ISM in inclined rotating disk  
  > "Under the assumption that the ISM is mainly distributed in an inclined, rotating disk" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
7. **Growth timescales**: t_acc=M_BH/Macc, t_SFR=Mdyn/SFR, exponential t_Edd and t_tau  
  > "A basic estimate of the present $M_{\rm BH}$ growth timescale can be derived as the ratio $t_{\rm acc} = M_{\rm BH}/\dot{M}_{\rm acc}$" (5.2)
   - assumption: accretion efficiency 0.1  
  > "once assumed a standard accretion efficiency $\epsilon=0.1$" (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration (pipeline) and imaging with clean  
  > "Visibilities were calibrated with the CASA 4.7.0 software (cite: McMullin07) in pipeline mode" (2 ALMA observation and data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| QSO continuum flux density (840 um) | 595 | 64 | uJy | 2 | 595$\pm$64 |
| QSO [CII] flux | 0.47 | 0.05 | Jy km/s | 2 | $f_{\rm [CII]}^{\rm QSO} = 0.47\pm 0.05$ Jy km s$^{-1}$ |
| z_[CII] | 4.407 | not stated | dimensionless | 2 | corresponding to a \[CII\]-based redshift $z_{\rm[CII]}=4.407$ |
| CompA [CII] FWHM | 60 | 13 | km/s | 2 | FWHM$_{\rm[CII]}^{\rm A} = 60\pm13$ km s$^{-1}$ |
| QSO SFR (SED B, AGN-corrected) | ~100 | not stated | Msun/yr | 4 | the resulting SFR of J1015$+$0020 is $\sim100$ M$_\odot$ yr$^{-1}$ |
| Log(L_[CII]/L_FIR) | -3.64 | +0.31/-0.18 | dimensionless | 4 | Log($L_{\rm [CII]}$/$L_{\rm FIR}$) = $-$3.64$^{+0.31}_{-0.18}$ |
| L_[CII]/L_FIR slope alpha | -0.61 | 0.06 | dimensionless | 4 | $\alpha = -0.61\pm0.06$ and $\beta = 4.5\pm0.8$ |
| M_BH | 5.7e9 | +3.4/-2.1 e9 | Msun | 5 | $5.7^{+3.4}_{-2.1}\times10^9$ M$_\odot$ |
| Eddington ratio | 0.23 | +0.14/-0.09 | dimensionless | 5 | $\lambda_{\rm Edd} = 0.23^{+0.14}_{-0.09}$ |
| Log(M_dyn) QSO | 10.6 | 0.3 | log Msun | 6 | Log$(M_{\rm dyn}/\rm M_\odot)=10.6\pm0.3$ |
| Total M_dyn QSO+companions | ~2.2e11 | not stated | Msun | 6 | $M_{\rm dyn}^{\rm Tot}\sim2.2\times10^{11}$ M$_\odot$ |
| Macc | 30 | 7 | Msun/yr | 7 | $\dot{M}_{\rm acc}=30\pm7$ M$_\odot$ yr$^{-1}$ |

## Qualitative findings

- Three [CII] companions (2.2, 8, 17 kpc) and two continuum emitters at ~3.5'' indicate a significant overdensity around the QSO.  
  > "Our analysis reveals an exceptional overdensity of \[CII\]-emitting companions with a very small ($<150$ km s$^{-1}$) velocity shift with respect to the QSO redshift." (abstract)

## Claim tuples

- H: Is J1015+0020 in an overdense environment? | E: ALMA [CII] and 840 um maps compared with number counts | R: 3 [CII] companions; two continuum sources ~100x above expected counts | F: Significant overdensity of star-forming galaxies | **supported**
- H: How does the QSO host compare to the local M_BH-M_dyn relation? | E: CIV black hole mass and [CII] dynamical mass | R: M_dyn/M_BH ~7 | F: Host is far below local ratio; will grow via mergers | **supported**
- H: Do host and SMBH grow on comparable timescales? | E: Compare t_acc, t_SFR, t_Edd, t_tau | R: comparable for constant Macc/SFR; host faster for constant Eddington/tau | F: Host growth timescale comparable or shorter than SMBH | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: M82-like template for Cont1 rejected; Arp220-like compatible  
  > "A M82-like template does not match with the upper limits at any redshift in this range." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclinations and sizes of marginally resolved sources are uncertain, affecting dynamical masses  
  > "inclination estimates of marginally resolved sources (such as J1015$+$0020 and CompA), detected at moderate signal-to-noise ratio, can be altered by non-circular beam shapes." (5.1)
- Caveat (inferred, ours): Single short observation; low S/N detections (~6 sigma) for companions
- Caveat (inferred, ours): Cont1/Cont2 association with the QSO rests on statistical argument without redshifts
- Caveat (inferred, ours): Dynamical masses depend on uncertain inclinations from Gaussian axis ratios
- Caveat (inferred, ours): CIV-based M_BH has large systematic uncertainty

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Cleaning threshold and mask
- Missing: SED fitting code/templates
- Missing: Exact region definitions for spectra
- Data volume (inferred): ~10-30 GB raw single-EB Band 7 dataset
- Score (inferred): 3/5, Single archival-type dataset with pipeline calibration and natural weighting is simple to redo, but SED fitting and some imaging details are unspecified.
- Rediscovery candidate: no, Public status of the data is not explicitly stated in the paper and several recipe details are missing.

## Links

- Method: (cite: Coatman17) (CIV blueshift-corrected black hole mass relation)
- Method: (cite: Wang13) (dynamical mass prescription)
- Companion: (cite: Duras17) (WISSH Herschel SED and SFR)
- Companion: (cite: Bischetti17) (WISSH project description)
- Related: WISSH

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 41,
  "rate": 0.532
 },
 "evidence_ok": true
}
```
