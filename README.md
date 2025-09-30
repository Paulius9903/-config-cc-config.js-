Fotografas AM

Consent Manager Installation Instructions

1. Extract the contents of this zip file
2. Place the files in your website directory
3. Add the following code to your HTML page, inside the <head> tag:

<link rel="stylesheet" id="silktide-consent-manager-css" href="path-to-css/silktide-consent-manager.css">
<script src="path-to-js/silktide-consent-manager.js"></script>
<script>
silktideCookieBannerManager.updateCookieBannerConfig({
  background: {
    showBackground: true
  },
  cookieIcon: {
    position: "bottomLeft"
  },
  cookieTypes: [
    {
      id: "privalomi",
      name: "Privalomi",
      description: "<p>Šie slapukai yra būtini tinklalapio tinkamam veikimui ir negali būti išjungti. Jie padeda atlikti tokias užduotis kaip prisijungimas ir privatumo nustatymų konfigūravimas.</p>",
      required: true,
      onAccept: function() {
        console.log('Add logic for the required Privalomi here');
      }
    },
    {
      id: "analitiniai",
      name: "Analitiniai",
      description: "<p>Šie slapukai padeda mums tobulinti svetainę, stebėdami, kurios puslapiai yra populiariausi ir kaip lankytojai naršo svetainėje.</p>",
      required: false,
      onAccept: function() {
        gtag('consent', 'update', {
          analytics_storage: 'granted',
        });
        dataLayer.push({
          'event': 'consent_accepted_analitiniai',
        });
      },
      onReject: function() {
        gtag('consent', 'update', {
          analytics_storage: 'denied',
        });
      }
    },
    {
      id: "rinkodara",
      name: "Rinkodara",
      description: "<p>Šie slapukai suteikia papildomų funkcijų ir personalizavimo galimybių, kad pagerintų jūsų patirtį.&nbsp;</p>",
      required: false,
      onAccept: function() {
        gtag('consent', 'update', {
          ad_storage: 'granted',
          ad_user_data: 'granted',
          ad_personalization: 'granted',
        });
        dataLayer.push({
          'event': 'consent_accepted_rinkodara',
        });
      },
      onReject: function() {
        gtag('consent', 'update', {
          ad_storage: 'denied',
          ad_user_data: 'denied',
          ad_personalization: 'denied',
        });
      }
    }
  ],
  text: {
    banner: {
      description: "<p>Mūsų svetainėje naudojame slapukus, kad pagerintume jūsų kaip vartotojo patirtį, pateiktume individualizuotą turinį ir analizuotume mūsų svetainės lankomumą. Slapukų politika.</p>",
      acceptAllButtonText: "Sutikti",
      acceptAllButtonAccessibleLabel: "Priimti visus",
      rejectNonEssentialButtonText: "Atmesti",
      rejectNonEssentialButtonAccessibleLabel: "Atmesti visus",
      preferencesButtonText: "Pasirinkimai",
      preferencesButtonAccessibleLabel: "Keisti pasirinkimus"
    },
    preferences: {
      title: "Pritaikyti slapukų nustatymus",
      description: "<p>Mes gerbiame jūsų teisę į privatumą. Galite nuspręsti neleisti naudoti tam tikrų tipų slapukų. Jūsų slapukų nustatymai bus taikomi visoje mūsų svetainėje.</p>",
      creditLinkText: "Get this banner for free",
      creditLinkAccessibleLabel: "Get this banner for free"
    }
  },
  position: {
    banner: "center"
  }
});
</script>
