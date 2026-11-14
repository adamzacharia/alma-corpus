# ALMA observations of TiO<SUB>2</SUB> around VY Canis Majoris

`2015A&A...580A..36D` | Astronomy and Astrophysics 2015 | first author: De Beck, E. | arXiv: 1506.00818 | DOI: 10.1051/0004-6361/201525990

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars, astrochemistry
- Question: Distribution and excitation of gas-phase TiO2 around the red supergiant VY CMa, and its role in dust condensation  
  > "We aim to constrain the distribution and excitation of TiO 2 around VY CMa in order to clarify its role in dust formation." (abstract)
- Target **VY CMa**: coordinates _not stated_; z/distance 1.2 kpc  
  > "The circumstellar environment of this red supergiant (at 1.2 kpc; Zhang et al., 2012)" (1. Introduction); distance from Zhang et al. 2012  
  > "The circumstellar environment of this red supergiant (at 1.2 kpc; Zhang et al., 2012)" (1. Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (~320 GHz), six spectral windows; Band 9 (~660 GHz), one  
  > "six spectral windows in ALMA’s band 7 (∼0.9 mm; ∼320 GHz) and one in band 9 (∼0.45 mm; ∼660 GHz)" (2. Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14 m to 2.7 km  
  > "With projected baselines of 14 m up to 2.7 km" (2. Observations)
- angular resolution: ~0.2'' at ~320 GHz, ~0.1'' at 658 GHz; beam 0.23x0.13''  
  > "the spatial resolution at ∼320 GHz and 658 GHz is ∼ 0 [′′] . 2 and ∼ 0 [′′] . 1, respectively" (2. Observations)
- max recoverable scale: 8.3'' (320 GHz), 4.0'' (658 GHz)  
  > "the maximum recoverable scales are 8 [′′] . 3 and 4 [′′] . 0" (2. Observations)
- sensitivity: rms 2-15 mJy/beam depending on window (Table 1)  
  > "321 309.501 − 310.437 0.98 3 0.23 × 0.13, 28.27 [◦]" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: TiO2 23(1,23)-22(0,22) (310782.713 MHz)
- Line: TiO2 22(1,21)-21(2,20) (310554.735 MHz)
- Other facility **SMA**: Earlier TiO2 detections for comparison (K+13a,b)  
  > "The peak fluxes of the ALMA and SMA detections are consistent within the uncertainties." (3. Results)
- External data: TiO2 line frequencies and spectroscopy from CDMS  
  > "TiO 2 identifications are based on the Cologne Database for Molecular Spectroscopy" (3. Results) [from Müller et al., 2001, 2005; Brünken et al., 2008]
- External data: Mass-loss rate 2e-4 Msun/yr  
  > "Assuming an average mass-loss rate of 2 × 10 [−][4] _M_ ⊙ yr [−][1] (e.g. De Beck et al., 2010)" (3.2 Excitation conditions) [from De Beck et al., 2010]
- External data: TiO2 dipole moment 6.33 Debye  
  > "The high dipole moment of TiO 2 (6.33 Debye; Wang et al., 2009)" (3.2 Excitation conditions) [from Wang et al., 2009]

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The synthesised beam sizes are obtained using natural weighting." (2. Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Poor in 312-314 GHz window due to line crowding; corrected line-by-line  
  > "the spectral window 312 − 314 GHz suffered from poor continuum subtraction owing to line crowding" (2. Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.23 x 0.13'' (321 GHz)  
  > "with a 0 [′′] . 23 × 0 [′′] . 13 beam" (3.1 Spatial distribution)
- final rms: _not stated_

### Inherited from earlier work

- Observations, calibration and reduction  
  > "The observations and data calibration and reduction are described by R+14." (2. Observations) [from Richards et al. 2014 (R+14)]
- Continuum image reduction and quality  
  > "The data reduction and quality of the continuum emission images at 321 GHz and 658 GHz are discussed in detail by R+14 and O+15." (2. Observations) [from Richards et al. 2014; O'Gorman et al. 2015]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (cell, image size, masks, threshold)
- Line-free channels used for continuum subtraction
- Exact procedure for correcting continuum leakage in the 312 GHz window
- Rotation diagram fitting method and treatment of blends
- Self-calibration and flux calibration details (deferred to R+14)

## Analysis recipe

1. **Extract spectra and identify TiO2 lines**: Spectra extracted in 1'' diameter aperture around the star; lines identified with CDMS  
  > "We analysed spectra extracted for a 1 [′′] diameter region around the stellar position." (3. Results)
   - assumption: Stellar vLSR of 22 km/s  
  > "Assuming [1] a stellar � LSR of 22 km s [−][1]" (3. Results)
   - fitting: _not stated_
   - validation: Compared with SMA detections of K+13a,b  
  > "The peak fluxes of the ALMA and SMA detections are consistent within the uncertainties." (3. Results)
2. **Map spatial distribution**: Channel maps at 2 km/s and integrated-intensity maps compared with continuum and HST  
  > "channel maps of the detected TiO 2 emission lines (Table 2, Fig. 1) at a velocity resolution of 2 km s [−][1]" (Appendix A: Maps of titanium dioxide emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Rotational diagram for column density and temperature**: Rotation diagram of unblended lines using intensities, source sizes and rms from Table 2  
  > "We investigate the excitation of TiO 2 lines via a rotational diagram analysis (Fig. 3)." (3.2 Excitation conditions)
   - assumption: Mass-loss 2e-4 Msun/yr, velocity 20 km/s, 0.9'' extent, 1.2 kpc for abundance  
  > "an average velocity of 20 km s [−][1], and an 0 [′′] . 9 diametric extent, at 1.2 kpc" (3.2 Excitation conditions)
   - fitting: _not stated_
   - validation: Agrees with K+13a  
  > "in agreement with K+13a" (3.2 Excitation conditions)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of TiO2 lines detected | 15 | not stated | dimensionless | 1 | We detect 15 transitions of TiO 2 |
| Column density | 5.65e15 | 1.33e15 | cm-2 | 3 | N col = 5.65 ± 1.33 × 10 [15] cm [−][2] |
| Rotational temperature | 198.0 | 28.5 | K | 3 | T rot = 198.0 ± 28.5 K |
| TiO2/H2 abundance | 3.8e-8 | 0.9e-8 | dimensionless | 3 | TiO 2 /H 2 ≈ 3.8 ± 0.9 × 10 [−][8] |

## Qualitative findings

- TiO2 outflow is clumpy and anisotropic, with a bipolar-like east-west structure and a south-west tail  
  > "The maps demonstrate a highly clumpy, anisotropic outflow" (abstract)

## Claim tuples

- H: TiO2 emission can be spatially resolved and traces the outflow structure | E: Channel and integrated maps of 15 lines | R: Resolved emission, ~0.9'' extent, bipolar-like structure and SW tail | F: Clumpy anisotropic outflow | **supported**
- H: TiO2 plays a major role in dust condensation | E: Compare TiO2 extent with dust-condensation radius, derive column density | R: TiO2 present far beyond dust condensation radius | F: TiO2 likely plays only a minor role as a dust seed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum leakage and cleaning artefacts in the 312-314 GHz window; blending  
  > "These features are artefacts of the cleaning procedure likely caused by imperfect phase corrections on a number of intermediate baselines." (2. Observations)
- Caveat (inferred, ours): Rotation diagram ignores radiative pumping and optical depth
- Caveat (inferred, ours): Line blending and artefacts affect identification
- Caveat (inferred, ours): No reprocessing details given

## Reproducibility

- Data public (paper): Retrieved from ALMA archive (science verification data)  
  > "We retrieved ALMA science verification data on VY CMa from the ALMA archives." (2. Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Continuum subtraction channel choices
- Missing: Rotation diagram fit details
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public data and clear results, but processing and fit details are sparse and defer to R+14.
- Rediscovery candidate: no, Imaging and fitting recipe is incomplete.

## Links

- Method: Richards et al. 2014 (R+14) (Observations and data reduction)
- Companion: O'Gorman et al. 2015 (O+15) (Submillimeter continuum of VY CMa)
- Related: ALMA science verification VY CMa

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00011.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 27,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
