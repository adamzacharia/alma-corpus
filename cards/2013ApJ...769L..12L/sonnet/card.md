# Clumping and the Interpretation of kpc-scale Maps of the Interstellar Medium: Smooth H I and Clumpy, Variable H<SUB>2</SUB> Surface Density

`2013ApJ...769L..12L` | The Astrophysical Journal Letters 2013 | first author: Leroy, Adam K. | arXiv: 1304.1586 | DOI: 10.1088/2041-8205/769/1/L12

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How do kpc-scale (area-weighted) surface densities of H I and CO-traced H2 relate to mass-weighted cloud-scale surface densities, as quantified by a clumping factor?  
  > "We define a “clumping factor” that captures this translation as the ratio of the mass-weighted surface density, which is often the quantity of physical interest, to the area-weighted surface density, which is observed." (abstract)
- Target **Antennae galaxies (North and South)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00003.SV
- bands: _not stated_
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
- Line: CO J=3-2 (not stated)
- Line: CO J=2-1 (not stated)
- Other facility **THINGS, LITTLE THINGS, VLA ANGST (H I)**: High-resolution H I integrated intensity maps  
  > "We make use of three recent H I surveys of nearby galaxies: THINGS (cite: WALTER08), LITTLE THINGS (cite: HUNTER12), and VLA ANGST (cite: OTT12)." (Data and Calculations)
- Other facility **MAGMA, NANTEN, IRAM 30-m, BIMA+FCRAO, BIMA SONG, CARMA, PAWS (CO)**: CO J=1-0 maps of LMC, M31, M33, M51 and other nearby galaxies  
  > "Except for the ALMA Antennae data, all of these data sets target the CO $J=1\rightarrow0$ line and include (sometimes exclusively) short-spacing data" (Data and Calculations)
- External data: Composite CO survey of the Milky Way  
  > "we also calculate $c$ from the composite CO survey of the Milky Way by (cite: DAME01)" (Data and Calculations) [from (cite: DAME01)]

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
- masking: Noise from empty regions; core of two successive channels with S/N>5, expanded to fainter emission  
  > "often two successive channels with $S/N > 5$ and expand this high significance core to include fainter but still significant emission" (Data and Calculations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Gaussian kernel to 1 kpc; LMC and M33 convolved to slightly worse resolution before masking  
  > "To calculate $\left< \Sigma \right>^{\rm A}$, we smooth from the native resolution to 1 kpc using a normalized Gaussian kernel." (Data and Calculations)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Exact mask expansion threshold for CO
- ALMA Antennae calibration, imaging and array details, and whether short spacings were included
- Antennae distance
- Kernel width and sampling details for the 1 kpc smoothing and the criterion for the sensitivity-based region selection
- Final per-dataset masks and convolved resolutions for LMC and M33

## Analysis recipe

1. **Build CO moment-0 maps**: Mask cubes using noise estimated from empty regions and a high-significance core, then integrate to moment 0  
  > "We integrate the masked data cube to produce a moment 0 map, which we use in further analysis." (Data and Calculations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute area- and mass-weighted surface density and clumping factor at 1 kpc**: Smooth Sigma to 1 kpc for the area-weighted value; smooth Sigma^2 and divide by the area-weighted value for the mass-weighted value; c is their ratio, sampled at hexagonal Nyquist points  
  > "we calculate $\Sigma^2$ at the native resolution, convolve this map to 1 kpc resolution using a normalized Gaussian kernel, and then divide that map by $\left< \Sigma \right>^{\rm A}$" (Data and Calculations)
   - assumption: Sigma proportional to I; alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1; N(HI) = 1.823e18 I_HI  
  > "adopting a fixed $\alpha_{\rm CO} = 4.35$ M$_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$" (Data and Calculations)
   - fitting: _not stated_
   - validation: Footnote test adding a faint diffuse CO component to PAWS M51 lowers c from ~6 to ~5.1  
  > "then $c$ drops from $\approx 6$ to $\approx 5.1$ over the region that we consider." (Footnote 2)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median H I clumping factor (ensemble) | 1.26 | +0.46/-0.15 | dimensionless | 2 | HI ensemble /  / $1.26_{-0.15}^{+0.46}$ |
| Median CO clumping factor across data sets | ~7 | factor 2-3 rms scatter | dimensionless | 2 | The median among all data sets is $\approx 7$ with a factor of $2$–$3$ rms scatter among measurements. |
| Antennae CO(2-1) North clumping factor | 13 | +6.7/-7.4 | dimensionless | 2 | Antennae CO(2-1) North / 135 / $13_{-7.4}^{+6.7}$ |
| Antennae CO(3-2) South clumping factor | 9.8 | +5.6/-2.9 | dimensionless | 2 | Antennae CO(3-2) South / 87 / $9.8_{-2.9}^{+5.6}$ |

## Qualitative findings

- H I is smooth; CO is clumpy and variable, so kpc H2/H I ratios do not translate to cloud-scale ratios  
  > "As a result, the ratio H$_2$/H I measured at $\sim$ kpc resolution cannot be trivially interpreted as a cloud-scale ratio of surface densities." (abstract)

## Claim tuples

- H: H I and H2 have similar clumping | E: Compute c at 1 kpc from high-resolution H I and CO maps | R: H I c~1.3; CO median c~7 | F: Molecular gas is far more clumped than atomic gas | **supported**
- H: CO arises from clouds with universal mass-weighted surface density | E: Compare mass-weighted surface density versus area-weighted | R: Spans two orders of magnitude | F: No good evidence for a fixed value, though not conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO data are scarce and heterogeneous; masking removes faint diffuse emission  
  > "This scarcity leads us to assemble a heterogeneous collection of high resolution CO." (Data and Calculations)
- Caveat (inferred, ours): Heterogeneous CO resolutions and sensitivities make c comparisons across datasets uncertain
- Caveat (inferred, ours): Masking choices affect the Sigma^2 term
- Caveat (inferred, ours): Fixed alpha_CO ignores variations

## Reproducibility

- Data public (paper): Several surveys public; CARMA M31 and PAWS data unpublished at the time  
  > "We acknowledge the BIMA SONG, LITTLE THINGS, and VLA ANGST collaborations for making their data public." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Antennae ALMA processing details
- Missing: Unpublished CARMA M31 and PAWS data
- Missing: Exact masks
- Data volume (inferred): Tens of GB across all surveys; ALMA SV Antennae portion a few GB
- Score (inferred): 3/5, Method and equations are clear and many data are public, but heterogeneous data and masking details are underspecified.
- Rediscovery candidate: no, Recipe depends on many heterogeneous datasets with incompletely specified masks.

## Links

- Companion: Hughes et al. (accepted) (Compares CO maps of M51, LMC and M33 PDFs)
- Related: THINGS
- Related: LITTLE THINGS
- Related: VLA ANGST
- Related: HERACLES
- Related: MAGMA
- Related: PAWS
- Related: BIMA SONG

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
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
  "facts": 55,
  "stated": 13,
  "rate": 0.236
 },
 "evidence_ok": true
}
```
