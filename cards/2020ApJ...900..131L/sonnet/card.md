# Ionized and Atomic Interstellar Medium in the z = 6.003 Quasar SDSS J2310+1855

`2020ApJ...900..131L` | The Astrophysical Journal 2020 | first author: Li, Jianan | arXiv: 2007.12339 | DOI: 10.3847/1538-4357/ababac

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the physical conditions of the ionized and atomic ISM in the z=6.003 quasar J2310+1855, and is there an imprint of AGN heating, as probed by [N II] 122um and [O I] 146um together with [C II] and [O III]?  
  > "To probe the gas physical conditions and search for imprints of active galactic nuclei (AGN) on the ISM, we report ALMA observations" (abstract)
- Target **SDSS J231038.88+185519.7 (J2310+1855)**: coordinates _not stated_; z/distance z = 6.003; D_L = 57.8 Gpc (H0=70, Om=0.3)  
  > "1$''$ corresponds to 5.7 kpc at the redshift of J2310+1855 and the luminosity distance to the quasar is 57.8 Gpc." (Introduction); distance from Redshift from [C II] (Wang et al. 2013); LambdaCDM cosmology  
  > "1$''$ corresponds to 5.7 kpc at the redshift of J2310+1855 and the luminosity distance to the quasar is 57.8 Gpc." (Introduction)

## Data provenance

- ALMA projects: 2015.1.01265.S
- bands: _not stated_
- frequencies and spectral setup: [O I] spw centered 294.1653 GHz; [N II] spw centered 351.1845 GHz; one 1.875 GHz line spw plus three continuum spws each  
  > "We set one of the four 1.875 GHz spectral windows centered on the redshifted \[O I\]$_{\rm 146 \mu m}$ line at 294.1653 GHz" (2 Observations); "We tuned one 1.875 GHz width spectral window centered at the redshifted \[N II\]$_{\rm 122 \mu m}$ frequency, 351.1845 GHz" (2 Observations)
- continuum bandwidth: continuum averaged over 281.2-295.2 and 336.2-352.2 GHz in line-free regions  
  > "By averaging the data over 281.2 (336.2) and 295.2 (352.2) GHz in the regions free of line emission" (2 Observations)
- arrays: _not stated_
- configurations: C36-3 ([O I]); C36-2 ([N II])  
  > "The array configuration was C36-3, where the number of antennas used was 36–38" (2 Observations); "we observed the \[N II\]$_{\rm 122 \mu m}$ line in the C36-2 configuration" (2 Observations)
- baselines: 15-539 m ([O I]); 15-377 m ([N II])  
  > "the baseline lengths were between 15 and 377 m" (2 Observations)
- angular resolution: 0.56"x0.46" ([N II]); 0.47"x0.39" ([O I])  
  > "The synthesized beam sizes were $0.56\ensuremath{''}$ $\times$ $0.46\ensuremath{''}$ and $0.47\ensuremath{''}$ $\times$ $0.39\ensuremath{''}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: line rms 0.20 mJy/beam (16 MHz chan, [O I]); 0.23 mJy/beam (94 MHz chan, [N II]); continuum 25 uJy/beam at 289.2 GHz, 49 uJy/beam at 344.2 GHz  
  > "we find a continuum sensitivity of 25 (49) $\rm \mu Jy\ beam^{-1}$ at 289.2 (344.2) GHz from our observations." (2 Observations)
- time on source: 73.4 min ([O I]); 67.8 min ([N II])  
  > "with a total observing time of 73.4 minutes on source" (2 Observations); "with a total observing time of 67.8 minutes on source" (2 Observations)
- observing dates: [O I]: 2016 Apr 14 and Nov 22; [N II]: 2016 Apr 9 and Jun 16  
  > "The \[O I\]$_{\rm 146 \mu m}$ line was observed on 2016 April 14 and November 22" (2 Observations)
