# Saúde Integral · como publicar e instalar

Custo: R$ 0. Usa o mesmo GitHub e o mesmo Firebase gratuito da Caderneta.

## 1. Criar o repositório no GitHub (Windows)

1. Entre em github.com com o usuário **brunotriani**.
2. Clique em **New** (novo repositório). Nome: `saude`. Deixe **Public** (o GitHub Pages gratuito exige). Clique em **Create repository**.
3. Clique em **uploading an existing file** e arraste todos os arquivos desta pasta:
   `index.html`, `manifest.webmanifest`, `sw.js`, `icon-180.png`, `icon-192.png`, `icon-512.png`.
4. No repositório da Caderneta, abra o arquivo `firebase-config.txt`, copie o conteúdo e crie um arquivo com o mesmo nome no repositório `saude` (**Add file › Create new file**), colando o mesmo texto.
5. **Não envie** o arquivo `meu-perfil-inicial.json`: ele tem seus dados de saúde e fica só com você.
6. Clique em **Commit changes**.

O código é público, mas não contém nenhum dado seu. Tudo o que você registrar fica criptografado no aparelho e na sua conta Firebase.

## 2. Ligar o site

1. No repositório `saude`: **Settings › Pages**.
2. Em **Branch**, escolha `main` e `/ (root)`. Clique em **Save**.
3. Em 1 a 2 minutos o app abre em: **https://brunotriani.github.io/saude/**

## 3. Instalar

- **iPhone:** abra o link no **Safari** › botão Compartilhar › **Adicionar à Tela de Início**.
- **Windows:** abra no **Chrome** ou **Edge** › ícone de instalar na barra de endereço (ou menu › Instalar app).

## 4. Primeiro acesso e sincronização

1. No **iPhone**, crie usuário e senha. Use **a mesma senha da Caderneta**, porque a sincronização usa a mesma conta Firebase.
2. Vá em **Perfil › Ajustes › Ativar sincronização** e entre com o mesmo e-mail e senha da Caderneta.
3. Em **Perfil › Ajustes › Importar arquivo**, escolha `meu-perfil-inicial.json` (salve antes no app Arquivos do iPhone).
4. No **Windows**, abra o app e toque em **Já uso em outro aparelho: entrar com e-mail**. Tudo desce sozinho.

Se aparecer **"O Firebase recusou o acesso"**, as regras do Firestore da Caderneta só liberam as coleções dela. No console do Firebase: **Firestore Database › Regras**, deixe assim e clique em **Publicar** (vale para os dois apps):

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
  }
}
```

## 5. Atualizações

Quando o Claude gerar uma versão nova, substitua só o `index.html` no GitHub (**Add file › Upload files**, mesmo nome). Os dados não são afetados. Feche e abra o app para carregar a versão nova.

## Limites gratuitos do Firebase (folgados para uso pessoal)

1 GB armazenado, 50 mil leituras e 20 mil gravações por dia. Arquivos de exames entram em pedaços cifrados de até 450 KB, sem usar o Storage pago.
