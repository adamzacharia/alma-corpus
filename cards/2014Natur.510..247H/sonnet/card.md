# Two γ-ray bursts from dusty regions with little molecular gas

`2014Natur.510..247H` | Nature 2014 | first author: Hatsukade, B. | arXiv: 1406.3071 | DOI: 10.1038/nature13325

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, high_z_galaxies
- Question: Do GRB host galaxies with high SFR and metallicity contain molecular gas (CO) and dust at the burst sites, and what are the molecular gas-to-dust ratios?  
  > "Here we report spatially resolved observations of CO line emission and" (abstract)
- Target **GRB 020819B host**: coordinates _not stated_; z/distance z = 0.41  
  > "GRB 020819B at a redshift of z = 0.41" (Methods); distance from CO line redshift (z=0.410)  
  > "GRB 020819B at a redshift of z = 0.41" (Methods)
- Target **GRB 051022 host**: coordinates _not stated_; z/distance z = 0.806  
  > "A Gaussian fit to the emission line gives a redshift of z = 0.806" (Figure 2 caption); distance from CO line redshift  
  > "A Gaussian fit to the emission line gives a redshift of z = 0.806" (Figure 2 caption)

## Data provenance

- ALMA projects: 2011.0.00232.S
- bands: Band 6 (1.2 mm), Cycle 0  
  > "We conducted ALMA band-6 observations of the GRB" (Methods)
