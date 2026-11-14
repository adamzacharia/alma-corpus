# An ALMA Multiline Survey of the Interstellar Medium of the Redshift 7.5 Quasar Host Galaxy J1342+0928

`2019ApJ...881...63N` | The Astrophysical Journal 2019 | first author: Novak, Mladen | arXiv: 1906.08569 | DOI: 10.3847/1538-4357/ab2beb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars, milky_way_ism
- Question: What are the dust continuum and the far-infrared fine-structure and molecular line properties of the ISM in the z=7.54 quasar host J1342+0928?  
  > "We use ALMA observations of the host galaxy of the quasar ULAS J1342+0928 at $z=7.54$ to study the dust continuum and far infrared lines emitted from its interstellar medium." (abstract)
- Target **ULAS J1342+0928**: coordinates 13h42m8.098s +9d28m38.35s (ICRS, 231.5 GHz continuum peak)  
  > "We have observed the quasar J1342+0928 at $z=7.5413$ with ALMA" (2.1 Observations and data reduction); "$13^{\text{h}}42^{\text{m}}8.098^{\text{s}}$ $+9^\circ28\ensuremath{'}38.35\ensuremath{''}$ (ICRS)" (3.1 The dust continuum emission); z/distance z=7.5413  
  > "We have observed the quasar J1342+0928 at $z=7.5413$ with ALMA" (2.1 Observations and data reduction); "$13^{\text{h}}42^{\text{m}}8.098^{\text{s}}$ $+9^\circ28\ensuremath{'}38.35\ensuremath{''}$ (ICRS)" (3.1 The dust continuum emission); distance from [CII] redshift from NOEMA (Venemans et al. 2017b)  
  > "We have observed the quasar J1342+0928 at $z=7.5413$ with ALMA" (2.1 Observations and data reduction); "$13^{\text{h}}42^{\text{m}}8.098^{\text{s}}$ $+9^\circ28\ensuremath{'}38.35\ensuremath{''}$ (ICRS)" (3.1 The dust continuum emission)

## Data provenance

