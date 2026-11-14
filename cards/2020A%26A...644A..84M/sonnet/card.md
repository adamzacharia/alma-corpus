# The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. I. Isomers of C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB>

`2020A&A...644A..84M` | Astronomy and Astrophysics 2020 | first author: Mininni, C. | arXiv: 2009.13297 | DOI: 10.1051/0004-6361/202038966

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Which C2H4O2 isomers (methyl formate, glycolaldehyde, acetic acid) are detected in the hot core G31.41+0.31, with what abundances and emission sizes, and what do they imply for formation pathways?  
  > "In this first paper, we present the survey and discuss the detection and relative abundances of the 3 isomers of $\mathrm{C_{2}H_{4}O_{2}}$: methyl formate, glycolaldehyde and acetic acid." (abstract)
- Target **G31.41+0.31 (G31) hot molecular core**: coordinates 18 47 34, -01 12 45 (J2000)  
  > "| 18 47 34 | -01 12 45 | 96.5 | $3.75$ | $4.4\times10^{4}$ | $70$ |" (Table 1); "a well-known and studied HMC located at a distance of 3.75 kpc (cite: immer2019)" (Introduction); z/distance 3.75 kpc; vLSR 96.5 km/s  
  > "| 18 47 34 | -01 12 45 | 96.5 | $3.75$ | $4.4\times10^{4}$ | $70$ |" (Table 1); "a well-known and studied HMC located at a distance of 3.75 kpc (cite: immer2019)" (Introduction); distance from Immer et al. 2019  
  > "| 18 47 34 | -01 12 45 | 96.5 | $3.75$ | $4.4\times10^{4}$ | $70$ |" (Table 1); "a well-known and studied HMC located at a distance of 3.75 kpc (cite: immer2019)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00501.S
- bands: Band 3, 84.05-115.91 GHz (~32 GHz)  
  > "The survey covered the complete spectral range of ALMA band 3, between 84.05 GHz and 115.91 GHz" (2.1 Observations)
- frequencies and spectral setup: 9 correlator configurations, 4 contiguous basebands of ~937 MHz each; resolution ~0.488 MHz (~1.3-1.7 km/s); overlaps ~7.3-29 MHz  
  > "We used 9 correlator configurations (*spec*) and for each of them, 4 contiguous basebands of $\sim937\,\mathrm{MHz}$ were observed simultaneously." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 43 antennas  
  > "using 43 antennas" (2.1 Observations)
- configurations: _not stated_
- baselines: 15-1397 m (spec 1-2); 15-783 m (spec 3-9)  
  > "| spec 1 | BB 1     | 84520.801  |   0.48824   |     1.1      | 15 - 1397 |" (Table 2)
