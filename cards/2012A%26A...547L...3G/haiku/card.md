# ALMA and VLA observations of recombination lines and continuum toward the Becklin-Neugebauer object in Orion

`2012A&A...547L...3G` | Astronomy and Astrophysics 2012 | first author: Galván-Madrid, R. | arXiv: 1210.1413 | DOI: 10.1051/0004-6361/201220330

Card schema 1.0 | model claude-haiku-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: Can millimeter and centimeter recombination lines give the line-of-sight velocity of the BN object and constrain the density and structure of its ionized envelope, and is the BN millimeter continuum variable?  
  > "In particular, observing hydrogen recombination lines (RLs) can be used to obtain the line-of-sight velocities of the radio sources" (Introduction)
- Target **Becklin-Neugebauer (BN) object, Orion**: coordinates ALMA pointing center 05h35m14.35s, -05°22'35.0" (BN position itself not stated)  
  > "The pointing center was $\alpha_\mathrm{J2000}=05^\mathrm{h}~35^\mathrm{m}~14\rlap.{^\mathrm{s}}35$, $\delta_\mathrm{J2000}=-05^\circ~22'~35\rlap.{''}0$." (Data); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: 1.3 mm (ALMA spectral windows 213.72 to 246.62 GHz)  
  > "The data consisted of 20 different spectral windows covering the frequency range from 213.72 GHz to 246.62 GHz." (Data)
- frequencies and spectral setup: 20 spectral windows; 0.488 MHz spectral resolution (about 0.6 km/s)  
  > "Each spectral window had a uniform spectral resolution of 0.488 MHz" (Data)
- continuum bandwidth: _not stated_
- arrays: ALMA 16 x 12-m antennas  
  > "The array used 16 12-m antennas in a compact configuration" (Data)
- configurations: compact configuration  
  > "The array used 16 12-m antennas in a compact configuration" (Data)
- baselines: 15 kλ to 269 kλ  
  > "with baselines in the range of 15 k$\lambda$ to 269 k$\lambda$" (Data)
- angular resolution: ALMA SV HPBW 1.3 x 0.6 arcsec (from table note e); 100 kλ-restricted maps used for BN  
  > "e: ALMA SV data, HPBW" (Table 2 notes)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 15 minutes per spectral window  
  > "was observed for an on-source time of" (Data)
- observing dates: 19 January 2012 (ALMA SV)  
  > "Orion BN/KL was observed on January 19, 2012 with ALMA as part of the SV program." (Data)
- pi or archival as stated: archival ALMA Science Verification data (2011.0.00009.SV), calibrated visibilities released 12 April 2012; VLA archival data also reused  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- Line: Hydrogen H30α (231.9009 GHz)
- Line: Hydrogen H53α (42.95197 GHz)
- Other facility **Very Large Array (VLA)**: archival 8.4 GHz (3.6 cm) A-configuration continuum epochs and archival B-array H53α data  
  > "We also present archival Very Large Array[^2] (VLA) data." (Data)
- Other facility **SMA calibrator database**: flux densities of phase calibrator J0607–085 for flux-scale check  
  > "The SMA data base[^1] reports flux densities for J0607–085 within ten days of the ALMA observation" (Data)
- External data: H53α B-array observations (42.95 GHz)  
  > "The H$53\alpha$ ($\nu_0=42.95197$ GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data) [from (cite: rodriguez09b)]
- External data: four 3.6-cm VLA-A BN flux epochs  
  > "together with the four epochs reported by (cite: zapata04), also at 3.6 cm" (Results) [from (cite: zapata04)]
- External data: BN 218 GHz flux S=150±50 mJy (OVRO 1993-1994)  
  > "the 218 GHz flux of $S=150\pm50$ mJy (from OVRO observations in 1993 and 1994)" (Results) [from (cite: plambeck95) and (cite: blake96)]
- External data: BN 231 GHz non-detection, 3-sigma about 34 mJy (CARMA 2007)  
  > "(cite: fs08) do not detect BN at 231 GHz down to a $3\sigma$ level of $\sim 34$ mJy (CARMA observations in 2007)." (Results) [from (cite: fs08)]
- External data: BN mass about 10 solar masses  
  > "The BN object is known to be a young star with a mass $M_\star \approx 10~M_\odot$ (cite: rodriguez05)." (Discussion) [from (cite: rodriguez05)]
