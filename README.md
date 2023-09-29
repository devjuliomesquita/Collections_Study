# [Collections] Collections tipos e funcionalidades

:::info
:bulb: Este artigo tem como objetivos esplanar cada tópico de collections.
:::

### :small_blue_diamond: :


## :book:Collections 

:::success
Lista de funções que são necessárias para dominar collections.
:::

### :small_blue_diamond: Equals:


## Explicações

:::success
Segue algumas descrições e exemplos.
:::

### :small_blue_diamond: Equals
:::info
:bulb: Por padrão o Java compara objetos pelo local de memória que os mesmo estam armazenados. O equals é uma método que realiza o comparativo entre valores do objeto ou atributos do mesmo.
:::

1. Reflexivo: **x.equals(x)** tem que ser true para tudo x que for diferente de null.
2. Simétrico: para **x e y diferentes de null** se *x.equals(y) == true* então *y.equals(x) == true*.
3. Transitivo: para **x, y e z diferentes de null** se *x.equals(y) == true e y.equals(z) == true então z.equals(x) == true*.
4. Consistente: Se **x for diferente de nul**l então *x.equals(null) sempre deve retornar false*.

#### :small_blue_diamond: Example
---

```gherkin=
@Getter
@Setter
@AllArgsConstructor
public class Smartphone {
    private String serialNumber;
    private String model;

    //Vamos satisfazer as condições
    @Override
    public boolean equals(Object o) {
    	if(o == null) return false;
    	if(this == o) return true;
    	if(this.getClass() != o.getClass()) return false;
    	Smartphone smartphone = (Smartphone) o;
    	return serialNumber != null && serialNumber.equals(smartphone.serialNumber);
    }
}

public class EqualsTest {
    public static vd main(String[] args) {
    	Smartphone smartphone1 = new Smartphone("1B2I3", "IPhone");
    	Smartphone smartphone2 = new Smartphone("1B2I3", "Motorola");
        System.out.println(smartphone1.equals(smartphone2));    
	}
}
```
> **Resultado = true** - pois o serialNumber são identicos então é         necessários entender a regra de negócio que identifica como um objeto é igual ao outro.


### :small_blue_diamond: HashCode
:::info
:bulb: Este método sempre está junto com equals. O hashCode é um código gerado na criação de um objeto. Isso faz com que as pesquisas em uma lista de seja mais performática.
:::
1. Simétrico: Se o **x.equals(y) == true** então o *y.hashCode == x.hashCode()*, porém se **y.hashCode == x.hashCode(**) não necessáriamente *x.equals(y) == true*.
2. Constante: Se **x.hashCode() != y.hashCode()** então o *x.equals(y) deverá ser false*.
```gherkin=
#Reutilizando o exemplo anterior... podemos implementar o hasCode assim:
public class Smartphone {
    private String serialNumber;
    private String model;

    ##Método Equals implementado...
    
    @Override
    public int hashCode() {
        return serialNumber == null ? 0 : this.serialNumber.hashCode();
    }
}

```
### :small_blue_diamond: List
:::info
:bulb: A List é uma interface que extende no pacote Collection. Lembre-se que as colleções são altamente coesas. Listas em resumo servem para ordanar.
:::
#### =>> Observações
1. A declaração de um lista sempre deve conter o tipo Wraper da coleção, **List<String**> == *lista de strings* ou **List<LocalDate>** == *lista de datas*, **nunca o tipo primitivo** pois neles não contém os métodos equals e hashCode.
    
#### :small_blue_diamond: Métodos | Operadores de Modificação
1. **.add**: Este método serve para adicionar um elemento no final da lista (operação opcional). O retorno do método é um boolean == true caso o elemento tenha sido inserido na lista do contrário false.
```gherkin=
    boolean add(E e); //"E" é tipo de elemento que será inserido.
```
2. **.remove**: Este método serve para remover um elemento da lista caso o mesmo seja encontrado. O retorno do método é um boolean == true caso o elemento tenha sido removido da lista do contrário false. O método tem sua sobrecarga. É possível passar um Object obj ou um int index.
```gherkin=
    boolean remove(Object o); 
```
#### :small_blue_diamond: Métodos | Operadores de Consulta (Query)
1. **.add**: Este método serve para adicionar um elemento no final da lista (operação opcional). O retorno do método é um boolean == true caso o elemento tenha sido inserido na lista do contrário false.
```gherkin=
    boolean add(E e); //"E" é tipo de elemento que será inserido.
```
2. **.remove**: Este método serve para remover um elemento da lista caso o mesmo seja encontrado. O retorno do método é um boolean == true caso o elemento tenha sido removido da lista do contrário false. O método tem sua sobrecarga. É possível passar um Object obj ou um int index.
```gherkin=
    boolean remove(Object o); 
```
    

