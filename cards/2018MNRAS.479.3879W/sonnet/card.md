# An ALMA survey of CO in submillimetre galaxies: companions, triggering, and the environment in blended sources

`2018MNRAS.479.3879W` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Wardlow, J. L. | arXiv: 1806.05193 | DOI: 10.1093/mnras/sty1526

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Are the multiple SMG components blended in single-dish submillimetre sources physically associated, and what are the companions and environments of SMGs (interaction triggering)?  
  > "In this paper we investigate whether the blended multiple SMG components of single-dish submillimetre sources are physically associated via an ALMA $^{12}$CO survey in Band 3, and VLT/XSHOOTER spectroscopic data." (Introduction)
- Target **LESS 41, LESS 49, LESS 71, LESS 75, LESS 87 (ECDFS) and UDS 306 (UDS)**: coordinates e.g. ALESS 41.1 03h31m10.07s -27d52m36.7s (J2000); per-source positions in Table 1  
  > "ALESS 41.1 | 03$^{\rm h}$31$^{\rm m}$10.07s $-$27$^\circ$52$'$36.7$''$" (Table 1); z/distance z=2.3-3.7 (CO redshifts)  
  > "ALESS 41.1 | 03$^{\rm h}$31$^{\rm m}$10.07s $-$27$^\circ$52$'$36.7$''$" (Table 1); distance from optical/NIR spectroscopic redshifts (Danielson17) and ALMA CO  
  > "ALESS 41.1 | 03$^{\rm h}$31$^{\rm m}$10.07s $-$27$^\circ$52$'$36.7$''$" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00754.S
- bands: Band 3 (~3.3 mm, ~90 GHz)  
  > "were taken in ALMA Band 3 (at $\sim3.3$ mm or $\sim90$ GHz)" (2.1 ALMA data)
