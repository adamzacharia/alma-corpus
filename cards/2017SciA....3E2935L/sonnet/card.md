# First detection of equatorial dark dust lane in a protostellar disk at submillimeter wavelength

`2017SciA....3E2935L` | Science Advances 2017 | first author: Lee, Chin-Fei | arXiv: 1704.08962 | DOI: 10.1126/sciadv.1602935

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Can a Class 0 protostellar disk (HH 212) be spatially resolved in submillimeter dust continuum, including its vertical structure?  
  > "Here we report ALMA observations in dust emission at $\sim$ 850 $\mu$m that clearly resolves the disk spatially." (INTRODUCTION)
- Target **HH 212 (IRAS 05413-0104)**: coordinates RA(2000)=05h43m51.4086s, Dec(2000)=-01d02m53.147s (possible source position)  
  > "HH 212 is a nearby protostellar system deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion at a distance of $\sim$ 400 pc." (INTRODUCTION); "Asterisks mark the possible source position at $\alpha_{(2000)}=05^\mathrm{h} 43^\mathrm{m} 51^\mathrm{s}_{^\textrm{.}} 4086$" (Figure 1 caption); z/distance ~400 pc  
  > "HH 212 is a nearby protostellar system deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion at a distance of $\sim$ 400 pc." (INTRODUCTION); "Asterisks mark the possible source position at $\alpha_{(2000)}=05^\mathrm{h} 43^\mathrm{m} 51^\mathrm{s}_{^\textrm{.}} 4086$" (Figure 1 caption); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00122.S, 2015.1.00024.S
- bands: Band 7 (~350 GHz), Cycles 1 and 3  
  > "Observations of the HH 212 protostellar system were carried out with ALMA in Band 7 at $\sim$ 350 GHz in Cycles 1 and 3" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 1875 MHz continuum window plus line-free channels of other windows, centered ~352 GHz  
  > "Line-free channels were extracted from all the spectral windows to make the continuum with a frequency centered at $\sim$ 352 GHz" (Observations)
- arrays: _not stated_
- configurations: C32-6 (Cycle 1); C36-7/8 (Cycle 3)  
  > "| 3 | 2015-11-05 | C36-7/8 | 45 | 44 | 78$-$16196 |" (Table S1)
- baselines: ~15 to 16200 m  
  > "with 32-45 antennas and projected baselines ranging from $\sim$ 15 to 16200 m" (Observations)
- angular resolution: 0.100x0.094 arcsec and 0.0203x0.0175 arcsec  
  > "This generates a synthesized beam of $0^{''}{\textrm{.}}0203$$\times$$0^{''}{\textrm{.}}0175$ at a P.A. of $-$65$^\circ$" (Observations)
- max recoverable scale: ~2 arcsec (high-resolution image)  
  > "only structure with a size scale greater than $\sim$ $2''$ could be filtered out in our image" (Observations)
- sensitivity: ~0.42 mJy/beam (0.1 arcsec image); ~0.08 mJy/beam (0.02 arcsec image)  
  > "a noise level of $\sim$ 0.08 mJy beam$^{-1}$ (2.2 K) (Figure 1d)" (Observations)
- time on source: ~148 minutes total  
  > "The total time on the HH 212 system is $\sim$ 148 minutes." (Observations)
- observing dates: 2015-08-29 (two executions), 2015-11-05, 2015-12-03  
  > "one on November 5 and one on December 3, during the Early Science Cycle 3 phase." (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.795991 GHz)
- Line: SiO J=8-7 (347.330631 GHz)
- Line: HCO+ J=4-3 (356.734288 GHz)
- Other facility **VLT**: H2 + 2.12 um image of jet and reflection nebula (context)  
  > "it was mapped in H$_2$ with the Very Large Telescope at $\sim$ $0^{''}{\textrm{.}}35$ resolution(cite: McCaughrean2002)" (RESULTS)
- External data: Disk spectral index ~2.6 giving beta ~0.6  
  > "Previous observations of the disk emission at 1.4 mm and 0.85 mm suggested a spectral index of $\sim$ 2.6(cite: Lee2008)" (DISCUSSION) [from (cite: Lee2008)]
- External data: Jet inclination ~4±2 deg to plane of sky  
  > "the jet has a small inclination angle of $\sim$ 4$\pm2$$^\circ$ to the plane of the sky(cite: Claussen1998; Lee2007)" (RESULTS) [from (cite: Claussen1998; Lee2007)]
