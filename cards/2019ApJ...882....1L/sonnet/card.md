# CO and Fine-structure Lines Reveal Low Metallicity in a Stellar-mass-rich Galaxy at z ∼ 1?

`2019ApJ...882....1L` | The Astrophysical Journal 2019 | first author: Lamarche, C. | arXiv: 1907.08633 | DOI: 10.3847/1538-4357/ab3389

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Is the CO-faint, star-forming FR-II galaxy 3C 368 (z=1.131) low-metallicity, and what is its molecular gas mass from CO(4-3), [CI] and dust?  
  > "Here we investigate one such CO-dark galaxy, 3C 368 (cite: Evans1996; Lamarche2017), which has an appreciable star-formation rate and seemingly very little molecular gas." (Introduction)
- Target **3C 368**: coordinates RA 18h05m06.40s, Dec +11d01m33.09s (J2000)  
  > "| z | 1.131 | (cite: Meisenheimer1992) |" (Table 2); "| R.A. (J2000) | 18$^h$05$^m$06$^s$.40 | (cite: Best1998) |" (Table 2); z/distance z = 1.131; D_L = 7,735 Mpc  
  > "| z | 1.131 | (cite: Meisenheimer1992) |" (Table 2); "| R.A. (J2000) | 18$^h$05$^m$06$^s$.40 | (cite: Best1998) |" (Table 2); distance from z from Meisenheimer & Hippelein 1992; flat LCDM H0=71, Om=0.27  
  > "| z | 1.131 | (cite: Meisenheimer1992) |" (Table 2); "| R.A. (J2000) | 18$^h$05$^m$06$^s$.40 | (cite: Best1998) |" (Table 2)

## Data provenance

