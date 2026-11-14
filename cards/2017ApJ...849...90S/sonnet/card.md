# Evolution of Molecular Clouds in the Superwind Galaxy NGC 1808 Probed by ALMA Observations

`2017ApJ...849...90S` | The Astrophysical Journal 2017 | first author: Salak, Dragan | arXiv: 1710.01829 | DOI: 10.3847/1538-4357/aa91cb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: What are the distribution, kinematics, star formation properties and evolution of molecular clouds, and the molecular outflow, in the central 1 kpc starburst of NGC 1808?  
  > "we focus on the distribution and kinematics of molecular clouds in the central 1 kpc starburst region traced by the CO (1-0) and CO (3-2) lines at high resolution" (1 Introduction)
- Target **NGC 1808**: coordinates RA 05h07m42.331s, Dec -37d30m45.88s (J2000)  
  > "Distance | $10.8~\mathrm{Mpc}$ ($1\ensuremath{''}=52$ pc) | \(3\)" (Table 1); "Right ascension (J2000.0) | $05^\mathrm{h}07^\mathrm{m}42.331s\pm0.003s$ | \(2\)" (Table 1); z/distance 10.8 Mpc  
  > "Distance | $10.8~\mathrm{Mpc}$ ($1\ensuremath{''}=52$ pc) | \(3\)" (Table 1); "Right ascension (J2000.0) | $05^\mathrm{h}07^\mathrm{m}42.331s\pm0.003s$ | \(2\)" (Table 1); distance from Tully 1988 Nearby Galaxy Catalog  
  > "Distance | $10.8~\mathrm{Mpc}$ ($1\ensuremath{''}=52$ pc) | \(3\)" (Table 1); "Right ascension (J2000.0) | $05^\mathrm{h}07^\mathrm{m}42.331s\pm0.003s$ | \(2\)" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00911.S, 2012.1.01004.S
- bands: ALMA Band 3 (93 GHz), Band 7 (350 GHz); CO(1-0) from cycle 1  
  > "Representative frequency \[GHz\] | 21 | 32 | 93 | 350" (Table 2)
- frequencies and spectral setup: B3 sub-bands at 86.800, 88.716, 97.981, 100.750 GHz; B7 sub-bands at 344.000, 345.796, 356.734, 358.000 GHz; CO(3-2) at 345.79599 GHz  
  > "Data were acquired from four sub-bands centered at the rest frequencies of 86.800, 88.716, 97.981, and 100.750 GHz" (2.2.1 Band 3); "The sub-bands were centered at the rest frequencies of 344.000, 345.796, 356.734, and 358.000 GHz." (2.2.2 Band 7)
- continuum bandwidth: _not stated_
- arrays: B3: 12 m array; B7: 12 m, ACA and TP  
  > "Band 7 observations took place during 2014 and 2015 with 38 antennas of the 12 m array, 9-10 antennas of the ACA, and 3 antennas of the TP." (2.2.2 Band 7)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: B3 continuum 1.17''x0.77''; B7 continuum 1.04''x0.56''; CO(1-0) 2.67''x1.48''  
  > "$1.17\ensuremath{''}\times0.77\ensuremath{''}$ | $1.04\ensuremath{''}\times0.56\ensuremath{''}$" (Table 2)
- max recoverable scale: ~26'' for Band 3  
  > "is $\sim26\ensuremath{''}$, which is larger than the central starburst region" (2.2.1 Band 3)
- sensitivity: B3 continuum 0.025 mJy/beam; B7 continuum 0.35 mJy/beam; CO(3-2) 8 mJy/beam at 5 km/s; CO(1-0) 5 mJy/beam at 10 km/s  
  > "The final CO (3-2) data cube has a sensitivity of $8~\mathrm{mJy~beam}^{-1}$ (velocity resolution $\Delta v=5~\mathrm{km~s}^{-1}$)" (2.2.2 Band 7)
- time on source: B3 about 24 min  
  > "The total on-source time was about 24 minutes." (2.2.1 Band 3)
- observing dates: B3: 2014 Aug 27, Dec 7, 2015 Apr 21; B7: 2014 Jun 14, Dec 13, 2015 May 1, Jun 28  
  > "Observation date | 2012 Sep 8 | 2012 Sep 8, 13 | 2014 Aug 27, Dec 7 | 2014 Jun 14, Dec 13" (Table 2)
- pi or archival as stated: Authors' own cycle 1 and 2 projects  
  > "as part of our cycle 2 project" (2.2.1 Band 3)
