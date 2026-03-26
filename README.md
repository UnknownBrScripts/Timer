# Timer para PowerPoint (Suplemento Office / Add-in)

Este projeto foi recriado como um **Suplemento Web do Office (Office Web Add-in)** usando HTML, CSS e JavaScript. Esta é a tecnologia oficial recomendada pela Microsoft (como visto na [documentação oficial](https://learn.microsoft.com/pt-br/office/dev/add-ins/overview/office-add-ins)), o que permite que ele seja publicado na Microsoft Store futuramente.

Diferente de um suplemento de "Painel de Tarefas" (Task Pane) que fica preso na lateral da tela, este projeto usa o tipo **Content Add-in (Suplemento de Conteúdo)**. Isso permite que o Timer seja inserido diretamente **dentro do slide** como um objeto, garantindo que ele tenha o fundo transparente e funcione perfeitamente tanto no modo de Edição quanto no modo de Apresentação.

## 📂 Estrutura dos Arquivos

1. **`manifest.xml`**: O arquivo de configuração do suplemento. Ele diz ao PowerPoint o nome do app, suas permissões e, o mais importante, a URL de onde ele vai carregar a interface (HTML).
2. **`index.html`**: A interface do usuário. Contém a lógica do cronômetro, estilos de transparência e o painel de configurações ajustável (cor, tamanho, tempo inicial).

---

## 🚀 Como testar o Suplemento no seu PowerPoint

Para que o PowerPoint aceite carregar o suplemento, a página web (`index.html`) **precisa obrigatoriamente estar hospedada em um servidor seguro (HTTPS)**. 

A forma mais rápida, gratuita e fácil de testar isso antes de publicar na loja é usando o **GitHub Pages**.

### Passo 1: Hospedar os arquivos na Web
1. Crie um repositório público no seu [GitHub](https://github.com/).
2. Faça o upload do arquivo `index.html` para este repositório.
3. Vá em **Settings (Configurações) > Pages**.
4. Em "Source", selecione a branch `main` e salve.
5. Em alguns minutos, o GitHub te dará um link como: `https://SEU-USUARIO.github.io/NOME-DO-REPO/`

### Passo 2: Atualizar o Manifest
1. Abra o arquivo `manifest.xml` no seu editor de texto.
2. Encontre a linha:
   `<SourceLocation DefaultValue="https://seu-usuario.github.io/timer-powerpoint/index.html" />`
3. Substitua essa URL pela URL real onde o seu `index.html` ficou hospedado no GitHub.

### Passo 3: Carregar no PowerPoint (Sideloading no Windows)
Para testar o suplemento sem publicá-lo na loja, você deve usar o método de "Pasta Compartilhada" do Windows:

1. Crie uma pasta no seu computador (ex: `C:\SuplementosOffice`).
2. Coloque o arquivo `manifest.xml` atualizado dentro dessa pasta.
3. Clique com o botão direito na pasta > **Propriedades** > aba **Compartilhamento** > **Compartilhar...**
4. Adicione o seu próprio usuário e clique em Compartilhar. Copie o caminho da rede (ex: `\\SEU-PC\SuplementosOffice`).
5. Abra o PowerPoint e crie uma apresentação em branco.
6. Vá em **Arquivo > Opções > Central de Confiabilidade > Configurações da Central de Confiabilidade**.
7. Selecione **Catálogos de Suplementos Confiáveis** (Trusted Add-in Catalogs).
8. No campo "URL de Catálogo", cole o caminho da rede (`\\SEU-PC\SuplementosOffice`) e clique em **Adicionar Catálogo**.
9. Marque a caixa "Mostrar no Menu" e clique em OK. Reinicie o PowerPoint.

### Passo 4: Inserir o Timer no Slide
1. Com o PowerPoint reaberto, vá na aba **Inserir** > **Obter Suplementos** (ou "Meus Suplementos").
2. Clique na aba **Pasta Compartilhada** (Shared Folder).
3. Você verá o **Timer Overlay Profissional**! Clique nele e depois em **Adicionar**.
4. O Timer aparecerá no seu slide. 
5. Passe o mouse sobre ele e clique no ícone de engrenagem ⚙️ no canto superior direito para ajustar o tempo, cor, e tamanho!

---

## 🎨 Funcionalidades Incluídas
- **Fundo 100% Transparente**: O fundo da página web está configurado como transparente, integrando-se perfeitamente ao fundo do seu slide.
- **Ajustes Visuais**: Modifique a cor e tamanho da fonte do cronômetro direto na interface.
- **Modo Edição e Apresentação**: Como é um "Content Add-in", ele permanece visível e interativo (clique para pausar/despausar) independente de o slide estar em tela cheia ou não.