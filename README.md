# ha-nefit
Home Assistant Nefit climate component

## Installation
Install the nefit library into your virtual python environment:
```
(venv) $ pip install nefit-client
```
Create ```custom_components/climate/``` in your homeassistant config directory and copy the file ```nefit.py``` into it.

## Configuration

```
climate:
  platform: nefit
  name: Heating
  serial: 'XXXXXXXXX'
  accesskey: 'xxxxxxxxx'
  password: 'xxxxxxxxx'
  holiday_temp: 7
  holiday_duration: 31
```

If any of your secrets in the configuration is numbers only, make sure to put it between quotes (`'`) to have homeassistant parse them correctly.

## Home Presence Detection
When home presence detection is turned on the according userprofiles are written to ```nefit_hed_userprofiles.yaml```.
After that you can mark a person as home using the service:
```
- service: climate.nefit_user_home
  data:
    profile_id: userprofile0
```

and away using the service:

```
- service: climate.nefit_user_away
  data:
    profile_id: userprofile0
```