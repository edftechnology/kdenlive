# Como instalar o `kdenlive` no `Linux Ubuntu`


## Resumo

Este documento apresenta os passos necessários para instalar o utilitário `kdenlive` no `Linux Ubuntu`.


## _Abstract_

_This document shows the steps required to install the `kdenlive` utility on `Linux Ubuntu`._


## Descrição

### `kdenlive`

O `kdenlive` é um editor de vídeo não linear de código aberto, integrante do projeto `KDE` e 
voltado para fornecer recursos profissionais de edição.


## 1. Instalar o `kdenlive` no `Linux Ubuntu`

Para instalar o `kdenlive`, siga os passos abaixo:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Digite:
    ```bash
    sudo apt clean
    ```

    2.2 Remover pacotes `.deb` antigos ou duplicados do `cache` local:
    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes instalados automaticamente e que não são mais necessários:
    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar atualizações disponíveis:
    ```bash
    sudo apt update
    ```

    2.5 Corrigir pacotes quebrados:
    ```bash
    sudo apt --fix-broken install
    ```

    2.6 Limpar novamente o `cache`:
    ```bash
    sudo apt clean
    ```

    2.7 Verificar pacotes que podem ser atualizados:
    ```bash
    sudo apt list --upgradable
    ```

    2.8 Atualizar os pacotes instalados:
    ```bash
    sudo apt full-upgrade -y
    ```

3. Instale o `kdenlive` e verifique a instalação:
    ```bash
    sudo apt update
    sudo apt install kdenlive
    kdenlive --version
    ```


## 2. Preparar a distribuição `PREDICTIONS`

O arquivo tar compactado `PREDICTIONS.tar.gz` contém os vários programas e _scripts_ necessários
para executar os procedimentos do `kdenlive`.

Faça o seguinte...

1. `gunzip PREDICTIONS.tar.gz`.

2. `tar -xvf PREDICTIONS.tar`.

Esses passos criam o diretório `PREDICTIONS`, que conterá as subpastas `MOLPAK`, `PMIN`, `UTILITIES`
e `new-U`, além de vários arquivos.

O diretório `PREDICTIONS` e cada uma das subpastas possuem arquivos `compile-all` para compilar e
ligar os programas.

Antes de compilar, substitua o nome do nosso compilador pelo nome do seu compilador em todos os
arquivos `compile-all`. Usamos `lf95`.

Há vários programas e scripts na subpasta `UTILITIES`. É necessário trocar o nome `PREDICTIONS` pelo
caminho do diretório em que os programas residirão para execução posterior. Por exemplo, nosso
diretório é `/export/software/PREDICTIONS`. Isso é feito pelos seguintes passos:

1. Substituir `lf95` pelo nome do seu compilador em `compile-all` no diretório superior, aqui
chamado de `PREDICTIONS`;

2. Copiar todos os arquivos de `new-U` para `UTILITIES`:

    ```bash
    cp new-U/* UTILITIES/.
    ```

3. `./compile-all`: compila e liga o programa `rename-dir.f90`;

4. `./rename-dir.com`: substitui todas as ocorrências de `PREDICTIONS` nos arquivos necessários em
`UTILITIES` por `/export/software/PREDICTIONS` ou qualquer diretório em que você estiver ao executar
`./rename-dir.com`.

Estabeleça os seguintes _aliases_:

```bash
alias transform /export/software/PREDICTIONS/UTILITIES/transform.exe
alias prepare-files /export/software/PREDICTIONS/UTILITIES/prepare-files.exe
alias make-files /export/software/PREDICTIONS/UTILITIES/make-files.com
alias chem3d /export/software/PREDICTIONS/UTILITIES/chem3d.exe
alias summarize /export/software/PREDICTIONS/UTILITIES/summarize_tab.com
alias resort-summarize /export/software/PREDICTIONS/UTILITIES/resort-summarize.com
```

Os _aliases_ facilitam a execução dos diversos cálculos. Por exemplo, para realizar tarefas com o
`kdenlive`, basta digitar `make-files` e responder às perguntas que se seguem.

## 3. Executar um arquivo de entrada

Você pode executar o `kdenlive` informando um arquivo de vídeo:
```bash
kdenlive ~/exemplos/video.mp4
```
Esse comando executa o programa usando o arquivo `video.mp4`.


## 4. Usar uma variável de terminal para definir o arquivo

Também é possível definir o caminho em uma variável antes de chamar o `kdenlive`:
```bash
input_file="~/exemplos/video.mp4"
kdenlive "$input_file"
```


## Referências

[1] OPENAI.
**Instalar o `kdenlive` no `linux ubuntu` pelo `terminal emulator`**.
Disponível em: <https://chatgpt.com/c/88d3b432-a9e7-4a62-b480-a0e38cd83113>.
ChatGPT.
Acessado em: 15/08/2025 13:07.

