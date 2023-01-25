# Atividade AWS e Linux
## Descrição da atividade
Repositório para atividade prática sobre linux e AWS do PB da Compass UOL.
##### **REQUISITOS AWS:**
- Gerar uma chave pública para acesso ao ambiente;
- Criar 1 instância EC2 com o sistema operacional
Amazon Linux 2 (Família t3.small, 16 GB SSD);
- Gerar 1 elastic IP e anexar à instância EC2;
- Liberar as portas de comunicação para acesso
público: (22/TCP, 111/TCP e UDP, 2049/TCP/UDP, 80
/TCP, 443/TCP).


##### **REQUISITOS NO LINUX:**
- Configurar o NFS entregue;
- Criar um diretorio dentro do filesystem do NFS com
seu nome;
- Subir um apache no servidor - o apache deve estar
online e rodando;
- Criar um script que valide se o serviço esta online e
envie o resultado da validação para o seu diretorio no
nfs;
- O script deve conter - Data HORA + nome do serviço
+ Status + mensagem personalizada de ONLINE ou
offline;
- O script deve gerar 2 arquivos de saida: 1 para o
serviço online e 1 para o serviço OFFLINE;
- Preparar a execução automatizada do script a cada 5
minutos.
- Fazer o versionamento da atividade;
- Fazer a documentação explicando o processo de
instalação do Linux.
***
## Gerando chave pública e associando a uma nova instância EC2
- Dentro da AWS acessar EC2, ir até Redes e Segurança >> Pares de chaves.
- Clicar em "Criar novo par de chaves" .
- Dar um nome para chave, selecionar formato .pem, clicar em criar par de chave se salvar em um local seguro.
- Ainda no EC2 clicar em Instâncias >> instâncias, Executar instâncias.
- Configurar as Tags para a nova instâncias com Name, Project e CostCenter. Selecionar instância e volume para cada tag.
- Selecionar imagem de máquina Amazon Linux 2.
- Tipo de instância Família t3.small.
- Selecionar o par de chave criado anteriormente
- Definir 16GB de armazenamento SSD gp2
- Clicar em Executar instância

## Gerando um ip elástico e anexando à instância EC2
- Ainda em EC2 vá até Redes e segurança >> IPs elásticos.
- Clicar em "Alocar endereço IP elástico".
- Clicar em Alocar.
- Selecionar o IP elástico.
- Clicar em Ações.
- Selecionar Associar endereço IP elástico.
- Selecionar a instância EC2 e clicar em associar.

## Liberar as portas de comunicação para acesso

- Na EC2 vá em Redes e segurança >> Security groups.
- Selecionar o grupo de segurança da instância que foi criada.
- Clicar em editar Regras.
- Configurar da seguinte forma as regras: (22/TCP, 111/TCP e UDP, 2049/TCP/UDP, 80
/TCP, 443/TCP).

## Configurar o Gateway de internet

- Acesse na AWS a pagina de VPC, vá até Nuvem privada virtual >> Gateways da internet.
- Clicar em criar Gateway da internet.
- Dá um nome para gateway e clicar em criar gateway.
- Selecionar a gateway criada e ir em Ações e "Associar a VPC".
- Selecionar a VPC da instância EC2 e clicar em associar.

## Configurar a rota de internet

- Ainda na página VPC, clicar em Tabelas de rotas.
- Selecione a tabela de rotas da EC2, clique em Ações e Editar rotas.
- Clique em adicionar rota.
- Destino 0.0.0.0/0 e em Alvo selecione Gateway da internet e selecione o gateway criado anteriormente.
- Clique em Salvar alterações.
