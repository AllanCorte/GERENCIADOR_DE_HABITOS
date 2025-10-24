## GERENCIADOR_DE_HÁBITOS

Instruções rápidas para configurar e rodar este projeto Django no Windows (PowerShell).

### Requisitos
- Python 3.10+ (já usado no ambiente)
- Git

### 1) Criar e ativar o ambiente virtual
No PowerShell (na pasta do projeto):

```pwsh
python -m venv venv
venv\Scripts\Activate
```

Se já existir `venv` criado (recomendado), ative com `venv\Scripts\Activate`.

### 2) Instalar dependências
Instale as dependências listadas em `requirements.txt`:

```pwsh
pip install -r requirements.txt
```

> Observação: este repositório inclui um `requirements.txt` com os pacotes top-level necessários (ex.: Django, colorama). Para reproduzir exatamente o ambiente local, use `pip freeze > requirements-full.txt` no ambiente e compartilhe esse arquivo.

### 3) Configurar o banco e criar migrations
```pwsh
python manage.py migrate
```

### 4) Criar usuário admin (opcional)
```pwsh
python manage.py createsuperuser
```

### 5) Rodar o servidor de desenvolvimento
```pwsh
python manage.py runserver
```

Abra http://127.0.0.1:8000/ no navegador.

### 6) Boas práticas de Git
- Não comite a pasta do ambiente virtual (`venv/`) — já adicionamos `.gitignore` contendo `venv/`.
- Atualize `requirements.txt` quando adicionar/atualizar dependências:

```pwsh
# no venv ativado
pip install <pacote>
pip freeze --local > requirements.txt
git add requirements.txt
git commit -m "Atualiza dependências"
```

### 7) Como desfazer um commit local (ex.: se você comitou algo e não quer enviar)
- Desfazer último commit e manter alterações staged:
```pwsh
git reset --soft HEAD~1
```
- Desfazer último commit e manter alterações no working tree (não staged):
```pwsh
git reset --mixed HEAD~1
```
- Desfazer último commit e descartar alterações (perigoso):
```pwsh
git reset --hard HEAD~1
```

### 8) Enviar para o remote
Quando estiver pronto para enviar (push):

```pwsh
git add .
git commit -m "Minha mensagem"
git push origin main
```

Se precisar reescrever histórico (remover arquivos sensíveis já enviados), entre em contato — isso exige `git filter-repo` ou `filter-branch` e `git push --force`.

### 9) Notas adicionais
- Evite manter o projeto dentro de pastas sincronizadas como OneDrive para prevenir locks em `.git`.
- Se encontrar problemas com arquivos bloqueados durante `git gc` ou operações de limpeza, pause o OneDrive e feche editores antes de tentar novamente.

---

Se quiser, eu posso: criar um `requirements-full.txt` (com `pip freeze`) e enviar os commits para o remote. Deseja que eu faça o push agora? 
