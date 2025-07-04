# Changelog – Brightwind Python Library
All notable changes to this project will be documented in this file. If you make a notable change to the project, please add a line describing the change to the "unreleased" section. The maintainers will make an effort to keep the [Github Releases](https://github.com/brightwind-dev/brightwind/releases) page up to date with this changelog. The format is based on [Semantic Versioning](https://semver.org/) e.g. '1.1.0'

Given a version number MAJOR.MINOR.PATCH, increment the:

    1. MAJOR version when you make incompatible API changes,
    2. MINOR version when you add functionality in a backwards compatible manner, and
    3. PATCH version when you make backwards compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

---


## [2.3.0]
This update brings a comprehensive set of **bug fixes** and **enhancements** across the Brightwind library. 
Key improvements include more reliable wind and solar data handling, expanded plotting capabilities (including 
colormap support and better legends), and the introduction of new functions for downloading and applying cleaning rules 
and device orientation offsets. 
Enhanced error messages and schema validation strengthen data integrity and user feedback.

### Bug Fixes
1. Fixed legend display in `plot_scatter_wspd` and `plot_scatter_wdir`, ensuring correct labeling in plots. ([#443](https://github.com/brightwind-dev/brightwind/issues/443))  
2. Corrected `is_file` usage, resolving an error when checking file existence. ([#447](https://github.com/brightwind-dev/brightwind/issues/447))  
3. Fixed bug in `_Measurements_get_table`, which affected how measurement tables were retrieved. ([#421](https://github.com/brightwind-dev/brightwind/issues/421))  
4. Made `_Measurements_get_names` public and fixed an issue with how names were retrieved. ([#450](https://github.com/brightwind-dev/brightwind/issues/450))  
5. Improved sensor calibration logic in `_Measurements__get_properties` for multi-type sensors by correctly selecting the appropriate calibration. ([#449](https://github.com/brightwind-dev/brightwind/issues/449))  
6. Fixed error for solar sites in `_Measurements__get_properties`, improving compatibility. ([#453](https://github.com/brightwind-dev/brightwind/issues/453))  
8. Improved support for solar and sodar sites in `_LoggerMainConfigs__get_properties`. ([#454](https://github.com/brightwind-dev/brightwind/issues/454))  
7. Resolved calculation issues in `dist()` function when constant values are sent as well as improved error messages. ([#459](https://github.com/brightwind-dev/brightwind/issues/459))  
9. Fixed issues in `monthly_means()`, correcting plot output and handling of missing months. ([#452](https://github.com/brightwind-dev/brightwind/issues/452), [#413](https://github.com/brightwind-dev/brightwind/issues/413))  
10. Corrected `Shear.TimeOfDay()` logic when months are missing along with improving error message and fixing plot labels. ([#441](https://github.com/brightwind-dev/brightwind/issues/441))

### New Features and Enhancements

1. Updated `monthly_means()` and `plot_monthly_means()` to improve output and visual clarity. ([#452](https://github.com/brightwind-dev/brightwind/issues/452), [#413](https://github.com/brightwind-dev/brightwind/issues/413))  
2. Enhanced `plot_timeseries()` to support more than 12 lines and introduced colormap-based coloring. ([#457](https://github.com/brightwind-dev/brightwind/issues/457), [#492](https://github.com/brightwind-dev/brightwind/issues/492))  
3. Added error feedback in `Shear`: More informative messages returned when no valid data is available. ([#205](https://github.com/brightwind-dev/brightwind/issues/205))  
4. `Shear.TimeSeries` and `TimeOfDay` now return `np.nan` for timestamps with no valid data. ([#205](https://github.com/brightwind-dev/brightwind/issues/205))  
5. Enhanced `LoadBrightHub.get_measurement_stations()` to support device type filtering and optional dictionary return format. ([#287](https://github.com/brightwind-dev/brightwind/issues/287), [#378](https://github.com/brightwind-dev/brightwind/issues/378))  
6. Added `LoadBrightHub.get_cleaning_rules()`, allowing programmatic retrieval of cleaning rules for a station. ([#461](https://github.com/brightwind-dev/brightwind/issues/461))  
7. Added `load.apply_cleaning_rules()`, enabling automated column cleaning based on BrightHub rules. ([#462](https://github.com/brightwind-dev/brightwind/issues/462))  
8. New function: `apply_device_orientation_offset()` adjusts wind direction data based on remote sensing device orientation as stated in it's data model. ([#451](https://github.com/brightwind-dev/brightwind/issues/451))  
9. Schema validation added to `MeasurementStation()`, ensuring input data matches the expected data model version. ([#489](https://github.com/brightwind-dev/brightwind/issues/489))


## [2.2.1]
1. Bug fix some users encounter with `plot.plot_shear_time_of_day()` (Issue [#429](https://github.com/brightwind-dev/brightwind/issues/429)).


## [2.2.0]
1. Modify `Correl.OrdinaryLeastSquares()` to force the intercept to pass through the origin (Issue [#412](https://github.com/brightwind-dev/brightwind/issues/412)).
1. Update `LoadBrightHub.get_data()` to use a new API (Issue [#419](https://github.com/brightwind-dev/brightwind/issues/419)).
1. Added new function `LoadBrightHub.get_cleaning_log()` to pull the cleaning log for a particular measurement station on BrightHub (Issue [#405](https://github.com/brightwind-dev/brightwind/issues/405)).
1. Added new function `LoadBrightHub.get_reanalysis()` to pull reanalysis datasets from BrightHub (Issue [#431](https://github.com/brightwind-dev/brightwind/issues/431)).
1. Modify `load.apply_cleaning()` and `apply_cleaning_windographer()` to clean columns specified in cleaning file by 
matching the sensor name from the beginning of the string. (Issue [#249](https://github.com/brightwind-dev/brightwind/issues/249)).


## [2.1.0]
1. Update behaviour of `time_continuity_gaps` to find any gap that
is not equal to the derived temporal resolution.
2. Added `data_resolution` argument to `average_data_by_period`, `monthly_means`, `coverage` and 
  `merge_datasets_by_period` functions (Issue [#297](https://github.com/brightwind-dev/brightwind/issues/297))
3. Update to work with Pandas 1.3.2. This mostly includes depreciating pd.Timedelta and using pd.DateOffset instead. (Pull request [#312](https://github.com/brightwind-dev/brightwind/pull/312)).
4. Update to work with Pandas 2.0.1, due to `date_format` input update for `pandas.to_datetime`. (Pull request [#387](https://github.com/brightwind-dev/brightwind/issues/387)).
5. Update to work with matplotlib 3.5.2 and bug fix for plot_freq_distribution and dist functions (Issue [#315](https://github.com/brightwind-dev/brightwind/issues/315)). 
6. Update to work with numpy>=1.20.0 when pandas=0.25.3. (Issue [#344](https://github.com/brightwind-dev/brightwind/issues/344)). 
7. Addressed all Future and Deprecation warnings for matplotlib<=3.6.3, numpy<=1.24.1, pandas<=1.5.3. (Issue [#356](https://github.com/brightwind-dev/brightwind/issues/356)).
8. In`Correl` fix issue when duplicate column names are sent to `SpeedSort` (Issue [#304](https://github.com/brightwind-dev/brightwind/issues/304))
9. Added subplotting functionality to `sector_ratio` and improved user control of plotting (Issue [#309](https://github.com/brightwind-dev/brightwind/issues/309))
10. Allow `dist()` function to take a pd.DataFrame so user can plot multiple distributions on the same plot. (Issue [#264](https://github.com/brightwind-dev/brightwind/issues/264))
    1. As part of this added subplotting functionality for bar plots
11. Allow `freq_table()` function to derive a seasonal adjusted frequency distribution if user sets 'seasonal_adjustment' 
to true. (Issue [#334](https://github.com/brightwind-dev/brightwind/issues/334))
    1. As part of this, added 'monthly_coverage_threshold' option for the user to ensure good coverage months. 
12. In `freq_table` added option to give as input target wind speed we want the mean frequency distribution to have 
(Issue [#269](https://github.com/brightwind-dev/brightwind/issues/269)).
13. Allow `freq_table` function to apply a `coverage_threshold` for both seasonal adjusted and base methods. (Issue [#386](https://github.com/brightwind-dev/brightwind/issues/386))
14. Updated `plot_timeseries` to use a subplot function (`_timeseries_subplot`) and added arguments _x_label_, _y_label_, _x_tick_label_angle_, 
_line_colors_, _legend_ and _figure_size_. (Issue [#349](https://github.com/brightwind-dev/brightwind/issues/349)).
15. In `average_data_by_period()` fixed issue when wind direction average is derived for a period equal to the data resolution period 
(Issue [#319](https://github.com/brightwind-dev/brightwind/issues/319)).
16. In `average_data_by_period()` fixed issue when wind direction average is derived for a period equal to the data resolution period (Issue [#319](https://github.com/brightwind-dev/brightwind/issues/319)).
17. Fixed bugs for `TI.by_speed` and `TI.by_sector` and added tests. Solved versions issue that were raised from Pandas 1.3.3. (Issue [#317](https://github.com/brightwind-dev/brightwind/issues/317)).
18. Address errors and warnings generated for `Shear.TimeOfDay` and `Shear` when pandas >=1.0.0 (Issue [#347](https://github.com/brightwind-dev/brightwind/issues/347)).
19. In `_calc_mean_speed_of_freq_tab` for `export_tab_file` fix issue around using wind speed bins less than 1 m/s (Issue [#359](https://github.com/brightwind-dev/brightwind/issues/359)).
20. Update to work with versions 1.0 to 1.2 of IEA WIND Task 43 WRA Data Model (Issue [#306](https://github.com/brightwind-dev/brightwind/issues/306)).
21. Updated `LoadBrightHub` URL and generalised functions used for connecting to BrightHub platform without using `boto3` (Issue [#355](https://github.com/brightwind-dev/brightwind/issues/355)).
22. Removed hardcoded colours for `Shear.TimeOfDay` plots when `plot_type` is 'step' or 'line' and added a colour map. (Issue [#376](https://github.com/brightwind-dev/brightwind/issues/376)).
23. Fixed bug for `SpeedSort` where the `sector_predict` function was not interpolating data using two fit lines. (Issue [#377](https://github.com/brightwind-dev/brightwind/issues/377)).
24. Updated `_ColorPalette` to automatically update color_list, color_map, color_map_cyclical and adjusted lightness color variables when main colors (primary, secondary etc.) are changed. (Issue [#381](https://github.com/brightwind-dev/brightwind/issues/381)).
25. Allow `momm` function to derive a seasonal adjusted mean of monthly mean, if user sets `seasonal_adjustment` to true, and allow to apply a `coverage_threshold` (Issue [#298](https://github.com/brightwind-dev/brightwind/issues/298))
26. Updated `slice_data`, `offset_timestamps`, `_LoadBWPlatform.get_data` functions to use 'less than' data_to if provided as input. (Issue [#385](https://github.com/brightwind-dev/brightwind/issues/385))


## [2.0.0]
- Major changes, notably
  - Incorporating the IEA WIND Task 43 WRA Data Model
  - Adding APIs to pull data from the BrightHub platform www.brightwindhub.com
  - Change license to MIT
  - Correl - add linear regression by direction sector
  - Correl - add different aggregation methods to both ref and target
  - better function to average wind directions
  - Bug fixes


## [1.0.0]
- Initial release
