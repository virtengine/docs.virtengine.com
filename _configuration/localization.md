---
title: Localization
order: 7
requirements:
  build: VirtEngine
  plan: public
---

English locale is enabled by default. Contribution is welcome for other locales.

---

### Copy the client.en.yml to the new language

Lets say we want to localize to `french`

1. Copy the */usr/share/detio/virtenginenilavu/config/client.en.yml* to */usr/share/detio/virtenginenilavu/config/client.fr.yml*

2. Copy the */usr/share/detio/virtenginenilavu/config/server.en.yml* to */usr/share/detio/virtenginenilavu/config/server.fr.yml*

3. Localize the text in the above files  */usr/share/detio/virtenginenilavu/config/client.fr.yml*

### Change the text in the site_settings

Localize the text in `/var/lib/detio/site_settings.yaml`

### Change the default_locale in site_settings

```yaml

basic:
  default_locale:
    default: 'fr'

```


### Restart VirtEngine

```bash

sv stop unicorn

sv start unicorn

```

### Let us know

If you run into any issues feel free to get in touch via our community  [forum](http://forums.virtengine.com){: target="_blank"}.
