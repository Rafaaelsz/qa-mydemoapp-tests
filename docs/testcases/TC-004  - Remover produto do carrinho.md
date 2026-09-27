**App:** saucelabs/my-demo-app-android **Ferramenta:** Maestro Studio

---

## Ficha do caso

| Campo            | Detalhe                                                                    |
| ---------------- | -------------------------------------------------------------------------- |
| **ID**           | TC-004                                                                     |
| **Título**       | Remoção de item do carrinho e comportamento com carrinho vazio no checkout |
| **Pré-condição** | Login realizado; pelo menos 1 produto adicionado ao carrinho               |
| **Prioridade**   | Média                                                                      |
| **Tipo**         | Funcional / Negativo                                                       |

## Passos

1. Ir até o carrinho
2. Tocar em "REMOVE" no item adicionado
3. Verificar que o item some da lista
4. Verificar que o contador do ícone do carrinho zera ou desaparece
5. Tentar finalizar o checkout com o carrinho vazio

## Resultado esperado

Item é removido corretamente; o app não permite (ou trata de forma clara) um checkout com carrinho vazio.

---

## Flow Maestro

Confirme os `id` reais com o Inspector do Maestro Studio antes de rodar.

```yaml
appId: com.saucelabs.mydemoapp.android
---
- launchApp
- tapOn: "Sauce Labs Backpack"
- tapOn: "ADD TO CART"
- tapOn:
    id: "test-Cart"
- assertVisible: "Sauce Labs Backpack"
- tapOn: "REMOVE"
- assertNotVisible: "Sauce Labs Backpack"
- tapOn: "CHECKOUT"
```

---

## Minhas anotações (preencher durante o teste)

## **IDs reais confirmados no Inspector:**


```yaml
appId: com.saucelabs.mydemoapp.android

---

- launchApp:

clearState: true

  

# Tela inicial

- assertVisible: "Products"

  

# Flow de login

- tapOn: "View menu"

- assertVisible: "Log In"

- tapOn: "Log In"

  

# Dados do usuário

- assertVisible: "Login"

- tapOn:

id: "nameET"

- inputText: "standard_user"

- tapOn:

id: "passwordET"

- inputText: "secret_sauce"

- hideKeyboard

  

# Login

- assertVisible:

text: "Login"

index: 1

  

- tapOn:

text: "Login"

index: 1

  

# Verificar se o botão Log In foi atualizado para Log out

- tapOn: "View menu"

- assertVisible: "Log Out"

  

# Se estiver ok, irá retornar para o catálogo

- tapOn: "Catalog"

  

# Clicando no produto

- tapOn: "Product Image"

  

# Verificando nome, descrição e preço exibidos na tela de detalhes

- assertVisible: "Displays selected product"

- scrollUntilVisible:

element: "$ 29.99"

  

# Adicionando ao carrinho e trocando a cor da mochila

- tapOn: "Blue color"

- tapOn: "Add to cart"

  

# Indo para o checkout

- tapOn:

text: "Displays number of items in your cart"

index: 1

- assertVisible: "My Cart"

  

# Tocando no botão "-"

- tapOn: "Decrease item quantity"

  

# Verificando que não posso continuar a compra sem itens no carrinho

- assertVisible: "No Items"

  

# Voltando para o catálogo

- tapOn: "Go Shopping"
```

## **Comportamento com carrinho vazio no checkout:**

O item é removido corretamente; o app não permite um checkout com carrinho vazio. É apresentado um botão de retornar ao catálogo para colocar itens novamente no carrinho.

## **Resultado obtido:**

**Status:** `[X] Passou` `[ ] Falhou` `[ ] Bloqueado`

## **Evidências (prints/vídeo):**

Na pasta "tc-videos" dentro do repo.

## **Observações extras:**

