Na początku chciałbym podziękować za możliwość przedstawienia swoich umiejętności. Zanim zaczniecie testować przeczytajcie prosze wcześniej opis który jest poniżej:

Skopiowałem wasze repo, i wdrożyłem na nim projekt z figmy.
Właściwie był to mój pierwszy projekt z użyciem nuxt-a. Miałem już jeden nuxtowy projekt na swoim koncie, ale robiłem go z członkiem zespołu, który ogarnia co nieco nuxt-a. Jak nietrudno się domyślić nie mogłem poprosić go o pomoc, dlatego opierałem się na dokumentacji. Jeśli coś zrobiłem źle to proszę o wyjaśnienie. Aby testować apkę na dev-ie/local-u trzeba w pliku nuxt.config.js:
- za komentować 3 oraz 4 linię
- od komentować 5 oraz 6 linię
- usunąć/za komentować publicPath w obiekcie 'build'
Nie trzeba tego robić i można testować apkę na lokalnie postawionym serwerze, do tego wystarczy npm run build i npm run start.

Zrobiłem projekt bez wykorzystania vuex-a, moim zdaniem vue z custom event jest tutaj w pełni wystarczające. Czytałem, że vuex odpala się w nuxt-cie z automatu po utworzeniu pliku w folderze 'store' jednak nie widziałem potrzeby, żeby go używać. Przekazuję tylko dane w prostej linii do rodzica, z którego przefiltrowany wynik pcham propsem do karuzeli. Moim zdaniem jest to bardzo logiczne.

Wykorzystałem flickity do karuzeli. Wiem, że mogłem wykorzystać dowolną inną bibliotekę, ale chciałem pokazać, że potrafię zaimplementować niereaktywną karuzelę w takim projekcie.
Po za tym może się to przydać w przyszłości, biorąc pod uwagę fakt, że na niej właśnie pracujecie.
Miałem z tym trochę problemów, ale ostatecznie działa bez zarzutów. Właśnie z tych powodów import wrzuciłem w watcha, na ilość itemów. Karuzela działa wraz ze zmianą/resetem filtrów oraz na resize.

W komponencie item zostawiłem wersję, która miałem pod wyświetlanie zdjęć na IE zanim wpadłem na to, że renderując komponent na serwerze 'window' jeszcze nie istnieje. Zostawiłem to jednak, aby pokazać jaki był zamysł, jak bym to zrobił stawiając static-a. Jest tam też za komentowany overlay który miałby ładnie odkrywać zdjęcie na hover jednak szpeci to wygląd produkt na zdjęciu. Zrobiłem to po to żeby przyrównać się trochę do projektu na figmie gdzie zdjęcie mebla jest bez tła i ma dodany gradient lub ma ciemne widoczne tło z gradientem. Tutaj otrzymuję zdjęcia z innym jaśniejszym tłem, jakie widać w projekcie.


Dodałem od siebie delikatną animację na 'X Reset filters' oraz ikonie z suwakami na itemie w karuzeli. Animację na ikonie wymyśliłem sobie inną, pierwszy i ostatni suwam miały dynamicznie przesuwać się w prawą stronę, a środkowy w lewą. Kod od tej animacji jest za komentowany, coś się już tam dzieje jednak zabrakło czasu na taki szczegół.  

Bardzo słabo wykorzystałem wasz design system. Design system mi się podoba, a dokumentacja napisana jest jasno. Od siebie dodałbym jeszcze animację, bardziej zaawansowane key-frames które by się powtarzały (manipulacja pseudo-elementami na integrację jak hover czy focus). Jednak trudno było mi uzyskać konkretne wartości z projektu za pomoca wartości z ds-a. Bez wątpienia ostatecznie doszedł bym do tego jednak zabrakło mi czasu. Wiem, że to jedno z gorszych wytłumaczeń jakim mogę sie bronić. Niestety prawda jest taka, że pracując 8h dziennie dla konkretnego pracodawcy nie zostaje zbyt wiele czasu na kodowanie po skończonej pracy. Ja w pierwszej kolejności przyłożyłem się do vue/nuxt i samego działania. Nie jestem wyjątkowo szybki, a było to moje pierwsze takie spotkanie z nuxt-em, figmą czy flickity.

Zdaję sobie sprawę, że to zadanie nie jest wykonane idealnie i że wiele muszę się jeszcze nauczyć. Wstydze się teraz za spaghetti w kodzie scss komponentu ItemsCarousel. Trochę zabrakło czasu i dobrego poznania ds-a co na pewno skróciłoby kod scss co najmneij dwukrotnie.

Jeśli macie jakiekolwiek pytania jestem do dyspozycji.

Jakub Ławniczak
jakub.lawniczk@hotmail.com