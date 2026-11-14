# Detection of CH<SUP>+</SUP>, SH<SUP>+</SUP>, and their <SUP>13</SUP>C- and <SUP>34</SUP>S-isotopologues toward PKS 1830-211

`2017A&A...606A.109M` | Astronomy and Astrophysics 2017 | first author: Muller, S. | arXiv: 1707.07446 | DOI: 10.1051/0004-6361/201731405

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, milky_way_ism
- Question: Are CH+, SH+ and their 13C and 34S isotopologues detected in the z=0.89 absorber toward PKS 1830-211, and what do their column densities and ratios along the two lensed sightlines say about gas molecular fraction and isotope ratios?  
  > "Here, we report the detection of CH$^+$, SH$^+$, and their $^{13}$C- and $^{34}$S- isotopologues in the $z$=0.89 absorber located in front of the quasar PKS 1830$-$211." (Introduction)
- Target **PKS 1830-211 (z=0.89 absorber, SW and NE lensed images)**: coordinates _not stated_; z/distance absorber z=0.88582 (heliocentric); quasar z=2.5  
  > "The quasar, at $z$=2.5 ((cite: lid99)), is gravitationally lensed by the foreground absorber, a nearly face-on spiral galaxy ((cite: win02))." (Introduction); distance from Table 1 note for z=0.88582; lid99 for quasar z  
  > "The quasar, at $z$=2.5 ((cite: lid99)), is gravitationally lensed by the foreground absorber, a nearly face-on spiral galaxy ((cite: win02))." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00056.S, 2013.1.00020.S
- bands: Band 8 (~440 GHz) for CH+; Band 7 (~280 GHz) for SH+  
  > "The CH$^+$ and $^{13}$CH$^+$ $J$=1-0 transitions, redshifted to $\sim$440 GHz in ALMA band 8, were observed simultaneously on 2015 May 20." (Observations); "redshifted to $\sim$280 GHz in ALMA band 7, were observed on 2014 May 5 (two executions) and July 18 (1 execution)." (Observations)
- frequencies and spectral setup: 1.875 GHz wide spectral windows, 1.1 MHz resolution (~0.8 km/s CH+, ~1.2 km/s SH+ after Hanning smoothing)  
  > "The correlator was configured with 1.875 GHz wide spectral windows and a spectral resolution of 1.1 MHz, corresponding to a velocity resolution, after Hanning smoothing, of $\sim$0.8 km s$^{-1}$." (Observations)
- continuum bandwidth: _not stated_
- arrays: 35 antennas (CH+ tuning); 30 antennas per execution (SH+ tuning)  
  > "The array was composed of 35 antennas, resulting in a synthesized beam of $\sim$0.3$\ensuremath{''}$, full-width at half maximum (FWHM)." (Observations); "In each execution, the array was composed of 30 antennas, resulting in a final synthesized beam smaller than 0.5$\ensuremath{''}$ FWHM." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.3" (CH+); <0.5" (SH+)  
  > "The array was composed of 35 antennas, resulting in a synthesized beam of $\sim$0.3$\ensuremath{''}$, full-width at half maximum (FWHM)." (Observations)
- max recoverable scale: _not stated_
- sensitivity: SH+ NE: better than 0.2% of continuum level  
  > "Despite a sensitivity better than 0.2% of the continuum level, SH$^+$ is not detected toward the NE image." (Results)
- time on source: ~17 min (CH+); ~1 hour (SH+)  
  > "The total on-source time was about 17 minutes." (Observations); "The total on-source time comprised about 1 hour." (Observations)
- observing dates: 2015 May 20 (CH+); 2014 May 5 (two executions) and July 18 (SH+)  
  > "were observed on 2014 May 5 (two executions) and July 18 (1 execution)." (Observations)
- pi or archival as stated: _not stated_
- Line: CH+ J=1-0 (835.137504 GHz)
- Line: 13CH+ J=1-0 (830.216096 GHz)
- Line: SH+ N_J=1_2-0_1 (F=2.5-1.5 strongest) (526.048023 GHz)
- Line: 34SH+ N_J=1_2-0_1 (~525.09 GHz (J=2-1 components))
- Line: H2 18O 1_10-1_01 (547.676 GHz)
- External data: SH+ rest frequencies from laboratory measurements  
  > "The rest frequencies for the SH$^+$ $N_J$=$1_2$-$0_1$ transitions are taken from laboratory measurements by (cite: hal15)." (Laboratory spectroscopic data) [from (cite: hal15)]
- External data: CH+ and 13CH+ rest frequencies from CDMS  
  > "The CH$^+$ and $^{13}$CH$^+$ rest frequencies were taken from the Cologne Database for Molecular Spectroscopy (CDMS)" (Laboratory spectroscopic data) [from (cite: CDMS01; CDMS05)]
