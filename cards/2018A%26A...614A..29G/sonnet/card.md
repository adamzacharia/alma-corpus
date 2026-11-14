# Large-amplitude late-time radio variability in GRB 151027B

`2018A&A...614A..29G` | Astronomy and Astrophysics 2018 | first author: Greiner, J. | arXiv: 1802.01882 | DOI: 10.1051/0004-6361/201731755

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients
- Question: Can a multi-frequency, multi-epoch afterglow dataset of GRB 151027B constrain all fireball model parameters, and what explains the large radio flux variations?  
  > "We have embarked on a multi-frequency, multi-epoch observing campaign to obtain sufficient data for a given GRB that allows us to test the simplest version of the fireball afterglow model." (abstract)
- Target **GRB 151027B**: coordinates RA, Dec (J2000) = 76.21955, -6.45029 deg (05:04:52.69 -06:27:01.1)  
  > "RA(2000.0), Dec(2000.0) = 76.21955$^\circ$, -6.45029$^\circ$, or 05:04:52.69 –06:27:01.1, with a 1$\sigma$ error of $\pm$0.25$''$." (2.2 GROND observations); "a redshift determination of $z = 4.063$ with VLT/X-shooter another four hours later (cite: Xu2015)" (2.1 GRB prompt and afterglow detection); z/distance z = 4.063  
  > "RA(2000.0), Dec(2000.0) = 76.21955$^\circ$, -6.45029$^\circ$, or 05:04:52.69 –06:27:01.1, with a 1$\sigma$ error of $\pm$0.25$''$." (2.2 GROND observations); "a redshift determination of $z = 4.063$ with VLT/X-shooter another four hours later (cite: Xu2015)" (2.1 GRB prompt and afterglow detection); distance from VLT/X-shooter (cite: Xu2015)  
  > "RA(2000.0), Dec(2000.0) = 76.21955$^\circ$, -6.45029$^\circ$, or 05:04:52.69 –06:27:01.1, with a 1$\sigma$ error of $\pm$0.25$''$." (2.2 GROND observations); "a redshift determination of $z = 4.063$ with VLT/X-shooter another four hours later (cite: Xu2015)" (2.1 GRB prompt and afterglow detection)

## Data provenance

