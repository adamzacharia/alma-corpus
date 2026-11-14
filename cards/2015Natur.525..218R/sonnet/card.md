# Dense cloud cores revealed by CO in the low metallicity dwarf galaxy WLM

`2015Natur.525..218R` | Nature 2015 | first author: Rubio, Monica | arXiv: 1603.04736 | DOI: 10.1038/nature14901

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: Does CO exist in dense, self-gravitating cloud cores in the very low metallicity dwarf galaxy WLM, and what are their sizes, masses and densities compared to Milky Way CO clouds?  
  > "we report interferometric observations of CO clouds in the local group dwarf irregular galaxy Wolf-Lundmark-Melotte (WLM)" (abstract)
- Target **WLM (NW and SE regions)**: coordinates not stated (cloud positions near RA 00 01 57 to 00 02 02, Dec -15 27 in Table 1)  
  > "WLM is an isolated dwarf galaxy at a distance of $985\pm33$ kpc(cite: leaman12)." (main text); z/distance 985±33 kpc  
  > "WLM is an isolated dwarf galaxy at a distance of $985\pm33$ kpc(cite: leaman12)." (main text); distance from Leaman et al. 2012  
  > "WLM is an isolated dwarf galaxy at a distance of $985\pm33$ kpc(cite: leaman12)." (main text)

## Data provenance

- ALMA projects: 2012.1.00208.S
- bands: CO(1-0) receivers (Cycle 1)  
  > "The ALMA receivers were tuned to the ground rotational transition of Carbon Monoxide, CO(1-0)." (ALMA Observations)
