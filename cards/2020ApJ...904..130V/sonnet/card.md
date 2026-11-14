# Kiloparsec-scale ALMA Imaging of [C II] and Dust Continuum Emission of 27 Quasar Host Galaxies at z ∼ 6

`2020ApJ...904..130V` | The Astrophysical Journal 2020 | first author: Venemans, Bram P. | arXiv: 2010.14874 | DOI: 10.3847/1538-4357/abc563

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the sizes, morphologies, positions relative to the black hole, SFR densities, [C II]/FIR ratios and environments of 27 z~6 quasar host galaxies at ~1 kpc resolution?  
  > "We therefore initiated a comprehensive study of $z\sim6$ quasar host galaxies using all available high-spatial-resolution FIR observations to probe the gas and dust on scales of $\sim$1 kpc." (Introduction)
- Target **27 quasars at z>5.7 (e.g. P007+04, J0100+2802, J1342+0928, P308-21)**: coordinates Table 1 lists ICRS positions of optical/NIR point sources, corrected with Gaia DR2  
  > "| P007+04    | 00$^\mathrm{h}$28$^\mathrm{m}$06$.\!\!^\mathrm{s}$568 | +04$^\circ$57$^\prime$25.39$''$ |" (Table 1); z/distance z_[CII] from 5.7788 to 7.5400 (Table 2)  
  > "| P007+04    | 00$^\mathrm{h}$28$^\mathrm{m}$06$.\!\!^\mathrm{s}$568 | +04$^\circ$57$^\prime$25.39$''$ |" (Table 1); distance from [C II] redshift fitted from spectra; cosmology H0=70, OmegaM=0.3  
  > "| P007+04    | 00$^\mathrm{h}$28$^\mathrm{m}$06$.\!\!^\mathrm{s}$568 | +04$^\circ$57$^\prime$25.39$''$ |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00240.S, 2012.1.00882.S, 2013.1.00273.S, 2015.1.00399.S, 2015.1.00692.S, 2016.A.00018.S, 2017.1.00396.S, 2017.1.01301.S, 2018.1.00908.S