- ALMA projects: 2015.1.00914.S
- bands: Band 6  
  > "using the Atacama Large Millimeter/submillimeter Array (ALMA)[^1] band-6 receivers." (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: ~4 GHz centered at 225.5 GHz (observed)  
  > "for a total continuum bandwidth of $\sim$ 4 GHz, centered at 225.5 GHz (observed-frame)" (2.1 ALMA)
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 772 m and up to 1462 m  
  > "the second conducted on August 20, 2016, with a PWV of 0.31 mm and baselines up to 1462 m" (2.1 ALMA)
- angular resolution: 0.41x0.31 arcsec (CO), 0.39x0.29 (CI), 0.38x0.29 (continuum)  
  > "with a synthesized beam of size 0$\ensuremath{''}$41 $\times$ 0$\ensuremath{''}$31." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 120 uJy/beam per 60 km/s channel (CO), 130 (CI), 13 uJy/beam continuum  
  > "we obtain an RMS sensitivity of 120 $\mu$Jy beam$^{-1}$ in each spectral channel" (2.1 ALMA)
- time on source: ~1 hour 40 minutes  
  > "The total on-source integration time for these two observations was $\sim$ 1 hour and 40 minutes." (2.1 ALMA)
- observing dates: June 3, 2016 and August 20, 2016  
  > "the first conducted on June 3, 2016, with a precipitable water vapor (PWV) measurement of 1.24 mm and baselines up to 772 m" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: CO 4-3 (not stated)
- Line: [CI] (1-0) 609 um (not stated)
- External data: SFR ~350 Msun/yr, FIR luminosity 2.0e12 Lsun, dust mass 1.4e8 Msun from SED modeling  
  > "who used that value to derive an FIR luminosity of 2.0 $\times$ 10$^{12}$ $L_{\odot}$" (3.2.1) [from (cite: Podigachoski2015)]
- External data: Previous ALMA 230 GHz continuum, [OIII] 52um flux, CO(2-1) upper limit, PDR modeling, electron density 1000 cm-3  
  > "using our previous observations of the [O iii] 52 $\ensuremath{\mu}m$ line (cite: Lamarche2017)." (3.2.2) [from (cite: Lamarche2017)]
- External data: Radio continuum at 8.21 and 4.71 GHz; lobe spectral index ~-1.5  
  > "together with radio continuum observations at 8.21 and 4.71 GHz (observed-frame) (cite: Best1998)" (3.2.1) [from (cite: Best1998)]
- External data: Optical line fluxes [OIII] 5007 6.8e-18, [OII] 3727 5.9e-18, Hdelta 2.8e-19 W m-2  
  > "Adopting an [O iii] 5007 Å  line flux of 6.8 $\times$ 10$^{-18}$ W m$^{-2}$ (cite: Jackson1997)" (3.2.3) [from (cite: Jackson1997; Best2000)]
- External data: Stellar mass 3.6e11 Msun  
  > "| M$_*$ | 3.6 $\times$ 10$^{11}$ M$_\odot$ | (cite: Best1998stellarmass) |" (Table 2) [from (cite: Best1998stellarmass)]

## Processing

### Calibration

- pipeline or manual: CASA ALMA pipeline  
  > "reduced using the Common Astronomy Software Application (CASA)[^2] ALMA pipeline, version 38366 (C4 — R2B), run in CASA version 4.7.0" (2.1 ALMA)
- casa version: 4.7.0 pipeline; 4.7.2 for combining/imaging  
  > "and subsequently combined, imaged, and cleaned, using CASA version 4.7.2." (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939 (also bandpass and phase)  
  > "J1751+0939 (PKS 1749 +096) was used as the bandpass, flux, and phase calibrator." (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "employing a robust parameter of 0.5" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum-subtracted moment-zero maps; continuum from two line-free spectral windows  
  > "A continuum image was created by combining the two line-free spectral windows present in the measurement set" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 60 km/s channels  
  > "Imaging the CO(4-3) measurement set at a spectral resolution of 60 km s$^{-1}$" (2.1 ALMA)
- final beam: _not stated_
- final rms: 13 uJy/beam continuum  
  > "we obtain an RMS noise of 13 $\mu$Jy beam$^{-1}$" (2.1 ALMA)

### Inherited from earlier work

- Electron density, 84% O++ fraction, 93% of [CII] from PDRs, and PDR model approach taken from previous paper  
  > "we predicted that $\sim$ 84% of the oxygen within the H ii regions of 3C 368 is in the O$^{++}$ state (cite: Lamarche2017)" (3.2.2) [from (cite: Lamarche2017)]
- Free-free/fine-structure abundance method  
  > "and more recently to high-redshift galaxies (cite: Lamarche2018)" (3.2.2) [from (cite: Lamarche2018)]
- [CI] gas mass formula and Q10=0.6  
  > "Following (cite: Bothwell2017):" (3.4 Molecular-Gas Mass) [from (cite: Bothwell2017)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and moment-map velocity ranges
- CLEAN threshold, masks, image size and cell size
- Self-calibration and flux-scale uncertainty
- Free-free flux density at 230 GHz details and CO(4-3) line width fits
- Exact PDR Toolbox fit procedure and input line fluxes
- Rest frequencies adopted for the lines

## Analysis recipe

1. **Measure line and continuum fluxes**: Continuum-subtracted moment-0 maps; 2D Gaussian fits; checked by integrating aperture spectra  
  > "with the corresponding line fluxes determined by fitting a two-dimensional Gaussian to the emitting region of each moment-zero map." (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: Numerical integration of aperture spectra consistent within uncertainties  
  > "These fluxes were verified by numerically integrating the spectra extracted from an aperture containing the core of 3C 368" (3.1)
2. **Dust slope and radio SED decomposition**: Rayleigh-Jeans index from 480.5 GHz and 205 um points; fit thermal+nonthermal radio SED with alpha_nth fixed at 0.7  
  > "Adopting a $\nu_{0,r}$ value of 230 GHz and holding $\alpha_{nth}$ fixed at 0.7 (cite: ShuBook), we fit for $S_{th,0,r}$ and $S_{nth,0,r}$." (3.2.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Metallicity from [OIII]52um and free-free; compare R23**: Ionic abundance from line flux/free-free ratio; T4=1, ne/np=1.05, ne=1000 cm-3; R23 compared  
  > "We additionally assume n$_e$/n$_p$ = 1.05, which accounts for the electrons contributed from helium, and T$_4$ = 1, a typical value for H ii regions." (3.2.2)
   - fitting: _not stated_
   - validation: Independent R23 optical estimate and q_IR check against AGN origin  
  > "This value is within the range seen in star-forming galaxies (cite: Ivison2010), suggesting that the attribution of the radio continuum to free-free emission in 3C 368 is appropriate." (3.2.2)
4. **PDR modeling and PDR mass**: PDR Toolbox fit including CO(4-3) and [CI]; PDR mass following Hailey-Dunsheath 2010  
  > "Including the CO(4-3) and [C i] 609 $\ensuremath{\mu}m$ lines, we obtain new best-fit values of G$_0$ $\sim$ 320 Habing units and n $\sim$ 3,200 cm$^{-3}$" (3.3.1)
   - software: PDR Toolbox
   - fitting: _not stated_
   - validation: _not stated_
5. **Molecular gas mass by three methods**: CO(4-3) with r43/21>1.3 and metallicity-scaled alpha_CO; [CI] luminosity; gas-to-dust ratio  
  > "the molecular-gas mass within 3C 368 can be estimated in three ways:" (3.4)
   - assumption: alpha_CO~18 from metallicity (Glover & Mac Low 2011); X_CI=3e-5; Q10=0.6; GDR=540 at 0.3 Zsun  
  > "we obtain $\alpha_{CO}$ $\sim$ 18 $M_{\odot}$(K km s$^{-1}$ pc$^2$)$^{-1}$" (3.4)
   - fitting: _not stated_
   - validation: Consistency between the three independent methods  
  > "We find a consistent gas mass estimate of $\sim$ 6.4 $\times$ 10$^{10}$ $M_{\odot}$ across these three methods" (4 Conclusions)
6. **Dynamical mass**: M_dyn = v_rot^2 r/G with v_rot=(pi/2) v_obs, r=0.5 FWHM from Gaussian fit  
  > "We estimate the radius from two-dimensional Gaussian fits to the CO(4-3) moment-zero map (r = 0.5 FWHM = 3.14 kpc)." (3.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0 (pipeline), 4.7.2 (imaging): Pipeline reduction, combining, imaging  
  > "and subsequently combined, imaged, and cleaned, using CASA version 4.7.2." (2.1 ALMA)
- **PDR Toolbox** : PDR modeling  
  > "we modeled the photo-dissociation regions (PDRs) within 3C 368 utilizing the PDR Toolbox (cite: Pound2008; Kaufman2006)" (3.3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(4-3) line flux | 1.08 | 0.14 | Jy km/s | 1 | We obtain a CO(4-3) line flux of 1.08 $\pm$ 0.14 Jy km s$^{-1}$ |
| [CI] 609um line flux | 0.85 | 0.09 | Jy km/s | 1 | a [C i] 609 $\ensuremath{\mu}m$ line flux of 0.85 $\pm$ 0.09 Jy km s$^{-1}$ |
| Continuum core flux density at 225.5 GHz | 96 | 21 | uJy | 1 | and the core at 96 $\pm$ 21 $\mu$Jy |
| Rayleigh-Jeans index | 3.7 | 0.4 | dimensionless | 2 | of 3.7 $\pm$ 0.4, or equivalently a dust-emissivity $\beta$ value |
| Gas-phase metallicity (free-free + [OIII]) | ~0.3 | factor of two | Zsun | 3 | we obtain an estimated [O/H] ratio of 1.2 $\times$ 10$^{-4}$, or $\sim$ 0.3 Z$_\odot$ (cite: Asplund2009), within about a factor of two uncertainty |
| R23 | ~12 | not stated | dimensionless | 3 | we obtain an R$_{23}$ value of $\sim$ 12. |
| PDR gas mass | 1.7e10 | not stated | Msun | 4 | We calculate a PDR gas mass of $\sim$ 1.7 $\times$ 10$^{10}$ $M_{\odot}$ |
| Molecular gas mass (metallicity-adjusted alpha_CO) | 6.4e10 | not stated | Msun | 5 | we obtain a molecular mass of 6.4 $\times$ 10$^{10}$ $M_{\odot}$ (see Table 2). |
| Gas-to-dust ratio | 464 | not stated | dimensionless | 5 | we obtain a value of $\delta_{GDR}$ = 464 |
| Dynamical mass | 1.5e11 | not stated | Msun | 6 | We obtain a dynamical mass of $\sim$ 1.5 $\times$ 10$^{11}$ $M_{\odot}$ |

## Qualitative findings


## Claim tuples

- H: 3C 368's CO faintness is due to low metallicity | E: Free-free+[OIII] and R23 metallicities; three gas-mass methods | R: Z~0.3 Zsun both ways; gas masses agree and GDR within ~15% of expected | F: 3C 368 has sub-solar metallicity and Mgas~6.4e10 Msun | **supported**
- H: Radio core emission is star-formation free-free rather than AGN | E: SED decomposition and q_IR | R: q_IR=2.6, within star-forming range | F: Free-free attribution appropriate but unresolved | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radio core emission from compact AGN synchrotron instead of free-free; not ruled out  
  > "may instead come from a compact AGN (cite: Roellig1986)" (3.2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Core continuum flux is a lower limit due to resolved-out extended emission  
  > "making the quoted flux density from the core a lower limit on the true value." (3.1)
- Caveat (inferred, ours): Metallicity relies on single [OIII] line, assumed T and density with factor-2 uncertainty
- Caveat (inferred, ours): alpha_CO and r43/21 depend on a CO(2-1) limit
- Caveat (inferred, ours): Dynamical mass assumes disk geometry

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (masks, image size, cell)
- Missing: Values of previous-paper measurements
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Key imaging settings stated, but much analysis depends on external numbers and unspecified fits.
- Rediscovery candidate: yes, Archival ALMA project code given, fluxes and masses numeric, recipe fairly clear.

## Links

- Method: (cite: Bothwell2017) ([CI] gas mass formula)
- Method: (cite: Hailey-Dunsheath2010) (PDR mass formula)
- Companion: (cite: Lamarche2017) (Earlier FIR/ALMA observations of 3C 368)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 74,
  "stated": 40,
  "rate": 0.541
 },
 "evidence_ok": true
}
```
