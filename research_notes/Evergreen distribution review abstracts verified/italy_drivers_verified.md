# Italian context (land abandonment, drought/climate, Q. ilex dieback, management): verification of earlier notes and gap closing (Round 2)

Access log (stated plainly):
- Abstracts were read via OpenAlex (abstract_inverted_index), Crossref, Semantic Scholar, Europe PMC, and the Forest@ page. Tags: [ABSTRACT-READ] = abstract text seen by me via API; [FULLTEXT-PARTLY-READ] = parts of full text seen (here only the locally stored INFC book PDF, and the Forest@ HTML via a fetch-summariser); [METADATA-ONLY] = bibliographic record only; [SEARCH-SUMMARY] = only a web-search tool's paraphrase of the abstract (not verbatim, treat as weaker than [ABSTRACT-READ]).
- Springer (link.springer.com), IRIS repositories (iris.unito.it, iris.univpm.it, iris.uniroma1.it) and OUP returned bot-challenge pages or HTTP 403 to curl and WebFetch. Springer abstracts are also "elided" in Semantic Scholar/OpenAlex/Crossref. So Garbarino 2020, Malandra 2019, Falcucci 2007, Malavasi 2018, Walther 2002 abstracts could NOT be read directly. For those I only have the web-search tool's paraphrase of the repository abstract.
- Google Scholar: scholar.google.com answered with HTTP 200 to a plain curl and returned real result lists for 3 queries ("deperimento leccio", "Quercus ilex dieback Italy 2017 drought", "Quercus ilex dieback Sardinia 2024"). After that it throttled (HTTP 429 / "system can't perform the operation now") for all later queries, including Italian-language queries on cedui/espansione leccio. So Scholar was usable only for the dieback block. Later gap searches used OpenAlex (also intermittently 429), Crossref, and the WebSearch tool (these cover Italian titles poorly).
- Bibliographic data (authors, volume, pages) were checked against Crossref for the key items; DOIs below resolved in at least one API.

---

## A. Verification of every paper in the earlier Italy note and the report (sections 1-3)

### Takeaway
Most earlier statements hold. Corrections that matter: (1) Colangelo 2018 is about Q. cerris vs Q. pubescens and Phytophthora QUERCINA, which was MORE frequent in non-declining trees, so it does not support "Phytophthora drives decline"; (2) the Garbarino ~0.6 %/yr is a forest-expansion rate for all forest (no leaf-habit), and what it is relative to is not clear from the abstract; (3) Gentilesca 2017 is mostly about ring-porous deciduous oaks; (4) Mombrini 2025 abstract does NOT say SPEI trends are steeper than SPI, and finds no region-wide trend; (5) the earlier report line "gasparini_2022_nfi_italy: 10.98 Mha forest, about +520,000 ha vs INFC2005" does not match the chapter I read: Forest (Bosco) 8,759,202 ha (INFC2005) to 9,085,186 ha (INFC2015), +325,984 ha (+3.7 %); Total wooded area 10,467,533 to 11,054,458 ha, +586,925 ha (+5.6 %).

### Cited Findings (per paper)

