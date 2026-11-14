# Deep JWST/NIRCam imaging of Supernova 1987A

`2024MNRAS.532.3625M` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Matsuura, Mikako | arXiv: 2404.10042 | DOI: 10.1093/mnras/stae1032

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, other
- Question: What do deep JWST/NIRCam images of SN 1987A reveal about its ejecta, equatorial ring and exterior emission, and what are the sources (dust, synchrotron, lines) of the NIR emission?  
  > "In the NIRCam images, we identify: 1) faint H$_2$ crescents, which are emissions located between the ejecta and the equatorial ring, 2) a bar, which is a substructure of the ejecta" (abstract)
- Target **SN 1987A**: coordinates _not stated_; z/distance 49.6 kpc (LMC)  
  > "in a neighbouring galaxy, the Large Magellanic Cloud, at a distance of $49.6$ kpc (cite: 2019Natur.567..200P)" (Introduction); distance from Pietrzyński et al. 2019 (cite: 2019Natur.567..200P)  
  > "in a neighbouring galaxy, the Large Magellanic Cloud, at a distance of $49.6$ kpc (cite: 2019Natur.567..200P)" (Introduction)

## Data provenance

- ALMA projects: 2021.1.00707.S
- bands: _not stated_
- frequencies and spectral setup: two tunings: 301.75–305.57 GHz and 313.73–317.52 GHz (LSRK)  
  > "ALMA observed SN 1987A with two tunings, 301.75–305.57 GHz in Kinematic Local Standard of Rest (LSRK) (993.51–981.09 $\mu$m) and 313.73–317.52 GHz" (Auxiliary data: ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.081"x0.061", PA 33.7 deg  
  > "The synthesized beam was 0.081"$\times$0.061" with a position angle of 33.7$^{\circ}$ for the major axis." (Auxiliary data: ALMA)
- max recoverable scale: 0.993"  
  > "The shortest baselines allowed for a maximum recoverable scale of 0.993"." (Auxiliary data: ALMA)
- sensitivity: _not stated_
- time on source: 10,813 sec total integration  
  > "The total integration time was 10,813 sec." (Auxiliary data: ALMA)
- observing dates: 2021 November 2  
  > "on 2021 November 2nd as part of the Project 2021.1.00707.S" (Auxiliary data: ALMA)
- pi or archival as stated: _not stated_
- Other facility **JWST/NIRCam**: Primary deep 1–5 micron imaging, program 1726, 8 filters  
  > "We obtained deep images of SN 1987A, using NIRCam on *JWST* under general observer program 1726." (2 JWST/NIRCam observations of SN 1987A)
- Other facility **HST ACS F656W**: 2003 image used for astrometric reference  
  > "First, an *HST* ACS F656W image observed in 2003 (cite: Tziamtzis.2010) was aligned with 23 *Gaia* stars" (Data reduction)
- Other facility **VLT/SINFONI and JWST/NIRSpec**: Spectra used to assess line and continuum contributions to filters  
  > "we used the spectra from SINFONI (cite: Larsson:2016bj) and *JWST*/NIRSpec (cite: Larsson.2023ytc)." (Line emission within filter bands)
- External data: Historical radio synchrotron fluxes before 2014  
  > "The historical measurements of the radio synchrotron emission before 2014 are plotted in blue circles" (3.3.1 NIR continuum: synchrotron and dust) [from Zanardo et al. (cite: Zanardo:2010p29272; Zanardo:2013fn; Zanardo:2014gu)]
- External data: 8.7 GHz flux at day 10,942  
  > "The day 10,942 flux measurement at 8.7 GHz from (cite: Cendes.2018z98) is plotted with the filled purple circle." (3.3.1 NIR continuum: synchrotron and dust) [from (cite: Cendes.2018z98)]
- External data: MIRI/MRS images replicated  
  > "The lower panels are MIRI/MRS images, replicated from (cite: Jones.20232sn)." (3.3.2 Spatial distributions of dust and synchrotron) [from (cite: Jones.20232sn)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration not described; JWST Calibration Pipeline used for NIRCam  
  > "The NIRCam data were reduced using the JWST Calibration Pipeline (cite: 2023zndo...7829329B) software version 2022$_-$3." (Data reduction)
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

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging procedure (CASA version, weighting, robust, cleaning, masking)
- how the ALMA 315 GHz total flux and flux excluding ejecta were measured
- ALMA project code printed in text (2021.1.00707.S) differs from the code linked by the archive (2021.1.00701.S)
- flux calibrator and ALMA flux scale uncertainty

## Analysis recipe

1. **Measure NIR SEDs and power-law indices in apertures**: Extract fluxes in several apertures after subtracting a blank-sky background, fit F_nu ∝ nu^-alpha to F323N, F356W, F444W  
  > "The fluxes at F323N, F356W and F444W follow a power-law continuum across SN 1987A (black lines in Fig [11](#fig:SED))." (3.3 Power-law spectra at 3–4 μm in the equatorial ring and its exterior)
   - fitting: _not stated_
   - validation: compared with radio-to-ALMA SED power law alpha=0.70  
  > "the grey line shows the power-law of $\alpha=0.70$ crossing the 8.7 GHz flux at day=10,942" (3.3.1 NIR continuum: synchrotron and dust)

## Software

- **JWST Calibration Pipeline** 1.8.5: NIRCam data reduction  
  > "The calibration software version number was 1.8.5 with CRDS version 11.16.16" (Data reduction)
- **WebbPSF** : simulated PSFs  
  > "Simulated PSFs were calculated using WebbPSF (cite: Perrin2014)." (Image convolutions)
- **PSF Matching** : convolution kernels to match resolution  
  > "The convolution was processed, using the python code PSF Matching (cite: Gordon2008; Aniano2011)." (Image convolutions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Power-law index of ejecta at 3–4 micron | 3.1 | not stated | dimensionless | 1 | The ejecta have the steepest power-law index $\alpha$ at a value of 3.1 |
| Power-law index at hot spots / diffuse emission | 1.6 / 1.5 | not stated | dimensionless | 1 | The power-law indices are as small as $\alpha=1.6$ at the hot spots on the ring and $\alpha=1.5$ within the diffuse emission. |
| Power-law index at western / eastern outer spots | 2.9 / 1.9 | not stated | dimensionless | 1 | The power-law indices are $\alpha=2.9$ and 1.9 at the western and eastern outer spots, respectively. |
| Minimum magnetic field for synchrotron break at 3 micron | ≥2.1 | not stated | mG | 0 | Having the break wavelength/frequency to be at 3 $\mu$m  requires the magnetic field of $B\ge2.1$ mG. |

## Qualitative findings

- 3–5 micron continuum in ring and exterior has substantial synchrotron contribution; dust emission is confined to outer spots and diffuse emission  
  > "In the ring and exterior to the ring, synchrotron emission contributes a substantial fraction to the continuum." (abstract)

## Claim tuples

- H: Is the 3–5 micron emission in the ring and exterior synchrotron? | E: Compared NIRCam SEDs with the radio/ALMA power law and MIRI dust images | R: Radio power law with alpha=0.70 matches the F323N and F356W fluxes; hot spots have little 7 micron dust | F: Synchrotron contributes substantially to the NIR continuum | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA 315 GHz flux likely underestimated because of the small maximum recoverable scale  
  > "The ALMA flux at 315 GHz is probably underestimated, because the interferometry had a fully recoverable size of only $0.99''$" (3.3.1)
- Caveat (inferred, ours): ALMA used only qualitatively and for one flux point; calibration unstated
- Caveat (inferred, ours): Synchrotron versus dust attribution relies on a power-law comparison with no formal fit

## Reproducibility

- Data public (paper): JWST pipeline-reduced data on MAST; ALMA data availability not stated  
  > "The pipeline reduced data are available at MIKULSKI archive (<http://dx.doi.org/10.17909/dzkq-7c90>)." (Data availability)
- Products in archive: _not stated_
- Missing: ALMA reduction details
- Missing: fitting method for power-law indices
- Data volume (inferred): ALMA ~ tens of GB; JWST small
- Score (inferred): 2/5, ALMA role minor and undocumented; JWST analysis qualitative.
- Rediscovery candidate: no, ALMA processing not described and the main results rely on JWST.

## Links

- Companion: Larsson et al. 2023 (cite: Larsson.2023ytc) (JWST NIRSpec spectra used for line contributions)
- Companion: Jones et al. 2023 (cite: Jones.20232sn) (MIRI/MRS SED analysis)
- Companion: Cigan et al. 2019 (cite: Cigan:2019cl) (earlier ALMA continuum images and dust)
- Related: JWST GO 1726
- Related: JWST program 1232

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2021.1.00707.S"
 ],
 "obscore_codes_not_in_card": [
  "2021.1.00701.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 57,
  "stated": 23,
  "rate": 0.404
 },
 "evidence_ok": true
}
```