- Line: 12CO J=3-2 (345.79599 GHz)
- Line: 12CO J=1-0 (not stated)
- Other facility **VLA**: K and Ka band continuum at 21 and 32 GHz, BnA configuration  
  > "with 27 antennas in configuration BnA" (2.1 VLA Observations)
- Other facility **ASTE**: single-dish CO data used for flux comparison  
  > "we compared the combined ALMA data to the single-dish ASTE data from (cite: Sal14)" (2.2.2 Band 7)
- External data: CO(1-0) 12 m array data previously presented  
  > "The data acquired by the 12 m array only were previously presented in (cite: Sal16)." (2.2.1 Band 3) [from (cite: Sal16)]
- External data: X_CO = 0.8e20 cm^-2 (K km/s)^-1  
  > "by using a relatively low conversion factor $X_\mathrm{CO}=0.8\times10^{20}~\mathrm{cm^{-2}(K~km~s^{-1})^{-1}}$ from (cite: Sal14)" (4.1 ISM mass from 350 GHz dust continuum) [from (cite: Sal14)]
- External data: Rotation curve from Figure 20 of Sal16 used for circular-motion model  
  > "using the rotation curve from Figure 20 of (cite: Sal16)" (5.2 Molecular gas outflows from the 500 pc ring) [from (cite: Sal16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: B3 and B7: J0522-364  
  > "Flux calibrator | 3C147 | 3C147 | J0522-364 | J0522-364" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: B3: Briggs robust 0.5; B7: natural weighting  
  > "The imaging was done interactively with Briggs weighting (robustness parameter set to 0.5)" (2.2.1 Band 3); "The imaging was done interactively in mosaic mode with natural weighting to maximize sensitivity" (2.2.2 Band 7)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Spectral lines flagged prior to continuum imaging  
  > "The spectral lines were flagged prior to continuum imaging." (2.2.1 Band 3)
- line free channels: _not stated_
- primary beam correction: All images corrected for primary beam attenuation  
  > "All images were corrected for the primary beam attenuation." (2.2.2 Band 7)
- array combination: CO(1-0): 12 m CLEANed with ACA, then CASA feather with TP; CO(3-2): 12m+ACA+TP combined with feather  
  > "corrected for the missing flux relative to the Total Power (TP) single-dish data cube using the CASA task “feather”" (2.2.1 Band 3)
- smoothing: _not stated_
- final beam: CO(3-2) 1.04''x0.57''  
  > "FWHM of the synthesized beam is $1.04\ensuremath{''}\times0.57\ensuremath{''}$" (2.2.2 Band 7)
- final rms: _not stated_

### Inherited from earlier work

- CO(1-0) cycle 1 data reduction and previous presentation  
  > "The data acquired by the 12 m array only were previously presented in (cite: Sal16)." (2.2.1 Band 3) [from (cite: Sal16)]
- Dust-continuum ISM mass using equation (3)  
  > "Using equation (3) from (cite: Sco15), we calculated the ISM mass" (4.1 ISM mass from 350 GHz dust continuum) [from (cite: Sco15)]
- SFR from free-free luminosity  
  > "Following (cite: Mur11), the SFR can be expressed as" (4.2 Star formation rate and efficiency from 93 GHz continuum) [from (cite: Mur11)]

### Not stated but needed to reproduce (our reading)

- CASA version and ALMA pipeline version for ALMA data
- Line-free channels and continuum subtraction method for CO cubes
- Image size, cell size, and clean thresholds/masks
- feather scaling and cube channel definitions
- Moment clipping thresholds other than the 5 sigma total flux
- Equation (3) of Sco15 constants applied
- Aperture definitions for region fluxes
- CLUMPFIND contour levels and step

## Analysis recipe

1. **Continuum imaging and fluxes**: Continuum images made in CASA from line-free data, core fluxes measured  
  > "The imaging was done interactively with Briggs weighting (robustness parameter set to 0.5) to achieve high angular resolution." (2.2.1 Band 3)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Spectral index and SED decomposition**: Least-squares fit of synchrotron + free-free + dust power laws to 21-350 GHz core flux  
  > "Also shown is a least-squares fit that includes contributions from three different types of emission: synchrotron (non-thermal), free-free, and dust (thermal)." (3.1.2 Spectral energy distribution of the core)
   - assumption: Fixed indices alpha_s=-0.9, alpha_ff=-0.1, alpha_d=3.8  
  > "we fixed the spectral indices as $\alpha_\mathrm{s}=-0.9$ (synchrotron)" (3.1.2 Spectral energy distribution of the core)
   - fitting: Least-squares, amplitudes free  
  > "where $K$ is the proportionality factor to be determined" (3.1.2 Spectral energy distribution of the core)
   - validation: Fit stated to be not unique  
  > "The fitting result is not unique" (3.1.2 Spectral energy distribution of the core)
3. **Moment maps and CO line ratio**: Moment 0/1/2 maps; R_CO = W(3-2)/W(1-0) at 2'' resolution  
  > "The CO line ratio in Figure 6(b) is defined as $R_\mathrm{CO}\equiv W_\mathrm{CO(3-2)}/W_\mathrm{CO(1-0)}$" (3.3 CO (3-2)/(1-0) line intensity ratio in the central 1 kpc)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Masses, SFR and SFE in regions**: ISM mass from 350 GHz continuum; molecular mass from CO(1-0); SFR from 93 GHz free-free  
  > "The star formation rate (SFR)[^3] in the CND and regions R1-R5 can be estimated from the band 3 continuum assuming that the SED is dominated by free-free emission at 93 GHz." (4.2 Star formation rate and efficiency from 93 GHz continuum)
   - assumption: Td = 20 and 100 K; X_CO = 0.8e20; Te = 5000 K; d = 10.8 Mpc  
  > "we calculated the ISM mass for dust temperatures of 20 and 100 K." (4.1 ISM mass from 350 GHz dust continuum)
   - fitting: _not stated_
   - validation: Compared ISM and molecular masses, agree within factor of few  
  > "The two measurements agree within the uncertainty of $T_\mathrm{d}$ and $X_\mathrm{CO}$ (a factor of few)" (4.1 ISM mass from 350 GHz dust continuum)
5. **Outflow kinematics from PVDs**: PVDs along the minor axis (PA 54 deg); velocity deprojected by 1/cos i; gradient measured; shell expansion velocity from line splitting  
  > "Assuming that the stream is perpendicular to the galactic plane (i.e., gas outflow), its velocity is $|V_\mathrm{LSR}-V_\mathrm{sys}|/\cos{i}\approx180$ km s$^{-1}$" (5.1 Kinematics of the nuclear outflow)
   - assumption: Vsys=998 km/s, i=57 deg, outflow perpendicular to disk  
  > "Assuming that the stream is perpendicular to the galactic plane (i.e., gas outflow), its velocity is $|V_\mathrm{LSR}-V_\mathrm{sys}|/\cos{i}\approx180$ km s$^{-1}$, where $V_\mathrm{sys}=998$ km s$^{-1}$ and $i=57\ensuremath{^\circ}$" (Kinematics of the nuclear outflow)
   - fitting: _not stated_
   - validation: _not stated_
6. **Cloud identification**: CLUMPFIND (IDL) 3D on CO(3-2) cube; fluxes converted to CO(1-0) via R_CO  
  > "we carried out cloud identification using the CLUMPFIND algorithm (IDL version) (cite: WdB94)" (6.1 GMC identification, distribution, and CO fluxes)
   - software: CLUMPFIND
   - parameter: min pixels = beam area; rms set to 23 mJy/beam  
  > "the global r.m.s. noise level was set to 23 mJy beam$^{-1}$ (about $3~\sigma$ in emission-free channels)" (6.1 GMC identification, distribution, and CO fluxes)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction, imaging, feather  
  > "Data reduction was done using the Common Astronomy Software Applications (CASA) program (cite: McM07)." (2.1 VLA Observations)
- **CLUMPFIND** IDL version: 3D cloud identification in CO(3-2) cube  
  > "we carried out cloud identification using the CLUMPFIND algorithm (IDL version) (cite: WdB94)" (6.1 GMC identification, distribution, and CO fluxes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) peak separation in CND | 1.17 (61 pc) | 0.07'' (4 pc) | arcsec | 3 | CO (3-2) exhibits a double peak with a projected separation of $1.17\ensuremath{''}\pm0.07\ensuremath{''}$ |
| Free-free fraction at 93 GHz (S_s:S_ff:S_d) | 0.22:0.72:0.06 | not stated | dimensionless | 2 | $S_\mathrm{s}:S_\mathrm{ff}:S_\mathrm{d}=0.22:0.72:0.06$ |
| Q_Lyc central region | 4.4e53 | not stated | s^-1 | 2 | we find $Q_\mathrm{Lyc}=4.4\times10^{53}~\mathrm{s}^{-1}$ |
| R_CO in central 1'' | 0.96 | 0.01 | dimensionless | 3 | $R_\mathrm{CO}=0.96\pm0.01$ |
| Total SFR r<15'' | ~4.5 | not stated | Msun/yr | 4 | $\mathrm{SFR}(r<15\ensuremath{''})\sim4.5~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$ |
| Total molecular gas mass in central starburst | 9.7e8 | not stated | Msun | 4 | $M_\mathrm{mol}=9.7\times10^8~M_\ensuremath{\odot}$ |
| Outflow velocity gradient | ~0.4 | not stated | km/s/pc | 5 | yielding a velocity gradient of $\Delta v/\Delta h\sim0.4$ km s$^{-1}$ pc$^{-1}$ |
| Shell expansion velocity | ~75 | not stated | km/s | 5 | $v_\mathrm{exp}\approx \Delta v_\mathrm{s}/2\sim75$ km s$^{-1}$ |
| Number of clumps identified | 214 | not stated | dimensionless | 6 | The program identified a total of 214 clouds (clumps) within the imaged central starburst region |
| Mass outflow rate of shells | ~0.25 | not stated | Msun/yr | 5 | the mass outflow rate is $\Delta M_\mathrm{sh}/\Delta t\sim0.25~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$ |

## Qualitative findings

- Molecular gas torus of radius ~30 pc in the CND with a continuum core offset between the CO peaks  
  > "The double peak of CO (3-2) intensity is modeled to be an inclined, rotating torus with a radius of $r\sim30~\mathrm{pc}$." (3.4 Gas torus and core in the central 100 pc)

## Claim tuples

- H: Is there a nuclear molecular outflow with a velocity gradient? | E: PVD along minor axis in CO(1-0) and CO(3-2) | R: Line splitting; velocity ~180 km/s; gradient ~0.4 km/s/pc | F: Nuclear molecular outflow confirmed and accelerating | **supported**
- H: Does star formation efficiency in CND and clouds exceed that of normal disks? | E: 350 GHz and CO masses with 93 GHz free-free SFR | R: SFE ~1e-8 /yr, depletion time 1e7-1e8 yr | F: Starburst-mode high SFE | **supported**
- H: Do molecular clouds evolve from bar inflow to star formation to outflow? | E: CLUMPFIND cloud fluxes vs location, R_CO, continuum | R: CO fluxes increase along ring orbit; shells from ring | F: Proposed evolutionary sequence, in terms of CO luminosity and excitation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: CO(3-2) used for clump finding for higher angular resolution  
  > "The CO (3-2) line was used instead of CO (1-0) because of higher angular resolution" (6.1 GMC identification, distribution, and CO fluxes)
- Alternative: Offset velocity not inflow in galactic plane, due to required large radial velocities vs simulations  
  > "The offset velocity component is not likely an inflow in the galactic plane (coplanar motion)" (5.1 Kinematics of the nuclear outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): X_CO analysis beyond scope; masses uncertain by factor of few  
  > "the analysis of the conversion factor $X_\mathrm{CO}$ is beyond the scope of this paper" (6.2 GMC evolution: inflow, star formation, and outflow)
- Caveat (inferred, ours): Single X_CO and fixed spectral indices drive derived masses and fractions
- Caveat (inferred, ours): Outflow geometry (perpendicular to disk) assumed
- Caveat (inferred, ours): Evolutionary sequence inferred from snapshot flux distribution
- Caveat (inferred, ours): CLUMPFIND parameters poorly specified

## Reproducibility

- Data public (paper): ALMA data cited by project code; no explicit public statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.01004.S and #2013.1.00911.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA/pipeline versions
- Missing: clean parameters and masks
- Missing: line-free channels
- Missing: region aperture definitions
- Missing: CLUMPFIND levels
- Data volume (inferred): ~100-500 GB raw (B3, B7 mosaic with ACA/TP, plus cycle 1 CO(1-0))
- Score (inferred): 3/5, Data public and recipes mostly described, but many imaging settings and the missing-flux CO(1-0) processing are in other papers.
- Rediscovery candidate: no, Key CO(1-0) cube comes from a companion/unpublished processing and imaging details are missing.

## Links

- Method: (cite: Sal16) (Earlier ALMA CO(1-0) data, rotation curve, outflow, dynamical fit)
- Method: (cite: WdB94) (CLUMPFIND algorithm)
- Companion: (cite: Sal16) (First paper in the NGC 1808 ALMA series)
- Related: 2012.1.01004.S

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.01004.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 47,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