- bands: _not stated_
- frequencies and spectral setup: two overlapping 1.875 GHz sidebands covering [C II] (~3.3 GHz, ~3600 km/s at z=6); two further 1.875 GHz continuum bandpasses ~15 GHz away  
  > "for most sources two overlapping sidebands (SPWs), of 1.875 GHz wide each, were used to cover the redshifted [C II] line" (2.2 ALMA Observations); "Two other bandpasses of 1.875 GHz each were placed $\sim$15 GHz away, probing only continuum emission." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 34 to 49 antennas  
  > "The number of antennas was 34 to 49" (2.2 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.1'' to 0.33''  
  > "the spatial resolution varies from 0.1$''$ to 0.33$''$" (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.13 to 0.54 mJy/beam per 30 MHz channel  
  > "The rms in the bandpasses containing the redshifted [C II] line ranged from 0.13 to 0.54 mJy beam$^{-1}$ per 30 MHz channel" (2.2 ALMA Observations)
- time on source: 16 to 161 min per dataset  
  > "The on-source integration time for each dataset ranged from 16 to 161 min" (2.2 ALMA Observations)
- observing dates: 2013 July 5 to 2019 September 24  
  > "The observations were carried out between 2013 July 5 and 2019 September 24." (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um fine structure (1900.54 GHz)
- Other facility **Gaia DR2**: astrometric correction of optical/NIR quasar positions  
  > "We corrected the position of stars within 2$'$ of the quasar in the optical/near-infrared catalogs that had a match in the Gaia DR2 catalog" (2.3 Optical/Near-infrared Coordinates)
- Other facility **Pan-STARRS1 and VIKING**: optical/NIR quasar positions  
  > "taken from catalogs of large surveys such as the Pan-STARRS1 survey (cite: cha16) and the near-infrared VIKING survey (cite: edg13)" (2.3 Optical/Near-infrared Coordinates)
- External data: quasar bolometric luminosities  
  > "The bolometric luminosity $L_\mathrm{bol}$ of the quasars was taken from the literature (cite: ven18)." (4.2 Star Formation Rate Density) [from (cite: ven18)]
- External data: J0305-3150 results in Table 2 taken from higher S/N data  
  > "Table notes: $^{a}$ Values taken from (cite: ven19)." (Table 2) [from (cite: ven19)]

## Processing

### Calibration

- pipeline or manual: standard pipeline with a few exceptions; details in Novak et al. 2020  
  > "The calibration of the data was performed using the standard pipeline, with a few exceptions." (2.2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "The reduced measurement sets were subsequently imaged using the CASA task tclean using Briggs weighting with the robust parameter set to robust=0.5." (2.2 ALMA Observations)
- deconvolver: mtmfs, nterms=2 for continuum maps  
  > "We created maps of the continuum emission by setting the deconvolver in tclean to mtmfs (multiterm multifrequency synthesis) with the number of Taylor coefficients set to two" (2.2 ALMA Observations)
- weighting robust: Briggs robust=0.5  
  > "The reduced measurement sets were subsequently imaged using the CASA task tclean using Briggs weighting with the robust parameter set to robust=0.5." (2.2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: cleaned down to 2 sigma  
  > "For all cubes and maps, we cleaned down to 2$\sigma$ with $\sigma$ being the rms noise." (2.2 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, fitorder=1  
  > "We subtracted the continuum in $uv$ space using the task uvcontsub with the polynomial order of the fit set to fitorder=1." (2.2 ALMA Observations)
- line free channels: channels at least 1.25 x FWHM of [C II] from line peak  
  > "The continuum was defined as all channels in two bandpasses surrounding the [C II] line that were at least 1.25 $\times$ FWHM of the [C II] line away from the peak of the line." (2.2 ALMA Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- data reduction and calibration details  
  > "For details on the data reduction and calibration, we refer to the accompanying paper by (cite: nov20)." (2.2 ALMA Observations) [from (cite: nov20)]
- residual-scale spectral extraction method  
  > "This method is described in detail in (cite: nov19; nov20)." (3.1 [C II] Spectra) [from (cite: nov19; nov20)]
- line search procedure  
  > "We followed a procedure that is similar to that described in (cite: gon19) but with a few differences." (3.3 Line Emitters in the Field) [from (cite: gon19)]
- dust SED T_d=47 K, beta=1.6  
  > "Following the literature, we assume that the dust SED can be described by a modified blackbody with a dust temperature of $T_d=47$ K and an emissivity index of $\beta=1.6$" (3.1 [C II] Spectra) [from (cite: bee06; lei14; ven18)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel selection and pipeline exceptions per dataset (in Novak et al. 2020)
- Cell size and image size for tclean
- Multiscale or deconvolution settings
- Details of annulus definitions and radial profile extraction for SFRD and [C II]/FIR
- Fit method/errors for the power-law in Sigma_[CII]/FIR vs Sigma_FIR
- Positional uncertainty combination for offsets
- Primary beam correction

## Analysis recipe

1. **image cubes and maps**: tclean with robust=0.5; 30 MHz channel cubes; uvcontsub; [C II] moment-0 averaging 1.2xFWHM; mtmfs continuum maps  
  > "intensity maps were created by averaging the channels 1.2 $\times$ FWHM around the peak of the [C II] line." (2.2 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **extract and fit total [C II] spectra**: aperture extraction (radii 0.4-1.5'') with residual scale method; single Gaussian plus constant continuum  
  > "We fitted a single Gaussian with a constant continuum to each of the extracted spectra." (3.1 [C II] Spectra)
   - fitting: single Gaussian + constant continuum  
  > "We fitted a single Gaussian with a constant continuum to each of the extracted spectra." (3.1 [C II] Spectra)
   - validation: _not stated_
3. **derive luminosities and SFR**: L_[CII] from line flux; L_FIR (42.5-122.5 um) from continuum at 1900 GHz with CMB correction; SFR = 2.1e-10 L_FIR  
  > "we compute the SFR from $L_{\mathrm{FIR}}$ using" (3.1 [C II] Spectra)
   - assumption: modified blackbody T_d=47 K, beta=1.6; Kroupa IMF; L_TIR=1.41 L_FIR; SED systematic factor ~2-3  
  > "The systematic uncertainty on the FIR luminosity due to the unknown shape of the dust SED is a factor of $\sim$2–3 (cite: ven18)." (3.1 [C II] Spectra)
   - fitting: _not stated_
   - validation: _not stated_
4. **measure sizes and positions**: 2D Gaussian fits to [C II] and continuum maps with imfit; centroids compared to Gaia-corrected optical positions  
  > "We measured the extent of the sources in both the [C II] and continuum map by fitting a 2D Gaussian to the sources using the CASA task imfit." (3.2 2D Maps and Size Measurements)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
5. **blind line-emitter search and clustering**: S/N>3 pixel search per channel in 56 cubes, Gaussian smoothing in frequency up to 400 MHz, fidelity from negative peaks (>=0.8), visual vetting; overdensity delta=(n_obs-n_exp)/n_exp  
  > "We searched the cubes by channel for pixels reaching an S/N threshold of 3." (3.3 Line Emitters in the Field)
   - assumption: candidates with |dv|<2000 km/s taken as [C II] companions  
  > "We therefore conservatively assume that sources with a velocity difference of $\Delta v < 2000$ km s$^{-1}$ are associated with the quasar." (4.4 Galaxy Clustering)
   - fitting: _not stated_
   - validation: fidelity from inverted cubes; channel maps on/off line; visual inspection  
  > "we first repeated the line search process except we inverted the cube, searching for the brightest negative peaks at various line widths." (3.3 Line Emitters in the Field)
6. **radial SFRD and [C II]/FIR profiles; power-law fit**: annuli profiles around dust peak; power-law fit of Sigma_[CII]/FIR vs Sigma_FIR  
  > "We fitted a power-law to the data in Figure [10](#fig:ciifirfir) and found the following relation:" (4.3 The [C II]-to-FIR Ratio)
   - assumption: single dust temperature everywhere  
  > "These discrepancies could be due to our assumption of a single dust temperature everywhere in the quasar host galaxies" (4.3 The [C II]-to-FIR Ratio)
   - fitting: _not stated_
   - validation: compared with Diaz-Santos 2014 slope  
  > "The slope of this correlation is very similar to the one published by (cite: dia14), who found a slope of $-0.39\pm0.07$" (4.3 The [C II]-to-FIR Ratio)

## Software

- **CASA** : reduction, tclean imaging, uvcontsub, imfit  
  > "The data were reduced following the standard reduction steps using the Common Astronomy Software Applications package (cite: mul07)." (2.2 ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] central emission size range | 1.0-4.8 | not stated | kpc | 4 | The [C II] emission in the bright, central regions of the quasars have sizes of 1.0–4.8 kpc. |
| quasars with companion galaxies | 13/27 (48%) | not stated | dimensionless | 5 | We find that 13 quasars (48%) have companion [C II]-emitting galaxies in the field |
| overdensity of companions, dv<2000 km/s | 2.4 | not stated | dimensionless | 5 | We find an overdensity of $\delta = 2.4$ for companions with $\Delta v < 2000$ km s$^{-1}$. |
| Pearson r, peak FIR surface density vs L_bol | -0.04 | not stated | dimensionless | 6 | (the Pearson correlation coefficient is $r=-0.04$) |
| Sigma_[CII]/FIR power-law slope | -0.447 | not stated | dimensionless | 6 | \Sigma_\mathrm{[CII]/FIR} = 9.6\times10^{-4} \left(\frac{\Sigma_\mathrm{FIR}}{10^{11} L_\odot\,\mathrm{kpc}^{-2}}\right)^{-0.447} |
| peak SFRD range | 30 to 1500 | not stated | Msun/yr/kpc^2 | 6 | from 30 $M_\ensuremath{\odot}$ yr$^{-1}$ kpc$^{-2}$ to 1500 $M_\ensuremath{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| mean L_[CII] of sample | 3.0e9 | not stated | Lsun | 3 | with a mean of $3.0\times10^9$ $L_\ensuremath{\odot}$ |

## Qualitative findings

- Dust continuum is more compact than [C II]  
  > "the continuum emission is more centrally concentrated than the [C II] emission" (3.2 2D Maps and Size Measurements)

## Claim tuples

- H: Black holes sit at the center of the host ISM | E: Compare Gaia-corrected optical positions with imfit centroids of dust and [C II] | R: Offsets mostly <0.1''; outliers up to ~750 pc | F: ISM and black hole are cospatial; outliers linked to mergers | **supported**
- H: The AGN dominates central dust heating | E: Compare peak FIR surface density with L_bol | R: r=-0.04 | F: dust predominantly heated by star formation | **supported**
- H: Quasars are clustered with companions | E: Blind line search in 56 cubes | R: 19 candidates within 2000 km/s vs ~5 expected | F: overdensity delta=2.4 (lower limit) | **supported**
- H: [C II] deficit in centers | E: Radial [C II]/FIR profiles | R: lowest few e-4 centrally, rising outward | F: intense radiation field may cause deficit | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: robust=0.5 chosen to optimize S/N and resolution  
  > "This value optimizes both signal-to-noise ratio (S/N) and spatial resolution." (2.2 ALMA Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Single dust temperature assumed; position offsets not corrected for differential chromatic refraction; sizes only for bright central emission  
  > "It should be noted that the position and uncertainties in the table do not account for systematic offsets that are due to differential chromatic refraction" (2.3 Optical/Near-infrared Coordinates)
- Caveat (inferred, ours): FIR/SFR rely on a single assumed T_d=47 K; radial dust temperature gradients could change profiles
- Caveat (inferred, ours): Gaussian size fits ignore substructure and low-S/N extended emission
- Caveat (inferred, ours): Line search candidates assumed [C II]; contamination by foreground CO
- Caveat (inferred, ours): Heterogeneous archival data, sample selection biased to bright sources

## Reproducibility

- Data public (paper): ALMA data from listed projects acknowledged; archive use implied  
  > "This paper makes use of the following ALMA data:" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration exceptions (Novak et al. 2020)
- Missing: Imaging cell/image sizes
- Missing: Annulus definitions and fitting details
- Data volume (inferred): Roughly 0.5-1 TB of raw ALMA data across 10 projects
- Score (inferred): 3/5, Data are archival and main steps are described, but calibration and several imaging parameters are deferred or omitted.
- Rediscovery candidate: no, Calibration and imaging details are deferred to companion papers, so the recipe is not complete enough to redo from this paper alone.

## Links

- Method: (cite: nov20) (data reduction, calibration and residual scale spectral extraction)
- Method: (cite: gon19) (line search procedure)
- Companion: (cite: nov20) (extended [C II] and outflow analysis)
- Companion: Neeleman M. et al. (2020, in preparation) ([C II] kinematics and dynamical masses)
- Related: ALMA [C II] z~6 quasar survey (Decarli et al. 2018)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00544.S"
 ],
 "codes_printed_but_missing": [
  "2016.1.00544.S",
  "2016.A.000018.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 42,
  "rate": 0.56
 },
 "evidence_ok": true
}
```
