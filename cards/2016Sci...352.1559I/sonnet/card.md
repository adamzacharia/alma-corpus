# Detection of an oxygen emission line from a high-redshift galaxy in the reionization epoch

`2016Sci...352.1559I` | Science 2016 | first author: Inoue, Akio K. | arXiv: 1606.04989 | DOI: 10.1126/science.aaf0714

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the ISM properties (oxygen abundance, dust, neutral gas) of a z=7.2 Lyman-alpha emitter, probed via [O III] 88 um and [C II] 158 um, and do they allow ionizing photon escape?  
  > "The non-detection of far-infrared continuum emission indicates a deficiency of interstellar dust in the galaxy." (abstract)
- Target **SXDF-NB1006-2**: coordinates RA 02h18m56.536s, Dec -05d19m58.87s (J2000)  
  > "Redshift of [O iii] 88 $\mu$m | $7.2120 \pm 0.0003$" (Table 1); "Right Ascension (J2000) | $2^\mathrm{h}18^\mathrm{m}56.536^\mathrm{s}$ ($\pm 0.002^\mathrm{s}$)" (Table 1); z/distance z = 7.2120 ± 0.0003  
  > "Redshift of [O iii] 88 $\mu$m | $7.2120 \pm 0.0003$" (Table 1); "Right Ascension (J2000) | $2^\mathrm{h}18^\mathrm{m}56.536^\mathrm{s}$ ($\pm 0.002^\mathrm{s}$)" (Table 1); distance from [O III] 88 um line (this work)  
  > "Redshift of [O iii] 88 $\mu$m | $7.2120 \pm 0.0003$" (Table 1); "Right Ascension (J2000) | $2^\mathrm{h}18^\mathrm{m}56.536^\mathrm{s}$ ($\pm 0.002^\mathrm{s}$)" (Table 1)

## Data provenance

- ALMA projects: 2013.1.01010.S, 2012.1.00374.S
- bands: Band 8 ([O III]) and Band 6 ([C II])  
  > "The ALMA band 8 data of the [O III] 88 $\mu$m emission line" (Materials and Methods)
