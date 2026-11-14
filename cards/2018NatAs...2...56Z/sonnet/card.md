# A dusty star-forming galaxy at z = 6 revealed by strong gravitational lensing

`2018NatAs...2...56Z` | Nature Astronomy 2018 | first author: Zavala, Jorge A. | arXiv: 1707.09022 | DOI: 10.1038/s41550-017-0297-8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Nature of a lensed dusty star-forming galaxy at z=6.027 (G09 83808): its intrinsic SFR, gas and dust properties, and [CII] deficit compared with local ULIRGs and SMGs  
  > "Here we report the spectroscopic identification of a gravitationally amplified ($\mu=9.3\pm1.0$) dusty star-forming galaxy at $z=6.027$." (abstract)
- Target **G09 83808 (HATLAS J090045.4+004125)**: coordinates RA 09h00m45.8s, Dec +00d41m23s  
  > "HATLAS J090045.4+004125 ($\alpha=09^\text{h}00^\text{m}45.8$, $\delta=+00^\circ41'23''$; hereafter G09 83808, since it was detected in the GAMA 09hrs field)" (main text); "The redshift of both sources is fixed at $z=0.776$ (based on X-Shooter/VLT observations(cite: fudamoto17)) and $z=6.027$, respectively." (Lensing model); z/distance z=6.027 (lens z=0.776)  
  > "HATLAS J090045.4+004125 ($\alpha=09^\text{h}00^\text{m}45.8$, $\delta=+00^\circ41'23''$; hereafter G09 83808, since it was detected in the GAMA 09hrs field)" (main text); "The redshift of both sources is fixed at $z=0.776$ (based on X-Shooter/VLT observations(cite: fudamoto17)) and $z=6.027$, respectively." (Lensing model); distance from LMT/RSR CO and H2O lines; lens redshift from X-Shooter/VLT  
  > "HATLAS J090045.4+004125 ($\alpha=09^\text{h}00^\text{m}45.8$, $\delta=+00^\circ41'23''$; hereafter G09 83808, since it was detected in the GAMA 09hrs field)" (main text); "The redshift of both sources is fixed at $z=0.776$ (based on X-Shooter/VLT observations(cite: fudamoto17)) and $z=6.027$, respectively." (Lensing model)

## Data provenance

