# Data: where charged electricity imports are replaced

Processed data, trained model weights and result artefacts for the paper **"Where charged electricity imports are
replaced: interconnector outages and a graph network-response model for the EU CBAM"** by Zirui Tong, Jiachen Shen
and Jian Shi (University of Houston).

Code: **https://github.com/Mercury0828/cbam-electricity-network-response**. Clone this repository into the `data/`
folder of the code repository:

```
git clone https://github.com/Mercury0828/cbam-electricity-network-response
cd cbam-electricity-network-response
git clone https://github.com/Mercury0828/cbam-electricity-network-response-data data
```

Every number in the tables and figures of the paper is read from the files below. The raw downloads are not
redistributed; the code downloads them from the original sources, and `manifest/download_manifest.jsonl` records each
request (URL, time, SHA-256, size).

## Layout

```
processed/
  *.json                        redispatch comparator, trading comparisons, fuel and carbon price inputs
                                (gnn_prices_monthly.json, fuel_monthly_*.json, carbon_monthly_2026.json)
  gnn/
    dataset_v4.npz              hourly graph dataset: 27 bidding zones, January 2019 - August 2026 (UTC)
    meta_v4.json                zone and link index of the dataset
    runs_v4/                    graph model weights: seeds 42, 123, 7, 2024, 999, and controls without
                                cross-border messages (_dropTACC)
    runs_netresp_r2_v4/         network-response layer weights, main model (seeds 42, 123, 7; _local = node-local)
    runs_netresp_r3_v4/         network-response layer weights, 24-hour-difference variant
    v4/                         prediction accuracy, local emission responses, response calibration
    netresp_r2_v4/              main model on the charged borders: per-hour responses (charged_*.npz), charged-import
                                retention (taxbase_*.npz), reference charge and rule comparison (net_rules.json,
                                net_states.json, net_taxbase.json), feasibility, information frontier
    netresp_r3_v4/              the same for the 24-hour-difference variant
    outage_*_v4.json / .npz     outage natural experiments: BritNed and Nemo Link estimates (outage_v2_v4.json),
                                model comparison, ten further HVDC links (outage_multi_*), Serbia-Hungary
                                (outage_rs_*), recovery check (outage_synthetic10_v4.json), subsets, events
    outage_events_v4.csv        every outage event with its treated hours, blocks, weights and confirming messages
                                (identifiers of the Elexon REMIT and Nord Pool UMM messages, JAO offered capacity)
    headline_numbers_v4.json    the numbers quoted in the paper, collected from the artefacts above
inputs/source/                  public price files read by the code: World Bank monthly commodity prices
                                (wb_cmo_monthly_*.xlsx), ACER LNG price assessments, ECB exchange rates, UK allowance
                                prices (DESNZ page); the EEX auction reports are not included (see the code README)
law/
  default_values.csv            CBAM default values for electricity by exporting country, with legal basis
  charged_borders.csv           exporting countries charged in 2026
manifest/
  download_manifest.jsonl       raw-data requests of the project
```

`.npz` files are NumPy archives (`numpy.load`); `.pt` files are PyTorch state dictionaries loaded by
`src/wedge/gnn/train.py` and `src/wedge/gnn/netresp.py` of the code repository.

## License

CC BY 4.0 for the data produced in this project (`LICENSE`). The processed series derive from third-party data that
remain subject to their providers' terms; `DATA_SOURCES.md` lists the sources and the required attributions.

## Citation

See `CITATION.cff`. The citation will be updated with the journal reference and the archive DOI.
