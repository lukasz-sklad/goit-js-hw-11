# goit-js-hw-11
### Zadanie domowe nr 11

_Nauka nie zawsze jest łatwa, ale zawsze przynosi dużo nagrody_ 💪

_Podsumujmy to, co już zrobiliśmy w module 11._

_Aby się sprawdzić, upewnij się, że znasz:_

* _różnicę między protokołami HTTP i HTTPS;_
* _podstawowe metody HTTP i jak je stosować;_
* _czym jest CRUD;_
* _jak wchodzić w interakcje z backendem._
_Teraz nadszedł czas, aby wykorzystać tę wiedzę w praktyce, tworząc własną aplikację._



__Zadanie domowe №11__

* Utwórz repozytorium `goit-js-hw-11`.
* Stwórz swój projekt za pomocą [Vite](https://vitejs.dev/). Przygotowaliśmy dla Ciebie [gotową kompilację](https://github.com/goitacademy/vanilla-app-template) ze wszystkimi dodatkowymi ustawieniami projektu i zalecamy użycie właśnie jej.
* Przeczytaj zadanie i wykonaj je w edytorze kodu.
* Upewnij się, że kod jest formatowany za pomocą `Prettier` i że nie ma żadnych błędów ani ostrzeżeń w konsoli po otwarciu strony zadania na żywo.
* Przekaż pracę domową do oceny.


__Format zadania.__ Praca domowa zawiera dwa linki: do plików źródłowych oraz do strony roboczej na `GitHub Pages`.



__Zadanie — Wyszukiwanie obrazów__

Utwórz aplikację do wyszukiwania obrazów według słów kluczowych i wyświetlania ich w galerii. Zaprojektuj elementy interfejsu zgodnie z układem.


<pre>
! Skorzystaj z tego <a href="https://www.figma.com/file/m8k9NQV7qZrtYDCvxfD68B/%D0%94%D0%97-JavaScript?type=design&amp;node-id=3-1009&amp;mode=design&amp;t=eCh8cUwdfWOakuAr-0" rel="noopener noreferrer" target="_blank">wzoru</a> do stylizacji układu zadania.
</pre>

__Formularz wyszukiwania__

Formularz wyszukiwania jest zawarty w dokumencie HTML. Użytkownik będzie wprowadzał tekst w polu tekstowym do wyszukiwania, a po przesłaniu formularza nastąpi wysłanie żądania HTTP z tym tekstem.



__Żądania HTTP__



Korzystaj z publicznego API usługi [Pixabay](https://pixabay.com/api/docs/) dla backendu. Zarejestruj się, uzyskaj unikalny klucz dostępu i zapoznaj się z [dokumentacją](https://pixabay.com/api/docs/#api_search_images).

Lista parametrów ciągu żądania, które trzeba określić:

* `key` — Twój unikalny klucz dostępu do API.
* `q` — słowo do wyszukania. To, co wprowadzi użytkownik.
* `image_type` — typ obrazu. Potrzebujesz tylko zdjęć, więc ustaw wartość `photo`.
* `orientation` — orientacja zdjęcia. Ustaw wartość `horizontal`.
* `safesearch` — filtrowanie według wieku. Ustaw wartość `true`.


Odpowiedź będzie zawierać obiekt z kilkoma właściwościami, z których jedna będzie zawierać tablicę obrazów spełniających kryteria parametrów wyszukiwania.



Jeśli backend zwróci pustą tablicę, oznacza to, że nie znaleziono nic odpowiedniego. W takim przypadku należy wyświetlić komunikat z tekstem `„Sorry, there are no images matching your search query. Please try again!”` („Przepraszamy, nie ma obrazów zgodnych z wyszukiwaniem. Spróbuj ponownie!”) . Do wyświetlania komunikatów użyj biblioteki [iziToast](https://izitoast.marcelodolza.com/).



Aby dołączyć kod CSS biblioteki do projektu, należy dodać kolejny import, oprócz tego opisanego w dokumentacji.


```css
// Opisany w dokumentacji
import iziToast from "izitoast";
// Opcjonalny import stylów
import "izitoast/dist/css/iziToast.min.css";
```


Obejrzyj film demo pokazujący działanie aplikacji na tym etapie — 

<pre>
<video src="https://goitlmsstorage.b-cdn.net/234b48b7-f415-4245-802b-1746016bac0a19.mp4" preload="auto" controls="" style="width: 100%; height: auto;"></video>
</pre>


__Galeria i karty obrazów__



Element galerii (lista podobnych elementów) jest zawarty w dokumencie HTML. Należy dodawać do niego znaczniki kart obrazów po żądaniach HTTP.



Każdy obraz jest opisany przez obiekt, z którego interesują nas tylko następujące właściwości:

* `webformatURL` — link do małego obrazka, aby wyświetlić listę kart w galerii.
* `largeImageURL` — link do dużego obrazu dla okna modalnego.
* `tags` — tekst opisujący obraz. Nadaje się do atrybutu alt.
* `likes` — liczba polubień.
* `views` — liczba wyświetleń.
* `comments` — liczba komentarzy.
* `downloads` — liczba pobrań.


Przed wyszukaniem nowego słowa kluczowego należy całkowicie oczyszczać zawartość galerii, aby nie mieszać wyników zapytań.

Obejrzyj film demo pokazujący działanie aplikacji na tym etapie — 


<video src="https://goitlmsstorage.b-cdn.net/5c24cb91-7b4c-4912-a1f4-c4a6dd6bf92920.mp4" preload="auto" controls="" style="width: 100%; height: auto;"></video>



Biblioteka `SimpleLightbox`



Dodaj wyświetlanie dużej wersji obrazu za pomocą biblioteki [SimpleLightbox](https://simplelightbox.com/), aby utworzyć pełnoprawną galerię.



Aby dołączyć kod CSS biblioteki do projektu, należy dodać jeszcze jeden import, oprócz tego opisanego w dokumentacji.


```javascript
// Opisany w dokumentacji
import SimpleLightbox from "simplelightbox";
// Opcjonalny import stylów
import "simplelightbox/dist/simple-lightbox.min.css";
```


* W znacznikach należy zawinąć każdą kartę obrazu w link, jak opisano w dokumentacji w [sekcji Markup](https://github.com/andreknieriem/simplelightbox#markup).
* Biblioteka zawiera metodę `[refresh()](<https://github.com/andreknieriem/simplelightbox#public-methods>)`, która musi być wywoływana przy każdym dodaniu nowych elementów do galerii.


Obejrzyj film demo pokazujący działanie aplikacji na tym etapie — 


<video src="https://goitlmsstorage.b-cdn.net/b35d5472-fe97-42b8-8264-a0f12e463dc821.mp4" preload="auto" controls="" style="width: 100%; height: auto;"></video>


__Wskaźnik pobierania__

Dodaj element, który informuje użytkownika, że trwa proces pobierania obrazów z backendu. Wskaźnik pobierania powinien pojawić się tuż przed rozpoczęciem żądania HTTP i zniknąć po jego zakończeniu.

Obejrzyj film demo pokazujący działanie aplikacji na tym etapie — 


<video src="https://goitlmsstorage.b-cdn.net/7cc20db1-f940-4252-9a69-9e837b5ec46c22.mp4" preload="auto" controls="" style="width: 100%; height: auto;"></video>


Zamiast zwykłego tekstu, jak zostało to pokazane w filmie demo, można użyć biblioteki z dobrymi wskaźnikami pobierania, takiej jak [css-loader](https://github.com/vineethtrv/css-loader). Wideotutorial na temat korzystania z tej biblioteki jest dostępny w [README.md](http://readme.md/) ich repozytorium.



Na co będzie zwracał uwagę mentor podczas sprawdzania pracy:

* Praca domowa zawiera dwa linki: do plików źródłowych i do żywej strony na `GitHub Pages`.
* Projekt został zrealizowany z pomocą [Vite](https://vitejs.dev/).
* Konsola w narzędziach deweloperskich nie zawiera błędów, ostrzeżeń i konsoli logów.
* Biblioteki iziToast, SimpleLightbox i css-loader są podłączone do projektu.
* Elementy na stronie są stylizowane zgodnie z układem (lub własnymi stylami).
* Strona ma formularz wyszukiwania obrazów według wyszukiwanego słowa.
* Po przesłaniu formularza przed wysłaniem żądania do backendu pojawia się wskaźnik pobierania z css-loadera, a poprzednie wyniki wyszukiwania na stronie są usuwane.
* Po przesłaniu formularza do backendu zostaje wysłane żądanie według słowa kluczowego w celu wyszukania obrazów ze wszystkimi parametrami określonymi w zadaniu domowym.
* Po otrzymaniu odpowiedzi z backendu wskaźnik pobierania znika, a obrazy są wyświetlane na stronie na podstawie danych otrzymanych z backendu. Lub pojawia się komunikat, że nie znaleziono odpowiednich wyników.
* Nowe obrazy są dodawane do DOM podczas jednej operacji.
* Po dodaniu nowych elementów do listy obrazów w instancji SimpleLightbox wywoływana jest metoda `refresh()`.
* Po kliknięciu małego obrazka w galerii jego powiększona wersja otwiera się w oknie modalnym przy użyciu biblioteki SimpleLightbox.
* Podczas wykonywania żądań HTTP, używane są metody `then()` i `catch()` aby poradzić sobie z możliwymi błędami i zapobiec awarii strony.

https://lukasz-sklad.github.io/goit-js-hw-11/