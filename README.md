from abc import ABC, abstractmethod

class Ciasto(ABC):
    def __init__(self, maka, cukier, woda):
        self.maka = maka
        self.cukier = cukier
        self.woda = woda

    @abstractmethod
    def przygotuj(self):
        pass

    @abstractmethod
    def sprawdz(self):
        pass

    @abstractmethod
    def piecz(self, czas, temperatura):
        pass

    @abstractmethod
    def ocen(self):
        pass

class Szarlotka(Ciasto):
    def __init__(self, maka, cukier, woda):
        super().__init__(maka, cukier, woda)
        self._czy_upieczone = False
        self._licznik_sprawdzen = 0
        self._cynamon = False
        self.kanadski_syr = False

    def przygotuj(self):
        self._czy_upieczone = False
        self._licznik_sprawdzen = 0
        self._cynamon = False
        self.kanadski_syr = False

    def sprawdz(self):
        return self._licznik_sprawdzen >= 3

    def piecz(self, czas, temperatura):
        if 55 <= czas <= 60 and 180 <= temperatura <= 200 and self._cynamon:
            while not self.sprawdz():
                self._licznik_sprawdzen += 1
            self._czy_upieczone = True

    def ocen(self):
        return self._czy_upieczone

    def cynamon(self):
        self._cynamon = True

    def dodaj_kanadski_syr(self):
        self.kanadski_syr = True

class Sernik(Ciasto):
    def __init__(self, maka, cukier, woda):
        super().__init__(maka, cukier, woda)
        self._czy_upieczone = False
        self._licznik_sprawdzen = 0
        self._rodzynki = 0

    def przygotuj(self):
        self._czy_upieczone = False
        self._licznik_sprawdzen = 0
        self._rodzynki = 0

    def sprawdz(self):
        return self._licznik_sprawdzen >= 3

    def piecz(self, czas, temperatura):
        if 65 <= czas <= 75 and 200 <= temperatura <= 220 and self._rodzynki >= 30:
            while not self.sprawdz():
                self._licznik_sprawdzen += 1
            self._czy_upieczone = True

    def ocen(self):
        return self._czy_upieczone

    def dodaj_rodzynki(self, liczba=10):
        self._rodzynki += liczba

sernik.piecz(czas=70, temperatura=210)

if sernik.ocen():
    print("Sernik jest upieczony!")
else:
    print("Sernik jest jeszcze surowy.")
