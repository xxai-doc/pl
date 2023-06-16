<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Część kodu strony jest open source, zapraszamy do pomocy w optymalizacji tłumaczenia.

## kod frontendowy

* [kod frontendowy](https://github.com/xxai-art/web)
* [Pakiety językowe dla całej witryny](https://github.com/xxai-art/web/tree/main/i18n)
* [Pakiety językowe dla modułów logowania](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Wielojęzyczna dokumentacja witryny](https://github.com/xxai-doc)

Front-endowy język programowania to [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , który dodaje pewne funkcje oparte na składni coffeescript, zobacz [./coffee_plus.md](./coffee_plus.md) .

## Umiędzynarodowienie stron internetowych i dokumentów

Opieraj się na następujących 3 projektach

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Sufiks to `.mdt` , możesz użyć składni podobnej do `<+ ./coffee_plus/import.js>` , aby odnieść się do plików zewnętrznych i wygenerować przecenę z sufiksem `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Tłumaczenie Markdown nie przetłumaczy kodów i linków i będzie przechowywać przetłumaczone zdania w pamięci podręcznej. Jeśli tłumaczenie zostało zmodyfikowane, ale oryginalny tekst nie został zmodyfikowany, ponowne wykonanie go nie spowoduje nadpisania modyfikacji tłumaczenia.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Pliki językowe do tłumaczenia stron internetowych generowanych przez `yaml` .
