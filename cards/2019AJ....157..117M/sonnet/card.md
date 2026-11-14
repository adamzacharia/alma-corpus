# On the Ubiquity and Stellar Luminosity Dependence of Exocometary CO Gas: Detection around M Dwarf TWA 7

`2019AJ....157..117M` | The Astronomical Journal 2019 | first author: Matrà, L. | arXiv: 1901.05004 | DOI: 10.3847/1538-3881/aaff5b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: Is CO gas present in the TWA 7 planetesimal belt, is it exocometary, and can exocometary release explain the increase of CO detection rate with stellar luminosity?  
  > "we aim to understand how the presence of CO gas in a planetesimal belt is affected by its stellar host, and explain the origin of the decreasing CO occurrence rates around stars of decreasing stellar luminosity." (Introduction)
- Target **TWA 7**: coordinates RA 10h42m30.413s Dec -33d40m16.700s (pointing of the extended configurations)  
  > "two with 36 antennas in a more extended configuration pointed at coordinates RA: 10h42m30.413s Dec: -33d40m16.700s" (Observations); "This nearby star (cite: Gaia2018) is part of the TWA association (cite: Webb1999), setting its age at $\sim$10 Myr (cite: Bell2015)." (Introduction); z/distance not stated (beam 1.8x1.7 arcsec = 62x58 au)  
  > "two with 36 antennas in a more extended configuration pointed at coordinates RA: 10h42m30.413s Dec: -33d40m16.700s" (Observations); "This nearby star (cite: Gaia2018) is part of the TWA association (cite: Webb1999), setting its age at $\sim$10 Myr (cite: Bell2015)." (Introduction); distance from Gaia (cite: Gaia2018)  
  > "two with 36 antennas in a more extended configuration pointed at coordinates RA: 10h42m30.413s Dec: -33d40m16.700s" (Observations); "This nearby star (cite: Gaia2018) is part of the TWA association (cite: Webb1999), setting its age at $\sim$10 Myr (cite: Bell2015)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.01015.S
- bands: Band 7  
  > "TWA 7 was observed by ALMA in Band 7 using the 12m array in 2016." (Observations)
- frequencies and spectral setup: ~1200 channels of 244.141 kHz around 345.796 GHz  
  > "covering $\sim$1200, 244.141 kHz-wide channels around the transition frequency (345.796 GHz)" (Observations)
- continuum bandwidth: 6.9 GHz over 4 spectral windows  
  > "we considered all 6.9 GHz covered by the 4 spectral windows of each of the observations." (Observations)
- arrays: 12m array  
  > "TWA 7 was observed by ALMA in Band 7 using the 12m array in 2016." (Observations)
- configurations: three observations: one with 42 antennas compact, two with 36 antennas more extended  
  > "one with 42 antennas in a compact configuration" (Observations)
- baselines: 15.1 m to 3.1 km  
  > "altogether spanning baselines from 15.1 m to 3.1 km" (Observations)
- angular resolution: 1.8 x 1.7 arcsec (with 2 arcsec taper)  
  > "for a synthesized beam size of $1.8\ensuremath{''}\times 1.7\ensuremath{''}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: CO cube RMS 7 mJy/beam per 244.141 kHz channel; continuum 0.07 mJy/beam  
  > "The continuum image has an RMS noise level of 0.07 mJy/beam for the same synthesized beam size." (Observations)
