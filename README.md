# Up Banking Home Assistant
Sensors for [Home Assistant](https://www.home-assistant.io/) integration of [Up Banking](https://up.com.au/)'s API

I've made this as clean as possible for now. Custom Integration is in the pipeline, but someone feel free to beat me to it.

Thanks to phnx on the Home Assistant [Discord](https://discord.gg/c5DvZ4e) for the help with the `% set parsed` assistance!

# What can I do with this?

Tons! This initial sensor.yaml config will map transactions and balances to separate sensors, so that you can do any of the following:

- Create a notification to be sent to your phone when an account goes below a certain value
- Have a dance-party of lights in your home when you have money sent to your account
- Flash lights red when money leaves your accounts
- Many, many more features! Let me know on twitter (@splatoonAU) if you have any other ways that you've implemented this!

# Pre-requisites:

- A token retrieved from https://developer.up.com.au/#welcome

- /config/configuration.yaml containing the following code:

  - `sensor: !include sensor.yaml`

- /config/secrets.yaml containing your Personal Access Token like the example below:

  - `up_api: Bearer up:yeah:`

# Instructions:

Copy/merge /config/sensor.yaml

That's it!

# To-Do

- DONE - Work out IF statement to stop "Quick save transfer", "Transfer from X saving" and "Interest" from showing
  - The above one is a little messy. Ideally I'd like to create a dictionary at the top of the sensor to allow rejectattr to parse out anything included there, rather than having multiple rejectattr in the one line. baby steps though.
  - If someone else is using this, change 'Cover from rent n bills' to whatever an account you transfer from is titled.
- Move $ to start of values, but keep total working
- DONE - Fix x.xx9999999999$ from showing in Total Balance
- DONE - Work out IF statement to stop round-ups from appearing in transactions
