# The physical and chemical structure of Sagittarius B2. II. Continuum millimeter emission of Sgr B2(M) and Sgr B2(N) with ALMA

`2017A&A...604A...6S` | Astronomy and Astrophysics 2017 | first author: Sánchez-Monge, Á. | arXiv: 1704.01805 | DOI: 10.1051/0004-6361/201730426

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the physical and chemical structure of the high-mass star forming sites Sgr B2(M) and Sgr B2(N), as traced by 1.3 mm continuum sources at ~4000 au resolution?  
  > "We want to characterize the physical and chemical structure of the two high-mass star forming sites Sgr B2(M) and Sgr B2(N) using high-angular resolution observations at millimeter wavelengths, reaching spatial scales of about 4000 au." (abstract)
- Target **Sgr B2(M)**: coordinates phase center RA 17h47m20.157s, Dec -28d23m04.53s (J2000)  
  > "$\delta$(J2000)=$-28\ensuremath{^\circ}23\ensuremath{'}04.53\ensuremath{''}$ for Sgr B2(M)" (2 Observations); "It is located at a distance of $8.34\pm0.16$ kpc (cite: Reid2014)" (1 Introduction); z/distance 8.34 kpc  
  > "$\delta$(J2000)=$-28\ensuremath{^\circ}23\ensuremath{'}04.53\ensuremath{''}$ for Sgr B2(M)" (2 Observations); "It is located at a distance of $8.34\pm0.16$ kpc (cite: Reid2014)" (1 Introduction); distance from Reid et al. 2014  
  > "$\delta$(J2000)=$-28\ensuremath{^\circ}23\ensuremath{'}04.53\ensuremath{''}$ for Sgr B2(M)" (2 Observations); "It is located at a distance of $8.34\pm0.16$ kpc (cite: Reid2014)" (1 Introduction)
- Target **Sgr B2(N)**: coordinates phase center RA 17h47m19.887s, Dec -28d22m15.76s (J2000)  
  > "$\delta$(J2000)=$-28\ensuremath{^\circ}22\ensuremath{'}15.76\ensuremath{''}$ for Sgr B2(N)" (2 Observations); z/distance 8.34 kpc  
  > "$\delta$(J2000)=$-28\ensuremath{^\circ}22\ensuremath{'}15.76\ensuremath{''}$ for Sgr B2(N)" (2 Observations); distance from Reid et al. 2014  
  > "$\delta$(J2000)=$-28\ensuremath{^\circ}22\ensuremath{'}15.76\ensuremath{''}$ for Sgr B2(N)" (2 Observations)

## Data provenance

- ALMA projects: 2013.1.00332.S
- bands: Band 6, 211-275 GHz  
  > "covering the broad frequency range from 211 GHz to 275 GHz (ALMA band 6) with 10 different spectral tunings." (2 Observations)
- frequencies and spectral setup: spectral scan, 10 tunings, 4 spectral windows of 1875 MHz with 3840 channels each; 0.5-0.7 km/s resolution  
  > "the digital correlator was configured in four spectral windows of 1875 MHz and 3840 channels each (with dual polarization), providing a resolution of 0.5–0.7 km s$^{-1}$" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, 34-36 antennas  
  > "using 34–36 antennas in an extended configuration with baselines in the range from 30 m to 650 m" (2 Observations)
- baselines: 30 m to 650 m  
  > "baselines in the range from 30 m to 650 m" (2 Observations)
- angular resolution: 0.4'' (super-resolution) and 0.7'' (medium); native beam 0.39''-0.65''  
  > "final synthesized beams of $0.7\ensuremath{''}$ (medium resolution images) and $0.4\ensuremath{''}$ (super-resolution images)" (2 Observations)
- max recoverable scale: 0.4''-5''  
  > "results in a sensitivity to structures in the range 0.4$''$–5$''$" (2 Observations)
- sensitivity: 10-20 mJy/beam per channel; 8 mJy/beam continuum  
  > "has a rms noise level of 8 mJy beam$^{-1}$" (2 Observations)