- ALMA projects: 2015.1.01558.T
- bands: Band 7 (343.495 GHz) and Band 3 (97.495 GHz)  
  > "A band 7 (343.495 GHz) observation was performed starting on 2015 November 2, 05:22 UT under a precipitable water vapour (PWV) of 0.71 mm" (2.4 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7 GHz; about 87% of each of four spectral windows used  
  > "integrated over a bandwidth of 7 GHz; taking into account that only about 87% of each of the four spectral windows was used" (2.4 ALMA observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 2σ upper limits 42 µJy (Band 3), 100 µJy (Band 7)  
  > "no source is detected in either observation, with 2$\sigma$ upper limits of 42 $\mu$Jy in band 3" (2.4 ALMA observations)
- time on source: _not stated_
- observing dates: Band 7: 2015 Nov 2; Band 3: 2015 Nov 4  
  > "a band 3 (97.495 GHz) observation started on 2015 November 4 at 07:45 UT under a PWV=0.31 mm" (2.4 ALMA observations)
- pi or archival as stated: Proposal 2015.1.01558.T, PI S. Schulze (ToO)  
  > "ALMA: ADS/JAO.ALMA#2015.1.01558.T (PI: Schulze)." (footnote)
- Other facility **GROND**: Simultaneous g'r'i'z'JHKs optical-NIR photometry  
  > "Simultaneous imaging in $g'r'i'z'JHK_{\rm s}$ continued for several further epochs" (2.2 GROND observations)
- Other facility **ATCA**: 5.5 and 9 GHz radio light curve over 8 epochs  
  > "We observed the field of GRB 151027B under program C2955 (PI: Greiner) simultaneously at 5.5 and 9 GHz" (2.3 ATCA observations)
- Other facility **Swift XRT**: Public X-ray data for the SED and light curve  
  > "combine this with public *Swift*-XRT X-ray data" (abstract)
- External data: Extinction determination of the afterglow  
  > "see (cite: Bolmer2017) for more details on the extinction determination" (3.2 Constraints on the fireball model) [from (cite: Bolmer2017)]
- External data: Swift/BAT fluence for E_gamma,iso  
  > "giving an energy fluence of (14.7$\pm$2.6) $\times 10^{-7}$ erg cm$^{-2}$" (3.2 Constraints on the fireball model) [from GCN notices_s/661869]

## Processing

### Calibration

- pipeline or manual: CASA, default calibration path used in ALMA Quality Assurance  
  > "following the default calibration path also used in ALMA Quality Assurance" (2.4 ALMA observations)
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
- primary beam correction: Included; correction >0.99  
  > "These values include the primary beam correction (though this is $>$0.99 due to being close to the center of the field of view)." (2.4 ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- ALMA flux and phase calibrators
- Imaging weighting, cell size and clean parameters
- Synthesized beams
- Spectral window frequencies
- Details of the fireball parameter derivation (Fig. 6)

## Analysis recipe

1. **Search for ALMA counterpart**: Imaged Band 3 and 7 and compared peak within GROND error circle to noise; peaks consistent with noise; derived 2σ upper limits  
  > "the area of the error circle contains 1914 spatial resolution pixels, so we expect 1914 pixels $\times$ 0.0016 = 3 pixels to be above a 3$\sigma$ flux level." (2.4 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared the number of expected noise peaks above threshold in the error circle  
  > "the area of the error circle contains 1914 spatial resolution pixels, so we expect 1914 pixels $\times$ 0.0016 = 3 pixels to be above a 3$\sigma$ flux level." (ALMA observations)
2. **Constrain fireball parameters**: Broken power-law light curves, SED fit, and ν_m constraints using ALMA limits, with an efficiency argument to constrain parameters  
  > "Assuming $\epsilon_\gamma = 0.2$" (3.2 Constraints on the fireball model)
   - assumption: ε_γ = 0.2, ISM density profile, slow cooling  
  > "Assuming $\epsilon_\gamma = 0.2$" (3.2 Constraints on the fireball model)
   - fitting: _not stated_
   - validation: Model radio light curve compared with the ATCA detections and limits  
  > "the ’predicted’ radio light curve of Fig. [7](#fig:modradio) corresponds roughly to the mean of the radio detections and upper limits." (3.2 Constraints on the fireball model)

## Software

- **CASA** : ALMA data analysis  
  > "The data analysis was performed using the standard ALMA data analysis package CASA" (2.4 ALMA observations)
- **MIRIAD** : ATCA data reduction  
  > "Data analysis was done using the standard software package `MIRIAD`" (2.3 ATCA observations)
- **pyraf/IRAF** : GROND data reduction  
  > "using pyraf/IRAF" (2.2 GROND observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 3 2σ upper limit | 42 | not stated | µJy | 1 | 2$\sigma$ upper limits of 42 $\mu$Jy in band 3 |
| ALMA Band 7 2σ upper limit | 100 | not stated | µJy | 1 | 100 $\mu$Jy in band 7 (343.495 GHz |
| Electron index p | 2.62 | 0.02 | dimensionless | 2 | $p=2.62 \pm 0.02$ |
| ν_m at 31 ks | 1.15e14 | 0.15e14 | Hz | 2 | $\nu_m$(31 ks)$= (1.15\pm0.15)\times 10^{14}$ Hz |

## Qualitative findings

- No ALMA detection; the Band 7 3.5σ blob could possibly be the afterglow  
  > "so we cannot completely rule out that the 3.5$\sigma$ blob in the band 7 image is not, indeed, the afterglow." (4 Conclusions)

## Claim tuples

- H: Is the afterglow consistent with the simplest fireball model? | E: Joint X-ray, optical/NIR and ALMA analysis | R: Constant density, slow cooling; n=0.03-5 cm^-3, ε_e=0.3-1.0 | F: The simplest fireball scenario fits | **supported**
- H: Is the radio variability due to scintillation? | E: ATCA 5.5/9 GHz monitoring and a scintillation comparison | R: Flux changes of more than a factor of 5 | F: Scintillation, requiring a nearby or multiple screens | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Cooling break below the GROND bands (p=1.62) rejected as inconsistent with the light curve  
  > "inconsistent with our observed light curve" (3.2 Constraints on the fireball model)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA limits are close to the model prediction  
  > "the ALMA flux limits are close to the prediction of our model" (4 Conclusions)
- Caveat (inferred, ours): The scintillation interpretation is not modelled quantitatively.
- Caveat (inferred, ours): ε_γ=0.2 is assumed, which drives the parameter ranges.

## Reproducibility

- Data public (paper): Only a data-use footnote; no public statement  
  > "This paper makes use of the following data: ATCA: Proposal C2955 (PI: Greiner), ALMA: ADS/JAO.ALMA#2015.1.01558.T (PI: Schulze)." (footnote 3 (title))
- Products in archive: _not stated_
- Missing: Full ALMA imaging parameters
- Missing: Fireball fit code and parameter derivation
- Data volume (inferred): ~10 GB for two ALMA ToO observations
- Score (inferred): 3/5, ALMA is a minor part, but the limits are simple; the modelling details are sparse.
- Rediscovery candidate: no, The ALMA result is a null detection, and the main modelling recipe is incomplete.

## Links

- Method: Granot & Sari 2002 (cite: grs02) (Fireball synchrotron spectrum framework)
- Companion: Bolmer et al. 2018 (cite: Bolmer2017) (Extinction determination)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 28,
  "rate": 0.459
 },
 "evidence_ok": true
}
```