- ALMA projects: 2013.1.00001.S
- bands: 870 um (~890 um in main text) continuum  
  > "The ALMA high-resolution $870 \, {\rm \mu m}$ observations used in this work" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: [335.49-339.49] GHz and [347.49-351.49] GHz  
  > "The default continuum spectral configuration was used, covering $[335.49 - 339.49]\, {\rm GHz}$ and $[347.49 - 351.49]\,{\rm GHz}$." (Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 1.6 km  
  > "when the array was in a relatively extended configuration with baselines up to $1.6 \, {\rm km}$" (Observations and data reduction)
- angular resolution: ~0.12 arcsec beam (0.24x0.13 arcsec in main text)  
  > "The beam size is then $\sim 0.12^{''}$" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.1 mJy/beam  
  > "the continuum sensitivity is ${\rm r.m.s.} \sim 0.1 \, {\rm mJy \, beam^{-1}}$" (Observations and data reduction)
- time on source: _not stated_
- observing dates: 31 August 2015  
  > "taken on 31 August 2015" (Observations and data reduction)
- pi or archival as stated: PI Rob Ivison, project 2013.1.00001.S  
  > "project 2013.1.00001.S, PI Rob Ivison" (Observations and data reduction)
- Line: [NII] 122 um (serendipitous, not detected) (not stated)
- Other facility **LMT (AzTEC, RSR)**: 1.1 mm continuum 20.0±1.0 mJy; 3 mm spectrum with CO(6-5), CO(5-4), H2O lines giving z=6.0269  
  > "G09 83808 was detected with a S/N $\approx20$ with a flux density of $S_{1.1\rm mm}=20.0\pm1.0$ mJy." (LMT observations)
- Other facility **SMA**: [CII] detection at 270.35 GHz and continuum 21.5±3 mJy  
  > "We measured the continuum flux density of the source to be $21.5\pm3$ mJy, in very good agreement with the AzTEC photometry." (SMA observations)
- External data: Herschel 250/350/500 um and SCUBA-2 850 um flux densities  
  > "The flux densities at 250, 350, 500, and 850 $\mu\rm m$ were taken from ref.(cite: ref12)" (Table 1) [from Ivison et al. 2016 (cite: ref12)]
- External data: CO line brightness ratios L'CO(5-4)/L'CO(1-0)=0.32±0.05 and L'CO(6-5)/L'CO(1-0)=0.21±0.04 from lower-z SMGs  
  > "$\rm L'_{CO(5-4)}/L'_{CO(1-0)}=0.32\pm0.05$, $\rm L'_{CO(6-5)}/L'_{CO(1-0)}=0.21\pm0.04$" (CO(1-0) line luminosity and molecular gas mass) [from Bothwell et al. 2013 (cite: ref28)]
- External data: Lens redshift z=0.776 from X-Shooter/VLT  
  > "The redshift of both sources is fixed at $z=0.776$ (based on X-Shooter/VLT observations(cite: fudamoto17))" (Lensing model) [from Fudamoto et al. 2017 (cite: fudamoto17)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, no further manual flagging  
  > "The data were calibrated using the ALMA pipeline, with no further manual flagging required." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The calibrated visibilities were imaged by using Briggs weighting with robust = 0.5" (Observations and data reduction)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lens modelling code and details (visilens)  
  > "The lens model was created using the publicly-available `visilens` code(cite: ref14); details of the code are given in that work." (Lensing model) [from Spilker et al. 2016 (cite: ref14)]
- LMT/RSR flux conversion and cross-correlation redshift analysis  
  > "A cross-correlation template analysis(cite: ref31) also identifies this redshift as the best solution with a S/N $=9.1$." (LMT observations) [from Yun et al. 2015 (cite: ref31)]

### Not stated but needed to reproduce (our reading)

- CASA/pipeline version for ALMA data
- Image size and cell size, deconvolver, masking
- visilens priors, MCMC settings, and burn-in
- Data-weight rescaling details
- SED fit priors and photometric errors treatment
- Cosmology adopted for luminosity distance

## Analysis recipe

1. **Lens modelling of ALMA continuum**: Fit SIE lens plus single elliptical Sersic source directly to uv visibilities with MCMC using visilens, allowing antenna phase errors  
  > "the lens mass profile is parameterized as a Singular Isothermal Ellipsoid, and the background source is modeled with a single elliptical Sérsic profile." (Lensing model)
   - software: visilens
   - parameter: lens z=0.776, source z=6.027 fixed  
  > "The redshift of both sources is fixed at $z=0.776$" (Lensing model)
   - fitting: MCMC sampling of lens and source parameters; model inverted to visibilities  
  > "The parameter space is explored using a Markov Chain Monte Carlo sampling method" (Lensing model)
   - validation: Additional source component not statistically motivated; residuals ~4 sigma; antenna phase shifts <10 deg  
  > "We have verified that an additional background source component is not statistically motivated." (Lensing model)
2. **SED fitting for LIR, SFR, Td, Md**: chi2 fit of galaxy templates (best Arp220), modified blackbody with fixed beta and nu0, dust mass from 850um kappa; MAGPHYS cross-check  
  > "We fit different galaxy SED templates to the photometry of G09 83808 through a $\chi^2$ minimization method." (SED fitting and dust properties)
   - software: MAGPHYS
   - parameter: beta=1.8 (1.5 alternative); nu0=c/100 um  
  > "the emissivity index is fixed (previous observational works suggest $\beta=1.5-2$; refs.(cite: ref44; ref45; ref46)), as well as $\nu_0=c/100\rm\ \mu m$" (SED fitting and dust properties)
   - assumption: kappa_d(850um)=0.07 m2/kg, isothermal dust, Chabrier IMF with Kennicutt 1998 SFR  
  > "Assuming normalization of $\kappa_{\rm d}(850\mu{\rm m})=0.07$ m$^2$ kg$^{-1}$ (ref.(cite: james2002))" (SED fitting and dust properties)
   - fitting: _not stated_
   - validation: Compared with SMG template and MAGPHYS results  
  > "We also fit the observerd photometry with the MAGPHYS(cite: cunha15) SED modelling code finding consistent results" (SED fitting and dust properties)
3. **Line luminosities**: Gaussian fits, L' from Solomon & Vanden Bout relation, Monte Carlo errors  
  > "The integrated flux, $S_{CO}\Delta V$, is calculated as the integral of the best-fit Gaussian distribution" (Spectral line properties)
   - fitting: _not stated_
   - validation: _not stated_
4. **Molecular gas mass, dynamical mass, gas fraction**: M(H2)=alpha L'CO(1-0) with L'CO(1-0) extrapolated from CO(5-4), (6-5); isotropic virial Mdyn  
  > "Using the former value and $\alpha=0.8\rm\ M_\odot\ (K\ km\ s^{-1}\ pc^{-2})^{-1}$" (CO(1-0) line luminosity and molecular gas mass)
   - parameter: FWHM=400 km/s, R1/2~0.6 kpc  
  > "which has been assumed to be 400 km/s (as the average between the CO and \[CII\] lines)" (Dynamical mass and gas mass fraction)
   - assumption: alpha=0.8 for starbursts  
  > "which is appropriate for starburst galaxies(cite: ref51)" (CO(1-0) line luminosity and molecular gas mass)
   - fitting: _not stated_
   - validation: Cross-check with Rayleigh-Jeans dust method gives consistent L'CO(1-0)  
  > "we obtain a consistent line luminosity of $\rm 1\pm0.1\times10^{10}\ K\ km\ s^{-1}\ pc^{-2}$" (CO(1-0) line luminosity and molecular gas mass)

## Software

- **visilens** : lens modelling in uv plane  
  > "The lens model was created using the publicly-available `visilens` code(cite: ref14)" (Lensing model)
- **MIRIAD** : SMA imaging (uvaver, uvlin, invert, clean)  
  > "The calibrated visibilities were exported to the MIRIAD software package for imaging and deconvolution." (SMA observations)
- **MIR** : SMA calibration  
  > "All of the basic calibration steps were performed using standard procedures in the MIR software package." (SMA observations)
- **MAGPHYS** : SED modelling cross-check  
  > "We also fit the observerd photometry with the MAGPHYS(cite: cunha15) SED modelling code" (SED fitting and dust properties)
- **DREAMPY** : LMT RSR data reduction  
  > "Data reduction was performed using the Data Reduction and Analysis Methods in Python (DREAMPY)." (LMT observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Magnification at 890 um | 9.3 | 1.0 | dimensionless | 1 | The best-fit magnification of the source is $\mu_\mathrm{890\mu m} = 9.3 \pm 1.0$ |
| Intrinsic half-light radius | 0.6 | 0.1 | kpc | 1 | half-light radius $0.10 \pm 0.01$” ($=0.6\pm0.1$ kpc) |
| Intrinsic 890um flux density | 4.3 | 0.5 | mJy | 1 | intrinsic flux density $S_\mathrm{890\ \mu\rm m} = 4.3 \pm 0.5$ mJy |
| LIR (8-1000 um) | 3.8e12 | 0.5e12 | Lsun | 2 | we derive an IR ($8-1000\mu\rm m$) luminosity of $3.8\pm0.5\times10^{12}\rm\ L_\odot$ |
| SFR (Chabrier) | 380 | 50 | Msun/yr | 2 | SFR) of $380\pm50\rm\ M_\odot\ yr^{-1}$ |
| Dust temperature (beta=1.8) | 49 | 3 | K | 2 | we derive $T_d=49\pm3\rm\ K$ for $\beta=1.8$ |
| Dust mass | 1.9e8 | 0.4e8 | Msun | 2 | we estimate a dust mass of $\rm M_d=1.9\pm0.4\times10^8\ M_\odot$ |
| Molecular gas mass | 1.6e10 | 0.6e10 | Msun | 4 | we derive a molecular mass of $\rm M(H_2)=1.6\pm0.6\times10^{10}\rm\ M_\odot$ |
| Dynamical mass | 2.6e10 | not stated | Msun | 4 | This results in a dynamical mass of $M_{\rm dyn}=2.6\times10^{10}\rm\ M_\odot$. |
| [CII] luminosity | 1.3e9 | 0.4e9 | Lsun | 3 | The luminosity of the \[CII\] ionized carbon line detected with the SMA is $1.3\pm0.4\times10^{9}\rm\ L_\odot$ |
| Redshift | 6.0269 | 0.0006 | dimensionless | 0 | we unambiguously determine the galaxy redshift to be $z=6.0269\pm0.0006$ |

## Qualitative findings

- The [CII]/FIR ratio follows the local LIRG [CII] deficiency trend, extending it to z=6  
  > "our source follows the same \[CII\] deficiency trend measured for local LIRGS(cite: ref30) extending it to $\rm L_{FIR}\gtrsim 10^{12}\ L_\odot$ and up to $z=6$." (main text)

## Claim tuples

- H: Is G09 83808 a lensed, less extreme dusty starburst at z=6? | E: ALMA uv-plane lens modelling plus SED fitting | R: mu=9.3±1.0; intrinsic SFR 380±50 Msun/yr | F: A ULIRG-like galaxy exists at z=6, less extreme than HFLS3-type SMGs | **supported**
- H: Do gas and dust properties and star-formation efficiency match local ULIRGs? | E: CO-based gas mass, L'CO-LIR relation, gas-to-dust ratio | R: M(H2)=1.6e10 Msun; GDR 80±30; similar SFE | F: Local trends extend to z=6 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Additional background source component in lens model rejected as not statistically motivated  
  > "We have verified that an additional background source component is not statistically motivated." (Lensing model)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust opacity uncertainty at least a factor of 3 not included  
  > "These calculations do not include the uncertainties of the dust mass absorption coefficient, which could be at least a factor of 3" (SED fitting and dust properties)
- Caveat (inferred, ours): CO(1-0) extrapolated from high-J lines with large scatter
- Caveat (inferred, ours): alpha_CO assumption drives gas mass and fgas
- Caveat (inferred, ours): Single-component Sersic lens model with 4 sigma residuals
- Caveat (inferred, ours): Single source, so conclusions on population are limited

## Reproducibility

- Data public (paper): ALMA project 2013.1.00001.S is named; the authors' own datasets are available on request  
  > "The datasets generated and analysed during this study are available from the corresponding author on reasonable request." (Methods)
- Products in archive: _not stated_
- Missing: visilens priors and MCMC settings
- Missing: imaging cell and image size
- Missing: LMT and SMA reduced data only on request
- Data volume (inferred): ~10-50 GB for ALMA band 7 continuum
- Score (inferred): 3/5, ALMA data are archival and lens model code is public, but many settings are missing and the LMT and SMA data are on request only.
- Rediscovery candidate: no, Key results depend on non-public LMT and SMA data and on unstated settings, though the ALMA lens model is repeatable.

## Links

- Method: Spilker et al. 2016 (cite: ref14) (visilens lens modelling code)
- Companion: Oteo et al. 2017 (cite: oteo17) (Same ALMA project 2013.1.00001.S)
- Related: H-ATLAS 500 um risers
- Related: HerMES

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 42,
  "rate": 0.56
 },
 "evidence_ok": true
}
```
