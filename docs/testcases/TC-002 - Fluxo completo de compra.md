
**App:** saucelabs/my-demo-app-android **Ferramenta:** Maestro Studio

---

## Ficha do caso

|Campo|Detalhe|
|---|---|
|**ID**|TC-002|
|**Título**|Fluxo completo de compra, do catálogo até a confirmação do pedido|
|**Pré-condição**|Login realizado com `standard_user` / `secret_sauce`; carrinho vazio|
|**Prioridade**|Alta|
|**Tipo**|Funcional / E2E|

## Passos

1. Na tela de catálogo, tocar no produto "Sauce Labs Backpack"
2. Verificar nome, descrição e preço exibidos na tela de detalhes
3. Tocar em "ADD TO CART"
4. Tocar no ícone do carrinho (topo direito)
5. Verificar que o item aparece com nome, preço e quantidade = 1
6. Tocar em "CHECKOUT"
7. Preencher First Name, Last Name e Postal Code
8. Tocar em "CONTINUE"
9. Verificar nome do produto, preço, subtotal, taxa e total
10. Tocar em "FINISH"

## Resultado esperado

Mensagem de confirmação do pedido é exibida (ex: "Thank you for your order").

---

## Flow Maestro

Confirme os `id` reais com o Inspector do Maestro Studio antes de rodar.

```yaml
appId: com.saucelabs.mydemoapp.android
---
- launchApp
- tapOn: "Sauce Labs Backpack"
- assertVisible: "Sauce Labs Backpack"
- tapOn: "ADD TO CART"
- tapOn:
    id: "test-Cart"
- assertVisible: "Sauce Labs Backpack"
- tapOn: "CHECKOUT"
- tapOn:
    id: "test-First Name"
- inputText: "Rafael"
- tapOn:
    id: "test-Last Name"
- inputText: "Silva"
- tapOn:
    id: "test-Zip/Postal Code"
- inputText: "88130000"
- tapOn: "CONTINUE"
- assertVisible: "Total"
- tapOn: "FINISH"
- assertVisible: "Thank you"
```

---

## Minhas anotações (preencher durante o teste)

## **IDs reais confirmados no Inspector:**

```yaml
appId: com.saucelabs.mydemoapp.android

---

- launchApp:

clearState: true

  

# Clicando no produto

- tapOn: "Product Image"

  

# Verificando nome, descrição e preço exibidos na tela de detalhes

- assertVisible: "Displays selected product"

- scrollUntilVisible:

element: "$ 29.99"

  

# Adicionando ao carrinho e trocando a cor da mochila

- tapOn: "Gray color"

- tapOn: "Add to cart"

  

# Indo para o checkout

- tapOn:

text: "Displays number of items in your cart"

index: 1

- assertVisible: "My Cart"

  

# Pagamento

- tapOn: "Proceed To Checkout"

  

# Adicionando credenciais de login

- assertVisible: "Login"

- tapOn:

id: "nameET"

- inputText: "standard_user"

- tapOn:

id: "passwordET"

- inputText: "secret_sauce"

- hideKeyboard

- assertVisible:

id: "loginBtn"

- tapOn:

id: "loginBtn"

  

# Adicionando dados de endereço de envio

- assertVisible: "Checkout"

- tapOn:

id: "fullNameET"

- inputText: "Rafael Tavares"

- tapOn: "Next"

- inputText: "R. Verão do Cometa"

- hideKeyboard

- tapOn:

id: "cityET"

- inputText: "Itaquera"

- tapOn:

id: "stateET"

- inputText: "SP"

- hideKeyboard

- tapOn:

id: "zipET"

- inputText: "8223-640"

- tapOn:

id: "countryET"

- inputText: "Brazil"

- hideKeyboard

  

# Indo para o pagamento

- scrollUntilVisible:

element: "To Payment"

- tapOn: "To Payment"

  

# Adicionando informações de cobrança

- assertVisible: "Enter a payment method"

- tapOn:

id: "nameET"

- inputText: "Rafael Tavares"

- tapOn: "Next"

- inputText: "5118159387903372"

- hideKeyboard

- tapOn:

id: "expirationDateET"

- inputText: "0928"

- tapOn:

id: "securityCodeET"

- inputText: "484"

- tapOn: "Done"

  

# Scrollando até a opção que salva as informações

- scrollUntilVisible:

element: "My billing address is the same as my shipping address."

- hideKeyboard

  

# Verificando as informações do pedido

- tapOn: "Review Order"

- scrollUntilVisible:

element: "Estimated to arrive within 3 weeks."

  

# Finalizando pedido

- tapOn: "Place Order"

  

# Conferindo se o pedido foi completo e voltando para a página de comprar

- assertVisible: "Checkout Complete"

- tapOn: "Continue Shopping"

- assertVisible: "Products"
```

## **Resultado obtido:**

**Status:** `[X] Passou` `[ ] Falhou` `[ ] Bloqueado`

## **Evidências (prints/vídeo):**
![[tc-002-checkout.mp4]]
## **Observações extras:**

Os testes foram realizados com sucesso e sem problemas apresentados durante o processo.