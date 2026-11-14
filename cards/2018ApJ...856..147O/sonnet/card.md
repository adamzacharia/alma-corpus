# Gravitationally Unstable Condensations Revealed by ALMA in the TUKH122 Prestellar Core in the Orion A Cloud

`2018ApJ...856..147O` | The Astrophysical Journal 2018 | first author: Ohashi, Satoshi | arXiv: 1803.03340 | DOI: 10.3847/1538-4357/aab3d0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Does the TUKH122 prestellar core in Orion A fragment into gravitationally bound condensations, and how do N2H+ and CH3OH trace its structure and chemistry?  
  > "These results suggested that the TUKH122 core is on the verge of star formation and is one of the good targets to investigate the physical conditions and fragmentation process" (Introduction)
- Target **TUKH122**: coordinates not stated (condensations near 5:39:42 -7:29:43 to 5:39:44 -7:30:31 in Table 1)  
  > "The distance of Orion A cloud is derived to be 418 pc (cite: kim08)." (Introduction); z/distance 418 pc  
  > "The distance of Orion A cloud is derived to be 418 pc (cite: kim08)." (Introduction); distance from Kim et al. 2008 (VLBI)  
  > "The distance of Orion A cloud is derived to be 418 pc (cite: kim08)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.01025.S
- bands: Band 3 (3 mm)  
  > "The Band 3 receivers were used." (2 Observations)
- frequencies and spectral setup: Four spectral windows (two continuum, one N2H+, one CH3OH); velocity resolution ~0.098 km/s  
  > "The correlator was set to have four spectral windows (two windows for continuum, one for N$_2$H$^+$, and one for CH$_3$OH)." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m (38 antennas) plus ACA 7-m (10 antennas)  
  > "in the C36-2/3 configuration with a total of 38 antennas and with the 7-m Array of the Atacama Compact Array (cite: igu09)" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Combined: continuum ~5.7"x5.2", lines ~3.2"x2.9"  
  > "Synthesized beam size of continuum observation | $\sim5.0\ensuremath{''}\times4.6\ensuremath{''}$ | $\sim17\ensuremath{''}\times10\ensuremath{''}$ | $\sim5.7\ensuremath{''}\times5.2\ensuremath{''}$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Combined continuum rms ~40 uJy/beam; line rms ~6.5 mJy/beam  
  > "Sensitivity of continuum observation (rms) | $\sim43$ $\mu$Jy beam$^{-1}$ | $\sim87$ $\mu$Jy beam$^{-1}$ | $\sim40$ $\mu$Jy beam$^{-1}$" (Table 1)
- time on source: _not stated_
- observing dates: 12-m: 2016 March 10-12; ACA: 2016 May 28, Aug 27, Sep 1-7  
  > "TUKH122 was observed with the ALMA 12-m Array on 2016 March 10-12" (2 Observations)
- pi or archival as stated: _not stated_
- Line: N2H+ J=1-0 (F1=1-1, F=0-1 used) (93.171621 GHz (F1=1-1,F=0-1))
- Line: CH3OH 2_K-1_K (2_-1-1_-1 E, 2_0-1_0 A+, 2_0-1_0 E) (not stated)
- Other facility **Herschel (HGBS)**: 250, 350, 500 um maps for dust temperature, mass, column density and total-power feathering  
  > "To derive the dust temperature and mass of the ALMA-ACA observing region by using the *Hershcel* 250, 350, and 500 $\mu$m data" (Analysis of the Herschel and ALMA continuum data)
- Other facility **VLA**: NH3 and CCS maps from earlier work for comparison  
  > "Figure [3](#vla_nh3) shows the ACA 7-m 3mm dust continuum image with the VLA NH$_3$ integrated intensity contours." (Results)
- External data: Dust opacity model: 5.5 cm2/g at 350 um, 2.7 cm2/g at 500 um  
  > "we adopt a dust opacity of 5.5 cm$^2$ g$^{-1}$ at 350 $\mu$m and 2.7 cm$^2$ g$^{-1}$ at 500 $\mu$m modeled by (cite: orm07)" (Analysis of the Herschel and ALMA continuum data) [from (cite: orm07)]
