# Pygame kierros-2

## Materiaali
#### [Luokat](https://www.w3schools.com/python/python_classes.asp) lyhyesti

#### [Lukkien laajentaminen](https://www.w3schools.com/python/python_inheritance.asp) lyhyesti

## Luokat ja olio-ohjelmointi
Havainnollistavia esimerkkejä olio-ohjelmoinnista Pythonissa
### Yksinkertainen luokka ja sen metodit
````python
# Luodaan luokka kana
class Kana():
    # Määritetään kanan tiedot
    def __init__(self, nimi, ikä):
        self.nimi = nimi
        self.ikä = ikä
    
    # Määritetään funktio kanan iän muuttamiselle
    def kasvata_ikää(self):
        self.ikä += 1

# Luodaan uusi kana
kana = Kana("Ozymandias", 2)
print(f"Kanan {kana.nimi} ikä on {kana.ikä}")
kana.kasvata_ikää() # Kasvatetaan kanan ikää
print(f"Kanan {kana.nimi} ikä on {kana.ikä}")
````
### Tuloste
````
Kanan Ozymandias ikä on 2
Kanan Ozymandias ikä on 3
````

### Luokan laajentaminen (inheritance)
````python
# Luodana yläluokka eläin. Jokaisella eläimellä pitää olla nimi ja ikä
class Eläin():
    def __init__(self, nimi, ikä):
        self.nimi = nimi
        self.ikä = ikä

# Luodaan luokkaa Eläin laajentava luokka Koira
class Koira(Eläin):
    def __init__(self, nimi, ikä):
        super().__init__(nimi, ikä)

# Luodaan luokkaa Eläin laajentava luokka Kissa
# Määritetään Kissalle myös muuttuja joka kuvaa sen elämiä jäljellä
class Kissa(Eläin):
    def __init__(self, nimi, ikä, elämiä_jäljellä):
        super().__init__(nimi, ikä)
        self.elämiä_jäljellä = elämiä_jäljellä

# Luodaan kissa ja koira
kissa = Kissa("Jölsfur", 7, 9)
koira = Koira("Tsardikus IV", 9)

# Luodaan lista eläimistä
lista: list[Eläin] = [kissa, koira]

# Käydään läpi listaa
for eläin in lista:
    # Jos eläin on kissa
    if isinstance(eläin, Kissa):
        print(f"Kissalla {eläin.nimi} on {eläin.elämiä_jäljellä} elämää jäljellä")
    else: # Muuten
        print(f"Koira {eläin.nimi} on {eläin.ikä} vuotias")
````
### Tuloste
````
Kissalla Jölsfur on 9 elämää jäljellä
Koira Tsardikus IV on 9 vuotias
````

## Tehtävänanto
> Hyödynnetään olio-ohjelmointia nykyisessä projektissa
- Luo uusi luokka nimeltään `Player`. Tämä tulee kuvaamaan pomppivaa palloa, eli meidän pelaajaa
- Anna Luokalle `Player` kentät `velocity_x`, `velocity_y`, `pos_x`, `pos_y`, sekä `radius`. Anna kentille järkevät aloitusarvot
- Annetaan luokalle `Player` metodi `draw()`, joka mahdollistaa pelaajan piirtämisen. Kopioi luokan määritelmä alta:
````python
def draw(window):
    pygame.draw.circle(window, (0, 0, 255), (self.pos_x, self.pos_y), self.radius)
````
- Hyödynnä pelaaja luokkaa tehtävä1:n koodissa.