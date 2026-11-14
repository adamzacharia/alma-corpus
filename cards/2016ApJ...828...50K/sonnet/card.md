# The Molecular Clouds Fueling A 1/5 Solar Metallicity Starburst

`2016ApJ...828...50K` | The Astrophysical Journal 2016 | first author: Kepley, Amanda A. | arXiv: 1607.01779 | DOI: 10.3847/0004-637X/828/1/50

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, astrochemistry
- Question: How do the molecular clouds, CO-to-H2 conversion factor and dust in the low-metallicity starburst blue compact dwarf II Zw 40 compare with other galaxies?  
  > "Our goal is to understand how the interplay of intense star formation and low metallicity within this galaxy shapes its molecular gas and dust" (Introduction)
- Target **II Zw 40**: coordinates 5:55:42.63161, 3:23:31.2387 (aperture center)  
  > "this galaxy is also only 10 Mpc away (cite: 1988cng..book.....T)" (Introduction); "centered at (5:55:42.63161, 3:23:31.2387)" (2.2 Continuum Emission in II Zw 40); z/distance 10 Mpc  
  > "this galaxy is also only 10 Mpc away (cite: 1988cng..book.....T)" (Introduction); "centered at (5:55:42.63161, 3:23:31.2387)" (2.2 Continuum Emission in II Zw 40); distance from Tully & Fisher 1988 (cite: 1988cng..book.....T)  
  > "this galaxy is also only 10 Mpc away (cite: 1988cng..book.....T)" (Introduction); "centered at (5:55:42.63161, 3:23:31.2387)" (2.2 Continuum Emission in II Zw 40)

## Data provenance