- frequencies and spectral setup: one ~2 GHz sideband tuned to CO(3-2) (CO(4-3) for LESS 71); ~7.5 GHz across two sidebands  
  > "tuned such that one of the $\sim2$ GHz sidebands included the expected CO(3–2) line" (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.8-1.1 arcsec  
  > "have angular resolutions of 0.8–1.1$''$" (2.1 ALMA data)
- max recoverable scale: ~11 arcsec  
  > "In these configurations the Maximum Recoverable Scale is $\sim11\ensuremath{''}$" (2.1 ALMA data)
- sensitivity: 3.3-mm continuum noise 2-11 uJy/beam (naturally weighted)  
  > "which have 3.3-mm continuum noise of 2–$11~\mu{\rm Jy~beam^{-1}}$" (2.1 ALMA data)
- time on source: ~800 to ~6400 s  
  > "Integration times ranged from $\sim800$ to $\sim6400$ s" (2.1 ALMA data)
- observing dates: Cycle 4, 2016 November 12, 16 and 20  
  > "The observations were taken during Cycle 4 on 2016 November 12, 16 and 20" (2.1 ALMA data)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (LESS 41, 49, 75, 87, UDS 306) (not stated)
- Line: 12CO J=4-3 (LESS 71) (not stated)
- Other facility **VLT/XSHOOTER**: optical/NIR spectroscopy of ALMA SMGs in UDS (programme 094.A-0811); no redshifts obtained  
  > "made with the XSHOOTER spectrograph (cite: Vernet11) on the ESO VLT/UT2 between 2014 November 20 and 2015 January 19 as part of programme 094.A-0811" (2.2 XSHOOTER spectroscopy)
- External data: 870-um positions and fluxes of SMGs from ALESS and AS2UDS ALMA continuum  
  > "Names, positions and 870-$\mu$m continuum fluxes ($S_{870}$) are from (cite: Hodge13) and (cite: Simpson15b) for 870-$\mu$m selected SMGs." (Table 1) [from (cite: Hodge13); (cite: Simpson15b)]
- External data: Optical/NIR spectroscopic redshifts  
  > "Redshifts from optical or near-infrared spectroscopy (cite: Danielson17)." (Table 1) [from (cite: Danielson17)]
- External data: Infrared luminosities from 250-870 um photometry  
  > "derived from the 250–870 $\mu$m photometry (cite: Swinbank14)" (4 Analysis and Discussion) [from (cite: Swinbank14)]
- External data: CO luminosity-L_IR comparison samples and CO brightness temperature ratios  
  > "using the brightness temperature ratios for the SMGs compiled by (cite: CarilliWalter13)" (4 Analysis and Discussion) [from (cite: CarilliWalter13); (cite: Bothwell13; Daddi15; Papovich16; Lee17; Stach17; Hayashi17)]
- External data: Literature blended SMG pairs with spectroscopic redshifts  
  > "There are a further five blended 870-$\mu$m sources in single-dish blank-field surveys with spectroscopic redshifts for both constituent SMGs" (4.1) [from (cite: Wang11; Danielson17; Hayward18)]
- External data: ASPECS blank-field counts for comparison  
  > "only the ALMA SPECtroscopic Survey in the Hubble Ultra-Deep Field (cite: Walter16; Aravena16a; Decarli16a; Decarli16b) provides a suitable comparison sample" (3.4) [from (cite: Walter16; Aravena16a; Decarli16a; Decarli16b)]
- Simulation/model as data: NFW halo velocity-separation curves (Lokas01 formalism, concentration 3.5)  
  > "calculated using the formalism of (cite: Lokas01) and assuming a concentration parameter of 3.5" (4.1)

## Processing

### Calibration

- pipeline or manual: ALMA-provided pipeline scripts  
  > "using the ALMA-provided pipeline scripts to reduce the data" (2.1 ALMA data)
- casa version: CASA 4.7.0  
  > "version 4.7.0, using the ALMA-provided pipeline scripts to reduce the data" (2.1 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass/phase calibrators also used for flux (J0334-4008, J0317-2803/J0343-2530; J0238+1636, J0217-0820)  
  > "and these were also used to calibrate the fluxes" (2.1 ALMA data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean (CASA)  
  > "The data were imaged in stages using the clean task." (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: natural weighting (Briggs robust=2)  
  > "natural weighting (i.e. Briggs weighting with ‘${\rm Robust=2}$’)" (2.1 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: sources manually masked, cleaned to ~rms level  
  > "manually masking sources and cleaning the data to approximately rms level" (2.1 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv-plane  
  > "Using uvcontsub, in the *uv*-plane, we fitted the continuum and subtracted it" (2.1 ALMA data)
- line free channels: channels containing emission lines excluded (specific ranges not given)  
  > "we excluded the channels containing emission lines and used clean to image the remaining data" (2.1 ALMA data)
- primary beam correction: fluxes measured with imfit on PB-corrected maps  
  > "measured from the primary beam corrected, naturally-weighted maps using the casa task imfit" (2.1 ALMA data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: typically 0.8-1.1 arcsec  
  > "with synthesized beams typically 0.8–1.1$''$" (2.1 ALMA data)
- final rms: 2-11 uJy/beam continuum  
  > "3.3-mm continuum noise of 2–$11~\mu{\rm Jy~beam^{-1}}$" (2.1 ALMA data)

### Inherited from earlier work

- Target 870-um positions, fluxes and component names  
  > "Names, positions and 870-$\mu$m continuum fluxes ($S_{870}$) are from (cite: Hodge13) and (cite: Simpson15b)" (Table 1) [from (cite: Hodge13); (cite: Simpson15b)]
- Detailed analyses of individual galaxies deferred  
  > "Detailed analyses of the individual galaxies will be presented in a forthcoming paper (Wardlow et al. in prep.)." (Introduction) [from Wardlow et al. in prep.]

### Not stated but needed to reproduce (our reading)

- Channel width/spectral resolution of cubes and exact line-free channels per field
- Clean threshold, cell and image size, mask definitions
- Number of execution blocks and array configurations per field
- Source of L_IR values per SMG and how L_IR limits were computed in detail
- Flux scale uncertainty
- Details of NFW pair-velocity calculation and halo-mass assignment for pairs
- Statistical method for the 64±18% and 21±12% fractions (error estimation)
- Rest frequencies used

## Analysis recipe

1. **Reduce and image ALMA data**: Pipeline calibration then clean imaging: dirty natural-weight cubes, line-free continuum maps, uvcontsub continuum-subtracted cubes  
  > "We initially used natural weighting (i.e. Briggs weighting with ‘${\rm Robust=2}$’) with no cleaning to generate a ‘dirty’ cube" (2.1 ALMA data)
   - software: CASA
   - parameter: natural weighting, robust=2  
  > "natural weighting (i.e. Briggs weighting with ‘${\rm Robust=2}$’)" (2.1 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect CO in targeted SMGs**: Extract beam-averaged spectra, rebin to 50/100/200 km/s, search for >=2 sigma peaks, fit Gaussians, threshold set by SNR where false detection rate on inverted spectra is zero  
  > "the SNR at which the false detection rate (FDR) drops to zero is used as the threshold for identifying emission lines from the SMGs" (3.1)
   - software: CASA
   - fitting: Gaussian profile fit; integrated SNR over twice expected FWHM  
  > "A Gaussian profile is fit to each potential line and the integrated signal-to-noise ratio (SNR) measured from the rebinned spectra over twice the expected FWHM." (3.1)
   - validation: Inverted spectra for false detections; CO redshifts compared with optical/NIR redshifts  
  > "The CO and optical/near-infrared redshifts agree within the expected uncertainties (to within 800 ${\rm km~s^{-1}}$ in all cases[^4])" (3.1)
3. **Blind search for serendipitous line emitters**: Collapse cubes into 200 km/s slices in 100 km/s steps, find pixels >5.5 sigma within the primary beam (zero false positives in inverted cubes); secondary 5.0 sigma search at 3.6 um source positions  
  > "we search within the primary beam for pixels brighter than $5.5$ times the rms noise of the slice" (3.2)
   - parameter: 5.5 sigma blind; 5.0 sigma at SIMPLE 3.6 um positions (15% contamination)  
  > "This secondary search has a false contamination rate of 15%" (3.2)
   - fitting: _not stated_
   - validation: Search repeated on inverted cubes  
  > "based on performing the same search on the inverted cubes" (3.2)
4. **Measure line fluxes and widths**: Iterative extraction of spectra over line-emission area, single/double Gaussian fits; errors from 1000 noise trials; 500 km/s Gaussian limits for non-detections  
  > "Uncertainties on the fit and derived parameters are determined from 1000 trials for each line" (3.3)
   - software: mpfit (IDL)
   - fitting: mpfit single or double Gaussian; 1000 Monte Carlo trials  
  > "The extracted spectra are fit with single or double Gaussian profiles using mpfit in IDL (cite: Markwardt09)." (3.3)
   - validation: _not stated_
5. **Search for serendipitous continuum sources**: Line-free dirty continuum map search; fluxes via imfit  
  > "Four 3.3-mm continuum emitters are identified that were not significantly detected in the original 870-$\mu$m ALMA data" (3.4)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Compared with ASPECS blank-field counts  
  > "We conclude that detecting four serendipitous continuum sources in our data is marginally in excess of the blank-field expectations." (3.4)
6. **Test whether blended SMGs are physically associated**: Compare CO limits of undetected SMGs to L'CO-L_IR relation and compare velocity/spatial separations of pairs with NFW halo curves  
  > "Curves showing the expected velocity separation of pairs of test masses in Navarro-Frenk-White (NFW; (cite: Navarro97)) halos are included" (4.1)
   - parameter: NFW concentration 3.5; CO searched within ~2500 km/s of primary  
  > "assuming a concentration parameter of 3.5, as expected for halos of mass $10^{12-14}$ ${\rm M_{\ensuremath{\odot}}}$ at $z=2$–3" (4.1)
   - assumption: Non-detected SMGs would follow the L'CO-L_IR trend if at same redshift  
  > "Figure [2](#fig:lirlco) includes limits on the CO-undetected SMGs in our sample, assuming that they have a redshift that would place CO within $\sim2500$ ${\rm km~s^{-1}}$ of the spectroscopically-confirmed SMG(s)." (4.1)
   - fitting: _not stated_
   - validation: Combined with five literature blended sources  
  > "Including these sources in the statistics reveals that only three [four] in 11 ($27\%$ [36%]) blended SMG fields contains closely physically associated SMGs" (4.1)
7. **Identify serendipitous line emitters and assess triggering**: Assume lines are CO(3-2) (same-sideband argument, ASPECS counts, L'CO-L_IR consistency), then compare pair separations with halo curves to count interaction-triggered SMGs  
  > "Instead all three of the serendipitous line sources are observed in the same sideband as the CO from the targeted 870-$\mu$m selected SMGs" (4.2)
   - assumption: L'CO(3-2)/L'CO(1-0)=0.66, alpha_CO=1 Msun (K km/s pc^2)^-1  
  > "assuming $L^{\prime}_{\rm CO(3-2)} / L^{\prime}_{\rm CO(1-0)}=0.66$ and $\alpha_{\rm CO}=1$ ${\rm M_{\ensuremath{\odot}}}$(K ${\rm km~s^{-1}}$ pc$^2)^{-1}$" (4.3)
   - fitting: _not stated_
   - validation: 12% random chance of all three lines in same sideband; ASPECS expectation 0-1 per sideband  
  > "making the likely emission CO(3–2) associated with the target SMG (12% random chance)" (4.2)

## Software

- **CASA** 4.7.0: data reduction (pipeline), clean imaging, uvcontsub, imfit  
  > "Common Astronomy Software Applications (casa) version 4.7.0" (2.1 ALMA data)
- **mpfit (IDL)** : Gaussian line fitting  
  > "using mpfit in IDL (cite: Markwardt09)" (3.3)
- **EsoRex** : XSHOOTER data reduction  
  > "Data reduction was carried out using the EsoRex[^3] pipeline" (2.2 XSHOOTER spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMGs detected in CO | 7 of 14 | not stated | count | 2 | We detect CO(3–2) or CO(4–3) at $z=2.3$–3.7 in seven of the 14 SMGs |
| Fraction of blended SMGs unlikely physically associated | 64 | ±18 | % | 6 | $64(\pm18)\%$ of the SMGs in blended submillimetre sources are unlikely to be physically associated |
| Fraction of SMGs with close kinematic companions | 21 | ±12 | % | 7 | We find that $21\pm12\%$ of SMGs have spatially-distinct and kinematically-close companion galaxies |
| New 3.3 mm continuum sources | 4 | not stated | count | 5 | Four 3.3-mm continuum emitters are identified that were not significantly detected in the original 870-$\mu$m ALMA data |
| Serendipitous line emitters | 3 (7.4, 13.9 and 5.0 sigma) | not stated | count | 3 | at 7.4 and $13.9\sigma$, respectively – and one line emitter in the 3.6-$\mu$m prior search |
| UDS 306.0-306.1 velocity separation | 1200 km/s across 50 kpc | not stated | km/s | 6 | has a velocity separation of 1200 ${\rm km~s^{-1}}$ across 50 kpc |
| ALESS 41.1 CO(3-2) integrated flux | 0.85 | 0.03 | Jy km/s | 4 | $0.85\pm0.03$ |

## Qualitative findings

- SMGs inhabit overdense regions, but not dense enough on ~100 kpc scales to cause blending given short SMG lifetimes  
  > "These data suggest that the SMGs inhabit overdense regions, but that these are not sufficiently overdense on $\sim100$ kpc scales to influence the source blending" (abstract)

## Claim tuples

- H: Blended SMGs in single-dish sources are physically associated | E: ALMA Band 3 CO search for secondary SMGs at the redshift of the spectroscopic primary, plus literature pairs | R: CO detected from only one of seven companion SMGs; 5/6 fields not closely associated; combined 36±18% associated | F: Most blended SMGs are line-of-sight alignments or in different parts of large-scale structure | **supported**
- H: Serendipitous emitters are companions at similar redshifts | E: Blind line search and ASPECS comparison | R: Three line emitters in same sideband as target CO | F: Most likely CO(3-2) from companions | **supported**
- H: Interactions trigger SMG star formation | E: Compare pair separations to halo velocity curves | R: 3 of 14 SMGs (21±12%) have close spatial/spectral companions | F: Interaction triggering possible for a minority; more studies needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Millimetre CO spectroscopy yields redshifts for all blended components simultaneously and is unaffected by dust absorption  
  > "where the multiple components can be observed simultaneously and dust absorption has a negligible effect on the ability to determine redshifts" (Introduction)
- Alternative: Possible line at 99.7 GHz near ALESS 41.3 (SNR 8.53 vs 8.50 threshold) excluded from analysis  
  > "given that the significance of this line is at the limit of our sample we do not include it in our subsequent analyses" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Spatial resolution ~1 arcsec insensitive to late-stage mergers, minor mergers and gas-poor companions  
  > "are therefore similarly insensitive to late-stage mergers (where the components have already coalesced to sub-arcsec separations), minor-mergers, or the interactions with a gas-poor companion" (4.3)
- Limitation (authors): Targeted fields more sensitive to line-of-sight than sky-plane structure; small sample  
  > "our targeted observations are more sensitive to line-of-sight structure than that in the plane of the sky" (4.3)
- Caveat (inferred, ours): Only six fields and ~11 total blends; fractions have large errors
- Caveat (inferred, ours): Non-detections rely on assumed L'CO-L_IR relation, and ALESS 71.3 has weak limit
- Caveat (inferred, ours): Serendipitous lines assumed CO(3-2) without confirmation
- Caveat (inferred, ours): Lyman-alpha redshifts offsets may affect pair velocities

## Reproducibility

- Data public (paper): Raw and pipeline-processed data available from ALMA Science Archive  
  > "The raw and pipeline-processed data used in this paper are available from the ALMA Science Archive" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Exact line-free channel ranges and clean parameters
- Missing: L_IR values and error propagation for fractions
- Missing: Companion literature pair selection details and halo-mass curves
- Data volume (inferred): ~tens of GB (six Band 3 pointings, short integrations)
- Score (inferred): 3/5, Data public and pipeline-based, simple recipe, but many imaging details and statistics unspecified and results mostly detection counts.
- Rediscovery candidate: no, Main results are counts and fractions relying on literature pairs and loosely specified statistics.

## Links

- Method: (cite: Lokas01) (NFW pair velocity formalism)
- Method: (cite: Markwardt09) (mpfit)
- Companion: Wardlow et al. in prep. (detailed analysis of individual galaxies)
- Companion: (cite: Hodge13) (ALESS 870-um ALMA catalogue)
- Companion: (cite: Simpson15b) (AS2UDS pilot ALMA catalogue)
- Companion: (cite: Danielson17) (spectroscopic redshifts of ALESS SMGs)
- Companion: (cite: Hayward18) (spectroscopy of submillimetre multiples)
- Related: ALESS
- Related: AS2UDS
- Related: LESS
- Related: S2CLS-UDS
- Related: ASPECS

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 60,
  "rate": 0.698
 },
 "evidence_ok": true
}
```
