# Exploring Magnetic Fields in a Merging Galaxy: Comparing Polarization and Velocity Gradient in the Centaurus Galaxy

`2024ApJ...977..121N` | The Astrophysical Journal 2024 | first author: Nguyen, Quynh Lan | arXiv: 2406.04242 | DOI: 10.3847/1538-4357/ad93a3

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Can the Velocity Gradient Technique applied to PHANGS-ALMA CO emission trace the magnetic field of the merging Centaurus galaxy, as tested against HAWC+ dust polarization?  
  > "In this study, we apply the Velocity Gradient Technique (VGT) to the merging Centaurus galaxy." (abstract); "We compare gradient maps derived from the PHANGS-ALMA survey using CO emission lines with magnetic field tracings from dust polarization data obtained via the HAWC+ instrument." (abstract)
- Target **Centaurus galaxy**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: 12CO (J = 2–1) per Introduction and Sec. 2.1 first sentence; Sec. 2.1 second sentence says J = 1 - 0 (inconsistent in the paper); velocity resolution 2.5 km/s  
  > "In this study, we utilized the $\rm ^{12}CO$ (J = 2–1) emission lines provided by the Physics at High Angular Resolution in Nearby Galaxies (PHANGS)–ALMA survey" (2.1 Emission Lines); "The PHANGS-ALMA survey offers $\rm ^{12}CO$ (J = 1 - 0) emission line data at a spatial resolution of approximately $8.13''$ (about 145.5 pc)" (2.1 Emission Lines)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: approximately 8.13'' (about 145.5 pc)  
  > "at a spatial resolution of approximately $8.13''$ (about 145.5 pc) and a velocity resolution of 2.5 km s$^{-1}$ for the nearby galaxy Centaurus." (2.1 Emission Lines)
- max recoverable scale: _not stated_
- sensitivity: RMS brightness temperature noise around ~0.30±0.13 K km/s  
  > "This survey achieves a high signal-to-noise ratio, with an RMS brightness temperature noise level around $\sim0.30\pm0.13$ K km s$^{-1}$." (2.1 Emission Lines)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data (PHANGS-ALMA survey)  
  > "The details of the archival data are shown in Section" (Introduction)
- Line: 12CO J = 2–1 (Sec. 2.1 also states J = 1 - 0) (not stated)
- Other facility **HAWC+ (SOFIA instrument, as named in the paper: High-resolution Airborne Wideband Camera Plus)**: 89 micron (band C, FWHM ~7.8'') dust polarization used to infer magnetic field orientation  
  > "we employed data from the High-resolution Airborne Wideband Camera Plus (HAWC+) archived in the HAWC+ database" (2.2 Polarization measurement); "Measurements were taken from band C (89 $\mu$m, FWHM $\approx7.8''$)." (2.2 Polarization measurement)
- External data: PHANGS-ALMA 12CO cube of Centaurus (data product and its survey properties)  
  > "provided by the Physics at High Angular Resolution in Nearby Galaxies (PHANGS)–ALMA survey (cite: 2021ApJS..257...43L)." (2.1 Emission Lines) [from (cite: 2021ApJS..257...43L) Leroy et al. 2021, ApJS, 257, 43]
- External data: HAWC+ dust polarization of Centaurus at 89 micron  
  > "the magnetic field in Centaurus has been studied by (cite: 2021NatAs...5..604L) using HAWC+ dust polarization at 89$\mu$m." (Introduction) [from (cite: 2021NatAs...5..604L) Lopez-Rodriguez 2021, Nature Astronomy, 5, 604]

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
- smoothing: polarization data smoothed to FWHM ~40'' to match the VGT resolution  
  > "To compare with the magnetic field measured with VGT, we smooth the polarization data to FWHM $\approx40''$ matching the spatial resolution of VGT." (2.2 Polarization measurement)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- VGT multi-step pipeline (gradients, sub-block averaging, pseudo-Stokes parameters)  
  > "In this study, we employed the VGT, following a multi-step process detailed in (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L)" (3.3 VGT pipeline) [from (cite: 2022ApJ...941...92H; 2023MNRAS.519.1068L)]
- Velocity Channel Gradients (VChGs) branch of VGT  
  > "particularly its branch, namely, Velocity Channel Gradients (VChGs; (cite: Lazarian_2018))" (Introduction) [from (cite: Lazarian_2018)]
- Alignment Measure (AM) definition  
  > "we utilize the Alignment Measure (AM; (cite: GL17))" (3.3 VGT pipeline) [from (cite: GL17)]
