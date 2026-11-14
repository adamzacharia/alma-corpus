# ALMA reveals sunburn: CO dissociation around AGB stars in the globular cluster 47 Tucanae

`2015MNRAS.453.4324M` | Monthly Notices of the Royal Astronomical Society 2015 | first author: McDonald, I. | arXiv: 1508.05240 | DOI: 10.1093/mnras/stv1968

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: Is CO (2-1) emission detectable from winds of the four most luminous AGB stars in 47 Tuc, and does UV dissociation by the cluster radiation field explain a non-detection?  
  > "ALMA observations show a non-detection of carbon monoxide around the four most luminous asymptotic giant branch (AGB) stars in the globular cluster 47 Tucanae." (abstract)
- Target **47 Tuc V1, V2, V3, V8**: coordinates V1: 00 24 12.65 -72 06 39.9 (J2000); V2: 00 24 18.56 -72 07 59.0; V3: 00 25 15.96 -72 03 54.8; V8: 00 24 08.59 -72 03 54.9  
  > "the intermediate-metallicity cluster 47 Tuc (NGC 104; 4.5 kpc, [Fe/H] = –0.72 dex" (Target selection); "V1 | 00 24 12.65 | –72 06 39.9" (Table 1); z/distance 4.5 kpc  
  > "the intermediate-metallicity cluster 47 Tuc (NGC 104; 4.5 kpc, [Fe/H] = –0.72 dex" (Target selection); "V1 | 00 24 12.65 | –72 06 39.9" (Table 1); distance from Harris10; Gnedin et al. 2002  
  > "the intermediate-metallicity cluster 47 Tuc (NGC 104; 4.5 kpc, [Fe/H] = –0.72 dex" (Target selection); "V1 | 00 24 12.65 | –72 06 39.9" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00333.S
- bands: Band 6  
  > "were carried out using ALMA in receiver band 6 on the night of 2013 Nov 05 over a 1.05 h integration." (ALMA & APEX observations)