- pi or archival as stated: _not stated_
- Line: [O I] 146 um (2060.0690 GHz)
- Line: [N II] 122 um (2459.3801 GHz)
- External data: [C II] 158um spectrum, flux, width, size, redshift  
  > "together with the \[C II\]$_{\rm 158 \mu m}$ spectrum from (cite: wang13)" (3 Results) [from (cite: wang13)]
- External data: [O III] 88um spectrum and luminosity 2.44e9 Lsun  
  > "Adopting an \[O III\]$_{\rm 88 \mu m}$ luminosity of $2.44 \times 10^{9}$ $\rm L_{\ensuremath{\odot}}$ (cite: hashimoto18)" (4.1 Properties of J2310+1855) [from (cite: hashimoto18)]
- External data: L_FIR = (1.03±0.22)e13 Lsun; Tdust=40 K, beta=1.6; CO(2-1) molecular gas mass  
  > "We adopt the J2310+1855 FIR luminosity of $L_{\rm FIR} = (1.03 \pm 0.22) \times 10^{13}$ $\rm L_{\ensuremath{\odot}}$ from (cite: shao19)." (4.2 Line-to-FIR luminosity ratios) [from (cite: shao19)]
- External data: Gas temperature 228 K from CO SLED  
  > "adopting a gas temperature of $T_{\rm kin} = 228 \ \rm K$ derived from the CO spectral line energy distribution (SLED) (cite: li20)" (4.1 Properties of J2310+1855) [from (cite: li20)]
- External data: Solar abundances of N, O, C  
  > "Adopting a solar nitrogen abundance $\chi (\rm N^{+})\lesssim N/H = 6.76 \times 10^{-5}$ from (cite: asplund09)" (4.1 Properties of J2310+1855) [from (cite: asplund09)]
- External data: Local and high-z comparison samples of line/FIR ratios  
  > "The comparison samples include samples of local dwarf galaxies, (U)LIRGs, and AGNs" (4.2 Line-to-FIR luminosity ratios) [from (cite: farrah13; cormier15; spinoglio15; rosenberg15; diaz17; herrera18a)]
- External data: Cloudy model grid of metallicity vs [O III]/[N II] (Table A1)  
  > "From the grid presented in Table A1 of (cite: pereira17)" (4.4 Gas-phase Metallicity) [from (cite: pereira17)]
- Simulation/model as data: Cloudy H II region model predictions of [C II]/[N II]205 and [N II]122/[N II]205  
  > "ratios in the H II region predicted by the radiative transfer code Cloudy (cite: ferland17)" (4.3 [C II] from the ionized gas)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "following the standard ALMA pipeline" (2 Observations)
