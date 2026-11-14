# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026ApJ...997..155M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES).\
XIII. Core Mass Function, Lifetime, and Growth of Prestellar Cores

## Abstract

The core mass function (CMF) of prestellar cores is essential for understanding the initial conditions of star and cluster formation. However, the universality of the CMF and its relationship to the initial mass function (IMF) remain unclear. We study the CMF in the earliest stage of high-mass star formation using 461 prestellar core candidates and 254 protostellar cores as a part of the ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). We find that prestellar core candidates tend to have lower masses than protostellar cores. We also find that the lifetime of prestellar cores is several times longer than the freefall time, although it approaches the freefall time as the core mass increases. The CMF, including both protostellar and prestellar cores, has a power-law slope of -2.05$\pm$0.04, shallower than Salpeter’s IMF slope of -2.35. Conversely, the CMF of gravitationally bound, prestellar cores has a steeper slope (-2.32$\pm$0.30), indistinguishable from Salpeter’s slope. This finding is consistent with observations in both low-mass star-forming regions and high-mass protoclusters, implying a universal core formation mechanism. The protostellar CMF with a larger maximum core mass can be reproduced by the prestellar CMF when an external gas infall is considered. The inferred mass infall rate is higher than the Bondi-Hoyle-Lyttleton accretion rate and follows a shallower mass dependence (smaller power-law index), more consistent with the tidal-lobe accretion. This may contribute to the evolution of CMFs seen in later stages.

show\]kaho.morii@cfa.harvard.edu

# Introduction

The initial mass function of stars (IMF) describes the distribution of stellar masses at the time of their formation. Since the properties and evolution of stars are primarily influenced by their mass, the IMF is essential for understanding the structure of our universe. The universality of the IMF has been proposed from observations in the solar neighborhood (cite: Salpeter55; Kroupa01; Chabrier03). Specifically, these IMFs exhibit a power-law tail in the range of 0.4–10 $M_\odot$ characterized by a power index of $\alpha = -2.35$ (cite: Salpeter55). Additionally, they show a log-normal distribution on the lower-mass end, with a peak around 0.1–0.2 $M_\odot$ (cite: Kroupa01; Chabrier03). This universality across various star forming regions suggests that IMFs are determined by universal physical properties. Recent advancements using highly precise parallaxes and proper motions from the Gaia mission have allowed for more accurate measurement of the Milky Way’s field IMF based on a much larger sample size (cite: Mor19-imf; Sollima19-imf). These findings do not contradict the notion of a universal IMF. However, it has been suggested that the IMF may vary with environmental factors such as those found in low-metalicity environments or in the galactic center (cite: Marks12; LeeHennebelle18). In fact, deviation from a universal IMF, such as a top-heavy IMF, have recently been observationally reported (cite: Hosek19; Li23-imf; KlessenGlover23-lowmetal). This raises critical questions about what makes the IMF universal and how it varies under different environmental conditions.

The core mass function (CMF) describes the mass distribution of cores, which are the progenitors of stars. In particular, the mass function of prestellar cores has been expected as the potential progenitor of the IMF. The CMF observed in nearby low-mass star-forming regions resembles the IMF, shifted to higher masses when compared to the IMF, but maintaining a similar shape (cite: Andre10; Konyves15; Fiorellino21). This suggests a constant core-to-star formation efficiency of $\sim$30–40%.

However, deriving the CMF from observations involves several challenges, including defining cores’s boundary, achieving adequate spatial resolution, and estimating the core mass. Accurate core identification requires sufficient spatial resolution and high sensitivity, as highlighted in (cite: Louvet21), especially to determine the CMF peak. Recently, (cite: Pelkonen21) suggest that the shapes of CMFs and IMFs can still resemble each other, even if there is no one-to-one correspondence between cores and stars, and that a significant fraction of the stellar mass originates from outside the initially bound cores.

With these considerations in mind, several studies have raised questions about the universality of CMFs based on observations in active cluster-forming regions, such as W43-MM1 (cite: Motte18_natas), showing a shallower slope at the high mass end. More recently, the ALMA-IMF Large Program (cite: Motte22-ALMAIMF; Ginsburg22-ALMAIMF) conducted high-resolution ALMA observations toward 15 massive protoclusters and increased the sample of top-heavy CMFs with a consistent methodology to derive CMFs (cite: Louvet24). (cite: Pouteau23) investigated the evolution of CMFs in the W43-MM2 and MM3 clusters, suggesting a transition from a Salpeter-like slope to a top-heavy slope as star formation becomes more active. Furthermore, (cite: Nony23) categorized cores as prestellar or protostellar based on the presence of molecular outflows, finding that the prestellar CMF follows a Salpeter-like distribution while the protostellar CMF exhibits a shallower slope. These studies highlight how radio interferometers enable to explore the CMF not only in our solar neighborhood but also in more distant, massive protoclusters.

Moreover, recent high-resolution observations have also revealed the inner structures of cores, such as fragments, asymmetric structures, and disk-like structures (cite: Beuther21; Sanhueza21; Sanhueza25; Olguin22; Olguin23; Li24_natureas; Sanna25; Olguin25-arxiv; Mai25-arxiv). This indicates a complex mass delivery process from cores to stars, especially in cluster-forming regions. A constant core-to-star formation efficiency and a simple shift in masses from the CMF to the IMF are likely oversimplifications based on the recent high-angular resolution observations. Nevertheless, the CMF, particularly the prestellar CMF, is an important key property characterizing the initial conditions of stellar cluster formation.

Infrared dark clouds (IRDCs) are dark clouds that appear in silhouette in infrared images due to the background galactic plane emission and the presence of dense gas. These clouds are believed to be the birthplace of high-mass stars or stellar clusters because of the lack of bright infrared emission (cite: Sridharan05; Rathborne06; BerginTafalla07; Chambers09; Sanhueza12; Sabatini19). IRDCs tend to be identified before widespread star formation is evident, and once the high-mass stars turn on, they disrupt the surrounding environment through intense radiation, stellar winds, and the formation of HII regions. Therefore, studying IRDCs is crucial for understanding the evolution of high-mass star formation (cite: Csengeri17b_progenitor; Sanhueza13; Sanhueza17). The CMF within IRDCs likely reflects the mass distribution of cores during the early stages of cluster evolution.

However, IRDCs are typically located far from the Sun (i.e., $>$a few kpc), and the CMFs that have been produced so far often suffer from small sample sizes or insufficient spatial resolution to accurately identify cores (cite: Ohashi16; Kong19_core; Liu18). Additionally, the complexity introduced by molecular outflows in these cluster-forming regions complicates the determination of the mass function of prestellar cores. In the ALMA Survey of 70 μm Dark High-Mass Clumps in Early Stages (ASHES), we obtained the large, extremely well-characterized population of cores embedded in the IRDCs (cite: Sanhueza19; Li20; Tafoya21; Morii21; Li22; Sabatini22; Sakai22; Li23; Morii23; Izumi24; Morii24; Lin25). We identified 839 cores and carefully classified their evolutionary stages by detecting molecular outflows and warm gas tracers (cite: Sanhueza19; Li20; Morii21; Morii23; Izumi24), as well as assessing their gravitational stability through virial analysis (cite: Li23; Morii24).