- External data: gravitational confinement radius about 55 AU  
  > "this mass is enough to gravitationally confine ionized hydrogen within a radius of $\approx 55$ AU (cite: keto07)." (Discussion) [from (cite: keto07)]
- External data: electron density from RL ratio (equation 3 of kzk08)  
  > "using equation 3 of (cite: kzk08), the average electron density traced by these RLs is" (Recombination lines) [from (cite: kzk08)]
- External data: RL linewidth combination formula  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines) [from (cite: gm09)]
- External data: electron-impact pressure broadening formula  
  > "They produce a broadening of width (cite: smirnov84):" (Linewidth of recombination lines) [from (cite: smirnov84)]
- External data: tabulated non-LTE departure coefficients b_n and beta_n  
  > "Using the tabulated values in the calculations of (cite: walmsley90)" (cm and (sub)mm recombination lines) [from (cite: walmsley90)]
- External data: infrared and optical RLs extending to >100 km/s  
  > "Infrared and optical RLs have also been detected toward BN and extend to velocities $>100$ km s$^{-1}$ (cite: scoville83)." (Discussion) [from (cite: scoville83)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 3.3.0 and 3.4.0  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- pipeline version: _not stated_
- archive products used as is: fully calibrated visibilities as released by the ALMA SV archive (12 April 2012)  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- flux calibrator: Callisto and Mars (absolute amplitude scale); phase calibrator J0607–085 (flux 1.40 Jy measured); VLA amplitude calibrator 1331+305 (5.21 Jy) for 8.4 GHz  
  > "The absolute amplitude scale was derived from observations of Callisto and Mars." (Data); "In all epochs 1331+305 was used as amplitude calibrator with an adopted flux density of 5.21 Jy." (Data)
- flux scale uncertainty: ~10%  
  > "From this, we estimate that the amplitude scale of the ALMA observations is accurate to" (Data)
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
- continuum subtraction: done in the u-v domain: line-free channels selected per spectral window and a linear spectral baseline fitted  
  > "Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline." (Results)
- line free channels: selected by hand per spectral window (channel ranges not stated)  
  > "carefully selecting the line-free channels in each spectral window" (Results)
- primary beam correction: maps not corrected for primary beam; flux values quoted after primary-beam correction  
  > "We present maps that have not been corrected for primary beam attenuation." (Results)
- array combination: _not stated_
- smoothing: baseline-length cut at ~100 kλ for compact-source continuum and H30α maps (uv restriction, not a taper)  
  > "We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results, filtering out the emission on scales $>1\rlap.{''}4$." (Results)
- final beam: _not stated_
- final rms: about 3 mJy/beam in the 100 kλ continuum map around BN  
  > "The noise is $\times 5$ lower than in Fig. 1 ($\sim 3$ mJy)." (Results)

### Inherited from earlier work

- H53α B-array VLA data previously presented  
  > "have been previously presented by (cite: rodriguez09b) (project AR635)." (Data) [from (cite: rodriguez09b)]
- electron density from equation 3 of the RL ratio method  
  > "using equation 3 of (cite: kzk08), the average electron density traced by these RLs is" (Recombination lines) [from (cite: kzk08)]
- FWHM combination formula for pressure and thermal and dynamical broadening  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines) [from (cite: gm09)]
- electron-collision pressure broadening width  
  > "They produce a broadening of width (cite: smirnov84):" (Linewidth of recombination lines) [from (cite: smirnov84)]
- tabulated b_n values for non-LTE correction  
  > "Using the tabulated values in the calculations of (cite: walmsley90)" (cm and (sub)mm recombination lines) [from (cite: walmsley90)]

### Not stated but needed to reproduce (our reading)

- Imaging weighting (robust or natural) and any uv taper used for the 1.3 mm continuum and H30α moment maps
- Cell size and image size for the ALMA maps
- Deconvolver, cleaning threshold and masking used for the ALMA and VLA images
- Exact channel ranges of line-free emission and the channel binning used for the H30α spectrum
- Whether self-calibration was applied to the ALMA data and at what solution interval
- Exact aperture definition and fit method used to measure BN line and continuum fluxes
- Primary-beam model used for the primary-beam correction
- Electron temperature and density assumed when computing the thermal and pressure broadening inputs (Te and Ne are adopted per equation, values not fully listed)
- Treatment of the BN continuum when deriving the dust contribution (dust opacity law and dust temperature not given)
- VLA data reduction details for the 3.6 cm epochs (weighting, self-calibration, imaging parameters)

