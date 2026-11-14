# Deep Submillimeter and Radio Observations in the SSA22 Field. I. Powering Sources and the Lyα Escape Fraction of Lyα Blobs

`2017ApJ...850..178A` | The Astrophysical Journal 2017 | first author: Ao, Y. | arXiv: 1704.05101 | DOI: 10.3847/1538-4357/aa960f

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, star_formation
- Question: What powers the 35 Lyα blobs (LABs) at z≈3.1 in SSA22 (star formation or AGN), and what are their Lyα escape fractions?  
  > "We study the heating mechanisms and Ly$\alpha$ escape fractions of 35 Ly$\alpha$ blobs (LABs) at $z \approx 3.1$ in the SSA22 field." (abstract)
- Target **SSA22 Lyα blobs (35 LABs, LAB1-LAB35)**: coordinates SCUBA-2 field centre 22:17:31.7 +00:17:50 (J2000)  
  > "SSA22 is such a suitable field because it has 35 LABs detected at $z \approx 3.1$ (Matsuda et al. 2004)" (1 Introduction); z/distance z≈3.1  
  > "SSA22 is such a suitable field because it has 35 LABs detected at $z \approx 3.1$ (Matsuda et al. 2004)" (1 Introduction); distance from Matsuda et al. (2004) LAB catalogue; spectroscopic redshifts from the literature  
  > "SSA22 is such a suitable field because it has 35 LABs detected at $z \approx 3.1$ (Matsuda et al. 2004)" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00704.S, 2013.1.00162.S
- bands: Band 7 (350 GHz) toward 4 LABs; Band 6 (263 GHz) for LAB12 and LAB14  
  > "ALMA observations were carried out in band 7 with a central frequency of 350 GHz towards 4 LABs (LAB1, LAB2, LAB5 and LAB18)" (2.2 ALMA observations); "in band 6 with a central frequency of 263 GHz" (2.2 ALMA observations)
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
- pi or archival as stated: _not stated_
- Other facility **JCMT/SCUBA-2**: 850 um continuum map, 91 h on source, rms 0.75 mJy/beam  
  > "The final beam-convolved map reaches an rms noise level of 0.75 mJy/beam within the central 15 arcmin" (2.1 JCMT/SCUBA-2 observations)
- Other facility **VLA**: S-band 2-4 GHz B-config radio mosaic, rms 1.5 uJy/beam, resolution 2.3x2.0 arcsec  
  > "reaching an rms sensitivity of 1.5 $\mu$Jy/beam (before primary beam correction) and an angular resolution of 2.3$\ensuremath{''}\times$2.0$\ensuremath{''}$" (2.3 VLA observations)
- Other facility **Chandra**: X-ray counterparts from literature  
  > "Deep X-ray observations with $Chandra$ are available for the SSA22 field (Geach et al. 2009; Lehmer et al. 2009)" (3.4 Comments on individual LABs)
- External data: Catalogue of 35 LABs with Lyα luminosities and isophotal areas  
  > "For the 35 LABs identified in Matsuda et al. (2004), all sources are covered by SCUBA-2 observations" (3.1 Submm emission) [from Matsuda et al. 2004 (cite: 2004AJ....128..569M)]
- External data: Previous (sub)mm flux measurements  
  > "Previously, three deep (sub)mm surveys had been carried out in this field" (3.1 Submm emission) [from Geach et al. 2005; Tamura et al. 2013; Hine et al. 2016]

## Processing

### Calibration

