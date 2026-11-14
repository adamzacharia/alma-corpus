# ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Luminosity Functions and the Evolution of the Cosmic Density of Molecular Gas

`2016ApJ...833...69D` | The Astrophysical Journal 2016 | first author: Decarli, Roberto | arXiv: 1607.06770 | DOI: 10.3847/1538-4357/833/1/69

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, cosmology
- Question: What are the blind CO luminosity functions and the evolution of the cosmic molecular gas density rho(H2) up to z~4.5, from ALMA band 3 and 6 scans of the UDF?  
  > "place blind constraints on the CO luminosity function and the evolution of the cosmic molecular gas density as a function of redshift up to $z\sim 4.5$" (abstract)
- Target **Hubble Ultra Deep Field (ASPECS field)**: coordinates RA = 03:32:37.900, Dec = –27:46:25.00 (J2000.0)  
  > "centered at RA = 03:32:37.900, Dec = –27:46:25.00 (J2000.0)" (2 Observations); z/distance blind CO detections at z~0.5-4.5  
  > "centered at RA = 03:32:37.900, Dec = –27:46:25.00 (J2000.0)" (2 Observations); distance from line identification with optical/near-IR spectroscopic, grism or photometric redshifts  
  > "centered at RA = 03:32:37.900, Dec = –27:46:25.00 (J2000.0)" (2 Observations)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (3mm) and Band 6 (1mm)  
  > "two frequency scans at 3mm (band 3) and 1mm (band 6) obtained with ALMA in the UDF" (2 Observations)