## Analysis recipe

1. **measure the 1.3 mm continuum of BN**: co-add line-free continuum visibilities from all spectral windows and image; for BN, restrict to baselines >100 kλ to suppress extended hot-core emission, then correct for primary beam  
  > "Figure [1](#f1_continuum) shows a deep continuum image from the ALMA data obtained by co-adding the line-free continuum visibilities from all spectral windows." (Results); "We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results, filtering out the emission on scales $>1\rlap.{''}4$." (Results)
   - software: CASA
   - parameter: average frequency 230.17 GHz (1.30 mm)  
  > "The average frequency (wavelength) in this map is 230.17 GHz (1.30 mm)." (Continuum.)
   - parameter: minimum baseline length about 100 kλ  
  > "We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results" (Results)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: BN flux the same within 20% for different uv restrictions  
  > "We note that the flux density for BN is the same, within $20~\%$, regardless of the u-v coverage restriction applied." (Continuum.)
2. **extract H30α and H53α spectra and moment-0 maps toward BN**: spectra toward BN; Gaussian fit to each line using an aperture matched to the emitting area; moment-0 maps for H30α use only baselines >100 kλ  
  > "Similar to the mm continuum, the H30$\alpha$ map uses only baselines with length $> 100$ k$\lambda$" (Recombination lines); "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3 notes)
   - parameter: H30α peak 181±14 mJy, vLSR 26.3±0.5 km/s, FWHM 15.4±1.3 km/s  
  > "H$30\alpha$ | 231.9009 | $181\pm14$" (Table 3)
   - assumption: H30α taken as best tracer of stellar line-of-sight velocity (outflow geometry argument of kzk08)  
  > "Therefore, the H$30\alpha$ line should give a better estimation of the line-of-sight velocity of the star inside the BN nebula" (Recombination lines)
   - fitting: Gaussian line fits  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3 notes)
   - validation: _not stated_
3. **decompose the RL width into thermal, pressure and bulk-motion terms**: compare observed FWHM with thermal width, Stark (ion and electron) pressure broadening and natural width, then bound Te and bulk motions  
  > "The H30$\alpha$ line is only broadened thermally and by dynamical motions" (Recombination lines); "Therefore, for the gas traced by the H$30\alpha$ line, $T_e$ is at most 4900 K" (Recombination lines)
   - parameter: thermal width 20.3 km/s at Te=9000 K (pure hydrogen)  
  > "For a pure-hydrogen gas with $T_e=9000$ K, $\Delta v_\mathrm{th}=20.3$ km s$^{-1}$." (Linewidth of recombination lines)
   - assumption: all gas thermalized to electron temperature Te; microturbulence neglected  
  > "Neglecting microturbulence, the thermal FWHM is" (Linewidth of recombination lines)
   - fitting: _not stated_
   - validation: _not stated_
4. **estimate electron density of the H30α/H53α emitting gas**: apply equation 3 of kzk08 to the RL results  
  > "using equation 3 of (cite: kzk08), the average electron density traced by these RLs is" (Recombination lines)
   - parameter: Ne = 8.4e6 cm^-3  
  > "the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$." (Recombination lines)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
5. **check non-LTE effects and dust contribution to the 1.3 mm continuum**: use tabulated departure coefficients to estimate the non-LTE correction; compare the observed line-to-continuum ratio of H30α and H53α with the expected ratio in the optically thin regime  
  > "Using the tabulated values in the calculations of (cite: walmsley90), $b_{30}\approx 0.98$ and $\beta_{30} \sim -1.5$ for a density $N_e=10^7$ cm$^{-3}$." (cm and (sub)mm recombination lines); "Under these assumptions, the expected ratio of the H30$\alpha$ to H$53\alpha$ line-to-continuum ratios is 6.4. However, the observed value is 1.6." (cm and (sub)mm recombination lines)
   - parameter: tau_C,1.3mm about 0.08 (from the data)  
  > "In the optically-thin case ($\tau_\mathrm{C,1.3mm}\sim0.08$ from the data)" (cm and (sub)mm recombination lines)
   - assumption: optically thin regime; LTE line emission coefficient scaling with frequency  
  > "In the optically-thin case" (cm and (sub)mm recombination lines)
   - fitting: _not stated_
   - validation: if ~32 mJy of the 1.3 mm continuum is free-free the expected ratio is recovered; dust inferred to contribute significantly  
  > "If we assume that only $\sim 32$ mJy of the 1.3-mm continuum are due to free-free then the line-to-continuum ratio would increase to the expected value." (cm and (sub)mm recombination lines)
