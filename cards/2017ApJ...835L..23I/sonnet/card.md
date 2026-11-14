# Evidence for a Dusty Dark Dwarf Galaxy in the Quadruple Lens MG 0414+0534

`2017ApJ...835L..23I` | The Astrophysical Journal Letters 2017 | first author: Inoue, Kaiki Taro | arXiv: 1701.05283 | DOI: 10.3847/2041-8213/835/2/L23

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, cosmology
- Question: Is the faint submillimeter object near the quadruple lens MG 0414+0534 a dusty dark dwarf galaxy that explains the flux-ratio anomaly and the reddening?  
  > "An anomaly in the flux ratio of the lensed images observed in Band 7 and the mid-infrared (MIR) band and the reddening of the QSO light color can be simultaneously explained" (abstract)
- Target **MG 0414+0534**: coordinates 04h14m37.7686s +05d34m42.352s (J2000, phase center)  
  > "The phase center was $\alpha=$04$^\textrm{h}$14$^\textrm{m}$37$^\textrm{s}$.7686, $\delta=$+05$^\circ$34$'$42.352$''$ (J2000)." (Observations and data reduction); "The source of MG 0414+0534, at a redshift of $z_{\textrm{S}}=2.639$, is lensed by a foreground elliptical galaxy G (the primary lens) at $z_{\textrm{L}}=0.9584$" (3.2 Flux-Ratio Anomaly); z/distance z_S=2.639; lens z_L=0.9584  
  > "The phase center was $\alpha=$04$^\textrm{h}$14$^\textrm{m}$37$^\textrm{s}$.7686, $\delta=$+05$^\circ$34$'$42.352$''$ (J2000)." (Observations and data reduction); "The source of MG 0414+0534, at a redshift of $z_{\textrm{S}}=2.639$, is lensed by a foreground elliptical galaxy G (the primary lens) at $z_{\textrm{L}}=0.9584$" (3.2 Flux-Ratio Anomaly); distance from cite: hewitt1992; lawrence1995; tonry1999  
  > "The phase center was $\alpha=$04$^\textrm{h}$14$^\textrm{m}$37$^\textrm{s}$.7686, $\delta=$+05$^\circ$34$'$42.352$''$ (J2000)." (Observations and data reduction); "The source of MG 0414+0534, at a redshift of $z_{\textrm{S}}=2.639$, is lensed by a foreground elliptical galaxy G (the primary lens) at $z_{\textrm{L}}=0.9584$" (3.2 Flux-Ratio Anomaly)

## Data provenance

- ALMA projects: 2013.1.01110.S
- bands: Band 7  
  > "The observations of MG 0414+0534 were carried out with ALMA at Band 7 on 2015 June 13 and August 14" (Observations and data reduction)
