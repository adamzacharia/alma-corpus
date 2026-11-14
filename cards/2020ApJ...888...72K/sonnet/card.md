# The Detection of Dust Gap-ring Structure in the Outer Region of the CR Cha Protoplanetary Disk

`2020ApJ...888...72K` | The Astrophysical Journal 2020 | first author: Kim, Seongjoong | arXiv: 1911.13017 | DOI: 10.3847/1538-4357/ab5d2b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the CR Cha disk have dust gap/ring substructure, and what mechanism (planet gap opening or dust trapping at a gas temperature/pressure bump) could produce it?  
  > "we show the results of the dust continuum and the CO isotopologue $J=2-1$ emission lines observed at ALMA Band 6 to examine the existence of small scale disk substructure like a gap or ring structure in the CR Cha disk." (Introduction)
- Target **CR Cha (Sz 6, Cha T8)**: coordinates _not stated_; z/distance 187.5±0.8 pc  
  > "The latest updated distance of CR Cha is $d\sim187.5\pm0.8\rm~pc$ (cite: GAIA2018)." (Introduction); distance from Gaia (Gaia Collaboration 2018)  
  > "The latest updated distance of CR Cha is $d\sim187.5\pm0.8\rm~pc$ (cite: GAIA2018)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00286.S
- bands: Band 6  
  > "The CR Cha protoplanetary disk is observed at ALMA Band 6 on November 2017 and March 2018" (Observation)
