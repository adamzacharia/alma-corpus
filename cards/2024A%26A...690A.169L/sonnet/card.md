# Neutral atomic and molecular gas dynamics in the nearby spiral galaxies NGC 1512, NGC 4535, and NGC 7496

`2024A&A...690A.169L` | Astronomy and Astrophysics 2024 | first author: Laudage, Sebastian | arXiv: 2407.04531 | DOI: 10.1051/0004-6361/202450265

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: Can H I kinematics constrain the disk orientation so as to improve CO and H I rotation curve determination, and what radial motions/mass flows do they show?  
  > "The hypothesis is that H I can provide a good probe of the gas disk’s intrinsic orientation, as long as additional factors that affect H I and CO are taken into consideration on a galaxy-by-galaxy basis." (Introduction)
- Target **NGC 1512**: coordinates 4h03m54.1s, -43d20m55s  
  > "NGC 1512 | SB(r)ab | $4^{\text{h}}03^{\text{m}}54.1^{\text{s}}$" (Table 1); z/distance 17.92±0.88 Mpc (Vsys 871.4 km/s)  
  > "NGC 1512 | SB(r)ab | $4^{\text{h}}03^{\text{m}}54.1^{\text{s}}$" (Table 1); distance from _not stated_
- Target **NGC 4535**: coordinates 12h34m20.31s, +8d11m56s  
  > "NGC 4535 | SAB(s)c | $12^{\text{h}}34^{\text{m}}20.31^{\text{s}}$" (Table 1); z/distance 15.77±0.37 Mpc (Vsys 1953.6 km/s)  
  > "NGC 4535 | SAB(s)c | $12^{\text{h}}34^{\text{m}}20.31^{\text{s}}$" (Table 1); distance from _not stated_
