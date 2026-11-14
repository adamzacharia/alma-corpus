# Chronology of Episodic Accretion in Protostars—An ALMA Survey of the CO and H<SUB>2</SUB>O Snowlines

`2019ApJ...884..149H` | The Astrophysical Journal 2019 | first author: Hsieh, Tien-Hao | arXiv: 1909.02706 | DOI: 10.3847/1538-4357/ab425a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Do chemical snowline tracers (N2H+ for CO, HCO+ for H2O) reveal past accretion bursts in Perseus protostars, and how does burst frequency change from Class 0 to Class I?  
  > "A snowline location at a much larger radius than that expected from the current luminosity suggests that an accretion burst has occurred in the past which has shifted the snowline outward." (abstract)
- Target **39 Class 0/I protostars in Perseus (Per-emb-2 to Per-emb-65)**: coordinates Table 1 lists R.A./Dec for each source (Gaussian fit to 1.2 mm continuum)  
  > "We selected 39 protostars from (cite: du15) in Perseus ($d=293$ pc, (cite: or18))" (2.1 Sample); z/distance 293 pc  
  > "We selected 39 protostars from (cite: du15) in Perseus ($d=293$ pc, (cite: or18))" (2.1 Sample); distance from Ortiz-León et al. 2018 (cite: or18)  
  > "We selected 39 protostars from (cite: du15) in Perseus ($d=293$ pc, (cite: or18))" (2.1 Sample)

## Data provenance