- frequencies and spectral setup: 4 SPWs: continuum at 233 and 217 GHz (1.8 GHz each); 12CO 230.538, 13CO 220.398, C18O 219.560 GHz; 61 kHz (~0.08 km/s) resolution  
  > "The spectral resolution for three CO isotopologue lines is 61 kHz, corresponding to $\rm \sim0.08~km~s^{-1}$ in velocity." (Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12.54 m to 7.908 km  
  > "The projected baselines are from 12.54 m to 7.908 km" (Observation)
- angular resolution: 0.087x0.052 arcsec (continuum); ~0.19x0.13 arcsec (CO)  
  > "Dust | 225 | $\sim0.0178$ |  | $0.087\times0.052$ | 35.75" (Table 1)
- max recoverable scale: ~5 arcsec  
  > "corresponding to a maximum angular coverage of $\sim5''$" (Observation)
- sensitivity: _not stated_
- time on source: ~2 hours on source (~3.2 hours total)  
  > "The total execution time for the observations is $\sim3.2$ hours including the target on-source time of $\sim2$ hours." (Observation)
- observing dates: November 2017 and March 2018  
  > "observed at ALMA Band 6 on November 2017 and March 2018" (Observation)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.398 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- External data: Dust opacity kappa_225GHz = 2.3 cm^2/g  
  > "$\rm \kappa_{\rm 225GHz}=2.3~cm^{2}~g^{-1}$ (cite: Beckwith1990) is the dust opacity at 225 GHz." (4.1) [from (cite: Beckwith1990)]
- External data: Stellar parameters: M*=1.657 Msun, Teff 4800 K, R*=3.113 Rsun  
  > "We adopt the stellar mass of $\rm 1.657~M_{\odot}$, the effective temperature of 4800 K, and the stellar radius of $\rm 3.113~R_{\rm \odot}$ (cite: Villebrun2019)." (4.4.2) [from (cite: Villebrun2019)]
- External data: Isotopologue abundance ratios 12CO/C18O=444, 12CO/13CO=67  
  > "We also assume the abundance ratio of $\rm^{12}CO/C^{18}O=444$ and $\rm ^{12}CO/^{13}CO=67$ (cite: Qi2011)." (4.4.2) [from (cite: Qi2011)]
- External data: C18O molecular data (S mu^2, Eu/k) from LAMDA and CDMS  
  > "from the Leiden Atomic and Molecular Database (cite: Schoier2005) and Cologne Database for Molecular Spectroscopy (cite: Muller2001CDMS)" (4.2) [from (cite: Schoier2005; Muller2001CDMS)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline  
  > "The basic calibration steps are progressed through the ALMA calibration pipeline using `CASA` package version 5.3." (Observation)
- casa version: CASA 5.3  
  > "using `CASA` package version 5.3" (Observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 and J0635-7516 (bandpass and flux); J1058-8003 phase calibrator  
  > "J1427-4206 and J0635-7516 are used for the bandpass and flux calibrations at each observation." (Observation)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal applied to continuum; applied to CO but no improvement  
  > "We also apply the phase self-calibration to the CO line data but the images are not improved." (Observation)

### Imaging

- task: CLEAN command in CASA  
  > "we make the images of dust continuum and CO isotopologue emission lines by `CLEAN` command in `CASA`." (Observation)
- deconvolver: _not stated_
- weighting robust: Continuum Briggs robust=0; CO robust=2.0 (natural)  
  > "The Briggs $\rm robust=0$ is used for the dust continuum image" (Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum 0.087x0.052 arcsec PA 35.75; 12CO 0.188x0.128; 13CO 0.196x0.143; C18O 0.194x0.142  
  > "The synthesized beam size is $\sim0.188''\times0.128''$ for the $^{12}$CO line, $\sim0.196''\times0.143''$ for the $^{13}$CO line" (Observation)
- final rms: Continuum ~0.0178 mJy/beam; CO cubes ~2.3-2.5 mJy/beam  
  > "The $1\sigma$ RMS level of dust continuum image is $\rm \sim0.0178~mJy~beam^{-1}$." (3.1)

### Inherited from earlier work

- Peak brightness temperature of optically thick line from line+continuum (no continuum subtraction) used as gas temperature  
  > "The line plus continuum intensity should be used in order to derive the gas temperature from the peak brightness temperature of an optically thick line (cite: Weaver2018)." (3.3) [from (cite: Weaver2018)]
- Gap-depth/width planet models and minimum planet mass  
  > "We adopt the model of (cite: Rosotti2016MNRAS_459_2790R) to estimate the minimum planet mass for reproducing the dust gap structure in the CR Cha disk." (4.4.1) [from (cite: Rosotti2016MNRAS_459_2790R); (cite: Kanagawa2017)]
- Dust opacity models for small and large grains  
  > "The opacity models for both small and large dust grains are described in (cite: Hashimoto2015)" (4.4.2) [from (cite: Hashimoto2015)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters: cell size, image size, masks, threshold, niter, uv taper
- Self-calibration solution intervals and number of iterations
- Line-free channels and continuum subtraction method
- Whether primary beam correction was applied
- Radial binning center/annulus details beyond 8 au, and how uncertainties were computed
- Fitting method details/priors and initial guesses for the Gaussian and power-law fits
- Disk-structure inputs for HO-CHUNK beyond those listed (luminosity, gas-dust coupling, grid setup)
- Pipeline version

## Analysis recipe

1. **Image continuum and CO lines**: CASA pipeline calibration, then CLEAN with Briggs robust 0 (continuum) and 2.0 (CO), phase self-cal on continuum  
  > "The Briggs $\rm robust=0$ is used for the dust continuum image" (Observation)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Disk geometry**: Ellipse fitting of continuum with imfit  
  > "We obtain the disk geometry by the ellipse fitting using `imfit` command in `CASA` package." (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Radial profiles and line ratios**: Azimuthal averaging in 8 au annuli within r<240 au; CO uses only the southern half-disk to avoid absorption  
  > "We azimuthally average every 8 au width annulus inside $\rm r\lesssim240$ au." (3.2)
   - fitting: _not stated_
   - validation: Ratios from dividing moment 0 maps first give identical results inside 200 au  
  > "even if we derive the line ratios by dividing the moment 0 maps first and then averaging azimuthally, the results are identical inside 200 au." (3.2)
4. **Gas temperature from peak brightness temperature**: Moment 8 maps without continuum subtraction; I_peak=B_nu(T_B,peak); fit power law + Gaussian over 20-200 au  
  > "we derive the peak brightness temperature (T$_{\rm B,peak}$) by assuming $\rm I_{ \nu,peak}=B_{\rm \nu}(T_{\rm B,peak})$" (3.3)
   - software: CASA
   - assumption: 12CO and 13CO optically thick so T_B = T_gas  
  > "Since $^{12}$CO and $^{13}$CO lines are optically thick, we can adapt the brightness temperature of these lines as a gas temperature." (Section 3.3 The peak brightness temperatures of the CO isotopologue lines)
   - fitting: Least-squares fit  
  > "we do the least square fit to the derived T$_{\rm B,peak}$ profiles using the power-law profile with a single Gaussian" (3.3)
   - validation: _not stated_
5. **Dust surface density and gap fit**: Sigma_dust from I_cont=B(T)(1-exp(-tau)), tau=kappa*Sigma; fit baseline power-law with exponential tail plus Gaussian gap  
  > "We derive the optical depth at 225 GHz, $\tau_{\rm 225GHz}$, using the radiative transfer equation" (4.1)
   - assumption: T_dust=T_gas=T_B,peak; kappa=2.3 cm2/g  
  > "we simply assume that the dust temperature is equal to the gas temperature" (4.1)
   - fitting: Least squares Gaussian on baseline-subtracted profile  
  > "the gap structure is fitted using a single Gaussian function" (4.1)
   - validation: _not stated_
6. **C18O column density and dust-to-CO-gas ratio**: Optical depth from Gaussian-fitted azimuthally averaged spectra (velocity-shifted by moment 1) with T_gas=T_B(13CO); column density via Yamamoto 2017 equation; N_CO=444 N_C18O  
  > "We adopt the following equation in (cite: Yamamoto2017) to derive the C$^{18}$O column density" (4.2)
   - assumption: X0=1e-4, eps0=1e-2 ISM values  
  > "We adopt the typical values in the ISM of $X_{0}=10^{-4}$ and $\epsilon_{0}=10^{-2}$" (4.3)
   - fitting: Gaussian line fitting  
  > "From the azimuthally averaged line spectra, we obtain the peak C$^{18}$O line intensity (I$_{\rm C^{18}O,peak}$) and the width ($\Delta$v$_{\rm C^{18}O}$) by Gaussian fitting." (Section 4.2 C$^{18}$O gas column density)
   - validation: _not stated_
7. **Planet-gap interpretation**: Fit Kanagawa et al. 2017 gap profile; minimum mass from Rosotti et al. 2016; upper limits from non-detection of gas gap  
  > "we evaluate the planet mass in the gap through the fitting of the observed gap structure using Equation (6)-(10) in (cite: Kanagawa2017)." (4.4.1)
   - assumption: T=22 K at gap center 91.47 au; M*=1.657 Msun; dust traces gas gap  
  > "We assume that the dust gap structure obtained from our observation can trace the gas gap structure." (4.4.1)
   - fitting: _not stated_
   - validation: _not stated_
8. **Dust-trap radiative transfer model**: HO-CHUNK Monte Carlo RT with compact dust disk (20-100 au), small and large grain populations, to get r-z temperature and 12CO/13CO photospheres  
  > "We perform the radiative transfer calculation to derive the temperature distributions in the disk $r-z$ plane" (4.4.2)
   - software: HO-CHUNK
   - assumption: n(a)∝a^-3.5; small 0.0025-0.2 um, large 0.01 um-1 mm; small surface density 10x smaller than large  
  > "The size distribution of both dust components is $n(a) \propto a^{-3.5}$" (4.4.2)
   - fitting: _not stated_
   - validation: Compared qualitatively with observed 13CO bump  
  > "This is consistent with the observed intensity bump of $^{13}$CO line around 130 au but nothing for the $^{12}$CO line." (4.4.2)

## Software

- **CASA** 5.3: Calibration, imaging, imfit, immoments  
  > "using `CASA` package version 5.3" (Observation)
- **HO-CHUNK** : Radiative transfer temperature calculation  
  > "by using a published code HO-CHUNK" (4.4.2)
- **makemask** : Keplerian rotation model/mask for channel maps  
  > "We used the python code written by Kevin Flaherty for generating the Keplerian rotation model." (Appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux density | ~0.139 | not stated | Jy | 1 | The total flux density of the dust disk is $\sim0.139$ Jy. |
| Disk inclination | 31.0 | 1.4 | deg | 2 | The estimated inclination of the disk is $31.0^{\circ}\pm1.4^{\circ}$ and disk PA is $36.2^{\circ}\pm1.8^{\circ}$. |
| Disk position angle | 36.2 | 1.8 | deg | 2 | The estimated inclination of the disk is $31.0^{\circ}\pm1.4^{\circ}$ and disk PA is $36.2^{\circ}\pm1.8^{\circ}$. |
| 13CO T_B,peak bump amplitude at ~127 au | ~4.3 (~1.4 sigma) | 1 sigma ≈ 3 K | K | 4 | has $\sim 4.3$ K amplitude, corresponding to $\sim1.4\sigma$ at this radius ($1\sigma\approx3$ K) |
| Dust gap depth | ~20 | upper limit | % | 5 | The derived gap depth is $\sim20\%$ on average. |
| Gap center (13CO case) | 91.47 | >500% | au | 5 | T$_{\rm B,peak.^{13}CO}$ / 91.47 / 6.72 / 0.038  / $\sim19.94$ |
| Minimum planet mass | ~0.2 | not stated | M_J | 7 | we obtain $M_{\rm p,min}\sim0.2~M_{\rm J}$. |
| Planet mass for gap | 0.99 (alpha/0.01)^0.5 | large | M_J | 7 | $$\begin{equation}
 M_{\rm p} = 0.99 M_{\rm J}\left(\frac{\alpha}{0.01}\right)^{0.5},
\end{equation}$$ |
| Dust-to-CO-gas ratio enhancement inside 80 au | ~50 times ISM | not stated | dimensionless | 6 | the dust-to-CO-gas mass ratio is $\sim50$ times higher than the typical ISM value. |

## Qualitative findings

- Gas disk (CO to ~240 au) is much more extended than the dust disk  
  > "They show that the gas disk of CR Cha is much extended than the dust disk." (3.1)
- Foreground absorption at ~4.5 km/s in 12CO and 13CO  
  > "There is a strong absorption feature at the velocity of $\sim4.5$ km s$^{-1}$ in the $^{12}$CO and $^{13}$CO spectra." (3.1)

## Claim tuples

- H: Does CR Cha have dust substructure? | E: Band 6 continuum imaging at ~0.06-0.09 arcsec | R: Gap at ~90 au and faint ring at ~120 au | F: Gap-ring structure detected in outer dust disk | **supported**
- H: Can a planet open the gap? | E: Fit Kanagawa et al. gap model to dust surface density | R: Mp≈0.99 MJ (alpha/0.01)^0.5 | F: About Jupiter-mass planet could explain gap, but very rough | **partially**
- H: Can dust accumulate at a gas temperature/pressure bump beyond the compact dust disk? | E: HO-CHUNK radiative transfer with compact dust disk | R: Small-grain temperature bump beyond ~90 au; 13CO traces it, 12CO does not | F: Consistent with observed 13CO bump and ring | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust sintering, secular gravitational instability and dead-zone edge are other possible origins  
  > "the dust sintering, secular gravitational instability, and the existence of the dead zone at the disk midplane also can explain the observed dust gap-ring structure" (Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Gap not resolved by beam; depth is an upper limit and uncertainties exceed 500%  
  > "The uncertainties of the fitting parameters are more than 500% for all parameters due to the small number of data points in the gap" (4.1)
- Caveat (inferred, ours): Gap fit relies on 2-3 points with beam larger than gap width
- Caveat (inferred, ours): T_dust=T_gas assumption biases surface density
- Caveat (inferred, ours): Single opacity value adopted; no exploration of dust properties
- Caveat (inferred, ours): RT model not fit to data and assumes extra outer dust

## Reproducibility

- Data public (paper): Project code given; ALMA data cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00286.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Self-cal details
- Missing: Fit initial conditions and error estimation
- Missing: HO-CHUNK input configuration
- Data volume (inferred): ~100-300 GB raw
- Score (inferred): 3/5, Data identified and analysis steps described with equations, but imaging and fitting details are incomplete.
- Rediscovery candidate: yes, Archive data public; numeric profiles and gap parameters derivable, though imaging details are missing.

## Links

- Method: (cite: Kanagawa2017) (Gap profile model for planet mass)
- Method: (cite: Rosotti2016MNRAS_459_2790R) (Minimum planet mass)
- Companion: (cite: Long2017) (Earlier ALMA CO survey of Cha I including CR Cha)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 86,
  "stated": 51,
  "rate": 0.593
 },
 "evidence_ok": true
}
```