- casa version: CASA 4.7.0  
  > "version 4.7.0 (cite: casa07)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2253+1608 ([O I] bandpass+flux); Pallas ([N II] flux)  
  > "The bandpass and flux calibrator was J2253+1608." (2 Observations); "and the flux calibrator was Pallas." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "We imaged the data using the CLEAN task in CASA with natural weighting." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We imaged the data using the CLEAN task in CASA with natural weighting." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB, first-order polynomial  
  > "through subtracting a first-order polynomial continuum from the original datacube" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: [O I] binned to 16 MHz (16 km/s); [N II] to 94 MHz (80 km/s)  
  > "We finally binned the \[O I\]$_{\rm 146 \mu m}$ datacube to 16 MHz (16 km $\rm s^{-1}$) wide channels" (2 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Ionized gas mass method from [N II]/[O III]  
  > "We follow the method in (cite: ferkinhoff11) to estimate the ionized gas mass" (4.1 Properties of J2310+1855) [from (cite: ferkinhoff11)]
- C+ and O mass formulae  
  > "the singly ionized carbon mass ((cite: weiss05); (cite: venemans17b))" (4.1 Properties of J2310+1855) [from (cite: weiss05); (cite: venemans17b)]
- SFR from line luminosities  
  > "We estimate the SFR based on the FS emission lines using Eq. 6 of (cite: farrah13)" (4.1 Properties of J2310+1855) [from (cite: farrah13)]
- [N II]205 estimates from FIR color relations  
  > "(Eq. 1 from (cite: zhao16))" (4.3 [C II] from the ionized gas) [from (cite: zhao16); (cite: lu15)]
- Sigma_FIR definition and ionization parameter method  
  > "we calculate $\Sigma_{\rm FIR}$ following the definition of (cite: herrera18a) and (cite: diaz17)" (4.2 Line-to-FIR luminosity ratios) [from (cite: herrera18a); (cite: diaz17); (cite: rigopoulou18)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters: niter, threshold, masks, cell and image size
- Line-free channels used for UVCONTSUB
- Exact aperture centering and Gaussian fit details (priors, errors)
- Flux calibrator model and flux scale uncertainty
- Method for deriving Sigma_FIR for high-z objects (sizes, L_FIR used)
- Cloudy model parameters used to infer density and C II fraction
- Whether continuum from the three line-free spws was jointly imaged

## Analysis recipe

1. **Calibrate and image data**: Standard ALMA pipeline in CASA 4.7.0; CLEAN with natural weighting; UVCONTSUB first-order; binning  
  > "We reduced the ALMA data with the Common Astronomy Software Applications (CASA) software package version 4.7.0 (cite: casa07), following the standard ALMA pipeline." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line flux, width and size**: Extract spectrum in 0.8" radius circular aperture; single Gaussian with center fixed to [C II] redshift; 2D Gaussian fit to intensity maps  
  > "we measure the flux and width by fitting a single Gaussian profile to the spectrum while the line center is fixed to that of the \[C II\]$_{\rm 158 \mu m}$ redshift" (3 Results)
   - parameter: aperture radius 0.8"  
  > "extracted within a circular aperture with a radius of $0.8\ensuremath{''}$ centered at the peak spaxel" (3 Results)
   - fitting: Single Gaussian; flux uncertainty is statistical fit error  
  > "the flux uncertainty is the statistical error from the Gaussian fit" (Table 1)
   - validation: Flux from clipping all line channels consistent with Gaussian fit  
  > "the line flux measured from clipping all the line emitting channels is consistent with that from a single Gaussian profile fitting" (3 Results)
3. **Derive ionized and neutral gas masses and SFR**: Minimum ionized mass from [N II] and [O III] LTE formula; C+ and O mass from [C II] and [O I]; SFR via Farrah et al. relations  
  > "The minimum ionized gas mass traced by singly ionized nitrogen is:" (4.1 Properties of J2310+1855)
   - parameter: T_ex = T_kin = 228 K  
  > "adopting a gas temperature of $T_{\rm kin} = 228 \ \rm K$" (4.1 Properties of J2310+1855)
   - assumption: Solar abundances (Asplund09); LTE  
  > "Assuming LTE where $T_{\rm kin} \approx T_{\rm ex}$" (4.1 Properties of J2310+1855)
   - fitting: _not stated_
   - validation: Compared with CO(2-1) molecular gas mass and dust-continuum SFR  
  > "The SFRs traced by both the dust continuum and the \[C II\]$_{\rm 158 \mu m}$, \[N II\]$_{\rm 122 \mu m}$ and \[O III\]$_{\rm 88 \mu m}$ FIR FS lines are consistent" (4.1 Properties of J2310+1855)
4. **Compare line/FIR ratios with local and high-z samples**: L_line/L_FIR vs L_FIR and Sigma_FIR  
  > "by studying the line-to-FIR ratio as a function of FIR luminosity ($L_{\rm FIR}$), and as a function of FIR surface brightness ($\Sigma_{\rm FIR}$)" (4.2 Line-to-FIR luminosity ratios)
   - fitting: _not stated_
   - validation: _not stated_
5. **Ionized density and [C II] ionized fraction**: Estimate [N II]205 from FIR color relations, compare [N II]122/205 with Cloudy to get density, then derive [C II] ionized fraction  
  > "we estimate that the ionized gas density is 45 $\rm cm^{-3}$ in J2310+1855" (4.3 [C II] from the ionized gas)
   - software: Cloudy
   - parameter: Tdust=40 K, beta=1.6  
  > "Adopting a dust temperature of 40 K and an emissivity index $\beta=1.6$ from (cite: shao19)" (4.3 [C II] from the ionized gas)
   - assumption: No significant XDR contribution to [N II]122  
  > "which disfavors a significant contribution of the \[N II\]$_{\rm 122 \mu m}$ emission from XDRs" (4.3 [C II] from the ionized gas)
   - fitting: _not stated_
   - validation: _not stated_
6. **Metallicity and diagnostic diagrams**: Continuum 88/122 um ratio gives log U; [O III]/[N II] with Pereira-Santaella grid gives Z  
  > "corresponds to a metallicity of $Z/Z_{\ensuremath{\odot}}$=1.5$-$2.1" (4.4 Gas-phase Metallicity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: data reduction, CLEAN imaging, UVCONTSUB  
  > "version 4.7.0 (cite: casa07)" (2 Observations)
- **Cloudy** : HII region models for [N II] ratios (from Ferland17); metallicity grids from literature  
  > "predicted by the radiative transfer code Cloudy (cite: ferland17)" (4.3 [C II] from the ionized gas)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [N II]122 line flux | 0.72 | 0.20 | Jy km/s | 2 | The measured fluxes are 0.72 $\pm$ 0.20 and 1.25 $\pm$ 0.08 Jy $\rm km\ s^{-1}$ |
| [O I]146 line flux | 1.25 | 0.08 | Jy km/s | 2 | The measured fluxes are 0.72 $\pm$ 0.20 and 1.25 $\pm$ 0.08 Jy $\rm km\ s^{-1}$ |
| [N II]122 FWHM | 328 | 58 | km/s | 2 | The resulting line widths of 328 $\pm$ 58 and 376 $\pm$ 16 km s$^{-1}$ in FWHM |
| [O I]146 FWHM | 376 | 16 | km/s | 2 | The resulting line widths of 328 $\pm$ 58 and 376 $\pm$ 16 km s$^{-1}$ in FWHM |
| Continuum flux density at 344.2 GHz | 14.94 | 0.08 | mJy | 2 | / 344.2 / 14.94 $\pm$ 0.08 / 49 / |
| Continuum flux density at 289.2 GHz | 11.76 | 0.04 | mJy | 2 | / 289.2 / 11.76 $\pm$ 0.04 / 25 / |
| Minimum ionized gas mass from [N II] | 6.2e8 | not stated | Msun | 3 | we derive a minimum ionized gas mass of $M^{min}_{ionized}= 6.2 \times 10^{8}$ |
| Minimum neutral gas mass from [C II] | 7.8e10 | not stated | Msun | 3 | we constrain the minimum atomic gas mass of $M^{min}_{neutral}= 7.8 \times 10^{10} \rm \ M_{\ensuremath{\odot}}$ |
| Minimum neutral gas mass from [O I] | 1.7e10 | not stated | Msun | 3 | which leads to $M^{min}_{neutral}= 1.7 \times 10^{10} \rm \ M_{\ensuremath{\odot}}$ |
| Ionized gas density | >=45 | not stated | cm^-3 | 5 | we estimate that the ionized gas density is 45 $\rm cm^{-3}$ in J2310+1855 |
| [C II] fraction from ionized gas | <=17 | not stated | % | 5 | we derive an ionized gas contribution of $\lesssim$17$\%$ to the \[C II\]$_{\rm 158 \mu m}$ line |
| Metallicity | 1.5-2.1 | not stated | Z/Zsun | 6 | corresponds to a metallicity of $Z/Z_{\ensuremath{\odot}}$=1.5$-$2.1 |
| [C II]/[O I]146 ratio | 6.5 | not stated | dimensionless | 6 | J2310+1855 exhibits a $L_{\rm [CII]_{158\mu m}}/ L_{\rm [OI]_{146\mu m}}$ ratio of 6.5 |
| [O III]/[O I]146 ratio | 1.9 | not stated | dimensionless | 6 | J2310+1855 exhibits a $L_{\rm [OIII]_{88\mu m}}/ L_{\rm [OI]_{146\mu m}}$ ratio of 1.9 |
| [O III]/[N II]122 ratio | 2.8 | not stated | dimensionless | 6 | the observed \[O III\]$_{\rm 88 \mu m}$/\[N II\]$_{\rm 122 \mu m}$ ratio of 2.8 |
| SFRs from [C II], [O I], [N II], [O III] | 1524, 11917, 2208, 1058 | 1.8 to 2.6 dex statistical | Msun/yr | 3 | are 1524, 11917, 2208, and 1058 $\rm M_{\ensuremath{\odot}}\ yr^{-1}$, respectively. |

## Qualitative findings

- [O I]146 shows no line deficit; [C II], [N II], [O III] show deficits similar to local systems  
  > "the \[O I\]$_{\rm 146 \mu m}$ line has a line-to-FIR flux ratio more than two times higher than that found in local galaxies" (5 Summary)

## Claim tuples

- H: Is there warm, dense neutral gas heated by the AGN in J2310+1855? | E: Compared [C II]/[O I]146 and [O I]/FIR with local and high-z samples | R: [C II]/[O I]=6.5, among lowest local AGN values; [O I]/FIR >2x local | F: Warm dense gas likely heated by the AGN | **supported**
- H: What fraction of [C II] arises in ionized gas? | E: Estimated [N II]205 and compared [N II]122/205 with Cloudy models | R: n_e >~45 cm^-3; <=17% of [C II] from ionized gas | F: [C II] dominantly neutral | **supported**
- H: What is the gas metallicity? | E: Used [O III]/[N II] ratio with Cloudy grid and estimated U | R: Z/Zsun=1.5-2.1 | F: Supersolar metallicity, with caveats about AGN and dust opacity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): SFR from [O I] unreliable; relations have large uncertainties and are extrapolated; dust opacity and XDR contribution may bias metallicity and [N II] results  
  > "The error bars of the parameters in the above relations are large, which result in large uncertainties in the SFR estimation." (4.1 Properties of J2310+1855)
- Caveat (inferred, ours): [N II]205 is not observed; density and C II fraction rely on indirect scaling relations from local ULIRGs
- Caveat (inferred, ours): Possible XDR/AGN contribution to [N II]122 undermines metallicity
- Caveat (inferred, ours): Lines are partly absorbed or contaminated by the absorption-like feature, so Gaussian fit errors may be off
- Caveat (inferred, ours): Comparison samples are galaxy-scale vs nuclear regions here

## Reproducibility

- Data public (paper): ALMA Cycle 3 program 2015.1.01265.S cited; public status not stated  
  > "This paper is based on ALMA observations: ADS/JAO.ALMA 2015.1.01265.S." (acknowledgement)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: line-free channel ranges
- Missing: comparison sample data tables (provided privately by authors)
- Missing: Cloudy model setups
- Data volume (inferred): ~ tens of GB raw (two Band 7 tunings, few hours)
- Score (inferred): 3/5, Data and main steps identified, but imaging details and external comparison data/models are missing.
- Rediscovery candidate: no, Line fluxes are reproducible from public data, but the derived physical conclusions depend on external literature data and models not provided.

## Links

- Method: (cite: ferkinhoff11) (ionized gas mass method)
- Method: (cite: farrah13) (SFR-line luminosity relations)
- Method: (cite: rigopoulou18) (ionization parameter from continuum ratio)
- Method: (cite: pereira17) (metallicity grid)
- Companion: (cite: li20) (CO SLED of the same quasar)
- Companion: (cite: wang13) ([C II] observations)
- Companion: (cite: hashimoto18) ([O III] observations)
- Companion: (cite: shao19) (dust continuum, FIR luminosity, CO(2-1))

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
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 50,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
