# Como instalar o `kdenlive` no `Kali Linux`


## Resumo

Este documento apresenta os passos necessários para instalar o editor de vídeo `kdenlive` no `Kali Linux` via `apt`.


## _Abstract_

_This document shows the steps required to install the `kdenlive` video editor on `Kali Linux` via `apt`._


## Descrição

### `kdenlive`

O `kdenlive` é um editor de vídeo não linear de código aberto, integrante do projeto `KDE` e
baseado em `Qt`, `KDE Frameworks` e `MLT Framework`. No `Kali Linux`, o pacote `kdenlive`
está disponível nos repositórios da distribuição e pode ser instalado pelo gerenciador de
pacotes `apt`.


## 1. Instalar o `kdenlive` no `Kali Linux`

Para instalar o `kdenlive`, siga os passos abaixo:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:
    ```bash
    sudo apt clean
    ```

    2.2 Remover pacotes `.deb` antigos ou duplicados do `cache` local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando:
    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando:
    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt update
    ```

    2.5 **Corrigir pacotes quebrados**: Isso atualizará a lista de pacotes disponíveis e tentará corrigir pacotes quebrados ou com dependências ausentes:
    ```bash
    sudo apt --fix-broken install
    ```

    2.6 Limpar o `cache` do gerenciador de pacotes `apt` novamente:
    ```bash
    sudo apt clean
    ```

    2.7 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt list --upgradable
    ```

    2.8 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update`. Digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt full-upgrade -y
    ```



3. Instalar o `kdenlive` pelo `apt` e verificar a instalação:
    
    ```bash
    sudo apt install kdenlive -y
    kdenlive --version
    ```

## 2. Verificar o pacote instalado

Após a instalação, confirme se o binário foi localizado pelo `shell` e se o pacote instalado vem
dos repositórios configurados do `Kali Linux`:

```bash
command -v kdenlive
apt policy kdenlive
```

Se o `apt` não localizar o pacote, verifique se o arquivo `/etc/apt/sources.list` contém os
repositórios oficiais do `Kali Linux` e execute novamente `sudo apt update` antes de repetir a
instalação.


## 3. Executar o `kdenlive`

Você pode abrir o `kdenlive` pelo menu de aplicativos ou pelo `Terminal Emulator`:
```bash
kdenlive
```
Também é possível informar um arquivo de vídeo para abrir o editor já apontando para esse arquivo:
```bash
kdenlive ~/Videos/video.mp4
```


## 4. Remover o `kdenlive`

Caso seja necessário remover o `kdenlive` instalado pelo `apt`, use:
```bash
sudo apt remove kdenlive -y
sudo apt autoremove -y
```


## Referências

[1] OPENAI. **Instalar o `kdenlive` no `kali linux` pelo `terminal emulator`**. Disponível em: <https://chatgpt.com/g/g-p-6980caf949648191ad6acfcdbe590f9e/c/7c35ad4d-d9c9-4498-9837-ab1b99548eb5>. ChatGPT. Acessado em: 07/09/2026.

[2] KALI. **Kdenlive**. Disponível em: <https://pkg.kali.org/pkg/kdenlive>. Acessado em: 07/09/2026.

[3] KDE. **Kdenlive downloads**. Disponível em: <https://kdenlive.org/download/>. Acessado em: 07/09/2026.

