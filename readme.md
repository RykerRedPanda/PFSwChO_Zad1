
1) (max. 20%)
Proszę napisać program serwera (dowolny język programowania), który realizować będzie
następującą funkcjonalność:
a. po uruchomieniu kontenera, serwer pozostawia w logach informację o dacie
uruchomienia, imieniu i nazwisku autora serwera (imię i nazwisko studenta) oraz porcie
TCP, na którym serwer nasłuchuje na zgłoszenia klienta.
b. na podstawie adresu IP klienta łączącego się z serwerem, w przeglądarce powinna
zostać wyświetlona strona informująca o adresie IP klienta i na podstawie tego adresu IP,
o dacie i godzinie w jego strefie czasowej.

Program serwera został utworzony w technologii Node.js.
Cały program znajduje się w pliku server.js, potrzebne paczki+konfiguracja w plikach package.json oraz package-lock.json


2) (max. 50%)
Opracować plik Dockerfile, który pozwoli na zbudowanie obrazu kontenera realizującego
funkcjonalność opisaną w punkcie 1. Przy ocenie brane będzie sposób opracowania tego pliku
(wieloetapowe budowanie obrazu, ewentualne wykorzystanie warstwy scratch, optymalizacja pod
kątem funkcjonowania cache-a w procesie budowania, optymalizacja pod kątem zawartości i ilości
warstw, healthcheck itd ). Dockerfile powinien również zawierać informację o autorze tego pliku
(ponownie imię oraz nazwisko studenta).

Dockerfile wykorzystuje oficjalny obraz Node.js w wersji 14 i ustawia port na 3000.
Więcej informacji zamieszone w komentarzach w Dockerfile

3) (max. 30%)
Należy podać polecenia niezbędne do:
a. zbudowania opracowanego obrazu kontenera,
b. uruchomienia kontenera na podstawie zbudowanego obrazu,
c. sposobu uzyskania informacji, które wygenerował serwer w trakcie uruchamiana kontenera
(patrz: punkt 1a),
d. sprawdzenia, ile warstw posiada zbudowany obraz.

a. 
docker build -t nodejs-server .
b. 
docker run -p 3000:3000 nodejs-server  (serwer i tak startuje po buildzie)
c. 
docker ps
znaleźć id kontenera
docker logs <id kontenera>
(oczywiście wcześniej należy wysłać zapytanie do serwera, najpewniej na http://localhost:3000/)
d.
docker images
znaleźć id obrazu
docker history --no-trunc <id kontenera>