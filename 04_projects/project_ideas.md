# Project ideas

Brainstorming general ideas for research projects


# Forests under pressure: climate-driven stress and early warning signals

> [!abstract] Motivation
> - Anthropogenic climate change is fundamentally altering the disturbance regime of European forests through increased frequency of compound hotter drought events (simultaneous low precipitation, elevated temperature, and high VPD) [[drought_mortality]]
> - Rising VPD intensifies physiological stress — driving xylem hydraulic failure and carbon starvation — in key conifer species and predisposes them to secondary biotic agents, particularly *Ips typographus* (European spruce bark beetle) [[forest_disturbances]]
> - Disturbance interactions (drought → bark beetle → windthrow) are non-linear and compounding: ignoring them underestimates total damage by a factor of 2.6–3.9× [[grünig_2026_climate_change_disturbances_forest]]
> - Pan-European Landsat evidence (EFDA, 1985–2023; 439,000 km² disturbed) and species-specific canopy cover loss assessments confirm accelerating disturbance rates and regionally differentiated forest response [[soto_2025_disturbance]], [[wegler_2026_canopy_cover_loss]]

>[!info] Research gap
> - Spatio-temporal attribution of stress signals to specific climatic drivers (VPD, cumulative water deficit, temperature anomaly) at Sentinel-2 (10 m) resolution remains unresolved
> - Early detection of pre-visual physiological decline — before detectable NDVI change — is an explicitly identified gap in the remote sensing forest health literature [[torres_2021_forest_health_remote_sensing]]
> - Integration of near-real-time Sentinel-2 SITS anomaly detection with climate reanalysis data for operational stress monitoring has not been demonstrated at regional scale
> - Topographic microclimate buffering (aspect, soil moisture, cold-air pooling) creates within-stand heterogeneity in stress exposure that is rarely accounted for in broad-scale analyses [[topographic_microclimate]]

> [!question] Research questions / Hypotheses
> - Which forest stands are most susceptible to climate-induced stress, and can susceptibility be predicted from species composition, topographic position, and historical disturbance history?
> - How do temperature anomaly and cumulative VPD deficit jointly determine the spatial pattern and severity of forest die-back across Central European forest landscapes?
> - Can near-real-time Sentinel-2 SITS-based anomaly detection provide operationally useful early warning of acute stress events prior to ground-detectable mortality?

### Methods
- Bayesian inference for stress likelihood

# Dying trees in Tyrolean forests: climatic triggers and spatio-temporal die-back dynamics

> [!abstract] Motivation
> - *Pinus sylvestris* (Scots pine) and *Picea abies* (Norway spruce) stands in Tyrol are experiencing episodic but intensifying individual-tree die-back following recent compound drought-heat events
> - Nationally, *Picea abies* accounted for 51.3% and *Pinus sylvestris* for 21.6% of total forest canopy cover loss in Germany 2018–2024, with mortality peaking in 2020–2021 as a delayed response to the 2018–2019 extreme drought [[wegler_2026_canopy_cover_loss]]
> - *Ips typographus* amplifies primary drought-induced mortality through secondary attack of physiologically weakened trees; drought-legacy effects (impaired recovery, continued vulnerability) persist for multiple years post-event [[drought_mortality]]
> - 20th-century redistribution of tree growth from energy- to water-limitation has accelerated in the Alps, with summer VPD emerging as the dominant growth constraint even in historically cold-humid stands [[babst_2019_redistribution]]

>[!info] Research gap
> - The specific climatic trigger thresholds (VPD peak magnitude, cumulative water deficit, compound temperature–drought duration) that initiate stand-level die-back in Tyrolean *Pinus sylvestris* and *Picea abies* are unquantified
> - Spatio-temporal mapping of individual-tree and stand-level die-back at high spatial resolution requires validated methods integrating Sentinel-2 SITS with terrain-corrected microclimate variables — such methods do not yet exist for the eastern Alps
> - The relative contributions of direct hydraulic failure, bark beetle secondary attack, and climate-legacy vulnerability to observed regional mortality patterns cannot be disentangled without temporally dense remote sensing data paired with field evidence
> - Future die-back trajectories and the potential persistence of topographically sheltered climate refugia under CMIP6 warming scenarios remain unquantified at local to regional scale [[species_distribution_models]]

