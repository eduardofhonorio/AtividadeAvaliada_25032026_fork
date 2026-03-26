# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Eduardo Ferreira Honório  
RA: 25000412
Data: 25/03/2026

---

# 1. Definição do MVP
Descreva aqui **qual parte do sistema** foi incluída no seu MVP.  
Explique claramente: Meu MVP passa pela venda de balcão e a gestão do estoque, da identificação do produto e cliente até a baixa automática de estoque e geração de todos os registros financeiros da farmácia.

- O que está **dentro** do MVP: o cadastro de produtos e clientes, o registro e a realização de vendas(à vista e a prazo), consultar e atualizaçao automática de estoque, emissão de comprovante e lançamentos de contas à pagar e a receber vindo das compras e vendas.
  
- O que está **fora** do MVP:  Transferência das mercadorias entre as unidades, relatórios de auditoria e gestão de convênios empresariais.
  
- Por que você fez essas escolhas: Eu fiz essa escolha de MVP pois ela se assemelha muito ao meu trabalho, que é em um atacadista que utiliza de um sistema ERP bem parecido com a da farmácia, por eu trabalhar no escritório e alternar entre um "atendente" e "gerente" ao mesmo tempo, me facilitou bastante na hora de escolher esse MVP.

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva **cada RN** de forma clara.

**RN01 —** **Proibir Medicação:** caso a medicação seja controlada e necessite de uma receita, ela só será liberada quando uma assinatura ou o registro do médico for exibida ao farmacêutico.

**RN02 —** **Bloquear produto sem estoque:** caso o estoque do produto esteja zerado, o sistema deve impossibilitar o atendente de inserir o produto no orçamento de venda do cliente.

**RN03 —**  **Vencimento e Bloqueio**: o cliente que não pagar uma compra feita à prazo em até 20 dias, vai ter a conta bloqueada e será impossibilitado de fazer um novo pedido, até o recebimento do pedido anterior ser confirmado.

**RN04 —** **Alerta de preço mínimo**: o produto não pode ser vendido a um preço inferior ao preço de custo que foi pago pela farmácia, caso a margem de lucro seja inferior a 10%, enviar uma mensagem com alerta questionando se o gerente inseriu o preço de venda correto.

**RN05 —**  **Atualização de estoque**: Toda vez que algum produto for vendido, o estoque deve ser atualizado no sistema, por exemplo: o estoque de um produto é 54 e o cliente comprou 5 unidades, o estoque vai para 49 unidades.


---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 —**  **Cadastro de Produtos:** O sistema deve permitir o gerente cadastrar, editar e excluir todos os produtos da farmácia.

**RF02 —**  **Registro de Vendas:** O sistema deve permitir o atendente registrar as vendas e a forma de pagamento, com acesso à todos os produtos e clientes da farmácia.

**RF03 —**  **Pesquisa de Itens:**: O sistema deve permitir o atendente pesquisar e consultar produtos pelo nome ou código.

**RF04 —**  **Cadastro de Clientes:**: O sistema deve permitir cadastrar os clientes contendo as informações:(Nome completo, telefone, gênero e CPF).

**RF05 —**  **Baixa de Estoque:**: O sistema deve permitir o gerente adicionar, editar ou remover o estoque em todos os produtos cadastrados.

**RF06 —**  **Gestão de contas a receber:** O sistema deverá criar uma categoria específica para compras feitas à prazo, assim, indicando se o pedido já foi pago na hora da compra ou não, caso não tenha pago, ficará com um título em amarelo escrito "À PRAZO" no pedido.

**RF07 —**  **Registro de compras:** O sistema deve registrar a entrada de notas fiscais dos fornecedores da farmácia, já atualizando e adicionando o estoque dos produtos que chegaram.

**RF08 —**  **Emissão de Comprovante:** O sistema deve gerar um orçamento de venda ao finalizar a compra, mostrando:(Nome do cliente, forma de pagamento, os produtos com seu valor unitário e o valor total da venda).


---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 —** **Usabilidade:** O registro da venda pelo atendente deve ser feita em no máximo 7 cliques, garantindo agilidade para o cliente.

**RNF02 —**  **Segurança:** O sistema deve exigir login e senha, conforme as permissões de cada usuário(Atendente, farmacêutico, gerente, financeiro e administrador);

**RNF03 —**  **Disponibilidade:** O banco de dados ceverá permitir o sistema de ser utilizado mesmo sem internet, principalmente o registro de vendas.