- angular resolution: 1.2'' x 1.2'' (~4400 au), all specs degraded to common beam  
  > "We decided to degrade the angular resolution of all the *specs* to the lowest one ($\sim1.2\ensuremath{''}$)" (2.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: map rms 0.5-1.9 mJy/beam; spectrum rms 7-27 mK, 27 mK adopted  
  > "$rms$ of the maps varies between 0.5 mJy/beam and 1.9 mJy/beam." (2.1 Observations)
- time on source: _not stated_
- observing dates: Cycle 5, 18 January - 7 September 2018  
  > "between the $18^{th}$ of January and the $7^{th}$ of September 2018" (2.1 Observations)
- pi or archival as stated: P.I. M. T. Beltrán  
  > "project 2017.1.00501.S, P.I.: M. T. Beltrán" (2.1 Observations)
- Line: CH3OCHO (methyl formate) 196 lines identified, 25 used in fit (e.g. 88.2207, 103.4787, 111.4084 GHz)
- Line: CH3COOH (acetic acid) 26 lines identified, 14 used in fit (e.g. 85.6331, 90.2462, 100.8554 GHz)
- Line: CH2OHCHO (glycolaldehyde) 20 lines detected, 12 used in fit (e.g. 88.5304, 93.0485, 95.7562 GHz)
- External data: Distance to G31 of 3.75 kpc  
  > "located at a distance of 3.75 kpc (cite: immer2019)" (Introduction) [from (cite: immer2019)]
- External data: Luminosity 4.4e4 Lsun and mass ~70 Msun (rescaled)  
  > "b) from (cite: oso2009), rescaled to a distance of 3.75 kpc; c) from (cite: cesa2019), after rescaling to a distance of 3.75 kpc." (Table 1) [from (cite: oso2009); (cite: cesa2019)]
- External data: Spectroscopic catalog entries (CDMS, JPL; acetic acid from Ilyushin et al. 2013)  
  > "The spectroscopic data of acetic acid, from the work of (cite: ilyushin2013), were introduced in CDMS in May 2019" (3.2 Spectral analysis) [from (cite: cdms2005); (cite: jpl1998); (cite: ilyushin2013)]
- External data: Isomer column density ratios, abundances and N(H2) for comparison sources (Table of literature)  
  > "References to the works on the 3 isormers: (1) (cite: xue2019); (2) (cite: el2019)" (Table 5) [from xue2019; el2019; Jorge2016; manigand2020; taquet2015 and others]
- External data: Dust opacity k0 = 0.8 cm2/g at 220 GHz  
  > "a dust opacity coefficient $k_0 = 0.8\,\mathrm{cm^2/g}$ at 220 GHz (cite: ossenkopf1994)" (3.1 Continuum) [from (cite: ossenkopf1994)]
- External data: MF Tex gradient (497 K at 0.22'' to 110 K at 1.32'')  
  > "(cite: beltran2018) found a decrease of $T_{\rm{ex}}$ of methyl formate with distance from the core center" (3.2 Spectral analysis) [from (cite: beltran2018)]

## Processing

### Calibration

- pipeline or manual: calibrated and imaged with CASA (pipeline vs manual not specified)  
  > "The data were calibrated and imaged with CASA" (2.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939 (flux and bandpass); phase calibrator J1851+0035  
  > "For all the *specs* the source used as flux and bandpass calibrator is J1751+0939, while J1851+0035 is the phase calibrator." (2.1 Observations)
- flux scale uncertainty: ~5%  
  > "The uncertainties in the flux calibration are $\sim5\%$ (from Quality Assesment 2 reports)" (2.1 Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0  
  > "The maps were created using a robust parameter of (cite: briggs) set equal to 0" (2.1 Observations)
- uv taper: _not stated_
- cell size: pixel 0.15''  
  > "smaller than the pixel size ($0.15\ensuremath{''}$)" (4.1 Methyl Formate)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: No line-free channels; continuum from STATCONT on spec5 BB1; line fit done without subtraction, continuum modelled as power law  
  > "it was not possible to find a sufficient number of channels without line emission that could be used to obtain a map of the continuum emission" (2.2 Continuum determination)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.2'' x 1.2'' restoring beam  
  > "a restoring sinthesized beam of $1.2\ensuremath{''}\times1.2\ensuremath{''}$" (2.1 Observations)
- final rms: 0.5-1.9 mJy/beam  
  > "$rms$ of the maps varies between 0.5 mJy/beam and 1.9 mJy/beam." (2.1 Observations)

### Inherited from earlier work

- STATCONT method for continuum determination  
  > "we used STATCONT (cite: alvaro2018), a python-based tool designed to determine the continuum emission level in spectral data" (2.2 Continuum determination) [from (cite: alvaro2018)]
- XCLASS LTE modelling and optical-depth formula  
  > "Eq. (B.28) of (cite: xclass) gives the optical depth of a line as a function of frequency" (Appendix B) [from (cite: xclass)]

### Not stated but needed to reproduce (our reading)

- Whether the archive pipeline or manual calibration and CASA version were used
- Exact tclean parameters (deconvolver, niter, threshold, masks, image size)
- How the beam was matched to 1.2'' (imsmooth/restoringbeam details)
- STATCONT parameters
- XCLASS optimizer algorithm, start values, iterations and the preliminary-fit FWHM/vLSR procedure
- Exact fit frequency ranges and line lists (only in appendix tables not reproduced)
- Size of the spectral extraction area and how N(H2) was extracted from the same area

## Analysis recipe

1. **Create continuum map and N(H2)**: STATCONT continuum from spec5 BB1; 2D Gaussian fit with imfit; N(H2) from flux in the extraction area  
  > "We have fitted a 2D gaussian to the continuum emission of the main core using the task *imfit* of CASA" (3.1 Continuum)
   - software: CASA, STATCONT
   - parameter: flux 0.1 Jy at 99.0 GHz  
  > "The flux of the continuum inside the area from which we extracted the spectrum is of 0.1 Jy at the mean frequency of 99.0 GHz" (3.1 Continuum)
   - assumption: Td = 150 K, beta = 2.0, k0 = 0.8 cm2/g at 220 GHz, mu = 2.33, gas-to-dust 100  
  > "Assuming a dust temperature of $150\,\mathrm{K}$, $\beta = 2.0$, a dust opacity coefficient $k_0 = 0.8\,\mathrm{cm^2/g}$ at 220 GHz" (3.1 Continuum)
   - fitting: _not stated_
   - validation: Consistent within a factor ~4 with Rivilla et al. 2017  
  > "This value is consistent within a factor $\sim4$ with the previous estimate by (cite: rivilla2017a)." (3.1 Continuum)
2. **Extract and merge spectra**: Mean spectrum within one beam at continuum peak; convert to T_SB (Rayleigh-Jeans); remove baseband jumps by matching overlaps; convert to rest frequency and rebin with HIPE  
  > "we forced the channels of spec1 BB2 in the overlapping region to match those of spec1 BB1, by subtracting from spec1 BB2 the mean value of the difference" (2.3 Combination of the spectral windows)
   - software: HIPE, CASA
   - parameter: vLSR 96.5 km/s; bin width 0.48840 MHz; conservative rms 27 mK  
  > "rebinned the spectra to a constant value of the bin width equal to 0.48840 MHz using HIPE" (2.3 Combination of the spectral windows)
   - fitting: _not stated_
   - validation: Baseline rms 1.2 K (~12% of continuum) included as error  
  > "This 12% error on the continuum level is included as additional error on the parameters derived from the fit to the spectrum." (2.3 Combination of the spectral windows)
3. **Line identification and selection**: Preliminary line identification of whole spectrum, then selection of unblended transitions with 3 rules (>3 rms, blending criteria)  
  > "We followed three rules to identify a transition of one of the 3 $\mathrm{C_2H_4O_2}$ isomers" (3.2 Spectral analysis)
   - software: XCLASS, CDMS, JPL
   - parameter: Eu < 250 K for the main fit; 25 MF, 12 GA, 14 AA lines  
  > "For MF we selected 25 lines, for GA 12 and for AA 14." (3.2 Spectral analysis)
   - fitting: _not stated_
   - validation: All lines optically thin (tau0 << 1)  
  > "we find that all transitions are optically thin ($\tau_{0}\ll1$)" (3.2 Spectral analysis)
4. **Fit LTE synthetic spectra for Tex and Ntot**: XCLASS single-component LTE chi2 fit; continuum, FWHM, vLSR fixed from preliminary fit; Tex and Ntot free  
  > "the continuum, from Eq. ([\[eqcontinuum\]]), the FWHM and $V_{\mathrm{LSR}}$ of the selected species were kept fixed to the values found by a preliminary fit" (3.2 Spectral analysis)
   - software: XCLASS
   - parameter: beam filling factor 1; single temperature component  
  > "The column densities of the 3 isomers have been derived assuming a beam filling factor of 1." (4 Results)
   - assumption: LTE, justified by n ~ 1e8 cm-3  
  > "a rough estimate of the volume density of the core is $n\sim10^8\,\mathrm{cm^{-3}}$" (3.2 Spectral analysis)
   - fitting: chi2 minimisation of observed vs synthetic spectrum  
  > "The fitting procedure varies the free parameters to minimize the $\chi^{2}$ between the observed spectrum and the synthetic one." (3.2 Spectral analysis)
   - validation: Fixed-Tex grids for AA (100-300 K) and GA (150-300 K); fit including Eu>250 K transitions for MF and AA  
  > "we performed the fit to AA for a grid of fixed temperatures, ranging from $100\,\mathrm{K}$ to $300\,\mathrm{K}$" (4.2 Acetic Acid)
5. **Abundances and emission size**: X = Ntot/N(H2) in the 1.2'' beam with 20% N(H2) uncertainty; moment-0 maps of 8 transitions per molecule normalised and averaged, 2D Gaussian with imfit  
  > "To obtain a mean value of diameter of the emitting region of each molecule, the 8 maps of a given molecule have been normalized with respect to the peak intensity, and averaged together." (4 Results)
   - software: CASA
   - fitting: 2D Gaussian (imfit)  
  > "The task *imfit* of CASA has been used to fit a 2D gaussian to these maps" (4 Results)
   - validation: _not stated_
6. **Compare with literature sources and chemical models**: Compare abundances and column density ratios with other sources and published chemical model predictions  
  > "Figure [9] shows the abundances with respect to H$_2$ (upper panel) and the column density ratios (lower panel)" (5.1 Comparison with other sources)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging, imfit Gaussian fits  
  > "The data were calibrated and imaged with CASA" (2.1 Observations)
- **STATCONT** : Continuum determination in line-rich data  
  > "we used STATCONT (cite: alvaro2018)" (2.2 Continuum determination)
- **XCLASS** : Line identification and LTE spectral fitting  
  > "The line identification and the fit to the $\mathrm{C_{2}H_{4}O_{2}}$ isomers have been obtained with the software XCLASS" (3.2 Spectral analysis)
- **HIPE** : Rebinning spectra to constant channel width  
  > "rebinned the spectra to a constant value of the bin width equal to 0.48840 MHz using HIPE" (2.3 Combination of the spectral windows)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Methyl formate Tex | 221 | ±27 | K | 4 | / $\mathrm{CH_{3}OCHO}$ / $6.8$ / $1.1$ / $221\pm27$ / $20\pm4$ / |
| Methyl formate Ntot | 2.0e18 | ±0.4e18 | cm-2 | 4 | $N_{\rm{tot}}=\mathrm{(2.0\pm0.4)\times10^{18}\,cm^{-2}}$ |
| Methyl formate abundance | 2.0e-7 | ±0.6e-7 | dimensionless | 5 | an abundance $X=(2.0\pm0.6)\times10^{-7}$ |
| Acetic acid Tex | 299 | ±42 | K | 4 | $T_{\rm{ex}}=299\pm42\,\mathrm{K}$ |
| Acetic acid Ntot | 8.4e17 | ±1.4e17 | cm-2 | 4 | $N_{\rm{tot}}=(8.4\pm1.4)\mathrm{\times10^{17}\,cm^{-2}}$ |
| Acetic acid abundance range | 4.3e-8 to 8e-8 | best fit 8±3e-8 | dimensionless | 5 | This implies a range in abundance $X$ between $4.3\times10^{-8}$ and $8\times10^{-8}$. |
| Glycolaldehyde Tex | 128 | ±17 | K | 4 | $T_{\rm{ex}}=128\pm17\,\mathrm{K}$ |
| Glycolaldehyde Ntot | 5.0e16 | ±0.7e16 | cm-2 | 4 | $N_{\rm{tot}}=\mathrm{(5.0\pm0.7)\times10^{16}\,cm^{-2}}$ |
| Glycolaldehyde abundance | 5.0e-9 | ±1.4e-9 | dimensionless | 5 | an abundance $X=(5.0\pm1.4)\times10^{-9}$ |
| N(H2) in 1.2'' beam | 1.0e25 | ±0.2e25 | cm-2 | 1 | $N_{\rm{H_2}}=(1.0\pm0.2)\mathrm{\times10^{25}\,cm^{-2}}$ |
| Continuum deconvolved size of HMC | 1.41'' x 1.22'' | not stated | arcsec | 1 | the deconvolved size of the continuum being $1.41\ensuremath{''}\times1.22\ensuremath{''}$ |
| Dust emissivity index beta of continuum power law | 0.4 | not stated | dimensionless | 2 | /   84.079   /     /          10.4          /     /   0.4   / |

## Qualitative findings

- MF emission is most extended and AA most compact; all emission comes only from the HMC  
  > "the emission of MF is the most extended among the 3 isomers, while AA is the most compact" (4 Results)
- G31 has the highest MF and AA abundances among compared sources  
  > "G31 has the highest values of abundance of MF and AA among the 4 sources shown" (5.1 Comparison with other sources)

## Claim tuples

- H: Are all three C2H4O2 isomers detected in G31? | E: XCLASS LTE fit of unblended transitions in Band 3 survey | R: MF, AA and GA fit with Tex 128-299 K and abundances 5e-9 to 2e-7 | F: All three isomers detected; MF and AA abundances highest in the literature sample | **supported**
- H: Do the isomers have different emission extents? | E: Averaged normalised moment-0 maps and radial profiles | R: MF most extended, AA most compact | F: Emission size differs among isomers | **supported**
- H: Which formation routes explain the abundances? | E: Compare with published chemical models | R: MF abundance not reproduced by gas-phase only; AA grain-surface route insufficient; GA ambiguous | F: Grain-surface needed for MF; GA both possible; AA gas-phase needs more testing | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-temperature fit chosen to reduce free parameters despite known Tex gradient  
  > "we decided to perform a single temperature component analysis, to reduce the number of free parameters as much as possible" (3.2 Spectral analysis)
- Alternative: Two-temperature component fit for MF did not converge or improve the fit  
  > "a two-temperature component fit does not properly converge and does not significantly improve the fit" (4.1 Methyl Formate)
- How they decided it was enough: _not stated_
- Limitation (authors): Tex-Ntot degeneracy for AA gives a factor ~2 uncertainty on Ntot  
  > "with an uncertainty on $N_{\rm{tot}}$ of a factor $\sim2$" (4.2 Acetic Acid)
- Limitation (authors): Some MF transitions under-reproduced; unidentified blends possible  
  > "we cannot exclude that some of these transitions may also be blended with still unidentified molecular species" (4.1 Methyl Formate)
- Caveat (inferred, ours): Beam-filling factor of 1 with a barely resolved source may bias column densities
- Caveat (inferred, ours): N(H2) from dust with assumed Td=150 K, beta=2 conflicts with fitted beta=0.4 and is uncertain beyond 20%
- Caveat (inferred, ours): Single-Tex fit ignores the known temperature gradient
- Caveat (inferred, ours): Continuum-level baseline from by-eye fit with spectral merging adds systematics

## Reproducibility

- Data public (paper): Data from ALMA project 2017.1.00501.S, acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00501.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Tclean parameters and CASA version
- Missing: Line lists in appendix tables (not provided in text)
- Missing: XCLASS fit configuration details
- Data volume (inferred): Large: 36 basebands over 9 setups, likely hundreds of GB raw; ~100s GB
- Score (inferred): 3/5, Data and spectral fitting recipe are largely described and results numeric, but imaging parameters, pipeline version and fit settings are missing.
- Rediscovery candidate: no, Public status not stated explicitly and imaging/fit settings are incomplete, although results are numeric.

## Links

- Method: Möller et al. 2017 (cite: xclass) (XCLASS software)
- Method: Sánchez-Monge et al. 2018 (cite: alvaro2018) (STATCONT continuum determination)
- Companion: Beltrán et al. 2018 (cite: beltran2018) (High-resolution ALMA study of G31 providing MF Tex gradient)
- Companion: Rivilla et al. 2017a (cite: rivilla2017a) (Previous IRAM 30m G31 COM column densities)
- Related: GUAPOS

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
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
  "facts": 84,
  "stated": 57,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