> [!question] Research questions / Hypotheses
> - What climatic event characteristics (intensity, duration, compound temperature–drought combination) function as die-back triggers in Tyrolean *Pinus sylvestris* and *Picea abies* stands, and do critical thresholds differ between species?
> - Can Sentinel-2 SITS anomaly detection — combined with terrain-derived microclimate variables — reconstruct the spatio-temporal evolution of recent die-back episodes at single-tree to stand spatial scale?
> - What is the relative contribution of direct physiological drought stress versus facilitated *Ips typographus* outbreak to regional mortality patterns, and how are these pathways separated in time and space?
> - Under projected climate scenarios (CMIP6 SSPs), which stand types and topographic positions in Tyrol represent the highest future die-back risk, and which may function as microclimate refugia?

# Alpine forest tree line under stress

- How does drought and low snow cover winters affect alpine tree line ecotone succession?
- increase in summer drought periods
- increase of winters with low snow cover -> soil freezes -> rejuvenation hindered
- pinus cembra in the tree line transition zone: rejuvenation dynamics under stress, resilience against winter/spring (soil-)frost and summer drought
- hypothesis: drought stress is more impactfull in open areas than in dense forest -> with higher stress frequency, densification of open areas gets slower/harder and rise of tree line is slowing
- methods: 
  - reference data from gloria plots in the alps (only tree line ecotone summits)
  - Interpretation of webcam imagery (long-term, or self installed for 1 year with infrared sensor)
  - dendrochronology as reference for bad growth years in juvenile trees
  - Solar-induced fluorescence (SIF) from drone imagery -> monthly flights under differing conditions (wet/normal/drought/spring etc.)
  - satellite imagery high resolution (e.g. planet) and long term hindcasting/prediction using Landsat/MODIS
- Workpackage 1:
  - Impact of drought and frost on photosynthetic activity in trees at the tree line ecotone
  - SIF measurements over open trees and in dense forests -> decrease of activity maybe even browning under differing conditions
- Workpackage 2:
  - modelling and predicting tree line ecotone shift under climatic drivers and constraints
  - high-resolution satellite imagery -> tree crown segmentation and stress monitoring per tree

> [!abstract] Motivation
> - Alpine treeline ecotones are among Earth's most climate-sensitive biome boundaries, where the thermal limit of tree growth (Körner 2012) is shifting upward; evidence from tree rings, aerial photography, and satellite time series confirms average upward advances of ~0.4 m/year in the Alps over the last century (Evidence for 40 Years of Treeline Shift, *Forests* 2023), but this advance is spatially inconsistent and potentially decelerating
> - *Pinus cembra* (Swiss stone pine) is the dominant keystone species of the Central Alpine treeline transition zone (1900–2400 m a.s.l. in Tyrol): slow-growing, long-lived (>500 yr), ectomycorrhizal-dependent, and central to the facilitation dynamics of tree island formation; its regeneration bottleneck determines whether the treeline ecotone can advance or stagnates [[albrich_2019_climate_change_mountain_forests]]
> - The 20th-century redistribution of tree growth limitation from energy- to water-limitation [[babst_2019_redistribution]] now extends into historically cold-humid subalpine zones, making even high-elevation trees in open ecotone positions increasingly drought-vulnerable — while trees sheltered in closed-canopy stands benefit from canopy facilitation [[topographic_microclimate]]
> - Winter snow cover is declining in the Alps: thin or absent snow exposes subalpine soils to deep frost events, with superficial layers (0–10 cm) remaining continuously frozen without snow insulation, damaging fine roots and ectomycorrhizal networks of *Pinus cembra* seedlings and impairing spring recruitment (Charra-Vaskou et al. 2026, *New Phytologist* DOI:10.1111/nph.70926); seasonal snow cover explains treeline elevation better than temperature at regional scale (Körner 2021; Grünig 2023, *Sci. Total Environ.*)
> - The combination of summer drought intensification and winter snow deficit creates a dual-stressor regime that may progressively slow — or in some years reverse — the upward advance of the *Pinus cembra* ecotone, even as temperature warming continues to favour it in the long term; and the stress may be spatially structured: more severe in open treeline positions (exposed trees, high VPD) than in closed subalpine forest (canopy-buffered microclimate)

