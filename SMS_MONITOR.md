SMS Monitor
===========

Existuju 2 stromy, jeden na `NatIp` a jeden na `Contract`. Najprv sa buduje strom `NatIp` 
pomocou bran, vstupnych IP a gatewayou. Potom sa z tohto stromu generuje `Contract` strom.

Nie kazda **NatIp** musi byt v `NatIp` strome. T.j. nemusi mat **NatIpNode**. V strome sa objavi kazda Brana, pretoze pri tej sa predpoklada ze bude parentom nejakej druhej IP. Ak zmluva nema branu, je takzvany leaf/list tak sa do stromu dostane. Takto je to spravene kvoli setreniu udajov v `NatIpNodeHierarchy` pretoze metoda closure_tree ma dost velku zlozitost.

Moze nastat takato situacia

```
Zmluva 01
 - 10.10.10.1 *
   L Zmluva 02
     - 10.10.10.2
     - 10.10.11.1 *
   L Zmluva 03
     - 10.10.10.3 *
```

IP oznacene * budu v `NatIp` strome => Z kazdej zmluvy aspon 1 IP. Nemusia byt vsetky pretoze hlavne je potom z toho poskladat `Contract` strom.
