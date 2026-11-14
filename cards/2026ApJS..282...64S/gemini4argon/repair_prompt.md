# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026ApJS..282...64S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# MAGellanic Outflow and chemistry Survey (MAGOS): Hot cores in the LMC

## Abstract

The Large Magellanic Cloud (LMC) provides a key laboratory for exploring the diversity of star formation and interstellar chemistry under subsolar metallicity conditions. We present the results of a hot core survey toward 30 massive protostellar objects in the LMC using the Atacama Large Millimeter/submillimeter Array (ALMA) at 350 GHz. Continuum imaging reveals 36 compact sources in total, among which line analyses identify 9 hot cores and 1 hot-core candidate, including two newly identified sources. We detect , , , , , , , , , , , , , , , , , , (tentative), and hydrogen recombination lines from hot cores. , a complex organic molecule larger than , is detected for the first time in a hot core outside the LMC bar region. All hot cores show stronger emission in the high-excitation SO line compared to non-hot-core sources, suggesting that its strong detection will be useful for identifying hot-core candidates in the LMC. Chemical analysis reveals a spread of more than two orders of magnitude in abundances, with some sources deficient in COMs. In contrast, is detected in all hot cores, and its abundance shows a good correlation with rotational temperature. The hot cores without detections are all located outside the LMC bar region and are characterized by either high luminosity or active star formation in their surroundings. A combination of locally low metallicity, active star formation in the vicinity, and high protostellar luminosity may jointly trigger the COM-poor hot core chemistry observed in the LMC.

# Introduction

Massive stars have played an important role throughout cosmic history (cite: ZY07; Tan14; Mot18; Beu25). The first stars born immediately after the Big Bang provided the first heavy elements to the Universe. In the present-day Galaxy, massive stars are the primary sources of ultraviolet (UV) radiation, turbulent energy, and heavy elements, which govern the dynamical and chemical evolution of the interstellar medium (ISM). Massive stars also play a significant role in shaping the molecular complexity of the ISM, as various interstellar molecules are frequently detected along sightlines toward embedded massive protostars (cite: Her09). Understanding the metallicity dependence of the physical and chemical processes in massive star formation is particularly important because the galactic metallicity increases with cosmic evolution.

Owing to its high resolution and sensitivity, the Atacama Large Millimeter/submillimeter Array (ALMA) has enabled observations of nearby low-metallicity galaxies, the Large and Small Magellanic Clouds (LMC/SMC), at molecular cloud core scales of $\sim$0.1 pc. The LMC is an ideal laboratory for low-metallicity star formation studies, owing to its proximity (cite: Pie13), moderately face-on geometry (cite: vdM01), and sub-solar metallicity environment (cite: Rus92; Duf82; Wes90; And02; Rol02).

Recent ALMA observations have indeed detected protostellar activities, such as outflows, in the LMC and SMC (cite: Fuk15; ST16; Tok22b; ST23).

Hot molecular cores are compact ($\lesssim$0.1 pc), dense ($\gtrsim$10$^6$ cm$^{-3}$), and hot ($\gtrsim$100 K) protostellar sources, which appear in the early evolutionary stage of star formation (cite: Kur00; Naz25). The chemistry at this stage is thought to be driven by the warm-up and sublimation of ice mantles of dust grains formed during the earlier, colder stages, as well as by subsequent high-temperature gas-phase reactions (cite: Cha92; NM04; Gar08b). A wide variety of molecular species, including complex organic molecules (COMs), are often detected in solar-metallicity hot cores owing to their chemically-rich nature (cite: Her09). A comprehensive understanding of the chemical compositions of hot cores across different metallicities is essential for elucidating how natal environments influence the chemical evolution of protostellar sources.

With ALMA, hot cores have now been detected in low-metallicity environments, including the LMC (cite: ST16; ST20; Sew18; Sew22a; Gol24; Bro25), the SMC (cite: ST23), and the extreme outer Galaxy (cite: ST21; Ike25). Among LMC hot cores, the abundance of CH$_3$OH, one of the simplest COMs and a classical hot core tracer, shows a large scatter: in some sources, it is roughly consistent with the metallicity-scaled abundance of their Galactic counterparts, while in others, it is significantly depleted beyond what would be expected from metallicity differences alone. The reason behind the chemical diversity of organic molecules in the LMC remains unclear; however, since CH$_3$OH is predominantly formed through surface reactions on cold dust grains (cite: Wat07), astrochemical simulations suggest that variations in chemical evolution during the ice formation stage may influence the abundances of organic molecules (cite: Ach15; Ach16; Ach18; Pau18; ST20). In contrast to organic molecules, sulfur-bearing species, SO and SO$_2$, are commonly detected in LMC/SMC hot cores with similar abundances (cite: ST23). This suggests that these inorganic molecules may serve as useful hot core tracers in the LMC, replacing CH$_3$OH, which is commonly used as a hot core tracer in solar-metallicity environments. However, the number of hot core samples observed in low-metallicity environments, including the LMC, remains limited, highlighting the need for systematic survey observations.

The “MAGellanic clouds Outflow and chemistry Survey (MAGOS)” is a comprehensive project aimed at exploring various aspects of star formation within the LMC and SMC with ALMA (PI: K. Tanaka; Project code 2019.1.01770.S). Using MAGOS data, (cite: ST23) have reported the detection of two new hot cores in the SMC. A series of studies have also used MAGOS data to identify and classify filamentary structures associated with protostars in the LMC (cite: Tok23) and the SMC (cite: Tok25). This paper presents the results of the hot core survey for $\sim$30 LMC massive protostellar objects.

