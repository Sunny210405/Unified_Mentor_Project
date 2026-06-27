# Atlantic Spain Top 50 Song Lifecycle Research Paper

## Abstract

This study converts Atlantic Recording Corporation's Spain Top 50 daily playlist snapshots into lifecycle intelligence. Instead of treating popularity as a static rank outcome, the analysis measures entry speed, peak timing, survival, churn, maturity stage, and content-attribute effects across Spanish playlist behavior.

## Data And Scope

- Source file: `Atlantic_Spain.csv`
- Raw rows: 27,800
- Cleaned analytical rows: 27,750
- Date range: 2024-05-18 to 2025-11-27
- Playlist days observed: 555
- Unique normalized song-artist pairs: 575
- Missing calendar dates inside range: 4 (2025-03-14, 2025-03-25, 2025-07-11, 2025-08-13)

## Data Validation And Normalization

Song identity was normalized by lowercasing and trimming whitespace across song and artist fields. Lifecycle calculations use one row per `date + position`, preserving the latest row when duplicate positions occur on the same date. This keeps each analytical snapshot aligned with the Top 50 structure.

Validation found 1 raw date(s) that failed the exact 50-entry rule:

| date | raw_rows | unique_positions | duplicate_positions | duplicate_song_artist | passes_50_rule |
| --- | --- | --- | --- | --- | --- |
| 01-03-2025 | 100 | 50 | 50 | 49 | False |

## Lifecycle Construction

For each normalized song-artist pair, the study computed entry date, exit date, observed playlist days, calendar span, peak position, first peak date, entry-to-peak days, average position, popularity levels, explicit flag, release form, duration, and album size. Observed days measure the number of daily snapshots in which a song appears, while calendar span measures the first-to-last appearance window.

## Key Performance Indicators

| KPI | Value | Interpretation |
|---|---:|---|
| Average days on playlist | 48.2 days | Typical playlist survival across unique songs |
| Entry-to-peak time | 10.5 days | Average maturity speed from first appearance to best rank |
| Playlist churn rate | 3.5% | Average daily replacement intensity |
| Retention stability index | 96.5% | Average day-to-day overlap of Top 50 songs |
| Explicit lifecycle score | 0.91x | Explicit average longevity divided by clean longevity |
| Single vs album longevity ratio | 1.54x | Single average longevity divided by album-track longevity |

## Lifecycle Stage Distribution

| stage | observations | share |
| --- | --- | --- |
| Mature Phase | 9326 | 0.34 |
| Decline Phase | 5988 | 0.22 |
| Peak Phase | 4861 | 0.18 |
| Growth Phase | 4655 | 0.17 |
| New Entry | 2920 | 0.11 |

The stage mix indicates how much of Spain's Top 50 inventory is being used for fresh discovery, peak holding, mid-rank durability, and decline management. New entries are intentionally separated from growth because Spain's playlist dynamics are highly sensitive to release freshness.

## Playlist Rotation And Churn

Average daily churn is 3.5%, meaning roughly 1.7 net entry-equivalent positions rotate per day. The retention stability index of 96.5% shows that the market has meaningful continuity but still rotates quickly enough to require tight release-week and post-peak planning.

Monthly rotation profile:

| month | avg_entries | avg_exits | avg_churn_rate | avg_stability |
| --- | --- | --- | --- | --- |
| 2024-05-01 | 1.54 | 1.54 | 0.03 | 0.97 |
| 2024-06-01 | 1.20 | 1.20 | 0.02 | 0.98 |
| 2024-07-01 | 1.00 | 1.00 | 0.02 | 0.98 |
| 2024-08-01 | 1.06 | 1.06 | 0.02 | 0.98 |
| 2024-09-01 | 1.33 | 1.33 | 0.03 | 0.97 |
| 2024-10-01 | 1.90 | 1.90 | 0.04 | 0.96 |
| 2024-11-01 | 1.50 | 1.50 | 0.03 | 0.97 |
| 2024-12-01 | 2.16 | 2.16 | 0.04 | 0.96 |
| 2025-01-01 | 2.03 | 2.03 | 0.04 | 0.96 |
| 2025-02-01 | 0.96 | 0.96 | 0.02 | 0.98 |
| 2025-03-01 | 2.24 | 2.24 | 0.04 | 0.95 |
| 2025-04-01 | 2.67 | 2.67 | 0.05 | 0.95 |
| 2025-05-01 | 1.71 | 1.71 | 0.03 | 0.97 |
| 2025-06-01 | 1.90 | 1.90 | 0.04 | 0.96 |
| 2025-07-01 | 1.57 | 1.57 | 0.03 | 0.97 |
| 2025-08-01 | 1.90 | 1.90 | 0.04 | 0.96 |
| 2025-09-01 | 1.50 | 1.50 | 0.03 | 0.97 |
| 2025-10-01 | 1.61 | 1.61 | 0.03 | 0.97 |
| 2025-11-01 | 3.37 | 3.37 | 0.07 | 0.93 |

## Explicit Vs Clean Lifecycle Behavior