- frequencies and spectral setup: four spectral windows at 335.0, 337.0, 347.0, 349.0 GHz, 2 GHz bandwidth, 15.625 MHz channel width  
  > "four spectral windows centered at 335.0 GHz, 337.0 GHz, 347.0 GHz and 349.0 GHz with a bandwidth 2 GHz and a frequency width of 15.625 MHz for each window" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 35 antennas (June), 42 antennas (August)  
  > "The number of antennas used in the observation in June was 35 and that in August was 42." (Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.278x0.243 arcsec (natural); 0.135x0.111 arcsec (robust -1)  
  > "the full widths at half maximum of the elliptical gaussian fitted to the dirty beam are ($0.278\ensuremath{''}\times 0.243\ensuremath{''}$) and ($0.135\ensuremath{''}\times 0.111\ensuremath{''}$)" (Observations and data reduction)
- max recoverable scale: ~3.3 arcsec  
  > "the recoverable largest angular size was $\sim 3.3$ arcsec" (Observations and data reduction)
- sensitivity: 1 sigma 49 uJy/beam (natural), 140 uJy/beam (robust -1)  
  > "The 1$\,\sigma$ noises in the flux density per pixel are 49 $\mu$Jy per beam and 140 $\mu$Jy per beam" (Observations and data reduction)
- time on source: 104.63 and 52.28 minutes  
  > "The total on-source integrating times were 104.63 minutes and 52.28 minutes" (Observations and data reduction)
- observing dates: 2015 June 13 and August 14 (Cycle 2)  
  > "on 2015 June 13 and August 14 as part of Cycle 2" (Observations and data reduction)
- pi or archival as stated: PI K.T. Inoue (own Cycle 2 program)  
  > "Project ID: 2013.1.01110.S, PI: K.T. Inoue" (Observations and data reduction)
- Other facility **HST (CASTLES archive)**: image positions, lens galaxy centroids, optical/NIR fluxes  
  > "We used the measured HST WFPC/WFPC2 positions of lensed images and centroids of lensing galaxies, G and X in the CASTLES data archive" (3.2 Flux-Ratio Anomaly)
- External data: MIR flux ratios A2/A1, B/A1, C/A1 = 0.919, 0.347, 0.139  
  > "$(\textrm{A2}/\textrm{A1}, \textrm{B}/\textrm{A1}, \textrm{C}/\textrm{A1}) =(0.919\pm 0.021,0.347\pm 0.013, 0.139\pm 0.014)$" (3.1 Dust continuum emission) [from (cite: minezaki2009; macleod2013)]
- External data: HST positions and optical/NIR fluxes of images and lens galaxies  
  > "The flux data were taken from the CASTLES data archive" (3.3 Differential Extinction) [from (cite: falco1997)]
- External data: X-ray differential hydrogen column density (3.3±1.0)e21 cm^-2  
  > "$\Delta N_{\textrm{H}_\textrm{I}}=(3.3 \pm 1.0)\times 10^{21}\,\textrm{cm}^{-2}$, which was measured with the X-ray spectra" (4 Discussions) [from (cite: dai2006)]

## Processing

### Calibration

- pipeline or manual: calibration done with CASA; details not given  
  > "The calibration and imaging of the data were carried out using the Common Astronomy Software Application package" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multi-scale CLEAN  
  > "We used $\textit{multi-scale}$ imaging (cite: cornwell2008)" (Observations and data reduction)
- weighting robust: natural weighting for imaging; robust = -1 for modeling  
  > "The continuum images produced with a natural or a robust ($\textit{robust}=-1$) weighting of the visibilities were used for imaging and modeling, respectively." (Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.02 arcsec (natural); 0.01 arcsec (robust -1)  
  > "(pixel size is 0.02 arcsec)" (Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0,6,12,24,48 (natural); 0,6,12,24 (robust -1)  
  > "with scales of 0, 6, 12, 24 and 48 for the natural weighting (pixel size is 0.02 arcsec) and 0, 6, 12 and 24 for the robust ($\textit{robust}=-1$) weighting" (Observations and data reduction)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not applied  
  > "The images have not been corrected for the primary beam attenuation because the source is small and located at the center of the primary beam." (Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 49 uJy/beam (natural), 140 uJy/beam (robust -1)  
  > "are 49 $\mu$Jy per beam and 140 $\mu$Jy per beam" (Observations and data reduction)

### Inherited from earlier work

- Magnification-weighted source model definition for simulation  
  > "using a linear combination of multiple lensed images with a magnification weighting (see (cite: inoue-minezaki2016) for its definition)" (3.2 Flux-Ratio Anomaly) [from (cite: inoue-minezaki2016)]
- Definition of effective Einstein radius b_G  
  > "We took a definition of $b_G$ for which the mass inside $b_G$ coincides with that inside the critical curve (cite: kormann1994)." (Footnote 2) [from (cite: kormann1994)]

### Not stated but needed to reproduce (our reading)

- Line-free/continuum channel selection and flagging
- CASA version used for calibration/imaging
- Clean threshold, mask, iterations
- Lens modeling code and optimizer
- Exact aperture photometry procedure and positions of source-free apertures
- Number of simulated noise realizations and PWV value

## Analysis recipe

1. **Image continuum**: CASA multi-scale imaging with natural and robust=-1 weighting  
  > "We used $\textit{multi-scale}$ imaging (cite: cornwell2008) with scales of 0, 6, 12, 24 and 48 for the natural weighting" (Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure flux ratios and flux of object Y**: Aperture photometry; errors from apertures at source-free locations; gaussian fit to Y  
  > "Note that the errors were estimated using the flux density in apertures of the same size placed at source-free locations." (3.1 Dust continuum emission)
   - parameter: aperture radius 0.26 arcsec for Y; 0.21 arcsec for images  
  > "The flux density of Y inside an aperture radius of $0.26\,\textrm{arcsec}$ centered at the peak is $0.26\,\textrm{mJy}$" (Results, Dust continuum emission)
   - assumption: error correlations negligible  
  > "We assumed that correlations between errors are negligible." (3.1 Dust continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Dust mass from submm flux**: Dust mass using opacity coefficient, beta 1-2, Td 20-50 K, zY 0.5-1  
  > "for an emissivity index $\beta=1-2$ with a dust temperature $T_\textrm{d}=20-50\,\textrm{K}$ and a dust redshift $z_{\textrm{Y}}=0.5-1$" (3.1 Dust continuum emission)
   - assumption: kappa_850/(1+z)=0.077(1+z)^beta m^2/kg (Dunne 2000)  
  > "$\kappa_{850\mu \textrm{m}/(1+z_{\textrm{Y}})} =0.077\,(1+z_{\textrm{Y}})^\beta\textrm{m}^2\textrm{kg}^{-1}$ (cite: dunne2000)" (3.1 Dust continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Lens modeling with G+X and G+X+Y**: SIE+external shear for G, cored SIS for X, SIE for Y; fit positions and MIR flux ratios with chi^2 and weak priors  
  > "Next, we added an SIE for modeling Y." (3.2 Flux-Ratio Anomaly)
   - parameter: priors gamma=0.05±0.05, e_G=0±1, e_Y=0±1; astrometric errors 0.2'' (X), 0.003'' (G), 0.13'' (Y)  
  > "We assumed a weak prior for the amplitude of the external shear $\gamma(=0.05\pm0.05)$ and the ellipticity $e_{\textrm{G}}(=0\pm 1)$." (3.2 Flux-Ratio Anomaly)
   - assumption: z_X = z_L; z_Y varied 0.5-1  
  > "The redshift $z_\textrm{X}$ of X was assumed to be $z_\textrm{X}=z_{\textrm{L}}$" (3.2 Flux-Ratio Anomaly)
   - fitting: chi^2 minimization  
  > "We had $\chi_{\textrm{tot}}^2/\textrm{dof}=29.0/4$ with a best-fit flux ratio $\textrm{A}2/\textrm{A}1=1.005$, which implies that the fit is not satisfactory" (Results, Flux-Ratio Anomaly)
   - validation: chi2/dof compared among models  
  > "We had $\chi_{\textrm{tot}}^2/\textrm{dof}=29.0/4$ with a best-fit flux ratio $\textrm{A}2/\textrm{A}1=1.005$" (3.2 Flux-Ratio Anomaly)
5. **Sidelobe test by simulated observation**: simalma simulation with same configurations and times, lens-model source  
  > "we simulated an ALMA observation using *simalma* command in CASA 4.5.3" (3.2 Flux-Ratio Anomaly)
   - software: CASA simalma
   - fitting: _not stated_
   - validation: no spots found at position of Y in simulation  
  > "However, we were not able to find any spots around the position of Y." (3.2 Flux-Ratio Anomaly)
6. **Differential extinction fit**: Fit SMC bar extinction curves to optical/NIR flux ratios A1/B, A2/B with MIR ratios as intrinsic; obscurer at z=0.5, 1.0  
  > "We adopted the dust extinction curve for the Small Magellanic Cloud (SMC) bar (cite: gordon2003) and assumed the MIR flux ratios as the intrinsic ones." (3.3 Differential Extinction)
   - parameter: systematic errors 0.01-0.04 dex added to give reduced chi2 = 1  
  > "The amount of systematic errors was $0.01$–$0.04$ dex." (3.3 Differential Extinction)
   - fitting: chi^2 fit of extinction curves  
  > "Then we fit extinction curves to the flux ratios of A1$/$B and A2$/$B in different wavelengths to estimate the amount of differential extinction." (Results, Differential Extinction)
   - validation: compared with Falco 1999  
  > "approximately agree with those in a previous study (cite: falco1999)" (3.3 Differential Extinction)

## Software

- **CASA** 4.5.3 (stated for simalma): calibration, imaging, simulation  
  > "The calibration and imaging of the data were carried out using the Common Astronomy Software Application package" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux ratios A2/A1, B/A1 (robust -1) | 0.87, 0.38 | 0.03, 0.06 | dimensionless | 2 | $(\textrm{A2}/\textrm{A1}, \textrm{B}/\textrm{A1}) =(0.87\pm 0.03,0.38\pm 0.06)$ |
| Flux density of Y in 0.26 arcsec aperture | 0.26 | 4.0 sigma | mJy | 2 | inside an aperture radius of $0.26\,\textrm{arcsec}$ centered at the peak is $0.26\,\textrm{mJy}$ |
| Dust mass of Y from continuum | 1e6-1e7 | not stated | Msun | 3 | the dust mass is $M_\textrm{d}=10^{6-7}\,M_{\odot}$ |
| chi2_tot/dof G+X | 29.0/4 | not stated | dimensionless | 4 | $\chi^2_{\textrm{tot}}/$dof / 29.0/4 / 5.4/2 / 6.0/2 |
| Allowed redshift of Y | 0.548-0.983 | not stated | dimensionless | 4 | yielded $0.548 \le z_{\textrm{Y}} \le 0.983$ |
| Mass of Y (dKappa>dKappa(A2)) | 1.3(1.1)e9 | not stated | Msun | 4 | the masses of Y are $1.3(1.1)\times 10^9 M_{\odot}$ and $3.7(3.6)\times 10^9 M_{\odot}$ |
| Velocity dispersion of Y | 25(28) | not stated | km/s | 4 | $\sigma_{\textrm{Y}}\sim 25(28)\,\textrm{km}\,\textrm{s}^{-1}$ |
| Differential extinction A2 rel. B (z=0.5, 1.0) | 1.11, 0.77 | 0.05, 0.04 | mag | 6 | those of A2 relative to B were $1.11\pm0.05$, $0.77\pm0.04$ for $0.5$, $1.0$, respectively |
| Dust mass from extinction | ~1e7 (1.6(0.6)e7 Galaxy; 2.7(1.1)e7 SMC) | not stated | Msun | 6 | $1.6(0.6) \times 10^7\,M_{\odot}$ for the Galaxy dust model, and $2.7(1.1) \times 10^7\,M_{\odot}$ for the SMC dust model |

## Qualitative findings

- Simulated observation shows Y is not a sidelobe of A1 or A2.  
  > "Therefore, it is unlikely that Y is related with sidelobes of A1 or A2." (3.2 Flux-Ratio Anomaly)

## Claim tuples

- H: A faint object Y near A2 is real and not a sidelobe artifact | E: Natural-weighted imaging, aperture photometry and simalma simulation | R: 4.0 sigma detection of 0.26 mJy; no spot in simulation | F: Y is a real faint submm source | **partially**
- H: Y as a lens substructure explains the submm/MIR flux-ratio anomaly | E: Lens models G+X vs G+X+Y | R: chi2/dof 29.0/4 improves to 5.4/2 with Y of e_Y=0.72 | F: Y with high ellipticity at 0.5<z<1 explains the anomaly | **supported**
- H: Y causes the differential extinction of A1 and A2 | E: Extinction curve fits and convergence ratio comparison | R: Convergence ratio 3.7-4.3 vs extinction ratio ~3.4; dust mass ~1e7 consistent with submm | F: Y is a good candidate obscurer; a dusty dark dwarf galaxy | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Sidelobe of A1/A2 rejected via simulation  
  > "Therefore, it is unlikely that Y is related with sidelobes of A1 or A2." (3.2 Flux-Ratio Anomaly)
- How they decided it was enough: _not stated_
- Limitation (authors): Detection only ~4 sigma; Y's redshift is not measured  
  > "We report the $4 \, \sigma$ detection of a faint object" (abstract)
- Caveat (inferred, ours): 4 sigma detection is marginal; no independent confirmation
- Caveat (inferred, ours): Lens model has few degrees of freedom (dof=2) and needs a weak prior and high ellipticity
- Caveat (inferred, ours): Y centroid fixed by matching bright spots, could bias model
- Caveat (inferred, ours): Dark nature rests on non-detection and very uncertain redshift

## Reproducibility

- Data public (paper): Archive project code cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2013.1.01110.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Lens modeling code not named
- Missing: CASA version for reduction
- Missing: Clean masks and thresholds
- Missing: Aperture photometry details
- Data volume (inferred): ~10-50 GB raw for two Band 7 execution blocks
- Score (inferred): 3/5, ALMA data identified and imaging parameters given, but lens modeling software and several imaging details missing.
- Rediscovery candidate: no, Marginal 4 sigma detection and unnamed lens modeling code make a faithful redo uncertain.

## Links

- Method: (cite: inoue-minezaki2016) (Source model magnification weighting definition)
- Companion: (cite: minezaki2009) (MIR flux ratios and anomaly background)
- Related: CASTLES

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 48,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
