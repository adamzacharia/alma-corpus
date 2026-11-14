# A MeerKAT view of pre-processing in the Fornax A group

`2021A&A...648A..32K` | Astronomy and Astrophysics 2021 | first author: Kleiner, D. | arXiv: 2101.10347 | DOI: 10.1051/0004-6361/202039898

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: Do H I, H alpha and molecular gas in the Fornax A group show evidence of pre-processing of galaxies, and at what stages?  
  > "we identify galaxies at different stages of pre-processing following various types of interactions." (Introduction)
- Target **Fornax A group (NGC 1316 and group members)**: coordinates MeerKAT pointing centre 03h 22m 41.7s, -37d 12' 30.0"  
  > "we assume a luminosity distance of 20 Mpc to the most massive galaxy (NGC 1316) in the Fornax A group" (Introduction); z/distance 20 Mpc  
  > "we assume a luminosity distance of 20 Mpc to the most massive galaxy (NGC 1316) in the Fornax A group" (Introduction); distance from Cantiello2013; Hatt2018  
  > "we assume a luminosity distance of 20 Mpc to the most massive galaxy (NGC 1316) in the Fornax A group" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00129.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA CO data for 7 galaxies from Morokuma-Matsui et al. 2019, used for H2 masses  
  > "The 5 galaxies that were not observed are ESO 301-IG 11, FCC 19, FCC 35, FCC  40, and FCC 46 (cite: Morokuma-Matsui2019)." (5.2 Pre-processing status of the group galaxies)
- Other facility **MeerKAT**: H I cube of the Fornax A group (two commissioning observations, Mk-36 and Mk-62)  
  > "The Fornax A group was observed with MeerKAT in two different commissioning observations in June 2018" (3.1 MeerKAT radio observation)
- Other facility **VST OmegaCAM**: H alpha narrow-band and r' broad-band imaging  
  > "we used a combination of H$\alpha$ narrow-band images and $r'$ broad-band images both collected using the OmegaCAM attached to the VST" (3.2 VST H alpha observation)
- Other facility **Fornax Deep Survey**: deep optical imaging, stellar masses  
  > "deep optical imaging from the Fornax Deep Survey" (Introduction)
- External data: ALMA CO-derived molecular gas data for group galaxies and which galaxies were observed  
  > "Both galaxies were observed with ALMA (cite: Morokuma-Matsui2019), although no CO was detected, placing upper limits on the H$_{2}$ mass." (5.2 Pre-processing status of the group galaxies) [from Morokuma-Matsui2019]
- External data: Stellar masses of group galaxies  
  > "estimated stellar masses (Table [\[tab:HI_prop\]](#tab:HI_prop)) from (cite: Raj2020) and (cite: Venhola2018)" (5.2 Pre-processing status of the group galaxies) [from Raj2020; Venhola2018]

## Processing

### Calibration

- pipeline or manual: MeerKAT data reduced with CARACal pipeline (Mk-62 end-to-end; Mk-36 previously reduced)  
  > "We used `CARACal` to reduce the Mk-62 observation end-to-end and include the already reduced Mk-36 observation" (3.1 MeerKAT radio observation)
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

- Mk-36 data reduction  
  > "these papers provide a detailed description of the data reduction process" (3.1 MeerKAT radio observation) [from (cite: Maccagni2020); (cite: Serra2019)]
- VST data reduction details  
  > "Details of the used reduction steps are given by (cite: Venhola2018)." (3.2 VST H alpha observation) [from (cite: Venhola2018)]

### Not stated but needed to reproduce (our reading)

- ALMA CO data reduction, imaging and CO fluxes (taken from Morokuma-Matsui2019)
- CO line ratio and which CO transition was used
- Final H2 masses per galaxy are not tabulated

## Analysis recipe

1. **Compute molecular gas masses and gas scaling ratios**: H2 masses from ALMA CO using Milky Way conversion factor; compute F_HI, Fgas, R_mol, F_H2 and compare with xGASS  
  > "We measure the molecular gas mass of the observed galaxies using the standard Milky Way CO-to-H$_{2}$ conversion factor of 4.36" (5.2 Pre-processing status of the group galaxies)
   - assumption: alpha_CO = 4.36 (Msun K km/s pc^2)^-1; helium removed; factor 1.3 for total gas  
  > "the total gas fraction Fgas $\equiv$ log(1.3(M$_{\rm HI}$ + M$_{\rm H2}$)/M$_{\star}$) where the 1.3 accounts for the helium contribution" (5.2 Pre-processing status of the group galaxies)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CARACal** : MeerKAT data reduction  
  > "We used the Containerised Automated Radio Astronomical Calibration" (3.1 MeerKAT radio observation)
- **SoFiA** : H I source finding  
  > "We searched for H I sources using `SoFiA` outside the `CARACal` pipeline." (3.1 MeerKAT radio observation)
- **WSclean** : continuum and H I imaging  
  > "Then, we created a H I cube by imaging the H I emission with `WSclean`" (3.1 MeerKAT radio observation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IGM H I mass | 1.12e9 | 0.02e9 | Msun | 0 | We detect a total of (1.12 $\pm$ 0.02) $\times$ 10$^{9}$ M$_{\odot}$ of H I in the IGM. |
| H I mass in NGC 1316 centre | 6.8e7 | 0.4e7 | Msun | 0 | we detect a H I mass in the centre of (6.8 $\pm$ 0.4) $\times$ 10$^{7}$ M$_{\odot}$ |

## Qualitative findings

- Galaxies classified as early (2), ongoing (5), advanced (4) pre-processing, 1 unclassified  
  > "2 (NGC 1326A and NGC 1326B) are in the early phase of pre-processing" (6 Conclusions)

## Claim tuples

- H: Group galaxies show different stages of pre-processing | E: H I morphology and H I/H2 ratios (ALMA CO) compared to xGASS trends | R: 9 of 12 galaxies show evidence of pre-processing | F: Pre-processing is driven by local interactions in the group | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA role is limited to literature CO data
- Caveat (inferred, ours): Single alpha_CO for all galaxies

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA CO fluxes
- Missing: reduction details for ALMA data
- Data volume (inferred): not applicable for the ALMA part (CO values from literature)
- Score (inferred): 2/5, ALMA is a minor ingredient taken from a previous paper.
- Rediscovery candidate: no, ALMA data are not processed here.

## Links

- Companion: Morokuma-Matsui2019 (Source of ALMA CO data)
- Companion: Serra2019 (Earlier MeerKAT H I study)
- Related: MeerKAT Fornax Survey
- Related: Fornax Deep Survey

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 19,
  "rate": 0.328
 },
 "evidence_ok": true
}
```