| explicit_label | songs | avg_days | median_days | avg_time_to_peak | avg_peak_position | avg_retention_ratio | avg_popularity |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Clean | 325 | 50.23 | 13.00 | 10.64 | 22.05 | 0.91 | 71.13 |
| Explicit | 250 | 45.64 | 12.00 | 10.28 | 21.46 | 0.92 | 69.26 |

Explicit tracks averaged 45.6 observed playlist days versus 50.2 for clean tracks. The explicit lifecycle score of 0.91x suggests that explicit repertoire is not merely a short-lived novelty category in this dataset; it can mature with comparable or stronger retention when the track is already accepted by playlist listeners.

## Single Vs Album Lifecycle Behavior

| release_form | songs | avg_days | median_days | avg_time_to_peak | avg_peak_position | avg_retention_ratio | avg_popularity |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Single | 283 | 58.65 | 26.00 | 11.35 | 20.66 | 0.91 | 74.94 |
| Album | 292 | 38.15 | 7.00 | 9.64 | 22.89 | 0.92 | 65.84 |

Singles averaged 58.6 observed playlist days versus 38.1 for album tracks. The single-to-album longevity ratio of 1.54x indicates that singles have a survival advantage in Spain's Top 50 environment, supporting single-led campaign pacing and careful album-focus selection.

## Top Lifecycle Performers

| song | artist | release_form | explicit_label | entry_date | exit_date | observed_days | calendar_span_days | peak_position | entry_to_peak_days | avg_popularity |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| La Bachata | Manuel Turizo | Album | Clean | 2024-05-18 | 2025-11-19 | 538 | 551 | 11 | 229 | 85.64 |
| Columbia | Quevedo | Single | Clean | 2024-07-08 | 2025-11-02 | 463 | 483 | 1 | 2 | 89.29 |
| VAGABUNDO | Sebastian Yatra & Manuel Turizo & Beéle | Single | Clean | 2024-05-18 | 2025-10-16 | 385 | 517 | 3 | 18 | 85.26 |
| LA FALDA | Myke Towers | Album | Explicit | 2024-11-25 | 2025-11-23 | 359 | 364 | 1 | 86 | 87.05 |
| LUNA | Feid | Album | Clean | 2024-12-02 | 2025-11-27 | 357 | 361 | 2 | 41 | 90.93 |
| QLONA | KAROL G | Album | Explicit | 2024-08-19 | 2025-10-19 | 342 | 427 | 8 | 27 | 90.01 |
| Manos Rotas | DELLAFUENTE & Morad | Single | Clean | 2024-11-18 | 2025-11-23 | 329 | 371 | 1 | 12 | 77.68 |
| El Merengue | Marshmello | Album | Clean | 2024-11-04 | 2025-11-18 | 317 | 380 | 19 | 2 | 77.79 |
| POLARIS - Remix | Saiko & Feid & Quevedo | Single | Explicit | 2024-06-11 | 2025-04-20 | 312 | 314 | 1 | 1 | 84.78 |
| LALA | Myke Towers | Album | Explicit | 2024-06-29 | 2025-09-24 | 310 | 453 | 1 | 7 | 93.45 |
| BABY HELLO | Rauw Alejandro | Album | Explicit | 2024-07-09 | 2025-04-19 | 281 | 285 | 3 | 1 | 77.19 |
| MODELITO | Mora | Album | Explicit | 2024-09-09 | 2025-06-17 | 279 | 282 | 4 | 65 | 81.70 |

## Strategic Recommendations

1. Prioritize the first seven days as a separate operating window. New-entry behavior should be monitored daily because early movement determines whether marketing should intensify, hold, or pivot.
2. Treat peak timing as a maturity trigger. Songs that peak quickly but lose rank need fast creative refresh, playlist negotiation, or social amplification before the decline phase hardens.
3. Keep singles at the center of Spain release strategy. The dataset shows stronger longevity for singles than album tracks, so album campaigns should identify only the most retention-capable focus tracks for playlist pushes.
4. Do not automatically soften explicit repertoire assumptions. Explicit tracks show durable lifecycle behavior in this data and should be evaluated by retention and peak behavior rather than maturity concerns alone.
5. Use churn to time follow-up actions. Higher-churn months require more aggressive entry support and shorter optimization cycles; lower-churn months reward sustained catalog and mid-rank maintenance.

## Limitations

The dataset does not include true release dates, stream counts, playlist add source, listener demographics, paid media spend, or off-platform social signals. "Freshness" is therefore measured as first observed playlist appearance, not actual market release age. One raw date contains duplicate position snapshots and four calendar dates are absent from the observed span, so cleaned lifecycle metrics should be interpreted as playlist-observed behavior rather than exhaustive market behavior.

## Conclusion

Spain's Top 50 behavior can be managed as a lifecycle system: entry, growth, peak, maturity, and decline. The analysis gives Atlantic Spain-specific signals for release timing, marketing intensity, catalog balance, explicit-content planning, and single-versus-album prioritization, avoiding direct copyover from US or UK playlist assumptions.