- External data: Dust opacity formula/value 0.054 cm2/g at 850 um  
  > "for a dust opacity of 0.054 cm$^2$ g$^{-1}$ at 850 $\mu$m(cite: Beckwith1990)" (DISCUSSION) [from (cite: Beckwith1990)]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA; quasars as bandpass, flux and phase calibrators  
  > "The data were calibrated with the Common Astronomy Software Applications (CASA) package, with quasars as bandpass, flux, and phase calibrators" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 / J0423-0120 (see Table S4)  
  > "| 2015-08-29 | J0607-0834, 1.20 Jy | J0423-013, 1.03 Jy | J0552+0313, 0.25 Jy |" (Table S4)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 2 (natural) for 15-2000 m baselines; robust = 0.5 with all baselines  
  > "Another one used a robust factor of 0.5 (super-uniform weighting) with all the baselines, in order to resolve the disk structure." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels  
  > "Line-free channels were extracted from all the spectral windows to make the continuum" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.100x0.094 arcsec PA -25 deg; 0.0203x0.0175 arcsec PA -65 deg  
  > "a synthesized beam (resolution) of $0^{''}{\textrm{.}}100$$\times$$0^{''}{\textrm{.}}094$ at a position angle (P.A.) of $-$25$^\circ$" (Observations)
- final rms: ~0.42 mJy/beam and ~0.08 mJy/beam  
  > "a noise level of $\sim$ 0.42 mJy beam$^{-1}$ (0.44 K) (Figure 1c)" (Observations)

### Inherited from earlier work

- Earlier 0.5 arcsec 850 um continuum map of envelope/disk  
  > "Gray contours show the continuum map of the envelope/disk at 850 $\mu$m obtained with ALMA at $\sim$ $0^{''}{\textrm{.}}5$ resolution(cite: Lee2014)." (Figure 1 caption) [from (cite: Lee2014)]