- ALMA projects: 2017.1.01693.S, 2015.1.01576.S
- bands: _not stated_
- frequencies and spectral setup: N2H+ channel width 30 kHz (~0.1 km/s); HCO+ 30.5 kHz (~0.03 km/s) averaged to 0.1 km/s  
  > "were 30.5 kHz ($\sim0.03~{\rm km~s^{-1}}$) and were averaged to 0.1 km s$^{-1}$ when imaging" (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- continuum bandwidth: centered at 268 GHz, ~1.85 GHz bandwidth  
  > "The window for continuum emission was centered at 268 GHz with a bandwidth of $\sim1.85$ GHz." (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- arrays: _not stated_
- configurations: N2H+: C43-4; HCO+ and continuum: C43-5  
  > "With the C43-4 configuration, the resulting beam size was $\sim2.4\ensuremath{''}\times1.5\ensuremath{''}$ using natural weighting." (2.2 N2H+ (1-0) observation); "The array configuration was C43-5" (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- baselines: _not stated_
- angular resolution: N2H+ ~2.4"x1.5" (natural); HCO+ 0.45"x0.30" natural, 0.33"x0.22" uniform  
  > "resulting in a beam size of $0.45\ensuremath{''}\times0.30\ensuremath{''}$ using natural weighting and $0.33\ensuremath{''}\times0.22\ensuremath{''}$ using uniform weighting" (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- max recoverable scale: ~12" (N2H+); ~2.6" (HCO+)  
  > "The largest scale covered is $\sim12\ensuremath{''}$." (2.2 N2H+ (1-0) observation); "The largest scale covered is $\sim2.6\ensuremath{''}$." (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- sensitivity: N2H+ ~13 mJy/beam at 0.1 km/s; HCO+ ~8-13 mJy/beam at 0.1 km/s  
  > "resulting in an rms noise level of $\sim13$ mJy beam$^{-1}$ at a spectral resolution of 0.1 km s$^{-1}$" (2.2 N2H+ (1-0) observation); "The rms noise level at a spectral resolution of 0.1 km s$^{-1}$ is $\sim8-13$ mJy beam$^{-1}$ depending on the weighting." (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- time on source: ~7.5 min per source (N2H+); ~12 min per source (HCO+)  
  > "The on-source time toward each source was $\sim7.5$ min" (2.2 N2H+ (1-0) observation); "The integration time is $\sim12$ min for each source." (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- observing dates: N2H+: 2018 March-April; HCO+: 2018 September  
  > "from 2018 March to 2018 April using ALMA" (2.2 N2H+ (1-0) observation); "in 2018 September during the same project" (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- pi or archival as stated: Own Cycle 5 program (PI Hsieh) plus earlier project 2015.1.01576.S for three targets  
  > "The N$_2$H$^+$ ($1-0$) data for the remaining three targets are taken from an earlier ALMA project (2015.1.01576.S)" (2.2 N2H+ (1-0) observation)
- Line: N2H+ J=1-0 (not stated)
- Line: HCO+ J=3-2 (not stated)
- Line: CH3OH 2(0,2)-1(-1,1) (254.015377 GHz)
- External data: Bolometric temperatures and luminosities, scaled to 293 pc  
  > "The bolometric temperature ($T_{\rm bol}$) and luminosity ($L_{\rm bol}$) are taken from (cite: du15)" (Table 1 notes) [from Dunham et al. 2015 (cite: du15)]
- External data: Outflow position angles  
  > "The position angle (P.A.) of the outflow axis is taken from the corresponding references." (Table 1 notes) [from Refs 1-11 in Table 1 (e.g. cite: st18; to16)]
- External data: Refreeze-out timescale formula  
  > "from (cite: vi12) and (cite: vi15)" (5.2.1 Evolution of burst frequency) [from Visser & Bergin 2012; Visser et al. 2015]
- External data: CO binding energy 1307 K  
  > "we use binding energies of 1307 K for CO ((cite: no12), measured from amorphous water ice)" (4.4.2 Dependence of the physical and chemical models) [from Noble et al. 2012 (cite: no12)]
- Simulation/model as data: MHW19 model grid: RADMC3D temperature, UMIST RATE12 static chemistry, Ulrich envelope with outflow cavity, line images for luminosities 0.01-200 Lsun  
  > "RADMC3D (cite: du12) is employed to calculate the temperature profile with a given central luminosity from 0.01 to 200 $L_\odot$." (4.2 MHW19 models)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0237+2848 or J0238+1636 (N2H+); J0237+2848 (HCO+)  
  > "The flux and bandpass calibrators were J0237+2848 for three executions and J0238+1636 for the remaining two executions." (2.2 N2H+ (1-0) observation)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural or uniform weighting depending on S/N (HCO+); natural (N2H+)  
  > "for each source, we choose the weighting based on the S/N of the image: uniform weighting is used for better detected sources" (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: HCO+ integrated over velocity ranges avoiding optically thick central channels, with continuum subtraction  
  > "we integrated the velocity ranges excluding the central channels in between the peak of the blue and red-shifted emission" (Appendix A)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Spectra averaged to 0.1 km/s channels  
  > "were averaged to 0.1 km s$^{-1}$ when imaging" (2.3 HCO+ (3-2) and 1.2 mm continuum observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- MHW19 model framework (grid, chemistry) from a paper in preparation  
  > "(Murillo, N. M, in prep., hereafter MHW19)" (4.2 MHW19 models) [from Murillo et al., in prep.]
- Refreeze-out timescales of 1000 yr (H2O) and 10,000 yr (CO)  
  > "Here we assume $\tau_{\rm fr}$ is 10,000 yr for CO and 1000 yr for (cite: vi15)." (5.2.1 Evolution of burst frequency) [from (cite: vi15)]
- T_bol=70 K boundary for Class 0/I  
  > "We use $T_{\rm bol}=70~K$ (cite: ev09) as a boundary to classify Class 0 and Class I sources." (Table 1 notes) [from (cite: ev09)]

### Not stated but needed to reproduce (our reading)

- Self-consistent CASA version and pipeline/manual calibration details
- Robust/uv taper, cell and image sizes, clean thresholds
- Rest frequencies of N2H+ and HCO+ and spectral window layout
- Exact biconical mask angle for each source
- MHW19 model grid and density parameters (not published)
- Flux calibration scale uncertainty

## Analysis recipe

1. **Measure continuum positions and fluxes**: Gaussian fitting of 1.2 mm continuum images  
  > "The source coordinates are obtained by a Gaussian fitting for the 1.2 mm images" (Table 1 notes)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make integrated intensity maps**: N2H+ integrated over all seven hyperfine components; HCO+ integrated avoiding optically thick central velocities  
  > "we integrated the emission from all seven hyperfine components in N$_2$H$^+$ ($1-0$)" (3.2 N2H+ maps)
   - software: CASA
   - parameter: Velocity ranges per source in Table 2  
  > "We integrated the line emission excluding the optically thick region near the systemic velocity" (3.3 HCO+ maps)
   - fitting: _not stated_
   - validation: Compared four map types with and without continuum subtraction (Appendix A)  
  > "shows the images of five selected targets with four types of maps for comparison which are (1) normal integration without continuum subtraction, (2) normal integration with continuum subtraction" (Appendix A (A. Comparison of continuum subtracted maps))
3. **Measure emission peak radii**: Biconical mask excludes outflow region; local maxima identified; radius is average distance of one or two peaks; uncertainty at least half-beam  
  > "we employ a biconical mask to filter out the outflow contaminated region" (4.1 The peak radii in the integrated intensity maps); "If only one peak is identified, the uncertainty is taken as the half-beam size." (4.1 The peak radii in the integrated intensity maps)
   - parameter: Mask excludes position angles smaller than 35-85 deg from the outflow axis  
  > "the region with a position angle smaller than $35-85\ensuremath{^\circ}$ from the outflow axis is excluded" (4.1 The peak radii in the integrated intensity maps)
   - fitting: _not stated_
   - validation: Intensity profiles and CH3OH extent checked against HCO+ peaks  
  > "The spatial extent of emission is broadly within the radius of the measured peak." (4.1 The peak radii in the integrated intensity maps)
4. **Model snowline peak radius vs luminosity**: RADMC3D temperature, UMIST RATE12 chemistry, RADMC3D line images convolved to observed beams, measured peaks at several inclinations  
  > "For a quantitative comparison between the model and observation, we measure the molecular peak radii from the models with different luminosities at different inclination angles" (4.2 MHW19 models)
   - software: RADMC-3D, CASA simobserve
   - parameter: Inclinations 15, 25, 45, 65, 75 deg  
  > "We make the images with inclination angles of 15$^\circ$, 25$^\circ$, 45$^\circ$, 65$^\circ$, and 75$^\circ$" (Appendix B)
   - assumption: Abundances of CO, N2H2 and H2O relative to H2 of 2e-4, 1e-4, 2e-4; cosmic-ray rate 1.2e-17 s-1; no disk; CO binding energy 1307 K  
  > "A constant cosmic-ray ionization rate of appropriate for the interstellar medium, $1.2\times10^{-17}~{\rm s^{-1}}$, is adopted." (4.2 MHW19 models)
   - fitting: _not stated_
   - validation: Per-emb-27 and 44 (in burst) used as calibrators for the model curve  
  > "These burst-phase sources can be used as calibrators for the model." (5.1 Sources in the burst phase)
5. **Derive burst luminosities and identify post-burst sources**: Compare peak radius with the model at i=45 deg (25-75 deg as uncertainty); post-burst if L_burst > L_bol  
  > "we derive the burst luminosity by comparing the measured peak radius to the model at an inclination angle of 45$^\circ$ and use the angle from $25\ensuremath{^\circ}-75\ensuremath{^\circ}$ as the uncertainty" (4.3 Identification of post-burst sources)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive burst frequency and mass accretion rates**: Post-burst fractions with binomial uncertainties give intervals as refreeze time over fraction; Macc from L_acc=GMMdot/R  
  > "If we assume that $L_{\rm burst}=L_{\rm acc}$, the accretion luminosity, we derive the mass accretion rate" (5.2.2 Mass accretion rate)
   - assumption: R=3 Rsun, M_star=0.25 Msun, tau_fr 10,000 yr (CO) and 1000 yr (H2O)  
  > "$R$ is the protostar radius (assumed to be 3 $R_\odot$, (cite: du10)), and $M_{\rm star}$ is the mass of the central source (assumed to be $0.25~M_\odot$" (5.2.2 Mass accretion rate)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction and simobserve for model images  
  > "*Software:* CASA (cite: mc07), RADMC-3D (cite: du12), Astropy (cite: as13), APLpy (cite: ro12)" (Software)
- **RADMC-3D** : Temperature and line radiative transfer  
  > "RADMC3D[^1] (cite: du12) is employed to calculate the temperature profile" (4.2 MHW19 models)
- **Astropy** : Listed in software  
  > "*Software:* CASA (cite: mc07), RADMC-3D (cite: du12), Astropy (cite: as13), APLpy (cite: ro12)" (Software)
- **APLpy** : Plotting  
  > "*Software:* CASA (cite: mc07), RADMC-3D (cite: du12), Astropy (cite: as13), APLpy (cite: ro12)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Post-burst fraction of Class 0 from HCO+ (H2O) | 58 | ±24% | % | 6 | we identify $58\pm24$% of Class 0 objects and $20\pm16$% of Class I objects are post-burst sources |
| Post-burst fraction of Class I from HCO+ | 20 | ±16% | % | 6 | we identify $58\pm24$% of Class 0 objects and $20\pm16$% of Class I objects are post-burst sources |
| Post-burst fraction of Class I from N2H+ (CO) | 90 | ±9% | % | 6 | we find $100\pm0$% of Class 0 objects are post-burst sources and $90\pm9$% of Class I objects are post-burst sources |
| Burst interval Class 0 (L_burst>10 Lsun, HCO+) | ~2400 | not stated | yr | 6 | $41\pm24\%$ of post-burst sources in Class 0 with an interval of $\sim$2,400 yr |
| Burst interval Class I (L_burst>10 Lsun, HCO+) | ~8000 | not stated | yr | 6 | $12\pm10\%$ of post-burst sources in Class I with an interval of $\sim$8,000 yr for Class I |
| Median burst-phase accretion rate (N2H+; HCO+) | ~7.6e-6; ~1.6e-5 | std dev ~(5.8-8.8)e-6 | Msun/yr | 6 | The median is $\sim7.6\times10^{-6}~{M_\odot~{\rm yr}^{-1}}$ from and $\sim1.6\times10^{-5}~{M_\odot~{\rm yr}^{-1}}$ from |
| Accumulated mass in bursts, Class 0 | ~0.06-0.19 | not stated | Msun | 6 | the protostar would accumulate $\sim0.06-0.19~{M_\odot}$ at the Class 0 stage and $\sim0.04-0.12~{M_\odot}$ at the Class I stage |
| Burst luminosities | ~10-100 | not stated | Lsun | 5 | The accretion luminosities during the past bursts are found to be $\sim10-100~L_\odot$. |

## Qualitative findings

- Nearly all sources have N2H+ snowline radii exceeding those expected from current luminosity; fewer from HCO+, with fewer in Class I.  
  > "We identified 18/18 Class 0 and 9/10 Class I post-burst sources from , and 7/17 Class 0 and 1/8 Class I post-burst sources from ." (abstract)

## Claim tuples

- H: Past accretion bursts are traceable via CO and H2O snowline displacement | E: Compare N2H+ and HCO+ peak radii to model radii at current Lbol | R: Most sources have peak radii beyond expectation (CO: 27/28; H2O: 8/25) | F: Many protostars are post-burst sources | **supported**
- H: Burst frequency evolves from Class 0 to Class I | E: Post-burst fractions converted to intervals with refreeze-out times | R: Interval 2400 yr (Class 0) vs 8000 yr (Class I) from H2O | F: Burst frequency decreases, though disk evolution is an alternative | **partially**
- H: Bursts account for stellar mass assembly | E: Combine burst accretion rates and intervals | R: 0.1-0.3 Msun accumulated in bursts | F: Bursts alone insufficient; quiescent accretion or super bursts needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Chemical tracers probe thermal history over longer timescales than direct luminosity monitoring  
  > "Chemical tracers are sensitive to the thermal history and can be used to probe past luminosity outbursts over a much longer timescale than direct observations of the luminosity" (1 Introduction)
- Alternative: Disk model rejected for simplicity; no-disk model gives conservative lower limits on burst luminosity  
  > "To keep the model simple, we chose to use the no-disk model." (4.4.2 Dependence of the physical and chemical models)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk evolution could shrink snowline radii in Class I, so the decreasing burst frequency may not be robust  
  > "our conclusion that the burst frequency decreases from the Class 0 to the Class I stage might in turn not be robust" (5.2.1 Evolution of burst frequency)
- Limitation (authors): Optical depth of continuum and line may bias HCO+ snowline radii  
  > "future observations with a resolution sufficient to resolve the continuum source or more warm-gas tracers are required to completely rule out the optical-depth issue" (4.4.1 Effect of optical depth for probing the snowline)
- Caveat (inferred, ours): Results rest on unpublished MHW19 models with a single geometry and chemical assumptions
- Caveat (inferred, ours): HCO+ snowline radii are mostly below half-beam, giving many upper limits
- Caveat (inferred, ours): Model degeneracy with inclination, binding energy and density
- Caveat (inferred, ours): Sample restricted after excluding sources
- Caveat (inferred, ours): Refreeze-out timescales assumed

## Reproducibility

- Data public (paper): Project codes given; ALMA archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01693.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: MHW19 model grids and parameters
- Missing: Imaging parameters (robust, cell, image size)
- Missing: CASA version and calibration procedure
- Missing: Per-source mask angles
- Data volume (inferred): ~50-200 GB raw for two Cycle 5 programs with 39 short-duration targets
- Score (inferred): 3/5, Public data and clear analysis outline, but reliant on unpublished models and missing imaging details.
- Rediscovery candidate: no, Main results depend on the unpublished MHW19 model grid and unspecified imaging/mask choices.

## Links

- Method: Hsieh et al. 2018 (cite: hs18) (Earlier N2H+ snowline analysis of VeLLOs)
- Method: Visser et al. 2015 (cite: vi15) (Refreeze-out timescales)
- Companion: Murillo et al., in prep. (MHW19) (Model framework and CH3OH discussion)
- Related: MASSES
- Related: COMPLETE
- Related: VANDAM
- Related: JCMT transient survey

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 49,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