In this paper, we present the mass function of cores identified in the ASHES, allowing for comparison with those from other star-forming regions. This paper is constructed as follows: Section [2](#sec:obs) describes the observation, data properties, and core sample. Section [3](#sec:results) explains how to derive the CMF, and display the produced CMF. We discuss the slope of the CMF and the lifetime of prestellar cores in Section [4](#sec:discussion). Our conclusion is listed in Section [5](#sec:conclusion).

# Observations and Data

We have used the observational data from the ASHES project. Observations were carried out with ALMA in Band 6 ($\sim$224 GHz; $\sim$1.3 mm) through three cycles: Cycle 3 (2015.1.01539.S, PI: P. Sanhueza), Cycle 5 (2017.1.00716.S, PI: P. Sanhueza), and Cycle 6 (2018.1.00192.S, PI: P. Sanhueza). The ASHES-sample consists of thirty-nine 70 μm-dark IRDC clumps with the potential for high-mass star formation (cite: Morii23). The data were taken with the main 12-m array and the Atacama Compact Array (ACA), including both the 7-m array and Total Power (TP; for spectral line data only). The average 1$\sigma$ rms noise level of the continuum images was $\sim$0.094 mJy beam$^{-1}$ with a beam size of $\sim$1.2$''$. (cite: Sanhueza19) and (cite: Morii23) describe the detailed ASHES program and the observation setup. In this paper, we use CO ($J$=2–1), H$_2$CO ($J_{K_a, K_c} = 3_{2,2}-2_{2,1}, 3_{2,1}-2_{2,0}$), CH$_3$OH ($J_K = 4_2-3_1$), and HC$_3$N ($J= 24-23$) for identifying protostellar cores. Their velocity resolutions are $\sim$1.3 km s$^{-1}$. DCO$^+$ ($J=3-2$) and N$_2$D$^+$ ($J=3-2$) with velocity resolutions of 0.17 km s$^{-1}$ are used for the virial analysis. Those lines are produced by combining the 12 m array data with the 7 m array data. We also use TP data of the C$^{18}$O ($J= 2-1$) to estimate the velocity dispersion of the clumps, which has a velocity resolution of 1.3 km s$^{-1}$ and an angular resolution of 29.6$''$.

By applying the dendrogram technique, implemented in `astrodendro` (cite: Rosolowsky08), to the 1.3 mm continuum images of 39 regions, we have identified 839 cores (cite: Morii23). We classified cores into prestellar core candidates and protostellar cores using the molecular lines. Detailed information and line setups are described in (cite: Morii24). Among 839 cores, 103 cores (12.3%) are associated with molecular outflows detected in CO ($J$=2–1), and 222 cores (26.4%) are not associated with CO outflows but have detections of at least one warm gas tracer, such as H$_2$CO ($J_{K_a, K_c} = 3_{2,2}-2_{2,1}, 3_{2,1}-2_{2,0}$), CH$_3$OH ($J_K = 4_2-3_1$), or HC$_3$N ($J= 24-23$), with $E_{\rm u}/k$ of 68.09, 68.11, 45.46, and 130.98 K, respectively. These warm gas tracers have similar spatial distributions as outflows and the derived rotational temperature is high ($\gtrsim$50 K), implying ongoing star formation activity (cite: Morii21; Izumi24). Hereafter, they are named as outflow cores and warm cores, respectively, or protostellar cores by combining both outflow and warm cores. The remaining 514 cores (61.3%) without any detections of star formation signatures are prestellar core candidates. We also calculated the virial parameters with the velocity dispersion estimated from the dense gas tracers of DCO$^+$ or N$_2$D$^+$ $J=3-2$ since their similar spatial distributions to the dust continuum emission and their high critical density indicates that they trace the dense cores (cite: Sakai22; Li23; Morii21). Among 839 cores, either of the lines is detected from 492 cores (58.6%), and 340 cores (69.1%) have virial parameter smaller than 2, classified as gravitationally bound cores ignoring external pressure and the magnetic field (cite: Morii24).

# Results

## Core Mass

The core masses are derived from the 1.3 mm dust continuum emission adopting the optically thin assumption in (cite: Morii23) as $$\begin{equation}
    M_\mathrm{core} = \mathbb{R}\frac{d^2 F_\nu}{\kappa_\nu B_\nu (T_\mathrm{dust})},
\label{equ:Mass}
\end{equation}$$ where $\mathbb{R}$ is the gas-to-dust mass ratio, $F_\nu$ is flux density, $\kappa_\nu$ is the dust absorption coefficient, $d$ is the distance to the source, and $B_\nu$ is the Planck function for a dust temperature $T_\mathrm{dust}$. For cores in eleven ASHES clumps, we used the rotational temperatures derived from NH$_3$ observations at $\sim$5$''$ (cite: Li23; Allingham24). For the remaining twenty-eight clumps, we adopted the clump temperature for the core mass calculation (cite: Guzman15). Column 3 in Table 4 in (cite: Morii23) shows the temperature used for each core in the mass estimation. We adopt the standard gas-to-dust mass ratio of 100, and a dust opacity of 0.9 cm$^2$ g$^{-1}$ (cite: Ossenkopf94).

We checked the optical depth at 1.3 mm ($\tau_{\rm 1.3mm}$) at first order by taking the ratio of $I_{\rm 1.3mm, peak} / \Omega$ to $B_{\rm 1.3mm}(T_{\rm dust})$, corresponding to 1-exp(-$\tau_{\rm 1.3mm}$), where $I_{\rm 1.3mm, peak}$ is the measured peak intensity, $\Omega$ is the beam solid angle, as introduced in Appendix B of (cite: Pouteau22). The cores have ratios smaller than 0.08 (median of 0.001), which is in agreement with the optically thin condition.

The derived core mass ranges from 0.06 to 81 $M_\odot$. The uncertainties of mass is $\sim$50%, largely contributed from the gas-to-dust mass ratio and the dust opacity (cite: Morii23).

The CMF with a differential histogram of all 839 cores is shown in the left panel of Figure [1](#fig:cmf-all). The bin size was determined with a task in `numpy` of *histogram bin edges* as Freedman Diaconis Estimator (fd), which takes into account data size. The colors light blue, green, and orange represent prestellar core candidates, warm cores, and outflow cores, respectively. Here, each bin represents the combined frequency from three evolutionary stages, stacked to show the relative contribution to the total count per bin. This plot clearly shows the increase of the percentage of protostellar cores as core mass increases. Although the minimum mass of outflow and warm cores is small, 0.2 $M_\odot$ and 0.06 $M_\odot$, respectively, the mass of protostellar cores are generally larger than those of prestellar core candidates.

![](CMF_all_class.pdf)

## Completeness

We calculated the mass completeness by inserting an artificial Gaussian core into the continuum images and varying the core mass. For each mass bin, the flux of the Gaussian core was calculated from Equation [\[equ:Mass\]](#equ:Mass) considering the primary beam correction. The inserted position of core center was uniformly random in a region where the primary beam response was higher than 40% to avoid cores located at the edge, consistent with the core identification process. After inserting a core, we applied the dendrogram algorithm to the image and checked if the inserted core was identified as a $\mathtt{leaf}$ whose peak position is consistent with the inserted position within the beam size. We repeated the test 5000 times and calculated the mean detection rate per mass bin from region to region to determine the 90% completeness level. Figure [2](#fig:CMF_completeness) (a) shows the fraction of detected cores as a function of core mass. The completeness level ranges from 0.3–4.5 $M_\odot$ with a median of $\sim$0.6 $M_\odot$. More deficient completeness comes from the worse mass sensitivities. To reduce these effects among the sample, we excluded five clumps with the lowest completeness (see the colored lines in the figure)[^1]. After this selection, our sample ensures a 90% completeness level above 1.2 $M_\odot$, resulting in a final sample of 715 cores for the CMF analysis.

![](Recoverable_fraction_all.pdf)

![](Recoverable_flux_34cl.pdf)

We also measured how much flux was recovered by the dendrogram algorithm by comparing the flux of leaves identified by `astrodendro` and the inserted flux. The recovered flux profile is shown in Figure [2](#fig:CMF_completeness) (b), showing that above 1.2 $M_\odot$, the recovered flux ranges from $\sim$0.7 to $\sim$1, but most closely resembles unity. The ratio of the identified and inserted flux can be higher than 1 if a core is inserted on the existing emission such as filament or another source, which may happens in the heavily clustered regions. Using this flux recovery profile, we corrected the observed masses by dividing them by the corresponding recovery fraction in each mass bin and region. The correction has been applied to the mass range of each core where the completeness level is higher than 0.5, colored in Figure [2](#fig:CMF_completeness). This correction slightly increases the masses of low-mass cores.

The CMFs of the selected 715 cores before and after flux correction are shown in the middle and right panels of Figure [1](#fig:cmf-all). Among the 715 cores in the middle panel, the numbers of prestellar core candidates, warm cores, and outflow cores are 461, 178, and 76, respectively. The worst 90% completeness level (1.2 $M_\odot$) is plotted as dotted lines. The middle panel of Figure [1](#fig:cmf-all) indicates that the completeness limit is above the detection limit of outflows and warm lines (see Appendix [6](#sec:Appendix_Ncore)) and also the protostellar core fraction increases as the core mass. A comparison between the left and middle panels reveals that the excluded sample contains some of the most massive cores[^2], but the distributions of the intermediate-mass range, which dominate the fitting result, are similar.

We applied the power-law fitting above 1.2 $M_\odot$ in the selected sample case. As expected from the recovered flux plot, the flux correction mostly affects low-mass cores near 1 $M_\odot$, and it makes a slightly steeper slope from -1.92$\pm$0.12 to -2.02$\pm$0.11. Here, the uncertainties includes the mass uncertainties and the fitting uncertainties. Even considering the uncertainties, these slopes are slightly shallower than -2.35, consistent with the first attempts of studying the CMF in the ASHES pilot survey (cite: Sanhueza19) and high-mass protoclusters (cite: Motte18_natas; Kong19_core; Moser20; Louvet24). To confirm our results are independent of the core identification method adopted (astrodendro), we ran `getsf` (cite: Menshchikov13; Menshchikov21), as described in Appendix [7](#sec:Appendix_coremethod), and obtain a consistent result.

## Prestellar CMF

Prestellar cores are cores on the verge of gravitational collapse, prior to the formation of protostars. Therefore, the prestellar mass function likely traces the initial conditions of star formation. By comparing its properties in various environments such as low-mass and high-mass star-forming regions, outer galaxy clouds, galactic center regions, and also with the IMF, we can investigate the universality of star formation in the galaxy. Our prestellar core sample consists of 461 cores without any signs of protostars detected by ALMA such as molecular outflows and warm gas tracers. It includes 130 gravitationally bound cores based on virial analysis. The CMF, in differential form, of both all prestellar core candidates and gravitationally bound prestellar cores is shown in Figures [3](#fig:cmf_prebound) (a) and (d).

In addition to the standard differential histogram, to avoid arbitrariness of binning and to directly compare with other references, we also derived the complementary cumulative distribution with variable-size bins, Figure [3](#fig:cmf_prebound) (b) and 3(e), following the recommendations of (cite: MaizApellaniz05) and (cite: Reid06), the same method as (cite: Motte18_natas). Also, we performed the fitting using maximum likelihood estimates (MLE; Figures [3](#fig:cmf_prebound) (c) and (f)) as developed by (cite: Clauset09), following one of the ALMA-IMF studies by (cite: Louvet24) and implemented in the Python package, `powerlaw` (cite: Alstott14). MLE determines the best-fit power-law slope directly from the unbinned data by maximizing the likelihood of the observed distribution, avoiding biases from histogram binning. Figure [3](#fig:cmf_prebound) shows all the CMFs of the prestellar core candidates (top) and gravitationally bound prestellar cores (bottom).

The black lines represent the best fit of the power law index above the lowest 90% completeness level of 1.2 $M_\odot$, $dN/dM \propto M^\alpha$, $N(> \mathrm{log} M) \propto M^{\alpha +1}$, or $P(m) = - \frac{\alpha +1}{M_{\rm min}} \left(\frac{m}{M_{\rm min}} \right)^{\alpha}$. The gray-shaded regions show 1$\sigma$ uncertainty on alpha, which comes from the fitting uncertainties and the mass uncertainties. The latter is estimated from the fitting of the simulated CMFs. Considering a 50% uncertainty in core masses (Section [3.1](#sec:mass)), we performed a Monte Carlo simulation to assess how the CMF changes. We multiplied a random value in the range of 0.5–1.5 for each core mass in one trial and produced the CMF. We repeated this simulation 1000 times and calculated a 1 sigma value coming from the mass uncertainty.

![](CMF_pre_prebound.pdf)

All distributions show power-law tails in the mass range of at least 1–5 $M_\odot$, then deviate toward a steeper decline at higher masses. This figure shows that the power-law index $\alpha$ slightly depends on the representations of the mass distribution in such a limited sample size at the high-mass end. The best fit $\alpha$ was -2.65 to -2.38 for prestellar core candidates (including bound and unbound cores) and -2.53 to -1.83 for bound prestellar cores. When comparing the CMFs derived from the same method, we find that the bound core-limited CMFs have a slightly shallower slope, but they still remain around -2.35.

# Discussion

## Power-law Index of CMFs

![](Slope_normaldist.pdf)

Figure [4](#fig:cmf-slope) summarizes the best-fit power-law index of CMF of prestellar core candidates (light blue) and bound-prestellar CMF (orange). The shaded probability density function is built from the fitting of the cumulative percentage distributions using the MLE method, corresponding to Figure [3](#fig:cmf_prebound) (c) and (f). The value of $\alpha=-2.35$ is indicated by the vertical line. The light blue and orange distributions are both located near or at values smaller than -2.35.

For comparison, we plotted the index and the uncertainties estimated in some studies of the ALMA-IMF project (cite: Nony23; Pouteau23; Louvet24). It should be noted that the completeness and the fitting range (i.e., the minimum mass used for fitting) is comparable, and all values in this plot are derived using the same fitting methods. One of the published ALMA-IMF papers, (cite: Nony23), only present the CMF of prestellar cores. They show that the slope of prestellar CMF is steeper than that of protostellar CMF, and it was $\alpha=-2.46 ^{+0.12}_{-0.19}$ (blue dashed line). Upon a direct comparison of the blue dashed line with our distribution, the best-fit index is well consistent, slightly below -2.35.

In addition to the prestellar core mass function, we also compare the CMF that includes both prestellar and protostellar cores, shown in green, red, and gray curves. (cite: Pouteau23) produced CMFs in subregions of the W43 protocluster to study their evolution. Here, we plot one of the measured values, $\alpha=-2.16^{+0.16}_{-0.30}$ from W43-MM10 (green dashed line), which is likely in an early evolutionary stage. (cite: Louvet24) derived CMFs by combining all the cores identified in 15 protoclusters and estimated $\alpha=-1.97 \pm 0.06$ (red dashed line). Since they used the MLE method, to directly compare with our sample, we also plot the best-fit index derived in the same way as a gray line ($\alpha=$-2.05$\pm$0.04). The gray line takes its peak similar to the green but smaller than the red line. Our sample consists of cores embedded in 70 μm-dark clumps that are likely in a very early evolutionary stage. W43-MM10 is also in similar, relatively quiescent region. This trend, from early evolutionary stages (quiescent, 70 μm-dark regions like our sample and W43‑MM10) to more evolved, active cluster-forming stages (like those in (cite: Louvet24)), is consistent with the ALMA‑IMF (cite: Pouteau23) results. Furthermore, it is also in agreement with the ALMAGAL survey (cite: Coletta25-almagal) which suggest an increase in the power-law index during cluster evolution.

In summary, Figure [4](#fig:cmf-slope) reveals two key findings. First, the comparison of the CMF of the full sample (including prestellar and protostellar cores) between quiescent regions (gray and green) and protoclusters (red) tells that the slope becomes shallower as protoclusters evolve. This implies that the full CMF reflects star formation activity and the formation of high-mass cores (see Section [4.3](#sec:core-growth) for further discussion). Second, the prestellar CMFs (light blue, orange, and blue) has a slope consistent with the Salpeter IMF, and this result has been reported across various evolutionary stages (cite: Nony23) and even in low-mass star-forming regions. This suggests that the prestellar core formation mechanism may be a universal process throughout the galaxy, largely independent of the surrounding star-forming activity.

## Lifetime of Prestellar Cores

The ASHES core sample, the large, well-characterized sample of cores embedded in IRDCs, allows us to constrain the lifetime of prestellar cores in cluster-forming regions.

Whether prestellar cores follow fast collapse or slow collapse models is one of the important questions in star formation. The former case expects $\lesssim$1 Myr, comparable to the freefall time of cores, where cores form through gravo-turbulent fragmentation (cite: Hennebelle12) and the latter expects a longer lifetime of 1–10 Myr, several times longer than the freefall time, due to the support from magnetic fields and turbulence (cite: Shu87). In nearby star-forming regions, several attempts have been made to estimate the lifetime of prestellar cores such as careful physical and chemical modeling (cite: Lin20; Lin24) and also in a statistical way counting the number of the prestellar and protostellar cores (cite: Beichman86; LeeMyers99; Jessop00; Ohnishi02; Konyves15; Tokuda20; Takemura23). Assuming a constant star formation rate throughout the cloud’s lifetime, the statistical lifetime can be derived as $$\begin{equation}
    t_{\rm pre} = \frac{\rm Number\,of\,prestellar\,core}{\rm Number\,of\,protostellar\,core} \times t_{\rm proto}, 
    \label{equ:lifetime}
\end{equation}$$ where $t_{\rm proto}$ is the reference lifetime. In the low-mass regime, or core density range of 10$^4$–10$^5$ cm$^{-3}$, the prestellar core lifetime has been estimated to be $\sim$1.2 Myr, a few times the core freefall time, $t_{\rm ff}$, which implies nonthermal support slow down collapse (cite: Ward-Thompson07; Konyves15; Tokuda20; Takemura23).

Here, we estimate the statitical lifetime of prestellar cores in the ASHES sample. Due to the lack of a formal definition of classes based on Spectral Energy Distributions (SEDs) in high-mass star-forming regions, and following studies that calculated the relative number of protostellar cores with HII regions (cite: Tige17; Motte18), we adopt 0.2 Myr as the protostellar lifetime, $t_{\rm proto}$. As discussed in (cite: Valeille-Manet25), this has an uncertainty of about a factor of two. By inserting the total number of bound, prestellar cores and the number of bound, protostellar cores (including both warm cores and outflow cores) into Equation [\[equ:lifetime\]](#equ:lifetime), we estimate the lifetime of prestellar cores to be 0.18 Myr. This value is $\sim$6 times longer than the freefall time of the ASHES cores, which is approximately 3$\times$10$^4$ yr.

The large core sample also allows us to investigate a possible differences of the core lifetime with respect to the core mass. Figure [5](#fig:lifetime) illustrates the estimated core lifetime as a function of mass, represented by orange crosses. The data points were obtained by first creating equally spaced mass bins on a logarithmic scale. In each mass bin, we counted the number of prestellar and protostellar cores and applied Equation [\[equ:lifetime\]](#equ:lifetime). Here, we limited the sample only to gravitationally bound cores. The resulting plot clearly demonstrates the mass dependency of the core lifetime. Gray circles represent the freefall time of each core. As the core mass increases, the lifetime decreases from $\sim$1 Myr to $\lesssim$0.1 Myr, approaching their corresponding freefall time.

Recently, the ALMA-IMF project reported the lifetime of high-mass prestellar core candidates ($>$8 $M_\odot$), as $\sim$0.12–0.24 Myr or $\sim$10$\times t_{\rm ff}$ assuming a protostellar lifetime of 0.3 Myr (cite: Valeille-Manet25). However, even though our sample at $\sim$10 $M_\odot$ is not large, the estimated lifetime is much shorter than 0.1 Myr. The non-detection of high-mass prestellar cores with masses larger than 10 $M_\odot$ and lower percentage of prestellar cores in the intermediate-mass range ($>5\,M_\odot$) in ASHES lead to a shorter lifetime. Even when comparing the number of prestellar core candidates and cores associated with outflows (i.e., excluding warm cores from the protostellar core sample) or including warm cores in the prestellar core sample, the derived lifetime is still less than 0.1 Myr at 10 $M_\odot$. In the lower mass range, the derived values are a few times longer than the freefall time, which is consistent with those in nearby regions, including Orion (cite: Konyves15; Takemura23).

Up to this point, our analysis of core lifetimes as a function of mass has implicitly assumed that core mass remains constant over time. This assumption is equivalent to a scenario where gas accretion onto the central protostar is perfectly balanced by replenishment from the surroundings. However, the evolution of core mass during star formation involves both accretion onto the central object (leading to a decrease in core mass) and gas infall from the surrounding clump (increasing core mass), and their rate can be different to each other. We now consider these two alternative scenarios to better understand the mass dependency of core lifetimes.

First, let us consider a scenario where the core mass decreases over time due to accretion onto the forming protostar. In this case, the initial core mass would have been larger than the currently observed core mass. For example, if half of the initial core mass has already been accreted onto the protostar, then their initial core mass would be twice the currently observed core mass ($M_{\rm proto}=2 \times M_{\rm obs}$). The red circles in Figure [5](#fig:lifetime) represent the core lifetimes estimated under this assumption. Although this scenario suggests a more rapid mass decrease, it does not significantly alter our primary conclusion: more massive cores still exhibit lifetimes of a few times 10$^4$ yr. This is comparable to the lifetime of the 70 μm dark phase (cite: Motte07; Tackenberg12; Csengeri14; Urquhart18; Sabatini21), implying a rapid mode of star formation.

Alternatively, the core mass may increase during its evolution as discussed in Section [4.3](#sec:core-growth). For instance, this considers the case in which the core continues to accrete material from the surrounding clump at a higher rate than the one from which the star accretes from the core. Indeed, (cite: Coletta25-almagal) revealed the increase of core masses as clump evolution as a part of the ALMAGAL project, implying such core growth (cite: Xu24; Morii25). Under this growth scenario, the initial core mass would be smaller than the currently observed core mass. For example, if the initial core mass was half of the observed mass ($M_{\rm proto}=0.5 \times M_{\rm obs}$), the estimated values are shown in Figure [5](#fig:lifetime) as blue squares. The derived prestellar lifetime at $M>$5 $M_\odot$ becomes longer, and around 0.1 Myr. In this case, even in the high-mass range, the lifetime may be several times longer than the freefall time. This is similar to the ALMA-IMF estimation (cite: Valeille-Manet25), although it is subject to considerable uncertainties.

Overall, the statistically derived timescale of prestellar cores in the mass range of 1–5 $M_\odot$ is generally around 0.1 Myr. This is likely a few times longer than the cores’ freefall time, even considering the accretion- or external-infall-dominated cases. It aligns with the statistical lifetime estimated in low-mass star-forming regions derived similarly. (cite: Bovino21) revealed a comparable prestellar lifetime using a chemical clock that combines the observed pD$_2$H$^+$/oH$_2$D$^+$ ratio with numerical calculations. Although their calculation assumes a low-mass star formation environment, the derived value of a few to 10 times the freefall time is consistent with ours. At $\sim$5–10 $M_\odot$, the prestellar lifetime may be close to cores’ freefall time without a significant infall contribution. Further investigation using the deuterium ratio in IRDCs, as attempted by (cite: Redaelli21; Redaelli22), would provide a different perspective to constrain the lifetime.

One caveat of this analysis is that we assumed that the star formation rate (SFR) remains constant within each clump. If the SFR at the current stage is low, the derived lifetime may be overestimated. In such cases, the lifetime of a prestellar core is generally longer than its freefall time, even for cores with a mass of $\sim$10 $M_\odot$.

![](lifetime_mass_bound.pdf)

## Core Growth and CMF

The ASHES project has investigated core properties in the very early stages and revealed a lack of high-mass cores in most targets (cite: Morii23), implying the need for core growth. This conclusion is supported not only by ASHES but also by recent ALMA surveys of high-mass star-forming regions, such as QUARKS (Querying Underlying mechanisms of massive star formation with ALMA-Resolved gas Kinematics and Structures; (cite: Xu24)) and SQUALO (QUiescent And Luminous Objects; (cite: Traficante23)), as well as large programs like ALMA-IMF (cite: Motte22-ALMAIMF) and ALMAGAL (cite: Molinari25-almagalI; Coletta25-almagal). Given the dense, massive, and clustered environments where high-mass stars form, it is natural to expect that gas initially unbound to cores continues to infall from the surroundings, even after protostellar formation. As seen in Figure [1](#fig:cmf-all), protostellar cores tend to have larger masses than prestellar cores. Figure [6](#fig:cmf_evolution) shows the CMF of gravitationally bound prestellar cores and that of bound protostellar cores as blue and red lines, respectively. Again, it shows that mass function of protostellar cores is shallower with a larger maximum core mass. Similar features have also been reported in more massive star cluster-forming regions (cite: Nony23).

Here, we investigate the effect of external infall or core growth on the CMF, as well as the amount of external infall needed to reproduce the observed protostellar CMF from the prestellar CMF.

First, we estimate the Bondi-Hoyle-Lyttleton (BHL) accretion as $$\begin{eqnarray}
    \nonumber
    \dot{M}_{\rm Bondi} &=& \frac{\pi \rho G^2 M^2}{\sigma^3} \\
    \nonumber
    &\sim& 1.65\times 10^{-7} \left( \frac{n_{\rm cl}}{4\times 10^4\,\rm cm^{-3}} \right)  \\
     &\times&
     \left( \frac{M_{\rm core}}{1\,M_\odot} \right)^2
      \left( \frac{\sigma_{\rm cl}}{1\rm\,km\,s^{-1}} \right)^{-3}\,M_\odot\,{\rm yr^{-1}}
      \label{equ:bhl}
\end{eqnarray}$$ for the median clump density ($n_{\rm cl}$) of $4\times 10^4\,\rm cm^{-3}$ and the median velocity dispersion of the clumps ($\sigma_{\rm cl}$) of $1\rm\,km\,s^{-1}$ (cite: Morii23). For cores with $M_{\rm core}>10\,M_\odot$, it will be on an order of 10$^{-5}$ $M_\odot$ yr$^{-1}$. For an intermediate mass core ($\sim$10 $M_\odot$) to be a $M_{\rm core}$=30 $M_\odot$, the required duration time of prestellar phase is $\sim$1.5 Myr. The gray dashed line in Figure [6](#fig:cmf_evolution) represents the case. The timescale needed for this model is comparable to the inertial inflow model proposed by (cite: Padoan20), although it is much longer than the prestellar lifetime estimated in Section [4.2](#subsec:lifetime). The CMF became shallower as the accretion rate is proportional to mass squared, and it is much shallower than the observed protostellar CMF (red line).

Then, to investigate which power-law index of mass can reproduce the observed CMFs, we assumed that the external mass infall rate follows a power-law dependence on mass ($\dot{M} = C M^{p}$), where C is a constant factor and estimated the best-fit parameter $p$ using non-linear least squares fitting with `scipy`’s `curve_fit`. The derived best-fit parameter is $p=1.16\pm0.02$ with $C=1.60\pm$0.01. Assuming a duration of external infall of 30 kyr, approximately free-fall time of ASHES cores, the mass infalll rate is described as $$\begin{equation}
    \dot{M}= 5.33\times 10^{-5} \left( \frac{M_{\rm core}}{1\,M_\odot} \right)^{1.16} \,M_\odot\,{\rm yr^{-1}}. 
    \label{equ:bestfit-mdot}
\end{equation}$$ This model is plotted as green dashed line in Figure [6](#fig:cmf_evolution). Compared with BHL accretion, the constant factor, $C$, is much larger, and the smaller power-law index affects the core growth of initially low- to intermediate-mass cores, not only higher-mass cores.

We compare the estimated value with theoretical predictions. One is the clump-fed model derived by (cite: Tan14) as their Equation (16), which is $$\begin{eqnarray}
\nonumber
    \dot{M} &=& 6.26  \times 10^{-5} 
    \left(\frac{\epsilon_{\rm ff}}{0.1} \right) 
    \left(\frac{\epsilon_{\rm cl}}{0.5}\right)^{-1} \left(\frac{m_{*}}{50 \,M_\odot} \right)\\
    &\times&
    \left(\frac{\Sigma_{\rm cl}}{0.3 {\rm \,g\,cm^{-2}}}\right)^{3/4} 
    \left(\frac{M_{\rm cl}}{800 \,M_\odot}\right)^{-1/4} 
     \,M_\odot\,{\rm yr^{-1}},
\end{eqnarray}$$ where $\epsilon_{\rm ff}$ is the star formation efficiency per free-fall time, $\epsilon_{\rm cl}$ is the final star formation efficiency from the clump, and $m_{*}$ is the final stellar mass. We inserted the median surface density and mass of the ASHES clump and assuming the $\epsilon_{\rm ff}$ and $\epsilon_{\rm cl}$ of 0.1 and 0.5, respectively, for normalization. The final stellar mass and the efficiencies are unclear but the constant factor and the power-law index is well similar to our best-fit, if the final stellar mass is somewhat proportional to the core mass.

In the case of clump-fed model in a gas-dominated potential, where tidal-lobe accretion dominates, the mass accretion rate is expected to have a power-law index of 2/3 (cite: Bonnell01), as discussed in (cite: Clark21). Indeed, (cite: Maschberger14) confirmed the mass dependence by analyzing a hydrodynamical sink particle simulation following (cite: Bonnel11). One recent observational study found $\dot{M} \propto M^{0.66}$ relation (cite: Wells24), preferring the tidal-lobe accretion. The ASHES project targets the early stage of high-mass star formation where gas potential likely dominates, but the best-fit parameter implies a factor 2 larger index. If the external infall duration time depends on mass, where more massive stars form earlier, the index may become closer to 2/3 since we assumed a constant duration time.

![](CMF_prob_preproto_model.pdf)

Equation [\[equ:bestfit-mdot\]](#equ:bestfit-mdot) gives a much higher mass infall rate than BHL accretion (Equation [\[equ:bhl\]](#equ:bhl)). Indeed, recent observations of core-scale infall have reported such high mass infall rates (cite: Contreras18; Sanhueza21; Redaelli22; Morii25; Sanhueza25), which enable core growth in timescales comparable to freefall timescales. It indicates that the differential core growth may modify the Salpeter distribution produced by the initial fragmentation. In fact, the ALMA-IMF project has shed light on the evolution of CMF in massive clusters at different evolutionary stages (cite: Pouteau23). Similarly, (cite: Coletta25-almagal) investigated the evolution of CMFs across three distinct evolutionary groups. Their findings indicate that CMFs in more evolved stages exhibit shallower tails and contain more massive cores, implying that core growth is a possible explanation.

The Global and Local Infall in the ASHES Sample (GLASHES) survey reveal signs of a correlation between the core mass and the mass infall rate (cite: Morii25). (cite: Wells24) also found a relation between core mass and flow rate along filamentary structures toward cores. These correlations will be further explored with a larger sample and can be interpreted as direct evidence of mass-dependent infall. This mechanism explains the change in the CMF slope at high masses with the passage of time, from the prestellar to the protostellar phase, as initially suggested by (cite: Sanhueza19). It is also consistent with the idea that more massive cores have shorter lifetimes due to faster gas consumption (see Section [4.2](#subsec:lifetime)).

These findings suggest that core-to-star formation efficiency is not a straightforward process, challenging the assumption that initial core mass directly determines the final stellar mass. The evolution from a top-heavy CMF to Salpeter’s IMF has not been discussed in this paper, primarily because our targets are in the similar evolutionary stages and the sample of protostellar cores is small. However, the ALMA-IMF project recently reported further evolution of the CMF from top-heavy to the Salpeter-like slope (cite: Armante24). Beyond core growth, processes such as further core fragmentation and multiple system formation may play a role (cite: Olguin22; Li24_natureas; Sanhueza25). If the core-to-star formation efficiency depends on core mass, it also affect the evolution from CMF to IMF. (cite: Pouteau22) explored how the power-law slope of CMFs changes under various core-to-star formation efficiencies and fragmentation effects. Studying CMFs with a similar number of cores in evolutionary stages more advanced than the ASHES targets will allow for discussions similar to those of the ALMA-IMF project, which targeted more extreme and active environments.

In summary, our study reveals a prestellar CMF with a power-law tail resembling Salpeter’s IMF. Nevertheless, it is increasingly understood that the IMF is not a simple scaling of the CMF, and the process of mass accretion is considerably more complex.

# Conclusion

We have presented the CMF using 715 cores derived from the ASHES (ALMA Survey of 70 μm dark High-mass clumps in Early Stages) project. We have obtained the following conclusions:

1.  The produced CMF has a power-law tail above $\sim$1 $M_\odot$. The slope differs when the protostellar cores are included or excluded. When the protostellar cores are included, the CMF has a slope slightly shallower than -2.35. In contrast, the CMF from only the prestellar cores has a steeper slope due to the lack of higher-mass prestellar cores.

2.  The estimated power-law slopes of the CMF of prestellar core candidates above the completeness limit of 1.2 $M_\odot$ were -2.65 to -2.38, depending on the CMF representation and fitting method. The CMF of the gravitationally bound prestellar core has a slightly shallower slope of -2.53 to -1.83. Both are indistinguishable from Salpeter’s slope of -2.35.

3.  The power-law index of the prestellar CMFs is similar to those derived in low-mass star-forming regions and also in more evolved, massive protoclusters. This implies a universal core formation mechanism to produce the mass distribution between low- and high-mass star-forming regions.

4.  We estimated the lifetime of prestellar cores in IRDCs based on the fraction of prestellar cores against the protostellar cores. This lifetime decreases as the core mass increases and approaches the freefall time at $M_{\rm core} \sim$10 $M_\odot$. Considering the core growth, even in the high-mass range, the lifetime of prestellar cores becomes a few times the cores’ freefall time, similar to the statistical lifetime estimated in low-mass star forming regions.

5.  The top-heavy, shallower CMF, including protostellar cores, observed in the ASHES sample is similar to the one seen in massive protoclusters. The core growth in mass with a higher mass infall rate and a smaller exponential index than the Bondi-Hoyle-Lyttleton accretion rate has the potential to produce such a shallower slope and increase in the core mass from the prestellar to protostellar stage.

We are grateful to the anonymous referee for their constructive suggestions, which helped improve the quality of this paper. K.M was financially supported by Grants-in-Aid for the Japan Society for the Promotion of Science (JSPS) Fellows (KAKENHI No. 22J21529). K.M was supported by the ALMA Japan Research Grant of NAOJ ALMA Project, NAOJ-ALMA-369. PS was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP23H01221) of the Japan Society for the Promotion of Science (JSPS). GS acknowledges the project PRIN MUR 2022 FOSSILS (“Chemical origins: linking the fossil composition of the Solar System with the chemistry of protoplanetary disks”, Prot. 2022JC2Y93), the project ASI-Astrobiologia 2023 MIGLIORA (“Modeling Chemical Complexity”, F83C23000800005), the INAF-GO 2023 fundings PROTOSKA (“Exploiting ALMA data to study planet forming disks: preparing the advent of SKA”, C13C23000770005) and the INAF Minigrant 2023 TRIESTE (“TRacing the chemIcal hEritage of our originS: from proTostars to planEts”; PI: G. Sabatini). X.L. acknowledges support from the Strategic Priority Research Program of the Chinese Academy of Sciences (CAS) Grant No. XDB0800300, the National Key R&D Program of China (No. 2022YFA1603101), State Key Laboratory of Radio Astronomy and Technology (CAS), the National Natural Science Foundation of China (NSFC) through grant Nos. 12273090 and 12322305, the Natural Science Foundation of Shanghai (No. 23ZR1482100), and the CAS “Light of West China” Program No. xbzg-zdsys-202212. Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan. This paper uses the following ALMA data: ADS/JAO.ALMA#2015.1.01539.S, ADS/JAO.ALMA#2017.1.00716.S and ADS/JAO.ALMA#2018.1.00192.S (PI: P. Sanhueza). ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), $MOST$ and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. Data analysis was in part carried out on the open-use data analysis computer system at the Astronomy Data Center (ADC) of the National Astronomical Observatory of Japan.

ALMA

# Software

Astropy (cite: Astropy_13; Astropy18; Astropy22), astrodendro (cite: Rosolowsky08), CASA (cite: CASA22), getsf (cite: Menshchikov13; Menshchikov21), Matplotlib (cite: Hunter_matplotlib), Numpy (cite: Harris20_numpy), powerlaw (cite: Alstott14), Scipy (cite: Virtanen_scipy), seaborn (cite: Waskom2021_seaborn).

# Core Mass Distribution by Evolutionary Stage

Figure [7](#fig:Ncore) shows the number of cores in each mass bin for each evolutionary stage. In contrast to Figure [1](#fig:cmf-all), the histograms are not stacked and the y-axis represents the pure number count, allowing for a clearer view of the population in each evolutionary stage as a function of core mass. The left and right panels show the distributions for all 839 cores and the selected 715 cores, respectively. This figure clearly demonstrates that we have detected outflow and warm gas tracers even from low-mass cores well below the completeness limit of 1.2 $M_\odot$ (gray line).

![](Ncore_all_class_pararell.pdf)

# Core Identification: astrodendro VS getsf

Cores are not an obvious structure. We define compact, dense structures that eventually collapse to form a single star or a multiple stellar system as cores. However, they are usually embedded in clumps or clouds, and sometimes they do not have clear boundaries from the surroundings. Therefore, there is always uncertainty when setting parameters and using algorithms for identification. Additionally, when identifying cores from observational images, we must keep in mind projection effects.

There are some identification algorithms or techniques such as `GaussClump` (cite: StutzkiGuesten90_gaussclump), `ClumpFind` (cite: Williams94), `CuTEx` (cite: Molinari11), `CSAR` (cite: kirk13_csar), `getsources` or `getsf` (cite: Menshchikov13; Menshchikov21), `FellWalker` (cite: Berry15), `GExt2D` (Bontemps et al., in prep.), as well as `astrodendro` (cite: Rosolowsky08). Each core (or clump) identification method has pros and cons. Some examples of discussion are given in (cite: Joncour20_coreexcraction; LiChong20_identification; Menshchikov21; Cheng24), and (cite: Pineda23). (cite: LiChong20_identification) demonstrated that the `astrodendro` has higher detection completeness and better performance in extracting parameters (e.g., size, mass, and flux) than other algorithms such as `ClumpFind` and `GaussClumps`.

As the continuum images of the ASHES project show, the clumps have pc-scale internal structures and compact sources embedded. In such a hierarchical structure, we tried to extract only the compact components and applied `astrodendro`. However, here as an appendix, we show how the different algorithms give different outputs by comparing `astrodendro` and `getsf`.

As we did with `astrodendro`, we ran `getsf` for 39 continuum images. In this case, we only needed to set the maximum size of the sources, which did not significantly affect the output. We set it to 10 arcsec, which is almost ten times larger than the beam size. As a result, 331 cores were identified from 39 clumps. Of those, 305 overlap with the cores identified by `astrodendro` according to their positions. The other 26 structures are only identified by `getsf`, though most are at the edge of the field of view or very small. There is no parameter regarding the minimum size of a structure for `getsf` identification, so it found further fragmentation in twelve cores identified by the dendrogram. Figure [8](#fig:image_dendro_getsf) shows examples of differences in identified structures. Magenta contours indicate the structures identified by each method in the left (`astrodendro`) and right (`getsf`) panels. Regions where a single `astrodendro` source corresponds to two distinct `getsf` sources are highlighted in orange.

![](dendro_getsf.pdf)

To quantitatively compare the physical properties, we plot the mass and the radius (geometrical mean of the major and minor FWHM) estimated by `getsf` and `astrodendro` in Figure [9](#fig:MR_dendro_getsf). Only cores that overlap with both samples (305) are plotted here. The plot clearly shows that the size of cores measured from `astrodendro` are generally larger, and the flux and mass are also larger, though the differences are mostly within a factor of two.

![](MR_dendro_getsf.pdf)

Then, to see how significantly the mass function differs, we made a CMF for both samples. Figure [10](#fig:CMF_dendro_getsf) shows the difference by plotting the CMFs with the same bins. The navy and dark red colors highlight the different samples of `astrodendro` and `getsf`, respectively. As in the main text, we excluded five clumps here. The navy plot is the same as the middle panel of Figure  fig:cmf-all. The power-law fit was applied to the CMFs with $M > 1.2 M_\odot$, and the best-fit parameters are $\alpha = -1.92\pm0.12$ and $-1.78\pm0.12$ for `astrodendro` and `getsf`, respectively. This indicates that individual core masses are not always similar, but the shallower slope than -2.35 holds and does not significantly change our conclusion in the analysis of CMFs.

![](CMF_selected_dendro_getsf.pdf)

natexlab

(ref: Allingham24) Allingham, D., Jackson, J. M., Hogge, T., et al. 2024, PASA, 41, e079, doi: [`10.1017/pasa.2024.68`](http://doi.org/10.1017/pasa.2024.68)

(ref: Alstott14) Alstott, J., Bullmore, E., & Plenz, D. 2014, PLoS ONE, 9, e85777, doi: [`10.1371/journal.pone.0085777`](http://doi.org/10.1371/journal.pone.0085777)

(ref: Andre10) André, P., Men’shchikov, A., Bontemps, S., et al. 2010, A&A, 518, L102, doi: [`10.1051/0004-6361/201014666`](http://doi.org/10.1051/0004-6361/201014666)

(ref: Armante24) Armante, M., Gusdorf, A., Louvet, F., et al. 2024, A&A, 686, A122, doi: [`10.1051/0004-6361/202347595`](http://doi.org/10.1051/0004-6361/202347595)

(ref: Astropy_13) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy22) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Ballesteros-Paredes20) Ballesteros-Paredes, J., André, P., Hennebelle, P., et al. 2020, Space Sci. Rev., 216, 76, doi: [`10.1007/s11214-020-00698-3`](http://doi.org/10.1007/s11214-020-00698-3)

(ref: Beichman86) Beichman, C. A., Myers, P. C., Emerson, J. P., et al. 1986, ApJ, 307, 337, doi: [`10.1086/164421`](http://doi.org/10.1086/164421)

(ref: BerginTafalla07) Bergin, E. A., & Tafalla, M. 2007, ARA&A, 45, 339, doi: [`10.1146/annurev.astro.45.071206.100404`](http://doi.org/10.1146/annurev.astro.45.071206.100404)

(ref: Berry15) Berry, D. S. 2015, Astronomy and Computing, 10, 22, doi: [`10.1016/j.ascom.2014.11.004`](http://doi.org/10.1016/j.ascom.2014.11.004)

(ref: Beuther21) Beuther, H., Gieser, C., Suri, S., et al. 2021, A&A, 649, A113, doi: [`10.1051/0004-6361/202040106`](http://doi.org/10.1051/0004-6361/202040106)

(ref: Bonnell01) Bonnell, I. A., Bate, M. R., Clarke, C. J., & Pringle, J. E. 2001, MNRAS, 323, 785, doi: [`10.1046/j.1365-8711.2001.04270.x`](http://doi.org/10.1046/j.1365-8711.2001.04270.x)

(ref: Bonnel11) Bonnell, I. A., Smith, R. J., Clark, P. C., & Bate, M. R. 2011, MNRAS, 410, 2339, doi: [`10.1111/j.1365-2966.2010.17603.x`](http://doi.org/10.1111/j.1365-2966.2010.17603.x)

(ref: Bovino21) Bovino, S., Lupi, A., Giannetti, A., et al. 2021, A&A, 654, A34, doi: [`10.1051/0004-6361/202141252`](http://doi.org/10.1051/0004-6361/202141252)

(ref: CASA22) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Chambers09) Chambers, E. T., Jackson, J. M., Rathborne, J. M., & Simon, R. 2009, ApJS, 181, 360, doi: [`10.1088/0067-0049/181/2/360`](http://doi.org/10.1088/0067-0049/181/2/360)

(ref: Cheng24) Cheng, Y., Lu, X., Sanhueza, P., et al. 2024, ApJ, 967, 56, doi: [`10.3847/1538-4357/ad3c41`](http://doi.org/10.3847/1538-4357/ad3c41)

(ref: Clark21) Clark, P. C., & Whitworth, A. P. 2021, MNRAS, 500, 1697, doi: [`10.1093/mnras/staa3176`](http://doi.org/10.1093/mnras/staa3176)

(ref: Clauset09) Clauset, A., Shalizi, C. R., & Newman, M. E. J. 2009, SIAM Review, 51, 661, doi: [`10.1137/070710111`](http://doi.org/10.1137/070710111)

(ref: Coletta25-almagal) Coletta, A., Molinari, S., Schisano, E., et al. 2025, A&A, 696, A151, doi: [`10.1051/0004-6361/202452706`](http://doi.org/10.1051/0004-6361/202452706)

(ref: Contreras18) Contreras, Y., Sanhueza, P., Jackson, J. M., et al. 2018, ApJ, 861, 14, doi: [`10.3847/1538-4357/aac2ec`](http://doi.org/10.3847/1538-4357/aac2ec)

(ref: Csengeri17b_progenitor) Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 601, A60, doi: [`10.1051/0004-6361/201628254`](http://doi.org/10.1051/0004-6361/201628254)

(ref: Csengeri14) Csengeri, T., Urquhart, J. S., Schuller, F., et al. 2014, A&A, 565, A75, doi: [`10.1051/0004-6361/201322434`](http://doi.org/10.1051/0004-6361/201322434)

(ref: Fiorellino21) Fiorellino, E., Elia, D., André, P., et al. 2021, MNRAS, 500, 4257, doi: [`10.1093/mnras/staa3420`](http://doi.org/10.1093/mnras/staa3420)

(ref: Ginsburg22-ALMAIMF) Ginsburg, A., Csengeri, T., Galván-Madrid, R., et al. 2022, A&A, 662, A9, doi: [`10.1051/0004-6361/202141681`](http://doi.org/10.1051/0004-6361/202141681)

(ref: Guzman15) Guzmán, A. E., Sanhueza, P., Contreras, Y., et al. 2015, ApJ, 815, 130, doi: [`10.1088/0004-637X/815/2/130`](http://doi.org/10.1088/0004-637X/815/2/130)

(ref: Harris20_numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hennebelle12) Hennebelle, P. 2012, A&A, 545, A147, doi: [`10.1051/0004-6361/201219440`](http://doi.org/10.1051/0004-6361/201219440)

(ref: Hosek19) Hosek, Jr., M. W., Lu, J. R., Anderson, J., et al. 2019, ApJ, 870, 44, doi: [`10.3847/1538-4357/aaef90`](http://doi.org/10.3847/1538-4357/aaef90)

(ref: Hunter_matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Izumi24) Izumi, N., Sanhueza, P., Koch, P. M., et al. 2024, ApJ, 963, 163, doi: [`10.3847/1538-4357/ad18c6`](http://doi.org/10.3847/1538-4357/ad18c6)

(ref: Jessop00) Jessop, N. E., & Ward-Thompson, D. 2000, MNRAS, 311, 63, doi: [`10.1046/j.1365-8711.2000.03011.x`](http://doi.org/10.1046/j.1365-8711.2000.03011.x)

(ref: Joncour20_coreexcraction) Joncour, I., Buckner, A., Khalaj, P., Moraux, E., & Motte, F. 2020, arXiv e-prints, arXiv:2006.07830, doi: [`10.48550/arXiv.2006.07830`](http://doi.org/10.48550/arXiv.2006.07830)

(ref: kirk13_csar) Kirk, J. M., Ward-Thompson, D., Palmeirim, P., et al. 2013, MNRAS, 432, 1424, doi: [`10.1093/mnras/stt561`](http://doi.org/10.1093/mnras/stt561)

(ref: KlessenGlover23-lowmetal) Klessen, R. S., & Glover, S. C. O. 2023, ARA&A, 61, 65, doi: [`10.1146/annurev-astro-071221-053453`](http://doi.org/10.1146/annurev-astro-071221-053453)

(ref: Kong19_core) Kong, S. 2019, ApJ, 873, 31, doi: [`10.3847/1538-4357/aaffd5`](http://doi.org/10.3847/1538-4357/aaffd5)

(ref: Konyves15) Könyves, V., André, P., Men’shchikov, A., et al. 2015, A&A, 584, A91, doi: [`10.1051/0004-6361/201525861`](http://doi.org/10.1051/0004-6361/201525861)

(ref: Kroupa01) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: LeeMyers99) Lee, C. W., & Myers, P. C. 1999, ApJS, 123, 233, doi: [`10.1086/313234`](http://doi.org/10.1086/313234)

(ref: LeeHennebelle18) Lee, Y.-N., & Hennebelle, P. 2018, A&A, 611, A88, doi: [`10.1051/0004-6361/201731522`](http://doi.org/10.1051/0004-6361/201731522)

(ref: Lee20) Lee, Y.-N., Offner, S. S. R., Hennebelle, P., et al. 2020, Space Sci. Rev., 216, 70, doi: [`10.1007/s11214-020-00699-2`](http://doi.org/10.1007/s11214-020-00699-2)

(ref: LiChong20_identification) Li, C., Wang, H.-C., Wu, Y.-W., Ma, Y.-H., & Lin, L.-H. 2020, Research in Astronomy and Astrophysics, 20, 031, doi: [`10.1088/1674-4527/20/3/31`](http://doi.org/10.1088/1674-4527/20/3/31)

(ref: Li23-imf) Li, J., Liu, C., Zhang, Z.-Y., et al. 2023, Nature, 613, 460, doi: [`10.1038/s41586-022-05488-1`](http://doi.org/10.1038/s41586-022-05488-1)

(ref: Li20) Li, S., Sanhueza, P., Zhang, Q., et al. 2020, ApJ, 903, 119, doi: [`10.3847/1538-4357/abb81f`](http://doi.org/10.3847/1538-4357/abb81f)

(ref: Li22) Li, S., Sanhueza, P., Lu, X., et al. 2022, ApJ, 939, 102, doi: [`10.3847/1538-4357/ac94d4`](http://doi.org/10.3847/1538-4357/ac94d4)

(ref: Li23) Li, S., Sanhueza, P., Zhang, Q., et al. 2023, ApJ, 949, 109, doi: [`10.3847/1538-4357/acc58f`](http://doi.org/10.3847/1538-4357/acc58f)

(ref: Li24_natureas) Li, S., Sanhueza, P., Beuther, H., et al. 2024, Nature Astronomy, 8, 472, doi: [`10.1038/s41550-023-02181-9`](http://doi.org/10.1038/s41550-023-02181-9)

(ref: Lin25) Lin, S., Feng, S., Sanhueza, P., et al. 2025, ApJ, 990, 229, doi: [`10.3847/1538-4357/adf208`](http://doi.org/10.3847/1538-4357/adf208)

(ref: Lin24) Lin, S.-J., Lai, S.-P., Pagani, L., Lefèvre, C., & Thieme, T. J. 2024, A&A, 688, A118, doi: [`10.1051/0004-6361/202348529`](http://doi.org/10.1051/0004-6361/202348529)

(ref: Lin20) Lin, S.-J., Pagani, L., Lai, S.-P., Lefèvre, C., & Lique, F. 2020, A&A, 635, A188, doi: [`10.1051/0004-6361/201936877`](http://doi.org/10.1051/0004-6361/201936877)

(ref: Liu18) Liu, M., Tan, J. C., Cheng, Y., & Kong, S. 2018, ApJ, 862, 105, doi: [`10.3847/1538-4357/aacb7c`](http://doi.org/10.3847/1538-4357/aacb7c)

(ref: Louvet21) Louvet, F., Hennebelle, P., Men’shchikov, A., et al. 2021, A&A, 653, A157, doi: [`10.1051/0004-6361/202040053`](http://doi.org/10.1051/0004-6361/202040053)

(ref: Louvet24) Louvet, F., Sanhueza, P., Stutz, A., et al. 2024, A&A, 690, A33, doi: [`10.1051/0004-6361/202345986`](http://doi.org/10.1051/0004-6361/202345986)

(ref: Mai25-arxiv) Mai, X., Liu, T., Liu, X., et al. 2025, arXiv e-prints, arXiv:2509.15527, doi: [`10.48550/arXiv.2509.15527`](http://doi.org/10.48550/arXiv.2509.15527)

(ref: MaizApellaniz05) Maı́z Apellániz, J., & Úbeda, L. 2005, ApJ, 629, 873, doi: [`10.1086/431458`](http://doi.org/10.1086/431458)

(ref: Marks12) Marks, M., Kroupa, P., Dabringhausen, J., & Pawlowski, M. S. 2012, MNRAS, 422, 2246, doi: [`10.1111/j.1365-2966.2012.20767.x`](http://doi.org/10.1111/j.1365-2966.2012.20767.x)

(ref: Maschberger14) Maschberger, T., Bonnell, I. A., Clarke, C. J., & Moraux, E. 2014, MNRAS, 439, 234, doi: [`10.1093/mnras/stt2403`](http://doi.org/10.1093/mnras/stt2403)

(ref: Menshchikov13) Men’shchikov, A. 2013, A&A, 560, A63, doi: [`10.1051/0004-6361/201321885`](http://doi.org/10.1051/0004-6361/201321885)

(ref: Menshchikov21) Men’shchikov, A. 2021, A&A, 654, A78, doi: [`10.1051/0004-6361/202141533`](http://doi.org/10.1051/0004-6361/202141533)

(ref: Molinari11) Molinari, S., Schisano, E., Faustini, F., et al. 2011, A&A, 530, A133, doi: [`10.1051/0004-6361/201014752`](http://doi.org/10.1051/0004-6361/201014752)

(ref: Molinari25-almagalI) Molinari, S., Schilke, P., Battersby, C., et al. 2025, A&A, 696, A149, doi: [`10.1051/0004-6361/202452702`](http://doi.org/10.1051/0004-6361/202452702)

(ref: Mor19-imf) Mor, R., Robin, A. C., Figueras, F., Roca-Fàbrega, S., & Luri, X. 2019, A&A, 624, L1, doi: [`10.1051/0004-6361/201935105`](http://doi.org/10.1051/0004-6361/201935105)

(ref: Morii25) Morii, K., Sanhueza, P., Csengeri, T., et al. 2025, ApJ, 979, 233, doi: [`10.3847/1538-4357/ada27f`](http://doi.org/10.3847/1538-4357/ada27f)

(ref: Morii21) Morii, K., Sanhueza, P., Nakamura, F., et al. 2021, ApJ, 923, 147, doi: [`10.3847/1538-4357/ac2365`](http://doi.org/10.3847/1538-4357/ac2365)

(ref: Morii23) Morii, K., Sanhueza, P., Nakamura, F., et al. 2023, ApJ, 950, 148, doi: [`10.3847/1538-4357/acccea`](http://doi.org/10.3847/1538-4357/acccea)

(ref: Morii24) Morii, K., Sanhueza, P., Zhang, Q., et al. 2024, ApJ, 966, 171, doi: [`10.3847/1538-4357/ad32d0`](http://doi.org/10.3847/1538-4357/ad32d0)

(ref: Moser20) Moser, E., Liu, M., Tan, J. C., et al. 2020, ApJ, 897, 136, doi: [`10.3847/1538-4357/ab96c1`](http://doi.org/10.3847/1538-4357/ab96c1)

(ref: Motte18) Motte, F., Bontemps, S., & Louvet, F. 2018a, ARA&A, 56, 41, doi: [`10.1146/annurev-astro-091916-055235`](http://doi.org/10.1146/annurev-astro-091916-055235)

(ref: Motte07) Motte, F., Bontemps, S., Schilke, P., et al. 2007, A&A, 476, 1243, doi: [`10.1051/0004-6361:20077843`](http://doi.org/10.1051/0004-6361:20077843)

(ref: Motte18_natas) Motte, F., Nony, T., Louvet, F., et al. 2018b, Nature Astronomy, 2, 478, doi: [`10.1038/s41550-018-0452-x`](http://doi.org/10.1038/s41550-018-0452-x)

(ref: Motte22-ALMAIMF) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8, doi: [`10.1051/0004-6361/202141677`](http://doi.org/10.1051/0004-6361/202141677)

(ref: Nony23) Nony, T., Galván-Madrid, R., Motte, F., et al. 2023, A&A, 674, A75, doi: [`10.1051/0004-6361/202244762`](http://doi.org/10.1051/0004-6361/202244762)

(ref: Ohashi16) Ohashi, S., Sanhueza, P., Chen, H.-R. V., et al. 2016, ApJ, 833, 209, doi: [`10.3847/1538-4357/833/2/209`](http://doi.org/10.3847/1538-4357/833/2/209)

(ref: Olguin22) Olguin, F. A., Sanhueza, P., Ginsburg, A., et al. 2022, ApJ, 929, 68, doi: [`10.3847/1538-4357/ac5bd8`](http://doi.org/10.3847/1538-4357/ac5bd8)

(ref: Olguin23) Olguin, F. A., Sanhueza, P., Chen, H.-R. V., et al. 2023, ApJL, 959, L31, doi: [`10.3847/2041-8213/ad1100`](http://doi.org/10.3847/2041-8213/ad1100)

(ref: Olguin25-arxiv) Olguin, F. A., Sanhueza, P., Ginsburg, A., et al. 2025, arXiv e-prints, arXiv:2508.15889, doi: [`10.48550/arXiv.2508.15889`](http://doi.org/10.48550/arXiv.2508.15889)

(ref: Ohnishi02) Onishi, T., Mizuno, A., Kawamura, A., Tachihara, K., & Fukui, Y. 2002, ApJ, 575, 950, doi: [`10.1086/341347`](http://doi.org/10.1086/341347)

(ref: Ossenkopf94) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Padoan20) Padoan, P., Pan, L., Juvela, M., Haugbølle, T., & Nordlund, Å. 2020, ApJ, 900, 82, doi: [`10.3847/1538-4357/abaa47`](http://doi.org/10.3847/1538-4357/abaa47)

(ref: Pelkonen21) Pelkonen, V. M., Padoan, P., Haugbølle, T., & Nordlund, Å. 2021, MNRAS, 504, 1219, doi: [`10.1093/mnras/stab844`](http://doi.org/10.1093/mnras/stab844)

(ref: Pineda23) Pineda, J. E., Arzoumanian, D., Andre, P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 233, doi: [`10.48550/arXiv.2205.03935`](http://doi.org/10.48550/arXiv.2205.03935)

(ref: Pouteau22) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26, doi: [`10.1051/0004-6361/202142951`](http://doi.org/10.1051/0004-6361/202142951)

(ref: Pouteau23) Pouteau, Y., Motte, F., Nony, T., et al. 2023, A&A, 674, A76, doi: [`10.1051/0004-6361/202244776`](http://doi.org/10.1051/0004-6361/202244776)

(ref: Rathborne06) Rathborne, J. M., Jackson, J. M., & Simon, R. 2006, ApJ, 641, 389, doi: [`10.1086/500423`](http://doi.org/10.1086/500423)

(ref: Redaelli21) Redaelli, E., Bovino, S., Giannetti, A., et al. 2021, A&A, 650, A202, doi: [`10.1051/0004-6361/202140694`](http://doi.org/10.1051/0004-6361/202140694)

(ref: Redaelli22) Redaelli, E., Bovino, S., Sanhueza, P., et al. 2022, ApJ, 936, 169, doi: [`10.3847/1538-4357/ac85b4`](http://doi.org/10.3847/1538-4357/ac85b4)

(ref: Reid06) Reid, M. A., & Wilson, C. D. 2006, ApJ, 650, 970, doi: [`10.1086/507019`](http://doi.org/10.1086/507019)

(ref: Rosolowsky08) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Sabatini19) Sabatini, G., Giannetti, A., Bovino, S., et al. 2019, MNRAS, 490, 4489, doi: [`10.1093/mnras/stz2818`](http://doi.org/10.1093/mnras/stz2818)

(ref: Sabatini21) Sabatini, G., Bovino, S., Giannetti, A., et al. 2021, A&A, 652, A71, doi: [`10.1051/0004-6361/202140469`](http://doi.org/10.1051/0004-6361/202140469)

(ref: Sabatini22) Sabatini, G., Bovino, S., Sanhueza, P., et al. 2022, ApJ, 936, 80, doi: [`10.3847/1538-4357/ac83aa`](http://doi.org/10.3847/1538-4357/ac83aa)

(ref: Sakai22) Sakai, T., Sanhueza, P., Furuya, K., et al. 2022, ApJ, 925, 144, doi: [`10.3847/1538-4357/ac3d2e`](http://doi.org/10.3847/1538-4357/ac3d2e)

(ref: Salpeter55) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: Sanhueza12) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2012, ApJ, 756, 60, doi: [`10.1088/0004-637X/756/1/60`](http://doi.org/10.1088/0004-637X/756/1/60)

(ref: Sanhueza13) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2013, ApJ, 773, 123, doi: [`10.1088/0004-637X/773/2/123`](http://doi.org/10.1088/0004-637X/773/2/123)

(ref: Sanhueza17) Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, ApJ, 841, 97, doi: [`10.3847/1538-4357/aa6ff8`](http://doi.org/10.3847/1538-4357/aa6ff8)

(ref: Sanhueza19) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102, doi: [`10.3847/1538-4357/ab45e9`](http://doi.org/10.3847/1538-4357/ab45e9)

(ref: Sanhueza21) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10, doi: [`10.3847/2041-8213/ac081c`](http://doi.org/10.3847/2041-8213/ac081c)

(ref: Sanhueza25) Sanhueza, P., Liu, J., Morii, K., et al. 2025, ApJ, 980, 87, doi: [`10.3847/1538-4357/ad9d40`](http://doi.org/10.3847/1538-4357/ad9d40)

(ref: Sanna25) Sanna, A., Oliva, A., Moscadelli, L., et al. 2025, A&A, 697, A206, doi: [`10.1051/0004-6361/202450330`](http://doi.org/10.1051/0004-6361/202450330)

(ref: Shu87) Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23, doi: [`10.1146/annurev.aa.25.090187.000323`](http://doi.org/10.1146/annurev.aa.25.090187.000323)

(ref: Sollima19-imf) Sollima, A. 2019, MNRAS, 489, 2377, doi: [`10.1093/mnras/stz2093`](http://doi.org/10.1093/mnras/stz2093)

(ref: Sridharan05) Sridharan, T. K., Beuther, H., Saito, M., Wyrowski, F., & Schilke, P. 2005, ApJL, 634, L57, doi: [`10.1086/498644`](http://doi.org/10.1086/498644)

(ref: StutzkiGuesten90_gaussclump) Stutzki, J., & Guesten, R. 1990, ApJ, 356, 513, doi: [`10.1086/168859`](http://doi.org/10.1086/168859)

(ref: Suarez21) Suárez, G., Galván-Madrid, R., Aguilar, L., et al. 2021, ApJ, 921, 48, doi: [`10.3847/1538-4357/ac1bb9`](http://doi.org/10.3847/1538-4357/ac1bb9)

(ref: Tackenberg12) Tackenberg, J., Beuther, H., Henning, T., et al. 2012, A&A, 540, A113, doi: [`10.1051/0004-6361/201117412`](http://doi.org/10.1051/0004-6361/201117412)

(ref: Tafoya21) Tafoya, D., Sanhueza, P., Zhang, Q., et al. 2021, ApJ, 913, 131, doi: [`10.3847/1538-4357/abf5da`](http://doi.org/10.3847/1538-4357/abf5da)

(ref: Takemura23) Takemura, H., Nakamura, F., Arce, H. G., et al. 2023, ApJS, 264, 35, doi: [`10.3847/1538-4365/aca4d4`](http://doi.org/10.3847/1538-4365/aca4d4)

(ref: Tan14) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 149, doi: [`10.2458/azu_uapress_9780816531240-ch007`](http://doi.org/10.2458/azu_uapress_9780816531240-ch007)

(ref: Tige17) Tigé, J., Motte, F., Russeil, D., et al. 2017, A&A, 602, A77, doi: [`10.1051/0004-6361/201628989`](http://doi.org/10.1051/0004-6361/201628989)

(ref: Tokuda20) Tokuda, K., Fujishiro, K., Tachihara, K., et al. 2020, ApJ, 899, 10, doi: [`10.3847/1538-4357/ab9ca7`](http://doi.org/10.3847/1538-4357/ab9ca7)

(ref: Traficante23) Traficante, A., Jones, B. M., Avison, A., et al. 2023, MNRAS, 520, 2306, doi: [`10.1093/mnras/stad272`](http://doi.org/10.1093/mnras/stad272)

(ref: Urquhart18) Urquhart, J. S., König, C., Giannetti, A., et al. 2018, MNRAS, 473, 1059, doi: [`10.1093/mnras/stx2258`](http://doi.org/10.1093/mnras/stx2258)

(ref: Valeille-Manet25) Valeille-Manet, M., Bontemps, S., Csengeri, T., et al. 2025, A&A, 696, A11, doi: [`10.1051/0004-6361/202451291`](http://doi.org/10.1051/0004-6361/202451291)

(ref: Virtanen_scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Ward-Thompson07) Ward-Thompson, D., André, P., Crutcher, R., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 33, doi: [`10.48550/arXiv.astro-ph/0603474`](http://doi.org/10.48550/arXiv.astro-ph/0603474)

(ref: Waskom2021_seaborn) Waskom, M. L. 2021, Journal of Open Source Software, 6, 3021, doi: [`10.21105/joss.03021`](http://doi.org/10.21105/joss.03021)

(ref: Wells24) Wells, M. R. A., Beuther, H., Molinari, S., et al. 2024, arXiv e-prints, arXiv:2408.08299, doi: [`10.48550/arXiv.2408.08299`](http://doi.org/10.48550/arXiv.2408.08299)

(ref: Williams94) Williams, J. P., de Geus, E. J., & Blitz, L. 1994, ApJ, 428, 693, doi: [`10.1086/174279`](http://doi.org/10.1086/174279)

(ref: Xu24) Xu, F., Wang, K., Liu, T., et al. 2024, Research in Astronomy and Astrophysics, 24, 065011, doi: [`10.1088/1674-4527/ad3dc3`](http://doi.org/10.1088/1674-4527/ad3dc3)

[^1]: The five clumps with low completeness levels are G010.991–00.082, G014.492–00.139, G018.801–00.297, G024.010+00.489, and G028.564–00.236.

[^2]: This is mostly due to G028.564–00.236, which host 5 out of 7 cores with masses of $>$25$M_\odot$

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Compute core masses from 1.3 mm continuum flux density using Equation 1, and check optical depth at 1.3 mm using the ratio of peak intensity over beam solid angle to the Planck function.",
  "failed_quote": "The core masses are derived from the 1.3 mm dust continuum emission adopting the optically thin assumption in (cite: Morii23) as $$\begin{equation} M_\\mathrm{core} = \\mathbb{R}\frac{d^2 F_\nu}{\\kappa_\nu B_\nu (T_\\mathrm{dust})}, \\label{equ:Mass} \\end{equation}$$"
 }
]
```
