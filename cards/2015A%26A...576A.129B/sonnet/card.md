# Antifreeze in the hot core of Orion. First detection of ethylene glycol in <ASTROBJ>Orion-KL</ASTROBJ>

`2015A&A...576A.129B` | Astronomy and Astrophysics 2015 | first author: Brouillet, N. | arXiv: 1502.03993 | DOI: 10.1051/0004-6361/201424588

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Is ethylene glycol (aGg' and gGg' conformers) detectable in Orion-KL hot core, and how do its abundance relative to methanol, ethanol and glycolaldehyde compare with Sgr B2 and comets?  
  > "In this paper, we report the results of our search for the two most stable conformers of ethylene glycol towards ." (Introduction)
- Target **Orion-KL (IRc2 region, Hot Core)**: coordinates RA 05h35m14.35s, Dec -05d22m35.0s (J2000, pointing centre)  
  > "The observations were centred on coordinates ($\alpha_{J2000}$ = 05$^{h}$35$^{m}$14$s$35, $\delta_{J2000}$ = $-$05$\ensuremath{^\circ}$22$\ensuremath{'}$35$\ensuremath{''}$00)" (2 Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6, 213.715-246.627 GHz  
  > "The observations were carried out with 16 x 12 m antennas in the Band 6 frequency range from 213.715 to 246.627 GHz." (2 Observations)
- frequencies and spectral setup: 20 overlapping spectral windows, 1.875 GHz each, 3840 channels, 0.488 MHz (0.64 km/s) spacing  
  > "20 slightly overlapping spectral windows were observed, each with a 1.875 GHz bandwidth and 3 840 channels resulting in a 0.488 MHz channel spacing" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 16 x 12 m antennas  
  > "The observations were carried out with 16 x 12 m antennas" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.90" x 1.40", PA 170 deg  
  > "The synthesized beam is 1.90$\ensuremath{''}$ $\times$ 1.40$\ensuremath{''}$ with a PA of 170$\ensuremath{^\circ}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 20 January 2012  
  > "taken on 20 January 2012 towards the IRc2 region in Orion" (2 Observations)
- pi or archival as stated: ALMA Science Verification data  
  > "We primarily use here the ALMA Science Verification (ALMA-SV) data" (2 Observations)
- Line: ethylene glycol aGg' conformer e.g. 23(2,22) v=1 - 22(2,21) v=0 (unblended) (228752.7765 MHz)
- Other facility **IRAM Plateau de Bure Interferometer**: Earlier interferometric data (Favre et al. 2011) used for comparison; blended lines discarded; continuum comparison  
  > "We also analyzed several observational data sets obtained with the IRAM Plateau de Bure Interferometer (cite: Favre:2011a)." (2 Observations)
- External data: CDMS spectroscopy for ethylene glycol conformers  
  > "We used the most recent CDMS data to search for transitions for the *aGg’* and *gGg’* conformers in the ALMA-SV data cube." (3.1) [from (cite: Muller:2001; Muller:2005)]
- External data: Column densities for Sgr B2, NGC 7129, comets used in comparison table  
  > "Table [\[comp-sgrB2\]](#comp-sgrB2) compares the column densities derived for ethylene glycol and related molecules towards , two other prominent interstellar sources and the 3 comets" (4.1) [from (cite: Crovisier:2004a; Biver:2014; Fuente:2014)]
- External data: Methanol column density 4.2e18 cm-2 at dM-1 (same position as MF2)  
  > "(cite: Peng:2012) derive a column density of $4.2\pm0.4\times10^{18}$ cm$^{-2}$ for the methanol peak named dM-1" (4.1) [from (cite: Peng:2012)]
- External data: Glycolaldehyde upper limit 3.5e14 cm-2 towards MF2  
  > "(cite: Favre:2011a) find an upper limit for the glycolaldehyde column density of 3.5 $\times$ 10$^{14}$ cm$^{-2}$ towards MF2" (4.1) [from (cite: Favre:2011a)]

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

- task: GILDAS line map cleaning with CLARK algorithm  
  > "The line maps were cleaned using the CLARK algorithm (cite: Clark:1980)." (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Subtraction of continuum built from carefully selected line-free channels  
  > "The continuum emission was subtracted in the maps by carefully selecting line-free channels (see Sect. [5](#sec:continuum))." (2 Observations)
- line free channels: Per 1000-channel sub-window, the two best line-free channels selected by max-min and pair-difference noise criteria  
  > "we have separated each one of the 20 spectral windows into four 1 000-channel sub-windows, and we have searched for line-free channels in each sub-window" (5 Continuum emission)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.90" x 1.40", PA 170 deg  
  > "The synthesized beam is 1.90$\ensuremath{''}$ $\times$ 1.40$\ensuremath{''}$ with a PA of 170$\ensuremath{^\circ}$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- N(H2) derived from the continuum map as in Favre et al. 2011  
  > "we derived the beam averaged projected density N$\rm_{H\rm_{2}}$ as in (cite: Favre:2011a)" (3.4) [from (cite: Favre:2011a)]
- Rotational diagram equation  
  > "we have estimated the rotational temperature and the column density of ethylene glycol using the equation (cite: Goldsmith:1999):" (3.4) [from (cite: Goldsmith:1999)]

### Not stated but needed to reproduce (our reading)

- CASA version and the initial processing/calibration steps
- Robust/weighting, cell and image size, and clean thresholds for GILDAS imaging
- Exact line-free channel lists and the continuum levels subtracted
- Integration windows and uncertainty treatment for rotational-diagram integrated intensities
- Treatment of beam dilution/source size in column density
- Method for deriving the H2 column density from continuum (dust temperature, opacity)

## Analysis recipe

1. **Process data and image**: Initial processing in CASA, visibilities exported to GILDAS, line maps cleaned with CLARK  
  > "We used the CASA software for initial processing, and then we exported visibilities to the GILDAS package for further analysis." (2 Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract continuum and make continuum cube**: Select line-free channel pairs per sub-window by channel max-min intensity and noise of pair difference; average best pair  
  > "Then we obtained the continuum map for a given sub-window by averaging the two channel maps of the best pair." (5 Continuum emission)
   - software: GILDAS
   - fitting: _not stated_
   - validation: Checked coherence of continuum maps of adjacent sub-windows; compared with PdBI  
  > "Finally, we checked the coherence of the continuum maps obtained for adjacent sub-windows." (5 Continuum emission)
3. **Identify ethylene glycol lines and spatial distribution**: Search CDMS aGg' and gGg' transitions predicted at 120 K; compare profiles and integrated maps of the least-blended lines  
  > "From line intensity predictions at 120 K, a typical temperature for the region (cite: Favre:2011a), we have examined the strongest lines among the ethylene glycol transitions" (3.1)
   - software: CDMS
   - fitting: Gaussian fit of normalized profiles: 7.6 km/s centre, 2.3 km/s width  
  > "They can be fitted with a Gaussian centred at a velocity of 7.6 km s$^{-1}$ and a line width of 2.3 km s$^{-1}$." (3.2)
   - validation: Snyder et al. criteria plus spatial coherence across transitions  
  > "For interferometric observations, another criterion can be added: the coherence of the spatial distribution." (3.3)
4. **Rotational diagram and column density**: Rotational diagram at emission peak from less-contaminated lines  
  > "The rotational diagram is obtained at the emission peak from the less-contaminated ethylene glycol lines to derive reliable physical parameters" (3.4)
   - parameter: Q(T) = 234 500 (CDMS at 145 K)  
  > "Taking the partition function *Q*(*T*) = 234 500 from the nonlinear plot of the CDMS values of *Q* at 145 K" (3.4)
   - assumption: Optically thin lines and LTE  
  > "Assuming optically thin lines and local thermodynamic equilibrium" (3.4)
   - fitting: _not stated_
   - validation: Synthetic spectrum overlaid on observed spectrum  
  > "Figure [6](#spesyn) shows the synthetic spectrum overlaid on the observed ALMA spectrum towards the ethylene glycol peak" (3.4)
5. **Upper limit for gGg' conformer**: Compare gGg' synthetic spectrum with observed spectrum at aGg' peak at 145 K and 250 K  
  > "we have also derived a synthetic spectrum at the *aGg’* peak for a temperature of 250 K" (3.5)
   - assumption: Same spatial distribution, temperature and partition function as aGg'  
  > "We have further assumed here that the partition functions of both conformers are identical" (3.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Initial processing  
  > "We used the CASA software[^3] for initial processing" (2 Observations)
- **GILDAS** : Further analysis, imaging, CLARK cleaning  
  > "then we exported visibilities to the GILDAS package[^4] for further analysis." (2 Observations)
- **Aladin** : Comparison of maps of other tracers  
  > "We compared the maps of these tracers using the Aladin software" (4.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Rotational temperature of aGg' | 145 | ±30 | K | 4 | we obtain a rotational temperature of 145$\pm$30 K |
| Column density of aGg' | 4.6e15 | ±0.8e15 | cm^-2 | 4 | total column density averaged over the synthesized beam *N*$\rm_{\textit{aGg'}}$ of 4.6$\pm$0.8 10$^{15}~$cm$^{-2}$ |
| gGg' column density upper limit (145 K) | 1e15 | not stated | cm^-2 | 5 | leads to a maximum column density of 10$^{15}~$cm$^{-2}$ |
| gGg' column density upper limit (250 K) | 2.3e15 | not stated | cm^-2 | 5 | We find a projected density upper limit of 2.3 10$^{15}~$cm$^{-2}$. |
| Deconvolved size upper limit | 2.4 x 1.1 | not stated | arcsec | 3 | We find an upper limit for the deconvolved size of 2.4$\ensuremath{''}$$\times$ 1.1$\ensuremath{''}$. |
| Ethylene glycol abundance relative to H2 | ~1e-9 | not stated | dimensionless | 4 | we find an ethylene glycol abundance of $\sim$10$^{-9}$ |
| Ethanol column density | ~2.5e16 | not stated | cm^-2 | 0 | we find a column density of $\sim$ 2.5 $\times$ 10$^{16}$ cm$^{-2}$ |

## Qualitative findings

- Ethylene glycol emission is compact, peaks ~2" SW of the main continuum peak and differs from other O-bearing species  
  > "The emission is compact and peaks towards the Hot Core close to the main continuum peak, about 2$\ensuremath{''}$ to the south-west" (abstract)

## Claim tuples

- H: Is aGg' ethylene glycol detected in Orion-KL? | E: Line search in ALMA-SV Band 6 cube with profile and map coherence | R: Many partially blended lines plus one unblended at 228752 MHz share peak position and profile | F: aGg' conformer detected | **supported**
- H: Is ethylene glycol relative to methanol similar to comets? | E: Compare column density ratios with Sgr B2, NGC 7129 and three comets | R: Ratio ~1e-3 vs 0.1-0.15 in comets | F: Interstellar abundance far below comets, outside the known correlation | **supported**
- H: Is gGg' conformer detected? | E: Synthetic spectra at 145 and 250 K | R: Only weak lines, strong ones blended | F: Not detected; N < 0.2 of aGg' | **supported**

## Reasoning

- Why this data: High spatial resolution reduces line confusion and wide bandwidth gives many transitions  
  > "Furthermore, a large spectral bandwidth is needed because many individual transitions are required to securely detect large organic molecules." (Summary (abstract))
- Why this method: _not stated_
- Alternative: PdBI lines discarded because of blending and different resolution  
  > "we have discarded these lines from the present analysis because of line blending problems" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Hypotheses for gGg' upper limit admittedly questionable; lines too few and weak to dispel confusion  
  > "Making the simplifying, but admittedly questionable, hypotheses" (3.5)
- Caveat (inferred, ours): Almost all lines blended; single unblended line, so LTE temperature rests on partially blended lines
- Caveat (inferred, ours): Uncertainties on N and T not described in detail
- Caveat (inferred, ours): No beam dilution/source size correction; calibration uncertainty not discussed
- Caveat (inferred, ours): Comparison across sources with different resolutions

## Reproducibility

- Data public (paper): ALMA Science Verification data available at a public URL  
  > "http://almascience.eso.org/almadata/sciver/OrionKLBand6/" (2 Observations (footnote 2))
- Products in archive: _not stated_
- Missing: CASA/calibration details
- Missing: Imaging parameters
- Missing: Line-free channel list
- Missing: Integrated intensities per line
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Public data and clear LTE method, but imaging, calibration and fitting details are sparse.
- Rediscovery candidate: no, Imaging recipe is incomplete and line blending requires judgement.

## Links

- Method: (cite: Favre:2011a) (Prior PdBI Orion-KL analysis; N(H2) method and source positions)
- Method: (cite: Goldsmith:1999) (Rotational diagram equation)
- Companion: (cite: Peng:2012) (Methanol and related ALMA/PdBI work on Orion-KL)
- Related: ALMA Science Verification Orion KL Band 6

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
