# CO (7-6), [C I] 370 μm, and [N II] 205 μm Line Emission of the QSO BRI 1335-0417 at Redshift 4.407

`2018ApJ...864...38L` | The Astrophysical Journal 2018 | first author: Lu, Nanyao | arXiv: 1807.05681 | DOI: 10.3847/1538-4357/aad3c9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What do CO(7-6), [CI] and [NII] line and continuum emission of the z=4.407 QSO BRI 1335-0417 reveal about its star formation, gas properties and merger vs disk nature?  
  > "The ALMA data presented here allow for not only some quantitative characterization of the SF and gas properties, but also further testing the galaxy merger scenario for this system" (1 INTRODUCTION)
- Target **BRI 1335-0417**: coordinates 13h38m03.419s, -04d32m35.06s (J2000, 270 GHz continuum fit)  
  > "BRI 1335-0417, an infrared luminous QSO at $z = 4.407$ (Storrie-Lombardi et al. 1994)" (1 INTRODUCTION); "Gaussian fit position$^b$ (J2000) | (13$^{\rm h}$38$^{\rm m}$03s419, -4$^\circ$32$'$35$''$06)" (Table 1); z/distance z = 4.407; luminosity distance 40,993 Mpc  
  > "BRI 1335-0417, an infrared luminous QSO at $z = 4.407$ (Storrie-Lombardi et al. 1994)" (1 INTRODUCTION); "Gaussian fit position$^b$ (J2000) | (13$^{\rm h}$38$^{\rm m}$03s419, -4$^\circ$32$'$35$''$06)" (Table 1); distance from Storrie-Lombardi et al. 1994 for z; flat cosmology H0=71, OmegaM=0.27  
  > "BRI 1335-0417, an infrared luminous QSO at $z = 4.407$ (Storrie-Lombardi et al. 1994)" (1 INTRODUCTION); "Gaussian fit position$^b$ (J2000) | (13$^{\rm h}$38$^{\rm m}$03s419, -4$^\circ$32$'$35$''$06)" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00388.S
- bands: Band 4 (CO(7-6)/[CI]) and Band 6 ([NII])  
  > "The CO (7$-$6)/[C i] observation of BRI 1334-0417 was carried out in the ALMA Band 4 in the time division mode (TDM)" (2.1 Observations and Data Reduction); "The separate ALMA band-6 [N ii] observation was conducted in TDM in one session on January 4, 2016" (2.1 Observations and Data Reduction)
