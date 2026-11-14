# VLA and ALMA Imaging of Intense Galaxy-wide Star Formation in z ∼ 2 Galaxies

`2016ApJ...833...12R` | The Astrophysical Journal 2016 | first author: Rujopakarn, W. | arXiv: 1607.07710 | DOI: 10.3847/0004-637X/833/1/12

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Where and over what area does intense star formation occur in main-sequence star-forming galaxies at z~2, as traced by VLA 5 cm and ALMA 1.3 mm imaging, relative to their stellar mass distribution?  
  > "focusing on the extinction-independent distributions of the star formation in SFGs at $z = 1-3$." (1 Introduction)
- Target **11 VLA+ALMA selected SFGs in the HUDF (UDF1-UDF16)**: coordinates Table 1 lists VLA positions, e.g. UDF1 53.18346, -27.77664 deg (J2000)  
  > "The sample has a median redshift of $z = 2.2$" (Results); "IDs, stellar mass (M$_*$), SFR$_{\rm IR}$, and redshift ($z$) are from D16." (Table 1); z/distance z = 1.3-3.0, median 2.2  
  > "The sample has a median redshift of $z = 2.2$" (Results); "IDs, stellar mass (M$_*$), SFR$_{\rm IR}$, and redshift ($z$) are from D16." (Table 1); distance from spectroscopic (e.g. VLT/MUSE) and photometric redshifts compiled by D16  
  > "The sample has a median redshift of $z = 2.2$" (Results); "IDs, stellar mass (M$_*$), SFR$_{\rm IR}$, and redshift ($z$) are from D16." (Table 1)

## Data provenance

