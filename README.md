# Driver do Kernel para IMX294

Este guia fornece instruções detalhadas sobre como instalar o driver do kernel IMX294 em um sistema Linux, especificamente o Raspbian.

## Pré-requisitos

Antes de iniciar o processo de instalação, certifique-se de que os seguintes pré-requisitos sejam atendidos:

- **Versão do kernel**: você deve estar executando um kernel Linux versão 6.1 ou superior. Você pode verificar a versão do seu kernel executando `uname -r` no terminal.

- **Ferramentas de desenvolvimento**: ferramentas essenciais como `gcc`, `dkms` e `linux-headers` são necessárias para compilar um módulo do kernel. Se ainda não estiverem instaladas, elas podem ser instaladas com o gerenciador de pacotes usando o seguinte comando:

   ```bash
   sudo apt install linux-headers dkms git
   ```

## Etapas de instalação

### Configurando as ferramentas

Primeiro, instale as ferramentas necessárias (`linux-headers`, `dkms` e `git`) caso ainda não as tenha:

```bash
sudo apt install linux-headers dkms git
```

### Obtendo o código-fonte

Clone o repositório para a sua máquina local e navegue até o diretório clonado:

```bash
git clone https://github.com/will127534/imx294-v4l2-driver.git
cd imx294-v4l2-driver/
```

### Compilando e instalando o driver do kernel

Para compilar e instalar o driver do kernel, execute o script de instalação fornecido:

```bash
./setup.sh
```

### Atualizando a configuração de inicialização

Edite o arquivo de configuração de inicialização usando o seguinte comando:

```bash
sudo nano /boot/config.txt
```

No editor aberto, localize a linha contendo `camera_auto_detect` e altere seu valor para `0`. Em seguida, adicione a linha `dtoverlay=imx294`. Assim, o arquivo ficará assim:

```
camera_auto_detect=0
dtoverlay=imx294
```

Depois de fazer essas alterações, salve o arquivo e saia do editor.

Lembre-se de reiniciar o sistema para que as alterações entrem em vigor.

## Agradecimentos especiais

Agradecimentos especiais ao projeto Raspberry Pi CM4 Carrier com Display MIPI de Alta Resolução de Sasha Shturma; o script de instalação foi adaptado a partir da página do projeto no GitHub: https://github.com/renetec-io/cm4-panel-jdi-lt070me05000
