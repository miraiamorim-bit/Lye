# Site HTML → APK

Transforma o seu site HTML em um app Android (APK) automaticamente, usando o GitHub Actions. Sem instalar nada no computador.

## Como usar

1. Coloque os arquivos do seu site na pasta `www/` (o `index.html` precisa ficar lá).
2. Envie para a branch `main` do GitHub.
3. Espere de 5 a 10 minutos e abra a página **Releases** do repositório: o arquivo `.apk` fica em **APK mais recente**. Abra essa página no celular e toque no arquivo para instalar.

Se o build não começar sozinho: aba **Actions → Gerar APK → Run workflow**.

## O que é feito automaticamente

- O nome do app é o nome do repositório (renomeie o repositório para mudar).
- O pipeline cria o projeto Android com [Capacitor](https://capacitorjs.com), copia o conteúdo de `www/` e compila o APK.
- Um pequeno CSS (`apk-safe-area.css`) é adicionado às páginas, só durante o build, para o conteúdo não ficar atrás das barras do Android.
- A cada push na `main`, o APK mais recente é substituído. Uma cópia também fica na aba **Actions**, em Artifacts.

## Limitações

- O APK é assinado com uma chave de teste (`debug.keystore.base64`): serve para instalar no seu celular. Para publicar na Play Store é preciso uma chave própria e um arquivo AAB.
- O ícone do app é o padrão do Capacitor.
- O Android pode pedir para permitir a instalação de apps de fontes desconhecidas.
