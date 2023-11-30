# Control del flujo stderr-stdout, operadores y procesos en segundo plano

#### Ver código estado comando

> echo $?

#### No imprimir errores de comando no encontrado en consola

Para errores de command no found (stderr)

> command 2>/dev/null

{% hint style="info" %}
2 -> stderr (error)&#x20;

\> -> redirector

/dev/null -> archivo donde desaparece cualquier recurso
{% endhint %}

Para errores de que no encuentra un fichero o archivo (stdout)

> 'command' > /dev/null 2>&1
>
> 'command' &>/dev/null

{% hint style="info" %}
'>' -> redirector

/dev/null -> archivo donde desaparece cualquier recurso

2 -> stderr

\> -> redirector

& -> AND

1 -> stdout&#x20;
{% endhint %}

Dejar whireshark en segundo plano sin imprimir errores

> whireshak &>/dev/null & disown
