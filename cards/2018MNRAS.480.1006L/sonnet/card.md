# The curious case of II Lup: a complex morphology revealed with SAM/NACO and ALMA

`2018MNRAS.480.1006L` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Lykou, Foteini | arXiv: 1808.00279 | DOI: 10.1093/mnras/sty1903

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, stellar_physics
- Question: What is the morphology of the circumstellar envelope of the carbon-rich AGB star II Lup, and is it non-spherical (spiral, binary-shaped) from near-IR aperture masking and archival ALMA data?  
  > "To test the validity of the asymmetries detected with aperture masking, we retrieved an ALMA data set from the archive" (7.2 Tracing the circumstellar envelope with ALMA)
- Target **II Lup**: coordinates 15 23 05.075 -51 25 58.73 (2MASS, J2000)  
  > "We have adopted the distance of 590 pc proposed by (cite: groenewegen2002a) and (cite: menzies2006)." (2.1 On the astrometry and distance.); "2MASS            | 15 23 05.075     | -51 25 58.73" (Table 1); z/distance 590 pc  
  > "We have adopted the distance of 590 pc proposed by (cite: groenewegen2002a) and (cite: menzies2006)." (2.1 On the astrometry and distance.); "2MASS            | 15 23 05.075     | -51 25 58.73" (Table 1); distance from Groenewegen 2002a and Menzies 2006, from the period-luminosity relation of Whitelock 2006  
  > "We have adopted the distance of 590 pc proposed by (cite: groenewegen2002a) and (cite: menzies2006)." (2.1 On the astrometry and distance.); "2MASS            | 15 23 05.075     | -51 25 58.73" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00070.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 39 12 m antennas  
  > "in an array configuration containing 39 of the 12 m antennas" (3.3 ALMA)
- configurations: _not stated_
- baselines: 15.06 m to 1574.37 m  
  > "minimum and maximum baselines of 15.06 m and 1574.37 m respectively" (3.3 ALMA)
- angular resolution: max resolution 0.42 arcsec at ~115.27 GHz  
  > "This provides a maximum resolution of 0.42 arcsec at frequency $\sim$115.27 GHz" (3.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: RMS 5 mJy per 2.54 km/s channel  
  > "The final image created has an RMS noise of 5mJy in a single 2.54 km s$^{-1}$ line-free channel" (3.3 ALMA)
- time on source: _not stated_
- observing dates: 2015 August 16  
  > "The ALMA observations were conducted on 2015 August 16" (3.3 ALMA)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.276 GHz)
- Line: HC3N J=11-10 (100.083 GHz)
- Line: CS J=2-1 (97.9873 GHz)
- Line: SiO v=0, J=2-1 (86.8526 GHz)
- Other facility **VLT/NACO SAM**: Ks, L', M' aperture-masking interferometry (9-hole mask)  
  > "We have used the 9–hole mask where each hole corresponds to an effective aperture of 0.92 metres." (3.1 NACO)
- Other facility **VLT/VISIR**: mid-IR images, unresolved, not used  
  > "The raw images indicated that II Lup is unresolved in both filters" (3.2 VISIR)
- External data: Gas expansion velocity 22.2 km/s  
  > "We adopt the gas expansion velocity $v_\text{exp}=22.2$ km s$^{-1}$(cite: nyman1993)" (7.1) [from (cite: nyman1993)]
- External data: Period-luminosity relation for C-rich Miras  
  > "Using the Period-Luminosity relation for carbon-rich Miras of (cite: whitelock2006) ($M_\text{bol}=-2.54\log P+1.87$)" (6.1) [from (cite: whitelock2006)]

## Processing

### Calibration

- pipeline or manual: Archive reduction scripts re-creating the calibrated measurement set  
  > "processed using the reduction scripts from the archive to re-create the fully calibrated measurement set" (3.3 ALMA)
