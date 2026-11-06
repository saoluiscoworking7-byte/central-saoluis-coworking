# Central São Luís Coworking

Sistema de gestão do São Luís Coworking: painel, reservas, clientes, contratos, financeiro, funil comercial e cadastros. Funciona no navegador do computador e do celular, com login da equipe e dados salvos no Supabase.

## O que tem nesta pasta

| Arquivo | Para que serve |
|---|---|
| `index.html` | O sistema inteiro |
| `config.js` | Onde você cola o endereço e a chave do banco |
| `logo-branca.png`, `logo-azul.png` | Logo usada no menu e na tela de login |
| `supabase/schema.sql` | Cria a tabela e as regras de segurança no banco |

## Passo 1 — Criar o banco no Supabase (uns 10 minutos)

1. Crie uma conta grátis em supabase.com e clique em **New project**. Escolha a região **South America (São Paulo)** e guarde a senha do banco.
2. Quando o projeto terminar de criar, abra **SQL Editor**, clique em **New query**, cole todo o conteúdo de `supabase/schema.sql` e clique em **Run**. Deve aparecer "Success".
3. Em **Authentication > Sign In / Providers**, desligue a opção que permite novos usuários se cadastrarem sozinhos. Assim só entra quem você cadastrar.
4. Em **Authentication > Users**, clique em **Add user > Create new user** e cadastre o e-mail e uma senha para cada pessoa da equipe. Marque a opção de confirmar o e-mail automaticamente.
5. Em **Project Settings > API** (ou **Data API**), copie a **Project URL** e a chave **anon public**.

## Passo 2 — Configurar o sistema

Abra `config.js` num editor de texto e troque os dois textos `COLE_AQUI...` pela URL e pela chave anon. Salve.

> Nunca use a chave `service_role` neste arquivo. A chave anon pode ficar pública porque o banco só libera os dados para quem fez login.

## Passo 3 — Colocar no GitHub e publicar

1. Crie uma conta em github.com (se ainda não tiver) e clique em **New repository**. Nome sugerido: `central-saoluis-coworking`. Pode deixar **Private** se o seu plano permitir publicar páginas privadas; no plano grátis, deixe **Public** (o código fica visível, mas os dados não, porque estão protegidos pelo login).
2. Na página do repositório, clique em **Add file > Upload files**, arraste todos os arquivos desta pasta (incluindo a pasta `supabase`) e clique em **Commit changes**.
3. Vá em **Settings > Pages**. Em **Source**, escolha **Deploy from a branch**, branch **main**, pasta **/ (root)**, e salve.
4. Em um ou dois minutos o endereço aparece no topo dessa tela, algo como `https://seu-usuario.github.io/central-saoluis-coworking/`.
5. Volte ao Supabase em **Authentication > URL Configuration** e coloque esse endereço em **Site URL**.

Alternativa: em vercel.com, importe o repositório do GitHub e clique em **Deploy**. Funciona igual e permite repositório privado no plano grátis.

## Passo 4 (opcional) — Domínio próprio

Para usar algo como `sistema.saoluiscoworking.com.br`, em **Settings > Pages > Custom domain** digite o endereço e, no painel onde o domínio está registrado, crie um registro **CNAME** apontando `sistema` para `seu-usuario.github.io`. Depois, atualize a **Site URL** no Supabase.

## Uso no dia a dia

- Cada pessoa entra com o próprio e-mail e senha. O botão **Sair** fica no rodapé do menu.
- O que uma pessoa cadastra aparece na hora para as outras.
- Para redefinir a senha de alguém: Supabase > **Authentication > Users** > clique no usuário.
- Para tirar alguém do sistema: exclua o usuário nessa mesma tela.
- No celular, abra o endereço e use **Adicionar à tela inicial** para abrir como um aplicativo.

## Cópia de segurança

No Supabase, **Table Editor > registros > Export to CSV** baixa todos os dados. Faça isso uma vez por mês.

## Começando do zero

O sistema começa vazio. A ordem recomendada é:
1. **Cadastros**: espaços (salas, auditório, estações), planos e contas bancárias.
2. **Clientes**.
3. **Contratos** e, todo mês, **Gerar mensalidades**.
4. **Reservas** e **Comercial** no dia a dia.
