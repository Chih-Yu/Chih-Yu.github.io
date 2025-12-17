---
title: "Configuration"
date: 2020-08-14
draft: false
description: "All the configuration variables available in Congo."
summary: "Discover all the site, language and theme configurations that are available in Congo and how they can be used to customise your project."
slug: "configuration"
tags: ["config", "docs"]
---

Congo is a highly customisable theme and uses some of the latest Hugo features to simplify how it is configured.

The theme ships with a default configuration that gets you up and running with a basic blog or static website.

> Configuration files bundled with the theme are provided in TOML format as this is the default Hugo syntax. Feel free to convert your config to YAML or JSON if you wish.

The default theme configuration is documented in each file so you can freely adjust the settings to meet your needs.

## Site configuration

Standard Hugo configuration variables are respected throughout the theme, however there are some specific things that should be configured for the best experience.

The site configuration is managed through the `config/_default/hugo.toml` file. The table below outlines all the settings that the Congo takes advantage of.

Note that the variable names provided in this table use dot notation to simplify the TOML data structure (ie. `outputs.home` refers to `[outputs] home`).
