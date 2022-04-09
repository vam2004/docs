Os seguintes exemplos ilustram como deveria ser realizada
a tradução da linguagem proposta para `Rust`:
1. De:
```
defina foo com a, b, c como:
	seja x = a + b + c
	retorne x ** 2
```
Para:
~~~rust
fn foo(a: lang_object, b: lang_object, c: lang_object) {
	let x = a + b + c;
	return math::pow(x, 2);
}
~~~
2. De:
```
defina foo2 com a inteiro, b real, c inteiro como:
	seja x = raiz_quadrada(b * c + a)
	seja y = raiz_enesima(2, a)
	retorne x + y
```
Para:
~~~rust
fn foo2(a: lang_int, b: lang_real, c: lang_int) {
	let x = raiz_quadrada(b * c + a);
	let y = raiz_enesima(2, a);
	return x + y;
}
~~~
3. De:
```
defina foo3 com a inteiro, b real, c inteiro como:
	x = inteiro(c)
	y = inteiro(b)
	x += y
	z = inteiro(real(a))
	retorne x + y + z como inteiro
```
Para:
~~~rust
fn foo3(a: lang_int, b: lang_real, c: lang_int) -> lang_int {
	let mut x = inteiro(c);
	let y = inteiro(b);
	x += y;
	z = inteiro(lang);
	return inteiro(x + y + z);
}
~~~
4. De:
```
classe foo_classe:
	x inteiro = 10
	y real = 15.5
```
Para:
~~~
struct foo_classe {
	inner: lang_object
}
foo_classe_static = build_static!(foo_classe, ("x", lang_int), ("y", lang_real));
~~~
5. De:
```
classe poo extende foo_classe:
	defina eval_from com x texto, y lista[inteiro] como:
		se y[0] > y[1] execute:
			imprima(x)
		ou execute:
			imprima("Menor")
		retorne 2.0 como inteiro
	construa esta_classe com x texto como:
		esta_classe.x = x
		esta_classe.y = foo_classe.x
		retorne esta_classe
```
Para:
~~~rust
struct poo {
	inner: lang_object
}
impl poo {
	fn eval_from(x: lang_text, y: lang_list<lang_int>) -> lang_int {
		if y[0] > y[1] {
			imprima(x);
		} else {
			imprima("Menor");
		}
	}
	fn esta_classe(x: lang_text, outra: foo_classe) -> Self {
		let esta_classe = Self {
			inner: lang_object::new()
		};
		esta_classe.inner._set("x", x);
		esta_classe.inner._set("x", <foo_classe as static>::_get("x"));
		return esta_classe;
	}
}
~~~
## Alguns recursos da implementação
Assim, é necessário implementar dentro do tempo execução várias funcionalidades. Entranto, fica defido alguns recurso a ser implementado:
- Uma classe será uma `struct` com uma única proprieade `inner`, representando sua instancia (objeto)
- Um objeto é uma dicionário de objetos (recursivo)
- Os tipos primitivos será prefixados por `lang_`
- Os métodos estáticos de uma classe são definidos como funções dentro de `impl`
- A macro `build_static` constroi as proprieades estáticas que são acessivel através de uma `trait`
- Para evitar ambiguidades
## Especificação da linguagem
- O retorno de uma função é baseado na sentença `como` da linguagem, seu tipo é inferido a partir disto, sendo necessário uma conversão de tipos quando a tipagem do valor fonte é desconhecida ou não confere com a tipagem do valor resultante
