# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019A%26A...632A..83S\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Probing fragmentation and velocity sub-structure in the massive NGC 6334 filament with ALMA

*Herschel* imaging surveys of galactic interstellar clouds support a paradigm for low-mass star formation in which dense molecular filaments play a crucial role. The detailed fragmentation properties of star-forming filaments remain poorly understood, however, and the validity of the filament paradigm in the intermediate- to high-mass regime is still unclear.

Here, following up on an earlier 350 $\mu$m dust continuum study with the ArT$\acute{\rm e}$MiS camera on the APEX telescope, we investigate the detailed density and velocity structure of the main filament in the high-mass star-forming region NGC 6334.

We conducted ALMA Band 3 observations in the 3.1 mm continuum and of the N$_2$H$^+$(1-0), HC$_5$N(36-35), HNC(1-0), HC$_3$N(10-9), CH$_3$CCH(6-5), and H$_2$CS(3-2) lines at an angular resolution of $\sim$3$\ensuremath{''}$, corresponding to 0.025 pc at a distance of 1.7 kpc.

The NGC 6334 filament was detected in both the 3.1 mm continuum and the N$_2$H$^+$, HC$_3$N, HC$_5$N, CH$_3$CCH, and H$_2$CS lines with ALMA.

We identified twenty-six compact ($< 0.03\,$pc) dense cores at 3.1 mm and five velocity-coherent fiber-like features in N$_2$H$^+$ within the main filament. The typical length ($\sim \,$0.5 pc) of, and velocity difference ($\sim \,$0.8 km s$^{-1}$) between, the fiber-like features of the NGC 6334 filament are reminiscent of the properties for the fibers of the low-mass star-forming filament B211/B213 in the Taurus cloud. Only two or three of the five velocity-coherent features are well aligned with the NGC 6334 filament and may represent genuine, fiber sub-structures; the other two features may trace accretion flows onto the main filament. The mass distribution of the ALMA 3.1 mm continuum cores has a peak at $\sim 10\, M_\odot$, which is an order of magnitude higher than the peak of the prestellar core mass function in nearby, low-mass star-forming clouds. The cores can be divided into seven groups, closely associated with dense clumps seen in the ArT$\acute{\rm e}$MiS 350 $\mu$m data. The projected separation between ALMA dense cores (0.03–0.1 pc) and the projected spacing between ArT$\acute{\rm e}$MiS clumps (0.2–0.3 pc) are roughly consistent with the effective Jeans length ($0.08\pm0.03\,$pc) in the filament and a physical scale of about four times the filament width, respectively, if the inclination angle of the filament to line of sight is $\sim 30^\circ$. These two distinct separation scales are suggestive of a bimodal fragmentation process in the filament.

Despite being one order of magnitude denser and more massive than the Taurus B211/B213 filament, the NGC 6334 filament has a density and velocity structure that is qualitatively very similar. The main difference is that the dense cores embedded in the NGC 6334 filament appear to be an order of magnitude denser and more massive than the cores in the Taurus filament. This suggests that dense molecular filaments may evolve and fragment in a similar manner in low- and high-mass star-forming regions, and that the filament paradigm may hold in the intermediate-mass (if not high-mass) star formation regime.

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
|  | Rest freq. | $\theta_{\rm beam}$(PA) | rms | dV |
|  | GHz | $\ensuremath{''} \times \ensuremath{''}$ ($^{\circ}$) | mJy/beam | km/s |
| 3.1 mm continuum (12m+7m) | ————– | 2.99 $\times$ 1.97 (82.6) | 0.2 | —- |
| 3.1 mm continuum (12m) | ————– | 2.80 $\times$ 1.84 (83.4) | 0.14 | —- |
| HNC (1–0,$E_{\rm u}$=4.35 K) | 90.663572 | 3.82 $\times$ 2.48 (85.9) | 0.3 | 60 |
| HC$_3$N (10–9,$E_{\rm u}$=24.015 K) | 90.978989 | 3.81 $\times$ 2.47 (85.9) | 0.27 | 60 |
| N$_2$H$^+$ (1–0,$E_{\rm u}$=4.472 K) | 93.176265 | 3.78 $\times$ 2.40 (84.1) | 4.4 | 0.2 |
| HC$_5$N (36–35,$E_{\rm u}$=80.504 K) | 93.188126 | 3.77 $\times$ 2.39 (84.1) | 5.4 | 0.2 |
| CH$_3$CCH (6$_0$–5$_0$,$E_{\rm u}$=17.225 K) | 102.54798 | 3.75 $\times$ 2.36 (79.1) | 0.36 | 60 |
| H$_2$CS (3$_{1,2}$-2$_{1,1}$,$E_{\rm u}$=23.213 K) | 104.61699 | 3.40 $\times$ 2.17 (84.3) | 0.22 | 60 |

# Introduction

*Herschel* imaging observations of galactic molecular clouds reveal an omnipresence of filamentary structures and suggest that filaments dominate the mass budget of the dense molecular gas where stars form (cite: Andre10; Molinari10; Hill11; Schisano14; Konyves15). At least in the nearby clouds of the Gould Belt, detailed studies of the radial column density profiles have found a common inner filament width of $\sim 0.1\,$pc, with a dispersion of a factor $\ensuremath{\lesssim} 2$, when averaged over the filament crests (cite: Arzoumanian11; Arzoumanian18; Palmeirim13; Koch15). Furthermore, most of the prestellar cores identified with *Herschel* are found to be embedded within such filamentary structures, showing that dense molecular filaments are the main sites of solar-type star formation (cite: Konyves15; Konyves19; Marsh16). Overall, the *Herschel* findings in nearby clouds support a filament paradigm for solar-type star formation in two main steps (cf. (cite: Andre14), (cite: Andre17); (cite: Inutsuka15)): first, multiple large-scale compressions of interstellar material in supersonic flows generate a pervasive web of $\sim$0.1-pc wide filaments in the cold interstellar medium (ISM); second, the densest filaments fragment into prestellar cores by gravitational instability near or above the critical mass per unit length of nearly isothermal gas cylinders, $M_{\rm line, crit} = 2\, c_{\rm s}^2/G \sim 16\, M_\odot$/pc, where $c_{\rm s} \sim 0.2$ km s$^{-1}$ is the isothermal sound speed for molecular gas at $T \sim 10$ K.

Since molecular filaments are also known to be present in other galaxies (cite: Fukui15), this paradigm may potentially have implications for star formation on galaxy-wide scales. The star formation efficiency in dense molecular gas is indeed observed to be remarkably uniform over a wide range of scales from pc-scale filaments and clumps to entire galactic disks (cite: Gao04; Lada10; Lada12; Shimajiri17; Zhang19), with possible deviations in extreme environments, such as the central molecular zone (cite: Longmore13). Assuming that all star-forming filaments have similar inner widths, as seems to be the case in nearby clouds (cite: Arzoumanian18), it is argued that the microphysics of filament fragmentation into prestellar cores may ultimately be responsible for this quasi-universal star formation efficiency (cite: Andre14; Shimajiri17).

The validity and details of the two-step filament paradigm remain controversial, however, especially beyond the Gould Belt and in high-mass star-forming clouds. In particular, an alternative scenario is proposed based on the notion of global hierarchical cloud collapse (cite: Vazquez19), which is especially attractive in the case of high-mass star formation to account for the structure of strongly self-gravitating hub-filament systems, where a massive cluster-forming hub is observed at the center of a converging network of filaments (cite: Myers09; Peretto13). In this alternative scenario, most if not all filaments would be generated by gravitational effects, as opposed to large-scale compression, and would represent accretion flows onto dense hubs.

The evolution and detailed fragmentation manner of star-forming filaments are also poorly understood. In particular, the mere existence of massive, $\sim$0.1-pc wide, filaments with masses per unit length $M_{\rm line}$ that exceed the critical line mass[^1] of an isothermal filament $M_{\rm line, crit}$ by one to two orders of magnitude is a paradox. Indeed, such filaments may be expected to undergo rapid radial contraction into spindles before any fragmentation into prestellar cores (cite: Inutsuka97). A possible solution for this paradox is that massive filaments accrete background cloud material while evolving (cite: Palmeirim13; Shimajiri18), and that this accretion process drives magneto-hydrodynamic (MHD) waves, generating sub-structure within dense filaments, and leading to a dynamical equilibrium (cite: Hennebelle13), where $M_{\rm line}$ approaches the virial mass per unit length $M_{\rm line, vir} = 2\, \sigma _{\rm 1D}^2/G$ (cite: Fiege00). The detection through molecular line observations of velocity-coherent fiber-like sub-structure within several nearby supercritical filaments (cite: Hacar13; Hacar18) may possibly be the manifestation of such a process.

The physical origin of observed fibers is nevertheless still under debate (cite: Tafalla15; Smith14; Clarke17; Clarke18), and

it is not yet clear whether dense molecular filaments in massive star-forming regions have similar characteristics to those observed in nearby clouds. Our recent APEX/ArT$\acute{\rm e}$MiS 350 $\mu$m study of the massive star-forming complex NGC 6334 showed that the main filament of the complex has an observed line mass of $\sim$1000 $M_{\odot}$/pc, consistent within uncertainties with the estimated virial mass per unit length $\sim$500 $M_{\odot}$/pc, and an inner width $\sim 0.15\pm 0.05\,$pc all along its length (cite: Andre16), within $\sim$$50\%$

of the typical inner filament width observed with *Herschel* in nearby clouds (cite: Arzoumanian18). NGC 6334 is a very active star-forming region at a distance $d \sim 1.7\,$kpc, which contains 150 OB stars and more than 2000 young stellar objects (cite: Persi08; Russeil13; Willis13; Tige17), for a total gas mass of $\sim$2.2$\times$10$^5$ $M_{\odot}$. Here, thanks to the high angular resolution and sensitivity of Atacama Large Millimeter Array (ALMA) data at 3 mm, we investigate the density and velocity sub-structure of the massive NGC 6334 filament and compare the results with those obtained for nearby, lower-mass star-forming filaments.