- External data: VLA NH3 kinetic temperature T_kin=11 K and T_rot=10.6 K  
  > "consistent with the previous results of $T_{\rm kin}=11$ K obtained by NH$_3$ spectra (cite: oha16)" (Analysis of the Herschel and ALMA continuum data) [from (cite: oha16)]
- External data: VLA NH3 and CCS maps  
  > "(cite: tat14b) also observed TUKH122 core with the NH$_3$ and CCS molecules using VLA and found that the CCS emission surrounds the NH$_3$ core." (Molecular line emission) [from (cite: tat14b)]

## Processing

### Calibration

- pipeline or manual: Standard CASA reduction and calibration  
  > "The reduction and calibration of the data were done with CASA version 4.5.3 (cite: mcm07) in a standard manner." (2 Observations)
- casa version: CASA 4.5.3  
  > "The reduction and calibration of the data were done with CASA version 4.5.3 (cite: mcm07) in a standard manner." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120, J0510+1800, J0522-3627, and Uranus  
  > "Flux calibration was performed using J0423-0120, J0510+1800, J0522-3627, and Uranus." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "All images were reconstructed with the CASA task CLEAN using natural weighting." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "All images were reconstructed with the CASA task CLEAN using natural weighting." (2 Observations)
- uv taper: 50 klambda for lines, 20 klambda for continuum  
  > "we also used uv tapering (50 k$\lambda$ for the molecular lines and 20 k$\lambda$ for continuum) for CLEAN." (2 Observations)
