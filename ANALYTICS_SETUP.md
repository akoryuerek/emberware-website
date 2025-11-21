# Analytics & SEO Setup Guide

Diese Anleitung hilft dir, Google Search Console und Microsoft Clarity für www.emberware.de einzurichten.

## 1. Google Search Console

### Schritt 1: Property hinzufügen
1. Gehe zu https://search.google.com/search-console
2. Klicke auf "Property hinzufügen"
3. Wähle "URL-Präfix" und gib ein: `https://www.emberware.de`

### Schritt 2: Inhaberschaft bestätigen
Du hast 2 Optionen:

**Option A: Meta-Tag Methode (einfacher)**
1. Wähle "HTML-Tag" in der Search Console
2. Kopiere den Verification-Code (z.B. `abcd1234efgh5678`)
3. Öffne `index.html` und ersetze Zeile 17:
   ```html
   <!-- <meta name="google-site-verification" content="YOUR_VERIFICATION_CODE"> -->
   ```
   mit:
   ```html
   <meta name="google-site-verification" content="abcd1234efgh5678">
   ```
4. Committe und pushe: `git add . && git commit -m "feat: Add Google Search Console verification" && git push`
5. Warte 30 Sekunden für Azure-Deployment
6. Klicke in Search Console auf "Bestätigen"

**Option B: HTML-Datei (Alternative)**
1. Lade die Verification-Datei herunter (z.B. `googleXXXXXX.html`)
2. Kopiere sie in das Website-Verzeichnis
3. Committe und pushe
4. Klicke auf "Bestätigen"

### Schritt 3: Sitemap einreichen
1. Nach erfolgreicher Verifizierung gehe zu "Sitemaps"
2. Gib ein: `sitemap.xml`
3. Klicke auf "Senden"
4. Die Sitemap wird innerhalb von 24-48 Stunden indiziert

## 2. Microsoft Clarity (Analytics)

### Vorteile von Clarity:
- ✅ **100% kostenlos** (keine Limits)
- ✅ **DSGVO-konform** (keine Cookies, keine Einwilligung nötig)
- ✅ **Heatmaps & Session Replays** inklusive
- ✅ **Bessere Nutzer-Insights** als Google Analytics

### Setup:
1. Gehe zu https://clarity.microsoft.com/
2. Melde dich mit Microsoft-Account an (kostenlos)
3. Klicke auf "Add new project"
4. Gib ein:
   - **Name:** Emberware Website
   - **Website:** https://www.emberware.de
5. Kopiere die **Projekt-ID** (z.B. `abc123def456`)
6. Öffne `index.html` und ersetze Zeilen 201-210:
   ```html
   <!-- Microsoft Clarity Analytics (DSGVO-konform) -->
   <script type="text/javascript">
     (function(c,l,a,r,i,t,y){
         c[a]=c[a]||function(){(c[a].q=c[a].q||[]).push(arguments)};
         t=l.createElement(r);t.async=1;t.src="https://www.clarity.ms/tag/"+i;
         y=l.getElementsByTagName(r)[0];y.parentNode.insertBefore(t,y);
     })(window, document, "clarity", "script", "abc123def456");
   </script>
   ```
7. Committe und pushe: `git add . && git commit -m "feat: Add Microsoft Clarity tracking" && git push`
8. Warte 5 Minuten - dann siehst du erste Daten in Clarity Dashboard

## 3. Datenschutzhinweis

**Microsoft Clarity ist DSGVO-konform:**
- Keine Cookies gesetzt
- Keine personenbezogenen Daten erfasst
- IP-Adressen werden anonymisiert
- **ABER:** Du solltest trotzdem einen Hinweis in `datenschutz.html` hinzufügen

### Zu ergänzen in datenschutz.html:

Füge in Abschnitt "4. Webanalyse" hinzu:

```html
<h3 class="text-xl font-semibold mb-4 text-cyber-500">4. Webanalyse mit Microsoft Clarity</h3>
<p class="mb-4">
  Wir nutzen Microsoft Clarity zur Verbesserung der Nutzerfreundlichkeit unserer Website.
  Clarity erfasst anonymisierte Nutzungsdaten (Klicks, Scrollverhalten, Verweildauer) ohne
  Verwendung von Cookies. IP-Adressen werden anonymisiert und nicht gespeichert.
</p>
<p class="mb-4">
  <strong>Rechtsgrundlage:</strong> Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse).<br>
  <strong>Datenempfänger:</strong> Microsoft Corporation, USA (EU-Standardvertragsklauseln).<br>
  <strong>Weitere Informationen:</strong> <a href="https://privacy.microsoft.com/de-de/privacystatement" target="_blank" class="text-cyber-400 hover:underline">Microsoft Privacy Statement</a>
</p>
```

## 4. Nächste Schritte

Nach erfolgreicher Einrichtung:
- ✅ Überprüfe nach 24h die Indexierung in Google Search Console
- ✅ Schaue dir Heatmaps und Session Replays in Clarity an
- ✅ Optimiere basierend auf Nutzerverhalten

## Support

Bei Fragen:
- Google Search Console: https://support.google.com/webmasters
- Microsoft Clarity: https://docs.microsoft.com/en-us/clarity/
