# Conceptual framework and data

This chapter describes the data and the conceptual framework utilized in
the following chapters. This research uses the ERA5 dataset as the
primary data source and also employs experimental data. Finally, the
software used in @sec-tehuantepec is introduced.

## Data and study area

The different approaches covered in this thesis require the manipulation
of diverse meteorological variables proven from distinct sources of
information, such as the ERA5 [@ERA5] reanalysis and actual data from
the "Atlas Eolico Mexicano" (AEM) project [@ineelAtlasEolicoMexicano].
These sources also have different time resolutions, with the lowest
resolution being hourly and the highest in the order of milliseconds.
The time resolution has been selected according to the specific problem
analyzed, and its details are thoroughly presented in the methodology
section of each of the following chapters. Data is summarized in Table
[\[tab: data\]](#tab: data){reference-type="ref" reference="tab: data"},
and the application areas are shown in Figure
[1](#fig: study_area){reference-type="ref" reference="fig: study_area"}.

![Areas of application of the topics in this thesis. Points
indicate the location of the towers from the AEM, used on @sec-enhancing_frequency. The Yucatan Peninsula and the Gulf of
Tehuantepec areas are analyzed in @sec-yucatan and @sec-tehuantepec, respectively.](tesis_diego//Tesis-UNAM-master//images/study_area_thesis.pdf){#fig-study_area}

### Experimental data {#sub: aem}

The "Atlas Eolico Mexicano" (AEM) [@ineelAtlasEolicoMexicano] project
provides data at seven sites nationwide with a 10-minute resolution. The
locations are shown in Figure [1](#fig: study_area){reference-type="ref"
reference="fig: study_area"} and specified in Table
[1](#tab: sites){reference-type="ref" reference="tab: sites"}. The
measurements were taken from sensors at 80 m above ground level. For
this research, we used data from 2018.

::: {#tab: sites}
  ------ ------------------------- ----------- ---------- -----------
  Site   Location                    Longitude   Latitude   Time Zone
                                                          
  M01    La Rumorosa, B. C.            -116.11      32.48   UTC-08:00
  M02    Merida, Yuc.                   -89.78      21.14   UTC-06:00
  M03    Cd. Cuauhtémoc, Chih.         -106.95      29.02   UTC-06:00
  M04    CERTE, La Ventosa, Oax.        -94.95      16.55   UTC-06:00
  M05    Ojuelos, Jal.                 -101.71      21.67   UTC-06:00
  M06    San Fernando, Tamps.           -98.09      25.02   UTC-06:00
  M07    Tepexi, Pue.                   -97.94      18.59   UTC-06:00
  ------ ------------------------- ----------- ---------- -----------

  : AEM Meteorological Tower Site Locations [@ineelAtlasEolicoMexicano].
:::

### Reanalysis dataset

Wind energy applications require reliable data sources that provide
extensive temporal and regional descriptions of wind resources and other
meteorological variables. Reanalysis datasets serve this purpose by
offering long-term, consistent records of atmospheric conditions. A
reanalysis is defined as "the process whereby an unchanging data
assimilation system is used to provide a consistent reprocessing of
meteorological observations, typically spanning an extended segment of
the historical data record" [@MERRA2].

Reanalysis data offers several advantages as a research tool
[@reanalysis]. These datasets provide consistent spatial and temporal
resolution over multiple decades, along with hundreds of meteorological
variables that have continuously improved in model resolution and bias
correction. Additionally, reanalysis integrates millions of observations
into a stable data assimilation system, enabling the study of complex
climate processes that would otherwise be difficult to analyze
individually. Despite the large file sizes, these datasets are
relatively easy to process, making them widely accessible for various
applications.

This thesis utilizes the ERA5 dataset [@ERA5], produced by the European
Centre for Medium-Range Weather Forecasts (ECMWF). ERA5 provides global
coverage at a spatial resolution of 0.25$^\circ$ x 0.25$^\circ$,
approximately 31 km at the equator, and an hourly temporal resolution,
spanning several decades from 1940 to the present. The dataset is
generated through 4D-Var data assimilation, a technique that combines
historical observations including satellite data, weather station
measurements, and ocean buoy records with advanced atmospheric modeling
to produce high-quality meteorological data.

## Concepts

### Atmospheric boundary layer {#sub: abl}

The atmospheric boundary layer (ABL) is the lowest part of the
atmosphere, where wind speed is influenced by surface roughness and
atmospheric stability. Over the ocean, the ABL is also affected by the
wave momentum flux [@coeff; @manwell].

For wind energy applications, it is crucial to have wind speed data at
the turbine's hub height. When such data is unavailable, vertical
extrapolation is used to estimate wind speeds at the required height.
The power-law profile is an empirical model for the vertical wind speed
profile used to extrapolate the wind speeds, is defined as:
$$\frac{U(z)}{U(z_r)} = \bigg(\frac{z}{z_r}\bigg)^\alpha
\label{eq: power_law}$$

where $U(z)$ is the wind speed at height $z$, $U(z_r)$ is the reference
wind speed at height $z_r$, and $\alpha$ is the power-law exponent. The
exponent $\alpha$ usually has a value of 1/7 but, it depends on
atmospheric stability and surface roughness [@neutral_abl].

### Power curve {#sub: power_curve}

The power curve is a fundamental characteristic of a wind turbine,
representing the relationship between wind speed and power output. As
shown in Figure [2](#fig: power_curve){reference-type="ref"
reference="fig: power_curve"}, a typical power curve identifies three
critical wind speeds:

-   **Cut-in wind speed**: The minimum wind speed at which the turbine
    begins generating power.

-   **Rated wind speed**: The wind speed at which the turbine reaches
    its maximum nominal power output.

-   **Cut-out wind speed**: The wind speed at which the turbine shuts
    down to prevent damage.

![Power curve for a typical wind turbine, highlighting cut-in, rated,
and cut-out wind speeds.](images/power_c.pdf){#fig: power_curve}

The power curve, provided by the manufacturer, is used to estimate
energy production by evaluating wind speeds against the curve. However,
this estimation is idealized, as it does not account for mechanical or
electrical losses that occur in real-world conditions [@wind_turbine].

### Annual energy production {#sub: aep}

The annual energy production (AEP) of a wind turbine is the total
electrical energy generated over one year. It is calculated by summing
the power output, evaluated using the power curve $P(U)$, over the total
hours on a year: $$AEP = \sum_{t=1}^{N} P(U) \triangle t
\label{eq: aep}$$

where $N$ is the number of wind speed observations and $\triangle t$ is
the time interval. This estimation does not account for losses such as
transmission inefficiencies, wake effects in wind farms, or maintenance
downtime.

### Capacity factor {#sub: cf}

The capacity factor (CF) measures the turbine's actual power output
relative to its maximum potential output over a given period. It is
calculated as:
$$CF = \frac{AEP}{(\text{Nominal power}) \times (\text{Time})}
\label{eq: cf}$$

The CF is a measure of the performance of a wind turbine or wind farm at
a specific location, a 100% value indicates that the turbine is
producing its maximum power output over a given period. However, this is
an idealized assumption, as wind speeds naturally fluctuate.

### Estimation of solar production {#sub: solar_production}

The power output $P_{out}$ of a PV module with a rated power, $P_N$, a
power temperature coefficient, $\gamma$ and a rate coefficient $c_1$ is
calculated as:

$$P_{out} = \frac{G_t}{G_{STC}} \cdot P_N \cdot c_1 \left[1 + \frac{\gamma}{100}(T_{PV} - T_{STC})\right],
\label{eq: solar_power}$$

where $G_t$ and $G_{STC}$ are the solar irradiances at the site and
standard test conditions (STC), respectively, and
$T_{STC} = 25^\circ C$. The PV module temperature $T_{PV}$ is calculated
as:

$$T_{PV} = T_a + G_t \cdot \frac{T_{PV, TETC} - T_{a, TETC}}{G_{TETC}}
\label{eq: temp_panel}$$

where $T_a$ is the ambient temperature, $T_{PV, TETC} = 47^\circ C$ and
$T_{a, TETC} = 20^\circ C$ are the module and ambient temperatures at
Temperature Estimation Test Condition (TETC), and $G_{TETC} = 800 W/m^2$
is the irradiance at TETC.

### Damage equivalent load {#sub: del}

The damage equivalent load (DEL) represents a simplified measure of
fatigue damage by converting varying load cycles into an equivalent
constant amplitude load [@grieve2022; @lee2005fatigue]. This allows to
quantify the fatigue loads experienced by a wind turbine by external
conditions such as wind and waves.

The ${DEL}_{M_{dir_{p}}}$ is the total damage equivalent load for all
events in wind direction *p* during 25 years, a typical lifetime for a
turbine, is defined as:

$$\text{DEL}_{M_{dir_{p}}} = \left( \sum_r P_r \left(\sum_i \frac{n_i M_i^k}{T_{sim}}\right) \right)^{1/k}$$

where:

-   $P_r$ is the probability of occurrence of a load case $r$,
    representing a specific combination of meteorological conditions.

-   $n_i$ is the number of load cycles for the $i$-th event, obtained
    from a load time series.

-   $M_i$ is the magnitude of the load (e.g., bending moment or stress)
    for the $i$-th event.

-   $k$ is the fatigue exponent, a material property that reflects the
    sensitivity of the material to fatigue damage.

-   $T_{sim}$ is the time duration of the simulation, used to normalize
    the load cycles over the simulation period.

This formulation aggregates the fatigue contributions from all load
events, scales them by their probabilities, and computes an equivalent
constant load.

## The OpenFAST software

OpenFAST is an open-source, multi-physics simulation tool developed by
the National Renewable Energy Laboratory (NREL) to model Fatigue,
Aerodynamics, Structures, and Turbulence of wind turbines
[@openfast_documentation]. It is widely used in the wind energy industry
and academy for analyzing the performance, structural loads, and
stability of both onshore and offshore wind turbines
[@fast_gov; @tranCFDStudyCoupled2018; @hashemiAssessmentHurricaneGenerated2021; @maWindwaveInducedDynamic2014; @moratoUltimateLoadsResponse2017a; @xuExtremeLoadsAnalysis2020; @papiTechnicalChallengesFloating2022].

To achieve realistic simulations, OpenFAST employs a multi-body dynamics
approach, where each component of the wind turbine such as blades,
tower, drivetrain, and foundation is modeled as a flexible or rigid body
with defined degrees of freedom. These components interact through
aerodynamic, hydrodynamic, and structural coupling, capturing the
intricate physics of turbine operation under various conditions.
OpenFAST solves the coupled equations of motion governing a wind turbine
system by integrating these multiple physical interactions.

OpenFAST requires detailed input data to initialize a simulation,
including turbine geometry, material properties, environmental
conditions such as wind and wave characteristics, and control system
parameters. The software processes these inputs and employs advanced
numerical solvers to iteratively compute structural deformations,
aerodynamic loads, and hydrodynamic interactions over time. A schematic
representation of a wind turbine model is shown in Figure
[5](#fig: turbine_sim){reference-type="ref"
reference="fig: turbine_sim"}, highlighting the various forces acting on
its components, such as blades, hub, tower, base, and platform.

<figure id="fig: turbine_sim">
<figure id="fig: hub">
<img src="tesis_diego/Tesis-UNAM-master/images/turbine_schema.png" />
<figcaption aria-hidden="true"></figcaption>
</figure>
<figure id="fig: platform">
<img src="tesis_diego/Tesis-UNAM-master/images/tower_schema.png" />
<figcaption aria-hidden="true"></figcaption>
</figure>
<figcaption>Schematic model of a wind turbine indicates the forces
involving (a) blades, rotor, nacelle, and (b) tower, base, and platform.
Obtained from <span class="citation"
data-cites="singh2014simulation"></span>.</figcaption>
</figure>

OpenFAST employs a time-domain approach to simulate turbine responses to
environmental conditions, including wind, waves, and currents. Advanced
numerical methods ensure accuracy and stability, even for highly complex
systems like floating offshore wind turbines. Once the simulation is
completed, the results can be analyzed to assess turbine performance,
identify potential structural stresses, and optimize design
configurations. Its modular design allows users to activate or
deactivate specific components depending on their analysis objectives.

The software's modular architecture enables users to model individual
components or simulate the entire turbine system based on specific
research and design needs. OpenFAST consists of several specialized
modules, each dedicated to a specific aspect of wind turbine modeling:

-   ElastoDyn: Models the structural dynamics of the turbine, including
    blade, tower, and drivetrain deformations. It captures the
    flexibility and interactions of these components using a modal
    representation.

-   AeroDyn: Simulates the aerodynamic forces on turbine blades,
    employing Blade Element Momentum (BEM) theory or Generalized Dynamic
    Wake (GDW) methods to compute lift, drag, and moments based on wind
    inflow conditions.

-   HydroDyn: Models hydrodynamic forces acting on offshore wind turbine
    foundations, accounting for wave loads, buoyancy, and added mass
    effects. It supports both fixed-bottom and floating offshore
    platforms.

-   ServoDyn: Simulates the turbine's control and protection systems,
    including pitch control, torque control, and emergency shutdown
    mechanisms. It enables users to implement custom control strategies.

-   TurbSim: Generates realistic turbulent wind fields for OpenFAST
    simulations, capturing spatial and temporal variations in wind
    speeds.

This section outlined the data sources and study areas relevant to the
problems addressed in this thesis. The theoretical framework was also
presented, providing the basis for the analyses performed in the
following chapters, where the treatment and analysis of data are
detailed in the respective methodology sections according to each
specific objective.
