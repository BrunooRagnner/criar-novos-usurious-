
A última senha do admin que apareceu nos logs foi:

```
⚠️ ADMIN CRIADO COM SENHA: 4rF1qSst2Ds
```

Portanto, tente:

- **Email:** `admin@sistema.com`
- **Senha:** `4rF1qSst2Ds`

Caso não funcione, execute no terminal para ver a senha mais recente:

```bash
fly logs | grep "ADMIN CRIADO COM SENHA"
```

Se quiser **resetar a senha** manualmente, posso gerar um código para você rodar no backend. Só me avise! 🚀

# criar-novos-usurious-
criar-novos usurious 
criar-novos usurious ## 🔑 Como alterar a senha do admin

Existem **3 formas** de alterar a senha do administrador. Escolha a mais fácil para você:

---

### ✅ Opção 1 – Pela interface do sistema (se você já estiver logado)

1. Faça login com a senha atual (`ArYLonhsgDY`).
2. No menu lateral ou superior, vá em **Configurações** → **Usuários** (ou **Administração** → **Usuários**).
3. Localize o usuário `admin@sistema.com` e clique em **Editar**.
4. Altere a senha e confirme.
5. Salve.

> ⚠️ Se ainda não tiver uma tela de edição de usuários, use as opções abaixo.

---

### ✅ Opção 2 – Via terminal (Fly.io) – **recomendado para suporte**

1. Acesse o servidor remoto:
   ```bash
   fly ssh console
   ```

2. Dentro do container, execute o Python:
   ```bash
   python3
   ```

3. Cole este código e pressione **Enter** (substitua `"nova_senha_123"` pela senha desejada):
   ```python
   from main import SessionLocal, Usuario, get_password_hash

   db = SessionLocal()
   admin = db.query(Usuario).filter(Usuario.email == "admin@sistema.com").first()

   if admin:
       admin.senha_hash = get_password_hash("nova_senha_123")
       db.commit()
       print("✅ Senha alterada para: nova_senha_123")
   else:
       print("❌ Admin não encontrado")

   db.close()
   ```

4. Saia do Python (`Ctrl+D` ou digite `exit()`).
5. Saia do SSH (`exit`).

Agora a nova senha é **`nova_senha_123`** (ou a que você escolheu).

---

### ✅ Opção 3 – Via rota da API (se tiver token de admin)

Se você já tiver um token de admin (após login), pode usar esta requisição:

**Endpoint:** `PUT /api/v1/usuarios/{id}/status` – não serve para senha.  
**Para alterar senha**, precisaria de uma rota específica, mas por enquanto use a opção 2.

---

## 📝 Como tornar a senha "copiável e colável"

Para facilitar o cliente copiar a senha, sempre envie ela em **texto simples** (sem caracteres especiais que confundam) e destaque em negrito.

**Exemplo de envio por WhatsApp:**

```
Sua nova senha é: **NovaSenha@123**
```

Se quiser, no futuro, podemos adicionar um botão "Copiar senha" na tela de login ou na mensagem de recuperação.

---

## 🔐 Recomendação final

- Após alterar, **teste o login** antes de enviar a nova senha ao cliente.
- Se o cliente ainda estiver com problemas, gere uma senha temporária e oriente-o a alterar imediatamente.

Precisa de ajuda para executar a opção 2? Posso detalhar passo a passo. 🚀