**RNF04 —**  **Desempenho**: A consulta de estoque, produtos e preço deve retornar resultados em menos de 1,5 segundos.


---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:

<img width="636" height="389" alt="image" src="https://github.com/user-attachments/assets/a018fd58-6e8d-4658-a246-9c21644f15c1" />


---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UC01 — Realizar Venda**
**Ator(es):** Atendente
**Descrição:** Processar o registro de venda, da identificação do item até a finalização do pagamento.
**Pré-condições:**  Usuário autenticado e produtos com saldo em estoqueee
**Pós-condições:**  Registro de venda salvo, estoque atualizado e comprovante gerado.

### Fluxo Principal
1.  O atendente inicia a venda no sistema da farmácia.
2.  o atendente identifica o produto
3.  o sistema consulta o estoque.
4.  o atendente insere a quantidade do produto.
5.  o sistema adiciona ao carrinho e já informa o valor total para o cliente pagar.
6.  o atendente seleciona a formde pagamento.
7.  o sistema atualiza o estoque.
8.  o sistema emite o comprovante.
9.  o sistema finaliza o orçamento de venda.

### Fluxos Alternativos / Exceções
- FA01 —  Medicamento Controlado: Se o produto for controlado, aciona o UC05 - Validar Receita.
- FA02 —  Cliente novo: se o cliente ainda não tiver cadastro, aciona o UC06 - Cadastrar Cliente.
- FA03 - Pagamento por prazo: se selecionado o pagamento por prazo, aciona o UC07 - Venda a Prazo.

### Relacionamentos
- **Include:** UC02,UC08,UC10
- **Extend:** UC05,UC06,UC07

<img width="365" height="379" alt="image" src="https://github.com/user-attachments/assets/f4b58e72-7fd7-4ab1-83e2-ad97e50b64da" />

---

## **UC02 — Consultar Estoque**
**Ator(es):** Atendente, Gerente.
**Descrição:** Verificar se o produto está disponível na farmácia.
**Pré-condições:**  Usuário autenticado e produto previamente cadastrado no sistema.
**Pós-condições:**  Informações de saldo e preço exibidas na tela.


### Fluxo Principal
1.  Usuário informa o código ou nome do produto.
2.  Sistema realiza a busca no banco de dados local.
3.  Sistema retorna a quantidade disponível e o preço unitário.

### Fluxos Alternativos / Exceções
- FA01 —  Produto não encontrado: Sistema exibe mensagem de erro "Produto não localizado".

  <img width="219" height="227" alt="image" src="https://github.com/user-attachments/assets/3f414497-1071-4828-a3aa-2f302fa05232" />

 ---

 ## **UC03 — Autenticar Usuário**
**Ator(es):** Todos os Usuários.
**Descrição:** Validar o acesso ao sistema através de credenciais.
**Pré-condições:** Sistema operacional e conexão com o banco de dados ativa.
**Pós-condições:** Sessão do usuário iniciada com as permissões do seu perfil.



### Fluxo Principal
1.  Usuário insere login e senha.
2.  Sistema valida as credenciais contra a base de dados.
3.  Sistema libera o acesso ao Dashboard principal.

### Fluxos Alternativos / Exceções
FA01 — Credenciais Inválidas: Sistema informa erro e nega o acesso.


<img width="182" height="227" alt="image" src="https://github.com/user-attachments/assets/becfde14-4540-4a5b-bed4-1bd7e4424575" />

---

 ## **UC04 — Manter Produto**
**Ator(es):** Gerente
**Descrição:** Gerenciar o catálogo de produtos (Incluir, Alterar, Inativar).
**Pré-condições:** Usuário logado com perfil de Gerente.
**Pós-condições:** Dados do produto persistidos no banco de dados..


### Fluxo Principal
1.  Gerente acessa o módulo de produtos.
2.  Seleciona a operação (Novo ou Editar).
3.  Preenche os campos (Descrição, Custo, Venda, Fabricante).
4.  Sistema valida a RN04 (Preço Mínimo).
5.  Sistema salva as alterações.

<img width="149" height="343" alt="image" src="https://github.com/user-attachments/assets/35642e1f-c7ac-44a4-964f-7f4d447f334f" />

--

 ## **UC05 — Validar Receita**