- ALMA projects: 2012.1.00984.S
- bands: 3 mm, 1 mm, 870 um (Bands 3, 6, 7)  
  > "observations of the CO and continuum emission from the central starburst region of the prototypical blue compact dwarf galaxy II Zw 40 at 3, 1 mm, and 870$\mu$m" (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.54x0.49 arcsec line cubes (~24 pc); 1 arcsec continuum  
  > "$0.54\times0.49$" (Table 3)
- max recoverable scale: ~12.4 arcsec  
  > "The largest angular scale of these images is approximately 12.4$''$." (Data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 Aug 30 (3 mm), 2014 Jun 14 (1 mm), 2013 Oct 09 (870um)  
  > "| Date | 2014 August 30 | 2014 June 14 | 2013 Oct 09 |" (Table 1)
- pi or archival as stated: PI A. Kepley, Cycle 1  
  > "ALMA Cycle 1 (proposal 2012.1.00984.S; PI: A. Kepley)" (Data)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 12CO J=1-0 (115.2712 GHz)
- Other facility **VLA**: 4.86, 8.46, 22.46 GHz continuum from Kepley et al. 2014  
  > "the VLA data from (cite: 2014AJ....147...43K)" (Data)
- Other facility **Herschel**: mid/far-IR photometry and fit from Remy-Ruyer 2013  
  > "we have added the mid- and far-infrared Herschel photometry and resulting fit from (cite: 2013A&A...557A..95R)" (2.2)
- External data: VLA continuum data  
  > "the VLA data from (cite: 2014AJ....147...43K)" (Data) [from (cite: 2014AJ....147...43K)]
- External data: Archival VLA HI data  
  > "we use archival VLA neutral hydrogen data (cite: 1998AJ....116.1186V)" (2.2) [from (cite: 1998AJ....116.1186V)]
- External data: Dust beta=1.71, T=33 K, dust mass 1.9e5 Msun  
  > "setting $\beta$ and the temperature to the values derived by (cite: 2013A&A...557A..95R): 1.71 and 33K" (2.2) [from (cite: 2013A&A...557A..95R)]
- External data: IRAM 30m CO(2-1) intensity 0.69 K km/s  
  > "single dish observations with the IRAM 30m is 0.69 $\rm{K \, km \, s^{-1}}$ (cite: 2004AaA...414..141A)" (2.1) [from (cite: 2004AaA...414..141A)]
- External data: Comparison cloud samples (MW, LMC, IC 10, Antennae, NGC 253)  
  > "It includes cloud samples from the Milky Way disk (cite: 2009ApJ...699.1092H)" (3) [from (cite: 2009ApJ...699.1092H); (cite: 2011ApJS..197...16W); (cite: 2006ApJ...643..825L); (cite: 2014ApJ...795..156W); (cite: 2015ApJ...801...25L)]

## Processing

### Calibration

- pipeline or manual: 870um and 1mm manual NAASC scripts in CASA; 3 mm CASA pipeline  
  > "The 870$\mu$m and 1 mm data were calibrated in CASA (cite: 2007ASPC..376..127M) using scripts provided by the North American ALMA Science Center (NAASC)." (Data)
- casa version: _not stated_
- pipeline version: Cycle2-R1-B (3 mm)  
  > "The 3 mm data were calibrated using the CASA pipeline version Cycle2-R1-B" (Data)
- archive products used as is: _not stated_
- flux calibrator: J0510+180, quasar; 0.75 Jy (870um), 1.5 Jy (1mm), 1.56 Jy (3mm)  
  > "Extrapolating between these two values gives a flux density for J0510+180 of 0.75 Jy." (Data)
- flux scale uncertainty: 10% at 870um; 20% at 3 mm and 1 mm  
  > "within 10% for the 870$\mu$m data and within 20% for the 3 mm and 1 mm data" (Data)
- self calibration: not applied; too faint  
  > "The data were not self-calibrated because the line and continuum emission from the source was too faint." (Data)

### Imaging

- task: CASA  
  > "We imaged the data in CASA." (Data)
- deconvolver: _not stated_
- weighting robust: robust = 0 for line cubes; natural for continuum  
  > "we imaged the line data sets with robust = 0 to maximize angular resolution" (Data)
- uv taper: inner uv limit 16 klambda, taper to 1 arcsec, common 1 arcsec beam  
  > "We imposed a inner uv plane limit of 16$k\lambda$ to match the largest angular scale and tapered the naturally weighted data to a $1\ensuremath{''}$ resolution" (Data)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: line cubes smoothed to the same beam  
  > "smoothed to the same beam size" (Data)
- final beam: 0.54x0.49 arcsec PA 28 deg (lines)  
  > "$0.54\times0.49$" (Table 3)
- final rms: CO(3-2) 2.6 mJy/beam, CO(2-1) 3.74 mJy/beam at 2 km/s  
  > "| 2.6 | 0.1 |" (Table 3)

### Inherited from earlier work

- VLA continuum data and SFR (0.34 Msun/yr), SED comparison  
  > "See the analysis in §4.1 of (cite: 2014AJ....147...43K) for a detailed discussion of this point." (Data) [from (cite: 2014AJ....147...43K)]
- Cloud property corrections (extrapolation to 0K, resolution correction)  
  > "corrected for the angular and velocity resolution of the data as described in (cite: 2006PASP..118..590R)" (3.1) [from (cite: 2006PASP..118..590R)]
- Dust kappa 4.5 m2/kg  
  > "This value is based on the models of (cite: 2004ApJS..152..211Z) and is the same value used in (cite: 2013A&A...557A..95R)." (2.2) [from (cite: 2004ApJS..152..211Z); (cite: 2013A&A...557A..95R)]

### Not stated but needed to reproduce (our reading)

- CASA version for the 870um and 1mm calibration
- line-free channels and continuum subtraction method
- image size, cell size, deconvolver, clean threshold, masks
- how the uv-matching and spectral smoothing were done in detail
- Monte Carlo/fit details of the SED fit (sampler, priors)
- exact cprops parameters beyond those given and handling of unresolved clouds
- exact pointing/phase center of the observed field

## Analysis recipe

1. **Calibrate and image data**: NAASC scripts/CASA pipeline; imaging with robust=0 line cubes and uv-matched tapered 1 arcsec continuum  
  > "we imaged the line data sets with robust = 0 to maximize angular resolution while retaining some sensitivity to larger-scale emission" (Data)
   - software: CASA
   - fitting: _not stated_
   - validation: VLA fluxes within 10% of Kepley et al. 2014; bandpass calibrator checked flux scale within 5%  
  > "Adopting the extrapolated flux density for J0510+180 yields a flux density within 5% of its measured flux." (Data)
2. **Fit continuum SED**: Two power law (free-free index -0.1 + synchrotron) fit in 9 arcsec aperture excluding 1 mm and 870um  
  > "We fit a simple two power law model to these values" (2.2)
   - parameter: nu0 = 4.86 GHz; 9 arcsec diameter aperture  
  > "set $\nu_0$ to 4.86 GHz" (2.2)
   - assumption: free-free spectral index fixed at -0.1  
  > "p_{th} \left(\frac{\nu}{\nu_0}\right)^{-0.1}" (2.2)
   - fitting: 2-parameter fit (p_th, alpha_nt); reduced chi2 0.18  
  > "The reduced $\chi^2$ value for the best fit is 0.18." (2.2)
   - validation: _not stated_
3. **Derive dust mass and gas-to-dust ratio**: Modified blackbody to ALMA dust excess with beta and T fixed to Remy-Ruyer values  
  > "we derive an estimate of the dust mass using only the ALMA data by setting $\beta$ and the temperature to the values derived by (cite: 2013A&A...557A..95R): 1.71 and 33K" (2.2)
   - assumption: kappa = 4.5 m2/kg; beta 1.71; T=33 K; distance 10 Mpc  
  > "We assume a value for $\kappa(\lambda_0)$ of 4.5 ${\rm m^2 \, kg^{-1}}$." (2.2)
   - fitting: _not stated_
   - validation: beta 1.71 to 2.0 changes mass <10%  
  > "Changing $\beta$ from 1.71 to 2.0 changes the mass by less than 10%." (2.2)
4. **Identify clouds and measure properties**: cprops on CO(3-2) cube: 5 sigma in two channels, expand to 2 sigma, decomposition box 0.35" x 0.35" x 6 km/s, contrast 1.5 sigma  
  > "we used a box of 0.35$''$ by 0.35$''$ by 6 $\rm{km \, s}^{-1}$" (3.1)
   - software: cprops
   - assumption: CO(3-2) scaled to CO(1-0) with 10 K blackbody (6 K for cloud G)  
  > "using a 10K blackbody" (3.1)
   - fitting: Gaussian fit to cloud sizes with beam and channel deconvolved  
  > "were taken from the Gaussian fit to the cloud sizes with the beam and channel width deconvolved" (3.1)
   - validation: Monte Carlo (100 iterations) errors; clumpfind gives similar results  
  > "After 100 iterations, we calculated the standard deviation of the resulting clump properties and used this value as the error." (3.1)
5. **Derive alpha_CO**: Slope in L_CO vs virial mass; dust-based via gas-to-dust ratio 650; Wolfire et al. 2010 model with resolved W_CO; Narayanan Eq. 7  
  > "by fitting a slope to the resolved giant molecular cloud population in ${\rm L_{CO}}$-$M_{vir}$ space" (3.2)
   - assumption: virial equilibrium; delta_GDR=650; Delta A_V=0.7  
  > "Assuming that the clouds in II Zw 40 are in virial equilibrium" (3.2)
   - fitting: _not stated_
   - validation: compared to dust-based and model estimates  
  > "we can use the simple photodissociation model developed by (cite: 2010ApJ...716.1191W) to estimate $\alpha_{co}$." (The CO-to-H$_2$ Conversion Factor)
6. **Star formation efficiency and cloud scaling relations**: SFE=SFR/M_H2; size-linewidth, C^2, Mach number compared to literature samples  
  > "SFE=SFR/$M_{H_2}$" (3.3)
   - assumption: c_s = 0.2 km/s (10 K)  
  > "We adopt a value of 0.2 $\rm{km \, s}^{-1}$ for $c_s$" (3.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** pipeline Cycle2-R1-B (3 mm): calibration and imaging  
  > "We imaged the data in CASA." (Data)
- **cprops** : cloud identification and properties  
  > "We used the cprops algorithm (cite: 2006PASP..118..590R) to identify individual molecular clouds" (3.1)
- **clumpfind** : alternative decomposition check  
  > "An alternative decomposition algorithm – clumpfind (cite: 1994ApJ...428..693W)" (3.1)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha_CO (virial) | 18.1 | 0.5 | Msun (K km/s pc2)^-1 | 5 | we derive a value for $\alpha_{co}$ of $18.1\pm0.5$ |
| alpha_CO upper estimate | 150.5 | not stated | Msun (K km/s pc2)^-1 | 5 | (18.1 to 150.5 |
| thermal fraction at 4.86 GHz | 0.34 | range 0 to 0.7 | dimensionless | 2 | The best fit thermal fraction is 0.34 with a range of 0 to 0.7 |
| non-thermal spectral index | -0.3 | range -0.21 to -0.87 | dimensionless | 2 | best fit non-thermal spectral index is -0.3 with a range of -0.21 to -0.87 |
| dust mass (ALMA) | 1.8e4 | 0.2e4 | Msun | 3 | We obtain a dust mass of $(1.8\pm0.2) \times 10^4 \ \ensuremath{\rm{M}_\odot}$ |
| gas-to-dust ratio | 720 to 3500 | not stated | dimensionless | 3 | These values give a range for $\delta_{GDR}$ of 720 to 3500. |
| molecular SFE (largest alpha_CO) | 6e-9 | not stated | yr^-1 | 6 | molecular star formation efficiency for II Zw 40 of $6 \times 10^{-9} \, {\rm yr}^{-1}$ |
| molecular SFE (virial alpha_CO) | 4e-8 | not stated | yr^-1 | 6 | $4 \times 10^{-8} \, {\rm yr}^{-1}$ |
| median Mach number | 36 | range 20-76 | dimensionless | 6 | The median Mach number of clouds in II Zw 40 is $\sim36$ with values ranging from 20 to 76. |
| CO(1-0) luminosity (9 arcsec aperture) | 3.8e5 | not stated | K km/s pc2 | 3 | corresponds to a $\rm{^{12} CO ({1}-{0})}$ luminosity of $3.8 \times 10^5$ |
| CO(2-1) flux resolved out | ~30% | not stated | percent | 1 | Approximately 30% of the total $\rm{^{12} CO ({2}-{1})}$ emission in II Zw 40 is resolved out by our ALMA observations. |

## Qualitative findings

- Only one of eight molecular clouds has associated star formation  
  > "Only one of eight molecular clouds has associated star formation." (abstract)

## Claim tuples

- H: Is the CO-to-H2 conversion factor elevated in II Zw 40? | E: Virial, dust-based and photodissociation-model estimates | R: 18.1 to 150.5 Msun (K km/s pc2)^-1 | F: alpha_CO is 4 to 35 times the Milky Way value | **supported**
- H: Is dust dominant in the submm continuum? | E: SED fit of VLA+ALMA matched images | R: dust only ~50% at 870um | F: continuum dominated by free-free and synchrotron | **supported**
- H: Is the SFE intrinsically higher? | E: SFR/M_H2 with derived alpha_CO | R: at least 10x higher than spirals | F: likely due to burst-dominated history | **partially**
- H: Do clouds' linewidths arise from high external pressure? | E: size-linewidth coefficients vs surface density | R: high coefficients like Antennae | F: high surface densities from merger shocks, not pressure | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum flux resolved out (~50%), so dust mass lower limit and GDR overestimate  
  > "we only recover $\sim$50% of the emission from this galaxy" (Data)
- Limitation (authors): Quasars used for flux calibration add flux scale uncertainty  
  > "which introduces additional uncertainty into the flux density scale" (Data)
- Caveat (inferred, ours): alpha_CO depends on assumed r31 and virial equilibrium
- Caveat (inferred, ours): only one pointing and few clouds, small-number statistics
- Caveat (inferred, ours): cloud decomposition parameters were tuned by eye

## Reproducibility

- Data public (paper): ALMA project cited with acknowledgment of the data; public status not stated explicitly  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2012.1.00984.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA versions and detailed tclean parameters
- Missing: line-free channels
- Missing: exact cprops inputs
- Data volume (inferred): ~50-200 GB raw for three bands
- Score (inferred): 3/5, Data are identifiable and main steps described, but imaging details and several literature inputs are missing.
- Rediscovery candidate: yes, Public ALMA data, numeric results such as alpha_CO and dust mass; recipe mostly stated.

## Links

- Method: (cite: 2006PASP..118..590R) (cprops algorithm)
- Method: (cite: 2010ApJ...716.1191W) (photodissociation model for alpha_CO)
- Companion: (cite: 2014AJ....147...43K) (VLA data and SFR of II Zw 40)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
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
  "facts": 84,
  "stated": 56,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
