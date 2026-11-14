# Global collapse of molecular clouds as a formation mechanism for the most massive stars

`2013A&A...555A.112P` | Astronomy and Astrophysics 2013 | first author: Peretto, N. | arXiv: 1307.2590 | DOI: 10.1051/0004-6361/201321318

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Does the kinematics of the dense gas in the IRDC SDC335 indicate global collapse that builds up massive cores, as opposed to primordial fragmentation?  
  > "The goal of this paper is to map the dense gas kinematics of SDC335 and analyse it in the context of massive star formation scenarios." (Introduction)
- Target **SDC335.579-0.292 (MM1, MM2)**: coordinates MM1: RA 16h30m58.76s, Dec -48d43m53.4s (J2000); MM2: RA 16h30m57.26s, Dec -48d43m39.7s  
  > "a massive infrared dark cloud (IRDC) located at a distance of 3.25 kpc from the Sun (distance obtained using the (cite: reid2009) model)" (Introduction); "which have J2000 coordinates (RA: 16$^h$30$^m$58.76$^s$; Dec: -48$^\circ$43$^\prime$53.4$^{\prime\prime}$)" (3.2 Dense cores); z/distance 3.25 kpc  
  > "a massive infrared dark cloud (IRDC) located at a distance of 3.25 kpc from the Sun (distance obtained using the (cite: reid2009) model)" (Introduction); "which have J2000 coordinates (RA: 16$^h$30$^m$58.76$^s$; Dec: -48$^\circ$43$^\prime$53.4$^{\prime\prime}$)" (3.2 Dense cores); distance from Reid et al. 2009 model  
  > "a massive infrared dark cloud (IRDC) located at a distance of 3.25 kpc from the Sun (distance obtained using the (cite: reid2009) model)" (Introduction); "which have J2000 coordinates (RA: 16$^h$30$^m$58.76$^s$; Dec: -48$^\circ$43$^\prime$53.4$^{\prime\prime}$)" (3.2 Dense cores)

## Data provenance

- ALMA projects: 2011.0.00474.S
- bands: 3 mm (3.2 mm continuum)  
  > "In September and November 2011 we observed SDC335 at 3mm wavelength with the 16 antennas of ALMA (Cycle 0) in its compact configuration." (2.3 ALMA observations)