**1. Pollastrini et al. 2019, Front. For. Glob. Change 2:74, doi 10.3389/ffgc.2019.00074** [ABSTRACT-READ; Crossref authors: Pollastrini, Puletti, Selvi, Iacopetti, Bussotti]
- Quote: "Deciduous tree species (Fagus sylvatica, Quercus pubescens, Quercus cerris) shed their leaves during the summer, but apical buds and twigs were preserved." "Mediterranean evergreen broadleaves, such as Quercus ilex and Phillyrea latifolia suffered of total or partial crown desiccation with wilting leaves and branch dieback. These species partially resprouted in 2018 from axillary and latent buds."
- Numbers in abstract: none beyond the event description (SPI and ESA soil moisture; event from Nov 2016; summer 2017; lowland Mediterranean-climate areas most affected). Mortality described ("whole tree mortality") but not quantified in the abstract.
- Assessment: worth reading; best direct Italian evidence for evergreen vs deciduous contrast. Case report on representative stands, not wall-to-wall. Cite in INTRO and DISC (transient crown loss vs mortality; resprouting). — [OpenAlex/Crossref](https://doi.org/10.3389/ffgc.2019.00074)

**2. Alderotti et al. 2023, Sci. Total Environ. 904:166809, doi 10.1016/j.scitotenv.2023.166809** [ABSTRACT-READ; authors per Crossref: Alderotti, Sillo, Brilli, Bussotti, Centritto, Ferrini, Gori, Inghes, Pasquini, Pollastrini, Saurer, Cherubini, Balestrini, Brunetti]
- Quote: "...different degree of crown damages even in close sites, as observed in two Q. ilex forest stands in southern Tuscany..." "Q. ilex at ND resulted more resilient to drought compared to trees at D, probably thanks to its safer water strategy. Genotyping analysis based on simple-sequence repeat (SSR) markers revealed the presence of different Q. ilex populations at D and ND stands."
- Numbers: two stands (declining D, non-declining ND), 2012 and 2017 droughts analysed; no tree counts stated in abstract.
- Assessment: the title "genetically determined" overreaches the design (two stands, correlation between stand and genotype, site differences not excluded; this is my reading of the abstract, which itself says "may be genetically driven"). Cite only for patchiness and intraspecific variation. Worth reading: moderate.

**3. Alderotti et al. 2025, Tree Physiol. 45(5):tpaf033, doi 10.1093/treephys/tpaf033** [ABSTRACT-READ]
- Quote: "In summer and autumn, CL2 and CL3 trees experienced 40-50% PLC, coinciding with reduced carbon uptake." "...moderate crown defoliation may conceal severe physiological damage."
- Numbers: PLC (percent loss of hydraulic conductivity) 40-50 % in moderately/severely defoliated trees, monitored over two years; defoliation classes CL1-CL3. Tree number and site not in abstract [still unverified].
- Assessment: useful in DISC only (why partial crown loss in remote sensing is not harmless). Not a distribution paper.

**4. Seddaiu et al. 2025, Forest@ 22:56-65, doi 10.3832/efor4934-022** [ABSTRACT-READ + FULLTEXT-PARTLY-READ (first 100,000 chars of the Italian HTML via fetch-summariser)]
- Quote (abstract): "In Italy, the first reports of Q. ilex dieback due to climatic events date back to 2012 in Tuscany, and with more extensive impacts observed following the extreme drought of 2017. During the summer of 2024, widespread dieback phenomena were reported across Southern Italian regions, including Apulia, Basilicata, and the islands of Sardinia and Sicily." Also: "The phenomenon of dieback and mortality of Q. ilex is still poorly understood in terms of the cause-and-effect relationships ... extension and severity of damage, and the ecological consequences."
- Numbers from body text (summariser extract, quote from Italian original, verify before citing): Sardinia mortality "intorno al 25%" in areas already affected; Sardinia 2024 about 110,000 ha affected (satellite vegetation indices); Basilicata 2017 about 50,000 ha of 350,000 ha forest with high stress; Tuscany coastal dieback front about 130 km (Cecina to Maremma); Sicily Mandredonne 60 % incidence, Pantalica about 40 % of stand, other Sicilian sites not above 10 %; Monte Minardo over 100 ha; CONECOFOR: about 250 trees in 11 permanent plots 2001-2024, defoliation fell 2001-2016 then rose, peak 2025 (Mann-Kendall p<0.05), mortality "sporadic and very limited"; SilvaCuore: 33 reports from five regions; 2017: no rain "over 3 months", temperature about 8 degrees above period average (central-southern Italy; wording from the paper, not independently checked).
- Q. suber: Sardinia 2024 cork oaks in lower Gallura and Ogliastra "completamente defogliate", most recovered in autumn; Sicily Buccheri up to 60 %; Tuscany high Maremma cork oak heavily affected with Phytophthora and Platypus cylindrus.
- Assessment: the anchor citation for the Italian dieback overview. It is an overview/perspective with compiled and partly anecdotal numbers (SilvaCuore is citizen science). The last 21,800 characters were not read. 2024 area figure (110,000 ha) coincides with the Satta et al. preprint figure, so these may not be independent [unverified].

**5. Gentilesca et al. 2017, iForest 10:796-806, doi 10.3832/ifor2317-010** [ABSTRACT-READ]
- Quote: "Our review reveals that drought is reported as the main driver triggering oak decline within the Mediterranean Basin, although other causes (i.e., increasing temperature, pathogens attack or excessive stand density) could exacerbate decline." "...it could be useful to shorten the rotation period of coppice stands or promoting their gradual conversion towards high forests, and favoring more drought-resistant species should also be considered."
- Abstract's wood-anatomy emphasis is on "ring-porous oak species"; the Scholar snippet says it reports one Q. ilex stand affected by 2012 drought, so Q. ilex is a minor part. Assessment: cite for drought as main driver and for coppice-conversion as a resilience measure (links to gap B4). Not Q. ilex specific.

**6. Colangelo et al. 2018, Front. Plant Sci. 9:1595, doi 10.3389/fpls.2018.01595** [ABSTRACT-READ; Crossref authors: Colangelo, Camarero, Borghetti, Gentilesca, Oliva, Redondo, Ripullone (7, earlier note's list was incomplete)]
- Quote: "The oak species most affected by drought-induced decline in terms of leaf shedding and mortality was Q. cerris ... In the studied area, Phytophthora quercina was isolated from 40% of the sampled trees, and tended to be more frequent amongst ND than amongst D trees."
- Numbers: 15 couples of declining/non-declining trees per species; growth reduction from 2000 onwards; P. quercina 40 % of sampled trees. Correction: the pathogen is P. quercina, more frequent in non-declining trees, so the paper explicitly does not show a pathogen role ("warrants further study as a potential predisposing factor"). The title "Drought and Phytophthora are associated" overstates relative to the data.
- Assessment: deciduous oaks, southern Italy; do not cite for holm oak. A different Colangelo paper (Tree Physiology 37:617, 2017, doi 10.1093/treephys/tpx002) turned up in Scholar for "Quercus ilex dieback"; its page covers Q. frainetto only, so it is NOT about holm oak [reject].

**7. Frisullo et al. 2018, Forest Sci. 64(3):290-298, doi 10.1093/forsci/fxx010** [ABSTRACT-READ; Crossref: 10 authors Frisullo, Lima, Magnano di San Lio, Camele, Melissano, Puglisi, Pane, Agosteo, Prudente, Cacciola]
- Quote: "...the oomycete Phytophthora cinnamomi was found to be consistently associated with tree decline and mortality in 7 municipalities of the province of Lecce." "...it was assumed to be the primary causal agent of holm oak decline in this area."
- Assessment: the "primary causal agent" is an assumption from consistent association plus seedling aggressiveness (abstract says "assumed"); no drought analysis. Cite for non-climatic confounding in Apulia. Newer, complementary: Bregant et al. 2025 (item B2).

**8. Bussotti et al. 2021, Forests 12(11):1476, doi 10.3390/f12111476** [ABSTRACT-READ; Crossref lists vol 12, authors Bussotti, Papitto, Di Martino, Cocciufa, Cindolo, Cenni, Bettini, Iacopetti, Pollastrini; the earlier note's "et al." was fine]
- Quote: "...a 24-year assessment carried out in Italy on 253 permanent plots ... substantial stability of crown conditions at the national level ... an increased fraction of extremely defoliated and dead trees was observed." "...Quercus species showed a progressive decrease in defoliation."
- Caveat: "Quercus species" are not split into evergreen/deciduous in the abstract, and Mediterranean evergreen woodland is thinly represented in ICP Level I (Seddaiu 2025 states 11 of 261 national permanent plots are Mediterranean). Cite as a national baseline with that caveat, not as evidence about holm oak.

**9. Garbarino et al. 2020, Landscape Ecol. 35(12):2679-2694, doi 10.1007/s10980-020-01013-9** [SEARCH-SUMMARY only; Springer, IRIS unito and IRIS univpm all blocked; abstract not read verbatim]
- Search-tool paraphrase of repository abstract: Corine Land Cover regional changes over 28 years (Alps and Apennines), landscape-scale changes over 58 years at 8 Alpine and 8 Apennine sites from aerial images; "forest expansion was the dominant landscape transition in both ranges, at an overall annual rate of 0.6%"; Apennine expansion strongest at lower elevations; distance to forest edge best predictor in the Alps, elevation in the Apennines.
- Resolution of your question: the 0.6 % is a forest-expansion rate for ALL forest (no leaf-habit information), pooled across both ranges. What it is relative to (percent of landscape area per year? relative to existing forest area? CLC regional or the 16 aerial-image sites?) is NOT determinable from what I could access. [still unverified]. Do not use "0.6 %/yr" as a background rate for evergreen oak, and do not call it national. A different paper (Anselmetto/Weisberg/Garbarino meta-analysis for the Alps) reports +0.64 %/yr, and Bebi et al. 2017 +0.37 %/yr for the Alps (both from a search summary; unverified, mention only as context that ~0.4-0.6 %/yr is a typical order of magnitude).
- Assessment: worth reading in full (needs the open post-print: iris.unito.it/handle/2318/1765594, fetch it manually in a browser).

**10. Falcucci et al. 2007, Landscape Ecol. 22(4):617-631, doi 10.1007/s10980-006-9056-4** [SEARCH-SUMMARY only; Semantic Scholar says abstract elided by publisher]
- Paraphrase: three LULC maps 1960-2000; forest increase mostly in mountain areas; artificial areas up near coasts; pastures down; "intensively farmed land declined only slightly, while extensively farmed land fell sharply"; forest birds, ungulates, carnivores increased; typical Mediterranean species declined. 726 citations (OpenAlex).
- Assessment: classic citation for national forest increase; contains no leaf-habit information. Old (data end 2000). INTRO only.

**11. Gasparini & Tabacchi 2022, chapter 13 of the Italian NFI book, doi 10.1007/978-3-030-98678-0_13** [ABSTRACT-READ + FULLTEXT-PARTLY-READ from /home/c7161037/Desktop/repos/notes/00_literature/gasparini_2022_nfi_italy.pdf, pp. 545-563 and Table 7.7]
- Verified numbers (pp. 547-549, 562-563): Forest (Bosco) 8,759,202 ha (SE 0.4 %) INFC2005 vs 9,085,186 ha (SE 0.4 %) INFC2015, +325,984 ha (+3.7 %). Other wooded land 1,708,333 to 1,969,272 ha (+260,939, +15.3 %). Total wooded area 10,467,533 to 11,054,458 ha (+586,925, +5.6 %). Regional: southern Apennines and islands Forest +7.2 %, northern/central Apennines +3.1 %, Alpine +2.0 %. Only Molise (+15.6 %) shows a "considerable" regional change. Gross change: new forest 749,596 ha vs new other-land uses 163,870 ha, balance 585,726 ha.
- Forest-type results relevant to the paper: area changes considerable (non-overlapping 2xSE intervals) only for "Other deciduous broadleaved" (+11.4 %) and "Other evergreen broadleaved" (+33.6 %); the authors state these are residual classes into which newly formed stands (e.g. maple-linden groves, Robinia and Ailanthus stands) fall. Holm oak area change is not flagged as considerable (exact INFC2005 holm oak area is only in Fig. 13.2, not in text; not extracted). Holm oak growing stock +15,601,302 m3 (+34.2 %) is flagged as considerable; holm oak aboveground biomass +15,321,040 Mg (+35.0 %).
- Holm oak area INFC2015 (Table 7.7, assumed INFC2015 by chapter context [verify]): 643,052 ha (SE 2.4 %), of which Sardegna 255,463 ha (about 40 %), Toscana 129,686, Calabria 48,692, Lazio 48,267, Umbria 41,289, Campania 37,485 ha. Cork oak and other evergreen broadleaved are small (Toscana 6,143 ha cork oak).
- Caveat stated by authors: samples of the two inventories are not independent; no hypothesis tests; category-level estimates have high SEs.
- Correction to earlier report: "10.98 Mha forest, +520,000 ha" is NOT in this chapter; use the numbers above. (The 10.98 Mha figure appears to be provisional INFC2015 total wooded area from a secondary source.)
- Assessment: strongest quantitative anchor for validation; says that "evergreen" area is not clearly increasing at national level in the inventory, which is a useful sanity check for the planned maps.

**12. Gazol & Camarero 2022, Sci. Total Environ. 816:151604, doi 10.1016/j.scitotenv.2021.151604** [ABSTRACT-READ]
- Quote: "In total, 143 out of 310 mortality events across Europe, i.e. 46% of cases, corresponded with rare compound events characterized by hot summers and dry years." ICP-Forest: "34% and 27% of the defoliation and mortality cases corresponded with rare compound climate events, respectively." Background mortality 1993-2013 higher "where summer temperature and VPD more steeply rose, where drought frequency increased."
- Assessment: earlier note correct. Pan-European, not Italy-specific; supports the hot-drought framing. Year is 2021 online (volume 816 in 2022).

**13. Mombrini et al. 2025, Hydrol. Earth Syst. Sci. 29:2255-2273, doi 10.5194/hess-29-2255-2025** [ABSTRACT-READ]
- Quote: "...finding limited areas with significant precipitation decrease and, conversely, a general temperature increase over the region ..." "Significantly, no trend is found at a region-wide level but is instead found when considering homogeneous areas defined by terrain ruggedness." "...the low-altitude part of the region displaying a tendency towards dryer conditions not in common with the mountainous area."
- Correction: the earlier statement "SPEI shows steeper trends than SPI because of temperature increase" is NOT in the abstract; remove it unless full text confirms. The robust statements: Piedmont/Aosta, 60 years, SPI/SPEI 3 and 12 months, temperature up generally (highest at high elevation), drying in lowlands only.
- Assessment: regional (NW Italy); cite for regional heterogeneity, not as national trend.

**14. Brunetti et al. 2006, Int. J. Climatol. 26(3):345-381, doi 10.1002/joc.1251** [ABSTRACT-READ]
- Quote: "...a positive trend for mean temperature of about 1 K per century all over Italy; it is generally higher for minimum temperature than for the maximum temperature. The progressive application of trend analysis shows that, in the last 50 years, behaviour is the opposite; the maximum temperature trend being stronger than that of the minimum temperature." "Precipitation shows a decreasing tendency, even if low and rarely significant, the negative trend being only 5% per century on a yearly basis."
- Assessment: confirmed. Ends around 2000; pair with ISPRA recent rates (below, grey literature).

**15. Vicente-Serrano et al. 2014, Environ. Res. Lett. 9:044001, doi 10.1088/1748-9326/9/4/044001** [ABSTRACT-READ]
- Quote: "...drought severity has increased in the past five decades, as a consequence of greater atmospheric evaporative demand resulting from temperature rise." Iberian Peninsula stations; streamflow of 287 rivers. Abstract only extrapolates to "other Mediterranean areas" speculatively ("probably applicable"). Cite as mechanism; not Italy.

**16. Carnicer et al. 2011, PNAS 108(4):1474-1478, doi 10.1073/pnas.1010070108** [ABSTRACT-READ]
- Actual content: "a generalized increase in crown defoliation in southern European forests occurring during 1987-2007" (ICP Level I); defoliation higher in the drier parts of species distributions; "defoliation trends are paralleled by significant increases in tree mortality rates in drier areas that are related to tree density and temperature effects" assessed specifically "in the Iberian Peninsula region"; plus "sudden changes in insect and fungal defoliation dynamics" (food-web disruption). So BOTH earlier notes were partly right: defoliation is southern European (including Italy plots, presumably; the abstract does not name Italy), mortality and the food-web part are Iberian. Do not cite for Italian mortality.

**17. Malandra et al. 2018, Forests 9(9):551, doi 10.3390/f9090551** [ABSTRACT-READ]
- Quote: "The results revealed a clear trend of forest expansion (+78%) and the reduction of croplands (−49%) and grasslands (−19%). We did not find significant changes in the landscape spatial patterns." Review of 51 manuscripts, 57 case studies; 83 % local scale; most in central and southern Italy. The earlier "grassland value truncated" is now filled: -19 %.
- Caveat: percentages are relative change of class area in heterogeneous local case studies (mean across studies is my reading; the abstract does not define the averaging). All forest, no leaf-habit.

**18. Malandra et al. 2019, Reg. Environ. Change 19(7):1973-1985, doi 10.1007/s10113-019-01531-6** [SEARCH-SUMMARY only; abstract elided]
- Paraphrase: replicate-landscape design, paired 16 km2 landscapes at 10 sites along the range, compares land-cover change by aspect and elevation; expansion "more rapidly at lower elevations, on steeper slopes, and closer to existing forests and cultivated areas" (search-tool wording). Quantitative results not read [still unverified].

**19. Peñuelas & Boada 2003, Glob. Change Biol. 9(2):131-140, doi 10.1046/j.1365-2486.2003.00566.x** [ABSTRACT-READ]
- Quote: "Beech (Fagus sylvatica) forest has shifted altitudinally upwards by ca. 70 m at the highest altitudes (1600-1700 m). Both the beech forests and the heather (Calluna vulgaris) heathlands are being replaced by holm oak (Quercus ilex) forest at medium altitudes (800-1400 m)." "In 'isolated' (small and surrounded by holm oaks) beech stands, beech trees are 30% more defoliated, beech recruitment is 41% lower, and holm oak recruitment is three times higher than in 'continental' (large and continuous) beech stands."
- Correction of the "3x recruitment claim": it is a comparison between isolated and continental beech stands (holm oak recruitment 3x higher inside isolated beech stands), NOT a time trend and not a whole-mountain recruitment factor. Drivers: "progressively warmer conditions, complemented by the land use changes (mainly the cessation of traditional land management)", labelled "apparent causes" (inference, not partitioned). Comparison is 1945 vs current distribution (NE Spain, Montseny).
- Assessment: cite, with that precise wording.

**20. Lloret et al. 2004, Glob. Change Biol. 10(12):2092-2099, doi 10.1111/j.1365-2486.2004.00870.x** [ABSTRACT-READ]
- Quote: "...the drought of 1994, which produced important changes in the Quercus ilex forests, with up to 76% of the trees showing complete canopy dieback." "Stump and crown resprouting was fairly extensive." "...recurrent droughts can produce a progressive loss of resilience, by depleting the ability of surviving plants to regenerate." Substrate (breccia vs schist) mediated damage. Catalonia, Garraf-type setting not named in the abstract.
- Assessment: correct; worth citing for both resprouting and the progressive loss of resilience (relevant to repeated 2012/2017/2024 events).

**21. Garcia-Fayos et al. 2020, PLoS ONE 15(10):e0239755, doi 10.1371/journal.pone.0239755** [ABSTRACT-READ]
- Quote: "The increase in aridity in the last decades has drastically reduced the recruitment of new individuals in the forests of Q. ilex located in the lower limit of their precipitation niche, regardless of the intensity of past deforestation." 17 plots of 5.3 ha, Iberian System, eastern Spain. Regeneration limit at the dry edge; Spain, not Italy. Good two-sided counterpoint.

**22. Seddaiu/Satta preprint (SSRN 5761729)** [METADATA-ONLY here; only seen as a Scholar hit with snippet "south-eastern Sardinia ... drone RGB showing widespread crown dieback in Quercus ilex"]. Preprint, not peer reviewed.

**23. Others in the earlier list**
- Cramer et al. 2018, Nature Clim. Change 8:972-980, doi 10.1038/s41558-018-0299-2 [METADATA-ONLY: abstract elided; authors verified incl. Peñuelas]. Context citation only. Open copy at hal.science/hal-01911390.
- Malavasi et al. 2018, Reg. Environ. Change 18(8):2459-2469, doi 10.1007/s10113-018-1368-9 [METADATA-ONLY]. Still unverified content; low priority.
- Walther 2002, Folia Geobot. 37:129-139, doi 10.1007/bf02803195 [METADATA-ONLY]. Conceptual only.
- Conedera et al. 2018, doi 10.1007/s10113-017-1212-7 [not re-read here; already in wiki].

### Inferences
- The only truly quantitative Italian numbers on dieback are in Seddaiu 2025 (compiled, partly anecdotal) and the unreviewed Satta preprint; both Sardinia 2024 area figures (about 110,000 ha) may share one origin.
- The INFC chapter's statement that the evergreen "other" class gains +33.6 % but is a residual class with newly formed stands warns against reading INFC "evergreen gain" as holm oak expansion.

### Gaps
- Garbarino 2020 and Malandra 2019 full texts remain unread (open post-prints exist at iris.unito.it handles 2318/1765594 and 2318/1723103; blocked from here).
- Alderotti 2025 sample size/site; Pollastrini 2019 mortality numbers; exact INFC2005 holm oak area (Fig. 13.2 only).

---

## B1. Italy-wide or regional drought/temperature trends

### Takeaway
No peer-reviewed Italy-wide SPEI trend paper for 1950-2020 with a clean "frequency of droughts" trend was found. The best verified national-scale items are Pascale & Ragone 2025 (1901-2023, SPEI/SPI, widespread multi-year droughts) and Brunetti 2006 (secular temperature trend), plus ISPRA grey literature for 1981-2023 warming. Regional studies disagree in sign by index and region.

### Cited Findings
- Pascale S, Ragone F (2025). Widespread multi-year droughts in Italy: identification and causes of development. Int. J. Climatol., doi 10.1002/joc.8827. [ABSTRACT-READ, Crossref] "Seven WMYD events are identified using two different precipitation datasets: 1921-1922, 1942-1944, 1945-1946, 2006-2008, 2011-2013, 2017-2018 and 2021-2023." (events affecting at least 30 % of Italy; SPEI and SPI; 1901-2023.) Three of seven events cluster in 2006-2023 and 2011-2013 and 2017-2018 coincide with Tuscany/Apulia dieback years. Attribution to anthropogenic change explicitly left as "a first step". Likely the "123-year Italian drought study" that the earlier note could only cite as a press report: now a primary source. Search tool also said "33 drought events affecting >30 %"; that number is not in the abstract [unverified]. Worth reading: yes (drivers section).
- Spinoni J, Naumann G, Vogt J (2017). Pan-European seasonal trends and recent changes of drought frequency and severity. Glob. Planet. Change, doi 10.1016/j.gloplacha.2016.11.013. [ABSTRACT-READ; year from DOI 2017 print, OpenAlex lists 2016 online; verify] SPEI-3/SPI-3 from E-OBS 1950-2015 and 1981-2015: SPI shows "a moderate opposite tendency over Southern Europe", SPEI "Southern and Eastern Europe show a more remarkable drying tendency". Pan-European, Italy not separated in abstract. Useful to justify SPEI over SPI at continental scale (this is the better support for the "SPEI more drying than SPI" claim that was wrongly attached to Mombrini).
- Becherini F, Stefanini C, della Valle A (2024). Multi-secular trend of drought indices in Padua, Italy. Climate 12(12):218, doi 10.3390/cli12120218. [ABSTRACT-READ] 1725-2023; "The innovative trend analysis applied to SPEI12 indicates a general increasing trend in droughts, while for SPI12, it is significant only for severe events"; SPI-SPEI difference grew since mid-20th century, related to warming. Single station; sound supporting evidence for SPEI > SPI.
- Venturi S, Dunea D, Mateescu E (2024). SPEI and SPI correlation ... Umbria. Environ. Sci. Pollut. Res., doi 10.1007/s11356-024-35740-2. [ABSTRACT-READ] 1961-2020; SPEI better captures temperature effects; SPEI-SPI correlation decreasing between 1961-1990 and 1991-2020.
- Aschale TM et al. (2024). Sicily SPI/SPEI trends 1950-2023, Water 16(18):2593, doi 10.3390/w16182593. [ABSTRACT-READ] 2002 most severe drought; SPI significantly increasing in eastern coast, SPEI significantly decreasing in western Sicily "mainly related to increased evapotranspiration rates". Shows regional sign differences.
- Baronetti A et al. (2022). Future droughts in northern Italy, Climatic Change, doi 10.1007/s10584-022-03370-7. [ABSTRACT-READ] Projections (EURO-CORDEX), "evapotranspiration anomaly is the main triggering factor"; not observational. Optional.
- Caloiero and co-authors, Calabria/Sardinia SPI trends (1951-2016; Sardinia 1922-2011 "the majority of the drought events have been detected after 1980") [SEARCH-SUMMARY only; no DOIs retrieved; regional]. Not recommended unless a regional argument is needed.
- Kew SF et al. (2019). The exceptional summer heat wave in Southern Europe 2017. BAMS, doi 10.1175/bams-d-18-0109.1 [METADATA-ONLY; abstract is "International audience" only]. Potential citation for the 2017 event attribution; content unread.
- ISPRA (grey literature, not peer reviewed; via search summary): Italy mean temperature trend 1981-2020 +0.37 ± 0.04 degC per decade (2021 report), about +0.40 degC per decade for 1981-2023 (2024 report), summer +0.55 ± 0.09 degC per decade; 2023 second warmest year since 1961. [SEARCH-SUMMARY; numbers need checking on indicatoriambientali.isprambiente.it before citing]. Toreti & Desiato 2007 (Temperature trend over Italy 1961-2004) is named by ISPRA but its content was not read.
- Cramer 2018, Peñuelas-related Mediterranean hot-spot papers: only Cramer's metadata verified.

### Inferences
- For the paper: Brunetti 2006 (secular trend) + Pascale & Ragone 2025 (national drought episodes) + Spinoni 2017 (SPEI vs SPI, Europe) + ISPRA (recent warming rate, flagged as grey) is an adequate, honest driver argument. The SPEI vs SPI choice is supported by Spinoni 2017, Becherini 2024 and Aschale 2024; Mombrini 2025 mainly shows heterogeneity.

### Gaps
- No peer-reviewed national gridded SPEI trend (e.g., 1981-2023 CHELSA/E-OBS based) found; no Italian winter-minimum-temperature trend paper verified (Brunetti 2006 has minimum vs maximum only to ~2000). Vicente-Serrano and Spinoni are not Italy-specific; no checked Italian paper using Cramer/Spinoni-type heat wave frequency counts.

---

## B2. Q. ilex dieback 2012/2017/2022/2024 beyond the known set; Q. suber Sardinia

### Takeaway
Beyond Pollastrini/Alderotti/Seddaiu there is a modest set of Italian items: Alderotti & Verdiani 2023 review, Bregant 2025 and Del Grosso 2024 on pathogens in Apulia, Conte 2019/2025 on oak decline in Basilicata, Ripullone et al. 2026 synthesis, and the 2020 Seddaiu Phytophthora overview for cork oak in Sardinia. I found no peer-reviewed paper that quantifies 2022 Q. ilex dieback in Italy and none that maps 2024 dieback other than the preprint.

### Cited Findings
- Alderotti F, Verdiani E (2023). God save the queen! How and why the dominant evergreen species of the Mediterranean Basin is declining? AoB PLANTS 15 (plad051), doi 10.1093/aobpla/plad051. [ABSTRACT-READ via Europe PMC PMC10601391] Review: "an increase in holm oak decline has been observed in the last decade"; abiotic and biotic stressors; proposes management choices. Worth reading for DISC and mechanisms; author order per Europe PMC "Alderotti F, Verdiani E" (journal pages and volume not verified [still unverified]).
- Bregant C, Carloni F, Borsetto G et al. (2025). Multiple Botryosphaeriaceae and Phytophthora species involved in the etiology of holm oak decline in southern Italy. Forests 16(7):1052, doi 10.3390/f16071052. [ABSTRACT-READ] Surveys winter 2024 in three Apulian woodlands, "sudden death, crown thinning, shoot and branch dieback, sunken cankers, and root rot"; Diplodia corticola, D. quercivora, Phytophthora cinnamomi, P. multivora, P. psychrophila, P. asparagi; Koch's postulates satisfied for P. asparagi and P. psychrophila on seedlings. Resolves the earlier "unread, scope unverified" flag: Apulia, not Sardinia. Supports pathogen complex alongside drought.
- Del Grosso C et al. (2024). First report of Diplodia quercivora and Neofusicoccum vitifusiforme ... holm oak ... southern Italy. J. Fungi 10(1):35, doi 10.3390/jof10010035. [METADATA-ONLY in this run; title/year/venue from OpenAlex] Minor (pathogen first report).
- Conte AL, Di Pietro R, Iamonico D, Di Marzio P, Cillis G, Lucia D, Fortini P (2019). Oak decline in the Mediterranean basin: a study case from the southern Apennines (Italy). Plant Sociology 56(2):69-80, doi 10.7338/pls2019562/05. [SEARCH-SUMMARY; the earlier assumption that this is Plant Biosystems was wrong according to the search tool] 2015 vs 2017 compared (described as hottest and driest years "since 1800"); satellite decline signs evident in 2017 and not 2015, confirmed by field Decline Severity; hypothesis: reduction of rainfall in the first semester. Study is Lucanian Apennine, mixed oaks incl. decline in holm oak coppices (per Scholar snippet). The "since 1800" claim is the authors' as paraphrased; not verified.
- Conte AL, Di Pietro R, Di Marzio P, Strumia S, Cillis G, Capuano A, Fortini P (2025). Oak decline in southern Italy: environmental and climate parameters for modelling purposes. Vegetation Ecology and Diversity 62:e160170, doi 10.3897/ved.160170. [METADATA-ONLY; page loaded without abstract text]. Scholar snippet mentions "crown damage by die back" and "thermophilic deciduous oak forests"; species coverage unverified.
- Ripullone F, Chiavetta U, La Mela Veca DS, Masiero M et al. (2026). Italian oak forests facing stress factors and climate change: current evidence, ecophysiological knowledge and management perspectives. Forest@ , doi 10.3832/efor5088-023. [ABSTRACT-READ] Workshop report. Quote: "Long-term data from the CONECOFOR program confirm species-specific strategies: Q. pubescens sheds leaves in summer, Q. cerris exhibits sudden mortality, while Q. ilex, though drought-tolerant, is vulnerable to extreme events." "Future scenarios predict a reduction in forest cover and the replacement of native species with more resistant species." Not an original data paper; useful as a very recent Italian synthesis (2026). Journal volume/pages not verified.
- Seddaiu S et al. (2020). An overview of Phytophthora species inhabiting declining Quercus suber stands in Sardinia (Italy). Forests 11(9):971, doi 10.3390/f11090971. [ABSTRACT-READ] 39 declining cork oak stands sampled 2015-2019; 14 Phytophthora species; P. cinnamomi most frequent from rhizosphere, then P. quercina, P. pseudocryptogea, P. tyrrhenica. Pathogen survey, no distribution change; the only verified Q. suber Sardinia item. Also Seddaiu et al. 2025 Mycol. Progress (metabarcoding, doi 10.1007/s11557-025-02039-6) and Linaldeddu et al. 2005 (Biscogniauxia) are listed by OpenAlex [METADATA-ONLY].
- Scanu B et al. (2025), Pollastrini M et al. (2025) conference abstracts (Florence repository, "Monitoring of Quercus ilex dieback and mortality in central and southern Italy"; "Mediterranean forest vulnerability to climate pressure") [METADATA-ONLY/Scholar snippets]. Snippet from Scanu: dieback in coastal Tuscany "since the extreme drought and heatwave of 2017"; "In Italy the highest anomalies for 2024 were observed in central and southern regions". Conference abstracts: do not cite as evidence.
- Pasquini et al. 2023 (BVOC, Sci. Total Environ.), Brunetti et al. EGU26 abstract ("Restore and improve the conservation status of threatened forests by holm oak dieback", doi 10.5194/egusphere-egu26-13751) [METADATA-ONLY]; conference/physiology, not needed.
- Italian-language: Scholar for "deperimento leccio" gave the Seddaiu Italian version and Ripullone 2026 (Forest@), a Workshop note in L'Italia Forestale e Montana (Ripullone et al. 2025, italiaforestalemontana.it/index.php/ifm/article/view/1208), a Scanu et al. 2015 Phytophthora congress paper (flore.unifi.it) and theses; no further primary Italian-language dieback data paper. [Scholar snippets only]
- 2022: no dedicated holm oak dieback paper found; Seddaiu 2025 names 2022 only among heat episodes.

### Inferences
- A defensible INTRO statement: dieback documented in Tuscany from 2012, widespread after 2017, and across Apulia, Basilicata, Sardinia, Sicily in 2024 (Seddaiu 2025), with pathogen complexes in Apulia (Frisullo 2018, Bregant 2025) and Sardinian cork oak (Seddaiu 2020); with resprouting in the following season (Pollastrini 2019, Seddaiu 2025).
- Colangelo 2017 (Q. frainetto) and Colangelo 2018 must not be cited for holm oak.

### Gaps
- No peer-reviewed spatial quantification of dieback extent except the SSRN preprint; no peer-reviewed Q. suber Sardinia distribution or cover-change paper (only pathogen and regeneration items; Vogiatzakis et al. 2020 Forests 11:593, "Incorporating landscape character in cork oak forest expansion in Sardinia", doi 10.3390/f11050593 [METADATA-ONLY], is a policy/landscape planning paper on planned expansion).

---

## B3. Land abandonment and forest expansion in Italy

### Takeaway
There is solid, repeated evidence of post-1950s forest expansion in Italy (Falcucci 2007; Malandra 2018; Vitali 2017; Santoro & Piras 2023; INFC 2005 to 2015 +3.7 % forest). All are all-forest or coarse-class (conifer/broadleaf/mixed). None separates evergreen from deciduous gain. Searches for Mazzoleni, Ferrara and Corti returned nothing usable (the search tool could not find them; absence of evidence from a weak search).

### Cited Findings
- Vitali A, Urbinati C, Weisberg PJ et al. (2017). Effects of natural and anthropogenic drivers on land-cover change and treeline dynamics in the Apennines (Italy). J. Veg. Sci. 28, doi 10.1111/jvs.12598. [ABSTRACT-READ] Corine 1990-2012 on 776 municipalities (43,000 km2): human population -3 % (1991-2011), shrublands +7 %, forests (mixed +4 %, conifers +2 %, broad-leaf +1 %), pastures -9 %; landscape scale 1954-2012: forests expanded "more on southwest (+109%) than on northeast (+19%) slopes". Notable: the only Corine breakdown with leaf type (broad-leaf +1 % in 1990-2012, no evergreen split). Cite for DRIV.
- Ascoli D, Moris JV, Marchetti M et al. (2024). Land use change towards forests and wooded land correlates with large and frequent wildfires in Italy. Ann. Silvic. Res. 49, doi 10.12899/asr-2264. [ABSTRACT-READ] Italian Land Use Inventory (IUTI) 1990-2008, 1,206,198 photo-interpreted points; "expansion of forests, shrubland and new settlements at the expense of agricultural land, grasslands and pastures". Relevant for a fire/disturbance mask and for IUTI as a national dataset; volume/pages unchecked.
- Sallustio L, Simpatico A, Munafo M et al. (2015). Recent trends in forest cover changes: only positive implications? L'Italia forestale e montana 70(4), doi 10.4129/ifm.2015.4.03. [ABSTRACT-READ] IUTI national LULCC trends, focus on natural reforestation at macroregion level. Italian-journal national source; numbers not in abstract.
- Santoro A, Piras F (2023). Natural forests or cultural forests? Forest changes within Italian protected areas in the last 85 years. Forests 14(5):921, doi 10.3390/f14050921. [ABSTRACT-READ] 1936 forest map vs now: forest surface in PAs +33.1 % (regional) to +45.2 % (national); Natura 2000 growth 8709 ha/year; 500-1000 m a.s.l. most affected; in 1936 most forests were coppice (44-62 %). Useful for the coppice/abandonment link. Uses the 1936 Kingdom Forest Map (Ferretti et al. 2018, Ann. Silvic. Res. 42, doi 10.12899/asr-1411 [ABSTRACT-READ]: map describes "forest extent and species composition for the whole of Italy"; potentially the only historical species-level baseline, to check whether holm oak is mapped).
- La Mela Veca DS, Cullotta S, Sferlazza S et al. (2016). Anthropogenic influences in land use/land cover changes in Mediterranean forest landscapes in Sicily. Land 5(1):3, doi 10.3390/land5010003. [ABSTRACT-READ] 7 landscapes 1955-2012, aerial photos; "for almost all study areas an increase of forest cover and expansion". Evergreen-oak landscapes included but not separated in abstract.
- Pallotta E et al. (2022). Forest dynamic in the Italian Apennines, Appl. Sci. 12(5):2474, doi 10.3390/app12052474 [ABSTRACT-READ]: Abruzzo, Lazio e Molise NP, 1954 to present, "forest surface expansion and an open areas decrease". Local.
- Cimini D, Tomao A, Mattioli W et al. (2013). Ann. Silvic. Res. 38, doi 10.12899/asr-771 [ABSTRACT-READ]: 1989-2008, 57 % of shrubland uptake and 46 % of forest uptake on former HNV farmland, Central Apennines NP. Local.
- Mancino G, Nole A, Ripullone F, Ferrara A (2013/2014). Landsat TM NDVI differencing, natural forest expansion Basilicata. iForest 7 (OpenAlex lists 2013; doi 10.3832/ifor0909-007) [ABSTRACT-READ]. 1984-2010: "total regional forest cover increased by 19.7% (70154 ha), consistent with National Forest Inventory data (1984-2005)"; 91.8 % accuracy; "considerable forest expansion also occurred on degraded soils in drought-prone Mediterranean areas". Directly relevant method precedent (Landsat, southern Italy); author "Ferrara" is Ferrara A (my recall of the author list is unverified; OpenAlex returned the first three names only).
- Sitzia T et al. (2015), eastern Italian Alps forest expansion despite traditional management [SEARCH-SUMMARY only; no DOI retrieved].
- Beffa G et al. (2025). Causes of co-existence of Fagus and evergreen Quercus forests in central Italy during the Holocene thermal maximum. Forest Ecosystems 12, doi 10.1016/j.fecs.2025.100345 [ABSTRACT-READ]: Lake Mezzano; "Fagus sylvatica declined and evergreen Quercus ilex expanded after 8,200 cal years BP when the climate became warmer"; human impact after 7,450 BP. Palaeo analogue for warming-driven evergreen expansion in Italy; citable as long-term context only.
- Otero I et al. (2015) Ecol. Soc. 20(2):7 (doi 10.5751/es-07378-200207): abstract field contained only the citation [METADATA-ONLY]; Catalonia; skip.
- Malavasi 2018 [METADATA-ONLY].

### Inferences
- Cimini/Ascoli/Sallustio/Mancino show Italian practice of mapping forest gain with IUTI and Landsat; the novelty claim (no Italian evergreen vs deciduous gain study) is not contradicted by anything I could read, but the search was weak for Italian-language and book-chapter sources.

### Gaps
- Mazzoleni, Ferrara, Corti not located; no verified paper separating evergreen from deciduous gain on abandoned land in Italy.

---

## B4. Coppice abandonment/conversion and evergreen oak or evergreen understory

### Takeaway
Coppice is large (about 35 % of Italian forest per Mairota et al. 2016; holm oak about 10 % of coppice) and widely aged/abandoned, but I found no paper testing whether abandonment favours Q. ilex over deciduous oaks. Available items are management-effect studies on holm oak coppice.

### Cited Findings
- Mairota P, Manetti MC, Amorini E et al. (2016). Opportunities for coppice management at the landscape level: the Italian experience. iForest 9:775-782, doi 10.3832/ifor1865-009. [FULLTEXT-PARTLY-READ via fetch-summariser of the iForest page; verbatim not available; internal inconsistency in numbers returned (36,631 km2 vs 340 km2) so treat the numbers as [unverified]] Coppice "almost 35%" of national forest cover; Quercus ilex "10 %" of coppice; generalised abandonment of coppice "likely to hamper ecological functionality"; many coppice-with-standards have "withering populations of stools"; utilisation about one third below increment; conversion "not generally feasible".
- Fabbio G, Cutini A (2017). Coppice today: which management beyond definitions? Forest 14:..., doi 10.3832/efor2562-014 [ABSTRACT-READ, Italian] Coppices cover "quasi 3.700.000 ettari (Gasparini & Tabacchi 2011)". Background only.
- Cutini A, Mattioli W, Roggero F et al. (2018). Coppice silviculture: are laws and regulations in line with current conditions in Italy? Forest 15, doi 10.3832/efor2772-015 [ABSTRACT-READ]: "less intensive management in the recent decades, coppices still cover a large part of Italian woodlands"; "aged" stands with large volumes.
- Manetti MC, Giannini T, Chianucci F et al. (2013). Structural and ecological changes in holm oak coppices 25 years after their conversion into high forest. Ann. Silvic. Res. 37, doi 10.12899/asr-770 [ABSTRACT-READ]: southern Sardinia; "Sardinia holds about 40% of holm oak cover in Italy" (matches INFC Table 7.7: 255,463 of 643,052 ha); "Most of holm oak stands originated from overgrown coppice forests partly undergoing conversion into high forest"; thinning gave simplified structure, poor biodiversity, positive evaluation of conversion. 2 plots only.
- Marziliano PA (2009). Deadwood in ageing holm oak coppices of Gargano. Forest 6, doi 10.3832/efor0555-006 [ABSTRACT-READ]: 34 m3/ha deadwood, 12.62 Mg C/ha; quantity "intrinsically linked ... to the culture abandonment or to the meteoric disturbances". Local.
- Sferlazza S et al. (2018). Carbon storage in holm oak coppice, Madonie. iForest 11:344-351, doi 10.3832/ifor2424-011 [ABSTRACT-READ]: "coppicing is a sustainable forest management choice from the point of view of the carbon balance"; not about distribution.
- Gazol A, Hereş A-M, Curiel Yuste J (2020). Land-use practices (coppices and dehesas) and management intensity modulate responses of holm oak growth to drought. Agric. For. Meteorol. 292-293:108235, doi 10.1016/j.agrformet.2020.108235 [ABSTRACT-READ via Semantic Scholar, truncated]: ten sites in Spain, declining dehesas vs declining and healthy coppices; SPEI-based. Spain. Page numbers/volume not verified.
- Santi I, Cabrucci M, Carrari E et al. (2025). Coppice management affects leaf traits in understory species of Mediterranean oak forests. For. Ecol. Manage. 122517, doi 10.1016/j.foreco.2025.122517 [ABSTRACT-READ]: two Italian sites, herbaceous understory under coppice vs high stands; not evergreen shrub understory; marginal.
- Gentilesca 2017 recommends shorter coppice rotation or gradual conversion to high forest as resilience measures [ABSTRACT-READ].
- Camponi L et al. (2022, 2023) on Turkey oak and holm oak cover and soil C, J. Environ. Manage. [METADATA-ONLY]; not distribution.

### Inferences
- The assumption that coppice abandonment helps evergreen oaks (via shade tolerance) is expert reasoning only; no Italian source tested it in what I could access. Treat as hypothesis, mark "needs verification" in the wiki.

### Gaps
- Italian-language searches (cedui di leccio, invecchiamento, conversione ad alto fusto) returned only general coppice reviews; Scholar was throttled when attempted. Not checked: Sherwood, L'Italia Forestale e Montana article lists, Annals of Silvicultural Research regional holm oak papers.

---

## B5. Holm oak expansion and range shifts in Italy

### Takeaway
I found NO verified Italian study of Q. ilex expansion into deciduous forest or upslope. Verified analogues: Peñuelas & Boada 2003 (Catalonia), Delzon 2013 (France, northern margin), Cruz-Alonso 2019 (Spain, abandoned fields), Beffa 2025 (Holocene, Italy), and Pignatti 2011 (Italian forest vegetation vs coldest-month temperature scenarios).

### Cited Findings
- Delzon S, Urli M, Samalens J-C et al. (2013). Field evidence of colonisation by holm oak, at the northern margin of its distribution range, during the Anthropocene period. PLoS ONE 8(11):e80443 (volume/issue not checked), doi 10.1371/journal.pone.0080443. [ABSTRACT-READ] Forest inventory 1880-2010; "Q. ilex has colonised substantial new areas over the last century"; maximum colonisation rate "22 to 57 m/year", "much slower than predicted by the models". Atlantic France, not Italy; strong analogue for expansion with speed limits.
- Cruz-Alonso V, Villar-Salvador P, Ruiz-Benito P et al. (2019). Long-term dynamics of shrub facilitation shape the mixing of evergreen and deciduous oaks in Mediterranean abandoned fields. J. Ecol. 107, doi 10.1111/1365-2745.13309. [ABSTRACT-READ] Old field, 30 years after abandonment: "Recruitment rate was the highest for the shrub, followed by the evergreen oak" (Q. ilex vs deciduous Q. faginea); colonisation under shrubs "appreciable 20 years after field abandonment". Spain; directly relevant mechanism for evergreen oak on abandoned land.
- Pignatti G (2011). Forest vegetation in view of some scenarios of climate change in Italy. Forest 8, doi 10.3832/efor0650-008. [ABSTRACT-READ] Scenario A2a/B2a HadCM3, coldest-month temperature up to +4.4 degC by 2080: "more Mediterranean species on lower mountains, hills and lowlands of the country". Projection, old GCM; supports the cold-limit mechanism but is not observation.
- Conedera 2018 (wiki), Peñuelas & Boada 2003 (above). Rigling et al. 2012 (GCB, pine to downy oak in Valais) appeared in searches [METADATA-ONLY]; not evergreen.
- Beffa 2025 (palaeo, above).
- Delzon-type or Italian Q. ilex SDM papers: none verified in this round.
- The unidentified claim about "an increase in the sclerophyllic evergreen oak component" in Apennine oak woods: a phrase search found no source; still unverifiable; do not cite.
- Alias S et al. 2010 iForest (shrub facilitation of Q. ilex and Q. pubescens regeneration in wooded pasture, central Sardinia, doi 10.3832/ifor0517-003) [METADATA-ONLY]; potentially relevant regeneration study; abstract not read.
- Cinque Terre note (parconazionale5terre.it) says evergreen oak woods formed after farming stopped [SEARCH-SUMMARY of a park web page; not peer reviewed].

### Inferences
- The gap statement "no Italian study quantifies evergreen expansion" survives this round (limited by failed Scholar queries).

### Gaps
- Italian-language ("leccio espansione quote") searches failed due to rate limits; no Apennine or alpine-foothill Q. ilex colonisation paper identified. Cinque Terre / Ligurian terrace abandonment literature not searched properly.

---

## B6. NFI-based evergreen vs deciduous change (INFC 1985/2005/2015)

### Takeaway
Only one verified source with figures: Gasparini & Tabacchi 2022 (INFC2005 vs INFC2015). INFC1985 vs 2005 comparison (De Natale & Gasparini 2011 chapter in INFC2005 book; cited inside Gasparini & Tabacchi) was not retrieved. Evergreen categories show no clearly reportable area gain except the residual "Other evergreen broadleaved".

### Cited Findings
- All numbers above under A.11 [FULLTEXT-PARTLY-READ]. In addition: Holm oak INFC2015 area 643,052 ha (SE 2.4 %); growing stock gain +34.2 % while area change was not "considerable". The authors note the first-phase sample is the same, so INFC2005 and 2015 estimates are not independent.
- INFC1985 (IFNI85) is not harmonised with INFC2005 ("diverge for some defining and classification aspects"), so a 1985-2005-2015 evergreen series needs reclassification; the chapter says so explicitly.
- D'Amico G et al. (2025). National Forest Inventory in Italy: new perspectives for forest monitoring. Ann. For. Sci., doi 10.1186/s13595-025-01303-9 [METADATA-ONLY]; method.
- Ferretti 2018 1936 map [ABSTRACT-READ]; "comparisons with current national forest inventory data" mentioned.

### Inferences
- INFC cannot validate small shifts in evergreen oak area (high SEs); comparing growing stock/biomass is more informative than area.

### Gaps
- INFC2005 holm oak area value (in Fig. 13.2 of the chapter only), INFC2015 online tables (inventarioforestale.org/statistiche_INFC) not accessible here; De Natale & Gasparini 2011 not retrieved.

---

## REJECTED / DEMOTED (with reasons)
- Colangelo et al. 2017, Tree Physiol. 37:617 (doi 10.1093/treephys/tpx002): Q. frainetto, southern Italy; not Q. ilex.
- Colangelo 2018 as holm oak evidence: deciduous oaks only; pathogen finding opposite to simple reading.
- Gentilesca 2017 for Q. ilex specifics: mostly ring-porous deciduous oaks.
- Mombrini 2025 as national trend or SPEI>SPI evidence: regional, abstract finds no region-wide trend.
- Conference abstracts (Scanu 2025, Pollastrini 2025, EGU 2026 Brunetti/Alderotti): not peer reviewed.
- Conte 2025 (VED): abstract unreadable, species unverified; Conte 2019 only via search summary.
- Gazol 2020 (Spanish coppice vs dehesa), Lloret 2004, Garcia-Fayos 2020, Peñuelas & Boada, Delzon 2013, Cruz-Alonso 2019: non-Italian analogues; keep only as analogues.
- Baronetti 2022 and Pignatti 2011: projections.
- Spinoni 2017, Vicente-Serrano 2014, Carnicer 2011, Cramer 2018: not Italy-specific.
- Santi 2025 (understory herbs), Sferlazza 2018 (carbon), Marziliano 2009 (deadwood), Camponi 2022/2023 (soil C): do not address distribution.
- Vogiatzakis 2020 (cork oak expansion planning), Otero 2015 (Catalonia), Kew 2019 (abstract unread): low priority or unread.
- Sources not usable: ISPRA warming rates are grey literature (verify on ISPRA site); the "33 events" figure and "since 1800" statements come from search-tool paraphrases.
