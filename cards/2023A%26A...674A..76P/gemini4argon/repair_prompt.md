# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...674A..76P\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ALMA-IMF. VI. Investigating the origin of stellar masses: Core mass function evolution in the W43-MM2&MM3 mini-starburst

Among the most central open questions regarding the initial mass function (IMF) of stars is the impact of environment on the shape of the core mass function (CMF) and thus potentially on the IMF.

The ALMA-IMF Large Program aims to investigate the variations in the core distributions (CMF and mass segregation) with cloud characteristics, such as the density and kinematic of the gas, as diagnostic observables of the formation process and evolution of clouds. The present study focuses on the W43-MM2&MM3 mini-starburst, whose CMF has recently been found to be top-heavy with respect to the Salpeter slope of the canonical IMF.

W43-MM2&MM3 is a useful test case for environmental studies because it harbors a rich cluster that contains a statistically significant number of cores (specifically, 205 cores), which was previously characterized in Paper III. We applied a multi-scale decomposition technique to the ALMA 1.3 mm and 3 mm continuum images of W43-MM2&MM3 to define six subregions, each 0.5-1 pc in size. For each subregion we characterized the high column density probability distribution function, $\eta$-PDF, and the shape of the cloud gas using the 1.3 mm image. Using the core catalog, we investigate correlations between the CMF and cloud and core properties, such as the $\eta$-PDF and the core mass segregation.

We classify the W43-MM2&MM3 subregions into different stages of evolution, from quiescent to burst to post-burst, based on the surface number density of cores, number of outflows, and ultra-compact Hii presence. The high-mass end ($>$1 $\ensuremath{M_{\odot}}$) of the subregion CMFs varies from close to the Salpeter slope (quiescent) to top-heavy (burst and post-burst). Moreover, the second tail of the $\eta$-PDF varies from steep (quiescent) to flat (burst and post-burst), as observed for high-mass star-forming clouds. We find that subregions with flat second $\eta$-PDF tails display top-heavy CMFs.

In dynamical environments such as W43-MM2&MM3, the high-mass end of the CMF appears to be rooted in the cloud structure, which is at high column density and surrounds cores. This connection stems from the fact that cores and their immediate surroundings are both determined and shaped by the cloud formation process, the current evolutionary state of the cloud, and, more broadly, the star formation history. The CMF may evolve from Salpeter to top-heavy throughout the star formation process from the quiescent to the burst phase. This scenario raises the question of if the CMF might revert again to Salpeter as the cloud approaches the end of its star formation stage, a hypothesis that remains to be tested.

# Introduction

Star formation takes place in molecular clouds, which are partly supported by thermal pressure, turbulence, and magnetic fields but are, above all, formed and shaped by gravity, stellar feedback, and Galactic motions (cite: krumholz2015; ballesteros-paredes2020). The gas reservoir available to form a star is difficult to define and depends strongly on whether the processes of cloud and star formation are quasi-static or dynamic. In the quasi-static scenario, which has long been the most generally accepted scenario, the cores are mass reservoirs for the collapse of protostars that will form a single star or, at most, a small stellar system (cite: shu1987; chabrier2003; mckeeOstriker2007). Observationally, we characterize cores as dense, $n_{\rm H_2}=10^4-10^8$ cm$^{-3}$, gravitationally bound cloud fragments that are referred to either as pre-stellar cores, when they are on the verge of collapse, or as protostellar cores, when a stellar embryo exists at the center of the collapsing core.

However, in dynamical scenarios of cloud and star formation, cores may not be the only mass reservoirs available for the collapse of protostars. In scenarios such as those described in competitive accretion, global hierarchical collapse, or inertial inflow models, the environment plays a crucial role in the assembly of core mass and the protostellar accretion of gas onto the newborn star (cite: smith2009; wang2010; vazquez2019; pelkonen2021). Clouds are observed to globally collapse toward a few, very specific sites, named filament hubs and ridges; they are cloud structures a few parsecs in size with mean volume densities similar to, or greater than, the minimum value observed for isolated starless cores, $n_{\rm H_2}=10^4$ cm$^{-3}$ (cite: schneider2010; peretto2013; busquet2013; galvanmadrid2013). Cores at these locations are fed, during both their pre-stellar and protostellar phases, by gas inflows originating from the global infall of ridges and hubs (cite: smith2009; motte2018a). In the present study, we define clouds and cores as molecular cloud structures of a few parsecs and $\sim$0.01 pc in size, respectively. Neither clouds nor cores, however, can be fully considered in isolation from their respective environment: they are dynamically evolving (cite: csengeri2011; olguin2021; sanhueza2021).

For decades, the stellar initial mass function (IMF), which characterizes the mass distribution of stars above 0.01 $M_{\odot}$, has been found to display a universal form that can be schematized by a lognormal function, peaking near $0.3~\ensuremath{M_{\odot}}$, and a power law of the form $\frac{{\rm d}N}{{\rm d}\log M} \propto M^{-1.35}$, or in its cumulative forms $N(>{\rm log}(M))\propto M^{-1.35}$, above $\sim$1$~\ensuremath{M_{\odot}}$ (cite: chabrier2005; bastian2010; hopkins2012; kroupa2013). The analogous function for cores, the core mass function (CMF), has also been long found to have a similar shape, or at least the same slope at the high-mass end as those of the canonical IMF (cite: motte1998; testi-sargent1998; enoch2008; konyves2015; konyves2020; takemura2021). These results led to the simple interpretation of a direct mapping between the CMF and the IMF. In the meantime, numerical simulations computed CMFs that also showed agreement with the IMF shape (cite: klessen2000; padoan2011) in some cases (but see (cite: smith2009)). All this taken together suggests that cores on the verge of collapse are the direct progenitors of stars and that their mass could be directly accreted, with a given efficiency, by the nascent star (cite: chabrier2005; andre2014).

More recently, however, top-heavy IMFs have been revealed in young massive clusters of the Milky Way (cite: kim2006; lu2013; maia2016; hosek2019), in nearby galaxies (cite: schneider2018), and in high-redshift galaxies (cite: smith2014; zhang2018). According to (cite: marks2012), the slope of the high-mass-end IMF could be directly related to cloud volume density for the precursors of extreme star clusters. When focusing on young, very dense, and massive Galactic clouds, (cite: motte2018b), (cite: kong2019), (cite: lu2020), and (cite: pouteau2022) all observed atypical CMFs. The CMFs of the W43-MM1 and W43-MM2&MM3 mini-starburst ridges, that of the G28.37 hub, and those of the massive clouds in the Central Molecular Zone are indeed top-heavy when compared to the canonical IMF. In detail, their CMF high-mass ends, which range from $\sim$1 $\ensuremath{M_{\odot}}$ to $\sim$100 $\ensuremath{M_{\odot}}$, can be fitted by a power law of the form $N(> \log M) \propto M^\alpha$ with $\alpha \in [-0.95;-0.85]$, compared to the canonical $\alpha_{\rm IMF} = -1.35$ Salpeter IMF slope (cite: salpeter1955). Recent numerical simulations used density-threshold-defined sink particles, which are interpreted as the numerical simulation equivalent of a forming star, and found variations in the sink mass function. In particular, the power-law index of the high-mass CMF is observed to depend on whether the initial cloud support is thermally dominated or turbulence-dominated (cite: ballesteros-paredes2015; leeHennebelle2018a; hennebelle2022).

In this framework, the ALMA-IMF[^1] Large Program (cite: motte2022) was set up to investigate the variations in the CMF with cloud characteristics, especially the density structure, which is likely related to the cloud formation process and evolutionary stage. ALMA-IMF imaged 15 massive protoclusters at different evolutionary stages and with cloud characteristics that cover a wide range in terms of mass (cite: motte2022) and density. The W43 complex hosts two such clouds, W43-MM1 and W43-MM2&MM3, whose column densities are greater than the column density threshold taken to define ridges ($>$10$^{23}$ cm$^{-2}$; (cite: hill2011; hennemann2012; nguyen2013)). These high-density, parsec-size filamentary structures have been qualified as mini-starbursts because they harbor protoclusters that efficiently form high-mass stars (cite: motte2003; louvet2014), as in other ridges or hubs (cite: nguyen2011b; galvanmadrid2013; nony2021) and in cloud complexes (cite: nguyen2016). Although they are located within 10 pc of an association of OB and Wolf-Rayet stars (cite: blum1999; bik2005), these two ridges are mainly composed of cold gas (21–28 K; see Fig. 2 of (cite: nguyen2013)). The ALMA-IMF Large Program imaged them with $\sim$0.5$\ensuremath{''}$ resolution (cite: motte2022; ginsburg2022), which corresponds to $\sim$2500 au at the $5.5$ kpc distance of W43 (cite: zhang2014). Its 1.3 mm images cover the massive clouds W43-MM1 and W43-MM2, $\sim$$1.3\times10^4~\ensuremath{M_{\odot}}$ and $\sim$$1.2\times10^4~\ensuremath{M_{\odot}}$ over 7 pc$^2$ and 6 pc$^2$, respectively, and their less massive neighbor W43-MM3, $\sim$$0.5\times10^4~\ensuremath{M_{\odot}}$ over 6 pc$^2$ (cite: motte2022). Paper III of this series (cite: pouteau2022) found that the W43-MM2&MM3 mini-starburst has an atypical CMF, with a top-heavy high-mass end with respect to the Salpeter slope of the canonical IMF.