- frequencies and spectral setup: 3mm: 84-115 GHz, single pointing; 1mm: 212-272 GHz, 7-point mosaic  
  > "The 3mm scan covers the 84-115 GHz range with a single spatial pointing." (2 Observations); "The 1mm scan encompasses the frequency window 212-272 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~3.5'' x 2.0'' at 3mm, ~1.5'' x 1.0'' at 1mm  
  > "The synthesized beams are $\sim 3.5''\times 2.0''$ at 3mm and $\sim 1.5''\times 1.0''$ at 1mm." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.15 mJy/beam per 20 MHz channel (3mm); ~0.5 mJy/beam per 30 MHz channel (1mm)  
  > "The typical RMS noise is 0.15 mJy beam$^{-1}$ per 20 MHz channel." (2 Observations); "The typical depth of the data is $\sim 0.5$ mJy beam$^{-1}$ per 30 MHz channel." (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 through 6-5 (CO(2-1) to CO(4-3) used in luminosity functions) (CO(2-1) 230.538 GHz; CO(3-2) 345.796 GHz; CO(4-3) 461.041 GHz)
- Line: [C II] 2P3/2-2P1/2 (not stated)
- Other facility **HST / optical-NIR spectroscopy and photometry**: Redshifts (slit spectroscopy, 3D-HST grism, photometric) for line identification and stacking  
  > "Optical spectroscopy (cite: lefevre05; coe06; skelton14; morris15) is considered secure" (3.1.1 Blind detections)
- External data: Blind CO line catalog (10 3mm and 11 1mm candidates) with line fluxes, widths, frequencies  
  > "We first concentrated on the “blind” CO detections presented in Paper I (Tab. 2)" (3 Analysis) [from Paper I (cite: walter16)]
- External data: CO excitation ratios r_J1 = 0.76, 0.42, 0.23 for J=2,3,5  
  > "we adopt $r_{\rm J1}$=$0.76\pm0.09$, $0.42\pm0.07$, $0.23\pm0.04$ for J=2,3,5" (3.2 CO luminosity functions) [from (cite: daddi15)]
- External data: 1mm continuum source flux densities used for dust-based ISM masses  
  > "for each 1mm continuum source (see the companion paper (cite: aravena16a)), the ISM mass is computed" (3.4 Estimates from dust continuum emission) [from (cite: aravena16a)]
- Simulation/model as data: Semi-analytical model and empirical CO luminosity function predictions (Lagos+12, Popping+16, Vallini+16) compared with the measurements  
  > "we include the predictions based on semi-analytical models by (cite: lagos12) and (cite: popping16) and on empirical IR luminosity function of *Herschel* sources by (cite: vallini16)" (3.2 CO luminosity functions)

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

- Observations, data reduction and imaging are described in Paper I  
  > "Details on the observations and data reduction are presented in Paper I, but the relevant information is briefly summarized here." (2 Observations) [from Paper I (cite: walter16)]
- Fidelity estimate from negative peaks  
  > "as described in Sec. 3.1.1 of Paper I" (3.1.1 Blind detections) [from Paper I (cite: walter16)]
- Dust-based ISM mass recipe  
  > "These are derived following (cite: scoville14)." (3.4 Estimates from dust continuum emission) [from (cite: scoville14)]
- alpha_CO = 3.6  
  > "Following (cite: daddi10a), we thus assume $\alpha_{\rm CO} = 3.6$" (3.3 Cosmic H2 mass density) [from (cite: daddi10a)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging settings (all in Paper I)
- ALMA project codes and observing dates
- Exact floating-average channel widths and S/N thresholds of the blind search
- Redshift-bin volume derivation details
- Luminosity bin edges and mapping to the plotted points
- Gamma_RJ values used for the dust masses
- Complete catalog of mock line parameters for completeness

## Analysis recipe

1. **Blind line search and line identification**: Floating average of channels in 50-300 km/s bins, S/N peak selection; identification via multiple lines, absence of counterparts, and optical/NIR redshifts  
  > "we perform a floating average of consecutive frequency channels in bins of $\sim$50–300 km s$^{-1}$ in the imaged cubes." (3.1.1 Blind detections)
   - software: findclumps.cl
   - parameter: 21 line candidates (10 at 3mm, 11 at 1mm); S/N>5  
  > "The final catalogue consists of 10 line candidates from the 3mm cube, and 11 from the 1mm cube." (3.1.1 Blind detections)
   - fitting: Gaussian fit to candidate spectra for flux, width, frequency  
  > "We use a Gaussian fit of the candidate spectra to estimate the line flux, width, and frequency" (3.1.1 Blind detections)
   - validation: Bootstrap of 1000 redshift draws proportional to comoving volume over possible line identifications  
  > "We then run 1000 extractions of the redshift values picked from their probability distributions" (3.1.1 Blind detections)
2. **Fidelity and completeness**: Fidelity from negative peaks; completeness from 2500 injected mock point-source lines  
  > "This is obtained by creating a sample of 2500 mock lines (as point sources)" (3.1.1 Blind detections)
   - parameter: fidelity = (Npos-Nneg)/Npos  
  > "the fidelity at a given S/N is defined as $(N_{\rm pos}-N_{\rm neg})/N_{\rm pos}$" (3.2 CO luminosity functions)
   - fitting: _not stated_
   - validation: Flux boosting argued negligible due to S/N>5  
  > "make the impact of flux boosting negligible in our analysis" (3.1.1 Blind detections)
3. **Line luminosity and CO luminosity functions**: L' from Solomon+97 formula; Phi = (1/V) sum Fid/C in 1-dex bins; Gehrels Poisson errors  
  > "The uncertainties on $\Phi(\log L_i)$ are set by the Poissonian errors on $N_i$, according to (cite: gehrels86)" (3.2 CO luminosity functions)
   - parameter: Planck15-like cosmology H0=70, Om=0.3, OL=0.7  
  > "$H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m}=0.3$ and $\Omega_{\Lambda}=0.7$" (1 Introduction)
   - fitting: _not stated_
   - validation: Comparison with Lagos+12, Popping+16, Vallini+16 predictions and HDF-N  
  > "we include the predictions based on semi-analytical models by (cite: lagos12) and (cite: popping16) and on empirical IR luminosity function of *Herschel* sources by (cite: vallini16), as well as the constraints obtained by the earlier study of the HDF–N" (3.2 CO luminosity functions)
4. **Convert to CO(1-0) luminosity functions**: log L'(1-0) = log L'(J) - log r_J1 with Daddi+15 template  
  > "$$\log L_{\rm CO(1-0)}'=\log L_{\rm CO(J-[J-1])}'-\log r_{\rm J1}$$" (3.2 CO luminosity functions)
   - parameter: r41 = 0.31±0.06 by interpolation (20% uncertainty)  
  > "yielding $r_{41}$=$0.31\pm0.06$, where we conservatively assume a 20% uncertainty" (3.2 CO luminosity functions)
   - fitting: _not stated_
   - validation: Robustness checked with the CO(2-1) bin where excitation corrections are small  
  > "This result is robust against CO excitation uncertainties: For example, it is already apparent in the $\langle z\rangle =1.43$ bin, where we covered the CO(2-1) line in our 3mm cube" (3.2 CO luminosity functions)
5. **Cosmic H2 density**: M_H2 = alpha_CO L'(1-0); rho(H2) = (1/V) sum M P / C  
  > "$$M_{\rm H2}=\alpha_{\rm CO} \, L_{\rm CO(1-0)}'$$" (3.3 Cosmic H2 mass density)
   - assumption: alpha_CO = 3.6 Msun (K km/s pc^2)^-1 for all sources  
  > "we thus assume $\alpha_{\rm CO} = 3.6$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for all the sources in our sample" (3.3 Cosmic H2 mass density)
   - fitting: _not stated_
   - validation: Not extrapolated beyond the observed luminosity range  
  > "we do not attempt to correct for undetected galaxies in lower luminosity bins given the large uncertainties in the individual luminosity bins and the unknown intrinsic shape of the CO luminosity function." (3.3 Cosmic H$_2$ mass density)
6. **Dust-based rho(ISM) comparison**: Scoville+14 recipe on 1mm continuum sources detected to S/N=3, summed per redshift bin  
  > "We include here all the sources detected down to S/N=3 in the 1mm continuum." (3.4 Estimates from dust continuum emission)
   - parameter: nu = 242 GHz, Gamma0 = 0.71  
  > "$\Gamma_0=0.71$ is the tuning value obtained at low-$z$" (3.4 Estimates from dust continuum emission)
   - assumption: Dust temperature 25 K  
  > "The dust temperature (implicit in the definition of $\Gamma_{\rm RJ}$), is set to 25 K." (3.4 Estimates from dust continuum emission)
   - fitting: _not stated_
   - validation: Compared with CO-based estimates  
  > "we compare the constraints on $\rho$(H$_2$) inferred from CO with those on $\rho$(ISM) derived from the dust continuum in our observations of the UDF." (3.4 Estimates from dust continuum emission)

## Software

- **findclumps.cl** : Blind search of line candidates  
  > "The code for the blind search of line candidates is publicly available at http://www.mpia.de/homes/decarli/ASPECS/findclumps.cl." (footnote 1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fraction of CO luminosity recovered (lower bound) | >50% | not stated | percent | 5 | we recover a large part ($>$50%) of the total CO luminosity per comoving volume |
| Evolution of cosmic H2 density z~2 vs z=0 | 3-10 times larger | large | dimensionless | 5 | The global amount of molecular gas stored in galaxies at the peak epoch of galaxy assembly is 3–10 times larger than at the present day. |
| Completeness 50% limit at 3mm (J>1) | (4-6)e9 | not stated | K km/s pc^2 | 2 | Our analysis is 50% complete down to line luminosities of $(4-6) \times 10^9$ K km s$^{-1}$ pc$^2$ at 3mm for any J$>$1 |
| Cosmic variance fractional uncertainty at z~2.5 | ~20% (~60% with Poisson) | not stated | percent | 0 | the fractional uncertainty in the number counts due to cosmic variance is $\sim 20$% ($\sim 60$% if we include Poissonian fluctuations) |

## Qualitative findings

- CO luminosity function knee shifts to higher luminosities from z~0 to z~2, with excess of bright sources relative to models at z>1, while 1mm shows low CO excitation  
  > "Our measurements reveal that the knee of the CO(1-0) luminosity function shifts toward higher luminosities as we move from $z\approx 0$" (3.2 CO luminosity functions)
- Dust-based densities are consistent with CO-based at z<2 but lower at z>2  
  > "discrepancies are found at $z>2$, where $\rho$(H$_2$) estimates based on CO tend to be larger than $\rho$(ISM) estimates based on dust" (3.4 Estimates from dust continuum emission)

## Claim tuples

- H: Does the CO luminosity function evolve from z~0 to z~2? | E: Blind CO LFs in redshift bins, converted to CO(1-0) | R: Knee shifts to higher luminosities; excess of bright sources at z>1 vs models | F: More CO-luminous, gas-rich galaxies at z~2 than models predict | **supported**
- H: How does rho(H2) evolve with redshift? | E: Sum of completeness- and fidelity-corrected H2 masses per bin | R: 3-10x higher at z~2 than z=0, possible decline at z>3 | F: Cosmic gas density follows the SFR density evolution partly | **partially**
- H: Do dust-based and CO-based gas densities agree? | E: Scoville+14 recipe on 1mm continuum sources | R: Roughly consistent at z<2, dust lower at z>2 | F: Possible causes are dust temperature/opacity or alpha_CO | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Blank-field scan avoids pre-selection bias and gives a well-defined volume  
  > "By focusing on a blank field, we avoid the biases due to pre-selection of sources." (1 Introduction)
- Alternative: Stack of 36 spectroscopic-redshift galaxies excluded due to only ~2-sigma detections  
  > "we opt not to include them in the remainder of the analysis" (3.1.2 CO line stack)
- How they decided it was enough: _not stated_
- Limitation (authors): rho(H2) is a lower limit as faint end not recovered; Poisson errors and cosmic variance large  
  > "our constraints on $\rho$(H$_2$) are actually lower limits, in the sense that they do not recover the full extent of the luminosity function" (4 Summary and Discussion)
- Caveat (inferred, ours): Single small field with strong cosmic variance
- Caveat (inferred, ours): Ambiguous line identifications for 11 of 21 lines handled statistically
- Caveat (inferred, ours): Fixed alpha_CO and excitation template drive rho(H2)
- Caveat (inferred, ours): Few sources per bin

## Reproducibility

- Data public (paper): Blind search code public; data in Paper I  
  > "The code for the blind search of line candidates is publicly available" (footnote 1)
- Products in archive: _not stated_
- Code: findclumps.cl at mpia.de/homes/decarli/ASPECS  
  > "The code for the blind search of line candidates is publicly available at http://www.mpia.de/homes/decarli/ASPECS/findclumps.cl." (footnote 1)
- Missing: Cubes and calibration details (Paper I)
- Missing: Project codes
- Missing: Redshift catalogs compilation
- Data volume (inferred): Large: two spectral-scan cubes (~tens of GB raw each)
- Score (inferred): 3/5, Analysis equations are clear, but data reduction and the line catalog depend on Paper I and project codes are not stated.
- Rediscovery candidate: no, Depends on Paper I for imaging and the line catalog, and project codes are not printed.

## Links

- Method: Paper I (cite: walter16) (Data reduction, blind search, fidelity)
- Method: (cite: scoville14) (Dust-based ISM mass recipe)
- Companion: (cite: aravena16a) (1mm continuum sources)
- Companion: (cite: decarli16) (Detailed analysis of CO-bright sources)
- Related: ASPECS
- Related: Hubble Ultra Deep Field
- Related: 3D-HST

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00146.S",
  "2013.1.00718.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 45,
  "rate": 0.542
 },
 "evidence_ok": true
}
```