- frequencies and spectral setup: 4 SPWs of 1875 MHz, 128 channels of 15.625 MHz; one SPW on the line(s), 3 for continuum; effective resolution 31.25 MHz (63 and 35 km/s)  
  > "Each SPW has 128 channels with a channel width of 15.625 MHz. The effective spectral resolution is 31.25 MHz, equivalent to 63 and 35 km s$^{-1}$" (2.1 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas: 39 (Band 4), 40 (Band 6)  
  > "A total of 40 of the 12-meter antennas were used, with baselines from 15 to 331 meters." (2.1 Observations and Data Reduction)
- configurations: _not stated_
- baselines: 15-460 m (Band 4); 15-331 m (Band 6)  
  > "The observation utilized 39 of the 12-meter antennas with baselines ranging from 15 to 460 meters." (2.1 Observations and Data Reduction)
- angular resolution: 1.2x0.9 arcsec PA 82 (Band 4); 1.1x0.8 arcsec PA 64 (Band 6)  
  > "ALMA beam ($\nu_{\rm obs} \approx$ 270 GHz) | (1.1$''$$\times$0.8$''$, 64$^\circ$)" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: continuum rms ~38 (57) uJy/beam; cube rms 0.29 (0.37) mJy/beam at 100 km/s  
  > "resulting in an r.m.s. noise of $\sim$0.29 (0.37) mJy beam$^{-1}$ for the CO (7$-$6)/[C i] ([N ii]) data." (2.1 Observations and Data Reduction)
- time on source: 607 s (Band 4); 303 s (Band 6)  
  > "The effective total on-target integration is 607 seconds." (2.1 Observations and Data Reduction)
- observing dates: March 4 and 19, 2016 (Band 4); January 4, 2016 (Band 6)  
  > "two equal-duration runs on March 4 and 19, 2016, respectively" (2.1 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=7-6 (806.652 GHz)
- Line: [CI] 3P2-3P1 (809.342 GHz)
- Line: [NII] 205 um (1461.134 GHz)
- External data: CO(2-1) flux 0.62 Jy km/s from VLA D-array  
  > "The total CO (2$-$1) flux from a VLA D-array observation is 0.62 ($\pm 0.03$) Jy  km s$^{-1}$ (Jones et al. 2016)." (3.1 CO (7-6) Emission) [from Jones et al. 2016]
- External data: CO(5-4) line flux and width 420+-60 km/s  
  > "CO (5$-$4) line width of 420 $\pm$ 60 km s$^{-1}$ given in Guilloteau et al. (1997)" (3.1 CO (7-6) Emission) [from Guilloteau et al. (1997)]
- External data: [CII] flux used for L[CII]  
  > "Based on the [C ii] flux in Wagg et al. (2010)." (Table 1) [from Wagg et al. (2010)]
- External data: Published continuum fluxes at other wavelengths for SED  
  > "are shown in Fig. 5, along with other published fluxes at various wavelengths." (3.4 Line Luminosity Ratios and FIR Dust Emission) [from not stated]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3  
  > "The data reduction was carried out with the Common Astronomy Software Applications (CASA) 4.5.3" (2.1 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, J1116+0829, J1332-0509, J1337-1257 (Band 4); J1337-1257 and J1332-0509 (Band 6)  
  > "were based on Ganymede, J1116+0829, J1332-0509 and J1337-1257 in the CO (7$-$6)/[C i] observation and on J1337-1257 and J1332-0509 in the [N ii] observation." (2.1 Observations and Data Reduction)
- flux scale uncertainty: ~10% absolute calibration  
  > "ALMA flux uncertainties cited do not include the absolute calibration uncertainty likely at $\sim$10%." (Table 1)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0  
  > "the final images were cleaned using the Briggs weighting with the parameter “robust” = 0" (2.1 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub, order 1  
  > "the continuum was removed using the CASA function “uvcontsub” of order $= 1$." (2.1 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel width reduced to 100 km/s  
  > "We further reduced the channel width of the final spectral cube to 100 km s$^{-1}$" (2.1 Observations and Data Reduction)
- final beam: 1.2x0.9 arcsec PA 82 (1.1x0.8, PA 64)  
  > "resulting in a synthesized beam of full width at half maximum (FWHM) of 1.2$''$$\times$0.9$''$ (1.1$''$$\times$0.8$''$)" (2.1 Observations and Data Reduction)
- final rms: continuum ~38 (57) uJy/beam  
  > "The r.m.s. noise in the final continuum image is $\sim$38 (57) $\mu$Jy beam$^{-1}$" (2.1 Observations and Data Reduction)

### Inherited from earlier work

- SFR from L_CO(7-6) and d_SF/Sigma_SFR prescription  
  > "Following Lu et al. (2015), the SFR inferred from $L_{\rm CO(7-6)}$ is 5.1 $\times 10^3$ $M_{\odot}\,$yr$^{-1}$" (3.5 Star Formation and Gas Properties) [from Lu et al. (2015)]
- Molecular gas mass from 850um flux  
  > "Following Scoville et al. (2016), we also derived $M_{\rm gas} \approx  5 \times 10^{11}\,M_{\odot}$" (3.5 Star Formation and Gas Properties) [from Scoville et al. (2016)]
- Gas mass from [CI] luminosity via eq. (11)  
  > "Using their eq. (11), we derived $M_{\rm gas} \approx 4.4 \times 10^{11}\,M_{\odot}$." (3.2 [C I] 370 um Emission) [from Jiao et al. (2017)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub
- Clean threshold, masks, cell and image size
- Whether archive pipeline products or manual calibration were used
- Continuum SED fit details and the full list of literature fluxes
- Exact frequency ranges for core/wing [NII] moment images
- Gray-body fit method (fitting algorithm, optical depth treatment)

## Analysis recipe

1. **Image continuum and lines**: CASA cleaning with Briggs weighting, uvcontsub, 100 km/s channels  
  > "the final images were cleaned using the Briggs weighting with the parameter “robust” = 0" (2.1 Observations and Data Reduction)
   - software: CASA
   - parameter: robust = 0; uvcontsub order 1  
  > "the continuum was removed using the CASA function “uvcontsub” of order $= 1$." (2.1 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure sizes, positions and moment maps**: 2D Gaussian fits to images; deconvolvefrombeam; moment 1/2 with immoments above 2.5 sigma  
  > "using the CASA function “immoments” on all the channel data points above 2.5$\sigma$" (2.2 Results)
   - software: CASA
   - fitting: Uncertainties following Condon (1997)  
  > "were estimated following the prescription in Condon (1997) for correlated noise cases." (Table 1)
   - validation: Moment patch checked against S/N cutoff 3.5  
  > "this patch completely disappears if the spaxel S/N cutoff is raised to S/N $>3.5$." (2.2 Results)
3. **Extract and fit spectra**: Elliptical aperture spectra (size index n=0.5-3.0); Gaussian and 3-Gaussian fits for [NII]  
  > "Fig. 3 shows the extracted 1d spectra using an elliptical aperture of the size index $n = 2.5$ (upper panels) or $n = 1.0$ (lower panels)" (2.2 Results)
   - fitting: Gaussian fits; errors following Lenz & Ayres (1992)  
  > "The uncertainties for the parameters from a Gaussian fit to a spectrum were estimated following the formulae in Lenz & Ayres (1992)." (Table 1)
   - validation: Reduced chi-squared 0.64 (3-Gaussian) vs 1.29 (single)  
  > "the reduced Chi-squared values are 0.64 and 1.29 for the 3-Gaussian and single-Gaussian fits in Fig. 3c, respectively" (3.3 [N II] 205 um Emission)
4. **Dust SED and C(60/100) from line ratios**: Gray-body fit to continuum with fixed beta=1.8; C(60/100) from line luminosity ratios  
  > "best gray-body spectral energy distribution (SED) fit to all the data points with a fixed dust emissivity power law index $\beta = 1.8$" (3.4 Line Luminosity Ratios and FIR Dust Emission)
   - assumption: beta = 1.8  
  > "with a fixed dust emissivity power law index $\beta = 1.8$ (Planck Collaboration et al. 2011)" (3.4 Line Luminosity Ratios and FIR Dust Emission)
   - fitting: _not stated_
   - validation: T_dust from SED agrees with line-ratio average of 41 +-2 K  
  > "This temperature estimate is in good agreement with that from the direct SED fit." (3.4 Line Luminosity Ratios and FIR Dust Emission)
5. **Derive SFR, SF size and gas mass**: SFR from L_CO(7-6); Sigma_SFR from C(60/100) and 70/160; d_SF from Sigma_SFR; M_gas from 850um flux and [CI]  
  > "The face-on FWHM diameter, $d_{\rm SF}$, of the SF region is estimated to be 1.7$^{+1.7}_{-0.8}$ kpc" (3.5 Star Formation and Gas Properties)
   - assumption: Chabrier IMF; Sigma_SFR = (1/2 SFR)/(1/4 pi d^2)  
  > "using the initial mass function (IMF) of Chabrier (2003)" (3.5 Star Formation and Gas Properties)
   - fitting: _not stated_
   - validation: [CI]-based and 850um-based gas masses agree  
  > "This is in good agreement with the molecular gas mass inferred from our [C i] flux above." (3.5 Star Formation and Gas Properties)

## Software

- **CASA** 4.5.3: data reduction, imaging, uvcontsub, immoments, deconvolvefrombeam  
  > "The data reduction was carried out with the Common Astronomy Software Applications (CASA) 4.5.3" (2.1 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(7-6) flux | 3.08 | 0.11 | Jy km/s | 3 | Flux (Jy km s$^{-1}$) / 3.08 ($\pm 0.11$) |
| [CI] flux | 1.04 | 0.09 | Jy km/s | 3 | Flux (Jy km s$^{-1}$) / 1.04 ($\pm 0.09$) |
| [NII] total flux | 1.95 | 0.23 | Jy km/s | 3 | Flux (Jy km s$^{-1}$) / 1.95 ($\pm 0.23$) |
| Continuum flux 270 GHz | 9.03 | 0.11 | mJy | 2 | $S_{\nu}$ (270 GHz) (mJy) / 9.03 ($\pm 0.11$) |
| Continuum flux 149 GHz | 1.17 | 0.07 | mJy | 2 | $S_{\nu}$ (149 GHz) (mJy) / 1.17 ($\pm 0.07$) |
| T_dust from SED | 41.5 | not stated | K | 4 | This SED fit gives $T_{\rm dust} = 41.5\,$K or $C(60/100) \approx 1.1$. |
| [NII] deconvolved size | 1.3 (9 kpc) | 0.3 arcsec (2 kpc) | arcsec | 2 | $d_{\rm deconv}$ = 1.3$''$$\pm$0.3$''$ (or 9$\pm$2 kpc) |
| CO(7-6) deconvolved size | 0.6 (4.1 kpc) | 0.1 arcsec | arcsec | 2 | beam-deconvolved diameter of $d_{\rm deconv} \approx 0.6$$''$$\pm$0.1$''$ (equivalent to 4.1$\pm$0.7 kpc) |
| SFR from L_CO(7-6) | 5.1e3 | 1.5e3 | Msun/yr | 5 | The $L_{\rm CO(7-6)}$-inferred SF rate is $5.1\,(\pm 1.5) \times 10^3\,M_{\odot}$ yr$^{-1}$. |
| SF region diameter | 1.7 | +1.7/-0.8 | kpc | 5 | effective star-forming region of 1.7$^{+1.7}_{-0.8}$ kpc in diameter |
| Molecular gas mass (850um) | 5e11 | factor ~2 | Msun | 5 | The formal uncertainty for this $M_{\rm gas}$ estimate is about a factor of 2. |
| L_FIR | 1.9e13 | not stated | Lsun | 4 | is 1.9 $\times 10^{13}\,L_{\odot}$ from the SED fit in Fig. 5 |
| log L_CO(7-6)/L_FIR | -4.46 | not stated | dimensionless | 4 | resulting in $\log L_{\rm CO(7-6)}/L_{\rm FIR} \approx -4.46$ |

## Qualitative findings

- CO(7-6) is more compact with higher velocity dispersion than [CI] and [NII], favoring merger-triggered SF over a rotating disk  
  > "a picture favoring a merger-triggered star formation (SF) scenario over an orderly rotating SF disk" (abstract)
- Possible QSO-driven CO(7-6) outflow up to 500-600 km/s  
  > "possible QSO-driven gas outflow that reaches a maximum line-of-sight velocity of 500 to 600 km s$^{-1}$" (abstract)

## Claim tuples

- H: Is the SF merger-driven rather than an orderly rotating disk? | E: Compared sizes and velocity dispersion of CO(7-6), [CI], [NII] | R: CO(7-6) peak dispersion ~180 km/s vs ~120 ([CI]) and ~80 ([NII]); [NII] twice as extended | F: The lines arise from different regions, favoring a merger | **supported**
- H: Is there a QSO-driven outflow in CO(7-6)? | E: Channel maps and spectra of CO(7-6) | R: Blue/red wing emission at S/N ~3-4 | F: Possible bipolar outflow, needs confirmation | **partially**
- H: Does L_CO(7-6) trace SFR and T_dust agree with line ratios? | E: Gray-body SED fit and line-ratio C(60/100) | R: T_dust 41.5 K vs 41+-2 K; log L_CO/L_FIR=-4.46 | F: SF-dominated, consistent with local LIRGs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: 2-Gaussian fits to [NII] gave chi2 ~1.34, worse than single Gaussian  
  > "The resulting reduced Chi-squared values of $\sim$1.34 are slightly larger than that for the single Gaussian fit." (3.3 [N II] 205 um Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Wing features and tidal tail picture detected only at S/N 2-3  
  > "the tidal tail picture remains as a speculation at this point" (3.3 [N II] 205 um Emission)
- Caveat (inferred, ours): Low resolution (~1.1 arcsec) limits size and merger conclusions
- Caveat (inferred, ours): Outflow and wings only ~3 sigma
- Caveat (inferred, ours): SED fit uses few points and fixed beta

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Clean parameters, masks, image sizes
- Missing: Literature continuum fluxes list for SED
- Missing: Line-free channels
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Short observations with stated CASA version and robust, but many imaging and SED details missing.
- Rediscovery candidate: no, Public data likely but recipe incomplete and several results depend on external literature calibrations.

## Links

- Method: Lu et al. (2015) (CO(7-6) SFR and C(60/100) line ratio methods)
- Method: Lu et al. (2017a) (CO SLED and [CI]/CO(7-6) calibration)
- Companion: Riechers et al. (2008) (High-resolution VLA CO(2-1) map of N and S sources)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 46,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
