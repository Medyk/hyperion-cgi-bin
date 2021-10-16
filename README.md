# hyperion-cgi-bin
Hyperion service control

Simple remote control for Hyperion service via cgi-bin. Used for HomeAssistant integration.
Required `jq` library for JSON response.


Example automations (turn on/off Hyperion on Xbox Series X on/off)

```
alias: Hyperion ON
description: ''
trigger:
  - platform: state
    entity_id: media_player.xsx
    from: 'off'
    to: 'on'
  - platform: state
    entity_id: media_player.xsx
    from: 'off'
    to: playing
  - platform: state
    entity_id: media_player.xsx
    from: 'off'
    to: paused
condition: []
action:
  - service: switch.turn_on
    target:
      entity_id: switch.hyperion
mode: single
```

```
alias: Hyperion OFF
description: ''
trigger:
  - platform: state
    entity_id: media_player.xsx
    from: 'on'
    to: 'off'
  - platform: state
    entity_id: media_player.xsx
    from: playing
    to: 'off'
  - platform: state
    entity_id: media_player.xsx
    from: paused
    to: 'off'
condition: []
action:
  - service: switch.turn_off
    target:
      entity_id: switch.hyperion
mode: single
```