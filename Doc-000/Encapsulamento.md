O Encapsulamento é o pilar da POO voltado à segurança e ao controle. Ele consiste em "esconder" os detalhes internos de como um objeto funciona e proteger seus dados de acessos indevidos ou acidentais vindos de fora.
Imagine um Controle Remoto: você interage com os botões (interface pública), mas não precisa (nem deve) mexer nos circuitos internos para trocar de canal. Se todos pudessem mexer nos fios internos, o risco de quebrar o aparelho seria enorme.
1. O que é Encapsulamento?
Encapsular é agrupar dados (atributos) e os métodos que manipulam esses dados em uma única unidade (a classe), restringindo o acesso direto ao estado do objeto.
Em termos práticos, os atributos geralmente são definidos como privados, e o acesso a eles é feito através de métodos públicos.
2. Modificadores de Acesso
Para implementar o encapsulamento, as linguagens de programação utilizam "palavras-chave" que definem quem pode ver o quê:
| Modificador | Visibilidade | Analogia |
|---|---|---|
| Público (public) | Todos podem ver e alterar. | A fachada de uma loja. |
| Privado (private) | Apenas a própria classe pode ver. | O cofre dentro do escritório da loja. |
| Protegido (protected) | A classe e suas filhas (herança) podem ver. | Um segredo de família. |
3. O uso de Getters e Setters
Como os atributos são privados, usamos métodos especiais para interagir com eles:
 * Getter (Obter): Um método que retorna o valor do atributo.
 * Setter (Definir): Um método que altera o valor do atributo, permitindo validação.
Exemplo de Desenvolvimento (Conceitual)
Se tivéssemos uma classe ContaBancaria, não deveríamos permitir que alguém alterasse o saldo diretamente para um valor negativo.
Classe ContaBancaria:
    Privado saldo = 0

    Método Público depositar(valor):
        Se valor > 0:
            saldo = saldo + valor
        Senão:
            Exibir "Valor inválido!"

    Método Público getSaldo():
        Retornar saldo

Por que isso é melhor? Se o saldo fosse público, qualquer parte do programa poderia fazer conta.saldo = -5000 sem passar por nenhuma regra de segurança.
4. Vantagens do Encapsulamento
 * Controle de Dados: Você decide quais dados podem ser lidos ou alterados.
 * Validação: O objeto pode impedir que valores inconsistentes (como uma idade negativa ou um CPF inválido) sejam salvos.
 * Facilidade de Manutenção: Se você mudar o nome de uma variável interna, o resto do sistema não quebra, pois ele só conhece os métodos (a interface), não a variável.
 * Flexibilidade: Você pode criar atributos que são "somente leitura" (criando apenas o Getter) ou "somente escrita".
5. Resumo Prático
Encapsular não é apenas "esconder" por esconder, mas sim criar uma fronteira protegida. O objeto passa a ser responsável pela integridade dos seus próprios dados.
> "Peça ao objeto para fazer algo, não mexa nas entranhas dele."
> 
cobrimos os principais conceitos (Classe, Objeto, Herança e Encapsulamento)

