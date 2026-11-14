# The Extraordinary Outburst in the Massive Protostellar System NGC 6334I-MM1: Flaring of the Water Masers in a North-South Bipolar Outflow Driven by MM1B

`2018ApJ...866...87B` | The Astrophysical Journal 2018 | first author: Brogan, C. L. | arXiv: 1809.04178 | DOI: 10.3847/1538-4357/aae151

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How did the 22 GHz water masers in NGC 6334I change after the MM1B accretion outburst, and how do they relate to outflows traced by ALMA CS (6-5)?  
  > "In this paper, we present follow-up observations with the VLA in 1.3 cm H$_2$O maser emission." (Introduction)
- Target **NGC 6334I (MM1, MM1B, CM2, MM3-UCHII, MM4, MM7)**: coordinates _not stated_; z/distance not stated explicitly; 1'' ~ 1300 au implied (3000 au = 2.2'')  
  > "We find remarkable flaring in the H$_2$O maser emission coinciding with the synchrotron source CM2, $2.2\ensuremath{''}$ (3000 au) north of MM1B" (Introduction); distance from not stated (cites Chibueze14; Reid14 as relatively nearby)  
  > "We find remarkable flaring in the H$_2$O maser emission coinciding with the synchrotron source CM2, $2.2\ensuremath{''}$ (3000 au) north of MM1B" (Introduction)

## Data provenance