- frequencies and spectral setup: 122 kHz per channel (0.32 km/s), 468.750 MHz bandwidth per baseband  
  > "The observations were done with a spectral resolution of 122 kHz per channel (0.32 km s$^{-1}$) and total bandwidth of 468.750 MHz per baseband." (ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-2/C32-3  
  > "The interferometer configuration C32-2/C32-3 provides a maximum baseline of 0.442 km." (ALMA Observations)
- baselines: maximum 0.442 km  
  > "The interferometer configuration C32-2/C32-3 provides a maximum baseline of 0.442 km." (ALMA Observations)
- angular resolution: 6.2x4.3 pc spatial resolution (HPBW)  
  > "The ALMA maps with $6.2\times4.3$ pc spatial resolution (HPBW), 5 mJy sensitivity, and 0.5 km s$^{-1}$ velocity resolution (FWHM)" (main text)
- max recoverable scale: 15"  
  > "The maximum angular scale for recovered emission was estimated to be 15”." (ALMA Observations)
- sensitivity: 5 mJy  
  > "5 mJy sensitivity, and 0.5 km s$^{-1}$ velocity resolution (FWHM)" (main text)
- time on source: _not stated_
- observing dates: 2013 July 8 and 2014 April 3  
  > "Observations were carried out on 2013 July 8 and 2014 April 3." (ALMA Observations)
- pi or archival as stated: Own proposal; DAH was PI  
  > "DAH, Principle Investigator of the ALMA proposal" (Author contributions)
- Line: 12CO J=1-0 (not stated)
- Other facility **APEX**: Earlier CO(3-2) detections used for comparison of total flux  
  > "we previously searched for CO(3-2) in WLM using the APEX telescope (cite: elmegreen13)" (main text)
- Other facility **Herschel**: [CII] 158 micron image of SE region  
  > "A \[CII\]$\lambda$158 $\mu$m image from the *Herschel* Space Observatory(cite: pilbratt10) is superposed on the Southeast region" (main text)
- External data: Dust-derived H2 and HI column densities for NW region; alpha_CO ~124±60  
  > "For the NW region(cite: elmegreen13), $\Sigma_{\rm H2}=31\pm15\;M_\odot$ pc$^{-2}$." (main text) [from Elmegreen et al. 2013 (cite: elmegreen13)]
- External data: Distance 985±33 kpc  
  > "WLM is an isolated dwarf galaxy at a distance of $985\pm33$ kpc(cite: leaman12)." (main text) [from (cite: leaman12)]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; originally calibrated data delivered by ALMA used, then re-imaged  
  > "MR re-processed the ALMA results from the originally calibrated data delivered by ALMA" (Author contributions)
- casa version: CASA 4.2.1  
  > "The data were calibrated, mapped, and cleaned using the ALMA reduction software CASA (version 4.2.1)." (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (flux); J2258–2758 bandpass; J2357–1125 gain  
  > "To set the absolute flux scale, Uranus was observed." (ALMA Observations)
- flux scale uncertainty: 10%  
  > "We estimated an uncertainty in absolute calibration of 10%." (ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using a better definition for masking of regions containing emission, and natural weighting to optimize sensitivity." (ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: improved mask definition around emission  
  > "using a better definition for masking of regions containing emission" (ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: convolved to 1.25"x1.25" for source identification  
  > "we convolved the image cube to a 1.25” $\times$1.25” beam" (Identifying sources)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Conversion of CO luminosity to mass and APEX flux/H2 data from previous work  
  > "The virial mass gives some perspective on the conversion from CO luminosity to mass derived previously(cite: elmegreen13)" (main text) [from (cite: elmegreen13)]

### Not stated but needed to reproduce (our reading)

- Task parameters for tclean/clean (cell size, image size, niter, threshold, mask definition)
- Final synthesized beam in arcsec and rms in Jy/beam per channel
- Continuum subtraction and line-free channels
- Rest frequency and Hanning smoothing/rebinning details
- Deconvolution procedure for sizes and linewidths (beam quadratic subtraction details)
- Pointing centres and number of execution blocks
- Details of Herschel [CII] reduction

## Analysis recipe

1. **Re-image cubes**: Redid cleaning with better masks and natural weighting from ALMA-calibrated data  
  > "we redid the cleaning (i.e., Fourier transform and beam deconvolution) using a better definition for masking of regions containing emission" (ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify candidate CO sources**: Visual search in 1.25" smoothed cube for knots coherent over at least three channels; confidence ranking  
  > "expecting coherence over at least three channels due to the Hanning-smoothing that had been applied." (Identifying sources)
   - fitting: _not stated_
   - validation: Inspected spectra and velocity-position maps; 10 of 20 NW candidates confirmed  
  > "we confirmed 10 CO clouds of the original 20 candidates." (Identifying sources)
3. **Extract spectra and measure sizes**: Moment maps over velocity ranges; spectra integrated within 2σ contour for sources ≥3σ; radius R=(A/π)^0.5 with beam-area quadratic deconvolution  
  > "a spectrum was obtained integrating over an area delineated by a contour drawn at $2\sigma$" (Identifying sources); "with $A$ determined after deconvolution by quadratic difference with the beam area." (main text)
   - fitting: Gaussian linewidths corrected for instrumental broadening  
  > "The linewidths were corrected for instrumental spectral broadening." (main text)
   - validation: Compared total ALMA flux with APEX  
  > "The sum of all the line emission measured by ALMA is within a factor of 2 of the total emission found at $18^{\prime\prime}$ resolution by the APEX telescope." (main text)
4. **Derive virial masses and CO luminosities**: M_vir=1044 R σ^2; L_CO=2453 S ΔV D^2  
  > "$M_{\rm vir}(M_\odot) =  1044 R \sigma^{2}$ for $R$ in pc and Gaussian linewidths $\sigma$ in km s$^{-1}$." (main text)
   - assumption: Distance 985 kpc  
  > "distance of $985\pm33$ kpc" (main text)
   - fitting: _not stated_
   - validation: Compared with scaling relations of other galaxies (Figure 3)  
  > "The CO clouds in WLM satisfy the usual correlations" (main text)
5. **Estimate densities, pressure and column density**: Virial density, pressure equilibrium with HI+H2 layers, and Av thresholds scaled to 13% metallicity  
  > "The corresponding pressure from self-gravity is $(\pi/2)G\Sigma_{\rm total}^2\sim1.6\times10^{-11}$ dynes." (main text)
   - assumption: Thermal CO(1-0)/CO(3-2) ratio of 1 for APEX comparison  
  > "assumed a thermal CO(1-0)/ CO(3-2) line ratio of 1" (Identifying sources)
   - fitting: _not stated_
   - validation: Three density estimates agree near 10^3 cm^-3  
  > "Thus the virial density, excitation density, and pressure equilibrium density are all about $10^3$ cm$^{-3}$." (main text)

## Software

- **CASA** 4.2.1: Calibration, imaging, cleaning  
  > "The data were calibrated, mapped, and cleaned using the ALMA reduction software CASA (version 4.2.1)." (ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO clouds | 10 | not stated | dimensionless | 2 | contain 10 CO clouds with an average radius of 2 parsecs and an average virial mass of $2\times10^3\;M_\odot$ |
| Cloud radius range | 1.5 to 6 | not stated | pc | 3 | The radii $R$ range from 1.5 to 6 pc |
| alpha_CO from virial masses | 28 | ±28 | Msun pc^-2 (K km/s)^-1 | 4 | the mean ratio is $\alpha_{\rm vir}\sim28\pm28\;M_\odot\;{\rm pc}^{-2}\left( \rm{K \;km\; s}^{-1}\right)^{-1}$ |
| Virial density | 4.1e-21 | not stated | g cm^-3 | 5 | $n(H_2) = 4.1\times10^{-21}$ g cm$^{-3}$ ($\sim10^3$ cm$^{-3}$) |
| Pressure-equilibrium density | 1.9e-21 | not stated | g cm^-3 | 5 | the equilibrium core density, $1.9\times10^{-21}$ g cm$^{-3}$, corresponding to $500$ H$_2$ cm$^{-3}$ |
| ALMA vs APEX flux, NW | 0.14 vs 0.66 | not stated | Jy | 3 | For WLM-NW we measured an ALMA flux of 0.14 Jy while the APEX flux converted to CO(1-0) is 0.66 Jy. |

## Qualitative findings

- WLM CO clouds are the smallest seen in any galaxy but follow standard scaling relations  
  > "The CO clouds in WLM satisfy the usual correlations although they are the smallest seen for any of these galaxies." (main text)

## Claim tuples

- H: CO clouds in WLM are dense cores with normal Milky Way-like properties | E: ALMA CO(1-0) mapping, virial analysis, pressure and column density estimates | R: Radii 1.5-6 pc, virial masses ~2e3 Msun, densities ~1e3 cm^-3 | F: Clouds are normal in density, pressure and column density and marginally self-bound | **supported**
- H: The small CO cloud mass explains the lack of massive clusters in dwarfs | E: Compared cloud masses to cluster properties | R: CO cores are small | F: Lack of massive clusters could have a physical origin, e.g. lack of massive CO clouds | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Re-imaged with natural weighting and better masks for sensitivity  
  > "natural weighting to optimize sensitivity" (ALMA Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): NW ALMA flux is lower than APEX; may reflect different line ratio, weak emission or resolved-out extended emission  
  > "it could be from emission that is larger in angular extent than the largest structures measured by the interferometer" (Identifying sources)
- Caveat (inferred, ours): Source identification is visual and subjective; half of NW candidates rejected
- Caveat (inferred, ours): Large size uncertainties (~50%) near the beam limit
- Caveat (inferred, ours): Virial masses assume bound clouds and no external pressure
- Caveat (inferred, ours): Many methods details (clean parameters) missing

## Reproducibility

- Data public (paper): ALMA project data acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00208.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters, masks, beam and rms values
- Missing: Exact source-extraction thresholds and deconvolution procedure
- Data volume (inferred): ~10-30 GB raw for two Cycle 1 fields
- Score (inferred): 3/5, Data are identifiable and results are tabulated, but imaging parameters and the visual source selection are underspecified.
- Rediscovery candidate: no, Source identification is subjective and imaging settings are missing.

## Links

- Companion: Elmegreen et al. 2013 (cite: elmegreen13) (Earlier APEX CO(3-2) detection and dust-derived H2 columns)
- Related: LITTLE THINGS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 42,
  "rate": 0.618
 },
 "evidence_ok": true
}
```
