---
layout: page
title: "IHC Light"
description: "Instructions on how to integrate IHC lights within Home Assistant."
date: 2017-11-27 13:35
sidebar: true
comments: false
sharing: true
footer: true
logo: ihc.png
ha_category: Light
ha_release: 0.62
ha_iot_class: "Local Push"
---

Before you can use the IHC Light platform, you must setup the
[IHC Component](/components/ihc/)

When auto setup is enabled the following products will be found in the IHC
project and setup as light devices:

- Wireless lamp outlet dimmer
- Wireless dimmer
- Wireless combi dimmer 4 buttons
- Wireless lamp outlet relay
- Wireless combi relay 4 buttons
- Wireless mobile dimmer
- Dataline lamp outlet

To manually configure IHC lights insert the "light" section in 
your IHC configuration:

```yaml
ihc:
  - url: 'http://192.168.1.3'
    username: YOUR_USERNAME2
    password: YOUR_PASSWORD2
    info: true 
    light:
      - id: 12345
        name: tablelight
      - id: 23432
```

{% configuration %}
light:
  description: List of lights to setup manually
  required: false
  type: map
  keys:
    dimmable:
      description: Set to True if the IHC resource is a light level.
      required: false
      type: boolean
      default: false
    id:
      description: The IHC resource id.
      required: true
      type: integer
    name:
      description: The name of the component
      required: false
      type: string
    note:
      description: Descriptive note.
      required: false
      type: string
    position:
      description: Where it is placed.
      required: false
      type: string
{% endconfiguration %}

In the example above 12345 is ihc resource id and "tablelight" is the name.
The IHC resource id can be a light level for dimmers or a boolean output of a
relay. For more information about IHC resource ids see
[Manual Setup](/components/ihc/#manual-setup).