- casa version: CASA 5.1.1-5 (imaging)  
  > "The calibrated data were imaged in casa ver.5.1.1-5 (cite: CASA)" (3.3 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "with the task tclean" (3.3 ALMA)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using a natural weighting of the visibilities" (3.3 ALMA)
- uv taper: 0.7 arcsec; baselines <30 m removed  
  > "Visibilities from the baselines less than 30 m were also removed during imaging as they contributed a large scale artefact" (3.3 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.144 x 0.821 arcsec2, elongated east-west  
  > "has a synthesised beam of $1.144\times 0.821$ arcsec$^2$, elongated east-west" (3.3 ALMA)
- final rms: 5 mJy per 2.54 km/s channel  
  > "RMS noise of 5mJy in a single 2.54 km s$^{-1}$ line-free channel" (3.3 ALMA)

### Inherited from earlier work

- SAM data reduction pipeline  
  > "We followed the standard data reduction process for SAM data using a pipeline developed at the University of Sydney" (3.1 NACO) [from (cite: tuthill2000; lacour2011)]
- Spiral analysis and arm separation to orbital period equation  
  > "we follow the analysis of (cite: mayer2013) to determine initial parameters for the putative spiral around II Lup" (7.2) [from (cite: mayer2013)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size for tclean
- Spectral window and channel choices and velocity frame
- Continuum subtraction and line-free channels
- Deconvolver, threshold and masking
- Method for primary beam correction
- How the radial cuts and peak positions were measured
- Spiral toy-model parameters (flattening, starting angle)
- Details of ALMA flux calibration

## Analysis recipe

1. **Image archival ALMA line cubes**: tclean on the archive-calibrated MS with natural weights, 0.7 arcsec uv-taper, baselines <30 m removed  
  > "using a natural weighting of the visibilities and a $uv$-taper of 0.7 arcsec to taper the signal from the longest baselines" (3.3 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure spiral arm separation from CO radial cuts**: Radial cuts in four directions from the 2MASS position; peaks measured and median separations computed; toy-model spiral overplotted  
  > "we obtain radial cuts in the CO image in four directions: south, north, east and west." (7.2)
   - fitting: _not stated_
   - validation: Compared with spiral models of Homan et al. 2015 via P-V diagrams  
  > "We compare these diagrams to the work of (cite: homan2015)" (7.2)
3. **Derive orbital period from arm separation**: rho = v_exp P pi (Mayer et al. 2013)  
  > "We derive an orbital period of about 128 years." (7.2)
   - assumption: v_exp = 22.2 km/s, distance 590 pc  
  > "for the adopted distance of 590 pc" (7.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1-5: ALMA imaging with tclean  
  > "imaged in casa ver.5.1.1-5 (cite: CASA), with the task tclean" (3.3 ALMA)
- **macim** : SAM image reconstruction  
  > "macim (cite: ireland2006) and mira (cite: thiebaut2008)" (3.1 NACO)
- **mira** : SAM image reconstruction with sparco  
  > "We used mira by incorporating the tool sparco (cite: kluska2014)" (5)
- **period04** : period analysis of IR light curves  
  > "We have re-analysed all available infrared time-series photometry from the literature with period04" (2.4)
- **Aladin** : astrometry  
  > "We extracted astrometric information on II Lup using the `Aladin`[^3] tool" (2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median CO spiral arm separation | 1.7 | not stated | arcsec | 2 | We find a median separation of 1.7 arcsec. |
| Number of spiral windings detected in CO | 12 | not stated | dimensionless | 2 | a total of 12 windings were detected, out to the largest distance of 23 arcsec |
| Orbital period from arm spacing | 128 | not stated | yr | 3 | We derive an orbital period of about 128 years. |
| CO envelope extent | 23 | not stated | arcsec | 1 | extends as far out as 23 arcsec from the central source in the CO (1–0) transition |

## Qualitative findings

- CO, SiO, CS and HC3N maps all show spiral signatures  
  > "All four images show a clear spiral signature." (7.2)

## Claim tuples

- H: Is the envelope of II Lup spiral-shaped, implying binarity? | E: Archival ALMA CO, SiO, CS and HC3N channel maps; radial cuts of CO | R: 12 windings with median separation 1.7 arcsec | F: A spiral exists; implied orbital period of 128 yr at 590 pc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO image affected by missing short spacings; large structure resolved out  
  > "The ALMA CO image is significantly affected by missing short spacings." (7.2)
- Caveat (inferred, ours): Spiral and period rest on assumed distance 590 pc and v_exp
- Caveat (inferred, ours): Spiral fit is a qualitative toy model without uncertainties
- Caveat (inferred, ours): The 1.7 arcsec separation is single-epoch and velocity-channel dependent

## Reproducibility

- Data public (paper): Data retrieved from the ALMA archive  
  > "were extracted from the ALMA archive" (3.3 ALMA)
- Products in archive: _not stated_
- Missing: Image and cell size, channel selection and masking
- Missing: Radial cut and peak-finding procedure
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public archival data and basic imaging parameters, but many details unstated and the spiral analysis is qualitative.
- Rediscovery candidate: no, Imaging recipe incomplete and the key results are partly qualitative.

## Links

- Method: (cite: mayer2013) (Spiral arm separation and orbital period equations)
- Method: (cite: homan2015) (Simulated P-V diagrams of AGB spirals)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 66,
  "stated": 35,
  "rate": 0.53
 },
 "evidence_ok": true
}
```