- ALMA projects: 2017.1.00396.S
- bands: Bands 3-8, eight setups, 93.5-412 GHz  
  > "eight different frequency setups reaching an effective bandwidth of 60 GHz, located between 93.5 GHz (band 3) and 412 GHz (band 8)" (2.1 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 41-46 12 m antennas  
  > "using between 41 and 46 antennas with 12 m diameter" (2.1 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.19-1.9 arcsec depending on setup; 231.5 GHz beam 0.27x0.19  
  > "$0.27\times 0.19$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 7.5-110 uJy/beam depending on setup  
  > "| 8 | 403.9 | $0.98\times 0.59$ | 110 |" (Table 1)
- time on source: 22 to 114 min per setup  
  > "2017 Dec 26 | 114 min" (Table 1)
- observing dates: 2017 Dec 26 to 2018 Aug 24  
  > "2018 Aug 23/24" (Table 1)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- Line: [OIII] 88 um (not stated)
- Line: CO J=7-6 to 17-16 (not stated)
- Other facility **NOEMA**: [CII] redshift, line width and earlier continuum  
  > "It was followed-up with NOEMA by (cite: venemans17c)" (Introduction)
- Other facility **VLA and FIRST**: radio continuum upper limits  
  > "$3\sigma$ upper limits on the radio continuum from the Faint Images of the Radio Sky at Twenty-cm (FIRST) survey and a targeted Karl G. Jansky Very Large Array (VLA) observation" (3.1 The dust continuum emission)
- External data: [CII] redshift z=7.5413 and FWHM 380 km/s  
  > "a redshift of $z=7.5413$, and a line-width of 380 $\text{km\,s}^{-1}$ were reported, which we adopt throughout" (Introduction) [from (cite: venemans17c)]
- External data: Dust opacity kappa=2.64 m2/kg at c/125um  
  > "We adopt the opacity coefficient of $\kappa_{\nu_0}=2.64$ m$^2$ kg$^{-1}$ at $\nu_0=c/(125\,\mu\mathrm{m})$ (cite: dunne03)." (3.1 The dust continuum emission) [from (cite: dunne03)]
- External data: PDR and XDR grid models  
  > "we make use of the PDR and XDR grid models developed by (cite: meijerink05; meijerink07)" (3.3.2 Photo-dissociation regions) [from (cite: meijerink05; meijerink07)]

## Processing

### Calibration

- pipeline or manual: default calibration pipeline in CASA  
  > "The default calibration pipeline was used to process the raw data with the Common Astronomy Software Applications (CASA) package" (2.1 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA  
  > "Visibility data of various execution blocks were merged together and imaged in CASA using tclean." (2.1 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used natural weighting to maximize sensitivity in the resulting maps." (2.1 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: clean in 4 arcsec circle at phase center plus circle on foreground source 10 arcsec away, to 2 sigma  
  > "cleaning was performed inside a circle of 4$\ensuremath{''}$ diameter located at the phase center" (2.1 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using all channels excluding possible line channels  
  > "We then subtracted the continuum estimated from all channels excluding the ones where emission lines might be detected using the uvcontsub task" (2.1 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- [CII] redshift and line width adopted  
  > "we adopt the redshift and the line width values reported in (cite: venemans17c) and use them throughout." (2.1 Observations and data reduction) [from (cite: venemans17c)]
- Residual scaling flux method  
  > "This method is called the residual scaling and is outlined in appendix A.2 of (cite: jorsater95)" (Appendix A) [from (cite: jorsater95)]

### Not stated but needed to reproduce (our reading)

- Channel ranges excluded from continuum fitting
- Exact CLEAN iterations and cell/image size
- Details of CO and water stacking procedure
- Cloudy setup (deferred to Decarli et al. in prep)
- Fit procedure and uncertainty method for modified black body
- CASA version

## Analysis recipe

1. **Image cubes, continuum and moment-zero maps**: tclean, uvcontsub, moment zero over 455 km/s centred at z=7.5413  
  > "we imaged integrated emission line maps (also known as moment zero maps) over a velocity width of 455 km s$^{-1}$" (2.1 Observations and data reduction)
   - software: CASA
   - parameter: 50 km/s channels  
  > "we produced a cube with a channel width corresponding to 50 km s$^{-1}$ at the central frequency of the setup" (2.1 Observations and data reduction)
   - fitting: _not stated_
   - validation: Adjacent 455 km/s channels imaged to check continuum subtraction  
  > "in order to visually check that the continuum subtraction performed as expected" (2.1 Observations and data reduction)
2. **Measure aperture flux densities**: 2.6 arcsec diameter aperture with residual scaling; error sigma*sqrt(N)  
  > "Error estimate of the measured flux density is calculated as $\sigma\sqrt{N}$" (2.2 Measuring flux densities)
   - parameter: aperture diameter 2.6 arcsec (13 kpc)  
  > "inside an aperture with a diameter of $2.6\ensuremath{''}$, corresponding to 13 kpc" (2.2 Measuring flux densities)
   - fitting: _not stated_
   - validation: Aperture chosen where [CII] flux reaches a plateau  
  > "the flux density reaches a plateau at $r=1.3\ensuremath{''}$" (Appendix A)
3. **Fit dust SED and derive dust mass, L_IR, SFR**: Optically thin modified black body with CMB correction, T_dust fixed at 47 K  
  > "we correct for both the contrast and the CMB heating as prescribed by (cite: dacunha13)" (3.1 The dust continuum emission)
   - parameter: kappa=2.64 m2/kg at 125 um; T_dust=47 K  
  > "Fixing the dust temperature to 47 K, as is often assumed for quasar hosts in the literature (cite: beelen06)" (3.1 The dust continuum emission)
   - assumption: Optically thin dust; Kennicutt98 SFR relation with Chabrier IMF  
  > "under the assumption that the dust optical depth is small at FIR wavelengths (optically thin regime)" (3.1 The dust continuum emission)
   - fitting: _not stated_
   - validation: Temperature range 37-57 K tested  
  > "A range of temperatures[^2] between 37 and 57 K yields $\beta=1.6-2.2$" (3.1 The dust continuum emission)
4. **Line luminosities, stacking and limits**: Standard L and L' equations; 3 sigma upper limits; stack of four CO lines  
  > "Line luminosities were derived using equations given in (cite: carilliwalter13) (cite: solomon97)" (3.2 Emission lines)
   - assumption: Same FWHM as [CII] for all lines  
  > "For other lines we assume that the full width at half maximum (FWHM) remains the same" (2.1 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive ISM properties**: PDR/XDR models, line ratios, Cloudy, CO SLED scaling to gas mass, H+ mass, metallicity calibration  
  > "we make use of the PDR and XDR grid models developed by (cite: meijerink05; meijerink07)" (3.3.2 Photo-dissociation regions)
   - software: Cloudy
   - assumption: alpha_CO=0.8 Msun/(K km/s pc2)  
  > "We employ a value of $\alpha_{\text{CO}}= 0.8\,\text{M}_\ensuremath{\odot} (\ensuremath{\text{K}\,\text{km}\,\text{s}^{-1}\,\text{pc}^{2}})^{-1}$ (cite: downes98)" (3.3.4 Gas mass)
   - assumption: Cosmology H0=70, OmegaL=0.7, Om=0.3  
  > "Hubble constant of $H_0=70$ km s$^{-1}$ Mpc$^{-1}$" (Introduction)
   - fitting: _not stated_
   - validation: Several gas-mass proxies compared  
  > "In this section we constrain the total molecular gas mass of J1342+0928 employing a variety of methods. They are listed in Table [2](#tab:gasmass) and explained below." (Gas mass)

## Software

- **CASA** : pipeline calibration, tclean imaging, uvcontsub  
  > "The default calibration pipeline was used to process the raw data with the Common Astronomy Software Applications (CASA) package" (2.1 Observations and data reduction)
- **Cloudy** : line ratio modelling of ionization parameter  
  > "available with the Cloudy spectral synthesis code (cite: ferland17)" (3.3.5 Ionized gas)
- **Astropy** : acknowledged Python package  
  > "This research made use of Astropy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| dust emissivity index beta | 1.85 | 0.3 | dimensionless | 3 | results in $\beta=1.85 \pm 0.3$ |
| dust mass | 0.35e8 | 0.02e8 | Msun | 3 | $M_{\mathrm{dust}}=(0.35\pm0.02)\times10^8$ M$_\ensuremath{\odot}$ |
| L_TIR | 1.5e12 | 0.3e12 | Lsun | 3 | $L_{\mathrm{TIR}}=(1.5\pm0.3)\times10^{12}$ L$_\ensuremath{\odot}$ |
| SFR from TIR | 150 | 30 | Msun/yr | 3 | resulting in SFR of $150\pm30\,\ensuremath{\mathrm{M}_{\odot}\,\mathrm{yr}^{-1}}$ |
| [CII] line luminosity | 14.0e8 | 1.9e8 | Lsun | 4 | / \[CII\]$_{158\,\mu\mathrm{m}}$ / $1.07\pm0.15$ / $14.0\pm1.9$ / |
| [OIII]88 luminosity | 26.5e8 | 9.7e8 | Lsun | 4 | / \[OIII\]$_{88\,\mu\mathrm{m}}$ / $1.14\pm0.41$ / $26.5\pm9.7$ / |
| CO stack line flux | 0.045 | 0.013 | Jy km/s | 4 | with a line flux of $0.045\pm0.013$ $\text{Jy\,km\,s}^{-1}$ |
| electron density lower limit | >180 | not stated | cm^-3 | 5 | set a lower limit on the electron density of $n_e>180\,\text{cm}^{-3}$ |
| gas-phase metallicity | 1.3 | +0.3/-0.1 | Zsun | 5 | $Z_{\mathrm{gas}}=1.3^{+0.3}_{-0.1}\,Z_\ensuremath{\odot}$ |
| [OIII]88/[NII]122 ratio | 7.5 | 4.0 | dimensionless | 5 | $\ensuremath{\text{\rm [O\textsc{iii}]}_{88\,\mu\mathrm{m}}}/\ensuremath{\text{\rm [N\textsc{ii}]}_{122\,\mu\mathrm{m}}}=7.5\pm4.0$ |

## Qualitative findings

- [CII] arises predominantly in neutral medium; XDR ruled out  
  > "which rules out XDR as the dominant regime in J1342+0928" (3.3.2 Photo-dissociation regions)

## Claim tuples

- H: Does the host have FIR line deficits like local ULIRGs? | E: Compared line-to-FIR ratios with local LIRGs | R: Consistent within scatter | F: Line deficits agree with local ULIRGs | **supported**
- H: What are PDR densities? | E: PDR models with [CII]/CO and [CII]/[CI] limits | R: n <~5e4 cm^-3, G0 >~1e3 | F: Low density PDRs | **supported**
- H: What is the gas-to-dust ratio? | E: Gas mass from several CO and [CII] proxies | R: Ratios from ~30 to ~1200 depending on proxy | F: CO data favor <100 | **partially**
- H: Is the ISM enriched? | E: [OIII]/[NII] metallicity calibration | R: Z=1.3 Zsun | F: Solar-like metallicity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Fixed 47 K because Rayleigh-Jeans data cannot constrain temperature  
  > "the fitting parameters are degenerate and the dust SED shape and its temperature cannot be fully constrained" (3.1 The dust continuum emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust mass uncertain by at least a factor of two due to opacity  
  > "provides the dominant uncertainty on the dust mass estimate, which is at least a factor of two" (3.1 The dust continuum emission)
- Limitation (authors): Low S/N prevents line profile fitting  
  > "Because of the low S/N of all lines except the $\text{[C\textsc{ii}]}_{158\,\mu\text{m}}$, we only analyze the integrated spectrum moment zero maps" (3.2 Emission lines)
- Caveat (inferred, ours): Dust temperature fixed, so beta and mass model-dependent
- Caveat (inferred, ours): Fixed line width for all lines may bias weak line fluxes
- Caveat (inferred, ours): Many results are limits; gas-mass conclusions depend on assumed CO SLEDs and alpha_CO

## Reproducibility

- Data public (paper): Program ID given; no explicit public statement  
  > "(program ID: 2017.1.00396.S, PI: Bañados)" (2.1 Observations and data reduction)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Line-free channels and cell/image size
- Missing: Cloudy setup
- Missing: SED fit details
- Data volume (inferred): ~100-300 GB raw across eight setups
- Score (inferred): 3/5, Recipe mostly described and results numeric, but imaging parameters and fit details are missing.
- Rediscovery candidate: no, Data are public, but key imaging and modelling details are missing and many results are limits.

## Links

- Method: (cite: jorsater95) (residual scaling flux method)
- Method: (cite: dacunha13) (CMB correction for dust SED)
- Companion: (cite: venemans17c) (NOEMA [CII] and continuum)
- Companion: Bañados et al., in prep. (high-resolution [CII] morphology)

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 46,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