- time on source: about 2.5 minutes per source and frequency  
  > "The on-source observing time per source and frequency is about 2.5 minutes." (2 Observations)
- observing dates: 2014 June and 2015 June (Cycle 2)  
  > "during Cycle 2 in 2014 June and 2015 June" (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **SMA 345 GHz**: 345 GHz fluxes and source catalogue for comparison  
  > "we have compared the ALMA continuum images with VLA and SMA continuum images at 40 GHz and 345 GHz respectively." (4.1 Origin of the continuum emission)
- Other facility **VLA 40 GHz**: 40 GHz fluxes used to estimate free-free contribution  
  > "The contamination of ionized gas emission at 1.3 mm is taken into account by using the fluxes at 40 GHz (cite: Rolffs2011)" (4.2 Physical properties)
- External data: VLA 40 GHz images/fluxes  
  > "The details of these observations can be found in (cite: Rolffs2011) and (cite: Qin2011)" (4.1 Origin of the continuum emission) [from Rolffs2011]
- External data: SMA 345 GHz images/fluxes  
  > "For completeness, we also list the flux at 40 GHz (cite: Rolffs2011) and the flux at 345 GHz (cite: Qin2011)" (4.1 Origin of the continuum emission) [from Qin2011]
- External data: 3D radiative transfer model of Sgr B2  
  > "(cite: Schmiedeke2016) used VLA 40 GHz data (cite: Rolffs2011) and SMA 345 GHz data (cite: Qin2011)" (4.4 Comparison with 3D-radiative transfer models) [from Schmiedeke2016]
- Simulation/model as data: 3D radiative transfer model of Sgr B2 from Paper I, post-processed to ALMA uv-sampling at 242 GHz  
  > "The synthetic images produced with the model are post-processed to the same uv-sampling of the ALMA observations" (4.4 Comparison with 3D-radiative transfer models)

## Processing

### Calibration

- pipeline or manual: CASA calibration; gains from nearby quasars; phases transferred from nearby spws for spws 12-15  
  > "For these spectral windows we transferred the phases derived from nearby (in frequency and in observing time) spectral windows." (2 Observations)
- casa version: CASA 4.4.0  
  > "The calibration and imaging were performed in CASA[^1] version 4.4.0." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (1.36 Jy at 228.265 GHz) and Titan  
  > "Flux calibration was obtained through observations of the bright quasar J1733$-$1304 (flux 1.36 Jy at 228.265 GHz, with spectral index $-0.71$) and the satellite Titan." (2 Observations)
- flux scale uncertainty: about 20%  
  > "The uncertainty in the flux calibration of the ALMA observations is also about 20%." (4.4 Comparison with 3D-radiative transfer models)
- self calibration: two phase-only iterations plus one amplitude+phase, using only bright (>500 mJy) components; self-calibrated images not used for continuum analysis  
  > "We applied two iterations of self-calibration in phase-mode only, and a last step in both amplitude and phase to correct the phases of the more noisy spectral windows" (2 Observations)

### Imaging

- task: CLEAN in CASA  
  > "Channel maps for each spectral window were created using the task CLEAN in CASA" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "with the robust parameter of (cite: Briggs1995) set equal to 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum level per pixel via STATCONT sigma-clipping (cSCM), alpha=2, per spectral window  
  > "the algorithm removes all the points that are smaller or larger than $\mu\pm\alpha\sigma$, where $\alpha$ is set to 2." (3.1 Continuum maps at 1.3 mm with ALMA)
- line free channels: _not stated_
- primary beam correction: applied to all images  
  > "All the images are corrected for the primary beam response of the ALMA antennas." (2 Observations)
- array combination: _not stated_
- smoothing: restored with Gaussian beams of 0.7'' and 0.4''  
  > "These images were restored with a Gaussian beam to have final synthesized beams of $0.7\ensuremath{''}$ (medium resolution images)" (2 Observations)
- final beam: _not stated_
- final rms: 8 mJy/beam continuum  
  > "has a rms noise level of 8 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Continuum determination procedure (STATCONT)  
  > "following the procedure described in Sánchez-Monge et al. (submitted, see also Sect. [3.1](#s:cont1mm))" (2 Observations) [from Sánchez-Monge et al. (submitted)]
- Ionized gas parameter expressions (ne, Mi, N_i)  
  > "We have used the expressions given in the Appendix C of (cite: Schmiedeke2016)" (4.2 Physical properties) [from Schmiedeke2016]
- Deconvolved size approach  
  > "We used the approach described in (cite: SanchezMonge2013a) to determine the effective observed full width at half maximum" (3.2 Source determination) [from SanchezMonge2013a]

### Not stated but needed to reproduce (our reading)

- STATCONT convergence tolerance value
- Clean threshold, masks, cell and image size
- Line-free channels / how lines were handled in STATCONT beyond sigma-clipping
- Self-calibration solution intervals
- Details of the 3D model and how synthetic images were generated
- Linear fit method for chemical-richness relations

## Analysis recipe

1. **Derive continuum maps per spectral window**: STATCONT cSCM sigma-clipping per pixel on each spw cube (40 maps), plus averaged maps  
  > "Each spectral window, corresponding to a bandwidth of 1.87 GHz, has been processed independently in order to produce 40 different continuum emission maps" (3.1 Continuum maps at 1.3 mm with ALMA)
   - software: STATCONT
   - parameter: alpha = 2 sigma clipping  
  > "where $\alpha$ is set to 2" (3.1 Continuum maps at 1.3 mm with ALMA)
   - fitting: _not stated_
   - validation: accurate within 5-10% against synthetic observations  
  > "This method has been proved against synthetic observations to be accurate within an uncertainty level of 5–10%" (3.1 Continuum maps at 1.3 mm with ALMA)
2. **Identify continuum sources and measure fluxes**: Source = closed 3 sigma contour in averaged maps; fluxes integrated over 3 sigma polygon on 242 GHz map; sizes from 50% polygon; no Gaussian fits  
  > "We refrain from fitting Gaussians due to the complex and extended structure of some sources. The flux is determined as the integrated flux over the 3$\sigma$ polygon." (3.2 Source determination)
   - parameter: sigma = 8 mJy/beam  
  > "(with $\sigma$ the rms noise level of the map: 8 mJy beam$^{-1}$)" (3.2 Source determination)
   - fitting: _not stated_
   - validation: features must appear in most of 7 averaged maps to be real  
  > "If some feature is only observed in one or two maps, we consider them artifacts of the cleaning process" (3.2 Source determination)
3. **Spectral index and nature of emission**: Linear fit of fluxes vs frequency across spws; comparison with VLA 40 GHz and SMA 345 GHz fluxes at 0.4'' resolution  
  > "The spectral index obtained by fitting the fluxes of all the spectral windows is listed in the last column" (4.1 Origin of the continuum emission)
   - fitting: _not stated_
   - validation: ALMA-only indices agree with those including VLA and SMA  
  > "The derived values are in agreement with the spectral indices derived only with the ALMA data from 211 to 275 GHz" (4.1 Origin of the continuum emission)
4. **Derive masses and densities**: Hildebrand formula for M_d+g at 242 GHz; n_H2 for spheres; ionized gas contribution subtracted by extrapolating 40 GHz with index -0.1  
  > "We assume a spectral index of $-0.1$ for the ionized gas, which corresponds to optically thin emission, and extrapolate the flux measured at 40 GHz" (4.2 Physical properties)
   - parameter: Td = 50 K and 100 K; D = 8.34 kpc; mu = 2.3  
  > "we list the mass derived for two different dust temperatures 50 K and 100 K" (4.2 Physical properties)
   - assumption: kappa at 230 GHz = 1.11 (Ossenkopf & Henning 1994), optically thin, gas-to-dust 100  
  > "optically thin emission, and a gas to dust conversion factor of 100" (4.2 Physical properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Chemical richness statistics**: count emission peaks >5 sigma per GHz (ADMIT-like, peaks within 5 channels discarded) and line luminosity L_line = 4 pi D^2 sum S dnu; linear fits to richness vs N(H2) and mass  
  > "The number of lines is automatically determined by searching for emission peaks above the 5$\sigma$ level across the whole spectrum" (4.3 Chemical content in the continuum sources)
   - software: ADMIT (approach)
   - parameter: 5 sigma threshold, sigma = 8 mJy/beam  
  > "with $\sigma$ being 8 mJy beam$^{-1}$" (4.3 Chemical content in the continuum sources)
   - fitting: linear fits excluding cores associated with ionized gas  
  > "The solid lines shown in the four panels correspond to linear fits to the data of those cores not associated with ionized gas." (4.3 Chemical content in the continuum sources)
   - validation: _not stated_
6. **Compare with 3D radiative transfer model**: Compare ALMA continuum and spectral index maps with model images at 242 GHz post-processed to ALMA uv sampling  
  > "Afterwards, we compute linear fits to the flux on a pixel-to-pixel basis to create the spectral index map." (4.4 Comparison with 3D-radiative transfer models)
   - fitting: _not stated_
   - validation: model intensity lower by factor 1.5 than observed  
  > "the intensity scale in the model image is off with respect to the observations by a factor of 1.5" (4.4 Comparison with 3D-radiative transfer models)

## Software

- **CASA** 4.4.0: calibration and imaging  
  > "The calibration and imaging were performed in CASA[^1] version 4.4.0." (2 Observations)
- **STATCONT** : continuum level determination in line-rich spectra  
  > "We have used the STATCONT[^2] python-based tool" (3.1 Continuum maps at 1.3 mm with ALMA)
- **ADMIT** : approach followed for line-peak counting  
  > "similar to the approach followed in ADMIT (ALMA Data Mining Toolkit; (cite: Friedel2015))" (4.3 Chemical content in the continuum sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| continuum sources in Sgr B2(N) | 20 | not stated | sources | 2 | We detect 27 continuum sources in Sgr B2(M) and 20 sources in Sgr B2(N). |
| continuum sources in Sgr B2(M) | 27 | not stated | sources | 2 | We detect 27 continuum sources in Sgr B2(M) and 20 sources in Sgr B2(N). |
| AN01 mass fraction of Sgr B2(N) | 73% (about 9000 Msun) | not stated | percent | 4 | that accounts for about 73% (about 9000 $M_\odot$) of the total mass in the region |
| mean / median core mass (50 K) | 495 / 103 | not stated | Msun | 4 | are 495 $M_\odot$ and 103 $M_\odot$ for the whole sample of cores |
| AN10 spectral index | -2.6 | 0.6 | dimensionless | 3 | The negative measured spectral index of $-2.6\pm0.6$ |
| mean lines per GHz, Sgr B2(N) vs (M) | 51 vs 23 | not stated | lines/GHz | 5 | The mean (median) number of lines per GHz is 51 (50) for Sgr B2(N), compared to 23 (13) for Sgr B2(M). |
| mean line luminosity fraction, N vs M | 20% vs 8% | not stated | percent | 5 | is 20% (16%) and 8% (9%) for Sgr B2(N) and Sgr B2(M), respectively |
| AN01 flux at 242 GHz | 25.74 | 2.97 | Jy | 2 | AN01 / 17:47:19.87 / $-$28:22:18.43 / $1.454\pm0.101$ / $25.74\pm2.97$ |

## Qualitative findings

- Brightest sources are dust dominated; weaker ones show free-free contamination  
  > "The brightest sources are dominated by (partially optically thick) dust emission, while there is an important degree of contamination from ionized gas free-free emission in weaker sources." (abstract)
- Lack of low-mass dense cores relative to Salpeter IMF  
  > "There seems to be a lack of low-mass dense cores in both regions." (abstract)

## Claim tuples

- H: Is the 1.3 mm emission of the sources dust or ionized gas? | E: Spectral indices across band 6 and comparison with VLA 40 GHz and SMA 345 GHz | R: Bright sources have alpha 2-4; some faint sources have flat/negative alpha coincident with VLA HII regions | F: Dust dominates bright sources; free-free contaminates weaker ones | **supported**
- H: How is mass distributed in the two regions? | E: Masses from 242 GHz fluxes at 50 and 100 K | R: AN01 holds ~73% of N mass; AM01+AM02 only ~50% of M mass | F: Sgr B2(N) is dominated by a single object, Sgr B2(M) is fragmented | **supported**
- H: Does chemical richness correlate with core mass? | E: Lines per GHz and line luminosity fraction versus N(H2) and mass, linear fits | R: Positive trends for cores not associated with ionized gas | F: More massive cores are more chemically rich, possibly a sensitivity effect | **partially**
- H: Does the 3D radiative transfer model reproduce the ALMA continuum? | E: Compare model images and spectral index maps at 242 GHz | R: General structure agrees; intensity off by factor 1.5; new sources missing | F: Model needs updating with new constraints | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: STATCONT used because continuum determination in line-rich sources is difficult; Gaussian fitting avoided due to complex source structure  
  > "In order to determine the continuum emission in these line-rich sources, we use a new statistical method, STATCONT" (abstract)
- Alternative: Self-calibrated images not used for continuum properties because extended emission can modify flux scale  
  > "we do not consider the self-calibrated images for the analysis of the continuum properties of Sgr B2(M) and (N)" (2 Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometer resolves out emission above ~5'', affecting faint-source spectral indices  
  > "the ALMA observations are sensitive to angular scales of only $<5$$''$, and this may result in resolving out extended emission" (4.1 Origin of the continuum emission)
- Limitation (authors): Optically thick cores give lower-limit masses; assumed temperatures may be low  
  > "This results in lower limits for the mass estimated listed in Table [\[t:properties\]](#t:properties)." (4.2 Physical properties)
- Caveat (inferred, ours): Masses depend strongly on assumed 50/100 K temperature and a single opacity law
- Caveat (inferred, ours): Free-free correction assumes optically thin HII regions with alpha=-0.1
- Caveat (inferred, ours): Flux scale uncertainty ~20% not propagated into masses
- Caveat (inferred, ours): Reliance on unpublished STATCONT paper at time of writing

## Reproducibility

- Data public (paper): ALMA data acknowledged under project 2013.1.00332.S; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00332.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: STATCONT available at a URL  
  > "<http://www.astro.uni-koeln.de/~sanchez/statcont>" (footnote 2)
- Missing: Clean parameters (threshold, masks, image size)
- Missing: STATCONT tolerance and settings
- Missing: Polygon definitions for each source (only coordinates given)
- Missing: VLA and SMA images from other papers
- Missing: 3D model files
- Data volume (inferred): Large: 10 tunings x 4 spws spectral scan, likely several hundred GB raw
- Score (inferred): 3/5, Data and main recipe are clear and tables give numeric results, but imaging details, STATCONT tolerance and external VLA/SMA/model data are missing.
- Rediscovery candidate: no, Requires STATCONT details, many unstated imaging parameters and external VLA/SMA data; large spectral scan data volume.

## Links

- Method: Sánchez-Monge et al. (submitted) (STATCONT continuum determination method)
- Companion: Schmiedeke2016 (Paper I: 3D radiative transfer model of Sgr B2)
- Companion: Bonfand2017 (detailed chemical analysis of Sgr B2(N) from same project)
- Related: SMA 345 GHz survey of Sgr B2 (Qin et al. 2011)
- Related: VLA 40 GHz survey (Rolffs et al. 2011)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 63,
  "rate": 0.724
 },
 "evidence_ok": true
}
```
