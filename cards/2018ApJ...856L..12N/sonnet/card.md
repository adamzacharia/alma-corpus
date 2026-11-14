# Molecular Emission from a Galaxy Associated with a z ∼ 2.2 Damped Lyα Absorber

`2018ApJ...856L..12N` | The Astrophysical Journal Letters 2018 | first author: Neeleman, Marcel | arXiv: 1803.05914 | DOI: 10.3847/2041-8213/aab5b1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, other
- Question: Is a high-metallicity z~2.2 DLA toward QSO B1228-113 associated with a molecular gas-rich galaxy, and what is the multi-phase nature of the absorbing gas?  
  > "we have targeted three DLAs at $z \sim 2$ with ALMA to search for CO emission from galaxies associated with the absorbers." (Introduction)
- Target **DLA toward QSO B1228-113 / ALMA J123055.50-113906.4**: coordinates QSO 12:30:55.62 -11:39:09.9; galaxy 12:30:55.50 -11:39:06.4 (J2000)  
  > "Right Ascension (J2000) | 12:30:55.62" (Table 1); "Redshift | 2.19289" (Table 1); "Throughout this Letter we assume a standard flat Lambda Cold Dark Matter cosmology with $\Omega_\Lambda = 0.7$, and $H_0 = 70~{\rm km~s^{-1}}$." (Introduction); z/distance z_DLA = 2.19289; CO z = 2.1933 ± 0.0005  
  > "Right Ascension (J2000) | 12:30:55.62" (Table 1); "Redshift | 2.19289" (Table 1); "Throughout this Letter we assume a standard flat Lambda Cold Dark Matter cosmology with $\Omega_\Lambda = 0.7$, and $H_0 = 70~{\rm km~s^{-1}}$." (Introduction); distance from DLA metal absorption; CO(3-2) emission redshift  
  > "Right Ascension (J2000) | 12:30:55.62" (Table 1); "Redshift | 2.19289" (Table 1); "Throughout this Letter we assume a standard flat Lambda Cold Dark Matter cosmology with $\Omega_\Lambda = 0.7$, and $H_0 = 70~{\rm km~s^{-1}}$." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00628.S
- bands: _not stated_
- frequencies and spectral setup: four spectral windows; one on CO(3-2) at 108.3 GHz, three for continuum  
  > "One of the four spectral windows was centered on the redshifted CO($3-2$) line at 108.3 GHz, and the remaining three spectral windows were set up to measure continuum emission." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, max baseline 453 m  
  > "with a compact configuration (maximum baseline of 453 m) for a total on-source integration time of 2.4 hours." (2.2 ALMA Observations)