- pipeline or manual: VLA: CASA Calibration Pipeline, then manual RFI flagging; ALMA: standard CASA reduction  
  > "Data were first processed through the VLA Common Astronomy Software Applications (CASA) Calibration Pipeline by NRAO staff, performing basic flagging and calibration." (2.3 VLA observations); "The data were reduced with the CASA package in a standard manner" (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: VLA mosaic made with CASA task CLEAN  
  > "The final mosaic of images was created with CASA task CLEAN" (2.3 VLA observations)
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
- smoothing: SCUBA-2 map convolved with 30 arcsec smoothed beam  
  > "the map is convolved with a smoothed beam of 30$\ensuremath{''}$ to optimize the detection of point sources" (2.1 JCMT/SCUBA-2 observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction details  
  > "for the details see Umehata et al. 2017b and Matsuda et al. in preparation" (2.2 ALMA observations) [from Umehata et al. 2017b; Matsuda et al. in preparation]
- IR SED template method for SFRs  
  > "we will follow the method described in Umehata et al. (2015) to use SED templates of well studied starburst galaxies" (3.3 Star formation rates) [from Umehata et al. (2015)]
- SCUBA-2 reduction  
  > "see also Hine et al. 2016 for more details" (2.1 JCMT/SCUBA-2 observations) [from Hine et al. 2016]

### Not stated but needed to reproduce (our reading)

- ALMA beams, rms, uv-coverage, imaging weights and flux extraction method
- ALMA calibrators and CASA version
- SED template fitting details and the extinction treatment
- Lyα escape fraction definition details
- Stacking procedure for undetected LABs

## Analysis recipe

1. **Measure SCUBA-2 and VLA fluxes at LAB positions**: SCUBA-2 850 um map smoothed to 30 arcsec; VLA S-band mosaic; detection thresholds 2.5 sigma submm and 4 sigma radio  
  > "9 out of the 35 LABs are detected in dust emission with peak SNRs above 2.5$\sigma$" (3.1 Submm emission); "Among the remaining 22 LABs, 9 are detected above 4$\sigma$." (3.2 Radio emission)
   - software: CASA, smurf
   - fitting: _not stated_
   - validation: Cross-checked with ALMA and VLA positions; chance-coincidence probabilities estimated from number counts  
  > "These consistent results support the reliability of the SCUBA-2 and VLA data, even for the marginal detections." (3.1 Submm emission)
2. **Derive SFRs from Lyα, IR and radio**: Lyα: SFR=0.62 L_Lyα/1e42; IR: SED templates integrated 8-1000 um, SFR=1.46 L_FIR/1e10 Lsun; radio: Bell (2003) with alpha=-0.8  
  > "SFR($\rm{Ly\alpha}$)/(M$_{\odot}$/yr)=$0.62~\times\thinspace L_{\rm Ly\alpha}$/(10$^{42}$ erg s$^{-1}$)" (3.3 Star formation rates); "SFR($L_{\rm FIR}$)/(M$_{\odot}$/yr)=$1.46\times$$L_{\rm FIR}$/(10$^{10}$ $L_{\odot}$)" (3.3 Star formation rates)
   - assumption: Unreddened Lyα/Hα = 8.7:1; radio spectral index alpha = -0.8; templates Arp 220, M82, ALESS composite, SMM J2135-0201  
  > "We use an unreddened Ly$\alpha$/H$\alpha$ ratio of 8.7:1" (3.3 Star formation rates); "a typical spectral index commonly adopted for SMGs (e.g., Ivison et al. 2010) is $\alpha$ = $-$0.8" (3.3 Star formation rates)
   - fitting: Best-fit SED for each template to redshift and SCUBA-2/ALMA measurements; median and min/max reported  
  > "We created best fit SEDs for each template based on redshift and SCUBA-2/ALMA measurements." (3.3 Star formation rates)
   - validation: _not stated_
3. **Test for radio excess (AGN)**: q_FIR parameter and SFR_radio/SFR_submm ratios compared with the Magnelli et al. 2015 redshift evolution  
  > "following the method described in Magnelli et al. (2015), we use the parametrisation of the FRC, q$_{\rm FIR}$, to study the radio excess in our sample" (4.2.1 Submm and radio detections)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive Lyα escape fraction**: Ratio of Lyα-derived SFR to dust-derived SFR; lower limits from SCUBA-2 upper limits and stacking  
  > "the Ly$\alpha$ escape fraction can also be calculated from the ratio of Ly$\alpha$ to dust continuum derived SFRs" (4.3 Lyα escape fraction)
   - fitting: _not stated_
   - validation: Compared with escape fractions of LAEs in the literature  
  > "which is consistent with our stacking results for the majority of the LABs" (4.3 Lyα escape fraction)

## Software

- **CASA** : ALMA and VLA reduction and VLA imaging (CLEAN)  
  > "The final mosaic of images was created with CASA task CLEAN" (2.3 VLA observations)
- **smurf makemap** : SCUBA-2 data reduction  
  > "Data reduction was carried out using the SubMillimeter User Reduction Facility (smurf) *makemap* pipeline (Chapin et al. 2013)" (2.1 JCMT/SCUBA-2 observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Submm-detected LABs | 11 of 35 | not stated | count | 1 | Dust continuum sources have been identified in 11 of the 35 LABs, all with star formation rates (SFRs) above 100M$_{\odot}$/yr. |
| Radio-detected LABs | 9 of 29 | not stated | count | 1 | Likely radio counterparts are detected in 9 out of 29 investigated LABs. |
| Median Lyα escape fraction, submm-detected LABs | about 3% | range ~2% to 45% | percent | 4 | The Ly$\alpha$ escape fraction ranges from $~$2% to 45% among the submm-detected LABs, with a median value of about 3%. |
| Lyα escape fraction lower limit, stacked undetected LABs | 11% | not stated | percent | 4 | leading to a lower limit of $f_{\rm esc}^{\rm Ly\alpha}$ to be 11%. |
| ALMA total flux density LAB18 | 9.47 | 0.36 | mJy | 1 | with a total flux density of 9.47$\pm$0.36 mJy |

## Qualitative findings

- Submm detection is more linked to Lyα physical size than to Lyα luminosity.  
  > "The detection of submm dust emission is more linked to the physical size of the Ly$\alpha$ emission than to the Ly$\alpha$ luminosities of the LABs." (abstract)
- All X-ray counterparts avoid LAB centres, while most radio sources without X-ray are central.  
  > "However, all X-ray counterparts avoid the central regions." (abstract)

## Claim tuples

- H: Is a radio excess (AGN) common in submm/radio detected LABs? | E: q_FIR and SFR_radio/SFR_submm comparison | R: 8 of 10 LABs detected in both have ratios above 2.5 | F: Radio excess is common, suggesting AGN presence | **supported**
- H: Do submm-detected LABs have lower Lyα escape fractions? | E: Compare Lyα SFR to dust SFR | R: Median ~3% versus a lower limit of 11% for undetected | F: High dust attenuation, dense environment and extinction-correction uncertainties may explain the difference | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Hard to discriminate between SF and AGN powering; SCUBA-2 beam and positional uncertainty limit identification.  
  > "However, it is very difficult to discriminate between predominately SF or AGNs powered LABs." (4.2.1 Submm and radio detections)
- Caveat (inferred, ours): ALMA data cover only 6 of 35 LABs and are treated as secondary, with details deferred to other papers
- Caveat (inferred, ours): SFRs depend on the assumed SED templates and a single radio spectral index
- Caveat (inferred, ours): Escape fraction from Lyα/dust SFR ignores resonant-scattering geometry and extinction corrections

## Reproducibility

- Data public (paper): ALMA projects cited in acknowledgements; SCUBA-2 and VLA project IDs given in Table  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00162.S and ADS/JAO.ALMA#2013.1.00704.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA imaging and flux extraction parameters
- Missing: SED fitting code and details
- Missing: Lyα luminosities and areas taken from Matsuda et al. 2004
- Data volume (inferred): ALMA ~tens of GB; VLA 41 h ~hundreds of GB; SCUBA-2 reduced maps
- Score (inferred): 3/5, Multi-facility with ALMA minor; the SFR and escape-fraction recipe is clear but ALMA processing is deferred.
- Rediscovery candidate: no, ALMA role is minor and most of the pipeline relies on SCUBA-2/VLA data and external catalogues.

## Links

- Method: Umehata et al. 2017b (cite: 2017ApJ...835...98U) (ALMA data reduction)
- Method: Hine et al. 2016 (cite: 2016MNRAS.460.4075H) (SCUBA-2 reduction)
- Method: Magnelli et al. 2015 (cite: 2015A&A...573A..45M) (FIR/radio correlation method)
- Companion: Matsuda et al. in preparation (ALMA observations of LABs)
- Companion: Ao et al. in preparation (SMGs in the same region)
- Related: JCMT SCUBA-2 Cosmology Legacy Survey (S2CLS)
- Related: SSA22 protocluster surveys

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 30,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
