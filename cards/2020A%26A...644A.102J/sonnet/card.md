# Rotational spectroscopic study of S-methyl thioformate. A global laboratory analysis of ground and excited torsional states up to 660 GHz

`2020A&A...644A.102J` | Astronomy and Astrophysics 2020 | first author: Jabri, A. | arXiv: - | DOI: 10.1051/0004-6361/202038200

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Can the ground and torsionally excited rotational spectrum of CH3SC(O)H be measured and modeled up to 660 GHz, and can the molecule then be detected in Orion KL and Sgr B2?  
  > "This work aims to experimentally study and theoretically analyze the ground and first torsional excited states for CH 3 SC(O)H in a large spectral range for astrophysical use." (abstract)
- Target **Orion KL (MF peak and ET peak)**: coordinates MF peak: RA 05h35m14.1s, Dec -05d22m36.8s (J2000); ET peak: RA 05h35m14.4s, Dec -05d22m34.74s  
  > "α = 05 [h] 35 [m] 14.1 [s] α = 05 [h] 35 [m] 14.4 [s]" (Table 3); z/distance _not stated_; distance from _not stated_
- Target **Sgr B2 (IRAM 30m)**: coordinates RA 17h47m20.0s, Dec -28d22m19.0s (J2000)  
  > "α = 17 [h] 47 [m] 20.0 [s]" (Table 3); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: ALMA SV data of Orion KL, 213.7-246.6 GHz  
  > "We used the ALMA science verification (SV) data of Orion KL between 213.7 and 246.6 GHz" (5. Search for methyl thioformate in space)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthetic beam ~2.0 x 1.5 arcsec  
  > "∼2.0 × 1.5 ∼2.0 × 1.5" (Table 3)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **IRAM 30m**: 3 mm survey of Sgr B2 (80-115.5 GHz) from Belloche et al. (2013)  
  > "3 mm survey of Sgr B2 provided by Belloche et al. (2013)." (5. Search for methyl thioformate in space)
- Other facility **Lille solid-state spectrometer**: Laboratory spectrum 150-660 GHz  
  > "The measurements in the frequency range under investigation (150−660 GHz) were performed using the Lille spectrometer" (2.2. Spectra measurements)
- External data: Methyl formate physical parameters in Orion KL (vLSR, FWHM, size, Trot) used for the CH3SC(O)H upper limit  
  > "Physical parameters derived for the main spectral component of HCOOCH 3 by Tercero et al. (2018)." (Table 3) [from Tercero et al. 2018]
- External data: Methyl formate parameters for two components in Sgr B2  
  > "Physical parameters derived for two spectral components of HCOOCH 3 by Belloche et al. (2013)." (Table 3) [from Belloche et al. (2013)]
- External data: Earlier microwave lines (54) and dipole moments from Stark measurements  
  > "These 54 lines were measured by Jones et al. (1976) and Caminati et al. (1981) in the microwave domain between 10 and 41 GHz" (Table 1) [from Jones et al. (1976); Caminati et al. (1981)]

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

- ALMA Orion KL observations and data reduction taken from earlier work  
  > "for observations and data reduction, see e.g., Tercero et al. 2018" (5. Search for methyl thioformate in space) [from Tercero et al. 2018]
