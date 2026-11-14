# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...696A...1H\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Resolved Gas Temperatures and ratios in SVS13A from ALMA Observations of and .

Multiple systems are common in field stars, and the frequency is found to be higher in early evolutionary stages. Thus, the study of young multiple systems during the embedded stages is key to have a comprehensive understanding of star formation. In particular, how material accretes from the large-scale envelope into the inner region and how this flow interacts with the system physically and chemically has not yet been well characterized observationally.

We aim to provide a snapshot of the forming protobinary system SVS13A, consisting of VLA4A and VLA4B. This includes clear pictures of its kinematic structures, physical conditions, and chemical properties.

We conducted ALMA observations toward SVS13A targeting and J=12-11 K-ladder line emission with a high spatial resolution of $\sim30$ au at a spectral resolution of $\sim0.08$ km s$^{-1}$

We perform LTE radiative transfer models to fit the spectral features of the line emission. We find the two-layer LTE radiative model including dust absorption is essential to interpret the and line emission. We identify two major and four small kinematic components, and derive their physical and chemical properties.

We find a possible infalling signature toward the bursting secondary source VLA4A, which may be fed by an infalling streamer from the large-scale envelope. The mechanical heating in the binary system, as well as the infalling shocked gas, likely play a role in the thermal structure of the protobinary system. By accumulating mass from the streamer, the system might have experienced a gravitationally unstable phase before the accretion outburst. Finally, the derived / ratio is lower than the canonical ratio in the ISM and is different between VLA4A and VLA4B.

# Introduction

Observations reveal that the frequency of multiple stellar systems increases during earlier evolutionary stages, with a multiplicity rate of 0.57 for Class 0 and 0.23 for Class I (cite: to18; of23). Multiple systems are also commonly observed among field stars (cite: to14).

Thus, to understand the most common pathway of star formation, it is essential to study multiple systems at an early stage (e.g., (cite: mu24)).

In contrast to the classical picture that stars form through isotropic collapse of dense cores (cite: sh77; te98), recent molecular line observations reveal non-axisymmetric accretion in progress (cite: pi23). This infalling material is distributed in spatially elongated yet narrow structures, named “infalling streamers”, that have been seen at different evolutionary stages (cite: ye19; pi20; al20; gi21; mu22b; ca21; ga22; th22; va22; fl23; gu24; va24). These infalling streamers can singificantly contribute to the mass accretion rate from the core to disk, $\sim$10$^{-6}$ M$_\odot$ yr$^{-1}$ (cite: va22). Infalling streamers are also seen in numerical simulation such as (cite: ku17). In addition, infalling streamers might play a crucial role in changing the physical structures and chemical compositions in the inner region (cite: ga22; po24). The complex organic molecule (COM) , with its K-ladder transitions, is widely used as a thermometer toward hot dense regions. It is more commonly seen in high-mass star-forming regions but is also found in low-mass star-forming regions (cite: bo07; bi08; be18; lo18; ca18; be20; ya21).

SVS13A is a well studied protobinary system located in the NGC1333 cluster in the Perseus Molecular Cloud ($d=$293 pc, (cite: or18)). It is a Class I close binary consisting of VLA4A and VLA4B (or Per-emb-44B and 44A) with a separation of $0.3\ensuremath{''}$ ($\sim$90 au) based on continuum emission (cite: an04; to18; se18). (cite: di22) derive the total mass of the binary to be 1.0$\pm$0.4 $M_\odot$ given the proper motion of the binary orbit. The individual masses of the protostars are estimated as 0.27$\pm$0.10 $M_\odot$ for VLA4A (secondary) and 0.60$\pm$0.20 $M_\odot$ for VLA4B (primary). The SVS13A binary system has a high bolometric luminosity of $L_{\rm bol}=45.3~L_\odot$ likely because the secondary VLA4A is in an outburst phase (cite: hs19). In addition, (cite: hs23) found a large-scale ($\sim$700 au) candidate streamer connected with the dusty spiral linked to VLA4A. This streamer is possibly infalling, funneling material to the binary system with a mass infall rate $>1.4\times10^{-6} M_\odot$ yr$^{-1}$. and the isotopologues and have been previously detected toward SVS13A (cite: bi19; hs23; bi22a). However, the emission had not been spatially resolved. Observations of O-bearing COMs at $\sim$300 au resolution in (cite: hs24) indicated that multiple structures should exist at tens of au scales based on multiple velocity components.