- time on source: _not stated_
- observing dates: 2016  
  > "TWA 7 was observed by ALMA in Band 7 using the 12m array in 2016." (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- Other facility **FUSE / HST (literature)**: C III 977.40 A flux of AU Mic and beta Pic and FUV luminosities used to rescale CO photodissociation  
  > "We therefore use the C III stellar line intensities as measured in FUSE spectra at 977.40 Å as a proxy" (4.1 CO photodissociation)
- External data: Disk inclination 13 deg and PA 91 deg from SPHERE near-IR imaging; belt 20-100 au  
  > "for a disk with an inclination (13$^{\circ}$) and position angle (PA, 91$^{\circ}$) as derived from high resolution dust imaging in the near-IR (cite: Olofsson2018)" (3.1) [from (cite: Olofsson2018)]
- External data: Minimum grain size ~0.16 um from SED fitting  
  > "we can simply use the $D_{\rm min}$ value of $\sim$0.16 $\mu$m constrained from SED fitting (cite: Bayo2018)" (4.3.1) [from (cite: Bayo2018)]
- External data: Stellar mass 0.55 Msun for Keplerian field  
  > "Keplerian velocity field expected around a star of 0.55 M$_{\odot}$ (cite: Neuhauser2000)" (3.1) [from (cite: Neuhauser2000)]
- External data: CO detection rates vs stellar type (68.8% for A stars, 6.7% for FG)  
  > "(cite: Moor2017) reported a very high detection rate of 68.8$^{+8.9}_{-13.1}$% in belts around A stars" (4.4.1) [from (cite: Moor2017)]
- External data: Literature 5-sigma CO flux limits for sample belts  
  > "These were obtained from the literature (cite: Daley2019subm; Booth2017; Marino2017a; Marino2018a; Lieman-Sifry2016; Marino2016; Booth2018; Matra2017a; Kospal2013; Moor2017; Matra2017b; Kennedy2018)" (4.4.2) [from multiple]
- Simulation/model as data: PHOENIX stellar photospheric model (Teff=3394 K, log g=3.7, [M/H]=0.0) and Draine 1978 ISRF for CO excitation  
  > "a PHOENIX stellar photospheric model fitted to observations of TWA 7 with synthetic photometry (T$_{\rm eff}$=3394 K, log(g)=3.7, \[M/H\]=0.0)" (3.2)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Standard calibrations were applied to each dataset using the ALMA pipeline in CASA v5.1.0." (Observations)
- casa version: CASA v5.1.0  
  > "Standard calibrations were applied to each dataset using the ALMA pipeline in CASA v5.1.0." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% in Band 7  
  > "The uncertainty on the line flux included an extra 10% added in quadrature to account for ALMA’s flux calibration uncertainty in Band 7" (3.2)
- self calibration: _not stated_

### Imaging

- task: tclean in mosaic mode  
  > "imaged both separately and together using the *tclean* task within CASA, in mosaic mode with multiscale deconvolution" (Observations)
- deconvolver: multiscale  
  > "in mosaic mode with multiscale deconvolution" (Observations)
- weighting robust: natural weighting  
  > "we use natural weighting and further apply a 2$\ensuremath{''}$ u-v taper" (Observations)
- uv taper: 2 arcsec  
  > "we use natural weighting and further apply a 2$\ensuremath{''}$ u-v taper to the visibilities prior to imaging" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA  
  > "with continuum emission subtracted from it using the *uvcontsub* CASA task" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.8 x 1.7 arcsec  
  > "for a synthesized beam size of $1.8\ensuremath{''}\times 1.7\ensuremath{''}$" (Observations)
- final rms: 7 mJy/beam per 244.141 kHz channel (CO)  
  > "The final CO data cube reaches an RMS sensitivity of 7 mJy/beam in a 244.141 kHz channel" (Observations)

### Inherited from earlier work

- Observation details  
  > "Further details of the observations can be obtained in (cite: Bayo2018)." (Observations) [from (cite: Bayo2018)]
- Spectro-spatial filtering technique  
  > "Following the method of (cite: Matra2015; Matra2017b), we apply a spectro-spatial filtering technique" (3.1) [from (cite: Matra2015; Matra2017b)]
- Non-LTE CO excitation code  
  > "we use the non-LTE excitation code of (cite: Matra2015; Matra2018a)" (3.2) [from (cite: Matra2015; Matra2018a)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub
- Mask and clean threshold, cell and image size, scales for multiscale
- Exact velocity range/channels used in moment-0 and spectral extraction
- Spectral windows and velocity resolution/binning of the cube
- Annulus widths for radial profiles
- Details of the non-LTE code inputs (collider density grid)
- Gaia distance value for TWA 7
- Stellar mass inconsistency (0.55 vs 0.51 Msun) not explained

## Analysis recipe

1. **Spectro-spatial filtering to detect CO**: Shift each pixel's spectrum by the expected Keplerian radial velocity and integrate over the region within ~3.5 arcsec where continuum is above 2 sigma, for both rotation senses  
  > "we assign each pixel a given expected radial velocity and shift the 1d spectrum in that pixel along the frequency (velocity) axis, by the negative of its assigned radial velocity." (3.1)
   - software: CASA
   - parameter: M*=0.55 Msun, i=13 deg, PA=91 deg  
  > "Keplerian velocity field expected around a star of 0.55 M$_{\odot}$ (cite: Neuhauser2000)" (3.1)
   - fitting: _not stated_
   - validation: No boost when velocity field sign inverted  
  > "whereas no boost is achieved when the sign of the velocity field is inverted." (3.1)
2. **Radial profile of CO vs continuum**: Moment-0 over 4 channels nearest stellar velocity after shifting; azimuthal average in elliptical annuli  
  > "we also produce a moment-0 map by spectrally integrating emission over the 4 channels nearest to the stellar velocity." (3.1)
   - fitting: _not stated_
   - validation: Compared with continuum radial profile  
  > "with a radial profile consistent with that extracted from the continuum images" (3.1)
3. **Measure line flux**: Gaussian fit to filtered spectrum  
  > "fitting a Gaussian to the green, spectrospatially filtered spectrum" (3.2)
   - software: SciPy curve_fit
   - parameter: Channel errors = RMS x sqrt(2.667) for correlated channels; 10% calibration error added in quadrature  
  > "assumed to be equal to the RMS of the spectrum multiplied by a factor $\sqrt{2.667}$" (3.2)
   - fitting: non-linear least squares  
  > "Uncertainties were calculated from SCIPY’s *curve_fit* non-linear least squares method" (3.2)
   - validation: _not stated_
4. **CO mass and optical depth**: Non-LTE excitation modelling for optically thin emission, range between LTE and radiation-dominated regimes; optical depth check assuming disk 20-100 au face-on  
  > "the best-fit line flux corresponds to CO masses in the range 0.8-80$\times10^{-6}$ M$_{\oplus}$" (3.2)
   - software: PHOENIX
   - parameter: stellar model scaled to 60 au; ISRF of Draine 1978  
  > "scaled to a distance of 60 au from the star" (3.2)
   - assumption: constant surface brightness belt between 20 and 100 au, face-on  
  > "we assume the disk to extend between 20 and 100 au, and to have a constant surface brightness." (3.2)
   - fitting: _not stated_
   - validation: Max optical depth tau<0.27 confirms optically thin  
  > "derive a maximum optical depth of $\tau<0.27$" (3.2)
5. **CO photodissociation timescale**: Rescale AU Mic FUSE C III 977.40 A flux and beta Pic values to TWA 7 by distance; combine with ISRF  
  > "we find that the CO-photodissociating radiation of M star TWA 7 is at least $\sim$6% that of A star $\beta$ Pic." (4.1)
   - assumption: C III line is dominant stellar CO photodissociator in TWA 7 as in AU Mic  
  > "this line is the likely dominant contributor to stellar CO photodissociation around AU Mic, and by inference around TWA 7." (4.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **Test primordial vs exocometary origin**: Include CO self-shielding and H2 shielding (Visser 2009) with CO/H2=1e-6 to compute maximum lifetime  
  > "the photodissociation lifetime is only prolonged by another factor 4 to 1000 years" (4.2)
   - assumption: CO/H2 ratio of 1e-6  
  > "with a CO/H$_2$ ratio of 10$^{-6}$ (cite: Favre2013)" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
7. **Exocomet CO(+CO2) mass fraction**: Steady-state: CO release equals photodissociation; small-grain mass loss rate from collisional cascade with Dmin from stellar wind  
  > "derive a CO(+CO$_2$) mass fraction $f_{\mathrm{CO}+\mathrm{CO}_2}$ $\geq70$% for exocomets around TWA 7." (4.3.2)
   - parameter: Dmin 0.16 um, M*=0.51 Msun, f=1.7e-3, R~60 au, width ~80 au  
  > "taking TWA 7’s stellar mass of 0.51 M$_{\odot}$, fractional luminosity of 1.7$\times$10$^{-3}$, and approximate belt radius of $\sim$60 au with width of $\sim$80 au" (4.3.1)
   - assumption: Small grain removal dominated by outward stellar wind pressure; other volatiles negligible  
  > "We therefore postulate that small grain removal from the TWA 7 belt is dominated by outward stellar wind pressure." (4.3.1)
   - fitting: _not stated_
   - validation: _not stated_
8. **Predict CO mass and flux vs stellar luminosity**: Eq. 2/3 for belts resolved by ALMA, convert predicted CO masses to line fluxes (optically thin, 20 K) and compare to literature 5-sigma thresholds  
  > "we assume, for all belts, optically thin emission for an excitation temperature of 20 K (cite: Matra2015)" (4.4.2)
   - parameter: R=73 L^0.19, tphd=120 yr, f_CO=20%, dR/R=0.4, M=L^0.25, f=1.56e-3 L^0.2  
  > "Assuming $R=73L_{\star}^{0.19}$ (cite: Matra2018b), a constant photodissociation timescale of 120 years, a CO(+CO$_2$) mass fraction of 20%" (4.4.1)
   - assumption: CO(+CO2) mass fraction range 0.8-80%  
  > "For each belt, we show the predicted range of exocometary CO gas masses for CO(+CO$_2$) ice mass fractions of 0.8-80%" (4.4.1)
   - fitting: simple regression of f-L relation  
  > "the best-fit from a simple regression of the observed $f-L_{\star}$ relation for the above sample" (4.4.1)
   - validation: Compared qualitatively with detected/undetected status of sample  
  > "This explains the trend of increasing detection rates as a function of stellar luminosity found by (cite: Moor2017)" (4.4.2)

## Software

- **CASA** v5.1.0: Pipeline calibration, uvcontsub, tclean imaging  
  > "Standard calibrations were applied to each dataset using the ALMA pipeline in CASA v5.1.0." (Observations)
- **SciPy (curve_fit)** : Gaussian fit to line and uncertainties  
  > "Uncertainties were calculated from SCIPY’s *curve_fit* non-linear least squares method (cite: Jones2001)." (3.2)
- **PHOENIX** : Stellar photospheric model for CO excitation  
  > "a PHOENIX stellar photospheric model fitted to observations of TWA 7" (3.2)
- **Matplotlib** : Plotting (listed in Software section)  
  > "Matplotlib (cite: Hunter2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak S/N of CO spectrum, unfiltered to filtered | 3.7 to 6.4 | not stated | sigma | 1 | the detection is significantly boosted from a peak S/N of 3.7$\sigma$ to 6.4$\sigma$ |
| Integrated CO J=3-2 line flux | 91 | 20 | mJy km/s | 3 | obtaining a value of 91$\pm$20 mJy km/s for a centroid radial velocity of 11.75$\pm$0.08 km/s |
| Centroid radial velocity | 11.75 | 0.08 | km/s | 3 | centroid radial velocity of 11.75$\pm$0.08 km/s |
| CO mass | 0.8-80e-6 | range from excitation regimes | Earth masses | 4 | CO masses in the range 0.8-80$\times10^{-6}$ M$_{\oplus}$ |
| Maximum CO optical depth | <0.27 | not stated | dimensionless | 4 | maximum optical depth of $\tau<0.27$ |
| CO unshielded photodissociation timescale at 60 au | 99 | not stated | years | 5 | the CO unshielded photodissociation timescale around TWA 7 is 99 years at 60 au |
| Shielded CO lifetime upper limit | 1000 | not stated | years | 6 | the photodissociation lifetime is only prolonged by another factor 4 to 1000 years |
| Mass loss rate of small grains | 0.003 | not stated | Earth masses per Myr | 7 | mass loss rate of small grains from the collisional cascade of 0.003 M$_{\oplus}$ Myr$^{-1}$ |
| CO(+CO2) mass fraction of exocomets | >=70 | lower limit | % | 7 | $f_{\mathrm{CO}+\mathrm{CO}_2}$ $\geq70$% for exocomets around TWA 7 |
| Predicted CO mass scaling with luminosity | L^1.37 | not stated | dimensionless | 8 | we should expect $M_{\rm CO}\propto L_{\star}^{1.37}$ |

## Qualitative findings

- CO emission is co-located with the dust belt and consistent with Keplerian rotation, East side receding  
  > "with the East side of the gas disk moving away from Earth." (3.1)

## Claim tuples

- H: CO gas is present in the TWA 7 belt, co-located with dust and Keplerian | E: Spectro-spatial filtering of the ALMA CO J=3-2 cube | R: Peak S/N boosted from 3.7 to 6.4 sigma for one rotation sense; radial profile matches continuum | F: First CO detection in a belt around an M star | **supported**
- H: TWA 7 CO is secondary (exocometary) | E: Photodissociation and shielding lifetime estimates | R: Max lifetime ~1000 yr, much less than the age | F: CO is exocometary | **supported**
- H: TWA 7 exocomets have composition like other exocomets | E: Steady-state mass-loss balance with Dmin from SED | R: f_CO+CO2 >= 70% | F: High CO content, but subject to uncertain assumptions (grain size, shielding, flares) | **partially**
- H: Exocometary release explains rising CO detection rate with stellar luminosity | E: Predict CO masses and fluxes for ALMA-resolved belts and compare with detection thresholds | R: Predicted flux rises with luminosity while sensitivity is roughly constant | F: Consistent with ubiquitous exocometary gas release | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Primordial CO ruled out via short shielded lifetime  
  > "Since this is much shorter than the age of the system, we conclude that primordial CO" (4.2)
- Alternative: Corpuscular wind drag dominated removal rejected because no inner hole filled with small grains or steep outer slope seen in SPHERE  
  > "These are not observed in SPHERE images of TWA 7, tracing the smallest grains" (4.3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Inner hole not resolved with this dataset  
  > "The present dataset does not allow us to resolve the inner hole of the dust belt" (3.1)
- Limitation (authors): Single CO transition leaves excitation unconstrained; mass uncertain over two orders of magnitude  
  > "the parameter dominating the uncertainty is the unknown molecular excitation for observations of a single transition" (4.4.2)
- Caveat (inferred, ours): Detection is only ~6 sigma after filtering that assumes disk geometry from near-IR
- Caveat (inferred, ours): Photodissociation rate rescaled from AU Mic with a single line
- Caveat (inferred, ours): Mass fraction depends on poorly constrained Dmin and wind parameters
- Caveat (inferred, ours): Luminosity trend uses heterogeneous literature sensitivities and a toy parametrization

## Reproducibility

- Data public (paper): Data cited as ALMA project 2015.1.01015.S, previously published in Bayo et al. 2018  
  > "This paper makes use of ALMA data ADS/JAO.ALMA#2015.1.01015.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters (mask, threshold, cell/image size, scales)
- Missing: Line-free channel selection
- Missing: Custom spectro-spatial filtering and excitation code not released
- Missing: Literature flux limits compiled in Fig. 3 not tabulated
- Data volume (inferred): ~20-50 GB for three Band 7 execution blocks
- Score (inferred): 3/5, Public data and clear outline, but imaging parameters and custom codes are missing.
- Rediscovery candidate: no, Key results rely on custom filtering/excitation code and many unspecified imaging settings.

## Links

- Method: (cite: Matra2015; Matra2017b) (spectro-spatial filtering method and exocometary composition framework)
- Method: (cite: Matra2018a) (non-LTE CO excitation code)
- Companion: (cite: Bayo2018) (same ALMA dataset, continuum analysis)
- Companion: (cite: Olofsson2018) (SPHERE imaging of the belt geometry)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 67,
  "rate": 0.698
 },
 "evidence_ok": true
}
```
