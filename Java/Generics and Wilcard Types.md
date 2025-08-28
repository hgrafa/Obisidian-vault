## Generics

### Motivação para usar Generics

Permite que classes, interfaces e métodos possam ser parametrizados por tipo.

- Reuso
- Type safety
- Performance

Imagine o seguinte serviço:

> 📦 `services` > ➕`PrintService.java`

```java
public class PrintService {

  private List<integer> list = new ArrayList<>();  

  public void addValue(Integer value) {
    list.add(value);
  }

}
```

Caso nosso objetivo fosse receber `String` ao invés de `Integer`, seira custoso.

### O problema do tipo Object

Sim, você pensou que seria fácil receber objetos do tipo `Object`, entretanto isto é uma operação perigosa, pois algumas operações não podem ser feitas normalmente.

> 📦 `services` > ➕`PrintService.java`

```java
public class PrintService {

  private List<Object> list = new ArrayList<>();

  public void addValue(Object value) {
    list.add(Object);
  }
  
}
```

Porém teríamos dificuldade de receber os dados no `Program.java`, afinal seria um `Scanner` para `.nextInt()` ou `.next()`?

Além disso, a digitação pode permitir que o vetor `[1, 2, "Maria", 3]` exista, já que o tipo Object aceita qualquer classe filha. O nosso objetivo seria determinar o tipo de vetor enquanto as variáveis são inseridas pelo usuário.

### Com Generics

Criaremos um tipo `<T>` qualquer e vamos referenciar nossa classe a ele.  

```java

public class PrintService <T> {

  List <T> list = new ArrayList<>();

  public void addValue( T value ){
    list.add(value);
  }
  
}
```

Desta forma utilizamos um tipo `generics` e tornaremos nossas operações seguras durante todo o programa.

### Genéricos Delimitados

avisando que um método vai trabalhar com um tipo `<T>`:

```java
  public <T> T max (List<T> list){

    //declara a existência do tipo T genérico
    // depois aceita retornar o tipo genérico T

  }
```

Inicialmente um `service` que encontra o maior numa lista de um tipo genérico `<T>`:

```java
public class CalculationService {

  public static <T extends Comparable<T>> T max(List<T> list) {

    if (list.isEmpty())
      throw new IllegalStateException("List can't be empty");

    T max = list.get(0);
    for (T item : list) {
      if (item.compareTo(max) > 0) max = item;
    }

    return max;
  }
}
```

Precisamos também implementar a `CompareTo` além de escrever o método para comparar corretamente a propriedade desejada.

Caso não quiséssemos ter problemas com superclasses que implementem o `CompareTo`, que são herdados pela classe aplicada ao `generics`, teríamos que fazer da seguinte forma:

```java
public static <T extends Comparable<? super T>> T max(List<T> list) {

}
```

## Wildcards

```java
List <Object> myObjects = new ArrayList<Object>();
```

Uma lista de objetos não é o supertipo de todas as listas, ainda que a Object seja supertipo de todas as Classes.

Caso seja usado dessa forma, haverá erro de compilação.

o supertipo neste caso é uma lista do tipo Curinga:

```java
List<?> muObjects = new ArrayList<Object>();
```

### Podemos fazer métodos genéricos para qualquer tipo:

```java
public class Program{

	public static void main(String[] args){
		List<Integer> myInts = Arrays.asList(5, 2, 10);
		printList(myInts);
	}

	public static void printList( List<?> list){
		for (Object obj : list){
			System.out.println(obj);
		}
	}

}
```

**Observação:** Não é possível adicionar elementos ao tipo curinga, o compilador no estado atual não consegue interpretar se o tipo da lista é o tipo do número a ser inserido.

### Bounded wildcards (Tipos Curinga delimitados)

São delimitações para superclasses ou subclasses de um tipo qualquer. Por exemplo, imagine uma lista que aceita qualquer elemento do tipo Shape e subclasses de shape. Se criado como tipo curinga:

- A operação que cria uma `List<Circle>` e passa para uma `List<? extends shape>` é segura, pois eu estou passando uma lista do mesmo homogênea para uma lista genérica qualquer.

- A operação `.add()` não é segura, pois eu sei que o tipo a entrar na lista é subclasse de shape, entretanto, pode ser um tipo `rectangle` entrando numa `List<? extends shape>` que já recebeu uma `List <Circle>`. É um problema similar ao *type safety*

```java
public class Program {

	public static void main(String[] args) {
		
		List<Shape> myShapes = new ArrayList<>();
		myShapes.add(new Rectangle(3.0, 2.0));
		myShapes.add(new Circle(2.0));
		
		List<Circle> myCircles = new ArrayList<>();
		myCircles.add(new Circle(2.0));
		myCircles.add(new Circle(3.0));
		
		System.out.println("Total area: " + totalArea(myCircles));
	}
	
	public static double totalArea(List<? extends Shape> list) {
		double sum = 0.0;
		for (Shape s : list) {
			sum += s.area();
		}
		return sum;
	}
}
```

### Princípios Get/Put

Vamos fazer métodos que copiam elementos de uma lista para outra que pode ser mais genérica que a primeira.

```java
List <Integer> myInts = Arrays.asList(1, 2, 3, 4);
List <Double> myDoubles = Arrays.asList(3.14, 6.28);
List <Object> myObjs = new ArrayList<Object>();
```

### 1. Princípio da Covariância

A Wrapper `Number` é uma classe intermediária entre a `Object` e todos os outros tipos numéricos.

Desta forma, se fizermos:

```java
List <Integer> intList = Arrays.asList(1, 2, 3);
List < ? extends Number > list = intList;
```

| get | put |
| :-: | :-:|
| OK | ERROR|

```java
Number x = list.get(0); // ok
list.add(10); // erro de compilação
```

Neste caso vamos da classe para as subclasses, e sendo assim, podemos ter operações menos seguras durante as inserções, basta lembrar das relações *é um/ é uma*.

> Shape não é um rectangle

> Shape não é um Circle

Isto justifica as inserções não serem seguras.

### 2. Princípio da Contravarância

Aqui faremos uma referência as superclasses de uma classe, 

```java
List <object> myObjs = Array.asList("Maria", "Alex");
List < ? super Number > myNums = myObjs;
```

| get | put |
| :-: | :-:|
| ERROR | OK |

```java
list.add(10); // é um number e com certeza é um objeto
// operação segura

list.add(3.14); // é um number e com certeza é um objeto
// operação segura

Number x = myNums.get(0);
// A lista pode ter elementos de uma superclasse
// por exemplo do tipo object ou string
// desta forma, passa o valor para Number não é seguro

```

### Retornando ao método copy

```java
public class Program {
  public static void main(String[] args) {

    List<Integer> myInts = Arrays.asList(1, 2, 3, 4);
    List<Double> myDoubles = Arrays.asList(3.14, 6.28);
    List<Object> myObjs = new ArrayList<Object>();
    
    copy(myInts, myObjs);
    printList(myObjs);
    copy(myDoubles, myObjs);
    printList(myObjs);
  
  }
  
  public static void copy(List<? extends Number> source, List<? super Number> destiny) {
    for(Number number : source) {
      destiny.add(number);
    }
  }
  
  public static void printList(List<?> list) {
    for (Object obj : list) {
      System.out.print(obj + " ");
    }
    
    System.out.println();
  }
}
```