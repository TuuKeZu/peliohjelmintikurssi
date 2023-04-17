# Pygame kierros-1

## Materiaali
### [Täältä](https://www.tutorialspoint.com/pygame/index.htm) löydät kaiken tarvittavan materiaalin tehtävän suorittamiseen.

## Aloitus
1. Avaa VS code:ssa työkansio
2. Luo uusi tiedosto nimellä `tehtävä1.py`
3. Kopio alla oleva koodi tiedostoon
````python
import pygame

pygame.init()
screen = pygame.display.set_mode([500, 500])
running = True

# Päästään käsiksi aikaan koodin sisällä
clock = pygame.time.Clock();

x = 150
y = 150

while running:
    # Aika edellisestä näytön päivityksestä (deltaTime)
    dt = clock.tick(60)/1000
    
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    screen.fill((255, 255, 255))

    # Liikuta palloa 100px oikealle sekunnissa riippumatta pelin nopeudesta
    x +=100*dt

    # Sijoita pallo takaisin alkupisteeseensä
    if(x > 500):
        x = 0

    pygame.draw.circle(screen, (0, 0, 255), (x, y), 75)
    pygame.display.flip()


pygame.quit()
````

## Tehtävänanto
> Tee yksinkertainen peli, jossa pallolla on painovoima ja sitä voidaan "pomputtaa" painamalla näppäimistön avulla
- Palloon tulee vaikuttaa painvoima, eli sen pitää pudota kiihtyvvällä liikkeellä
- Pallon ei tule pudota ikkunan ulkopuolelle
- Painamalla `space`-näppäintä pallo "hyppää" ylöspäin

## Mikä ihmeen `deltatime`
-  halutettssassi voit katsoa mitä `deltaTime` tarkoittaa [täältä](https://drewcampbell92.medium.com/understanding-delta-time-b53bf4781a03)

## Vinkkejä
- Pallon kiihtyvyyttä vartten kannattaa tehdä oma muuttuja, joka ilmaisee pallon nopeuden muutoksen.
- Kannattaa myös luoda oma muuttuja, joka kertoo onko pallo putoavassa liikkeessä