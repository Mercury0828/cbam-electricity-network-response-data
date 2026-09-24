# Data sources

The processed data in this repository are derived from the public sources below. Raw downloads are not included;
the code repository downloads them, and `manifest/download_manifest.jsonl` lists each request. Users of the processed
data must respect the terms of the original providers and give the attributions stated here.

| Source | Used for | Terms and attribution |
|---|---|---|
| Elexon, Balancing Mechanism Reporting Service / Insights Solution (https://bmrs.elexon.co.uk) | GB generation by type (AGPT, FUELHH), Market Index Price, interconnector flows by cable (INTOUTHH), REMIT unavailability messages | Elexon terms for BMRS data. Attribution: "Contains BMRS data © Elexon Limited copyright and database right 2026." |
| Energy-Charts, Fraunhofer Institute for Solar Energy Systems ISE (https://energy-charts.info) | Continental and Serbian generation by type, day-ahead prices, cross-border physical flows | CC BY 4.0 unless Energy-Charts states otherwise for a series. Attribution: "Energy-Charts, Fraunhofer ISE." |
| Joint Allocation Office (https://www.jao.eu) | Explicit capacity auctions on the GB links and the Serbia-Hungary border (offered capacity, allocation, price) | JAO publication terms. Only derived quantities are included (offered-capacity coverage of outage hours, auction summaries). |
| Nord Pool UMM platform (https://umm.nordpoolgroup.com) | Transmission unavailability messages published under REMIT | Only message identifiers and derived confirmation flags are included. |
| European Union Agency for the Cooperation of Energy Regulators (ACER) | Daily LNG price assessments, used to derive the TTF gas price | ACER publication; reuse with acknowledgement of the source. |
| World Bank Commodity Price Data (Pink Sheet) | Monthly coal price; monthly gas price (natural gas, Europe) of the graph model | CC BY 4.0. Attribution: "World Bank Commodity Price Data." |
| European Energy Exchange (EEX), EU ETS primary auction reports | Monthly EU allowance prices of the graph model | EEX publication; not redistributed here. |
| KOBiZE (Poland) monthly EU ETS market reports; UK Department for Energy Security and Net Zero; Bank of England; European Central Bank | Monthly EU and UK allowance prices, exchange rates | Public statistics; UK government data under the Open Government Licence v3.0. |
| HM Revenue and Customs | Carbon Price Support rate | Open Government Licence v3.0. |
| Regulation (EU) 2023/956, Implementing Regulation (EU) 2025/2621, Commission CBAM certificate price notices | CBAM default values for electricity, certificate price | EU legal acts and notices, reuse under Commission Decision 2011/833/EU. |
| IPCC 2006 Guidelines; EU best-available-techniques conclusions (Implementing Decision (EU) 2021/2326) | Fuel emission factors, plant efficiency ranges | Cited values only. |

`inputs/source/` holds the public source files of the World Bank (CC BY 4.0), ACER, the ECB and the UK government (Open Government Licence v3.0) that the code reads. The EEX EU ETS primary auction reports are not redistributed; they are public downloads (one file per year) listed in the code repository.

Project-produced data (model weights, estimates, results) are released under CC BY 4.0.
