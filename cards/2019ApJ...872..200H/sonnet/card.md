# ALMA Observations of the Massive Molecular Outflow G331.512-0.103. II. Physical Properties, Kinematics, and Geometry Modeling

`2019ApJ...872..200H` | The Astrophysical Journal 2019 | first author: Hervías-Caimapo, Carlos | arXiv: 1812.09779 | DOI: 10.3847/1538-4357/aaf9ac

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical conditions, kinematics and geometry of the massive molecular outflow and ambient core G331.512-0.103, from 18 newly analyzed ALMA band 7 lines?  
  > "Here we investigate for the first time 18 newly analyzed lines, along with the 4 already analyzed there, with the goal of characterizing the physical conditions, kinematics and morphology of the massive molecular outflow." (Introduction)
- Target **G331.512-0.103**: coordinates RA 16h12m10.09s, Dec -51d28m38.4s (J2000)  
  > "This source is located in the tangent of the Norma spiral arm, at a heliocentric distance of $\sim 7.5$ kpc" (Introduction); "centered at $\alpha_{2000} = 16^h12^m10.09^s$, $\delta_{2000} = -51\ensuremath{^\circ} 28\ensuremath{'} 38.4\ensuremath{''}$" (Observations); z/distance ~7.5 kpc  
  > "This source is located in the tangent of the Norma spiral arm, at a heliocentric distance of $\sim 7.5$ kpc" (Introduction); "centered at $\alpha_{2000} = 16^h12^m10.09^s$, $\delta_{2000} = -51\ensuremath{^\circ} 28\ensuremath{'} 38.4\ensuremath{''}$" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00524.S
- bands: Band 7, Cycle 0  
  > "The observations were performed with the Atacama Large Millimeter/submillimeter Array (ALMA) during Cycle 0, as described in ." (Observations)
- frequencies and spectral setup: 4 spectral windows centered at 345.8, 347.2, 357.3, 358.6 GHz, each 1875 MHz, 3840 channels  
  > "The four spectral windows (SW) are centered at 345.8, 347.2, 357.3 and 358.6 GHz, each extending over 1875 MHz and consisting on 3840 channels." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam 1.38" x 0.68", PA -37.6 deg  
  > "the synthesized beam was $1.38\ensuremath{''} \times 0.68\ensuremath{''}$, with a position angle of $-37\ensuremath{^\circ}.6$." (Observations)
