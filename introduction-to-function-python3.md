# Uma introdução a funções em Python 3.9+
Considere a seguinte linha de código executada em modo interativo no Python:
~~~python
>>> print("Hello World!")
~~~
Como requerimento, você deveria conhecer de antemão qual seria o resultado. Entretando, o que há de novo?
Para responde-lo, é necessário antes denominar o que está occorendo: uma chamada a uma função.
# Funções
Funções (ou subrotina) pode ser definida como uma porção do código que permite referênciada e executa em uma outra parte, isto é, permite a divisão de tarefas em problemas em subproblemas e tarefas menores. Assim com a rotina principal, uma subrotina pode possuir uma entrada e uma saída. A saída de uma função pode ser chamada de retorno. Quando um conjunto de dados são passados a uma função, denomina-se argumentos. Enquanto aqueles esperados por ela são denominados parâmetros. Funções, por definição, precisam ser referências, para isso recebem um nome (rótulo ou indentificador, se preferir) válido.
# Chamada de uma função
Considere `foo` uma função válida, então `foo` pode ser chamada como:
~~~python
foo()
~~~
Neste caso, diz que passado nenhum argumento para `foo`, entretanto pode ocorrer erro como, por exemplo:
~~~
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: foo() missing 1 required positional argument: 'argument'
~~~
Entreanto, para entender isso é necessário entender o que uma assinatura de uma função, isto é, quais são os seus parâmetros (o que ela espera) e seu possíveis retornos (o que ela devolve)
# Argumentos
Um argumento pode ser qualquer valor, desde que a função espere esse argumento, isto é, seja declarado em seus parâmetros.
Há basicamente dois tipos de argumentos enquanto a forma que são passados a uma função:
- Argumentos posicionais: São definidos pela posição (ordem) na qual são passados, donde o nome.
- Argumentos nomeados: São definidos por uma palavra-chave como, por exemplo, `my_argument`, ao serem passados a uma função.
Uma função pode receber mais de um argumento - com ou sem limites em sua quantidade - dependendo da assinatura dela.
Por exemplo, `end` e `sep` são argumentos nomeados na seguinte chamada:
~~~python
print("Hello ", "", sep="Wor", end="ld!\n")
~~~
Não se esqueça do caractere de nova linha, pois comportamento de `print` muda ao definir `end` - ela não imprime o caractere de nova linha por padrão, ao invés é necessário declará-lo explícitamente.
Enquanto agora `greetings` e `its_name` são argumentos posicionais na seguinte chamada:
~~~python
greetings = "Hello"
its_name = "World!"
print(greetings, its_name)
~~~
Como você pode perceber, funções podem ser chamadas com váriaveis, bem como expressões:
~~~python
print(10 + 15 - 7 * 2) 
~~~
# Declaração de uma função
Uma função pode ser declarada usando a palavra reservada `def`, seguida por sua assinatura e por seu bloco:
~~~python
def sum(a, b):
	return a + b
~~~
Primeiro coloca-se `def`, em seguida seu nome e sua assinatura. Ela, por sua vez, é colocada entre parêntes, depois coloca-se os dois ponto indicando o começo de um bloco.
Na segunda linha, como em qualque bloco, as expressões são precessidas por uma identação, chamada de indentação do bloco, podem haver mais de uma expressão no mesmo bloco, em cada linha com o mesmo nível de indentação. A palavra chave `return` serve para indicar o retorno. 
# A assinatura de uma função
Tente a seguinte linha de código em modo interativo:
~~~python
>>> def sum(a, b):
...	return a + b
...
>>> sum(10, 5)
~~~
Cuidado com os caracteres `>>>` e `...`, eles são apenas decorativos e ilustram o `prompt` padrão do Python quando em modo normal e indentado, respectivamente. Se preferir, em modo `script` seria, provalvemente, assim:
~~~python
def sum(a, b):
	return a + b

print(sum(10, 5))
~~~
Como você pode perceber, uma função também é uma expressão, e como tal, o valor de retorno pode ser repassado a outra função, isto é, pode ocorrer uma chamada aninhada. Neste caso, a expressão dentro dos parênteses é avalida primeiro, como qualquer expressão, para se determinar o valor que será repassado a outra função.
Considere a seguinte linha de código em modo interativo:
~~~python
>>> def sum(a, b):
...	return a + b
>>> sum(1, 6)
~~~
O resultado seria algo como:
~~~
File "<stdin>", line 3
    sum(1,6)
    ^^^
SyntaxError: invalid syntax
~~~
Isto ocorre porque o interpretador expera uma expressão indentada dento do bloco da declaração da função, para evitar isso, recomenda-se sempre colocar uma nova linha (até aparecer `>>>`) após a declaração de uma função.
