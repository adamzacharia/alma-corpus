# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023ApJ...951L..38N\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Evidence for ubiquitous carbon grain destruction in hot protostellar envelopes

## Abstract

Earth is deficient in carbon and nitrogen by up to ${\sim}4$ orders of magnitude compared with the Sun. Destruction of (carbon- and nitrogen-rich) refractory organics in the high-temperature planet forming regions could explain this deficiency. Assuming a refractory cometary composition for these grains, their destruction enhances nitrogen-containing oxygen-poor molecules in the hot gas ($\gtrsim 300$ K) after the initial formation and sublimation of these molecules from oxygen-rich ices in the warm gas (${\sim}150$ K). Using observations of $37$ high-mass protostars with ALMA, we find that oxygen-containing molecules (CH$_3$OH and HNCO) systematically show no enhancement in their hot component. In contrast, nitrogen-containing, oxygen-poor molecules (CH$_3$CN and C$_2$H$_3$CN) systematically show an enhancement of a factor ${\sim} 5$ in their hot component, pointing to additional production of these molecules in the hot gas. Assuming only thermal excitation conditions, we interpret these results as a signature of destruction of refractory organics, consistent with the cometary composition. This destruction implies a higher C/O and N/O in the hot gas than the warm gas, while, the exact values of these ratios depend on the fraction of grains that are effectively destroyed. This fraction can be found by future chemical models that constrain C/O and N/O from the abundances of minor carbon, nitrogen and oxygen carriers presented here.

# Introduction

Molecules containing carbon are important in discussions related to the origin of life on Earth or other terrestrial planets ((cite: Oberg2021)). However, the Earth is known to be deficient in carbon and nitrogen by at least ${\sim}1-2$ and up to 4 orders of magnitude compared with the interstellar grains and many comets including 1P/Halley and 67P/Churyumov–Gerasimenko ((cite: Geiss1987); (cite: Allegre2001); (cite: Wooden2008); (cite: Marty2012); (cite: Bergin2015); (cite: Rubin2019); (cite: Fischer2020)). To explain this difference, multiple works have suggested that Earth should have formed from solids that are dominated by silicates and depleted of carbon (e.g., (cite: Jura2012); (cite: Gail2017); (cite: Li2021)).

Assuming that all grains start with composition similar to those of the interstellar grains ((cite: Rubin2019); (cite: Duval2022)), a second step of processing of these grains should occur in the inner planet-forming regions around the young star to explain the depletion in carbon. This further processing is thought to be the destruction of solid material that are rich in carbon. Destruction of carbon-rich solids in the inner most regions is also implicated by the deficiency of carbon in the atmospheres of polluted white dwarfs ((cite: Jura2006), (cite: Jura2007); (cite: Gansicke2012); (cite: Farihi2013); (cite: Farihi2016)) due to accretion of carbon-poor asteroids by the white dwarfs.