- other sub-block sizes were tested in earlier work  
  > "although other sizes have been tested (cite: YL17a; LY18a; 2020ApJ...905..129H)" (3.3 VGT pipeline) [from (cite: YL17a; LY18a; 2020ApJ...905..129H)]

### Not stated but needed to reproduce (our reading)

- Exact PHANGS-ALMA data product (cube version, resolution tier, masked or unmasked) and its download source
- Whether the CO line is J = 2-1 or J = 1-0 (the paper states both)
- Velocity range v_los,min to v_los,max used in the pseudo-Stokes integration
- Pixel size, which sets the physical size of the 20x20 pixel sub-blocks; how the CO map is brought to the ~40'' resolution quoted for VGT
- Whether the noise threshold keeps pixels above or below 3 x RMS (text says 'less than'; likely a typo, not resolvable from the paper)
- Centaurus distance, coordinates and inclination (only 145.5 pc per 8.13'' is given)
- HAWC+ data identifiers, reduction version and debiasing of p
- How AM-versus-SNR bins in the AM histogram were defined and which SNR (CO or polarization)
- Gaussian-fit details for orientation histograms (bins, fit method, rejection of failed fits)
- Regridding and registration between VGT and HAWC+ maps; no code beyond the mention of Julia

## Analysis recipe

1. **Prepare HAWC+ polarization reference field**: Convert HAWC+ 89 micron polarization angles to B-field orientation, keep p/sigma_p > 1 pixels, smooth to FWHM ~40''  
  > "Magnetic field orientations were determined using the relation $\phi_B=\phi+\pi/2$, where $\phi$ represents the polarization angle." (2.2 Polarization measurement); "We limited our analysis to pixels where the polarization fraction ($p$) divided by its uncertainty ($\sigma_p$) exceeds 1 ($p/\sigma_p > 1$)." (2.2 Polarization measurement)
   - parameter: p/sigma_p > 1; smoothed to FWHM ~40''  
  > "To compare with the magnetic field measured with VGT, we smooth the polarization data to FWHM $\approx40''$ matching the spatial resolution of VGT." (2.2 Polarization measurement)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute velocity-channel gradient angles**: Convolve each thin CO channel map with 3x3 Sobel kernels to get gradients and pixel gradient angle psi_g; keep pixels by a 3 x RMS brightness threshold  
  > "Each thin channel map, $p(x, y, v_{\rm los})$, undergoes convolution with 3$\times$3 Sobel kernels $G_x$ and $G_y$ to compute the gradients:" (3.3 VGT pipeline); "Only pixels with a brightness temperature less than three times the RMS noise are retained for subsequent analysis." (3.3 VGT pipeline)
   - parameter: 3x3 Sobel kernels; per-channel width 2.5 km/s  
  > "undergoes convolution with 3$\times$3 Sobel kernels $G_x$ and $G_y$" (3.3 VGT pipeline)
   - assumption: Velocity caustics dominate the intensity fluctuations in the 2.5 km/s channels  
  > "Given that the PHANGS-ALMA survey offers a velocity resolution of 2.5 km/s, this ensures that the velocity caustics dominate the observed intensity in the spectroscopic velocity channels." (3.2 Velocity caustics)
   - assumption: Turbulence injection scale in Centaurus may exceed the ~100 pc used for quiescent galaxies; 145.5 pc resolution assumed adequate for this pilot study  
  > "it is reasonable to hypothesize that the injection scale $L_{\rm inj}$ in the Centaurus galaxy, which has experienced dynamic merger events, could be larger than 100 pc" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Average gradient orientation in sub-blocks**: Split each psi_g map into 20x20 pixel sub-blocks; histogram the orientations in each block, fit a Gaussian, take its peak as the block orientation  
  > "The pixelized map $\psi_g(x, y, v_{\rm los})$ is segmented into 20$\times$20 pixel sub-blocks" (3.3 VGT pipeline); "A histogram of gradient orientations within each sub-block is produced and fitted with a Gaussian distribution." (3.3 VGT pipeline); "The peak of this Gaussian distribution is taken as the dominant gradient orientation for that sub-block." (3.3 VGT pipeline)
   - parameter: sub-block size 20x20 pixels  
  > "is segmented into 20$\times$20 pixel sub-blocks" (3.3 VGT pipeline)
   - fitting: Gaussian fit to the gradient-orientation histogram in each sub-block (priors and likelihood not stated)  
  > "A histogram of gradient orientations within each sub-block is produced and fitted with a Gaussian distribution." (3.3 VGT pipeline)
   - validation: _not stated_
