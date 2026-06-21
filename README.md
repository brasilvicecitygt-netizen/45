# Tutorial do Launcher Black Russia (PT-BR)

## Índice
1. Abrindo o projeto no Android Studio
2. Configurando server.json e stories.json
3. Configuração do cache (arquivos do jogo)
4. Alterando o nome do launcher
5. Alterando o ícone do launcher
6. Alterando o IP do servidor e compilando os fontes JNI
7. Gerando a APK

# Abrindo o projeto no Android Studio
Baixe o código-fonte do projeto e extraia o arquivo ZIP em uma pasta de sua preferência.

Abra o Android Studio, clique em **Open** e selecione a pasta do projeto.

Se aparecer a janela **Trust Project**, clique em **Trust Project**.

Caso apareça um erro relacionado ao Gradle, clique em **Upgrade Gradle Wrapper**.

Após isso, o projeto deverá abrir normalmente.

# Configurando server.json e stories.json
Os arquivos `server.json` e `stories.json` são responsáveis pelo monitoramento dos servidores e pelas histórias exibidas no launcher.

Edite os arquivos em qualquer editor de texto, envie-os para um serviço de nuvem (recomendado: Dropbox) e obtenha um **link direto**.

No Android Studio, abra:

`app/java/com/blackrussia/launcher/other/Interface.java`

Substitua os links originais de `server.json` e `stories.json` pelos seus links diretos.

Pronto!

# Configuração do cache (arquivos do jogo)
Baixe os arquivos do jogo (cache).

Abra o arquivo `settings.ini` dentro da pasta `SAMP`.

Recomenda-se alterar apenas:
- Nickname padrão do jogador.
- Limite máximo de FPS.

Salve o arquivo e atualize o conteúdo do arquivo compactado.

Envie o cache para um serviço de nuvem e obtenha um link direto.

Depois abra:

`app/java/com/blackrussia/launcher/activity/LoaderActivity.java`

Troque o link do cache pelo seu próprio link direto.

Pronto!

# Alterando o nome do launcher
Abra:

`app/res/values/strings/strings.xml`

Altere o valor de `app_name` para o nome desejado.

# Alterando o ícone do launcher
Use uma imagem PNG de 1060x1060 pixels.

Substitua os arquivos `ic_launcher.png` e demais ícones nas pastas drawable correspondentes.

Para alterar também o visual do launcher, modifique as imagens localizadas em:

`app/src/main/res/drawable/`

# Alterando o IP do servidor e compilando JNI
Abra:

`Jni source/jni/util/CJavaWrapper.cpp`

Próximo da linha 276 haverá o IP e a porta do servidor.

Substitua pelos dados do seu servidor e salve.

Baixe o Android NDK compatível com seu sistema operacional (versão 64 bits recomendada).

## Compilação no Windows

Abra o Prompt de Comando:

```bat
cd "CAMINHO_DO_NDK"
```

Compile:

```bat
ndk-build -C "CAMINHO_DA_PASTA_JNI_SOURCE"
```

Se a compilação for concluída com sucesso, será gerado:

`Jni Source/libs/armeabi-v7a/libsamp.so`

Substitua este arquivo em:

`app/jniLibs/armeabi-v7a/libsamp.so`

Pronto!

# Gerando a APK
No Android Studio:

Build -> Build App Bundle(s) / APK(s) -> Build APK(s)

Aguarde a compilação.

Quando finalizar, clique em **Locate** ou abra:

`app/debug/`

A APK gerada estará nessa pasta.

---

OBS: O tutorial original ainda estava em desenvolvimento.
