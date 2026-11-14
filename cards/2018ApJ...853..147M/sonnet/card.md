# Molecular Reconnaissance of the β Pictoris Gas Disk with the SMA: A Low HCN/(CO+CO<SUB>2</SUB>) Outgassing Ratio and Predictions for Future Surveys

`2018ApJ...853..147M` | The Astrophysical Journal 2018 | first author: Matrà, L. | arXiv: 1801.03945 | DOI: 10.3847/1538-4357/aaa42a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: Which molecules other than CO are present in the exocometary gas disk of beta Pictoris, and what do the upper limits imply for the HCN/(CO+CO2) outgassing ratio and for future surveys?  
  > "use it to turn the SMA CN/CO flux ratio constraint into an upper limit of $<2.5$% on the HCN/(CO+CO$_2$) ratio of outgassing rates." (abstract)
- Target **beta Pictoris**: coordinates R.A. 05h47m17.0877s, Dec. -51 03 59.44 (J2000) (SMA pointing center)  
  > "Pointing center             | R.A. $05^{h}47^{m}17.0877s$, Dec. $-51^{h}03^{m}59.44s$ (J2000)" (Table 1 (SMA Observational Parameters)); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00142.S
- bands: ALMA Band 6; SMA 222 and 274 GHz (1.35 and 1.09 mm)  
  > "We extracted ALMA Band 6 observations of $\beta$ Pictoris from the archive" (2.2 ALMA); "detected in both SMA datasets at 222 and 274 GHz (1.35 and 1.09 mm)" (3.1 SMA continuum and CO J=2-1 detections)
