# ALMA observations of the nearby AGB star L<SUB>2</SUB> Puppis. I. Mass of the central star and detection of a candidate planet

`2016A&A...596A..92K` | Astronomy and Astrophysics 2016 | first author: Kervella, P. | arXiv: 1611.06231 | DOI: 10.1051/0004-6361/201629877

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, exoplanets, stellar_physics
- Question: What is the mass of the AGB star L2 Pup A from the Keplerian gas rotation, and is there a companion (source B) detected in continuum and CO emission?  
  > "With the goal of precisely determining the mass of the AGB star, we obtained very high angular resolution observations in ALMA’s band 7 ($330-360$ GHz), covering several molecular lines and the continuum" (1 Introduction)
- Target **L2 Puppis**: coordinates 07:13:32.47687, -44:38:17.8443 (continuum peak)  
  > "The position of the continuum peak was located at $\alpha = 07$:13:32.47687, $\delta = -44$:38:17.8443 with an absolute position uncertainty of $\pm 7$ mas." (2 Observations and data reduction); "At a distance of $64 \pm 4$ pc ($\pi = 15.61\pm 0.99$ mas, )" (1 Introduction); z/distance 64 ± 4 pc (parallax 15.61 ± 0.99 mas)  
  > "The position of the continuum peak was located at $\alpha = 07$:13:32.47687, $\delta = -44$:38:17.8443 with an absolute position uncertainty of $\pm 7$ mas." (2 Observations and data reduction); "At a distance of $64 \pm 4$ pc ($\pi = 15.61\pm 0.99$ mas, )" (1 Introduction); distance from Hipparcos parallax (van Leeuwen 2007)  
  > "The position of the continuum peak was located at $\alpha = 07$:13:32.47687, $\delta = -44$:38:17.8443 with an absolute position uncertainty of $\pm 7$ mas." (2 Observations and data reduction); "At a distance of $64 \pm 4$ pc ($\pi = 15.61\pm 0.99$ mas, )" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00141.S