- Partition function method for internal rotor  
  > "Using a method and a code developed by Favre et al. (2014); Carvajal et al. (2019), we calculated the partition function for an internal rotor" (4. Intensity calculation) [from Favre et al. (2014); Carvajal et al. (2019)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and continuum subtraction steps, which are only referenced to Tercero et al. 2018
- Line-detection criterion and noise level (rms) used to set the upper limits
- Exact spectral windows, spectra extraction apertures and the MADEX input files
- How the 1.0e14 cm-2 limit was derived from the synthetic spectrum comparison

## Analysis recipe

1. **Global fit of laboratory spectrum**: Fit of A and E torsion-rotation lines using the RAM Hamiltonian in BELGI-Cs, with weights by measurement uncertainty  
  > "we used the BELGI-C _s_ [1] program (Hougen et al. 1994) using the rho-axis method (RAM)" (3.1. Theoretical model)
   - software: BELGI-Cs
   - parameter: Line weights from uncertainties of 30, 50, 100 kHz; 150 kHz for earlier microwave lines  
  > "we weighted the microwave transitions measured in earlier studies by Jones et al. (1976) and Caminati et al. (1981) to 150 kHz." (3.2. Millimeter- and submillimeter-wave spectral analysis)
   - fitting: 61 parameters floated for 5154 transitions  
  > "A global unitless standard deviation of 1.01 was obtained by floating 61 parameters for 3599 transitions belonging to the ground state" (3.2. Millimeter- and submillimeter-wave spectral analysis)
   - validation: Unitless standard deviation 1.01; comparison of energy levels to ab initio  
  > "A global unitless standard deviation of 1.01 was obtained" (3.2. Millimeter- and submillimeter-wave spectral analysis)
2. **Compute line strengths and partition functions**: BELGI-Cs line strengths with dipole components transformed to the RAM axis system; partition function with torsional contribution  
  > "We used the BELGI-C _s_ code to calculate the line strengths, using the energy parameters determined in Table 2." (4. Intensity calculation)
   - software: BELGI-Cs
   - assumption: Nuclear spin degeneracy assumed as 1  
  > "The nuclear spin degeneracy is assumed as 1." (Table A.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Search for CH3SC(O)H in ALMA SV Orion KL and IRAM 30m Sgr B2 and derive upper limits**: LTE synthetic spectra with MADEX, using methyl formate physical parameters, compared to data; only transitions with predicted uncertainty <0.1 MHz  
  > "we used MADEX to derive the synthetic spectrum of CH 3 SC(O)H for both sources assuming local thermodynamic equilibrium (LTE)" (5. Search for methyl thioformate in space)
   - software: MADEX
   - parameter: Orion KL: Trot 150 K, FWHM 2-3 km/s, source size 3 arcsec  
  > "_T_ rot (K) 150 150 80 / 80" (Table 3)
   - assumption: Same physical parameters as methyl formate  
  > "the same physical parameters as those derived for methyl formate by Tercero et al. (2018) and Belloche et al. (2013)" (5. Search for methyl thioformate in space)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **BELGI-Cs** : Global fit of torsion-rotation spectrum and line strengths  
  > "This work presents a global fit consisting of pure rotational transitions and rotation-torsion transitions using the BELGI-C _s_ code" (7. Conclusion)
- **MADEX** : Synthetic LTE spectra and upper limits to column density  
  > "Using the rotational constants of Table 2 and the MADEX code (Cernicharo 2012), we searched for methyl thioformate" (5. Search for methyl thioformate in space)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Barrier height V3 | 127.4846 | 0.0015 | cm-1 | 1 | V 3 = 127.4846(15) cm [−][1] |
| Global fit standard deviation | 1.01 | not stated | dimensionless | 1 | A global unitless standard deviation of 1.01 was obtained |
| Internal rotation constant F | 5.332339 | 0.000021 | cm-1 | 1 | F = 5.332339(21) cm [−][1] |
| CH3SC(O)H column density upper limit, Orion KL (both peaks) | <=1.0e14 | upper limit | cm-2 | 3 | ≤1.0 × 10 [14] ≤1.0 × 10 [14] |
| Angle theta_RAM between PAS and RAS | 30.6 | not stated | deg | 2 | The value of the angle between the PAS and the RAS was calculated using Eq. (1) to be 30.6 [◦] . |

## Qualitative findings

- CH3SC(O)H not detected in the ALMA SV Orion KL data or IRAM 30m Sgr B2 data  
  > "We did not find this species above the detection limit of both sets of data." (5. Search for methyl thioformate in space)

## Claim tuples

- H: Can the ground and excited torsional states be modeled globally? | E: BELGI-Cs global fit of 150-660 GHz lab data plus earlier microwave data | R: Std dev 1.01 for 61 parameters, V3 = 127.4846(15) cm-1 | F: Global fit reproduces data close to experimental accuracy | **supported**
- H: Is CH3SC(O)H detectable in Orion KL and Sgr B2? | E: LTE synthetic spectra compared with ALMA SV and IRAM 30m data | R: No detection; N <= 1.0e14 cm-2 in Orion KL | F: Only upper limits; abundance ratio methyl formate/CH3SC(O)H >10^3 in Orion KL | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: A global RAM approach is needed because of the large A-E splittings from the low barrier  
  > "Therefore, the use of a suitable theoretical model based on the RAM is needed to predict these rotational lines correctly." (3.2. Millimeter- and submillimeter-wave spectral analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Sgr B2 upper limit is weakly constrained due to line confusion in IRAM 30m data  
  > "the latter value may be greatly underestimated due to the high level of line confusion in the IRAM 30m data of Sgr B2" (5. Search for methyl thioformate in space)
- Limitation (authors): No E-species assigned for nu18=2  
  > "No E-species could be assigned without ambiguity for this state." (6. Discussion)
- Caveat (inferred, ours): Upper limits assume methyl formate excitation conditions apply to the sulfur species
- Caveat (inferred, ours): Detection threshold and rms not given
- Caveat (inferred, ours): ALMA reduction details only by reference

## Reproducibility

- Data public (paper): ALMA SV data acknowledged; BELGI code on PROSPE site; full Table A.1 at CDS  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2011.0.00009.SV." (Acknowledgements)
- Products in archive: _not stated_
- Code: BELGI source code, example input and readme available at PROSPE site  
  > "The source code BELGI for the fit, an example of input data file and a readme file are available at the web site PROSPE" (3.1. Theoretical model)
- Missing: Laboratory line list is only in Table A.1 excerpt (full at CDS)
- Missing: ALMA reduction and extraction details
- Missing: MADEX setup and detection criteria
- Data volume (inferred): ALMA SV Orion KL band 6 data cubes: tens to hundreds of GB; laboratory fit needs only small tables
- Score (inferred): 3/5, The lab fit is well documented with code available, but the ALMA part is a brief upper limit relying on references.
- Rediscovery candidate: no, The main results are a laboratory fit; the ALMA part is a minor non-detection with an incomplete recipe.

## Links

- Method: Hougen et al. 1994 (BELGI-Cs RAM Hamiltonian)
- Method: Kleiner 2010 (RAM intensity calculation and axis transformation)
- Method: Carvajal et al. (2019) (partition function method)
- Companion: Tercero et al. 2018 (ALMA SV Orion KL observations, reduction and methyl formate parameters)
- Companion: Belloche et al. (2013) (IRAM 30m Sgr B2 survey and methyl formate parameters)
- Related: ALMA Science Verification Orion KL

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 29,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