- ALMA projects: 2015.A.00022.T
- bands: ALMA 1 mm; VLA K-band 1.3 cm (22.235 GHz) and C-band 5 cm  
  > "The ALMA 1 mm observations presented in this paper are from project 2015.A.00022.T" (2.2 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: VLA A, A, B configs for three maser epochs (2011 Sep 09, 2017 Jan 08, 2017 Oct 08)  
  > "| Antenna Configuration | A | A | B |" (Table 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CS (6-5) beam 0.28''x0.21'' at -84 deg; 1 mm continuum 0.24''x0.17''  
  > "The synthesized beam of the 1 mm continuum image is $0.24\ensuremath{''} \times 0.17\ensuremath{''}$ ($-84\ensuremath{^\circ}$), while the synthesized beam of the CS (6-5) image is $0.28\ensuremath{''} \times 0.21\ensuremath{''}$ at $-84\ensuremath{^\circ}$." (ALMA Observations)
- max recoverable scale: smooth structures <~6''  
  > "These data are sensitive to smooth spatial structures $\lesssim 6\ensuremath{''}$ in size." (2.2 ALMA Observations)
- sensitivity: 1 mm continuum 0.6 mJy/beam; CS (6-5) emission-free channels 3 mJy/beam  
  > "The sensitivity of the 1 mm continuum is 0.6 mJy beam$^{-1}$, while the sensitivity of the CS (6-5) channels free of significant emission is 3 mJy beam$^{-1}$." (2.2 ALMA Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CS J=6-5 (293.9120865 GHz)
- Line: H2O maser 22 GHz (22.235 GHz)
- Other facility **VLA**: Three epochs of 22 GHz H2O maser spectral line data  
  > "The VLA 22.235 GHz water maser spectral line data presented in this paper arise from three epochs: 2011.7, 2017.0, and 2017.8" (2.1 VLA Observations)
- External data: 6.7 GHz methanol and 6.035 GHz OH maser positions (2016.9 epoch) and 5 cm continuum  
  > "the 2016.9 epoch 6.7 GHz methanol and 6.035 GHz excited OH maser positions reported by (cite: Hunter18)" (Discussion) [from (cite: Hunter18)]
- External data: 2011.7 epoch VLA water maser data first presented earlier  
  > "The 2011.7 epoch data were also presented in (cite: Brogan16)." (2.1 VLA Observations) [from (cite: Brogan16)]

## Processing

### Calibration

- pipeline or manual: VLA pipeline in CASA for the two new epochs; strong maser feature used for iterative self-calibration  
  > "The two new epochs of 1.3 cm data were calibrated using the VLA pipeline[^1] in the Common Astronomy Software Applications (CASA) package." (2.1 VLA Observations); "A strong maser feature was used to iteratively self-calibrate the spectral line data for each dataset." (2.1 VLA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C286 (VLA)  
  > "| Flux calibrator | 3C286 | 3C286 | 3C286 |" (Table 1)
- flux scale uncertainty: 10%  
  > "do not include the flux calibration uncertainty of 10%" (Table 2 notes)
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
- continuum subtraction: uv continuum subtraction in CASA using line-free channels from STATCONT c-SCM plus aggregate deviation spectrum  
  > "These channels are then used to perform uv continuum subtraction in CASA." (2.2 ALMA Observations)
- line free channels: Channels with aggregate deviation spectrum below a manually adjusted level; typically 10-20% of bandwidth  
  > "For NGC 6334I, the continuum bandwidth identified using this method is typically $10-20\%$ of the total observed spectral bandwidth." (2.2 ALMA Observations)
- primary beam correction: applied to ALMA images and VLA maser flux densities  
  > "primary beam correction was applied to the images presented here" (2.2 ALMA Observations)
- array combination: _not stated_
- smoothing: CS (6-5) imaged at 2 km/s resolution; VLA cubes 0.25 km/s channels  
  > "that were imaged with a spectral resolution of 2 km s$^{-1}$" (2.2 ALMA Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA 1 mm data previously described  
  > "have been described in earlier publications which showed the 1 mm dust continuum image" (2.2 ALMA Observations) [from (cite: Hunter18); (cite: McGuire17)]
- C-band 5 cm continuum from epoch 2016.9 originally described elsewhere  
  > "The C-band 5 cm continuum data from epoch 2016.9 used in this paper were originally described in (cite: Hunter18)." (2.1 VLA Observations) [from (cite: Hunter18)]
- Line-free channel method relies on STATCONT c-SCM  
  > "first uses the corrected sigma clipping method (c-SCM) approach of STATCONT (cite: Sanchez18)" (2.2 ALMA Observations) [from (cite: Sanchez18)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration details (CASA version, calibrators, pipeline vs manual)
- tclean parameters for the CS (6-5) cube (weighting/robust, cell, image size, masking, deconvolver)
- Final ALMA line-free channel list and ADS threshold
- VLA CASA version and imaging parameters (weighting, cell size) for maser cubes
- Distance adopted for au conversions
- Details of the parabola fit to bow shock and the proper-motion fitting method

## Analysis recipe

1. **Calibrate VLA data and image maser cubes**: VLA pipeline in CASA, Hanning smoothing, self-calibration on strong maser, Stokes I cubes at 0.25 km/s  
  > "Stokes I cubes of the maser emission were made with a channel spacing (and effective spectral resolution) of 0.25 km s$^{-1}$." (2.1 VLA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Removed correlator ghost artifacts at -36 dB  
  > "We have removed these false components from our analysis." (2.1 VLA Observations)
2. **Fit maser spots per channel**: Fit Gaussian point sources to each channel with emission >=6 sigma, with primary beam correction  
  > "We fit each channel of the water maser cube that had significant emission ($\ge 6\sigma$) with an appropriate number of Gaussian point sources" (3.1 Water masers)
   - parameter: 6 sigma threshold  
  > "We fit each channel of the water maser cube that had significant emission ($\ge 6\sigma$)" (3.1 Water masers)
   - fitting: Gaussian point-source fits, initial guess from pixel peaks  
  > "using the pixel position of each emission peak as the initial guess for the fitted parameters" (3.1 Water masers)
   - validation: Discarded weak artifacts in dynamic-range-limited channels  
  > "A few weak sources that could be attributed to imaging artifacts in the dynamic-range limited channels were discarded" (3.1 Water masers)
3. **Image CS (6-5) outflows**: Identify line-free channels with STATCONT-based method, uv continuum subtraction, image CS (6-5), integrated intensity maps  
  > "we have developed a technique of identifying relatively line-free channels" (2.2 ALMA Observations)
   - software: STATCONT, CASA
   - parameter: alpha=3; SCL corrected by -0.5 sigma_SCM (case D)  
  > "The SCL is then corrected for noise by $-0.5\sigma_{\rm SCM}$ (case D of STATCONT)." (2.2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive bulk proper motion and dynamical time of southern masers**: Compare box positions of UCHII-W1/W2 between 2011.7 and 2017.0 over 5.33 yr; combine with radial velocity for inclination  
  > "If we interpret the shift in position of the maser associations between epochs as bulk motion over the intervening 5.33 yr" (4.4)
   - assumption: Systemic velocity -7 km/s; theta_inc = theta_H2O  
  > "by assuming $\theta_{inc} = \theta_{H_2O}$, we can now refine to a dynamical time estimate" (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : VLA pipeline calibration and ALMA uv continuum subtraction  
  > "These channels are then used to perform uv continuum subtraction in CASA." (2.2 ALMA Observations)
- **STATCONT** : Continuum level via c-SCM for line-free channel selection  
  > "first uses the corrected sigma clipping method (c-SCM) approach of STATCONT (cite: Sanchez18)" (2.2 ALMA Observations)
- **Astropy** : Python analysis package  
  > "Astropy, a community-developed core Python package for Astronomy (cite: astropy)" (Acknowledgments)
- **APLpy** : Plotting  
  > "APLpy (cite: aplpy2012), an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Proper motion of UCHII-W1/W2 | 0.0182 | 0.0019 | arcsec/yr | 4 | the implied vector sum proper motion on the sky plane is $0.0182\pm0.0019~\ensuremath{''}$ yr$^{-1}$ |
| Sky-plane velocity | 112 | 12 | km/s | 4 | a sky plane velocity estimate of $112\pm12$ km s$^{-1}$ |
| 3D jet velocity | 117 | 12 | km/s | 4 | the 3D vector velocity is $v_{\rm jet}=117\pm12$ km s$^{-1}$ |
| Dynamical time (refined) | 166 | 22 | yr | 4 | dynamical time estimate of $\sim 166\pm22$ yr |
| CM2 total integrated flux ratio 2017.8/2011.7 | 6.5 | not stated | dimensionless | 2 | / CM2 Total   / ...            / ...            / 1840   / 11500  / 12000  / 6.3               / 6.5 |
| Bow shock radius of curvature | 0.12'' (~150 au) | not stated | arcsec | 0 | yields a radius of curvature $r_0=0.12\ensuremath{''} \approx 150$ au |
| Jet-to-ambient density ratio | <0.066 | not stated | dimensionless | 0 | which implies a density ratio between the jet and the ambient medium of $\eta < 0.066$ |

## Qualitative findings

- Water masers near MM1 weakened while CM2 masers flared, forming a bow shock pointing back to MM1B  
  > "Since the outburst, the water maser emission toward MM1 has substantially weakened." (abstract)

## Claim tuples

- H: Flaring CM2 water masers trace the interaction of an MM1B outflow with ambient gas | E: Three-epoch VLA water maser imaging and ALMA CS (6-5) imaging | R: Bow shock pattern with vertex at CM2; N-S CS outflow encompassing masers | F: Masers trace the MM1B N-S outflow; radiative energy of outburst strengthened northern masers | **supported**
- H: Southern water masers show bulk motion away from MM1B | E: Compare UCHII-W1/W2 positions in 2011.7 and 2017.0 | R: 0.0182''/yr, 112 km/s sky-plane, 3D 117 km/s | F: Dynamical time ~170 yr | **supported**
- H: Outburst dust heating reduces water maser pumping near MM1 | E: Compare maser fluxes across epochs | R: MM1 masers faded by factors of 5 to 16 | F: Attributed to increased dust temperature reducing pump efficiency | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: NGC 6334I-South maser might be associated with star TPR-9 outflow or pumped by beamed MM1B radiation; cannot exclude  
  > "we cannot exclude the possibility that this maser was somehow pumped by narrowly beamed radiation from MM1B" (4.5)
- How they decided it was enough: _not stated_
- Limitation (authors): CS line emission not modelled because Band 10 data scales do not match  
  > "we have not attempted to model the CS line emission" (3.3)
- Caveat (inferred, ours): Proper motion is from box offsets between two epochs with different array configs; systematic error not fully explored
- Caveat (inferred, ours): Inclination assumed from radial velocity of masers
- Caveat (inferred, ours): ALMA processing details sparse
- Caveat (inferred, ours): Distance not stated in text

## Reproducibility

- Data public (paper): ALMA project 2015.A.00022.T acknowledged; VLA project codes listed  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.A.00022.T." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA imaging parameters
- Missing: Distance adoption
- Missing: Maser grouping/association assignment criteria
- Missing: Bulk motion box definitions
- Data volume (inferred): ~100-300 GB for ALMA band 6/7 data plus ~tens of GB VLA
- Score (inferred): 3/5, Data sources clear and maser fitting described, but many ALMA imaging and motion-measurement details are missing.
- Rediscovery candidate: no, Recipe incomplete for the ALMA imaging and proper motion measurement.

## Links

- Method: (cite: Sanchez18) (STATCONT continuum level method)
- Companion: (cite: Hunter18) (Methanol and OH maser observations of the same outburst)
- Companion: (cite: Brogan16) (Initial ALMA/VLA observations of NGC 6334I)
- Companion: (cite: Hunter17) (ALMA confirmation of sustained outburst on MM1B)
- Related: VLA 493_1
- Related: VLA 16B-402
- Related: VLA 17B-258

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 39,
  "rate": 0.549
 },
 "evidence_ok": true
}
```
