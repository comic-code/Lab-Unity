<h1 align="center">
  Lab <img src="https://cdn.worldvectorlogo.com/logos/unity-69.svg" width=35>
</h1>


<h2 align="center">  
  
  :memo:
  
  Programação em C#
</h2>

## <a name="i">:robot: Índice</a>

- 4 -   [Introdução](#4-1)
  - 4.1 [Scripts](#4-1)
  - 4.2 [Variáveis e Constantes](#4-2)
  - 4.3 [Comentários](#4-3)
  - 4.4 [Casting / Conversão](#4-4)
  - 4.5 [Escopo](#4-5)
  - 4.6 [Operadores Aritméticos](#4-6)
  - 4.7 [Métodos](#4-7)
  - 4.8 [Passando Parâmetros](#4-8)
  - 4.9 [Operadores Lógicos && e ||](#4-9)
  - 4.10 [Condicional If-Else](#4-10)
  - 4.11 [Mini Game Arkanoid](#4-11)
  - 4.12 [Condicional Switch](#4-12)
  - 4.13 [Acessando Componentes](#4-13)
  - 4.14 [Arrays](#4-14)
  - 4.15 [Listas](#4-15)
  - 4.16 [While](#4-16)
  - 4.17 [Do While](#4-17)
  - 4.18 [Foreach](#4-18)
  - 4.19 [For](#4-19)
  - 4.20 [Iterando Arrays Uni e Bidimensionais](#4-20)
  - 4.21 [Enum - Enumeradores](#4-21)
  - 4.22 [Corrotinas](#4-22)
  - 4.23 [Singletons](#4-23)
  - 4.24 [Delegates, Events e Actions](#4-24)
****

## <a name="4-1">Scripts</a>

Todo jogo precisam de determinada ações.

- Scripts padrões da unity são criados herdando a classe **MonoBehaviour**, classe da própria Unity que nós dá a possibilidade de acessar vários métodos. Graças a ele, tbm é possível adicionar o script a um objeto, como se fosse um Componente.

- Start()
  - Ações que devem ocorrer quando o GameObject for criado na tela

- Update()
  - Ações a todo frame do jogo

- Também é possível usar métodos próprios ou do próprio MonoBehaviour

****

## <a name="4-2">Variáveis e Constantes</a>

Espaços na memória para guardar informações. O C# é uma linguagem fortemente tipada.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
 
public class Variaveis : MonoBehaviour
 
{ 
  // vai de -2.147.483.648 até 2.147.483.647
  public int integerTest = 10; // É possível acessar lá do Editor, ou em outros scripts 
  int integerTest = 10; // Por padrão se entende como private, só poderá ser acessada nesse arquivo

  //precisão de 6 a 9 dígitos
  public float _decimal = 0.386f; // É NECESSÁRIO COLOCAR f no final.


  // precisão de 15 a 17 dígitos
  public double _decimal2 = 0.545; // Não precisa do f no final, apesar de poder colocar d.

  // vai de 0 a 18.446.744.073.709.551.615
  public ulong megaNumber; // APENAS números positivos

  // vai de -9,223,372,036,854,775,808 até 9,223,372,036,854,775,807
  public long bigNumber; 

  // NÃO é considerada como 0 ou 1  
  public bool trueOrFalse = false;
  public bool trueOrFalse = true;
  
 
  // APENAS um caractere
  public char a = 'x'; // Utiliza aspas simples
  
  // Vários caracteres
  public string text = "texto"; // Utiliza aspas duplas
  

  // Constantes 
  public const string NAME = "João"; // Utiliza letras maiúsculas
  private const float HEIGHT = 1.82f;
 
  // Variáveis lá da UNITY
  public GameObject _gameObject;
  public Sprite sprite;
  public Rigidbody2D rb2D;
 
//----------------------------
 
  void Start() {
    trueOrFalse = true;
    
    text = "outro texto";
    
    integerTeste = 20;
  }
 
}
```
> Normalmente para números é utilizado **int**.   
> Em casos de camelCase a unity separa automaticamente no editor.    


### **Variáveis no Editor**

Caso um script seja adicionado a um objeto, no Inspector é possível ver os valores das variáveis
- É possível arrastar sprites para variáveis do tipo sprite pelo editor.

*****

## <a name="4-3">Comentários</a>

```c#
// Comentário

/*
  Comentário
*/
```

### **Region**

```c#
#region

  code...

#endregion
```
> É possível "minimizar" o código por regiões no editor
*****

## <a name="4-4">Casting / Conversão</a>

C# é um linguagem fortemente tipada, uma variável do tipo inteiro vai sempre morrer como um inteiro. Porém as vezes é necessário mudar o tipo desse valor, basta converter em uma nova variável.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
 
public class Casting : MonoBehaviour
{
  // Castings e Conversões -> converter os dados de um tipo para outro tipo
  
  void Start()
  {
    float _decimal = 234.7f;
    // Casting
    int _inteiro = (int)_decimal; //  (234) Não arredonda.
    
    // Conversão
    string _characters = _inteiro.ToString(); // ("234")
    int _inteiro2 = int.Parse(_characters); // (234)
    
    //Casting
    float _decimal2 = (float)_inteiro2; //(234.0)
    
    
    bool _bool = true;
    string booleanString = _bool.ToString(); ("true")
    
  }
}
```

****

## <a name="4-5">Escopo</a>

Na programação escopo são "blocos". Um estado engloba cidades, um pais engloba estados.
> Uma lei estadual funcionariam em todas as cidades do estados, mas não em outros estados, diferente de uma lei federal que funcionaria em todos os estados.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Escopo : MonoBehaviour 
{
  string global = "global"; // Não será possível acessar em outras classes

  void Start()
  {
    Debug.Log(global);
  }

  void Update()
  {

  }

  void Test(int _teste) // Parâmetros apenas na própria função
  {
    string local = "local";
    Debug.Log(global);
    Debug.Log(local);
  }
}
```

****

## <a name="4-6">Operadores Aritméticos</a>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
 
 
public class Operadores : MonoBehaviour
{
  int testeInt = 50;
  int testeInt2 = 150;
  int testeTotal;
  int remainder;
  float testeFloat = 50.3f;
  float testeFloat2 = 150.5f;
 
  void Start()
  {
    testeTotal = 50 * 150;              //multiplicação
    
    testeTotal = testeInt / testeInt2;  //divisão
    
    testeTotal = testeInt - testeInt2;  //subtração
    
    testeTotal = testeInt + testeInt2;  //soma
  
    // Mathf é uma classe de operações matemáticas

  
    testeFloat = Mathf.Sqrt(9.0f);        //raiz quadrada
    
    testeFloat2 = Mathf.Pow(9.0f, 2.0f);  //potenciação
    
    testeFloat = Mathf.Abs(testeFloat);   //número absoluto (sempre positivo)  
  
    remainder = testeInt % testeInt2;     //sobra da divisão de um número pelo outro:
  
    // --------

    testeInt++;//soma 1
  
    testeInt--;//subtrai 1
  
    testeInt += 2; //soma 2
  
    testeInt -= 3; //subtrai 3:
  }
}
```

****

## <a name="4-6">Métodos</a>

Nada mais é que um bloco de código que contem determinadas instruções.

```c#

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
 
public class Metodos : MonoBehaviour
{
 
  int exemploA;
  string exemploB;
  bool exemploC;
  int exemploD;
 
  private void Awake()
  {
    CountDown(1, "teste", true);
  }
  
  void Start()
  {
  
  }
  
  void Update()
  {
  
  }

  void FixedUpdate() {

  }
  
  /*
    private ou public
    tipo de retorno (void, int, string...)
    nome sempre com maiúsculo
    parâmetros 
  */

  public void CountDown(int _a, string _b, bool _c)
  {
    exemploA = _a; 
    exemploB = _b;
    exemploC = _c;
  }
}
```
> O **Awake()** é rodado antes do Start();   
> FixedUpdate é mais para coisas de física, como o movimento do personagem, já que o Update é por frame. 

## <a name="4-7">Passando Parâmetros</a>

- Forma de **Valor**
  - Tudo que for feito, **não muda** o valor original
****
- Forma de **Referência** 
  - Tudo que for feito, **muda** o valor original

```c#
using UnityEngine;

public class Test : MonoBehaviour
{
    float value;
    float refer;
    
    void Start()
    {
        ValueXRefer(value);
    }

    void ValueXRefer(float local)
    {
        local += 10;
        Debug.Log("local = " + local);
    }
}
```
> Neste caso se trata de valor, sendo assim value não será alterado.

****

```c#
using UnityEngine;

public class Test : MonoBehaviour
{
    float value;
    float refer = 10.0f;
    
    void Start()
    {
        ValueXRefer(ref refer);
    }

    void ValueXRefer(ref float local)
    {
        local += 10;
        Debug.Log("local = " + local);
    }
}
```
> Neste caso se trata de referência, refer será alterado.