# Criando uma segunda vm seguindo a configuração da primeira atividade
Na VirtualBox, crie uma nova máquina. as opções recomendadas pelo sistema da VM são as melhores para o momento de instalação, como na primeira vm.
É possível fazer melhorias personalizadas nas configurações da máquina antes mesmo da instalação.
Em configurações, deve-se entrar em aquisição-extensão e selecionar a imagem ISO) com a qual essavd.iso virtual deve interagir.
Iniciar uma máquina.
Selecione Instalar Oracle Linux.
Na parte de escolher o idioma, é recomendado escolher o inglês padrão.
Altere o layout do teclado, se necessário (ex: alterar o padrão do teclado para português Brasil).
Em Destino de Instalação, selecione o disco. uma. Em Storage Configuration, selecione Costum, depois confirme em Done (Isso permitirá que façamos repartições personalizadas no nosso hd automaticamente durante a instalação). b. Selecione Clique aqui para criá-los automaticamente (selecionando essa opção ele nos apresentará como partições que serão criadas e nos permitirá criar e redimensionar a quantidade de memória em cada uma das repartições). c. redimensione / e /home e tenha a pasta /tmp e /var/lib/docker (!a /var/lib/docker tem que ter 10 GIB e o File System tem que estar selecionado em ext4 | a pasta / tem que ter no mínimo 10 GIB pra rodar o sistema | e as pasta /var, /tmp, /home e / tem que estar com o File System padrão que é o xfs !). d. Selecione Concluído e depois Aceitar Alterações.
Vá em time & date para alterar o padrão de hora e dados para o de Brasília.
Vá em Software Selection e mude para o pacote de instalação Minimal Install.
Vá em Root Password e defina uma senha para o usuário Root.
Vá em User Creation e defina um usuário Root para usar.
Vá em Network & Host.. e ative a internet.
Agora só instalar no Begin Installation.

existe uma outra opção que seria clonar a VM ultilizada no trabalho anterior, e poupar tempo.

# Configurando o acesso ssh
Execute o comando sudo vi /etc/ssh/sshd_config e aperte : depois digite set number isso fará com que apareçam números nas linhas, agora altere a seguintes linhas respectivamente:
43 PermitRootLogin no
48 PubkeyAuthentication yes
84 #GSSAPIAuthentication yes
85 #GSSAPICleanupCredentials no
101 UsePAM yes
Depois salve apertando esc seguido de :wq para salvar e sair.
Execute o comando systemctl restart sshd depois systemctl inicia sshd seguido de systemctl habilita sshd e pronto.

# Configurando a internet
Execute o comando cd /etc/sysconfig/network-scripts/ seguido de sudo vi ifcfg-enp0s3 ou sudo vi {unico arquivo do diretório} e mude a configuração BOOTPROTO=dhcp para static e adicione as seguintes linhas:
IPADDR=10.0.2.15
NETMASK=255.255.255.0
GATEWAY=10.0.2.2
Depois salve apertando esc seguido de :wq para salvar e sair.
Execute o comando systemctl restart network caso não funcione dê um reboot.
Confira através do ping google.com ou do yum install mlocate se a internet está funcionando.

# Configurando o DNS
Execute o seguinte comando sudo vi /etc/hosts e adicione a seguinte linha: 127.0.0.1 labmongodbancodocker depois salve esc aperte :wq para salvar e sair.
Vá no arquivo C:\Windows\System32\drivers\etc\hosts do Windows e adicione a seguinte linha: 127.0.0.1 labmongodbancodocker depois salve e saia.