- Model parameters p=2 and q=0.75 adopted from literature  
  > "We assume $p=2$ and $q=0.75$ for the disk(cite: Armitage2015)." (Model) [from (cite: Armitage2015)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- Imaging task, deconvolver, cell and image size, masks, clean threshold
- Specific line-free channel ranges
- Self-calibration, if any
- Flux scale uncertainty
- Radiative transfer code details (code unnamed) and how model parameters were fitted
- Source distance reference choice and whether 400 pc vs other

## Analysis recipe

1. **Make continuum images at two resolutions**: Continuum from line-free channels; natural weighting for 15-2000 m and robust 0.5 with all baselines  
  > "Two different weightings were used to generate the continuum maps at two different resolutions." (Observations)
   - software: CASA
   - parameter: robust 2 (15-2000 m) and robust 0.5 (all baselines)  
  > "One used a robust factor of 2 (natural weighting) with the baselines from $\sim$ 15 to 2000 m" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure dark lane cut and brightness temperatures**: Intensity cut along the dark lane, converting flux density to Tb  
  > "A cut along the dark lane shows that the flux density increases rapidly from $\sim$ 0.4 mJy beam$^{-1}$ ($T_b\sim 11$ K, 5 $\sigma$)" (RESULTS)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate optically thin disk mass**: Total flux 157 mJy, T=50 K, kappa=0.054 cm2/g at 850 um  
  > "If the emission is optically thin and all thermal at a temperature of 50 K, then the disk mass is $\sim 0.014$ M$_\odot$" (DISCUSSION)
   - assumption: optically thin, thermal, T = 50 K, kappa = 0.054 cm2/g, beta~0.6  
  > "for a dust opacity of 0.054 cm$^2$ g$^{-1}$ at 850 $\mu$m(cite: Beckwith1990)" (DISCUSSION)
   - fitting: _not stated_
   - validation: _not stated_
4. **Toy radiative transfer disk model to reproduce hamburger shape**: Parametrized flared disk with density, temperature and scale-height prescriptions; ray-traced 850 um map with attenuation  
  > "generated a synthetic map by integrating along each line of sight the local emission that is attenuated by the optical depth" (Model)
   - software: in-house radiative transfer code
   - parameter: Ro=68±12 AU, Rt=36±8 AU, ht=12±4 AU, nt=2.2±0.6e10 cm-3, Tt=73±10 K  
  > "we adopted $n_\mathrm{t}\sim 2.2\pm0.6\times10^{10}$ cm$^{-3}$ and $T_\mathrm{t}\sim$ 73$\pm$10 K" (Model)
   - assumption: p=2, q=0.75, passive disk, Keplerian rotation, rho=1.4 n m_H2  
  > "We assume $p=2$ and $q=0.75$ for the disk(cite: Armitage2015)." (Model)
   - fitting: parameters chosen by comparison to Figure 1d by eye; no formal fit stated  
  > "Based on the disk structure seen in the dust emission map in Figure 1d, we find that" (Model)
   - validation: Model brightness ~2.0 mJy/beam (~55 K) consistent with observed Figure 2  
  > "consistent with Figure 2" (Model)

## Software

- **CASA** : calibration and imaging  
  > "The data were calibrated with the Common Astronomy Software Applications (CASA) package" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk radius | ~60 | not stated | AU | 2 | The disk is nearly edge-on and has a radius of $\sim$ 60 AU. |
| Total disk flux | ~157 | not stated | mJy | 3 | The total flux of the disk emission is $\sim$ 157 mJy. |
| Optically thin disk mass | ~0.014 | not stated | Msun | 3 | the disk mass is $\sim 0.014$ M$_\odot$ |
| Model disk mass | ~0.05 | not stated | Msun | 4 | \sim 0.05\,M_\odot |
| Dark lane center brightness temperature | ~58 | not stated | K | 2 | to $\sim$ 2.1 mJy beam$^{-1}$ ($T_b\sim 58$ K) at the center |
| Noise level at 0.02 arcsec | ~0.08 | not stated | mJy/beam | 1 | the noise level becomes $\sim$ 0.08 mJy beam$^{-1}$ (see Methods) |

## Qualitative findings

- Disk shows dark equatorial lane between two brighter regions (hamburger), from low temperature and high optical depth near midplane  
  > "it shows a prominent equatorial dark lane sandwiched between two brighter features, due to relatively low temperature and high optical depth near the disk midplane." (abstract)
- Northeast surface brighter than southwest, consistent with slight tilt of nearside  
  > "the emission in the northeast is less absorbed by the nearside of the disk and thus brighter than the emission in the southwest." (RESULTS)

## Claim tuples

- H: Is the HH 212 Class 0 disk resolved in submm dust with vertical structure? | E: 0.02 arcsec ALMA Band 7 continuum imaging | R: Bright disklike structure with dark lane, radius ~60 AU, Tb jump ~10 over envelope | F: A rotationally supported-like disk with equatorial dark lane is detected | **supported**
- H: Can temperature and optical depth explain the dark lane? | E: Toy radiative transfer model with warmer surface | R: Model reproduces dark lane and brighter, asymmetric regions | F: Dark lane arises from cool optically thick midplane | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust continuum may be the only viable way to characterize youngest disks when lines are optically thick and hard to measure  
  > "In this case, the dust continuum may be the only viable way to detect and characterize these youngest protostellar disks." (DISCUSSION)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass estimate highly uncertain; model is illustrative and lacks self-consistent temperature and scattering  
  > "We refrain from drawing quantitative conclusions about the disk parameters from the model" (DISCUSSION)
- Caveat (inferred, ours): Disk flaring and thinning at the edge inferred only qualitatively
- Caveat (inferred, ours): Model parameters not formally fitted; degeneracies untested
- Caveat (inferred, ours): Dust scattering could affect the lane interpretation
- Caveat (inferred, ours): Mass depends on assumed opacity and temperature

## Reproducibility

- Data public (paper): ALMA data obtainable from the ALMA Science Data Archive  
  > "Our ALMA data can also be obtained from the ALMA Science Data Archive" (acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Radiative transfer code not released or named
- Missing: Cell/image size and masks
- Data volume (inferred): ~100-300 GB raw for four executions in two projects
- Score (inferred): 3/5, Public data and key weighting given, but CASA version, imaging details and model code are missing.
- Rediscovery candidate: no, Imaging recipe is incomplete and the model code is unnamed, though data are public.

## Links

- Companion: (cite: Lee2014) (Earlier lower-resolution ALMA continuum and HCO+ study of HH 212)
- Companion: (cite: Codella2014) (ALMA C17O kinematics indicating Keplerian disk)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 40,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