- ALMA projects: 2012.1.00173.S
- bands: ALMA 1.3 mm; VLA C-band 4-8 GHz (5 cm)  
  > "The ALMA HUDF Deep Field is a 1.3-mm survey of the 4.5-arcmin$^2$ HUDF using a 45-pointing mosaic" (Observations and Ancillary Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA 0.37'' x 0.48'' beam; VLA 0.31'' x 0.61''  
  > "the synthesized beam is $0.37\ensuremath{''} \times 0.48\ensuremath{''}$" (Observations and Ancillary Data)
- max recoverable scale: _not stated_
- sensitivity: ALMA rms 29 uJy/beam (natural weighting); VLA rms 0.32 uJy/beam  
  > "The rms noise of the naturally-weighted ALMA map is 29 $\mu$Jy beam$^{-1}$" (Observations and Ancillary Data)
- time on source: ALMA ~20 hours total; VLA 177 hours  
  > "We observed the HUDF for 177 hours in the A, B, and C configurations" (Observations and Ancillary Data)
- observing dates: ALMA 2014 July - 2015 May, 13 sessions; VLA 2014 March - 2015 September  
  > "during 2014 July $-$ 2015 May in 13 sessions, utilizing a total of approximately 20 hours" (Observations and Ancillary Data)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 5 cm continuum imaging of the HUDF (program VLA/14A-360)  
  > "this paper makes use of VLA data from program VLA/14A-360" (Acknowledgments)
- Other facility **HST**: Stellar-mass maps from spatially-resolved SED fitting, morphology classification  
  > "from which we construct stellar-mass maps by fitting spatially-resolved SEDs" (Observations and Ancillary Data)
- Other facility **Chandra 4 Ms**: X-ray AGN identification  
  > "We identify X-ray AGN using the 4 Ms *Chandra* catalog (cite: Xue11)" (Observations and Ancillary Data)
- External data: SFR_IR, stellar masses, redshifts, ALMA/VLA flux densities for sample  
  > "IDs, stellar mass (M$_*$), SFR$_{\rm IR}$, and redshift ($z$) are from D16." (Table 1) [from Dunlop16]
- External data: Chandra X-ray catalog  
  > "We identify X-ray AGN using the 4 Ms *Chandra* catalog (cite: Xue11)" (Observations and Ancillary Data) [from Xue11]
- Simulation/model as data: Rieke09 infrared SED library used to predict S5cm/S1.3mm  
  > "in comparison with the ratio predicted by the (cite: Rieke09) infrared SED library" (3.1)

## Processing

### Calibration

- pipeline or manual: ALMA: calibration with CASA; VLA: VLA Data Reduction Pipeline plus RFI removal  
  > "Calibration was carried out with CASA and imaging with the task `CLEAN`" (Observations and Ancillary Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: J0334-301; VLA: 3C48  
  > "Each session observed J0334-301 for flux and bandpass calibrations" (Observations and Ancillary Data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: ALMA: CLEAN; VLA: TCLEAN  
  > "imaging with the task `CLEAN`, adopting natural weighting to maximize sensitivity" (Observations and Ancillary Data)
- deconvolver: VLA MT-MFS nterms=2; ALMA no deconvolution  
  > "Deconvolution was not performed as there are no strong sidelobes from 1.3-mm objects in the HUDF." (Observations and Ancillary Data)
- weighting robust: ALMA natural; VLA Briggs robust 0.5  
  > "Briggs weighting with robust parameter of 0.5" (Observations and Ancillary Data)
- uv taper: Multiple uv tapering scales for size measurement, highest S/N adopted  
  > "We also construct images at multiple $u,v$ tapering scales to accurately measure sizes of extended sources" (3.2)
- cell size: VLA 0.06'' pixel  
  > "$0.06\ensuremath{''}$ pixel size" (Observations and Ancillary Data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ALMA 0.37'' x 0.48''; VLA 0.31'' x 0.61''  
  > "The final image has a $0.31\ensuremath{''} \times 0.61\ensuremath{''}$ synthesized beam" (Observations and Ancillary Data)
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations, data reduction, source extraction  
  > "Details of the ALMA observations, data reduction, and source extraction are given in a companion paper on the ALMA HUDF survey (cite: Dunlop16)." (Observations and Ancillary Data) [from Dunlop16]
- Stellar-mass map construction via spatially-resolved SED fitting  
  > "using the procedures described by (cite: Cibinel15)" (Observations and Ancillary Data) [from Cibinel15]
- X-ray AGN luminosity cut  
  > "L$_{\rm X}$($0.5-8$ keV) $\geqslant 3 \times 10^{42}$ erg s$^{-1}$ following (cite: Xue11)" (3.1) [from Xue11]

### Not stated but needed to reproduce (our reading)

- ALMA calibration details, CASA version, flagging and spectral setup (deferred to Dunlop16)
- Exact uv taper scales used
- Size/ellipse treatment for circularization and half-light radius conversion
- SFR_IR and stellar mass SED-fitting details (in D16)
- Dust opacity normalization used with Li & Draine
- Asymmetry/M20 classification thresholds
- Aperture/PyBDSM parameters and injection simulation details

## Analysis recipe

1. **Measure star-formation sizes**: Deconvolved 2D elliptical Gaussian fitting of VLA and ALMA images, circularized half-light radius; combine bands per AGN criteria  
  > "deconvolved source sizes determined from 2D elliptical Gaussian fitting" (3.2)
   - software: PyBDSM
   - parameter: Islands above 3 sigma; multiple Gaussians allowed  
  > "all Gaussian components from the same flux ‘island’ above 3$\sigma$ are grouped together into a source" (3.2)
   - fitting: _not stated_
   - validation: Injected simulated sources into HUDF maps; no size bias down to S/N 4  
  > "We find no bias in extracted sizes down to our S/N limit of 4" (3.2)
2. **Compare SF location with stellar mass**: Half-mass radius from stellar-mass maps and separation of barycenters  
  > "The location of star-formation concentration in relation to the hosts’ stellar-mass concentration is quantified by the separation between their barycenters" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Test far-infrared/radio correlation and identify AGN**: Compare S5cm/S1.3mm vs redshift to Rieke09 template; radio AGN if excess >2x highest SF template level  
  > "We classify as radio AGN those with S$_{5\,{\rm cm}}$ enhancement greater than two times the highest level expected from star-forming SED templates" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive dust mass, gas fraction, depletion time**: Dust masses from 1.3 mm flux with Li & Draine opacities; gas = 100 x dust  
  > "We estimate the dust masses from the 1.3 mm fluxes using the (cite: LiDraine01) dust mass absorption coefficients." (3.3)
   - assumption: T_dust = 25 K (20-30 K for uncertainty); gas-to-dust ratio 100  
  > "prompting us to adopt T$_{\rm dust} = 25$ K" (3.3)
   - fitting: _not stated_
   - validation: Compared with Magdis12 stacking dust masses  
  > "The dust mass estimates are in agreement with the (cite: Magdis12) results of stacking analysis" (3.3)
5. **Derive SFR surface density**: SFR averaged over area defined by r_SF  
  > "The $\Sigma_{\rm SFR}$ is averaged over the entire star-formation surface areas indicated by r$_{\rm SF}$." (Table 3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : VLA and ALMA calibration and imaging (TCLEAN, CLEAN)  
  > "Data reduction was carried out with CASA (cite: McMullin07)" (Observations and Ancillary Data)
- **PyBDSM** : Gaussian source size fitting  
  > "This is carried out with PyBDSM" (3.2)
- **Web-PIMMS** : X-ray column densities  
  > "based on `Web-PIMMS`" (3.5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median r_SF | 2.1 | 0.9 | kpc | 1 | We find a median SFGs’ r$_{\rm SF}$ of $2.1 \pm 0.9$ kpc. |
| Median r_Mstar | 2.6 | 0.7 | kpc | 2 | median r$_{\rm M_*} = 2.6 \pm 0.7$ kpc |
| Median star-formation diameter | 4.2 | 1.8 | kpc | 1 | The median star-formation diameter in our main-sequence SFGs sample is $4.2 \pm 1.8$ kpc |
| Median Sigma_SFR | 2.5 | not stated | Msun/yr/kpc^2 | 5 | median $\Sigma_{\rm SFR}$ $= 2.5$ ${\rm M}_\odot$yr$^{-1}$kpc$^{-2}$ |
| Rms scatter of S5cm/S1.3mm around template | 0.03 | not stated | dex | 3 | the rms scatter of the ratio for these five objects around this template is 0.03 dex |
| Average gas fraction | 0.5 | 0.2 | dimensionless | 4 | is on average $0.5 \pm 0.2$ |
| Average gas depletion time | 0.4 | 0.2 | Gyr | 4 | is $0.4 \pm 0.2$ Gyr |
| Median separation of SF and stellar-mass barycenters | 0.36 r_Mstar (0.9 kpc) | not stated | r_Mstar | 2 | the median separation is 0.36 r$_{\rm M_*}$, corresponding to 0.9 kpc |

## Qualitative findings

- Star formation occurs nearly co-spatially with stellar-mass concentrations over galaxy-wide areas; VLA and ALMA trace the same regions  
  > "indicating that star formation occurs nearly co-spatially with the stellar-mass concentration" (3.2)

## Claim tuples

- H: VLA and ALMA trace the same extent of star formation in individual main-sequence SFGs | E: Compared S5cm/S1.3mm to SED template and r1/2 from both bands | R: Scatter 0.03 dex for 5 non-AGN; r1/2 agree except UDF2 | F: FIR/radio correlation holds and both bands are interchangeable for non-AGN | **supported**
- H: Star formation in z~2 main-sequence SFGs is galaxy-wide | E: Measured r_SF vs stellar mass half-mass radius | R: median r_SF 2.1 kpc vs r_M* 2.6 kpc | F: Star formation extends over area comparable to stellar mass | **supported**
- H: Compact star formation emerges above a characteristic SFR | E: Compared sizes with ALMA SMGs | R: SFG radii 2-4 times larger than SMGs with 3-8 times higher SFR | F: Threshold SFR ~300 Msun/yr | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Radio and mm continuum give extinction-independent, complementary star-formation tracers  
  > "The combination of the two surveys therefore provides complementary strengths" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample; FIR/radio test on only five SFGs; thermal fraction at 5 cm uncertain  
  > "Although we are only able to investigate the correlation for five SFGs with SFRs $\sim 100$ ${\rm M}_\odot$yr$^{-1}$" (3.1)
- Caveat (inferred, ours): Sample of 11 ALMA-selected galaxies is biased to massive, high-SFR systems
- Caveat (inferred, ours): Sizes of low-S/N ALMA sources are uncertain, some only upper limits
- Caveat (inferred, ours): Dust mass depends on assumed T_dust and gas-to-dust ratio
- Caveat (inferred, ours): Sample selection and key inputs depend on companion paper D16

## Reproducibility

- Data public (paper): ALMA project code printed; VLA program 14A-360  
  > "this paper makes use of VLA data from program VLA/14A-360" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and ALMA calibration details (in Dunlop16)
- Missing: Catalogs of fluxes, SFR_IR, stellar masses from D16
- Missing: HST stellar-mass maps from Cibinel15 procedure
- Missing: PyBDSM settings and taper scales
- Data volume (inferred): ~100-300 GB for ALMA 45-pointing mosaic raw data; VLA 177 h data several TB
- Score (inferred): 3/5, ALMA data public, but calibration, SED-derived inputs and mass maps are deferred to companion papers; size measurement recipe moderately specified.
- Rediscovery candidate: no, Key inputs (SFR, masses, mass maps) come from other papers and VLA data volume is large.

## Links

- Method: Dunlop16 (ALMA observations, reduction, source extraction, SFR and stellar masses)
- Method: Cibinel15 (stellar-mass maps and asymmetry-M20 classification)
- Companion: Dunlop16 (ALMA HUDF survey)
- Related: ALMA HUDF survey
- Related: VLA HUDF 5 cm survey
- Related: CANDELS
- Related: 4 Ms Chandra Deep Field South

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
