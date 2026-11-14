# Fragmentation properties of massive protocluster gas clumps: an ALMA study

`2018A&A...615A..94F` | Astronomy and Astrophysics 2018 | first author: Fontani, F. | arXiv: 1804.02429 | DOI: 10.1051/0004-6361/201832672

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What regulates fragmentation (magnetic field vs turbulence) in massive, young protocluster clumps, as probed by the fragment population in 278 GHz continuum and compared with MHD simulations?  
  > "in order to better understand the dominant ingredient regulating the fragmentation process in collapsing massive dense clumps in very early stages of evolution." (Introduction)
- Target **11 MSX-dark clumps (e.g. 16061–5048c1, 15470–5419c3, 16482–4443c2)**: coordinates e.g. 16061–5048c1: 16:10:06.61;–50:50:29 (J2000); others in Table 1  
  > "| 16061–5048c1$^{(f)}$ | 16:10:06.61;–50:50:29 | 332.06;0.08 | 3.6 | 28.1 |" (Table 1); "Clump coordinates, distances, and main physical properties of the 11 selected clumps are summarised in Table" (Source sample); z/distance 2.4–4.4 kpc (e.g. 3.6 kpc for 16061–5048c1)  
  > "| 16061–5048c1$^{(f)}$ | 16:10:06.61;–50:50:29 | 332.06;0.08 | 3.6 | 28.1 |" (Table 1); "Clump coordinates, distances, and main physical properties of the 11 selected clumps are summarised in Table" (Source sample); distance from Beltrán et al. 2006  
  > "| 16061–5048c1$^{(f)}$ | 16:10:06.61;–50:50:29 | 332.06;0.08 | 3.6 | 28.1 |" (Table 1); "Clump coordinates, distances, and main physical properties of the 11 selected clumps are summarised in Table" (Source sample)

## Data provenance

- ALMA projects: 2012.1.00366.S
- bands: _not stated_
- frequencies and spectral setup: ~278 GHz continuum  
  > "Observations with the ALMA array at a frequency of $\sim 278$ GHz were performed during cycle-2 and 3" (3 Observations)
- continuum bandwidth: ~1.7 GHz  
  > "The total bandwidth used is $\sim 1.7$ GHz." (3 Observations)
- arrays: _not stated_
- configurations: C36-6, baselines up to 1091 m  
  > "in configuration C36-6 with baselines up to 1091 m" (3 Observations)
- baselines: _not stated_
- angular resolution: 0.25 arcsec  
  > "providing an angular resolution of $0.25\ensuremath{''}$, and a maximum recoverable scale of $3.5\ensuremath{''}$" (3 Observations)
- max recoverable scale: 3.5 arcsec  
  > "providing an angular resolution of $0.25\ensuremath{''}$, and a maximum recoverable scale of $3.5\ensuremath{''}$" (3 Observations)
- sensitivity: unresolved fragments ≳0.05–0.1 Msun  
  > "We are sensitive to unresolved fragments of $\gtrsim 0.05 - 0.1$ $M_\odot$." (3 Observations)
