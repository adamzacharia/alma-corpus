# The IBISCO survey. I. Multiphase discs and winds in the Seyfert galaxy Markarian 509

`2021A&A...655A..25Z` | Astronomy and Astrophysics 2021 | first author: Zanchettin, M. V. | arXiv: 2107.06756 | DOI: 10.1051/0004-6361/202039773

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the molecular gas content, disc kinematics, stability and molecular winds in the Seyfert 1.5 galaxy Mrk 509, and are the winds AGN- or SN-driven?  
  > "In this paper, we exploit ALMA data of Mrk509 to trace the distribution and kinematics of cold molecular gas and to look for evidences of molecular winds." (Introduction)
- Target **Mrk 509**: coordinates _not stated_; z/distance D ~ 142.9 Mpc (0.689 kpc/arcsec)  
  > "Mrk 509 is a Seyfert 1.5 galaxy located at D $\sim$ 142.9 Mpc (cite: hucra) implying a physical scale of 0.689 kpc/arcsec" (Introduction); distance from Huchra et al. 1993 (cite: hucra)  
  > "Mrk 509 is a Seyfert 1.5 galaxy located at D $\sim$ 142.9 Mpc (cite: hucra) implying a physical scale of 0.689 kpc/arcsec" (Introduction)

## Data provenance

