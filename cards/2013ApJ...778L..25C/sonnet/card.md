# Unveiling the Dust Nucleation Zone of IRC+10216 with ALMA

`2013ApJ...778L..25C` | The Astrophysical Journal Letters 2013 | first author: Cernicharo, J. | arXiv: 1310.7383 | DOI: 10.1088/2041-8205/778/2/L25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What are the physical and chemical conditions of the dust nucleation zone of IRC+10216, as probed by vibrationally excited HNC J=3-2 lines in early ALMA data?  
  > "The HNC data are interpreted through a 1D–spherical non–local radiative transfer model, coupled to a chemical model that includes chemistry at thermochemical equilibrium for the innermost regions" (abstract)
- Target **IRC+10216**: coordinates continuum peak RA 09h47m57.446s, Dec +13d16m43.86s (J2000)  
  > "We adopt a distance to IRC+10216 of 130 pc (cite: groenewegen2012) and a radius for the star of 4$\times$10$^{13}$ cm (cite: menten2012)." (Radiative Transfer and Chemical Modeling); "continuum emission peak at $\alpha$=09$^h$ 47$^m$ 57.446$^s$ and $\delta$=13$^o$ 16’ 43.86" (J2000)" (2 Observations); z/distance 130 pc  
  > "We adopt a distance to IRC+10216 of 130 pc (cite: groenewegen2012) and a radius for the star of 4$\times$10$^{13}$ cm (cite: menten2012)." (Radiative Transfer and Chemical Modeling); "continuum emission peak at $\alpha$=09$^h$ 47$^m$ 57.446$^s$ and $\delta$=13$^o$ 16’ 43.86" (J2000)" (2 Observations); distance from Groenewegen et al. 2012  
  > "We adopt a distance to IRC+10216 of 130 pc (cite: groenewegen2012) and a radius for the star of 4$\times$10$^{13}$ cm (cite: menten2012)." (Radiative Transfer and Chemical Modeling); "continuum emission peak at $\alpha$=09$^h$ 47$^m$ 57.446$^s$ and $\delta$=13$^o$ 16’ 43.86" (J2000)" (2 Observations)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6, 255.3 to 274.8 GHz over 4 setups  
  > "They consisted in 4 spectral setups covering the frequency range 255.3 to 274.8 GHz (receiver band 6) with a 0.5 MHz channel spacing." (Observations)
- frequencies and spectral setup: setup id4, 269.8 to 274.0 GHz, 2 runs  
  > "Observations were obtained in 2 runs in a single spectral setup (referenced as id4 in the ALMA archive), which covered the range 269.8 to 274.0GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 16 antennas, up to 402 m  
  > "The array was configured with 16 antennas extending up to 402 m." (Observations)
- baselines: _not stated_
- angular resolution: 0.6"x0.5" synthetic beam  
  > "The final synthetic beam is 0.6"x0.5" and the r.m.s. per channel is $\sim$5 mJy/Beam." (Observations)
- max recoverable scale: _not stated_
- sensitivity: ~5 mJy/beam per channel; continuum 2 mJy/beam  
  > "That of the continuum map is 2 mJy/Beam" (Observations)
- time on source: two runs of ~72 min each, 26 min on source  
  > "Two runs of about 72 min each were performed, of which 26 min correspond to correlations on source." (Observations)
- observing dates: April 8 to 23, 2012 (Cycle 0)  
  > "The observations of IRC+10216 with ALMA were made between April 8 and 23, 2012 (ALMA Cycle0)." (Observations)
- pi or archival as stated: _not stated_
- Line: HNC J=3-2, nine vibrational states (not stated)
- Line: SiS v=1 J=15-14 (270.917 GHz)
- Other facility **IRAM 30-m**: single-dish spectrum for comparison with ALMA, used in HNC fits  
  > "the ALMA spectrum superimposed on the spectrum observed with the IRAM 30-m single-dish telescope (cite: Cernicharo2011)" (Line modeling and Discussion)
- Other facility **Herschel/HIFI**: HNC high-J ground-state lines modeled by Daniel et al. 2012  
  > "High–$J$ rotational lines of its ground vibrational level have recently been observed in IRC+10216 from *Herschel*/HIFI observations." (Introduction)
