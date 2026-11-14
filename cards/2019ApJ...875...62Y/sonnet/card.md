# ALMA Observations of Layered Structures due to CO Selective Dissociation in the ρ Ophiuchi A Plane-parallel PDR

`2019ApJ...875...62Y` | The Astrophysical Journal 2019 | first author: Yamagishi, M. | arXiv: 1903.02192 | DOI: 10.3847/1538-4357/ab0d80

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Does the rho Oph A PDR show layered CO isotopologue structures from selective dissociation, indicating a plane-parallel rather than clumpy PDR, and how do 13CO/C18O abundance ratios vary?  
  > "The main motivation of the present study is examining the PDR structure using the high spatial resolution of ALMA." (Introduction)
- Target **rho Ophiuchi A PDR (Be star S1)**: coordinates _not stated_; z/distance 137.3±1.2 pc  
  > "the closest PDR ($d$=137.3$\pm$1.2 pc; (cite: Ortiz-Leon17)), and is illuminated by the Herbig Be star, S1" (Introduction); distance from Ortiz-Leon17  
  > "the closest PDR ($d$=137.3$\pm$1.2 pc; (cite: Ortiz-Leon17)), and is illuminated by the Herbig Be star, S1" (Introduction)
- Target **GY-51 (flat-spectrum YSO)**: coordinates _not stated_; z/distance in rho Oph A, 137.3 pc  
  > "spatially coincident with the YSO, GY-51 ((cite: Bontemps01))" (3.2 GY-51); distance from Ortiz-Leon17  
  > "spatially coincident with the YSO, GY-51 ((cite: Bontemps01))" (3.2 GY-51)

## Data provenance