- bands: Band 7 (330-360 GHz)  
  > "very high angular resolution observations in ALMA’s band 7 ($330-360$ GHz)" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2.5 GHz of line-free continuum  
  > "Obvious spectral lines were identified in the visibility data, leaving 2.5 GHz of line-free continuum." (2 Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 0.09 to 16 km, 45 antennas  
  > "Forty-five antennas were present for most of the observations, providing baselines from 0.09 to 16 km and resulting in an angular resolution better than 15 mas." (2 Observations and data reduction)
- angular resolution: 17.7 x 14.5 mas, PA 73 deg (continuum, natural weighting)  
  > "The continuum image (made with natural weighting) has a synthesized beam size $17.7 \times 14.5$ mas at position angle (PA) 73$^\circ$." (2 Observations and data reduction)
- max recoverable scale: about 200 mas  
  > "giving a maximum angular scale of about 200 mas for reliable imaging" (2 Observations and data reduction)
- sensitivity: _not stated_
- time on source: 84 min total on target  
  > "The target was observed for a total of 84 min" (2 Observations and data reduction)
- observing dates: 5 November 2015 (two executions)  
  > "L$_2$ Pup was observed on 5 November 2015 at UT08:39:25" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 29SiO v=0 J=8-7 (342.98085 GHz)
- Line: 12CO v=0 J=3-2 (345.79599 GHz)
- Line: 13CO v=0 J=3-2 (330.58797 GHz)
- Other facility **VLT/SPHERE-ZIMPOL**: Visible companion detection and plume features used for comparison  
  > "The relative position of source B with respect to A is closely coincident with that of the companion detected by at visible wavelengths." (2.1 Secondary source L2 Pup B)
- Other facility **AAVSO**: Visible light curve to place ALMA epoch in pulsation phase  
  > "The AAVSO light curve[^1] of L$_2$ Pup at visible wavelengths presented in Fig. [3](#aavso) shows" (3.1.1 Flux from L2 Pup A)
- External data: Photospheric angular diameter theta_LD = 17.9 ± 1.6 mas from near-infrared interferometry  
  > "The angular diameter of the photosphere of L$_2$ Pup A has been measured by using near-infrared interferometry at $\theta_\mathrm{LD} = 17.9 \pm 1.6$ mas" (3.1.1 Flux from L2 Pup A) [from not given in text (cite key stripped)]
- External data: Disk inclination i = 84 deg and 82 deg from earlier studies  
  > "has been estimated by to $i = 84^\circ$ and slightly revised by to $i = 82^\circ$." (3.2.2 Mass of the central object) [from not given in text (cite key stripped)]
- External data: Hipparcos parallax 15.61 ± 0.99 mas  
  > "$\pi = 15.61\pm 0.99$ mas" (1 Introduction) [from van Leeuwen 2007]
- External data: PARSEC+COLIBRI TP-AGB isochrones, version PR16, from CMD 2.8  
  > "We retrieved the isochrones from the CMD 2.8 web site[^2]." (4.1 Mass and evolutionary state of L2 Pup A) [from Marigo et al. models, not given in text]

## Processing

### Calibration

- pipeline or manual: Standard human-steered ALMA data reduction scripts  
  > "Standard human-steered ALMA data reduction scripts were used ." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0538-4405 at 1.04488 Jy at 338.994438 GHz, spectral index -0.596  
  > "The flux density of J0538-4405 was taken as 1.04488 Jy at 338.994438 GHz, spectral index $-0.596$" (2 Observations and data reduction)
- flux scale uncertainty: 7% overall  
  > "the overall flux scale accuracy is 7%." (2 Observations and data reduction)
- self calibration: Iterative phase and amplitude self-calibration using continuum clean components as model  
  > "The clean components of this image were used as a model for phase self-calibration, and iterative cycles of phase and amplitude self-calibration were performed." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (continuum)  
  > "The continuum image (made with natural weighting)" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: 2.5 mas pixel  
  > "A 2.5 mas pixel size and a field of view of $2.56\ensuremath{''}$ were used for all images unless otherwise stated." (2 Observations and data reduction)
- image size: field of view 2.56 arcsec  
  > "A 2.5 mas pixel size and a field of view of $2.56\ensuremath{''}$ were used for all images unless otherwise stated." (2 Observations and data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 17.7 x 14.5 mas, PA 73 deg  
  > "has a synthesized beam size $17.7 \times 14.5$ mas at position angle (PA) 73$^\circ$." (2 Observations and data reduction)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Imaging task, deconvolver, clean threshold and masks
- Robust/weighting used for line cubes
- Line-free channels and continuum subtraction method for line cubes
- Self-calibration solution intervals and number of iterations
- Software and version used for calibration and imaging (CASA not named)
- Details of PVD derivative peak finding and Keplerian fit code
- Which Hipparcos and photometric inputs were used in COLIBRI isochrone selection

## Analysis recipe

1. **Measure continuum fluxes of A and B**: Fit 2D elliptical Gaussian to central source and subtract it; measure residual at B; subtract dust contribution estimated from the disk  
  > "we estimated the contribution of the central star by fitting a two-dimensional elliptical Gaussian to the central source and we subtracted it from the continuum image." (3.1.2 Secondary source L2 Pup B)
   - parameter: f_dust at A = 1.4 ± 0.3 mJy/beam; at B = 1.34 ± 0.10 mJy/beam  
  > "we find $f_\mathrm{dust} = 1.34 \pm 0.10$ mJy beam$^{-1}$" (3.1.2 Secondary source L2 Pup B)
   - assumption: Dust emission at B equals that at the point symmetric about the star  
  > "We estimate the dust contribution from a point in the disk located symmetrically to B with respect to the central star" (3.1.2 Secondary source L2 Pup B)
   - fitting: _not stated_
   - validation: Compared f_A with blackbody expectation of 92 mJy (T=3500 K, 18 mas)  
  > "we verified that the measured flux from the central AGB star $f_A$ is close to the emission of $f = 92$ mJy expected for a blackbody" (3.1.1 Flux from L2 Pup A)
2. **Build position-velocity diagrams and locate inflection points**: PVDs from cubes with 20 mas east-west slit; derivative along position axis gives radius of maximum slope per velocity bin  
  > "We computed PVDs for each emission line from the reconstructed ALMA image cubes using a virtual slit of 20 mas oriented in the east-west direction" (3.2.1 Position velocity diagrams)
   - parameter: slit 20 mas, PA = 90 deg  
  > "a virtual slit of 20 mas oriented in the east-west direction (position angle $PA = 90^\circ$" (3.2.1 Position velocity diagrams)
   - fitting: _not stated_
   - validation: Argued inflection point is insensitive to Gaussian broadening and beam convolution  
  > "would not change the position of the point of inflection" (3.2.1 Position velocity diagrams)
3. **Fit Keplerian profile for central mass**: Fit Keplerian velocity profile to inflection points between 2.5 and 4.5 AU; correct for inclination  
  > "The yellow curve in Fig. [7](#29SiO-pvd) represents the best-fit Keplerian velocity profile to the inflection points, adjusted between radii of 2.5 and 4.5 AU." (3.2.2 Mass of the central object)
   - parameter: position uncertainty fixed at ±2.5 mas, velocity uncertainty ±0.5 km/s  
  > "The radial position uncertainty in the point of inflection is fixed in the fit at $\pm 2.5$ mas (one reconstructed image pixel), and the velocity uncertainty to $\pm 0.5$ km s$^{-1}$." (3.2.2 Mass of the central object)
   - assumption: i = 82 ± 5 deg; parallax 15.61 mas; B mass not subtracted  
  > "We therefore adopt a value of $i = 82 \pm 5^\circ$." (3.2.2 Mass of the central object)
   - fitting: Least-squares-type fit with fixed errors (sampler/likelihood not stated)  
  > "The radial position uncertainty in the point of inflection is fixed in the fit at $\pm 2.5$ mas (one reconstructed image pixel), and the velocity uncertainty to $\pm 0.5$ km s$^{-1}$." (Analysis, Mass of the central object)
   - validation: _not stated_
4. **Fit sub-Keplerian outer profile**: Power law fit for 6<R<20 AU  
  > "The adjustment of a power law to the observed profile in the sub-Keplerian domain ($6 < R < 20$ AU)" (3.3 Sub-Keplerian disk rotation)
   - fitting: _not stated_
   - validation: _not stated_
5. **Detect molecular emission from B**: Subtract eastern PVD from western PVD (east scaled by 0.8, median smoothed 7.5 mas x 1.2 km/s)  
  > "We applied a global multiplicative factor of 0.8 to the east PVD as the emission is stronger in average (possibly due to absorption from dust), and we smoothed it using a moving median box" (3.4 Molecular emission from L2 Pup B)
   - fitting: _not stated_
   - validation: _not stated_
6. **Mass of B from barycenter offset**: Compare photocenter of A (2D Gaussian fit to continuum) with center of rotation G from matching east/west Keplerian velocities; m_B = d(Ph-G)/(d(BA)-d(Ph-G)) x m_A  
  > "We measured the position of $G$ by matching the Keplerian velocities on each side of the PVD (east and west) of the $^{29}$SiO$(\varv=0,J=8-7)$ line" (4.2.1 Mass from molecular disk dynamics)
   - assumption: Only one companion besides star A  
  > "We assumed in this reasoning that only one companion source is present in addition to the central star A." (4.2.1 Mass from molecular disk dynamics)
   - fitting: _not stated_
   - validation: _not stated_
7. **Orbital radius and period of B**: R_B from projected separation and sub-Keplerian projected velocity; Kepler's third law  
  > "Its orbital radius $R_B$ is necessarily larger than its currently observed radius $R_0$ from A" (4.2.2 Orbital period and radius)
   - assumption: Circular orbit coplanar with the disk  
  > "We assumed that the orbit of B is circular and coplanar with the disk." (4.2.2 Orbital period and radius)
   - fitting: _not stated_
   - validation: Consistent with astrometric displacement between ZIMPOL and ALMA epochs  
  > "this period is consistent with the small observed astrometric displacement of source B between the ZIMPOL (2014.93) and ALMA (2015.84) epochs" (4.2.2 Orbital period and radius)
8. **Compare A with evolutionary models**: Compare mass, radius, log g, L, Teff, period with PARSEC+COLIBRI TP-AGB isochrones (no interpolation)  
  > "We chose to not interpolate them as the correlations between parameters are potentially complex." (4.1 Mass and evolutionary state of L2 Pup A)
   - software: PARSEC, COLIBRI
   - parameter: Z = 0.008 (sub-solar, thick-disk)  
  > "we therefore adopted a sub-solar metallicity of $Z=0.008$." (4.1 Mass and evolutionary state of L2 Pup A)
   - fitting: _not stated_
   - validation: Delta between model and observed in sigma (Table)  
  > "The agreement between the model and observed parameters is very good." (4.1 Mass and evolutionary state of L2 Pup A)

## Software

- **PARSEC+COLIBRI (PR16)** PR16: TP-AGB isochrones for evolutionary state  
  > "database of PARSEC+COLIBRI models of thermally pulsating AGB stars (TP-AGB) developed by in version PR16" (4.1 Mass and evolutionary state of L2 Pup A)
- **Astropy** : Python analysis (general)  
  > "This research made use of Astropy[^3], a community-developed core Python package for Astronomy ." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass of L2 Pup A | 0.659 | ±0.011 (stat) ±0.041 (parallax syst); ±0.043 combined (6.6%) | Msun | 3 | $m_A = 0.659\pm 0.011\pm 0.041\,M_\odot$ ($\pm 6.6\%$) |
| m sin i within 2.5 AU | 0.653 | ±0.011 ±0.041 | Msun | 3 | $$m_\mathrm{2.5\,AU} \sin(i) = 0.653\pm 0.011\pm 0.041\ M_\odot,$$ |
| Flux ratio f_B/f_A at 338 GHz | 1.28 | ±0.13 | percent | 1 | $$\begin{equation}
f_B / f_A = 1.28 \pm 0.13\%.
\end{equation}$$ |
| Net flux of A | 77.2 | ±0.3 | mJy/beam | 1 | f_A = 77.2 \pm 0.3\ \mathrm{mJy\,beam}^{-1}. |
| Net flux of B | 0.99 | ±0.11 | mJy/beam | 1 | f_B = 0.99 \pm 0.11\ \mathrm{mJy\,beam}^{-1}, |
| Projected separation of B | 30.6 mas = 1.96 AU | ±2.5 mas, ±0.16 AU | mas / AU | 1 | $\rho = 30.6\pm 2.5$ mas, which is equivalent to a linear radius of $R_0 = 1.96\pm 0.16$ AU |
| Radial velocity of B | 12.2 | ±1.0 | km/s | 5 | $v_0 = +12.2 \pm 1.0$ km s$^{-1}$ |
| Mass of B | 12 | ±16 | Mjup | 6 | & = & 12\pm 16\,M_\mathrm{Jup}. |
| Orbital radius of B | 2.43 | ±0.16 | AU | 7 | $R_B = 2.43 \pm 0.16$ AU |
| Orbital period of B | 4.69 | ±0.45 | yr | 7 | the orbital period is $P_\mathrm{orb} = 4.69 \pm 0.45$ years |
| Sub-Keplerian velocity law, 6-20 AU | v = 40.7 R^-0.853 | ±5.5 on amplitude, ±0.059 on index | km/s (R in AU) | 4 | v = (40.7\pm 5.5) \times R^{(-0.853\pm 0.059)} \ \mathrm{km}\ \mathrm{s}^{-1} |

## Qualitative findings

- Gas rotation is Keplerian inside the dust cavity (R<~5 AU) and sub-Keplerian beyond the dust inner rim (6 AU)  
  > "changes from the purely Keplerian regime in the central cavity ($v \approx R^{-1/2}$) to a markedly sub-Keplerian regime beyond the inner rim of the dust disk (6 AU)" (3.3 Sub-Keplerian disk rotation)
- L2 Pup A had a near-solar main-sequence mass and is an analog of the future Sun  
  > "Its initial mass on the main sequence was very close to solar" (4.1 Mass and evolutionary state of L2 Pup A)

## Claim tuples

- H: Can the mass of the AGB star be measured from the gas kinematics? | E: Keplerian fit to 29SiO PVD inflection points between 2.5 and 4.5 AU | R: m_A = 0.659 ± 0.043 Msun | F: Gas is Keplerian in the cavity, mass determined to 6.6%, dominated by parallax error | **supported**
- H: Is there a companion in the ALMA data? | E: PSF subtraction of continuum and east-west PVD subtraction in CO lines | R: Source B at ~30 mas, f_B/f_A=1.28%, CO excess at 12.2 km/s | F: Source B detected in continuum and CO | **supported**
- H: What is the nature of B? | E: Barycenter offset between photocenter and rotation center of the gas disk | R: m_B = 12 ± 16 Mjup | F: Most likely a planet or low-mass brown dwarf, though a dense clump cannot be formally excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Derivative of PVD is less sensitive to angular resolution than a fixed flux threshold  
  > "Compared to the use of a fixed flux detection threshold, for instance, this technique has the advantage to be less sensitive to the angular resolution of the observation" (3.2.1 Position velocity diagrams)
- Alternative: Very low-mass star excluded at 4 sigma; dense coreless aggregate disfavoured by persistence over one year  
  > "we can exclude that it is a very low-mass star at a $4\sigma$ level." (4.3 Nature of L2 Pup B); "The persistence of source B over a period of one year favors the hypothesis of a compact object over a core-less aggregate." (4.3.2 Persistence over time)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass of B has no firm lower limit; assumes a single companion  
  > "We emphasize, however, that the properties of source B are still uncertain as we do not have a firm lower limit on its mass." (Conclusion)
- Limitation (authors): Extended slow envelope is resolved out by long baselines  
  > "there exists an extended, slowly expanding, diffuse envelope that is resolved out by the long baselines of the interferometer" (Appendix 12CO line)
- Caveat (inferred, ours): Measured flux of A is ~20% below blackbody expectation, with the explanation speculative
- Caveat (inferred, ours): Fixed 2.5 mas and 0.5 km/s fit errors are not derived from data
- Caveat (inferred, ours): Mass of B depends on sub-mas photocenter alignment and assumes photocenter equals center of mass
- Caveat (inferred, ours): Orbit of B assumed circular and coplanar, with only two epochs
- Caveat (inferred, ours): Inclination adopted from literature affects mass

## Reproducibility

- Data public (paper): ALMA data cited with project code in acknowledgements  
  > "This article makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00141.S ." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Self-calibration details
- Missing: Code for PVD derivative analysis and fits
- Missing: Cited literature values for inclination and stellar parameters
- Data volume (inferred): ~100-500 GB raw for two executions of a long-baseline band 7 setup with high spectral resolution
- Score (inferred): 3/5, Public data and clear analysis chain, but imaging and fitting parameters are only partially stated and software versions are missing.
- Rediscovery candidate: no, Data are public, but the recipe lacks imaging and fitting details, and the core measurements depend on custom PVD analysis.

## Links

- Companion: Kervella et al. 2015, A&A 578, A77 (Earlier SPHERE/ZIMPOL detection of the companion and plumes (inferred from reference list))
- Companion: Kervella et al. 2014, A&A 564, A88 (NACO discovery of the edge-on disk and stellar parameters (inferred))
- Related: VLT/SPHERE-ZIMPOL
- Related: VLT/NACO

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 55,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