- frequencies and spectral setup: 3.2mm continuum, CH3OH(13-12) and N2H+(1-0), ~0.1 km/s resolution; 11-pointing mosaic  
  > "We simultaneously observed the 3.2mm dust continuum, along with the CH$_3$OH(13-12) and N$_2$H$^+$(1-0) transitions at a spectral resolution of $\sim0.1$ km/s." (2.3 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 16 antennas, compact configuration  
  > "with the 16 antennas of ALMA (Cycle 0) in its compact configuration" (2.3 ALMA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 5.6" x 4.0", PA +97 deg  
  > "The synthesized beam is $5.6\hbox{$^{\prime\prime}$}\times4.0\hbox{$^{\prime\prime}$}$ with a position angle of $+97\hbox{$^\circ$}$." (2.3 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.4 mJy/beam; line rms 14 mJy/beam (~0.08 K)  
  > "The rms noise in the continuum is 0.4 mJy/beam, while for the line we reach an rms sensitivity of 14 mJy/beam ($\sim0.08$ K)." (2.3 ALMA observations)
- time on source: _not stated_
- observing dates: September and November 2011  
  > "In September and November 2011 we observed SDC335 at 3mm wavelength" (2.3 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CH3OH 13-12 (105.063761 GHz)
- Line: N2H+ 1-0 (not stated)
- Line: HCO+ 1-0 (Mopra) (not stated)
- Other facility **Mopra 22m**: HCO+, H13CO+, N2H+ (1-0) maps, used as ALMA short spacings  
  > "In May 2010 we observed SDC335 with the ATNF Mopra 22m single-dish telescope." (2.2 Mopra observations)
- Other facility **Herschel Hi-GAL**: 160 and 350 um data for column density and temperature  
  > "We also used the PACS (cite: poglitsch2010) 160$\mu$m and SPIRE (cite: griffin2010) 350$\mu$m *Herschel* (cite: pilbratt2010) data from the Hi-GAL survey" (2.1)
- Other facility **Spitzer GLIMPSE**: 8 um extinction and 4.5 um images  
  > "We used publicly available[^1] *Spitzer* GLIMPSE data (cite: churchwell2009)." (2.1)
- External data: 6cm free-free non-detection limit of 0.2 mJy  
  > "no 6cm free-free emission has been detected towards SDC335 down to a limit of 0.2 mJy (cite: garay2002)" (Introduction) [from (cite: garay2002)]
- External data: 8um extinction mass map of SDC335  
  > "we performed an independent mass measurement directly using the 8$\mu$m extinction map from (cite: peretto2009)" (3.1) [from (cite: peretto2009)]
- Simulation/model as data: RAMSES MHD simulation of a 10000 Msun turbulent magnetised cloud (DR21 model) used for comparison  
  > "a snapshot of a published MHD simulation modelling the evolution of a turbulent and magnetized 10 000 M$_{\odot}$ cloud" (5.5)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (flux), B1600-445 (phase)  
  > "Flux and phase calibration were performed on Neptune and B1600-445, respectively." (2.3 ALMA observations)
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
- array combination: Mopra single-dish data combined with ALMA using GILDAS; combined cube rms 0.14 Jy/beam (~0.8 K)  
  > "we used the Mopra single-dish data to provide the short-spacing information, for which we used the GILDAS[^3] software." (2.3 ALMA observations)
- smoothing: _not stated_
- final beam: 5.6" x 4.0", PA +97 deg  
  > "The synthesized beam is $5.6\hbox{$^{\prime\prime}$}\times4.0\hbox{$^{\prime\prime}$}$ with a position angle of $+97\hbox{$^\circ$}$." (2.3 ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- Herschel data reduction with ROMAGAL map making  
  > "These data were reduced as described in (cite: traficante2011), using the ROMAGAL map making algorithm." (2.1) [from (cite: traficante2011)]
- Dust opacity law kappa=0.1(lambda/0.3mm)^-beta cm2/g with beta=2  
  > "Using the dust opacity law (cite: hildebrand1983; beckwith1990)" (3.1) [from (cite: hildebrand1983; beckwith1990)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging parameters (weighting, cleaning, masks)
- Line-free channels and continuum subtraction method
- Combination parameters for Mopra and ALMA short spacing in GILDAS
- Mopra data reduction details
- RATRAN grid details and fit criteria for infall velocity
- Herschel colour-temperature conversion from 160/350 ratio
- Details of ALMA fit regions for N2H+ hyperfine fits

## Analysis recipe

1. **Herschel column density and mass of cloud, filaments**: Temperature from 160/350um ratio, column density from 350um via modified blackbody; second map with T lowered by 2 K; masses averaged  
  > "we decided here to use the 160$\mu$m/350$\mu$m ratio map[^4] of SDC335 as an indicator of the dust temperature" (3.1)
   - assumption: mu=2.33, beta=2, kappa=0.1(lambda/0.3mm)^-beta cm2/g  
  > "$\mu=2.33$ is the average molecular weight" (3.1)
   - fitting: _not stated_
   - validation: Independent 8um extinction mass confirms Herschel filament masses  
  > "confirming the *Herschel* mass measurements" (3.1)
2. **Core fluxes and gas masses**: 2D Gaussian fit to 3.2mm continuum; mass from flux with Td=50 K  
  > "The results of a 2D Gaussian fit to the 3.2mm continuum emission of these compact sources give integrated fluxes of 101($\pm10$) mJy and 12($\pm2$) mJy" (3.2 Dense cores)
   - assumption: Td=50 K with factor 2 uncertainty; kappa_3.2=8.7e-4 cm2/g; dust-to-gas 1%  
  > "we adopted an intermediate dust temperature of 50 K for both MM cores" (3.2 Dense cores)
   - fitting: _not stated_
   - validation: Free-free contamination upper limits estimated, up to 30% for MM1  
  > "implies an upper limit on the free-free contamination of 30% of the observed 3.2mm flux" (3.2 Dense cores)
3. **Core systemic velocities and filament velocities**: Gaussian fits to CH3OH spectra; N2H+ hyperfine fitting  
  > "Gaussian fits to the methanol spectra observed at the central position of the two cores" (4.1)
   - software: GILDAS
   - fitting: Hyperfine fitting in GILDAS  
  > "the N$_2$H$^+$(1-0) hyperfine line-fitting (performed with GILDAS) gives an opacity lower than 1 everywhere in the cloud" (4.3 ALMA N2H+(1-0) cloud velocity field)
   - validation: _not stated_
4. **HCO+ abundance via RADEX**: Iterate column density to match observed Tpeak  
  > "Then we iterate on the last input parameter, i.e. the molecule column density" (4.2)
   - software: RADEX
   - assumption: Tkin 20+-5 K, density 6e4 cm-3, dispersion 1.3 km/s  
  > "the kinetic temperature ($20\pm5$ K, estimated from *Herschel* data)" (4.2)
   - fitting: _not stated_
   - validation: [HCO+]/[H13CO+] compared with expected 12C/13C  
  > "the predicted $\rm{[^{12}C]/[^{13}C]}$ is around 30 (cite: langer1993; savage2002). The value we find is about half this value, which, considering the uncertainties on these kinds of measurements, is in reasonable agreement." (4.2 Mopra HCO+(1-0) self-absorbed lines)
5. **Infall velocity via RATRAN**: Grid of 1D models varying infall velocity and dispersion, compared by reduced chi2  
  > "For each spectrum we calculated a reduced $\chi^2$ parameter representative of the quality of the fit." (5.3)
   - software: RATRAN
   - parameter: rho∝r^-1.5, T=20 K, X(HCO+)=7e-10, [HCO+]/[H13CO+]=30  
  > "a cloud-density profile $\rho\propto r^{-1.5}$, and a constant temperature profile of 20 K" (5.3)
   - fitting: grid, reduced chi2  
  > "We then ran a grid of models varying the last two input parameters, i.e., the infall velocity and the velocity dispersion." (5.3 Collapse on large scales)
   - validation: H13CO+ predictions compared in Appendix B  
  > "The corresponding H$^{13}$CO$^+$(1-0) predictions from the model are displayed in Appendix B." (5.3 Collapse on large scales)
6. **Virial parameter and infall rate**: alpha_vir=5 sigma^2 R/(GM); Mdot = N pi R^2 V rho for filaments and 4 pi R^2 V rho spherical  
  > "the total accretion rate becomes $\dot{M}_{inf}=4\pi R_{sph}^2 V_{inf}\rho_{sph}$" (5.5)
   - assumption: Non-filament gas collapses at similar infall velocity  
  > "Assuming that the remaining gas is collapsing off filaments at a similar infall velocity" (5.5)
   - fitting: _not stated_
   - validation: Comparison to MHD simulation  
  > "Overall, this simulation shows some similarities with SDC335, i.e. massive cores in the centre, the formation of filaments converging towards these cores, and a velocity field resembling the one observed in SDC335" (5.5 Large-scale velocity field and accretion rates)

## Software

- **CASA** : ALMA data reduction  
  > "The data were reduced using CASA[^2] (cite: mcmullin2007)." (2.3 ALMA observations)
- **GILDAS** : Combining Mopra and ALMA; N2H+ hyperfine fits  
  > "for which we used the GILDAS[^3] software" (2.3 ALMA observations)
- **RADEX** : HCO+ abundance  
  > "1D non-LTE RADEX radiative transfer code (cite: vandertak2007)" (4.2)
- **RATRAN** : Infall velocity modelling  
  > "we used the RATRAN 1D Monte Carlo radiative transfer code (cite: hogerheijde2000)" (5.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MM1 gas mass | 545 | +770/-385 | Msun | 2 | $M_{MM1}=545^{+770}_{-385}$ M$_{\odot}$ |
| MM2 gas mass | 65 | +92/-46 | Msun | 2 | $M_{MM2}=65^{+92}_{-46}$ M$_{\odot}$ |
| MM1 3.2mm flux | 101 | 10 | mJy | 2 | integrated fluxes of 101($\pm10$) mJy and 12($\pm2$) mJy |
| SDC335 mass | 5500 | 800 | Msun | 1 | $5.5( \pm0.8) \times10^3$ |
| Infall velocity | 0.7 | 0.2 | km/s | 5 | $V_{inf} =0.7(\pm0.2)$ km/s |
| Total mass infall rate | 2.5e-3 | 1.0e-3 | Msun/yr | 6 | $\dot{M}_{inf}=2.5(\pm1.0)\times10^{-3}$ M$_{\odot}$/yr |
| Virial parameter | 0.4 | +0.4/-0.2 | dimensionless | 6 | $\alpha_{vir}=0.4_{-0.2}^{+0.4} < 1$ |
| HCO+ abundance | 7e-10 | +8/-4 e-10 | dimensionless | 4 | $X_{HCO^+}=7^{+8}_{-4}\times10^{-10}$ |

## Qualitative findings

- Blue-shifted self-absorbed HCO+ profiles over at least 12 Mopra beams indicate global collapse  
  > "strongly suggest that SDC335 is collapsing" (4.2)

## Claim tuples

- H: MM1 is among the most massive compact cores | E: 3.2mm continuum mass compared with literature cores | R: MM1 545 Msun in 0.05 pc | F: One of the most massive compact protostellar cores | **supported**
- H: SDC335 is globally collapsing | E: HCO+ line shapes, RATRAN modelling, virial parameter | R: Vinf~0.7 km/s, alpha_vir 0.4 | F: Cloud in global collapse feeding the cores | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Rotation and expansion ruled out by blue-shifted asymmetry  
  > "already rule out the possibility of a rotating or expanding cloud" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust opacity, temperature uncertainties; 1D model cannot describe filaments  
  > "Obviously, a 1D model cannot describe the detailed kinematics of the filamentary structures observed in SDC335" (5.3)
- Caveat (inferred, ours): Core mass depends on assumed 50 K and opacity
- Caveat (inferred, ours): Single cloud; infall rate extrapolated from filaments to all gas

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: GILDAS combination details
- Missing: Mopra data availability
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data are Cycle 0 and the recipe is partly described, but imaging and modelling details are missing.
- Rediscovery candidate: no, Needs Mopra data and unstated imaging parameters.

## Links

- Related: Hi-GAL
- Related: GLIMPSE

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 46,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
