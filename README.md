# up_banking_homeassistant
Sensors for [Home Assistant](https://www.home-assistant.io/) integration of [Up Banking](https://up.com.au/)'s API

I've made this as clean as possible for now. Custom Integration is in the pipeline, but someone feel free to beat me to it.

# Pre-requisites:

- A token retrieved from https://developer.up.com.au/#welcome

- /config/configuration.yaml containing the following code:

  - `sensor: !include sensor.yaml`

- /config/secrets.yaml containing your Personal Access Token like the example below:

  - `up_api: Bearer up:yeah:`

# Instructions: 

Copy/merge /config/sensor.yaml

That's it!
