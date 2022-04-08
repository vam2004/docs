# Uma introdução a funções em Python 3.9+
Considere a seguinte linha de código executada em modo interativo no Python:
~~~python
>>> print("Hello World!")
~~~
Como requerimento, você deveria conhecer de antemão qual seria o resultado. Entretando, o que há de novo?
Para responde-lo, é necessário antes denominar o que está occorendo: uma chamada a uma função. Vamos começar
# Funções
Funções (ou subrotina) pode ser definida como uma porção do código que permite ser referênciada e executada em uma outra parte, isto é, permite a divisão de tarefas em problemas em subproblemas e tarefas menores. Assim como a rotina principal, uma subrotina pode possuir uma entrada e uma saída. A saída de uma função pode ser chamada de retorno. Quando um conjunto de dados são passados a uma função, denomina-se argumentos. Enquanto aqueles esperados por ela são denominados parâmetros. Funções, por definição, precisam ser referências, para isso recebem um nome (rótulo ou indentificador, se preferir) válido.
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
