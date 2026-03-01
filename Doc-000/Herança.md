A Herança é um dos pilares mais poderosos da Programação Orientada a Objetos. Ela permite que uma classe (filha) adquira as características e comportamentos de outra classe (pai), promovendo a reutilização de código e a criação de hierarquias lógicas.
Imagine que você está desenvolvendo um sistema para um zoológico. Em vez de escrever o código para "comer" e "dormir" em cada animal individualmente, você define isso uma única vez.
1. O que é Herança?
A herança é o mecanismo pelo qual uma Subclasse (classe filha) estende uma Superclasse (classe pai).
 * Superclasse: Contém os atributos e métodos genéricos, comuns a vários objetos.
 * Subclasse: Herda tudo da superclasse e pode adicionar seus próprios atributos específicos ou modificar comportamentos existentes.
2. Relação "É UM"
A regra de ouro para saber se deve usar herança é a frase "é um":
 * Um Gato é um Animal. (Herança faz sentido)
 * Um Diretor é um Funcionario. (Herança faz sentido)
 * Um Carro é um Motor. (Não! Um carro tem um motor. Aqui usa-se Composição, não herança).
3. Desenvolvimento de uma Estrutura de Herança
Vamos visualizar como isso funciona na prática de design de software:
A Superclasse (Pai)
Classe: Veiculo
Atributos: marca, modelo, ano
Método: buzinar() { "Beep Beep!" }

As Subclasses (Filhas)
Ao herdar de Veiculo, não precisamos redefinir marca ou ano. Apenas focamos no que é único:
 * Classe: Carro (Herda de Veiculo)
   * Atributo extra: numeroDePortas
   * Usa o buzinar() do pai.
 * Classe: Moto (Herda de Veiculo)
   * Atributo extra: cilindradas
   * Método extra: darGrau()
4. Sobrescrita de Métodos (Override)
Às vezes, a classe filha herda um método, mas precisa que ele funcione de um jeito diferente. Isso é chamado de Sobrescrita.
> Exemplo: A classe Animal tem o método emitirSom().
>  * A classe Cachorro sobrescreve para retornar "Au Au".
>  * A classe Gato sobrescreve para retornar "Miau".
> 
5. Vantagens da Herança
 * Economia de Código: Você não repete as mesmas variáveis em dez lugares diferentes.
 * Manutenção Facilitada: Se você precisar mudar como um Funcionario recebe aumento, muda na classe pai e todos os tipos de funcionários (Gerente, Estagiário, Analista) são atualizados automaticamente.
 * Polimorfismo: Você pode tratar diferentes objetos filhos como se fossem o pai (ex: criar uma lista de Animais que contém gatos e cachorros misturados).
6. Cuidados Importantes
 * Acoplamento: Se a classe pai mudar drasticamente, todas as filhas podem quebrar.
 * Herança Múltipla: Algumas linguagens (como Java e C#) não permitem que uma classe tenha dois pais diretos para evitar confusão, enquanto outras (como Python e C++) permitem.
Quer que eu transforme esse conceito de Herança em um código real em Python ou Java para você ver como as palavras-chave extends ou super() funcionam?