- frequencies and spectral setup: CO(3-2) at 245.072 GHz and CO(4-3) at 255.142 GHz; 1,875 MHz per baseband (488.28 kHz x 3,840 channels), four basebands, 7.5 GHz total  
  > "The correlator was used in the frequency domain mode with a bandwidth of 1,875 MHz (488.28 kHz × 3,840 channels). Four basebands were used, giving a total" (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-402 m (GRB 020819B), 15-382 m (GRB 051022)  
  > "The range of baseline lengths of the configuration is 15-402 m and 15-382 m" (Methods)
- angular resolution: _not stated_
- max recoverable scale: 10"  
  > "for the array configurations is 10", which is large enough to cover the" (Methods)
- sensitivity: _not stated_
- time on source: 47 min (GRB 020819B), 71 min (GRB 051022)  
  > "The on-source time is 47 min and 71 min for the GRB 020819B host and the GRB 051022" (Methods)
- observing dates: 2012 Nov 17 (GRB 020819B); 2012 Nov 21 and Dec 2 (GRB 051022)  
  > "in 2012 November 17 with 27 antennas and the GRB 051022 host in 2012 November" (Methods)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (redshifted observed at 245.072 GHz)
- Line: CO J=4-3 (redshifted observed at 255.142 GHz)
- Other facility **Herschel PACS**: 100, 160, 250 micron photometry for dust SED  
  > "We used the Herschel/Photodetector Array Camera and Spectrometer (PACS) [37] data in the archive." (Methods)
- Other facility **Gemini North/South**: Optical R-band images  
  > "Optical R -band image obtained with the Gemini North" (Figure 1 caption)
- External data: Herschel 100, 160, 250 um photometry used in SED fit  
  > "Herschel 100-μm, 160-μm, and 250-μm (ref. 9)" (Methods) [from Hunt et al. 2014 (ref 9)]
- External data: Radio 3 cm and 6 cm upper limits  
  > "the 3σ upper limits of S 3cm < 138 μJy and S 6cm < 33 μJy (ref. 45)" (Supplementary Information) [from Stanway et al. 2010 (ref 45)]

## Processing

### Calibration

- pipeline or manual: CASA, 'in a standard manner'  
  > "package in a standard manner." (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (flux); J2253+161 (3C454.3) for bandpass and phase  
  > "Uranus was observed as a flux calibrator and a quasar J2253+161 (3C454.3) was observed for bandpass and phase" (Methods)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN algorithm  
  > "The maps were processed with the CLEAN algorithm with Briggs" (Methods)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "weighting (with robust parameter of 0.5)" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum map from ~7.5 GHz excluding line channels  
  > "continuum maps were created with a total bandwidth of ~7.5 GHz, excluding channels with emission" (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: CO(3-2) 0.040 Jy/beam km/s; continuum 0.030 mJy/beam; CO(4-3) 0.037 Jy/beam km/s; continuum 0.032 mJy/beam  
  > "Contours start from ±3σ with 1σ step (1σ = 0.030 mJy beam [-1] )." (Figure 1 caption)

### Not stated but needed to reproduce (our reading)

- CASA version
- Line-free channels and CLEAN masks, cell and image size, iteration threshold
- Velocity range used to integrate CO
- Flux calibration accuracy
- Photometry apertures or fitting for ALMA sources
- SED fitting method, priors and Herschel flux values
- Whether archive-delivered calibration was used

## Analysis recipe

1. **Image CO and continuum**: CASA reduction, CLEAN with Briggs weighting; continuum from line-free channels; CO velocity-integrated maps  
  > "The maps were processed with the CLEAN algorithm with Briggs" (Methods)
   - software: CASA
   - parameter: robust = 0.5  
  > "weighting (with robust parameter of 0.5)" (Methods)
   - fitting: Gaussian fit to CO spectrum and map  
  > "A Gaussian fit to the emission line gives a redshift of z = 0.410" (Figure 2 caption)
   - validation: _not stated_
2. **Derive molecular gas mass**: L'CO from S dv, nu_obs, D_L; convert to CO(1-0) with M82 ratios; Mgas = alpha_CO L'CO(1-0)  
  > "Molecular gas" (Methods: Molecular Gas Mass)
   - assumption: CO(3-2)/CO(1-0)=0.93, CO(4-3)/CO(1-0)=0.85 (M82); alpha_CO=4.3 Msun (K km/s pc2)^-1; cosmology H0=71, OmegaM=0.27, OmegaL=0.73  
  > "We assume a CO line ratio of CO(3–2)/CO(1–0) = 0.93 and CO(4–3)/CO(1–0) = 0.85" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit dust SED**: Single-temperature modified blackbody fit to Herschel 100/160/250 um and ALMA 1.2 mm  
  > "we fitted the far-infrared-millimetre photometry data of Herschel 100-μm, 160-μm, and 250-μm (ref. 9), and ALMA 1.2 mm with a single temperature modified blackbody form" (Methods: Modified blackbody fit)
   - software: SExtractor
   - fitting: _not stated_
   - validation: Compared to Tdust of previous SED study; missing ALMA flux at PACS scales negligible  
  > "We note that the missing flux in the ALMA observations in the scale of the" (Methods)
4. **Derive dust mass, LFIR, SFR, gas-to-dust ratio**: _not stated_
   - assumption: kappa_d proportional to nu^beta, kappa_d(125 um)=26.4 cm2/g  
  > "d (125 μm) = 26.4 cm [2] g [-1] (ref. 422)" (Methods)
   - fitting: _not stated_
   - validation: SFR compared with extinction-corrected UV/optical SFR  
  > "The SFRs are comparable to the" (abstract)

## Software

- **CASA** : ALMA data reduction and imaging  
  > "The data were reduced with the Common Astronomy Software Applications [31]" (Methods)
- **SExtractor** : Aperture photometry on Herschel 160 um image  
  > "160-μm image of the GRB 051022 host with SExtractor [38]" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mgas nuclear GRB 020819B host | 2.4e9 | 0.2e9 | Msun | 2 | (2.4 ± 0.2) |
| Mgas GRB 051022 host | 2.1e9 | 0.4e9 | Msun | 2 | The derived molecular gas masses are M gas = |
| Tdust GRB 020819B host | 28 | 3 | K | 3 | T dust = 28 ± 3 K and β = 1.9 ± 0.3 |
| Tdust GRB 051022 host | 34 | 6 | K | 3 | T dust = 34 ± 6 K and β = 1.8 ± 0.5 |
| Mdust GRB 020819B site | 4.8e7 | 1.0e7 | Msun | 4 | The derived dust mass is (4.8 ± 1.0) |
| Mgas/Mdust at GRB 020819B site | <9-14 | 3 sigma limit | dimensionless | 4 | M gas / M dust >51–60 <9–14 58–86 |
| SFR GRB 020819B site | 18 | 4 | Msun/yr | 4 | calculated to be 18 ± 4 |

## Qualitative findings

- CO is detected at the nucleus of the GRB 020819B host while 1.2 mm dust continuum is detected at the GRB site, ~3" (16 kpc) away; hosts lie closer to the starburst sequence  
  > "The bursts happened in regions rich in dust, but not particularly rich in molecular gas." (abstract)

## Claim tuples

- H: GRB sites are rich in molecular gas | E: ALMA CO and 1.2 mm continuum of two GRB hosts | R: Gas-to-dust ratio at GRB site <9-14 | F: GRB sites are dust-rich but gas-poor, lower than the Milky Way and nearby galaxies | **supported**
- H: The continuum is dust emission | E: Position match, radio upper limits | R: Positional offset 0.06"; chance coincidence ~3e-5 | F: Dust thermal emission from star formation | **supported**

## Reasoning

- Why this data: Hosts chosen for high SFR and metallicity to maximize CO and dust detection  
  > "to maximize the possibility of detecting the CO emission line and dust continuum emission." (Methods)
- Why this method: _not stated_
- Alternative: Background galaxy and synchrotron origins of continuum rejected  
  > "the upper limits reject the possibility that the 1.2-mm continuum emission is attributed to synchrotron" (Supplementary Information)
- How they decided it was enough: _not stated_
- Limitation (authors): GRB 051022 host is unresolved so site-vs-nucleus is uncertain  
  > "although the angular resolution is not good enough to be certain." (abstract)
- Caveat (inferred, ours): alpha_CO and M82 line ratios are assumed
- Caveat (inferred, ours): Only two targets; low S/N continuum (about 4.7 sigma)
- Caveat (inferred, ours): Dust temperature poorly constrained with few SED points

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited  
  > "ADS/JAO.ALMA#2011.0.00232.S" (Author Information)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Herschel photometry values
- Missing: Integration velocity ranges
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 3/5, Public Cycle 0 data and numeric results, but sparse imaging details and SED fitting specifics.
- Rediscovery candidate: yes, Public data, numeric results, formula-based derivations; some imaging details are missing.

## Links

- Companion: Hatsukade et al. 2011 (ref 4) (Earlier CO observations of a GRB host)
- Related: Herschel PACS archive

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