- Target **NGC 7496**: coordinates 23h09m47.3s, -43d25m40s  
  > "NGC 7496 | SBb | $23^{\text{h}}09^{\text{m}}47.3^{\text{s}}$" (Table 1); z/distance 18.72±2.82 Mpc (Vsys 1639.2 km/s)  
  > "NGC 7496 | SBb | $23^{\text{h}}09^{\text{m}}47.3^{\text{s}}$" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: CO spectral resolution 2.5 km/s; H I 5.5 km/s per channel  
  > "The spectral resolution is 2.5 km s^−1^." (2.3 PHANGS-ALMA CO observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec (~100 pc) for CO(2-1); 15 arcsec for MeerKAT H I  
  > "at an angular resolution of ${\sim}1''$ which corresponds to linear scales of ${\sim}\SI{100}{\parsec}$" (2.3 PHANGS-ALMA CO observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **MeerKAT**: H I 21cm cubes, 6 h per galaxy, 15 arcsec, 5.5 km/s  
  > "The galaxies (see [\[table:Properties\]](#table:Properties)) were each observed for 6 hours in a frequency range from 1.411 GHz to 1.414 GHz." (2.2 MeerKAT 21cm observations)
- External data: PHANGS-ALMA CO(2-1) data products (cubes, moment1 wprior maps)  
  > "To trace the molecular component we used observations from the PHANGS-ALMA survey (cite: 2021ApJS..257...43L)." (2.3 PHANGS-ALMA CO observations) [from (cite: 2021ApJS..257...43L)]
- External data: Previous CO rotation curves for comparison and initial Vrot  
  > "We overplotted the results with previous RCs derived by (cite: 2020ApJ...897..122L), which represent the latest kinematic analysis of these galaxies." (4.2 CO Rotation Curves) [from (cite: 2020ApJ...897..122L)]
- External data: Star formation rates  
  > "Star formation rates taken from (cite: 2019ApJS..244...24L)" (Table 2 caption) [from (cite: 2019ApJS..244...24L)]

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
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CO: PHANGS 'moment1 wprior' map from strict mask; H I strict mask (core S/N>4 in 2 channels, outer S/N>2)  
  > "we used another product offered by the PHANGS-ALMA pipeline, the "moment1 wprior" map." (2.3 PHANGS-ALMA CO observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Strict masking procedure for H I  
  > "We used the strict masking procedure described in (cite: 2021ApJS..257...43L) that was initially used for the PHANGS-ALMA CO(2-1) observations." (2.2 MeerKAT 21cm observations) [from (cite: 2021ApJS..257...43L)]
- Radial velocity fitting approach  
  > "following an approach similar to (cite: 2021ApJ...923..220D), we fit the radial velocities in a singular run" (3.3 Radial Velocities) [from (cite: 2021ApJ...923..220D)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes and PHANGS-ALMA data product version
- 3DBarolo version and parameter file (ring separation, Bezier order, mask/normalization settings)
- Exact Bezier function parameters
- H I cube processing details

## Analysis recipe

1. **Fit H I tilted rings**: 3D tilted-ring fits in staged runs: free fit, fix center/Vsys, regularize geometry, fit Vrot and sigma  
  > "Once the geometry of the galaxy is fixed, the kinematics are fitted." (3.2)
   - software: 3DBarolo
   - parameter: ring width 15 arcsec; weighting |cos θ|^2; rings with Vrot errors >±30 km/s dropped  
  > "Rings that have large error bars ($>\SI{\pm30}{\kilo\meter\per\second}$) on the V$_{\text{rot}}$ values are neglected from here on." (3.2)
   - fitting: 3DBarolo default error calculation  
  > "based on $^{\text{3D}}$Barolo’s default error calculation method" (3.2)
   - validation: Residual maps, scale height tests, comparison with literature  
  > "we created residual maps by subtracting the modeled velocities from the observations" (5.1)
2. **Fit CO rotation curves**: Start from H I best fit; fix center and Vsys; thin disk z0=100 pc; fit i, phi, Vrot, sigma then fix geometry  
  > "After a first initial fitting stage where $i$, $\phi$, V$_{\text{rot}}$, and $\sigma_{\text{gas}}$ are kept free to vary, the geometry ($i$ and $\phi$) is fixed" (3.2)
   - software: 3DBarolo
   - fitting: _not stated_
   - validation: Compared to Lang et al. 2020 curves  
  > "Overall the circular velocities derived by $^{\text{3D}}$Barolo  agree well with the values from the previous work by (cite: 2020ApJ...897..122L)" (4.2)
3. **Radial velocities and mass flow rates**: Fit Vrad with other parameters fixed, sin^2 φ weighting; Mdot=2πRΣHI Vrad ×1.33 for helium  
  > "the H I  mass flow $\dot{M}_{\text{HI}}$ is multiplied by the factor 1.33 which takes the primordial abundance of helium into account" (3.4 Mass flow rates)
   - software: 3DBarolo ELLPROF
   - assumption: Optically thin H I  
  > "when assuming that the H I  emission is optically thin" (3.4 Mass flow rates)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **3DBarolo** : 3D tilted ring fits of H I and CO  
  > "we compute rotation curves using $^{\text{3D}}$Barolo which fits tilted ring models to emission line data cubes in three dimensions" (3 Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NGC 1512 H I Vrot,max | 177.3 | 16.4 | km/s | 1 | $177.3\pm16.4$ |
| NGC 4535 H I Vrot,max | 188.8 | 6.2 | km/s | 1 | $188.8\pm6.2$ |
| NGC 7496 CO Vrot,max | 118.11 | 6.09 | km/s | 2 | $118.11\pm6.09$ |
| NGC 1512 average mass flow | 2.02 | 1.85 | Msun/yr | 3 | NGC 1512 / $0.75\pm0.75$ / $4.47\pm8.1$ / $2.02\pm1.85$ |

## Qualitative findings

- H I and CO rotation curves agree for most overlapping radii; radial flows are consistent with little net mass flow except NGC 1512.  
  > "The H I  and CO circular velocities are in agreement for most bins where measurements overlap." (5.3)

## Claim tuples

- H: H I-derived orientation can be used to fit CO rotation curves | E: H I-based geometry used as input for CO 3DBarolo fits and compared to Lang et al. 2020 | R: CO and H I curves agree in most overlapping bins | F: Recommend using H I to model disk orientation before deriving CO RCs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample and large uncertainties preclude definitive conclusions on radial flows  
  > "The limited sample size and the presence of substantial uncertainties in our data preclude us from making definitive conclusions." (5.4)
- Caveat (inferred, ours): Only three galaxies
- Caveat (inferred, ours): Non-circular bar motions not modeled
- Caveat (inferred, ours): Constant scale height assumed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project codes and data versions
- Missing: MeerKAT H I cubes access
- Missing: 3DBarolo settings
- Data volume (inferred): ~tens of GB
- Score (inferred): 3/5, Public PHANGS products but H I data and fit settings partly unspecified.
- Rediscovery candidate: no, MeerKAT cubes and detailed settings not stated as public.

## Links

- Method: (cite: 2015MNRAS.451.3021D) (3DBarolo)
- Method: (cite: 2021ApJS..257...43L) (PHANGS-ALMA data and masking)
- Companion: (cite: Eibensteiner2024) (MeerKAT H I data)
- Related: PHANGS-ALMA
- Related: PHANGS-MeerKAT

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00392.S",
  "2017.1.00886.L",
  "2018.1.01651.S",
  "2018.A.00062.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 27,
  "rate": 0.391
 },
 "evidence_ok": true
}
```
