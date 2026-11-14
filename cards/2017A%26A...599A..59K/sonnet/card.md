# An observational study of dust nucleation in Mira (o Ceti). II. Titanium oxides are negligible for nucleation at high temperatures

`2017A&A...599A..59K` | Astronomy and Astrophysics 2017 | first author: Kamiński, T. | arXiv: 1610.01141 | DOI: 10.1051/0004-6361/201629838

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Do titanium oxides (TiO, TiO2) and other Ti-bearing species in Mira's extended atmosphere indicate that they initiate dust nucleation in M-type AGB stars?  
  > "seek an observational verification of whether titanium oxides play a major role in the onset of dust formation in M-type asymptotic-giant-branch (AGB) stars." (abstract)
- Target **Mira (o Ceti)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00014.SV, 2013.1.00047.S, 2012.1.00524.S, 2013.1.00156.S
- bands: Band 7 (four runs), plus Band 9 and Band 6 (Paper I)  
  > "Mira was observed by ALMA in Band 7 on four different observing runs" (2.1 Submillimeter/millimeter and FIR data)
- frequencies and spectral setup: 2015: 342.2–345.9 and 354.2–357.9 GHz, 0.9 km/s resolution; Band 9: 679.11–682.77 GHz  
  > "| 21 Jul 2015 | Kamiński | 342.2–345.9, 354.2–357.9 | 0.9 | 0.16$''$$\times$0.13$''$ | Paper I |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~145 mas best (Band 7, 21 Jul 2015; 0.154x0.125 arcsec for TiO 11-10)  
  > "Our best angular resolution of $\sim$145 mas was achieved in the Band 7 data from 2015" (2.1 Submillimeter/millimeter and FIR data)