6. **look for cm continuum variability of BN**: reprocess archival VLA A-array 8.4 GHz epochs in AIPS with standard methods and compare with earlier cm fluxes  
  > "Finally, several epochs of continuum observations at 8.4 GHz in the A configuration were processed using standard methods in the AIPS software." (Data); "Based on this data set, the 3.6-cm flux is quite stable (within $30~\%$ of the maximum value)." (Results)
   - software: AIPS
   - parameter: amplitude calibrator 1331+305 at 5.21 Jy  
  > "In all epochs 1331+305 was used as amplitude calibrator with an adopted flux density of 5.21 Jy." (Data)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.3.0 and 3.4.0: processing of the ALMA SV visibilities, continuum imaging and H30α spectral extraction  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- **AIPS** : standard processing of the VLA 8.4 GHz continuum epochs  
  > "were processed using standard methods in the AIPS software." (Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H30α LSR velocity of BN (central line-of-sight) | 26.3 | ±0.5 | km s^-1 | 2 | From the H$30\alpha$ line, the central line-of-sight LSR velocity of BN is 26.3 km s$^{-1}$. |
| H30α peak flux density | 181 | ±14 | mJy | 2 | H$30\alpha$ / 231.9009 / $181\pm14$ |
| H30α FWHM | 15.4 | ±1.3 | km s^-1 | 2 | $15.4\pm1.3$ |
| H53α LSR velocity at peak | 19.8 | ±2.1 | km s^-1 | 2 | $19.8\pm2.1$ |
| H53α FWHM | 39.0 | ±5.0 | km s^-1 | 2 | $39.0\pm5.0$ |
| electron temperature upper limit from H30α linewidth | at most 4900 | not stated | K | 3 | for the gas traced by the H$30\alpha$ line, $T_e$ is at most 4900 K |
| average electron density traced by RLs | 8.4e6 | not stated | cm^-3 | 4 | the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$. |
| BN 1.3 mm flux density, primary-beam corrected | 126 | ±14 | mJy | 1 | After primary beam correction, the flux density of BN is $S_\mathrm{1.3mm}=126$ mJy. |
| BN 1.3 mm peak intensity (primary-beam corrected) | 112 | not stated | mJy/beam | 1 | we detect BN with a peak intensity of 55 mJy beam$^{-1}$ (112 mJy beam$^{-1}$ when primary beam attenuation is taken into account). |
| faint source 4.3 arcsec south of BN, primary-beam corrected 1.3 mm flux | 26 | not stated | mJy | 1 | A faint compact source with primary beam corrected flux $S_\mathrm{1.3mm}=26$ mJy is also detected $4\rlap.{''}3$ south of BN. |
| H53α-derived outflow velocity toward observer | 6.5 | not stated | km s^-1 | 2 | The H$53\alpha$ line appears to be tracing gas that is outflowing toward us with a velocity $\sim 6.5$ km s$^{-1}$ blueshifted with respect to the systemic. |
| expected H30α/H53α line-to-continuum ratio | 6.4 | not stated | dimensionless | 5 | the expected ratio of the H30$\alpha$ to H$53\alpha$ line-to-continuum ratios is 6.4. |
| observed H30α/H53α line-to-continuum ratio | 1.6 | not stated | dimensionless | 5 | However, the observed value is 1.6. |
| free-free contribution to 1.3 mm continuum needed to match expected ratio | 32 | not stated | mJy | 5 | If we assume that only $\sim 32$ mJy of the 1.3-mm continuum are due to free-free |
| H30α departure coefficient b30 | 0.98 | not stated | dimensionless | 5 | $b_{30}\approx 0.98$ and $\beta_{30} \sim -1.5$ |
| amplitude scale accuracy of ALMA data | 10 | not stated | percent | 1 | From this, we estimate that the amplitude scale of the ALMA observations is accurate to $\sim 10~\%$. |

## Qualitative findings

- BN 1.3 mm RL (H30α) emission is detected for the first time toward BN, arising from a dense, slowly moving base of the ionized envelope  
  > "We report the first detection of 1.3 mm RL (H$30\alpha$) emission toward Orion from the BN object." (Conclusions)
- 3.6 cm flux of BN is stable within 30% over the epochs reprocessed  
  > "Based on this data set, the 3.6-cm flux is quite stable (within $30~\%$ of the maximum value)." (Results)
- The ionized gas has low electron temperature and small bulk motions  
  > "This ionized gas has a relatively low electron temperature ($T_e<4900$ K) and small ($<<10$ km s$^{-1}$) bulk motions." (abstract)

## Claim tuples

- H: Can mm recombination lines give the systemic line-of-sight velocity of BN and the properties of its ionized base? | E: Detect H30α toward BN with ALMA SV data and fit a Gaussian; compare linewidth with thermal, pressure and bulk-motion broadening. | R: H30α LSR velocity 26.3±0.5 km/s, FWHM 15.4±1.3 km/s; Te at most 4900 K; Ne = 8.4e6 cm^-3. | F: The H30α line traces a dense, slowly moving base of the ionized envelope and gives the BN line-of-sight velocity. | **supported**
- H: Does the BN millimeter continuum vary between epochs? | E: Compare the ALMA 1.3 mm flux with earlier OVRO and CARMA 1.3 mm measurements and with reprocessed VLA 3.6 cm fluxes. | R: ALMA 1.3 mm flux 126±14 mJy; CARMA 3-sigma upper limit about 34 mJy; OVRO 150±50 mJy; 3.6 cm flux stable within 30%. | F: BN may have large mm flux variations, but dedicated uniform observations are needed to confirm. | **partially**
- H: Does dust in the line of sight contribute significantly to the 1.3 mm continuum of BN? | E: Compare the observed H30α/H53α line-to-continuum ratio with the LTE-based expected ratio. | R: Expected ratio 6.4 vs observed 1.6; matching requires only about 32 mJy of free-free emission at 1.3 mm. | F: Dust contributes a significant fraction of the 1.3 mm continuum. | **partially**
- H: Are mm RLs of BN close to LTE? | E: Apply tabulated non-LTE departure coefficients to the optically thin H30α and H53α case. | R: b30 about 0.98 and beta30 about -1.5, so the H30α line is amplified by about 3%; H53α is closer to LTE. | F: The RLs are reasonably close to LTE. | **supported**

## Reasoning

- Why this data: mm RLs are preferred for the central velocity because they are more optically thin, less pressure broadened and intrinsically brighter than cm lines.  
  > "Millimeter (mm) RLs are in principle better suited to giving the central velocity of the system because they are more optically thin, much less pressure broadened, and intrinsically brighter than centimeter (cm) lines" (Introduction)
- Why this method: Using the 100 kλ uv restriction removes extended hot-core emission around BN so its compact emission can be measured.  
  > "However, at the position of BN, where emission is fainter, the restricted u-v coverage effectively removes the extended emission around BN." (Results)
- Alternative: Flux variations from differences in u-v coverage rejected as the main explanation because BN is less than one arcsecond in size.  
  > "Differences in u-v coverage may also mimic flux variations, but since the continuum emission from BN is less than one arcsecond in size, this effect should not be important." (Discussion)
- Alternative: Observed mm flux variations considered possibly caused by sudden recombination of dense gas.  
  > "Alternatively, if BN is variable in the mm, it could be caused by the sudden recombination of dense gas (cite: osterbrock89)." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Mm flux variability cannot be confirmed because the earlier mm measurements used inhomogeneous setups.  
  > "However, the significance of these variations can be affected by the inhomogeneity of the mm observations." (Results)
- Limitation (authors): Infrared and optical RLs may trace a different volume than radio and mm RLs.  
  > "so they may trace gas from a different volume than the radio and (sub)mm RLs." (Discussion)
- Caveat (inferred, ours): The H30α line is blended with bright hot-core molecular emission, and the 100 kλ restriction removes part of the flux, so line flux depends on uv cut.
- Caveat (inferred, ours): The flux variability claim rests on comparing heterogeneous mm and cm measurements.
- Caveat (inferred, ours): The dust contribution estimate depends on an assumed free-free fraction and not on an independent dust measurement.
- Caveat (inferred, ours): Only one ALMA SV track is used, so no multi-epoch ALMA variability is tested.

## Reproducibility

- Data public (paper): ALMA Science Verification archive, calibrated visibilities released 12 April 2012  
  > "obtained from the Atacama Large Millimeter/submillimeter Array (ALMA) Science Verification archive and the Very Large Array (VLA)." (abstract)
- Products in archive: fully calibrated visibilities (2011.0.00009.SV) used as released  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- Code: _not stated_
- Missing: Imaging weighting, cell size, image size and deconvolution settings
- Missing: Channel ranges for line-free selection and H30α spectral binning
- Missing: Self-calibration choices and CASA task settings
- Missing: Aperture definition for BN flux and line measurements
- Missing: Primary-beam model and BN position used for the correction
- Missing: Dust opacity and temperature assumed for the dust contribution estimate
- Missing: VLA 3.6 cm reduction parameters
- Data volume (inferred): small: one ALMA SV track of 20 spectral windows (tens of GB at most) plus archival VLA A and B-array continuum and H53α data
- Score (inferred): 4/5, Data are public and the main numbers are stated, but imaging parameters, line-free channel ranges, self-calibration and aperture choices are missing, so a reproduction would need substantial guessing.
- Rediscovery candidate: no, Data are public and results are numeric, but the recipe lacks imaging weighting, cell size, line-free channels and aperture definitions, so it is not complete enough to redo.

## Links

- Method: (cite: gm09) (Source of the combined RL linewidth formula used to separate pressure, thermal and dynamical broadening.)
- Method: (cite: kzk08) (Source of the electron-density equation (equation 3) and of the outflow geometry argument for H30α versus H53α.)
- Method: (cite: walmsley90) (Source of tabulated non-LTE departure coefficients b_n and beta_n.)
- Companion: (cite: rodriguez09b) (Previously published H53α VLA B-array observations of the same source used here.)
- Companion: (cite: zapata04) (Four earlier VLA 3.6 cm epochs of BN compared in the variability table.)
- Related: ALMA Science Verification program 2011.0.00009.SV
- Related: VLA archival projects AM335, AM442, AM494, AM543, AM668, AR593 (8.4 GHz) and AR635 (H53α)

## Checks

```json
{
 "quotes": 102,
 "quotes_ok": 102,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 70,
  "rate": 0.686
 },
 "evidence_ok": true
}
```

## Figures

- **Figure 1** (sky_image, 1 panel(s), data): Continuum ALMA image at 230.17 GHz of the Orion BN/KL region, dominated by the extended Hot Core emission, with the cm sources I, BN and n marked by circles.
  - axes: x: J2000 Right Ascension [hours:minutes:seconds]; y: J2000 Declination [arcsec]; colour: continuum flux density per beam [Jy/beam]
  - supports step 1
  - read off the plot: approx. peak 0.8 Jy/beam in the Hot Core; approx. noise scale of -0.1 to 0.1 Jy/beam in the colour bar
- **Figure 2** (sky_image, 1 panel(s), data): Compact 1.3 mm continuum emission of the BN object, built from baselines longer than 100 kλ, showing BN as an unresolved source.
  - axes: x: J2000 Right Ascension [hours:minutes:seconds]; y: J2000 Declination [arcsec]; colour: continuum flux density per beam [Jy/beam]
  - supports step 1
  - read off the plot: approx. peak 0.06 Jy/beam at BN; approx. negative colour scale down to -0.01 Jy/beam
  - reproduction target
- **Figure 3** (spectrum, 2 panel(s), data, model): Hydrogen recombination line spectra toward BN (grey) with Gaussian fits (red): H30α from ALMA in the top panel and H53α from the VLA in the bottom panel.
  - axes: x: LSR velocity [km/s]; y: flux density [Jy]
  - supports step 2
  - validation: Gaussian fits to the H30α and H53α line profiles, showing the lines are detected at the BN position.
  - read off the plot: approx. H30α peak 0.18 Jy at 26 km/s; approx. H53α peak 0.01 Jy at 20 km/s; approx. H30α channel width 2.0 km/s; approx. H53α channel width 10.9 km/s
  - reproduction target
- **Figure 4** (moment_map, 1 panel(s), data): Velocity-integrated (moment 0) H30α emission toward BN in colour, with H53α VLA moment-0 contours overlaid.
  - axes: x: J2000 Right Ascension [hours:minutes:seconds]; y: J2000 Declination [arcsec]; colour: H30α velocity-integrated emission [Jy/beam km/s]; contours: H53α velocity-integrated emission [Jy/beam km/s (not labelled)]
  - supports step 2
  - read off the plot: approx. H30α peak 1.4 Jy/beam km/s at BN; approx. colour scale from -0.2 to 1.4 Jy/beam km/s
  - reproduction target
