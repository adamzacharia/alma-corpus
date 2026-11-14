# Laboratory spectroscopic study and astronomical detection of vibrationally excited n-propyl cyanide

`2016A&A...595A..87M` | Astronomy and Astrophysics 2016 | first author: Müller, Holger S. P. | arXiv: 1608.08129 | DOI: 10.1051/0004-6361/201629309

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Determine spectroscopic parameters of low-lying vibrational states of both n-propyl cyanide conformers in the laboratory and search for these states in ALMA EMoCA data toward Sgr B2(N2)  
  > "We wanted to determine spectroscopic parameters of low-lying vibrational states of both conformers of *n*-propyl cyanide to search for them in our ALMA data." (abstract)
- Target **Sgr B2(N2)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: spectral line survey 84.1-114.4 GHz  
  > "to perform a spectral line survey of Sgr B2(N) between 84.1 and 114.4 GHz" (1 Introduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.6''  
  > "The high angular resolution ($\sim$1.6$''$)" (1 Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Laboratory spectrometer, Universität zu Köln**: Rotational spectra of n-PrCN 36-70 GHz and 89-127 GHz  
  > "we recorded rotational spectra of *n*-PrCN in two spectral windows, 36 to 70 GHz and 89 to 127 GHz" (1 Introduction)
- External data: Ground state spectroscopic parameters of n-PrCN  
  > "The ground state rotational and centrifugal distortion parameters of *n*-PrCN were taken from (cite: det-PrCN_EtFo)" (4 Spectroscopic results) [from (cite: det-PrCN_EtFo)]
- External data: Quantum chemical vibrational energies  
  > "Scaled values from a quantum chemical calculation (cite: n-PrCN_IR_etc_2001) were taken for vibrational energies of the lowest three fundamental modes" (3 Spectroscopic properties) [from (cite: n-PrCN_IR_etc_2001)]

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

- Observations, reduction and analysis method of full EMoCA data set  
  > "A detailed account of the observations, reduction, and analysis method of the full data set covering 84.1 to 114.4 GHz was reported by (cite: deuterated_SgrB2N2_2016)." (5 Results of astronomical observations) [from (cite: deuterated_SgrB2N2_2016)]
- LTE parameters of vibrational ground state (source size 1.0'', 150 K, 5 km/s, 73.5 km/s)  
  > "A source size of 1.0$\ensuremath{''}$ was derived by (cite: i-PrCN_det_2014) from Gaussian fits" (5 Results of astronomical observations) [from (cite: i-PrCN_det_2014)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version and imaging parameters (deferred to Belloche et al. 2016)
- Software used for LTE modeling (e.g. XCLASS/WEEDS) not named
- Spectral extraction position for Sgr B2(N2)

## Analysis recipe

1. **fit laboratory spectra**: Fit vibrational changes relative to fixed ground state parameters, with Coriolis and Fermi terms for v18=1/v30=2  
  > "Using ground state spectroscopic parameters and fitting the vibrational changes has two distinct advantages." (4 Spectroscopic results)
   - software: SPCAT, SPFIT
   - fitting: _not stated_
   - validation: _not stated_
2. **LTE modeling of ALMA spectrum**: Same LTE parameters as ground state applied to vibrationally excited states  
  > "Using the same LTE parameters as for the vibrational ground state, we looked for lines from within vibrationally excited states" (5 Results of astronomical observations)
   - parameter: T = 150 K, linewidth 5 km/s, velocity 73.5 km/s, source size 1.0''  
  > "with a temperature of 150 K, a linewidth of 5 km s$^{-1}$, and a velocity of 73.5 km s$^{-1}$" (5 Results of astronomical observations)
   - assumption: LTE  
  > "The spectrum was well-fit under the local thermodynamic equilibrium (LTE) approximation" (5 Results of astronomical observations)
   - fitting: _not stated_
   - validation: All states well fit with same parameters  
  > "The fact that the lines of all states, including the vibrational ground state, are well-fit with the same parameters, gives us confidence" (5 Results of astronomical observations)

## Software

- **SPCAT/SPFIT** : predict and fit rotational spectra  
  > "We used Pickett’s SPCAT and SPFIT programs (cite: spfit_1991) to predict and fit rotational spectra" (4 Spectroscopic results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| n-PrCN column density | 1.7e17 | not stated | cm^-2 | 2 | leading to a column density of $1.7 \times 10^{17}$ cm$^{-2}$ after correction |
| Rotation temperature from population diagram | 142 | 4 | K | 2 | A fit to this diagram yields a temperature of 142 $\pm$ 4 K. |
| Energy difference v30=2 / v18=1 (anti) | 33.956 | 0.020 | cm^-1 | 1 | The experimentally determined energy difference of $33.956 \pm 0.020$ cm$^{-1}$ between these two states |

## Qualitative findings

- All eight vibrationally excited states detected toward Sgr B2(N2); far-infrared pumping not important  
  > "far-infrared pumping is, at least, not so important that it alters the apparent vibrational temperature" (6 Conclusion)

## Claim tuples

- H: Vibrationally excited n-PrCN states can be detected in the ALMA data | E: Lab spectroscopy then LTE modeling of the EMoCA spectrum | R: Lines of all eight excited states detected | F: All states reproduced by the same LTE model | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): v28=1 gauche and some anti b-type lines could not be fit well  
  > "Their frequencies could not be reproduced with one set of reasonable spectroscopic parameters." (4 Spectroscopic results)
- Caveat (inferred, ours): Some states rest on a single line
- Caveat (inferred, ours): Contamination handled by model

## Reproducibility

- Data public (paper): Interferometric data available in the ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduction details in Belloche et al. 2016
- Missing: LTE modeling software
- Data volume (inferred): hundreds of GB
- Score (inferred): 3/5, Data are public but the ALMA processing is inherited and LTE software is unnamed.
- Rediscovery candidate: no, The ALMA recipe is deferred to other papers and the main results are laboratory.

## Links

- Method: (cite: deuterated_SgrB2N2_2016) (EMoCA observations, reduction and analysis)
- Companion: (cite: i-PrCN_det_2014) (First n-PrCN LTE modeling)
- Related: EMoCA

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 17,
  "rate": 0.288
 },
 "evidence_ok": true
}
```
