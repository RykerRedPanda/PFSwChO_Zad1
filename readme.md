
# 1) (max. 20%)
**Proszę napisać program serwera (dowolny język programowania), który realizować będzie
następującą funkcjonalność:
a. po uruchomieniu kontenera, serwer pozostawia w logach informację o dacie
uruchomienia, imieniu i nazwisku autora serwera (imię i nazwisko studenta) oraz porcie
TCP, na którym serwer nasłuchuje na zgłoszenia klienta.
b. na podstawie adresu IP klienta łączącego się z serwerem, w przeglądarce powinna
zostać wyświetlona strona informująca o adresie IP klienta i na podstawie tego adresu IP,
o dacie i godzinie w jego strefie czasowej.**

Program serwera został utworzony w technologii Node.js.
Cały program znajduje się w pliku server.js, potrzebne paczki+konfiguracja w plikach package.json oraz package-lock.json


# 2) (max. 50%)
**Opracować plik Dockerfile, który pozwoli na zbudowanie obrazu kontenera realizującego
funkcjonalność opisaną w punkcie 1. Przy ocenie brane będzie sposób opracowania tego pliku
(wieloetapowe budowanie obrazu, ewentualne wykorzystanie warstwy scratch, optymalizacja pod
kątem funkcjonowania cache-a w procesie budowania, optymalizacja pod kątem zawartości i ilości
warstw, healthcheck itd ). Dockerfile powinien również zawierać informację o autorze tego pliku
(ponownie imię oraz nazwisko studenta).**

1. Dockerfile wykorzystuje oficjalny obraz Node.js w wersji 14 i ustawia port na 3000.
2. Więcej informacji zamieszone w komentarzach w Dockerfile

# 3) (max. 30%)
**Należy podać polecenia niezbędne do:**
**1. zbudowania opracowanego obrazu kontenera,**
**3. uruchomienia kontenera na podstawie zbudowanego obrazu,**
**4. sposobu uzyskania informacji, które wygenerował serwer w trakcie uruchamiana kontenera
(patrz: punkt 1a),**
**5. sprawdzenia, ile warstw posiada zbudowany obraz.**

1. 
docker build -t nodejs-server .
2. 
docker run -p 3000:3000 nodejs-server  (serwer i tak startuje po buildzie)
3. 
docker ps
znaleźć id kontenera
docker logs <id kontenera>
(oczywiście wcześniej należy wysłać zapytanie do serwera, http://localhost:3000/)
4.
docker images
znaleźć id obrazu
docker history --no-trunc <id kontenera>
