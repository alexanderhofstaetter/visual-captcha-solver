# Visual Captcha Solver

Script zur automatischen Lösung des [Visual Captchas](https://visualcaptcha.net/).

Dieses Skript deaktiviert das Captcha und ersetzt es durch einen Anmeldebutton.

![](demonstration.gif?raw=true)

Die Captcha Bilder sind ursprünglich unter [desirepath41/visualCaptcha-PHP](https://github.com/desirepath41/visualCaptcha-PHP/tree/v4.2.0/images) zu finden. Außerdem sind sie in diesem Repository.

## Installation
Das Skript muss im Browser eingebunden werden. Am einfachsten geht dies per Plugin. Für FireFox z.B.: [Custom Style Script](https://addons.mozilla.org/de/firefox/addon/custom-style-script/) oder für Chrome: [Custom JavaScript for websites](https://chrome.google.com/webstore/detail/custom-javascript-for-web/poakhlngfciodnhlhhgnaaelnpjljija). 

Dort kann das [JavaScript File](visual-captcha-solver.js) aus diesem Repository nachgeladen werden.

Im Browserplugin folgenden JavaScript Code hinzufügen.

```
$.ajax({
	url: 'https://cdn.jsdelivr.net/gh/alexanderhofstaetter/visual-captcha-solver/visual-captcha-solver.js',
	dataType: "script"
});
```

`https://cdn.jsdelivr.net/gh` dient hierbei als automatischer wrapper für Files in GitHub Repositories und fügt den passenden MIME-Type hinzu.

## Funktionsweise

Das Skript liest den Hinweis (Text) aus und wandelt ihn in einen Slug im. Dieser wird gegen ein Array abgeglichen und so das passende Bild herausgefunden. Die Bilder sind unter `https://raw.githubusercontent.com/alexanderhofstaetter/visual-captcha-solver/master/images/<filename>.png` verfügbar. Das Skript lädt dann das richtige Bild von GitHub runter, codiert die Binärdaten als BASE64 und gleicht es gegen den BASE64 String von allen auf der Seite vorhandenen Captcha-Bildern ab. Stimmen die BASE64 codierten Strings überein, handelt es sich um das gleiche Bild. Die `index`Nummer des Bildes wird dann verwendet um darauf zu klicken. Außerdem gibts noch ein paar UI Optimierungen dazu.

Mit diesem Skript soll aufgezeigt werden, dass eingsetzte Software durchaus auf Sinnhaftigkeit überprüft werden sollte.

## Copyright & License

Copyright (c) 2019 Alexander Hofstätter - Released under the [MIT license](LICENSE).