- External data: Dipole moments: CH+ 1.68 D; SH+ 1.28 D  
  > "We adopt the electric dipole moment $\mu_{{\rm CH}^+} = 1.68$ Debye ((cite: che07))" (Laboratory spectroscopic data) [from (cite: che07; sen85)]
- External data: HI column densities from the kinematical model  
  > "we use those derived from the source kinematical model by (cite: koo05) and given in Table [\[tab:ncol\]]" (Time variations) [from (cite: koo05)]
- External data: Column densities of other species (ArH+, OH+, H2O+, CH, HF, HCO+ etc.) and H2 in comparison table  
  > "$(b)$ (cite: hmul15a); $(c)$ (cite: mul16); $(d)$ (cite: mul14b); $(e)$ this work; $(f)$ (cite: kaw16); $(g)$ (cite: mul14a); $(h)$ (cite: mul11)" (Table 4 notes) [from hmul15a; mul16; mul14b; kaw16; mul14a; mul11]
- External data: CMB temperature 5.14 K at z=0.89  
  > "$T_\mathrm{CMB}$=5.14 K at $z$=0.89, (cite: mul13)" (Results) [from (cite: mul13)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedure; bandpass from J1924-292; gain self-calibrated on PKS 1830-211 continuum  
  > "the data calibration was done within the CASA[^1] package, following a standard procedure." (Observations); "The gain solutions were self-calibrated on the continuum of PKS 1830$-$211." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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

- Covering factor and column density method (alpha coefficients, T_rot = T_CMB) following earlier work  
  > "are calculated for a given transition $i$-$j$ for $T_\mathrm{rot}$=5.14 K (see e.g., (cite: mul14a))." (Results) [from (cite: mul14a)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Flux calibrator and flux scale uncertainty
- Phase/self-cal solution intervals
- Exact UVMULTIFIT settings and starting parameters
- Fitting algorithm, priors and initial guesses for Gaussian components
- Channel/velocity range used to normalize continuum
- Spectrum extraction for NE image continuum levels

## Analysis recipe

1. **Extract spectra toward both lensed images**: Fit two-point-source model to visibilities with UVMULTIFIT per channel  
  > "The final spectra were extracted toward both lensed images of PKS 1830$-$211 using the CASA-python task UVMULTIFIT ((cite: mar14)) and fitting a model of two point sources to the interferometric visibilities." (Observations)
   - software: CASA, UVMULTIFIT
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit absorption profiles with Gaussian velocity components**: Normalized spectra modelled as I = 1 - fc[1-exp(-sum tau_i)] with Gaussian opacity components; SH+ fit convolved with hyperfine structure, 34SH+ fitted jointly with shift delta  
  > "This profile was obtained by the fit of Gaussian velocity components convolved with the hyperfine structure." (Results)
   - parameter: fc=1 assumed unless constrained (SW CH+ ~97%)  
  > "In the absence of such constraints, we assume $f_c$=1 to derive apparent optical depths, and thus obtain lower limits to the column densities." (Results)
   - assumption: Excitation coupled to CMB, T=5.14 K  
  > "assuming that the excitation of CH$^+$ and SH$^+$ is strongly coupled to the cosmic microwave background" (Results)
   - fitting: Gaussian statistics assumed on errors; sampler not stated  
  > "For simplicity, we assume Gaussian statistics on the errors in the fit." (Column density ratios)
   - validation: Residuals at the noise level  
  > "Only three Gaussian components are required to fit the profile, leaving residuals at the level of the noise" (Results)
3. **Derive column densities**: N = alpha * integral tau dv with alpha for T_rot=5.14 K; saturated CH+ lower limit by capping tau at 3  
  > "By cutting the optical depths at a threshold of $\tau =3$, we estimate a lower limit of $6.4 \times 10^{14}$ cm$^{-2}$." (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Simultaneous fit of CH+, 13CH+ and OH+ for SW saturation correction and isotope ratio**: Single intrinsic velocity profile, three Gaussians, common fc, constant [OH+]/[CH+] ratio assumed over the SW absorption  
  > "we can perform a simultaneous fit of the CH$^+$, $^{13}$CH$^+$, and OH$^+$ spectra, using Eq. [\[eq:abs_function\]] with a single intrinsic velocity profile for all species." (Column density ratios)
   - fitting: _not stated_
   - validation: Reproduces spectra with residuals near noise  
  > "It reproduces well the spectra and leaves residuals close to the noise level." (Column density ratios)
5. **Compare SW/NE column densities and molecular fraction tracers**: Compute gamma_SW/NE and CH+/H abundances using HI and H2 from literature  
  > "(hereafter $\gamma_{\rm SW/NE}$) for a given species is a good indicator of what kind of gas it preferentially traces." (Comparison of the two lines of sight)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data calibration  
  > "the data calibration was done within the CASA[^1] package, following a standard procedure." (Observations)
- **UVMULTIFIT** : Extracting spectra of the two lensed images via visibility fitting  
  > "using the CASA-python task UVMULTIFIT ((cite: mar14))" (Observations)
- **CDMS** : Rest frequencies and spectroscopic data  
  > "taken from the Cologne Database for Molecular Spectroscopy (CDMS)" (Laboratory spectroscopic data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH+ NE total column density | 1.9e14 | not stated | cm^-2 | 3 | The total CH$^+$ column density is about $1.9 \times 10^{14}$ cm$^{-2}$. |
| CH+ SW saturation-corrected column density | 9.7e14 | not stated | cm^-2 | 4 | we derive a new “saturation-corrected” total column density for CH$^+$ of $9.7 \times 10^{14}$ cm$^{-2}$. |
| [SH+]/[34SH+] SW | 16.2 | 1.3 | dimensionless | 2 | we also find a ratio SH$^+$/$^{34}$SH$^+$ of $16.2 \pm 1.3$ |
| 34SH+ frequency shift delta | 952.5 | 1.9 | MHz | 2 | We find $\delta = 952.5 \pm 1.9$ MHz |
| [CH+]/[13CH+] SW | 97 | 6 | dimensionless | 4 | \[CH$^+$\]/\[$^{13}$CH$^+$\] $= 97 \pm 6$ |
| [CH+]/[13CH+] NE | 146 | 43 | dimensionless | 2 | yields a \[CH$^+$\]/\[$^{13}$CH$^+$\] ratio of $146 \pm 43$ |
| SH+ SW column density | 3.9e13 | not stated | cm^-2 | 3 | / SH$^+$        / 2014 $^{(e)}$      / $3.9 \times 10^{13}$    / $< 3.2\times 10^{11}$   / $> 120$              / |
| SH+ NE column density upper limit | <3.2e11 | 3 sigma | cm^-2 | 3 | This corresponds to an upper limit of $3.2 \times 10^{11}$ cm$^{-2}$ for the column density. |
| fc SW from joint fit | 97.8 | 0.3 | % | 4 | The best fit with three Gaussian components yields $fc= 97.8 \pm 0.3$ % |
| gamma_SW/NE for CH+ | 5.1 | not stated | dimensionless | 5 | / CH$^+$        / 2015 $^{(e)}$      / $9.7 \times 10^{14}$    / $1.9 \times 10^{14}$    / 5.1                  / |
| [CH+]/[SH+] SW and NE | ~25 (SW); >600 (NE) | not stated | dimensionless | 5 | $\sim 25$ toward the SW image and $> 600$ toward the NE |

## Qualitative findings

- First extragalactic detection of SH+ and first interstellar detection of 34SH+; SH+ is absent toward the NE sightline  
  > "We report the first interstellar detection of $^{34}$SH$^+$ in the same line of sight." (Summary and conclusions)

## Claim tuples

- H: Are CH+ and SH+ detectable in the z=0.89 absorber, and does SH+ differ between sightlines? | E: ALMA band 7 and 8 absorption spectra toward both lensed images | R: SH+ and 34SH+ detected SW only; SH+ NE upper limit; CH+ in both | F: SH+ resides in higher molecular fraction gas or NE conditions disfavour its formation | **supported**
- H: Does gamma_SW/NE trace molecular fraction? | E: Compare SW/NE column density ratios for many species | R: CH+ gamma=5, SH+ >120, ordered consistent with f_H2 trends | F: gamma_SW/NE is a good indicator of molecular fraction, consistent with chemical predictions | **supported**
- H: What are the 12C/13C ratios along the two sightlines? | E: Joint fits of CH+ and 13CH+ spectra | R: ~97 SW, 146 NE | F: Higher ratio in NE suggests less processed material, with uncertainty | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Covering factor unresolved; apparent opacities give lower limits for column densities  
  > "we assume $f_c$=1 to derive apparent optical depths, and thus obtain lower limits to the column densities." (Results)
- Caveat (inferred, ours): Indirect SW 12C/13C ratio depends on assumed constant [OH+]/[CH+] ratio
- Caveat (inferred, ours): Observations of different species at different epochs despite time variability
- Caveat (inferred, ours): fc assumption affects column densities
- Caveat (inferred, ours): Excitation assumed CMB-coupled

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibrator details
- Missing: Component starting values and fit algorithm
- Missing: Self-cal parameters
- Data volume (inferred): Tens of GB (two projects, several executions)
- Score (inferred): 3/5, Data public in archive and method simple, but calibration and fitting details sparse.
- Rediscovery candidate: no, Fitting details and calibration settings are insufficiently specified.

## Links

- Method: (cite: mar14) (UVMULTIFIT visibility fitting)
- Method: (cite: mul14a) (Column density and covering factor method)
- Companion: (cite: mul16) (OH+, H2O+ observations in same source)
- Companion: (cite: hmul15a) (ArH+ observations in same source)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 33,
  "rate": 0.458
 },
 "evidence_ok": true
}
```
