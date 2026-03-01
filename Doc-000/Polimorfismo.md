O Polimorfismo é o quarto e mais sofisticado pilar da Programação Orientada a Objetos. A palavra vem do grego e significa "muitas formas".
Na POO, o polimorfismo permite que objetos de diferentes classes (geralmente ligadas por herança) respondam à mesma "mensagem" ou chamada de método de maneiras específicas.
1. O que é Polimorfismo?
Imagine que você tem um controle remoto com o botão "Reproduzir".
 * Se você apontar para um CD Player, ele toca música.
 * Se você apontar para um DVD Player, ele exibe um vídeo.
 * Se você apontar para um Spotify, ele inicia um streaming.
O comando é o mesmo (reproduzir()), mas o resultado depende do tipo de objeto que o recebe.
2. Tipos de Polimorfismo
Existem duas formas principais de aplicar esse conceito:
A. Polimorfismo de Sobrescrita (Dinâmico)
Acontece quando uma subclasse altera o comportamento de um método que já existe na classe pai (usando a herança).
 * Classe Pai (Animal): Método fazerSom().
 * Classe Filha (Cachorro): Sobrescreve fazerSom() para retornar "Au Au".
 * Classe Filha (Gato): Sobrescreve fazerSom() para retornar "Miau".
B. Polimorfismo de Sobrecarga (Estático)
Acontece quando você tem métodos com o mesmo nome na mesma classe, mas que recebem parâmetros diferentes.
 * desenhar(raio) -> Desenha um círculo.
 * desenhar(largura, altura) -> Desenha um retângulo.
3. Desenvolvimento de um Exemplo (Conceitual)
Vamos criar um sistema de pagamentos onde tratamos diferentes métodos de forma polimórfica:
Estrutura Base
Classe Pagamento (Mãe):
    Método processar(valor):
        Exibir "Processando pagamento genérico..."

Classe Pix (Filha):
    Método processar(valor):
        Exibir "Gerando QR Code para " + valor

Classe Cartao (Filha):
    Método processar(valor):
        Exibir "Conectando à operadora para cobrar " + valor

O "Poder" do Polimorfismo
A grande vantagem é que você pode criar uma lista de pagamentos mistos e processar todos com um único comando:
Lista de contas = [Novo Pix(), Novo Cartao(), Novo Pix()]

Para cada item na lista:
    item.processar(100.00) 
    # O sistema decide na hora qual método chamar: Pix ou Cartão!

4. Vantagens do Polimorfismo
 * Flexibilidade: Você pode adicionar novos tipos de objetos (ex: PagamentoCripto) sem precisar alterar o código que processa a lista de pagamentos.
 * Abstração: O programador que usa a classe não precisa saber se o objeto é um Pix ou Cartão, ele só precisa saber que o objeto "sabe se processar".
 * Código Limpo: Evita o uso excessivo de blocos if/else ou switch para verificar o tipo do objeto.
5. Resumo da POO
Agora que passamos pelos 4 pilares, veja como eles se conectam:
 * Classe: O molde.
 * Objeto: O produto do molde.
 * Encapsulamento: Protege os dados do objeto.
 * Herança: Reaproveita código entre moldes parecidos.
 * Polimorfismo: Faz objetos diferentes agirem de formas diferentes sob o mesmo comando.
Gostaria que eu montasse um pequeno projeto prático (em código real) que utilize todos esses pilares juntos para você ver a "mágica" acontecer?