> [!info] Research gap
> - The relative contribution of summer drought vs. winter snow deficit (soil frost) to stagnation or reversal of *Pinus cembra* juvenile recruitment in the Eastern Alpine treeline ecotone is unquantified; most studies focus on either warming or drought, not their interaction with snow cover dynamics
> - Whether drought stress operates differentially between open ecotone positions (isolated tree islands, exposed to high VPD) and closed subalpine forest stands (canopy-buffered microclimate) — and whether this difference produces divergent regeneration trajectories within the same landscape — has not been tested empirically [[topographic_microclimate]]
> - Near-continuous physiological monitoring of photosynthetic activity (SIF) across the open-to-closed forest gradient at the *Pinus cembra* treeline does not exist for the Eastern Alps; UAV-based SIF has been demonstrated at a boreal site (2024, Springer) but not at Alpine treeline positions or across the ecotone gradient
> - Dendrochronological chronologies for *juvenile* (DBH < 10 cm) *Pinus cembra* individuals at the Tyrolean treeline ecotone are lacking; existing chronologies focus on adult trees, missing the most climate-sensitive recruitment cohort
> - High-resolution satellite treeline monitoring has been demonstrated for Italian mountains (Baglioni et al. 2025, *Biogeosciences* 22:4349–4366) but no analogous 40-year Landsat time series analysis exists for the Austrian/Tyrolean Alps
> - The snow cover deficit → soil frost → recruitment failure → treeline stagnation pathway has only recently been documented experimentally (Charra-Vaskou et al. 2026) but has not been connected to landscape-scale treeline dynamics or remote sensing observables; GLORIA ground monitoring provides species-cover ground truth but has not been linked to RS-derived treeline change metrics

> [!question] Research questions / Hypotheses
> - **RQ1** Does summer drought physiological stress differ systematically between open ecotone positions (isolated tree islands) and closed subalpine forest stands for *Pinus cembra*, and is this differential detectable in drone-based SIF time series and annual growth ring widths of juvenile trees?
> - **RQ2** Does reduced winter snow cover depth lead to measurable soil frost at seedling root depth, and does soil frost intensity predict *Pinus cembra* seedling recruitment failure and sapling tissue damage in the treeline ecotone?
> - **RQ3** Can 40-year Landsat SITS combined with Sentinel-2 anomaly detection and Planet high-resolution crown segmentation quantify the rate and spatial pattern of treeline ecotone advance, stagnation, and stress response across the Tyrolean Alps?
> - **RQ4** Under projected CMIP6 climate scenarios (SSP2-4.5, SSP5-8.5), do combined drought intensification and snow cover reduction predict net deceleration of the *Pinus cembra* treeline ecotone advance despite continued warming, and which topographic positions represent refugia?
> - **H1** Drought stress is systematically greater in open (exposed) treeline positions than in closed-canopy forest stands due to lack of canopy facilitation buffering of VPD and radiation extremes → detectable as reduced SIF during drought weeks and narrower annual rings in juvenile trees during negative pointer years
> - **H2** In winters with below-median snow cover depth, soil frost penetrates to critical root depth (>5–10 cm) → acute damage to *Pinus cembra* seedling fine roots and ectomycorrhizal networks → significantly reduced recruitment rates in open ecotone positions vs. facilitated microsites within tree islands
> - **H3** Compound drought-frost years produce a detectable spectral anomaly (NDVI, SIF-proxy, NBR) preferentially in open treeline positions, visible in Sentinel-2 seasonal composites within 1–2 months of the event, and the cumulative multi-year signal correlates with stagnation of ecotone advance in the 40-year Landsat record
