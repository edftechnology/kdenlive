# Como instalar o `molpak` no `Linux Ubuntu`

## Resumo

Este documento apresenta os passos necessários para instalar o utilitário `molpak` no `Linux Ubuntu`.

## _Abstract_

_This document shows the steps required to install the `molpak` utility on `Linux Ubuntu`._

## Descrição

### `molpak`

O `molpak` é um conjunto de programas para predição de estruturas cristalinas, auxiliando no estudo de empacotamento molecular.

## 1. Instalar o `molpak` no `Linux Ubuntu`

Para instalar o `molpak`, siga os passos abaixo:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

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

3. Instale o `molpak` e verifique a instalação:
    ```bash
    sudo apt update
    sudo apt install molpak
    molpak --help
    ```

## 2. Preparar a distribuição `PREDICTIONS`

O arquivo tar compactado `PREDICTIONS.tar.gz` contém os vários programas e scripts necessários para executar os procedimentos de predição de estruturas `molpak/pmin`.

Faça o seguinte...
1. `gunzip PREDICTIONS.tar.gz`.
2. `tar -xvf PREDICTIONS.tar`.

Esses passos criam o diretório `PREDICTIONS`, que conterá as subpastas `MOLPAK`, `PMIN`, `UTILITIES` e `new-U`, além de vários arquivos.

O diretório `PREDICTIONS` e cada uma das subpastas possuem arquivos `compile-all` para compilar e ligar os programas.

Antes de compilar, substitua o nome do nosso compilador pelo nome do seu compilador em todos os arquivos `compile-all`. Usamos `lf95`.

Há vários programas e scripts na subpasta `UTILITIES`. É necessário trocar o nome `PREDICTIONS` pelo caminho do diretório em que os programas residirão para execução posterior. Por exemplo, nosso diretório é `/export/software/PREDICTIONS`. Isso é feito pelos seguintes passos ->
1. substituir `lf95` pelo nome do seu compilador em `compile-all` no diretório superior, aqui chamado de `PREDICTIONS`;
2. copiar todos os arquivos de `new-U` para `UTILITIES` -> `cp new-U/* UTILITIES/.`;
3. `./compile-all` -> compila e liga o programa `rename-dir.f90`;
4. `./rename-dir.com` -> substitui todas as ocorrências de `PREDICTIONS` nos arquivos necessários em `UTILITIES` por `/export/software/PREDICTIONS` ou qualquer diretório em que você estiver ao executar `./rename-dir.com`.

Estabeleça os seguintes aliases:
```bash
alias transform /export/software/PREDICTIONS/UTILITIES/transform.exe
alias prepare-files /export/software/PREDICTIONS/UTILITIES/prepare-files.exe
alias make-files /export/software/PREDICTIONS/UTILITIES/make-files.com
alias chem3d /export/software/PREDICTIONS/UTILITIES/chem3d.exe
alias summarize /export/software/PREDICTIONS/UTILITIES/summarize_tab.com
alias resort-summarize /export/software/PREDICTIONS/UTILITIES/resort-summarize.com
```

Os aliases facilitam a execução dos diversos cálculos. Por exemplo, para realizar cálculos `molpak/pmin`, basta digitar `make-files` e responder às perguntas que se seguem.

EXEMPLOS são fornecidos. BOA SORTE!

## 3. Executar um arquivo de entrada

Você pode executar o `molpak` informando um arquivo de entrada:
```bash
molpak ~/exemplos/entrada.dat
```
Esse comando executa o programa usando o arquivo `entrada.dat`.

## 4. Usar uma variável de terminal para definir o arquivo

Também é possível definir o caminho em uma variável antes de chamar o `molpak`:
```bash
input_file="~/exemplos/entrada.dat"
molpak "$input_file"
```

## Referências

[1] OPENAI. ***Como instalar o molpak no Linux Ubuntu***. Disponível em: <https://chatgpt.com/c/68949d8a-17d0-8331-b342-8d3807ccf395>. ChatGPT. Acessado em: 08/08/2025 00:19.