- max recoverable scale: _not stated_
- sensitivity: about 1.7 mJy/beam per 0.97 km/s (2015 data)  
  > "This procedure resulted in a nominal sensitivity of about 1.7 mJy/beam per 0.97 km s$^{-1}$" (2.1 Submillimeter/millimeter and FIR data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 2015 data PI Kamiński; others Ramstedt, Planesas, archival  
  > "| 16 Jun 2014 | Planesas | 679.11–682.77 | 6.9 | 0.23$''$$\times$0.16$''$ | (cite: planesas) |" (Table 1)
- Line: 48TiO J=11-10 Delta3 (355623.35 MHz)
- Line: 50TiO J=11-10 Delta1 (344722.34 MHz)
- Other facility **APEX**: Spectra with FLASH+ and SHeFi-1 covering TiO and TiO2 lines  
  > "utilized the FLASH$^+$ (cite: flash) and SHeFi-1 (cite: shfi) receivers to cover multiple spectral ranges between 222 and 500 GHz" (2.1 Submillimeter/millimeter and FIR data)
- Other facility **Herschel/HIFI**: Archival spectra searched for TiO lines  
  > "All archival spectra obtained with the HIFI instrument (cite: hifi) on *Herschel* were examined" (2.1 Submillimeter/millimeter and FIR data)
- Other facility **Mercator/HERMES and archival optical spectra**: Multi-epoch optical spectra for Ti I and TiO  
  > "Twelve epochs were covered between July 2009 and August 2014, but most of the data come from 2009." (2.2 Optical spectroscopy)
- External data: CDMS rotational line predictions for TiO and TiO2  
  > "Predictions of the rotational spectrum of $^{48}$TiO were taken from the Cologne Database for Molecular Spectroscopy (cite: CDMS_1; CDMS_2)." (4.1 Line lists) [from (cite: CDMS_1; CDMS_2)]
- External data: Hydrogen column density 1e22-1e24 cm-2 from CODEX hydrodynamical models  
  > "hydrodynamical models of Mira of the CODEX grid (cite: ireland2011) give the hydrogen column density in the range $10^{22}-10^{24}$ cm$^{-2}$" (4.5 Excitation and column densities of TiO and TiO2) [from (cite: ireland2011)]
- External data: Band 9 ALMA data description  
  > "Those observations are described in detail in (cite: planesas)" (2.1 Submillimeter/millimeter and FIR data) [from (cite: planesas)]
- Simulation/model as data: Chemical kinetic shock model of IK Tau (Teff 2200 K) used as representative for Mira's chemistry  
  > "We assume here that this model is representative of the chemistry of the Mira's envelope and compare the model predictions with our observational constraints." (6.1 Tracing titanium chemistry in O-type AGB stars)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.6  
  > "Interferometric data were processed and imaged in CASA 4.6 (cite: casa) in the same way as described in Paper I." (2.1 Submillimeter/millimeter and FIR data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Complex gains (self-)calibrated on continuum of Mira A/B  
  > "The complex gains of those interferometric observations were (self-)calibrated on the strong continuum sources of the Mira A/B binary system." (2.1 Submillimeter/millimeter and FIR data)

### Imaging

- task: CLEAN in CASA  
  > "all spectral data were processed in CLEAN after continuum subtraction in the $u\varv$ domain (cf. Appendix B of Paper I)." (2.1 Submillimeter/millimeter and FIR data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in the uv domain  
  > "all spectral data were processed in CLEAN after continuum subtraction in the $u\varv$ domain (cf. Appendix B of Paper I)." (2.1 Submillimeter/millimeter and FIR data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA processing and imaging procedure  
  > "Interferometric data were processed and imaged in CASA 4.6 (cite: casa) in the same way as described in Paper I." (2.1 Submillimeter/millimeter and FIR data) [from Paper I (Kamiński et al. 2016, (cite: kami_mira1))]
- Stellar radius R*=14.4 mas definition and envelope zone definitions  
  > "As in Paper I, we define R$_{\star}$=14.4 mas" (3 The state and structure of Mira's atmosphere) [from Paper I]
- Optical spectra and visual phase calculation  
  > "We use the optical spectra presented in Paper I." (2.2 Optical spectroscopy) [from Paper I]
- Rotational-diagram assumptions  
  > "As discussed in Paper I, the values of $T_{\rm ex}$ and $N$ are derived under the assumption that all lines are optically thin" (4.5 Excitation and column densities of TiO and TiO2) [from Paper I]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (weighting, robust, cell, image size, masks, channel width) not given here
- Line-free channels for continuum subtraction
- Distance to Mira and source coordinates
- Exact line flux extraction apertures/procedure
- Which ALMA execution blocks correspond to each project code

## Analysis recipe

1. **Measure submm continuum source**: Fit models to calibrated visibilities (Gaussian and elliptical uniform disk)  
  > "We measured the submm-continuum source by fitting models to calibrated visibilities." (3.1 Continuum)
   - software: CASA
   - assumption: Blackbody of 2440 K, radius 25.8 mas = 1.8 R* underlies gas  
  > "We assume here that a blackbody source of 2440 K with a radius of $\langle r \rangle$=25.8 mas=1.8 R$_{\star}$ underlies the circumstellar gas" (3.1 Continuum)
   - fitting: _not stated_
   - validation: Compared with long-baseline Band 6 sizes within 15%  
  > "This disk size and temperature are consistent, within 15%, with those measured in long-baseline Band 6 data" (3.1 Continuum)
2. **Measure emission sizes and positions of TiO and TiO2**: Gaussian fits to line images (TiO2: seven transitions combined)  
  > "These values were measured as a Gaussian fit to an image of seven combined TiO$_2$ transitions to obtain a better S/N." (4.4 Spatio-kinematical characteristics TiO2-bearing gas)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive TiO excitation temperature and column density**: Rotational-diagram fit to all TiO lines (APEX, ALMA, Herschel)  
  > "We used the rotational-diagram method (cite: popdiagr) to derive the temperature and column density of TiO that is traced in the main emission component." (4.5 Excitation and column densities of TiO and TiO2)
   - parameter: source size 116x93 mas  
  > "for a source size of 116$\times$93 mas" (4.5 Excitation and column densities of TiO and TiO2)
   - assumption: Optically thin, Boltzmann populations, equal Trot of fine-structure components, no time variation  
  > "all lines are optically thin, the level populations follow the Boltzmann distribution, the rotational temperatures in the three fine-structure components are equal" (4.5 Excitation and column densities of TiO and TiO2)
   - fitting: Linear fit of rotational diagram  
  > "We used the rotational-diagram method (cite: popdiagr) to derive the temperature and column density of TiO that is traced in the main emission component." (4.5 Excitation and column densities of TiO and TiO2)
   - validation: Refit with isotopologue fluxes scaled by abundances improved the fit  
  > "This improved the quality of the fit and yielded $T_{\rm ex}$=474$\pm$69 K" (4.5 Excitation and column densities of TiO and TiO2)
4. **Derive TiO2 temperature and column density and isotopologue ratios**: LTE chi2 grid of models compared to ten line profiles  
  > "we employed the LTE package of CASSIS and performed a $\chi^2$ minimization in which a grid of models was compared to ten observed line profiles." (4.5 Excitation and column densities of TiO and TiO2)
   - software: CASSIS
   - parameter: Gaussian profile FWHM 8.5 km/s, centre 46.8 km/s  
  > "we approximated the profiles by a Gaussian with a FWHM of 8.5 km s$^{-1}$ and a central velocity of 46.8 km s$^{-1}$" (4.5 Excitation and column densities of TiO and TiO2)
   - assumption: Single isothermal component  
  > "the quality of data and their spread in parameters space do not warrant multi-component models" (4.5 Excitation and column densities of TiO and TiO2)
   - fitting: chi2 minimization on a grid  
  > "performed a $\chi^2$ minimization in which a grid of models was compared to ten observed line profiles." (4.5 Excitation and column densities of TiO and TiO2)
   - validation: Optically thin check (tau0<=1); Band 9 blend at 675.9 GHz consistent  
  > "the observation of the 675.9 GHz blend confirms our identification and excitation analysis." (4.2 Identification of TiO, TiO2, and their isotopologues)
5. **Compare with chemical models and optical spectra**: Compare abundances/distribution with Gobrecht et al. kinetic model and analyze Ti I/TiO optical emission  
  > "We compare the gas characteristics deduced from the observations with chemical models to better constrain the titanium chemistry in an O-rich star like Mira." (6.1 Tracing titanium chemistry in O-type AGB stars)
   - software: MARCS, pgopher
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.6: Processing and imaging of ALMA data  
  > "Interferometric data were processed and imaged in CASA 4.6 (cite: casa)" (2.1 Submillimeter/millimeter and FIR data)
- **CASSIS** : LTE chi2 modelling of TiO2 and isotopologues  
  > "we employed the LTE package of CASSIS" (4.5 Excitation and column densities of TiO and TiO2)
- **pgopher** : Simulating TiO2 and TiH optical bands  
  > "We performed a simulation of the TiO$_2$ bands in `pgopher` (cite: pgopher)" (5.4 TiO2 absorption)
- **MARCS** : Synthetic photospheric spectra  
  > "generate a synthetic spectrum from the MARCS model photosphere (cite: MARCS)" (Isotopic composition from optical bands of TiO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| TiO excitation temperature (best) | 474 | 69 | K | 3 | yielded $T_{\rm ex}$=474$\pm$69 K and $N$($^{48}$TiO)=(4.1$\pm$0.7)$\cdot$10$^{16}$ cm$^{-2}$ |
| N(48TiO) (best) | 4.1e16 | 0.7e16 | cm-2 | 3 | yielded $T_{\rm ex}$=474$\pm$69 K and $N$($^{48}$TiO)=(4.1$\pm$0.7)$\cdot$10$^{16}$ cm$^{-2}$ |
| TiO2 rotational temperature | 174 | 7 | K | 4 | $T_{\rm rot}=174\pm7$ K and $N$(TiO$_2$)=$(1.15\pm0.12)\cdot 10^{16}$ cm$^{-2}$ (1$\sigma$ errors) |
| N(TiO2) | 1.15e16 | 0.12e16 | cm-2 | 4 | $T_{\rm rot}=174\pm7$ K and $N$(TiO$_2$)=$(1.15\pm0.12)\cdot 10^{16}$ cm$^{-2}$ (1$\sigma$ errors) |
| TiO main emission size (beam-deconvolved FWHM) | 115.9x93.3, PA 106 deg | 2.7 mas; 5 deg | mas | 2 | beam-deconvolved FWHM of 115.9$\times$93.3 ($\pm$2.7) mas and a position angle of the major axis (PA) of 106$^\circ$$\pm$5$^\circ$ |
| TiO2 emission size | 159x78, PA 107 deg | 10, 11 mas | mas | 2 | beam-deconvolved full size of about (159$\pm$10)$\times$(78$\pm$11) mas at PA=107$^\circ$ |
| 46TiO2/48TiO2 | 0.32 | 0.04 | dimensionless | 4 | $^{46}$TiO$_2$/$^{48}$TiO$_2$=0.32$\pm$0.04 |
| Continuum disk size | 53.8x49.5 mas, Tb 2440 K | 0.1 mas | mas | 1 | elliptical disk with a full size of 53.8$\times$49.5 ($\pm$0.1) mas at PA=–54.7$^\circ$$\pm$0.6$^\circ$, which corresponds to a brightness temperature of 2440 K |
| TiO/TiO2 column density ratio | 3.4 | 0.9 | dimensionless | 5 | the observed source-averaged column-density ratio is TiO/TiO$_2$=3.4$\pm$0.9 |

## Qualitative findings

- Ti I emission at 5173 A is resonantly scattered and arises in the extended atmosphere  
  > "Resonant scattering is therefore a reasonable explanation of the Ti I emission." (5.1 Neutral atomic titanium)

## Claim tuples

- H: Do TiO and TiO2 gas reside in the extended atmosphere of Mira? | E: ALMA Band 7 imaging of TiO and TiO2 lines | R: TiO radius (FWHM/2) ~4 R*, TiO2 2.7–5.5 R*, TiO2 more anisotropic | F: Both are in the extended atmosphere | **supported**
- H: Do shock chemistry models match Ti-species observations? | E: Compare with Gobrecht et al. kinetic model | R: General agreement except TiO2 produced more efficiently | F: Non-equilibrium models are favored over thermal equilibrium | **supported**
- H: Do titanium oxides initiate dust formation in Mira? | E: Search for hot Ti condensate precursors and Ti depletion | R: High gas-phase Ti abundances, no hot precursors | F: Titanium oxides are unlikely seeds; alumina is a better candidate | **supported**

## Reasoning

- Why this data: Mira chosen for accessible multi-wavelength, multi-epoch observations  
  > "it was chosen to be the main target of our study owing to relatively easily accessible observations covering several wavelength regimes and multiple epochs" (6.2 Implications for seed formation)
- Why this method: _not stated_
- Alternative: Shock excitation of Ti I 5173 emission excluded; resonant scattering preferred  
  > "any shock-triggered emission would show dramatic changes in intensity and velocity which are not observed in Ti I." (5.1 Neutral atomic titanium)
- How they decided it was enough: _not stated_
- Limitation (authors): Abundances relative to H uncertain by over an order of magnitude; single-epoch TiO2 data  
  > "Because the derived abundances for TiO and TiO$_2$ are uncertain by more than one order of magnitude" (6.2 Implications for seed formation)
- Caveat (inferred, ours): Source sizes for column densities are from beam-limited Gaussian fits
- Caveat (inferred, ours): TiO2 analysis relies on few clean lines and heavy blending
- Caveat (inferred, ours): Results from one star and one epoch; generalization to other AGB stars is uncertain

## Reproducibility

- Data public (paper): ALMA project codes listed in acknowledgements; archival data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00014.SV, 2013.1.00047.S, 2012.1.00524.S, 2013.1.00156.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (deferred to Paper I)
- Missing: Line flux extraction details
- Missing: Distance and coordinates
- Data volume (inferred): ~100-300 GB for four ALMA Band 7/9 datasets
- Score (inferred): 3/5, Public data and clear analysis methods, but imaging details deferred to Paper I and heavy line blending complicates flux extraction.
- Rediscovery candidate: no, Processing recipe is incomplete in this paper and relies on Paper I.

## Links

- Method: Kamiński et al. 2016, Paper I (cite: kami_mira1) (ALMA processing and imaging, rotational diagram assumptions, optical spectra)
- Companion: (cite: kami_tio) (Analogous Ti study of VY CMa)
- Related: HIFISTARS

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 45,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
