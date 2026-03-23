# energy spot prices
If you want to make smart decisions regarding electricity prices one needs to know the actual electricity price.

## Nord Pool
The Nord Pool flow fetches the electricity price for today and tomorrow. Additionally, it identifies the 50% most expensive timeslots for today as well as the cheapest timeslot of the day. All being saved as global context variables.

Before starting, update the "Set Nord Pool parameters" node. This node contains the area of interest and the duration of timeslots (15, 30, or 60 minutes). The area of interest can be any of the following:
EE,LT,LV,AT,BE,FR,GER,NL,PL,DK1,DK2,FI,NO1,NO2,NO3,NO4,NO5,SE1,SE2,SE3,SE4,BG,TEL
![Nord Pool flow](/images/Nord%20Pool.gif)

## EPEX Energy price 
Plain energy prices from EPEX can be obtained via [energy-charts.info](https://energy-charts.info) in EUR/MWh

More information on the api can be found here: [https://api.energy-charts.info/#/prices](https://api.energy-charts.info/#/prices)
This node-red flow can be easily adjusted to any of the countries below by replacing NL to the corresponding country code in the http request node

- AT (Austria)
- BE (Belgium)
- CH (Switzerland)
- CZ (Czech Republic)
- DE-LU (Germany, Luxembourg)
- DE-AT-LU (Germany, Austria, Luxembourg)
- DK1 (Denmark 1)
- DK2 (Denmark 2)
- FR (France)
- HU (Hungary)
- IT-North (Italy North)
- NL (Netherlands)
- NO2 (Norway 2)
- PL (Poland)
- SE4 (Sweden 4)
- SI (Slovenia) 
![energy-charts.info flow](/images/energy-charts.info.gif)

## Frank energie
Frank energie is a energy provider in The Netherlands and Belgium. In The Netherlands the total energy price for consumers is a sum of the following:
- EPEX price + VAT
- Additional energy tax for 2025 it is € 0,10154 (ex VAT) or €0,1286 (inc VAT) for households [belastingdienst](https://www.belastingdienst.nl/wps/wcm/connect/bldcontentnl/belastingdienst/zakelijk/overige_belastingen/belastingen_op_milieugrondslag/energiebelasting/)
- Fee energy provider

Even though EPEX prices changes every 15min, Frank energie applies hourly prices. The hourly price applied by Frank energie is the average of EPEX price for that hour.

Frank energie has a GraphQL api available, more details can be found through this link: [https://reversed.notion.site/Marktprijzen-API-89ce600a88ac4abe8c2ad89d3167a83e](https://reversed.notion.site/Marktprijzen-API-89ce600a88ac4abe8c2ad89d3167a83e) 
Node-red flow to request the day ahead price for Frank energie.
![Frank energie flow](/images/Frank%20energie.gif)