The paper is organized as follows. In Sect. [2](#ALMA_obs), we describe our ALMA observations of NGC 6334 in both the N$_2$H$^+$(1–0), HC$_3$N(10–9), HC$_5$N(36–35), CH$_3$CCH(6$_0$–5$_0$), H$_2$CS(3$_{1,2}$–2$_{1,1}$) lines and the 3.1 mm continuum. In Sect. [3](#Sect:Results), we show the spatial distributions of the detected molecular lines and continuum emission. We also analyze the velocity features observed in N$_2$H$^+$(1–0) emission and extract dense structures such as compact cores and fiber-like components. In Sect. [4](#Sect:Discussion), we discuss the evidence of a bimodal fragmentation pattern in the NGC 6334 filament, emphasize the presence of both unusually massive cores and fiber-like velocity-coherent components in the filament, and comment on the possible origin of these multiple velocity components. Our conclusions are summarized in Sect. [5](#Sect:Conclusions).

![](NGC6334_mom0s_a_12m_final.png)

# ALMA observations of the NGC 6334 filament

We carried out ALMA Cycle 3 observations in Band 3 toward NGC 6334 with both the 12m antennas (C36-2 configuration) and the Atacama Compact Array (ACA) 7m antennas, as part of project 2015.1.01404.S (PI: Ph. Andr$\acute{\rm e}$). We imaged the main filament in the NGC 6334 region using a 17-pointing mosaic with the 12m array and a 8-pointing mosaic with the ACA array. The N$_2$H$^+$(1–0) line was observed in narrow-band mode at a frequency resolution of 61.035 kHz, corresponding to $\sim\,$0.2 km s$^{-1}$. The HC$_5$N ($J$=36–35) line was included in the same narrow-band, high spectral resolution window. The 3.1 mm continuum emission was observed using three wide bands, each covering a bandwidth of 1875.0 MHz. The HNC (1–0), HC$_3$N (10–9), CH$_3$CCH (6$_0$–5$_0$), and H$_2$CS (3$_{1,2}$-2$_{1,1}$) lines were included in these wide bands and observed at a frequency resolution of 31.250 MHz, corresponding to $\sim\,$100 km s$^{-1}$. The 12m-array observations were carried out on 23, 24, 26 January 2016 with 42, 46, and 37 antennas, respectively, and projected baseline lengths ranging from 11.7 k$\lambda$ to 326.8 k$\lambda$. The ACA observations were carried out between 16 March 2016 and 8 July 2016 with 7-9 antennas and projected baseline lengths ranging from 4.5 k$\lambda$ to 48.2 k$\lambda$. In the calibration process, we made additional flagging of a few antennas that had too low gain or showed large amplitude dispersion in time. The bandpass calibration was achieved by observing the quasar J1617-5848 with the 12m array and the three quasars J1924-2914, J1517-2422, and J1427-4206 with the ACA array. The complex gain calibration was carried out using the quasar J1713-3418 with the 12m array and the quasar J1717-3342 with ACA. Absolute flux calibration was achieved by observing two solar system objects (Callisto and Titan) with the 12m array and planets (Mars and Neptune) with ACA. Calibration and data reduction were performed with the Common Astronomy Software Application (CASA) package (version 4.5.3 for 12m data calibration and imaging, version 4.6.0 for 7m data calibration). For imaging, we adopted the Briggs weighting scheme with a robust parameter of 0.5, as a good compromise between maximizing angular resolution and sensitivity to extended structures. The resulting synthesized beam sizes ($\sim$3$\ensuremath{''}$, corresponding to 0.025 pc) and rms noise levels for each line and the continuum are summarized in Table [\[table:alma_obs\]](#table:alma_obs).

With a minimum projected baseline length of 4.5 k$\lambda$, our ALMA$+$ACA observations are estimated to be sensitive to angular scales up to $\sim$37$\ensuremath{''}$ (corresponding to $\sim$0.3 pc) at the 10% level (cite: Wilner94). For comparison, we expect the transverse size of any filament sub-structures to be smaller than the $\sim$0.15 pc inner width of the NGC 6334 filament (cite: Andre16). Likewise with a minimum projected baseline of 11.7 k$\lambda$, our 12m-only observations are sensitive to angular scales up to $\sim$14$\ensuremath{''}$ (corresponding to $\sim$0.1 pc) at the 10% level. For comparison, the scales of individual dense cores are at most $\sim$0.1 pc (cite: Konyves15). Moreover, simulations of ALMA observations performed with CASA, using the same set of baselines as the real ALMA$+$ACA data, show that interferometric-filtering effects do not generate spurious sub-structures within the filament (see Fig. [10](#fig_alma_sim) in Appendix A).

# Results and analysis

In this section, we show the results of our ALMA 3.1 mm continuum and N$_2$H$^+$ (1–0) line observations, and then extract compact 3.1 mm continuum sources and fiber-like velocity-coherent structures from the ALMA data.

## 3.1 mm continuum emission

Our ALMA 3.1 mm continuum map of the NGC 6334 filament region is shown in panel $a$ of Fig. [1](#figs) (color scale and contours). It is also overlaid as contours

on a *Spitzer* 8 $\mu$m emission map in panel $d$

of Fig. [1](#figs). Hereafter, we call the map resulting from the combination of APEX/ArT$\acute{\rm e}$MiS 350 $\mu$m (cite: Andre16) and *Herschel*/SPIRE 350 $\mu$m (cite: Russeil13) data the ArT$\acute{\rm e}$MiS 350 $\mu$m map. The counterpart of the dense filament seen in the ArT$\acute{\rm e}$MiS 350 $\mu$m map can be

recognized in the northern part of the ALMA 3.1 mm continuum map. In the southern part of the field, the filament is not clearly detected in the ALMA 3.1 mm continuum map, but a shell-like structure can be seen. Conversely, the shell-like structure is not seen in the ArT$\acute{\rm e}$MiS 350 $\mu$m map. A compact HII region associated with a 4.9 GHz radio continuum source labeled source D in (cite: Rodriguez82) lies close to the contours of this shell-like structure. The shell-like structure in the ALMA 3.1 mm continuum map also coincides with bright, extended mid-infrared emission detected at 8 $\mu$m with *Spitzer* as shown in Fig. [1](#figs)$d$. We conclude that the 3.1 mm continuum emission in the shell-like structure is most likely dominated by free-free emission from the compact HII region around the luminous embedded star associated with source D.

## Molecular lines

### Spatial distribution of the N$_2$H$^+$(1–0) emission

Figure [1](#figs)$b$ shows the integrated intensity map of the N$_2$H$^+$(1–0) line emission around the NGC 6334 main filament. It can be seen that the prominent dusty filament in the ArT$\acute{\rm e}$MiS 350 $\mu$m map (Fig. [1](#figs)$c$) is very well traced by the ALMA N$_2$H$^+$(1–0) data. In addition, a few N$_2$H$^+$ blobs can be recognized outside the main filament.

### Spatial distributions of other molecular line tracers

The ALMA maps obtained in all other molecular line tracers, except HNC(1–0), also show the NGC 6334 filament (see Fig. [11](#figs_otherlines)$a$–$e$ in Appendix [6](#Sect:Complementary)). The map obtained in HNC(1–0) differs from the other maps in that it shows a rather scattered distribution of discrete blobs. Due to a lower effective excitation density (cite: Shirley15), the emission from the HNC(1–0) transition may be more extended than the emission in the other dense gas tracers observed here and may be resolved out due to interferometric filtering effects, even with ACA. The maps obtained in CH$_3$CCH(6$_0$–5$_0$), H$_2$CS(3$_{1,2}$–2$_{1,1}$), HC$_3$N(10–9), and HC$_5$N(36–35) emission appear to trace the same filamentary structure as detected in N$_2$H$^+$(1–0). The HC$_5$N(36–35) line has a high upper state energy of 80.504 K, implying that some of the gas in the main filament has a high temperature and/or density. Indeed, (cite: Andre16) estimated the average column density and average volume density of the entire NGC 6334 filament to be 1-2$\times$10$^{23}$ cm$^{-2}$ and 2.2$\times$10$^{5}$ cm$^{-3}$, respectively. This exceeds the (column) density values observed by (cite: Palmeirim13) for the low-mass star-forming filament B211/B213 in Taurus ($\sim$1.4$\times$10$^{22}$ cm$^{-2}$ and 4.5$\times$10$^{4}$ cm$^{-3}$) by an order of magnitude.

### Observed line profiles

![](averaged_hc5n_n2h+_spectrum.png)

![](NGC6334_cont_clustering_only12m.png)

The N$_2$H$^+$(1–0) and HC$_5$N(36–35) line observations were obtained in narrow-band mode with a velocity resolution of 0.2 km s$^{-1}$, which allows us to investigate the velocity structure of the NGC 6334

filament.

Here, we discuss the velocity profiles obtained in N$_2$H$^+$(1–0) and HC$_5$N(36–35).

Figure [2](#figs:hc5n_n2h+_spectrum) shows the N$_2$H$^+$(1–0) and HC$_5$N(36–35) spectra averaged over the pixels where significant emission was detected above the 5$\sigma$ level. Two peaks at $V_{\rm sys}$=$-$2.6 and $V_{\rm sys}$=$-$1.0 km s$^{-1}$ can be recognized in the HC$_5$N(36–35) spectrum. We set the velocity scale of the N$_2$H$^+$ (1–0) spectrum using the rest frequency of the isolated component of the N$_2$H$^+$ ($v$=0, $J$=1–0, $F_1$=0–1, $F$=1–2, 93.176265 GHz) hyperfine structure (HFS) multiplet as a reference. Hereafter, we call this isolated N$_2$H$^+$ component "HFS 1" and the other components "HFS 2-7" (see Fig. [2](#figs:hc5n_n2h+_spectrum)). The peak velocity of HFS 1 ($\sim$ $-$2.6 km s$^{-1}$) is consistent with the peak velocity of the HC$_5$N(36–35) emission. In addition, the N$_2$H$^+$ HFS 1 line profile exhibits an emission wing at highly blueshifted velocities (up to $-$12 km s$^{-1}$, see Fig. [2](#figs:hc5n_n2h+_spectrum)). This blueshifted emission does not appear to be associated with the NGC 6334 filament itself since it is mainly detected outside the main filamentary structure (see Fig. [17](#figs:n2h+_blue)). At positions where the blueshifted emission between $-$12 to $-$6 km s$^{-1}$ overlaps with the main velocity component at $\sim$ $-$2.6 km s$^{-1}$ in the plane of the sky, the HFS 2-7 counterparts of the blueshifted emission can be confused with HFS 1 emission from the $-$2.6 km s$^{-1}$ component since the velocity offsets of the HFS 2-7 components range from 7.3 km s$^{-1}$ to 14.9 km s$^{-1}$ with respect to the velocity of HFS 1 (see Appendix [7](#Sect:Contamination)).

## Extraction of compact continuum sources and "fiber-like" velocity structure from the data

To extract compact continuum sources from the ALMA/ACA 3.1 mm continuum map and fiber-like velocity-coherent features from the ALMA/ACA N$_2$H$^+$ (1–0) data cube, we made use of the *getsources*, *getfilaments*, and *getimages* algorithms (cite: Menshchikov12; Menshchikov13; Menshchikov17).

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID$^{1}$ | RA | DEC | $R_{\rm major} \times R_{\rm minor}$ | PA | S$_{\rm 3.1mm}^{\rm peak}$ | S/N | $S_{\rm 3.1mm}^{\rm tot}$ | $M_{\rm tot}$ | $\overline{n_{\rm H_2}}$ | Velocity channel at which | Association with |  |
|  |  |  |  |  |  |  |  |  |  | source is detected in N$_2$H$^+$ | N$_2$H$^+$ features |  |
|  | \[hms\] | \[dms\] | \[$\ensuremath{''} \times \ensuremath{''}$\]$^{3,4}$ | \[deg\]$^{3}$ | \[mJy/beam\]$^{3}$ | \[$\sigma$\] | \[mJy\]$^{3}$ | \[$M_{\odot}$\]$^{5}$ | \[$\times$10$^6$ cm$^{-3}$\]$^{6}$ | \[km s$^{-1}$\] |  |  |
| **1** | 17:20:43.13 | -35:47:54.9 | 2.9$\times$2.3 (0.02 pc $\times$ 0.02 pc) | 1 | 5.1$\pm$0.2 | 36.4 | 11.4 | 31.5 | 11.1 | \[-2.2,-1.8\] | F-2 |  |
| 2 | 17:20:41.78 | -35:48:9.2 | 2.8$\times$1.7 (0.02 pc $\times$ 0.01 pc) | 10 | 6.9$\pm$0.2 | 49.2 | 13.5 | 13.8 | 8.1 |  | No N$_2$H$^{+}$ |  |
| 3 | 17:20:45.00 | -35:46:42.7 | 1.7$\times$0.8 (0.01 pc $\times$ 0.01 pc) | -33 | 2.9$\pm$0.2 | 21.0 | 4.1 | 11.2 | 42.5 | -1.2$^{7}$ |  |  |
| **4** | 17:20:43.56 | -35:47:51.4 | 2.2$\times$1.1 (0.02 pc $\times$ 0.01 pc) | 36 | 3.0$\pm$0.2 | 21.4 | 4.7 | 12.8 | 22.6 | \[-1.4,-1.2\] | F-2 |  |
| **5** | 17:20:43.16 | -35:47:46.6 | 1.2$\times$0.8 (0.01 pc $\times$ 0.01 pc) | -8 | 2.5$\pm$0.2 | 18.2 | 3.2 | 8.9 | 54.3 | \[-2.6,-2.4\],\[-2.0,-1.8\] | F-1 |  |
| **6** | 17:20:44.66 | -35:46:54.3 | 1.7$\times$1.3 (0.01 pc $\times$ 0.01 pc) | 6 | 2.4$\pm$0.2 | 17.0 | 3.5 | 9.6 | 19.1 | \[-3.0,-2.8\],\[-1.8\],\[-1.4,-1.2\] | F-2 |  |
| **7** | 17:20:44.51 | -35:47:0.8 | 2.0$\times$1.1 (0.02 pc $\times$ 0.01 pc) | -32 | 2.4$\pm$0.2 | 17.3 | 3.7 | 10.1 | 19.1 | -3.8,-2.8$^{7}$ | F-1(marginal)/F-3(marginal) |  |
| **8** | 17:20:40.42 | -35:48:51.1 | 1.9$\times$1.4 (0.02 pc $\times$ 0.01 pc) | -22 | 3.0$\pm$0.2 | 21.5 | 4.7 | 12.9 | 18.5 | \[-2.6,-1.4\] |  |  |
| **9** | 17:20:44.48 | -35:47:17.1 | 1.9$\times$1.5 (0.02 pc $\times$ 0.01 pc) | 40 | 2.7$\pm$0.2 | 19.4 | 4.3 | 11.9 | 14.7 | \[-2.8,-2.6\],\[-1.8,-1.2\] | F-2 |  |
| **10** | 17:20:39.27 | -35:49:16.9 | 2.1$\times$0.9 (0.02 pc $\times$ 0.01 pc) | 35 | 3.3$\pm$0.2 | 23.8 | 5.0 | 13.7 | 35.1 | \[-3.8,-3.0\] | F-1 |  |
| **11** | 17:20:41.25 | -35:48:18.3 | 1.5$\times$1.0 (0.01 pc $\times$ 0.01 pc) | -39 | 2.3$\pm$0.2 | 16.6 | 3.2 | 8.7 | 28.4 | \[-3.6,-2.6\] |  |  |
| **12** | 17:20:39.44 | -35:49:2.8 | 2.4$\times$1.4 (0.02 pc $\times$ 0.01 pc) | -42 | 3.5$\pm$0.2 | 24.8 | 6.0 | 16.6 | 15.8 | \[-3.8,-2.4\] |  |  |
| 13 | 17:20:39.05 | -35:49:20.7 | 2.4$\times$0.9 (0.02 pc $\times$ 0.01 pc) | 19 | 1.8$\pm$0.2 | 13.1 | 2.9 | 8.1 | 15.3 | -3.8$^{7}$ |  |  |
| **14** | 17:20:45.52 | -35:46:33.6 | 1.7$\times$1.5 (0.01 pc $\times$ 0.01 pc) | -28 | 1.7$\pm$0.2 | 12.1 | 2.6 | 7.1 | 10.7 | \[-3.2,-2.8\],\[-2.2, -2.0\], -1.2 | F-2 |  |
| 15$^{2}$ | 17:20:41.58 | -35:48:37.5 | 1.5$\times$1.0 (0.01 pc $\times$ 0.01 pc) | -23 | 2.6$\pm$0.2 | 18.3 | 2.1 | 7.0 | 24.4 |  | No N$_2$H$^{+}$/free-free contamination |  |
| 16 | 17:20:43.38 | -35:48:47.0 | 2.3$\times$0.9 (0.02 pc $\times$ 0.01 pc) | -32 | 4.5$\pm$0.2 | 32.3 | 7.1 | 19.6 | 37.8 |  | No N$_2$H$^{+}$/Out of main filament |  |
| **17** | 17:20:39.39 | -35:49:13.7 | 2.1$\times$1.7 (0.02 pc $\times$ 0.01 pc) | 6 | 3.9$\pm$0.2 | 28.1 | 6.6 | 18.2 | 17.7 | \[-3.8,-2.8\] |  |  |
| **18** | 17:20:42.35 | -35:48:34.2 | 2.0$\times$1.7 (0.02 pc $\times$ 0.01 pc) | -39 | 4.8$\pm$0.2 | 34.5 | 8.1 | 22.3 | 21.9 | -3.4,\[-1.6, -1.4\] | free-free contamination |  |
| 19$^{2}$ | 17:20:40.97 | -35:48:21.2 | 1.5$\times$1.0 (0.01 pc $\times$ 0.01 pc) | -19 | 2.0$\pm$0.2 | 13.9 | 1.8 | 5.4 | 18.6 |  | No N$_2$H$^{+}$ |  |
| **20** | 17:20:40.66 | -35:48:39.4 | 1.3$\times$1.0 (0.01 pc $\times$ 0.01 pc) | 44 | 2.1$\pm$0.2 | 15.0 | 2.8 | 7.6 | 31.0 | \[-3.4,-2.6\] | F-1 |  |
| **21**$^{2,3}$ | 17:20:41.20 | -35:48:28.5 | 1.4$\times$0.9 (0.01 pc $\times$ 0.01 pc) | -33 | 1.1$\pm$0.1 | 8.1 | 1.4 | 3.1 | 13.4 | \[-2.4,-1.2\] | F-1 |  |
| **22** | 17:20:44.39 | -35:47:26.4 | 2.1$\times$1.6 (0.02 pc $\times$ 0.01 pc) | -2 | 2.2$\pm$0.2 | 16.0 | 3.7 | 10.2 | 10.7 | \[-3.8,-3.2\], \[-1.8,-1.2\] | F-2 |  |
| **23** | 17:20:41.65 | -35:48:3.1 | 3.0$\times$1.3 (0.02 pc $\times$ 0.01 pc) | 44 | 1.7$\pm$0.2 | 12.2 | 3.2 | 8.9 | 7.0 | \[-3.4,-2.4\] | F-1 |  |
| **24** | 17:20:47.61 | -35:47:53.7 | 1.6$\times$1.5 (0.01 pc $\times$ 0.01 pc) | 31 | 1.2$\pm$0.2 | 8.3 | 1.7 | 4.8 | 8.1 | \[-3.4,-3.2\],-2.0, -1.2 | Out of main filament |  |
| 25 | 17:20:42.87 | -35:49:36.0 | 1.9$\times$0.8 (0.02 pc $\times$ 0.01 pc) | 34 | 1.9$\pm$0.2 | 13.7 | 2.8 | 7.6 | 23.9 |  | No N$_2$H$^{+}$/Out of main filament |  |
| **26** | 17:20:42.87 | -35:48:6.6 | 2.0$\times$0.2 (0.02 pc $\times$ 0.00 pc) | 28 | 1.5$\pm$0.2 | 10.5 | 2.0 | 5.6 | 141.9 | \[-1.4,-1.2\] | F-2 |  |
| **27** | 17:20:38.94 | -35:49:5.9 | 2.1$\times$1.0 (0.02 pc $\times$ 0.01 pc) | -19 | 1.9$\pm$0.2 | 13.6 | 2.9 | 7.9 | 17.0 | \[-2.2,-1.6\] |  |  |
| 28 | 17:20:41.88 | -35:49:1.6 | 3.4$\times$0.9 (0.03 pc $\times$ 0.01 pc) | -41 | 2.2$\pm$0.2 | 16.0 | 4.3 | 11.9 | 14.4 |  | No N$_2$H$^{+}$/Out of main filament |  |
| 29$^{2,3}$ | 17:20:39.59 | -35:48:42.6 | 1.4$\times$0.9 (0.01 pc $\times$ 0.01 pc) | 15 | 0.6$\pm$0.1 | 4.5 | 0.3 | 1.7 | 7.4 |  | No N$_2$H$^{+}$ |  |
| 30 | 17:20:42.35 | -35:49:31.8 | 1.7$\times$1.7 (0.01 pc $\times$ 0.01 pc) | 1 | 2.7$\pm$0.2 | 19.1 | 4.2 | 11.6 | 14.6 |  | No N$_2$H$^{+}$/Out of main filament |  |
| **31** | 17:20:44.42 | -35:47:21.2 | 2.2$\times$1.5 (0.02 pc $\times$ 0.01 pc) | 22 | 2.1$\pm$0.2 | 15.2 | 3.5 | 9.7 | 10.7 | -3.8, \[-2.0, -1.8\] | F-2 |  |
| 32$^{2,3}$ | 17:20:44.26 | -35:49:14.1 | 1.4$\times$0.9 (0.01 pc $\times$ 0.01 pc) | 39 | 3.3$\pm$0.1 | 23.4 | 1.1 | 9.0 | 38.5 |  | No N$_2$H$^{+}$/Out of main filament |  |
| 33$^{2}$ | 17:20:43.39 | -35:47:57.3 | 1.5$\times$1.0 (0.01 pc $\times$ 0.01 pc) | 42 | 2.3$\pm$0.2 | 16.4 | 0.7 | 6.3 | 21.9 | -1.8$^{7}$ | F-2(marginal) |  |
| **34** | 17:20:39.27 | -35:47:59.3 | 2.3$\times$1.3 (0.02 pc $\times$ 0.01 pc) | 34 | 2.0$\pm$0.2 | 14.4 | 3.4 | 9.2 | 10.7 | \[-3.8, -3.6, -3.4\], \[-2.8, -2.6\] | Out of main filament |  |
| 35$^{2,3}$ | 17:20:38.34 | -35:48:32.4 | 1.4$\times$0.9 (0.01 pc $\times$ 0.01 pc) | 15 | 0.9$\pm$0.1 | 6.7 | 1.2 | 2.6 | 11.0 | -2.2$^{7}$ | Out of main filament |  |
| 36 | 17:20:42.92 | -35:49:24.7 | 2.1$\times$1.9 (0.02 pc $\times$ 0.02 pc) | -19 | 3.8$\pm$0.2 | 27.0 | 6.7 | 18.5 | 14.1 |  | No N$_2$H$^{+}$/Out of main filament |  |
| 37 | 17:20:36.73 | -35:48:56.6 | 1.9$\times$1.4 (0.02 pc $\times$ 0.01 pc) | 38 | 1.4$\pm$0.2 | 9.9 | 2.2 | 6.0 | 8.4 |  | No N$_2$H$^{+}$/Out of main filament |  |
| 38 | 17:20:43.44 | -35:49:6.4 | 2.2$\times$1.8 (0.02 pc $\times$ 0.01 pc) | -4 | 1.8$\pm$0.2 | 12.9 | 3.1 | 8.7 | 7.2 |  | No N$_2$H$^{+}$/Out of main filament |  |
| **39** | 17:20:40.25 | -35:48:46.7 | 2.5$\times$1.5 (0.02 pc $\times$ 0.01 pc) | -36 | 2.3$\pm$0.2 | 16.4 | 4.0 | 11.1 | 10.0 | \[-2.6,-2.2\] |  |  |
| 40 | 17:20:42.82 | -35:49:20.4 | 2.0$\times$1.9 (0.02 pc $\times$ 0.02 pc) | 0 | 3.4$\pm$0.2 | 24.4 | 5.9 | 16.3 | 13.8 |  | No N$_2$H$^{+}$/Out of main filament |  |

Table notes:\
\
\
\
\
\

![](NGC6334_artemis_all.png)

![](3d_skelton_a.png)

### Compact source extraction from the ALMA 3.1 mm continuum data with *getsources*

To identify compact sources in the ALMA 3.1 mm continuum map, we applied the *getsources* algorithm (cite: Menshchikov12). *getsources* is a multi-scale source extraction algorithm primarily developed for the exploitation of multi-wavelength far-infrared and submillimeter continuum data resulting from *Herschel* surveys of Galactic star-forming regions (cite: Konyves15), but can also be used with single-band continuum data and spectral line data. Source extraction with this algorithm has only one free parameter, namely the maximum size of the structures to be extracted from the images. Here, we adopted a maximum size of 15 $\ensuremath{''}$ (or $\sim$0.12 pc), which is comparable to the transverse full width at half maximum (FWHM) size of the filament as measured with ArTéMiS (cite: Andre16).

After running *getsources* on the 12m-only data[^2] and applying post-extraction selection criteria (see Appendix [8](#Sect:getsources_post_selection_detail)), we identified a total of 40 candidate compact 3.1 mm continuum sources. As shown in Fig. [1](#figs)$a$, 28 of these 40 sources are located within the main filament defined as the intersection of the area within $\pm$30$\ensuremath{''}$ (or $\pm$0.25 pc) from the filament crest and the area enclosed within the 5 Jy beam$^{-1}$ contour in the ArT$\acute{\rm e}$MiS 350 $\mu$m map (see also Fig. [3](#figs:ArTeMiS_ALMA_core_association) and Table [\[table:cont_getsources_12m_only\]](#table:cont_getsources_12m_only)). Two of these 28 sources (IDs 15, 18 in Table [\[table:cont_getsources_12m_only\]](#table:cont_getsources_12m_only)) are probably affected by contamination from free-free emission as mentioned in Sect. [3.1](#result:cont). The positions and sizes of all of these 40 compact continuum sources are summarized in Table [\[table:cont_getsources_12m_only\]](#table:cont_getsources_12m_only), along with their basic properties.

To investigate whether the compact continuum sources identified above are associated with N$_2$H$^+$ emission, we also applied *getsources* to each N$_2$H$^+$ velocity channel map (see Appendix [8](#Sect:getsources_post_selection_detail) for details). We found that 23 of the 40 compact continuum sources are associated with N$_2$H$^+$ emission in at least two consecutive channels. In addition, five of the 40 compact sources (IDs 3, 7, 13, 33, 35 in Table [\[table:cont_getsources_12m_only\]](#table:cont_getsources_12m_only)) are associated with N$_2$H$^+$ (1–0) line emission in only one channel, but these sources did not pass our post-extraction selection criteria (see Appendix [8](#Sect:getsources_post_selection_detail)). Although contamination of the 3.1 mm continuum data by free-free emission is an issue, compact sources robustly detected in both 3.1 mm continuum and N$_2$H$^+$ emission are unlikely to be affected.

We estimated the mass ($M_{\rm tot}$) of each compact continuum source, under the assumption that all of the 3.1 mm continuum emission arises from dust and that the emission is optically thin. The mass

was obtained from the integrated 3.1 mm flux density $S_{\rm 3.1mm}^{\rm tot}$ derived from two-dimensional Gaussian fitting in the 12m$+$7m continuum image[^3] using the formula:

$$\begin{equation}
\label{eq1}
M_{\rm tot} = \frac{S_{\rm 3.1mm}^{\rm tot} d^2}{\kappa_{\rm 3.1mm} B_{\rm 3.1mm}(T_{\rm d})}, 
\end{equation}$$

where $d$, $\kappa_{\rm 3.1mm}$, and $B_{\rm 3.1mm}$($T_{\rm d}$) are the distance to the target, the dust opacity (per unit mass of gas + dust), and the Planck function at dust temperature $T_{\rm d}$, respectively. We adopted the same dust opacity law as the *Herschel* Gould Belt survey team, namely $\kappa_\lambda$ = 0.1 ($\lambda$/300$\mu$m)$^{-\beta}$ cm$^2$g$^{-1}$ (cite: Hildebrand83; Roy14) with $\beta =2$ and here $\lambda = 3.1\,$mm. If $\beta = 1.5$ instead of $\beta = 2$, the core masses would be a factor of $\sim$3 lower than the values listed in Table [\[table:cont_getsources_12m_only\]](#table:cont_getsources_12m_only). For most sources, we adopted $T_{\rm dust}$ = 20 K which corresponds to the median dust temperature derived from *Herschel* data along the crest of the filament (cite: Andre16; Tige17). For source ID 1, we adopted a higher temperature value ($T_{\rm dust}$ = 50 K) as this object coincides with a bright *Spitzer* 8 $\mu$m source and is most likely an internally-heated, relatively massive protostellar core. The 5$\sigma$ mass sensitivity of the ALMA 12m continuum data for compact sources is $\sim$$2.0\, M_{\odot}$, corresponding to $S_{\rm 3.1mm}^{\rm tot} =0.7$ mJy, assuming $\beta$ = 2 and $T_{\rm dust}$ = 20 K. The average gas density ($\equiv \overline{n_{\rm H_2}}$) of each source was then derived assuming spheroidal cores as follows:

$$\begin{equation}
\overline{n_{\rm H_2}} = \frac{M_{\rm tot}}{\frac{4}{3}\pi[\sqrt{R_{\rm major} R_{\rm minor}}]^3}, 
\end{equation}$$

where $R_{\rm major}$ and $R_{\rm minor}$ are the deconvolved FWHM sizes along the major and minor axis of the source, respectively (cite: Konyves15). The median mass of the 26 compact continuum sources embedded in the main filament[^4] is $9.6^{+3.0}_{-1.9}$ $M_{\odot}$ (lower quartile: 7.7 $M_{\odot}$, upper quartile: 12.6 $M_{\odot}$) and their median volume-averaged density 1.6$\times$10$^{7}$ cm$^{-3}$ (lower quartile: 1.0$\times$10$^{7}$ cm$^{-3}$, upper quartile: 2.2$\times$10$^{7}$ cm$^{-3}$). The 26 continuum sources embedded in the main filament are compact (with an estimated typical outer radius $\sim 5000\,$au) and have a very high volume-averaged density ($\sim$10$^{7}$ cm$^{-3}$),

suggesting that they are on their way to form stars. Moreover, their spatial distribution closely follows that of the ArT$\acute{\rm e}$MiS 350$\mu$m emission clumps (see Fig. [3](#figs:ArTeMiS_ALMA_core_association) and Sect. [4.1](#two_levels)). In the following, we therefore regard these 26 compact 3.1 mm continuum sources as dense cores.

### Extraction of fiber-like structures from the N$_2$H$^+$ data cube with *getfilaments*

*Removal of unrelated velocity components.* In the NGC 6334 region, we found evidence of the presence of several velocity components along the line of sight (see Sect. [3.2.3](#Sect:velo_structure)). To avoid contamination of the N$_2$H$^+$(1–0) HFS 1 line emission from the main velocity component at $V_{\rm sys}$=$-$2.6 km s$^{-1}$ by the HFS 2-7 emission from other velocity components, we fit the N$_2$H$^+$ emission observed at each pixel with a multiple-velocity-component HFS model and subtracted the corresponding HFS 2-7 emission from the data cube. As shown in Fig. [12](#figs:N2Hp_contamination) in Appendix [7](#Sect:Contamination)), if the velocity width of each component is $\sim$1.0 km s$^{-1}$, then the N$_2$H$^+$ HFS 1 emission of the main component can be contaminated by the HFS 2-7 emission of a more blue-shifted velocity component when the velocity difference between the two components along the line of sight is $\sim \,$5.0-7.0 km s$^{-1}$. Figure [13](#figs:n2h+_spectrum_removal) shows four examples of N$_2$H$^+$(1–0) spectra obtained after subtraction of contaminating components. Hereafter, we use the subtracted data cube in our scientific analysis.

![](spectra_fibers.png)

| ID  | length  |     velocity range     |     |
|:----|:-------:|:----------------------:|:---:|
| F-1 | 1.21 pc | \[$-$3.4,$-$2.2 km/s\] |     |
| F-2 | 0.72 pc | \[$-$2.2,$-$1.2 km/s\] |     |
| F-3 | 0.33 pc | \[$-$3.6,$-$2.4 km/s\] |     |
| F-4 | 0.26 pc | \[$-$3.4,$-$3.2 km/s\] |     |
| F-5 | 0.17 pc | \[$-$2.2,$-$1.6 km/s\] |     |

: N$_2$H$^+$ "fiber-like" structures identified with *getfilaments*

![](NGC6334_artemis_fiber_zoom_north_south.png)

*Extraction of velocity-coherent fiber-like features with *getfilaments*.* We extracted filamentary structures from the ALMA N$_2$H$^+$ data cube after subtraction of compact N$_2$H$^+$ emission using the *getfilaments* algorithm (cite: Menshchikov13). Each N$_2$H$^+$ velocity channel map was decomposed into a set of spatially-filtered single-scale images from small (3$\ensuremath{''}$) to large (16$\ensuremath{''}$) scales. At each scale, the algorithm separated filamentary structures and compact sources, and extracted significant filamentary structures in the source-subtracted image component. All extracted filamentary structures were merged into a single image per velocity channel map. We selected only filamentary structures whose $>$90% pixels along the crest were detected above the $>$ 3$\sigma$ level in each channel. As the velocity resolution of our ALMA N$_2$H$^+$ data (0.2 km s$^{-1}$, that is, less than the isothermal sound speed in the cloud) should be sufficient to resolve the velocity width of the filament, we also imposed that a selected filamentary structure should be detected in at least two consecutive velocity channels. By comparing velocity-channel maps, we therefore associated filamentary structures with matching spatial distributions among channels (see Appendix [9](#Sect:getfilament_post_selection_detail)). Our procedure is similar to that used by (cite: Hacar13) to trace velocity-coherent structures in data cubes, in the sense that both methods work in position-position-velocity (PPV) space[^5]. In this way, we identified five distinct fiber-like structures, labeled F-1 to F-5, whose crests are displayed in Fig. [4](#figs:getfilament) and Fig. [5](#figs:3d_skelton). Examples of individual N$_2$H$^+$ (HFS 1) spectra across the two main fiber-like structures F-1 and F-2 are shown in Fig. [6](#figs:n2h+_fiber_spectrum). The spatial distribution of the structure labeled F-2 partly overlaps with the distribution of F-1 at $-$2.4 km s$^{-1}$. But the northern portion of F-2 lies slightly to the west of F-1, while the southern part of F-2 lies to the east of F-1 (see, e.g., Fig. [4](#figs:getfilament)b). Moreover, at positions where F-1 and F-2 overlap in the plane of the sky, the N$_2$H$^+$ spectra clearly exhibit distinct velocity components \[see, e.g., positions (c) and (d) in Fig. [6](#figs:n2h+_fiber_spectrum)\]. Therefore, F-1 and F-2 seem to be distinct velocity-coherent features. The five fiber-like structures are likely associated with the dust continuum filament seen in the ArT$\acute{\rm e}$MiS 350 $\mu$m map. Similar sub-filamentary structures have been found in the low-mass star-forming filament B211/B213 in Taurus (cite: Hacar13) and have been called fibers in the literature (cite: Tafalla15). At this point, we refer to the five features F-1–F-5 as fiber-like structures. (In Sect [4.3](#fibers) below, we argue that only two of them, F-1 and F-2, may be genuine fibers, that is velocity-coherent sub-structures of the main filament itself.) Their typical length is 0.5$\pm$0.4 pc (see Table [1](#table:N$_2$H$^+$_filament), which also gives their velocity ranges).

A portion of the dusty filament seen in the ArT$\acute{\rm e}$MiS 350 $\mu$m continuum map was not traced by *getfilaments* in the N$_{2}$H$^{+}$ data, especially in the southern part of the field in Fig. [1](#figs) although the filament can be recognized by eye in the N$_2$H$^+$(1–0) integrated intensity map (Fig.[1](#figs)$b$). The reason why this southern portion was not traced in the N$_2$H$^+$ velocity channel maps with *getfilaments* is that the N$_2$H$^+$ emission becomes very clumpy in this area and was subtracted out as a collection of point-like sources by *getsources* before identification of filamentary structures.

F-1 is the longest and F-2 the second longest of the five extracted velocity features. Both of these fiber-like structures are roughly parallel to the dust continuum filament seen in the ArT$\acute{\rm e}$MiS 350 $\mu$m map. In contrast, the crest of F-5 is roughly perpendicular to the dust filament. In the northern part of the N$_2$H$^+$ map (north of -35$^{\circ}$47$\ensuremath{'}$10$\ensuremath{''}$ in Fig. [4](#figs:getfilament) and Fig. [7](#figs:getfilament_zoom)a), the spatial distributions of F-1, F-2, F-4 partly overlap in the plane of sky. The three features F-1, F-2, F-4 are nevertheless separated from each other in velocity space (see Table [1](#table:N$_2$H$^+$_filament)). The crests of F-1, F-2, F-4 are also slightly shifted from one another by typically one ALMA beam ($\sim$3$\ensuremath{''}$, see Fig. [7](#figs:getfilament_zoom)a). In the northern part, they are distributed in the sequence F-1, F-2, F-4 from east to west (see Fig. [7](#figs:getfilament_zoom)a). In contrast, the projected LSR velocities are in the order F-4 ($\sim$ $-$3.3 km s$^{-1}$), F-1 ($\sim$ $-$2.8 km s$^{-1}$), F-2 ($\sim$ $-$1.7 km s$^{-1}$). Assuming F-1, F-2, F-4 are part of the same filament, this different ordering between the spatial and velocity distributions cannot be explained by a simple transverse velocity gradient across the parent filament due to either accretion onto and/or rotation of the filament. In the southern part of the field (south of -35$^{\circ}$47$\ensuremath{'}$10$\ensuremath{''}$ in Fig. [4](#figs:getfilament) and Fig. [7](#figs:getfilament_zoom)b), F-4 is not detected and F-1, F-2 are distributed in the order F-2, F-1 from east to west (see Fig. [7](#figs:getfilament_zoom)b).

These opposite spatial configurations for F-1, F-2 between the northern and the southern part of the dust filament are suggestive of an intertwined, double helix-like pattern (DNA-like) (see Fig. [\[figs:DNA_fiber\]](#figs:DNA_fiber)b).

We also extracted filamentary structures from the ALMA HC$_3$N, HC$_5$N, CH$_3$CCH, and H$_2$CS integrated intensity maps using *getfilaments*. We detected one filamentary structure in HC$_3$N, one filamentary structure in HC$_5$N, one filamentary structure in CH$_3$CCH, and two filamentary structures in H$_2$CS. These filamentary structures roughly correspond to the F-1 and/or F-2 "fiber-like" features identified in N$_2$H$^+$. Due to the lower effective sensitivity of the H$_2$CS(3$_{1,2}$-2$_{1,1}$) data, the NGC 6334 filament is broken up into two segments in H$_2$CS. The H$_2$CS filamentary structures coincide with the northern and southern parts of the filamentary structures traced in other lines. Owing to the lower line intensities and/or lower spectral resolution of our data in HC$_3$N, HC$_5$N, CH$_3$CCH, and H$_2$CS, we could not carry out as detailed a PPV analysis in these lines as in N$_2$H$^+$.

![](NNStest_vs_obs.png)

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ArT$\acute{\rm e}$MiS | RA | DEC | $R_{\rm major} \times R_{\rm minor}$$^\dag$ | PA | $S_{350\mu m}^{\rm peak}$ | $S_{350\mu m}^{\rm tot}$ | $M_{\rm clump}$$^\ddag$ | $\overline{n_{\rm H_2}}$ | $\sigma_{\rm N_2H^+}$ | IDs of |
| clump | \[h:m:s\] | \[d:m:s\] |  | \[deg\] | \[Jy/beam\] | \[Jy\] | \[$M_{\odot}$\] | \[$\times$10$^5$ cm$^{-3}$\] | \[km/s\] | associated ALMA cores |
| 1 | 17:20:44.9 | -35:46:60 | 31.$\ensuremath{''}$9$\times$13.$\ensuremath{''}$7 (0.26pc $\times$0.11pc) | 15 | 17 | 227 | 320 | 2.1 | 0.5 | 6,7 (Group2) |
| 2 | 17:20:44.3 | -35:47:28 | 21.$\ensuremath{''}$2$\times$14.$\ensuremath{''}$8 (0.17pc $\times$0.12pc) | 22 | 11 | 106 | 149 | 1.7 | 0.8 | 9,19,24 (Group1) |
| 3 | 17:20:43.0 | -35:47:53 | 23.$\ensuremath{''}$6$\times$16.$\ensuremath{''}$9 (0.19pc $\times$0.14pc) | 24 | 18 | 216 | 303 | 2.3 | 1.0 | 1,4,5,21,25 (Group5) |
| 4 | 17:20:41.4 | -35:48:06 | 10.$\ensuremath{''}$9$\times$7.$\ensuremath{''}$5 (0.09pc $\times$0.06pc) | 26 | 9 | 36 | 51 | 4.2 | 0.3 | 2,11,16,18,20 (Group7) |
| 5 | 17:20:42.5 | -35:48:28 | 14.$\ensuremath{''}$7$\times$13.$\ensuremath{''}$7 (0.12pc $\times$0.11pc) | -80 | 12 | 82 | 116 | 2.5 | 0.8 |  |
| 6 | 17:20:40.7 | -35:48:37 | 24.$\ensuremath{''}$6$\times$13.$\ensuremath{''}$0 (0.20pc $\times$0.11pc) | 13 | 11 | 117 | 164 | 1.8 | 0.4 | 8,17,23,26 (Group6) |
| 7 | 17:20:39.2 | -35:49:06 | 25.$\ensuremath{''}$3$\times$14.$\ensuremath{''}$0 (0.21pc $\times$0.12pc) | 19 | 16 | 177 | 249 | 2.3 | 0.5 | 10,12,13,15,22 (Group4) |

Table notes:\

# Discussion

Our ALMA study has revealed, for the first time, the presence of density and velocity sub-structure in the NGC 6334 filament. We discuss the two types of sub-structure in turn in the following.

## Bimodal fragmentation in the NGC 6334 filament

While it was not clear whether dense cores were embedded in the NGC 6334 filament based only on the ArT$\acute{\rm e}$MiS 350 $\mu$m data (cite: Andre16), our ALMA 3.1 mm continuum map with an angular resolution of $\sim$$2.3\ensuremath{''}$ has allowed us to identify 26 candidate dense cores within the filament (cf. Sect. [3.3.1](#sect:getsources)). These ALMA cores appear to be clustered in several groups closely associated with ArT$\acute{\rm e}$MiS clumps (see Fig. [3](#figs:ArTeMiS_ALMA_core_association)). Figure [8](#figs:NNS_result) shows a dendrogram tree obtained when applying a nearest neighbor separation (NNS) analysis to the population of ALMA dense cores (with the *scipy* function *cluster.hierarchy.linkage* and the *single* method). Here, we adopted two values of the NNS grouping threshold, 0.1 pc and 0.15 pc, consistent with both the typical inner width of the filament and the typical FWHM size of the ArT$\acute{\rm e}$MiS clumps (see Table [\[table:ArTeMiS_clumps\]](#table:ArTeMiS_clumps)). Based on the NNS analysis with a grouping threshold of 0.1 pc, the 26 dense cores can be divided into seven groups of cores (groups 1–7). Using a grouping threshold of 0.15 pc instead of 0.1 pc, groups 2, 3

join group 1 and groups 4, 5, 6, 7

merge into the same group (see Fig. [8](#figs:NNS_result)).

Remarkably, the seven groups of ALMA compact cores roughly correspond to dense clumps visible as closed contours in the ArT$\acute{\rm e}$MiS 350 $\mu$m map of the NGC 6334 filament at 8$\ensuremath{''}$ resolution (see Figs. [1](#figs)c and [17](#figs:n2h+_blue)). For the purpose of this paper, we used GAUSSCLUMPS (cite: Stutzki90) to characterize the properties of the ArT$\acute{\rm e}$MiS clumps. We applied GAUSSCLUMPS with a detection threshold

of 1 Jy/8$''$ -beam corresponding to 5$\sigma$ (where 1$\sigma$=0.2 Jy/8$''$ -beam). A total of seven clumps were identified in this way within the footprint of the main filament, defined as the intersection of the area within $\pm$30$\ensuremath{''}$ (or $\pm$0.25 pc)[^6] from the filament crest and the interior of the 5 Jy/8$''$ -beam ArT$\acute{\rm e}$MiS contour (see solid white contour in Fig. [8](#figs:NNS_result)), whose positions, sizes, and estimated masses are given in Table [\[table:ArTeMiS_clumps\]](#table:ArTeMiS_clumps). These seven ArT$\acute{\rm e}$MiS clumps are also identified with the *getsources* (cite: Menshchikov12; Menshchikov13) and REINHLOD (cite: Berry07) source extraction algorithms, as described in Appendix [11](#Sect:comparison_IDs). They correspond to six groups of ALMA cores (groups 1, 2, 3, 5, 6, 7). More precisely, if we consider a group of ALMA dense cores to be associated with an ArT$\acute{\rm e}$MiS clump when all of the cores in the group lie within the closed contours of the clump (Table [\[table:ArTeMiS_clumps\]](#table:ArTeMiS_clumps)), then we find that each ArT$\acute{\rm e}$MiS clump consists of at least two ALMA cores (Fig. [3](#figs:ArTeMiS_ALMA_core_association)a).

To test whether the observed clustering of ALMA cores and close association with ArT$\acute{\rm e}$MiS clumps may also be present in the case of randomly distributed cores, we inserted 26 sources at random positions within the footprint of the main filament (see solid white contour in Fig. [8](#figs:NNS_result)) using the python module *random* and then applied the same NNS analysis. A total of 100 realizations of such random source distributions were constructed. Two examples of resulting NNS dendrogram trees are displayed in Fig. [\[figs_NNStest\]](#figs_NNStest), where they are compared to the NNS tree obtained for the real ALMA cores. It can be seen that randomly distributed sources tend to be less clustered than the observed cores, that is, a higher number of randomly-placed sources are isolated (not grouped by the NNS analysis) compared to the observations. In contrast to the observed cores, there is also no clear association between the groups of randomly-placed sources and the ArT$\acute{\rm e}$MiS clumps. The clustering of the observed ALMA cores within the ArT$\acute{\rm e}$MiS clumps is highly significant, at the $> 5\sigma$ level according to binomial statistics: 16 out of 26 cores ($> 60\%$) lie within the FWHM ellipses of the clumps, while only $3\pm2$ ($\sim 13\%$) of 26 randomly-placed objects would be expected within the clumps. Furthermore, the mean separation between observed cores ($0.04\pm 0.01$ pc) is smaller than the mean separation between randomly-placed sources found over 100 realizations ($0.06\pm 0.01$ pc).

It is also apparent in the top row of Fig. [8](#figs:NNS_result) that the observed cores lie significantly closer to the filament crest than randomly-placed objects within the filament footprint (solid white contour). Quantitatively, the distribution of offsets between the observed cores and the filament crest has a median value of only 0.02 pc (lower quartile: 0.01 pc, upper quartile: 0.03 pc) while the median offset between randomly-placed sources and the crest is 0.07 pc (lower quartile: 0.03 pc, upper quartile: 0.13 pc). In other words, the spatial distribution of observed cores is almost one-dimensional (1D) along the filament crest. To further test whether significant 1D grouping of the cores exists along the crest, we repeated the same experiment with randomly-placed objects as described above but using a narrower footprint, defined as the area within $\pm$6$\ensuremath{''}$ (or $0.05\,$pc) of the filament crest (dashed white contour in Fig. [8](#figs:NNS_result)). The transverse width of this inner filament footprint is $\sim\,$0.1 pc, which is comparable to the dispersion of observed core positions about the crest. In this case, the mean separation between randomly-placed sources becomes identical to the mean separation between observed cores ($0.04\pm 0.01\,$pc). The observed ALMA cores nevertheless remain more closely associated with the ArT$\acute{\rm e}$MiS clumps than randomly-distributed objects along the filament crest: only $8\pm3$ of 26 randomly-placed sources would be expected within the clumps, while 16 are observed, a difference which is significant at the $\sim 3\, \sigma$ level according to binomial statistics. We conclude that, even in 1D, there is marginal evidence of non-random core grouping along the filament axis.

The projected nearest-neighbor separation between the ArT$\acute{\rm e}$MiS clumps ranges from 0.2 pc to 0.3 pc, and the typical projected separation between ALMA dense cores embedded within a given ArT$\acute{\rm e}$MiS clump is $0.04\pm0.01$ pc. These observational findings are interesting to compare with theoretical expectations. When the line mass of a cylindrical gas filament is close to the critical mass per unit length (thermal case) or the virial mass per unit length (nonthermal case, more appropriate here – see end of Sect. [1](#intro)), the filament is expected to fragment into overdensities with a typical separation of about four times the filament width according to self-similar solutions which describe the collapse of an isothermal filament under the effect of self-gravity (cite: Inutsuka92; Inutsuka97). With a typical inner width of $0.15\pm 0.05\,$pc from the ArTéMiS results (cite: Andre16), the NGC 6334 filament can therefore be expected to fragment with a characteristic separation of $\sim \, 0.6\pm 0.2$ pc. This separation scale is roughly consistent with the projected separation of 0.2–0.3 pc observed between ArT$\acute{\rm e}$MiS clumps, assuming a plausible inclination angle of $\sim 30^\circ$ between the filament axis and the line of sight.

![](ngc6334_cmf_vs_aquila_cmf_ver2.pdf)

On the other hand, the effective Jeans length $\lambda_{\rm J,eff}$ or Bonnor-Ebert diameter $D_{\rm BE,eff}$ within the filament and its clumps may be estimated as (cite: Bonnor56):

$$\begin{equation}
\lambda_{\rm J,eff} \equiv D_{\rm BE,eff} \approx 0.98 \sqrt{\frac{C_{\rm s,eff}^2}{G\, \rho_{\rm clump}}}, 
\end{equation}$$

where

$$\begin{equation}
C_{\rm s,eff}= \sqrt{\sigma_{\rm N_2H^+}^2 + kT_{\rm k} (\frac{1}{m}-\frac{1}{m_{\rm N_2H^+}})}, 
\end{equation}$$

and $G$, $\rho_{\rm clump}$, $\sigma_{\rm N_2H^+}$, $T_{\rm k}$, $m$, and $m_{\rm N_2H^+}$ are the gravitational constant, the density of each ArT$\acute{\rm e}$MiS clump (see Table [\[table:ArTeMiS_clumps\]](#table:ArTeMiS_clumps)), the velocity dispersion measured in N$_2$H$^+$, the gas kinetic temperature, the mean molecular mass, and the mass of the N$_2$H$^+$ molecule, respectively. Assuming a gas kinetic temperature of 20 K, which corresponds to the median dust temperature derived from *Herschel* data along the crest of the filament (cite: Andre16; Tige17) and using the velocity dispersion measured in N$_2$H$^+$ for each ArT$\acute{\rm e}$MiS clump ($\sigma_{\rm N_2H^+}$= $\delta V_{\rm FWHM}$/$\sqrt{8\ln(2)}$, where $\delta V_{\rm FWHM}$ is the FWHM linewidth), the effective Jeans length in the clumps of the filament is estimated to range from $\sim$0.04 pc to $\sim$0.3 pc (median: 0.08 pc). This is roughly consistent with the typical projected separation between ALMA dense cores (0.04$\pm$0.01 pc) assuming random projection effects within the ArT$\acute{\rm e}$MiS clumps.

These two characteristic separation scales are suggestive of two distinct fragmentation modes within the NGC 6334 filament: (i) a cylindrical fragmentation mode into clumps or groups of cores with a separation of $\sim 4$ times the filament width, and (ii) a spherical Jeans-like fragmentation mode into compact cores with a separation on the order of the effective Jeans length. Similar bimodal fragmentation patterns were first reported by (cite: Takahashi13) in Orion OMC3 and (cite: Kainulainen13) in the infrared dark cloud (IRDC) G11.11-0.12 (see also (cite: Teixeira16) and (cite: Kainulainen17)). Recent theoretical works on filament fragmentation have tried to account for these two fragmentation modes based on perturbations to standard cylinder fragmentation models (cite: Clarke16; Gritschneder17; Lee17).

## Unusually massive cores in the NGC 6334 filament

Remarkably, the median mass of the ALMA cores ($9.6^{+3.0}_{-1.9}\, M_{\odot}$) is an order of magnitude higher than the peak of the prestellar core mass function (CMF) at $\sim 0.6\, M_\odot$ as measured with *Herschel* in nearby clouds (cite: Konyves15). This is illustrated in Fig. [9](#figs:CMF) which compares a rough estimate of the CMF in the NGC 6334 filament based on the present ALMA study to the CMF derived from *Herschel* data in the Aquila cloud. Although the two data sets differ somewhat in nature and wavelength (e.g., ALMA 3.1 mm vs. *Herschel* 160–500$\, \mu$m), cores were extracted from dust continuum maps using the same algorithm (*getsources*) in both cases. Moreover, the ALMA 3.1 mm continuum data used here are sensitive to the typical size scales of dense cores identified with *Herschel* in Gould Belt clouds ($\sim$ 0.02 pc to $\sim$ 0.1 pc – see Sect. [2](#ALMA_obs) and Fig. 7 of (cite: Konyves15)). The two CMFs shown in Fig. [9](#figs:CMF) are thus directly comparable. The difference in typical core mass between NGC 6334 and Aquila largely exceeds possible uncertainties in the dust emissivity at 3.1 mm. For instance, if the dust emissivity index $\beta = 1.5$ (instead of $\beta = 2$ as assumed in Table [\[table:cont_getsources_12m_only\]](#table:cont_getsources_12m_only) and Fig. [9](#figs:CMF)), the median core mass in NGC 6334 would still be a factor $\sim$5 higher than the CMF peak in Aquila. The median mass of observed ALMA cores essentially corresponds to the peak of the NGC 6334 CMF, and lies more than a factor of three above the estimated 90% completeness level ($2.6\, M_{\odot}$) of the present core census[^7]. While the NGC 6334 CMF shown in Fig. [9](#figs:CMF) is admittedly quite uncertain due to, for instance, low-number statistics and uncertainties in the 3.1 mm dust emissivity, we stress that it represents one of the first estimates of the CMF generated by a single, massive filament[^8] (see (cite: Takahashi13; Zhang15; Ohashi16) for examples of CMFs in somewhat less massive filaments or IRDCs with $M_{line} < 500\, M_\odot$/pc).

The median core mass derived from the ALMA data is roughly consistent with the effective critical Bonnor-Ebert mass $M_{\rm BE,eff}$ in the clumps of the filament, which can be expressed as (cite: Bonnor56):

$$\begin{equation}
M_{\rm BE,eff} = 1.18 \frac{C_{\rm s,eff}^3}{\sqrt{G^3\rho_{\rm clump}}},
\end{equation}$$

or about 7.2 $M_{\odot}$ (lower quartile: 5.0 $M_{\odot}$, upper quartile: 23.9 $M_{\odot}$). Together with the results of Sect. [4.1](#two_levels) on core grouping, this supports the view that the ALMA dense cores arise from effective Jeans-like fragmentation of the ArT$\acute{\rm e}$MiS clumps. Our results also suggest that more massive cores may form in denser/more massive filaments and are consistent with a picture in which the global prestellar CMF, and possibly the stellar initial mass function (IMF) itself, originate from the superposition of the CMFs generated by individual filaments with a whole spectrum of masses per unit length (cite: Andre+2019).

## Likelihood of the NGC 6334 filament being a system of two velocity-coherent fibers

As described in Sect. [3.3](#Sect:Filament_ID), our ALMA observations show that the $\sim \,$0.15-pc wide filament detected in the ArT$\acute{\rm e}$MiS 350 $\mu$m dust continuum map is sub-structured in five fiber-like N$_2$H$^+$(1–0) components with different velocities. The typical length of these fiber-like sub-structures is 0.5$\pm$0.4 pc and the typical velocity difference between them is 0.8 km s$^{-1}$ (standard deviation of the five N$_2$H$^+$ velocity components). The N$_2$H$^+$ velocity-coherent sub-structures may be broadly categorized into two groups. The first group consists of the N$_2$H$^+$ fiber-like sub-structures F-1 and F-2, which are also detected in other molecular line tracers of dense gas such as CH$_3$CCH, H$_2$CS, HC$_3$N, and HC$_5$N and harbor compact dense cores detected in 3.1 mm continuum emission. The second group (F-3, F-4, and F-5) is made up of velocity-coherent sub-structures detected only in N$_2$H$^+$ and which do not seem to contain dense cores. There are at least two possible explanations for these two groups. First, the physical excitation conditions in the two groups of sub-structures may differ. Second, the low velocity resolution of the current CH$_3$CCH, H$_2$CS, HC$_3$N line data (see Table [\[table:alma_obs\]](#table:alma_obs)) may prevent the identification of fiber-like features in these tracers. To test the former explanation, observations in several transitions of each species would be required to estimate the excitation temperature, column density, and chemical abundance of the various molecules. To investigate the latter effect, ALMA observations of the same tracers at higher spectral resolution would be required.

The presence of velocity-coherent fiber-like sub-structures in molecular filaments was first reported by (cite: Hacar13) in the case of the low-mass star-forming filament B211–B213 in Taurus ($d\sim$140 pc). In this filament, Hacar et al. used their friends in velocity (FIVE) algorithm to identify at least 20 velocity-coherent components in N$_2$H$^+$ and C$^{18}$O (see Table 3 in (cite: Hacar13)), which were subsequently called fibers. Since then, similar velocity-coherent components have also been detected in N$_2$H$^+$ in the IRDC

G035.39-00.33 (cite: Henshaw14), the NGC 1333 protocluster (cite: Hacar17), IRDC G034.43+00.24 (cite: Barnes18), and the Orion A integral-shaped filament (cite: Hacar18). The fiber-like sub-structures identified in NGC 1333 and Orion A may, however, differ in nature from those observed in the Taurus B211/B213 filament and in the present target NGC 6334 (cite: Clarke17). The velocity-coherent sub-structures observed in the NGC 1333 and Orion A cases are indeed well separated in the plane of the sky, while those in the Taurus and NGC 6334 filaments overlap in the sky and can mostly be distinguished in PPV space.

The typical length (0.6$\pm$0.5 pc) and velocity difference between components (0.7 km s$^{-1}$) reported by (cite: Hacar13) for the fiber-like sub-structures of the (low-mass) B211/B213 filament in Taurus are remarkably similar to the properties estimated here for the velocity-coherent sub-structures of the (high-mass) NGC 6334 filament. We further note that (cite: Hacar13) divided up their B211/B213 fibers into two groups, fertile and sterile, depending on whether they contained dense cores or not. Most of the 35 velocity-coherent sub-structures identified in B211/B213 were sterile and detected mostly in C$^{18}$O(1–0), while only 7 fiber-like sub-structures were fertile and also detected in N$_2$H$^+$(1–0). This is reminiscent of the situation found here for the NGC 6334 filament, where the two sub-structures detected in multiple dense gas tracers (F-1 and F-2) are the only two fertile fibers harboring ALMA dense cores. We argue below that these two categories of fiber-like structures differ in physical nature and possibly origin.

## Possible origin(s) of the fiber-like sub-structures

Three scenarios for the formation of velocity-coherent fiber-like sub-structures have been proposed in the literature. One is the “fray and fragment” scenario proposed by (cite: Tafalla15) and supported by (cite: Clarke17). In this scenario, a main filament forms first by collision of two supersonic turbulent gas flows. Then, the main filament fragments into an intertwined system of velocity-coherent sub-structures, due to a combination of residual turbulent motions and self-gravity. In this picture, the sub-structures are formed by fragmentation of a single filament, and the velocity-coherent sub-structures are expected to be roughly aligned with the main filament (cite: Smith14). The second scenario is the “fray and gather” scenario, in which turbulent compression first generates short, velocity-coherent filamentary structures within the parent cloud, which are then gathered by large-scale collapse of the cloud, as proposed by (cite: Smith14). In a third, alternative picture, a dense star-forming filament forms within a shell-like molecular gas layer as a result of large-scale anisotropic compression associated with, for instance, expanding bubble(s) or cloud-cloud collision (cite: Chen14; Inutsuka15; Inoue18), and subsequently grows in mass by accreting ambient gas from the surrounding shell-like structure due to its own gravitational potential (cite: Palmeirim13; Shimajiri18). This accretion process supplies gravitational energy to the dense filament, which is then converted into turbulent kinetic energy in the form of MHD waves (cite: Hennebelle13), explaining the increase in velocity dispersion with column density observed for thermally supercritical filaments (cite: Arzoumanian13). A quasi-stationary state is reached as a result of a dynamical equilibrium between accretion-driven MHD turbulence and the dissipation of this MHD turbulence owing to ion-neutral friction, possibly accounting for the roughly constant filament width of $\sim 0.1\,$pc (cite: Hennebelle13). In this “compress, accrete, and fragment” scenario, sterile fiber-like structures would correspond to portions of the accretion flow onto the central filament (cite: Clarke18), while fertile fiber-like structures would be the direct imprint of accretion-driven MHD waves within the main filament system.

While further observational constraints will be needed to fully discriminate between the above three pictures, the available constraints tend to support a scenario intermediate between the fray and fragment and the fray and gather picture, perhaps more similar to the compress, accrete, and fragment picture that we propose here. Indeed, the NGC 6334 region may be affected by cloud-cloud collision (cite: Fukui18), and some of the N$_2$H$^+$ velocity-coherent sub-structures identified here (e.g., F-5) are not aligned with, but roughly perpendicular to, the main filament traced at 350$\, \mu$m by ArTéMiS and in N$_2$H$^+$ by the two main sub-structures (F-1, F-2 in Table [1](#table:N$_2$H$^+$_filament)). Furthermore, (cite: Shimajiri18) recently reported kinematic evidence that the B211/B213 filament in Taurus may have formed inside a shell-structure resulting from large-scale compression.

# Conclusions

To study the detailed density and velocity structure of the massive filament in the NGC 6334 complex, we carried out ALMA observations at $\sim\,$$3\ensuremath{''}$ resolution in the 3.1 mm continuum and the N$_2$H$^+$(1-0), HC$_5$N(36-35), HNC(1-0), HC$_3$N(10-9), CH$_3$CCH(6-5), H$_2$CS(3-2) lines. Our main results may be summarized as follows:

1.  Both the 3.1 mm continuum emission and the N$_2$H$^+$(1–0), HC$_5$N(36–35), HC$_3$N(10–9), CH$_3$CCH(6–5), H$_2$CS(3–2) lines detected with ALMA trace the dusty filament imaged earlier at 350 $\mu$m at lower ($8\ensuremath{''}$) resolution with the ArT$\acute{\rm e}$MiS camera on APEX.

2.  We identified a total of 40 compact dense cores in the ALMA 3.1 mm continuum map, 26 of them being embedded in the NGC 6334 filament. The majority (21/26 or 80%) of these dense cores are also detected in N$_2$H$^+$(1–0) emission. The median core mass is $10^{+3}_{-2}\, M_\odot$ (lower quartile: 8 $M_{\odot}$, upper quartile: 13 $M_{\odot}$), compared to a 5$\sigma$ mass sensitivity of $2\, M_{\odot}$.

3.  The CMF derived from the sample of ALMA cores in the NGC 6334 filament (Fig. [9](#figs:CMF)) presents a peak at the median core mass of $\sim$10 $M_\odot$, which lies an order of magnitude higher than the peak of the prestellar CMF measured with *Herschel* in nearby clouds.

4.  The projected separation between ALMA dense cores is 0.03–0.1 pc, which is roughly consistent with the effective Jeans length within the filament. The ALMA cores can be grouped into seven groups, approximately corresponding to dense clumps seen in the ArT$\acute{\rm e}$MiS 350 $\mu$m continuum map. The projected separation between these groups is 0.2–0.3 pc, which roughly agrees with the characteristic spacing of four times the filament width expected from the linear fragmentation theory of nearly isothermal gas cylinders. These two distinct fragmentation scales are suggestive of two fragmentation modes: a cylindrical mode corresponding to groups of cores, and a spherical, Jeans-like mode corresponding to cores within groups.

5.  We also identified five fiber-like, velocity-coherent sub-structures within the filament by applying the *getfilaments* algorithm to the ALMA N$_2$H$^+$(1–0) data cube. The typical length of these fiber-like structures is 0.5 pc and the projected velocity difference between them is $\sim \,$0.8 km s$^{-1}$. Only two or three of these five velocity-coherent features are well aligned with the NGC 6334 filament and may represent genuine, intertwined fiber sub-structures. The other two detected velocity-coherent features may rather trace accretion flows onto the main filament.

6.  With the important exception of the typical core mass (which is here an order of magnitude higher), the fragmentation properties and velocity structure of the massive ($\ensuremath{\gtrsim} 500\, M_\odot /$pc) filament in NGC 6334 are remarkably similar to the properties observed by (cite: Hacar13) and (cite: Tafalla15) for the low-mass ($\sim 50\, M_\odot /$pc) B211/B213 filament in the Taurus cloud.

7.  As both regions appear to be affected by large-scale compressive flows, we suggest that the density and velocity sub-structure observed in the NGC 6334 and the Taurus filament may have originated through a similar mechanism, which we dub “compress, accrete, and fragment”.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01404.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada),NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work was supported by the ANR-11-BS56-010 project “STARFICH" and the European Research Council under the European Union’s Seventh Framework Programme (ERC Advanced Grant Agreement no. 291294 – ‘ORISTARS’). YS also received support from the ANR project NIKA2SKY (grant agreement ANR-15-CE31-0017). This work was supported by NAOJ ALMA Scientific Research Grant Numbers 2017-04A. We also acknowledge support from the French national programs of CNRS/INSU on stellar and ISM physics (PNPS and PCMI).

69 natexlab

(ref: Andre17) André, P. 2017, Comptes Rendus Geoscience, 349, 187

(ref: Andre+2019) André, P., Arzoumanian, D., Könyves, V., Shimajiri, Y., & Palmeirim, P. 2019, A&A, 629, L4

(ref: Andre14) André, P., Di Francesco, J., Ward-Thompson, D., et al. 2014, Protostars and Planets VI, 27

(ref: Andre10) André, P., Men’shchikov, A., Bontemps, S., et al. 2010, A&A, 518, L102

(ref: Andre16) André, P., Revéret, V., Könyves, V., et al. 2016, A&A, 592, A54

(ref: Arzoumanian11) Arzoumanian, D., André, P., Didelon, P., et al. 2011, A&A, 529, L6

(ref: Arzoumanian18) Arzoumanian, D., André, P., Könyves, V., et al. 2019, A&A, 621, A42

(ref: Arzoumanian13) Arzoumanian, D., André, P., Peretto, N., & Könyves, V. 2013, A&A, 553, A119

(ref: Barnes18) Barnes, A. T., Henshaw, J. D., Caselli, P., et al. 2018, MNRAS, 475, 5268

(ref: Belloche11) Belloche, A., Schuller, F., Parise, B., et al. 2011, A&A, 527, A145

(ref: Berry07) Berry, D. S., Reinhold, K., Jenness, T., & Economou, F. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 425

(ref: Bonnor56) Bonnor, W. B. 1956, MNRAS, 116, 351

(ref: Chen14) Chen, C.-Y. & Ostriker, E. C. 2014, ApJ, 785, 69

(ref: Clarke17) Clarke, S. D., Whitworth, A. P., Duarte-Cabral, A., & Hubber, D. A. 2017, MNRAS, 468, 2489

(ref: Clarke16) Clarke, S. D., Whitworth, A. P., & Hubber, D. A. 2016, MNRAS, 458, 319

(ref: Clarke18) Clarke, S. D., Whitworth, A. P., Spowage, R. L., et al. 2018, MNRAS, 479, 1722

(ref: Fiege00) Fiege, J. D. & Pudritz, R. E. 2000, MNRAS, 311, 85

(ref: Fukui15) Fukui, Y., Harada, R., Tokuda, K., et al. 2015, ApJL, 807, L4

(ref: Fukui18) Fukui, Y., Kohno, M., Yokoyama, K., et al. 2018, PASJ, 70, S41

(ref: Gao04) Gao, Y. & Solomon, P. M. 2004, ApJ, 606, 271

(ref: Gritschneder17) Gritschneder, M., Heigl, S., & Burkert, A. 2017, ApJ, 834, 202

(ref: Hacar17) Hacar, A., Tafalla, M., & Alves, J. 2017, A&A, 606, A123

(ref: Hacar18) Hacar, A., Tafalla, M., Forbrich, J., et al. 2018, A&A, 610, A77

(ref: Hacar13) Hacar, A., Tafalla, M., Kauffmann, J., & Kovács, A. 2013, A&A, 554, A55

(ref: Hennebelle13) Hennebelle, P. & André, P. 2013, A&A, 560, A68

(ref: Henshaw14) Henshaw, J. D., Caselli, P., Fontani, F., Jiménez-Serra, I., & Tan, J. C. 2014, MNRAS, 440, 2860

(ref: Hildebrand83) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Hill11) Hill, T., Motte, F., Didelon, P., et al. 2011, A&A, 533, A94

(ref: Inoue18) Inoue, T., Hennebelle, P., Fukui, Y., et al. 2018, PASJ, 70, S53

(ref: Inutsuka15) Inutsuka, S.-i., Inoue, T., Iwasaki, K., & Hosokawa, T. 2015, A&A, 580, A49

(ref: Inutsuka92) Inutsuka, S.-I. & Miyama, S. M. 1992, ApJ, 388, 392

(ref: Inutsuka97) Inutsuka, S.-I. & Miyama, S. M. 1997, ApJ, 480, 681

(ref: Kainulainen13) Kainulainen, J., Ragan, S. E., Henning, T., & Stutz, A. 2013, A&A, 557, A120

(ref: Kainulainen17) Kainulainen, J., Stutz, A. M., Stanke, T., et al. 2017, A&A, 600, A141

(ref: Koch15) Koch, E. W. & Rosolowsky, E. W. 2015, MNRAS, 452, 3435

(ref: Konyves19) Könyves, V., André, P., Arzoumanian, D., et al. 2019, A&A, in press (arXiv:1910.04053)

(ref: Konyves15) Könyves, V., André, P., Men’shchikov, A., et al. 2015, A&A, 584, A91

(ref: Lada12) Lada, C. J., Forbrich, J., Lombardi, M., & Alves, J. F. 2012, ApJ, 745, 190

(ref: Lada10) Lada, C. J., Lombardi, M., & Alves, J. F. 2010, ApJ, 724, 687

(ref: Lee17) Lee, Y.-N., Hennebelle, P., & Chabrier, G. 2017, ApJ, 847, 114

(ref: Longmore13) Longmore, S. N., Bally, J., Testi, L., et al. 2013, MNRAS, 429, 987

(ref: Marsh16) Marsh, K. A., Kirk, J. M., André, P., et al. 2016, MNRAS, 459, 342

(ref: Menshchikov13) Men’shchikov, A. 2013, A&A, 560, A63

(ref: Menshchikov17) Men’shchikov, A. 2017, A&A, 607, A64

(ref: Menshchikov12) Men’shchikov, A., André, P., Didelon, P., et al. 2012, A&A, 542, A81

(ref: Molinari10) Molinari, S., Swinyard, B., Bally, J., et al. 2010, A&A, 518, L100

(ref: Myers09) Myers, P. C. 2009, ApJ, 700, 1609

(ref: Ohashi16) Ohashi, S., Sanhueza, P., Chen, H.-R. V., et al. 2016, ApJ, 833, 209

(ref: Palmeirim13) Palmeirim, P., André, P., Kirk, J., et al. 2013, A&A, 550, A38

(ref: Peretto13) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, A&A, 555, A112

(ref: Persi08) Persi, P. & Tapia, M. 2008, Star Formation in NGC 6334, ed. B. Reipurth, 456

(ref: Rodriguez82) Rodriguez, L. F., Canto, J., & Moran, J. M. 1982, ApJ, 255, 103

(ref: Roy14) Roy, A., André, P., Palmeirim, P., et al. 2014, A&A, 562, A138

(ref: Russeil13) Russeil, D., Schneider, N., Anderson, L. D., et al. 2013, A&A, 554, A42

(ref: Schisano14) Schisano, E., Rygl, K. L. J., Molinari, S., et al. 2014, ApJ, 791, 27

(ref: Shimajiri17) Shimajiri, Y., André, P., Braine, J., et al. 2017, A&A, 604, A74

(ref: Shimajiri18) Shimajiri, Y., André, P., Palmeirim, P., et al. 2019, A&A, 623, A16

(ref: Shirley15) Shirley, Y. L. 2015, PASP, 127, 299

(ref: Smith14) Smith, R. J., Glover, S. C. O., & Klessen, R. S. 2014, MNRAS, 445, 2900

(ref: Stutzki90) Stutzki, J. & Guesten, R. 1990, ApJ, 356, 513

(ref: Tafalla15) Tafalla, M. & Hacar, A. 2015, A&A, 574, A104

(ref: Takahashi13) Takahashi, S., Ho, P. T. P., Teixeira, P. S., Zapata, L. A., & Su, Y.-N. 2013, ApJ, 763, 57

(ref: Teixeira16) Teixeira, P. S., Takahashi, S., Zapata, L. A., & Ho, P. T. P. 2016, A&A, 587, A47

(ref: Tige17) Tigé, J., Motte, F., Russeil, D., et al. 2017, A&A, 602, A77

(ref: Vazquez19) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, submitted (astro-ph/1903.11247)

(ref: Willis13) Willis, S., Marengo, M., Allen, L., et al. 2013, ApJ, 778, 96

(ref: Wilner94) Wilner, D. J. & Welch, W. J. 1994, ApJ, 427, 898

(ref: Zhang19) Zhang, M., Kainulainen, J., Mattern, M., Fang, M., & Henning, T. 2019, A&A, 622, A52

(ref: Zhang15) Zhang, Q., Wang, K., Lu, X., & Jiménez-Serra, I. 2015, ApJ, 804, 141

# Complementary figures

Figure [10](#fig_alma_sim) and Figure [11](#figs_otherlines) are complementary figures.

![](NGC6334_artemis_sim_comp3.png)

![](NGC6334_mom0s_b.png)

# Treatment of multiple velocity components in the N$_2$H$^+$(1–0) spectra

In order to disentangle between the N$_2$H$^+$(1–0) HFS 1 emission from the main velocity component at $V_{\rm LSR} = -6\,$km s$^{-1}$ and the HFS 2-7 emission from other velocity components, we compared the observations with synthetic N$_2$H$^+$ emission models including two velocity components along the line of the sight.

Assuming the same excitation temperature and the same linewidth for all hyperfine transitions (HFS 1-7), and Gaussian line opacity profiles as a function of velocity, the N$_2$H$^+$ temperature and the N$_2$H$^+$ opacity at velocity $V$ are given by:

$$\begin{equation}
T(V) = \frac{p_1}{p_4}\Bigl(1-e^{-\tau(V)}\Bigr),
\end{equation}$$

where

$$\begin{equation}
\tau(V) = p_4 \times \Sigma_{i=1}^{7} r_i \exp \Bigl[-4\ln 2 \Bigl(\frac{V-V_i-p_2}{p_3}\Bigr)^2 \Bigr]
\end{equation}$$

where the parameters $p_1$, $p_2$, $p_3$, $p_4$ represent $T$ $\times$ $\tau$, $V_{\rm LSR}$, linewidth, and opacity $\tau$ for the main HFS component (HFS 3)[^9].

Figure [12](#figs:N2Hp_contamination) shows model spectra in the case of two velocity components (components 1 and 2) along the line of the sight. To make it simple, we assumed $p_1$=1.0, $p_3$=1.0 km s$^{-1}$, and $p_4$=0.2 for both velocity components. We adopted a LSR velocity $p_2$=$-$2.6 km s$^{-1}$ for component 1. For component 2, we added a velocity offset of $-$4, $-$5, and $-$6 km s$^{-1}$ to $p_2$=$-$2.6 km s$^{-1}$. It can be seen that, for an offset of $-$4 km s$^{-1}$, the HFS 1 emission of component 1 is not contaminated by the HFS 2-7 emission of component 2. However, for offsets between $-$5 and $-$6 km s$^{-1}$, the HFS 1 emission of component 1 can be significantly contaminated. Thus, to avoid contamination by the HFS 2-7 emission from other velocity components, we performed a multi-component HFS fitting of the observed spectra for all pixels showing evidence of more than one velocity component along the line of sight with blueshifted velocity offsets $>$ 4 km s$^{-1}$ in magnitude. This HFS fitting with $N$ HFS components was applied to each pixel, where $N$=1, 2, or 3. A initial HFS fitting step was first performed with $N$=1. Whenever the peak signal to noise ratio (S/N) of the residual intensity was lower than 10, the fit was deemed to be acceptable and the corresponding spectrum was assumed to consist of $N=1$ Gaussian components. Whenever the peak S/N of the residuals was larger than 10, an additional HFS fitting step was performed with $N$+1 components. In practice, all pixels with detected N$_2$H$^+$ emission were fit with $N$ $\leq$ 3 components. The fit HFS 2-7 emission was then subtracted from the observed spectra. Accordingly, the resulting data cube only has significant emission from HFS 1 as shown in Fig. [13](#figs:n2h+_spectrum_removal).

![image](HFS_sim_m4.png) ![image](HFS_sim_m5.png) ![image](HFS_sim_m6.png)

![](NGC6334_N2H+_mom0_4_spec.png)

# Post-extraction selection of *getsources* results

In Sect. [3.3.1](#sect:getsources), we applied the *getsources* algorithm to extract compact sources from the ALMA 3.1 mm continuum map and N$_2$H$^+$ data cube. Here, we describe the additional criteria used to select robust compact sources from the *getsources* extraction results.

The *getsources* code identified a total of 49 compact sources in the 3.1 mm continuum map. First, we removed all sources lying closer than 3 ALMA beams from the edge of the map. With this criterion, 3 of the 49 initial sources were removed. We also removed 6 sources identified by *getsources* with a peak intensity below $<$ 5$\sigma$. As a result of these two selection steps, only 40 robust continuum sources remained.

Then, in order to investigate the potential association of these compact 3.1 mm continuum sources with compact N$_2$H$^+$ emission/sources, we also applied the *getsources* algorithm to each velocity channel map in the N$_2$H$^+$ data cube. In this case, we removed extracted sources with a peak intensity below $<$3$\sigma$ in individual channel maps. We selected only compact N$_2$H$^+$ sources detected in at least two contiguous velocity channels (where the channel width corresponds to 0.2 km s$^{-1}$) and lying within one ALMA beam ($\sim$$3\ensuremath{''}$ or $\sim$0.02 pc) of a 3.1 mm continuum source. As a result, we found that 21 (or 81%) of the 26 continuum cores are associated with compact N$_2$H$^+$ emission.

# Post-extraction selection of *getfilaments* results

In Sect. [\[sect:Post-selection\]](#sect:Post-selection), we summarized the additional criteria used to select robust filamentary (sub-)structures from the *getfilaments* results. Here, we provide more details.

Our first criterion was to impose that $>$90% of the pixels on the crest of a robust filamentary structure are detected above the 3$\sigma$ level. In Fig. [14](#figs:post_selection_1st) (a), for instance, $>$90% of the pixels on the crest of the filamentary structure are detected above 3$\sigma$. Thus, this filamentary structure would pass the first criterion. In Fig. [14](#figs:post_selection_1st) (b), $<$90% of the pixels on the crest of the filamentary structure are detected above 3$\sigma$. Thus, this structure would be regarded as a fake filamentary structure and would be removed from the detection list.

![](post_selection_1st.png)

Then, we connected filamentary structures detected in distinct velocity channels by comparing their spatial distributions in adjacent velocity-channel maps: Whenever two structures detected in adjacent velocity-channel maps overlapped over $>$60% of the pixels, they were connected together.

In practice, our step-by-step procedure to associate velocity-coherent features seen in adjacent velocity channels, from the most blueshifted to the most redshifted channel, can be described as follows. Figures [15](#figs:channel_map_subtracted) and [16](#figs:channel_map_crest) show the velocity channel maps of the compact-source-subtracted N$_{2}$H$^+$ emission cube that were used for the identification of filamentary structures with *getfilaments* and the crests of these structures

in each velocity channel (after post-extraction selection).\
In the channel map at $V_{\rm LSR}$ = $-$3.6 km s$^{-1}$, one filamentary structure is detected. This filamentary structure is labeled F-3[^10].\
In the channel maps at $V_{\rm LSR}$ = $-$3.4 km s$^{-1}$ and $-$3.2 km s$^{-1}$, three filamentary structures are detected in both channels. The spatial distributions of the detected filamentary structures are consistent in both channels. The filamentary structure whose distribution coincides with that of F-3 at $-$3.6 km s$^{-1}$ is identified as F-3. The other two filamentary structures are labeled F-4 and F-1.\
In the channel map at $V_{\rm LSR}$ = $-$3.0 km s$^{-1}$, three discrete filaments are detected. The spatial distribution of one part of the northernmost filamentary structure coincides with the distribution of F-3 at $-$3.6 to $-$3.2 km s$^{-1}$. Thus, this filamentary structure is identified as being F-3. The spatial distribution of another one overlaps that of F-1 at $-$3.4 km s$^{-1}$. The spatial distribution of the third structure coincides with the distribution of one of the filamentary structures detected in the next velocity channel ($-$2.8 km s$^{-1}$). Thus, these features are identified as being the same filamentary structure (F-3).\
In the channel maps for $V_{\rm LSR}$ = $-$2.8 and $-$2.6 km s$^{-1}$, two filamentary structures corresponding to F-3 and F-1 are detected. At $-$2.6 km s$^{-1}$, the filamentary structure shown as a black curve was removed as it is only detected in this channel.\
In the channel map at $V_{\rm LSR}$ = $-$2.4 km s$^{-1}$, three filamentary structures are detected. One of them was removed since it is only detected in this channel. The other two discrete structures are identified as F-1 since their distributions

overlap with that of F-1 at $-$2.6 km s$^{-1}$.\
In the channel map at $V_{\rm LSR}$ = $-$2.2 km s$^{-1}$, four components can be identified. Two discrete structures correspond to F-1 since their distributions overlap with that of F-1 at $-$2.4 km s$^{-1}$. The filamentary structure labeled as F-3 is roughly perpendicular to the other filamentary structures. The spatial distribution of the structure labeled F-2 partly overlaps with the distribution of F-1 at $-$2.4 km s$^{-1}$. Thus, there is a possibility that F-1 and F-2 are actually part of the same physical structure. But the northern portion of F-2 lies slightly to the west of F-1, while the southern part of F-2 lies to the east of F-1. Moreover, at positions where F-1 and F-2 overlap in the plane of the sky, the N$_2$H$^+$ spectra clearly exhibit distinct velocity components \[see, e.g., positions (c) and (d) in Fig. [6](#figs:n2h+_fiber_spectrum)\]. Therefore, F-1 and F-2 seem to be distinct velocity-coherent features.\
In the channel maps at $V_{\rm LSR}$ = $-$2.0 to $-$1.6 km s$^{-1}$, two filamentary structures (F-5 and F-2) can be identified. But F-2 lies slightly to the west of F-1 in the northern part (DEC \> -35:47:30), while the southern part of F-2 lies to the east of F-1 in the southern part (DEC \< -35:47:30). At $-$1.8 km s$^{-1}$, one structure was removed since it is detected in only one channel.

![](channel_no_compact.png)

![](crest_channel.jpg)

# Origin of the highly blueshifted N$_2$H$^+$ blobs

We detected highly blue-shifted N$_2$H$^+$ blobs, with LSR velocities up to $-$12 km s$^{-1}$ compared to the filament systemic velocity of $-$2.6 km s$^{-1}$ (see Sect. [3.2.3](#Sect:velo_structure)). There are at least two possibilities for their origin.

The first possibility is that the highly blue-shifted N$_2$H$^+$ blobs are associated with cloud-cloud collision. (cite: Fukui18) found the presence of highly blue-shifted emission up to $-$20 km s$^{-1}$ on $\sim \,$10-pc scales in their wide-field NANTEN2 $^{12}$CO (1–0, 2–1) data around Galactic longitude of $l =\ $351.1–351.5 deg which includes our ALMA observed area. They suggested that a large-scale cloud-cloud collision occurred a few Myr ago and produced this highly blue-shifted $^{12}$CO emission in the NGC 6334 complex.

The second possibility is that the highly blue-shifted N$_2$H$^+$ emission blobs are associated with the expanding shell produced by source D. As described in Sect. [3.1](#result:cont), the distribution of the 3.1 mm continuum emission is shaped like a shell around source D. Most of the highly blue-shifted N$_2$H$^+$ blobs are distributed on the outskirts of this shell-like structure. While the northern part of the NGC 6334 filament is seen in absorption in the *Spitzer* 8 $\mu$m

map, such absorption is not seen in the southern part (around the shell-like structure). This suggests that the southern part of the NGC 6334 filament is in the back of the exciting star (source D). If the N$_2$H$^+$ blobs were associated with the shell-like structure, their velocity would be expected to be redshifted compared to the surrounding gas material. This is not consistent with the fact that the N$_2$H$^+$ blobs are blueshifted.

We conclude that the highly blueshifted N$_2$H$^+$ blobs are more likely related to the cloud-cloud collision scenario proposed by (cite: Fukui18).

![](NGC6334_N2Hp_blue_artemis_cont.png)

# Comparison between GAUSSCLUMPS, *getsources*, and REINOHLD extractions of clumps in the ArTéMiS map

As described in Sect. [4.1](#two_levels), we applied GAUSSCLUMPS to identify seven clumps in the ArT$\acute{\rm e}$MiS 350$\mu$m map.

To investigate the robustness of this identification, we also applied the *getsources* algorithm, already used to identify compact sources in the ALMA 3.1 mm continuum map (see Sect. [3.3.1](#sect:getsources)),

as well as the REINOLD algorithm, available as a python package (*pycupid*; (cite: Berry07)).

REINOLD

marks the edges of emission clumps that have shell or ring shapes. Then, all pixels within each ring or shell are assigned to be a single clump. Here, we adopted the following REINOLD parameters: RMS = 0.08 Jy beam$^{-1}$, FLATSLOPE = 1$\sigma$, FWHMBEAM = beam size, MAXBAD= 0.05, MINLEN = beam size/pixel size, THRESH=10, and MINPIX = beam size. Seven clumps were identified in the main filament. Figure [18](#figs:comp_gaussclump_reinhold) compares the distributions of the clumps identified with GAUSSCLUMPS, *getsources*, and REINHOLD. The *getsources* algorithm identified seven sources within the main filament. Five of these seven *getsources* objects coincide with a clump found with GAUSSCLUMPS. REINHOLD also identified seven clumps within the main filament. One clump identified with GAUSSCLUMPS is not identified with REINHOLD, but is identified with *getsources*. All clumps identified with GAUSSCLUMPS are also identified with *getsources* and/or REINHOLD. Thus, we conclude that the seven clumps identified with GAUSSCLUMPS are robust.

![](NGC6334_artemis_reinhold_getsources.png)

[^1]: The critical line mass is $M_{\rm line,crit} = 2\,c_{\rm s}^2$/G, where $c_{\rm s}$ is the isothermal sound speed, corresponding to $M_{\rm line,crit} \approx  33\, M_{\odot}$/pc for a molecular gas temperature $T$ = 20 K.

[^2]: We used the 12m-only instead of the 12m$+$7m image as the sensitivity of the data is better for the detection of compact ($< 0.1\,$pc) sources (cf. Table [\[table:cont_getsources_12m_only\]](#table:cont_getsources_12m_only)).

[^3]: We used the 12m$+$7m data to estimate the integrated flux densities and masses of the sources detected in the 12m-only continuum map, in order to avoid missing-flux problems due to interferometric filtering of large scales as much as possible. For four weak unresolved sources, undetected above the $3\sigma$ level in the 12m$+$7m map, the 12m-only data were used instead (cf. Table [\[table:cont_getsources_12m_only\]](#table:cont_getsources_12m_only)).

[^4]: The median mass of all 40 compact continuum sources is 9.4$^{+3.4}_{-1.9}$ $M_{\odot}$ (lower quartile: 7.5 $M_{\odot}$, upper quartile: 12.8 $M_{\odot}$) and the median volume-averaged density 1.4$\times$10$^{7}$ cm$^{-3}$ (lower quartile: 0.8$\times$10$^{7}$ cm$^{-3}$, upper quartile: 2.0$\times$10$^{7}$ cm$^{-3}$).

[^5]: As only a small ($\geq 5$) number of velocity-coherent features appeared to be present in our N$_2$H$^+$ data cube (see Table [1](#table:N$_2$H$^+$_filament)) and we had no experience with the FIVE method developed by (cite: Hacar13), we preferred to follow a procedure based on channel-by-channel *getfilaments* extractions and careful visual inspection of the data cube (see Appendix [9](#Sect:getfilament_post_selection_detail)).

[^6]: The area within $\pm$0.25 pc of the filament crest extends well into the power-law wing of the filament radial profile (see Fig. 3a of (cite: Andre16)) and includes the bulk of the ArTéMiS 350 $\mu$m emission from the filament (see Fig. [8](#figs:NNS_result)).

[^7]: The 90% completeness level was estimated to be $2.6\, M_{\odot}$ assuming Gaussian statistics and a 5$\sigma$ peak-flux detection threshold of 0.7 mJy/beam. Under these assumptions, $\sim$10% of sources with intrinsic peak fluxes at the 6.3$\sigma$ level of $\sim 0.9$ mJy/beam will have measured peak fluxes below 5$\sigma$. Thus, one can expect the 90% completeness level to roughly correspond to the 6.3$\sigma$ level (cite: Belloche11).

[^8]: Despite the presence of fiber-like sub-structures, we regard the prominent filamentary structure seen in the ArTéMiS 350 $\mu$m continuum map and the ALMA N$_2$H$^+$(1–0) integrated intensity map (cf. Fig. [1](#figs)) as a single filament, comparable to the many filaments detected with *Herschel* in nearby clouds (cite: Arzoumanian11; Arzoumanian18) and to the B211/B213 filament in Taurus (cite: Palmeirim13; Hacar13).

[^9]: See <https://www.iram.fr/IRAMFR/GILDAS/doc/pdf/class.pdf> for details.

[^10]: In Table [1](#table:N$_2$H$^+$_filament), the identified fiber-like features are listed by decreasing order of length.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "getsources on the 12m-only continuum map, with post-selection (remove sources within 3 beams of the edge and below 5σ)",
  "failed_quote": "After running *getsources* on the 12m-only data and applying post-extraction selection criteria (see Appendix A), we identified a total of 40 candidate compact 3.1 mm continuum sources."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Cross-check with N2H+ channel maps",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "2D Gaussian fitting",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "HFS model with same Tex and linewidth for all hyperfine components",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Synthetic two-component spectra",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Visual inspection of PPV",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[4].validation.evidence[0]",
  "value": "Comparison with getsources and REINHOLD; random distributions",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[5].assumptions[0].evidence[0]",
  "value": "Tk = 20 K",
  "failed_quote": "(no quote given)"
 }
]
```
