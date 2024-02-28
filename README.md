# Instalação do Linux no Windows com WLS

O WSL permite executar um ambiente Linux diretamente no Windows. Ele oferece uma maneira de usar ferramentas e aplicativos nativos do Linux sem a necessidade de virtualização completa ou dual boot.


# Pré-Requisitos:


Você deve estar executando o Windows 10 versão 2004 e superior (Build 19041 e superior) ou o Windows 11 para usar os comandos abaixo.Se você estiver em versões anteriores, consulte [a página de instalação manual](https://learn.microsoft.com/pt-br/windows/wsl/install-manual).

# Comando de instalação:


Agora você pode instalar tudo o que precisa para executar o WSL com apenas um comando. Abra o PowerShell ou o Prompt de Comando do Windows no modo de **administrador** clicando com o botão direito do mouse e selecionando "Executar como administrador"; insira o comando wsl --install e reinicie o computador.

    wsl --install
    
Esse comando habilitará os recursos necessários para executar o WSL e instalar a distribuição Ubuntu do Linux. ([Essa distribuição padrão pode ser alterada](https://learn.microsoft.com/pt-br/windows/wsl/basic-commands#install).)

Se você estiver executando um build mais antigo ou simplesmente prefere não usar o comando para instalar e quer instruções passo a passo, confira  **[Etapas de instalação manual do WSL para versões mais antigas](https://learn.microsoft.com/pt-br/windows/wsl/install-manual)**  .

Na primeira vez que você iniciar uma distribuição do Linux recém-instalada, uma janela de console será aberta e será solicitado que você aguarde para que os arquivos sejam descompactados e armazenados em seu computador. Todas as futuras inicializações deverão levar menos de um segundo.

**observações**
O comando acima só funcionará se o WSL não estiver instalado. Se você executar `wsl --install` e vir o texto de ajuda do WSL, tente executar `wsl --list --online` para ver a lista de distribuições disponíveis e execute `wsl --install -d <DistroName>` para instalar uma distribuição. Para desinstalar o WSL, confira [Desinstalar a versão herdada do WSL](https://learn.microsoft.com/pt-br/windows/wsl/troubleshooting#uninstall-legacy-version-of-wsl) ou [Cancelar o registro ou fazer a desinstalação de uma distribuição do Linux](https://learn.microsoft.com/pt-br/windows/wsl/basic-commands#unregister-or-uninstall-a-linux-distribution).



#  Alterar a distribuição padrão do Linux instalada:

Por padrão, a distribuição do Linux instalada será o Ubuntu. Isso pode ser alterado usando o sinalizador  `-d`.

-   Para alterar a distribuição instalada, insira:  `wsl --install -d <Distribution Name>`. Substitua  `<Distribution Name>`  pelo nome da distribuição que você gostaria de instalar.
-   Para ver uma lista das distribuições do Linux disponíveis para download por meio da loja online, insira:  `wsl --list --online`  ou  `wsl -l -o`.
-   Para instalar distribuições adicionais do Linux após a instalação inicial, você também pode usar o comando:  `wsl --install -d <Distribution Name>`.

Dica

Se você quiser instalar distribuições adicionais usando uma linha de comando Linux/Bash (em vez do PowerShell ou prompt de comando), deverá usar .exe no comando:  `wsl.exe --install -d <Distribution Name>`  ou, para listar as distribuições disponíveis:  `wsl.exe -l -o`.

Se você encontrar um problema durante o processo de instalação, verifique a  [seção de instalação do guia de solução de problemas](https://learn.microsoft.com/pt-br/windows/wsl/troubleshooting#installation-issues).

Para instalar uma distribuição do Linux que não esteja listada como disponível, você pode  [importar qualquer distribuição do Linux](https://learn.microsoft.com/pt-br/windows/wsl/use-custom-distro)  usando um arquivo TAR. Ou, em alguns casos,  [como no Arch Linux](https://wsldl-pg.github.io/ArchW-docs/How-to-Setup/), você pode fazer a instalação usando um arquivo  `.appx`. Você também pode criar sua  [distribuição personalizada do Linux](https://learn.microsoft.com/pt-br/windows/wsl/build-custom-distro)  a ser usada com o WSL.

[](https://learn.microsoft.com/pt-br/windows/wsl/install#set-up-your-linux-user-info)

## Configurar suas informações de usuário do Linux

Depois de instalar o WSL, você precisará criar uma conta de usuário e uma senha para a distribuição do Linux recém-instalada. Confira o guia  [Melhores práticas para configurar um ambiente de desenvolvimento do WSL](https://learn.microsoft.com/pt-br/windows/wsl/setup/environment#set-up-your-linux-username-and-password)  para mais informações.

[](https://learn.microsoft.com/pt-br/windows/wsl/install#set-up-and-best-practices)

## Configuração e melhores práticas

Recomendamos seguir nosso guia  [Melhores práticas para configurar um ambiente de desenvolvimento do WSL](https://learn.microsoft.com/pt-br/windows/wsl/setup/environment)  para ver um passo a passo de como configurar um nome de usuário e uma senha para suas distribuições do Linux instaladas, usar comandos do WSL básicos, instalar e personalizar o Terminal do Windows, configurar para o controle de versão do Git, editar e depurar código usando o servidor remoto do VS Code, conhecer boas práticas para armazenamento de arquivos, configurar um banco de dados, montar uma unidade externa, configurar a aceleração de GPU e muito mais.

[](https://learn.microsoft.com/pt-br/windows/wsl/install#check-which-version-of-wsl-you-are-running)

## Verificar a versão do WSL que você está executando

Você pode listar suas distribuições do Linux instaladas e verificar a versão do WSL para a qual cada uma está definida inserindo o comando:  `wsl -l -v`  no PowerShell ou Prompt de Comando do Windows.

Para definir a versão padrão como WSL 1 ou WSL 2 quando uma nova distribuição do Linux é instalada, use o comando:  `wsl --set-default-version <Version#>`, substituindo  `<Version#>`  por 1 ou 2.

Para definir a distribuição padrão do Linux usada com o comando  `wsl`, insira  `wsl -s <DistributionName>`  ou  `wsl --set-default <DistributionName>`, substituindo  `<DistributionName>`  pelo nome da distribuição do Linux que você gostaria de usar. Por exemplo, do PowerShell/CMD, insira:  `wsl -s Debian`  para definir a distribuição padrão como Debian. Agora, executar  `wsl npm init`  no PowerShell executará o comando  `npm init`  no Debian.

Para executar uma distribuição específica do WSL no PowerShell ou no Prompt de Comando do Windows sem alterar sua distribuição padrão, use o comando:  `wsl -d <DistributionName>`, substituindo  `<DistributionName>`  pelo nome da distribuição que você deseja usar.

Saiba mais no guia de  [Comandos básicos para WSL](https://learn.microsoft.com/pt-br/windows/wsl/basic-commands).

[](https://learn.microsoft.com/pt-br/windows/wsl/install#upgrade-version-from-wsl-1-to-wsl-2)

## Atualizar a versão do WSL 1 para o WSL 2

As novas instalações do Linux, instaladas usando o comando  `wsl --install`, serão definidas como WSL 2 por padrão.

O comando  `wsl --set-version`  pode ser usado para fazer downgrade do WSL 2 para o WSL 1 ou atualizar as distribuições do Linux instaladas anteriormente do WSL 1 para o WSL 2.

Para ver se a distribuição do Linux está definida como WSL 1 ou WSL 2, use o comando:  `wsl -l -v`.

Para mudar de versão, use o comando:  `wsl --set-version <distro name> 2`  substituindo  `<distro name>`  pelo nome da distribuição do Linux que você quer atualizar. Por exemplo,  `wsl --set-version Ubuntu-20.04 2`  definirá sua distribuição do Ubuntu 20.04 para usar o WSL 2.

Se você instalou o WSL manualmente antes da disponibilização do comando  `wsl --install`, poderá ser necessário  [habilitar o componente opcional de máquina virtual](https://learn.microsoft.com/pt-br/windows/wsl/install-manual#step-3---enable-virtual-machine-feature)  usado pelo WSL 2 e  [instalar o pacote do kernel](https://learn.microsoft.com/pt-br/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package), se isso ainda não foi feito.

Para saber mais, confira  [Referência de comando para WSL](https://learn.microsoft.com/pt-br/windows/wsl/basic-commands)  para obter uma lista de comandos do WSL,  [Comparar WSL 1 e WSL 2](https://learn.microsoft.com/pt-br/windows/wsl/compare-versions)  para obter diretrizes sobre qual deles usar para seu cenário de trabalho ou  [Práticas recomendadas para configurar um ambiente de desenvolvimento do WSL](https://learn.microsoft.com/pt-br/windows/wsl/setup/environment)  para obter diretrizes gerais sobre como configurar um bom fluxo de trabalho de desenvolvimento com o WSL.

[](https://learn.microsoft.com/pt-br/windows/wsl/install#ways-to-run-multiple-linux-distributions-with-wsl)

## Maneiras de executar várias distribuições do Linux com o WSL

O WSL dá suporte à execução de quantas distribuições do Linux diferentes você gostaria de instalar. Isso pode incluir a escolha de distribuições da  [Microsoft Store](https://aka.ms/wslstore), a  [importação de uma distribuição personalizada](https://learn.microsoft.com/pt-br/windows/wsl/use-custom-distro)  ou a  [criação da sua distribuição personalizada](https://learn.microsoft.com/pt-br/windows/wsl/build-custom-distro).

Há várias maneiras de executar suas distribuições do Linux depois de instaladas:

-   [Instalar o Terminal do Windows](https://learn.microsoft.com/pt-br/windows/terminal/get-started)_**(recomendado)**_  O uso do Terminal do Windows dá suporte a quantas linhas de comando você precisar instalar e permite que você as abra em várias guias ou painéis de janela e alterne rapidamente entre várias distribuições do Linux ou outras linhas de comando (PowerShell, Prompt de Comando, CLI do Azure etc.). Você pode personalizar totalmente o terminal com esquemas de cores exclusivos, estilos de fonte, tamanhos, imagens de tela de fundo e atalhos de teclado personalizados.  [Saiba mais.](https://learn.microsoft.com/pt-br/windows/terminal)
-   Você pode abrir diretamente sua distribuição do Linux visitando o menu Iniciar do Windows e digitando o nome das distribuições instaladas. Por exemplo: "Ubuntu". Isso abrirá o Ubuntu na própria janela do console.
-   No Prompt de Comando do Windows ou no PowerShell, você pode inserir o nome da distribuição instalada. Por exemplo:  `ubuntu`
-   No Prompt de Comando do Windows ou no PowerShell, você pode abrir sua distribuição padrão do Linux dentro da linha de comando atual inserindo:  `wsl.exe`.
-   No Prompt de Comando do Windows ou no PowerShell, você pode usar sua distribuição padrão do Linux dentro da linha de comando atual inserindo, sem entrar em uma nova, inserindo:  `wsl [command]`. Substituindo  `[command]`  por um comando do WSL, como:  `wsl -l -v`  para listar distribuições instaladas ou  `wsl pwd`  para ver onde o caminho de diretório atual está montado em WSL. No PowerShell, o comando  `get-date`  fornecerá a data do sistema de arquivos do Windows e  `wsl date`  fornecerá a data do sistema de arquivos do Linux.

O método selecionado deve depender do que você está fazendo. Se você abriu uma linha de comando do WSL dentro de uma janela do PowerShell ou Prompt do Windows e quer sair, insira o comando:  `exit`.

[](https://learn.microsoft.com/pt-br/windows/wsl/install#want-to-try-the-latest-wsl-preview-features)

## Deseja experimentar os recursos de versão prévia mais recentes do WSL?

Experimente os recursos ou atualizações mais recentes do WSL participando do  [Programa Windows Insider](https://insider.windows.com/getting-started). Depois de ingressar no Windows Insider, você pode escolher o canal do qual gostaria de receber compilações de pré-visualização no menu de configurações do Windows para receber automaticamente todas as atualizações ou recursos de versão prévia do WSL associados a esse build. Você pode escolher:

-   Canal do Desenvolvedor: atualizações mais recentes, mas baixa estabilidade.
-   Canal Beta: ideal para os usuários pioneiros, builds mais confiáveis do que o canal do Desenvolvedor.
-   Canal de pré-visualização de lançamento: visualize correções e principais recursos da próxima versão do Windows antes de estar disponível para o público em geral.

[](https://learn.microsoft.com/pt-br/windows/wsl/install#additional-resources)

## Recursos adicionais

-   [Blog da linha de comando do Windows: instalação do WSL com um só comando agora disponível no Windows 10 versão 2004 e superior](https://devblogs.microsoft.com/commandline/install-wsl-with-a-single-command-now-available-in-windows-10-version-2004-and-higher/)