Most of the carbon is in the so-called refractory organic matter that in addition to carbon contains other elements such as H, N and O, while there are smaller fractions of carbon that exist in other forms such as hydrocarbons and pure carbon grains ((cite: Kissel1986Giotto); (cite: Fomenkova1994); (cite: Fomenkova1997); (cite: Fomenkova1999); (cite: Bardyn2017)). These carbonaceous materials, depending on their form, are thought to be destroyed at different temperatures and through different mechanisms. Figure [1](#fig:layers) summarizes these temperatures as a simple cartoon (see the figure caption for references) ignoring any non-thermal sublimation processes. However, destruction of carbon grains has not yet been directly observed due to absence of spectral features and extinction in protostellar systems. Therefore, an indirect method to observe this phenomenon is to search for its effects on the chemical composition of the hot gas ($\gtrsim 300$ K) located close to the young protostar.

Given that most of carbon is thought to be in refractory organics ((cite: Kissel1986); (cite: Fomenkova1994); (cite: Fray2016)), here we consider the effect of destruction of these types of carbonaceous material on the hot gas chemistry. Destruction of refractory organics has been argued to happen within the first million years of the planetary system formation ((cite: Li2021)). Furthermore, this destruction occurs at high temperatures (${\sim}400-500$ K; (cite: Li2021); (cite: Gail2017)). These high temperatures are achieved up to larger radii in the protostellar phase making young and embedded protostars the prime objects to search for any effect from carbon grain destruction on the gas-phase molecules. Moreover, recent ALMA results have shown that planets start forming in these earlier stages ((cite: Manara2018); (cite: Tychoniec2020)) making the protostellar phase even more relevant for this study.

In the protostellar envelope the temperature at which the refractory organics are sublimated could decrease from ${\sim}400-500$ K to ${\sim}300$ K due to the lower densities and pressures compared to those of the inner disk (see (cite: vantHoff2020) for detailed explanation). Therefore, for spatially unresolved hot core observations where the disk and envelope are not separated the temperature at which the refractory organics are destroyed is likely between ${\sim}300$ K and ${\sim}400$ K. These hot regions are the focus of this work.

It has been speculated that destruction of the refractory organics will result in a top-down formation of oxygen-poor complex organic molecules (COMs, (cite: Herbst2009); (cite: Ceccarelli2022)) in the hot gas ((cite: vantHoff2020)). Therefore, both column densities and excitation temperatures of the oxygen-poor molecules should be affected if carbon grain destruction is effective. We note that this top-down gas-phase formation in the hot gas is an addition to the early cold phase bottom-up formation of COMs in ices ((cite: Gibb2004); (cite: Jorgensen2020)) and the thermal sublimation of these species at temperatures of around 100 K (see Figure [1](#fig:layers)). The hot gas-phase chemistry should be a natural result of destruction of refractory organics if the composition of refractory organics is similar to the refractory material of comets ((cite: Rubin2019)). In particular, (cite: vantHoff2020) searched for differences in the excitation temperatures between O- and N-bearing COMs (i.e., molecules with and without oxygen) as a potential sign of sublimation of carbon grains. In their literature survey, they found that the excitation temperatures for the N-COMs are higher than those for the O-COMs in some sources and the opposite is true for some other sources. Given the non-homogeneous literature reports, while this study showed some interesting trends it was inconclusive, emphasizing the need for systematic surveys and analysis.

In this work we use one such molecular surveys with the Atacama Large Millimeter/submillimeter Array (ALMA) to search for the signatures of destruction of carbon grains through a two-component temperature fit to oxygen-rich and oxygen-poor organics. A similar fitting method was performed by (cite: Neill2014) for their *Herschel* observations. We consider two of the most abundant COMs, namely methanol (CH$_3$OH) and methyl cyanide (CH$_3$CN), in addition to two other molecules with and without oxygen in a large sample of high-luminosity (and potentially high-mass) protostellar systems. These additional species are isocyanic acid (HNCO) and vinyl cyanide (C$_2$H$_3$CN). For the purposes of this paper, when referred to oxygen-rich molecules we imply HNCO and CH$_3$OH and when referred to oxygen-poor molecules we imply CH$_3$CN and C$_2$H$_3$CN. We use data from the large program ALMA Evolutionary study of High Mass Protocluster Formation in the Galaxy (ALMAGAL, PIs: S. Molinari, P. Schilke, C. Battersby, P. Ho) because of its high sensitivity to detect both optically thin minor isotopologues of the most abundant molecules such as methanol to probe the warm gas and the optically thin weak lines of the major isotopologues with $E_{\rm up} > 400-500$ K to probe the hot gas. Therefore, it is only now possible to measure the hot ($\gtrsim 300$ K) and warm ($200 \gtrsim T_{\rm ex} \gtrsim 100$ K) components of the above molecules from their high- and low-$E_{\rm up}$ (upper energy level) lines for a large sample of sources.

In this letter we use data from the ALMAGAL survey to measure the hot column densities of HNCO, CH$_3$OH, CH$_3$CN, and C$_2$H$_3$CN. These molecules have similar sublimation temperatures. We use the detected lines of these molecules with $E_{\rm up} > 400-500$ K (i.e., probing $T \gtrsim 300$ K) for the hot components. We take the warm column densities for the above species from (cite: Nazari2022ALMAGAL), who measure them from the $^{13}$C or $^{18}$O isotopologues of the targeted molecules which only have detected lines with $E_{\rm up} \lesssim 300-400$ K (i.e., probing $T \sim 150$ K). We then compare the ratios of the hot number of molecules to warm number of molecules for species with and without oxygen in a sample of 37 protostellar systems. We develop a simple analytical model to interpret the observations. Through the comparison of observations with the model we search for signs of destruction of refractory organics and find it to be common.

# Observations and methods

## Data

In this work we use the publicly available ALMA data from the ALMAGAL large program (project ID: 2019.1.00195.L). We consider the (high-luminosity and potentially high-mass) sources that were analyzed by (cite: Nazari2022ALMAGAL) (see (cite: vanGelder2022) and (cite: vanGelder2022Deuteration) for results on methanol). The works mentioned above present the full details of the data, here we only give a summary of the observational parameters.

All data used here have an angular resolution between ${\sim} 0.5\ensuremath{''}$ and ${\sim} 1.5\ensuremath{''}$. The angular resolution for high-mass sources located at distances of $2-3$ kpc correspond to radii of between ${\sim}500$ au and ${\sim}2500$ au. The frequency ranges covered for the selected sample are $217.00-218.87$ GHz and ${\sim}219.07-220.95$ GHz. The spectral resolution is around $0.7$ km s$^{-1}$ which results in spectrally resolved molecular lines toward the protostellar systems. The spectra are the same as those used in (cite: Nazari2022ALMAGAL) which were extracted from the peak pixel of the CH$_3$CN 12$_4$–11$_4$ moment zero map. The line rms is ${\sim}0.2$ K for the spectra.

## Spectral fitting

In this work we consider CH$_3$CN, CH$_3$OH, HNCO, and C$_2$H$_3$CN in the data described in Section [2.1](#sec:data) and analyze them with a two-component temperature model. The warm column densities of CH$_3$CN, CH$_3$OH and HNCO are measured from their $^{13}$C or $^{18}$O isotopologues in (cite: Nazari2022ALMAGAL). The isotope ratios in that work were calculated from the relations given in (cite: Wilson1994) and (cite: Milam2005) and the distances of the objects from the Galactic center. If an object is an outlier with respect to those relations, the calculated column densities from isotope ratios could have an additional uncertainty. Using the isotopologues to calculate the column densities is desirable because it avoids the optically thick lines of the main isotopologues. However, it is limited to lower K lines and derivation of a single excitation temperature between 100 K and 200 K. In other words, the $^{13}$C or $^{18}$O isotopologues of CH$_3$CN, CH$_3$OH and HNCO only have lines with $E_{\rm up} < 400$ K detected and hence those column densities miss the hot gas.

Here we attempt to find the column densities of the relevant molecules in the hot regions closer to the protostars by only fitting the optically thin lines of the main isotopologues with $E_{\rm up} \gtrsim 400$ K. The measured hot column densities and excitation temperatures for all the 37 sources are given in Table [\[tab:results\]](#tab:results). The line lists are taken from the Cologne Database for Molecular Spectroscopy (CDMS; (cite: Muller2001); (cite: Muller2005)). Frequencies, quantum numbers, $E_{\rm up}$ and $A_{\rm ij}$ of the considered lines are given in Tables B.1 and E.7 of (cite: vanGelder2022) and (cite: Nazari2022ALMAGAL). For more information on the spectroscopy see Appendix [7](#sec:spec_info). We use the CASSIS[^1] spectral analysis tool ((cite: Vastel2015)) to fit the spectra assuming the same emitting area that was used in (cite: Nazari2022ALMAGAL) for the warm component. However, we stress that the relevant quantity for our study is the total number of molecules ($\mathcal{N} = A N$, where $A$ and $N$ are the emitting area and column density) which does not change if a different emitting area is used as long as the lines are optically thin. In other words, if a smaller emitting area is assumed the derived column density will increase and vice versa such that the total number of molecules stays the same. Therefore, after the derivation of column densities we compare the total numbers of hot and warm molecules with each other (see Section [3](#sec:obs_comparison)). For all sources the column density of the hot component is found using the same fit-by-eye method used in (cite: Nazari2022ALMAGAL) (also see (cite: Chen2023)). Below we explain our method in more detail for each molecule.

Methyl cyanide (CH$_3$CN) in the chosen sample normally has three unblended detected lines with $E_{\rm up} > 400$ K (419 K, 526 K and 782 K) which in addition to the column density, allow the measurement of excitation temperature for the hot gas separately from that of the warm gas. However, when the 782 K line is not detected the temperature is fixed to 300 K. This value is chosen based on the mean of the hot CH$_3$CN excitation temperatures for other sources where a measurement is possible (see Appendix [9](#sec:add_tab_plots)). To test whether this assumption is valid, we varied the excitation temperature from 200 K to as high as 500 K for a few sources and found that the column densities could only change by a factor of $\lesssim2$. Therefore, the conclusions of this work will not be affected by this assumption. For the most line-rich sources the line with $E_{\rm up} = 931$ K is also detected. When fitting these high-$E_{\rm up}$ lines, the lines with $E_{\rm up} < 400$ K are ignored as they are usually (marginally) optically thick and even if they were not optically thick, their emission would be dominated by the warm component. Appendix [9](#sec:add_tab_plots) presents an example of the fitting for the hot column density of CH$_3$CN.

Methanol (CH$_3$OH), similar to methyl cyanide, normally has multiple relatively unblended lines with $E_{\rm up} > 400$  detected in the chosen ALMAGAL sample. These lines have $E_{\rm up}$ of 508 K, 746 K, 776 K, 802 K, and 1181 K. The line with $E_{\rm up} = 508$ K for the most line-rich sources becomes optically thick. Therefore, we ignore this line for all sources to avoid any potentially optically thick lines. When the line with ${\sim}1200$ K ($\nu = 220.887$ GHz and $A_{\rm ij} = 7.5 \times 10^{-5}$ s$^{-1}$) is detected the excitation temperature is measured. Otherwise, it is fixed to 300 K or the upper limit on temperature. Again the lines with $E_{\rm up} < 400$ K are ignored in the fitting for robust measurements of the hot column densities.

Isocyanic acid (HNCO) in the chosen sample normally has two detected lines with $E_{\rm up} > 400$ K, at $E_{\rm up} = 448$ K and $E_{\rm up} = 750$ K. We find the excitation temperatures in addition to the column densities for those sources. However, we note that these excitation temperatures are uncertain given the lack of detected lines with a large range of $E_{\rm up}$, while column densities can be measured accurately. If the HNCO line with $E_{\rm up} = 750$ K is not detected toward a source the temperature is fixed to 300 K. There are also two HNCO transitions with $E_{\rm up}$ of 1050 K and 1450 K which are useful for constraining the upper limit on excitation temperature. Given the tentative nature of C$_2$H$_3$CN results, a description of our methods to obtain C$_2$H$_3$CN column densities is given in Appendix [8](#app:C2H3CN).

# Observational comparison of hot and warm components

The total number of hot to the total number of warm molecules of methanol and methyl cyanide are presented in Figure [2](#fig:ratio_methanol_methyl). The hot to warm ratios of methanol have a weighted mean of 0.12 while that for methyl cyanide is 0.48. The spread around the mean is tight for the two molecules with only a spread of a factor 1.78 and 1.33 around the mean for methanol and methyl cyanide, respectively. Figure [2](#fig:ratio_methanol_methyl) points to an enhancement in the hot component of an oxygen-poor molecule relative to an oxygen-rich one.

To examine whether this trend holds for other molecules with and without oxygen we also found the total number of hot molecules of HNCO (another molecule in addition to methanol with oxygen) and C$_2$H$_3$CN (another molecule in addition to methyl cyanide without oxygen) where possible for our sources (see Table [\[tab:results\]](#tab:results)). Left panel of Figure [3](#fig:ratio_all) presents the hot to warm ratios of these molecules in addition to methanol and methyl cyanide. Figure [3](#fig:ratio_all) shows that HNCO has a similar mean and a similar standard deviation to methanol (factor of 1.77 around the mean). Moreover, the number of hot to the number of warm vinyl cyanide molecules are more similar to those of methyl cyanide with a mean of 1.47 and a factor of 1.44 scatter around the mean. This results in two distinct population of molecules, with at least a ${\sim}0.7$ dex (factor of ${\sim}$5) difference between the mean of the ratios. To conclude, we find that oxygen-poor molecules have a stronger contribution from the hot gas relative to oxygen-rich ones.

# Envelope-only analytical model

Here we explain what is expected for the hot and warm number of molecules from a simple analytical model. Detailed radiative transfer models of low- and high-mass protostars and the effect of temperature structure on number of molecules are found in (cite: Nazari2023).

The number of molecules of species $i$ in the gas phase is the abundance of that molecule ($X_{i}$) multiplied by the total number of hydrogen atoms in the gas phase. Here we assume that $X_{i}$ is solely found from the sublimation of ices at temperature $T_{\rm sub}$. Hence, the total number of molecules for species $i$ in the gas phase is

$$\begin{equation}
     \mathcal{N}_{i} = \int_{0}^{R_{T_{i, \rm sub}}} 4 \pi X_{i} n_{\rm H}(R) R^{2}dR 
    \label{eq:COM_num}
\end{equation}$$

where $R$ is the radius, $n_{\rm H}$ is the number density of hydrogen nucleus and $R_{T_{i,\rm{sub}}}$ is the radius at which the molecule $i$ is sublimated. Once a molecule is thermally sublimated into the gas phase it can trace the hot regions close to the protostar or warm regions further from the protostar at $R < R_{T_{\rm sub}}$.

Therefore, to measure the number of molecules in the hot and warm gas, Equation [\[eq:COM_num\]](#eq:COM_num) can be re-written with the integral limit to be either $R_{T_{i,\rm{hot}}}$ or $R_{T_{i,\rm{warm}}}$ instead of $R_{T_{i,\rm{sub}}}$. Assuming a spherical model with a power-law density and temperature as a function of radius with powers $p=-1.5$ and $q=-0.4$ based on observations and radiative transfer models ((cite: Adams1985); (cite: vanderTak2000); (cite: Nazari2022Lowmass)), the number of molecules for species $i$ in the hot (or warm) gas can be written as (see Appendix B of (cite: Nazari2021))

$$\begin{equation}
    \mathcal{N}_{i, \rm hot} \propto X_{i, \rm hot} T_{i,\rm{hot}}^{-3.75},
    \label{eq:N_i}
\end{equation}$$

The total number of molecules of species $i$ in the hot gas and in the warm gas can then be compared as

$$\begin{equation}
    \frac{\mathcal{N}_{i, \rm hot}}{\mathcal{N}_{i, \rm warm}} = \frac{X_{i,\rm hot}}{X_{i,\rm warm}} \left(\frac{T_{i,\rm{hot}}}{T_{i,\rm{warm}}}\right)^{-3.75}.
    \label{eq:ratio}
\end{equation}$$

Assuming $T_{\rm hot} = 300$ K and $T_{\rm warm} = 150$ K consistent with the average excitation temperatures of the hot and warm gas for the studied molecules (see Appendix [9](#sec:add_tab_plots)), $(T_{i,\rm{hot}}/T_{i,\rm{warm}})^{-3.75} =0.07$. Therefore, if there is no additional gas phase chemistry in the hot gas (i.e., $X_{i,\rm hot}/X_{i,\rm warm} = 1$), $$\begin{equation}
    \frac{\mathcal{N}_{i, \rm hot}}{\mathcal{N}_{i, \rm warm}} \sim 0.1.
\end{equation}$$

It is worth noting that this result is valid for molecules with sublimation temperatures of $\lesssim 100-150$ K so that there exists a warm component in the gas. For example if a molecule has a sublimation temperature of $200-300$ K (e.g., NH$_2$CHO) the molecule will not be present in the gas-phase at 150 K and this result will not be valid for that molecule. The molecules considered in this work (CH$_3$OH, CH$_3$CN, HNCO and C$_2$H$_3$CN) have similar binding energies and hence similar sublimation temperatures at around 100-150 K in the interstellar conditions ((cite: Collings2004); (cite: Das2018); (cite: Song2016); (cite: Wakelam2017); (cite: Bertin2017); (cite: Penteado2017); (cite: Ferrero2020); (cite: Busch2022); (cite: Minissale2022)).

There are some caveats in the above calculation, such as the assumed power of -0.4 for the temperature structure as a function of radius. This value is based on the regions where the envelope is optically thin to the reprocessed emission. To check how this assumption changes the calculations we take a steeper temperature profile with $q=-0.5$ for the optically thick regime (see (cite: Adams1985) for low-mass and (cite: Nazari2023Highmass) for high-mass sources). This will change the power of -3.75 to -3.0 and the value of $\mathcal{N}_{i, \rm hot}/\mathcal{N}_{i, \rm warm}$ from 0.07 to 0.13. Therefore, our assumption of $q$ for high-mass sources such as those from the ALMAGAL sample is only expected to produce a small scatter in the value of 0.1. Moreover, the larger the difference between the assumed $T_{\rm hot}$ and $T_{\rm warm}$, the smaller would be the ratio of $\mathcal{N}_{i, \rm hot}/\mathcal{N}_{i, \rm warm}$. The conclusion is that without any gas-phase chemistry the number of molecules in the hot gas should be around one order of magnitude smaller than that in the warm gas with some variations (less than a factor 2) based on the exact thermal and density structure of the protostellar system.

# Discussion and conclusions

Our findings in Section [3](#sec:obs_comparison) show that the mean of hot number of molecules to warm number of molecules for oxygen-rich species agrees well with the expected ratio of ${\sim} 0.1$ from the simple analytical model in Section [4](#sec:toy). However, this ratio for oxygen-poor species deviates from the analytical model by a factor of about 5 (right panel of Figure [3](#fig:ratio_all)). Therefore, the main assumption made in that model, that is no additional gas-phase chemistry in the hot gas, does not hold for oxygen-poor molecules. This means an enhancement of oxygen-poor species in the hot gas and $X_{i,\rm hot}/X_{i,\rm warm}$ of ${\gtrsim}5$ for these molecules (see Equation [\[eq:ratio\]](#eq:ratio)). In other words, there should be a gas-phase formation route for methyl cyanide (or vinyl cyanide) in the hot gas that does not exist for methanol (or isocyanic acid). This additional route could be the top-down formation mechanism suggested by (cite: vantHoff2020) for nitrogen-bearing oxygen-poor COMs as a result of destruction of refractory organics.

When refractory organics are destroyed nitrogen- and carbon-bearing compounds should increase in the hot gas more than the oxygen-bearing compounds. This is because of the higher percentage of nitrogen and carbon in cometary dust grains compared with cometary ices, while the percentage of oxygen in cometary dust grains is lower than in ices (see (cite: Rubin2019) Table 5). Moreover, the fraction of nitrogen to carbon in pre-solar organic nano-globules is ${\sim}0.1$ and thus nitrogen exists in dust grains ((cite: Jones2016)). The nitrogen- and carbon-bearing compounds could be in the form of NH$_3$, CN, CH$_4$ and other forms of hydrocarbons ((cite: Nakano2003); (cite: wang2013effect); (cite: Gail2017); (cite: vantHoff2020)). This agrees well with chemical models of protoplanetary disks where they find an increase of nitrogen-bearing species such as HCN and depletion of oxygen-rich ones as a result of carbon grain destruction ((cite: Wei2019)). This is also inline with the results from the Infrared Space Observatory which showed enhanced abundances of C$_2$H$_2$ and HCN with increasing temperature in the gas around massive young stellar objects ((cite: Lahuis2000)).

After this additional release of nitrogen- and carbon-bearing species due to the destruction of refractory organics, species without oxygen such as CH$_3$CN could form in the gas-phase. One possible formation route is reaction of CH$_3^+$ and HCN to first form CH$_3$CNH$^+$ which can then produce CH$_3$CN through electronic dissociative recombination ((cite: Garrod2022)). At higher temperatures above 300 K, atomic nitrogen is expected to be released from NH$_3$, NH$_2$ or NH that can then react with CH$_3$ to produce HCN which could again turn into CH$_3$CN through the same mechanism as explained above ((cite: Garrod2022)). For C$_2$H$_3$CN, a plausible high-temperature gas-phase formation route could be the reaction of C$_2$H$_4$ with CN ((cite: Garrod2022)). Both of these minor species are expected to be released from destruction of refractory organics.

We attribute the enhancement of oxygen-poor molecules, CH$_3$CN and C$_2$H$_3$CN, in the hot gas to destruction of refractory organics and find it to be common in high-mass protostellar systems. It is yet to be confirmed whether the trend seen in Fig. [3](#fig:ratio_all) holds for other oxygen-poor (e.g., C$_2$H$_5$CN) and oxygen-rich species (e.g., CH$_3$OCH$_3$). If this conclusion can be extended to low-mass protostellar systems (pending further observations), the carbon deficiency on Earth could be generalized to other terrestrial planets.

The grains that are destroyed at high temperatures most likely have similar composition to cometary refractory material which have a higher percentage of carbon and nitrogen than oxygen ((cite: Rubin2019)). Therefore, destruction of these grains in the hot gas will inevitably increase the C/O and N/O ratios in the hot gas close to the protostars compared to the warm gas further away. In other words, Figure [3](#fig:ratio_all) shows a systematic increase in the C/O and N/O ratios of the hot gas. However, the exact values of these ratios depend on the fraction of refractory organics that are destroyed in these high-temperature regions which is not known. Future chemical models to constrain these elemental ratios based on the abundances of minor carbon, nitrogen and oxygen carriers discussed in this work are needed to constrain the fraction of refractory organics that are destroyed in the hot gas. Assuming a few caveats the measured fraction from these chemical models can then be used to estimate the amount of carbon depletion in rocky planets forming in the inner regions of protostellar systems. These caveats include a similar destruction of grains in low-mass protostars, particularly in the inner parts of the disk, and a weak dependence of the inner disk gas and dust elemental abundances on dust traps.

# Acknowledgments

We thank the referee for the helpful and constructive comments. We thank A. P. Jones and P. Caselli for the helpful discussions. Astrochemistry in Leiden is supported by EU A-ERC grant 101019751 MOLDISK, NOVA, and by the NWO grant 618.000.001. Support by the Danish National Research Foundation through the Center of Excellence “InterCat” (Grant agreement no.: DNRF150) is also acknowledged. B.T. acknowledges support from the Programme National “Physique et Chimie du Milieu Interstellair” (PCMI) of CNRS/INSU with INC/INP and co-funded by CNES. M.L.R.H. acknowledges support from the Michigan Society of Fellows. J.K.J. acknowledges support from the Independent Research Fund Denmark (grant number 0135-00123B). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00195.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Spectroscopic information

The line lists and spectroscopic information for CH$_3$CN are taken from the CDMS ((cite: Kukolich1973); (cite: Boucher1977); (cite: Kukolich1982); (cite: Cazzoli2006); (cite: Muller2015)). The partition function has been calculated for temperatures below 500 K in the CDMS and contribution from lower vibrational states have been included. The higher vibrational states each contribute to less than 1% at 300 K and hence are ignored here. If these were included the difference between methyl cyanide and methanol results presented here would be larger.

The spectroscopic data for CH$_3$OH are taken from the CDMS ((cite: Lees1968); (cite: Pickett1981); (cite: Herbst1984); (cite: Xu1995); (cite: Xu2008)). The vibrational levels included in the partition function are sufficient for temperatures up to 300 K. The line data for HNCO and C$_2$H$_3$CN are also taken from the CDMS ((cite: Kukolich1971); (cite: Hocking1975); (cite: Stolze1985); (cite: Demaison1994); (cite: Colmont1997); (cite: Muller2008)). Low-lying vibrational modes are included in the calculation of partition function in the CDMS for C$_2$H$_3$CN.

# Measurement of hot column densities of C$_2$H$_3$CN

There are not enough lines with $E_{\rm up} > 400$ K detected in the spectra, for robust measurement of hot column densities of C$_2$H$_3$CN. Usually there is only one relatively unblended line with $E_{\rm up} {\sim} 400$ K in the spectra. Hence, we fix the temperature to 300 K and only fit the line with $E_{\rm up} \sim 435.0$ K to find an approximation for the hot column densities of C$_2$H$_3$CN. We do not measure the error bars as it is not possible to firmly measure them. These values are approximate and not as accurate as what we find for CH$_3$CN, CH$_3$OH and HNCO. Therefore, deeper observations are needed for robust measurement of the column densities of the hot component and those of the warm component from the $^{13}$C isotopologues of vinyl cyanide to avoid the potentially optically thick lines of C$_2$H$_3$CN with $E_{\rm up} < 400$ K.

# Additional tables and plots

Table [\[tab:results\]](#tab:results) presents the column densities and excitation temperatures of the hot component for the molecules and sources considered here. In this table a few column densities are not reported for various sources and molecules. For all our molecules if the upper limit on the excitation temperature of the hot gas is $\leq 200$ K, the hot column density is not measured to avoid potential contribution from the warm gas in the calculations.

Methanol in sources 721992 and 779984 does not have a column density because no line with $E_{\rm up}>600$ K is detected and the minor isotopologue of methanol is also an upper limit in (cite: Nazari2022ALMAGAL). For sources 707948, 865468A and G345.5043+00.3480 the high-$E_{\rm up}$ lines of HNCO are too blended and hence it is not possible to measure the hot column density. Lines of HN$^{13}$CO for source 800751 are too blended ((cite: Nazari2022ALMAGAL)) and hence the column density for HNCO is not given here. For sources 732038 and 876288 only an upper limit for the hot component is possible while the $^{13}$C isotopologue is also an upper limit, therefore, those values are not useful for our analysis. For C$_2$H$_3$CN, the sources with no measurement are those with no detection of the warm component in (cite: Nazari2022ALMAGAL).

+---------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------+----------------------------------------------------+
|                     | CH$_3$CN                                                     | CH$_3$OH                                                     | HNCO                                                        | C$_2$H$_3$CN                                       |
+:====================+:======================================+:=====================+:======================================+:=====================+:=====================================+:=====================+:============================+:=====================+
| 2-3 Source          | $N (\rm cm^{-2})$                     | $T_{\rm ex} (\rm K)$ | $N (\rm cm^{-2})$                     | $T_{\rm ex} (\rm K)$ | $N (\rm cm^{-2})$                    | $T_{\rm ex} (\rm K)$ | $N (\rm cm^{-2})$           | $T_{\rm ex} (\rm K)$ |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 101899              | 1.3$^{+0.1}_{-0.1}$ $\times 10^{16}$  | 230$^{+40}_{-40}$    | 3.0$^{+0.3}_{-0.3}$ $\times 10^{17}$  | 250$^{+20}_{-20}$    | 1.0$^{+0.1}_{-0.1}$ $\times 10^{16}$ | 320$^{+100}_{-90}$   | $<$ 2.5 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 126348              | 2.3$^{+1.1}_{-0.7}$ $\times 10^{15}$  | 350$^{+150}_{-170}$  | 7.5$^{+2.5}_{-2.0}$ $\times 10^{16}$  | 250$^{+50}_{-50}$    | 9.7$^{+2.3}_{-1.2}$ $\times 10^{14}$ | \[300\]              | $<$ 1.2 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 615590              | 1.2$^{+0.1}_{-0.1}$ $\times 10^{16}$  | 250$^{+80}_{-80}$    | 6.5$^{+5.5}_{-2.3}$ $\times 10^{17}$  | 190$^{+30}_{-30}$    | 2.2$^{+0.3}_{-0.2}$ $\times 10^{16}$ | 310$^{+50}_{-50}$    | –                           | –                    |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 644284A             | 3.7$^{+0.3}_{-0.2}$ $\times 10^{15}$  | \[300\]              | –                                     | $<$ 190              | 6.5$^{+1.5}_{-0.8}$ $\times 10^{15}$ | 300$^{+140}_{-110}$  | –                           | –                    |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 693050              | –                                     | $<$ 160              | –                                     | $<$ 150              | 7.0$^{+2.0}_{-1.5}$ $\times 10^{15}$ | 210$^{+60}_{-50}$    | $<$ 8.5 $\times 10^{14}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 705768              | 2.5$^{+1.0}_{-0.4}$ $\times 10^{15}$  | 350$^{+150}_{-190}$  | 9.0$^{+9.0}_{-3.0}$ $\times 10^{16}$  | 200$^{+50}_{-40}$    | 9.0$^{+2.0}_{-1.0}$ $\times 10^{14}$ | \[300\]              | –                           | –                    |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 707948              | –                                     | $>$ 500              | 1.4$^{+0.4}_{-0.2}$ $\times 10^{18}$  | 250$^{+20}_{-30}$    | –                                    | –                    | $\sim$ 2.0 $\times 10^{16}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 717461A             | 2.4$^{+0.2}_{-0.3}$ $\times 10^{15}$  | \[300\]              | –                                     | $<$ 200              | 1.8$^{+0.2}_{-0.2}$ $\times 10^{15}$ | \[300\]              | $<$ 9.0 $\times 10^{14}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 721992              | 5.0$^{+7.0}_{-2.7}$ $\times 10^{15}$  | 120$^{+60}_{-30}$    | –                                     | –                    | 6.0$^{+1.2}_{-1.0}$ $\times 10^{14}$ | \[300\]              | $<$ 1.3 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 724566              | 8.0$^{+3.0}_{-0.8}$ $\times 10^{15}$  | 340$^{+110}_{-150}$  | $\sim$ 1.2 $\times 10^{17}$           | \[300\]              | 3.0$^{+0.3}_{-0.2}$ $\times 10^{15}$ | \[300\]              | $<$ 2.0 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 732038              | 3.0$^{+0.2}_{-0.3}$ $\times 10^{15}$  | \[300\]              | –                                     | $<$ 190              | –                                    | –                    | –                           | –                    |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 744757A             | 4.0$^{+0.3}_{-0.2}$ $\times 10^{15}$  | 250$^{+80}_{-50}$    | 1.5$^{+1.3}_{-0.5}$ $\times 10^{17}$  | 210$^{+30}_{-40}$    | 4.8$^{+0.4}_{-0.4}$ $\times 10^{15}$ | \[300\]              | $<$ 9.0 $\times 10^{14}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 767784              | –                                     | $<$ 170              | –                                     | $<$ 180              | 1.6$^{+0.2}_{-0.1}$ $\times 10^{15}$ | \[300\]              | –                           | –                    |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 778802              | 1.0$^{+0.1}_{-0.2}$ $\times 10^{15}$  | \[300\]              | 3.0$^{+4.0}_{-1.0}$ $\times 10^{16}$  | 250$^{+90}_{-90}$    | $<$ 6.0 $\times 10^{14}$             | \[300\]              | $<$ 1.0 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 779523              | 1.2$^{+0.1}_{-0.2}$ $\times 10^{15}$  | \[300\]              | 1.0$^{+1.5}_{-0.4}$ $\times 10^{17}$  | 200$^{+50}_{-60}$    | 6.5$^{+1.0}_{-1.0}$ $\times 10^{14}$ | \[300\]              | –                           | –                    |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 779984              | 1.0$^{+0.1}_{-0.2}$ $\times 10^{15}$  | \[300\]              | –                                     | –                    | 1.0$^{+0.1}_{-0.1}$ $\times 10^{15}$ | 430$^{+70}_{-80}$    | $<$ 7.5 $\times 10^{14}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 783350              | 2.3$^{+0.2}_{-0.2}$ $\times 10^{15}$  | \[300\]              | 8.0$^{+11.0}_{-3.2}$ $\times 10^{16}$ | 200$^{+60}_{-50}$    | 1.2$^{+0.1}_{-0.2}$ $\times 10^{15}$ | \[300\]              | $<$ 8.0 $\times 10^{14}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 787212              | 1.6$^{+0.1}_{-0.1}$ $\times 10^{16}$  | 230$^{+40}_{-30}$    | 4.5$^{+3.0}_{-1.0}$ $\times 10^{17}$  | 190$^{+20}_{-30}$    | 9.9$^{+0.1}_{-0.4}$ $\times 10^{15}$ | 350$^{+60}_{-80}$    | $\sim$ 2.7 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 792355              | 1.2$^{+0.1}_{-0.1}$ $\times 10^{15}$  | \[300\]              | 3.0$^{+0.3}_{-0.3}$ $\times 10^{16}$  | \[250\]              | 7.5$^{+1.5}_{-1.5}$ $\times 10^{14}$ | \[300\]              | –                           | –                    |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 800287              | 1.3$^{+0.1}_{-0.1}$ $\times 10^{16}$  | \[300\]              | 2.1$^{+1.0}_{-0.7}$ $\times 10^{17}$  | 240$^{+50}_{-50}$    | 8.0$^{+1.0}_{-0.8}$ $\times 10^{15}$ | 340$^{+160}_{-120}$  | $\sim$ 2.9 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 800751              | 3.4$^{+0.4}_{-0.4}$ $\times 10^{15}$  | 230$^{+40}_{-40}$    | 2.0$^{+0.9}_{-0.8}$ $\times 10^{17}$  | 180$^{+30}_{-20}$    | –                                    | –                    | $<$ 7.5 $\times 10^{14}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 865468A             | 8.2$^{+1.3}_{-1.2}$ $\times 10^{16}$  | 430$^{+50}_{-50}$    | 1.7$^{+0.4}_{-0.4}$ $\times 10^{18}$  | 250$^{+30}_{-30}$    | –                                    | –                    | $\sim$ 7.0 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 876288              | 2.2$^{+0.2}_{-0.2}$ $\times 10^{15}$  | \[300\]              | 1.0$^{+1.1}_{-0.3}$ $\times 10^{17}$  | 190$^{+30}_{-40}$    | –                                    | –                    | –                           | –                    |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| 881427C             | 2.6$^{+0.3}_{-0.2}$ $\times 10^{16}$  | 300$^{+40}_{-40}$    | 5.5$^{+1.0}_{-1.0}$ $\times 10^{17}$  | 250$^{+40}_{-30}$    | 1.2$^{+0.1}_{-0.1}$ $\times 10^{16}$ | 450$^{+50}_{-50}$    | $\sim$ 6.0 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G023.3891+00.1851   | 3.5$^{+0.6}_{-0.5}$ $\times 10^{15}$  | 450$^{+50}_{-50}$    | 8.0$^{+4.0}_{-2.5}$ $\times 10^{16}$  | 250$^{+50}_{-50}$    | 1.8$^{+0.2}_{-0.1}$ $\times 10^{15}$ | 450$^{+50}_{-50}$    | $\sim$ 5.5 $\times 10^{14}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G025.6498+01.0491   | 1.0$^{+0.1}_{-0.1}$ $\times 10^{16}$  | 300$^{+50}_{-60}$    | 6.5$^{+3.5}_{-2.5}$ $\times 10^{17}$  | 190$^{+30}_{-30}$    | 1.0$^{+0.1}_{-0.1}$ $\times 10^{16}$ | 350$^{+100}_{-110}$  | $\sim$ 2.4 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G305.2017+00.2072A1 | 6.0$^{+1.8}_{-1.5}$ $\times 10^{15}$  | 190$^{+40}_{-40}$    | –                                     | $<$ 200              | 4.7$^{+1.3}_{-0.9}$ $\times 10^{15}$ | 210$^{+50}_{-50}$    | $<$ 1.2 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G314.3197+00.1125   | 5.5$^{+1.3}_{-1.2}$ $\times 10^{15}$  | 430$^{+70}_{-90}$    | –                                     | $<$ 200              | 2.3$^{+0.3}_{-0.3}$ $\times 10^{15}$ | \[300\]              | $<$ 1.7 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G316.6412-00.0867   | 1.1$^{+0.1}_{-0.1}$ $\times 10^{16}$  | 270$^{+50}_{-40}$    | 3.0$^{+1.3}_{-0.9}$ $\times 10^{17}$  | 230$^{+40}_{-30}$    | 6.0$^{+0.5}_{-0.5}$ $\times 10^{15}$ | 400$^{+100}_{-100}$  | $\sim$ 1.2 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G318.0489+00.0854B  | 3.9$^{+0.3}_{-0.4}$ $\times 10^{15}$  | \[250\]              | –                                     | $<$ 170              | –                                    | $<$ 200              | $<$ 1.1 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G318.9480-00.1969A1 | 1.8$^{+0.2}_{-0.1}$ $\times 10^{16}$  | 240$^{+40}_{-40}$    | 8.0$^{+4.0}_{-2.5}$ $\times 10^{17}$  | 210$^{+30}_{-30}$    | 1.7$^{+0.1}_{-0.2}$ $\times 10^{16}$ | 320$^{+80}_{-70}$    | $\sim$ 1.2 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G323.7399-00.2617B2 | 1.2$^{+0.3}_{-0.2}$ $\times 10^{16}$  | 180$^{+40}_{-30}$    | –                                     | $<$ 190              | 1.0$^{+0.1}_{-0.2}$ $\times 10^{16}$ | 230$^{+30}_{-40}$    | $\sim$ 9.5 $\times 10^{14}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G326.4755+00.6947   | 1.1$^{+0.1}_{-0.1}$ $\times 10^{15}$  | \[300\]              | $\sim$ 6.0 $\times 10^{16}$           | \[220\]              | 1.2$^{+0.2}_{-0.2}$ $\times 10^{15}$ | \[300\]              | $<$ 8.0 $\times 10^{14}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G326.6618+00.5207   | 2.8$^{+28.2}_{-0.4}$ $\times 10^{15}$ | 230$^{+60}_{-50}$    | 1.0$^{+0.6}_{-0.3}$ $\times 10^{17}$  | 200$^{+30}_{-30}$    | 3.1$^{+0.3}_{-0.3}$ $\times 10^{15}$ | \[300\]              | $<$ 6.5 $\times 10^{14}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G327.1192+00.5103   | 1.5$^{+0.2}_{-0.1}$ $\times 10^{16}$  | \[220\]              | –                                     | $<$ 200              | 2.1$^{+0.1}_{-0.1}$ $\times 10^{16}$ | 350$^{+100}_{-110}$  | $<$ 2.9 $\times 10^{15}$    | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G343.1261-00.0623   | 2.2$^{+0.3}_{-0.2}$ $\times 10^{16}$  | 310$^{+50}_{-40}$    | 1.8$^{+0.7}_{-0.7}$ $\times 10^{17}$  | 220$^{+30}_{-30}$    | 2.6$^{+0.2}_{-0.2}$ $\times 10^{16}$ | 330$^{+90}_{-90}$    | $\sim$ 5.0 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+
| G345.5043+00.3480   | 4.2$^{+0.8}_{-0.7}$ $\times 10^{16}$  | 400$^{+60}_{-70}$    | $\sim$ 7.5 $\times 10^{17}$           | \[250\]              | –                                    | –                    | $\sim$ 7.0 $\times 10^{15}$ | \[300\]              |
+---------------------+---------------------------------------+----------------------+---------------------------------------+----------------------+--------------------------------------+----------------------+-----------------------------+----------------------+

Figure [4](#fig:fitting) presents an example source with the CASSIS fits (in red) on top of the data (in black) for measurement of the warm (top panels) and hot (bottom panels) column densities of methyl cyanide. Figure [5](#fig:T) presents the excitation temperatures of warm and hot methanol and methyl cyanide when the measurement was possible. Given the errors bars, the temperatures of hot methanol and methyl cyanide are similar, the same is true for the warm methanol and methyl cyanide.

natexlab

(ref: Adams1985) Adams, F. C., & Shu, F. H. 1985, ApJ, 296, 655, doi: [`10.1086/163483`](http://doi.org/10.1086/163483)

(ref: Alata2014) Alata, I., Cruz-Diaz, G. A., Muñoz Caro, G. M., & Dartois, E. 2014, A&A, 569, A119, doi: [`10.1051/0004-6361/201323118`](http://doi.org/10.1051/0004-6361/201323118)

(ref: Allegre2001) Allègre, C., Manhès, G., & Lewin, É. 2001, E&PSL, 185, 49, doi: [`10.1016/S0012-821X(00)00359-9`](http://doi.org/10.1016/S0012-821X(00)00359-9)

(ref: Anderson2017) Anderson, D. E., Bergin, E. A., Blake, G. A., et al. 2017, ApJ, 845, 13, doi: [`10.3847/1538-4357/aa7da1`](http://doi.org/10.3847/1538-4357/aa7da1)

(ref: Bardyn2017) Bardyn, A., Baklouti, D., Cottin, H., et al. 2017, MNRAS, 469, S712, doi: [`10.1093/mnras/stx2640`](http://doi.org/10.1093/mnras/stx2640)

(ref: Bergin2015) Bergin, E. A., Blake, G. A., Ciesla, F., Hirschmann, M. M., & Li, J. 2015, PNAS, 112, 8965, doi: [`10.1073/pnas.1500954112`](http://doi.org/10.1073/pnas.1500954112)

(ref: Bertin2017) Bertin, M., Doronin, M., Fillion, J. H., et al. 2017, A&A, 598, A18, doi: [`10.1051/0004-6361/201629394`](http://doi.org/10.1051/0004-6361/201629394)

(ref: Boucher1977) Boucher, D., Burie, J., Demaison, J., et al. 1977, JMoSp, 64, 290, doi: [`10.1016/0022-2852(77)90267-3`](http://doi.org/10.1016/0022-2852(77)90267-3)

(ref: Busch2022) Busch, L. A., Belloche, A., Garrod, R. T., Müller, H. S. P., & Menten, K. M. 2022, A&A, 665, A96, doi: [`10.1051/0004-6361/202243383`](http://doi.org/10.1051/0004-6361/202243383)

(ref: Cazzoli2006) Cazzoli, G., & Puzzarini, C. 2006, JMoSp, 240, 153, doi: [`10.1016/j.jms.2006.09.013`](http://doi.org/10.1016/j.jms.2006.09.013)

(ref: Ceccarelli2022) Ceccarelli, C., Codella, C., Balucani, N., et al. 2022, arXiv e-prints, arXiv:2206.13270, doi: [`10.48550/arXiv.2206.13270`](http://doi.org/10.48550/arXiv.2206.13270)

(ref: Chen2023) Chen, Y., van Gelder, M. L., Nazari, P., et al. 2023, Submitted to A&A

(ref: Collings2004) Collings, M. P., Anderson, M. A., Chen, R., et al. 2004, MNRAS, 354, 1133, doi: [`10.1111/j.1365-2966.2004.08272.x`](http://doi.org/10.1111/j.1365-2966.2004.08272.x)

(ref: Colmont1997) Colmont, J. M., Wlodarczak, G., Priem, D., et al. 1997, JMoSp, 181, 330, doi: [`10.1006/jmsp.1996.7174`](http://doi.org/10.1006/jmsp.1996.7174)

(ref: Das2018) Das, A., Sil, M., Gorai, P., Chakrabarti, S. K., & Loison, J. C. 2018, ApJS, 237, 9, doi: [`10.3847/1538-4365/aac886`](http://doi.org/10.3847/1538-4365/aac886)

(ref: Demaison1994) Demaison, J., Cosleou, J., Bocquet, R., & Lesarri, A. G. 1994, JMoSp, 167, 400, doi: [`10.1006/jmsp.1994.1245`](http://doi.org/10.1006/jmsp.1994.1245)

(ref: Farihi2016) Farihi, J. 2016, New A Rev., 71, 9, doi: [`10.1016/j.newar.2016.03.001`](http://doi.org/10.1016/j.newar.2016.03.001)

(ref: Farihi2013) Farihi, J., Gänsicke, B. T., & Koester, D. 2013, Sci, 342, 218, doi: [`10.1126/science.1239447`](http://doi.org/10.1126/science.1239447)

(ref: Ferrero2020) Ferrero, S., Zamirri, L., Ceccarelli, C., et al. 2020, ApJ, 904, 11, doi: [`10.3847/1538-4357/abb953`](http://doi.org/10.3847/1538-4357/abb953)

(ref: Finocchi1997) Finocchi, F., Gail, H. P., & Duschl, W. J. 1997, A&A, 325, 1264

(ref: Fischer2020) Fischer, R. A., Cottrell, E., Hauri, E., Lee, K. K. M., & Le Voyer, M. 2020, PNAS, 117, 8743, doi: [`10.1073/pnas.1919930117`](http://doi.org/10.1073/pnas.1919930117)

(ref: Fomenkova1997) Fomenkova, M. N. 1997, in ASPC, Vol. 122, From Stardust to Planetesimals, ed. Y. J. Pendleton, 415

(ref: Fomenkova1999) Fomenkova, M. N. 1999, Space Sci. Rev., 90, 109, doi: [`10.1023/A:1005237828783`](http://doi.org/10.1023/A:1005237828783)

(ref: Fomenkova1994) Fomenkova, M. N., Chang, S., & Mukhin, L. M. 1994, GeCoA, 58, 4503, doi: [`10.1016/0016-7037(94)90351-4`](http://doi.org/10.1016/0016-7037(94)90351-4)

(ref: Fray2016) Fray, N., Bardyn, A., Cottin, H., et al. 2016, Natur, 538, 72, doi: [`10.1038/nature19320`](http://doi.org/10.1038/nature19320)

(ref: Gail2017) Gail, H.-P., & Trieloff, M. 2017, A&A, 606, A16, doi: [`10.1051/0004-6361/201730480`](http://doi.org/10.1051/0004-6361/201730480)

(ref: Gansicke2012) Gänsicke, B. T., Koester, D., Farihi, J., et al. 2012, MNRAS, 424, 333, doi: [`10.1111/j.1365-2966.2012.21201.x`](http://doi.org/10.1111/j.1365-2966.2012.21201.x)

(ref: Garrod2022) Garrod, R. T., Jin, M., Matis, K. A., et al. 2022, ApJS, 259, 1, doi: [`10.3847/1538-4365/ac3131`](http://doi.org/10.3847/1538-4365/ac3131)

(ref: Geiss1987) Geiss, J. 1987, A&A, 187, 859

(ref: Gibb2004) Gibb, E. L., Whittet, D. C. B., Boogert, A. C. A., & Tielens, A. G. G. M. 2004, ApJS, 151, 35, doi: [`10.1086/381182`](http://doi.org/10.1086/381182)

(ref: Herbst1984) Herbst, E., Messer, J. K., De Lucia, F. C., & Helminger, P. 1984, JMoSp, 108, 42, doi: [`10.1016/0022-2852(84)90285-6`](http://doi.org/10.1016/0022-2852(84)90285-6)

(ref: Herbst2009) Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427, doi: [`10.1146/annurev-astro-082708-101654`](http://doi.org/10.1146/annurev-astro-082708-101654)

(ref: Hocking1975) Hocking, W. H., Gerry, M. C. L., & Winnewisser, G. 1975, CaJPh, 53, 1869, doi: [`10.1139/p75-239`](http://doi.org/10.1139/p75-239)

(ref: Jones2016) Jones, A. P. 2016, RSOS, 3, 160224, doi: [`10.1098/rsos.160224`](http://doi.org/10.1098/rsos.160224)

(ref: Jorgensen2020) Jørgensen, J. K., Belloche, A., & Garrod, R. T. 2020, ARA&A, 58, 727, doi: [`10.1146/annurev-astro-032620-021927`](http://doi.org/10.1146/annurev-astro-032620-021927)

(ref: Jura2006) Jura, M. 2006, ApJ, 653, 613, doi: [`10.1086/508738`](http://doi.org/10.1086/508738)

(ref: Jura2007) Jura, M., Farihi, J., & Zuckerman, B. 2007, ApJ, 663, 1285, doi: [`10.1086/518767`](http://doi.org/10.1086/518767)

(ref: Jura2012) Jura, M., Xu, S., Klein, B., Koester, D., & Zuckerman, B. 2012, ApJ, 750, 69, doi: [`10.1088/0004-637X/750/1/69`](http://doi.org/10.1088/0004-637X/750/1/69)

(ref: Kissel1986Giotto) Kissel, J., Brownlee, D. E., Buchler, K., et al. 1986a, Natur, 321, 336, doi: [`10.1038/321336a0`](http://doi.org/10.1038/321336a0)

(ref: Kissel1986) Kissel, J., Sagdeev, R. Z., Bertaux, J. L., et al. 1986b, Natur, 321, 280, doi: [`10.1038/321280a0`](http://doi.org/10.1038/321280a0)

(ref: Klarmann2018) Klarmann, L., Ormel, C. W., & Dominik, C. 2018, A&A, 618, L1, doi: [`10.1051/0004-6361/201833719`](http://doi.org/10.1051/0004-6361/201833719)

(ref: Kukolich1982) Kukolich, S. G. 1982, , 76, 97, doi: [`10.1063/1.442694`](http://doi.org/10.1063/1.442694)

(ref: Kukolich1971) Kukolich, S. G., Nelson, A. C., & Yamanashi, B. S. 1971, JAChS, 93, 6769, doi: [`10.1021/ja00754a010`](http://doi.org/10.1021/ja00754a010)

(ref: Kukolich1973) Kukolich, S. G., Ruben, D. J., Wang, J. H. S., & Williams, J. R. 1973, , 58, 3155, doi: [`10.1063/1.1679636`](http://doi.org/10.1063/1.1679636)

(ref: Lahuis2000) Lahuis, F., & van Dishoeck, E. F. 2000, A&A, 355, 699

(ref: Lee2010) Lee, J.-E., Bergin, E. A., & Nomura, H. 2010, ApJL, 710, L21, doi: [`10.1088/2041-8205/710/1/L21`](http://doi.org/10.1088/2041-8205/710/1/L21)

(ref: Lees1968) Lees, R. M., & Baker, J. G. 1968, , 48, 5299, doi: [`10.1063/1.1668221`](http://doi.org/10.1063/1.1668221)

(ref: Li2021) Li, J., Bergin, E. A., Blake, G. A., Ciesla, F. J., & Hirschmann, M. M. 2021, SciA, 7, eabd3632, doi: [`10.1126/sciadv.abd3632`](http://doi.org/10.1126/sciadv.abd3632)

(ref: Manara2018) Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3, doi: [`10.1051/0004-6361/201834076`](http://doi.org/10.1051/0004-6361/201834076)

(ref: Marty2012) Marty, B. 2012, E&PSL, 313, 56, doi: [`10.1016/j.epsl.2011.10.040`](http://doi.org/10.1016/j.epsl.2011.10.040)

(ref: Milam2005) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126, doi: [`10.1086/497123`](http://doi.org/10.1086/497123)

(ref: Minissale2022) Minissale, M., Aikawa, Y., Bergin, E., et al. 2022, ESC, 6, 597, doi: [`10.1021/acsearthspacechem.1c00357`](http://doi.org/10.1021/acsearthspacechem.1c00357)

(ref: Muller2008) Müller, H. S. P., Belloche, A., Menten, K. M., Comito, C., & Schilke, P. 2008, JMoSp, 251, 319, doi: [`10.1016/j.jms.2008.03.016`](http://doi.org/10.1016/j.jms.2008.03.016)

(ref: Muller2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, JMoSt, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](http://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: Muller2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: Muller2015) Müller, H. S. P., Brown, L. R., Drouin, B. J., et al. 2015, JMoSp, 312, 22, doi: [`10.1016/j.jms.2015.02.009`](http://doi.org/10.1016/j.jms.2015.02.009)

(ref: Nakano2003) Nakano, H., Kouchi, A., Tachibana, S., & Tsuchiyama, A. 2003, ApJ, 592, 1252, doi: [`10.1086/375856`](http://doi.org/10.1086/375856)

(ref: Nazari2023Highmass) Nazari, P., Tabone, B., & Rosotti, G. P. 2023a, A&A, 671, A107, doi: [`10.1051/0004-6361/202244801`](http://doi.org/10.1051/0004-6361/202244801)

(ref: Nazari2023) Nazari, P., Tabone, B., Rosotti, G. P., & van Dishoeck, E. F. 2023b, Submitted to A&A

(ref: Nazari2022Lowmass) Nazari, P., Tabone, B., Rosotti, G. P., et al. 2022a, A&A, 663, A58, doi: [`10.1051/0004-6361/202142777`](http://doi.org/10.1051/0004-6361/202142777)

(ref: Nazari2021) Nazari, P., van Gelder, M. L., van Dishoeck, E. F., et al. 2021, A&A, 650, A150, doi: [`10.1051/0004-6361/202039996`](http://doi.org/10.1051/0004-6361/202039996)

(ref: Nazari2022ALMAGAL) Nazari, P., Meijerhof, J. D., van Gelder, M. L., et al. 2022b, A&A, 668, A109, doi: [`10.1051/0004-6361/202243788`](http://doi.org/10.1051/0004-6361/202243788)

(ref: Neill2014) Neill, J. L., Bergin, E. A., Lis, D. C., et al. 2014, ApJ, 789, 8, doi: [`10.1088/0004-637X/789/1/8`](http://doi.org/10.1088/0004-637X/789/1/8)

(ref: Oberg2021) Öberg, K. I., & Bergin, E. A. 2021, Phys. Rep., 893, 1, doi: [`10.1016/j.physrep.2020.09.004`](http://doi.org/10.1016/j.physrep.2020.09.004)

(ref: Penteado2017) Penteado, E. M., Walsh, C., & Cuppen, H. M. 2017, ApJ, 844, 71, doi: [`10.3847/1538-4357/aa78f9`](http://doi.org/10.3847/1538-4357/aa78f9)

(ref: Pickett1981) Pickett, H. M., Cohen, E. A., Brinza, D. E., & Schaefer, M. M. 1981, JMoSp, 89, 542, doi: [`10.1016/0022-2852(81)90046-1`](http://doi.org/10.1016/0022-2852(81)90046-1)

(ref: Duval2022) Roman-Duval, J., Jenkins, E. B., Tchernyshyov, K., et al. 2022, ApJ, 928, 90, doi: [`10.3847/1538-4357/ac5248`](http://doi.org/10.3847/1538-4357/ac5248)

(ref: Rubin2019) Rubin, M., Altwegg, K., Balsiger, H., et al. 2019, MNRAS, 489, 594, doi: [`10.1093/mnras/stz2086`](http://doi.org/10.1093/mnras/stz2086)

(ref: Song2016) Song, L., & Kästner, J. 2016, PCCP, 18, 29278, doi: [`10.1039/C6CP05727F`](http://doi.org/10.1039/C6CP05727F)

(ref: Stolze1985) Stolze, M., & Sutter, D. H. 1985, ZNatA, 40, 998, doi: [`10.1515/zna-1985-1007`](http://doi.org/10.1515/zna-1985-1007)

(ref: Tychoniec2020) Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19, doi: [`10.1051/0004-6361/202037851`](http://doi.org/10.1051/0004-6361/202037851)

(ref: vanderTak2000) van der Tak, F. F. S., van Dishoeck, E. F., Evans, Neal J., I., & Blake, G. A. 2000, ApJ, 537, 283, doi: [`10.1086/309011`](http://doi.org/10.1086/309011)

(ref: vanGelder2022) van Gelder, M. L., Nazari, P., Tabone, B., et al. 2022a, A&A, 662, A67, doi: [`10.1051/0004-6361/202142769`](http://doi.org/10.1051/0004-6361/202142769)

(ref: vanGelder2022Deuteration) van Gelder, M. L., Jaspers, J., Nazari, P., et al. 2022b, A&A, 667, A136, doi: [`10.1051/0004-6361/202244471`](http://doi.org/10.1051/0004-6361/202244471)

(ref: vantHoff2020) van ’t Hoff, M. L. R., Bergin, E. A., Jørgensen, J. K., & Blake, G. A. 2020, ApJL, 897, L38, doi: [`10.3847/2041-8213/ab9f97`](http://doi.org/10.3847/2041-8213/ab9f97)

(ref: Vastel2015) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. M., & Boiziot, M. 2015, in 2015sf2a conf, 313–316

(ref: Wakelam2017) Wakelam, V., Loison, J. C., Mereau, R., & Ruaud, M. 2017, MolAs, 6, 22, doi: [`10.1016/j.molap.2017.01.002`](http://doi.org/10.1016/j.molap.2017.01.002)

(ref: wang2013effect) Wang, S., Liu, J., Jiang, X., Han, X., & Tong, J. 2013, Oil shale, 30, 27

(ref: Wei2019) Wei, C.-E., Nomura, H., Lee, J.-E., et al. 2019, ApJ, 870, 129, doi: [`10.3847/1538-4357/aaf390`](http://doi.org/10.3847/1538-4357/aaf390)

(ref: Wilson1994) Wilson, T. L., & Rood, R. 1994, ARA&A, 32, 191, doi: [`10.1146/annurev.aa.32.090194.001203`](http://doi.org/10.1146/annurev.aa.32.090194.001203)

(ref: Wooden2008) Wooden, D. H. 2008, Space Sci. Rev., 138, 75, doi: [`10.1007/s11214-008-9424-2`](http://doi.org/10.1007/s11214-008-9424-2)

(ref: Xu1995) Xu, L. H., & Hougen, J. T. 1995, JMoSp, 173, 540, doi: [`10.1006/jmsp.1995.1255`](http://doi.org/10.1006/jmsp.1995.1255)

(ref: Xu2008) Xu, L.-H., Fisher, J., Lees, R. M., et al. 2008, JMoSp, 251, 305, doi: [`10.1016/j.jms.2008.03.017`](http://doi.org/10.1016/j.jms.2008.03.017)

[^1]: <http://cassis.irap.omp.eu/>

</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Hot-to-warm abundance enhancement (X_hot / X_warm) for oxygen-poor molecules = >=5 dimensionless",
  "failed_quote": "This means an enhancement of oxygen-poor species in the hot gas and $X_{i,\\rm hot}/X_{i,\\rm warm}$ of ${\\gtrsim}5$ for these molecules (see Equation [eq:ratio])."
 }
]
```