- ALMA projects: 2013.1.00839.S
- bands: Band 6 (1.3 mm, 226 GHz), Cycle 2  
  > "We analyzed ALMA Cycle-2 data at Band-6 for a 2$\ensuremath{'}$$\times$3$\ensuremath{'}$ region of $\rho$ Oph A" (Observation and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m Array and ACA 7-m Array  
  > "obtained using the 12-m Array and the ACA 7-m Array" (Observation and data reduction)
- configurations: _not stated_
- baselines: uv ranges 12.5–348 kλ (12-m) and 8.1–48 kλ (7-m)  
  > "The uv ranges sampled in the 12-m Array and 7-m Array data were 12.5–348 k$\lambda$ and 8.1–48 k$\lambda$, respectively" (Observation and data reduction)
- angular resolution: common beam 1.45" x 0.94"  
  > "We used a common synthesized beam (1$\ensuremath{''}$45 $\times$ 0$\ensuremath{''}$94) and velocity grid (0.2 km s$^{-1}$) in the map making." (Observation and data reduction)
- max recoverable scale: minimum uv distance of combined data corresponds to 25"  
  > "The minimum uv distance of the combined data corresponds to 25$\ensuremath{''}$." (Observation and data reduction)
- sensitivity: 1σ: 45 (12CO), 45 (13CO), 33 (C18O) mJy/beam at 0.2 km/s; continuum 0.24 mJy/beam  
  > "are 45 mJy beam$^{-1}$, 45 mJy beam$^{-1}$, and 33 mJy beam$^{-1}$, respectively, at a velocity resolution of 0.2 km s$^{-1}$, while that of the continuum map is 0.24 mJy beam$^{-1}$." (Observation and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI F. Nakamura  
  > "(PI: F. Nakamura; Project code: 2013.1.00839.S)" (Observation and data reduction)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **Spitzer/IRAC 4.5 um**: image of PDR shell  
  > "Figure [1](#obsarea) shows a $Spitzer$/IRAC 4.5 $\ensuremath{\mu}m$ image of the $\rho$ Oph A PDR" (Introduction)
- External data: G0=(3–4)e3 FUV intensity at PDR shell  
  > "The FUV intensity at the PDR shell was estimated to be $G_0$=(3–4)$\times$10$^3$ ((cite: Shimajiri17))." (Introduction) [from Shimajiri17]
- External data: lower limit Tex 45 K from JCMT 12CO(3-2)  
  > "we set the lower limit of the excitation temperature as 45 K, as previously estimated from the JCMT $^{12}$CO ($J$=3–2) data ((cite: White15))" (3.1) [from White15]
- External data: solar system 13CO/C18O ratio 5.5  
  > "significantly larger than the 5.5 seen in the solar system ((cite: Anders89))" (3.1) [from Anders89]
- External data: 12CO/13CO ratio ~4 in HL Tau  
  > "measured toward another flat-spectrum YSO, HL Tau, is $\sim$4 ((cite: Wu18))" (3.2) [from Wu18]

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
- array combination: 12-m and 7-m data combined (12-m only for GY-51 CO)  
  > "CO data obtained from only the 12-m Array are presented to examine relatively compact ($<10\ensuremath{''}$) structures around GY-51." (3.2 GY-51)
- smoothing: _not stated_
- final beam: 1.45" x 0.94"  
  > "We used a common synthesized beam (1$\ensuremath{''}$45 $\times$ 0$\ensuremath{''}$94)" (Observation and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Image reduction methods  
  > "The images used in the present paper were reduced using the same methods described in (cite: Kawabe18)." (Observation and data reduction) [from Kawabe18]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration and imaging parameters (weighting, deconvolver, masks, continuum subtraction), since deferred to Kawabe18
- Rest frequencies and spectral setup
- Exact procedure and pixel selection for Tex/column density maps
- Coordinates of targets

## Analysis recipe

1. **Identify CO layered structure in channel maps**: Inspect channel maps of 12CO, 13CO, C18O at 2.2–2.6 km/s relative to S1 and the 1.3 mm continuum  
  > "distinct layered structures of the CO isotopologues are clearly detected at 2.2 km s$^{-1}$, 2.4 km s$^{-1}$ and 2.6 km s$^{-1}$" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive Tex, optical depths and column densities, then R13/18 maps**: Tex from peak 12CO brightness temperature; tau13, tau18 from that Tex; N under LTE via Nishimura15 eq. 11  
  > "$N$($^{13}$CO) and $N$(C$^{18}$O) were estimated under the LTE condition for simplicity by using equation (11) in (cite: Nishimura15)" (3.1)
   - parameter: Tex lower limit 45 K  
  > "we set the lower limit of the excitation temperature as 45 K" (3.1)
   - assumption: common Tex among isotopologues; 12CO(2-1) heavily optically thick; LTE  
  > "Here we assumed that the excitation temperature is common among the CO isotopologues, and that the $^{12}$CO ($J$=2–1) emission is heavily optically thick." (3.1)
   - fitting: _not stated_
   - validation: Tested Tex>50 K and 55 K; trend unchanged, R lower by ~20%  
  > "higher $T_{\mathrm{ex}}$ generally shows lower $R_{13/18}$ by $\sim$20 %" (3.1)
3. **Radial profile of R13/18 and comparison with PDR models**: Profile versus projected distance from S1, error propagation formula, compare with van Dishoeck & Black 1988 scaled by density  
  > "Figure [5](#profile) shows spatial variations of $R_{13/18}$ as a function of projected distance from S1." (3.1)
   - assumption: nH ~1e5 cm-3 from Loren83  
  > "The hydrogen density derived for a region 0.1 pc away from the $\rho$ Oph A core is $n_\mathrm{H}\sim10^{5}$ cm$^{-3}$ ((cite: Loren83))." (3.1)
   - fitting: _not stated_
   - validation: Consistency with predicted depth ~4e-3 pc  
  > "Therefore, an equivalent depth of $\Delta d \sim4\times10^{-3}$ pc is expected for the $\rho$ Oph A PDR" (3.1)
4. **GY-51 CO intensity ratio and disk dust mass**: Spectra from 3.6"x2.4" region of 12-m data; ratio lower limit; dust mass from 1.3 mm flux  
  > "the dust mass of the disk around GY-51 is estimated as $M_\mathrm{dust} = 1.6\times 10^{-5}M_{\odot}$" (3.2 GY-51)
   - assumption: Tdust=60 K, kappa1.3mm=2.3 cm2/g, gas-to-dust 100, CO/H2 6e-5, Tgas=60 K, disk radius 70 au, 12C/13C=62  
  > "$T_{\mathrm{dust}}=60$ K and $\kappa_{\rm 1.3mm}=2.3$ cm$^2$ g$^{-1}$ are assumed" (3.2 GY-51)
   - fitting: _not stated_
   - validation: Compared with Williams14 disk models  
  > "According to the model calculations, the observed gas mass of $\sim 1.6\times 10^{-3}M_{\odot}$ is too large to achieve the high intensity ratio of $>$21." (3.2 GY-51)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Layer separation | 10 arcsec = 6.6e-3 pc = 1400 au | not stated | arcsec | 1 | 10$\ensuremath{''}$ = 6.6$\times$10$^{-3}$ pc = 1400 au |
| R13/18 near emission front | as high as 40 | not stated | dimensionless | 2 | $R_{13/18}$ is as high as 40 near the shell |
| Angular scale of R13/18 decline | 3"–5" = (2.0–3.4)e-3 pc | not stated | arcsec | 3 | rapidly decreases from 20–40 to the standard value in a small angular scale of 3$\ensuremath{''}$–5$\ensuremath{''}$ |
| Peak 12CO brightness | 3.8 Jy/beam, 69 K | not stated | Jy/beam | 2 | is 3.8 Jy beam$^{-1}$ which corresponds to a brightness temperature of 69 K |
| Tex range | 45–75 | not stated | K | 2 | are 45–75 K, 0.03–4.4, 0.02–0.77 |
| GY-51 12CO flux | 3.2 | 0.1 | Jy km/s | 4 | the $^{12}$CO emission is clearly detected (3.2$\pm$0.1 Jy km s$^{-1}$) |
| GY-51 12CO/13CO ratio | >21 | 3σ lower limit | dimensionless | 4 | The 3$\sigma$ lower limit of the $I(^{12}{\rm CO}(2-1))/I(^{13}{\rm CO}(2-1))$ intensity ratio is $>21$. |
| GY-51 1.3 mm flux density | 40.5 | not stated | mJy | 4 | total flux density of 40.5 mJy within a $3.6\ensuremath{''}\times2.4\ensuremath{''}$ region |
| GY-51 dust mass | 1.6e-5 | not stated | Msun | 4 | $M_\mathrm{dust} = 1.6\times 10^{-5}M_{\odot}$ |

## Qualitative findings

- 12CO, 13CO, C18O emission lie inside, on, and behind the shell respectively  
  > "$^{12}$CO, $^{13}$CO, and C$^{18}$O emission is bright inside the shell, on the shell, and behind the shell, respectively." (3.1)

## Claim tuples

- H: CO isotopologues show layered structure in rho Oph A, implying a plane-parallel PDR | E: ALMA channel maps of three CO isotopologues | R: Layers separated by ~10" at 2.2–2.6 km/s | F: rho Oph A is plane-parallel-like | **supported**
- H: Selective dissociation enhances 13CO/C18O | E: LTE column density ratio maps | R: R13/18 up to 40 dropping to 5.5 within ~4" | F: consistent with van Dishoeck & Black prediction | **supported**
- H: Selective dissociation affects GY-51 disk CO | E: 12CO/13CO intensity ratio | R: >21 versus ~4 in other YSOs | F: photo-evaporation plus selective photodissociation may explain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Clumpy PDR disfavoured since layering is hard to form with inhomogeneous density  
  > "It is difficult to form such layered structures in a clumpy PDR" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Near systemic velocity emission attenuated/resolved out; observed R13/18 is a lower limit; LTE assumed  
  > "the observed $R_{13/18}$ should be treated as the lower limit to the actual $R_{13/18}$." (3.1)
- Caveat (inferred, ours): LTE with a single Tex and a floor of 45 K strongly affects R13/18
- Caveat (inferred, ours): Spatial filtering and absorption near the systemic velocity bias ratios
- Caveat (inferred, ours): Disk mass/opacity estimates for GY-51 are simplistic

## Reproducibility

- Data public (paper): ALMA project code given; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00839.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging recipe (in Kawabe18)
- Missing: Tex/column density map pipeline details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 4/5, Public data and simple analysis, but imaging details deferred to Kawabe18 and no software named.
- Rediscovery candidate: yes, Public data, numeric results from simple LTE analysis, though imaging settings are inherited.

## Links

- Method: Kawabe18 (Image reduction methods)
- Method: Nishimura15 (LTE column density equation (11))

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