- frequencies and spectral setup: CO J=2-1 at 230.538 GHz; 3840 channels of 244.141 kHz  
  > "The correlator output consisted of 3840 channels of 244.141 kHz each." (ALMA & APEX observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 26 of 29 antennas within ~250 m of array centre; three at ~530, ~790, ~1014 m  
  > "the majority of antennae (26 of 29) were positioned within $\sim$250m of the array centre" (ALMA & APEX observations)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: 15.7 arcsec (shortest baseline 17 m)  
  > "The shortest baseline (17 m) corresponds to a maximum detectable object size of 15$\ensuremath{''}$7" (ALMA & APEX observations)
- sensitivity: ~14 mJy/beam per 0.64 km/s channel pair (V1,V3,V8); ~16 (V2)  
  > "$\sim$14 mJy beam$^{-1}$ per 0.64 km s$^{-1}$ channel pair for V1, V3 and V8, and $\sim$16 mJy beam$^{-1}$ per channel pair for V2" (ALMA & APEX observations)
- time on source: 1.05 h integration  
  > "on the night of 2013 Nov 05 over a 1.05 h integration" (ALMA & APEX observations)
- observing dates: 2013 Nov 05  
  > "on the night of 2013 Nov 05" (ALMA & APEX observations)
- pi or archival as stated: _not stated_
- Line: 12C16O J=2-1 (230.538 GHz)
- Other facility **APEX**: 4 h CO(3-2) observation of V1; no detection, limit ~0.1 Jy per 10 km/s bin  
  > "A four-hour integration on 47 Tuc V1 was made in the 345 GHz $^{12}$C$^{16}$O $J = 3 \rightarrow 2$ transition" (ALMA & APEX observations)
- External data: Stellar parameters, IR mass-loss rates, wind velocities, dust composition  
  > "mass-loss rates, wind expansion velocities, and dust condensation temperatures and mineralogies, based on modelling dust emission in infrared spectra, from (cite: MBvLZ11)" (Table 2) [from (cite: MBvLZ11)]
- External data: Reimers and SC05 efficiency parameters eta  
  > "the following efficiency parameters were derived for the median stars in globular clusters" (3.2.1) [from (cite: MZ15b)]
- External data: Post-AGB evolution model and cluster ISRF  
  > "We then take the post-AGB stellar evolution model of (cite: MZ15a)" (3.3) [from (cite: MZ15a)]

## Processing

### Calibration

- pipeline or manual: standard ALMA QA calibration  
  > "The data were processed following the standard ALMA quality assurance calibration and imaging processes." (ALMA & APEX observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (amplitude); J1924-291 bandpass; J0102-7546 phase  
  > "Neptune was used for amplitude calibration and the quasars J1924–291 and J0102–7546 for bandpass and phase calibration, respectively." (ALMA & APEX observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "using the `uvtaper` parameter set to `True` and the `outaper` option set to 1.5$^{\prime\prime}$ in CASA’s clean task" (ALMA & APEX observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: outertaper 1.5 arcsec  
  > "the `outaper` option set to 1.5$^{\prime\prime}$ in CASA’s clean task" (ALMA & APEX observations)
- cell size: 0.15 arcsec/pixel  
  > "The pixel scale in both cubes is 0.15$^{\prime\prime}$ pixel$^{-1}$." (ALMA & APEX observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes with 10-channel (3.2 km/s) and 2-channel (0.64 km/s) binning; boxcar smoothing  
  > "one with a binning of ten spectral channels (channel width: 3.2 km s$^{-1}$ bin$^{-1}$) and one with two-channel binning (0.64 km s$^{-1}$ bin$^{-1}$)" (ALMA & APEX observations)
- final beam: restoring beam 2"x2"  
  > "a restoring beam of $2^{\prime\prime} \times 2^{\prime\prime}$ was also applied at the CLEANing stage" (ALMA & APEX observations)
- final rms: _not stated_

### Inherited from earlier work

- Stellar and dust-wind parameters, dust composition, dust-to-gas ratio, stellar radius and condensation  
  > "[2] Following (cite: MBvLZ11)." (Table 3) [from (cite: MBvLZ11)]
- CO dissociation radius for Galactic stars  
  > "This represents a shell $\sim$22$\times$ smaller than predicted by (cite: MGH88) for a similar Galactic star." (3.4.2) [from (cite: MGH88)]

### Not stated but needed to reproduce (our reading)

- Cleaning threshold, mask, niter and weighting/robust
- CASA version
- Exact position and size of box used for upper limits and boxcar fit details
- Flux-density scale uncertainty
- Details of arepo modifications and smmol inputs beyond Table 3

## Analysis recipe

1. **search for CO(2-1) emission**: Imaged cubes; spectra from 3x3 pixel box; boxcar smoothing over velocity and width  
  > "On-source spectra were extracted using a 3$\times$3 pixel box surrounding the central source." (ALMA & APEX observations)
   - software: CASA
   - parameter: boxcar centres vLSR -50 to 0 km/s, widths 1.27 to 85 km/s  
  > "different widths, from 1.27 km s$^{-1}$ to 85 km s$^{-1}$ (4–133 channels)" (Results)
   - assumption: vexp < 20 km/s; line centre within 5 km/s of stellar velocity  
  > "We presume the expansion velocity is $v_{\rm exp} < 20$ km s$^{-1}$" (Results)
   - fitting: _not stated_
   - validation: noise checked to be Gaussian on and off source  
  > "Each spectrum was examined and found to have noise following a Gaussian distribution" (ALMA & APEX observations)
2. **expected mass-loss rates**: Reimers/SC05 scaling plus evolutionary mass budget  
  > "We can therefore expect the mass-loss rate from our four observed stars to lie in the range 1.2–3.5 $\times$ 10$^{-7}$ M$_\odot$ yr$^{-1}$." (3.2.3)
   - software: MESA
   - assumption: 0.53 Msun final WD mass; one star passes RGB tip every 80000 yr  
  > "We assume these stars will end their lives as a 0.53 M$_\odot$ white dwarf" (3.2.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **model ISRF at each star**: 3D Monte Carlo cluster model, 100 runs of 10^6 yr, post-AGB event every 80000 yr  
  > "This model was run 100 times, in order to simulate different radial distributions of the radiation sources and observed targets." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **CO dissociation radius**: arepo toy model of expanding shell with time-dependent chemistry, 50 Habing UV field  
  > "By a radius of 2.8 $\times$ 10$^{15}$ cm (0.00092 pc, or 218 R$_\ast$), 90 per cent of the CO has been dissociated." (3.4.2)
   - software: arepo
   - parameter: Mdot 3e-7 Msun/yr; shell mass 9e-4 Msun  
  > "expanding shell of gas with a total mass of 9 $\times$ 10$^{-4}$ M$_\odot$" (3.4.2)
   - assumption: [C/H] = -0.72, dust-to-gas 1:1000  
  > "We assume a dust-to-gas ratio of 1:1000 (cite: MBvLZ11)" (3.4.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **predict CO line fluxes**: smmol non-LTE ALI radiative transfer  
  > "Smmol is a spherical-geometry, non-LTE radiative transfer code which solves level populations with the accelerated lambda iteration (ALI) scheme" (3.5.1)
   - software: smmol
   - parameter: wind 8 to 11 km/s, turbulent 2 km/s  
  > "A turbulent velocity of 2 km s$^{-1}$ was adopted." (3.5.1)
   - fitting: _not stated_
   - validation: compared with observed upper limits  
  > "Smmol clearly predicts line strengths below the upper limits of our observations" (3.5.2)

## Software

- **CASA** : clean imaging  
  > "in CASA’s clean task" (ALMA & APEX observations)
- **arepo** : CO photochemistry toy model  
  > "We used the moving-mesh code arepo" (3.4.2)
- **smmol** : CO line radiative transfer  
  > "We have therefore predicted line strengths from our envelope using the smmol radiative transfer code" (3.4.2)
- **MESA** : evolutionary track  
  > "This track was generated with the mesa (Modules for Experiments in Stellar Astrophysics) stellar evolution code" (3.2.2)
- **Dusty** : dust SED models (earlier work)  
  > "using the dusty code (cite: NIE99)" (2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) flux upper limit V1 | <183 | rms 85 | mJy km/s | 1 | V1 / $<$183 / 85 / 2.1 |
| CO(2-1) flux upper limit V2 | <168 | rms 114 | mJy km/s | 1 | V2 / $<$168 / 114 / 1.4 |
| CO(2-1) flux upper limit V3 | <170 | rms 99 | mJy km/s | 1 | V3 / $<$170 / 99 / 1.7 |
| CO(2-1) flux upper limit V8 | <162 | rms 70 | mJy km/s | 1 | V8 / $<$162 / 70 / 2.3 |
| Expected mass-loss rate range | 1.2–3.5e-7 | not stated | Msun/yr | 2 | in the range 1.2–3.5 $\times$ 10$^{-7}$ M$_\odot$ yr$^{-1}$ |
| Radius where 90% CO dissociated (V1 model) | 2.8e15 cm (0.00092 pc, 218 R*) | not stated | cm | 4 | By a radius of 2.8 $\times$ 10$^{15}$ cm (0.00092 pc, or 218 R$_\ast$), 90 per cent of the CO has been dissociated. |
| Predicted CO(2-1) flux V1 | 2.6 | not stated | mJy km/s | 5 | $J$ = 2$\rightarrow$1 / $<$183 $\pm$ 85$^{[2]}$ / 2.6 |
| Predicted CO(3-2) flux V1 | 6.1 | not stated | mJy km/s | 5 | $J$ = 3$\rightarrow$2 / ${\lower-1.2pt\vbox{\hbox{\rlap{$<$}\lower 5pt\vbox{\hbox{$\sim$}}}}}$2000$^{[1]}$ / 6.1 |

## Qualitative findings

- CO envelopes are truncated at a few hundred stellar radii, lines ~2 orders of magnitude below limits  
  > "We estimate that the CO envelopes will be truncated at a few hundred stellar radii from their host stars" (abstract)

## Claim tuples

- H: Do 47 Tuc AGB stars show CO(2-1) as Galactic stars would? | E: ALMA Band 6 imaging of four stars | R: No emission, limits ~<200 mJy km/s | F: Naive expectation of detection fails | **supported**
- H: Strong cluster ISRF dissociates CO close to the star | E: ISRF model, arepo chemistry, smmol | R: Shell ~22x smaller; predicted flux well below limits | F: Photodissociation explains non-detection | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Episodic mass loss, stellar self-destruction of CO, encounters, tidal disruption and halo-gas sweeping were considered and judged unlikely  
  > "we consider whether alternative processes acting on globular cluster stars may also affect the size of the CO envelope." (Appendix)
- How they decided it was enough: _not stated_
- Limitation (authors): Predicted fluxes are only order-of-magnitude estimates  
  > "We stress that these fluxes are only order-of-magnitude estimates, as many wind parameters are not accurately known." (3.5.2)
- Caveat (inferred, ours): Non-detection only; conclusions rest on models with simple temperature law
- Caveat (inferred, ours): ISRF scaled to 50 Habing in toy model
- Caveat (inferred, ours): Mass-loss expectation depends on uncertain eta

## Reproducibility

- Data public (paper): ALMA data acknowledged with project code  
  > "ADS/JAO.ALMA#2012.1.00333.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters and CASA version
- Missing: model code configurations for arepo and smmol
- Data volume (inferred): ~10-20 GB
- Score (inferred): 3/5, Public ALMA data and simple imaging, but modelling uses non-public modified codes and sparse imaging parameters.
- Rediscovery candidate: no, Main result is non-detection upper limits plus model predictions needing unreleased code.

## Links

- Method: (cite: MBvLZ11) (dust-wind modelling and stellar parameters)
- Method: (cite: Olofsson08) (CO(2-1) flux scaling relation)
- Companion: (cite: MZ15a) (ISRF and ionisation in globular clusters)
- Companion: (cite: MZ15b) (mass-loss efficiency in globular clusters)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 78,
  "stated": 46,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
