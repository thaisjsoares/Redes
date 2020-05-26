# Redes

## Projeto da formação em Administrador de Redes do Alura.

**Site:** [Alura](www.alura.com.br)

**Duração:** 90 horas (divididas em 10 cursos)

**Progresso atual:** 3/10 cursos finalizados

**Programa utilizado:** Packet Tracer 7.3.0


## Descrição:

No cenário hipotético da formação, fui contratada pela empresa fictícia * *Multillidae* * para montar e configurar uma rede corporativa. A empresa, de aproximadamente 400 funcionários, conta com o departamento de vendas e com o departamento de finanças. Há por volta de 300 funcionários trabalhando no departamento de vendas e cerca de 100 funcionários no departamento de finanças.

## Objetivo:

Implementar um rede corporativa com as seguintes características:

- os departamentos devem estar em redes diferentes;
- as máquinas dos funcionários devem receber ips automaticamente, de acordo com o departamento;
- deve haver redundância para garantir o acesso mesmo quando algum cabo for danificado;
- a distribuição dos ips deve ser eficiente, considerando o número de funcionários;
- apenas os gerentes de departamento podem ter acesso ao servidor interno da empresa e
- todos precisam ter acesso à internet.

## Passos realizados:

1.Criei uma vlan para cada departamento. As configurações foram adicionadas tanto ao switch de cada departamento quanto ao roteador.
2.Dividi a interface do roteador em sub-interfaces, uma para atribuir ips automaticamente (através do dhcp) para a vlan do departamento de vendas e outra para atribuir ips (dhcp) para a vlan do departamento de finanças.
3.Adicionei switches de forma a criar uma redundância: os switches de cada departamento se comunicam um com o outro, além de cada um se comunicar com um terceiro switch, esse diretamente ligado ao roteador. O terceiro switch tem o modo * *switchport trunk* * para que possa lidar com as duas vlans.
4.Transformei esse terceiro switch no switch root do * *spanning-tree protocol.* *
5.Devido ao número de funcionários, utilizei um número de ip da classe B. Porém, usei sub-redes para entregar 300 ips para o departamento de vendas e 100 ips para o departamento de finanças, evitando a compra de mais ips do que necessário.
6.Acrescentei um servidor interno à empresa. Crei mais uma vlan para o servidor e ele recebeu um ip estático de uma terceira sub-rede.
7.No roteador, criei uma nova sub-interface para permitir a comunicação dessa terceira vlan com as outras duas, ou seja, para que o servidor pudesse ser acessado de dentro dos departamentos.
8.Atribuí ips estáticos aos gerentes e excluí esses ips do pool do dhcp. Em seguida, criei uma lista de acesso permitindo que pacotes tcp chegassem ao servidor vindos exclusivamente dos ips estáticos dos dois gerentes e negando todos os outros. As demais comunicações foram permitidas.
9.Conectei o roteador da empresa ao roteador externo, do provedor de serviço internet. Para tanto, adicionei uma placa de rede serial ao roteador da empresa e atribuí um ip público à porta serial (na mesma sub-rede que o ip do roteador externo, do provedor).
10.Por fim, criei uma lista de acesso NAT no roteador da empresa e configurei o nat para traduzir todos os ips da empresa para ips públicos, permitindo o acesso à internet.

## Lista de arquivos:

curso.pkt - Projeto salvo no Packet Tracer com todas as configurações feitas.
curso.png - Foto da tela do Packet Tracer com o projeto aberto.