- frequencies and spectral setup: SMA ASIC 128 channels x 48 chunks, 0.8125 MHz spacing, LO 273.732 and 221.654 GHz; SWARM on second track; ALMA native channel 488.281 kHz  
  > "The ASIC correlator was configured with 128 channels (0.8125 MHz spacing) in each of 48 chunks" (2.1 SMA); "native channel spacing of 488.281 kHz" (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array (compact and extended) plus ACA; SMA compact configuration  
  > "observations were performed between 2013 and 2015 with the 12-m array in a compact and extended configuration, as well as with the Atacama Compact Array (ACA)" (2.2 ALMA)
- configurations: _not stated_
- baselines: SMA 6 to 67 m  
  > "Min/Max baseline            | 6 to 67 meters" (Table 1 (SMA Observational Parameters))
- angular resolution: ALMA tapered beam 0.30'' x 0.26'' (p.a. -83.9 deg); SMA 7.7''x3.3'' and 8.7''x3.7''  
  > "$0.30\ensuremath{''}\times0.26\ensuremath{''}$, or 13.4$\times$10.7 au at the distance of $\beta$ Pictoris" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: SMA line rms 0.09 and 0.06 Jy/beam; continuum rms 1.4 and 0.57 mJy/beam  
  > "rms noise (continuum image) | 1.4 mJy beam$^{-1}$                                               | 0.57 mJy beam$^{-1}$" (Table 1 (SMA Observational Parameters))
- time on source: ALMA 28, 114 and 50 min (compact, extended, ACA)  
  > "with total on-source times of 28, 114, and 50 mins, respectively" (2.2 ALMA)
- observing dates: SMA 2014 Nov 11 and 2015 Dec 15; ALMA 2013-2015  
  > "The first track was obtained on 2014 November 11 using 7 antennas." (2.1 SMA)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Line: CN N=2-1, J=5/2-3/2 (226.875 GHz)
- Line: HCN J=3-2 (265.886 GHz)
- Line: HCO+ J=3-2 (267.558 GHz)
- Line: N2H+ J=3-2 (279.512 GHz)
- Line: H2CO 4_14-3_13 (281.527 GHz)
- Line: H2S 2_2,0-2_1,1 (216.710 GHz)
- Line: CH3OH 5_1,4-4_2,2 (216.946 GHz)
- Line: SiO J=5-4 (217.105 GHz)
- Line: DCN J=3-2 (217.239 GHz)
- Other facility **SMA**: New 222 and 274 GHz continuum and CO, CN, HCN, HCO+, N2H+, H2CO line data  
  > "We observed the $\beta$ Pictoris debris disk with the Submillimeter Array (SMA) on Mauna Kea, Hawaii in two tracks" (2.1 SMA)
- Other facility **Herschel PACS**: Archival spectrum covering the OH 2.51 THz line, giving an upper limit  
  > "we found unpublished PACS observations of $\beta$ Pictoris covering the OH line" (5.2 Predictions)
- External data: Solar System comet HCN/CO and HCN/(CO+CO2) abundance values  
  > "compared to HCN/(CO+CO$_2$) and HCN/CO values measured in Solar System comets from (cite: LeRoy2015) and references therein" (5.1) [from (cite: LeRoy2015)]
- External data: Photodissociation cross sections  
  > "Photodissociation timescales for all molecules were calculated using photodissociation cross sections from (cite: Heays2017)" (4.2) [from (cite: Heays2017)]
- External data: Stellar UV spectrum from HST/STIS and FUSE plus photospheric model  
  > "obtained by superimposing observed spectra from HST/STIS (cite: Roberge2000) and FUSE (cite: Bouret2002; Roberge2006) on the photospheric model spectrum of (cite: Fernandez2006)" (4.2) [from (cite: Roberge2000; Bouret2002; Roberge2006; Fernandez2006)]
- External data: CO rate matrix incl. vibrational/electronic levels  
  > "For CO, we obtain radiative transition rates from (cite: Thi2013) and references therein." (Appendix A) [from (cite: Thi2013)]
- External data: ALMA CO J=3-2/J=2-1 column density and ALMA CO line fluxes  
  > "we first take the CO column density at the clump location as determined through J=3-2/J=2-1 line ratio observations (cite: Matra2017a)" (5.2 Predictions) [from (cite: Matra2017a)]

## Processing

### Calibration

- pipeline or manual: SMA calibrated with MIR; ALMA calibration deferred to Matra2017a  
  > "All of the calibration was performed using the `MIR`[^1] software package." (2.1 SMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto and Uranus (SMA)  
  > "The absolute flux scale for the two tracks were set using observations of Callisto and Uranus, with an estimated accuracy of 20%." (2.1 SMA)
- flux scale uncertainty: 20% (SMA)  
  > "with an estimated accuracy of 20%" (2.1 SMA)
- self calibration: _not stated_

### Imaging

- task: SMA imaging and clean in miriad  
  > "Continuum and spectral line imaging and clean deconvolution were done in the `miriad` package." (2.1 SMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: SMA: natural weighting plus 3'' Gaussian taper east-west; ALMA: taper to match CO beam  
  > "for natural weighting plus a $3''$ Gaussian taper in the east-west direction" (Table 1 notes); "we applied a taper to the visibilities in order to produce datacubes with exactly the same synthesized beam size" (2.2 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ALMA 0.30'' x 0.26'', p.a. -83.9 deg  
  > "position angle (p.a., -83$\ensuremath{^\circ}$9) as the CO dataset" (2.2 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- ALMA calibration and CO imaging procedures  
  > "We direct the reader to (cite: Matra2017a) for a detailed description of the calibration and CO imaging procedures." (2.2 ALMA) [from (cite: Matra2017a)]
- Spectro-spatial filtering technique  
  > "we implement a spectro-spatial filtering technique similar to that introduced in (cite: Matra2015)" (3.2) [from (cite: Matra2015)]
- Steady-state exocometary release model and NLTE excitation details  
  > "use the steady state exocometary gas release model of (cite: Matra2015; Matra2017b) and expand it" (4.1) [from (cite: Matra2015; Matra2017b)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA calibration scripts and CASA version
- Clean parameters (weighting, thresholds, masks, taper values) for SMA and ALMA
- Taper values to match ALMA CO beam
- Mask definition and number of independent channels in filtering
- Electron density and temperature adopted for the final 2.5% limit
- Stellar spectrum from private communication
- Distance to beta Pic

## Analysis recipe

1. **Measure continuum and CO J=2-1 with SMA**: Gaussian fit to visibilities at baselines <30 kλ; moment 0 and moment 1 maps  
  > "obtained by fitting a Gaussian to the visibilities at baselines shorter than 30 k$\lambda$" (3.1)
   - software: miriad
   - parameter: moment 0 integrated within ±7 km/s of stellar velocity  
  > "spectrally integrating the datacube within $\pm 7$ km/s of the stellar velocity" (3.1)
   - fitting: Gaussians fit to spectra at every spatial location for moment 1  
  > "This centroid was obtained by fitting Gaussians to spectra at all spatial locations." (3.1)
   - validation: Compared with previous ALMA CO and continuum measurements  
  > "the CO J=2-1 line shape and integrated line flux are consistent with the previous ALMA measurements" (3.1)
2. **Derive upper limits on non-CO molecules**: Shift spectra by CO moment 1 velocity, integrate over CO spatial mask, 3σ limit = RMS × independent channels across CO line width; also unfiltered limits over continuum region within ±5 km/s  
  > "We measure the filtered integrated flux upper limits by multiplying the filtered spectrum’s root mean square (RMS, measured away from the line frequency) by the number of independent spectral channels" (3.2)
   - assumption: All molecules share CO's spectro-spatial distribution  
  > "we here assume emission from all molecules to have similar spectro-spatial distributions of emission as observed for the CO molecule" (3.2)
   - fitting: _not stated_
   - validation: Filtering demonstrated on detected CO; agnostic unfiltered limits computed  
  > "we also calculate upper limits in a more agnostic way by spatially integrating the unfiltered data cubes over regions where the mm continuum is detected" (3.2)
3. **Compute photodissociation timescales**: Unshielded rates from Heays2017 cross sections in stellar spectrum plus ISRF; CO self-shielding included  
  > "The radiation field includes both the observed spectrum of the $\beta$ Pic star and the interstellar radiation field (ISRF)." (4.2)
   - assumption: Destruction dominated by photodissociation; CN from HCN photodissociation; no shielding for non-CO species  
  > "We neglect self-shielding and shielding by CO for all other molecules" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **NLTE excitation including fluorescence for CO and CN**: Statistical equilibrium over rotational, vibrational and electronic levels with collisions from electrons, CMB, stellar and dust radiation  
  > "the total rate of radiative and collisional transitions populating each of N$_{\rm lev}$ energy levels is equated to the total rate of transitions depopulating the level." (Appendix A)
   - assumption: Collisional excitation of vibrational/electronic levels neglected; hyperfine splitting neglected  
  > "We neglect hyperfine splitting of the lines" (Appendix A)
   - fitting: _not stated_
   - validation: LTE limit matches Boltzmann distribution  
  > "our statistical equilibrium results match the analytical calculation from the Boltzmann distribution" (Appendix A)
5. **Convert CN/CO flux limit to HCN/(CO+CO2) outgassing ratio**: Apply steady-state line flux ratio equation with Einstein A, upper level populations and photodissociation timescales  
  > "Plugging CN/CO ratios of upper level populations, photodissociation timescales and observed fluxes into Eq. [\[eq:releaseratetoflux\]](#eq:releaseratetoflux) allows us to derive an upper limit on the HCN/CO ratio of outgassing rates" (Deriving the HCN/(CO+CO$_2$) ratio of outgassing rates)
   - assumption: CO2 released with CO and photodissociates to CO  
  > "CO gas is also produced via rapid photodissociation of CO$_2$ gas." (4.4)
   - fitting: _not stated_
   - validation: _not stated_
6. **Predict line fluxes for future surveys**: LTE line flux ratios relative to CO for Solar System comet abundances, best transition by effective S/N, optical depth correction  
  > "We select the best observable transition for each temperature and molecule to be that with the highest ‘effective S/N’." (5.2)
   - parameter: gas kinetic temperature 52 K to 210 K; stellar field at 85 AU  
  > "We vary the gas kinetic temperature between 52 K (cite: Kral2016) and 210 K (cite: Matra2017a)." (5.2)
   - assumption: All species co-located with CO; LTE excitation  
  > "First, we assume all species are co-located with CO, leading to similar spatial distributions and excitation conditions." (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIR** : SMA calibration  
  > "All of the calibration was performed using the `MIR`[^1] software package." (2.1 SMA)
- **miriad** : SMA continuum and line imaging and clean  
  > "Continuum and spectral line imaging and clean deconvolution were done in the `miriad` package." (2.1 SMA)
- **CASA** : listed in software section; ALMA processing  
  > "MIR, miriad (cite: Sault1995), CASA (cite: McMullin2007), Matplotlib (cite: Hunter2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMA 222 GHz continuum flux | 21.0 | 3.0 | mJy | 1 | Flux density measurements from the SMA observations at 222 and 274 GHz are $21.0\pm3.0$ mJy and $25.9\pm6.4$ mJy, respectively |
| SMA 274 GHz continuum flux | 25.9 | 6.4 | mJy | 1 | Flux density measurements from the SMA observations at 222 and 274 GHz are $21.0\pm3.0$ mJy and $25.9\pm6.4$ mJy, respectively |
| SMA CO J=2-1 line flux | 3.9 | 0.8 | Jy km/s | 1 | /              /                       /         /      3.9$\pm$0.8       /  SMA   /  1   / |
| ALMA CO J=2-1 line flux | 4.5 | 0.5 | Jy km/s | 1 | 4.5$\pm$0.5       /  ALMA  /  2 |
| CN N=2-1 3σ upper limit | <=1.0 (1.2 unfiltered) | not stated | Jy km/s | 2 | $\leqslant$1.0 (1.2)  /  SMA |
| HCN J=3-2 3σ upper limit | <=2.0 (1.4) | not stated | Jy km/s | 2 | $\leqslant$2.0 (1.4)  /  SMA |
| Unshielded CO photodissociation lifetime | 42 | not stated | yr | 3 | We therefore revise the unshielded CO photodissociation lifetime from 120 yrs (cite: Kamp2000; Dent2014) down to 42 yrs. |
| CO lifetime with self-shielding | ~105 | not stated | yr | 3 | the CO lifetime increases from 42 to $\sim$105 yrs |
| CN unshielded photodissociation timescale | 16 | not stated | yr | 3 | unshielded photodissociation timescales of 96, 42 and 16 years |
| CN/CO upper level population ratio | 0.49 to 0.71 | not stated | dimensionless | 4 | the ratio in fractional upper level populations between CN and CO varies between 0.49 and 0.71 |
| Updated total CO mass | 3.6e-5 | +0.9/-0.6 e-5 | Earth masses | 4 | we report an updated value of $3.6^{+0.9}_{-0.6}\times10^{-5}$ M$_{\oplus}$ |
| HCN/(CO+CO2) outgassing rate ratio upper limit | <2.5 | not stated | percent | 5 | sets the most conservative upper limit of 2.5% on the HCN/CO ratio of outgassing rates |
| Herschel PACS OH 3σ upper limit | 2.1e2 | not stated | Jy km/s | 6 | set a 3$\sigma$ upper limit on the integrated line flux of 2.1$\times$10$^2$ Jy km/s |

## Qualitative findings

- Only CO is detected; non-detections of other molecules are explained by rapid photodissociation in the strong UV field; CN is the longest-lived after CO.  
  > "CN is the longest-lasting and most easily detectable molecule after CO in this environment." (abstract)
- UV fluorescence plays a key role in CO and CN excitation in the low-density regime.  
  > "finding it plays a key role in CO and CN excitation" (abstract)

## Claim tuples

- H: Can molecules other than CO be detected in the beta Pic gas disk? | E: SMA and archival ALMA line searches with CO-template spectro-spatial filtering | R: No detections other than CO; 3σ limits e.g. CN <=1.0 Jy km/s | F: Non-detections attributable to rapid photodissociation | **supported**
- H: How does the HCN/(CO+CO2) outgassing ratio compare to Solar System comets? | E: Convert CN/CO limit using NLTE+fluorescence populations and photodissociation timescales | R: Upper limit of 2.5% | F: Consistent with but at the low end of comet range | **supported**
- H: Will future ALMA surveys detect CN and HCN around beta Pic? | E: LTE line flux predictions for Solar System comet abundances vs facility sensitivities | R: CN, HCN and OH are promising | F: CN and HCN should be readily detectable with ALMA | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Spectro-spatial filtering with CO template maximizes S/N by removing noise-dominated pixels/channels  
  > "This maximizes the signal-to-noise ratio by effectively removing noise-dominated pixels/channels." (3.2)
- Alternative: CN destruction by atomic oxygen (timescale ~3 yr) neglected due to uncertain O abundance  
  > "Given the uncertainty on the oxygen abundance, however, we opt to neglect this destruction pathway of CN in this work." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Predictions assume LTE and CO-like distribution; OH prediction sensitive to temperature and spatial distribution.  
  > "our prediction is very sensitive to the choice of OH temperature or spatial distribution, which may be oversimplified here" (5.2)
- Caveat (inferred, ours): Upper limits rely on assumption that all molecules follow CO distribution, though CN daughter products would be more compact
- Caveat (inferred, ours): Neglecting CN destruction by O could change the limit by a factor of a few
- Caveat (inferred, ours): Electron density and HCN-only origin of CN are assumed
- Caveat (inferred, ours): Final limit is conservative and not tied to a stated uncertainty budget

## Reproducibility

- Data public (paper): ALMA data from archive project 2012.1.00142.S; SMA data availability not stated  
  > "We extracted ALMA Band 6 observations of $\beta$ Pictoris from the archive (project number 2012.1.00142.S)" (2.2 ALMA)
- Products in archive: _not stated_
- Missing: SMA data archive location
- Missing: Stellar spectrum (private communication)
- Missing: Full imaging parameters
- Missing: NLTE code not released
- Data volume (inferred): ALMA Band 6 12m+ACA, tens of GB; SMA small
- Score (inferred): 4/5, ALMA data public and the filtering and flux ratio steps are described, but heavy reliance on prior papers, SMA data and a custom NLTE code limit reproduction.
- Rediscovery candidate: no, Main results are non-detections and model-dependent limits requiring SMA data and unreleased NLTE code.

## Links

- Method: (cite: Matra2015) (Spectro-spatial filtering and NLTE excitation model)
- Method: (cite: Matra2017a) (ALMA calibration and CO imaging of beta Pic)
- Companion: (cite: Dent2014) (Original ALMA CO detection in beta Pic)

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 52,
  "rate": 0.612
 },
 "evidence_ok": true
}
```