4. **Build pseudo-Stokes maps and VGT B-field orientation**: Integrate intensity-weighted cos(2 psi_gs) and sin(2 psi_gs) over the velocity range to get Q_g and U_g; B-field orientation psi_B = 0.5 arctan(U_g/Q_g) + pi/2  
  > "Repeating the Steps 1 and 2 for every channel within the velocity range of interest, we can then construct the pseudo-Stokes parameters $Q_g(x,y)$ and $U_g(x,y)$:" (3.3 VGT pipeline); "The POS magnetic field orientation is inferred from:" (3.3 VGT pipeline)
   - assumption: Turbulent eddies elongate along the magnetic field, so velocity gradients are perpendicular to the local field  
  > "This anisotropy suggests that turbulent eddies elongate along magnetic field lines, manifesting notably in local reference frames." (3.1 Theoretical consideration: Velocity Gradient Technique)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare VGT and polarization fields with the Alignment Measure**: Compute AM = 2(cos^2 theta_r - 1/2) with theta_r = |phi_B - psi_B| per pixel; map it and examine it against signal-to-noise ratio  
  > "To quantify the agreement between VGT and the magnetic field inferred from polarization, we utilize the Alignment Measure (AM; (cite: GL17)), expressed as:" (3.3 VGT pipeline); "An AM value of 1 implies parallel alignment of $\phi_{\rm B}$ and $\psi_{\rm B}$, while -1 indicates perpendicularity." (3.3 VGT pipeline); "we observe that we do not observe a negative AM at the high signal-to-noise ratio regions." (4 Result)
   - fitting: _not stated_
   - validation: VGT-CO compared against HAWC+ dust polarization as an independent tracer  
  > "Specifically, we measure velocity gradients in the Centaurus galaxy and evaluate their effectiveness in tracing magnetic fields, using dust polarization as a comparative measure." (5 Conclusion)

## Software

- **Julia** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Radius of central region where VGT-CO magnetic field shows a twist | approximately 500 | not stated | pc | 4 | it exhibits a twist across the central region of approximately 500 pc radius around the nucleus. |
| AM in the northwest of the central disk | ≈ 0 | not stated | dimensionless | 5 | The anti-alignment, indicated by negative AM values, is observed in the two tails, while a misalignment with AM $\approx 0$ is noted in the northwest of the central disk. |

## Qualitative findings

- Anti-alignment between VGT-CO and polarization-inferred fields is seen in the two tails and in the radio jet regions  
  > "Specifically, we identify jet regions as areas of anti-alignment, consistent with previous reports that gradients tend to rotate 90 degrees in outflow regions." (abstract); "The anti-alignment, indicated by negative AM values, is observed in the two tails" (4 Result)
- Alignment is best at the highest signal-to-noise ratios; no negative AM at high SNR  
  > "Statistically, we find that the alignment of magnetic fields, as revealed by polarization, is most accurate in regions with the highest signal-to-noise ratios." (abstract)
- VGT-CO and HAWC+ fields agree over most of the galaxy, especially the central disk  
  > "Our analysis reveals a strong correspondence between the directions indicated by these two tracers across most of the galactic image." (abstract)

## Claim tuples

- H: VGT based on CO channel gradients can trace the magnetic field in a merging galaxy | E: Applied VChG to the PHANGS-ALMA CO cube of Centaurus and compared the inferred field with HAWC+ 89 micron polarization using AM | R: Strong correspondence between the two tracers across most of the image | F: VGT results generally agree with dust polarization on a statistical basis | **supported**
- H: Jets and outflows cause the gradient and polarization directions to differ | E: Mapped AM and inspected regions with negative AM against the radio jet | R: Anti-alignment (negative AM) in the two tails and in the radio jet regions | F: Anti-alignment in jet regions is consistent with gradients rotating in outflows, but its origin needs further study | **partially**
- H: Misalignment is related to data quality | E: Examined the AM histogram as a function of signal-to-noise ratio | R: Largest misalignment lies in low-density, low-SNR regions; no negative AM at high SNR | F: Alignment is most reliable where the SNR is highest | **supported**
- H: Differences between warm dust and cold CO gas contribute to low-AM regions | E: Compared low-AM regions with HI absorption and the different phases traced by 89 micron dust and CO | R: Central low-AM region coincides with strong HI absorption | F: Low AM could reflect different field morphology in warm and cold gas (not tested directly) | **partially**

