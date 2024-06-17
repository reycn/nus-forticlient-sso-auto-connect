# vpn-auto-connect

Script de Automação para Conexão VPN

## Descrição

Este repositório contém um script Python que automatiza o processo de conexão a uma VPN usando OpenConnect e Selenium para login SSO. O script oferece funcionalidades para instalação de dependências, criptografia de senhas, execução manual ou automática do login, e manutenção da sessão sudo ativa.

## Funcionalidades

- Instalação de pacotes necessários
- Criptografia e descriptografia de senhas
- Automação do login SSO utilizando Selenium
- Suporte a execução manual do login
- Conexão automática à VPN utilizando cookies gerados
- Manutenção da sessão sudo ativa

## Requisitos

- Python 3
- Sistema operacional baseado em Unix (Linux, macOS)
- Navegador Google Chrome

## Instalação

1. Clone o repositório:
    ```sh
    git clone https://github.com/rafaelbiasi/forticlient-sso-auto-connect.git
    cd forticlient-sso-auto-connect
    ```
2. Defina o `vpn-auto-connect` como executavel:
   ```
   chmod +x vpn-auto-connect
   ```
4. Instale as dependências:
    ```sh
    sudo apt install python3-dev python3-pip python3-setuptools
    vpn-auto-connect --install
    ```
## Uso

### Configuração Inicial

1. Crie um arquivo de configuração `vpn-config.json` no mesmo diretório do script com o seguinte formato:
    ```json
    {
        "username": "seu_usuario",
        "password": "sua_senha",
        "encrypted-password": "sua_senha_criptografada",
        "host_mapping": {
            "1": "vpn.example.com",
            "2": "vpn2.example.com"
        },
        "server_cert": "sha256:...",
        "vpn_slice": "..."
    }
    ```
   Escolha uma das duas opções: `password` e `encrypted-password`. Caso deseje mais segurança, use a faça o procedimento abaixo, se não, a opção `password` é de preechimento obrigatório.

2. Criptografe a senha (opcional):
    ```sh
    vpn-auto-connect --encrypt
    ```

### Conectando à VPN
1. Exibe a ajuda:
    ```sh
    vpn-auto-connect --help
    ```
    
2. Conectar com login automático:
    ```sh
    vpn-auto-connect
    ```

3. Conectar com login manual:
    ```sh
    vpn-auto-connect --manual
    ```

4. Conectar com LAN desabilitada:
    ```sh
    vpn-auto-connect --off
    ```

5. Forçar a exibição do navegador durante o login SSO:
    ```sh
    vpn-auto-connect --browser
    ```

### Outras Opções

- Verificar se há atualizações para o script:
    ```sh
    vpn-auto-connect --update
    ```

- Atualizar o script:
    ```sh
    vpn-auto-connect --upgrade
    ```

## Autor

[Rafael Costa Biasi](https://rafaelbiasi.com.br/)

## Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para mais detalhes.
