# Associação entre as classes

# Herança

Trazendo para vida real a herança é feita após o falecimento de uma pessoa, onde é transmitido bens por sucessão.

- Herança é repassar o que você tem.

Na programação, é semelhante à herança da vida real no sentido de “passar algo para os filhos” (subclasse), mas com duas diferenças importantes:

**Não depende de eventos da vida**

- Não precisa que algo aconteça (como a morte).

**Não partilha**

- Não tem divisão ou perda: cada “herdeiro” tem acesso completo, igual ao original.

### **Algumas características:**

Override: é como um aviso: “Ei, esse método existia no pai, mas aqui no filho ele vai ter um comportamento diferente”.

- "Mesmo Botão, ações diferentes".

```java
// Classe base
class Animal {
    String nome;

    Animal(String nome) {
        this.nome = nome;
    }

    void falar() {
        System.out.println("Som genérico");
    }
}
```

```java
// Subclasse que herda de Animal
class Cachorro extends Animal {
    Cachorro(String nome) {
        super(nome); // chama o construtor da superclasse
    }

    @Override
    void falar() {
        System.out.println(nome + " diz: Au au!");
    }
}
```

- Na herança você tem um bom reaproveitamento de código, mas como consequência tem uma grande inflexibilidade entre as classes.
- **Efeito dominó**: A classe filha é muito depende da classe pai, se eu mudo algo na classe pai, a classe filha também quebra.

# **Composição / Associação**

### **Na composição, eu escolho quais classes vão para compor minha classe.**

- É como você escolher quais recheios você quer no seu pastel.
- Diferente da herança que já vem com a base definida e você tem que herdar.

Exemplo em código:

```java
// Classe Componente
class Motor {
    void ligar() {
        System.out.println("Motor ligado!");
    }
}
```

```java
// Classe Principal que USA o componente (composição)
class Carro {
    private Motor motor; // Carro TEM um Motor

    public Carro() {
        this.motor = new Motor(); // monta a peça dentro do carro
    }

    public void andar() {
        motor.ligar(); // usa o motor para andar
        System.out.println("Carro está andando!");
    }
}
```

### Por que composição é melhor que herança?

- Você tira aquela dependência pai que tinha na herança, tornando mais flexível.
- Tem uma combinação de comportamentos, você decide o que sua classe vai compor.
- A manutenção é mais fácil, pois não tem tanta dependência entre as classes.

# **DIP (Dependency Inversion Principle)**

### O princípio da DIP existe para tornar o sistema mais flexível, fácil de manter e testável.

- Em uma sorveteria (sistema), pense no self-service, você decide o que por dentro do copo (módulo de alto nível). Essa é a ideia do DIP;

O DIP diz que:

**Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações:** Quer dizer se você criar um método diretamente no módulo de baixo nível, você cria um sistema rígido e de difícil manutenção. Quando ambos (baixo e alto nível) dependem de abstração, você está criando um sistema flexível e modular.

- Abstração é a ponte entre os módulos de alto e baixo nível, permitindo que o projeto seja sustentável e testável.

**Abstrações não devem depender de detalhes,  os detalhes devem depender de abstrações:** Quer dizer que abstrações não pode conter detalhes, pois estaria amarrando o módulo ao detalhe.

```java
interface Sorveteria{

void adicionar(); ✅
}
```

```java
interface Sorveteria{

void adicionarSorvete(); ❌
}
```

O método adicionarSorvete está adicionando mais detalhes do que deveria, porquê a abstração ficaria limitada apenas a adição do sorvete, sendo que existe complemento(recheios) em uma sorveteria.