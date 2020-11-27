https://github.com/vocart/PriceChecker/blob/master/PriceChecker.py

Nie wiem co te bibiloteki robią co tam używasz, wiec ciężko mi to wsystko sprawdzić, ale:

1) czemu masz price1 = int(bla bla), a price2 i price 3 nie? I czmeu potem masz: print(int(price1), int(price2), int(price3)) skoro już wcześniej rzutowałeś to na liczby (linijka 19).
2) Kolejność metod jest zła. Najpierw musi być price_checkerm potem send_mail i na koniec get_pass. Wynika to z faktu, że metody mają być ustawione w kolejności wywołań, czyli najpierw jest price_checker, potem on woła send_mail i send_mail woła get_pass. Jes to po to, żeby móc płynnie czytać kod od góry do dołu i nie musieć po nim skakać.


%%%%%%%%%%%%%%%%%
pozmieniałem
%%%%%%%%%%%%%%%%%



3) print('sending') powinno być w send_mail bo send_mail robi sending ;)

%%%%%%%%%%%%%%%%%
jest tu i tu żeby pokazało mi też info w shellu
%%%%%%%%%%%%%%%%%



4) Z tego można zrobić osobną metodę: int(soup.find_all(class_="value")[0].get_text()) co dostaje inta na wejściu (index) i zwraca int(soup.find_all(class_="value")[index].get_text())

%%%%%%%%%%%%%%%%%
każda strona ma inaczej ponazywane szukane klucze, czasem to jest 'class' czasem nie, a jakie mająnazwy 'valkue' to już tylko wyobraźnia ich ogranicza:D poza tym zrobiłem teraz jedną szukaną, było kilka jak by się pojawiło parę ofert na ceneo, wtedy brało nie tylko pierwszą bo ona nie koniecznie była najniższa i w shellu pokazywało mi wszystkie ceny na wszelki wypadek, mogłem zrobić w sumie funkcję żeby sprawdzał czy jakakolwiek z tych wartości jest mniejsza niż założenie ale zmodyfikowałem program, ceneo jest głupią platformą do tego, na razie zostanie jako przykład:p
%%%%%%%%%%%%%%%%%



5) get_pass() - dorze by było mieć tu ogarnięte szyfrowanie hasła i deszyfrowanie bo teraz masz plain text.
%%%%%%%%%%%%%%%%%
z tego co widziałem i tak pobiera się elementy spoza programu żeby odszyfrować hasło, chyba niewiele to zmienia?
%%%%%%%%%%%%%%%%%


6) Z send_mail można wydzielić pod metody. Np. metoda logowania do poczty co ma linijki 40-45 i zwraca server. Dodatkow metoda co buduje msg. Ogólnie z resztą mógłby zrobić klasę do wysyłania maili co te czynności obudowuje i klasa miała by metody open(user,password), sendMail(to, topic, message) i close().  wtedy open by miało to co napisałem wcześniej. Pomyśl jak taki kod by musiał wyglądaćgdybyś chciał wysłać wiele maili, albo do większej ilosc userów tego samego. Można takze port, adres, i login trzymać takze w pliku wteyd zmiana maila nie zmienia pliku py.

%%%%%%%%%%%%%%%%%
podzieliłem i zmieniłem wyzwalanie. Musiałem dodać zmienne globalne żeby to działało przy podzieleniu kodu. Ale jak będzie wyzwalanie programu wielokrotne (np. sprawdzanie 100 cen) to za każdym razem i tak wyzeruje te zmienne i wygeneruje nowe
Wiele maili z listy - wysyłane w pętli funkcją send_mail:)
%%%%%%%%%%%%%%%%%



7) 4000 zró z tego stałą i nazwij ją, np. EXPECTED_PRICE. Bo teraz to w sumie nie wiadomo z czego wynika taka wartość, a tak to nazwałeś to, potem mógłbyś mieć plik konfiguracyjny gdzie masz np. adres do ceneo i oczekwana kwota. Potem mógłbyś mieć wiele takich plików czytać je w pętli i np. wyślesz sobie wiele maili o wszytkim co Ciebie interesuje ;) A jak poszalejesz to kod można tak zmienić, żeby mógł używać różna strony, np. także https://promoklocki.pl/ :D (Wtedy sam bym korzystał :D )

%%%%%%%%%%%%%%%%%
dobry pomysł;]
jednak przez głupie nazwy zmiennych i różne typy zmiennych na stronach trzeba by zrobić program pewnie pod daną stronę gdzie za każdym razem cena będzie miała np. klasę 'class' i nazwę 'value'. Chyba że się znajdzie wspólne cechy dla paru stron i zbierze w kupę w parę funkcji i w zależności jakie dane znajdzie na stronie to będzie odpalać te różne funkcje.
%%%%%%%%%%%%%%%%%