- frequencies and spectral setup: Band 8: 400.1–403.6 and 412.1–414.0 GHz, FDM 1.875 GHz windows, 7.8125 MHz resolution; Band 6: 215.7–219.5 and 230.4–234.2 GHz, 0.488 MHz resolution  
  > "400.1–403.6 and 412.1–414.0 GHz were covered by four spectral windows" (Materials and Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 8 C34-6/7; Band 6 C32-5  
  > "30–34 antennas were operational under the C32-5 configuration" (Materials and Methods)
- baselines: Band 8: 21.3–783.5 m; Band 6: 17.2–558.2 m  
  > "the maximum and minimum baseline lengths were 783.5 m and 21.3 m, respectively" (Materials and Methods)
- angular resolution: Band 8 natural 0.35x0.26 arcsec; tapered 0.45x0.38 arcsec; Band 6 0.80x0.60 arcsec  
  > "The resulting beam size is $0.''45 \times 0.''38$ (PA = $+78^{\circ}$)." (Materials and Methods)
- max recoverable scale: _not stated_
- sensitivity: Band 8: 0.53 mJy/beam (20 km/s cube), 0.042 mJy/beam continuum; Band 6: 0.26 and 0.014 mJy/beam  
  > "The achieved noise levels for the 20 km s$^{-1}$ cube and the continuum image are 0.26 and 0.014 mJy beam$^{-1}$, respectively." (Materials and Methods)
- time on source: Band 8: 2.0 hr; Band 6: 1.8 hr  
  > "A total of 2.0 hour was spent for on-source integration" (Materials and Methods)
- observing dates: Band 8: 2015 June 7, 9, 14; Band 6: 2014 August 1 and 5  
  > "were obtained on 2015 June 7, 9 and 14" (Materials and Methods)
- pi or archival as stated: _not stated_
- Line: [O III] 88 um (3393.01 GHz)
- Line: [C II] 158 um (1900.54 GHz)
- Other facility **Subaru, UKIRT/UKIDSS, Spitzer/IRAC**: Optical-NIR photometry (NB1006, J, H, K, 3.6, 4.5 um) for SED fitting  
  > "We have gathered archival optical-to-near infrared (NIR) deep images available in the SXDF" (Optical-to-near infrared data)
- External data: [O III]-SFR relation  
  > "If we assume the relation derived from the entire sample of (cite: delooze14), we obtain a SFR $>100$ M$_\odot$ yr$^{-1}$" (Empirical SFR estimation) [from De Looze et al. 2014 (cite: delooze14)]
- External data: Ly-alpha redshift and NB1006 narrowband data  
  > "slightly lower than the redshift determined from the Ly$\alpha$ emission line (cite: shibuya12)" (Results) [from Shibuya et al. 2012 (cite: shibuya12)]
- External data: [O III] line emission model  
  > "For the [O iii] 88 $\mu$m line, the model presented in (cite: inoue14) is adopted." (Nebular emission) [from Inoue et al. 2014 (cite: inoue14)]
- External data: z~7 cosmic ionizing emissivity and UV luminosity functions  
  > "$\log_{10}(\dot N_{\rm ion} {\rm [s^{-1}~Mpc^{-3}]})=50.79\pm0.06$ at $z\sim7$" (Ionizing photon emission efficiency) [from Bouwens et al. 2015b (cite: bouwens15b); Bouwens 2015 (cite: bouwens15); Finkelstein 2015 (cite: finkelstein15)]
- Simulation/model as data: Cosmological hydrodynamic simulation (gadget-3) galaxies at z=7.22, 2x640^3 particles in 100 h^-1 Mpc box  
  > "We employ $2\times640^3$ particles for dark matter and gas in a comoving volume of $100h^{-1}$ Mpc cube." (Comparison with a cosmological simulation)

## Processing

### Calibration

- pipeline or manual: Standard observatory calibration script plus manual flagging  
  > "along with a standard calibration script provided by the observatory" (Materials and Methods)
- casa version: CASA 4.3.1 ([O III]) and 4.2.1 ([C II])  
  > "version 4.3.1 and 4.2.1 for the [O III] and [C II] data, respectively" (Materials and Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 8: Ceres; Band 6: Neptune and J0238+166  
  > "Both Neptune and J0238+166 were used for flux calibration to cross-check the amplitude scaling." (Materials and Methods)
- flux scale uncertainty: 10% (Band 8), 8% (Band 6)  
  > "The flux calibration accuracy is estimated at 10%." (Materials and Methods)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Imaging is carried out using a CASA task, `clean`, with the natural weighting" (Materials and Methods)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with the natural weighting to maximize the point-source sensitivities" (Materials and Methods)
- uv taper: outertaper = 0.3 arcsec for [O III]  
  > "we also make a $uv$-tapered image with `outertaper` = $0.''3$ to achieve a good detection" (Materials and Methods)
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN down to 1.5 sigma for [O III]  
  > "Synthesized-beam deconvolution was made for the [O III] image using the CLEAN algorithm down to a $1.5\sigma$ level." (Materials and Methods)
- multiscale scales: _not stated_
- continuum subtraction: not subtracted; no continuum found  
  > "Continua are not subtracted in [O iii] and [C ii] imaging because no continuum emission is found." (Materials and Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.45x0.38 arcsec (tapered [O III])  
  > "The resulting beam size is $0.''45 \times 0.''38$ (PA = $+78^{\circ}$)." (Materials and Methods)
- final rms: _not stated_

### Inherited from earlier work

- Lyα redshift and profile/narrowband photometry from earlier survey paper  
  > "which is also consistent with the observed FWHM of the line (11.5 Å (cite: shibuya12))" (Results) [from Shibuya et al. 2012 (cite: shibuya12)]
- SED nebular emission prescription  
  > "following the prescription of (cite: inoue10; inoue11)" (Nebular emission) [from Inoue 2010, 2011 (cite: inoue10; inoue11)]
- Simulation details  
  > "further details of the simulation are found in (cite: shimizu14; shimizu15)" (Comparison with a cosmological simulation) [from Shimizu et al. 2014, 2015]

### Not stated but needed to reproduce (our reading)

- Line-free channels / velocity-axis and channel settings for clean
- Exact clean threshold in mJy, image size and cell size
- Mask definition for clean
- Details of the Monte Carlo Schechter integration
- Grid spacing for SFR, age, E(B-V), fesc in SED fit
- Aperture/position used for spectrum extraction

## Analysis recipe

1. **Calibrate and image ALMA data**: Standard CASA calibration, manual flagging, natural-weighted clean plus uv-tapered [O III] image  
  > "we also make a $uv$-tapered image with `outertaper` = $0.''3$ to achieve a good detection" (Materials and Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: Separate images for three tracks each show ~3 sigma peak  
  > "We find a $\sim 3\sigma$ peak at the position of SXDF-NB1006-2 in every image" (Results)
2. **Measure [O III] flux and redshift**: Gaussian fit to spectrum for redshift; imfit Gaussian fit of tapered integrated intensity image, beam-deconvolved  
  > "fitting the tapered integrated intensity image to a Gaussian using a CASA task, `imfit`, and deconvolving the clean beam" (Results)
   - software: CASA imfit
   - parameter: Integrated over -300 to +230 km/s  
  > "integrated over $-300$ to $+230$ km s$^{-1}$" (Results)
   - fitting: Gaussian  
  > "First, we have made a fitting with a Gaussian function and obtained the following results: $A=(1.67\pm0.15)\times10^{-18}$ erg s$^{-1}$ cm$^{-2}$ Å$^{-1}$" (Velocity offset between Ly$\alpha$ and [O iii] lines)
   - validation: Pixel SNR histogram Gaussian below SNR 4  
  > "is well described by a Gaussian (i.e., normal distribution) at the pixel values below SNR $<4$" (Results)
3. **Upper limits on [C II] and continuum; TIR**: 3 sigma limits; TIR from modified blackbody integrated 8–1000 um  
  > "integrated over the rest-frame wavelengths of 8–1000 $\mu$m" (Dust continuum)
   - assumption: T_dust = 40 K, beta = 1.5  
  > "the dust temperature and emissivity index are assumed to be $T_{\rm dust}=40$ K and $\beta = 1.5$, respectively" (Dust continuum)
   - fitting: _not stated_
   - validation: _not stated_
4. **Lyα velocity offset**: Asymmetric Gaussian fit to Lyα profile vs [O III] systemic redshift, heliocentric correction  
  > "We have performed a profile fitting of the Ly$\alpha$ line with an asymmetric Gaussian function" (Velocity offset between Ly$\alpha$ and [O iii] lines)
   - fitting: Asymmetric Gaussian with sigma fixed at 4.71 A  
  > "Next, we have made a fitting with an asymmetric Gaussian function with a fixed $\sigma=4.71$ Å from the Gaussian fit" (Velocity offset between Ly$\alpha$ and [O iii] lines)
   - validation: _not stated_
5. **SED fitting for physical properties**: chi^2 minimization over PEGASE2 models with nebular lines and Lyα IGM transmission, using 8 constraints including [O III] flux and IR limit  
  > "This is based on a standard $\chi^2$ minimization method" (Spectral energy distribution modeling)
   - software: PEGASE, cloudy
   - parameter: Z grid 0.0004–0.05; T_IGM 0.20–0.45; Rgs = 1 or 2; age lower limit 1 Myr  
  > "$Z=0.0004$, 0.001, 0.002, 0.004, 0.008, 0.02($=Z_\odot)$, or 0.05, $T_{\rm Ly\alpha}^{\rm IGM}=0.20$, 0.30, 0.35, 0.40, or 0.45, and $R_{\rm gs}=1$ or 2." (Spectral energy distribution modeling, Results)
   - assumption: Salpeter IMF 0.1–100 Msun, constant SFH, Calzetti law  
  > "A constant star formation history is also assumed for simplicity." (Stellar continuum)
   - fitting: 68.4% ranges via Delta chi2<1  
  > "The resultant best-fit values and their 68.4% ranges (i.e. $\Delta \chi^2<1$) are summarized in Table S4" (Spectral energy distribution modeling, Results)
   - validation: Alternative upper-limit treatments give same best-fit  
  > "We have tried these two methods and found that the best-fit parameters do not change" (Spectral energy distribution modeling)
6. **Ionizing photon efficiency vs reionization requirement**: Compute fesc*xi_ion; Monte Carlo of Schechter fits to z~7 UV LFs to compare  
  > "We have performed a set of Monte Carlo realizations of Schechter function fits" (Ionizing photon emission efficiency)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1 / 4.2.1: Calibration, clean, imfit  
  > "version 4.3.1 and 4.2.1 for the [O III] and [C II] data, respectively" (Materials and Methods)
- **PEGASE** 2: Stellar population models for SED fit  
  > "PEGASE ver. 2" (Stellar continuum)
- **cloudy** : HII region and [O III] line models  
  > "a public photoionization code, cloudy (cite: ferland13)" (Nebular emission)
- **gadget-3** : Cosmological simulation compared  
  > "The simulation code we used is gadget-3" (Comparison with a cosmological simulation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [O III] 88um line significance | 5.3 | not stated | sigma | 2 | The [O iii] line is detected with a significance of $5.3\sigma$ |
| [O III] integrated intensity | 0.45 | 0.09 | Jy km/s | 2 | Integrated intensity (Jy km s$^{-1}$) / $0.45 \pm 0.09$ |
| [O III] luminosity | 3.8e35 | 0.8e35 | W | 2 | $3.8(\pm0.8)\times10^{35}$ |
| [O III] redshift | 7.2120 | 0.0003 | dimensionless | 2 | Redshift of [O iii] 88 $\mu$m / $7.2120 \pm 0.0003$ |
| [C II] flux upper limit | <5.3e-22 | 3 sigma | W m^-2 | 3 | $< 5.3
     \times 10^{-22}$ $(3\sigma)$ |
| Total IR luminosity limit (40 K) | <2.9e37 | 3 sigma | W | 3 | $<2.9\times10^{37}$ ($3\sigma$) |
| Lyα velocity offset | +110 | 30 | km/s | 4 | $+1.1(\pm0.3)\times10^2$ |
| log fesc*xi_ion | 25.44 | +0.46/-0.84 | Hz erg^-1 | 6 | $\log_{10}(f_{\rm esc}\xi_{\rm ion}/{\rm Hz~erg^{-1}})=25.44^{+0.46}_{-0.84}$ |
| Escape fraction of ionizing photons | 0.54 | +0.17/-0.54 | dimensionless | 5 | Escape fraction of ionizing photons / $0.54_{-0.54}^{+0.17}$ |
| log stellar mass | 8.54 | +0.79/-0.22 | log Msun | 5 | $8.54_{-0.22}^{+0.79}$ |

## Qualitative findings

- Galaxy has oxygen abundance ~5%-100% solar, very little dust and little neutral gas.  
  > "The observed strong [O iii] line flux favors an oxygen abundance of 5% to 100% that of the Sun" (main text)

## Claim tuples

- H: Can [O III] 88um be detected from a z>7 LAE and constrain its metallicity? | E: ALMA Band 8 observation plus SED modeling | R: 5.3 sigma detection; Z between 0.05 and 1 solar | F: Chemical enrichment already proceeded | **supported**
- H: Is the galaxy dust-poor and HI-poor? | E: Continuum and [C II] upper limits vs nearby dwarfs and simulation | R: Dust-to-metal ratio <20%; [C II] undetected | F: Deficiency of dust and neutral gas | **supported**
- H: Can galaxies like this drive reionization? | E: Compare fesc*xi_ion with required emissivity | R: Sufficient if M_UV<-17 galaxies are similar | F: Possible prototype of reionization source | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Other treatments of non-detections in SED fit (1.5 sigma, Sawicki 2012) gave same best fit  
  > "We have tried these two methods and found that the best-fit parameters do not change" (Spectral energy distribution modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Low SNR; origin of possible high-velocity components uncertain; [C II] marginal features affected by ozone line  
  > "we can not conclude the origin of the possible high-velocity components because of the limited SNR for the moment" (Possible kinematics signature)
- Caveat (inferred, ours): Only 5.3 sigma detection
- Caveat (inferred, ours): SED fit uses constant SFH and fixed grid parameters, 8 constraints vs 7 parameters
- Caveat (inferred, ours): Metallicity depends on cloudy model assumptions
- Caveat (inferred, ours): fesc strongly model dependent

## Reproducibility

- Data public (paper): ALMA data available in archive  
  > "which are available at https://almascience.nao.ac.jp/alma-data/archive" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean mask and threshold details
- Missing: SED fit code and grid
- Missing: Simulation outputs
- Data volume (inferred): ~50-100 GB raw for two projects
- Score (inferred): 3/5, Public data and decent description, but SED and imaging details sparse.
- Rediscovery candidate: yes, Public ALMA data, clear imaging recipe, numeric results (flux, redshift).

## Links

- Companion: Shibuya et al. 2012 (cite: shibuya12) (Discovery of SXDF-NB1006-2)
- Related: SXDF
- Related: UKIDSS UDS
- Related: SEDS

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 55,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