This paper is structured as follows. Section [2](#sec_tarobsred) describes the details of target selection, observations, and data reduction. Section [3](#sec_res) presents the spectra and line intensity distributions of LMC hot cores obtained from the observations. Section [4](#sec_ana) outlines the analysis of column densities based on the detected molecular lines and continuum emission. Section [5](#sec_disc) discusses the molecular species that serve as hot core tracers in the LMC, compares the associated physical properties and molecular compositions, and examines the possible factors contributing to the chemical diversity of organic molecules in the LMC. Finally, Section [6](#sec_sum) provides a summary of this work.

# Observations and Data Reduction

## Target selection

The target sources were selected from the catalog of young stellar objects (YSOs) presented by (cite: Sea09), which includes 277 sources. From this catalog, 30 infrared sources were chosen as the pointing centers for the present ALMA observations.

To begin the selection process, we calculated the luminosities of the sources in the catalog. The sources in the (cite: Sea09) catalog include near-infrared and mid-infrared photometric data, which are based on the 2MASS and Spitzer SAGE catalogs (cite: Skr06; Mei06). Far-infrared data were obtained by performing positional cross-matching between the (cite: Sea09) sources and the Herschel HERITAGE catalog (cite: Mei10), resulting in spectral energy distributions (SEDs) covering the 1–500 $\mu$m range. The bolometric luminosities ($L_{\mathrm{bol}}$) were derived by directly integrating the fluxes at the available wavelengths: 1.2, 1.7, 2.2, 3.6, 4.5, 5.8, 8.0, 24, 100, 160, 250, 350, and 500 $\mu$m. The luminosities of the target YSOs are primarily dominated by far-infrared fluxes, for which the angular resolutions of Herschel/PACS at 100 $\mu$m and 160 $\mu$m are approximately 7$\ensuremath{''}$ and 11$\ensuremath{''}$, respectively (cite: Mei13).

Next, we divided the sources into three luminosity bins: $10^{4}$–$10^{4.5}$ $L_\odot$ (119 sources), $10^{4.5}$–$10^{5}$ $L_\odot$ (57 sources), and $10^{5}$–$10^{5.5}$ $L_\odot$ (17 sources). Sources with luminosities below $10^{4}$ $L_\odot$ (84 sources) were excluded from the selection. Within each luminosity bin, we arbitrarily selected 10 sources, resulting in a total of 30 targets. Sources were chosen based on the presence of molecular outflows, hot-core signatures, or infrared spectral features indicative of early evolutionary stages, e.g., silicate/ice absorption, or polycyclic aromatic hydrocarbon (PAH) emission. Therefore, the final sample is not a purely random selection. We denote the 10 sources in the $10^{4}$–$10^{4.5}$ bin as Ll01 to Ll10, those in the $10^{4.5}$–$10^{5}$ bin as Lm01 to Lm10, and those in the $10^{5}$–$10^{5.5}$ bin as Lh01 to Lh10.

![](f1.pdf)

The spatial distribution of the selected targets across the LMC is shown in Figure [1](#distribution). The targets are distributed widely across the LMC. Detailed information on the selected sources is summarized in Table [1](#sourcelist).

Some of the infrared sources were resolved into multiple continuum sources in the present ALMA observations. In such cases, the luminosity was divided among the resolved components in proportion to their 850 $\mu$m continuum fluxes obtained. These resolved sources are labeled with suffixes, such as Lh05-1 and Lh05-2. In total, 36 continuum sources were identified in this survey.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:---|
| Source | R.A. | Decl. | $V_{\rm sys}$$^{a}$ | Luminosity$^{b}$ | HC$^{c}$ | IR$^{d}$ | Other Name/Reference |
|  | (ICRS) | (ICRS) | (km s$^{-1}$) | ($10^4\,L_\odot$) |  |  |  |
| Lh10 | 05:26:46.61 | -68:48:47.03 | 250.8 | 23.0 | $\checkmark$ | S | ST11 (1) |
| Lh09 | 04:51:53.31 | -69:23:28.54 | 235.8 | 20.8 | $\checkmark$ | SE | H72.96-69.39 (2) |
| Lh08 | 05:39:38.93 | -69:39:10.80 | 238.1 | 17.3 | $\checkmark$ | PE | N160A-mm (3) |
| Lh07 | 05:13:25.16 | -69:22:45.44 | 239.6 | 15.5 | $\checkmark$ | P | N113 A1 (4) |
| Lh06 | 05:09:50.54 | -68:53:5.32 | 237.7 | 15.3 |  | P | N105-1A (5) |
| Lh05-1 | 05:09:51.99 | -68:53:28.40 | 242.9 | 7.2 | $\checkmark$ | PE | N105-2A (5) |
| Lh05-2 | 05:09:52.57 | -68:53:28.15 | 243.6 | 7.5 | $\checkmark$ | PE | N105-2B (5) |
| Lh05-3$^{$\dag$}$ | 05:09:52.22 | -68:53:22.55 | 243.0 | – |  | – | N105-2C (5) |
| Lh04 | 05:39:41.97 | -69:46:12.03 | 237.5 | 12.7 |  | PE | N159W-S YSO-S (6) |
| Lh03 | 05:19:12.31 | -69:09:7.32 | 265.6 | 11.6 | $\checkmark$ | S | ST16 (7) |
| Lh02 | 05:39:37.59 | -69:45:26.18 | 237.7 | 11.3 |  | PE | N159W-N YSO-N (6) |
| Lh01-1 | 05:39:36.71 | -69:45:38.00 | 237.2 | 6.0 |  | PE | N159W-N MMS2d (8) |
| Lh01-2 | 05:39:37.09 | -69:45:36.66 | 235.8 | 4.3 |  | PE | N159W-N MMS2a (8) |
| Lm10 | 04:51:11.35 | -69:26:46.57 | 241.0 | 8.3 | $\checkmark$ | S |  |
| Lm09 | 04:52:9.26 | -66:55:21.69 | 272.6 | 8.0 |  | PE |  |
| Lm08 | 05:30:54.29 | -68:34:28.20 | 256.8 | 7.8 |  | S | ST5 (9) |
| Lm07 | 05:38:39.71 | -69:05:38.13 | 244.9 | 6.2 | ? | PE | S5-A (10) |
| Lm06 | 05:39:31.25 | -70:12:16.94 | 223.5 | 4.6 |  | P | ST1 (9) |
| Lm05-1 | 05:13:18.90 | -69:21:51.73 | 235.4 | 2.5 |  | PE |  |
| Lm05-2 | 05:13:18.93 | -69:21:47.44 | 237.5 | 1.7 |  | PE |  |
| Lm04 | 05:22:2.69 | -67:47:2.90 | 282.4 | 3.7 |  | P |  |
| Lm03 | 05:22:49.81 | -66:40:55.78 | 296.4 | 3.5 |  | PE |  |
| Lm02 | 05:39:55.70 | -71:10:1.27 | 230.8 | 3.5 |  | PE |  |
| Lm01 | 04:55:50.65 | -66:34:34.70 | 275.9 | 3.2 |  | S | ST13 (11) |
| Ll10 | 05:23:33.44 | -69:37:12.27 | 250.1 | 2.8 | $\checkmark$ | S | 14A (12) |
| Ll09 | 05:22:1.92 | -67:57:57.86 | 283.6 | 2.8 |  | PE |  |
| Ll08 | 05:10:24.17 | -70:14:6.53 | 236.3 | 2.8 |  | S | ST17 (13) |
| Ll07-1 | 05:26:21.53 | -68:39:59.29 | 267.2 | 0.9 |  | P |  |
| Ll07-2 | 05:26:22.02 | -68:39:57.16 | 266.2 | 1.0 |  | P |  |
| Ll06 | 05:04:38.21 | -70:54:44.17 | 231.6 | 1.9 |  | PE |  |
| Ll05 | 04:58:42.49 | -66:08:35.55 | 275.3 | 1.5 |  | S |  |
| Ll04-1 | 05:03:56.15 | -67:20:39.50 | 270.9 | 1.4 |  | PE |  |
| Ll04-2$^{$\dag$}$ | 05:03:55.86 | -67:20:44.97 | 267.9 | – |  | – | Field 12 (12) |
| Ll03 | 05:37:54.86 | -69:34:35.71 | 265.2 | 1.1 |  | S |  |
| Ll02 | 04:54:8.18 | -66:46:30.48 | 274.5 | 1.1 |  | PE |  |
| Ll01 | 05:26:1.24 | -67:30:11.98 | 287.1 | 1.1 |  | SE |  |

: Source List

Table notes: $^{a}$ Source velocities measured using the HCO$^+$(4-3) line for a 1.0 pc diameter region around each continuum peak. $^{b}$ If multiple submillimeter sources are associated with a single infrared source, their luminosities were estimated based on the ratio of their continuum fluxes. $^{c}$ “$\checkmark$” and “?” indicate that the source is associated with a hot core or a hot core candidate, respectively. $^{d}$ Infrared spectral group classified in (cite: Sea09). See Section [5.3.3](#sec_disc_IRtype) for details. $^{$\dag$}$ These sources are spatially well separated from the infrared source, and their luminosities and infrared spectral types are unknown.

## Observations

The MAGOS observations were conducted with ALMA in October 2019 during Cycle 7. The sky frequency of 343.90–344.83, 344.89–347.70, 356.20–359.68 GHz, were covered by five spectral windows with a velocity resolution of 0.41–0.43 km s$^{-1}$. The total number of 12 m antennas used was 41–46, where the minimum–maximum baseline lengths were 14–783 m. The typical precipitable water vapor was 0.5–1.1 mm during the observations. The on-source integration time per target was 7.6 minutes and the total observation time for all LMC targets was 6.7 hours.

## Data reduction

Raw data was processed with the *Common Astronomy Software Applications* (CASA) package (cite: casa2022). We performed the imaging process with the pipeline-calibrated visibility data provided by the observatory. The CASA task `tclean` was used for imaging and the masking was done using the auto-multithresh algorithm. The original synthesized beam size is 0.30$''$–0.31$''$ $\times$ 0.37$''$–0.39$''$ with the Briggs weighting and a robustness parameter of 0.5. For the spectral analysis in this work, all line images were restored to have a common circular beam size of 0.40$''$, which corresponds to 0.1 pc at the distance of the LMC. Continuum images have a typical beam size of 0.30$''$ $\times$ 0.37$''$. The maximum recoverable scale is about 4$\ensuremath{''}$. The images were corrected for the primary beam pattern using the `impbcor` task in CASA. The aggregate continuum image was constructed by selecting line-free channels. A typical rms noise level of continuum images is 0.1-0.2 mJy/beam. The continuum emission was subtracted from the spectral data using the `uvcontsub` task in CASA.

# Results

## Continuum and SO emission maps

To characterize the spatial distributions of submillimeter emission toward the observed protostellar objects, we first examine their continuum and SO(8$_8$–7$_7$) emission maps, which are shown in Appendix [7](#sec_app_image_all). We identified 36 continuum point sources in total, whose detailed information is summarized in Table [1](#sourcelist). CO(3–2) and HCO$^{+}$(4–3) lines are detected in all sources, and HCO$^+$ images are presented in (cite: Tok23).

## Spectra

To further investigate the physical and chemical properties of the detected sources, we extracted spectra and continuum fluxes from the 0.41$''$ (0.1 pc) diameter circular region centered at each continuum peak. For Lh09, the extraction was performed for an elliptical region covering the continuum center (0.62$''$ $\times$ 0.41$''$, position angle = 65$\ensuremath{^\circ}$), since its high-excitation SO$_2$ emission is elongated. The rms noise levels of the spectral data are typically 0.24–0.30 K for sources located at the center of the observed field. We identified spectral lines with the aid of the Cologne Database for Molecular Spectroscopy[^1] (cite: Mul01; Mul05) and the molecular database of the Jet Propulsion Laboratory[^2] (cite: Pic98).

## Hot core identification

Hot cores are identified based on the presence of compact high-temperature gas associated with continuum sources. In this work, gas temperatures are estimated by excitation analyses of SO$_2$ and/or CH$_3$OH lines (see Section [4](#sec_ana)), and sources with rotational temperatures exceeding 100 K are classified as hot cores. Nine hot cores (Lh10, Lh09, Lh08, Lh07, Lh05-1, Lh05-2, Lh03, Lm10, and Ll10) and one hot-core candidate (Lm07) are identified in this survey (see Section [4.5](#sec_disc_indiv) for their details).

The spectra of the identified hot cores are shown in Appendix [8](#sec_app_spec), and the detected molecules are summarized in Table [2](#tab_MolSum). For the detected lines, we estimate the peak brightness temperatures, full widths at half maximums (FWHM), central velocities, and integrated intensities by fitting Gaussian profiles. The measured line intensities for all continuum sources are summarized in Appendix [8](#sec_app_spec) for the selected transitions.

Figures [\[img1\]](#img1)–[2](#img3) show integrated intensity distributions of high-excitation CH$_3$OH, SO$_2$, and SO lines for the hot cores. The images are constructed by integrating spectral data in the velocity range where the emission is detected. For CH$_3$OH and SO$_2$, high-excitation lines are stacked to reduce the noise level. The intensity peaks of these molecular emission coincide with those of the continuum emission as shown in the figures. In all hot cores, the spatial offsets between the peaks of the high-temperature molecular gas emission and the continuum sources are smaller than half the beam size, suggesting that the present observations are tracing hot-core regions in the vicinity of embedded protostars.

| Source |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | RRL$^{a}$ |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Lh10 | $\checkmark$ | $\checkmark$ | $\checkmark$ | ? | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | – | – | – | – | $\checkmark$ |
| Lh09 | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | – | – | – | – | $\checkmark$ |
| Lh08 | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | – | – | ? | – | – | – | ? |
| Lh07$^{$\dag$}$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – |
| Lh05-1 | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | – | $\checkmark$ | $\checkmark$ | – | – | – |
| Lh05-2 | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | $\checkmark$ | – | $\checkmark$ | – | – | ? | – |
| Lh03 | $\checkmark$ | $\checkmark$ | $\checkmark$ | NA | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | $\checkmark$ | – | – | – | – |
| Lm10 | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | – |
| Lm07 | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | $\checkmark$ | $\checkmark$ | – | – | – | – | – | – | – | – | – |
| Ll10 | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | – | – | – | – | $\checkmark$ | – | – | – | – |

: Summary of detected species

Table notes: “$\checkmark$": detection, “?”: tentative detection, “–”: non-detection, "NA": data not available because the line falls outside the frequency coverage. $^{a}$ Radio Recombination Line (RRL), H37$\gamma$. $^{$\dag$}$ In Lh07, , , and are also detected, and is tentatively detected.

![](f2.pdf)

![](f3.pdf)

![](f4.pdf)

![](f5.pdf)

![](f6.pdf)

![](f7.pdf)

# Data Analysis

## Rotation diagram analysis of and 

Multiple high-excitation lines are detected for hot-core sources, and these lines are used for the excitation analysis. We use the rotation diagram method with the following standard formulae to estimate column densities and temperatures (cite: Sut95):

$$\begin{equation}
\log \left(\frac{ N_{u} }{ g_{u} } \right) = - \left(\frac {\log e}{T_{\mathrm{rot}}} \right) \left(\frac{E_{u}}{k} \right) + \log \left(\frac{N}{Q(T_{\mathrm{rot}})} \right),  \label{Eq_rd1}
\end{equation}$$ where $$\begin{equation}
\frac{ N_{u} }{ g_{u} } = \frac{ 3 k \int T_{\mathrm{b}} dV }{ 8 \pi^{3} \nu S \mu^{2} }, \label{Eq_rd2} \\ 
\end{equation}$$

and $N_{u}$ is a column density of molecules in the upper energy level, $g_{u}$ is the degeneracy of the upper level, $k$ is the Boltzmann constant, $\int T_{\mathrm{b}} dV$ is the integrated intensity estimated from the observations, $\nu$ is the transition frequency, $S$ is the line strength, $\mu$ is the dipole moment, $T_{\mathrm{rot}}$ is the rotational temperature, $E_{u}$ is the upper state energy, $N$ is the total column density, and $Q(T_{\mathrm{rot}})$ is the partition function at $T_{\mathrm{rot}}$. Eq. [\[Eq_rd1\]](#Eq_rd1) is derived from Eq. [\[Eq3\]](#Eq3) assuming $T_{\mathrm{rot}}$ $>>$ $T_{\mathrm{bg}}$. We assume an optically thin condition and the local thermodynamic equilibrium (LTE). All the spectroscopic parameters required in the analysis are extracted from the CDMS or JPL database.

The results of the analyses are shown in Figure [3](#rd1) for CH$_3$OH, Figure [4](#rd2) for SO$_2$, and Figure [5](#rd3) for other molecular species. For SO$_2$ and $^{34}$SO$_2$, a straight-line fit is separated into low- and high-temperature regimes ($E_{u}$ $\lesssim$80 K and $E_{u}$ $\gtrsim$90 K), because different temperature components are seen in the diagram. The derived rotational temperatures of CH$_3$OH or SO$_2$ exceed 100 K, suggesting the presence of high-temperature gas associated with each protostar.

## Column densities of other molecules

Column densities of other molecules are derived with the assumed temperatures. The following equation is used based on the standard treatment of optically thin emission in the LTE (cite: Yam17):

$$\begin{equation}
N = \frac{3 k Q(T_{\mathrm{rot}}) \int T_{\mathrm{b}} dV}{8 \pi^{3} \nu S \mu^{2}} \Bigg{\{} 1 - \frac{\exp(h \nu / kT_{\mathrm{rot}})-1}{\exp(h \nu / kT_{\mathrm{bg}})-1} \Bigg{\}}^{-1} \exp\Bigg{(}\frac{E_u}{kT_{\mathrm{rot}}}\Bigg{)}  \label{Eq3}, 
\end{equation}$$ where $N$ is the total column density, $k$ is the Boltzmann constant, $T_{\mathrm{rot}}$ is the rotational temperature, $T_{\mathrm{bg}}$ is the cosmic microwave background temperature (2.73 K) , $Q(T_{\mathrm{rot}})$ is the partition function at $T_{\mathrm{rot}}$, $\int T_{\mathrm{b}} dV$ is the integrated intensity estimated from the observations, $\nu$ is the transition frequency, $S$ is the line strength, $\mu$ is the dipole moment, $h$ is the Planck constant, and $E_{u}$ is the upper state energy. All the spectroscopic parameters required in the analysis are extracted from the CDMS database, except for , , and , which are based on the JPL database.

The assumed rotational temperatures are summarized in the table in Appendix [9](#sec_app_n). $T_{\mathrm{rot}}$ for SO and are assumed to be the same as the high-temperature component of , presuming that these sulfur-bearing species trace the same gas in a hot core. $T_{\mathrm{rot}}$ for the other complex species (i.e., CH$_3$CHO, HC$_3$N, and H$_2$CCO in Lh07; HCOOH in Lh05-1 and Lh05-2; HCOOH, HCOOCH$_3$, C$_2$H$_5$OH, CH$_3$CHO in Lm10) are assumed to be the same as that of CH$_3$OH.

The rotational temperature ($T_{\mathrm{rot}}$) of is assumed to be equal to that of high-temperature SO$_2$ or CH$_3$OH, or their average when both are available, assuming that SiO originates from a hot core. A 50$\%$ uncertainty is applied to the assumed $T_{\mathrm{rot}}$ of SiO, and this is propagated into the column density calculation. exhibits extended spatial distributions (cite: Tok23), and is therefore unlikely to trace the high-temperature gas component of hot core regions. Therefore, the column density of H$^{13}$CO$^+$ was calculated by varying the rotational temperature between 30 K and 60 K, assuming that it traces a relatively cold and extended gas component.

## H$_2$ column density and abundances 

The column density of molecular hydrogen ($N_{\mathrm{H_2}}$) is estimated from the dust continuum data based on the standard treatment of optically thin emission. We use the following equation:

$$\begin{equation}
N_{\mathrm{H_2}} = \frac{F_{\nu} / \Omega}{2 \kappa_{\nu} B_{\nu}(T_{d}) Z \overline{M}_w m_{\mathrm{H}}} \label{Eq_h2}, 
\end{equation}$$

where $F_{\nu}/\Omega$ is the continuum flux density per beam solid angle as estimated from the observations, $\kappa_{\nu}$ is the mass absorption coefficient of dust grains coated by thin ice mantles taken from (cite: Oss94) and we use 1.96 cm$^2$ g$^{-1}$ at 850 $\mu$m, $T_{d}$ is the dust temperature and $B_{\nu}(T_{d})$ is the Planck function, $Z$ is the dust-to-gas mass ratio, $\overline{M}_w$ is the mean atomic mass per hydrogen (cite: Cox00), and $m_{\mathrm{H}}$ is the hydrogen mass. The continuum fluxes are measured as beam-averaged values over the same regions as the molecular lines, which cover both continuum and molecular line peaks. We use the dust-to-gas mass ratio of 0.0027, which is derived by dividing the Galactic value (0.008) by three, based on the metallicity difference of the LMC. The dust temperature is assumed to be the same as the $T_{\mathrm{rot}}$ of high-temperature SO$_2$ or CH$_3$OH, or their average if both are available, assuming that the dust emission mainly arises from a hot-core region. The actual dust temperature in a hot core is uncertain and may differ from the assumed value. Here, we adopt a 30$\%$ uncertainty for $N_{\mathrm{H_2}}$, which corresponds to the variation in $N_{\mathrm{H_2}}$ that would result from a factor of 1.5 deviation in the assumed dust temperature.

For Lh09, its continuum emission may be dominated by free-free emission even at 850 $\mu$m, as pointed out in (cite: Nay19) based on mm and cm continuum flux of this region. With the above method, the $N_{\mathrm{H_2}}$ of Lh09 is estimated to be 2 $\times$ 10$^{24}$ cm$^{-2}$, but this should be considered as an upper limit, given a possible contribution from free-free emission. The $N_{\mathrm{H_2}}$ values of high-luminosity hot-core sources (Lh07, Lh08, Lh10) range from 4 $\times$ 10$^{23}$ to 8 $\times$ 10$^{23}$ cm$^{-2}$. Considering this range, we here assume $N_{\mathrm{H_2}}$ = 8 $\pm$ 4 $\times$ 10$^{23}$ cm$^{-2}$ for Lh09.

The 850 $\mu$m continuum brightnesses for all sources are summarized in the table in Appendix [8](#sec_app_spec). The derived H$_2$ column densities ($N_{\mathrm{H_2}}$) for hot-core sources are listed in the table presented in Appendix [9](#sec_app_n). Fractional molecular abundances relative to H$_2$ are calculated using these $N_{\mathrm{H_2}}$ values and are also included in the table.

The $N_{\mathrm{H_2}}$ values of the present hot-core sources range from 1 to 8 $\times$ 10$^{23}$ cm$^{-2}$, corresponding to gas number densities of $n_{\mathrm{H_2}}$ = 0.5–4 $\times$ 10$^6$ cm$^{-3}$, assuming a source diameter of 0.1 pc and a uniform spherical gas distribution around each protostar. Since the target sources are not spatially well resolved, these gas densities should be regarded as lower limits.

![](f8.pdf)

## Optical thickness of CH$_3$OH and SO$_2$ lines

Isotopologues of CH$_3$OH and SO$_2$ are detected in several sources, and we therefore estimate the optical depth of the main species in this section. For $^{13}$CH$_3$OH, one clean line, $^{13}$CH$_3$OH(14$_{1}$ A$^-$–14$_{0}$ A$^-$, 347.1882830 GHz, $E_{u}$ = 254 K) is detected in Lh07, which is the most COM-rich hot core (Figure [6](#13CH3OH)). The $^{13}$CH$_3$OH(7$_{2}$ E–6$_{1}$ E, 357.6579540 GHz) line is also detected; however, it is blended with SO$_2$(9$_{4,6}$–9$_{3,7}$, 357.6718206 GHz) and $^{33}$SO$_2$(20$_{0,20}$–19$_{1,19}$, 357.6588389 GHz), and thus is not used in the following discussion. Using the rotational temperature derived from $^{12}$CH$_3$OH, the column density of $^{13}$CH$_3$OH is calculated, yielding a $^{12}$CH$_3$OH/$^{13}$CH$_3$OH column density ratio of $(3.4 \times 10^{16}) / (1.0 \times 10^{15}) = 34$. This value is slightly lower than, the $^{12}$C/$^{13}$C ratio of HCN previously reported for the LMC (cite: Wan09). This trend is in line with carbon isotope fractionation in dense gas, which tends to enrich in $^{13}$C and to deplete HCN in $^{13}$C (cite: ichimura24). Even if we assume that the intrinsic $^{12}$C/$^{13}$C ratio of CH$_3$OH is 49, the optical depth of the $^{12}$CH$_3$OH emission is estimated to be $\tau \sim 0.7$ (cite: Gol99). Even in the most COM-rich source, $^{12}$CH$_3$OH emission appears to be only moderately thick. In other sources, the CH$_3$OH column densities are more than a factor of two lower than in Lh07, and $^{13}$CH$_3$OH lines are not detected, suggesting that the $^{12}$CH$_3$OH emission is optically thin in these sources.

$^{34}$SO$_2$ is detected in seven hot cores, and analysis using rotational diagrams has been carried out. The derived $^{32}$SO$_2$/$^{34}$SO$_2$ column density ratios are 11 (Lh03), 7 (Lh05-1), 15 (Lh05-2), 11 (Lh07), 6 (Lh08), 11 (Lh09), and 9 (Lh10), considering only the high-temperature components. These values are about 1.0 to 2.5 times lower than the $^{32}$S/$^{34}$S ratio reported for the LMC (cite: Wan09; ST20; Gon23). Based on these results, the optical depth of the $^{32}$SO$_2$ emission is estimated to be up to $\tau \sim2.2$.

In the following discussion sections, the column densities of CH$_3$OH and SO$_2$ are, when available, based on $^{13}$CH$_3$OH and $^{34}$SO$_2$ data, respectively. We adopt $^{12}$C/$^{13}$C = 49 and $^{32}$S/$^{34}$S = 15, as reported in the references above. Uncertainties of 30 $\%$ and 10 $\%$ are assumed for the carbon and sulfur isotope ratios, respectively, and these are propagated into the column density calculations.

## Notes on Individual Hot Cores

In this survey, nine hot cores and one hot-core candidate are identified based on the presence of compact, high-temperature gas associated with continuum sources. One hot core (Lm10) and one hot-core candidate (Lm07) are newly identified in this survey. A brief description of each source is provided below.

### Lh10

This source was reported as a hot core in (cite: ST16b) and represents the first hot core identified outside the Milky Way. Only H$_2$CO has been detected as an organic molecule in the previous study; COMs such as CH$_3$OH have not been detected to date, whereas sulfur-bearing species like SO and SO$_2$ are abundant. This study confirms these results, and the derived molecular abundances are consistent with those reported by (cite: ST16b).

### Lh09

This source is located in a region reported by (cite: Nay19) as a super star cluster candidate, where active star formation has been observed. Unlike the other hot cores, the high-excitation SO$_2$ emission is elongated and slightly offset to the northwest from the continuum source. No COMs are detected in this work. Recent JWST MIRI observations have obtained infrared spectra around Lh09, in which hydrogen recombination lines, H$_2$ lines, and fine-structure lines have been detected (cite: Nay24c).

### Lh08

This source shows tentative signs of CH$_3$OH emission in the multiline stacked images (see Figure [\[img1\]](#img1)), however, high-$E_u$ CH$_3$OH lines are not significantly detected in the spectra. On the other hand, (cite: Bro25) reported it as a hot core and detected high-temperature CH$_3$OH gas, albeit with a low abundance. In the present study, we conservatively provide an upper limit based on the non-detection of the CH$_3$OH(16$_1$ A$^-$–15$_2$ A$^-$) line. This upper limit is comparable to the value reported by (cite: Bro25). High-temperature SO$_2$ gas is clearly detected in both studies.

### Lh07

This source has the highest CH$_3$OH abundance among the currently known hot cores in the LMC. It was reported as a hot core by (cite: Sew18), and COMs larger than CH$_3$OH, namely CH$_3$OCH$_3$ and HCOOCH$_3$ were detected. In addition to these species, the present study also detects HCOOH, HC$_3$N, C$_2$H$_5$OH, and tentatively H$_2$CCO. The CH$_3$OH and SO$_2$ column densities derived in this work are approximately three times higher than those reported by (cite: Sew22a). This difference is likely due to our use of isotopologues for deriving column densities or different spectral coverage.

### Lh05-1,2

These two hot cores are located in the same region. They are separated by only about 3$\ensuremath{''}$ (0.7 pc) and have nearly identical systemic velocities, suggesting a common origin from the same molecular cloud. Compared to Lh05-1, Lh05-2 exhibits broader molecular line widths; for example, the FWHM of SO$_2$(19$_{1,19}$–18$_{0,18}$) is 3.9 km s$^{-1}$ for Lh05-1 and 11.6 km s$^{-1}$ for Lh05-2. Although their molecular abundances are similar, these results indicate significant differences in gas kinematics within the hot cores. Both sources were reported as hot cores by (cite: Sew22a), and the molecular abundances obtained in this study are consistent with theirs.

### Lh03

This source was previously analyzed in detail by (cite: ST20) based on ALMA Band 6 and 7 spectra. That study detected CH$_3$OH and CH$_3$CN but no larger COMs, which is consistent with the results of the present survey. Our CH$_3$OH abundance is approximately twice as high, likely due to the limited number of CH$_3$OH lines covered in our survey. (cite: ST16) conducted VLT/ISAAC observations targeting the 3.53 $\mu$m CH$_3$OH ice band, but no detection was made ($N$(CH$_3$OH)/$N$(H$_2$O) $<$6 $\%$). Our SO$_2$ column density is consistent with that reported by (cite: ST20).

### Lm10

This hot core is newly discovered in the present survey. It is the second most COM-rich source after Lh07 among the present samples, with detections of organic molecules such as CH$_3$OH, HCOOH, and CH$_3$OCH$_3$. This represents the first detection of COMs larger than CH$_3$OH in a hot core located outside the LMC bar region. It is situated near Lh09, a COM-poor hot core (Fig. [1](#distribution)). Recent JWST MIRI observations have obtained spectra of an infrared source near Lm10, in which the CO$_2$ ice absorption as well as emission features from PAHs, H$_2$, and fine-structure lines are detected (cite: Nay24c).

### Lm07

This source exhibits compact SO$_2$ gas at $\sim$80 K but no detection of CH$_3$OH. Since gas exceeding 100 K was not detected and the line intensities are weaker than those of other hot cores, we classify this source as a hot core candidate. It is situated in a highly active star-forming region near 30 Doradus.

### Ll10

This is the least luminous hot core among those observed in this survey. It was reported as a hot core (source 14A) by (cite: Gol24), and our molecular abundances are consistent with their results.

# Discussion

## Distribution of hot cores within the LMC

The spatial distribution of the observed hot cores within the LMC is shown in Figure [1](#distribution). The bar region of the LMC, characterized by its high stellar density and relatively high metallicity, is shown with a light-blue background in the figure. Among the present hot core samples (including one candidate), five out of ten hot cores are located within the bar region. In the direction of N11, the second-largest H II region in the LMC after 30 Dor and located at the northwestern edge of the LMC, four sources (Ll05, Lm01, Ll02, Lm09) were observed in this survey, but no hot cores were detected.

All COM-poor hot cores (Lh10, Lh09, Lh08, Lm07) are located outside the bar region. As pointed out by (cite: Gol24), these regions are considered to have relatively low metallicity, which may suggest that environmental differences influence the chemical evolution of hot cores. However, Lm10, the second most COM-rich hot core after Lh07, is located near the COM-poor source (Lh09), and this area lies outside the bar region.

This implies that low local metallicity may be a necessary condition for triggering COM-poor hot core chemistry; however, it is not a sufficient condition, and additional factors besides low metallicity may also play a role. Further discussion on the trigger of COM-poor hot-core chemistry in the LMC is presented in Section [5.5](#sec_disc_molab2).

![](f9.pdf)

![](f10.pdf)

## Molecular tracer of LMC hot cores

Identifying molecular tracers that can distinguish sources associated with hot cores provides valuable information for planning larger-sample surveys. Figure [7](#vsIntensity) shows the relationships between integrated or peak line intensities and bolometric luminosities for all sources. Overall, sources associated with hot cores tend to exhibit stronger line intensities, and more luminous sources show stronger line emission.

Of particular interest in these plots is the utility of the high-excitation SO line (8$_{8}$–7$_{7}$, $E_{u}$ = 88 K, $S\mu^{2}$ = 18.6 Debye$^2$) as a good tracer of LMC hot cores. As shown in the figure, all LMC hot cores show the strong high-excitation SO line, which clearly distinguish them from non-hot-core sources. All sources with SO integrated intensities greater than approximately 20 K km s$^{-1}$ are hot cores accompanied by high-excitation SO$_2$ and/or CH$_3$OH lines, whereas no such high-excitation lines are detected in sources below this SO threshold. The hot core candidate, Lm07, also shows a relatively high SO integrated intensity, placing it between hot-core and non-hot-core sources. Similar trends are also seen for the SO$_2$ ($E_{u}$ = 49 and 168 K) and SiO ($E_{u}$ = 75 K) lines, suggesting that strong emission in these lines, along with their spatial association with continuum sources, could serve as good evidence for the presence of hot cores. However, because these lines are generally weaker than the SO (8$_{8}$–7$_{7}$) line, the high-excitation and large-$S\mu^{2}$ SO line is likely more suitable for large-sample surveys.

In the case of the high-excitation CH$_3$OH line ($E_{u}$ = 333 K), some hot cores show non-detections. This is likely due to the large source-to-source variation in the abundance of organic molecules in LMC hot cores (see Section [5.4](#sec_disc_molab)). While CH$_3$OH is often used as a tracer of hot cores in nearby solar-metallicity star-forming regions, it may not serve as a universal tracer in LMC hot cores, which exhibit different chemical evolution. Regarding low-excitation CH$_3$OH, it is detected with similar intensities in some non-hot-core sources as in hot cores, indicating that it is not necessarily associated exclusively with hot cores. Low-excitation CH$_3$OH gas may be released via non-thermal desorption mechanisms, such as shock spattering, which likely contribute to its detection in non-hot-core sources.

For the H$^{13}$CO$^+$ line ($E_{u}$ = 42 K), the separation between hot-core and non-hot-core sources is less clear compared to the SO line, making it difficult to identify hot cores based solely on the intensity of H$^{13}$CO$^+$. For the CO ($E_{u}$ = 33 K) and HCO$^+$ ($E_{u}$ = 43 K) lines, their peak intensities are shown in the figure, as these lines are considered to be optically thick. The HCO$^+$ peak intensities show a good correlation with luminosity (correlation coefficient = 0.84), likely reflecting the presence of warmer and denser gas surrounding more luminous protostars. Even in the CO and HCO$^+$ plots, sources associated with hot cores tend to show higher line intensities overall. However, the separation between hot-core and non-hot-core sources is not as prominent as with the high-excitation SO line. Particularly, at the lower-luminosity end, it is difficult to identify hot-core sources based solely on CO or HCO$^+$ peak intensities.

The continuum emission show similar behavior to CO and HCO$^+$ (bottom right of Fig. [7](#vsIntensity)). The continuum fluxes show a good correlation with luminosity (correlation coefficient = 0.89) and tend to be higher in hot core sources. However, since continuum flux alone does not provide sufficient information on the temperature of molecular gas, high-excitation molecular line tracers are more reliable indicators for hot core identification.

We note that luminosity information is missing for some sources, and that the infrared data used to derive luminosities have significantly lower spatial resolution compared to the ALMA data (see Section [2.1](#sec_tar)). In contrast, ALMA submillimeter continuum traces compact components well. Therefore, we also plot the line intensities against the 850 $\mu$m continuum brightnesses in Figure [8](#vsIntensity_conti). As mentioned in the previous paragraph, luminosities and 850 $\mu$m continuum brightnesses show a good correlation; thus, similar trends are observed in this comparison as in the one with luminosity discussed above. For the high-excitation SO line, the integrated intensities show a good correlation with the 850 $\mu$m continuum, with a correlation coefficient of 0.87. This correlation is somewhat stronger than that seen in the comparison with luminosity (i.e., correlation coefficient = 0.74 in the SO panel in Figure [7](#vsIntensity)). For the HCO$^+$ line, the correlation is even tighter, with a correlation coefficient of 0.93. Other lines also exhibit trends similar to those observed in the comparison with luminosity.

## Molecular abundances vs. physical properties

To investigate the physical factors contributing to the chemical diversity of hot cores, this section compares the physical properties and chemical compositions of LMC hot cores.

### vs. Rotational temperatures

Figure [9](#vsTrot) shows the relationship between molecular abundances and rotational temperature for CH$_3$OH and SO$_2$ in LMC hot cores. A strong correlation is observed for SO$_2$ (correlation coefficient = 0.91), suggesting that temperature rise in hot core regions contribute to enhanced SO$_2$ abundances. This trend is likely related either to an additional supply of sulfur from dust grains in high-temperature gas or to enhanced SO$_2$ synthesis via high-temperature gas-phase chemistry (cite: NM04).

In contrast, CH$_3$OH shows no significant correlation with $T_\mathrm{rot}$. The correlation coefficient based on eight hot cores with high-temperature CH$_3$OH detections, including two literature samples from (cite: Sew22a), is 0.10. Furthermore, there are hot cores in which CH$_3$OH is not detected despite the presence of high-temperature gas traced by SO$_2$.

Sublimation of ice mantles is a key process that significantly influences the chemical composition of hot cores, particularly for species like CH$_3$OH, which are predominantly formed via surface reactions on dust grains during the cold prestellar stage (cite: McC23). Binding energies on water ice surfaces have been reported to be $\sim$2000 K for SO (cite: Ngu24) and $\sim$5000 K for SO$_2$ and CH$_3$OH (cite: Per22; Das18), respectively. These values correspond to sublimation temperatures of $\sim$40 K for SO and $\sim$100 K for SO$_2$ and CH$_3$OH, respectively. The rotational temperatures of SO$_2$ measured for hot cores without CH$_3$OH detections (Lh10, Lh09, and Lh08) suggest that these sources possess physical conditions suitable for ice sublimation. However, CH$_3$OH is deficient in the sublimated high-temperature gas in these sources. This implies that factors other than ice sublimation, such as the efficiency of organic molecule formation during the ice-mantle growth stage, or molecular destruction in the hot core phase, may significantly affect the CH$_3$OH abundance in LMC hot cores.

![](f11.pdf)

### vs. Line widths

Figure [10](#vsFWHM) shows the relationship between line FWHM and molecular abundances. No clear correlation is observed for CH$_3$OH and SO$_2$. For SO and SiO, a weak positive correlation is seen (correlation coefficient $\sim$0.6), but it cannot be regarded as a strong one. This suggests that there is no strong link between non-thermal gas motions in hot-core regions and their chemical composition.

In shock regions associated with protostellar outflows, molecular abundances are expected to increase. However, with the present survey data obtained at a resolution of 0.1 pc, chemical and kinematic signatures attributable to shock regions would not be fully captured, or would be diluted. Figure [11](#Cont_vs_FWHM) presents a comparison between the FWHM of the HCO$^+$(4-3) line and the continuum brightness. As shown in the figure, a strong correlation is found regardless of the presence or absence of hot cores (correlation coefficient = 0.93). This correlation may reflect that more massive cores induce stronger feedback, resulting in more pronounced non-thermal gas motions. At the present spatial resolution, the line widths of cores appear to be primarily governed by their mass. Future higher-resolution observations are expected to reveal the chemical and physical properties of molecular gas associated with shock regions around LMC hot cores (Chen et al., in prep.).

![](f12.pdf)

![](f13.pdf)

### vs. Infrared spectral characteristics

Figure [12](#vsIR) shows a comparison between the molecular compositions of hot cores and their infrared spectral characteristics. (cite: Sea09) classified massive YSOs in the LMC based on 5–38 $\mu$m spectra obtained with Spitzer/IRS. In their classification, the sources were grouped into five categories, S, SE, P, PE, and E. Sources that did not fall into any of these categories were labeled as F, and those for which classification was not possible due to limited spectral coverage were labeled as U. The S group includes sources dominated by silicate and ice absorption features, while the SE group shows similar features along with fine-structure lines from ionized gas. The P group is characterized by prominent PAH emission features, and the PE group exhibits both PAH features and fine-structure lines. The E group consists of sources in which fine-structure lines from ionized gas dominate the spectrum. In the MAGOS project, we targeted sources belonging to the S, SE, P, and PE groups, and identified at least one hot core in each group.

As shown in Figure [12](#vsIR), there is no clear correlation between the infrared spectral group and molecular composition. Sources with low CH$_3$OH abundances are not confined to any specific infrared spectral group. (cite: Sea09) proposed that YSOs evolve in the sequence S $\rightarrow$ SE $\rightarrow$ P $\rightarrow$ PE, corresponding to an increasing prominence of infrared emission features. Within the current sample, there is no apparent relationship between the molecular compositions of hot cores and the evolutionary stages inferred from their infrared spectral characteristics. To remove systematic uncertainties associated with $N_{\mathrm{H_2}}$ normalization, Figure [12](#vsIR) also shows abundance ratios normalized by SO$_2$, but this comparison reveals a similar lack of correlation.

It should be noted, however, that there is a significant difference in spatial scale between the regions from which molecular lines were extracted with ALMA and those observed in infrared spectroscopy with Spitzer. Given the slit width of Spitzer/IRS, the infrared spectra were extracted from regions approximately 4$\ensuremath{''}$ to 11$\ensuremath{''}$ in size, centered on the infrared point source. In contrast, the spectral extraction region in the present ALMA observations corresponds to 0.41$''$. Although the hot core sources are the dominant contributors to the submillimeter continuum flux, and possibly to the infrared flux, within the field of view, the Spitzer spectra are likely affected by non-negligible contamination from emission components outside the hot core regions. Such contamination can significantly affect the evaluation of the evolutionary stage of protostars based on absorption features in their infrared spectra. Future high-spatial-resolution observations with JWST will be essential for obtaining infrared data that are directly comparable to the ALMA observations.

![](f14.pdf)

### vs. Star formation activities

Figure [13](#vsSF) shows a comparison between the molecular compositions of hot cores and the degree of star formation activity in their surrounding environments. The 24 $\mu$m infrared emission primarily traces thermal emission from warm dust and is commonly used as a tracer of large-scale star formation rates (cite: Cal07; Ken09). In this figure, we plot the 24 $\mu$m surface brightness averaged over a 10 pc radius around each hot core, using the 24$\mu$m emission map of the LMC obtained by Spitzer/MIPS (cite: Mei06). The hot core candidate, Lm07, is also included in the plot, because it is located in the most active region near 30 Dor among the present hot core samples.

Hot cores with no CH$_3$OH detection (Lh10, Lh09, Lh08, and Lm07) are all located in regions with relatively high 24 $\mu$m brightness ($\gtrsim$2 mJy arcsec$^{-2}$). A similar trend is seen in the plot of abundance ratios of CH$_3$OH normalized by SO$_2$. For SO$_2$, no apparent relationship is found between its abundance and the 24 $\mu$m brightness of the surrounding regions.

It cannot be ruled out that increased radiation fields associated with active star formation in the natal molecular cloud may contribute to triggering COM-poor hot core chemistry. However, given that CH$_3$OH abundances vary by nearly two orders of magnitude among sources with similar 24 $\mu$m brightness, it is evident that the degree of surrounding star formation activity alone does not determine the presence or absence of organic molecules in hot cores.

![](f15.pdf)

![](f16.pdf)

## Molecular abundances variation within LMC hot cores

The large source-to-source variation of CH$_3$OH abundances reported in previous studies of the LMC is also confirmed in the present survey, which adopted a uniform spatial and spectral setup. Figure [14](#abundance)(a) shows a comparison of metallicity-scaled abundances of CH$_3$OH and SO$_2$ in hot cores across environments with different metallicities.

To focus on the high-temperature gas components associated with hot cores, this study derives $N_{\mathrm{H_2}}$ using dust temperatures estimated from CH$_3$OH and/or SO$_2$. For the SMC hot cores plotted in the figure, $N_{\mathrm{H_2}}$ has been recalculated using the same method as in this study, based on the data from (cite: ST23). In the SMC, compact and warm gas components have only been detected in SO$_2$, while CH$_3$OH is detected in just one source, and only as an extended component at $\sim$40 K. Thus, for the SMC hot cores in this figure, we plot upper limits of CH$_3$OH estimated from the 7${_2}$ A$^+$–6${_2}$ A$^+$ transition ($E_u$ = 103 K). For the hot core in the extreme outer Galaxy, we plot values based on data obtained from the 0.1 pc region around the protostar reported by (cite: ST21), with $N_{\mathrm{H_2}}$ recalculated using the same method as in this study. For comparison, we include Galactic hot core data: CH$_3$OH values are taken from 28 hot cores reported by (cite: Bae22), while SO$_2$ values are taken from 10 hot cores reported by (cite: Sut95; Mac96; Hel97; Hat98b; Qin10; Zer12; Xu13), and their median abundances are plotted in the figure.

As shown in Figure [14](#abundance)(a), CH$_3$OH abundances exhibit large source-to-source variations even after correcting for metallicity, suggesting that its abundance in hot cores cannot be explained by metallicity scaling alone. Such large variations are not seen in SO$_2$, another common hot core tracer. Among the LMC sources, the CH$_3$OH abundance varies by a factor of $>$350 between the most enriched and most depleted sources, while the variation for SO$_2$ is a factor of 12. The spread factor, defined as 10 to the power of the 1$\sigma$ standard deviation in log$_{10}$ space (cite: Naz22b), is calculated to be $>$6.8 for CH$_3$OH and 2.2 for SO$_2$.

Figure [14](#abundance)(b) shows the abundance ratio of CH$_3$OH to SO$_2$. For comparison, Galactic hot cores with gas temperatures above 100 K from the massive protostar sample in (cite: vanGel22a) and (cite: San24) are also plotted. This comparison reveals a similar trend to that seen in the $N_{\mathrm{H_2}}$-normalized abundances. Among the LMC sources, the CH$_3$OH/SO$_2$ ratio varies by more than two orders of magnitude, with a spread factor greater than 5.4, comparable to that found for the $N_{\mathrm{H_2}}$-normalized abundances. This indicates that the large variation in CH$_3$OH abundances among LMC hot cores is not merely an artifact of the method used to derive $N_{\mathrm{H_2}}$.

![](f17.pdf)

## Trigger of COM-poor hot core chemistry

The reason why the gas-phase abundance of CH$_3$OH exhibits such large variations among LMC hot cores, particularly the extreme COM-poor nature observed in some sources, which is not typically seen in solar-metallicity environments, remains under debate. Multiple factors may influence the abundance of COMs in hot cores, including observational factors such as optical depth or beam dilution effects, as well as intrinsic physical factors such as source size and structure, the degree of ice mantle sublimation, differences in evolutionary stage, variations in shock conditions, and local physical conditions.

As discussed in Section [4.4](#sec_disc_tau), optical depth effects on CH$_3$OH are limited and unlikely to account for order-of-magnitude abundance variations. Shock conditions also appear to have a minor influence, as clear correlation is not observed between line width and line intensity, especially for CH$_3$OH and SO$_2$ (see Section [5.3.2](#sec_disc_FWHM)). Differences in evolutionary stage may have an effect, but as discussed in Section [5.3.3](#sec_disc_IRtype), there is no clear correlation between the Spitzer spectral classifications and molecular abundances. This warrants further infrared studies with higher spatial resolution.

The high-temperature components of most hot cores are not well spatially resolved in the present survey. The FWHM sizes of the continuum emission in hot cores derived from two-dimensional Gaussian fits range from 0.4$''$ to 0.6$''$, which is slightly larger than the typical continuum beam size (0.30$''$ $\times$ 0.37$''$). In contrast, the Gaussian FWHM sizes of the high-excitation SO$_2$ and CH$_3$OH emission, except for Lh09, are 0.4$''$–0.5$''$, which are roughly comparable to the 0.40$''$ beam size. One possible reason why the dust emission appears somewhat more extended is that the continuum contains contributions not only from the high-temperature dust in the hot core region but also from the surrounding, relatively low-temperature dust. However, it cannot be ruled out that the true emitting region of the high-temperature dust is intrinsically more extended than that of the high-temperature molecular gas. In this work, we derive beam-averaged column densities within the 0.1 pc (0.41$''$) diameter region under the assumption of a beam filling factor of unity for both the molecular gas and the continuum-based H$_2$ (see Section [4](#sec_ana)). If the true spatial extent of the high-excitation molecular gas is significantly smaller than that of the high-temperature dust, the molecular abundances would be underestimated due to beam dilution. This point should also be kept in mind when comparing our results with those for interferometric observations of nearby star-forming regions, where the hot gas and dust emission are spatially well resolved.

In nearby Galactic protostars, the dust opacity of the envelope and the presence of disks have been discussed as factors influencing COM intensity (cite: DeS20; Naz22a; Che25). Such effects occur on spatial scales of a hundred to several thousand au. Given the spatial resolution of the present observations (0.1 pc), these dense substructures are unlikely to affect the observed CH$_3$OH intensity (cite: Naz23). We note, however, that the current dataset does not allow us to assess how small-scale physical structures and the extent of hot gas emission are related to COM abundances. This issue will be addressed in a forthcoming paper based on high-resolution follow-up observations of the hot core sample presented here.

A clear correlation is seen between SO$_2$ abundances and rotational temperature of hot cores, with warmer cores exhibiting higher SO$_2$ abundances (see Section [5.3.1](#sec_disc_Trot)). This suggests that the source-to-source variation in SO$_2$ abundance seen in Figure [14](#abundance)(a) is largely attributable to temperature differences. In contrast, CH$_3$OH shows no such trend with temperature, and some hot cores with high-temperature gas exhibit low CH$_3$OH abundances, implying that additional factors must be considered.

Local environmental differences may influence COM abundances. Astrochemical simulations targeting the chemical evolution of hot cores in the LMC and SMC suggest that the dust temperature during the early ice formation stage can affect the gas-phase CH$_3$OH abundance in the subsequent hot core phase (cite: Ach18; ST20). This is because solid CH$_3$OH formation is sensitive to dust temperature (cite: Cha12) and is suppressed on warmer dust surfaces (cite: ST16). On the other hand, astrochemical simulations suggest that the solid SO$_2$ formation is less sensitive to the dust temperature compared to that of solid CH$_3$OH at least under the solar metallicity conditions (cite: Fur24). Variations in local metallicity and radiation field strength may introduce diversity in the physical conditions during the ice formation stage, leading to differences in CH$_3$OH abundance.

The all COM-poor hot cores are located outside the LMC bar region, as discussed in Section [5.1](#sec_disc_distribution). However, the present observations also reveal a hot core, Lm10, which exhibit rich COM abundances, despite being located near a COM-poor hot core outside the bar. This would indicate that low metallicity is not a sufficient condition for triggering COM-poor hot core chemistry. As discussed in Section [5.3.4](#sec_disc_SF), all COM-poor hot cores are found in regions with active star formation. Intense interstellar radiation fields in such environments, in combination with low metallicity, may raise the dust temperature during the ice formation stage, potentially triggering COM-poor hot core chemistry.

We also note that CH$_3$OH-non-detected hot cores are biased toward high-luminosity protostars. This suggests that UV-induced molecular destruction within hot cores may also contribute to the onset of COM-poor chemistry. If this is the case, the COM-poor hot core chemistry would originate in the protostellar stage rather than the prestellar stage.

For reference, the hot core WB89-789 SMM1 in the extreme outer Galaxy, an environment with metallicity lower than that of the LMC, exhibits rich COM chemistry (cite: ST21), and its CH$_3$OH abundance is consistent with metallicity scaling. Rich COM chemistry has also been suggested in another outer Galaxy hot core, Sh 2-283-1a SMM1 (cite: Ike25).

These sources differ from the LMC hot cores in that they have luminosities nearly an order of magnitude lower and are located in a region of relatively quiescent star formation (i.e., the outskirts of the Galaxy). The mid-infrared surface brightness within a 10 pc radius of these objects, as measured from the IRAS 25 $\mu$m data (cite: Neu84), is about 0.1–0.2 mJy arcsec$^{-2}$. Such relatively quiescent conditions may facilitate efficient COM formation even in low-metallicity environments.

Based on the above discussion, we speculate that a combination of multiple factors, including low metallicity, active star formation in the vicinity, and high protostellar luminosity, would jointly trigger the unique COM-poor hot core chemistry observed in some LMC sources. A schematic illustration summarizing the discussion is presented in Figure [15](#conceptual). Larger-sample hot-core surveys targeting low-metallicity systems, as well as more detailed investigations through astrochemical simulations incorporating a range of physical, structural, and environmental parameters, will be essential.

Finally, to investigate the origin of organic molecules in the hot core stage and to assess environmental effects, detailed observations of solid CH$_3$OH toward low-metallicity hot cores are crucial. (cite: ST16) reported the detection of CH$_3$OH ice toward two massive embedded protostars (ST6 and ST10) in the LMC, based on ground-based infrared spectroscopy with the Very Large Telescope (VLT). More recently, (cite: Sew25), using JWST, detected complex organic ices larger than CH$_3$OH toward one of these protostars, ST6. However, these protostars are not included in the present survey. Future comprehensive studies of both ice and gas toward low-metallicity hot cores will be essential for elucidating the formation of COMs and their connection to the hot core chemistry in such environments.

# Summary

- We conducted a uniform hot-core survey toward 30 spectroscopically confirmed massive protostellar objects in the LMC, using ALMA at 350 GHz with a spatial resolution of 0.1 pc.

- We detect 36 continuum sources in total. Among them, nine are identified as hot cores and one as a hot-core candidate, based on the presence of compact ($\sim$0.1 pc) and high-temperature ($\gtrsim$100 K) and/or gas. One new hot core (Lm10) is discovered, in which is detected, representing the first detection of a COM larger than in a protostar located outside the LMC bar region.

- A variety of molecules are detected in the hot cores, including , , , , , , , , , , , , , , , , , and . is tentatively detected in one source, and hydrogen radio recombination lines are detected in two sources.

- is detected in the most COM-rich hot core (Lh07, or N113 A1). The emission in this source is estimated to be only moderately optically thick ($\tau$ $\sim$0.7). In contrast, emission is optically thick in several hot cores ($\tau$ up to 2.2), and thus is used for column density estimates.

- A tight positive correlation is observed between the HCO$^+$(4-3) line widths and 850 $\mu$m continuum brightnesses. They follow the same correlation irrespective of the presence or absence of hot cores, suggesting that more massive cores induce stronger feedback, resulting in more pronounced non-thermal gas motions.

- All hot-core sources show stronger emission in the high-excitation SO line compared to non-hot-core sources, suggesting that its strong detection will be useful for identifying hot-core candidates in the LMC.

- The abundance of shows large source-to-source variations among LMC hot cores, with some sources deficient in COMs despite being associated with high-temperature gas. In contrast, such a large chemical diversity is not seen in .

- A good positive correlation is found between abundances and rotational temperatures, suggesting that the gas temperature contributes to its chemical enrichment. On the other hand, such correlation is not seen in . No clear correlation is found between molecular abundances and infrared spectral characteristics.

- The present LMC hot cores without detections are all located outside the LMC bar region and are characterized by either high luminosity or active star formation in their surroundings. We speculate that a combination of multiple factors, including locally low metallicity, active star formation in the vicinity, and high protostellar luminosity, may jointly trigger the unique COM-poor hot core chemistry observed in some LMC sources.

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2019.1.01770.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has made extensive use of the Cologne Database for Molecular Spectroscopy and the molecular database of the Jet Propulsion Laboratory. This work was supported by JSPS KAKENHI grant Nos. 20H05845, 20H05847, 21H01145, 25K07364, and 25K07365. This work was supported by NAOJ ALMA Scientific Research Grant Code 2025-29B. T. S. gratefully acknowledges support from the Uchida Energy Science Promotion Foundation. K.E.I.T. gratefully acknowledges support from Center for Fundamental Research, Institute of Science Tokyo, through a Grant-in-Aid for Challenging Research and a Grant-in-Aid for Pioneering Research. A. S. acknowledges support by the grant CNS2023-145240 (Consolida), PID2020-117710GB-I00, and PID2023-146675NB-I00 (MCI-AEI-FEDER, UE). Finally, we would like to thank an anonymous referee for insightful comments, which substantially improved this paper.

# Software

CASA (cite: McM07))

natexlab

(ref: Ach15) Acharyya, K., & Herbst, E. 2015, ApJ, 812, 142, doi: [`10.1088/0004-637X/812/2/142`](http://doi.org/10.1088/0004-637X/812/2/142)

(ref: Ach16) —. 2016, ApJ, 822, 105, doi: [`10.3847/0004-637X/822/2/105`](http://doi.org/10.3847/0004-637X/822/2/105)

(ref: Ach18) —. 2018, ApJ, 859, 51, doi: [`10.3847/1538-4357/aabaf2`](http://doi.org/10.3847/1538-4357/aabaf2)

(ref: And02) Andrievsky, S. M., Kovtyukh, V. V., Korotin, S. A., Spite, M., & Spite, F. 2001, A&A, 367, 605, doi: [`10.1051/0004-6361:20000407`](http://doi.org/10.1051/0004-6361:20000407)

(ref: Bae22) Baek, G., Lee, J.-E., Hirota, T., Kim, K.-T., & Kim, M. K. 2022, ApJ, 939, 84, doi: [`10.3847/1538-4357/ac81d3`](http://doi.org/10.3847/1538-4357/ac81d3)

(ref: Beu25) Beuther, H., Kuiper, R., & Tafalla, M. 2025, ARA&A, 63, 1, doi: [`10.1146/annurev-astro-013125-122023`](http://doi.org/10.1146/annurev-astro-013125-122023)

(ref: Bro25) Broadmeadow, A., Sewiło, M., Mundy, L., et al. 2025, ApJ, 991, 59, doi: [`10.3847/1538-4357/ade9ae`](http://doi.org/10.3847/1538-4357/ade9ae)

(ref: Cal07) Calzetti, D., Kennicutt, R. C., Engelbracht, C. W., et al. 2007, ApJ, 666, 870, doi: [`10.1086/520082`](http://doi.org/10.1086/520082)

(ref: casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Cha12) Chang, Q., & Herbst, E. 2012, ApJ, 759, 147, doi: [`10.1088/0004-637X/759/2/147`](http://doi.org/10.1088/0004-637X/759/2/147)

(ref: Cha92) Charnley, S. B., Tielens, A. G. G. M., & Millar, T. J. 1992, ApJL, 399, L71, doi: [`10.1086/186609`](http://doi.org/10.1086/186609)

(ref: Che25) Chen, Y., Garrod, R. T., Rachid, M., et al. 2025, A&A, 696, A198, doi: [`10.1051/0004-6361/202453389`](http://doi.org/10.1051/0004-6361/202453389)

(ref: Cox00) Cox, A. N. 2000, Allen’s astrophysical quantities (Springer)

(ref: Das18) Das, A., Sil, M., Gorai, P., Chakrabarti, S. K., & Loison, J. C. 2018, ApJS, 237, 9, doi: [`10.3847/1538-4365/aac886`](http://doi.org/10.3847/1538-4365/aac886)

(ref: DeS20) De Simone, M., Ceccarelli, C., Codella, C., et al. 2020, ApJL, 896, L3, doi: [`10.3847/2041-8213/ab8d41`](http://doi.org/10.3847/2041-8213/ab8d41)

(ref: Duf82) Dufour, R. J., Shields, G. A., & Talbot, Jr., R. J. 1982, ApJ, 252, 461, doi: [`10.1086/159574`](http://doi.org/10.1086/159574)

(ref: Fuk15) Fukui, Y., Harada, R., Tokuda, K., et al. 2015, ApJL, 807, L4, doi: [`10.1088/2041-8205/807/1/L4`](http://doi.org/10.1088/2041-8205/807/1/L4)

(ref: Fur24) Furuya, K. 2024, ApJ, 974, 115, doi: [`10.3847/1538-4357/ad6b20`](http://doi.org/10.3847/1538-4357/ad6b20)

(ref: Gar08b) Garrod, R. T., Weaver, S. L. W., & Herbst, E. 2008, ApJ, 682, 283, doi: [`10.1086/588035`](http://doi.org/10.1086/588035)

(ref: Gol99) Goldsmith, P. F., & Langer, W. D. 1999, ApJ, 517, 209, doi: [`10.1086/307195`](http://doi.org/10.1086/307195)

(ref: Gon23) Gong, Y., Henkel, C., Menten, K. M., et al. 2023, A&A, 679, L6, doi: [`10.1051/0004-6361/202348017`](http://doi.org/10.1051/0004-6361/202348017)

(ref: Gol24) Hamedani Golshan, R., Sánchez-Monge, Á., Schilke, P., et al. 2024, A&A, 688, A3, doi: [`10.1051/0004-6361/202349077`](http://doi.org/10.1051/0004-6361/202349077)

(ref: Hat98b) Hatchell, J., Thompson, M. A., Millar, T. J., & MacDonald, G. H. 1998, A&A, 338, 713

(ref: Hel97) Helmich, F. P., & van Dishoeck, E. F. 1997, A&AS, 124, doi: [`10.1051/aas:1997357`](http://doi.org/10.1051/aas:1997357)

(ref: Her09) Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427, doi: [`10.1146/annurev-astro-082708-101654`](http://doi.org/10.1146/annurev-astro-082708-101654)

(ref: ichimura24) Ichimura, R., Nomura, H., & Furuya, K. 2024, ApJ, 970, 55, doi: [`10.3847/1538-4357/ad47ba`](http://doi.org/10.3847/1538-4357/ad47ba)

(ref: Ike25) Ikeda, T., Shimonishi, T., Izumi, N., et al. 2025, ApJ, 988, 111, doi: [`10.3847/1538-4357/ade235`](http://doi.org/10.3847/1538-4357/ade235)

(ref: Ken09) Kennicutt, Jr., R. C., Hao, C.-N., Calzetti, D., et al. 2009, ApJ, 703, 1672, doi: [`10.1088/0004-637X/703/2/1672`](http://doi.org/10.1088/0004-637X/703/2/1672)

(ref: Kur00) Kurtz, S., Cesaroni, R., Churchwell, E., Hofner, P., & Walmsley, C. M. 2000, Protostars and Planets IV, 299

(ref: Mac96) MacDonald, G. H., Gibb, A. G., Habing, R. J., & Millar, T. J. 1996, A&AS, 119, 333

(ref: McC23) McClure, M. K., Rocha, W. R. M., Pontoppidan, K. M., et al. 2023, Nature Astronomy, 7, 431, doi: [`10.1038/s41550-022-01875-w`](http://doi.org/10.1038/s41550-022-01875-w)

(ref: McM07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mei06) Meixner, M., Gordon, K. D., Indebetouw, R., et al. 2006, AJ, 132, 2268, doi: [`10.1086/508185`](http://doi.org/10.1086/508185)

(ref: Mei10) Meixner, M., Galliano, F., Hony, S., et al. 2010, A&A, 518, L71, doi: [`10.1051/0004-6361/201014662`](http://doi.org/10.1051/0004-6361/201014662)

(ref: Mei13) Meixner, M., Panuzzo, P., Roman-Duval, J., et al. 2013, AJ, 146, 62, doi: [`10.1088/0004-6256/146/3/62`](http://doi.org/10.1088/0004-6256/146/3/62)

(ref: Mot18) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41, doi: [`10.1146/annurev-astro-091916-055235`](http://doi.org/10.1146/annurev-astro-091916-055235)

(ref: Mul05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](http://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: Mul01) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: Nay19) Nayak, O., Meixner, M., Sewiło, M., et al. 2019, ApJ, 877, 135, doi: [`10.3847/1538-4357/ab1b38`](http://doi.org/10.3847/1538-4357/ab1b38)

(ref: Nay24c) Nayak, O., Hirschauer, A. S., Kavanagh, P. J., et al. 2024, ApJ, 963, 94, doi: [`10.3847/1538-4357/ad18bc`](http://doi.org/10.3847/1538-4357/ad18bc)

(ref: Naz25) Nazari, P. 2025, arXiv e-prints, arXiv:2508.15771, doi: [`10.48550/arXiv.2508.15771`](http://doi.org/10.48550/arXiv.2508.15771)

(ref: Naz23) Nazari, P., Tabone, B., & Rosotti, G. P. 2023, A&A, 671, A107, doi: [`10.1051/0004-6361/202244801`](http://doi.org/10.1051/0004-6361/202244801)

(ref: Naz22a) Nazari, P., Tabone, B., Rosotti, G. P., et al. 2022a, A&A, 663, A58, doi: [`10.1051/0004-6361/202142777`](http://doi.org/10.1051/0004-6361/202142777)

(ref: Naz22b) Nazari, P., Meijerhof, J. D., van Gelder, M. L., et al. 2022b, A&A, 668, A109, doi: [`10.1051/0004-6361/202243788`](http://doi.org/10.1051/0004-6361/202243788)

(ref: Neu84) Neugebauer, G., Habing, H. J., van Duinen, R., et al. 1984, ApJL, 278, L1, doi: [`10.1086/184209`](http://doi.org/10.1086/184209)

(ref: Ngu24) Nguyen, T., Oba, Y., Sameera, W. M. C., Furuya, K., & Watanabe, N. 2024, ApJ, 976, 250, doi: [`10.3847/1538-4357/ad88ec`](http://doi.org/10.3847/1538-4357/ad88ec)

(ref: NM04) Nomura, H., & Millar, T. J. 2004, A&A, 414, 409, doi: [`10.1051/0004-6361:20031646`](http://doi.org/10.1051/0004-6361:20031646)

(ref: Oss94) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Pau18) Pauly, T., & Garrod, R. T. 2018, ApJ, 854, 13, doi: [`10.3847/1538-4357/aaa96a`](http://doi.org/10.3847/1538-4357/aaa96a)

(ref: Per22) Perrero, J., Enrique-Romero, J., Ferrero, S., et al. 2022, ApJ, 938, 158, doi: [`10.3847/1538-4357/ac9278`](http://doi.org/10.3847/1538-4357/ac9278)

(ref: Pic98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883, doi: [`10.1016/S0022-4073(98)00091-0`](http://doi.org/10.1016/S0022-4073(98)00091-0)

(ref: Pie13) Pietrzyński, G., Graczyk, D., Gieren, W., et al. 2013, Nature, 495, 76, doi: [`10.1038/nature11878`](http://doi.org/10.1038/nature11878)

(ref: Qin10) Qin, S.-L., Wu, Y., Huang, M., et al. 2010, ApJ, 711, 399, doi: [`10.1088/0004-637X/711/1/399`](http://doi.org/10.1088/0004-637X/711/1/399)

(ref: Rol02) Rolleston, W. R. J., Trundle, C., & Dufton, P. L. 2002, A&A, 396, 53, doi: [`10.1051/0004-6361:20021088`](http://doi.org/10.1051/0004-6361:20021088)

(ref: Rus92) Russell, S. C., & Dopita, M. A. 1992, ApJ, 384, 508, doi: [`10.1086/170893`](http://doi.org/10.1086/170893)

(ref: San24) Santos, J. C., van Gelder, M. L., Nazari, P., Ahmadi, A., & van Dishoeck, E. F. 2024, A&A, 689, A248, doi: [`10.1051/0004-6361/202450736`](http://doi.org/10.1051/0004-6361/202450736)

(ref: Sea09) Seale, J. P., Looney, L. W., Chu, Y., et al. 2009, ApJ, 699, 150, doi: [`10.1088/0004-637X/699/1/150`](http://doi.org/10.1088/0004-637X/699/1/150)

(ref: Sew18) Sewiło, M., Indebetouw, R., Charnley, S. B., et al. 2018, ApJL, 853, L19, doi: [`10.3847/2041-8213/aaa079`](http://doi.org/10.3847/2041-8213/aaa079)

(ref: Sew22a) Sewiło, M., Cordiner, M., Charnley, S. B., et al. 2022a, ApJ, 931, 102, doi: [`10.3847/1538-4357/ac4e8f`](http://doi.org/10.3847/1538-4357/ac4e8f)

(ref: Sew22b) Sewiło, M., Karska, A., Kristensen, L. E., et al. 2022b, ApJ, 933, 64, doi: [`10.3847/1538-4357/ac6de1`](http://doi.org/10.3847/1538-4357/ac6de1)

(ref: Sew25) Sewiło, M., Rocha, W. R. M., van Gelder, M., et al. 2025, ApJL, 992, L30, doi: [`10.3847/2041-8213/ae0ccd`](http://doi.org/10.3847/2041-8213/ae0ccd)

(ref: thesis) Shimonishi, T. 2012, PhD thesis, The University of Tokyo

(ref: ST16) Shimonishi, T., Dartois, E., Onaka, T., & Boulanger, F. 2016a, A&A, 585, A107, doi: [`10.1051/0004-6361/201526559`](http://doi.org/10.1051/0004-6361/201526559)

(ref: ST20) Shimonishi, T., Das, A., Sakai, N., et al. 2020, ApJ, 891, 164, doi: [`10.3847/1538-4357/ab6e6b`](http://doi.org/10.3847/1538-4357/ab6e6b)

(ref: ST21) Shimonishi, T., Izumi, N., Furuya, K., & Yasui, C. 2021, ApJ, 922, 206, doi: [`10.3847/1538-4357/ac289b`](http://doi.org/10.3847/1538-4357/ac289b)

(ref: ST) Shimonishi, T., Onaka, T., Kato, D., et al. 2008, ApJL, 686, L99, doi: [`10.1086/592948`](http://doi.org/10.1086/592948)

(ref: ST16b) Shimonishi, T., Onaka, T., Kawamura, A., & Aikawa, Y. 2016b, ApJ, 827, 72, doi: [`10.3847/0004-637X/827/1/72`](http://doi.org/10.3847/0004-637X/827/1/72)

(ref: ST23) Shimonishi, T., Tanaka, K. E. I., Zhang, Y., & Furuya, K. 2023, ApJL, 946, L41, doi: [`10.3847/2041-8213/acc031`](http://doi.org/10.3847/2041-8213/acc031)

(ref: Skr06) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163, doi: [`10.1086/498708`](http://doi.org/10.1086/498708)

(ref: Sut95) Sutton, E. C., Peng, R., Danchi, W. C., et al. 1995, ApJS, 97, 455, doi: [`10.1086/192147`](http://doi.org/10.1086/192147)

(ref: Tan14) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 149–172, doi: [`10.2458/azu_uapress_9780816531240-ch007`](http://doi.org/10.2458/azu_uapress_9780816531240-ch007)

(ref: Tok22b) Tokuda, K., Zahorecz, S., Kunitoshi, Y., et al. 2022a, ApJL, 936, L6, doi: [`10.3847/2041-8213/ac81c1`](http://doi.org/10.3847/2041-8213/ac81c1)

(ref: Tok22a) Tokuda, K., Minami, T., Fukui, Y., et al. 2022b, ApJ, 933, 20, doi: [`10.3847/1538-4357/ac6b3c`](http://doi.org/10.3847/1538-4357/ac6b3c)

(ref: Tok23) Tokuda, K., Harada, N., Tanaka, K. E. I., et al. 2023, ApJ, 955, 52, doi: [`10.3847/1538-4357/acefb7`](http://doi.org/10.3847/1538-4357/acefb7)

(ref: Tok25) Tokuda, K., Kunitoshi, Y., Zahorecz, S., et al. 2025, ApJ, 980, 269, doi: [`10.3847/1538-4357/ada5f8`](http://doi.org/10.3847/1538-4357/ada5f8)

(ref: vdM01) van der Marel, R. P., & Cioni, M.-R. L. 2001, AJ, 122, 1807, doi: [`10.1086/323099`](http://doi.org/10.1086/323099)

(ref: vanGel20) van Gelder, M. L., Kaper, L., Japelj, J., et al. 2020, A&A, 636, A54, doi: [`10.1051/0004-6361/201936361`](http://doi.org/10.1051/0004-6361/201936361)

(ref: vanGel22a) van Gelder, M. L., Nazari, P., Tabone, B., et al. 2022, A&A, 662, A67, doi: [`10.1051/0004-6361/202142769`](http://doi.org/10.1051/0004-6361/202142769)

(ref: Wan09) Wang, M., Chin, Y.-N., Henkel, C., Whiteoak, J. B., & Cunningham, M. 2009, ApJ, 690, 580, doi: [`10.1088/0004-637X/690/1/580`](http://doi.org/10.1088/0004-637X/690/1/580)

(ref: Wat07) Watanabe, N., Mouri, O., Nagaoka, A., et al. 2007, ApJ, 668, 1001, doi: [`10.1086/521421`](http://doi.org/10.1086/521421)

(ref: Wes90) Westerlund, B. E. 1990, A&ARv, 2, 29, doi: [`10.1007/BF00873541`](http://doi.org/10.1007/BF00873541)

(ref: Xu13) Xu, J.-L., & Wang, J.-J. 2013, MNRAS, 431, 2385, doi: [`10.1093/mnras/stt331`](http://doi.org/10.1093/mnras/stt331)

(ref: Yam17) Yamamoto, S. 2017, Introduction to Astrochemistry: Chemical Evolution from Interstellar Clouds to Star and Planet Formation (Springer), doi: [`10.1007/978-4-431-54171-4`](http://doi.org/10.1007/978-4-431-54171-4)

(ref: Zer12) Zernickel, A., Schilke, P., Schmiedeke, A., et al. 2012, A&A, 546, A87, doi: [`10.1051/0004-6361/201219803`](http://doi.org/10.1051/0004-6361/201219803)

(ref: ZY07) Zinnecker, H., & Yorke, H. W. 2007, ARA&A, 45, 481, doi: [`10.1146/annurev.astro.44.051905.092549`](http://doi.org/10.1146/annurev.astro.44.051905.092549)

# Continuum and SO emission for all sources

Figure [16](#image_all) shows the intensity distributions of the 850 $\mu$m continuum and SO(8$_{8}$–7$_{7}$) line for all sources. The SO images are obtained by integrating the emission over a velocity range of $V_{\rm sys}$ $\pm$7 km s$^{-1}$, where $V_{\rm sys}$ of each source is listed in Table [1](#sourcelist).

![](fb1.pdf)

# Spectra of hot cores

Figures [17](#spec1)–[26](#spec10) show the ALMA Band 7 spectra of the hot cores and the hot core candidate observed in this survey. Table [3](#tab_intensity) summarizes the measured line parameters of the selected key transitions. The detection criterion adopted here is a 3$\sigma$ significance level combined with velocity consistency with the systemic velocities. For weak lines, two or three channels are binned to improve sensitivity.

![](fa1.pdf)

![](fa2.pdf)

![](fa3.pdf)

![](fa4.pdf)

![](fa5.pdf)

![](fa6.pdf)

![](fa7.pdf)

![](fa8.pdf)

![](fa9.pdf)

![](fa10.pdf)

+--------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
| Source |            | Integrated Intensity                                                                                                                                        | Peak Intensity      |
+:=======+:==========:+:=================:+:=====================:+:=========================:+:=====================:+:===============================:+:========:+:==============:+:========:+:========:+
| 3-9    | Continuum  | SO                | SO$_2$                | SO$_2$                    | CH$_3$OH              | CH$_3$OH                        | SiO      | H$^{13}$CO$^+$ | CO       | HCO$^+$  |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
|        | 850 $\mu$m | (8$_{8}$–7$_{7}$) | (4$_{4,0}$–4$_{3,1}$) | (19$_{1,19}$–18$_{0,18}$) | (4$_{1}$ E–3$_{0}$ E) | (16$_{1}$ A$^-$–15$_{2}$ A$^-$) | (8–7)    | (4–3)          | (3–2)    | (4–3)    |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
|        | (mJy/beam) | (K km/s)          | (K km/s)              | (K km/s)                  | (K km/s)              | (K km/s)                        | \(K\)    | \(K\)          |          |          |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh10   | 35.1       | 241.2             | 45.8                  | 93.3                      | $<$ 0.8               | $<$ 0.7                         | 19.6     | 16.4           | 77.4     | 41.3     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh09   | 67.5       | 138.8             | 12.9                  | 34.4                      | $<$ 0.7               | $<$ 0.5                         | 9.0      | 13.9           | 86.9     | 35.1     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh08   | 15.7       | 62.1              | 9.3                   | 24.5                      | 2.1?                  | $<$ 1.0                         | 6.4      | 9.6            | 72.9     | 31.0     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh07   | 25.5       | 204.2             | 34.8                  | 76.4                      | 38.6                  | 19.6                            | 40.7     | 28.1           | 69.2     | 50.6     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh06   | 24.2       | 16.9              | $<$ 0.7               | $<$ 0.6                   | $<$ 0.8               | $<$ 1.1                         | $<$ 1.1  | 7.1            | 42.1     | 18.9     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh05-1 | 10.4       | 50.2              | 9.3                   | 18.9                      | 11.0                  | 2.9                             | 6.8      | 13.8           | 47.9     | 26.4     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh05-2 | 10.9       | 143.6             | 33.1                  | 68.5                      | 6.7                   | 2.9                             | 40.8     | 22.7           | 56.2     | 30.7     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh05-3 | 3.4        | 13.4              | $<$ 0.8               | $<$ 1.0                   | $<$ 1.0               | $<$ 0.8                         | $<$ 1.0  | 2.7            | 25.6     | 11.2     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh04   | 4.3        | 15.3              | $<$ 0.8               | $<$ 0.7                   | $<$ 0.9               | $<$ 0.7                         | $<$ 0.7  | 5.5            | 53.7     | 16.5     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh03   | 9.9        | 73.3              | 16.5                  | 33.1                      | 3.6                   | 2.0                             | 8.7      | 16.6           | 55.8     | 37.2     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh02   | 4.0        | 16.0              | $<$ 1.2               | 2.6                       | $<$ 0.8               | $<$ 0.6                         | $<$1.9   | 9.4            | 29.8     | 20.0     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh01-1 | 3.4        | 17.2              | $<$ 0.7               | $<$ 0.7                   | 5.3                   | $<$ 0.7                         | $<$ 0.7  | 3.6            | 21.0     | 14.4     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lh01-2 | 2.6        | 12.9              | 1.1                   | $<$ 0.7                   | 1.1                   | $<$ 0.7                         | 0.7?     | 8.7            | 45.4     | 21.8     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm10   | 12.0       | 90.3              | 12.7                  | 26.1                      | 16.1                  | 6.5                             | 7.5      | 9.0            | 51.0     | 26.8     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm09   | 3.7        | 11.5              | $<$ 0.7               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | 6.1            | 40.5     | 15.0     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm08   | 4.1        | 12.7              | 1.2                   | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | 5.4            | 48.7     | 16.5     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm07   | 6.7        | 18.0              | 1.8                   | 3.0                       | $<$ 0.8               | $<$ 0.6                         | $<$ 1.0  | 17.9           | 52.9     | 24.4     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm06   | 2.9        | 9.3               | $<$ 1.2               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | 3.6            | 21.1     | 12.4     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm05-1 | 2.0        | 1.5               | $<$ 0.7               | $<$ 1.1                   | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | $<$ 0.6        | 30.0     | 5.9      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm05-2 | 1.4        | 4.4               | $<$ 0.3               | $<$ 1.1                   | $<$ 1.3               | $<$ 1.6                         | $<$ 0.6  | $<$ 1.1        | 46.3     | 8.4      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm04   | 2.6        | 10.8              | $<$ 0.7               | $<$ 0.7                   | 4.8                   | $<$ 0.7                         | $<$ 0.7  | 2.6            | 31.9     | 8.9      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm03   | 0.6        | $<$ 0.6           | $<$ 0.8               | $<$ 0.7                   | $<$ 0.9               | $<$ 0.7                         | $<$ 0.7  | 1.5            | 42.3     | 5.2      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm02   | 1.6        | 3.5               | $<$ 0.7               | $<$ 0.6                   | 2.2                   | $<$ 0.6                         | $<$ 0.6  | 2.7            | 20.0     | 9.8      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Lm01   | 2.2        | 2.3               | $<$ 0.5               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 1.4  | $<$ 0.6        | 34.1     | 6.0      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll10   | 4.7        | 31.1              | 3.8                   | 12.5                      | 4.0                   | 3.1                             | 8.0      | 7.7            | 42.3     | 22.2     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll09   | 2.0        | 7.6               | $<$ 2.0               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | $<$ 1.1        | 22.3     | 10.1     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll08   | 1.8        | 8.6               | $<$ 0.7               | 2.8                       | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | 2.8            | 23.4     | 9.5      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll07-1 | 0.7        | $<$ 0.6           | $<$ 0.7               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 1.4  | $<$ 0.6        | 14.4     | 5.5      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll07-2 | 0.8        | $<$ 0.7           | $<$ 0.7               | $<$ 0.6                   | $<$ 1.3               | $<$ 0.6                         | $<$ 0.6  | $<$ 0.6        | 17.8     | 5.4      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll06   | 0.6        | $<$ 0.6           | $<$ 0.7               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 0.3  | $<$ 0.2        | 32.8     | 3.3      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll05   | 2.0        | 12.2              | $<$ 0.7               | 2.6                       | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | 4.5            | 26.6     | 10.6     |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll04-1 | 0.4        | $<$ 0.6           | $<$ 0.7               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.7                         | $<$ 0.6  | $<$ 0.6        | 39.5     | 4.0      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll04-2 | 0.9        | $<$ 1.4           | $<$ 0.9               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 1.4  | $<$ 0.6        | 32.0     | 6.8      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll03   | 0.8        | 4.6               | $<$ 0.6               | $<$ 0.6                   | $<$ 0.8               | 1.1?                            | $<$ 0.6  | $<$ 0.6        | 18.7     | 5.7      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll02   | 0.2?       | $<$ 0.6           | $<$ 0.6               | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | $<$ 0.6        | 29.0     | 3.0      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Ll01   | 1.2        | 5.9               | $<$1.8                | $<$ 0.6                   | $<$ 0.8               | $<$ 0.6                         | $<$ 0.6  | 3.4            | 23.7     | 9.2      |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+
| Error  | ...        | $\pm$1.4          | $\pm$1.2              | $\pm$1.1                  | $\pm$1.1              | $\pm$0.9                        | $\pm$1.3 | $\pm$1.1       | $\pm$0.3 | $\pm$0.4 |
+--------+------------+-------------------+-----------------------+---------------------------+-----------------------+---------------------------------+----------+----------------+----------+----------+

: Continuum and Line intensities

Table notes: The last row indicates the typical error. “?” indicates tentative detection.

# Derived column densities and fractional abundances

Table [4](#tab_n) summarizes derived column densities and rotational temperatures for the hot cores and the hot core candidate observed in this survey.

|  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|
| Object | Molecule | $T_{\mathrm{rot}}$ | $N$(X) | $N$(X)/$N_{\mathrm{H_2}}$ | Note |
|  |  | \(K\) | (cm$^{-2}$) |  |  |
| Lh10 | H$_2$ | 172 | (7.9 $\pm$ 2.4 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 172 | $<$7 $\times$ 10$^{14}$ | $<$9 $\times$ 10$^{-10}$ | \(2\) |
|  | SO$_2$ (high-$T$) | 172$^{+2}_{-2}$ | (7.8 $\pm$ 0.1 ) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ (low-$T$) | 22$^{+1}_{-1}$ | (4.9 $\pm$ 0.9) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ ($^{34}$S, high-$T$) | ... | (1.3 $\pm$ 0.3 ) $\times$ 10$^{16}$ | (1.6 $\pm$ 0.6 ) $\times$ 10$^{-8 }$ | \(4\) |
|  | $^{34}$SO$_2$ (high-$T$) | 138$^{+30}_{-21}$ | (8.6 $\pm$ 2.0 ) $\times$ 10$^{14}$ | (1.1 $\pm$ 0.4 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | $^{34}$SO$_2$ (low-$T$) | $\sim$40 | $\sim$6 $\times$ 10$^{14}$ | ... | \(3\) |
|  | SO | 172 | (5.0 $\pm$ 0.1 ) $\times$ 10$^{15}$ | (6.3 $\pm$ 1.9 ) $\times$ 10$^{-9 }$ | \(2\) |
|  | SO$^+$ | 172 | (7.7 $\pm$ 0.4 ) $\times$ 10$^{14}$ | (9.7 $\pm$ 3.0 ) $\times$ 10$^{-10}$ | \(2\) |
|  | SiO | 172 | (3.1 $\pm$ 1.0 ) $\times$ 10$^{13}$ | (3.9 $\pm$ 1.7 ) $\times$ 10$^{-11}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (3.5 $\pm$ 0.4 ) $\times$ 10$^{14}$ | (4.4 $\pm$ 1.4 ) $\times$ 10$^{-10}$ | \(6\) |
|  |  |  |  |  |  |
| Lh09 | H$_2$ | ... | (8.0 $\pm$ 4.0 ) $\times$ 10$^{23}$ | ... | \(7\) |
|  | CH$_3$OH | 113 | $<$3 $\times$ 10$^{14}$ | $<$4 $\times$ 10$^{-10}$ | \(2\) |
|  | SO$_2$ (high-$T$) | 113$^{+3}_{-3}$ | (2.4 $\pm$ 0.1 ) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ (low-$T$) | 18$^{+3}_{-2}$ | $\sim$1 $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ ($^{34}$S, high-$T$) | ... | (3.2 $\pm$ 1.5 ) $\times$ 10$^{15}$ | (4.0 $\pm$ 2.7 ) $\times$ 10$^{-9 }$ | \(4\) |
|  | $^{34}$SO$_2$ (high-$T$) | 86$^{+37}_{-20}$ | (2.1 $\pm$ 1.0 ) $\times$ 10$^{14}$ | (2.6 $\pm$ 1.8 ) $\times$ 10$^{-10}$ | \(3\) |
|  | $^{34}$SO$_2$ (low-$T$) | $\sim$30 | $\sim$2 $\times$ 10$^{14}$ | ... | \(3\) |
|  | SO | 113 | (2.4 $\pm$ 0.1 ) $\times$ 10$^{15}$ | (3.0 $\pm$ 1.5 ) $\times$ 10$^{-9 }$ | \(2\) |
|  | SO$^+$ | 113 | (2.3 $\pm$ 0.2 ) $\times$ 10$^{14}$ | (2.9 $\pm$ 1.5 ) $\times$ 10$^{-10}$ | \(2\) |
|  | SiO | 113 | (1.2 $\pm$ 0.3 ) $\times$ 10$^{13}$ | (1.5 $\pm$ 0.8 ) $\times$ 10$^{-11}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (3.0 $\pm$ 0.3 ) $\times$ 10$^{14}$ | (3.8 $\pm$ 1.9 ) $\times$ 10$^{-10}$ | \(6\) |
|  |  |  |  |  |  |
| Lh08 | H$_2$ | 123 | (5.0 $\pm$ 1.5 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 123 | $<$2 $\times$ 10$^{15}$ | $<$4 $\times$ 10$^{-9 }$ | \(2\) |
|  | SO$_2$ (high-$T$) | 123$^{+18}_{-14}$ | (1.6 $\pm$ 0.3 ) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ (low-$T$) | 18$^{+4}_{-3}$ | $\sim$8 $\times$ 10$^{14}$ | ... | \(3\) |
|  | SO$_2$ ($^{34}$S, high-$T$) | ... | (3.8 $\pm$ 2.3 ) $\times$ 10$^{15}$ | (7.6 $\pm$ 5.1 ) $\times$ 10$^{-9 }$ | \(4\) |
|  | $^{34}$SO$_2$ (high-$T$) | 108$^{+81}_{-32}$ | (2.5 $\pm$ 1.5 ) $\times$ 10$^{14}$ | (5.0 $\pm$ 3.4 ) $\times$ 10$^{-10}$ | \(3\) |
|  | $^{34}$SO$_2$ (low-$T$) | $\sim$20 | $\sim$1 $\times$ 10$^{14}$ | ... | \(3\) |
|  | SO | 123 | (1.1 $\pm$ 0.1 ) $\times$ 10$^{15}$ | (2.2 $\pm$ 0.7 ) $\times$ 10$^{-9 }$ | \(2\) |
|  | SO$^+$ | 123 | $<$3 $\times$ 10$^{13}$ | $<$5 $\times$ 10$^{-11}$ | \(2\) |
|  | SiO | 123 | (8.7 $\pm$ 3.4 ) $\times$ 10$^{12}$ | (1.7 $\pm$ 0.9 ) $\times$ 10$^{-11}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (2.1 $\pm$ 0.4 ) $\times$ 10$^{14}$ | (4.2 $\pm$ 1.5 ) $\times$ 10$^{-10}$ | \(6\) |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
| Lh07 | H$_2$ | 259 | (3.7 $\pm$ 1.1 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 155$^{+4}_{-4}$ | (3.4 $\pm$ 0.1 ) $\times$ 10$^{16}$ | ... | \(3\) |
|  | CH$_3$OH ($^{13}$C) | ... | (4.9 $\pm$ 1.8 ) $\times$ 10$^{16}$ | (1.3 $\pm$ 0.6 ) $\times$ 10$^{-7 }$ | \(8\) |
|  | $^{13}$CH$_3$OH | 155 | (1.0 $\pm$ 0.2 ) $\times$ 10$^{15}$ | (2.7 $\pm$ 1.0 ) $\times$ 10$^{-9 }$ | \(9\) |
|  | SO$_2$ (high-$T$) | 363$^{+10}_{-10}$ | (1.2 $\pm$ 0.1 ) $\times$ 10$^{16}$ | ... | \(3\) |
|  | SO$_2$ (low-$T$) | 27$^{+1}_{-1}$ | (3.9 $\pm$ 0.5) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ ($^{34}$S, high-$T$) | ... | (1.7 $\pm$ 0.2 ) $\times$ 10$^{16}$ | (4.6 $\pm$ 1.5 ) $\times$ 10$^{-8 }$ | \(4\) |
|  | $^{34}$SO$_2$ (high-$T$) | 145$^{+6}_{-5}$ | (1.1 $\pm$ 0.1 ) $\times$ 10$^{15}$ | (3.0 $\pm$ 0.9 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | SO | 363 | (7.0 $\pm$ 0.2 ) $\times$ 10$^{15}$ | (1.9 $\pm$ 0.6 ) $\times$ 10$^{-8 }$ | \(2\) |
|  | SO$^+$ | 363 | (3.1 $\pm$ 0.7 ) $\times$ 10$^{14}$ | (8.4 $\pm$ 3.1 ) $\times$ 10$^{-10}$ | \(2\) |
|  | SiO | 259 | (8.5 $\pm$ 3.3 ) $\times$ 10$^{13}$ | (2.3 $\pm$ 1.1 ) $\times$ 10$^{-10}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (6.0 $\pm$ 0.4 ) $\times$ 10$^{14}$ | (1.6 $\pm$ 0.5 ) $\times$ 10$^{-9 }$ | \(6\) |
|  | CH$_3$OCH$_3$ | 97$^{+13}_{-10}$ | (2.6 $\pm$ 0.3 ) $\times$ 10$^{15}$ | (7.0 $\pm$ 2.2 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | HCOOCH$_3$ | 114$^{+30}_{-20}$ | (2.9 $\pm$ 1.6 ) $\times$ 10$^{15}$ | (7.8 $\pm$ 4.9 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | C$_2$H$_5$OH | 83$^{+25}_{-16}$ | (2.0 $\pm$ 1.3 ) $\times$ 10$^{15}$ | (5.4 $\pm$ 3.9 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | *trans*-HCOOH | 141$^{+41}_{-26}$ | (6.9 $\pm$ 2.0 ) $\times$ 10$^{14}$ | (1.9 $\pm$ 0.8 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | HC$_3$N | 155 | (6.8 $\pm$ 0.6 ) $\times$ 10$^{13}$ | (1.8 $\pm$ 0.6 ) $\times$ 10$^{-10}$ | \(9\) |
|  | H$_2$CCO | 155 | (2.2 $\pm$ 0.5 ) $\times$ 10$^{14}$ | (5.9 $\pm$ 2.2 ) $\times$ 10$^{-10}$ | \(9\) |
|  | CH$_3$CHO | 155 | $<$2 $\times$ 10$^{14}$ | $<$5 $\times$ 10$^{-10 }$ | \(9\) |
|  |  |  |  |  |  |
| Lh05-1 | H$_2$ | 146 | (2.7 $\pm$ 0.8 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 121$^{+15}_{-13}$ | (6.1 $\pm$ 1.7 ) $\times$ 10$^{15}$ | (2.3 $\pm$ 0.9 ) $\times$ 10$^{-8 }$ | \(3\) |
|  | SO$_2$ (high-$T$) | 170$^{+15}_{-13}$ | (1.6 $\pm$ 0.2 ) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ (low-$T$) | 23$^{+5}_{-3}$ | $\sim$1 $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ ($^{34}$S, high-$T$) | ... | (3.5 $\pm$ 1.1 ) $\times$ 10$^{15}$ | (1.3 $\pm$ 0.6 ) $\times$ 10$^{-8 }$ | \(4\) |
|  | $^{34}$SO$_2$ (high-$T$) | 174$^{+70}_{-39}$ | (2.3 $\pm$ 0.7 ) $\times$ 10$^{14}$ | (8.5 $\pm$ 3.6 ) $\times$ 10$^{-10}$ | \(3\) |
|  | SO | 170 | (1.0 $\pm$ 0.1 ) $\times$ 10$^{15}$ | (3.7 $\pm$ 1.2 ) $\times$ 10$^{-9 }$ | \(2\) |
|  | SO$^+$ | 170 | $<$2 $\times$ 10$^{13}$ | $<$7 $\times$ 10$^{-11}$ | \(2\) |
|  | SiO | 146 | (3.0 $\pm$ 0.3 ) $\times$ 10$^{13}$ | (1.1 $\pm$ 0.3 ) $\times$ 10$^{-10}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (3.0 $\pm$ 0.3 ) $\times$ 10$^{14}$ | (1.1 $\pm$ 0.3 ) $\times$ 10$^{-9 }$ | \(6\) |
|  | *trans*-HCOOH | 121 | (2.5 $\pm$ 1.1 ) $\times$ 10$^{14}$ | (9.3 $\pm$ 4.9 ) $\times$ 10$^{-10}$ | \(9\) |
|  |  |  |  |  |  |
| Lh05-2 | H$_2$ | 148 | (2.8 $\pm$ 0.8 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 149$^{+36}_{-24}$ | (4.3 $\pm$ 1.2 ) $\times$ 10$^{15}$ | (1.5 $\pm$ 0.6 ) $\times$ 10$^{-8 }$ | \(3\) |
|  | SO$_2$ (high-$T$) | 148$^{+5}_{-5}$ | (4.9 $\pm$ 0.3 ) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ (low-$T$) | 21$^{+2}_{-1}$ | (3.4 $\pm$ 1.2) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ ($^{34}$S, high-$T$) | ... | (4.9 $\pm$ 0.3 ) $\times$ 10$^{15}$ | (1.7 $\pm$ 0.5 ) $\times$ 10$^{-8 }$ | \(4\) |
|  | $^{34}$SO$_2$ (high-$T$) | 134$^{+78}_{-36}$ | (3.2 $\pm$ 1.5 ) $\times$ 10$^{14}$ | (1.1 $\pm$ 0.6 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | SO | 148 | (2.8 $\pm$ 0.1 ) $\times$ 10$^{15}$ | (1.0 $\pm$ 0.3 ) $\times$ 10$^{-9 }$ | \(2\) |
|  | SO$^+$ | 148 | (1.2 $\pm$ 0.3 ) $\times$ 10$^{14}$ | (4.3 $\pm$ 1.6 ) $\times$ 10$^{-10}$ | \(2\) |
|  | SiO | 148 | (6.0 $\pm$ 1.6 ) $\times$ 10$^{13}$ | (2.1 $\pm$ 0.8 ) $\times$ 10$^{-10}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (4.9 $\pm$ 0.4 ) $\times$ 10$^{14}$ | (1.8 $\pm$ 0.5 ) $\times$ 10$^{-9 }$ | \(6\) |
|  | *trans*-HCOOH | 149 | $<$8 $\times$ 10$^{13}$ | $<$3 $\times$ 10$^{-10}$ | \(9\) |
|  |  |  |  |  |  |
| Lh03 | H$_2$ | 246 | (1.5 $\pm$ 0.5 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 185$^{+61}_{-37}$ | (4.0 $\pm$ 1.6 ) $\times$ 10$^{15}$ | (2.7 $\pm$ 1.4 ) $\times$ 10$^{-8 }$ | \(3\) |
|  | SO$_2$ (high-$T$) | 306$^{+12}_{-1}$ | (4.7 $\pm$ 0.2 ) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ (low-$T$) | 31$^{+2}_{-2}$ | (1.6 $\pm$ 0.3) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO$_2$ ($^{34}$S, high-$T$) | ... | (6.5 $\pm$ 3.1 ) $\times$ 10$^{15}$ | (4.3 $\pm$ 2.5 ) $\times$ 10$^{-8 }$ | \(4\) |
|  | $^{34}$SO$_2$ (high-$T$) | 245$^{+90}_{-52}$ | (4.3 $\pm$ 1.2 ) $\times$ 10$^{14}$ | (2.9 $\pm$ 1.2 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | $^{34}$SO$_2$ (low-$T$) | $\sim$45 | $\sim$2 $\times$ 10$^{14}$ | ... | \(3\) |
|  | SO | 306 | (2.1 $\pm$ 0.1 ) $\times$ 10$^{15}$ | (1.4 $\pm$ 0.5 ) $\times$ 10$^{-8 }$ | \(2\) |
|  | SO$^+$ | 306 | (2.6 $\pm$ 0.6 ) $\times$ 10$^{14}$ | (1.7 $\pm$ 0.7 ) $\times$ 10$^{-9 }$ | \(2\) |
|  | SiO | 246 | (1.8 $\pm$ 0.8 ) $\times$ 10$^{13}$ | (1.2 $\pm$ 0.7 ) $\times$ 10$^{-10}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (3.6 $\pm$ 0.3 ) $\times$ 10$^{14}$ | (2.4 $\pm$ 0.8 ) $\times$ 10$^{-9 }$ | \(6\) |
|  |  |  |  |  |  |
| Lm10 | H$_2$ | 182 | (2.4 $\pm$ 0.7 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 169$^{+15}_{-13}$ | (1.6 $\pm$ 0.3 ) $\times$ 10$^{16}$ | (6.7 $\pm$ 2.3 ) $\times$ 10$^{-8 }$ | \(3\) |
|  | SO$_2$ (high-$T$) | 192$^{+16}_{-14}$ | (2.2 $\pm$ 0.2 ) $\times$ 10$^{15}$ | (9.2 $\pm$ 2.8 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | SO$_2$ (low-$T$) | 26$^{+2}_{-2}$ | (1.2 $\pm$ 0.4) $\times$ 10$^{15}$ | ... | \(3\) |
|  | SO | 192 | (2.0 $\pm$ 0.1 ) $\times$ 10$^{15}$ | (8.3 $\pm$ 2.5 ) $\times$ 10$^{-9 }$ | \(2\) |
|  | SO$^+$ | 192 | (1.2 $\pm$ 0.4 ) $\times$ 10$^{14}$ | (5.0 $\pm$ 2.2 ) $\times$ 10$^{-10}$ | \(2\) |
|  | SiO | 182 | (1.3 $\pm$ 0.5 ) $\times$ 10$^{13}$ | (5.4 $\pm$ 2.6 ) $\times$ 10$^{-11}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (1.9 $\pm$ 0.3 ) $\times$ 10$^{14}$ | (7.9 $\pm$ 2.6 ) $\times$ 10$^{-10}$ | \(6\) |
|  | CH$_3$OCH$_3$ | 83$^{+30}_{-17}$ | (8.0 $\pm$ 2.4 ) $\times$ 10$^{14}$ | (3.3 $\pm$ 1.4 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | *trans*-HCOOH | 169 | (4.1 $\pm$ 1.3 ) $\times$ 10$^{14}$ | (1.7 $\pm$ 0.7 ) $\times$ 10$^{-9 }$ | \(9\) |
|  | HCOOCH$_3$ | 169 | $<$2 $\times$ 10$^{15}$ | $<$8 $\times$ 10$^{-9 }$ | \(3\) |
|  | C$_2$H$_5$OH | 169 | $<$7 $\times$ 10$^{14}$ | $<$3 $\times$ 10$^{-9 }$ | \(9\) |
|  | CH$_3$CHO | 169 | $<$2 $\times$ 10$^{14}$ | $<$8 $\times$ 10$^{-10}$ | \(9\) |
|  |  |  |  |  |  |
| Lm07 | H$_2$ | 78 | (3.5 $\pm$ 1.1 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 78 | $<$2 $\times$ 10$^{14}$ | $<$7 $\times$ 10$^{-10}$ | \(2\) |
|  | SO$_2$ | 78$^{+13}_{-10}$ | (3.1 $\pm$ 0.1 ) $\times$ 10$^{14}$ | (8.9 $\pm$ 2.8 ) $\times$ 10$^{-10}$ | \(3\) |
|  | SO | 78 | (3.0 $\pm$ 0.2 ) $\times$ 10$^{14}$ | (8.6 $\pm$ 2.8 ) $\times$ 10$^{-10}$ | \(2\) |
|  | SO$^+$ | 78 | $<$2 $\times$ 10$^{14}$ | $<$4 $\times$ 10$^{-10}$ | \(2\) |
|  | SiO | 78 | $<$2 $\times$ 10$^{12}$ | $<$5 $\times$ 10$^{-12}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (3.8 $\pm$ 0.3 ) $\times$ 10$^{14}$ | (1.1 $\pm$ 0.4 ) $\times$ 10$^{-9}$ | \(6\) |
|  |  |  |  |  |  |
| Ll10 | H$_2$ | 143 | (1.2 $\pm$ 0.4 ) $\times$ 10$^{23}$ | ... | \(1\) |
|  | CH$_3$OH | 200$^{+130}_{-57}$ | (4.7 $\pm$ 2.0 ) $\times$ 10$^{15}$ | (3.6 $\pm$ 1.9 ) $\times$ 10$^{-8 }$ | \(3\) |
|  | SO$_2$ (high-$T$) | 87$^{+8}_{-7}$ | (7.5 $\pm$ 1.1 ) $\times$ 10$^{14}$ | (5.8 $\pm$ 2.0 ) $\times$ 10$^{-9 }$ | \(3\) |
|  | SO$_2$ (low-$T$) | 36$^{+15}_{-8}$ | $\sim$2 $\times$ 10$^{14}$ | ... | \(3\) |
|  | SO | 87 | (5.2 $\pm$ 0.3 ) $\times$ 10$^{14}$ | (4.0 $\pm$ 1.3 ) $\times$ 10$^{-9 }$ | \(2\) |
|  | SO$^+$ | 87 | $<$2 $\times$ 10$^{13}$ | $<$2 $\times$ 10$^{-10}$ | \(2\) |
|  | SiO | 143 | (1.2 $\pm$ 0.5 ) $\times$ 10$^{13}$ | (9.2 $\pm$ 4.8 ) $\times$ 10$^{-11}$ | \(5\) |
|  | HCO$^+$ | 30–60 | (1.6 $\pm$ 0.3 ) $\times$ 10$^{14}$ | (1.2 $\pm$ 0.4 ) $\times$ 10$^{-9 }$ | \(6\) |

: Estimated rotation temperatures, column densities, and fractional abundances

Table notes: Uncertainties and upper limits are of 2$\sigma$ level and do not include systematic errors due to adopted spectroscopic constants. See Section [4](#sec_ana) for more details. (1) $N_{\mathrm{H_2}}$ is derived from dust continuum. The dust temperature is assumed to be equal to the rotational temperature of SO$_2$ or CH$_3$OH, or the average of the two if both are available. A 30$\%$ uncertainty is assumed for $N_{\mathrm{H_2}}$. (2) $T_{\mathrm{rot}}$ is assumed to be the same as that of the high-temperature component of SO$_2$. (3) Based on the rotation diagram. (4) Estimated from $^{34}$SO$_2$ assuming $^{32}$S/$^{34}$S = 15. (5) A 50$\%$ uncertainty is assumed for the adopted $T_{\mathrm{rot}}$. (6) Estimated from H$^{13}$CO$^+$ assuming the adopted $T_{\mathrm{rot}}$. (7) See Section [4](#sec_ana) for the derivation of $N_{\mathrm{H_2}}$ for Lh09. (8) Estimated from $^{13}$CH$_3$OH assuming $^{12}$C/$^{13}$C = 49. (9) $T_{\mathrm{rot}}$ is assumed to be the same as that of CH$_3$OH.

[^1]: https://www.astro.uni-koeln.de/cdms

[^2]: http://spec.jpl.nasa.gov

</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[4].what.evidence[1]",
  "value": "SMC, extreme outer Galaxy, and Galactic hot core molecular abundances for cross-metallicity comparison",
  "failed_quote": "For comparison, we include Galactic hot core data: CH$_3$OH values are taken from 28 hot cores reported by (cite: Bae22), while SO$_2$ values are taken from 10 hot cores reported by (cite: Sut95; Mac96; Hel97; Hat98b; Qin10; Xu13), and their median abundances are plotted in the figure."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[1]",
  "value": "Optical depth effects, shock conditions, and evolutionary stage differences were considered and rejected as the primary explanations for the order-of-magnitude CH3OH abundance variations.",
  "failed_quote": "Shock conditions appear to have a minor influence, as clear correlation is not observed between line width and line intensity, especially for CH$_3$OH and SO$_2$ (see Section 5.3.2)."
 }
]
```