- time on source: ~18–20 minutes per source  
  > "The total integration time on each source was $\sim 18 - 20$ minutes." (3 Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **SEST/SIMBA 1.2 mm**: Single-dish continuum used for missing-flux estimate and clump properties  
  > "comparing the total integrated flux in the primary beam of the ALMA images with the single-dish continuum measured by Beltrán et al. ((cite: beltran2006))" (3 Observations)
- Other facility **ATLASGAL 870 um**: Single-dish emission peaks to check SIMBA pointing  
  > "comparing the ALMA maps with the ATLASGAL images (Schuller et al. (cite: schuller2009)) at $\sim 870$ $\mu$m" (4.1)
- Other facility **Spitzer 24 um**: Identification of embedded infrared sources  
  > "The 1.2 mm continuum maps of all clumps are shown in Fig. [1](#fig_simba), superimposed on the Spitzer 24 $\mu$m images." (2 Source sample)
- Other facility **APEX**: N2H+(3-2) detection and C18O(3-2) depletion/line widths  
  > "detection in the high-density gas tracer N$_{2}$H$^{+}$ (3–2) with APEX (Fontani et al. (cite: fontani2012))" (2 Source sample)
- External data: Clump distances and sizes  
  > "$^{(a)}$ from Beltrán et al. ((cite: beltran2006));" (Table 1) [from Beltrán et al. 2006 (cite: beltran2006)]
- External data: Gas mass, Tk, N(H2), Sigma(H2)  
  > "$^{(b)}$ from Giannetti et al. ((cite: giannetti));" (Table 1) [from Giannetti et al. 2013 (cite: giannetti)]
- External data: CO depletion factors and C18O line widths  
  > "$^{(c)}$ from Fontani et al. ((cite: fontani2012));" (Table 1) [from Fontani et al. 2012 (cite: fontani2012)]
- External data: Fragment properties of 16061–5048c1  
  > "We also refer to the same paper for the properties of the fragments identified in 16061–5048c1" (4.2) [from Fontani et al. 2016 (cite: fontani2016)]
- Simulation/model as data: RAMSES MHD collapse simulations (100 and 300 Msun, mu=2 vs 130/200, T=10/20 K, Mach 3/6.4), post-processed with RADMC-3D and CASA simulator at 3.6 kpc, stopped at SFE 15%  
  > "These maps have then been post-processed through the CASA simulator to obtain synthetic images with the same observational conditions as the real observations" (5.2)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Ceres (bandpass J1427–4206, phase J1617–5848)  
  > "The absolute flux scale was set through observations of Titan and Ceres." (3 Observations)
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
- continuum subtraction: Continuum from averaging line-free channels  
  > "Continuum was extracted by averaging in frequency the line-free channels." (3 Observations)
- line free channels: _not stated_
- primary beam correction: applied always  
  > "Primary beam correction was always applied" (3 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Fragment flux, diameter and mass computation (Eq. A1, Sect. A.1), gas-to-dust 100 and dust opacity index  
  > "we adopt the same approach as in Fontani et al. ((cite: fontani2016)), hence we give in the following a brief description of the methods adopted" (4.2) [from Fontani et al. 2016 (cite: fontani2016)]
- Simulation setup and synthetic-image post-processing  
  > "We have post-processed the simulations as made in Fontani et al. ((cite: fontani2016))." (5.2) [from Fontani et al. 2016 (cite: fontani2016); Commerçon et al. 2011/2012]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Weighting/robust, cell and image size, deconvolver and masks
- Line-free channels and spectral setup
- Dust opacity law value and frequency scaling (only referenced to Fontani 2016)
- Noise rms per map
- Self-calibration usage
- Exact GILDAS MAPPING procedure for fragment flux integration

## Analysis recipe

1. **Image continuum**: Calibrate and image in CASA; continuum from line-free channels; primary-beam corrected  
  > "Calibration and imaging were performed with the CASA[^1] software (McMullin et al. 2007)." (3 Observations)
   - software: CASA, GILDAS MAPPING
   - fitting: _not stated_
   - validation: Missing flux estimated vs SIMBA single-dish  
  > "We estimated the missing flux by comparing the total integrated flux in the primary beam of the ALMA images with the single-dish continuum" (3 Observations)
2. **Identify fragments**: By eye: peak >5 sigma; overlapping fragments resolved if separate at half peak; fragments outside primary beam need ≥10 sigma  
  > "(1) peak intensity greater than 5 times the noise level; (2) two partially overlapping fragments are considered as resolved if they are separate at their half peak intensity level." (4 Results)
   - fitting: _not stated_
   - validation: By-eye chosen over Clumpfind due to parameter sensitivity  
  > "because small changes in their input parameters could lead to big changes in the number of identified clumps" (4 Results)
3. **Derive fragment flux, diameter and mass**: Integrate flux within 3 sigma polygon; D = equivalent-circle diameter; mass via Eq. A1 of Fontani 2016  
  > "$F_{\nu}$ has been computed by integrating the flux density inside the white polygon depicted in Figs. [12](#fig_map_08477)$-$[18](#fig_map_16573), which corresponds to the 3$\sigma$ rms level of the map." (4.2)
   - software: GILDAS MAPPING
   - assumption: Dust temperature = clump mean gas temperature; gas-to-dust 100; opacity as in Fontani 2016  
  > "we have assumed the same gas-to-dust ratio (100) and the same expression for the dust mass opacity index as in Fontani et al." (4.1)
   - fitting: _not stated_
   - validation: Mass uncertainty up to factor 2-3 from opacity  
  > "which can be up to a factor 2-3" (4.1)
4. **Correlate fragment and clump properties**: Compare number, masses, separations with clump T, mass, sigma_nth, Mach number, SFE  
  > "We have searched for possible relations between the properties of the fragment population in Table [\[tab_averages\]](#tab_averages), and the physical parameters of the parent clumps" (5.1)
   - fitting: _not stated_
   - validation: Only qualitative; authors note need for higher statistics  
  > "all the conclusions drawn in this Section should be corroborated by a higher statistics" (5.1)
5. **Compare with MHD simulations**: RAMSES runs with mu=2 and 200 (130), converted via RADMC-3D to dust continuum, CASA-simulated, same fragment criteria  
  > "we have calculated the properties of the fragments using the same criteria adopted for the real images" (5.3)
   - software: RAMSES, RADMC-3D, CASA
   - assumption: Distance 3.6 kpc; spherical clump with density contrast 10; stopped at SFE 15%  
  > "we have decided to analyse the simulations stopped at a SFE of $15\%$" (5.2)
   - fitting: _not stated_
   - validation: Qualitative morphology comparison  
  > "our main aim is to compare the overall morphology of the real and synthetic images" (5.2)

## Software

- **CASA** : Calibration and imaging; synthetic observations  
  > "Calibration and imaging were performed with the CASA[^1] software (McMullin et al. 2007)." (3 Observations)
- **GILDAS MAPPING** : Analysis of final images  
  > "the final images were analysed following standard procedures with the software MAPPING of the GILDAS[^2] package" (3 Observations)
- **RAMSES** : 3D MHD collapse simulations  
  > "through 3D numerical simulations adapted from Commerçon et al. ((cite: commercon2011)) using the RAMSES code" (5.2)
- **RADMC-3D** : Convert simulations to dust continuum flux maps  
  > "using the RADMC-3D radiative transfer code (Dullemond et al. (cite: dullemond2012))" (5.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of clumps with detected fragments | 8 of 11 | not stated | clumps | 2 | We have detected fragments in eight out of the 11 targets observed, and found at least four significant fragments in all of the eight clumps |
| Fragments per clump | 4 to 14 | not stated | fragments | 2 | The number of fragments detected ranges from a minimum of four to a maximum of 14 fragments. |
| Total fragment mass range | ~4 to ~53 | not stated | Msun | 3 | the total mass in the fragments is in between $\sim 53$ $M_\odot$ towards 16061–5048c1 and $\sim 4$$M_\odot$ in 08477–4359c1 |
| Most massive fragment (16482–4443c2) | ~14 | not stated | Msun | 3 | the most massive fragment is of $\sim 14$ $M_\odot$ towards 16482–4443c2 |
| Missing flux 15470–5419c1 | 98% | not stated | percent | 1 | the missing flux is huge ($98\%$ in 15470–5419c1, and $90\%$ in 16061–5048c4 |

## Qualitative findings

- Warmer and more massive clumps tend to have more fragments; no clear correlations otherwise  
  > "overall, there are no clear (anti-)correlations, although the sources with the largest temperature and mass tend to have more fragments." (5.1)
- Simulations with M~3 give no fragmentation; fragmentation needs high turbulence; mu=2 yields fewer, more massive fragments  
  > "(1) the $\mu=2$ case produces fewer and more massive fragments; (2) more than 1 fragment is possible only if the turbulence is higher" (5.3)

## Claim tuples

- H: Magnetic support dominates fragmentation in young massive clumps | E: Compare ALMA fragment morphology/number with RAMSES mu=2 vs mu=200 synthetic images | R: Filamentary morphology only in strong-field runs; other sources irregular and consistent with weaker field or interplay | F: Filamentary multi-fragment clumps require dominant magnetic field; others allow turbulence-magnetic interplay | **partially**
- H: Clump properties determine fragment population | E: Correlate fragment number/mass/separation with clump parameters | R: No clear relations; tentative trends with mass and temperature | F: Weak tentative trends only | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fragments identified by eye rather than algorithms  
  > "We decided to use these criteria and decompose the map into cores by eye instead of using decomposition algorithms" (4 Results)
- Alternative: Clumpfind-like decomposition rejected  
  > "small changes in their input parameters could lead to big changes in the number of identified clumps" (4 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Fragment numbers are lower limits due to large missing flux and pointing offsets  
  > "The number of fragments is likely a lower limit given the huge amount of missing flux in most of the sources." (Conclusions)
- Limitation (authors): Mass estimates are likely upper limits for warm fragments; simulations use single spherical clumps  
  > "In these cases, our mass estimates are likely upper limits." (4.1)
- Caveat (inferred, ours): Small sample of 8 detections; no statistical tests for correlations
- Caveat (inferred, ours): Single-configuration data lose most extended flux
- Caveat (inferred, ours): Simulations are not tailored to each clump

## Reproducibility

- Data public (paper): ALMA project 2012.1.00366.S cited in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA.2012.1.00366.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: Opacity law details (in Fontani 2016)
- Missing: Simulation outputs
- Data volume (inferred): ~50-100 GB raw for 11 fields
- Score (inferred): 4/5, Data public and fragment tables given, but imaging parameters and mass formula are not stated and fragment identification is by eye.
- Rediscovery candidate: no, Imaging settings are missing and fragment extraction is subjective, so the results are hard to redo exactly.

## Links

- Method: Fontani et al. 2016 (cite: fontani2016) (Fragment property derivation and simulation procedures)
- Companion: Fontani et al. 2016 (cite: fontani2016) (First source of the survey, 16061–5048c1)
- Related: SIMBA/SEST MSX-dark clump sample
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 80,
  "stated": 48,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
