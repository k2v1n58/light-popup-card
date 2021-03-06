# Light popup card (homekit style)
Popup lovelace card with brightness slider and optional scene selection or a light switch for lights without brightness.
Can be used in combination with thomas loven browser_mod or custom pop-up card or in combination with my homekit style card: https://github.com/DBuit/Homekit-panel-card


## Configuration

### Installation instructions

Copy the .js file to your www directory and add the following to your ui-lovelace.yaml file:

```yaml
resources:
  url: /local/custom-light-popup-card.js
  type: module
```

### Main Options

| Name | Type | Default | Supported options | Description |
| -------------- | ----------- | ------------ | ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `entity` | string | **Required** | `light.kitchen` | Entity of the light |
| `icon` | string | optional | `mdi:lightbulb` | It will use customize entity icon or from the config as a fallback it used lightbulb icon |
| `scenes` | object | optional | `scenes:`  | define scenes that you can activate from the pop-up. |
| `scenesInARow` | number | optional | 3 | number of scenes that will be placed in a row under the brightness slider |
| `brightnessWidth` | string | optional | 150px | The width of the brightness slider |
| `brightnessHeight` | string | optional | 400px | The height of the brightness slider |
| `switchWidth` | string | optional | 150px | The width of the switch |
| `switchHeight` | string | optional | 400px | The height of the switch |

To show scenes in the pop-up you add `scenes:` in the config of the card follow bij multiple scenes:
```
scenes:
  - scene: scene.sceneone
    color: "#FDCA64"
    name: "first scene"
  - scene: scene.scenetwo
    color: "#FDCA64"
```
The name option within a scene is **optional**


Example configuration in lovelace-ui.yaml
```
popup_cards:
  light.beganegrond:
    title: ""
    style:
      position: fixed
      z-index: 999
      top: 0
      left: 0
      height: 100%
      width: 100%
      display: block
      align-items: center
      justify-content: center
      background: rgba(0, 0, 0, 0.8)
      flex-direction: column
      margin: 0
      "--iron-icon-fill-color": "#FFF"
    card:
      type: custom:custom-light-popup-card
      entity: light.beganegrond
      icon: mdi:led-strip
      scenesInARow: 2
      brightnessWidth: 150px
      brightnessHeight: 400px
      switchWidth: 150px
      switchHeight: 400px
      scenes:
        - scene: scene.ontspannen
          color: "#FDCA64"
          name: ontspannen
        - scene: scene.helder
          color: "#FFE7C0"
          name: helder
        - scene: scene.concentreren
          color: "#BBEEF3"
        - scene: scene.energie
          color: "#8BCBDD"
```

![Screenshot of card](https://github.com/DBuit/hass-custom-light-popup-card/blob/development/screenshot.png)
![Screenshot of card with switch](https://github.com/DBuit/hass-custom-light-popup-card/blob/development/screenshot-switch.png)

