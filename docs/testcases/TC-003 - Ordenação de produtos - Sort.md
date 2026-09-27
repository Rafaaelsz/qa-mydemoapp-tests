**App:** saucelabs/my-demo-app-android **Ferramenta:** Maestro Studio

---

## Ficha do caso

| Campo            | Detalhe                                |
| ---------------- | -------------------------------------- |
| **ID**           | TC-003                                 |
| **Título**       | Ordenação de produtos por preço e nome |
| **Pré-condição** | Tela de catálogo visível               |
| **Prioridade**   | Média                                  |
| **Tipo**         | Funcional                              |

## Passos

1. Tocar no ícone/menu de ordenação (geralmente um ícone de filtro no topo)
2. Selecionar a opção "Price (low to high)"
3. Observar a ordem dos produtos exibidos
4. Repetir selecionando "Price (high to low)" e "Name (A to Z)"

## Resultado esperado

A lista de produtos reordena corretamente conforme o critério selecionado, sem duplicar ou sumir com nenhum item.

---

## Flow Maestro

Confirme os `id` reais com o Inspector do Maestro Studio antes de rodar — o ícone de ordenação e as opções do menu variam de nome conforme a versão do app.

```yaml
appId: com.saucelabs.mydemoapp.android
---
- launchApp
- tapOn:
    id: "test-Modal Selector Button"
- tapOn: "Name (A to Z)"
- assertVisible: "Sauce Labs Backpack"
- tapOn:
    id: "test-Modal Selector Button"
- tapOn: "Price (low to high)"
- tapOn:
    id: "test-Modal Selector Button"
- tapOn: "Price (high to low)"
```

---

## Minhas anotações (preencher durante o teste)

## **IDs reais confirmados no Inspector:**

**Critérios testados:**  Price low-high; Price high-low; Name A-Z; Name Z-A

## **Resultado obtido:**

**Status:** `[X] Passou` `[ ] Falhou` `[ ] Bloqueado`

## **Evidências (prints/vídeo):**

Na pasta "tc-videos" dentro do repo.

## **Observações extras:**
Os testes foram realizados com sucesso e sem problemas apresentados durante o processo. O resulado esperado foi obtido.

Foi observado que alguns dos itens estão com nomes de Strings, sendo assim, encontrado um erro no app. Os itens são as T-shirts com o valor de $ 15.99.