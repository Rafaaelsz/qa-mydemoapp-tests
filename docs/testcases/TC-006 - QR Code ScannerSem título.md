**App:** saucelabs/my-demo-app-android **Ferramenta:** Maestro Studio

---

## Ficha do caso

| Campo            | Detalhe                                                                              |
| ---------------- | ------------------------------------------------------------------------------------ |
| **ID**           | TC-006                                                                               |
| **Título**       | Leitura de QR Code e tratamento de permissão de câmera                               |
| **Pré-condição** | App instalado; permissão de câmera ainda não concedida (testar o pior caso primeiro) |
| **Prioridade**   | Baixa                                                                                |
| **Tipo**         | Funcional / Permissão                                                                |

## Passos

1. Abrir o menu lateral
2. Tocar em "QR CODE SCANNER"
3. Na primeira vez, negar a permissão de câmera → verificar comportamento
4. Reabrir e agora conceder a permissão de câmera
5. Apontar para um QR Code contendo uma URL válida

## Resultado esperado

- Ao negar permissão: app exibe mensagem clara, sem crash
- Ao conceder: câmera abre normalmente
- Ao ler QR com URL: o navegador abre automaticamente com o link

---

## Flow Maestro

Permissões de câmera geralmente precisam ser tratadas com `assertVisible`/`tapOn` no dialog nativo do Android, ou configuradas antes via `launchApp` com permissions. Confirme o comportamento real no Inspector do Studio.

```yaml
appId: com.saucelabs.mydemoapp.android
---
- launchApp:
    permissions:
      camera: "deny"
- tapOn:
    id: "test-Menu"
- tapOn: "QR CODE SCANNER"
- assertVisible: "permission"
```

---

## Minhas anotações (preencher durante o teste)
Teste não funcionou corretamente por conta do hardware do meu notebook/emulador.

## **IDs reais confirmados no Inspector:**

```yaml
appId: com.saucelabs.mydemoapp.android

---

- launchApp:

clearState: true

  

# Abrindo o QR code scanner

- tapOn: "View menu"

- tapOn: "QR Code Scanner"
```

## **Comportamento ao negar permissão:**
O app não pediu permissão para acessar a câmera.
## **Comportamento ao conceder permissão:**
O app não pediu permissão para acessar a câmera.

## **Resultado obtido:**

**Status:** `[ ] Passou` `[X] Falhou` `[ ] Bloqueado`

## **Evidências (prints/vídeo):**
Na pasta "tc-videos" dentro do repo.

## **Observações extras:**