# MoodleInstall

Para que toda a instalação do XAMPP e Moodle funcione, é necessário que os dois possuam tecnologias em versões compatíveis. Neste tutorial se utilizaram as seguintes versões:

- XAMPP 8.0.30-0
  - Linux x64
  - Debian GNU/Linux 12

- Moodle 4.0.12
  - PHP 7.3
  - MariaDB 10.2.29
  - MySQL 5.7
  - Postgres 10
  - MSSQL 2017
  - Oracle 11.2

# Instalação do XAMPP no Debian

1. Para instalar o XAMPP é preciso baixar a versão do programa referente ao seu sistema operacional. Acesse o site da Apache Friends (https://www.apachefriends.org/pt_br/index.html) e selecione a opção “XAMPP para Linux”. O download irá iniciar automaticamente.

## Torna o instalador do XAMPP executável

1. Após a conclusão do download, é preciso tornar o instalador do XAMPP executável.

2. Abra o terminal e acesse a pasta onde você salvou o arquivo e rode um dos seguintes comandos:

```bash
sudo chmod 755 xampp-linux-*-installer.run

# ou

sudo chmod +x xampp-linux-*-installer.run
```

## Instalar o XAMPP

1. Para instalar o XAMPP rode o seguinte comando no terminal:

```bash
sudo ./xampp-linux-*-installer.run
```

2. O painel de instalação irá iniciar, clique em Next

3. A próxima janela permite que você selecione os componentes que você deseja instalar. Deixe todas as opções marcadas.

4. Na janela seguinte, o programa mostrará onde será feita a instalação do programa. Por padrão ela é feita na pasta /opt/lampp

5. Na tela seguinte será mostrado que o programa está pronto para ser instalado. Clique em Next.

6. A instalação irá iniciar e é só esperar o programa terminar de ser instalado.

7. Quando a janela abaixo aparecer, marque a caixa Launch XAMPP para iniciar o painel de controle do XAMPP e clique em Finish.

8. Se tudo correu como o esperado você verá a tela abaixo, ela possui três abas, a aba Welcome, a aba Manage Servers e a aba Application Log.

9. A aba Manage Servers é onde você poderá iniciar, parar, reiniciar e configurar os serviços.

10. Selecione o serviço e clique em Start para iniciar um serviço específico ou em Start All para iniciar todos de uma vez.

11. Para verificar se tudo está funcionando corretamente, com os serviços ativos, digite a seguinte url no seu navegador: http://localhost/dashboard/

12. A seguinte tela irá aparecer para você. A partir dela você terá acesso a diversos serviços oferecidos pelo XAMPP, incluindo o phpMyAdmin para a criação e manipulação de banco de dados.

## Como iniciar o XAMPP

Por padrão o XAMPP não fica no menu de aplicativos, para iniciar os serviços você pode seguir dois caminhos, direto pelo painel de controle com uma interface gráfica, a mesma mostrada anteriormente, ou usando comandos via terminal para cada serviço.

## Gerenciar serviços pelo painel de controle do XAMPP

1. Para iniciar o painel de controle do XAMPP e poder gerenciar os serviços a partir de uma interface gráfica, rode o seguinte comando:

```bash
sudo /opt/lampp/manager-linux-x64.run
```

2. O painel de controle abrirá e você poderá iniciar, parar ou reiniciar os serviços.

Talvez seja um pouco chato fica digitando esse comando no terminal toda vez que quiser iniciar o XAMPP. Há duas alternativas para resolver esse problema: criar um ícone para o menu de aplicativos ou um alias para o terminal.
Gerenciar serviços do XAMPP pelo terminal

3. Para iniciar todos os serviços do XAMPP de uma vez, rode o seguinte comando:

```bash
sudo /opt/lampp/lampp start
```

4. Para parar todos os serviços do XAMPP de uma vez, rode o seguinte comando:

```bash
sudo /opt/lampp/lampp stop
```

5. Para iniciar apenas o Apache, rode o seguinte comando:

```bash
sudo /opt/lampp/lampp startapache
```

6. Para parar apenas o Apache, rode o seguinte comando:

```bash
sudo /opt/lampp/lampp stopapache
```

7. Para iniciar apenas o FTP ProFTPD, rode o seguinte comando:

```bash
sudo /opt/lampp/lampp startftp
```

8. Para parar apenas o FTP ProFTPD, rode o seguinte comando:

```bash
sudo /opt/lampp/lampp stopftp
```

9. Para iniciar apenas o MySQL, rode o seguinte comando:

```bash
sudo /opt/lampp/lampp startmysql
```

10. Para parar apenas o MySQL, rode o seguinte comando:

```bash
sudo /opt/lampp/lampp stopmysql
```

**OBS**: Às vezes ao rodar os comandos para iniciar os serviços individualmente aparece um erro no terminal dizendo que o comando não foi encontrado, mas ao acessar o http://localhost/dashboard/ os serviços estarão ativos normalmente.

## Configurar as variáveis de ambiente

Para usar os serviços oferecidos pelo XAMPP você precisa configurar as variáveis de ambiente.

Se você rodar o comando mysql para tentar manipular bancos de dados pelo terminal, retornará o erro de comando não encontrado, mesmo que você tenha iniciado o MySQL.

Se você tentar verificar, por exemplo, as versões dos serviços pelo terminal, obterá o mesmo erro.

Para resolver esse problema e poder usar os serviços é preciso adicionar a pasta bin do XAMPP ao arquivo .bashrc

1. Para isso, abra o terminal e rode o seguinte comando:

```bash
sudo nano .bashrc
```

2. No final do arquivo que abrirá adicione a seguinte linha:

`export PATH=/opt/lampp/bin:$PATH`

3. Salve o arquivo com as modificações e para elas serem aplicadas rode o seguinte comando:

```bash
source .bashrc
```

Após isso já será possível usar todos os serviços do XAMPP

**OBS**: Para acessar o MySQL é preciso estar logado como root e por padrão a senha do root é vazia.

## Liberar acesso à pasta htdocs

Para criar seus projetos usando o XAMPP você deve criar as pastas dos seus projetos dentro da pasta htdocs, no entanto, por padrão essa pasta não é habilitada para que os usuários comuns do sistema criem pastas dentro dela.

1. Para liberar o acesso rode o seguinte comando no terminal:

```bash
sudo chmod 777 -R /opt/lampp/htdocs
```

A partir de agora você já pode criar suas pastas e arquivos normalmente.

## Conclusão

A partir de agora você já pode usar todos os serviços oferecidos pelo XAMPP. Espero que esse artigo tenha sido útil para você e se acha que ele pode ser útil para outras pessoas, compartilhe.

# Instalação do Moodle com XAMPP

Após iniciar seu servidor web local, abra seu navegador e digite http://localhost/phpmyadmin/. Esse local administra o banco de dado MySQL instalado pelo XAMPP. Uma tela complexa cheia de botões irá aparecer, procure o campo “create new database“, preencha com a palavra “moodle” e aperte “create“. Pronto, agora você tem seu novo Banco de Dados especial para o Moodle pronto para receber os arquivos.

Agora faça download da última versão do Moodle e descompacte o arquivo final. Haverá uma pasta nomeada “moodle” com diversos arquivos dentro, esses são os arquivos do programa que devem ser hospedados. Copie essa pasta e cole no seguinte caminho:

- MAC OS: /Applications/XAMPP/xamppfiles/htdocs/
- Windows: C:/xampp/htdocs/
- Debian: /opt/lampp/htdocs

Esse local “htdocs” onde o arquivo do Moodle ficará é a Hospedagem de Arquivo instalada pelo XAMPP. Cada pasta criada nesse local poderá ser acessada pela url http://localhost/pasta em seu navegador, assim você pode acessar todos osCMS’sque pretende instalar em seu servidor local.

O próximo passo é escrever no seu navegador o código http://localhost/moodle, onde a instalação irá começar, então siga as etapas abaixo:

1. Escolha a linguagem “Português – Brasil (pt_br)” e aperte “Próximo”;

2. Não altere nada e aperte “Próximo”;

3. Certifique-se de que a seleção está “Improved MySQL (native/mysqli)” e aperte “Próximo”;

4. Preencha conforme abaixo e aperte “Próximo”:  
    4.1. Host da base de dados: localhost  
    4.2. Nome da base de dados: moodle  
    4.3. Usuário da base de dados: root  
    4.4. Senha da base de dados: não coloque nada  
    4.5. Prefixo das tabelas: mdl_  
    4.6. Porta de banco de dados: não coloque nada  
    4.7. Unix socket: não coloque nada  

5. Aperte “Continuar”;

6. Aperte “Continuar”;

7. Pode demorar um pouco, depois aperte “Continuar”;
  
8. Preencha conforme abaixo e aperte “Atualizar perfil”:  
    8.1. Identificação de usuário: admin  
    8.2. Nova senha: aA1*bbbbbb  
    8.3. Forçar mudança de senha: você escolhe  
    8.4. Nome: Administrador  
    8.5. Sobrenome: Usuário  
    8.6. Endereço de Email: seu email, como seu_email@site.com  
    8.7. Mostrar endereço de email: você escolhe  
    8.8. Cidade/Município: sua cidade  
    8.9. Selecione um País: seu país  
    8.10. Zona de fuso horário: Fuso horário do servidor (América/São_Paulo)  
    8.11. Descrição: você escolhe
   
9. Preencha conforme abaixo e aperte “Salvar mudanças”:  
    9.1. Nome completo do site: Moodle Teste  
    9.2. Nome breve do site: Moodle  
    9.3. Descrição da página inicial: você escolhe  
    9.4. Fuso-horário padrão: América/São_Paulo  
    9.5. Auto-registro: Desabilitar  

Finalmente você tem o Moodle para testes instalado em seu computador local. Nele, você pode utilizar todas as funcionalidades da plataforma e fazer os testes necessários. Sempre que reiniciar o seu computador, não se esqueça de ligar novamente o XAMPP, iniciar o Apache e o MySQL e escrever na url http://localhost/moodle.

**OBS**: Instalação no Servidor Final - A instalação do Moodle no seu servidor final, ou seja, http://seu_site.com é mais complicada, entretanto basta seguir os mesmos passos anteriores, apenas alterando algumas informações.
Primeiro que a Hospedagem de Arquivos não será feita no seu computador, e sim num local na internet. Para ter acesso à esse local, recomendamos softwares de Gerenciamento de Arquivos Remotos, sendo o Filezilla para Windows e Transmitpara MAC OS. Para ter acesso à hospedagem é preciso preencher os dados de FTP, você pode ter acesso à eles com a central de atendimento do serviço contratado. Assim que realizar a conexão, você deve enviar a pasta moodle para o diretório “public_html”.
Como os arquivos não estão mais no seu computador, o endereço localhost não será mais utilizado. O serviço de hospedagem que você contratar terá o novo endereço de Banco de Dados MySQL para que você crie a Base de Dados moodle, com login e senha próprios. Não se esqueça que, ao começar a inserir as informações no processo de instalação do Moodle, preencha as informações certas do Banco de Dados.

# Habilitar acesso ao Moodle Local através de outros Computadores

### Descobrir o IP do servidor

No terminal do servidor (onde o XAMPP e Moodle estão instalados), rode:

```bash
ip a
```

Procure pelo IP na interface que você usa (exemplo: enp2s0 ou wlan0), algo como:

`inet 10.125.1.2/24`

O número antes da barra (10.125.1.2) é o IP que você vai usar.

### Editar o arquivo config.php do Moodle
Abra o arquivo config.php do Moodle, que normalmente fica em:

`/opt/lampp/htdocs/moodle/config.php`

edite a linha:

`$CFG->wwwroot = 'http://localhost/moodle';`

para:

`$CFG->wwwroot = 'http://SEU_IP/moodle';`

para este caso:

`$CFG->wwwroot = 'http://10.125.1.2/moodle';`

### Acessar o Moodle de outro computador
No navegador do outro computador (na mesma rede), digite: http://10.125.1.2/moodle
