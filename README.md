# Up Banking Home Assistant
Sensors for [Home Assistant](https://www.home-assistant.io/) integration of [Up Banking](https://up.com.au/)'s API

I've made this as clean as possible for now. Custom Component is in the pipeline, but someone feel free to beat me to it.

Thanks to phnx on the Home Assistant [Discord](https://discord.gg/c5DvZ4e) for the help with the `% set parsed` assistance!
Additional thanks to [Jack465](https://github.com/Jack465) for their [PR](https://github.com/ryandanger/up_banking_homeassistant/pull/1) which prompted me to add a ton more features!

# What can I do with this?

Tons! This initial sensor.yaml config will map transactions and balances to separate sensors, so that you can do any of the following:

- Create a notification to be sent to your phone when an account goes below a certain value
- Have a dance-party of lights in your home when you have money sent to your account
- Flash lights red when money leaves your accounts
- Many, many more features! Let me know on twitter (@splatoonAU) if you have any other ways that you've implemented this!

# Features:

| Name                 | Description                          |
| -------------------- | ------------------------------------ |
| Retrieve balances    | Retrieve account balances            |
| Format balances      | Append $ to value of accounts        |
| Removal of transfers | Allows to view cleaner transactions  |
|                      |                                      |
| Recent transactions  | Retrieve 5x recent transactions      |
| Format transactions  | Append $ to value of transactions,   |
|                      | plus additional lookup values:       |
| incl.                | Date                                 |
|                      | Full Name                            |
|                      | Message                              |
|                      | Transaction Status                   |
|                      | RoundUp Amount                       |
|                      | Category/Parent Category             |
|                      | Cashback (not yet implemented in Up) |

# Pre-requisites:

- A token retrieved from https://developer.up.com.au/#welcome

- /config/configuration.yaml containing the following code:

  - `sensor: !include sensor.yaml`

- /config/secrets.yaml containing your Personal Access Token like the example below:

  - `up_api: Bearer up:yeah:`

# Instructions:

Copy/merge /config/sensor.yaml

That's it! However, do feel free to edit and configure to your liking :)

# To-Do:

- Fix recent_saving_transaction, as I'd really like to automate loud noises when a savings account is touched. This is easy to do if you replace parts of the URL to make it static, though this is potentially unsafe to store in sensor.yaml, however ymmv :)

# Cannot be added

- N/A right now!

# Recently Added:

- DONE - Fix x.xx9999999999$ from showing in Total Balance
- DONE - Work out IF statement to stop round-ups from appearing in transactions
- DONE - Work out IF statement to stop "Quick save transfer", "Transfer from X saving" and "Interest" from showing
  - The above one is a little messy. Ideally I'd like to create a dictionary at the top of the sensor to allow rejectattr to parse out anything included there, rather than having multiple rejectattr in the one line. baby steps though.
  -  It seems impossible to use wildcard values and my own dictionary with Jinja2's rejectattr, but I've done what I can to limit the lines from 72 onwards. Edit those to your leisure.
- DONE - Thanks to Jack465, we can now show dollar values at the beginning of values
- DONE - Add additional transaction details to each recent_transaction, all shown in Features above