## Reasoning

- Why this data: Centaurus is among the closest nuclear active galaxy mergers, so it is taken as a test-bed for VGT  
  > "Centaurus galaxy, as one of the closest nuclear active galaxy mergers, is the best test-bed for VGT." (Introduction)
- Why this method: VGT with CO spectroscopy isolates the magnetic field associated with molecular gas, unlike dust polarization that mixes gas phases  
  > "To separate the magnetic field associated with molecular gas, which is the most important fueling material for the galactic nuclei, (cite: 2022ApJ...941...92H) proposed the use of the Velocity Gradient Technique" (Introduction)
- Alternative: Other sub-block sizes than 20x20 pixels have been tested (in earlier work)  
  > "although other sizes have been tested (cite: YL17a; LY18a; 2020ApJ...905..129H)" (3.3 VGT pipeline)
- How they decided it was enough: _not stated_
- Limitation (authors): Merger dynamics are more complicated than in normal galaxies, making the comparison harder to interpret  
  > "However, it should be noted that the dynamics of galaxy mergers are more complicated than normal galaxies. This makes the interpretation of the comparison more difficult." (Introduction)
- Limitation (authors): Origin of the misalignment needs further study; higher-SNR data and synchrotron polarization are needed  
  > "Future research, utilizing higher signal-to-noise data and incorporating synchrotron polarization, is essential to further explore these findings." (5 Conclusion); "Further studies of the origin of this discrepancy are required." (4 Result)
- Caveat (inferred, ours): Line identification is inconsistent (CO J=2-1 vs J=1-0) for the same dataset
- Caveat (inferred, ours): The paper gives no mean AM, uncertainties or quantitative SNR dependence; claims are mostly visual
- Caveat (inferred, ours): VGT map resolution (~40'') is much coarser than the 8.13'' CO data, and the 145.5 pc scale is assumed adequate without test
- Caveat (inferred, ours): The 3 x RMS threshold wording ('less than') looks like a typo
- Caveat (inferred, ours): Single galaxy and single comparison tracer; HI contamination of dust polarization is argued, not tested
- Caveat (inferred, ours): Jet-region anti-alignment is attributed to outflows without independent kinematic check

## Reproducibility

- Data public (paper): CO from the PHANGS-ALMA survey and HAWC+ data from the HAWC+ database are described as archival  
  > "The details of the archival data are shown in Section" (Introduction); "we employed data from the High-resolution Airborne Wideband Camera Plus (HAWC+) archived in the HAWC+ database" (2.2 Polarization measurement)
- Products in archive: _not stated_
- Missing: No code release or repository stated; only Julia is named
- Missing: PHANGS cube identifier/version and HAWC+ observation identifiers
- Missing: Velocity integration range, pixel scale and registration details
- Missing: Quantitative AM statistics (mean AM, per-SNR bins) are not tabulated
- Data volume (inferred): Small: one PHANGS-ALMA CO cube of a single galaxy (likely under 1 GB) plus one HAWC+ polarization map.
- Score (inferred): 2/5, Public archival data are used and the VGT steps are listed, but key settings (velocity range, pixel scale, data versions, threshold wording) and numeric results are missing, and no code is given.
- Rediscovery candidate: no, Main results are qualitative maps with few numbers, and several needed settings are not stated.

## Links

- Method: (cite: 2022ApJ...941...92H) Hu et al. 2022 (VGT pipeline in external galaxies followed here)
- Method: (cite: 2023MNRAS.519.1068L) Liu et al. 2023 (VGT pipeline followed here)
- Method: (cite: Lazarian_2018) Lazarian & Yuen 2018 (Velocity Channel Gradients technique)
- Method: (cite: GL17) González-Casanova & Lazarian 2017 (Alignment Measure)
- Companion: (cite: 2021NatAs...5..604L) Lopez-Rodriguez 2021 (HAWC+ dust polarization study of Centaurus)
- Companion: (cite: 2024ApJ...967...18Z) Zhao et al. 2024a (earlier VGT application to NGC 0628)
- Companion: (cite: 2021ApJS..257...43L) Leroy et al. 2021 (PHANGS-ALMA survey data source)
- Related: PHANGS-ALMA
- Related: HAWC+ (SOFIA)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00803.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 35,
  "rate": 0.449
 },
 "evidence_ok": true
}
```
