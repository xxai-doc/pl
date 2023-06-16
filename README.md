<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Zaleca się zainstalowanie najpierw nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , a następnie `direnv allow` po wejściu do katalogu ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) zostanie wykonany automatycznie po wejściu do katalogu).

Znaczenie jest następujące: chińskie tłumaczenie na japoński, koreański, angielski, angielskie na wszystkie inne języki. Jeśli chcesz obsługiwać tylko chiński i angielski, możesz po prostu napisać `zh: en` .

Znaczenie jest następujące: chińskie tłumaczenie na japoński, koreański, angielski, angielskie na wszystkie inne języki. Jeśli chcesz obsługiwać tylko chiński i angielski, możesz po prostu napisać `zh: en` .

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

### Instrukcje automatyzacji tłumaczenia dokumentów

Zobacz repozytorium kodu [xxai-art/doc](https://github.com/xxai-art/doc)

Zaleca się zainstalowanie najpierw nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , a następnie `direnv allow` po wejściu do katalogu ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) zostanie wykonany automatycznie po wejściu do katalogu).

Aby uniknąć dużej bazy kodu przetłumaczonej na setki języków, stworzyłem oddzielną bazę kodu dla każdego języka i stworzyłem organizację do przechowywania bazy kodu

Ustawienie zmiennej środowiskowej `GITHUB_ACCESS_TOKEN` , a następnie uruchomienie [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) spowoduje automatyczne utworzenie repozytorium kodu.

Oczywiście możesz również umieścić go w bazie kodu.

Odniesienie do skryptu tłumaczenia [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Kod skryptu jest interpretowany w następujący sposób:

[bunx](https://bun.sh/docs/cli/bunx) zastępuje npx, który jest szybszy. Oczywiście, jeśli nie masz zainstalowanego bun, możesz zamiast tego użyć `npx` .

`bunx mdt zh` renderuje `.mdt` w katalogu zh jako `.md` , patrz 2 połączone pliki poniżej

* [kawa_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [kawa_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` to podstawowy kod do tłumaczenia (jeśli masz zainstalowane tylko `nodejs` , ale `bun` i `direnv` nie są zainstalowane, możesz także uruchomić `npx i18n` , aby przetłumaczyć).

Przeanalizuje [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , konfiguracja `i18n.yml` w tym dokumencie jest następująca:

```
en:
zh: ja ko en
```

Znaczenie jest następujące: chińskie tłumaczenie na japoński, koreański, angielski, angielskie na wszystkie inne języki. Jeśli chcesz obsługiwać tylko chiński i angielski, możesz po prostu napisać `zh: en` .

Ostatnim jest [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , który wyodrębnia zawartość między głównym tytułem a pierwszym podtytułem pliku `README.md` każdego języka w celu wygenerowania wpisu `README.md` . Kod jest bardzo prosty, możesz sam na niego spojrzeć.

Google API służy do bezpłatnego tłumaczenia. Jeśli nie możesz uzyskać dostępu do Google, skonfiguruj i ustaw serwer proxy, taki jak:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Skrypt tłumaczenia wygeneruje przetłumaczoną pamięć podręczną w katalogu `.i18n` , sprawdź ją za pomocą `git status` i dodaj do repozytorium kodu, aby uniknąć powtarzania tłumaczeń.

Uruchom `bunx i18n` za każdym razem, gdy modyfikujesz tłumaczenie, aby zaktualizować pamięć podręczną.

Jeśli oryginalny tekst i tłumaczenie zostaną zmodyfikowane w tym samym czasie, pamięć podręczna zostanie zdezorientowana, więc jeśli chcesz zmodyfikować, możesz zmodyfikować tylko jedną, a następnie uruchomić `bunx i18n` , aby zaktualizować pamięć podręczną.