In this work, we present new Atacama Large Millimeter ter/submillimeter Array (ALMA) molecular line observations of and towards SVS13A. We resolve the emission from the COM species and down to 30 au (0.1 arcsecond). The high angular- and spectral-resolution data resolved the line emission, tracing the disks or rotating envelope around the protobinary VLA4A and VLA4B. In Section [2](#sec:observation), we present the data and imaging process. The results are reported in Section [3](#sec:result). In Section [4](#sec:analysis), we discuss the LTE radiative transfer fitting and identify the kinematic components. The discussions and conclusions are in Sections [5](#sec:discussion) and [6](#sec:summary), respectively.

![](Spectra_of_VLA4.pdf)

# Observations

## ALMA observation

We conducted ALMA observations in June 2023 with three executions with the project ID 2022.1.00479. In these executions, 43, 44, 45 antennas were used. PWV among the observations were from 0.4 to 0.55 mm. With the ALMA C-7 configuration, the baselines were $91-8282$ m ($\sim$$65-6000$ k$\lambda$) at 220 GHz, recovering scales from 0.1 to 1.2 arcsec ($\sim$30$-$360 au). The total on-source (SVS13A) time was 144 min toward the phase center at International Celestial Reference System (ICRS) $\alpha$ = 3$^{\rm h}$29$^{\rm m}$ 03$^{\rm s}$.74, $\delta$ = 31$^{\rm d}$16$^{\rm m}$03$^{\rm s}$.8. The three executions shared the same bandpass and flux calibrator as J0423-0120, while the phase calibrator either J0328+3139 or J0336-3218 depending on the execution.

The observations were designed to observe multiple chemical and kinematic tracers toward SVS13A such that multiple high-resolution spectral windows were placed accompanied with one continuum window at 234.5 GHz with 1.875 GHz bandwidth and 488 kHz (0.6 km s$^{-1}$) channel width (band 6, (cite: ed04)). In this paper, we present the J=12-11 window which covers a wavelength ranging from 220.52 GHz to 220.75 GHz with a channel width of 61 kHz (0.08 km s$^{-1}$). We use the pipeline calibrated data restored using CASA 6.4.12 (cite: casa). Imaging was done using the `tclean` package with a robust weighting of 0.5, resulting in a beam size of $0.11\ensuremath{''}\times0.08\ensuremath{''}$ ($\sim$30 au) for the cube. This image cube has an rms noise level of 1.7 mJy beam$^{-1}$ (4.7 K) at the spectral resolution of 0.08 km s$^{-1}$.

## STATCONT for continuum subtraction

Many spectral lines adding up to a ’forest’ features have been seen in high-mass star forming regions (cite: sa18), making the determination of the continuum level difficult. This may also happen in low-mass star forming regions for the chemically-rich sources, e.g., hot corinos (cite: ce04), especially with high-sensitivity data. SVS13A, with high luminosity (45.3 L$_\odot$), has plenty of line features already known in the literature (cite: bi19; bi22; di22; hs23), see also Figure [1](#fig:spe_vla).

We use STATCONT (cite: sa18) to determine the continuum level and find the line-free channels. STATCONT performs continuum subtraction in image domain pixel by pixel, and provides a continuum-subtracted cube and continuum image as outputs. We used the default sigma-clipping algorithm, which removes the line-emitting channels by iteratively measuring the median and standard deviation in a histogram of spectral points. As a result, we obtained the continuum image from the continuum window and the line image cube from the window.

# Results

## Continuum emission

Figure [1](#fig:spe_vla) shows the continuum image as contours. The binary components VLA4A as the secondary and VLA4B as the primary are well resolved and two spirals are seen, consistent with previous observations (cite: to18; di22). The continuum emission from the secondary (VLA4A) is more extended than that of the primary. However, VLA4A peak brightness is lower (70 K) than the primary VLA4B (90K). The relative brightness is consistent with that at 0.9 mm, 260 K for VLA4A and 430 K for VLA4B (cite: di22). It is likely that the inner 30 au are optically thick for both VLA4A and VLA4B at 0.9 mm, as seen in other compact binary system (e.g., (cite: ma22)). In this case, the difference could indicate either a lower dust temperature for the secondary or higher amounts of material therein, leading to higher levels of self-obscuration (e.g., (cite: ga18)). VLA4A likely is the more active source during an accretion outburst (cite: hs19), also given its connection to the potential infalling streamer (the spiral) and the spectral features to be discussed below.

##  and 

and J $=12-11$ emission are spatially resolved toward SVS13A. The K-ladder is detected in the observing windows with K $=0-7$ for and K $=0-5$ for (Figure [1](#fig:spe_vla)). Given the forest of lines, a particular line can be severely contaminated by other molecules especially for . emission is relatively strong but is still partially affected by a few bright lines such as and (see Figure 2 in (cite: hs23)). Using the broad wavelength coverage provided by the large program PROtostars & DIsks: Global Evolution (PRODIGE) using NOEMA, (cite: hs23; hs24) thoroughly identify the molecular lines by performing LTE modeling for each molecule with multiple transitions. However, there are still unidentified lines in the spectral window presented here (Figure [1](#fig:spe_vla)).

In Figures [2](#fig:12_mom0) and [3](#fig:13_mom0) we show the integrated intensity maps from three transitions of and that cover different energy levels and suffer less from contamination. For , it is clear that the emission peaks towards VLA 4A while for , the emission peaks in the region between the protostars. In addition, ring-like emission surrounding VLA4B from and is revealed especially for the lines with lower upper energy levels, for which also the emission is the brightest. Such a ring structure has been found in other sources such as V883 Ori (cite: le19; ya24). This can be interpreted either as due to the high optical depths of the dust or due to destruction of COMs in the inner disk via strong UV or X-ray radiation (cite: ga06; ob09). An extreme case for this absorption is found in NGC1333 IRAS4A1 with absorption line features (cite: sa19). For SVS13A VLA4B we favor the high dust optical depth scenario because 1) VLA4B indeed has stronger continuum emission than VLA4A, and 2) the UV radiation is likely more powerful in VLA4A as the source is undergoing an accretion burst (cite: hs19).

Although the line emission is dominated by VLA4A, the emission peak is located in between VLA4A and VLA4B. It is unclear at the current stage if this is the material interacting between the binary system (cite: jo22). This is consistent with the result from (cite: hs23); they speculate that and emission comes from different regions or layers due to the different optical depths. With the resolved map, we can clearly see the spatial difference even in the optically thin emission, i.e., K=7 from . In other words, these results suggest a spatially inhomogeneous isotopologue ratio of / toward the protobinary SVS13A.

![](CH3CN_mom0_k037.pdf)

![](CH313CN_mom0_k125.pdf)

# Analysis

## LTE model setup

We apply local thermal equilibrium (LTE) modeling to the and lines for the whole map (pixel by pixel). A spatial mask is taken using a threshold of S/N\>12 from the K=3 integrated intensity map (Figure [4](#fig:spe_multi)). To avoid the contamination from other lines, a selected mask at specific velocities is provided manually (such as the blue-shifted side in K=6 or K=3 components). The LTE model is constructed based on CASSIS and XCLASS manuals (cite: va15; mo17). The line data are taken from CDMS (cite: mu05; en16) and JPL (cite: pi98), whereas the original catalogues are from (cite: mu09; mu15). The details are in Appendix [7.1](#app:lte).

## Radiative transfer model

We conduct LTE models throughout the emitting regions pixel by pixel, adopting a one- or two-layer model. Here we introduce these two models and present the model selection in section [4.3](#sec:clustering).

### One-layer model

We first conduct a one velocity component LTE modeling which takes into account dust absorption. This approach assumes that the dust and gas are co-located instead of assuming the dust as a background to the gas (see (cite: sa19; ro21; bo21; ya24)), and that the dust and gas temperature are the same, $T_{\rm ex}$. The continuum subtracted spectrum is thus $$\begin{equation}
    I_{\nu} (v)= [J_{\nu}(T_{\rm ex})-J_\nu(T_{\rm bg})]  (1-e^{-\tau (v)}) e^{-\tau_{\rm dust}},
\label{eq:rad}
\end{equation}$$ where $T_{\rm bg}=2.7$ K, $\tau(v)$ is the line optical depth, and $\tau_{\rm dust}$ is the dust optical depth. The detailed derivation can be found in Appendix [7.2](#app:lte_one). As a result, we have a scale factor of $\exp{(-\tau_{\rm dust})}$. This plays the same role as in (cite: hs23; hs24), where a beam filling factor was used to scale the emission. At the edge of the emitting area, a beam might cover a partially line-free region where a beam-filling factor would be needed so that the $\tau$ might be overestimated. We chose a high S/N= 12 as a mask in the integrated intensity map of K$=$3 to avoid this. We note that an LTE model without considering dust absorption was also tried but failed to interpret the line spectrum: without the scaling factor $e^{-\tau_{\rm dust}}$, the model naturally would underestimate the column density with a small $\tau$ in order to fit the absolute brightness of the observed spectrum, resulting an inconsistent line ratio.

![](Spectra_of_2layer.pdf)

The spectra in Figures [1](#fig:spe_vla) (position VLA4B) and [4](#fig:spe_multi) (positions 2 and 5) show the one-layer model fit toward these positions. Figure [5](#fig:para_one) shows the maps of the six free parameters from the fit. The temperature peaks toward VLA4A. We note that the partition function $Q(T)$ is provided by CDMS up to 900 K, so the boundary of the fitting is set to 800 K. The derived $\tau_{\rm dust}$ from the line fit is quite similar to the continuum emission, supporting that the dust optical depths are reasonably estimated. The peak $\tau\sim2.5$ suggests that only $\sim10$% of line emission might escape from these regions. There are also regions with $\tau<1$, suggesting that the continuum emission is not optically thick through the entire line emitting region. Thus, it is reasonable to assume coupling of gas and dust rather than an optically thick continuum emission as background. column density is higher toward VLA4A as expected. The $V_{\rm lsr}$ and FWHM maps are in general similar to the average-velocity maps and moment 2 maps from previous high-resolution COM maps (cite: di22; bi22). The isotopologue ratio / is taken as $\frac{N_{\rm tot,\ch{CH3CN}}}{N_{\rm tot,\ch{CH3^{13}CN}}}$ (see equations [\[eq:tau_v\]](#eq:tau_v) and [\[eq:tau\]](#eq:tau)). As a result, the spatially inhomogeneous distribution is presented.

![](oneGaussian_para.pdf)

### Two-layer model

Although the LTE model with dust absorption can interpret the relative intensities of the K-ladder transitions, the high spectral resolution data reveal double-peak features in some areas (Figure [4](#fig:spe_multi)). (cite: hs24) have conducted multi-component LTE fitting of O-bearing COMs toward SVS13A, decomposing different kinematic components. In that work, the kinematic components are assumed spatially separated within the NOEMA beam. However, with the spatially-resolved ALMA map, the double peak spectral profiles are still present in particular regions, indicating two components along the line of sight. Thus, we conduct the two-layer LTE model to interpret these spectra. Each layer has its own excitation temperature ($T_{\rm ex}$), dust optical depth ($\tau_{\rm dust}$), column density ($N_{\rm tot}$), central velocity ($V_{\rm LSR}$), linewidth ($\Delta V$), and isotopologue ratio (/); twelve free parameters are included. The continuum subtracted spectrum is $$\begin{equation}
\label{eq:2_layer}
\begin{aligned}
    I_{\nu} (v) = 
        &\, [J_{\nu}(T_{\rm ex, 1})-J_\nu(T_{\rm ex, 2})]  (1-e^{-\tau_1 (v)}) e^{-\tau_{\rm dust, 1}} \\
        +&\, [J_{\nu}(T_{\rm ex, 2})-J_\nu(T_{\rm bg})]  (1-e^{-[\tau_1 (v)+\tau_2 (v)]}) e^{-(\tau_{\rm dust, 1}+\tau_{\rm dust, 2})},
\end{aligned}
\end{equation}$$ and the detailed derivation is in Appendix [7.3](#app:lte_two). This equation can be considered as a variation from the two-layer model in (cite: my96) and its family (cite: le01; di01; de05; ka12). The original two-layer model is applied to infall motion at molecular core where the dust absorption might be negligible. Equation [\[eq:2_layer\]](#eq:2_layer) will converge to the original two-layer model when $\tau_{\rm dust,1}=0$ and $\tau_{\rm dust,2}=0$. In addition, the original two-layer model assumes two uniform layers with the same optical depth $\tau(v)$ (see equation [\[eq:tau_v\]](#eq:tau_v)) as symmetrically infalling. Here the LTE model requires number densities of population for energy levels (defining $\tau$) to follow the Boltzmann distribution with the given $T_{\rm ex}$ (equations [\[eq:tau\]](#eq:tau) and [\[eq:boltzmann\]](#eq:boltzmann)). We find that a symmetric model, i.e., the same velocity dispersion $\sigma$ and $N_{\rm tot}$ for the two layers, is insufficient for some regions, for example, position 4 in Figure [4](#fig:spe_multi) with linewidths of 0.9 and 1.5 km s$^{-1}$ for the first and the second layer, respectively. It is noteworthy that this 2-layer model will also converge to the gas-dust decoupling model when $\tau_{\rm dust,1}=0$ (gas front layer) and $\tau_2(v)=0$ (dust rear layer) as (cite: ro21). Clearly, if we have an optically thick dust continuum as the rear layer ($\tau_{\rm dust,2}\gg1$), only the first term in equation [\[eq:2_layer\]](#eq:2_layer) is left with $T_{\rm ex,2}$ representing the background temperature of the dust layer.

We perform the fit throughout the line emitting region (Figure [4](#fig:spe_multi)). Such a fit with many free parameters is difficult to converge and suffers from degeneracy (see Appendix [8](#app:degeneracy)). To address these issues, good initial guesses are required. We first perform Markov Chain Monte Carlo (MCMC) sampling of a grid of positions in the emitting regions (in total 41 positions with gaps around emission of roughly beam size). We tune the sampling boundary (prior range) of the MCMC fitting and find the most reasonable solution. For example, the fitting results should not show dramatic difference in between two neighboring positions. These solutions at each points in the grid are then interpolated to a map of initial guesses for the fitting. Figure [4](#fig:spe_multi) shows the spectra of a few selected positions for which the best-fit from MCMC sampling are plotted (with one- or two-layer model in use, see section [4.3](#sec:clustering)).

![](Cluster_paper.pdf)

![](Infall.pdf)

## Clustering into kinematic components

Here we discuss how we select the one- or two-layer model in each pixel and cluster them into kinematic components. We use a criterion for the two layer-model: the difference of the centroid velocities ($V_{\rm in}=V_{\rm LSR,1}-V_{\rm LSR,2}$) is larger than the velocity dispersions of both layers, $\sigma_1$ and $\sigma_2$. This threshold set a strict situation for using two-layer model only when the double-peak is clearly seen in the position. For example, in Figure [4](#fig:spe_multi) position 4 and 5 using one-layer model, the spectral profiles in fact shows blue or red asymmetry which is considered as an indicator of infall or expansion motions in cloud cores (cite: ma97; ta98; le01; em09; pi12; hs15; re22). Although the two-layer model better reproduces the spectra profile with lower reduced $\chi^2$ and Akaike information criterion (AIC, see appendix [8](#app:degeneracy)), the one-layer model is chosen in case where no clear double peak is presented. It is possible that the two layers are blended with similar centroid velocities or broad linewidths. For example in Figure 7 in (cite: bi17) with isotopologues toward SVS13A, a broken power law is seen in the rotation diagram, decomposing components without spatially or spectrally resolved data. However, in our case with only eight energy levels from J=12-11 K=0-7 (in the rotational diagram), we decide to be more conservative, using one-layer model for positions without a clear double peak. More importantly, to study the kinematic structure, these regions with small relative velocity between two layers (see also Figure [11](#fig:aic) right panel) will not be decomposed or extracted as a new kinematic component by the clustering algorithms in the position-position diagram.

After the model selection, we have a final map at each position containing one or two velocity components (from the one- or two-layer model respectively). Figure [6](#fig:3d_cluster) shows the position-position-velocity diagram (PPV), because it can better decompose the distribution than P-V diagrams. We use the clustering algorithm DBSCAN (cite: es96; va23; gi24) with `eps=0.3` and `min_samples=10`, clustering these points into six groups. For discarded points, we simply use the one-layer model at such positions, so that they go back to the major kinematic component I (Figure [6](#fig:3d_cluster)).

As a result, two major kinematic components I and II, and four small components III-VI are identified (Figure [6](#fig:3d_cluster)). Table [\[tab:para\]](#tab:para) lists their physical parameters. Because the two-layer model in fact determines the front layer and the rear layer, i.e., equation [\[eq:2_layer\]](#eq:2_layer), the infall or expansion of the two layers can be obtained. A positive value of $V_{\rm in}$ in Table [\[tab:para\]](#tab:para) indicate expanding motion while a negative one indicates an infalling motion (cite: my96; ma97). However, there is a caveat to determine this given the degeneracy of the model. For example, although the double peak profiles with blue excess are clearly seen toward the region with component II as infalling signatures, we can find another fit for expanding motion due to the asymmetric layers (see Appendix [8](#app:degeneracy) for the degeneracy). To completely break the degeneracy, multi-band observations would help with measuring dust opacity at different wavelengths (for example, optically thick dust emission as (cite: pi12)). Finally the absolute value of the relative velocity of each component with respect to component I is presented in Figure [7](#fig:infall). Figure [8](#fig:para_multi) shows the best-fit parameters of all six components and Table [\[tab:para\]](#tab:para) lists them.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | size | $T_{\rm ex}$ | $\tau_{\rm dust}$ | log$_{10}(N_{\rm tot})$ | $V_{\rm LSR}$ | $V_{\rm in}$ $^a$ | $\Delta V$ | / |
| component | (au$^2$) | \(K\) |  | (cm$^{-2}$) | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) |  |
| one-layer | 27660 | 210.6$^{+72.7}_{-42.1}$ | 1.1$^{+0.3}_{-0.3}$ | 16.4$^{+0.6}_{-0.4}$ | 8.0$^{+0.8}_{-0.6}$ | \- | 1.0$^{+0.2}_{-0.2}$ | 19.8$^{+6.9}_{-5.9}$ |
| I | 27660 | 205.5$^{+79.1}_{-43.1}$ | 0.9$^{+0.4}_{-0.3}$ | 16.3$^{+0.5}_{-0.4}$ | 7.9$^{+0.8}_{-0.7}$ | \- | 0.9$^{+0.2}_{-0.2}$ | 19.5$^{+8.6}_{-5.6}$ |
| II | 7282 | 178.9$^{+73.7}_{-47.0}$ | 0.4$^{+0.7}_{-0.4}$ | 15.8$^{+0.6}_{-0.3}$ | 9.0$^{+0.2}_{-0.1}$ | -2.1$^{+0.3}_{-0.3}$ | 0.8$^{+0.2}_{-0.2}$ | 38.6$^{+34.0}_{-11.9}$ |
| III | 1139 | 105.8$^{+38.6}_{-6.6}$ | 0.4$^{+0.3}_{-0.4}$ | 15.6$^{+0.1}_{-0.1}$ | 10.6$^{+0.4}_{-0.2}$ | -2.2$^{+0.1}_{-0.2}$ | 0.9$^{+0.1}_{-0.1}$ | $>$80.0 |
| IV | 1274 | 77.6$^{+31.5}_{-24.7}$ | 0.0$^{+0.1}_{-0.0}$ | 15.3$^{+0.3}_{-0.2}$ | 6.2$^{+0.1}_{-0.1}$ | 1.9$^{+0.1}_{-0.1}$ | 0.5$^{+0.1}_{-0.1}$ | 68.5$^{+11.5}_{-38.3}$ |
| V | 869 | 139.9$^{+18.2}_{-33.8}$ | 0.0$^{+0.3}_{-0.0}$ | 15.3$^{+0.0}_{-0.1}$ | 9.0$^{+0.1}_{-0.1}$ | 1.1$^{+0.2}_{-0.2}$ | 0.3$^{+0.0}_{-0.0}$ | 42.5$^{+37.5}_{-15.1}$ |
| VI | 270 | 121.1$^{+13.9}_{-11.8}$ | 0.0$^{+0.0}_{-0.0}$ | 15.3$^{+0.1}_{-0.1}$ | 7.5$^{+0.1}_{-0.1}$ | 1.3$^{+0.0}_{-0.1}$ | 0.8$^{+0.1}_{-0.1}$ | 15.0$^{+5.9}_{-3.4}$ |

\
Table notes: The numbers in the upper and lower limits are taken from the distributions in quantiles of 0.25 and 0.75.\

![](Components_para.pdf)

![](ToomeQ.pdf)

# Discussion

## Kinematic structures

The velocity map, panel (d) of Figure [5](#fig:para_one), in general reveals similar structures to average-velocity maps from literature (cite: di22; bi22). However, our two-layer model aims at ambitiously studying the motion in the line of sight of the system (Figure [8](#fig:para_multi)). The velocity gradient along west-east of the major component I is larger than that in the one-layer model because at the west side, the red-shifted emission is decomposed to the component II.

Figure [7](#fig:infall) shows the absolute value of the relative velocity $|\delta V_{\rm relative}|$ of these components with respect to the main component I. A major portion of Component II is around VLA4A, perhaps also affected or induced by the dusty spiral which is considered as a possible infalling streamer (cite: hs23).

Figure [7](#fig:infall) reveals a velocity pattern ($|\delta V_{\rm relative}|$) of component II relative to I with a radial symmetric structure centered to the west of VLA4A. We note again that, although the two-layer model has defined front and rear layers with different velocities, these two layers can frequently be hard to disentangle (see Appendix [8](#app:degeneracy)). Thus, we are not able to determine if it is an infall or outward motion only from the spectra. However, the majority of component II shows blue excess favor infall motion. In addition, the radial symmetric structure in Figure [7](#fig:infall), i.e., the relative velocity between component I and II, implies this traces an infall motion centering around VLA4A. If this is the case, it might help understanding the nature of the possible infalling streamer (cite: hs23). In this case, the secondary source VLA4A is fed by the infalling streamer during an accretion outburst. A caveat is that, the possible infalling streamer found by (cite: hs23) via DCN has a landing velocity at the blue-shifted emission $7-8$ km s$^{-1}$ similar to from the spiral (cite: to18). This is different from the component II with velocity around 9 km s$^{-1}$ (Table [\[tab:para\]](#tab:para) and Figure [8](#fig:para_multi)). This implies that the component II from the emission is not directly associated with the dusty spiral.

Regarding the rotation, (cite: di22) found a disk surrounding VLA4A and a circumbinary disk via ethylene glycol and CS observations, respectively. The $V_{\rm lsr}$ maps from our LTE fitting, i.e., panel (d) in Figures [5](#fig:para_one), are broadly similar to the mean-velocity map in (cite: di22). The S-shape pattern in between the blue- and red-shifted emission can be explained by the simultaneous presence of infall and rotation (cite: fl23). We looked at position-velocity (PV) diagrams (Figures [12](#fig:12_pv) and [13](#fig:13_pv)), where the position axis goes from west to east and passes through A and B. In the PV-diagrams, likely only the blue-shifted emission in the west of the Keplerian rotation is seen via and , as in component I (Figure [8](#fig:para_multi)). Figure [9](#fig:Q) compares the velocity pattern of component I with thin disk models given the parameters from (cite: di22). Consistent with the literature, the model can broadly describe the VLA4A disk while in VLA4B there is no detection of a gas disk (see Figures [12](#fig:12_pv) and [13](#fig:13_pv)), for which the inclination angle is obtained from dust continuum. This makes component II interesting in that it likely is associated with infalling materials, but not directly to the infalling streamer or the continuum spiral.

## Physical conditions

Figures [5](#fig:para_one) and [8](#fig:para_multi) show the gas temperature structures from the K-ladder. The temperature map of the major component I is similar to that of the one-layer model. Both components I and II have a peak temperature toward VLA4A. This could also explain the high column density of at VLA4A, where molecules are sublimated from the dust mantles. The component II is relatively cooler than component I (Table [\[tab:para\]](#tab:para)). As the component I is likely associated with the rotating disk or envelope around VLA4A (Figures [6](#fig:3d_cluster) and [12](#fig:12_pv)), the component II might trace materials induced by the possible infalling streamer.

Radiation from central protostars is usually considered as the main heating source, which is used to determine the temperature from previous modeling works (cite: ra17; hs18; hs19; mu22a). Toward SVS13A, although the temperature is mostly determined by the protostellar radiation, it is unlikely the only factor in order to reproduce the asymmetric structure. First, toward VLA4B, the gas temperature in its west side is clearly higher than that in the east. Likely, the circumbinary material in between VLA4A and VLA4B is relatively warmer. More interestingly, the temperature is relatively high along the spiral, the possible infalling streamer (Figures [5](#fig:para_one) and [8](#fig:para_multi)). Mechanical heating has been suggested to interpret such asymmetric temperature structures as in IRAS16293-2422 (cite: ma22). If the dusty spiral traces a streamer accreting onto the protostellar or circumbinary disk, it can induce shocked gas and heat up the material. For example, shocked gas traced via SO has been detected toward the landing position of an infalling streamer in HL Tau (cite: ga22) and in Per-emb-50 (cite: va22). High-spatial and high-spectral resolution observations of SO might help disentangle the shocked gas induced in SVS13A.

## Toomre Q analysis

Disk fragmentation is considered as a formation process of close binary systems (cite: of23). The Toomre Q parameter is widely used to test if a disk is gravitationally unstable as $$\begin{equation}
\label{eq:toomre}
Q=\frac{c_S \Omega}{\pi G \Sigma},
\end{equation}$$ where $c_S$ is the sound speed, $\Omega$ is the angular velocity, $G$ is the gravitational constant, and $\Sigma$ is the disk surface density (cite: to64). Here we use the $T_{\rm ex}$ from the one-layer model to derive the sound speed (Figure [5](#fig:para_one), see also (cite: ah23)). We use $\tau$ map (Figure [5](#fig:para_one)) to estimate $\Sigma$ assuming the dust opacity $\kappa=0.899$ cm$^{2}$ g$^{-1}$ at 1.3 mm (cite: os94; to18), a gas to dust mass ratio of 100, with inclination correction from (cite: di22). It is noteworthy that the dust opacity can bring an uncertainty of a few (cite: ti18). To estimate the angular velocity, we compare the velocity map from Figure [8](#fig:para_multi) and thin disk models for VLA4A and VLA4B given the star masses and inclination angle from (cite: di22) (Figure [9](#fig:Q)). We note here the component I in Figure [8](#fig:para_multi) is used because the one-layer velocity map (Figure [5](#fig:para_one)) includes the contribution from component II with the red-shifted emission in the east (Figures [8](#fig:para_multi) and [12](#fig:12_pv)). By assuming Keplerian rotation, we obtain $Q$ maps for VLA4A and VLA4B (Figure [9](#fig:Q)).

The Q parameter maps show that the disks are in general stable near the protostars (Q $>1$). However, VLA4A is likely undergoing an accretion outburst, suggesting that the high temperature is temporary. If we assume $T\propto L^{0.2}$ (cite: go74) and the luminosity was 100 times less during the quiescent phase, the $c_s$ as well as the $Q$ parameter should be a factor of $\sim$0.6 of the current values. This makes more area in the disk gravitationally unstable so that the disk fragmentation might occur during the quiescent phase causing the binary formation or triggering the accretion burst (cite: bo08; vo05; vo10; of09; ma11). Also, surrounding VLA4A is the potential infalling pattern (Figure [7](#fig:infall)) and the possible infalling streamer (cite: hs23) which could be in part responsible for the accretion burst via gravitational instability (cite: pi23).

## / spatial distribution

The / ratio has been measured toward different protostellar systems (cite: bu24) in prep., and is usually found to be lower relative to the canonical ratio in the local ISM /$\simeq$68 (cite: mi05). It is also found to vary at different distances from the central source (cite: yo22; yo24; be24) Toward SVS13A, (cite: hs23) find a low value of 16 as they suggest that the and might trace different regions or layers toward SVS13A. This is supported by the integrated intensity maps of Figures [2](#fig:12_mom0) and [3](#fig:13_mom0). In other words, the isotopologue ratios can vary across SVS13A. With the LTE model (Figures [5](#fig:para_one) and [8](#fig:para_multi)), we find low values in comparison with the canonical one throughout the maps except for component III and IV, but with large error (Table [\[tab:para\]](#tab:para)). Other than these two components, the / ratios $\sim$$20-40$ are in general lower than the canonical value of 68. Interestingly, it is even lower around the primary source VLA4B from both one- and two-layer model (Figures [5](#fig:para_one) and [8](#fig:para_multi)). This suggests a chemical segregation between VLA4A and VLA4B as reported by (cite: bi22) with other COMs. Furthermore, as the secondary VLA4A is likely connected to the dusty spiral, possibly tracing an infalling streamer (cite: hs23), this hints that the infalling streamer might affect the chemistry in the inner region. For example, via , an infalling streamer is suggested to deliver chemical fresh materials from the cores into the disks in Per-emb-2 (cite: pi20).

# Summary

We present and observations toward SVS13A using ALMA with a spatial resolution of $\sim23\times32$ au and spectral resolution of $\sim$0.08 km s$^{-1}$. We conduct LTE radiative transfer fitting of line emission. Our main findings are summarized:

1.  The and integrated intensity are tracing material near both protostars as well as material along the direction connecting both protostars. However, the is the brightest towards the secondary protostar VLA4A while its isotopologue is the brightest in between the two protostars. In addition, towards the primary VLA4B, the emission from both and shows a dip at the location of the continuum peak resulting in a ring-like morphology. This can be interpreted as dust absorption.

2.  We modeled the lines from / considering the optical depth of the dust (i.e, dust absorption), assuming that the dust and gas are co-spatial and have the same temperature. We inferred temperatures $\ensuremath{\gtrsim}$100 K in the line-emitting region, with the highest temperatures towards VLA4A (the secondary, $>$500 K), the region between the protostars ($\sim$300 K), and that along the possible infalling streamer ($\sim$250 K). The inhomogenous distribution of the temperature suggests that in addition to irradiation from the outbursting protostar VLA4A, there is also heating from shocks possibly induced by an infalling streamer.

3.  Toward some regions with resolved double-peak line profiles, we conduct two-layer LTE radiative transfer modeling to reproduce the features. This enables us to identify two major kinematic components I and II. While the component I is likely associated with rotating disk or envelope around VLA4A and VLA4B, the component II might be associated with the dusty spiral structure, a possible infalling streamer, around VLA4A. The velocities of this material differs from the main component by 1 to 3 km s$^{-1}$ and could be connected to the infalling material towards the secondary VLA4A which is undergoing an accretion burst.

4.  Using the individual protostellar masses, the measured gas temperature for and dust optical depth at 1.3 mm, we derive maps of the Toomre Q parameter around the protostars. We find broadly gravitationally stable disks (or rotating materials) with the current conditions. However, in the past, previous to the accretion outburst conditions experiences by VLA4A, the disk was cooled down and massive enough in some parts being gravitationally unstable. It could have fragmented to trigger the binary formation or accretion bursts.

5.  The / ratio is lower than the canonical / ratio in the ISM over the whole region, but with variations across the map. The ratio towards the primary VLA4B, as well as for the material between the protostars, is around 10. On the other hand, the western part of the emission which includes VLA4A shows values between 15 and 50. Streaming material towards VLA4A could be the origin of this difference.

# Acknowledgements

We thank Dr. Naomi Hirano for the insight discussion. T.-H. H., J.E.P., P.C., M.T.V, and M.J.M. acknowledge the support by the Max Planck Society. T.-H. H. is supported by Taiwan Astronomical Research Alliance (TARA) with National Science and Technology Council (NSTC 113-2740-M-008-005). TARA is committed to advancing astronomy in Taiwan and paving the way for the establishment of a national observatory. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.00479.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

101 natexlab

(ref: ah23) Ahmadi, A., Beuther, H., Bosco, F., et al. 2023, A&A, 677, A171

(ref: al20) Alves, F. O., Cleeves, L. I., Girart, J. M., et al. 2020, ApJL, 904, L6

(ref: an04) Anglada, G., Rodrı́guez, L. F., Osorio, M., et al. 2004, ApJL, 605, L137

(ref: astropy) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: aplpy) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: be20) Belloche, A., Maury, A. J., Maret, S., et al. 2020, A&A, 635, A198

(ref: be24) Bergin, E. A., Bosman, A., Teague, R., et al. 2024, ApJ, 965, 147

(ref: be18) Bergner, J. B., Guzmán, V. G., Öberg, K. I., Loomis, R. A., & Pegues, J. 2018, ApJ, 857, 69

(ref: bi22a) Bianchi, E., Ceccarelli, C., Codella, C., et al. 2022a, A&A, 662, A103

(ref: bi17) Bianchi, E., Codella, C., Ceccarelli, C., et al. 2017, MNRAS, 467, 3011

(ref: bi19) Bianchi, E., Codella, C., Ceccarelli, C., et al. 2019, MNRAS, 483, 1850

(ref: bi22) Bianchi, E., López-Sepulcre, A., Ceccarelli, C., et al. 2022b, ApJL, 928, L3

(ref: ti18) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45

(ref: bi08) Bisschop, S. E., Jørgensen, J. K., Bourke, T. L., Bottinelli, S., & van Dishoeck, E. F. 2008, A&A, 488, 959

(ref: bo08) Boley, A. C. & Durisen, R. H. 2008, ApJ, 685, 1193

(ref: bo21) Bosman, A. D., Bergin, E. A., Loomis, R. A., et al. 2021, ApJS, 257, 15

(ref: bo07) Bottinelli, S., Ceccarelli, C., Williams, J. P., & Lefloch, B. 2007, A&A, 463, 601

(ref: bu24) Busch, L. 2024, in in prep.

(ref: ca21) Cabedo, V., Maury, A., Girart, J. M., & Padovani, M. 2021, A&A, 653, A166

(ref: ca18) Calcutt, H., Jørgensen, J. K., Müller, H. S. P., et al. 2018, A&A, 616, A90

(ref: casa) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: ce04) Ceccarelli, C. 2004, in Astronomical Society of the Pacific Conference Series, Vol. 323, Star Formation in the Interstellar Medium: In Honor of David Hollenbach, ed. D. Johnstone, F. C. Adams, D. N. C. Lin, D. A. Neufeeld, & E. C. Ostriker, 195

(ref: de05) De Vries, C. H. & Myers, P. C. 2005, ApJ, 620, 800

(ref: di01) Di Francesco, J., Myers, P. C., Wilner, D. J., Ohashi, N., & Mardones, D. 2001, ApJ, 562, 770

(ref: di22) Diaz-Rodriguez, A. K., Anglada, G., Blázquez-Calero, G., et al. 2022, ApJ, 930, 91

(ref: ed04) Ediss, G. A., Carter, M., Cheng, J., et al. 2004, in Fifteenth International Symposium on Space Terahertz Technology, ed. G. Narayanan, 181–188

(ref: em09) Emprechtinger, M., Caselli, P., Volgenau, N. H., Stutzki, J., & Wiedner, M. C. 2009, A&A, 493, 89

(ref: en16) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: es96) Ester, M., Kriegel, H.-P., Sander, J., & Xu, X. 1996, in Second International Conference on Knowledge Discovery and Data Mining (KDD’96). Proceedings of a conference held August 2-4, ed. D. W. Pfitzner & J. K. Salmon, 226–331

(ref: fl23) Flores, C., Ohashi, N., Tobin, J. J., et al. 2023, ApJ, 958, 98

(ref: ga18) Galván-Madrid, R., Liu, H. B., Izquierdo, A. F., et al. 2018, ApJ, 868, 39

(ref: ga06) Garrod, R. T. & Herbst, E. 2006, A&A, 457, 927

(ref: ga22) Garufi, A., Dominik, C., Ginski, C., et al. 2022, A&A, 658, A137

(ref: gi24) Gieser, C., Pineda, J. E., Segura-Cox, D. M., et al. 2024, arXiv e-prints, arXiv:2410.18941

(ref: gi21) Ginski, C., Facchini, S., Huang, J., et al. 2021, ApJL, 908, L25

(ref: go74) Goldreich, P. & Kwan, J. 1974, ApJ, 189, 441

(ref: gu24) Gupta, A., Miotello, A., Williams, J. P., et al. 2024, A&A, 683, A133

(ref: hs15) Hsieh, T.-H., Lai, S.-P., Belloche, A., Wyrowski, F., & Hung, C.-L. 2015, ApJ, 802, 126

(ref: hs19) Hsieh, T.-H., Murillo, N. M., Belloche, A., et al. 2019, ApJ, 884, 149

(ref: hs18) Hsieh, T.-H., Murillo, N. M., Belloche, A., et al. 2018, ApJ, 854, 15

(ref: hs24) Hsieh, T. H., Pineda, J. E., Segura-Cox, D. M., et al. 2024, A&A, 686, A289

(ref: hs23) Hsieh, T. H., Segura-Cox, D. M., Pineda, J. E., et al. 2023, A&A, 669, A137

(ref: matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90

(ref: jo22) Jørgensen, J. K., Kuruwita, R. L., Harsono, D., et al. 2022, Nature, 606, 272

(ref: ka12) Kang, S.-J. & Kerton, C. R. 2012, ApJ, 759, 13

(ref: ko22) Koposov, S., Speagle, J., Barbary, K., et al. 2022, joshspeagle/dynesty: v2.0.3

(ref: ku17) Kuffmeier, M., Haugbølle, T., & Nordlund, Å. 2017, ApJ, 846, 7

(ref: le01) Lee, C. W., Myers, P. C., & Tafalla, M. 2001, ApJS, 136, 703

(ref: le19) Lee, J.-E., Lee, S., Baek, G., et al. 2019, Nature Astronomy, 3, 314

(ref: lo18) Loomis, R. A., Cleeves, L. I., Öberg, K. I., et al. 2018, ApJ, 859, 131

(ref: ma11) Machida, M. N., Inutsuka, S.-i., & Matsumoto, T. 2011, ApJ, 729, 42

(ref: ma97) Mardones, D., Myers, P. C., Tafalla, M., et al. 1997, ApJ, 489, 719

(ref: ma22) Maureira, M. J., Gong, M., Pineda, J. E., et al. 2022, ApJL, 941, L23

(ref: mi05) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126

(ref: mo17) Möller, T., Endres, C., & Schilke, P. 2017, A&A, 598, A7

(ref: mu15) Müller, H. S. P., Brown, L. R., Drouin, B. J., et al. 2015, Journal of Molecular Spectroscopy, 312, 22

(ref: mu09) Müller, H. S. P., Drouin, B. J., & Pearson, J. C. 2009, A&A, 506, 1487

(ref: mu05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: mu24) Murillo, N. M., Fuchs, C. M., Harsono, D., et al. 2024, A&A, 689, A267

(ref: mu22b) Murillo, N. M., Hsieh, T. H., & Walsh, C. 2022a, A&A, 665, A68

(ref: mu22a) Murillo, N. M., van Dishoeck, E. F., Hacar, A., Harsono, D., & Jørgensen, J. K. 2022b, A&A, 658, A53

(ref: my96) Myers, P. C., Mardones, D., Tafalla, M., Williams, J. P., & Wilner, D. J. 1996, ApJL, 465, L133

(ref: ob09) Öberg, K. I., Garrod, R. T., van Dishoeck, E. F., & Linnartz, H. 2009, A&A, 504, 891

(ref: of09) Offner, S. S. R., Klein, R. I., McKee, C. F., & Krumholz, M. R. 2009, ApJ, 703, 131

(ref: of23) Offner, S. S. R., Moe, M., Kratter, K. M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 275

(ref: or18) Ortiz-León, G. N., Loinard, L., Dzib, S. A., et al. 2018, ApJ, 865, 73

(ref: os94) Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943

(ref: pi98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: pi23) Pineda, J. E., Arzoumanian, D., Andre, P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 233

(ref: pi12) Pineda, J. E., Maury, A. J., Fuller, G. A., et al. 2012, A&A, 544, L7

(ref: pi20) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, 4, 1158

(ref: po24) Podio, L., Ceccarelli, C., Codella, C., et al. 2024, A&A, 688, L22

(ref: ra17) Rab, C., Elbakyan, V., Vorobyov, E., et al. 2017, A&A, 604, A15

(ref: re22) Redaelli, E., Chacón-Tanarro, A., Caselli, P., et al. 2022, ApJ, 941, 168

(ref: ro21) Rosotti, G. P., Ilee, J. D., Facchini, S., et al. 2021, MNRAS, 501, 3427

(ref: sa19) Sahu, D., Liu, S.-Y., Su, Y.-N., et al. 2019, ApJ, 872, 196

(ref: sa18) Sánchez-Monge, Á., Schilke, P., Ginsburg, A., Cesaroni, R., & Schmiedeke, A. 2018, A&A, 609, A101

(ref: se18) Segura-Cox, D. M., Looney, L. W., Tobin, J. J., et al. 2018, ApJ, 866, 161

(ref: sh77) Shu, F. H. 1977, ApJ, 214, 488

(ref: sk04) Skilling, J. 2004, in American Institute of Physics Conference Series, Vol. 735, Bayesian Inference and Maximum Entropy Methods in Science and Engineering: 24th International Workshop on Bayesian Inference and Maximum Entropy Methods in Science and Engineering, ed. R. Fischer, R. Preuss, & U. V. Toussaint (AIP), 395–405

(ref: so20) Sokolov, V., Pineda, J. E., Buchner, J., & Caselli, P. 2020, ApJL, 892, L32

(ref: sp20) Speagle, J. S. 2020, MNRAS, 493, 3132

(ref: ta98) Tafalla, M., Mardones, D., Myers, P. C., et al. 1998, ApJ, 504, 900

(ref: te98) Terebey, S., Shu, F. H., & Cassen, P. 1984, ApJ, 286, 529

(ref: th22) Thieme, T. J., Lai, S.-P., Lin, S.-J., et al. 2022, ApJ, 925, 32

(ref: to18) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2018, ApJ, 867, 43

(ref: to14) Tokovinin, A. 2014, AJ, 147, 87

(ref: to64) Toomre, A. 1964, ApJ, 139, 1217

(ref: va24) Valdivia-Mena, M. T., Pineda, J. E., Caselli, P., et al. 2024, A&A, 687, A71

(ref: va22) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2022, A&A, 667, A12

(ref: va23) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2023, A&A, 677, A92

(ref: numpy) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22

(ref: va15) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. M., & Boiziot, M. 2015, in SF2A-2015: Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics, 313–316

(ref: scipy) Virtanen, P., Gommers, R., Burovski, E., et al. 2020, scipy/scipy: SciPy 1.5.3

(ref: vo05) Vorobyov, E. I. & Basu, S. 2005, ApJL, 633, L137

(ref: vo10) Vorobyov, E. I. & Basu, S. 2010, ApJ, 719, 1896

(ref: ya24) Yamato, Y., Notsu, S., Aikawa, Y., et al. 2024, AJ, 167, 66

(ref: ya21) Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, ApJ, 910, 20

(ref: ye19) Yen, H.-W., Gu, P.-G., Hirano, N., et al. 2019, ApJ, 880, 69

(ref: yo24) Yoshida, T. C., Nomura, H., Furuya, K., et al. 2024, ApJ, 966, 63

(ref: yo22) Yoshida, T. C., Nomura, H., Furuya, K., Tsukagoshi, T., & Lee, S. 2022, ApJ, 932, 126

*Software:* Numpy ((cite: numpy)), Scipy ((cite: scipy)), APLpy ((cite: aplpy)), Matplotlib ((cite: matplotlib)), Astropy ((cite: astropy)) CASA ((cite: casa))

# LTE Radiative transfer models

## Boltzmann distribution and optical depth

LTE-radiative transfer model are constructed to fit the line profiles of the J=12-11, K=0-7 and J=12-11, K=0-5 transitions given the observed wavelength coverage. This is done following the XCLASS and CASSIS manuals[^1] (cite: mo17) and (cite: va15).

The LTE $\tau (v)$ as a Gaussian function of velocity ($v$) was first constructed: $$\begin{equation}
    \tau (v)=\sum_{\rm i} \tau_{\rm i,peak} \exp(-\frac{(v-V_{\rm LSR})^2}{2\sigma^2}),
    \label{eq:tau_v}
\end{equation}$$ where $i$ is the transition including and , $\sigma$ is the velocity dispersion ($\sigma\sim\frac{\Delta V}{2\sqrt{2\ln{2}}}$), $V_{\rm LSR}$ is the centroid velocity, $$\begin{equation}
    \tau_{\rm peak}=\frac{A_{\rm ul} c^3}{8\pi \nu^3 \Delta V \frac{(\pi ln2)^{1/2}}{2}} N_{\rm u} (e^{h\nu/kT_{\rm ex}}-1),
    \label{eq:tau}
\end{equation}$$ for which $A_{\rm ul}$ is the Einstein coefficient, c is light speed, and $\nu$ is the rest frequency of the transition from the Cologne Database for Molecular Spectroscopy (CDMS[^2]; (cite: mu05; en16)). $N_{\rm u}$ is the column density at the upper energy state as $$\begin{equation}
\label{eq:boltzmann}
    N_{\rm u}=N_{\rm tot}\frac{g_{\rm u}}{Q(T_{\rm ex})} e^{-E_{\rm u}/kT_{\rm ex}},\qquad
    g_{\rm u} =
    \begin{cases} 
    50 & \text{if } K = 0, 1, 2 \ldots \\
    100 & \text{if } K=3n
    \end{cases}
\end{equation}$$ where $g_{\rm u}$ is the degeneracy, $Q(T_{\rm ex})$ is the partition function, and $E_{\rm u}$ is the upper energy level. We note here the partition function $Q(T)$ of is taken from due to the lack of the vibrational correction. This causes at most $0.06\%$ error at $T<500$ K ((cite: hs23)).

## Radiative transfer model with dust optical depth

Here we discuss the contribution of dust absorption in the LTE radiative transfer model. Under the LTE assumption with the same gas temperature and dust temperature ($T_{\rm ex}=T_{\rm dust}$), the gas and dust are assumed to share the same space. The continuum-subtracted line emission with dust absorption can be expressed as: $$\begin{equation}
    \begin{aligned}
    \Delta I_{\nu} (v) 
        = &\, I_{\rm line} (v) - I_{\rm dust}    \\
        = &\, [J_{\nu}(T_{\rm bg})e^{-[\tau (v)+\tau_{\rm dust}]} + J_{\nu}(T_{\rm ex})(1-e^{-[\tau (v)+\tau_{\rm dust}]})] \\
        &\, - [J_{\nu}(T_{\rm bg})e^{-\tau_{\rm dust}} + J_{\nu}(T_{\rm ex})(1-e^{-\tau_{\rm dust}})] \\
        = &\, [J_{\nu}(T_{\rm ex})-J_\nu(T_{\rm bg})]  (1-e^{-\tau (v)}) e^{-\tau_{\rm dust}}. 
    \end{aligned}
\label{eq:rad_one}
\end{equation}$$ Here, in an optically thin case, $\tau_{\rm dust}$ is 0, i.e., $e^{-\tau_{\rm dust}}$ is $\sim$1, so that the equation reverts to the commonly used equation. Here $\tau (v)$ contains the following parameters: linewidth $\sigma$ and central velocity $V_{\rm LSR}$ as Gaussian profiles while the peak is determined by the column density $N_{\rm tot}$ and $T_{\rm ex}$ (equations [\[eq:tau_v\]](#eq:tau_v), [\[eq:tau\]](#eq:tau), and [\[eq:boltzmann\]](#eq:boltzmann)). Together with the isotopologue ratio $N_{\rm tot, \ch{CH3CN}}/N_{\rm tot, \ch{CH3^{13}CN}}$, six free parameters are included: excitation temperature ($T_{\rm ex}$), column density ($N_{\rm tot, \ch{CH3CN}}$), dust optical depth ($\tau_{\rm dust}$), central velocity ($V_{\rm LSR}$), linewidth ($\Delta V$), and isotopologue ratio ($N_{\rm tot, \ch{CH3CN}}/N_{\rm tot, \ch{CH3^{13}CN}}$).

## Two layer LTE radiative transfer model

The two layer model simply adds one more layer with independent $T_{\rm ex}$, $\tau (v)$, and $\tau_{\rm dust}$, so that: $$\begin{equation}
    \begin{aligned}
    \Delta I_{\nu} (v) 
        = &\, I_{\rm line} (v) - I_{\rm dust}\\
        = &\, J_{\nu}(T_{\rm bg})e^{-[\tau_1 (v)+\tau_{\rm dust,1} +\tau_2 (v) + \tau_{\rm dust,2}]} \\
            &\, + J_{\nu}(T_{\rm ex,1})(1-e^{-[\tau_1 (v)+\tau_{\rm dust,1}]}) \\
            &\, + J_{\nu}(T_{\rm ex,2})(1-e^{-[\tau_2 (v)+\tau_{\rm dust,2}]}) e^{-[\tau_1 (v)+\tau_{\rm dust,1}]}\\
            &\, - [J_{\nu}(T_{\rm bg})e^{-(\tau_{\rm dust,1}+\tau_{\rm dust,2})} + J_{\nu}(T_{\rm ex,1})(1-e^{-\tau_{\rm dust,1}}) + J_{\nu}(T_{\rm ex,2})(1-e^{-\tau_{\rm dust,2}}) e^{-\tau_{\rm dust,1}}]\\
        = &\, [J_{\nu}(T_{\rm ex, 1})-J_\nu(T_{\rm ex, 2})]  (1-e^{-\tau_1 (v)}) e^{-\tau_{\rm dust, 1}} \\
        &\, +[J_{\nu}(T_{\rm ex, 2})-J_\nu(T_{\rm bg})]  (1-e^{-[\tau_1 (v)+\tau_2 (v)]}) e^{-(\tau_{\rm dust, 1}+\tau_{\rm dust, 2})}.
    \end{aligned}
\label{eq:rad_two}
\end{equation}$$ The layer one with $T_{\rm ex,1}$, $\tau_1 (v)$, and $\tau_{\rm dust,1}$ is thus the front layer while the layer two with $T_{\rm ex,2}$, $\tau_2 (v)$, and $\tau_{\rm dust,2}$ is the rear layer. Each of $\tau_1 (v)$ and $\tau_2 (v)$ thus is described by excitation temperature ($T_{\rm ex}$), column density ($N_{\rm tot, \ch{CH3CN}}$), central velocity ($V_{\rm LSR}$), and linewidth ($\Delta V$) (see section [7.1](#app:lte)). Again, with an isotopologue ratio ($N_{\rm tot, \ch{CH3CN}}/N_{\rm tot, \ch{CH3^{13}CN}}$) for each component, the two layer model has in total $6\times2=12$ free parameters. Here again, if $\tau_{\rm dust,1}=0$ and $\tau_{\rm dust,2}=0$, the equation [\[eq:rad_two\]](#eq:rad_two) can be rewritten to the widely used two-layer model, i.e. $\Delta I_{\nu} (v) = J_{\nu}(T_{\rm ex,1}) [1-e^{-\tau_1(v)}] +J_{\nu}(T_{\rm ex,2}) [1-e^{-\tau_2(v)}]e^{-\tau_1(v)} - J_{\nu}(T_{\rm bg})[1-e^{-\tau_1(v)-\tau_2(v)}]$ for molecular cores (i.e., Equation 2 in (cite: my96)). On the other hand, if the first layer (front-layer) is optically thin ($\tau_{\rm dust,2}\sim0$) and the second layer (rear-layer) is optically thick ($\tau_{\rm dust,2}\gg1$), the equation is similar to that with gas-dust decoupled model $\Delta I_{\nu} (v) = [J_{\nu}(T_{\rm ex, 1})-J_\nu(T_{\rm ex, 2})]  (1-e^{-\tau_1 (v)})$ with $T_{\rm ex,2}$ representing the dust temperature of the optically thick continuum background.

# Degeneracy and model selection

Given the 12 free parameters in the two-layer model, degeneracy can occur during fitting. We focus on the determination of the front and rear layers. Taking an extreme example as position 3 in Figure [4](#fig:spe_multi), with the clearly seen double peak, the front and rear layers only have small overlap in velocity. In such a case, the fit with front layer in red-shifted and rear layer in the blue-shifted indicates an infall motion. However, the fitting can also converge to a solution with the opposite result as outward motion depending on the initial guess for the fitting or the prior set in MCMC sampling. As a result, the relative velocity can be obtained but it is difficult to determine an infalling or outward motion. We note that for the classical two-layer model in (cite: my96) or its families (see also appendix [7.3](#app:lte_two)), the infall signature is obtained because it assumes symmetric structures, i.e., the two layers share the same $\tau$ and linewidth. In our case, the two layers are clearly not symmetric, for example toward position 6 (Figure [4](#fig:spe_multi)), the linewidths are quite different (0.9 and 1.5 km s$^{-1}$) in the two layers. In this work, we set the initial guess to fit the spectra with blue excess using infall and with red excess using outward motion as the classical picture.

![](Corner_position33.pdf)

![](AIC.pdf)

Figure [10](#fig:corner) shows the corner plot from the MCMC sampling toward position 1 in Figure [4](#fig:spe_multi). A correlation between the $\tau_{\rm dust, 1}$ and $\tau_{\rm dust, 2}$ from the two layers is shown. This might be expected given the equation [\[eq:2_layer\]](#eq:2_layer) or [\[eq:rad_two\]](#eq:rad_two). Figure [8](#fig:para_multi) second column with $\tau_{\rm dust}$ maps also gives a hint for this degeneracy. Likely, the model shows degeneracy between $\tau_{\rm dust, 1}$ and $\tau_{\rm dust, 2}$ while the summation of these two values might be reasonable. To overcome this problem requires observations at longer wavelengths of with optically thin dust continuum. Also, for the region with optically thin line emission, i.e., $(1-e^{-\tau(v)})\approx{\tau(v)}$, the constraint for $\tau_{\rm dust}$ can be more difficult given equation [\[eq:rad_one\]](#eq:rad_one). To break these degeneracies, multiple wavelength observations from optically thin to thick continuum with might help with understanding the dust properties. This could eventually distinguish between infall and outward motions in the spectra.

Figure [10](#fig:corner) reveals another unconstrained parameter in the isotopologue ratio of / for which the sample reaches its upper boundary of 80 in the prior. This is also expected toward the region with low S/N in (this example is position 1 in Figure [4](#fig:spe_multi)). Thanks to the high-sensitivity data, it is not a problem in the regions with robust detection (Figure [3](#fig:13_mom0)).

Here we discuss our selection of model for each pixel with either one- or two-layer. Figure [11](#fig:aic) (left panel) shows the Akaike information criterion (AIC) map ($AIC = 2{\rm k}+\chi^2+C$ where k is the degree of freedom, $\chi^2$ is the chi-squared, and C is a constant). The low $\Delta AIC$ would be in favor for two-layer model. In general, two-layer model works better, especially for the component II region. In addition, we have also calculated Bayesian evidence with nested sampling algorithm (cite: sk04) using Dynesty (cite: sp20; ko22) toward the 41 grid positions (Figure [11](#fig:aic) middle panel); Bayesian evidence has been used to make model selection in line modeling (cite: so20). The result is roughly consistent with AIC method favor two-layer model especially for the component II region. However, toward some regions, the relative velocity of the two layers can be very small. Kinematically, this region will not be decomposed to an additional component when clustering in the position-position velocity space (section [4.3](#sec:clustering)). Thus, for these regions without a clear double-peak revealed, we decide to be conservative and use the one-layer model. As a result, we use the criteria that $|\delta V_{\rm relative}|$ is larger than the velocity dispersion from both layers.

# Position-Velocity diagram

Figures [12](#fig:12_pv) and [13](#fig:13_pv) show the position-velocity diagram of three selected transitions from and , respectively. The PV-cut is taken along the west to east along VLA4A and VLA4B. The Keplerian rotation curves are plotted given the parameters from (cite: di22) (see also Figure [9](#fig:Q)). We note that since the gas disk is not found in (cite: di22), the inclination of the Keplerian curve is taken from the dust disk.

![](PV_diagram_k037.pdf)

![](PV_diagram_k125.pdf)

[^1]: http://cassis.irap.omp.eu/docs/RadiativeTransfer.pdf

[^2]: https://cdms.astro.uni-koeln.de/cdms/portal/

</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[1]",
  "value": "ICRS 03h29m03.74s, +31d16m03.8s (phase center)",
  "failed_quote": "ICRS $\\alpha$ = 3$^{\\rm h}$29$^{\\rm m}$ 03$^{\\rm s}$.74, $\\delta$ = 31$^{\\rm d}$16$^{\\rm m}$03$^{\\rm s}$.8"
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[1]",
  "value": "d = 293 pc",
  "failed_quote": "ICRS $\\alpha$ = 3$^{\\rm h}$29$^{\\rm m}$ 03$^{\\rm s}$.74, $\\delta$ = 31$^{\\rm d}$16$^{\\rm m}$03$^{\\rm s}$.8"
 },
 {
  "path": "science.targets[0].distance_source.evidence[1]",
  "value": "Ortiz-León et al. 2018 (cite: or18)",
  "failed_quote": "ICRS $\\alpha$ = 3$^{\\rm h}$29$^{\\rm m}$ 03$^{\\rm s}$.74, $\\delta$ = 31$^{\\rm d}$16$^{\\rm m}$03$^{\\rm s}$.8"
 }
]
```