- max recoverable scale: ~11-14.0"  
  > "The interferometric observations miss the recovery of large spatial scales above $\sim 11-14.0\ensuremath{''}$." (Observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: SiO J=8-7 (not stated)
- Line: HC3N J=38-37, v7=1 (346.9491233 GHz)
- Line: HC3N J=38-37 (345.60901 GHz)
- Other facility **APEX**: SiO(7-6) and (8-7) single-dish spectra, used for SiO excitation temperature and line ratio  
  > "we use the single-beam ($\sim 18.0\ensuremath{''}$) observations of SiO(J$=7-6$) and (J$=8-7$) from obtained with APEX." (4.1.5 SiO shocks)
- External data: SiO rotational temperatures from APEX: 123±15 K (blue), 138±29 K (red)  
  > "$123\pm15$ K (blue wing) and $138\pm29$ K (red wing)." (Estimation of column density and temperature) [from (cite: merello_2013)]
- External data: Dust opacity kappa=1.89 cm2/g  
  > "$\kappa_{\nu}=1.89$ cm$^2$g$^{-1}$ (cite: ossenkopf_1994)" (Fractional abundances) [from (cite: ossenkopf_1994)]
- External data: SiO shock model grid (pre-shock density, shock velocity)  
  > "Following the model of (cite: gusdorf_2008), we compare our observations of SiO(J$=8-7$) with the rotational spectra simulated in that work." (4.1.5 SiO shocks) [from (cite: gusdorf_2008)]
- External data: Dust temperatures 35 K (SED) and 400 K used as limits for abundances  
  > "We use these two limits to calculate a range of possible abundances" (Fractional abundances) [from (cite: merello_2013)]

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
- weighting robust: briggs, robust = 0.5  
  > "The generated maps considered a “briggs” weighting mode on the data (robust parameter = 0.5)." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: channel-by-channel emission mask during cleaning  
  > "required a careful channel-by-channel determination of the emission mask during the cleaning reduction process." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation and calibration details, outflow axis PA 102.5 deg, and prior analysis of 4 lines  
  > "The observations were performed with the Atacama Large Millimeter/submillimeter Array (ALMA) during Cycle 0, as described in ." (Observations) [from (cite: merello_2013_alma)]
- Ring model method for azimuthal PV  
  > "The method follows from (cite: lopez_2016)." (Ring model) [from (cite: lopez_2016)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (deferred to earlier paper)
- Line-free channels for continuum and continuum subtraction
- Cell size, image size, clean threshold
- Continuum flux and area used for abundances
- MOLLIE input grid details beyond appendix and collisional data
- Flux scale calibrator

## Analysis recipe

1. **Image cubes and moment maps / PV plots**: CASA imaging; moment 0 over -95.6 to -79.9 km/s; PV along and perpendicular to outflow axis, 11-pixel slit  
  > "integrated in the velocity range $-95.6$ to $-79.9$ km s$^{-1}$ (systemic velocity range)." (4.1 Moment 0 maps)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **SiO column density**: Optically thin, assumed Trot from APEX  
  > "Assuming a common $T_{\rm rot}$ for the SiO transitions and that they are optically thin, we calculate the column densities of the outflow wings." (Estimation of column density)
   - assumption: Tex 123 K blue, 138 K red from APEX  
  > "$123\pm15$ K (blue wing) and $138\pm29$ K (red wing)." (Estimation of column density)
   - fitting: _not stated_
   - validation: _not stated_
3. **SO2 rotational diagram**: Rotational diagrams of 7 SO2 lines, linear regression, in four averaged regions; also maps  
  > "In total, 7 lines were used in the blue and red wings." (SO2 analysis)
   - parameter: 20% error on ln(Eu/gu); 80% confidence intervals  
  > "we consider a conservative error of 20% for the $\ln(E_u/g_u)$ values." (SO2 analysis)
   - assumption: optically thin emission  
  > "assuming optically thin emission, we use the rotational diagram technique" (SO2 analysis)
   - fitting: linear regression, errors from covariance matrix  
  > "The 1$\sigma$ errors are calculated from the covariance matrix from the linear fit." (SO2 analysis)
   - validation: _not stated_
4. **Fractional abundances**: Equate dust mass from 862 um continuum with mass from molecular column density, Td 70 K and 400 K  
  > "Equating $M_{\rm cd}$ to $M_{\rm d}$" (Fractional abundances)
   - assumption: gas-to-dust 100, kappa 1.89 cm2/g, D=7.5 kpc, mean molecular weight 2.29  
  > "The following values will be used: $\kappa_{\nu}=1.89$ cm$^2$g$^{-1}$ (cite: ossenkopf_1994) and $D=7.5$ kpc." (Fractional abundances)
   - fitting: _not stated_
   - validation: Compared with other sources  
  > "We compare our fractional abundances results with similar sources studied in the literature." (Fractional abundances)
5. **Density from SO2 line ratios**: RADEX LVG grid; chi2 minimization on 4 SO2 line ratios in n(H2)-N(SO2) space  
  > "only 4 lines were used for this analysis." (RADEX)
   - software: RADEX
   - parameter: Tk=170 K, linewidth 16.5 km/s, Tbg 2.73 K, ratio error 20%  
  > "The kinetic temperature is fixed to $170$ K, which is the value constrained by SO$_2$." (RADEX)
   - fitting: chi2 contours at 0.5,1,2,3 sigma  
  > "The contours corresponding to 0.5, 1, 2, and 3$\sigma$ are shown" (RADEX)
   - validation: _not stated_
6. **Core density power law from continuum**: Radial profile from contours of equal flux; fit density power law with Td profile T∝r^-0.4, mean 70 K  
  > "We assume that the temperature profile follows a power-law with index $q=0.4$" (4.1.4)
   - assumption: optically thin; outer radius 2.1" (5 sigma contour)  
  > "As external radius of the clump, we use $2.1\ensuremath{''}$, which is the radius of the $5\sigma$ contour level in the 862 $\mu$m emission." (4.1.4)
   - fitting: power-law fit  
  > "a direct fit to the observed flux radial profile with a power-law gives an index of $m=1.0\pm0.2$." (4.1.4 Density radial gradient, dust continuum observations)
   - validation: _not stated_
7. **SiO shock parameters**: Compare APEX SiO(7-6)/(8-7) ratio with Gusdorf 2008 model grid  
  > "The (J$=7-6$)/(J$=8-7$) line ratio from the APEX data is $0.86 \pm 0.02$ (red wing) and $0.89 \pm 0.03$ (blue wing)." (4.1.5)
   - fitting: _not stated_
   - validation: _not stated_
8. **Radial and azimuthal PV plots and ring model**: kshell radial PV; ellipse-based azimuthal PV; fit 7-parameter 3D ring by minimizing distance; chi2 test  
  > "this function is minimized for the best fit 7 parameters: $X_0,Y_0,\alpha,\beta,R,V_0$ and $V$." (Ring model)
   - software: KARMA
   - assumption: constant expansion velocity ring  
  > "Consider a ring in the plane XY of the sky expanding in the outwards direction at a constant velocity." (Ring model)
   - fitting: distance minimization in (X,Y,Vz)  
  > "A function calculating the sum of the distance in the 3D space ($X$,$Y$,$V_{Z}$) between the observed and modeled coordinates is defined." (4.2.2 Ring model for the SiO(J$=8-7$) azimuthal PV plot)
   - validation: reduced chi2 = 0.42  
  > "The resulting reduced-$\chi^2$ is $\chi_{\nu} = 0.42$" (Ring model)
9. **3D radiative transfer model of SiO(8-7)**: MOLLIE model of conical outflow plus expanding shell, passed through CASA simobserve/simanalyze, compared qualitatively  
  > "simobserve, to simulate a set of measured visibilities with the compact configuration of the ALMA array; and *simanalyze*" (Radiative transfer model)
   - software: MOLLIE, CASA
   - parameter: X_SiO ~1e-8 (outflow), 1e-11 (ambient); core 70 K, outflow edge 150 K  
  > "We will use the value estimated in Section [4.1.2](#sec:abundances), $X_{\rm SiO} \sim 10^{-8}$." (Appendix B)
   - fitting: _not stated_
   - validation: qualitative comparison of integrated map and PV  
  > "In general terms, the model is able to qualitatively reproduce the observations." (Radiative transfer modeling)

## Software

- **CASA** : data processing, imaging, simobserve/simanalyze  
  > "The data were processed using the Common Astronomy Software Application (cite: mcmullin2007)." (Observations)
- **RADEX** : non-LTE SO2 line-ratio density constraints  
  > "The radiative transfer code *RADEX* (cite: vandertak_2007) is a non-LTE radiative code" (RADEX)
- **MOLLIE** : 3D radiative transfer of SiO(8-7)  
  > "This model is performed with the 3D radiative transfer code *MOLLIE*." (4.2.3)
- **KARMA** : kshell radial PV plots  
  > "using the function *kshell*, part of the KARMA package (cite: karma_paper)" (4.2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ambient core temperature (CH3CCH) | ~70 | ±7 K | K | 3 | we consider $T_K=70\pm7$ K, the temperature of the main emission region. |
| SO2 rotational temperature, red peak (red/blue wing) | 189/202 (red peak); 146/147 (blue peak) | ±47/±28; ±12/±17 | K | 3 | / red peak          / $7.8\pm0.1$/$15.1\pm0.1$  /                                 / $8\pm3$/$8\pm2$         / $189 \pm 47$/$202 \pm 28$ / |
| SiO column density blue/red peaks | 1.45e15 / 1.51e15 | not stated | cm^-2 | 2 | $1.45\times10^{15}$ cm$^{-2}$ and $1.51\times10^{15}$ cm$^{-2}$, respectively |
| SiO X abundance (Td=400 K) | 1.3e-8 | not stated | dimensionless | 4 | / SiO / $1.7(-9)$ / $1.3(-8)$ / |
| Outflow lobe mass from SiO | ~12 | not stated | Msun | 2 | we estimated the masses to be $\sim 12 M_{\odot}$, for each outflow wing. |
| Density of shocked gas (SO2, RADEX) | >~1e9 | not stated | cm^-3 | 5 | The measured density is quite high ($n \gtrsim 10^9$ cm$^{-3}$). |
| Density power-law index p (constant T / with T profile) | 0.8 / 0.6 | ±0.2 / ±0.1 | dimensionless | 6 | the fitted density model is a power-law with index $p=0.6\pm0.1$. |
| Shock velocity and pre-shock density | vs ~34 km/s, nH ~1e6 | not stated | km/s; cm^-3 | 7 | the shocks traced by the SiO observations have a speed of $v_s \sim 34$ km s$^{-1}$ and pre-shock densities of $n_H \sim 10^6$ cm$^{-3}$. |
| Ring model expansion velocity | 21 | not stated | km/s | 8 | / Expansion velocity $V$ / 21 km s$^{-1}$ / |
| Ring model radius | 1.2 | not stated | arcsec | 8 | / Radius $R$ / $1.2\ensuremath{''}$ / |
| Ring inclination alpha | -8 | not stated | deg | 8 | / Line of sight angle $\alpha$ / -8$^{\circ}$ / |

## Qualitative findings

- Lines split into wide (outflow/shocked) and narrow (ambient core) groups; HC3N v7=1 explains the secondary H13CO+ peak so the molecular bullet is discarded.  
  > "so the presence of a molecular bullet can be discarded" (Observations)

## Claim tuples

- H: Do SiO and SO2 trace dense hot shocked outflow gas? | E: Rotational diagram and RADEX analyses | R: SO2 T~150-200 K, n~1e9 cm-3 | F: SiO and SO2 trace very dense, hot shocked gas | **supported**
- H: Is the SiO ring an expanding cavity/shell nearly aligned with the line of sight? | E: Azimuthal PV ring fit | R: alpha -8 deg, V 21 km/s, chi2_nu 0.42 | F: Expanding shell blown by UCHII stellar wind | **supported**
- H: Can a MOLLIE outflow plus shell model reproduce SiO(8-7)? | E: 3D radiative transfer, simulated observation | R: wings and shell reproduced qualitatively; ring contrast not reproduced | F: Main features reproduced, clumpiness missing | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust-continuum mass chosen over virial mass for abundances  
  > "The latter method is used in this work, and the mass is calculated from the 862 $\mu$m continuum emission." (Fractional abundances)
- Alternative: Molecular bullet interpretation rejected in favor of HC3N v7=1 line  
  > "so the presence of a molecular bullet can be discarded" (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Model does not reproduce ring-to-cavity contrast or single-peaked ring spectra; shell inhomogeneity needed.  
  > "To improve the model, possible inhomogeneities present in the shell must be accounted for." (4.2.3)
- Caveat (inferred, ours): SiO Tex taken from APEX at lower resolution
- Caveat (inferred, ours): Strong dependence of abundances on assumed Td (70 vs 400 K)
- Caveat (inferred, ours): MOLLIE model hand-tuned without goodness-of-fit
- Caveat (inferred, ours): RADEX temperature fixed to rotational diagram value

## Reproducibility

- Data public (paper): ALMA project acknowledged; archive access implied  
  > "This Paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00524.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration details (in earlier paper)
- Missing: CASA version and clean parameters
- Missing: MOLLIE model setup files
- Missing: Line-free channels and continuum flux values
- Data volume (inferred): ~10-50 GB (Cycle 0, 4 SPWs x 3840 channels)
- Score (inferred): 3/5, Public data and many equations/parameters given, but calibration and imaging details are deferred to a prior paper and the radiative transfer model is hand-tuned.
- Rediscovery candidate: no, Calibration/imaging recipe incomplete and the modeling is qualitative.

## Links

- Method: (cite: lopez_2016) (Ring model and azimuthal PV method)
- Method: (cite: gusdorf_2008) (SiO shock model grid)
- Companion: (cite: merello_2013_alma) (Paper I: ALMA observations and first analysis)
- Companion: (cite: merello_2013) (APEX data and SED analysis of the source)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
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
  "facts": 92,
  "stated": 49,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
