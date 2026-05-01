# Hong Kong Pedestrian-Crash Incident-Level Records 2014-2019 — Snapshot for NMTI Paper Reproducibility

This archive provides a snapshot of the Hong Kong incident-level traffic-crash
records used in the paper:

> Liao Bo, et al. (forthcoming). *Constructing and Validating a Non-Motorized
> Transport Index with Modal Integration Quality: Cross-City Evidence from
> Three Asian Megacities.* Transportation Research Part D: Transport and
> Environment.

## What is in this archive

| File | Size | Lines | Description |
|---|---|---|---|
| `hk_accidents.csv` | 21,632,105 bytes | 95,822 (1 header + 95,821 rows) | Incident-level accident records 2014-2019 with WGS84 coordinates |
| `hk_casualties.csv` | 13,856,275 bytes | 120,111 | Per-casualty records linked to accidents (severity, role of casualty, etc.) |
| `hk_vehicles.csv` | 7,727,751 bytes | 153,063 | Per-vehicle records linked to accidents |
| `CHECKSUMS.sha256` | — | — | Cryptographic integrity hashes |

Field schema for `hk_accidents.csv`:
`OBJECTID, Year, Serial_No_, Severity, District_Council_District,
Hit_and_Run, Weather, Rain, Natural_Light, Junction_Control,
Road_Classification, Vehicle_Movements, Type_of_Collision,
No__of_Vehicles_Involved, No__of_Casualties_Injured,
Grid_E, Grid_N, Date, Time, latitude, longitude`

## Data provenance — three-link chain

```
Hong Kong Transport Department (TD)
   |
   |  Freedom of Information request (lawful release under Code on
   |  Access to Information, 2011)
   v
hong-kong-districts-info / hkdatasets  (R package, MIT license, v1.0.0, Sep 2021)
   |
   |  HK1980-grid -> WGS84 coordinate conversion via the HK80 R package
   v
This archive  (snapshot 2026-04, MIT license preserved)
```

**Original source**: Hong Kong Transport Department, accessed via Freedom of
Information request and curated by the hkdatasets project at
https://github.com/hong-kong-districts-info/hkdatasets (MIT license).

**This archive's purpose** is *secondary preservation* for paper
reproducibility, not primary distribution. Users seeking the most current
data should consult:

1. The upstream `hkdatasets` repository (MIT-licensed, may be updated):
   https://github.com/hong-kong-districts-info/hkdatasets
2. Hong Kong Transport Department aggregate statistics at DATA.GOV.HK:
   https://data.gov.hk (search "Road Traffic Accident Statistics")

## License

MIT (inherited from upstream hkdatasets package). See `LICENSE.txt`.

Permitted: academic use, redistribution, modification, commercial use, with
attribution.

## How to cite

If you use this archive, please cite **both**:

1. The upstream package (primary credit):
   > hong-kong-districts-info contributors (2021). hkdatasets: A
   > collection of datasets relating to Hong Kong, with a focus on the
   > 18 districts. R package version 1.0.0.
   > https://github.com/hong-kong-districts-info/hkdatasets

2. This archive (for the specific snapshot used in the paper):
   > Liao Bo (2026). Hong Kong Pedestrian-Crash Incident-Level Records
   > 2014-2019: Snapshot for NMTI Paper Reproducibility. Zenodo.
   > [DOI inserted upon Zenodo deposit]

3. The original data custodian (Transport Department) as the underlying
   source, in your paper text:
   > "Incident-level pedestrian-crash records (2014-2019) were obtained
   > from the hkdatasets community-curated R package (MIT license),
   > which sources the data from a Freedom of Information request to
   > the Hong Kong Transport Department."

## How the data were used in the paper

- **Primary analysis** (§4.5.1, §3.6): 95,821 records geocoded to a 500-m
  analytical grid for Hong Kong, yielding 19,284 grid-year observations
  (3,214 grids × 6 years 2014-2019). Negative Binomial regression of
  pedestrian-crash counts on the NMTI composite indicator and its
  dimensional decomposition.
- **Robustness layer**: 18-district panel (108 obs) with Wild Cluster
  Bootstrap inference for ecological cross-validation.
- **Stratification**: ZINB layer reveals the MIQ -> intersection
  pedestrian-crash pathway aligned with the IIC sub-dimension's
  theoretical centrality.

Match rate to 500-m grid: 93.6% (4.4% lost due to coordinate-out-of-bounds
or grid-boundary edge cases).

## Cross-validation against Hong Kong Transport Department aggregates

(Recommended for paper SI.) Aggregate the records by district and year and
compare against the TD-published *Road Traffic Accident Statistics* annual
totals at DATA.GOV.HK; the match should be >= 99% by district-year.

## Snapshot integrity

Cryptographic hashes are listed in `CHECKSUMS.sha256`. Verify with:

```
sha256sum -c CHECKSUMS.sha256
```

## Limitations

1. Time coverage 2014-2019 only; no records 2020 onward in this snapshot.
2. Original Freedom of Information letter terms are not publicly
   redistributed alongside the data.
3. Severity classification follows the Transport Department's own coding
   (Slight / Serious / Fatal); no independent re-classification.
4. Anonymization at the level of the public record: no victim names,
   driver identifiers, or vehicle license plates. Coordinates are at the
   accident location and may, in combination with date and time,
   theoretically permit re-identification in rare scenarios; standard
   academic anonymization expectations apply.

## Snapshot date

2026-04-24 (download from upstream hkdatasets repo, master branch raw URL).