- ALMA projects: 2017.1.01439.S
- bands: Band 6, 221.8-223.7 GHz  
  > "for a total integration time of 75 minutes in the frequency range 221.8-223.7 GHz (band 6)" (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 12 m array, C43-5, 44 antennas  
  > "The obervations were conducted with the 12 m array in the C43-5 configuration with 44 antennas" (2 Observations and data reduction)
- baselines: 14.6 m to 1397.9 m  
  > "minimum baseline of 14.6 m and maximum baseline of 1397.9 m" (2 Observations and data reduction)
- angular resolution: about 0.4 arcsec  
  > "This provided us an angular resolution of about 0.4 arcsec" (2 Observations and data reduction)
- max recoverable scale: ~4.6 arcsec  
  > "a largest angular scale of $\sim$ 4.6 arcsec" (2 Observations and data reduction)
- sensitivity: continuum rms 0.014 mJy/beam; cube rms 0.38 mJy/beam per 10.6 km/s channel  
  > "a r.m.s. noise of 0.38 mJy/beam for a channel width of 10.6 km/s" (2 Observations and data reduction)
- time on source: 75 minutes total integration  
  > "for a total integration time of 75 minutes" (2 Observations and data reduction)
- observing dates: September 2018 (Cycle 5)  
  > "during cycle 5 on September 2018" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **HST (FQ508N)**: [OIII] image compared with CO moment 0 map  
  > "We compare our CO(2-1) moment 0 map with the HST image in FQ508N filter" (6 Discussion)
- Other facility **GALEX**: UV imaging giving disc inclination 44±10 deg  
  > "The inclination from the minor/major axis ratio from UV imaging (GALEX archive) is $44\pm10$ deg" (4 Molecular Discs)
- External data: Stellar mass and SFR (5.1±0.5 Msun/yr) from SED decomposition  
  > "The rest-frame SED is fitted with a three components model using the approach described in (cite: gruppioni2016)." (Stellar Mass) [from Gruppioni et al. 2016 (cite: gruppioni2016)]
- External data: Bolometric luminosity L_Bol=10^44.99 erg/s  
  > "a bolometric luminosity of $L_{Bol}=  10^{44.99}\mathrm{\,erg\,s^{-1}}$ (cite: duras2020)" (Introduction) [from Duras et al. 2020 (cite: duras2020)]
- External data: Black hole mass 10^8.04 Msun  
  > "a black hole with mass $M_{bh} = 10^{8.04}~\mathrm{M_{\odot}}$ (cite: bentz)" (Introduction) [from Bentz et al. 2009 (cite: bentz)]
- External data: Ionised [OIII] wind properties (290 km/s, 5 Msun/yr)  
  > "with velocity 290 km/s and mass outflow rate $\dot{M}_{of}$ = 5 $\mathrm{M_{\odot}/yr}$" (Introduction) [from Liu et al. 2015 (cite: liu)]

## Processing

### Calibration

- pipeline or manual: pipeline mode with default observatory calibrators  
  > "We calibrated the visibilities in the pipeline mode and using the default calibrators provided by the observatory" (2 Observations and data reduction)
- casa version: CASA 5.4.1  
  > "We used CASA 5.4.1 software (cite: mcmullin)" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2148+0657 and J2000-1748 (bandpass/flux); J2025-0735 phase  
  > "bandpass and flux calibrators J2148+0657 and J2000-1748, J2025-0735 phase/amplitude calibrator" (2 Observations and data reduction)
- flux scale uncertainty: better than 10%  
  > "The absolute flux accuracy is better than 10$\%$." (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We imaged CO(2-1) and continuum using the `tclean` task" (2 Observations and data reduction)
- deconvolver: hogbom, threshold 3x rms  
  > "by using the `hogbom` cleaning algorithm with a detection threshold of 3 times the r.m.s. noise" (2 Observations and data reduction)
- weighting robust: natural  
  > "by adopting a natural weighting scheme" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "a pixel size of 0.05 arcsec" (2 Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first-order polynomial (zeroth order checked)  
  > "with the `uvcontsub` task, adopting a first order polynomial. We verified that using a zero order polynomial did not affect the results." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.396x0.343 arcsec PA 51 deg; cube 0.412x0.353 arcsec PA 48 deg  
  > "a clean data-cube with a beam size of 0.412 $\times$ 0.353 $\mathrm{arcsec^2}$ at a PA = 48 deg" (2 Observations and data reduction)
- final rms: continuum 0.014 mJy/beam; cube 0.38 mJy/beam  
  > "The resulting r.m.s. noise in the clean continuum map is 0.014 mJy/beam in the aggregated bandwidth." (2 Observations and data reduction)

### Inherited from earlier work

- alpha_CO conversion function based on stellar mass  
  > "we use the stellar mass $M_*$ and the conversion function by (cite: accurso)" (3 Results) [from (cite: accurso)]
- SED decomposition method for M* and SFR  
  > "We defer to (cite: gruppioni2016) for further details about the SED decomposition method." (Stellar Mass) [from (cite: gruppioni2016)]
- Outflow rate relation assuming spherical sector  
  > "The wind mass outflow rate is computed using the relation from (cite: fiore2017), assuming a spherical sector" (5 Molecular Wind) [from (cite: fiore2017)]
- v98 definition for wind velocity  
  > "the velocity enclosing 98$\%$ of the cumulative velocity distribution of the outflowing gas (cite: bischetti2019)" (5 Molecular Wind) [from (cite: bischetti2019)]

### Not stated but needed to reproduce (our reading)

- Spectral windows, channel widths and line-free channel ranges used for continuum
- Regions/masks used to extract spectra A and B and how v98 and S_CO were measured
- 3DBarolo parameters (rings, widths, mask, normalisation, fitting settings)
- Boundaries of the clean mask
- Conversion of CO(2-1) to CO(1-0) (r21) used for alpha_CO
- Catalog photometry for SED fit
- How uncertainties on M_dyn were propagated
- Exact coordinates of the target

## Analysis recipe

1. **Calibrate and image continuum and CO(2-1)**: Pipeline calibration, uvcontsub, tclean natural weighting, hogbom  
  > "We imaged CO(2-1) and continuum using the `tclean` task by adopting a natural weighting scheme" (2 Observations and data reduction)
   - software: CASA 5.4.1
   - parameter: pixel 0.05 arcsec, 10.6 km/s channels  
  > "a pixel size of 0.05 arcsec and a spectral resolution of 10.6 km/s" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: zero-order continuum fit gave same result  
  > "We verified that using a zero order polynomial did not affect the results." (2 Observations and data reduction)
2. **Measure continuum flux and CO line flux, luminosity and gas mass**: 2D image-plane fit for continuum; three-Gaussian fit of spectrum; L'CO from Solomon relation; M_H2 using alpha_CO from Accurso  
  > "We fitted the emission line with a combination of three Gaussian profiles" (3 Results)
   - software: CASA
   - assumption: alpha_CO = 3.3 Msun (K km/s pc^2)^-1 from stellar mass M*=1.2e11 Msun  
  > "We derive a total stellar mass of $M_* = 1.2 \times 10^{11} \, \mathrm{M_{\odot}}$, and a $\alpha_{CO}\,= 3.3" (3 Results)
   - fitting: three Gaussian components; details not stated  
  > "We fitted the emission line with a combination of three Gaussian profiles whose parameters are reported in the Table" (Results)
   - validation: _not stated_
3. **Model disc kinematics**: 3D tilted-ring fit; first run free inclination and PA, second run inclination fixed to 44 deg; residual cube, PV diagrams  
  > "We fitted a 3D tilted-ring model to the emission line data-cube to provide a first order dynamical model of the CO-emitting gaseous disc." (4 Molecular Discs)
   - software: 3DBarolo
   - parameter: kinematic centre fixed to continuum position; PV slit 0.45 arcsec wide  
  > "We fixed the kinematic center to the 1.2 mm continuum position" (4 Molecular Discs)
   - assumption: inclination 44 deg from GALEX UV imaging  
  > "we fix it to 44 deg in the model" (4 Molecular Discs)
   - fitting: 3DBarolo tilted ring  
  > "We fitted a 3D tilted-ring model to the emission line data-cube to provide a first order dynamical model of the CO-emitting gaseous disc." (Molecular Discs)
   - validation: second run residuals ~2% vs ~5% in first run in moment 0  
  > "The second run, with fixed inclination, produces residuals of amplitude about 2%, therefore we adopt the latter as best-fit disc model." (4 Molecular Discs)
4. **Dynamical mass and Toomre Q map**: M_dyn = r v_rot^2/2G; Q_gas = a v_rot sigma/(pi R G Sigma_gas) pixel by pixel from moments 0 and 2  
  > "The velocity dispersion and $\Sigma_{gas}$ are calculated pixel by pixel from the moment 2 and 0 maps, respectively; the radius $R$ is deprojected." (6 Discussion)
   - parameter: a=1 up to R=1.1 arcsec, a=1.4 beyond  
  > "We adopt $a$=1 up to $R$=1.1 arcsec, where the rotation curve is steep, and $a$=1.4 at larger radii." (6 Discussion)
   - fitting: _not stated_
   - validation: central 0.3 arcsec excluded for beam smearing  
  > "excluding the central region of 0.3 arcsec radius, to avoid the beam-smearing effect" (6 Discussion)
5. **Molecular outflow properties**: Residual cube spectra in regions A and B; Mdot=3 M v98/R; optically thin/thick alpha_CO; escape velocity; momentum load  
  > "$$\dot{M}_{of} = 3 \frac{M_{of}\,v_{of}}{R_{of}}$$" (5 Molecular Wind)
   - software: 3DBarolo
   - assumption: alpha_CO = 0.3 (optically thin) and 0.8 (thick) Msun (K km/s pc^2)^-1  
  > "adopting a conversion factor $\alpha_{CO}\,= 0.3\mathrm{\,M_{\odot} (K\,km/s\,pc^{2})^{-1}}$ for the optically thin" (5 Molecular Wind)
   - fitting: _not stated_
   - validation: compare with momentum- and energy-conserving expectations and SN energetics  
  > "The molecular wind A and the ionised wind are consistent with a momentum conserving driving (black dashed line), and are well below the expectation for energy conserving winds." (Discussion)
6. **Model nuclear warped disc**: Nuclear disc fit with inclination 66 deg, PA 330 deg fixed; v_rot and dispersion free, first guesses 80 and 50 km/s  
  > "We allow two parameters to vary: the rotational velocity $v_{rot}$ and the velocity dispersion $\sigma_{gas}$ with first guess values set to 80 and 50 km/s" (Inner disc model)
   - software: 3DBarolo
   - fitting: _not stated_
   - validation: compare model PV with data  
  > "The right panel of Fig.[5](#residuo0) shows the position velocity diagrams cut along the kinematic major axis (330 deg); where the grey-scale and blue contours refer to the data and the red contours to the model." (Inner disc model)

## Software

- **CASA** 5.4.1: calibration, uvcontsub, tclean imaging, 2D continuum fit  
  > "We used CASA 5.4.1 software (cite: mcmullin) to produce a set of calibrated visibilities and to generate clean data-cubes." (2 Observations and data reduction)
- **3DBarolo** : 3D tilted-ring dynamical modelling  
  > "we build a dynamical model of the system using $^{3D}BAROLO$ (cite: diteodoro)" (4 Molecular Discs)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.2 mm continuum flux density | 2.17 | 0.04 | mJy | 2 | We measure a continuum flux density $S_{1.2 mm} = 2.17 \pm 0.04$ mJy |
| CO(2-1) integrated flux | 36.7 | 0.8 | Jy km/s | 2 | $S_{CO} = 36.7 \pm \mathrm{0.8 \, Jy\, km/s}$ |
| L'CO(2-1) | 5.0e8 | 0.1e8 | K km/s pc^2 | 2 | $L'_{CO(2-1)}= (5.0 \pm 0.1)\times 10^8$ |
| Molecular gas mass | 1.65e9 | 0.04e9 | Msun | 2 | we derive a molecular gas mass $M_{H_2} = (1.65\, \pm \, 0.04)\times 10^9\, \mathrm{M_{\odot}}$ |
| Disc PA | 248 | 5 | deg | 3 | The disc model has a position angle PA = $248 \pm 5$ deg |
| Dynamical mass | 2.0e10 | 1.1e10 | Msun | 4 | $M_{dyn}$ = (2.0 $\pm$ 1.1) $\times$ $10^{10}$ $\mathrm{M_{\odot}}$ within a $\sim$2.6 kpc radius |
| Molecular gas fraction | ~5 | not stated | % | 4 | is then $\mu \sim 5 \%$ |
| Toomre Q_gas range | 0.5-10 | not stated | dimensionless | 4 | We find values that range from $Q_{gas}\approx$ 0.5 up to 10 |
| Outflow rate region A | 5.5-14.7 | not stated | Msun/yr | 5 | $\dot{M}_{of}\,=\,5.5-14.7 \mathrm{\,M_{\odot}/yr}$ |
| Outflow rate region B | 0.86-2.30 | not stated | Msun/yr | 5 | $\dot{M}_{of}\,=\,0.86-2.30 \mathrm{\,M_{\odot}/yr}$ |
| Total molecular outflow rate | 6.4-17.0 | not stated | Msun/yr | 5 | whose total molecular outflow rate is in the range 6.4 - 17.0 $\mathrm{M_\odot/yr}$ |
| Momentum load A | 0.5 | 0.2 | dimensionless | 5 | A / 250 / 0.3 / 0.51$\pm 0.05$ / 2.1-5.6 / 5.5-14.7 / 11-30 / 0.5 $\pm$ 0.2 / 140 |
| Star formation efficiency | 6.2e-9 | not stated | 1/yr | 4 | $SFE = SFR/M_{H_2} =  6.2 \times 10^{-9} \rm yr^{-1}$ |

## Qualitative findings

- Molecular wind A overlaps the ionised wind with similar velocity, suggesting a cooling sequence in a multiphase AGN-driven wind.  
  > "The spatial overlap of the inner molecular wind with the ionised wind, and their similar velocity suggest a cooling sequence within a multiphase wind driven by the AGN." (abstract)

## Claim tuples

- H: Does Mrk 509 host molecular winds and are they AGN-driven? | E: 3DBarolo disc model residuals, spectra at A and B, outflow energetics | R: Total outflow rate 6.4-17.0 Msun/yr; momentum load 0.06-0.5 | F: Wind A is a momentum-conserving AGN-driven wind co-spatial with the ionised wind | **supported**
- H: Is outer wind B driven by the starburst ring? | E: Compare energetics with SN-driven wind estimate | R: Mdot 3-8 Msun/yr at R=0.4 kpc; E_SN 3.5e41 erg/s | F: B consistent with SN-driven wind | **partially**
- H: Is the molecular disc gravitationally stable? | E: Toomre Q map | R: Q_gas 0.5-10 | F: Marginally unstable across starburst ring, stable at nucleus and lopsided ring | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Wind B related to the merger tidal tail rejected based on opposite velocity (-100 vs 200 km/s)  
  > "Therefore it is unlikely that the molecular gas in A and B is related to the tidal tail." (6 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Nuclear region barely resolved; higher resolution needed  
  > "We note that observations with higher angular resolution would be required to better assess the kinematic properties in this region." (4 Molecular Discs)
- Limitation (authors): Cannot discriminate consecutive episodes from a decelerating wind  
  > "Current data cannot discriminate between these two scenarios." (5 Molecular Wind)
- Caveat (inferred, ours): Optical depth and alpha_CO for the wind are unconstrained, spanning a factor ~2.7
- Caveat (inferred, ours): Single-object outflow identification relies on residuals from a simple model with marginal resolution
- Caveat (inferred, ours): Beam smearing may affect the dispersion and Q values

## Reproducibility

- Data public (paper): Archive project cited; public status not explicitly stated  
  > "This paper makes use of the ALMA data from project: ADS/JAO.ALMA$\#$2017.1.01439.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: 3DBarolo configuration
- Missing: Region definitions for A and B
- Missing: SED photometry
- Data volume (inferred): ~20-50 GB raw, single 12m-array execution block
- Score (inferred): 3/5, Data and main imaging steps stated and public via archive, but 3DBarolo settings and region extractions are missing.
- Rediscovery candidate: yes, Single public dataset, mostly stated imaging recipe, numeric results (gas mass, flux, outflow rates).

## Links

- Method: Di Teodoro & Fraternali 2015 (cite: diteodoro) (3DBarolo)
- Method: Fiore et al. 2017 (cite: fiore2017) (outflow rate relation)
- Companion: Gruppioni et al. 2016 (cite: gruppioni2016) (SED decomposition, SFR)
- Related: IBISCO
- Related: INTEGRAL IBIS catalog
- Related: BASS

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
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
  "facts": 83,
  "stated": 58,
  "rate": 0.699
 },
 "evidence_ok": true
}
```
