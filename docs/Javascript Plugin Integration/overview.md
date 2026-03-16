---
title: Overview
excerpt: Basic plugin functionality
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# Overview

Whether we are hosting your site or you are using a different host, such as Squarespace,\
integrating the sitewide consumer-facing functions of CompleteDTC couldn't be easier.

These functions are typically placed in the site's footer, and consist of the following\
elements:

1. `<script src="/lz_client/base.min.js"></script>` sets up the core environment for all\
   plugins
2. `<script src="/cp/lz_js/{plugin-specific script}"></script>` loads the plugin-specific\
   script
3. `<script type="text/javascript">{optional JSON data array}</script>` sets up the\
   configuration parameters for a plugin, if required

In cases where placement of the resulting HTML element needs to be within other elements,\
you will also need to create and specify a `<div>` in which the output will be placed.

Note that the site's Home page often has its own header and footer, so you may need to add\
the plugin code there as well.

The final CSS file for all sitewide plugins is at Administration->Stylesheets for\
Plugins->Site-wide plugin stylesheet.

There are four sitewide plugins…