- External data: HNC collisional rate coefficients for rotational transitions  
  > "The collisional rate coefficients for the rotational transitions of HNC were derived from the calculations of (cite: dumouchel2010)." (Radiative Transfer and Chemical Modeling) [from (cite: dumouchel2010)]
- External data: CSE temperature profile  
  > "adopting the temperature radial profile of (cite: agundez2012)" (Radiative Transfer and Chemical Modeling) [from (cite: agundez2012)]
- External data: HCN abundance profile  
  > "by using the HCN abundance profile derived by (cite: Fonfria2008)" (Radiative Transfer and Chemical Modeling) [from (cite: Fonfria2008)]
- External data: HNC effective abundance profile for r>=10 R*  
  > "we kept for radii $\geq 10 \, R_*$ the $"$effective$"$ abundance profile derived from the analysis of the *Herschel* observations by (cite: daniel2012)" (Radiative Transfer and Chemical Modeling) [from (cite: daniel2012)]

## Processing

### Calibration

- pipeline or manual: calibration with CASA  
  > "Calibration was performed with the CASA software package, and data analysis with GILDAS." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C279 and 3C273 for bandpass and absolute flux; 4.26 Jy adopted for J0854+201 at 272.4 GHz  
  > "A flux of 4.26 Jy was adopted as reference for J0854+201 at 272.4 GHz" (Observations)
- flux scale uncertainty: ~8%  
  > "We estimate an uncertainty for the flux calibration of $\sim$ 8%" (Observations)
- self calibration: iterative self-cal on compact SiS v=1 J=15-14 source  
  > "this standard calibration was subsequently improved by iterative self-calibration on the highly compact, bright source at the origin of vibrationally excited SiS emission" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "Imaging restoration was made with moderate robust weighting (with a 0.5 robustness value) for all the available channels" (Observations)
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
- final beam: 0.6"x0.5"  
  > "The final synthetic beam is 0.6"x0.5"" (Observations)
- final rms: ~5 mJy/beam per channel; 2 mJy/beam continuum  
  > "the r.m.s. per channel is $\sim$5 mJy/Beam." (Observations)

### Inherited from earlier work

- Chemistry and CSE structure (temperature, dust opacity, velocity profiles) taken from earlier models  
  > "its gas/dust temperatures, dust opacity, and radial velocity profiles are taken from (cite: Fonfria2008), (cite: agundez2012) and (cite: daniel2012)" (Radiative Transfer and Chemical Modeling) [from (cite: Fonfria2008), (cite: agundez2012), (cite: daniel2012)]
- Non-local radiative transfer code  
  > "we performed non–local radiative transfer (RT) calculations with the code described in (cite: daniel2008)" (Radiative Transfer and Chemical Modeling) [from (cite: daniel2008)]

### Not stated but needed to reproduce (our reading)

