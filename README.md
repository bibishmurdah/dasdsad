from abc import ABC, abstractmethod

class Ciasto(ABC):
    def init(self, maka, cukier, woda):
        self.maka = maka
        self.cukier = cukier
        self.woda = woda
    
    def przygotuj(self):
        pass
    
    def sprawdz(self):
        pass
    
    def piecz(self, czas, temperatura):
        pass
    
    def ocen(self):
        pass

class Szarlotka(Ciasto):
    def init(self, maka, cukier, woda):
        super().init(maka, cukier, woda)
        self._czy_upieczone = False
        self._licznik_sprawdzen = 0
        self.cynamon = False
    
    def przygotuj(self):
        self._czy_upieczone = False
        self._licznik_sprawdzen = 0
        self.__cynamon = False
    
    def _sprawdz(self):
        return self._licznik_sprawdzen < 3
    
    def piecz(self, czas, temperatura):
        if self.__cynamon:
            while not self._czy_upieczone:
                if self._sprawdz():
                    self._licznik_sprawdzen += 1
                else:
                    self._czy_upieczone = True
        else:
            if czas >= 55 and czas <= 60 and temperatura >= 180 and temperatura <= 200:
                self._czy_upieczone = True
    
    def ocen(self):
        return self._czy_upieczone
    
    def cynamon(self):
        self.__cynamon = True

class Sernik(Ciasto):
    def __init(self, maka, cukier, woda):
        super().init(maka, cukier, woda)
        self._czy_upieczone = False
        self._licznik_sprawdzen = 0
        self.__rodzynki = 0
    
    def przygotuj(self):
        self._czy_upieczone = False
        self._licznik_sprawdzen = 0
        self.__rodzynki = 0
    
    def _sprawdz(self):
        return self._licznik_sprawdzen < 3
    
    def piecz(self, czas, temperatura):
        if self.__rodzynki >= 30:
            while not self._czy_upieczone:
                if self._sprawdz():
                    self._licznik_sprawdzen += 1
                else:
                    self._czy_upieczone = True
        else:
            if czas >= 65 and czas <= 75 and temperatura >= 200 and temperatura <= 220:
                self._czy_upieczone = True
    
    def ocen(self):
        return self._czy_upieczone
    
    def rodzynki(self, liczba=10):
        self.__rodzynki += liczba

szarlotka = Szarlotka(maka=200, cukier=100, woda=150)

szarlotka.przygotuj()

szarlotka.cynamon()

szarlotka.piecz(czas=60, temperatura=190)

if szarlotka.ocen():
    print("Szarlotka jest upieczona!")
else:
    print("Szarlotka jest jeszcze surowa.")

sernik = Sernik(maka=300, cukier=150, woda=100)

sernik.przygotuj()

sernik.rodzynki(40)

sernik.piecz(czas=70, temperatura=210)

if sernik.ocen():
    print("Sernik jest upieczony!")
else:
    print("Sernik jest jeszcze surowy.")
