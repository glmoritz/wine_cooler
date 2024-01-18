# wine_cooler
UPDATE: The hardware is working using this PID script -> https://github.com/glmoritz/tasmota_berry_pid


Control board replacement for an Electrolux Wine Cooler (https://loja.electrolux.com.br/adega-elctrolux--8-garrafas-1-porta-preta-acabamento-em-aluminio---acb08-/p?idsku=310118741&amp;utm_source=google&amp;utm_campaign=googlepla&amp;utm_medium=shopping&amp;gclid=CjwKCAjwl6OiBhA2EiwAuUwWZblqWcRMnEFmYsLsG8LWJ7mZvVhUz-GGubBmveTbVgpU_DQ_GiCKHBoC1JoQAvD_BwE)


The original control board for this wine cooler is a SH14387 board which is known to present failures during its lifespan. So, instead of ordering a new one for my broken wine cooler I decided to build my own control board using cheap aliexpress components.

The controller will be based on ESP32 Devboard C. This way I can run Tasmota in Thermostat mode and set/monitor all Cooler parameters using MQTT. Tasmota seamslessy integrates with Home Assistant, this way I will have very little work in firmware programming (just recompiling and configuring Tasmota with the correct parameters and then adding the device to Home Assistant).

Tasmota thermostat is very capable. It uses a mixed on/off PID strategy which seems to work well. Time will tell...

Board features:

- The board expects a 12V@6A input, which can be provided by a simple COTS power source.

- Controlled 12V 5A output for driving the peltier board.

- 2x Controlled 12V 200mA output for driving the cold/hot peltier fans.

- 10k NTC input for reading the built in Cooler NTC 

- DS1820 input (https://pt.aliexpress.com/item/4000895660165.html?spm=a2g0o.productlist.main.13.715dCEOXCEOXKd&algo_pvid=4737a506-6fa5-4de9-a575-1d5200c734fe&aem_p4p_detail=202304260539214864307083257520000789679&algo_exp_id=4737a506-6fa5-4de9-a575-1d5200c734fe-6&pdp_npi=3%40dis%21USD%210.94%210.85%21%21%21%21%21%40211bf3f716825127612216301d0789%2110000010464721123%21sea%21BR%21141474435&curPageLogUid=qv3l3xPca3AL&ad_pvid=202304260539214864307083257520000789679_7&ad_pvid=202304260539214864307083257520000789679_7)

This will be the Thermostat feedback sensor. The built in sensor is installed directly on peltier cell which is always colder than the cooler interior. I am planning to install the DS1820 nearer to the bottles to have a more precise temperature control.