- Imaging task and cleaning parameters (masks, thresholds, cell and image size)
- Continuum subtraction and line-free channels
- Self-calibration solution intervals
- Numerical H2 density profile and HNC abundance profile (only shown in figures)
- Line-integration or fitting procedure for the line profiles
- CASA version

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA calibration with self-calibration on SiS v=1 emission; imaging with robust 0.5; analysis in GILDAS  
  > "Calibration was performed with the CASA software package, and data analysis with GILDAS." (Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines**: Line identification with MADEX  
  > "The line identification was made with the MADEX code (cite: Cernicharo2012)." (Line modeling and Discussion)
   - software: MADEX
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute thermochemical-equilibrium HNC abundance**: TE calculation for 1-10 R* with 21 elements and ~300 molecules  
  > "Our calculations include 21 elements and nearly 300 molecular species" (Radiative Transfer and Chemical Modeling)
   - software: TE code of Tejero & Cernicharo 1991
   - assumption: solar abundances except C raised over O by factor 1.5  
  > "We adopted solar elemental abundances (cite: asplund2009), except for C, whose abundance was increased over O by a factor of 1.5." (Radiative Transfer and Chemical Modeling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Non-local RT modeling of HNC lines and constrain H2 density**: RT with 8 vibrational states, J up to 55, l-type doubling; ~950 levels and ~8700 transitions; H2 density tuned to fit profiles  
  > "The number of energy levels considered is thus $\sim$950, which translates to a total of $\sim$8700 radiative transitions." (Radiative Transfer and Chemical Modeling)
   - software: non-local RT code (Daniel & Cernicharo 2008)
   - parameter: ro-vibrational collision rates = rotational rates scaled down by 100  
  > "They were estimated by scaling down the rotational rate coefficients by a factor of 100" (Radiative Transfer and Chemical Modeling)
   - assumption: distance 130 pc, R* = 4e13 cm, spherical symmetry  
  > "We adopt a distance to IRC+10216 of 130 pc (cite: groenewegen2012) and a radius for the star of 4$\times$10$^{13}$ cm (cite: menten2012)." (Radiative Transfer and Chemical Modeling)
   - fitting: best fit by eye (not formal)  
  > "The best fit to the data is obtained with the density profile shown by the blue curves in Figure [3](#fig3)." (Radiative Transfer and Chemical Modeling)
   - validation: tested sensitivity to rate scaling factor and IR pumping  
  > "Several runs were performed to check the effect of this assumption on the results." (Radiative Transfer and Chemical Modeling)

## Software

- **CASA** : calibration  
  > "Calibration was performed with the CASA software package" (Observations)
- **GILDAS** : data analysis  
  > "data analysis with GILDAS" (Observations)
- **MADEX** : line identification and HNC frequencies/strengths  
  > "The line identification was made with the MADEX code (cite: Cernicharo2012)." (Line modeling and Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HNC emitting region radius | ~0.06 | not stated | arcsec | 4 | the radius inferred for the emitting region is $\sim$0.06$\ensuremath{''}$ (i.e., $\simeq$ 3 stellar radii) |
| HNC abundance relative to H2 | 1e-8 to 1e-6 | range | dimensionless | 4 | $10^{-8} <$ $\chi$(HNC) $< 10^{-6}$ |
| TE HNC abundance at stellar surface | 2e-6 | not stated | relative to H2 | 3 | It is maximum at the stellar surface (2 $\times$ 10$^{-6}$ relative to H$_2$) |
| Emitting region H2 density | >5e9 | not stated | cm^-3 | 4 | $n$(H$_2$) $>$ $5\, 10^9$ cm$^{-3}$ and T$_g$ $>$ 1300 K |

## Qualitative findings

- The ALMA spectrum contains many narrow unidentified lines arising near the star  
  > "also shows a surprising large number of narrow, unidentified lines that arise in the vicinity of the star" (abstract)

## Claim tuples

- H: Vibrationally excited HNC lines probe the dust formation zone and can be explained by TE chemistry | E: Non-local RT plus TE chemistry model fitted to ALMA HNC lines | R: Lines up to ~5300 K reproduced; emission from 1-3 R* | F: HNC emission arises from a hot, dense region of about 0.06", similar in size to the IR dusty clumps | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Emitting region unresolved; higher resolution and 2D/3D modeling needed  
  > "The emitting region is still unresolved with the current observations" (Discussion)
- Caveat (inferred, ours): Density constrained by eye-fit with no uncertainties
- Caveat (inferred, ours): Collisional rates for vibrational transitions are guessed
- Caveat (inferred, ours): 1D model for a clumpy region

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: RT and TE codes are not public
- Missing: Final model profiles only in figures
- Data volume (inferred): ~10-50 GB
- Score (inferred): 2/5, Data are archival but the modeling relies on unreleased codes and unstated profiles.
- Rediscovery candidate: no, Modeling code is not available and the results are model-dependent.

## Links

- Method: (cite: daniel2008) (RT code)
- Method: (cite: Cernicharo2012) (MADEX)
- Companion: (cite: daniel2012) (Herschel HNC analysis)
- Companion: (cite: Cernicharo2011) (HCN modeling and IRAM 30-m survey)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00229.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 40,
  "rate": 0.563
 },
 "evidence_ok": true
}
```