The present study aims to investigate the CMF variations in W43-MM2&MM3 and establish the link between the CMF shape and local conditions. The variation in these conditions is quantified by estimating the median properties, density structure, and evolutionary state of the cloud, as well as the spatial distribution and mass segregation of cores. Among the statistical tools used to characterize molecular clouds, probability distribution functions (PDFs) of density and column density are one of the most widely used in both theoretical and numerical studies (cite: klessen2000; girichidis2014; leeHennebelle2018a; jaupartChabrier2020) and in observational studies (cite: kainulainen2009; schneider2012; schneider2016; schneider2022; stutzKainulainen2015). In simulations, PDFs are usually obtained from cloud volume density, while in observations they are obtained from column density ($\eta$-PDF; see the definition in Sect. [3.2](#sect:PDFs)), which can be related to radial density distributions in clouds but only in idealized cases (cite: federrathKlessen2013; myers2015). In agreement with observations, PDFs are expected to be lognormal if isothermal supersonic turbulence is dominant and to develop a power-law tail at high column densities when gravity is no longer negligible (cite: klessen2000; kainulainen2009; ballesteros-paredes2011; schneider2013; pokhrel2016). The $\eta$-PDF sometimes harbors a second, flatter tail at column densities higher than $5-10\times 10^{22}$ cm$^{-2}$ (cite: schneider2015; lin2016; schneider2022), whose nature is still a matter of debate (cite: sadavoy2014; tremblin2014; motte2018a; khullar2021; donkov2021). Because the high-column-density parts of a cloud host most of the cores, understanding the link between the tails of the $\eta$-PDF and the shape of the CMF may provide insights into the possible universality of the CMF.

As for mass segregation, it measures whether the most massive objects, in particular stars or cores, show a significantly different distribution than their lower-mass counterparts and whether they are more clustered. The mass segregation of young stars and cores is generally studied to determine whether the mass segregation observed in stellar clusters is inherited by a primordial mass segregation of cores in clouds (cite: hetem2019; dib2018segreg) or is rapidly erased through dynamical interactions of the stars and expulsion of the gas (cite: parkerMeyer2012; FujiiPortegies-Zwart2016). A dozen studies have investigated the mass segregation of 0.002–0.1 pc cloud structures, but only five found clear evidence of segregation (cite: lane2016; parker2018; plunkett2018; dibHenning2019; nony2021). (cite: dibHenning2019) and (cite: nony2021) proposed that the level of core mass segregation depends on how the gas mass is assembled to form the molecular clouds. Environmental factors could therefore have an impact on both core mass segregation and CMF shape.

![](NH2_image+cores.jpg)

![](NH2_zooms.jpg)

The paper is organized as follows: In Sect. [2](#sect:database and basic properties) we present the database used in this work, separate the W43-MM2&MM3 into six subregions, compute their column density maps, and estimate their characteristics, such as mass, volume density, and column density PDF. In Sect. [3](#sect:analysis) we then search for variations: within these six subregions, in the CMF shape, in the cloud characteristics, and in the core mass segregation. In Sect. [4](#sect:discussion) we investigate the correlation between the power-law index of the CMF high-mass end and the cloud characteristics, including the $\eta$-PDF, the spatial core distribution, and the cloud and star formation histories. We summarize the paper and present our conclusions in Sect. [5](#sect:conclusions).

![](MnGSeg-scales-1mm.png)

![](MnGSeg-scales-3mm.png)

# Database and basic properties

## Observations and core catalog

The W43-MM2&MM3 mini-starburst ridge is among the targets of the ALMA-IMF Large Program (cite: motte2022), whose observations were taken between December 2017 and December 2018. The present paper uses the 12 m array continuum images in the ALMA band 6 (1.3 mm, central frequency $\nu_{\rm c}\simeq 228.4$ GHz) and band 3 (3 mm, $\nu_{\rm c}\simeq99.66$ GHz) and the core catalog[^2] all reported in Paper III (cite: pouteau2022). Images of individual ALMA-IMF fields W43-MM2 and W43-MM3 were first cleaned using the iterative self-calibration pipeline scripts[^3] developed by the ALMA-IMF consortium and fully described in Paper II (cite: ginsburg2022). Paper III (cite: pouteau2022) used the multi-scale option of the TCLEAN task, with parameters of 0, 3, 9, 27 pixels (up to 81 at 3 mm), to minimize interferometric artifacts associated with missing short spacings. Images at 3 mm were then smoothed to the 1.3 mm synthesized beam of $\Theta_{\rm beam} \simeq 0.46\ensuremath{''}$ of both 1.3 mm fields, corresponding to $\sim$2500 au (or 0.013 pc) at the 5.5 kpc distance of W43. According to Paper II, the maximum recoverable scales are $\sim$5.6 $\ensuremath{''}$ at 1.3 mm and $\sim$8.1 $\ensuremath{''}$ at 3 mm (cite: ginsburg2022), corresponding to $\sim$0.15 pc and $\sim$0.2 pc, respectively. Because W43-MM2 and W43-MM3 share a common area in both bands, the mosaics were combined using primary-beam shape weights in Paper III (cite: pouteau2022). The multi-scale non-Gaussian segmentation technique (cite: robitaille2019) was also applied to reduce the noise level of the best-sensitivity (`bsens`) 1.3 mm and 3 mm images by $\sim$30% (cite: pouteau2022). The resulting images are qualified as `bsens``denoised`, with a continuum sensitivity of $\sim$80 $\mu$Jy$\,$beam$^{-1}$ and $\sim$21 $\mu$Jy$\,$beam$^{-1}$ at 1.3 mm and 3 mm, respectively.

Paper III identified cores by extracting compact emission peaks from their surrounding background in the ALMA 12 m array continuum images at 1.3 mm, with a $5\sigma$ sensitivity per beam unit of $\sim$0.25 $\ensuremath{M_{\odot}}$ (cite: pouteau2022). The *getsf* algorithm (cite: men2021getsf) was applied on the `denoised`, `bsens` and `cleanest` images at 1.3 mm and 3 mm that were built by using all frequency channels and selecting those without line emission, respectively (cite: pouteau2022). The *getsf* catalog at 1.3 mm was then filtered to exclude free-free emission peaks and continuum fluxes were corrected for line contamination and optically thick thermal dust emission (cite: pouteau2022). The resulting core catalog contains 205 cores, with a median size full width at half maximum (FWHM) of 3 400 au and masses, $M^{\rm core}$, ranging from 0.1 to 70 $\ensuremath{M_{\odot}}$ (see Tables E.1–E.2 of (cite: pouteau2022)). Figure [1](#fig:nh2 and cores) locates the rich protocluster of cores discovered and characterized by Paper III (cite: pouteau2022) in the W43-MM2&MM3 ridge. A companion paper, Paper V (cite: nony2023) investigates the protostellar or pre-stellar nature of the W43-MM2&MM3 cores and finds that between 41 and 51 ($46\pm5$) protostars are driving outflows or igniting hot cores.

+:---------:+:-------------:+:--------------:+:-------------------------------:+:-------------------:+:------------------------------:+:--------------:+:-------------:+:------------------------------------------:+:------------------------------------------:+
| Subregion | $A$           | $T_{\rm dust}$ | $N_{\rm H_2}$                   | $M^{\rm subregion}$ | $n_{\rm H_2}$                  | Number         | Core          | $\sum \limits_{\rm subregion}M^{\rm core}$ | $\sum \limits_{\rm subregion}M^{\rm core}$ |
+-----------+               +----------------+---------------------------------+                     |                                +----------------+---------------+                                            +--------------------------------------------+
| name      |               | range          | range                           |                     |                                | of cores       | density       |                                            | $/ M^{\rm subregion}$                      |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
|           | \[pc$^2$\]    | \[K\]          | \[$\times 10^{23}\,$cm$^{-2}$\] | \[$M_{\odot}$\]     | \[$\times 10^{3}\,$cm$^{-3}$\] | $N_{\rm core}$ | \[pc$^{-2}$\] | \[$M_{\odot}$\]                            | \[%\]                                      |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
| \(1\)     | \(2\)         | \(3\)          | \(4\)                           | \(5\)               | \(6\)                          | \(7\)          | \(8\)         | \(9\)                                      | \(10\)                                     |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
| Outskirts | $\sim$7$\pm2$ | $21-42$        | $0.1-5.5$                       | $>$120              | $>$0.07                        | $35\pm20$      | 5$\pm2$       | $26\pm2$                                   | $<22$                                      |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
| MM51      | 0.7$\pm0.3$   | $22-28$        | $0.1-8.7$                       | $>$35               | $>$25                          | 22$\pm1$       | 31$\pm18$     | $27\pm2$                                   | $<77$                                      |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
| MM10      | 0.9$\pm0.3$   | $21-40$        | $0.3-30.0$                      | $340\pm10$          | $101\pm45$                     | 41$\pm6$       | 46$\pm19$     | $61\pm4$                                   | $\sim$18                                   |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
| MM12      | 0.6$\pm0.2$   | $21-33$        | $0.1-22.0$                      | $200\pm10$          | $188\pm25$                     | 19$\pm1$       | 32$\pm14$     | $48\pm3$                                   | $\sim$24                                   |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
| MM2       | 0.8$\pm0.2$   | $20-65$        | $0.4-260.6$                     | $1300\pm20$         | $490\pm150$                    | 59$\pm11$      | 74$\pm5$      | $240\pm11$                                 | $\sim$18                                   |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
| MM3       | 0.8$\pm0.3$   | $22-35$        | $0.5-80.2$                      | $1020\pm50$         | $375\pm90$                     | 29$\pm7$       | 36$\pm6$      | $140\pm7$                                  | $\sim$14                                   |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+
| Total     | $\sim$11      | $20-65$        | $0.1-107.3$                     | $>$3000             | $>$0.5                         | 205            | 19            | $540\pm25$                                 | $<$18                                      |
+-----------+---------------+----------------+---------------------------------+---------------------+--------------------------------+----------------+---------------+--------------------------------------------+--------------------------------------------+

\(2\) Area of the subregions defined in Sect. [2.2](#sect:subregions def) (see also Figs. [1](#fig:nh2 and cores)–[2](#fig:mngseg scales)). Except for the full area, labeled as Total, the uncertainties reflect the inherent difficulty in defining the subregion outlines and are the basis for the uncertainties given in cols. 5–8.

\(3\) Temperature range measured on the dust temperature image of [12](#appendixfig:PPMAP with NH2) (cite: pouteau2022).

\(4\) Column density range measured on the column density image of [1](#fig:nh2 and cores).

\(5\) Subregion mass computed from the 1.3 mm and dust temperature images of [12](#appendixfig:PPMAP with NH2) (cite: pouteau2022) following [\[eq:optically thin mass\]](#eq:optically thin mass). These values are lower limits for the MM51 and Outskirts subregions, and for the Total region (see Sect. [2.3](#sect:subregions coldens and mass)).

\(6\) Volume densities computed from cols. 2 and 5 following [\[eq:density\]](#eq:density).

(7)–(8) Number and surface number density of cores, detected by (cite: pouteau2022), which are located over subregion areas of col. 2 (see also [2](#fig:mngseg scales)).

\(9\) Cumulative mass of cores, taken from Table E.2 of (cite: pouteau2022). Uncertainties arise from those associated with individual core mass estimates that depend on flux and temperature uncertainties, thus the ignoring uncertainties of col. 7.

\(10\) Concentration of subregion gas mass within cores computed from cols. 5 and 9.

## Splitting the W43-MM2&MM3 ridge into six subregions

As shown in [1](#fig:nh2 and cores), the W43-MM2&MM3 ridge displays an inhomogeneous gas distribution. We separated it into subregions of $\sim$0.5–1 pc scales, which, in the framework of dynamical cloud formation, would correspond to cloud subparts with more homogeneous characteristics and star formation activities than the whole cloud. To define the boundaries of these subregions, we used the MnGSeg technique developed by (cite: robitaille2019). This algorithm, based on complex wavelet decomposition, has the main objective of separating coherent structures associated with star formation from the turbulent cloud structures, which are incoherent from one scale to another and referred to as Gaussian. We used it here solely for its multi-scale decomposition ability of the `bsens` continuum images at 1.3 mm and 3 mm. Decomposed spatial scales range from the beam, $\Theta_{\rm beam}$ corresponding to $\sim$0.013 pc, to the largest scales traced by the present interferometric images, $\sim$0.15 pc at 1.3 mm and $\sim$0.2 pc at 3 mm (cite: ginsburg2022; motte2022).

Figure [2](#fig:mngseg scales) shows, for the W43-MM2&MM3 ridge, the wavelet filtered spatial scale tracing cloud structures of 0.11–0.19 pc ($4\ensuremath{''}-7\ensuremath{''}$ at 5.5 kpc), which are thus the largest traced by the ALMA-IMF configurations of the 12 m array at 1.3 mm and 3 mm. Five subregions of $\sim$0.5–1 pc sizes were identified in both Figs. [2](#fig:mngseg scales)a–b; their boundaries were visually defined by following the minimum inflection points, corresponding to minima or saddle points. Discovered as separate cloud structures in (sub)millimeter continuum images with $\sim$0.3 pc spatial resolutions, we keep their labeling that comes from the rank of their extraction (cite: motte2003). The W43-MM2&MM3 subregions identified here are thus called MM2, MM3, MM10, MM12, and MM51. Figures [2](#fig:mngseg scales)a-b are dominated by the two centrally concentrated subregions MM2 and MM3, the latter of which hosts a well-known ultra-compact (UC) Hii region (cite: nguyen2017). Additionally, Fig. [2](#fig:mngseg scales)a displays three networks of filaments with lower density: MM10, MM12, and MM51. In [2](#fig:mngseg scales)b, the bright region south of MM12, known as MM13, is mainly associated with free-free emission from an UCHii region (cite: motte2003; nguyen2017). Since this subregion was not imaged at 1.3 mm, we ignore it in the following analysis. Once the five subregions mentioned above are subtracted from the area imaged at 1.3 mm, an area remains that we call here the Outskirts subregion.

[\[tab:subregions chara\]](#tab:subregions chara) lists the characteristics of these six subregions (MM2, MM3, MM10, MM12, MM51, and Outskirts) as derived from measurements in the 1.3 mm `bsens``denoised` image obtained with the 12 m array of ALMA (see Sect. [2.1](#sect:obs and catalog)). We chose the 1.3 mm image because, unlike the 3 mm image, it is less contaminated by free-free emission. [\[tab:subregions chara\]](#tab:subregions chara) lists their spatial area, temperature and column density ranges, mass, and density, along with the basic properties of their core populations (number, surface density, and cumulative mass of cores, as well as subregion mass concentration in core mass). These values are computed in the following Sects. [2.3](#sect:subregions coldens and mass) and [3.1](#sect:spatial variations of core pop). Uncertainties are estimated by slightly varying the integration areas of Figs. [1](#fig:nh2 and cores)–[2](#fig:mngseg scales) (see [\[tab:subregions chara\]](#tab:subregions chara)) to take into account uncertainties in the definition of subregion outlines and areas.

## Subregion column density and mass estimates

Because the thermal dust emission of clouds is mostly optically thin at 1.3 mm, we computed the column densities and masses of the W43-MM2&MM3 subregions, under the assumption of optically thin thermal dust emission. The column density image of [1](#fig:nh2 and cores), $N_{\rm H_2}$, is computed from the 1.3 mm fluxes, $S_{\rm 1.3mm}^{\rm peak}$, measured in the 12 m array continuum image with a $0.46\ensuremath{''}$-beam. Using the correction for optical thickness proposed by Paper III, would only change its values by 15% toward the center of four cores (cite: pouteau2022). We used the following equation, and provide a numerical application for typical values of $S_{\rm 1.3mm}^{\rm peak}$, dust temperature and opacity per unit (gas $+$ dust) mass column density at 1.3 mm, $T_{\rm dust}$ and $\kappa_{\rm 1.3mm}$. After the numerical application using the Planck function, the dependence on each physical variable is given, for simplicity, in the Rayleigh-Jeans approximation: $$\begin{equation}
    \begin{split}
    N_{\rm H_2}\; [{\rm cm}^{-2}] \: &=  \frac{S_{\rm 1.3mm}^{\rm peak}}{ \Omega_{\rm beam}\;\mu\,m_{\rm H} \: \kappa_{\rm 1.3mm}\: B_{\rm \tiny 1.3mm}(T_{\rm dust})} + N_{\rm H_2}^{\rm bckg} \\
    &\simeq\:  1.3\times10^{23}~{\rm cm^{-2}} \times \left(\frac{S_{\rm 1.3mm}^{\rm peak}}{\rm mJy\, beam^{-1}}\right)
    \, \left(\frac {T_{\rm dust}}{\rm 23~K}\right)^{-1}\\
    & \times
     \left(\frac {\kappa_{\rm 1.3\,mm}}{\rm 0.01\,cm^2\, g^{-1}}\right)^{-1}
    + 0.7\times10^{23}~\rm cm^{-2},
    \end{split}
\label{eq:nh2 region} 
\end{equation}$$ where $\Omega_{\rm beam}=\frac{\pi \; 0.51\ensuremath{''} \times 0.40\ensuremath{''}}{4\,\ln{2}}$ is the beam solid angle, $\mu = 2.8$ is the mean molecular weight per hydrogen molecule (assuming an helium abundance of 10%), $m_{\rm H}$ is the mass of atomic hydrogen, $B_{\rm \tiny 1.3mm}(T_{\rm dust})$ is the Planck function for $T_{\rm dust}$ at $\nu_{\rm 1.3mm}$, and $N_{\rm H_2}^{\rm bckg}$ is the background column density, filtered by ALMA observations.

The dust temperature image is taken from Paper III (cite: pouteau2022), with values ranging from 20 K to 65 K (see [12](#appendixfig:PPMAP with NH2)). It has an angular resolution of $2.5\ensuremath{''}$ over the majority of the map but of $0.46\ensuremath{''}$ toward the protostellar cores (cite: pouteau2022). The frequency $\nu_{\rm 1.3mm} = 228.9$ GHz is taken from Paper II (cite: ginsburg2022) assuming a spectral index of $3.5;$ which corresponds to a spectral index of $\beta = 1.5$ for the dust opacity and which is suitable for optically thin dense gas (cite: andre1993; juvela2015). Because the W43-MM2&MM3 ridge is a dense cloud (cite: nguyen2013), we adopted a dust opacity per unit (gas $+$ dust) mass at 1.3 mm and adapted for cold cloud structures: $\kappa_{\rm 1.3mm}=0.01\,\rm cm^2\,g^{-1}$ (cite: OssenkopfHenning1994). This dust opacity corresponds to that of dust grains that have developed thick ice mantles during a cold phase preceding the strong (external) heating of the W43-MM2&MM3 ridge by the OB and Wolf-Rayet stellar cluster (cite: blum1999). This value should be adapted even for the Outskirts region, whose 1.3 mm flux restored by our interferometric image is constituted, for a large fraction, of the sum of core fluxes (see [\[tab:subregions chara\]](#tab:subregions chara)).

Since, due to interferometer filtering, scales larger than $\sim$5.6$\ensuremath{''}$ are missing (see Sect. [2.1](#sect:obs and catalog)), we added a $N_{\rm H_2}^{\rm bckg}\sim 0.7\times10^{23}~\rm cm^{-2}$ level measured at the periphery of the cloud ridge on the *Herschel* column density image[^4], with $25\ensuremath{''}$ resolution, by (cite: nguyen2013). Figure [13](#appendixfig:pdf W43 herschel)a compares the $\eta$-PDF (see definition in Sect. [3.2](#sect:PDFs)) of the column density images derived from the present ALMA data (see above) and these *Herschel* data. It shows that a value of $N_{\rm H_2}^{\rm bckg}\sim 0.7\times10^{23}~\rm cm^{-2}$ indeed allows these $\eta$-PDF functions to be consistent with each other. This first-order correction probably overestimates, by up to $\sim$$0.15\times10^{23}~\rm cm^{-2}$, the column density values in low-density subregions such as Outskirts and MM51, and underestimates it, by up to $\sim$$0.3\times10^{23}~\rm cm^{-2}$, in centrally concentrated subregions such as MM2 and MM3. We therefore assumed a different background column density for each subregion: $N_{\rm H_2}^{\rm bckg} = (0.55\pm 0.10) \times10^{23}~\rm cm^{-2}$ for Outskirts and MM51, $N_{\rm H_2}^{\rm bckg} = (0.70\pm 0.15) \times10^{23}~\rm cm^{-2}$ for MM10 and MM12, and $N_{\rm H_2}^{\rm bckg} = (1.0\pm 0.2) \times10^{23}~\rm cm^{-2}$ for MM2 and MM3. Future studies will be performed on maps combining present ALMA 12 m array data with ALMA-IMF data of the 7 m array and total power antennas. Their reduction and combination is not simple but the ALMA-IMF consortium is working on it (cite: ginsburg2022; cunningham2023). Figure [1](#fig:nh2 and cores) presents the resulting column density image of the W43-MM2&MM3 ridge, with $N_{\rm H_2}$ values varying from $\sim$1$\times10^{22}~\rm cm^{-2}$, in region where missing large-scale emission creates interferometric artifacts consisting of negative bowls, to $\sim$2.6$\times10^{25}~\rm cm^{-2}$ toward the peak of MM2. This column density image is consistent with the one of Dell’Ova et al. (in prep.), which was produced by the point process mapping of the temperature (PPMAP) procedure (cite: marsh2015) and achieves a $2.5\ensuremath{''}$ resolution. Except for the column density range of each subregion, measurements performed in Tables [\[tab:subregions chara\]](#tab:subregions chara)–[\[tab:cmf and s\]](#tab:cmf and s) do not depend on the exact value chosen for the background column density.

Subregion masses, $M^{\rm subregion}$, are computed from the 1.3 mm peak fluxes and dust temperatures measured for each pixel $i$ within the subregion area $A$, $\left(S^{\rm peak}_{\rm 1.3\,mm} \right)_{\rm i}$ and $(T_{\rm dust})_{i}$ read in images provided by Paper III (cite: pouteau2022). We used the following equation: $$\begin{equation}
    \begin{split}
    M^{\rm subregion} \; [\ensuremath{M_{\odot}}] \: &= \sum \limits_{\rm pixel\, i}\limits^{A} \frac{ \left(S^{\rm peak}_{\rm 1.3\,mm} \right)_{\rm i} \; d^2}{ \kappa_{\rm 1.3\,mm}\; B_{\rm 1.3\,mm}\left[(T_{\rm dust})_{i}\right]} \times \frac{\Omega_{\rm pixel}}{\Omega_{\rm beam}},
    \end{split}
\label{eq:optically thin mass}
\end{equation}$$ where $d$ is the $5.5$ kpc distance of W43 (cite: zhang2014) and $\Omega_{\rm pixel}=(0.1\ensuremath{''})^2$ is the pixel area of our images. Subregion masses, listed in [\[tab:subregions chara\]](#tab:subregions chara), range from $\sim$$35~\ensuremath{M_{\odot}}$ to $\sim$$1\,300~\ensuremath{M_{\odot}}$. We assumed that the ALMA-IMF configurations filter out the emission of the cloud surrounding each subregion. This assumption is correct for the centrally concentrated subregions MM2, MM3, MM10, and MM12, but totally incorrect for the MM51 and Outskirts subregions as well as the total imaged area.

Volume densities of subregions are computed assuming a spherical geometry and a line-of-sight radius equal to the equivalent plane-of-the-sky radius of its defined area, $A$: $$\begin{equation}
    \begin{split}
    n_{\rm H_2} \; [{\rm cm}^{-3}] &= \frac{1}{\mu\;m_{\rm H}} \times \frac{M^{\rm subregion}}{\frac{4}{3}\pi \; \left(\frac{A}{\pi}\right)^{3/2}} \\
    &\simeq 2.1\times 10^5\,{\rm cm}^{-3} \times \left( \frac{M^{\rm subregion}}{10^3~\ensuremath{M_{\odot}}}\right) \left( \frac{A}{1~{\rm pc}^2} \right)^{-3/2}.
    \end{split}
    \label{eq:density}
\end{equation}$$ The volume densities for MM10, MM51, and Outskirts are uncertain because the spherical assumption is more questionable for these subregions, and even more important for Outskirts, because its size along the line of sight is poorly approximated by the equivalent radius of its defined area. Uncertainties given for $M^{\rm subregion}$ and $n_{\rm H_2}$ take into account uncertainties in the definition of subregion outlines, which constitute the relative uncertainties from one subregion to another. We estimate that the absolute uncertainties in column densities, subregion masses, and volume densities arise primarily from our poor knowledge of the absolute value of the dust opacity per unit mass and are a factor of about two.

In summary, the W43-MM2&MM3 ridge consists of six subregions with a large diversity of environments. They have maximum column densities, masses, and volume densities covering more than one order of magnitude: $6-110 \times 10^{23}$ cm$^{-2}$, $35-1\,300~\ensuremath{M_{\odot}}$, and $0.07-500 \times 10^{3}$ cm$^{-3}$ (see [\[tab:subregions chara\]](#tab:subregions chara)).

# Analysis

Paper III (cite: pouteau2022) studied the CMF of the W43-MM2&MM3 mini-starburst ridge and revealed it is top-heavy with respect to the Salpeter slope of the canonical IMF (cite: salpeter1955; kroupa2002). We here investigate variations throughout the W43-MM2&MM3 subregions of the core properties and cloud density structure (see Sects. [3.1](#sect:spatial variations of core pop)–[3.3](#sect:mass segregation)), with the aim of searching for correlations between them in Sect. [4](#sect:discussion). [\[tab:cmf and s\]](#tab:cmf and s) provides the parameters (fit ranges and power-law indices) characterizing the CMF and $\eta$-PDF of the W43-MM2&MM3 subregions studied in Sects. [3.1](#sect:spatial variations of core pop)–[3.2](#sect:PDFs). It also gives measurements of the protostellar fraction of their core population and an estimation of their evolutionary stage, performed in Sects. [3.1](#sect:spatial variations of core pop) and [4.3](#sect:link with sf history).

## Spatial variations in the core populations

We have taken advantage of the good statistics allowed by the large core catalog of Paper III (cite: pouteau2022) to examine whether the core mass range of one subregion is statistically differentiable from another (see Sect. [3.1.1](#sect:core populations)) and whether the CMF is top-heavy everywhere in the W43-MM2&MM3 ridge (see Sect. [3.1.2](#sect:CMFs)).

### Subregion core populations

We separated the 205 cores of W43-MM2&MM3 into six core populations associated with the subregions defined in Sect. [2.2](#sect:subregions def). The numbers of cores hosted in the subregions range from $19\pm1$ for MM12 to $59\pm11$ for MM2, the most massive, the densest, and therefore also the most populated subregion of W43-MM2&MM3 (see [\[tab:subregions chara\]](#tab:subregions chara)). Cores are not evenly spatially distributed, with surface number densities varying from 5 pc$^{-2}$ to 74 pc$^{-2}$. As for the concentration of the subregion mass within cores, it is similar within the subregions, $\sum \limits_{\rm subregion}M^{\rm core}/ M^{\rm subregion}\sim 18\%$, in agreement with the values measured for ALMA-IMF clouds qualified as Young (see [\[tab:subregions chara\]](#tab:subregions chara) and Table 5 of (cite: motte2022)). The completeness levels of each subregion catalog were estimated from the core extraction simulations of Paper III (cite: pouteau2022). They vary from $\sim$0.45$\pm 0.2~\ensuremath{M_{\odot}}$ to $\sim$1.1$\pm 0.2~\ensuremath{M_{\odot}}$ for the Outskirts and MM2 subregions, respectively and are listed in [\[tab:cmf and s\]](#tab:cmf and s).

We used the protostellar versus pre-stellar core nature determined by Paper V (cite: nony2023) to compute the fraction of protostellar cores, $f_{\rm proto}$, in the six W43-MM2&MM3 subregions: $$\begin{equation}
    f_{\rm proto}= N_{\rm proto}/N_{\rm core},
\end{equation}$$ where $N_{\rm proto}$ and $N_{\rm core}$ are the number of protostellar cores and the total number of cores including protostellar and pre-stellar cores. On average, the protostellar fraction above the $90\%$ completeness levels of core catalogs is $f_{\rm proto} \simeq 30\%$ (see [\[tab:cmf and s\]](#tab:cmf and s)). While the protostellar fraction is enhanced, $f_{\rm proto} \simeq 40\%$, in the MM2 and MM12 subregions, it is significantly low, $f_{\rm proto} < 10\%$, in the Outskirts.

![](SubregionMass-CoreMass.png)

+:----------------:+:----------------:+:-----------------------:+:------------------------------:+:------------------------------:+:------------:+:------------------------------:+:------------:+:------------:+:------------:+
| Subregion        | Core mass        | $\alpha$                | $N_{\rm H_2}^{\rm bckg}$       | Fitted                         | $s_2$        | Fitted                         | $s_3$        | Protostellar | Evolutionary |
+------------------+------------------+                         +--------------------------------+--------------------------------+              +--------------------------------+              +--------------+--------------+
| name             | range            |                         | offset                         | range ($s_2$)                  |              | range ($s_3$)                  |              | fraction     | stage        |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
|                  | \[$M_{\odot}$\]  |                         | \[$\times 10^{21}$ cm$^{-2}$\] | \[$\times 10^{21}$ cm$^{-2}$\] |              | \[$\times 10^{21}$ cm$^{-2}$\] |              | \[%\]        |              |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| \(1\)            | \(2\)            | \(3\)                   | \(4\)                          | ( 5)                           | \(6\)        | \(7\)                          | \(8\)        | \(9\)        | \(10\)       |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| **CMF high-mass ends close to the Salpeter slope or steeper**                                  |                                |              |                                |              |              |              |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| Outskirts        | $0.45-3.4$       | $-1.54_{-0.42}^{+0.32}$ | $55\pm10$                      | 100–550                        | $>-5$        | –                              | –            | $7\%\pm1$    | Quiescent    |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| MM51             | $0.6-4.3$        | $-1.17_{-0.35}^{+0.18}$ | $55\pm10$                      | 100–250                        | $>-5$        | 250–900                        | $-0.8\pm0.2$ | $25\%\pm5$   | Quiescent    |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| MM10             | $0.65-11.2$      | $-1.16_{-0.30}^{+0.16}$ | $70\pm15$                      | 100–300                        | $-2.4\pm0.2$ | 300–3000                       | $-0.9\pm0.3$ | $21\%\pm2$   | Pre-burst?   |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| **Top-heavy CMFs**                  |                         |                                |                                |              |                                |              |              |              |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| MM12             | $0.75-17.8$      | $-0.95_{-0.36}^{+0.15}$ | $70\pm15$                      | 100–500                        | $-2.1\pm0.3$ | 500–2200                       | $-0.1\pm0.2$ | $41\%\pm5$   | Main-burst?  |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| MM2              | $1.1-69.9$       | $-0.93_{-0.21}^{+0.11}$ | $100\pm20$                     | 150–1000                       | $-0.6\pm0.2$ | 1000–26 000                    | $-0.2\pm0.3$ | $37\%\pm2$   | Main burst   |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| MM3              | $1.1-44.6$       | $-0.59_{-0.12}^{+0.07}$ | $100\pm20$                     | 150–1200                       | $-0.8\pm0.2$ | 1200–8000                      | $-0.7\pm0.3$ | $22\%\pm3$   | Post-burst   |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+
| Total            | $0.8-69.9$       | $-0.93_{-0.10}^{+0.07}$ | $70\pm15$                      | 100–1000                       | $-0.9\pm0.3$ | 1000–26 000                    | $-0.3\pm0.2$ | $27\%\pm3$   | –            |
+------------------+------------------+-------------------------+--------------------------------+--------------------------------+--------------+--------------------------------+--------------+--------------+--------------+

\(2\) Mass range used to fit a power law to the subregion CMF. The lower limit of this mass range is the 90% completeness limit of each subregion, with an error of $\pm 0.2~\ensuremath{M_{\odot}}$ (cite: pouteau2022). Its upper limit corresponds to the maximum mass of cores detected in the subregion.

\(3\) Power-law index of the high-mass end of the subregion CMF in its cumulative form, $N(> \log M) \propto M^\alpha$, measured over the mass range of col. 2. Uncertainties are estimated by taking into account the fit uncertainties associated with the small-sample statistics, the completeness limit uncertainty of col. 2, and by varying core masses according to flux, dust temperature, and emissivity uncertainties (see Sect. [3.1.2](#sect:CMFs)).

\(4\) Column density offset assumed to correspond to the background of each subregion and used in [\[eq:nh2 region\]](#eq:nh2 region) to compute their PDF (see Sect. [2.3](#sect:subregions coldens and mass)).

\(5\) and (7) Ranges of column density used to fit two consecutive power laws to the subregion $\eta$-PDF tail. The limits of these ranges are defined in Sect. [3.2](#sect:PDFs).

\(6\) and (8) Power-law indices of second an third tails of the subregion $\eta$-PDF, $p_\eta \propto (N_{\rm H_2})^s$ (see Sect. [3.2](#sect:PDFs)), measured over the column density ranges of cols. 5 and 7, respectively. Uncertainties are estimated by varying the number of bins, the limits of the fitted ranges, and the column density offset of col. 4.

\(9\) Protostellar fraction of the core catalog above $0.8~\ensuremath{M_{\odot}}$, as derived from the pre-stellar versus protostellar nature of cores determined by (cite: nony2023).

\(10\) Subregion evolutionary stage defined in Sect. [4.3](#sect:link with sf history), based on the ratio of pre-stellar versus protostellar cores (col. 9), the surface number density of cores (col. 8 of [\[tab:subregions chara\]](#tab:subregions chara)), and the presence of Hii regions.

Figure [3](#fig:subregion mass vs core mass) displays, for the W43-MM2&MM3 subregions, their mass as a function of the individual and integrated masses of the cores they host. A correlation trend appears between the total mass of the subregions and the integrated mass of the cores within them, in agreement with the almost constant concentration of the subregion mass into cores discussed above. Moreover, the most massive regions, MM2 and MM3, host the most massive cores (see [3](#fig:subregion mass vs core mass)). A similar correlation was observed by (cite: motte2022) for cores in the ALMA-IMF clouds, and also by (cite: lin2019) for structures mostly on larger scales than cores. In that respect, the MM10 subregion is an exception among the four subregions more massive than $200~\ensuremath{M_{\odot}}$ because its most massive core is only $\sim$11.5 $\ensuremath{M_{\odot}}$ and its median mass is 1.5 times lower (see [3](#fig:subregion mass vs core mass) and [\[tab:cmf and s\]](#tab:cmf and s)). At the opposite side of the core mass range, the population of low-mass cores with respect to intermediate-mass cores appears to be under-numerous in the MM3 subregion compared with other W43-MM2&MM3 subregions. We ran a two-sample Kolmogorov-Smirnov (KS) test to assess the likelihood that two distributions are drawn from the same parent sample (null hypothesis). In the case of the MM3 subregion, the KS test provides significant evidence that its core sample is drawn from a different population than the complementary core catalog consisting of all cores of the MM2, MM10, MM12, MM51, and Outskirts subregions (with a KS statistic of 0.3 and a p-value of $p = 0.014$).

We have therefore observed correlation trends of the mass of the subregion with the integrated mass of the cores they host as well as with the mass of their most massive core. However, the small number of W43-MM2&MM3 subregions and the large uncertainties in the masses prevent us from making a reliable estimate of the significance and strength of these correlations. Similar analysis performed for the 15 clouds observed by the ALMA-IMF Large Program should allow us to analyze these potential relationships and their implications.

![](CMF_stack_salpeter.png)

![](CMF_stack_top-heavy.png)

![](bootstrap_KSmetric_subreg.png)

### Varying subregion CMFs

Figure [4](#fig:various cmfs) presents the CMFs of the six W43-MM2&MM3 subregions, in comparison to that of the total imaged area covering the main part of the ridge, where cores are expected to form. The latter was published by Paper III (cite: pouteau2022) and referred to as the CMF of the W43-MM2&MM3 ridge. As shown in [4](#fig:various cmfs)b, the ridge CMF is primarily from the MM2 subregion, which accounts for $\sim$45% of the total subregion mass and of the total mass into cores (see [\[tab:subregions chara\]](#tab:subregions chara)). The second largest contributor to the W43-MM2&MM3 CMF is the MM3 subregion, with 35% of the total subregion mass and 25% of the mass into cores (see [\[tab:subregions chara\]](#tab:subregions chara)).

The CMFs of all six subregions are presented in their complementary cumulative distribution form (cumulative form, for short) and fitted by single power laws of the form $N(> \log M) \propto M^\alpha$, from their 90% completeness limits to the mass of their most massive core (see [\[tab:cmf and s\]](#tab:cmf and s)). To do so, we used the maximum likelihood estimation (MLE) method of (cite: clauset2009) and (cite: alstott2014), which is based on the KS metric and dedicated to probability laws fitted by power laws. Given the small-number statistics for the core sample of each W43-MM2&MM3 subregion, we did not directly apply the (cite: alstott2014) method to their CMF but used it in a bootstrap procedure that simultaneously estimates the most likely CMF power-law index and its uncertainty. In detail, for each subregion, we computed the bootstrapping probability density function of 5000 slopes of CMF high-mass ends, which are fitted by power laws using the (cite: alstott2014) method. These synthetic CMFs are built from core samples generated from a random draw with discount of the observed core sample of each W43-MM2&MM3 subregion. To account for uncertainties associated with the core mass estimates, the mass of each randomly drawn core is allowed to vary in a $2\sigma$ Gaussian range of $[M_{\rm min}-M_{\rm max}]$. Here, $M_{\rm max}$ and $M_{\rm min}$ are the maximum and minimum masses, respectively, of each core as computed from its measured flux, estimated temperature, and dust opacity, plus or minus their associated $1\,\sigma$ uncertainties (see Tables E.1–E.2 and Sect. 5.1 of (cite: pouteau2022)). To account for the uncertainty associated with the sample incompleteness, we used the ability of the (cite: alstott2014) method to fit the initial point of the power-law fit. We allowed the fit of the initial point of the power-law fit to uniformly vary from the 90% completeness level, plus or minus its uncertainty, $\pm 0.2~\ensuremath{M_{\odot}}$ (see [\[tab:cmf and s\]](#tab:cmf and s)). Given that most cores are intermediate-mass and pre-stellar (with $T_{\textrm{dust}}\simeq 23\pm3$ K; see [12](#appendixfig:PPMAP with NH2)) taking a constant dust temperature for all cores, including the most massive ones associated with hot cores, would change the power-law indices fitted to the subregion CMF by at most $18\%$.

Figure [5](#fig:BS subreg) shows the bootstrapping probability density functions of the six W43-MM2&MM3 subregions. The peak of these functions locate the most likely power-law index of their CMF high-mass ends, which vary from $\alpha=-1.54$ for the Outskirts to $\alpha=-0.59$ for the MM3 subregion (see [\[tab:cmf and s\]](#tab:cmf and s)). To account for the asymmetry of these bootstrapping functions, their histograms are fitted by exponentially modified Gaussians (EMGs) with a negative skewness. For each subregion, uncertainties on the power-law index, $-\sigma$ and $+\sigma$, are estimated as the ranges of indices that are below and above, respectively, the peak of the bootstrapping probability density function and contain 68.2% of the fitted indices. In W43-MM2&MM3 subregions, uncertainties range from $\sigma=0.07$ to $\sigma=0.42$, with lower limits about 1.8 times larger than higher limits. The power-law indices and uncertainties derived by this bootstrapping procedure are reported in [4](#fig:various cmfs) and [\[tab:cmf and s\]](#tab:cmf and s). To test the validity of our approach, we compared the power-law index fitted by the bootstrapping procedure described above with those directly fitted by the method of (cite: alstott2014) and a linear regression on its cumulative form. The W43-MM2&MM3 ridge, whose cumulative CMF was studied by Paper III (cite: pouteau2022), has a CMF high-mass end with a sufficiently high number statistics for this purpose. The power-law index we measured with our bootstrapping procedure, $\alpha=-0.93_{-0.10}^{+0.07}$, is consistent with those fitted by the method of (cite: alstott2014) and by linear regression, $\alpha_{\rm Alstott}=-0.96\pm0.11$ and $\alpha_{\rm LinReg}=-0.95\pm0.04$, respectively.

According to [\[tab:cmf and s\]](#tab:cmf and s) and [5](#fig:BS subreg), there is a continuous flattening of the power-law indices measured for the CMF high-mass end of W43-MM2&MM3 subregions. First, the Outskirts have a power-law index steeper than, but still consistent with, the slope of the Salpeter’s IMF: $\alpha=-1.54_{-0.42}^{+0.32}$ compared to $\alpha_{\rm IMF}=-1.35$. Second, the MM10 and MM51 subregions have CMF high-mass ends close to the Salpeter slope, $\alpha \simeq -1.16_{-0.32}^{+0.17}$. Third, the MM2 and MM12 subregions present top-heavy CMFs with similar power-law indices, $\alpha \simeq -0.94_{-0.28}^{+0.13}$. And fourth, the MM3 subregion displays the flattest CMF with an irregular shape, $\alpha = -0.59_{-0.12}^{+0.07}$. These subregions are separated in [\[tab:cmf and s\]](#tab:cmf and s) but they do not constitute distinct groups because of the index ranges allowed by the power-law uncertainties as defined by the bootstrap procedure overlap (see Figs. [5](#fig:BS subreg) and [14](#appendixfig:EMG subreg)). Since the core catalogs of the Outskirts, MM51, and MM12 subregions have small-number statistics, their CMF high-mass end is barely constrained. As for the subregions with larger statistics, MM2, MM3, and MM10, they present more robust CMFs that can be considered different, although not completely separate, in terms of the power-law index of their high-mass end (see [14](#appendixfig:EMG subreg)).

![](PDF_full.png)

## Varying column density $\eta$-PDFs

To trace the density structure of the W43-MM2&MM3 molecular cloud and its variations within subregions, we used PDFs applied to column density images. Column densities are typically estimated from maps of the dust continuum emission (cite: schneider2012; stutzKainulainen2015) but some studies also used dust extinction (cite: kainulainen2009; alves2014) and even molecular line emission (cite: carlhoff2013; schneider2016). In the present study, we used three column density images. The first column density image is built from the W43-MM2&MM3 mosaic observed with the ALMA 12 m array (see Sect. [2.3](#sect:subregions coldens and mass)), and the second one from the background image of its cores as defined by *getsf* (cite: men2021getsf) and which corresponds to this same image minus the emission of the cores (see column density image and core locations in [1](#fig:nh2 and cores)). The third column density image, provided by the HOBYS[^5] consortium, is computed from *Herschel* images of the W43-Main cloud (cite: nguyen2013). While the two column density images derived from ALMA data cannot constrain the low and intermediate column density emission of the W43-MM2&MM3 mini-starburst, the *Herschel* column density image does not have sufficient angular resolution to trace very high column densities. For each subregion, we analyzed the PDF of the ALMA image and used the PDF of the background image of its cores to define the column density range where cores dominate and estimate the variation in the power-law exponents of the PDF tail with and without cores. We also used the PDF of the *Herschel* image to confirm that the first tail of the W43-MM2&MM3 PDF is not observable by the present ALMA data.

The PDFs of star-forming regions are generally described as the sum of a lognormal function at low column densities and a power-law function at higher column densities (see, e.g., (cite: froebrichRowles2010; schneider2013; schneider2022), and the automatic method proposed by (cite: veltchev2019)). The power-law tail is characterized from the point of differentiation of the PDF from a lognormal function, observed to vary from $\sim$$1\times 10^{21}$ cm$^{-2}$ to $\sim$$40\times 10^{21}$ cm$^{-2}$ (cite: schneider2022). Our ability to determine the exact value of this departure point depends strongly on whether the lognormal is correctly described in the data (cite: Ossenkopf-Okada2016; alves2017). When PDFs are contaminated by low noise levels and/or background or foreground emissions from diffuse clouds, they have their lognormal function and their departure point modified but their power-law tail almost unchanged. In contrast, column density maps computed from interferometric images do not trace the low intensity, large-scale emission associated with the cloud, and as a consequence the measured departure point of the PDF tail and the absolute value of its power-law exponent are uncertain (cite: Ossenkopf-Okada2016). In order to correct for the interferometric filtering effects at first order, we added to our ALMA 12 m array image different column density offsets simulating the varying background of the W43-MM2&MM3 subregions (see Sect. [2.3](#sect:subregions coldens and mass)). We also used the uncertainty of these offsets to investigate the variation of power-law exponents describing the PDF tail. All these elements taken together provide a good estimate of the uncertainty on the characterization of the PDF tail when using present interferometric images of W43-MM2&MM3.

The PDF of the column density, N-PDF, is a histogram of discretized probabilities of finding gas in the column density ranges \[$b_1$;$b_2$\]: $$\begin{equation}
    p_{N_{\rm H_2}} (N_{\rm H_2}\in [b_1;b_2]) = \int^{b_2}_{b_1} p_{N_{\rm H_2}} ~{\rm d}N_{\rm H_2}.
\end{equation}$$ To make the sum of all probabilities equal to one, the numbers of map pixels in the $[b_1;b_2]$ range are normalized by the total number of map pixels. Observations generally analyze the PDF of the natural logarithm of the normalized column density, $\eta \equiv \ln{(N_{\rm H_2}/ \overline{N_{\rm H_2}})}$ with $\overline{N_{\rm H_2}}$ the mean column density, and fit the PDF with power laws of exponent $s$: $$\begin{equation}
    p_\eta = N_{\rm H_2}\times p_{N_{\rm H_2}} \propto (N_{\rm H_2})^s .
\end{equation}$$ Figure [6](#fig:various eta-PDF) displays the $\eta$-PDF derived from the ALMA images of the W43-MM2&MM3 subregions. These $\eta$-PDFs exhibit a peaked distribution around the selected value of $N_{\rm H_2}^{\rm bckg}$, from $0.55\times 10^{23}$ cm$^{-2}$ to $1.0 \times 10^{23}$ cm$^{-2}$ (see [\[tab:cmf and s\]](#tab:cmf and s)). At much higher column densities than the PDF peak typically derived from *Herschel* images of clouds, $0.1-15\times 10^{21}$ cm$^{-2}$ (cite: schneider2022), the $\eta$-PDF peaks derived from our ALMA data (see Figs. [6](#fig:various eta-PDF)a–f) cannot be interpreted as the lognormal function associated with turbulent gas. Rather, they correspond to the remaining information associated with the W43-MM2&MM3 background, which is largely filtered out in our interferometric image and lies mostly outside our small imaged area (cite: lin2016). This is confirmed in [13](#appendixfig:pdf W43 herschel)a by comparison with the $\eta$-PDF obtained from the *Herschel* column density image of W43-Main (cite: nguyen2013).

We used the procedure of (cite: schneider2022) and fit the *Herschel* $\eta$-PDF by the sum of a lognormal function at column densities lower than $1.5\times10^{23}~\rm cm^{-2}$ and two consecutive tails (see [13](#appendixfig:pdf W43 herschel)b). The W43-Main $\eta$-PDF has a lognormal distribution that peaks at $\sim$25$\times 10^{21}$ cm$^{-2}$, consistent with but slightly higher than the column density peaks observed in other less dense clouds (cite: froebrichRowles2010; schneider2022). As for the $\eta$-PDF tail of W43-Main, it is fitted by two power laws, the second of which is measured on column densities reasonably close to those traced by ALMA, $0.6-4\times10^{23}$ cm$^{-2}$ versus $1-10\times10^{23}$ cm$^{-2}$ (see [13](#appendixfig:pdf W43 herschel)b and [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)).

At column densities higher than their peak, the ALMA $\eta$-PDFs of most W43-MM2&MM3 subregions exhibit a tail with a continuous flattening that we describe by two consecutive tails and fit by power laws (see [6](#fig:various eta-PDF)). These two ALMA $\eta$-PDF tails are called second and third tails ($s_2$ and $s_3$) because the first $\eta$-PDF tail ($s_1$) observed with *Herschel* data is filtered by the ALMA interferometer. We explain below the method used to define the column density ranges of these tails, whose boundaries are called departure or end points and whose associated pixels of the column density map are located between the contours in Figs. [1](#fig:nh2 and cores)b–c and [12](#appendixfig:PPMAP with NH2). We first symmetrized the ascending distribution of each ALMA $\eta$-PDF, badly fitted by a lognormal, and define the first departure point of the $\eta$-PDF tail as the first bin higher by 50% with respect to the symmetrized function (and $100\times 10^{21}$ cm$^{-2}$ otherwise). Then, the second departure point is on the one hand considered the first inflection point observed on the $\eta$-PDF tail of the subregions MM51, MM10, and MM12 (see Figs. [6](#fig:various eta-PDF)b–d). It actually corresponds to the maximum column density of the background image of cores in these three subregions. For MM2 and MM3 on the other hand, it is difficult to define a clear inflection point on their $\eta$-PDF tail. We therefore took as second departure point the boundary between ranges of column densities dominated by their cores and by their background image (see Figs. [6](#fig:various eta-PDF)e–f). The range between the first and second departure points is the column density range used to fit a power law on what we call the second tail because it is close to that observed for the *Herschel* $\eta$-PDF (see Tables [\[tab:cmf and s\]](#tab:cmf and s) and [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)). The ALMA $\eta$-PDF tail of W43-MM2&MM3 has also a power-law exponent, which is consistent to that observed for the *Herschel* $\eta$-PDF: $s_2^{\rm ALMA}=-0.9\pm0.3$ versus $s_2^{Herschel}=-1.3\pm0.3$ (see [13](#appendixfig:pdf W43 herschel)b). Finally, the range between the second departure point and, as an end point, the maximum column density detected in subregions (see [\[tab:subregions chara\]](#tab:subregions chara)) is used to fit a power law on what we call the third tail. [\[tab:cmf and s\]](#tab:cmf and s) lists, for each subregion, the ranges of these two $\eta$-PDF tails and their fitted power-law exponents, $s_2$ and $s_3$. Uncertainties on the power-law exponents are estimated by varying the number of bins of the $\eta$-PDFs, the limits of the fit ranges, and by taking into account the uncertainty on the column density offset (see [\[tab:cmf and s\]](#tab:cmf and s)). The assumption on the dust temperature used to compute the column density image has a negligible effect on the $\eta$-PDFs since, with a constant temperature on all pixels, the power-law exponents of their $s_2$ and $s_3$ tails are not changed by more than $10\%$. While the third $\eta$-PDF tail is, by definition, related to cores, the second tail is mainly composed of pixels surrounding the cores, thus excluding their contribution to the $\eta$-PDF tail (see Figs. [1](#fig:nh2 and cores) and [12](#appendixfig:PPMAP with NH2)).

As shown in Figs. [6](#fig:various eta-PDF)c–f, the MM10, MM12, MM2, and MM3 subregions all have second and third tails of their $\eta$-PDF that are clearly defined. As for the other two regions, MM51 has only a third tail (see [6](#fig:various eta-PDF)b) and Outskirts no tail that can be revealed with current data (see [6](#fig:various eta-PDF)a). The power-law exponent of their potential second tail must be greater than $s_2 \sim -5$ and could be the continuation of the first tail observed in the *Herschel* $\eta$-PDF, $s_1\sim -2.9$ (see [13](#appendixfig:pdf W43 herschel) and [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)). Subregions with top-heavy CMFs, MM12, MM2, and MM3, have flatter second tails and reach much higher column densities in their third tail than the MM10 subregion, whose CMF high-mass end is close to Salpeter (see [6](#fig:various eta-PDF) and [\[tab:cmf and s\]](#tab:cmf and s)). Moreover, there is a clearer continuity between the second and third tails of the MM2 and MM3 subregions, than between the tails of MM10, MM12, and even worse MM51.

![image](sigma6_a.png) ![image](sigma6_b.png)

![](lambda_mm2_mm51.png)

![](lambda_mm10_mm12.png)

![](lambda_mm3.png)

## Varying core mass segregation

We here quantify the mass segregation of cores and its variations within the W43-MM2&MM3 subregions, with the aim of revealing any correlation with their CMF shape in Sect. [4.1](#sect:BadCorrelations). There are several ways to measure if a set of objects is more clustered than others (see comparison of methods in (cite: parkerGoodwin2015)). We followed the recommendations of (cite: parkerGoodwin2015) and used two different indicators in tandem. The first one measures, for each core using its six closest neighbors, the local core surface density of a subregion, $\Sigma_{\rm 6\,cores}$ (cite: maschbergerClarke2011). A larger $\Sigma_{\rm 6\,cores}$ value for the most massive cores of a subregion indicates a spatial concentration of cores around the most massive ones. In order to assess this spatial concentration around massive cores in the small-statistic samples of cores of the W43-MM2&MM3 subregions, we measured the $\Sigma_{\rm 6\,cores}$ for the five most massive cores, $\left(\Sigma_{\rm 6\,cores}\right)_{\rm massive}$. Comparing this value to the general core surface density of each subregion, $\overline{\Sigma_{\rm 6\,cores}}$, can give insights on the level of core mass segregation, which is considered significant for $\left(\Sigma_{\rm6\,cores}\right)_{\rm massive}/\overline{\Sigma_{\rm6\,cores}}>2$.

The second indicator we chose, the mass segregation ratio of cores, $\Lambda_{\rm MSR}$ (cite: allison2009b), has been used for cores in several high-mass star-forming studies (cite: dib2018segreg; sanhueza2019; busquet2019; nony2021). This indicator is based on the minimum spanning tree (MST) method and is computed with the following equation: $$\begin{equation}
 \label{eq:lambda msr}
    \Lambda_{\rm MSR} (N_{\rm MST}) = \frac{\overline{l_{\rm random}}}{l_{\rm massive}} \pm \frac{\sigma_{\rm random}}{l_{\rm massive}},
\end{equation}$$ where $l_{\rm massive}$ is the MST length of the $N_{\rm MST}$ most massive cores of a subregion and $\overline{l_{\rm random}}$ is the average MST length of sets of $N_{\rm MST}$ random cores. When $\Lambda_{\rm MSR}$ is plotted against $N_{\rm MST}$, $l_{\rm massive}$ includes an increasing number of cores, which are ordered by decreasing mass. To estimate $\overline{l_{\rm random}}$ and the associated $\sigma_{\rm random}$ of sets of random cores, we used a total of 500 sets of $N_{\rm MST}$ cores uniformly randomly distributed in space. When $\Lambda_{\rm MSR}\simeq1$, massive cores of a subregion do not show any particular spatial distribution. In contrast, $\Lambda_{\rm MSR}>1$ indicates a spatial concentration of the massive cores and a core population that then qualifies as segregated in mass. [1](#tab:mass segregation) lists these two indicators of core mass segregation, $\left(\Sigma_{\rm6\,cores}\right)_{\rm massive}/ \overline{\Sigma_{\rm6\,cores}}$ and $\left[ \Lambda_{\rm MSR};~ N_{\rm MST} \right]$, and qualifies the segregation level of each W43-MM2&MM3 subregion accordingly.

+:---------:+:--------------------------------------------------:+:-------------------:+:-----------------:+:----------:+
| Subregion | $\left(\Sigma_{\rm 6\,cores}\right)_{\rm massive}$ | $\Lambda_{\rm MSR}$ | $N_{\rm MST}$     | Mass segr. |
+-----------+----------------------------------------------------+                     +-------------------+------------+
| name      | / $\overline{\Sigma_{\rm6\,cores}}$                |                     | range             | level      |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
| \(1\)     | \(2\)                                              | \(3\)               | \(4\)             | \(5\)      |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
| Outskirts | $<1$                                               | \-                  | \-                | none       |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
| MM51      | $<1$                                               | \-                  | \-                | none       |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
| MM10      | 3.1                                                | $2.3\pm0.7$         | $3\rightarrow7$   | high       |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
| MM12      | $<1$                                               | \-                  | \-                | none       |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
|           |                                                    |                     |                   |            |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
| MM2       |                                                    | $5\pm2$             | $3\rightarrow6$   | very high  |
|           +----------------------------------------------------+---------------------+-------------------+------------+
|           | 2.6                                                | $2.3\pm0.4$         | $7\rightarrow14$  | high       |
|           +----------------------------------------------------+---------------------+-------------------+------------+
|           |                                                    | $1.8\pm0.2$         | $15\rightarrow31$ | moderate   |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
|           |                                                    |                     |                   |            |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
| MM3       | 3.6                                                | $1.8\pm0.4$         | $3\rightarrow15$  | moderate   |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+
| Total     | 6.6                                                | –                   | –                 | –          |
+-----------+----------------------------------------------------+---------------------+-------------------+------------+

: Core mass segregation in subregions of W43-MM2&MM3.

\(2\) Ratio of the local core surface density measured for the five most massive cores to that averaged for all cores in each W43-MM2&MM3 subregion.

\(3\) and (4) Core mass segregation ratio computed from [\[eq:lambda msr\]](#eq:lambda msr) over the $N_{\rm MST}$ range.

\(5\) Core mass segregation level (see Sect. [3.3](#sect:mass segregation)); three regimes for the MM2 subregion corresponding to the plateaus observed in [8](#fig:lambda msr)a.

Figure [7](#fig:sigma6) displays the local surface density of cores in the W43-MM2&MM3 mini-starburst, $\Sigma_{\rm 6\,cores}$. For the MM2, MM3, and MM10 subregions, we observe a correlation trend between the mass of a core and its local core surface density when this core is above the completeness limit of their catalogs (see Figs. [7](#fig:sigma6)a–b). Such a behavior has already been observed in several studies (cite: lane2016; parker2018; dibHenning2019; nony2021) and can be related to the need of high-density gas to form cores, and especially massive cores. While this correlation trend is clear for the MM2 and MM3 subregions, it is only tentative for MM10 and absent for the other subregions. In addition, in the MM2, MM3, and MM10 subregions, the five most massive cores have local core surface densities $2.6-3.6$ times greater than the core surface densities averaged over the entire subregions (see Figs. [7](#fig:sigma6)a–b and [1](#tab:mass segregation)). This result indicates that in the MM2, MM3, and MM10 subregions, cores spatially concentrate around the most massive ones. It argues in favor of a large clustering of massive cores in these subregions but could also correspond to the peculiar situation where these five massive cores are surrounded by low-mass cores at five different locations. We verified in [1](#fig:nh2 and cores) that this is not the case of any of the MM2, MM3, and MM10 subregions. As for the other three subregions of W43-MM2&MM3, in each subregion the core surface density of their five most massive cores is lower than that averaged over their entire core sample (see [1](#tab:mass segregation)).

Therefore, according to the local core surface density indicator, $\Sigma_{\rm 6\,cores}$, the MM2, MM3, and MM10 subregions show some evidence of mass segregation and not the other three subregions. We seek here to confirm this result by using the $\Lambda_{\rm MSR}$ indicator. Figure [8](#fig:lambda msr) displays the mass segregation ratio of the W43-MM2&MM3 subregions, excluding the Outskirts, which is not a coherent subregion with convex boundaries. As classically done, we started computing for each subregion, the $\Lambda_{\rm MSR}$ at $N_{\rm MST}=3$ to avoid divergence on the first MST measurements. If massive cores are spatially concentrated, the mass segregation ratio decreases when it is measured over a larger group of cores. This trend is clearly observed for the MM2 and MM10 core catalogs, well above their completeness level (see Figs. [8](#fig:lambda msr)a–b). The MM2 and MM3 subregions therefore qualify as mass-segregated, in agreement with the local core surface density measurements (see Figs. [7](#fig:sigma6)a–b and [1](#tab:mass segregation)). The $\Lambda_{\rm MSR}$ function observed for the core catalog of MM3 is more complex to interpret. The most massive cores of the MM3 subregion do not appear mass-segregated but taking a larger group of cores reveals some evidence of moderate mass segregation (see [8](#fig:lambda msr)c and [1](#tab:mass segregation)). The unusual shape of the $\Lambda_{\rm MSR}$ function in the MM3 subregion suggests that the structure of its core cluster is not just mass-segregated. This complexity could be a consequence of the MM3 subregion being at an evolved stage, as it already developed an UCHii region. According to the $\Lambda_{\rm MSR}$ indicator, the MM12 and MM51 subregions do not show evidence of mass segregation, while the completeness level of their core catalogs would allow for it (see Figs. [8](#fig:lambda msr)a–b).

In [1](#tab:mass segregation), we qualified the evidence of core mass segregation using the $\Lambda_{\rm MSR}$ values: moderate for $1.5 <\Lambda_{\rm MSR}< 2$, high for $2 \le \Lambda_{\rm MSR} < 3$, and very high for $\Lambda_{\rm MSR} \ge 3$. Using this classification, the level of mass segregation of MM2, MM10, and MM3 is very high, high, and moderate, respectively (see [1](#tab:mass segregation)). The number of points involved in the mass-segregated part of the $\Lambda_{\rm MSR}$ function can sometimes be used to define several regimes. This is the case of the MM2 subregion, whose core mass segregation is so high that $\Lambda_{\rm MSR}$ displays three plateaus. It has a very high level of mass segregation for $N_{\rm MST}=3\rightarrow 6$, high for $N_{\rm MST}=7\rightarrow 14$, and moderate for $N_{\rm MST}=15\rightarrow 31$ out of 58 cores. Among the dozen or so studies that have investigated the mass segregation of cloud structures, only two found similarly high segregation levels in the NGC 2264, W43-MM1, and Corona Australis star-forming regions (cite: dibHenning2019; nony2021). Others notably studying early stages of intermediate- to high-mass star formation found no evidence (cite: sanhueza2019; busquet2019). The variety of core mass segregation levels we measured in the W43-MM2&MM3 subregions is reminiscent of that found by (cite: dibHenning2019) and (cite: nony2021) in five and three (sub)regions, respectively.

In conclusion, our analysis of the core mass segregation suggests that three out of the six W43-MM2&MM3 subregions could be mass-segregated, the MM2, MM3, and MM10 subregions (see [1](#tab:mass segregation)). Interestingly, the cores that are mass segregated in the MM10 subregion have low to intermediate, $2.0-11.2~\ensuremath{M_{\odot}}$, masses, while those in MM2, and MM3 span the $11-70~\ensuremath{M_{\odot}}$ and $7-45~\ensuremath{M_{\odot}}$ range, respectively.

# Discussion

In the subregions of the W43-MM2&MM3 ridge, the high-mass end of the CMF is observed to vary from steeper or close to the Salpeter slope of the canonical IMF, to top-heavy (see Sect. [3.1.2](#sect:CMFs)). In Sect. [4.1](#sect:BadCorrelations), we examine, the link between the CMF shape and the cloud properties and core mass segregation characterized in Sects. [3.1](#sect:spatial variations of core pop) and [3.3](#sect:mass segregation), respectively. In Sect. [4.2](#sect:link CMF-PDF), we then study the link between the power-law index of the CMF high-mass end and the slope of the $\eta$-PDF tail measured in Sect. [3.2](#sect:PDFs) for each subregion. In Sect. [4.3](#sect:link with sf history), we finally determine the likely evolutionary stage of subregions and interpret their CMF variations in the framework of a scenario of the cloud and star formation histories across the W43-MM2&MM3 ridge.

## Correlation trends between the CMF and the basic cloud and core properties

The W43-MM2&MM3 ridge presents a large variety of environments, with the MM2 subregion being the most extreme and the Outskirts the least extreme. In detail, the MM2 subregion, compared to the Outskirts, has $\sim$11 times more total gas mass, $\sim$7000 times higher densities, $\sim$15 times greater core density per surface units, $\sim$9 times more gas mass into cores, and displays a very high core mass segregation (see Tables [\[tab:subregions chara\]](#tab:subregions chara) and [1](#tab:mass segregation)).

We first searched for correlations of the power-law index of the CMF high-mass end, given in [\[tab:cmf and s\]](#tab:cmf and s), with all the parameters listed in [\[tab:subregions chara\]](#tab:subregions chara). As a general trend, the more extreme the subregion in terms of mass or associated volume density or in terms of mass into core, the shallower its CMF power-law index. This result is reminiscent of the correlation found between IMF indices and cloud densities of extragalactic starburst environments (cite: marks2012). While being an extreme cloud of the Milky Way, the W43-MM2&MM3 ridge has a density, $n_{\rm H_2} \sim 3\times 10^4$ cm$^{-3}$ in $\sim$11 pc$^{-3}$ (cite: nguyen2013), just at the level of the lowest densities of the regions studied by (cite: marks2012). The W43-MM2 subregion, which is about 17 times denser than the global ridge (see [\[tab:subregions chara\]](#tab:subregions chara)) just reaches the minimum density where an effect on the IMF slope is suspected (cite: marks2012).

We then searched for some relationship between the core mass segregation and the CMF shape. Both core mass segregation and top-heavy CMF are indeed, by definition, favored by the presence of high-mass, or at least intermediate-mass, cores. This high-density gas, however, needs to be centrally concentrated to define a single major star-forming site that displays mass segregation, as it is the case of MM2 and to a lesser extent MM3 and MM10 (see [1](#fig:nh2 and cores)). This condition is not a necessary one to build a flat CMF, as proven by the MM12 subregion where no mass segregation is observed (see Tables [\[tab:cmf and s\]](#tab:cmf and s)–[1](#tab:mass segregation)). Conversely the MM10 subregion, consisting of a major filament plus a lower density medium, shows core mass segregation while its CMF high-mass end remains close to the Salpeter slope (see [3](#fig:subregion mass vs core mass) and Tables [\[tab:cmf and s\]](#tab:cmf and s)–[1](#tab:mass segregation)). In that respect, the link between the level of core mass segregation and the slope of the CMF high-mass end may exist but not as a one-to-one correspondence.

These general trends could physically constrain models, but we recall that they are currently based on only six data points that correspond to the six subregions of the W43-MM2&MM3 ridge. We should be able to confirm these trends into definite correlations or to refute them using a much larger sample of subregions that will be defined within the 15 protoclusters imaged by the ALMA-IMF Large Program.

+:-----------------------+:----------------------------:+:-----------------------------:+:--------------:+:-----------------------------:+:--------------:+:-------------------------------------+
| Region                 | Reference paper              | Fitted range ($s_1$)          | $s_1$          | Fitted range ($s_2$)          | $s_2$          | Consistent with studies by           |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
|                        |                              | \[$\times10^{21}$ cm$^{-2}$\] |                | \[$\times10^{21}$ cm$^{-2}$\] |                |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| \(1\)                  | \(2\)                        | \(3\)                         | \(4\)          | \(5\)                         | \(6\)          | \(7\)                                |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| **Low-mass star-forming regions**                                                                                                                       |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Taurus$^{\dagger}$     | (cite: schneider2022)        | 3–18                          | -2.3           | 18–50                         | -4.4           | (cite: kainulainen2009)              |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| $\rho$-Oph$^{\dagger}$ | (cite: ladjelate2020)        | 7–15                          | -1.3           | 15–65                         | -2.8           | (cite: schneider2022)                |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Aquila$^{\dagger}$     | (cite: schneider2022)        | 5–18                          | -2.1           | 18–250                        | -2.4           | (cite: schneider2013; konyves2015)   |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| **Intermediate-mass star-forming regions**                                                                                                              |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Orion B$^{\dagger}$    | (cite: jaupartChabrier2020)  | 2–23                          | -2.0           | 23$^{\star}$–50$^{\star}$     | -3.0$^{\star}$ | (cite: kainulainen2009; konyves2020) |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
|                        |                              |                               |                |                               |                | (cite: schneider2013; schneider2022) |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Orion A$^{\dagger}$    | (cite: stutzKainulainen2015) | 17–80                         | -0.9           | 80$^{\star}$–160$^{\star}$    | -3.0$^{\star}$ | (cite: kainulainen2009)              |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Mon R2                 | (cite: schneider2015)        | 8–36                          | -2.1           | 36–200                        | -1.0           | (cite: schneider2022)                |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| **High-mass star-forming regions**                                                                                                                      |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| W3 Main/(OH)           | (cite: riveraIngraham2015)   | 12–36                         | -2.1$^{\star}$ | 36–190$^{\star}$              | -1.6$^{\star}$ |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| NGC 6334               | (cite: russeil2013)          | 11–90                         | -2.0           | 90$^{\star}$–280$^{\star}$    | -1.3$^{\star}$ | (cite: schneider2022)                |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Cygnus-X North         | (cite: schneider2016)        | 12–85$^{\star}$               | -2.3$^{\star}$ | 85$^{\star}$–280$^{\star}$    | -1.5$^{\star}$ | (cite: schneider2022)                |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| W43                    | (cite: carlhoff2013)         | 37$^{\star}$–190$^{\star}$    | -2.5$^{\star}$ | 190$^{\star}$–660$^{\star}$   | -1.3$^{\star}$ | This article                         |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| **W43-MM2&MM3 mini-starburst ridge and its subregions**                                                                                                 |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| W43-Main (without MM1) | This article                 | 40–60                         | -2.9           | 60–400                        | -1.3           | (cite: carlhoff2013)                 |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| MM10                   | This article                 | –                             | –              | 100–300                       | -2.4           |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| MM2                    | This article                 | –                             | –              | 150–1000                      | -0.6           |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| **Numerical simulations**                                                                                                                                                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Model #24              | (cite: kainulainen2013)      | 3$^{\star}$–40$^{\star}$      | -1.6$^{\star}$ | –                             | –              |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Model #C1t03           | (cite: leeHennebelle2018a)   | $10^6-10^{12}$ cm$^{-3}$      | $\equiv$-2     | \-                            | –              |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+
| Model M=3, SFE=20%     | (cite: jaupartChabrier2020)  | 1–20                          | -2.0           | 20$^{\star}$–400$^{\star}$    | -1.0$^{\star}$ |                                      |
+------------------------+------------------------------+-------------------------------+----------------+-------------------------------+----------------+--------------------------------------+

$\dagger$: Low- to intermediate-mass star-forming regions, which exhibit typical CMFs with a high-mass end fitted by a power-law index close to that of the Salpeter slope of the canonical IMF (cite: polychroni2013; konyves2015; marsh2016; konyves2020; ladjelate2020).

$^{\star}$Values derived graphically from the reference paper.

![image](correlation_alpha_s.png) ![image](correlation_alpha_proto.png)

![](PDF_mm2_mm10.png)

![](CMF_stack_mm2_mm10.png)

## Linking the CMF high-mass end to the $\eta$-PDF tail

### Comparison with observational studies in the literature

We here compare the $\eta$-PDF tail of the W43-MM2&MM3 subregions that are characterized in Sect. [3.2](#sect:PDFs) with those obtained from the literature for ten observed star-forming clouds and three simulated clouds (cite: schneider2022; jaupartChabrier2020). These $\eta$-PDF tails cover different column density ranges depending on the type (low-, intermediate-, and high-mass) of the star-forming regions considered and are quantified by fitting one or two consecutive power laws (cite: kainulainen2009; schneider2015). They are as follows:

*First $\eta$-PDF tail*: Above the transition from a lognormal function to a power-law tail, the first slope of the tails measured in the literature is $s_1 \in [-2.5; -0.9]$, with most values around $s_1 \simeq -2$, (see [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)). The first tail of W43-MM2&MM3 is observed in the $\eta$-PDF of the *Herschel* column density image (see [13](#appendixfig:pdf W43 herschel)b and [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)), but not in the $\eta$-PDFs derived from the ALMA 12 m array alone (see Sect. [3.2](#sect:PDFs)).

*Second $\eta$-PDF tail*: At higher column densities, above $40-100\times 10^{21}$ cm$^{-2}$, a flatter second tail is observed for high-mass star-forming regions: $s_2 \in [-1.6; -1.3]$ (see [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)). In contrast, the second tails of the low- and intermediate-mass star-forming regions (with the exception of Mon R2) are steep, indicating a lack of cloud structures at high column densities in maps with spatial resolution about the core size. The ALMA $\eta$-PDF built for the W43-MM2&MM3 subregions have $s_2$ slopes that range from $s_2>-5$ for MM51 and the Outskirts to $s_2=-0.6\pm 0.2$ for MM2. While the $s_2$ tails of the Outskirts and MM51 resemble those of low-mass star-forming regions, those of MM10 and MM12 follow the typical slope of the first tail, and those of MM2 and MM3 are as flat as, or even flatter than, the second slope measured in high-mass star-forming regions. Figure [9](#fig:correlation alpha vs s and proto) displays, for each W43-MM2&MM3 subregion, the relation between the power-law index of the CMF high-mass end and the slope coefficient of the second $\eta$-PDF tail, $\alpha$ and $s_2$, and the protostellar fraction listed in [\[tab:cmf and s\]](#tab:cmf and s). We observed a correlation trend between these power-law indices but the small number of W43-MM2&MM3 subregions and the large uncertainties on $\alpha$ and $s_2$ prevent us from making a reliable estimate of the significance and strength of this correlation.

*Third $\eta$-PDF tail*: The $\eta$-PDFs of the W43-MM2&MM3 subregions reach extremely high column densities, up to $900-26\,000\times 10^{21}$ cm$^{-2}$), never before reported in other published $\eta$-PDF studies (see [6](#fig:various eta-PDF)). At these column densities corresponding to those of cores, from $250-900\times 10^{21}$ cm$^{-2}$ to $1000-26\,000\times 10^{21}$ cm$^{-2}$, the $\eta$-PDF of the W43-MM2&MM3 subregions all have $s_3$ slopes that are very flat, $s_3\in [-0.9;-0.1]$ (see [\[tab:cmf and s\]](#tab:cmf and s)). As suggested by (cite: myers2017), we could expect the third $\eta$-PDF tail, which is associated with cores, to more strongly correlate with the CMF core distribution than the second tail, which traces the high-column-density gas surrounding cores. For the MM2 and MM3 subregions, the second and third tails have their power-law exponents $s_2$ and $s_3$ very close to each other. This suggests that, in these subregions, the distribution of column density within cores originate from the gas distribution in their cloud hubs, in agreement with the dynamical picture of cloud formation (cite: smith2009).

Figure [10](#fig:PDF CMF mm2 mm10) displays the $\eta$-PDFs and CMFs of two representative subregions of W43-MM2&MM3, MM2 and MM10, along with those of the reference low-mass star-forming region Aquila (cite: konyves2015; schneider2022). While MM10 has a steep $\eta$-PDF tail and a CMF high-mass end close to the Salpeter slope of the canonical IMF, the MM2 subregion displays a much flatter second $\eta$-PDF tail and a top-heavy CMF (see [10](#fig:PDF CMF mm2 mm10) and [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)). Interestingly, the MM10 subregion has $\eta$-PDF and CMF power-law indices, $s_2=-2.4\pm0.2$ and $\alpha=-1.16_{-0.30}^{+0.16}$, that are similar to those of the low- to intermediate-mass star-forming regions. Taurus, $\rho$ Oph, Aquila, Orion B, and Orion A are indeed known to have tails dominated by a steep power law ($s_2 \in [-4.4; -2.4]$; see [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)) and to exhibit typical CMFs with a high-mass end close to the Salpeter slope (cite: polychroni2013; konyves2015; marsh2016; konyves2020; ladjelate2020).

Besides, subregions with the most top-heavy CMFs (MM2 and MM3) have second $\eta$-PDF tail at high column density described by a power law with a slope, $s_2\in[-0.8; -0.6]$, close to but flatter than the one measured for the second power-law tails observed in high-mass star-forming regions (e.g., (cite: schneider2015; schneider2022), see also our [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)). The first elements of a physical interpretation for the observed variations of the $\eta$-PDF and CMF shapes are given in Sect. [4.2.2](#sect:interpretation link pdf-cmf).

### Interpretation of $\eta$-PDF tails and their link with the CMF

It is tempting to make a direct link between the slope of the cloud column density $\eta$-PDF and the power-law index of the CMF high-mass end. We here compare the two representative subregions in W43-MM2&MM3, illustrated in [10](#fig:PDF CMF mm2 mm10), with published models and discuss various interpretations proposed in observational and theoretical studies. Analytical studies and numerical simulations often analyze the PDF of the natural logarithm of the normalized volume density, $\phi \equiv \ln{(\rho / \overline{\rho})}$ with $\overline{\rho}$ the mean density and fit the PDF with power laws of exponent $\psi$: $$\begin{equation}
    p_\phi = \rho\times p_\rho \propto \rho^\psi .
\end{equation}$$ In the idealized case of a spherical cloud with a purely radial density distribution, $\rho \propto r^{-a}$, (cite: federrathKlessen2013) have analytically demonstrated the relation that exists between the slope coefficients of $p_\eta$ and $p_\phi$ and that of the volume density, $s$ and $\psi$ versus $a$, respectively: $s = \frac{2}{1-a}$ and $\psi = \frac{-3}{a}$ (cite: federrathKlessen2013). It leads to the following relation: $$\begin{equation}
\label{eq:s}
    s=\frac{2}{1+3/\psi}.
\end{equation}$$

We used [\[eq:s\]](#eq:s) to predict, from the power-law exponent, $\psi$, of the models, the power-law exponent $s$ that an $\eta$-PDF tail computed from the simulated volume density cube projected into a column density image would have (cite: kainulainen2013; leeHennebelle2018b; jaupartChabrier2020). The models of [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics) exhibit power-law exponents with $s_1\sim -2$, close to those found for the first $\eta$-PDF tail of low-mass star-forming regions and that of W43-MM2&MM3 (see [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)). It has been interpreted by many studies as evidence of volume density with a power-law index of $a\simeq 2$ that could be associated with the collapse of a spherically symmetric isothermal cloud (cite: schneider2022). We however caution that relation of [\[eq:s\]](#eq:s) is only valid for the idealized and unrealistic case of a spherical cloud with a radial density distribution. While [\[eq:s\]](#eq:s) could also apply, and $s_1= -2$ is expected, for a collection of well-resolved collapsing cores, the complex structure of the cloud at high column density should not be neglected when interpreting the slope of $\eta$-PDF tails.

As for the flat second tails of the $\eta$-PDF obtained for Orion A, Mon R2, all high-mass star-forming regions of [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics) and the MM2 and MM3 subregions, they have been associated with their hosted hubs. The density profiles of ridges and hubs, when measured, are steeper than the classical $\rho(r)\propto r^{-2}$ profile (cite: hill2011; didelon2015; motte2018a) and interpreted by (cite: motte2018a) as a consequence of adiabatic heating, rotation, or magnetic field, in relation with the observed slow-down of the ridge collapse (cite: wyrowski2016). Ridges and hubs are expected to form by dynamical processes such as cloud collision during the initial cloud formation phase or feedback effects associated with the expansion of Hii regions in more evolved clouds (cite: motte2018a). In fact, these second tails were already associated with feedback effects of Hii regions (cite: tremblin2014; riveraIngraham2015) or the young evolutionary stage of a cloud (cite: sadavoy2014; stutzKainulainen2015). In agreement with the interpretations by, for example, (cite: schneider2015) and (cite: motte2018a), models by (cite: khullar2021) and (cite: donkov2021) showed that the onset of rotation and a change in the equation of state for a hard polytrope both lead to second flatter PDF tails.

According to (cite: leeHennebelle2018a) and (cite: hennebelle2022), a cloud with a $\rho$-PDF exhibiting a tail instead of a simple lognormal shape, develops a CMF high-mass end that is shallower than the Salpeter slope. While these simulation studies qualitatively agree with present observations, they associate a top-heavy CMF with a tail slope of $\psi= -1.5$, or potentially in an equivalent manner $s=-2$ (see above). This power-law exponent of the $\eta$-PDF remains steeper than what is observationally found for the exponents of the second power-law tail of high-mass star-forming clouds and second and third tails of the MM2 and MM3 subregions. A handful of other models predicted a flatter tail (cite: kainulainen2013) but their impact on the CMF shape still needs to be investigated.

## Core population, a witness of the history of cloud and star formation

Beyond a simple study of the correlation between the distribution in space and mass of the cloud and cores, it is necessary to take into account the history of cloud and star formation to understand the variety of the subregions properties and core populations in W43-MM2&MM3. [4.2](#sect:link CMF-PDF) revealed a correlation pattern between the CMF and $\eta$-PDF. In Sect. [4.3.1](#sect:evolutionary stage), we define the evolutionary status of the subregions and, in Sect. [4.3.2](#sect:impact on cloud and cores), make the link between the CMF and $\eta$-PDF quantities to finally propose a cloud and star formation scenario (see [11](#fig:summary)).

### Evolutionary stage of subregions

In W43-MM2&MM3 as in the W43-MM1 mini-starburst ridge, clouds are expected to form via a global collapse, which is initiated by colliding flows of Hi gas (cite: nguyen2011b; nguyen2013; motte2014; louvet2016). In dynamical star formation theories, a dynamical cloud assembly is followed by a burst of star formation (cite: smith2009; leeHennebelle2018a; vazquez2019; pelkonen2021). This in fact is the favored scenario for the W43 Main cloud and in particular the W43-MM1 and W43-MM2&MM3 mini-starburst ridges, which are observed to efficiently form stars (cite: motte2003; nguyen2013; louvet2014). During star formation bursts, clouds actively form cores that should immediately collapse and host protostars in their main accretion phase (cite: pelkonen2021; hennebelle2022). We therefore expect the protostellar core fraction to be higher in the burst phase than in quiescent regions or in the pre-burst phase. While the burst is a phase when massive cores have not yet had time to develop UCHii regions, the post-burst phase should be characterized by the presence of Hii regions. Because the W43-MM2&MM3 subregions are at different evolutionary stages (see below), separating the ridge into subregions allows us to focus on cloud structures that will, do, or did simultaneously form stellar clusters.

Defining the evolutionary stage of the W43-MM2&MM3 subregions is however not a straightforward task. We focus on durations several free-fall times of the subregions. With volume densities of $n_{\rm H_{2}}\simeq 0.2-5\times10^5$ cm$^{-3}$ (excluding the Outskirts; see [\[tab:subregions chara\]](#tab:subregions chara)), this would correspond to time spans of $\sim$10$^5-10^6$ yr, with the shortest and longest potentially being for the MM2 and MM51 subregions, respectively. To define the evolutionary stage of these $\sim$0.5–1 pc cloud structures, we quantify the development of the star formation process through three criteria. These are the protostellar core fraction of the subregion, its surface density of cores, both quantified in Sect. [3](#sect:analysis) (see Tables [\[tab:subregions chara\]](#tab:subregions chara) and [1](#tab:mass segregation)), and the potential UCHii regions. Our classification allows us to state whether these subregions are a handful of $10^5$ years before, during, or after their main star formation event, or whether they are and will remain quiescent. [\[tab:cmf and s\]](#tab:cmf and s) gives the evolutionary stage of each W43-MM2&MM3 subregion, as defined below, using the following criteria:

*MM51 and Outskirts*: They qualify as quiescent because their surface number density of cores and their protostellar fraction are lower or equal to the average values measured in the W43-MM2&MM3 subregions ($\sim$35 cores/pc$^2$ and $\sim$25%; see Tables [\[tab:subregions chara\]](#tab:subregions chara)–[\[tab:cmf and s\]](#tab:cmf and s)). These two subregions could well remain quiescent, aside from the most active sites of the W43-MM2&MM3 mini-starburst, never entering a burst mode.

*MM10*: Potentially in a pre-burst regime, it has an enhanced surface number density of cores, $\sim$1.3 higher, but a protostellar fraction that remains slightly lower than the average values (see Tables [\[tab:subregions chara\]](#tab:subregions chara)–[\[tab:cmf and s\]](#tab:cmf and s)). Its large number of cores is consistent with MM10 being a site of intense cloud formation by cloud-cloud collision, as evidenced by its strong SiO emission tracing low-velocity shocks (cite: nguyen2013). We therefore expect MM10 to enter, in the near future, in its main phase of star formation and to form the high-mass cores that it surprisingly lacks at this stage (see Sect. [3.1](#sect:spatial variations of core pop)).

*MM12*: It most probably is at the beginning of its burst because it displays an increase of the protostellar core fraction by a factor of $\sim$1.6 but has a surface number density of cores close to the average value measured for the W43-MM2&MM3 subregions (see Tables [\[tab:subregions chara\]](#tab:subregions chara)–[\[tab:cmf and s\]](#tab:cmf and s)).

*MM*2: It qualifies as being in its main burst because its surface number density of cores and protostellar core fraction are increased, by factors of $\sim$2.1 and $\sim$1.5 compared to the average values, respectively (see Tables [\[tab:subregions chara\]](#tab:subregions chara)–[\[tab:cmf and s\]](#tab:cmf and s)). Among the 19 protostellar cores discovered in this subregion by (cite: nony2023), three cores are hot core candidates (see (cite: pouteau2022) and Bonfand et al. in prep.) powered by $10^3-10^4~L_{\odot}$ protostars (cite: motte2003; bally2010). These luminosities and the absence of UCHii region provide evidence that MM2 is at an early stage of the high-mass star formation process.

*MM3*: It is post-burst because it hosts an UCHii region and its stellar activity decreased, as proven by their surface number density of cores and protostellar core fraction back to the average values (see [\[tab:cmf and s\]](#tab:cmf and s)). This UCHii region developed over the past $\sim$3$\times 10^5$ years (cite: lumsden2013) and originates from the formation of a $\sim$22 $\ensuremath{M_{\odot}}$[^6] star (see [3](#fig:subregion mass vs core mass)). We expect MM3 to have already formed a first-generation of stars, which could be searched for with high-sensitivity and high-resolution mid-infrared images of the James Webb Space Telescope (JWST) satellite.

### Impact of this evolutionary stage on cloud and cores

In the framework of dynamical cloud and star formation models (cite: vazquez2019), the density structure of clouds and distribution of core populations in clouds, both in mass through the CMF and in space and mass through the core mass segregation, should result from the cloud formation, star formation, and evolution processes. This is confirmed in [9](#fig:correlation alpha vs s and proto)b, where the slope of the CMF high-mass end tends to correlate with the protostellar fraction, which is the main criterion used to define the evolutionary stage of a subregion (see Sect. [4.3.1](#sect:evolutionary stage)). This is particularly true when ignoring the MM3 subregion, whose core population has likely changed from its younger stages of burst or pre-burst regimes.

Figure [11](#fig:summary) presents a schematic evolutionary diagram of subregions expected in ridges, with typical cloud and core properties, including the shapes of the CMFs and $\eta$-PDFs. Ridges are by definition high-density filamentary clouds, which are formed by dynamical processes of cloud formation and where star formation is enhanced (cite: motte2018a). We used W43-MM2&MM3 subregions as examples because their cloud and core properties are well studied (see Sect. [3](#sect:analysis)) and their evolutionary stages are robustly defined (see Sect. [4.3.1](#sect:evolutionary stage)). The physical characteristics of quiescent subregions and of subregions in their pre-burst, main burst, and post-burst phases, which means before, during, and after their main star formation event, are detailed below.

In quiescent subregions of ridges (see top-panels of [11](#fig:summary))

the cloud volume densities should be among the lowest and the slopes of their $\eta$-PDF tail among the steepest (like MM51 and the Outskirts in Tables [\[tab:subregions chara\]](#tab:subregions chara)–[\[tab:cmf and s\]](#tab:cmf and s)). Their CMF high-mass end is most probably close to the Salpeter slope of the canonical IMF and the subregions do not present core mass segregation (like MM51 and the Outskirts in [1](#tab:mass segregation)). The quiescent subregions therefore have properties that resemble those of nearby, low- to intermediate-mass star-forming clouds, which are also for the most part quiescent.

Subregions in pre-burst regime or at the beginning of their main burst (see top and central-panels of [11](#fig:summary)) should have similar cloud properties. Their volume densities are around the average values observed for the ridge subregions but their column density $\eta$-PDFs tail may start flattening (like MM10 and MM12 in Tables [\[tab:subregions chara\]](#tab:subregions chara)–[\[tab:cmf and s\]](#tab:cmf and s)). The case of MM10 is interesting because it contains a filament, with column density enhancement and mass segregation of intermediate-mass cores (see [8](#fig:lambda msr)b). These characteristics combined with the shock evidence found by (cite: nguyen2013) suggest that this filament currently forms through cloud concentration and gas mass inflows. As for MM12, its proximity to the MM2 subregion suggests it formed during the same cloud concentration phase as MM2 and could accrete and concentrate more gas in the near future. Subregions in the transitory phase between pre-burst and burst should have a CMF high-mass end, which slowly gets flatter than the Salpeter slope (like MM12 in [\[tab:cmf and s\]](#tab:cmf and s)).

The subregions in their main burst (see central panels of [11](#fig:summary)) should have mean cloud volume densities a few times larger and a column density $\eta$-PDF tail much flatter than other ridge subregions (see [6](#fig:various eta-PDF)e in the case of MM2). The high level of core mass segregation observed in MM2 (see [8](#fig:lambda msr)a and [1](#tab:mass segregation)) is in line with that observed after the intense phase of cloud concentration associated with the hierarchical global collapse model (cite: vazquez2019). Subregions in their main burst should exhibit a CMF high-mass end, which is top-heavy (see, e.g., [10](#fig:PDF CMF mm2 mm10)b). This associated over-numerous population of high-mass cores, with respect to intermediate-mass cores, is a consequence of the high cloud dynamics developing during a burst. Gas streams would indeed preferentially feed high-mass cores, increasing their mass even more (cite: smith2009), while preventing the formation of low-mass cores, whose low density hardly protects them from disruptions by shearing motions (cite: ntormousi2015).

Subregions in a post-burst regime (see bottom-panels of [11](#fig:summary)) probably have cloud properties similar to those of subregions in their main burst, both in terms of volume density and slope of the column density $\eta$-PDF tail (see Tables [\[tab:subregions chara\]](#tab:subregions chara)–[\[tab:cmf and s\]](#tab:cmf and s) and [6](#fig:various eta-PDF)f in the case of MM3). However, in the densest parts of the post-burst cloud, young stars should have replaced their first-generation cores and feedback effects due to the expansion of potential Hii regions likely slow further core formation. This first star formation event likely reshaped the CMF and $\Lambda_{\rm MSR}$ functions (see Figs. [4](#fig:various cmfs)b and [8](#fig:lambda msr)c), with the most massive cores at cloud center being consumed and subsequent formation of low-mass cores being slowed down due to tidal effects of shearing motions (cite: ntormousi2015).

![](fig-resume.png)

To confirm the cloud formation scenario of [11](#fig:summary), it is necessary to trace gas inflow through for instance, C$^{18}$O, DCN, and N$_2$H$^+$ lines, and shocks associated with cloud formation and gas feeding onto cores, notably with SiO and methanol lines (cite: peretto2013; louvet2016; csengeri2018). The ALMA-IMF survey provides the appropriate lines and associated dynamical studies are planned (cite: cunningham2023). The present article studied two protoclusters that are too young to constrain the latest phases of the evolutionary scenario of [11](#fig:summary). The ALMA-IMF Large Program imaged four evolved, massive protoclusters, which are associated with developed Hii regions: G010.62, G012.80, G333.60, and W51-IRS2 (cite: motte2022). They are the focus of ongoing studies for their core population (cite: louvet2023) that will soon give us insights on the latest phases of the CMF evolution.

# Summary and conclusions

We have used the most complete and most robust sample of cores obtained to date as part of the ALMA-IMF Large Program to study the dependence of the CMF on the cloud and protocluster properties. Our main results and conclusions can be summarized as follows.

- We used a database consisting of the 1.3 mm continuum image and core catalog produced by Paper III (cite: pouteau2022) for the W43-MM2&MM3 mini-starburst ridge. The ALMA image covers the $\sim$10 pc$^2$ cloud and hosts a cluster of 205 cores with sizes of $\sim$3400 au and masses ranging from 0.1 $\ensuremath{M_{\odot}}$ to 70 $\ensuremath{M_{\odot}}$ (see Sect. [2.1](#sect:obs and catalog) and [1](#fig:nh2 and cores)). The pre-stellar versus protostellar nature of cores is taken from Paper V (cite: nony2023) to estimate the protostellar fraction.

- Using the MnGSeg technique, we separated the W43-MM2&MM3 ridge into six subregions that are expected to simultaneously form stellar clusters. They have typical sizes of $0.5-1$ pc and are called MM2, MM3, MM10, MM12, MM51, and Outskirts (see Sect. [2.2](#sect:subregions def) and [2](#fig:mngseg scales)). We then built the column density image of W43-MM2&MM3 from its continuum image at 1.3 mm and an offset measured on the *Herschel* column density image (see Sect. [2.3](#sect:subregions coldens and mass) and Figs. [1](#fig:nh2 and cores) and [13](#appendixfig:pdf W43 herschel)). These subregions span a large range of masses, column densities, and volume densities (see [\[tab:subregions chara\]](#tab:subregions chara)).

- The measured high-mass end of subregion CMFs in their cumulative form varies from being top-heavy, $\alpha\in [-0.95;-0.59]$, to close to the Salpeter slope, $\alpha\in [-1.54;-1.16]$, (see Sect. [3.1](#sect:spatial variations of core pop), [4](#fig:various cmfs) and [\[tab:cmf and s\]](#tab:cmf and s)). They are fitted by single power laws of the form $N(> \log M) \propto M^\alpha$ using a bootstrapping method that uses a MLE method and takes the uncertainties on the core masses and on the sample low-number statistics as well as the incompleteness into account.

- We then analyzed the variations, in W43-MM2&MM3, of the cloud density structure and the core mass segregation (see Sects. [3.2](#sect:PDFs)–[3.3](#sect:mass segregation)). The subregion $\eta$-PDFs exhibit a tail up to extremely high column densities, $N_{\rm H_2}\sim 2.6\times 10^{25}$ cm$^{-2}$ (see [6](#fig:various eta-PDF)), which is fitted by two power laws, with slope $s_2$ in the range \[-2.4 ; -0.6\] and $s_3$ in the range \[-0.9 ; -0.1\] (see Sect. [3.2](#sect:PDFs) and [\[tab:cmf and s\]](#tab:cmf and s)). We then examined the mass segregation of cores in the subregions using the $\Sigma_{\rm 6\,cores}$ and $\Lambda_{\rm MSR}$ indicators (see Sect. [3.3](#sect:mass segregation) and Figs. [7](#fig:sigma6)–[8](#fig:lambda msr)). We find that the MM2, MM3, and MM10 subregions can be mass-segregated, with a very high level for MM2 (see [1](#tab:mass segregation)).

- Subregions with top-heavy CMFs display flat $\eta$-PDF tails, which is consistent with those obtained for the second tail of high-mass star-forming regions (see Sect. [4.2](#sect:link CMF-PDF) and [\[tab:eta-pdf characteristics\]](#tab:eta-pdf characteristics)). In contrast, subregions with a CMF high-mass end close to the Salpeter slope have much steeper $\eta$-PDF tails, reminiscent of those measured for low-mass star-forming regions. In more detail, we observed a correlation trend between the CMF power-law index and the slope coefficient of the second $\eta$-PDF tail that corresponds to the cores’ immediate background (see [9](#fig:correlation alpha vs s and proto)a).

- We used the fraction of protostellar cores and the existence of an UCHii region in MM3 to define the evolutionary stage of subregions, ranging from quiescent to post-burst via pre-burst and burst (see Sect. [4.3.1](#sect:evolutionary stage) and [\[tab:cmf and s\]](#tab:cmf and s)). Subregions in their main burst of star formation, just at its beginning or its end, are those with the flattest $\eta$-PDF tails and top-heavy CMFs, both likely resulting from an intense cloud formation and concentration at high column density. Subregions in the quiescent or pre-burst regimes have the steepest $\eta$-PDF tails and CMFs close to the Salpeter slope. We find a correlation trend between the power-law index of the CMF at the high-mass end and the protostellar fraction, which is used as a proxy for the star formation history in the W43-MM2&MM3 subregions.

In the framework of dynamical cloud and star formation scenarios, such as in the competitive accretion, global hierarchical collapse, or inertial inflow models, part of the cloud collapses and most of it disperses (cite: smith2009; vazquez2019; pelkonen2021). At parsec scales and high column density ($>10^{23}$ cm$^{-2}$), cloud ridges created by this global collapse would in turn contain centrally concentrated, collapsing hubs, which are the focus of large amounts of gas, and more weakly concentrated subregions, which should not be much impacted by the hierarchical collapse (cite: motte2018a; vazquez2019). The W43-MM2&MM3 ridge indeed consists of the weakly concentrated subregions MM51 and Outskirts, the intermediate subregions MM10 and MM12, and the centrally concentrated hubs MM2 and MM3, with MM2 and MM3 likely in their burst and post-burst regimes, respectively (see [11](#fig:summary)).

In the weakly concentrated subregions of W43-MM2&MM3, star formation may develop in a continuous, almost quasi-static manner. Their more distributed cloud structure would lead to a core population without mass segregation and exhibiting a typical CMF that resembles the canonical IMF. In contrast, in the centrally concentrated subregions of W43-MM2&MM3, the cloud $\eta$-PDF has a flat second tail that could be the signature of the onset of rotation. The extreme column density reached in these subregions favors the formation of massive cores. The resulting CMF high-mass end is top-heavy, leading to a star formation burst and a high level of core mass segregation. When feedback effects begin to set in, the characteristics of the core population, such as CMF and mass segregation, are impacted well before the cloud density structure, including its $\eta$-PDF function.

Since the largest part of a cloud, even if dynamically forming, would more closely resemble the MM51 or Outskirts subregions, we expect the average CMF of the cloud to be typical of low-mass star-forming regions, with a high-mass end close to the Salpeter slope. Top-heavy CMFs would then develop only locally, at a few specific locations in a globally collapsing cloud where column density is greater than $10^{23}$ cm$^{-2}$.

Better understanding the link of the cloud structure, and in particular its $\eta$-PDF, to the CMF shape and possibly the IMF shape would require theoretical models to specifically simulate and analyze extreme-density clouds either corresponding to the converging points of clouds undergoing a hierarchical global collapse or to clouds heated and compressed by stellar feedback.

# Acknowledgements

This paper makes use of the ALMA data ADS/JAO.ALMA#2017.1.01355.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This project has received funding from the European Research Council (ERC) via the ERC Synergy Grant *ECOGAL* (grant 855130), from the French Agence Nationale de la Recherche (ANR) through the project *COSMHIC* (ANR-20-CE31-0009), and the French Programme National de Physique Stellaire and Physique et Chimie du Milieu Interstellaire (PNPS and PCMI) of CNRS/INSU (with INC/INP/IN2P3).

YP acknowledges funding from the IDEX Université Grenoble Alpes under the Initiatives de Recherche Stratégiques (IRS) “Origine de la Masse des Étoiles dans notre Galaxie” (OMEGa).

YP, BL and GB acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme, for the Project “The Dawn of Organic Chemistry” (DOC), grant agreement No 741002. GB also acknowledges funding from the State Agency for Research (AEI) of the Spanish MCIU through the AYA2017-84390-C2-2-R grant and from the PID2020-117710GB-I00 grant funded by MCIN/ AEI /10.13039/501100011033 .

RGM, TN, and DDG acknowledge support from UNAM-PAPIIT project IN108822. RGM is also supported by CONACyT Ciencia de Frontera project ID 86372. TN acknowledges support from the postdoctoral fellowship program of the UNAM.

AGi acknowledges support from the National Science Foundation under grant No. 2008101.

TCs and MB have received financial support from the French State in the framework of the IdEx Université de Bordeaux Investments for the future Program.

PS was supported by a Grant-in-Aid for Scientific Research (KAKENHI Number 18H01259) of the Japan Society for the Promotion of Science (JSPS). P.S. and H.-L.L. gratefully acknowledge the support from the NAOJ Visiting Fellow Program to visit the National Astronomical Observatory of Japan in 2019, February.

AS gratefully acknowledges funding support through Fondecyt Regular (project code 1180350), from the ANID BASAL project FB210003, and from the Chilean Centro de Excelencia en Astrofísica y Tecnologías Afines (CATA) BASAL grant AFB-170002.

FL acknowledges the support of the Marie Curie Action of the European Union (project *MagiKStar*, Grant agreement number 841276).

SB acknowledges support from the French Agence Nationale de la Recherche (ANR) through the project *GENESIS* (ANR-16-CE92-0035-01).

TB acknowledges the support from S. N. Bose National Centre for Basic Sciences under the Department of Science and Technology, Govt. of India.

LB gratefully acknowledges support by the ANID BASAL projects ACE210002 and FB210003.

K.T. was supported by JSPS KAKENHI (Grant Number 20H05645).

130 natexlab

(ref: allison2009b) Allison, R. J., Goodwin, S. P., Parker, R. J., et al. 2009, ApJL, 700, L99

(ref: alstott2014) Alstott, J., Bullmore, E., & Plenz, D. 2014, PLoS ONE, 9, e85777

(ref: alves2014) Alves, J., Lombardi, M., & Lada, C. J. 2014, A&A, 565, A18

(ref: alves2017) Alves, J., Lombardi, M., & Lada, C. J. 2017, A&A, 606, L2

(ref: andre2014) André, P., Di Francesco, J., Ward-Thompson, D., et al. 2014, Protostars and Planets VI, 27

(ref: andre1993) André, P., Ward-Thompson, D., & Barsony, M. 1993, ApJ, 406, 122

(ref: ballesteros-paredes2020) Ballesteros-Paredes, J., André, P., Hennebelle, P., et al. 2020, Space Sci. Rev., 216, 76

(ref: ballesteros-paredes2015) Ballesteros-Paredes, J., Hartmann, L. W., Pérez-Goytia, N., & Kuznetsova, A. 2015, MNRAS, 452, 566

(ref: ballesteros-paredes2011) Ballesteros-Paredes, J., Vázquez-Semadeni, E., Gazol, A., et al. 2011, MNRAS, 416, 1436

(ref: bally2010) Bally, J., Anderson, L. D., Battersby, C., et al. 2010, A&A, 518, L90

(ref: bastian2010) Bastian, N., Covey, K. R., & Meyer, M. R. 2010, ARA&A, 48, 339

(ref: bik2005) Bik, A., Kaper, L., Hanson, M. M., & Smits, M. 2005, A&A, 440, 121

(ref: blum1999) Blum, R. D., Damineli, A., & Conti, P. S. 1999, AJ, 117, 1392

(ref: busquet2019) Busquet, G., Girart, J. M., Estalella, R., et al. 2019, A&A, 623, L8

(ref: busquet2013) Busquet, G., Zhang, Q., Palau, A., et al. 2013, ApJL, 764, L26

(ref: carlhoff2013) Carlhoff, P., Nguyen Luong, Q., Schilke, P., et al. 2013, A&A, 560, A24

(ref: chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: chabrier2005) Chabrier, G. 2005, in Astrophysics and Space Science Library, Vol. 327, The Initial Mass Function 50 Years Later, ed. E. Corbelli, F. Palla, & H. Zinnecker, 41

(ref: clauset2009) Clauset, A., Shalizi, C. R., & Newman, M. E. J. 2009, SIAM Review, 51, 661

(ref: csengeri2011) Csengeri, T., Bontemps, S., Schneider, N., Motte, F., & Dib, S. 2011, A&A, 527, A135

(ref: csengeri2018) Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2018, A&A, 617, A89

(ref: cunningham2023) Cunningham, N., Ginsburg, A., & Galván-Madrid, R. 2023, A&A (submitted)

(ref: dibHenning2019) Dib, S. & Henning, T. 2019, A&A, 629, A135

(ref: dib2018segreg) Dib, S., Schmeja, S., & Parker, R. J. 2018, MNRAS, 473, 849

(ref: didelon2015) Didelon, P., Motte, F., Tremblin, P., et al. 2015, A&A, 584, A4

(ref: donkov2021) Donkov, S., Stefanov, I. Z., Veltchev, T. V., & Klessen, R. S. 2021, MNRAS, 505, 3655

(ref: enoch2008) Enoch, M. L., Evans, Neal J., I., Sargent, A. I., et al. 2008, ApJ, 684, 1240

(ref: federrathKlessen2013) Federrath, C. & Klessen, R. S. 2013, ApJ, 763, 51

(ref: froebrichRowles2010) Froebrich, D. & Rowles, J. 2010, MNRAS, 406, 1350

(ref: FujiiPortegies-Zwart2016) Fujii, M. S. & Portegies Zwart, S. 2016, ApJ, 817, 4

(ref: galvanmadrid2013) Galván-Madrid, R., Liu, H. B., Zhang, Z. Y., et al. 2013, ApJ, 779, 121

(ref: ginsburg2022) Ginsburg, A., Csengeri, T., Galván-Madrid, R., et al. 2022, A&A, 662, A9 (Paper II)

(ref: girichidis2014) Girichidis, P., Konstandin, L., Whitworth, A. P., & Klessen, R. S. 2014, ApJ, 781, 91

(ref: hennebelle2022) Hennebelle, P., Lebreuilly, U., Colman, T., et al. 2022, arXiv e-prints, arXiv:2210.12475

(ref: hennemann2012) Hennemann, M., Motte, F., Schneider, N., et al. 2012, A&A, 543, L3

(ref: hetem2019) Hetem, A. & Gregorio-Hetem, J. 2019, MNRAS, 490, 2521

(ref: hill2011) Hill, T., Motte, F., Didelon, P., et al. 2011, A&A, 533, A94

(ref: hopkins2012) Hopkins, P. F. 2012, MNRAS, 423, 2037

(ref: hosek2019) Hosek, Matthew W., J., Lu, J. R., Anderson, J., et al. 2019, ApJ, 870, 44

(ref: jaupartChabrier2020) Jaupart, E. & Chabrier, G. 2020, ApJL, 903, L2

(ref: juvela2015) Juvela, M., Demyk, K., Doi, Y., et al. 2015, A&A, 584, A94

(ref: kainulainen2009) Kainulainen, J., Beuther, H., Henning, T., & Plume, R. 2009, A&A, 508, L35

(ref: kainulainen2013) Kainulainen, J., Federrath, C., & Henning, T. 2013, A&A, 553, L8

(ref: khullar2021) Khullar, S., Federrath, C., Krumholz, M. R., & Matzner, C. D. 2021, MNRAS, 507, 4335

(ref: kim2006) Kim, S. S., Figer, D. F., Kudritzki, R. P., & Najarro, F. 2006, ApJL, 653, L113

(ref: klessen2000) Klessen, R. S. 2000, ApJ, 535, 869

(ref: kong2019) Kong, S. 2019, ApJ, 873, 31

(ref: konyves2020) Könyves, V., André, P., Arzoumanian, D., et al. 2020, A&A, 635, A34

(ref: konyves2015) Könyves, V., André, P., Men’shchikov, A., et al. 2015, A&A, 584, A91

(ref: kroupa2002) Kroupa, P. 2002, Science, 295, 82

(ref: kroupa2013) Kroupa, P., Weidner, C., Pflamm-Altenburg, J., et al. 2013, in Planets, Stars and Stellar Systems. Volume 5: Galactic Structure and Stellar Populations, ed. T. D. Oswalt & G. Gilmore, 115

(ref: krumholz2015) Krumholz, M. R. 2015, in Astrophysics and Space Science Library, Vol. 412, Very Massive Stars in the Local Universe, ed. J. S. Vink, 43

(ref: ladjelate2020) Ladjelate, B., André, P., Könyves, V., et al. 2020, A&A, 638, A74

(ref: lane2016) Lane, J., Kirk, H., Johnstone, D., et al. 2016, ApJ, 833, 44

(ref: leeHennebelle2018a) Lee, Y.-N. & Hennebelle, P. 2018a, A&A, 611, A88

(ref: leeHennebelle2018b) Lee, Y.-N. & Hennebelle, P. 2018b, A&A, 611, A89

(ref: lin2019) Lin, Y., Csengeri, T., Wyrowski, F., et al. 2019, A&A, 631, A72

(ref: lin2016) Lin, Y., Liu, H. B., Li, D., et al. 2016, ApJ, 828, 32

(ref: louvet2016) Louvet, F., Motte, F., Gusdorf, A., et al. 2016, A&A, 595, A122

(ref: louvet2014) Louvet, F., Motte, F., Hennebelle, P., et al. 2014, A&A, 570, A15

(ref: louvet2023) Louvet, F., Sanhueza, P., & Stutz, A. 2023, A&A (submitted)

(ref: lu2013) Lu, J. R., Do, T., Ghez, A. M., et al. 2013, ApJ, 764, 155

(ref: lu2020) Lu, X., Cheng, Y., Ginsburg, A., et al. 2020, ApJL, 894, L14

(ref: lumsden2013) Lumsden, S. L., Hoare, M. G., Urquhart, J. S., et al. 2013, ApJS, 208, 11

(ref: maia2016) Maia, F. F. S., Moraux, E., & Joncour, I. 2016, MNRAS, 458, 3027

(ref: marks2012) Marks, M., Kroupa, P., Dabringhausen, J., & Pawlowski, M. S. 2012, MNRAS, 422, 2246

(ref: marsh2016) Marsh, K. A., Kirk, J. M., André, P., et al. 2016, MNRAS, 459, 342

(ref: marsh2015) Marsh, K. A., Whitworth, A. P., & Lomax, O. 2015, MNRAS, 454, 4282

(ref: martins2005) Martins, F., Schaerer, D., & Hillier, D. J. 2005, A&A, 436, 1049

(ref: maschbergerClarke2011) Maschberger, T. & Clarke, C. J. 2011, MNRAS, 416, 541

(ref: mckeeOstriker2007) McKee, C. F. & Ostriker, E. C. 2007, ARA&A, 45, 565

(ref: men2021getsf) Men’shchikov, A. 2021, A&A, 649, A89

(ref: motte1998) Motte, F., Andre, P., & Neri, R. 1998, A&A, 336, 150

(ref: motte2022) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8 (Paper I)

(ref: motte2018a) Motte, F., Bontemps, S., & Louvet, F. 2018a, ARA&A, 56 \[\]

(ref: motte2014) Motte, F., Nguyên Luong, Q., Schneider, N., et al. 2014, A&A, 571, A32

(ref: motte2018b) Motte, F., Nony, T., Louvet, F., et al. 2018b, Nature Astronomy, 2, 478

(ref: motte2003) Motte, F., Schilke, P., & Lis, D. C. 2003, ApJ, 582, 277

(ref: motte2010) Motte, F., Zavagno, A., Bontemps, S., et al. 2010, A&A, 518, L77

(ref: myers2015) Myers, P. C. 2015, ApJ, 806, 226

(ref: myers2017) Myers, P. C. 2017, ApJ, 838, 10

(ref: nguyen2017) Nguyen-Luong, Q., Anderson, L. D., Motte, F., et al. 2017, ApJL, 844, L25

(ref: nguyen2013) Nguyen Luong, Q., Motte, F., Carlhoff, P., et al. 2013, ApJ, 775, 88

(ref: nguyen2011b) Nguyen Luong, Q., Motte, F., Schuller, F., et al. 2011, A&A, 529, A41

(ref: nguyen2016) Nguyen-Luong, Q., Nguyen, H. V. V., Motte, F., et al. 2016, ApJ, 833, 23

(ref: nony2023) Nony, T., Galvan-Madrid, R., Motte, F., et al. 2023, arXiv e-prints, arXiv:2301.07238 (Paper V)

(ref: nony2021) Nony, T., Robitaille, J. F., Motte, F., et al. 2021, A&A, 645, A94

(ref: ntormousi2015) Ntormousi, E. & Hennebelle, P. 2015, A&A, 574, A130

(ref: olguin2021) Olguin, F. A., Sanhueza, P., Guzmán, A. E., et al. 2021, ApJ, 909, 199

(ref: OssenkopfHenning1994) Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943

(ref: Ossenkopf-Okada2016) Ossenkopf-Okada, V., Csengeri, T., Schneider, N., Federrath, C., & Klessen, R. S. 2016, A&A, 590, A104

(ref: padoan2011) Padoan, P. & Nordlund, Å. 2011, ApJL, 741, L22

(ref: parker2018) Parker, R. J. 2018, MNRAS, 476, 617

(ref: parkerGoodwin2015) Parker, R. J. & Goodwin, S. P. 2015, MNRAS, 449, 3381

(ref: parkerMeyer2012) Parker, R. J. & Meyer, M. R. 2012, MNRAS, 427, 637

(ref: pelkonen2021) Pelkonen, V. M., Padoan, P., Haugbølle, T., & Nordlund, Å. 2021, MNRAS, 504, 1219

(ref: peretto2013) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, A&A, 555, A112

(ref: plunkett2018) Plunkett, A. L., Fernández-López, M., Arce, H. G., et al. 2018, A&A, 615, A9

(ref: pokhrel2016) Pokhrel, R., Gutermuth, R., Ali, B., et al. 2016, MNRAS, 461, 22

(ref: polychroni2013) Polychroni, D., Schisano, E., Elia, D., et al. 2013, ApJL, 777, L33

(ref: pouteau2022) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26 (Paper III)

(ref: riveraIngraham2015) Rivera-Ingraham, A., Martin, P. G., Polychroni, D., et al. 2015, ApJ, 809, 81

(ref: rivera-soto2020) Rivera-Soto, R., Galván-Madrid, R., Ginsburg, A., & Kurtz, S. 2020, ApJ, 899, 94

(ref: robitaille2019) Robitaille, J. F., Motte, F., Schneider, N., Elia, D., & Bontemps, S. 2019, A&A, 628, A33

(ref: russeil2013) Russeil, D., Schneider, N., Anderson, L. D., et al. 2013, A&A, 554, A42

(ref: sadavoy2014) Sadavoy, S. I., Di Francesco, J., André, P., et al. 2014, ApJL, 787, L18

(ref: salpeter1955) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: sanhueza2019) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102

(ref: sanhueza2021) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10

(ref: schneider2018) Schneider, F. R. N., Sana, H., Evans, C. J., et al. 2018, Science, 359, 69

(ref: schneider2013) Schneider, N., André, P., Könyves, V., et al. 2013, ApJL, 766, L17

(ref: schneider2015) Schneider, N., Bontemps, S., Girichidis, P., et al. 2015, MNRAS, 453, 41

(ref: schneider2016) Schneider, N., Bontemps, S., Motte, F., et al. 2016, A&A, 587, A74

(ref: schneider2010) Schneider, N., Csengeri, T., Bontemps, S., et al. 2010, A&A, 520, A49+

(ref: schneider2012) Schneider, N., Csengeri, T., Hennemann, M., et al. 2012, A&A, 540, L11

(ref: schneider2022) Schneider, N., Ossenkopf-Okada, V., Clarke, S., et al. 2022, arXiv e-prints, arXiv:2207.14604

(ref: shu1987) Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23

(ref: smith2014) Smith, R. J. 2014, MNRAS, 443, L69

(ref: smith2009) Smith, R. J., Clark, P. C., & Bonnell, I. A. 2009, MNRAS, 396, 830

(ref: stutzKainulainen2015) Stutz, A. M. & Kainulainen, J. 2015, A&A, 577, L6

(ref: suarez2023) Suárez, G., Juárez-Gama, M., & Galván-Madrid, R. 2023, A&A (submitted)

(ref: takemura2021) Takemura, H., Nakamura, F., Kong, S., et al. 2021, ApJL, 910, L6

(ref: testi-sargent1998) Testi, L. & Sargent, A. I. 1998, ApJL, 508, L91

(ref: tremblin2014) Tremblin, P., Schneider, N., Minier, V., et al. 2014, A&A, 564, A106

(ref: vazquez2019) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061

(ref: veltchev2019) Veltchev, T. V., Girichidis, P., Donkov, S., et al. 2019, Monthly Notices of the Royal Astronomical Society, 489, 788

(ref: wang2010) Wang, P., Li, Z.-Y., Abel, T., & Nakamura, F. 2010, ApJ, 709, 27

(ref: wyrowski2016) Wyrowski, F., Güsten, R., Menten, K. M., et al. 2016, A&A, 585, A149

(ref: zhang2014) Zhang, B., Moscadelli, L., Sato, M., et al. 2014, ApJ, 781, 89

(ref: zhang2018) Zhang, Z.-Y., Romano, D., Ivison, R. J., Papadopoulos, P. P., & Matteucci, F. 2018, Nature, 558, 260

# Complementary figures

Appendix [6](#appendixsect:complementary figures) shows in [12](#appendixfig:PPMAP with NH2) the temperature map with the $N_{\rm H_2}$ contours of Figs. [1](#fig:nh2 and cores)b–c, and in [13](#appendixfig:pdf W43 herschel) the comparison of the column density $\eta$-PDFs derived from [1](#fig:nh2 and cores) and *Herschel* data (cite: nguyen2013). It also displays the fitted functions to the bootstrapping distributions of power-law indices of the CMF high-mass end measured in the MM2, MM3, MM10, and Outskirts subregions (see [14](#appendixfig:EMG subreg)).

![](MM2MM3_temperature_map_contoursNH2.jpg)

![image](PDF_Herschel-ALMAoffsets.png) ![image](PDF_Herschel-Alma.png)

![](emg_subreg.png)

[^1]: ALMA project #2017.1.01355.L; see <http://www.almaimf.com> (PIs: Motte, Ginsburg, Louvet, Sanhueza).

[^2]: Full catalog is available at the CDS via anonymous ftp to cdsarc.u-strasbg.fr (ftp://130.79.128.5) or via <http://cdsarc.u-strasbg.fr/viz-bin/cat/J/A+A/664/A26>

[^3]: This pipeline performs several iterations of phase self-calibration using custom masks in order to better define the self-calibration model and clean more and more deeply using the TCLEAN task and refined parameters after each pass. The pipeline is available at <https://github.com/ALMA-IMF/reduction> .

[^4]: The *Herschel* column density image used here is taken from the archival data products of the HOBYS key program (cite: motte2010). See <https://www.hobys.org/data.html>.

[^5]: https://www.hobys.org/

[^6]: As described in (cite: suarez2023), we used the equations in (cite: rivera-soto2020) and (cite: martins2005) and estimated a mass of $\sim$22 $\ensuremath{M_{\odot}}$ for the star ionizing the UCHii .

</paper>

## Items to check

```json
[
 {
  "path": "data.simulations_or_models_as_data[0].evidence[1]",
  "value": "Three numerical simulation models (Model #24, Model #C1t03, Model M=3, SFE=20%) used for comparing theoretical volume/column density PDF slopes with observed eta-PDF tails",
  "failed_quote": "We used [eq:s] to predict, from the power-law exponent, $\\psi$, of the models, the power-law exponent $s$ that an $\\eta$-PDF tail computed from the simulated volume density cube projected into a column density image would have (cite: kainulainen2013; leeHennebelle2018b; jaupartChabrier2020)."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Subregion uncertainties estimated by slightly varying the integration areas",
  "failed_quote": "Uncertainties are estimated by slightly varying the integration areas of Figs. 1–2 (see [tab:subregions chara]) to take into account uncertainties in the definition of subregion outlines and areas."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[1]",
  "value": "5000 bootstrap iterations; fit range from 90% completeness limit (+/- 0.2 M_sun) to maximum core mass in each subregion",
  "failed_quote": "We allowed the fit of the initial point of the power-law fit to uniformly vary from the 90% completeness level, plus or minus its uncertainty, $\\pm 0.2~\\ensuremath{M_{\\odot}}$ (see [tab:cmf and s])."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[1]",
  "value": "Power-law fits to the second (s_2) and third (s_3) tails; Herschel eta-PDF fitted by the sum of a lognormal function (< 1.5 x 10^23 cm^-2) and two consecutive power-law tails following Schneider et al. (2022).",
  "failed_quote": "[tab:cmf and s] lists, for each subregion, the ranges of these two $\\eta$-PDF tails and their fitted power-law exponents, $s_2$ and $s_3$."
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Uncertainties estimated by varying bin numbers, fit range limits, and background column density offsets; tested constant dust temperature assumption (changes s_2 and s_3 by <= 10%).",
  "failed_quote": "Uncertainties on the power-law exponents are estimated by varying the number of bins of the $\\eta$-PDFs, the limits of the fit ranges, and by taking into account the uncertainty on the column density offset (see [tab:cmf and s])."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Compute two mass segregation indicators in tandem: (1) ratio of local core surface density of the five most massive cores (using 6 closest neighbors) to the subregion average, (Sigma_6cores)_massive / mean(Sigma_6cores); and (2) mass segregation ratio Lambda_MSR using the minimum spanning tree (MST) method.",
  "failed_quote": "in the W43-MM2&MM3 subregions, we measured the $\\Sigma_{\\rm 6\\,cores}$ for the five most massive cores, $\\left(\\Sigma_{\\rm 6\\,cores}\\right)_{\\rm massive}$."
 },
 {
  "path": "analysis_steps[5].method.evidence[0]",
  "value": "Classify subregions into evolutionary stages (Quiescent, Pre-burst, Main burst, Post-burst) based on protostellar core fraction, core surface number density, and UCHII region presence; compare CMF high-mass end index alpha against subregion properties, core mass segregation, second eta-PDF tail slope s_2, and protostellar fraction.",
  "failed_quote": "To define the evolutionary stage of these $\\sim$0.5–1 pc cloud structures, we quantify the development of the star formation process through three criteria. These are the protostellar core fraction of the subregion, its surface density of cores, both quantified in Sect. 3 (see Tables [tab:subregions chara] and 1), and the potential UCHii regions."
 },
 {
  "path": "analysis_steps[5].method.evidence[1]",
  "value": "Classify subregions into evolutionary stages (Quiescent, Pre-burst, Main burst, Post-burst) based on protostellar core fraction, core surface number density, and UCHII region presence; compare CMF high-mass end index alpha against subregion properties, core mass segregation, second eta-PDF tail slope s_2, and protostellar fraction.",
  "failed_quote": "Figure 9 displays, for each W43-MM2&MM3 subregion, the relation between the power-law index of the CMF high-mass end and the slope coefficient of the second $\\eta$-PDF tail, $\\alpha$ and $s_2$, and the protostellar fraction listed in [tab:cmf and s]."
 },
 {
  "path": "analysis_steps[5].key_parameters[0].evidence[0]",
  "value": "Average core surface density ~35 cores/pc^2 and average protostellar fraction ~25% used as baseline thresholds",
  "failed_quote": "They qualify as quiescent because their surface number density of cores and their protostellar fraction are lower or equal to the average values measured in the W43-MM2&MM3 subregions ($\\sim$35 cores/pc$^2$ and $\\sim$25%; see Tables [tab:subregions chara]–[tab:cmf and s])."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "Subregions with flat second eta-PDF tails display top-heavy CMFs, whereas subregions with steep second eta-PDF tails have CMFs close to the Salpeter slope.",
  "failed_quote": "Subregions with top-heavy CMFs display flat $\\eta$-PDF tails, which is consistent with those obtained for the second tail of high-mass star-forming regions (see Sect. 4.2 and [tab:eta-pdf characteristics])."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "The CMF is not uniform across the ridge; it varies from Salpeter-like in quiescent/pre-burst environments to top-heavy in dense, active star-forming hubs.",
  "failed_quote": "The peak of these functions locate the most likely power-law index of their CMF high-mass ends, which vary from $\\alpha=-1.54$ for the Outskirts to $\\alpha=-0.59$ for the MM3 subregion (see [tab:cmf and s])."
 },
 {
  "path": "claims[2].evidence[0]",
  "value": "While extreme centrally concentrated hubs like MM2 show both very high mass segregation and a top-heavy CMF, there is no one-to-one correspondence between core mass segregation and the slope of the CMF high-mass end.",
  "failed_quote": "This condition is not a necessary one to build a flat CMF, as proven by the MM12 subregion where no mass segregation is observed (see Tables [tab:cmf and s]–1)."
 }
]
```
