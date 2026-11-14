# Systematic Analysis of Spectral Energy Distributions and the Dust Opacity Indices for Class 0 Young Stellar Objects

`2017ApJ...840...72L` | The Astrophysical Journal 2017 | first author: Li, Jennifer I-Hsiu | arXiv: 1704.06246 | DOI: 10.3847/1538-4357/aa6f04

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Do dust opacity indices (beta) of nine Class 0 YSOs show grain growth signatures, derived from SED fitting of archival interferometric data?  
  > "A systematic data analysis is performed to derive dust temperatures, optical depths, and dust opacity indices based on single-component modified black body fittings to the spectral energy distributions (SEDs)." (abstract)
- Target **L1527**: coordinates 04:39:53.90, +26:03:10.0  
  > "L1527 | 04:39:53.90, +26:03:10.0 | Taurus   | 140           | 0/I" (Target sources); z/distance 140 pc  
  > "L1527 | 04:39:53.90, +26:03:10.0 | Taurus   | 140           | 0/I" (Target sources); distance from chen2013SMA  
  > "L1527 | 04:39:53.90, +26:03:10.0 | Taurus   | 140           | 0/I" (Target sources)

## Data provenance

- ALMA projects: 2011.0.00210.S
- bands: ALMA 345 GHz for L1527 (Cycle 0, 2012)  
  > "| 345 | ALMA | 12–432 | 2012 Aug. 29 |" (Table 2)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **SMA, VLA/JVLA, CARMA, NMA, Spitzer MIPS**: Archival visibilities at 30-340 GHz and 24/70 um photometry for SEDs  
  > "we include the Spitzer Multiband Imaging Photometer (MIPS) 24 and 70 $\ensuremath{\mu}m$ data to our SED fitting." (FIR data)
- External data: Source distances  
  > "We quote their distances from (cite: chen2013SMA), except for Serpens FIRS1" (Target sources) [from (cite: chen2013SMA); (cite: dzib2010vlba)]

## Processing

### Calibration

- pipeline or manual: ALMA data reduced with CASA  
  > "the CASA (cite: mcmullin2007casa) software package to reduce (J)VLA data taken after 2010 and ALMA data" (Submillimeter, millimeter, and radio interferometric data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 20% nominal absolute flux calibration  
  > "we consider the nominal, 20% absolute flux calibration uncertainty for all of our observations" (Intrinsic errors)
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
- continuum subtraction: CASA UVCONTSUB for ALMA  
  > "We separate the continuum data using the CASA task `UVCONTSUB`." (ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA L1527 observation details  
  > "The observation was conducted in ALMA Cycle 0 in 2012 (cite: Sakai2014)." (ALMA observations) [from (cite: Sakai2014)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for ALMA continuum
- Imaging parameters (weighting, cell size)
- Fit algorithm and priors for SED fits
- Which MS/execution blocks of 2011.0.00210.S were used
- Spitzer flux values and source

## Analysis recipe

1. **Bin visibility amplitudes**: Azimuthal average with UVAMP, dynamic binning  
  > "We first compute the azimuthally averaged visibility amplitudes at each *uv* distance using the MIRIAD task `UVAMP`." (Visibility Amplitude Analysis)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Decompose compact and extended components**: Two Gaussians or Gaussian plus point source fit to binned amplitudes  
  > "the binned visibility amplitudes are fitted by two Gaussian profiles if the compact component is marginally resolved" (Gaussian Decomposition)
   - fitting: best fit by reduced chi^2  
  > "The best fit was searched by evaluating the reduced $\chi^{2}$." (Gaussian Decomposition)
   - validation: _not stated_
3. **Fit modified black body SEDs**: Fit compact-component fluxes with F=Omega(1-exp(-tau))B(T), tau power law, nu0=300 GHz  
  > "We set $\nu_0=$ 300 GHz in our fittings." (SED fitting)
   - assumption: Common solid angle for all bands  
  > "We assume that compact components at all frequency bands share an identical sold angle of $\Omega$=0$\ensuremath{''}$5" (SED fitting)
   - fitting: _not stated_
   - validation: Monte Carlo with 1000 repetitions, 16/84 percentiles  
  > "The above procedure is repeated for 1000 times to compute the median values of $\beta$ and $\beta_{RJ}$." (Uncertainty estimation)

## Software

- **CASA** : ALMA and post-2010 VLA reduction  
  > "the CASA (cite: mcmullin2007casa) software package to reduce (J)VLA data taken after 2010 and ALMA data" (Submillimeter, millimeter, and radio interferometric data)
- **MIRIAD** : CARMA reduction, uv amplitudes, binary subtraction  
  > "Finally, MIRIAD is used to evaluate visibility amplitudes as a function of *uv* distance." (Submillimeter, millimeter, and radio interferometric data)
- **AIPS** : VLA data before 2010  
  > "We use the AIPS (cite: greisen2002aips) software package to reduce the VLA data taken before 2010" (Submillimeter, millimeter, and radio interferometric data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| beta median, L1448CN | 0.75 | 16%-84%: 0.56-0.94 | dimensionless | 3 | / L1448CN  / 0.58     / **0.75**   / 0.56   / 0.94 |
| beta median, L1527 | 0.63 | 16%-84%: 0.17-1.15 | dimensionless | 3 | / L1527    / 0.30     / **0.63**   / 0.17   / 1.15 |
| beta median, B1bS | 2.19 | 16%-84%: 1.95-2.51 | dimensionless | 3 | / B1bS     / 2.02     / **2.19**   / 1.95   / 2.51 |
| mean beta and beta_RJ | 1.3 and 1.1 | not stated | dimensionless | 3 | with the average values of $\beta= 1.3$ and $\beta_{RJ} = 1.1$ |

## Qualitative findings


## Claim tuples

- H: Grain growth has lowered beta in Class 0 YSOs | E: Single-component SED fits of compact components for nine sources | R: beta spans 0.3-2.0; four sources below 1.7 (<1) | F: Low beta in four sources may be due to obscured hot inner disks (toy models with beta=2), so no robust grain growth evidence | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Fit degeneracy and single-component assumption; low-resolution FIR data  
  > "The values of $\beta$ can be underestimated when the assumption of a single uniform emission component breaks down." (Dust opacity indices beta)
- Caveat (inferred, ours): Heterogeneous archival epochs with variable free-free
- Caveat (inferred, ours): Toy model underconstrained
- Caveat (inferred, ours): Missing flux in extended components

## Reproducibility

- Data public (paper): Archival data  
  > "abundant archival interferometric observations" (abstract)
- Products in archive: _not stated_
- Missing: Fitting algorithm details
- Missing: Archive IDs for non-ALMA data
- Missing: Spitzer fluxes
- Data volume (inferred): Tens of GB across many archives
- Score (inferred): 3/5, Multi-archive data with partial recipe; ALMA is minor.
- Rediscovery candidate: no, Many non-ALMA archives and incomplete settings.

## Links

- Companion: (cite: Lee2017) (Spatially resolved self-obscured disk at 345 GHz)
- Related: VANDAM

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
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
  "facts": 60,
  "stated": 22,
  "rate": 0.367
 },
 "evidence_ok": true
}
```