- cell size: 0.5 arcsec  
  > "The pixel size was set to 0$\ensuremath{''}$5." (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Continuum images in Fig. 2 not corrected; fluxes in Table 1 corrected  
  > "These images are not corrected by the primary beam pattern to keep the same noise level within the images." (Results)
- array combination: 12-m and ACA combined in the uv plane; Herschel 250 um feathered with CASA feather  
  > "we combine the ALMA 12-m and ACA in the uv plane." (2 Observations)
- smoothing: _not stated_
- final beam: Combined continuum 5.7"x5.2" (PA=-66 deg)  
  > "the beamsize is $5.7\ensuremath{''}\times5.2\ensuremath{''}$ (PA$=-66^\circ$)" (Results)
- final rms: 40 uJy/beam (continuum)  
  > "The 1$\sigma$ noise level is 40 $\mu$Jy beam$^{-1}$" (Results)

### Inherited from earlier work

- N2H+ hyperfine fitting with uniform Tex, IDL code  
  > "assuming a uniform excitation temperature in the same way as (cite: oha14; oha16) using IDL fitting code" (Analysis of N2H+ spectra) [from (cite: oha14; oha16)]
- CH3OH rotation diagram procedure optimized for cold gas  
  > "We follow the procedure described in (cite: san13), which is optimized for cold gas." (Analysis of CH3OH spectra) [from (cite: san13)]
- Core/condensation nomenclature  
  > "we will follow the nomenclature of (cite: oha16c) and refer to cores as an entity of $0.01-0.1$ pc." (Introduction) [from (cite: oha16c)]
- N2H+ column density formula  
  > "Then, the column density can be calculated by following (cite: san12; man15)." (Analysis of N2H+ spectra) [from (cite: san12; man15)]

### Not stated but needed to reproduce (our reading)

- Herschel map version and processing (HGBS products) and how flux was measured
- Line-free channels and continuum subtraction method
- CLEAN threshold, masks, iterations, mosaic/feather details
- Relative weighting of 12-m and ACA data in combination
- How the reference dendrogram parameters were applied (software package, min_delta)
- Uncertainty calculations for masses
- Details of Herschel-ALMA feathering and scaling
- Which spectral window frequencies exactly

## Analysis recipe

1. **Herschel dust temperature and mass**: Compute mass and Td from Herschel 250/350/500 um fluxes with opacity model  
  > "By calculating the flux density within the ALMA observed field, the dust temperature of TUKH122 is derived to be 12 K" (Analysis of the Herschel and ALMA continuum data)
   - assumption: Gas-to-dust ratio 100; kappa 5.5 and 2.7 cm2/g at 350/500 um (Ormel et al.)  
  > "$f_d$ is the gas to dust mass ratio (assumed to be 100)" (Analysis of the Herschel and ALMA continuum data)
   - fitting: _not stated_
   - validation: Compared with T_kin=11 K from NH3  
  > "consistent with the previous results of $T_{\rm kin}=11$ K obtained by NH$_3$ spectra (cite: oha16)" (Analysis of the Herschel and ALMA continuum data)
2. **Filament column density profiles**: Average perpendicular profile (15" width) towards PA=236.3 deg; fit Plummer-like profile  
  > "the profile is calculated by averaging the flux densities within 15$\ensuremath{''}$ width at each distance from the peak position" (Analysis of the Herschel and ALMA continuum data)
   - parameter: Filament PA=146.3 deg from 2D Gaussian fit on Herschel  
  > "P.A. =146.3$ degrees derived by 2D gaussian fitting on the *Herschel* image" (Analysis of the Herschel and ALMA continuum data)
   - assumption: Mean molecular weight 2.33  
  > "We derive the column density assuming the mean molecular weight of 2.33." (Analysis of the Herschel and ALMA continuum data)
   - fitting: Plummer-like profile with slope p; Herschel p=1.6, ALMA-ACA p=4.0; priors/likelihood not stated  
  > "the red line shows the power law of $p=1.6$, while the black solid line shows the power law of $p=4.0$" (Analysis of the Herschel and ALMA continuum data)
   - validation: _not stated_
3. **Identify condensations and derive masses**: Dendrogram on combined continuum image; leaves = condensations; masses at Td=12 K  
  > "We define “leaves” as “condensations” in this paper because the leaf is the smallest structure." (The 3 mm dust continuum emission seen by ALMA)
   - software: astrodendro (not named)
   - parameter: Threshold 3 sigma, 1 sigma steps, min pixels 3 x theta_beam, must be >3 sigma in 12-m data  
  > "We adopt a threshold of 3$\sigma$ and 1$\sigma$ interval steps." (The 3 mm dust continuum emission seen by ALMA)
   - assumption: kappa=0.0755 cm2/g at 3 mm, beta=2, Td=12 K  
  > "We adopt a dust opacity of 0.0755 cm$^2$ g$^{-1}$, assuming a dust emissivity index of $\beta=2$ (cite: orm07)." (The 3 mm dust continuum emission seen by ALMA)
   - fitting: _not stated_
   - validation: Feathered with Herschel 250 um; masses change ~10% except MM5 (~60%)  
  > "The MM1 to MM4 condensations increase in mass only $\sim10$% but the MM5 increases $\sim60$% in mass" (The 3 mm dust continuum emission seen by ALMA)
4. **Virial analysis**: Uniform-density virial mass from CH3OH 2_0-1_0 A+ Gaussian linewidth  
  > "The linewidth is derived by gaussian fitting of the CH$_3$OH ($J_K=2_0-1_0$ $A^{+}$) emission because this line is optically thin." (The 3 mm dust continuum emission seen by ALMA)
   - parameter: M_vir = 210 r Dv^2 Msun (r in pc, Dv in km/s)  
  > "M_{\rm vir}=210 \times \left( \frac{r}{ \mathrm{pc}} \right) \times \left( \frac{\Delta v}{ \mathrm{km \, s^{-1}}} \right)^2 M_\odot" (The 3 mm dust continuum emission seen by ALMA)
   - assumption: Uniform density  
  > "Assuming a uniform density structure, the virial mass can be estimated as" (The 3 mm dust continuum emission seen by ALMA)
   - fitting: _not stated_
   - validation: _not stated_
5. **N2H+ and CH3OH line analysis**: Hyperfine fit of weakest N2H+ component for tau, VLSR, dv; CH3OH rotation diagram on averaged spectra  
  > "Therefore, we only use the weakest and the most optically thin component ($J=1-0$, $F_1=1-1$, $F=0-1$) to derive physical parameters." (Analysis of N2H+ spectra)
   - software: IDL fitting code
   - parameter: Fitting for pixels above 5 sigma; Tex from peak intensity + 2.7 K CMB  
  > "The fitting is performed for the pixels above 5$\sigma$." (Analysis of N2H+ spectra)
   - assumption: LTE, optically thin CH3OH; filling factor unity  
  > "Assuming LTE and optically thin conditions, we can estimate the column density" (Analysis of CH3OH spectra)
   - fitting: Gaussian fits; rotation diagram  
  > "we can estimate the column density ($N_{\rm CH_3OH}$) and rotation temperature ($T_{\rm rot}$) using the rotation diagram technique" (Analysis of CH$_3$OH spectra)
   - validation: Trot consistent with NH3 value of 10.6 K  
  > "This rotation temperature is consistent with $T_{\rm rot}=10.6$ K derived by using the NH$_3$ ($J,K=1,1$) and ($J,K=2,2$) lines (cite: oha16)." (Analysis of CH3OH spectra)
6. **Jeans fragmentation and timescales**: Compare condensation separation (sinusoidal fit, 0.035 pc) with Jeans lengths  
  > "The green line represents a sinusoidal column-density variation with an interval of 0.035 pc to visually match the observed variations." (Density profile)
   - parameter: c_s=0.2 km/s at 12 K; central density 5.5e5 cm-3  
  > "we derive the central density, $\rho_{c}\sim5.5\times10^5$ cm$^{-3}$ assuming the numerical factor of $A=\pi/2$." (Density profile)
   - assumption: Infinite uniform medium (Jeans 1902) preferred over cylindrical case  
  > "The thermal Jeans instability with the assumption of an infinite and a uniform density, the equation ([\[jeans\]](#jeans)), would be better explained to form the condensations." (Density profile)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: Reduction, calibration, CLEAN imaging and feather  
  > "The reduction and calibration of the data were done with CASA version 4.5.3 (cite: mcm07) in a standard manner." (2 Observations)
- **feather (CASA)** : Combine ALMA+ACA with Herschel 250 um  
  > "we combine our ALMA and ACA data with the *Herschel* 250 $\mu$m data using *feather* in CASA." (The 3 mm dust continuum emission seen by ALMA)
- **IDL** : N2H+ hyperfine fitting  
  > "using IDL fitting code" (Analysis of N2H+ spectra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Herschel dust temperature | 12 | not stated | K | 1 | the dust temperature of TUKH122 is derived to be 12 K |
| Herschel mass of ALMA field | ~29 | not stated | Msun | 1 | The mass is also derived to be $\sim29$ $M_{\odot}$. |
| Total mass recovered by ALMA-ACA | 8.4 (2.5 for 12-m only) | not stated | Msun | 3 | The total mass of TUKH122 is derived to be 8.4 $M_\odot$ (2.5 $M_\odot$ for ALMA 12-m data) |
| Number of condensations | 6 | not stated | dimensionless | 3 | identify 6 condensations with a mass range of $0.1-0.4$ $M_\odot$ |
| Condensation mass range | 0.1-0.4 | not stated | Msun | 3 | identify 6 condensations with a mass range of $0.1-0.4$ $M_\odot$ and a radius of $\lesssim0.01$ pc |
| Condensation separation | ~0.035 | not stated | pc | 6 | The separation of these condensations is $\sim0.035$ pc |
| Jeans lengths | 0.031 and 0.099 | not stated | pc | 6 | The Jeans length is derived to be $\sim0.031$ pc and $\sim0.099$ pc, respectively |
| Density from lambda_Jeans=0.035 pc | 4.4e5 | not stated | cm-3 | 6 | the density is derived to be $n({\rm H_2})\sim4.4\times10^{5}$ cm$^{-3}$ |
| CH3OH column density | 1.1e13 | 0.1e13 | cm-2 | 5 | $N_{\rm CH_3OH}=(1.1\pm0.1)\times10^{13}$ cm$^{-2}$ and $T_{\rm rot}=10.8\pm0.4$ K |
| CH3OH rotation temperature | 10.8 | 0.4 | K | 5 | $N_{\rm CH_3OH}=(1.1\pm0.1)\times10^{13}$ cm$^{-2}$ and $T_{\rm rot}=10.8\pm0.4$ K |
| N2H+ abundance at dust peak | 3.4e-10 | 0.4e-10 | dimensionless | 5 | the N$_2$H$^+$ abundance is derived to be $X({\rm N_2H^+})=(3.4\pm0.4)\times10^{-10}$ |
| Free-fall time at 1e6 cm-3 | 4e4 | not stated | yr | 6 | the free fall time at a density of $10^6$ cm$^{-3}$ will be $4\times10^4$ yr |

## Qualitative findings

- CH3OH emission forms a shell around the continuum and N2H+ emission, consistent with non-thermal desorption.  
  > "the CH$_3$OH emission is weak at the central part of the TUKH122 core, resembling a shell-like structure that surrounds the continuum and N$_2$H$^+$ emission." (The molecular line emission of N2H+ and CH3OH)
- N2H+ is optically thick even in the weakest hyperfine component and shows self-absorption toward MM5.  
  > "Even though N$_2$H$^+$ has been used as an optically thin dense gas tracer, we show that this molecule becomes optically thick in this core." (Conclusions)

## Claim tuples

- H: Does the prestellar core contain gravitationally bound condensations? | E: Dendrogram on ALMA+ACA continuum and virial analysis with CH3OH linewidths | R: 6 condensations of 0.1-0.4 Msun with masses well above virial masses | F: Condensations are bound and may collapse unless supported by magnetic fields | **supported**
- H: Is the fragmentation set by thermal Jeans instability? | E: Compare ~0.035 pc separation with Jeans length | R: Jeans length 0.031 pc at central density; 0.035 pc corresponds to 4.4e5 cm-3 | F: Fragmentation by thermal Jeans instability still occurs in the prestellar core | **supported**
- H: Is the dust peak condensation beginning to collapse? | E: N2H+ optical depth and linewidth maps | R: N2H+ partially depleted and broader linewidth toward MM4 | F: MM4 may be beginning to collapse | **partially**

## Reasoning

- Why this data: TUKH122 has the highest N2H+/CCS ratio among starless cores in Orion A, so it is likely closest to star formation  
  > "(cite: tat14a) have found a dense core (TUKH122) having the largest value of $N$(N$_2$H$^+$)/$N$(CCS) among the starless dense cores in the Orion A cloud." (Introduction)
- Why this method: _not stated_
- Alternative: Cylindrical Jeans length (0.099 pc) rejected in favour of uniform infinite case.  
  > "The thermal Jeans instability with the assumption of an infinite and a uniform density, the equation ([\[jeans\]](#jeans)), would be better explained to form the condensations." (Density profile)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux: ALMA-ACA recovers only 8.4 of ~29 Msun, so density profile of ALMA-ACA cannot be discussed.  
  > "We cannot discuss the density profile or the power law of the ALMA-ACA observations." (Analysis of the Herschel and ALMA continuum data)
- Limitation (authors): Several condensations not well resolved; radius close to beam size.  
  > "These results indicate that these three condensations (MM1,2 and 6) are not well resolved with our observations." (The 3 mm dust continuum emission seen by ALMA)
- Caveat (inferred, ours): Virial analysis neglects magnetic fields, external pressure and uncertainty in sizes near beam scale
- Caveat (inferred, ours): Sinusoidal fit of separation was done by eye
- Caveat (inferred, ours): Single temperature 12 K for all condensations
- Caveat (inferred, ours): Dust opacity and optical-depth issues of N2H+ make abundance only rough

## Reproducibility

- Data public (paper): ALMA project ID given; Herschel from HGBS  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01025.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Herschel data processing
- Missing: Dendrogram implementation details
- Missing: Exact weighting for ALMA+ACA combination
- Data volume (inferred): ~50-100 GB raw for 12-m+ACA Band 3 mosaic
- Score (inferred): 3/5, Public data and clear analysis outline, but imaging/combination parameters and Herschel processing are sparse.
- Rediscovery candidate: no, Recipe lacks key imaging and combination parameters, and relies on Herschel products.

## Links

- Method: Rosolowsky et al. 2008 (cite: ros08) (Dendrogram method)
- Method: Sanhueza et al. 2013 (cite: san13) (CH3OH rotation diagram for cold gas)
- Companion: Tatematsu et al. 2014b (cite: tat14b) (VLA NH3 and CCS of TUKH122)
- Companion: Ohashi et al. 2016b (cite: oha16) (NH3 single-pointing observations of TUKH122)
- Related: Herschel Gould Belt survey

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 62,
  "rate": 0.697
 },
 "evidence_ok": true
}
```
