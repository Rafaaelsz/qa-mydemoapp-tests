**App:** saucelabs/my-demo-app-android **Ferramenta:** Maestro Studio

---

## Ficha do caso

| Campo            | Detalhe                                                                                |
| ---------------- | -------------------------------------------------------------------------------------- |
| **ID**           | TC-005                                                                                 |
| **Título**       | Reset do estado do app via botão de reset no menu                                      |
| **Pré-condição** | Login realizado; pelo menos 1 item no carrinho e alguma ordenação customizada aplicada |
| **Prioridade**   | Média                                                                                  |
| **Tipo**         | Funcional                                                                              |

## Passos

1. Tocar no botão de reset do menu após aplicar as pré-condições
2. Aguardar o app processar o reset
3. Verificar o estado do carrinho
4. Verificar se a ordenação de produtos voltou ao padrão

## Resultado esperado

Carrinho é esvaziado e preferências voltam ao estado inicial, sem crash ou tela travada.

Por que testar isso: esse é o mecanismo que os QAs da Sauce Labs usam pra "limpar" o app entre testes automatizados — se ele falhar, todos os outros testes automatizados que dependem dele ficam não-confiáveis (o conceito de flakiness que vimos na teoria).

---

## Flow Maestro

Confirme os `id` reais com o Inspector do Maestro Studio antes de rodar — o Maestro tem o comando `longPressOn` específico pra esse tipo de interação.

```yaml
appId: com.saucelabs.mydemoapp.android
---
- launchApp
- tapOn: "Sauce Labs Backpack"
- tapOn: "ADD TO CART"
- longPressOn:
    id: "test-App Icon"
- assertNotVisible: "1"
```

---

## Minhas anotações (preencher durante o teste)
Verificado que ao clicar (dependendo do estado da ordenação) em quase todos os itens sem ser algumas das mochilas, o app apresenta crashes constantes, sendo um problema de Severidade Gravíssima.

Foi verificado também que todas as mochilas (com exceção da primeira apresentada na tela de inicio), na tela do produto e na tela do checkout apresenta a cor escolhida somente como cinza.

## **IDs reais confirmados no Inspector:**
```yaml
appId: com.saucelabs.mydemoapp.android

---

- launchApp:

clearState: true

  

# Alterando a ordenação do catálogo

- tapOn: "Shows current sorting order and displays available sorting options"

- tapOn: "Name - Descending"

  

# Adicionando item no carrinho para validação do reset de estado do app

- tapOn: "Product Image"

- scrollUntilVisible:

element: "Add to cart"

- tapOn: "Add to cart"

  

# Verificando o carrinho com o item

- tapOn:

text: "Displays number of items in your cart"

index: 1

  

# Voltando para a tela inicial

- tapOn: "View menu"

- tapOn: "Catalog"

  

# Resetando o estado do app

- tapOn: "View menu"

- tapOn: "Reset App State"

- tapOn: "RESET APP"

  

# Verificando se o estado do app foi resetado

- assertVisible: "App State has been reset."

- tapOn: "OK"

- tapOn: "Displays number of items in your cart"

  

# Voltando para a tela inicial novamente

- assertVisible: "No Items"

- tapOn: "Go Shopping"
```

## **Estado do carrinho após o reset:**
O carrinho foi esvaziado.

## **Ordenação voltou ao padrão?**
Não.

## **Resultado obtido:**

**Status:** `[ ] Passou` `[X] Falhou` `[ ] Bloqueado`

## **Evidências (prints/vídeo):**

## **Observações extras:**
O estado app não foi totalmente resetado, visto que ao realizar o reset e voltar para a tela inicial, o filtro de ordenação dos produtos não foi resetado.
