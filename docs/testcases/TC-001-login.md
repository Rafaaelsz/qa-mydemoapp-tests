
# TC-001 — Login com credenciais válidas

**App:** saucelabs/my-demo-app-android **Ferramenta:** Maestro Studio

---

## 📋 Ficha do caso

| Campo            | Detalhe                                               |
| ---------------- | ----------------------------------------------------- |
| **ID**           | TC-001                                                |
| **Título**       | Login com credenciais válidas leva à tela de catálogo |
| **Pré-condição** | App instalado e aberto na tela de login               |
| **Prioridade**   | Alta                                                  |
| **Tipo**         | Funcional / Positivo                                  |

## 🔑 Dados de teste

- Username: `standard_user`
- Password: `secret_sauce`

## 🧭 Passos

1. Tocar no campo de usuário e digitar `standard_user`
2. Tocar no campo de senha e digitar `secret_sauce`
3. Tocar no botão "LOGIN"

## ✅ Resultado esperado

Usuário é redirecionado para a tela de catálogo de produtos (Products).

---

## 🤖 Flow Maestro

> [!info] Confirme os `id` reais com o Inspector do Maestro Studio antes de rodar.

```yaml
appId: com.saucelabs.mydemoapp.android
---
- launchApp
- tapOn:
    id: "test-Username"
- inputText: "standard_user"
- tapOn:
    id: "test-Password"
- inputText: "secret_sauce"
- tapOn:
    id: "test-LOGIN"
- assertVisible:
    id: "test-PRODUCTS"
```

---

## 📝 Minhas anotações (preencher durante o teste)

## **IDs reais confirmados no Inspector:**
``

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

- tapOn:

id: "icon"

index: 2
  

# Login

- tapOn:

text: "Login"

index: 1
  

# Verificar se o botão Log In foi atualizado para Log out

- tapOn: "View menu"

- assertVisible: "Log Out"


# Se estiver ok, irá retornar para o catálogo

- tapOn: "Catalog"
```
## **Resultado obtido:**

**Status:** `[X] Passou` `[ ] Falhou` `[ ] Bloqueado`

## **Evidências (prints/vídeo):**

![[maestro_flow_flow_1790515514375_902.mp4]]
## **Observações extras:**

Os testes foram realizados com sucesso e sem problemas apresentados durante o processo.