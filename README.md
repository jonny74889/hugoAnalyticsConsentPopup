# hugoAnalyticsConsentPopup
Implementation for CookieConsent3 based Analytics consent popup for Hugo

### GDPR
As hugo generates static sites you have usually less problems with cookies as there are simply none.
However once you want to use 3rd Party services or JavaScript for Google Analytics or similar features you need to deal with this.
Hugo comes out of the box with nice GDPR settings and the possibility to disable the tracking.
However if you want to enable it and give the user a choice you need to implement your own Cookie Consent logic.

Details about hugo's GDPR settings and features can be found [here][1]

As hugo is simply generating the page according to your settings there is no way to dynamically influence this. Therefore you need to come up with your own solution.

I implemented it via implementing some javascript in a partial which is used on the main page.
A partial is a kind of template you can define for HTML or JS which is repeatedly used. As this is a bit more advanced I will not cover it in more detail here.

To enable the cookieconsent button I set the googleAnalytics attribute in the config.toml but deactivated it per default as I wanted to control it via my JS.

Below an excerpt of the config.toml settings:

```
googleAnalytics = "UA-XXXXXX-3" #your GA ID
# GDPR settings
[privacy]
#   [privacy.disqus]
#     disable = false
  #   anonymizeIP = true
  [privacy.googleAnalytics]
    disable = true #Disable hugo GA logic, use theme logic
```

Once the settings are set copy or create the GDPR_Popup.html partial and paste it in the layouts/partials/ folder.
Import the partial in your base layout html file or wherever you need it. It should be always loaded on the main page, but in the end it is up to you.

To use the partial in the base of your page simply import it via `{{ partial "GDPR_Popup.html" . }}`.