- baselines: _not stated_
- angular resolution: continuum beam 2.9'' x 2.0''; cube 2.6'' x 1.8''  
  > "resulting in a synthesized beam of $2.9'' \times 2.0''$ at $-83.8$° and a root mean square (RMS) noise of 6.9 $\mu$Jy beam$^{-1}$" (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 6.9 uJy/beam; cube 0.15 mJy/beam per 43.2 km/s channel  
  > "an RMS of 0.15 mJy beam$^{-1}$ per 43.2 ${\rm km~s}^{-1}$ channel" (2.2 ALMA Observations)
- time on source: 2.4 hours  
  > "for a total on-source integration time of 2.4 hours" (2.2 ALMA Observations)
- observing dates: UT 2017 April 7 and 8  
  > "was observed with ALMA on UT 2017 April 7 and 8" (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated (observed 108.3 GHz))
- Other facility **VLT-UVES**: High-resolution QSO spectrum for metal absorption lines  
  > "a high resolution spectrum was obtained of QSO B1228$-$113 using the Ultraviolet and Visual Echelle Spectrograph" (2.1 UVES Observations)
- Other facility **VLT-SINFONI**: Archival NIR IFU data for Halpha  
  > "We use archival Very Large Telescope-SINFONI data to detect H$\alpha$ emission from the associated galaxy" (abstract)
- Other facility **GMRT**: HI 21 cm absorption spectroscopy  
  > "were used to carry out a search for redshifted H I 21 cm absorption from the DLA towards QSO B1228$-$113 on 2017 May 8." (2.4 GMRT Observations)
- External data: VLBA 327 MHz core flux density of the quasar, used for covering factor  
  > "(cite: Kanekar2009) used the Very Long Baseline Array (VLBA) to measure the core flux density of the quasar" (2.4 GMRT Observations) [from (cite: Kanekar2009)]
- External data: CO(3-2)/CO(1-0) ratio r31 = 0.57  
  > "$r_{31} = L'_{\text{CO(3$-$2)}}/L'_{\text{CO(1$-$0)}} = 0.57$ (cite: Dessauges2015)" (3.1 Galaxy Properties) [from (cite: Dessauges2015)]
- External data: Previous QSO flux used to scale SINFONI cube  
  > "The final co-added data cube was scaled to match the previously measured flux of the integrated QSO spectrum (cite: Ellison2005)." (2.3 SINFONI Observations) [from (cite: Ellison2005)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA for initial calibration  
  > "The initial calibration was carried out using the ALMA pipeline in the Common Astronomy Software Applications (cite: McMullin2007) package." (2.2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto and Ganymede  
  > "Callisto and Ganymede were used as flux calibrators" (2.2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: performed in AIPS using the quasar continuum (18.8 mJy)  
  > "was sufficient to perform self-calibration, which was done in the Astronomical Image Processing System (cite: Greisen2003) package." (2.2 ALMA Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The continuum image was created in CASA using natural weighting" (2.2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning-smoothed to 43.2 km/s  
  > "The spectral cube was Hanning-smoothed to a velocity resolution of 43.2 ${\rm km~s}^{-1}$." (2.2 ALMA Observations)
- final beam: _not stated_
- final rms: 6.9 uJy/beam continuum; 0.15 mJy/beam per channel cube  
  > "an RMS of 0.15 mJy beam$^{-1}$ per 43.2 ${\rm km~s}^{-1}$ channel" (2.2 ALMA Observations)

### Inherited from earlier work

- UVES observation and reduction procedures  
  > "Details of the observations and reduction procedures are described in (cite: Akerman2005)." (2.1 UVES Observations) [from (cite: Akerman2005)]
- GMRT analysis with standard low-frequency procedures  
  > "analyzed in AIPS using standard procedures for low-frequency imaging and spectroscopy (cite: Kanekar2014)" (2.4 GMRT Observations) [from (cite: Kanekar2014)]
- Modified blackbody SED parameters for L(TIR)  
  > "$\text{T}_{\text{dust}} = 35$ K, to the measured flux density (cite: Neeleman2017)" (3.1 Galaxy Properties) [from (cite: Neeleman2017)]

### Not stated but needed to reproduce (our reading)

- ALMA/CASA and pipeline versions
- Line-free channels and continuum subtraction method
- Image size and cell size
- Self-calibration solution intervals
- Method of fitting the CO line and extracting flux (aperture or Gaussian)
- Flux scale uncertainty
- SINFONI aperture and narrow-band widths
- Details of SFR-TIR dust correction calibration

## Analysis recipe

1. **Calibrate and image ALMA data**: ALMA pipeline in CASA, self-calibration in AIPS, natural-weighted continuum and Hanning-smoothed cube  
  > "The initial calibration was carried out using the ALMA pipeline in the Common Astronomy Software Applications (cite: McMullin2007) package." (2.2 ALMA Observations)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CO line luminosity and total IR luminosity**: Fit modified blackbody to 100.5 GHz continuum flux  
  > "we fitted a modified black-body spectrum with mid-infrared slope, $\alpha = 1.5$, spectral emissivity index, $\beta = 1.5$, and dust temperature, $\text{T}_{\text{dust}} = 35$ K" (3.1 Galaxy Properties)
   - assumption: alpha=1.5, beta=1.5, T_dust=35 K  
  > "spectral emissivity index, $\beta = 1.5$, and dust temperature, $\text{T}_{\text{dust}} = 35$ K" (3.1 Galaxy Properties)
   - fitting: _not stated_
   - validation: Consistent with L'(CO)-L(TIR) relation in high-z galaxies  
  > "this estimate is consistent with the estimate obtained from our $L'\text{(CO)}$ measurement" (3.1 Galaxy Properties)
3. **Measure Halpha flux and SFR**: SINFONI re-reduction, pseudo narrow-band image, Gaussian fit of Halpha and [NII]; Kennicutt & Evans SFR with TIR dust correction  
  > "We fitted both emission lines with the Image Reduction and Analysis Facility package (cite: Tody1993) using NGAUSSFIT" (2.3 SINFONI Observations)
   - software: ESO SINFONI pipeline, IRAF
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate molecular gas mass**: M_mol from L'CO(3-2) with r31 and alpha_CO  
  > "assuming a CO(3$-$2) to CO(1$-$0) line ratio of $r_{31} = L'_{\text{CO(3$-$2)}}/L'_{\text{CO(1$-$0)}} = 0.57$ (cite: Dessauges2015)" (3.1 Galaxy Properties)
   - assumption: alpha_CO = 4.3 Msun (K km/s pc^2)^-1, r31 = 0.57  
  > "a CO-to-H$_2$ conversion factor of $\alpha_{\text{CO}} = 4.3~\text{M}_\odot~(\text{K~km~s}^{-1}~\text{pc}^2)^{-1}$" (3.1 Galaxy Properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit absorption lines and HI 21cm spin temperature**: MCMC Voigt fitting of UVES metal lines with tied components; GMRT 21 cm optical depth limit and covering factor  
  > "a Monte Carlo Markov Chain Voigt profile fitting routine publicly available in the LINETOOLS" (2.1 UVES Observations)
   - software: LINETOOLS, AIPS
   - parameter: six components fit to Ni II 1741/1751; assumed 20 km/s FWHM Gaussian for 21 cm  
  > "assuming a Gaussian line profile with a FWHM of 20 km s$^{-1}$" (2.4 GMRT Observations)
   - fitting: MCMC Voigt profile fitting; priors not stated  
  > "refitted the metal lines using a Monte Carlo Markov Chain Voigt profile fitting routine publicly available in the LINETOOLS [^1] package" (UVES Observations)
   - validation: Metallicity consistent with previous measurement  
  > "consistent with the previous measurement" (2.1 UVES Observations)

## Software

- **CASA** : ALMA pipeline calibration and imaging  
  > "The continuum image was created in CASA using natural weighting" (2.2 ALMA Observations)
- **AIPS** : ALMA self-calibration and GMRT data analysis  
  > "The GMRT data were analyzed in AIPS" (2.4 GMRT Observations)
- **LINETOOLS** : MCMC Voigt profile fitting  
  > "a Monte Carlo Markov Chain Voigt profile fitting routine publicly available in the LINETOOLS" (2.1 UVES Observations)
- **IRAF** : NGAUSSFIT of Halpha and [NII]  
  > "using NGAUSSFIT" (2.3 SINFONI Observations)
- **ESO SINFONI pipeline** v. 2.9: re-reduction of SINFONI data  
  > "We re-reduced the data using the ESO SINFONI pipeline v. 2.9." (2.3 SINFONI Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) velocity-integrated flux | 0.73 | 0.06 | Jy km/s | 1 | $\int S_{\rm CO(3-2)} dv$ (Jy ${\rm km~s}^{-1}$)        / $0.73 \pm 0.06$ |
| CO(3-2) FWHM | 600 | 60 | km/s | 1 | FWHM$_{\rm CO(3-2)}$ (${\rm km~s}^{-1}$)                / $600 \pm 60$ |
| Continuum flux at 100.5 GHz | 46 | 10 | uJy | 1 | $S_{\rm cont}$ at $\nu_{\rm obs}$ = 100.5 GHz ($\mu$Jy) / $46 \pm 10$ |
| L'CO(3-2) | 1.88e10 | 0.15e10 | K km/s pc^2 | 2 | $L'_{\text{CO(3$-$2)}}$ = $(1.88 \pm 0.15) \times 10^{10}$ K ${\rm km~s}^{-1}$ pc$^2$ |
| L_TIR | 2.2e12 | 0.5e12 (systematic ~0.6 dex) | Lsun | 2 | $L\text{(TIR)} = (2.2 \pm 0.5) \times 10^{12}~L_\odot$ |
| Dust-corrected SFR | 110 | +60/-30 | Msun/yr | 3 | yields a dust-corrected SFR of $110^{+60}_{-30}$ M$_\odot$ yr$^{-1}$ |
| Halpha SFR (uncorrected) | 3.9 | 0.4 | Msun/yr | 3 | dust-uncorrected star formation rate (SFR) of $3.9 \pm 0.4$ M$_\odot$ yr$^{-1}$ |
| Molecular mass | 1.4e11 | 0.2e11 | Msun | 4 | $M_{\text{mol}} = (1.4 \pm 0.2) \times 10^{11} \times (\alpha_{\text{CO}}/4.3) \times (0.57/r_{31})$ M$_\odot$ |
| Spin temperature lower limit | 1895 x (f/0.93) | 3 sigma limit | K | 5 | The $3\sigma$ lower limit to the DLA spin temperature is then $T_{\rm s} > 1895 \times (f/0.93)$ K. |
| DLA metallicity [M/H] | -0.27 | 0.10 | dex | 5 | resulting in an updated metallicity of ${\rm [M/H]} = -0.27 \pm 0.10$ |

## Qualitative findings

- CO redshift agrees with low-ion absorption within ~40 km/s, disfavoring bulk-motion gas scenarios  
  > "disfavors scenarios where the absorber is probing gas with a bulk motion with respect to the galaxy" (3.2 Galaxy/DLA Association)

## Claim tuples

- H: High-metallicity z~2 DLAs arise near massive gas-rich galaxies | E: ALMA CO(3-2) search around the DLA sightline | R: CO detected 3.5'' (30 kpc) away at the DLA redshift with M_mol ~1.4e11 Msun | F: Galaxy is associated with the DLA; consistent with massive-galaxy origin | **supported**
- H: The galaxy is dust-obscured | E: Compare Halpha SFR with TIR-based SFR | R: 3.9 vs 110 Msun/yr | F: Highly dust-obscured | **supported**
- H: DLA HI is multi-phase | E: GMRT 21 cm plus UVES CI | R: Ts > 1895 K but CI present | F: Cold components contribute little HI but ~50% of metals | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Starburst-like alpha_CO~1 and r31~1 (mass lower by ~10) disfavored since the SFR is below typical starburst SFRs  
  > "However, we disfavor this scenario, as even the dust-corrected SFR estimate is significantly below the median SFRs seen in starburst galaxies" (3.1 Galaxy Properties)
- How they decided it was enough: _not stated_
- Limitation (authors): L_TIR has large systematic uncertainty because beta and T_dust are unconstrained by a single continuum point  
  > "This estimate has a large systematic uncertainty ($\sim$0.6 dex) because both $\beta$ and $\text{T}_{\text{dust}}$ are not constrained by the single dust continuum measurement." (3.1 Galaxy Properties)
- Caveat (inferred, ours): Single continuum point gives poorly constrained L_TIR and SFR
- Caveat (inferred, ours): alpha_CO and r31 uncertain
- Caveat (inferred, ours): Source unresolved; no kinematic modelling
- Caveat (inferred, ours): Single system

## Reproducibility

- Data public (paper): ALMA project code printed; SINFONI data archival  
  > "We use archival Very Large Telescope-SINFONI data" (abstract)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Self-cal details
- Missing: Line-fit method details
- Data volume (inferred): ~10-30 GB for ALMA raw data
- Score (inferred): 5/5, Public ALMA data and simple measurements, but imaging and fitting details are sparse.
- Rediscovery candidate: yes, Public ALMA project; main results are numeric (line flux, continuum flux), though some settings are unstated.

## Links

- Method: (cite: Neeleman2017) (SED modified blackbody parameters for L(TIR))
- Method: (cite: Kanekar2014) (GMRT HI 21 cm analysis procedures)
- Companion: (cite: Neeleman2016b) (First molecular emission detection from Lyα absorber galaxy)
- Companion: (cite: KanekarPrep) (CO emission from z~0.7 high-metallicity absorbers)
- Related: ALMA search for CO around three z~2 DLAs

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "stated": 45,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