**Ator(es):** Farmacêutico
**Descrição:** Conferência técnica de receitas para medicamentos de uso controlado.
**Pré-condições:** Item identificado como "controlado" no UC01.
**Pós-condições:** Venda autorizada ou item bloqueado para venda.


### Fluxo Principal
1.  Sistema solicita validação para item controlado.
2.  Farmacêutico analisa a receita física.
3.  Insere os dados do prescritor (CRM, Nome).
4.  Confirma a autorização no sistema.
5.  Sistema salva as alterações.

### Fluxos Alternativos / Exceções
FA01 — Receita Inválida: Farmacêutico nega a venda; o item é removido do carrinho.


   
<img width="275" height="220" alt="image" src="https://github.com/user-attachments/assets/20fc9e7a-786f-4529-af9b-27fbda5a27d8" />

---

 ## **UC06 — Cadastrar Cliente**
**Ator(es):** Atendente
**Descrição:** Registrar novos clientes no banco de dados durante a venda.
**Pré-condições:** Cliente não localizado no banco de dados através do CPF.
**Pós-condições:** Novo registro de cliente salvo no sistema.



### Fluxo Principal
1.  Atendente solicita CPF do cliente.
2.  Preenche Nome e Telefone
3.  Salva o registro para vincular à venda atual.

### Fluxos Alternativos / Exceções


<img width="233" height="220" alt="image" src="https://github.com/user-attachments/assets/3ccce1b6-e74f-4cd1-9acd-ee3815968351" />

---

 ## **UC07 — Registrar Venda a Prazo**
**Ator(es):** Financeiro
**Descrição:** Geração de duplicatas para pagamentos futuros (convênios/recorrentes).
**Pré-condições:** Cliente identificado e com crédito aprovado (RN03).
**Pós-condições:** Título financeiro gerado em "Contas a Receber".



### Fluxo Principal
1.  Atendente seleciona opção "A Prazo".
2.  Sistema valida o histórico do cliente.
3.  Sistema gera as parcelas e datas de vencimento.
4.  Finaliza a operação vinculando o débito ao CPF

### Fluxos Alternativos / Exceções


<img width="248" height="220" alt="image" src="https://github.com/user-attachments/assets/76f0bb0f-a081-4aee-afd6-3aa9dcdec41e" />

---

 ## **UC08 — Atualizar Estoque**
**Ator(es):** Sistema 
**Descrição:** Sincronizar o saldo físico após movimentações de entrada ou saída.
**Pré-condições:** Finalização de uma Venda (UC01) ou de uma Compra (UC09).
**Pós-condições:** Saldo atualizado e alerta de estoque mínimo gerado, se necessário.



### Fluxo Principal
1.  Sistema recebe o sinal de conclusão da transação.
2.  Subtrai (venda) ou Soma (compra) as quantidades.
3.  Verifica se o saldo atingiu o nível crítico (RN05)

### Fluxos Alternativos / Exceções

<img width="143" height="204" alt="image" src="https://github.com/user-attachments/assets/ff777c4e-1317-4c06-ba04-708c679d5dbd" />

---

 ## **UC09 — Registrar Compra**
**Ator(es):** Gerente
**Descrição:** Entrada de mercadorias via nota fiscal de fornecedores.
**Pré-condições:** Fornecedor cadastrado e mercadoria entregue.
**Pós-condições:** Estoque incrementado e lançamento em "Contas a Pagar".



### Fluxo Principal
1.  Gerente insere os dados da Nota Fiscal.
2.  Lista os itens e quantidades adquiridas.
3.  Sistema executa o UC08 (Atualizar Estoque).
4.  Sistema gera o lançamento financeiro no Contas a Pagar.

<img width="146" height="213" alt="image" src="https://github.com/user-attachments/assets/726448d5-110c-42ff-8b7e-95371eef7ab4" />


--

 ## **UC10 — Emitir Comprovante**
**Ator(es):** Sistema
**Descrição:** Geração do documento de resumo da venda para o cliente.
**Pré-condições:** Venda concluída e pagamento confirmado no UC01.
**Pós-condições:** Documento enviado para a impressora ou exibido em tela.



### Fluxo Principal
1.  Sistema compila itens, valores e impostos.
2.  Gera o layout do comprovante.
3.  Envia o comando para o spooler de impressão.



### Fluxos Alternativos / Exceções


<img width="125" height="149" alt="image" src="https://github.com/user-attachments/assets/ec18e21e-4e8c-4645-b9f4-c6fad3ec225b" />



> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).


