# High-resolution ALMA observations of SDP.81. II. Molecular clump properties of a lensed submillimeter galaxy at z = 3.042

`2015PASJ...67...93H` | Publications of the Astronomical Society of Japan 2015 | first author: Hatsukade, Bunyo | arXiv: 1503.07997 | DOI: 10.1093/pasj/psv061

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the spatially resolved molecular gas, dust and stellar properties of the lensed SMG SDP.81, and do its molecular clumps follow the star-formation law?  
  > "We present spatially-resolved properties of molecular gas and dust in a gravitationally-lensed submillimeter galaxy H-ATLAS J090311.6$+$003906 (SDP.81) at $z=3.042$ revealed by the Atacama Large Millimeter/submillimeter Array (ALMA)." (abstract)
- Target **SDP.81 (H-ATLAS J090311.6+003906)**: coordinates _not stated_; z/distance z = 3.042 (lens at z = 0.2999)  
  > "SDP.81 is an SMG at $z = 3.042 \pm 0.001$ that is gravitationally lensed by a foreground massive elliptical galaxy at $z = 0.2999 \pm 0.0002$" (Introduction); distance from Negrello et al. 2010, 2014  
  > "SDP.81 is an SMG at $z = 3.042 \pm 0.001$ that is gravitationally lensed by a foreground massive elliptical galaxy at $z = 0.2999 \pm 0.0002$" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Band 4 (151 GHz, 2.0 mm), Band 6 (236 GHz, 1.3 mm), Band 7 (290 GHz, 1.0 mm)  
  > "at Band 4 (151 GHz, or 2.0 mm), Band 6 (236 GHz, or 1.3 mm), and Band 7 (290 GHz, or 1.0 mm)" (2.1 ALMA Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~5-15 km, 31-36 antennas  
  > "with the baseline lengths of $\sim$5–15 km and with 31–36 antennas" (2.1 ALMA Data)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: October 2014 (Science Verification, Long Baseline Campaign)  
  > "SDP.81 was observed as part of Science Verification of the ALMA Long Baseline Campaign in October, 2014" (2.1 ALMA Data)
- pi or archival as stated: Public calibrated data from ALMA Science Portal  
  > "We used the calibrated data set publicly available through the ALMA Science Portal." (2.1 ALMA Data)
- Line: CO 5-4 (not stated)
- Other facility **HST/WFC3 F160W**: H-band image of stellar components, archival data from Negrello et al. 2014  
  > "We made use of the archival data of *HST*/Wide Field Camera 3 (WFC3) taken by (cite: negr14)." (2.2 HST Data)
- Other facility **SDSS DR12**: astrometric calibration of HST image  
  > "We calibrated the coordinates of the image using the catalog data from the Data Release 12 of the Sloan Digital Sky Survey (SDSS)." (2.2 HST Data)
- External data: Gravitational lens model and dust clump positions  
  > "The analysis of gravitational lensing was conducted by (cite: tamu15) using the glafic software package (cite: ogur10)." (3 Lens Model) [from (cite: tamu15)]
- External data: Dust temperature T_dust = 39.3 K  
  > "The dust temperature of $T_{\rm dust} = 39.3$ K was derived by (cite: negr14) for the integrated value of SDP.81" (4.2) [from (cite: negr14)]
- External data: CO(5-4)/CO(1-0) = 0.3  
  > "We used a CO line ratio of CO(5–4)/CO(1–0) $= 0.3$ (cite: alma15b)." (4.2) [from (cite: alma15b)]
- External data: Magnification mu = 11  
  > "Corrected for the gravitational lensing magnification factor of $\mu = 11$ (cite: buss13)" (Introduction) [from (cite: buss13)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated public data set used  
  > "We used the calibrated data set publicly available through the ALMA Science Portal." (2.1 ALMA Data)
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
- smoothing: CO line cube with 21 km/s spectral resolution  
  > "line cube (spectral resolution of 21 km s$^{-1}$)" (4.1 Clump Identification)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation and data reduction details  
  > "The details of observations and data reduction are described in (cite: alma15a) and (cite: alma15b)." (2.1 ALMA Data) [from (cite: alma15a), (cite: alma15b)]
- Lens model  
  > "By using our lens model (cite: tamu15) and the glafic software, we determined the positions of molecular clumps on the source plane" (5.2) [from (cite: tamu15)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, beam, rms) of the CO(5-4) cube and 1.0 mm map
- Continuum subtraction and line-free channels
- Clumpfind parameters (thresholds, levels)
- Exact lens model parameters and magnification maps
- Which archive files were used
- Rest frequency/sigma definition of noise

## Analysis recipe

1. **Identify molecular clumps**: Peak search >=3.5 sigma in velocity-integrated map (pixels >1.5 sigma) plus clumpfind in the cube; keep clumps found by both  
  > "We identified 14 molecular clumps along the arcs detected by both methods" (4.1 Clump Identification)
   - software: clumpfind
   - fitting: _not stated_
   - validation: Counter-image candidates assessed using positions and velocities  
  > "we suggest that clumps 1 and 13 and clumps 4 and 5 are possibly counter images of the same source" (4.1 Clump Identification)
2. **Photometry and gas/SFR surface densities**: Photometry in >2 sigma CO regions; L'CO, M_H2 with alpha_CO, dust mass and L_FIR from 1.0 mm flux, SFR from Kennicutt  
  > "We used regions above 2$\sigma$ in the CO(5–4) velocity-integrated map for conducting photometry and estimating the physical quantities of each clump." (4.2)
   - parameter: kappa_d(125 um)=2.64 m^2/kg, beta=1.5, T_dust=39.3 K  
  > "adopt $\kappa_d(125\ \mu m) = 2.64 \pm 0.29$ m$^2$ kg$^{-1}$ (cite: dunn03) and $\beta = 1.5$" (4.2)
   - assumption: alpha_CO = 0.8, filling factor of unity, CO(5-4)/CO(1-0)=0.3  
  > "we assume a filling factor of unity in this study" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Source-plane positions and kinematics**: Map clumps, dust clumps and HST stellar components to source plane with the lens model  
  > "we determined the positions of molecular clumps on the source plane" (5.2)
   - software: glafic
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **clumpfind** : clump search in line cube  
  > "We then used the clumpfind package (cite: will94) to search for clumps in the line cube." (4.1)
- **glafic** : lens model positions in source plane  
  > "By using our lens model (cite: tamu15) and the glafic software" (5.2)
- **galfit** : deblend lens galaxy from background source in HST  
  > "We used the software galfit (cite: peng02) to deblend the background lensed source from the foreground lens galaxy." (2.2 HST Data)
- **iraf MultiDrizzle** : coadd HST WFC3 exposures  
  > "coadded them by ourselves using the iraf MultiDrizzle package" (2.2 HST Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of molecular clumps | 14 | not stated | clumps | 1 | We identified 14 molecular clumps in the CO(5–4) line data. |
| SFR surface density range | 100-300 | not stated | Msun/yr/kpc^2 | 2 | The SFR density ranges between 100–300 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| Gas depletion time | ~100 | not stated | Myr | 2 | with a gas depletion time scale of $\sim$100 Myr |
| Velocity gradient peak-to-peak | ~300 | not stated | km/s | 3 | A velocity gradient with a peak-to-peak value of $\sim$300 km s$^{-1}$ in the north-south direction |
| Stellar extent | ~6 | not stated | kpc | 3 | distributed over $\sim$6 kpc in the NE-SW direction |

## Qualitative findings

- Molecular and dust clumps confined within ~2 kpc; stellar emission offset to the west  
  > "The molecular and dust clumps are confined within a $\sim$2 kpc region" (abstract)

## Claim tuples

- H: Do z~3 molecular clumps follow the local starburst star-formation law? | E: Computed Sigma_H2 and Sigma_SFR for clumps | R: Surface densities >3 orders above local spirals, on the burst sequence for alpha_CO=0.8 | F: Clumps follow the starburst star-formation law | **supported**
- H: Are gas, dust and stars co-spatial? | E: Source-plane reconstruction | R: Gas/dust within ~2 kpc; stars ~6 kpc and offset west | F: Rotating disk with obscured stars or a merger | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Galactic alpha_CO=4.3 would put clumps on the normal-galaxy sequence  
  > "If we adopt the Galactic conversion factor ($\alpha_{\rm CO} = 4.3 M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$; (cite: bola13)), these clumps are located on the sequence of normal star-forming galaxies." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Clumps may be unresolved; filling factor and counter-images uncertain  
  > "it is likely that they are unresolved" (4.1)
- Caveat (inferred, ours): Result depends on alpha_CO and the CO excitation ratio
- Caveat (inferred, ours): Single T_dust for all clumps
- Caveat (inferred, ours): Low S/N CO(5-4) clumps possibly multiple images

## Reproducibility

- Data public (paper): Public ALMA SV data  
  > "publicly available through the ALMA Science Portal" (2.1 ALMA Data)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: clumpfind settings
- Missing: Lens model from Tamu15 including magnification maps
- Missing: Table values not included in text
- Data volume (inferred): ~tens of GB (calibrated SV measurement sets) or less if using released images
- Score (inferred): 4/5, Public data and clear formulae, but clump-finding settings and lens model are external or missing.
- Rediscovery candidate: no, Needs the external lens model and unstated clumpfind settings.

## Links

- Method: (cite: tamu15) (lens model)
- Method: (cite: alma15b) (ALMA data reduction)
- Companion: (cite: tamu15) (Paper I, dust clumps and lens model)
- Related: ALMA Long Baseline Campaign Science Verification
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
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
  "facts": 69,
  "stated": 31,
  "rate": 0.449
 },
 "evidence_ok": true
}
```
