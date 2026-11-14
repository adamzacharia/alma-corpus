# An Extreme Protocluster of Luminous Dusty Starbursts in the Early Universe

`2018ApJ...856...72O` | The Astrophysical Journal 2018 | first author: Oteo, I. | arXiv: 1709.02809 | DOI: 10.3847/1538-4357/aaa1f1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: What is the nature, star-formation rate, gas content and mass of the Dusty Red Core (DRC), an ultrared H-ATLAS source revealed as a z=4.002 proto-cluster of dusty star-forming galaxies?  
  > "In this paper we report on the nature of this unique system, along with the observations which led to its discovery." (1 Introduction)
- Target **DRC (Dusty Red Core)**: coordinates R.A. = 00:42:23.8, decl. = -33:43:34.8  
  > "This source was nicknamed the Dusty Red Core (DRC, R.A. = 00:42:23.8, decl. = $-$33:43:34.8), and it might represent the core of a larger proto-cluster of galaxies at $z_{\rm spec} = 4.002$." (1 Introduction); z/distance z_spec = 4.002  
  > "This source was nicknamed the Dusty Red Core (DRC, R.A. = 00:42:23.8, decl. = $-$33:43:34.8), and it might represent the core of a larger proto-cluster of galaxies at $z_{\rm spec} = 4.002$." (1 Introduction); distance from this paper, from CO(6-5), [CI](1-0), H2O lines in ALMA data  
  > "This source was nicknamed the Dusty Red Core (DRC, R.A. = 00:42:23.8, decl. = $-$33:43:34.8), and it might represent the core of a larger proto-cluster of galaxies at $z_{\rm spec} = 4.002$." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00449.S, 2013.A.00014.S, 2013.1.00001.S, 2016.1.01287.S
- bands: Band 3 (3 mm spectral scan), Band 4 (2 mm), 870 um high-resolution continuum  
  > "In project 2016.1.01287.S we observed DRC at $2 \, {\rm mm}$ in 14 SBs, each about $70 \, {\rm min}$ long" (2.2 ALMA observations)
