# An Extremely High Velocity Molecular Jet Surrounded by an Ionized Cavity in the Protostellar Source Serpens SMM1

`2016ApJ...823L..27H` | The Astrophysical Journal Letters 2016 | first author: Hull, Charles L. H. | arXiv: 1604.03569 | DOI: 10.3847/2041-8205/823/2/L27

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the nature of the CO jet and the ionized outflow cavity around Serpens SMM1, and what ionizes the cavity walls?  
  > "This begs the question: could the centimeter emission be from dust as well?" (Characterizing the free-free emission); "Both shocks and UV ionization could cause the free-free emission seen in the cavity around the EHV jet." (DISCUSSION)
- Target **Serpens SMM1 (SMM1-a, SMM1-b)**: coordinates SMM1-a: 18:29:49.81 +1:15:20.41 (J2000); SMM1-b: 18:29:49.67 +1:15:21.15  
  > "the brighter eastern source as SMM1-a ($\alpha_{\textrm{J2000}} =$ 18:29:49.81, $\delta_{\textrm{J2000}} =$ +1:15:20.41)" (OBSERVATIONS); "($d = 415$ pc; (cite: Dzib2010))" (INTRODUCTION); z/distance d = 415 pc  
  > "the brighter eastern source as SMM1-a ($\alpha_{\textrm{J2000}} =$ 18:29:49.81, $\delta_{\textrm{J2000}} =$ +1:15:20.41)" (OBSERVATIONS); "($d = 415$ pc; (cite: Dzib2010))" (INTRODUCTION); distance from Dzib et al. 2010  
  > "the brighter eastern source as SMM1-a ($\alpha_{\textrm{J2000}} =$ 18:29:49.81, $\delta_{\textrm{J2000}} =$ +1:15:20.41)" (OBSERVATIONS); "($d = 415$ pc; (cite: Dzib2010))" (INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00726.S
- bands: Band 6 (1.3 mm)  
  > "The 1.3 mm (Band 6) ALMA data we present include wide-band dust continuum windows" (OBSERVATIONS)
- frequencies and spectral setup: CO(2-1) window with 0.6 km/s velocity resolution  
  > "The CO($J$ = 2 $\rightarrow\,$1) window had a velocity resolution of 0.6 km s$^{-1}$" (OBSERVATIONS)
- continuum bandwidth: 1.35 GHz, ~216–232 GHz  
  > "The 1.35 GHz of dust continuum bandwidth comprise both dedicated continuum windows" (OBSERVATIONS)
- arrays: _not stated_
- configurations: two array configurations, ~0.3'' and ~1'' resolution  
  > "The ALMA observations were taken in two different array configurations[^2] on 2014 August 18 ($\sim$ 0.3$\ensuremath{''}$ angular resolution) and 2015 April 06" (OBSERVATIONS)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 0.5 mJy/beam rms in dust map  
  > "The rms noise level in the dust map is 0.5 mJy bm$^{-1}$" (OBSERVATIONS)
- time on source: _not stated_
- observing dates: 2014 August 18 and 2015 April 06  
  > "on 2014 August 18 ($\sim$ 0.3$\ensuremath{''}$ angular resolution) and 2015 April 06 ($\sim$ 1$\ensuremath{''}$ resolution)" (OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Other facility **VLA**: 4 cm (7.44 GHz) free-free emission data, from Rodriguez-Kamenetzky et al. 2016  
  > "The combined VLA C (4.5–6.5 GHz) and X (8–10 GHz) band data have an average frequency of 7.44 GHz" (OBSERVATIONS)
- External data: 7 mm VLA data used for the spectral index fit  
  > "7 mm data from the VLA from (cite: Choi2009)" (Characterizing the free-free emission) [from (cite: Choi2009)]
- External data: VLA 4 cm data  
  > "centimeter-wave data from the Karl G. Jansky Very Large Array (VLA), reported in (cite: RodriguezKamenetzky2016)" (INTRODUCTION) [from (cite: RodriguezKamenetzky2016)]
- External data: Lbol of SMM1 = 100 Lsun  
  > "$L_{\textrm{bol}}$ of SMM1 is 100 $L_\odot$ (cite: Kristensen2012)" (Cavity ionization by UV radiation) [from (cite: Kristensen2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, multi-scale, both configurations combined  
  > "was produced by using the CASA task **CLEAN** to combine the data from the two configurations using multi-scale **CLEAN** with a weighting parameter of robust = 0." (OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: continuum robust = 0; CO robust = 2  
  > "were produced with a weighting parameter of robust = 2" (OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: maps smoothed with 1'' circular Gaussian for flux fitting  
  > "we smoothed all of the maps with a circular Gaussian with a FWHM of 1$\ensuremath{''}$" (footnote 3)
- final beam: continuum 0.36''x0.30'' PA -60 deg; CO 0.55''x0.45'' PA -53 deg  
  > "the final synthesized beam is $0.36\ensuremath{''}\times0.30\ensuremath{''}$ at a position angle of –60$\degree$." (OBSERVATIONS)
- final rms: 0.5 mJy/beam (continuum)  
  > "The rms noise level in the dust map is 0.5 mJy bm$^{-1}$" (OBSERVATIONS)

### Inherited from earlier work

- VLA data details  
  > "(see (cite: RodriguezKamenetzky2016) for details)" (OBSERVATIONS) [from (cite: RodriguezKamenetzky2016)]
- Component naming SMM1-a/b  
  > "Following (cite: Choi2009) and (cite: Dionatos2014) we will refer to the brighter eastern source as SMM1-a" (OBSERVATIONS) [from (cite: Choi2009), (cite: Dionatos2014)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- flux/bandpass/gain calibrators
- multiscale scales, cell and image size, masks
- continuum line-free channels
- CLEAN threshold
- spectral index fit method
- VLA 7 mm flux values

## Analysis recipe

1. **image continuum and CO**: CASA CLEAN multi-scale combining two configurations  
  > "using the CASA task **CLEAN** to combine the data from the two configurations using multi-scale **CLEAN**" (OBSERVATIONS)
   - software: CASA
   - parameter: robust = 0 continuum, robust = 2 CO  
  > "were produced with a weighting parameter of robust = 2" (OBSERVATIONS)
   - fitting: _not stated_
   - validation: visibility weights inspected before combining  
  > "We carefully inspected the weights from both datasets before combining the data to ensure that they were applied properly." (footnote 2)
2. **spectral index of cavity emission**: fit fluxes at 1.3 mm, 7 mm and 4 cm summed in two 1'' circular areas on cavity lobes, after smoothing to 1''  
  > "The fluxes were calculated by summing the fluxes in two circular 1$\ensuremath{''}$ areas placed on the northern and southern cavity lobes." (footnote 3)
   - assumption: 1.3 mm emission all dust; dust spectral index fixed at 3.2  
  > "We assumed the 1.3 mm emission was all from dust, and fixed the dust emission spectral index to a conservative value of 3.2" (Characterizing the free-free emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Lyman continuum photon rate and UV ionization test**: N_Ly formula (Rubin 1968) compared with FUV luminosities of T Tauri stars  
  > "The rate of ionizing, Lyman-continuum photons required to sustain a given amount of free-free emission is as follows (cite: Rubin1968; MartinHernandez2003):" (Cavity ionization by UV radiation)
   - parameter: S=2 mJy at 7.44 GHz  
  > "integrated flux density of $S_{\nu}$ $\approx$ 2 mJy at $\nu = 7.44$ GHz" (Cavity ionization by UV radiation)
   - assumption: d = 415 pc, Te = 10,000 K, purely 13.6 eV photons  
  > "Assuming a distance to the source $d = 415$ pc, an electron temperature $T_{e} = 10,000$ K" (Cavity ionization by UV radiation)
   - fitting: _not stated_
   - validation: _not stated_
4. **recombination time vs precession period**: t_cool = (n_e alpha)^-1 compared with 20 yr precession  
  > "The recombination time $t_{\textrm{cool}} = \left(n_e \alpha\right)^{-1}$" (Cavity ionization by the precessing jet)
   - assumption: Te ~ 1e4 K, ne >~ 1e4 cm^-3  
  > "For $T_e \sim 10^4$ K (the typical temperature of an HII region) and $n_e \ensuremath{\gtrsim} 10^4$ cm$^{-3}$" (Cavity ionization by the precessing jet)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN imaging  
  > "was produced by using the CASA task **CLEAN**" (OBSERVATIONS)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO jet velocity relative to vLSR | ~30–80 | not stated | km/s | 1 | one-sided, redshifted EHV CO jet ($\sim$ 30–80 km s$^{-1}$ relative to SMM1’s $v_{\textrm{LSR}}$ = 9 km s$^{-1}$) |
| Lyman continuum luminosity needed | 6.9e32 | not stated | erg/s | 3 | $L_{\textrm{Ly-cont}} \approx 6.9 \times 10^{32}$ erg s$^{-1}$ |
| L_FUV/L_bol | ~0.1 | not stated | dimensionless | 3 | thus $L_{\textrm{FUV}} / L_{\textrm{bol}} \sim 0.1$ |
| UV attenuation at n=3000 cm^-3 | tau_UV ≈ 0.06 (6%) | not stated | dimensionless | 3 | This corresponds to an optical depth in the UV of $\tau_{\textrm{UV}} \approx 0.06$ |
| recombination time | within a factor of 2 of the precession period (~8 yr at 1e4 K, 1e4 cm^-3) | not stated | yr | 4 | the recombination timescale is within a factor of 2 of the precession period |

## Qualitative findings

- 4 cm emission in the cavity is dominated by free-free emission  
  > "Even in this conservative case the 4 cm flux is clearly dominated by free-free emission" (Characterizing the free-free emission)

## Claim tuples

- H: Is the cm emission from the cavity free-free rather than dust? | E: Fit fluxes at 1.3 mm, 7 mm, 4 cm with dust index fixed at 3.2 | R: 4 cm flux dominated by free-free | F: Cavity walls are ionized | **supported**
- H: Can UV photons from accretion ionize the cavity? | E: Compare required Lyman continuum with FUV luminosities of T Tauri stars | R: L_FUV/L_bol ~0.1 and low attenuation | F: UV ionization plausible | **supported**
- H: Can the precessing jet ionize the walls? | E: Compare recombination time with 20 yr precession | R: within factor of 2 | F: plausible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Wide-angle wind shocks considered but not detected; discussed qualitatively  
  > "the ionization in the cavity could be caused by shocking of material from a (fast and undetected) wide-angle wind with the cavity walls" (Cavity ionization by a wide-angle wind)
- How they decided it was enough: _not stated_
- Limitation (authors): Lyman continuum equation ignores optical depth  
  > "Note that Equation [\[eqn:UV\]](#eqn:UV) does not take optical depth into account." (Cavity ionization by UV radiation)
- Caveat (inferred, ours): Mechanisms are only shown to be plausible, not discriminated
- Caveat (inferred, ours): Spectral index fit has few points and a fixed dust index
- Caveat (inferred, ours): Cavity density is assumed from other work

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details and CASA version
- Missing: Imaging parameters
- Missing: VLA 7 mm and 4 cm maps
- Missing: Flux values used in the fit
- Data volume (inferred): ~50-100 GB for two ALMA execution blocks
- Score (inferred): 3/5, Data are linked to a project code, but calibration and imaging details are sparse and the VLA data are external.
- Rediscovery candidate: no, Imaging recipe is incomplete and the main results are mostly qualitative or morphological.

## Links

- Companion: (cite: RodriguezKamenetzky2016) (Source of the VLA data and the precession model)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 36,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
