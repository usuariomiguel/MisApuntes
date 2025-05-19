# Codificación y decodificación en base64 \[Bandit10]

Encontrar la contraseña en el fichero data.txt, la encontraremos filtrando contenido codificado en base64&#x20;

```
// Decodificar base64
base64 -d data.txt
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

// Codificar base64
echo "hola mundo" | base64
```

{% hint style="info" %}
El algoritmo de codificación Base64 no es un algoritmo de cifrado, se decodifica fácilmente y, por lo tanto, no debe utilizarse como un método de cifrado seguro. No recomiendo que utilicéis esta técnica para proteger datos confidenciales, ya que se puede tensar en cuestión de segundos. En tal caso, es recomendable emplear métodos de cifrado seguros.
{% endhint %}