- frequencies and spectral setup: Band 3 scan with five tunings covering 84–114.88 GHz  
  > "corresponding to the five tunings needed to cover most of ALMA band 3, between 84 and $114.88\,{\rm GHz}$." (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3 mm: 0.6–1.2''; DDT: ~2.0''; 870 um: ~0.12''; 2 mm: 1.68''x1.54''  
  > "with a synthesized beam size (fwhm) of $1.68'' \times 1.54''$ in both pointings." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 2 mm: ~50 uJy/beam per 100 km/s channel, ~6 uJy/beam continuum; 3 mm: ~0.75 mJy/beam per 100 km/s  
  > "The resulting r.m.s. sensitivity is $\sim 50 \, {\rm \mu Jy \, beam^{-1}}$ in $100 \, {\rm km \, s^{-1}}$ channels and $\sim 6\,{\rm \mu Jy\, beam^{-1}}$ in the continuum map" (2.2 ALMA observations)
- time on source: DDT ~1 hour; 2 mm 14 SBs of ~70 min each  
  > "In project 2013.A.00014.S we observed DRC for about one hour" (2.2 ALMA observations)
- observing dates: 3 mm scan 2014 Jul 3–Aug 28; DDT 2015 Jan 14  
  > "The observations were taken between 2014 July 03 and August 28, in a total of five scheduling blocks (SBs)" (2.2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: [CI] (1-0) (not stated)
- Line: 12CO 6-5 (not stated)
- Line: H2O 2_11-2_02 (not stated)
- Other facility **APEX/LABOCA**: 870 um wide-field map showing DSFG over-density  
  > "The wide-field LABOCA map at $870\,{\rm \mu m}$" (3 An extreme over-density of DSFGs)
- Other facility **ATCA**: CO(2-1) and radio continuum  
  > "The $^{12}$CO(2–1) emission from DRC was observed with the Australia Telescope Compact Array" (2.6 ATCA observations)
- Other facility **VLA**: 28/32 GHz continuum  
  > "Therefore, we utilize only the continuum map in this paper" (2.3 Jansky VLA observations)
- Other facility **VLT/MUSE**: Lya imaging  
  > "Using our MUSE observations of the proto-cluster core we have created a continuum-subtracted Ly$\alpha$ image" (4.5 Stellar and Lya emission)
- Other facility **Gemini/FLAMINGOS-2, VLT/FORS2, Spitzer/IRAC**: Ks, I band and 3.6/4.5 um imaging of stellar emission  
  > "Broad-band near-IR observations in the $K_s$ filter were carried out" (2.5 Gemini observations)
- External data: ALESS SED template used to convert 2 mm flux to LIR and SFR  
  > "by using the ALESS template (cite: Swinbank2014MNRAS.438.1267S), which represents the average FIR SED of the classical DSFG population at $z \sim 2.5$" (3 An extreme over-density of DSFGs) [from (cite: Swinbank2014MNRAS.438.1267S)]
- External data: sigma_DM,15 ~1083 km/s and alpha ~0.336 for velocity dispersion-mass relation  
  > "Using $\sigma_{\rm DM, 15} \sim 1,083 \, {\rm km \, s^{-1}}$ and $\alpha \sim 0.336$ (cite: Wang2016ApJ...828...56W)" (4.4 Velocity dispersion and total mass) [from (cite: Wang2016ApJ...828...56W)]
- External data: Total IR luminosity-halo mass relation at z=4  
  > "we estimate the total mass using the relation between the total IR luminosity and halo mass at $z = 4$ by (cite: Aversa2015ApJ...810...74A)" (4.4 Velocity dispersion and total mass) [from (cite: Aversa2015ApJ...810...74A)]

## Processing

### Calibration

- pipeline or manual: 3 mm scan reduced in CASA with standard procedures; other projects with ALMA pipeline  
  > "The data for each SB were reduced in CASA, following standard procedures." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting for 3 mm, DDT and 2 mm; Briggs (robust not stated) for 870 um  
  > "imaging was done using Briggs weighting, which represents a good compromise between depth and spatial resolution." (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 2 mm: two-pointing mosaic, concatenated visibilities  
  > "imaging was done using natural weighting in the concatenated visibilities corresponding to the two pointings." (2.2 ALMA observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 870 um high-resolution observation, calibration and imaging details  
  > "Details on the observations, data calibration and imaging can be found in (cite: Oteo2016ApJ...827...34O) and (cite: Oteo2017arXiv170904191O)." (2.2 ALMA observations) [from (cite: Oteo2016ApJ...827...34O); (cite: Oteo2017arXiv170904191O)]
- [CI]-based H2 mass method  
  > "Then, we have calculated the ${\rm H_2}$ mass of each DRC component following (cite: Bothwell2017MNRAS.466.2825B) and (cite: Alaghband2013MNRAS.435.1493A)" (4.2 Molecular gas mass) [from (cite: Bothwell2017MNRAS.466.2825B); (cite: Alaghband2013MNRAS.435.1493A)]
- LABOCA observations, reduction and source extraction  
  > "More details about the observations, data reduction and source extraction can be found in Lewis et al. (in prep)." (2.1 APEX observations) [from Lewis et al. (in prep)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value for the 870 um imaging
- Line-free channels and continuum subtraction method for cubes
- Method and apertures for extracting component flux densities and line fluxes (moment-0 masks, fitting)
- Exact definition of velocity dispersion calculation and cosmology factor h(z)
- Cell/image sizes, clean thresholds, and ALMA pipeline/CASA versions
- Rest frequencies used for the lines
- Details of how the ALESS template was scaled and integrated per component

## Analysis recipe

1. **Measure 2 mm and 3 mm continuum of components**: Identify components in ultra-deep 2 mm continuum map and measure flux densities, with 3 mm detections where available  
  > "The ultra-deep ALMA continuum map at $2\,{\rm mm}$ reveals that the extended LABOCA source associated with DRC is resolved into at least 11 DSFGs" (3 An extreme over-density of DSFGs)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive LIR and SFR**: Rescale the ALESS template to 2 mm flux, integrate 8–1000 um rest frame, Kennicutt calibration  
  > "by re-scaling the ALESS template and integrating it between rest-frame 8–$1000 \, {\rm \mu m}$." (4.1 Total star-formation rate)
   - assumption: Salpeter IMF, Kennicutt 1998 calibration, ALESS SED for all components  
  > "the SFRs are derived from $L_{\rm IR}$ by assuming a Salpeter IMF and the classical (cite: Kennicutt1998ARA&A..36..189K) calibration." (1 Introduction)
   - fitting: _not stated_
   - validation: Compared with other SED templates (Pearson, Arp 220, Pope, Cosmic Eyelash, G15.141) giving factors 0.66–2.21  
  > "The Arp 220 SED gives higher SFRs than the ALESS template by a factor $1.36\times$." (4.1 Total star-formation rate)
3. **Measure line fluxes and central velocities**: Line fluxes from moment-0 maps; central velocities from CO(6-5)  
  > "The line fluxes have been derived from the moment-0 maps of \[C i\](1–0) for each component." (4.2 Molecular gas mass)
   - assumption: Undetected [CI] assumed same width as CO(6-5)  
  > "we have assumed that the \[C i\](1–0) and $^{12}$CO(6–5) transitions have the same width." (4.2 Molecular gas mass)
   - fitting: _not stated_
   - validation: _not stated_
4. **Molecular gas mass from [CI](1-0)**: Equation with X_[CI], A10, Q10 following Bothwell+2017 and Alaghband-Zadeh+2013  
  > "where $X_{\rm [C\,I]}$ is the \[C i\] / ${\rm H_2}$ abundance ratio (assumed to be $X_{\rm [C\,I]} = 3 \times 10^{-5}$)" (4.2 Molecular gas mass)
   - parameter: A10 = 7.93e-8 s^-1, Q10 = 0.6  
  > "$A_{10}$ is the Einstein coefficient ($A_{10} = 7.93 \times 10^{-8} \, {\rm s}^{-1}$) and $Q_{10}$ is the excitation factor, assumed to be $Q_{\rm 10} = 0.6$" (4.2 Molecular gas mass)
   - assumption: CMB effect not included; would raise masses ~2x  
  > "This means that the molecular gas masses of the DRC components would be a factor of $2 \times$ higher than those given by Equation" (4.2 Molecular gas mass)
   - fitting: _not stated_
   - validation: Cross-check for DRC-1 with CO(4-3) and alpha_CO=0.8, r41=0.46 gives ~1.1e11 Msun; also compared to dust-based masses  
  > "the derived molecular gas mass for DRC-1 from $^{12}$CO(4–3) is $M_{\rm H_2} \sim 1.1 \times 10^{11} \, {\rm M}_\odot$." (4.2 Molecular gas mass)
5. **Gas-depletion times**: Ratio of molecular gas mass to SFR  
  > "from the ratio between their molecular gas masses and their SFRs" (4.3 Gas-depletion time)
   - fitting: _not stated_
   - validation: _not stated_
6. **Velocity dispersion and total mass**: Velocity dispersion from component CO(6-5) centroids; mass via Evrard relation, virial estimate and LIR-halo mass relation  
  > "we have measured the central velocity of all the DRC components (see Table [\[table_properties_DRC_components\]](#table_properties_DRC_components)), from which we can derive a velocity dispersion, $\sigma_{\rm v} = 794 \, {\rm km \, s^{-1}}$." (4.4 Velocity dispersion and total mass)
   - assumption: Uniform spherical distribution for virial estimate; proto-cluster not virialized  
  > "First, proto-clusters at $z \sim 4$ are not virialized." (4.4 Velocity dispersion and total mass)
   - fitting: _not stated_
   - validation: Three methods compared; wide range noted  
  > "The different methods used above to estimate the total mass of the proto-cluster core give a wide range of values" (4.4 Velocity dispersion and total mass)

## Software

- **CASA** : Reduction and imaging of ALMA data; imaging ATCA data  
  > "The data for each SB were reduced in CASA, following standard procedures." (2.2 ALMA observations)
- **MIRIAD** : ATCA calibration  
  > "The data were calibrated by using the standard techniques in MIRIAD" (2.6 ATCA observations)
- **BoA** : LABOCA data reduction  
  > "The data were reduced using the Python-based BOlometer data Analysis Software package" (2.1 APEX observations)
- **THELI** : Gemini data reduction  
  > "performed with THELI" (2.5 Gemini observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectroscopic redshift | 4.002 | not stated | dimensionless | 3 | spectroscopically confirmed to lie at $z_{\rm spec} = 4.002$ |
| Total obscured SFR of core | ~6500 | not stated | Msun/yr | 2 | is as extreme as ${\rm SFR} \sim 6,500 \, {\rm {\rm M}_\odot \, yr^{-1}}$ |
| Total molecular gas mass | >=6.6e11 | not stated | Msun | 4 | The total molecular gas is at least $M_{\rm H_2} \sim 6.6 \times 10^{11} \, {\rm M}_\odot$. |
| Gas-depletion times | ~90–230 | not stated | Myr | 5 | range between $\sim 90$–230$\, {\rm Myr}$ |
| Velocity dispersion | 794 | not stated | km/s | 6 | $\sigma_{\rm v} = 794 \, {\rm km \, s^{-1}}$ |
| Total mass from Evrard relation | ~9.3e13 | not stated | Msun | 6 | we derive a total mass of $M_{\rm total} \sim 9.3 \times 10^{13} \, {\rm M}_\odot$ |
| Total mass from LIR-halo relation | ~4.4e13 | not stated | Msun | 6 | obtaining $M_{\rm total} \sim 4.4 \times 10^{13}\,M_\odot$ |
| DRC-1 2 mm flux density | 2.117 | 0.058 | mJy | 1 | / DRC–1 / 00:42:23.52 / $-$33:43:23.4 / $2.117 \pm 0.058$ / $0.406 \pm 0.028$ / |

## Qualitative findings

- No Lya emitters in the core apart from a ~60 kpc Lya blob next to DRC-2; star formation is dust-obscured dominated  
  > "indicating that the star formation in this most extreme region is dominated by dust-obscured star formation." (4.5 Stellar and Lya emission)
- Radio emission from DRC-6 suggests an AGN  
  > "our radio observations reveal at least one AGN" (3 An extreme over-density of DSFGs)

## Claim tuples

- H: Is the extended LABOCA source a single high-z system or a proto-cluster? | E: ALMA 2 mm and 3 mm continuum and line cubes | R: At least 11 DSFGs, at least 10 at z=4.002 over 260x310 kpc | F: DRC is a proto-cluster core with extreme source density | **supported**
- H: Is the SFR higher than other proto-clusters at z>4? | E: ALMA 2 mm flux to SFR with ALESS template | R: SFR ~6500 Msun/yr | F: Highest obscured SFR among spectroscopically confirmed z>4 proto-clusters | **supported**
- H: Will DRC evolve into a Coma-like cluster? | E: Mass estimates and evolutionary tracks | R: Mass 3e13–9e13 Msun | F: Likely progenitor of a cluster at least as massive as Coma, with high uncertainty | **partially**

## Reasoning

- Why this data: 2 mm observations aimed to detect additional lines to fix redshift unambiguously  
  > "with the aim of detecting one or more additional emission lines to determine the redshift of DRC unambiguously" (2.2 ALMA observations)
- Why this method: _not stated_
- Alternative: Initial CO(7-6)/[CI](2-1) redshift interpretation rejected; line was [CI](1-0)  
  > "revealed that the initial line detected in the ALMA $3 \, {\rm mm}$ and DDT observations was not CO, but instead \[C i\](1–0)" (3.1 Redshift confirmation of DRC)
- How they decided it was enough: _not stated_
- Limitation (authors): SFRs assume ALESS template for all components; mass estimates highly uncertain  
  > "This method assumes that the SEDs (from $8$ to $1000 \, {\rm \mu m}$ in the rest frame) of all DRC components are well represented by the ALESS template" (4.1 Total star-formation rate)
- Caveat (inferred, ours): Velocity dispersion from 10 sources with two outliers is not robust
- Caveat (inferred, ours): Gas masses depend on assumed X_CI and Q10 and CMB correction not applied
- Caveat (inferred, ours): Over-density significance of wide LABOCA field only 2 sigma and no redshifts for surrounding sources

## Reproducibility

- Data public (paper): ALMA project codes listed; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00449.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, cell size, clean settings)
- Missing: Line extraction details
- Missing: Companion papers Lewis et al. and Oteo et al. in prep
- Data volume (inferred): ~100–300 GB raw across four ALMA projects
- Score (inferred): 3/5, Data and many steps stated but imaging and extraction details sparse.
- Rediscovery candidate: no, Key imaging and flux extraction settings are missing, so exact numbers hard to redo.

## Links

- Method: (cite: Bothwell2017MNRAS.466.2825B) ([CI] gas mass method)
- Method: (cite: Swinbank2014MNRAS.438.1267S) (ALESS SED template)
- Companion: (cite: Ivison2016ApJ...832...78I) (Ultrared DSFG selection in H-ATLAS)
- Companion: (cite: Oteo2016ApJ...827...34O) (ALMA ultrared DSFG observations)
- Related: H-ATLAS
- Related: HerMES

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 48,
  "rate": 0.565
 },
 "evidence_ok": true
}
```
