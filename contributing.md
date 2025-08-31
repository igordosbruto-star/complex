# Guia de Contribuição — Robô Universal de Vendas para WhatsApp (CodeX)

Obrigado por querer contribuir com o projeto **Robô Universal de Vendas para WhatsApp**! 🎉  
Este guia descreve como você pode colaborar de forma eficiente e organizada.

---

## 1. Como Contribuir
- **Reportar problemas:** Abra uma *issue* descrevendo claramente o problema, passos para reproduzir e ambiente utilizado.
- **Sugerir melhorias:** Use o template de *feature request* no GitHub para novas ideias ou recursos.
- **Contribuir com código:** Crie uma *branch* a partir da `main`, implemente suas mudanças e abra um *Pull Request* (PR).

---

## 2. Fluxo de Trabalho (Workflow)
1. **Fork/clone** o repositório ou crie uma nova *branch* no **CodeX**.
2. **Crie uma *issue*** descrevendo a tarefa ou problema (se ainda não existir).
3. **Desenvolva a feature/fix** em uma branch com o padrão:
   ```
   feature/nome-da-feature
   fix/descricao-curta-bug
   chore/descricao-curta
   ```
4. **Commit** usando a convenção de mensagens:
   ```
   tipo(escopo): descrição curta
   ```
   Exemplos:
   - `feat(catalogo): adicionar suporte a múltiplas imagens`
   - `fix(api): corrigir erro 500 ao criar pedido`
   - `chore(ci): atualizar workflow de build`

5. **Pull Request:** abra um PR vinculado à issue correspondente. Preencha o template, descrevendo:
   - O que foi alterado.
   - Como testar.
   - Prints ou exemplos (quando aplicável).

6. **Revisão:** o PR passará por revisão de outro colaborador e pelo **CodeX** (assistente de IA).

7. **Merge:** após aprovação e checagens de CI, o PR será integrado na branch `main`.

---

## 3. Padrões de Código
- **Linguagem principal:** C++ (C++17/20) com **SFML** e integrações.
- **Outras linguagens:** Python (scripts de automação), JavaScript/TypeScript (Node‑RED, integrações, UI).
- **Estilo:**
  - C++: `PascalCase` para classes, `camelCase` para métodos e variáveis.
  - Python: PEP 8 (snake_case).
  - JavaScript/TypeScript: camelCase.
- **Logs:** usar função `wr:p` com níveis (`info`, `warn`, `error`) para padronizar saídas.
- **Testes:** sempre incluir testes unitários e, quando aplicável, testes de integração.

---

## 4. Diretrizes para Issues
- Título claro e objetivo.  
- Descrição detalhada com passos para reproduzir o problema ou detalhar a feature.  
- Etiquetar corretamente (ex.: `bug`, `feature`, `doc`, `infra`).  
- Se a issue estiver relacionada a outra, referenciar com `#id`.

---

## 5. Diretrizes para Pull Requests
- Um PR deve resolver **apenas uma issue** ou um conjunto de tarefas relacionadas.  
- Sempre rebase antes de abrir o PR.  
- Utilize o template de PR disponível no repositório.  
- Inclua testes automatizados quando possível.  
- Garanta que o *CI/CD* esteja passando sem erros antes da revisão final.  

---

## 6. Comunicação
- Use os comentários do GitHub para discutir dúvidas ou sugerir melhorias.  
- Para dúvidas rápidas ou ideias, utilize os canais de comunicação da equipe.  
- Respeite a comunidade: mantenha o tom profissional e colaborativo.

---

## 7. Licença
Este projeto está licenciado sob a licença **MIT**. Ao contribuir, você concorda que seu código poderá ser utilizado sob os termos desta licença.

---

✨ Obrigado por ajudar a construir o **Robô Universal de Vendas (CodeX)** e tornar a automação de vendas acessível a todos os empreendedores!

