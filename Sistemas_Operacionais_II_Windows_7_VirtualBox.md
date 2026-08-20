# Sistemas Operacionais II — Instalação e Configuração do Windows 7 em Máquina Virtual

## 1. Introdução

Este material apresenta a criação e a configuração de uma máquina virtual no **Oracle VM VirtualBox**, utilizando o **Windows 7 Enterprise 64 bits** como sistema operacional convidado.

A atividade envolve principalmente:

- criação de uma máquina virtual;
- definição dos recursos de hardware virtual;
- instalação do Windows 7;
- criação do usuário e identificação do computador;
- configuração inicial do sistema;
- configuração de data, hora e fuso horário;
- configuração do adaptador de rede;
- definição de endereço IP;
- acesso às propriedades do protocolo TCP/IPv4;
- verificação das conexões de rede;
- configuração do Firewall do Windows.

> **Objetivo:** compreender, na prática, como um sistema operacional pode ser instalado e configurado dentro de um ambiente virtualizado, além de observar as principais configurações de rede e segurança do Windows 7.

---

# 2. Conceitos importantes

## 2.1 Máquina virtual

Uma **máquina virtual (VM — Virtual Machine)** é um computador criado por software dentro de outro computador.

Ela possui recursos virtuais próprios, como:

- memória RAM;
- processador;
- disco rígido;
- placa de rede;
- unidade óptica;
- sistema operacional.

No exercício, o computador físico executa o **VirtualBox**, e o VirtualBox executa o **Windows 7** como sistema operacional convidado.

### Estrutura utilizada

```text
COMPUTADOR FÍSICO
        |
        v
Oracle VM VirtualBox
        |
        v
Máquina Virtual
"ltape Windows 7 Manhã"
        |
        v
Windows 7 Enterprise 64 bits
```

---

# 3. Criação da máquina virtual no VirtualBox

A primeira imagem apresenta a tela de resumo da criação da máquina virtual.

## 3.1 Nome da máquina virtual

Foi definida uma máquina virtual com o nome:

```text
ltape Windows 7 Manhã
```

O nome serve para identificar a VM dentro do VirtualBox.

É importante utilizar nomes organizados, principalmente quando existem várias máquinas virtuais no mesmo computador.

---

## 3.2 Local de armazenamento

A máquina virtual é armazenada em uma pasta específica do VirtualBox.

Essa pasta contém os arquivos utilizados pela VM, como:

- disco virtual;
- arquivos de configuração;
- informações da máquina virtual;
- snapshots, quando utilizados.

---

## 3.3 Imagem ISO

Foi selecionada uma imagem ISO do Windows 7.

A ISO funciona como uma mídia de instalação virtual, equivalente a colocar um DVD de instalação na unidade óptica de um computador físico.

Na atividade, o sistema identificado é:

```text
Windows 7 Enterprise
Windows 7 — 64 bits
```

---

# 4. Configuração do hardware virtual

Na tela de resumo do VirtualBox aparecem os recursos destinados à máquina virtual.

## 4.1 Memória RAM

Foi configurada:

```text
Memória principal: 2048 MB
```

Ou seja:

```text
2048 MB = 2 GB de RAM
```

Essa memória será utilizada pelo Windows 7 enquanto a máquina virtual estiver em execução.

### Por que definir a memória?

A máquina virtual precisa de memória própria para executar o sistema operacional.

Entretanto, essa memória é retirada temporariamente da memória RAM do computador físico.

Por isso, não é recomendável reservar toda a RAM do computador para uma VM.

---

## 4.2 Processador

Foi configurado:

```text
Processadores: 1
```

Isso significa que a máquina virtual terá acesso a um processador virtual.

Para uma atividade básica com Windows 7, um processador virtual pode ser suficiente.

---

## 4.3 EFI

A opção apresentada é:

```text
Use EFI: false
```

Isso significa que a máquina virtual não utilizará EFI/UEFI para o processo de inicialização.

O sistema será iniciado utilizando o método de BIOS virtual tradicional.

---

## 4.4 Disco rígido virtual

Foi configurado:

```text
Hard Disk Size: 15,00 GB
```

O disco virtual funciona como o HD/SSD de um computador físico.

Dentro dele serão armazenados:

- arquivos do Windows;
- programas;
- configurações;
- arquivos do usuário;
- arquivos temporários.

### Atenção

Os **15 GB** correspondem ao espaço disponível para o disco virtual configurado na atividade. Esse espaço deve ser suficiente para a finalidade didática apresentada, mas é pequeno para usos modernos mais exigentes.

---

# 5. Resumo da configuração da VM

A configuração observada nas imagens pode ser organizada da seguinte forma:

| Recurso | Configuração |
|---|---|
| Software de virtualização | Oracle VM VirtualBox |
| Sistema operacional | Windows 7 Enterprise |
| Arquitetura | 64 bits |
| Memória RAM | 2048 MB |
| Processadores | 1 |
| EFI | Desativado |
| Disco virtual | 15 GB |
| Instalação | A partir de imagem ISO |

---

# 6. Início da instalação do Windows 7

Após a criação da máquina virtual, o Windows 7 é iniciado dentro do VirtualBox.

A instalação utiliza a imagem ISO configurada anteriormente.

Durante o processo, o instalador apresenta as etapas necessárias para preparar o sistema operacional.

---

# 7. Seleção do disco para instalação

Em uma das telas, o instalador apresenta o disco virtual e suas partições.

A imagem mostra uma pequena partição reservada pelo sistema e espaço disponível para a instalação.

### Partição reservada pelo sistema

A imagem apresenta aproximadamente:

```text
100 MB
```

Essa área é criada pelo instalador para funções relacionadas ao sistema.

### Espaço não alocado

Também aparece espaço não alocado no disco.

Esse espaço é utilizado para criar a partição onde o Windows será instalado.

---

# 8. Criação do usuário

Durante a configuração inicial do Windows 7, é solicitado o nome de usuário.

Na imagem, aparece:

```text
Nome de usuário: mav
```

O usuário representa a conta utilizada para acessar o sistema operacional.

Uma conta de usuário permite:

- autenticação;
- acesso ao sistema;
- personalização;
- utilização de arquivos;
- execução de programas;
- aplicação de permissões.

---

# 9. Nome do computador

Também é solicitado um nome para identificar o computador na rede.

Na imagem aparece:

```text
Nome do computador: ESTMI5PC
```

O nome do computador é importante em ambientes de rede porque permite identificar a máquina.

Por exemplo:

```text
Computador A → ESTMI5PC
Computador B → SERVIDOR
Computador C → CLIENTE
```

Isso facilita a identificação dos dispositivos durante atividades de administração de redes.

---

# 10. Definição da senha

A instalação apresenta uma etapa para criação de senha para a conta.

São apresentados campos para:

- senha;
- confirmação da senha;
- dica de senha.

## 10.1 Senha

A senha protege a conta contra acesso não autorizado.

Uma senha deve ser:

- difícil de adivinhar;
- diferente de informações pessoais;
- preferencialmente longa;
- composta por diferentes tipos de caracteres.

## 10.2 Confirmação

A confirmação serve para verificar se a senha foi digitada corretamente nas duas tentativas.

## 10.3 Dica de senha

A dica pode ajudar o usuário a lembrar a senha.

Porém, ela não deve revelar diretamente a senha.

---

# 11. Configurações de atualização do Windows

O Windows 7 apresenta opções relacionadas às atualizações.

Entre as opções mostradas estão:

### Usar configurações recomendadas

Permite que o sistema instale atualizações importantes e recomendadas.

### Instalar somente atualizações importantes

Prioriza atualizações importantes para o funcionamento e a segurança do sistema.

### Perguntar depois

Adia a decisão sobre as configurações de atualização.

## Importância das atualizações

As atualizações de um sistema operacional podem corrigir:

- falhas de segurança;
- problemas de funcionamento;
- erros do sistema;
- vulnerabilidades.

Em um ambiente real, manter sistemas atualizados é uma das medidas básicas de segurança.

---

# 12. Configuração de data e hora

Outra etapa apresenta as configurações de data e hora.

Na imagem aparece o fuso:

```text
(UTC-03:00) Brasília
```

Também são apresentadas opções relacionadas ao ajuste automático do relógio.

## Por que data e hora são importantes?

A configuração correta de data e hora é importante para:

- registros de eventos;
- logs;
- autenticação;
- certificados;
- comunicação em rede;
- atualização do sistema;
- organização de arquivos.

Em redes corporativas, diferenças significativas de horário entre máquinas podem causar problemas em determinados serviços.

---

# 13. Configuração da rede no VirtualBox

Depois da instalação, a atividade passa para a configuração da rede.

No menu **Dispositivos** do VirtualBox aparece a opção relacionada à configuração da rede.

A placa de rede virtual permite que o Windows 7 se comunique com:

- o computador físico;
- outras máquinas virtuais;
- uma rede local;
- a Internet, dependendo da configuração utilizada.

---

# 14. Modo Bridge / Placa em modo Bridge

A configuração mostrada na imagem indica:

```text
Ligado a: Placa em modo Bridge
```

Também aparece uma interface física semelhante a:

```text
Realtek PCIe GbE Family Controller
```

## O que é Bridge?

O modo **Bridge**, também chamado de **Placa em modo Bridge**, faz com que a máquina virtual participe da rede como se fosse outro dispositivo conectado à rede física.

A comunicação pode ser representada assim:

```text
              Roteador / Rede
                    |
          +---------+---------+
          |                   |
          v                   v
   Computador físico       Máquina Virtual
                          Windows 7
```

Nesse modo, a máquina virtual pode receber um endereço IP da rede em que o computador físico está conectado, dependendo da configuração do ambiente.

---

# 15. Adaptador de rede virtual

Dentro do Windows 7, a placa de rede virtual aparece como uma conexão de rede.

O VirtualBox fornece o hardware virtual, enquanto o Windows utiliza um driver para se comunicar com esse dispositivo.

A imagem mostra uma interface semelhante a:

```text
Intel(R) PRO/1000 MT Desktop Adapter
```

Isso representa o adaptador de rede apresentado à máquina virtual.

---

# 16. Central de Rede e Compartilhamento

No Windows 7, a área:

```text
Painel de Controle
→ Rede e Internet
→ Central de Rede e Compartilhamento
```

permite visualizar e administrar informações relacionadas à rede.

Nessa área é possível observar:

- rede ativa;
- tipo de rede;
- conexão com a Internet;
- configurações do adaptador;
- opções de compartilhamento;
- diagnóstico de problemas.

---

# 17. Conexões de Rede

A atividade também apresenta a área:

```text
Painel de Controle
→ Rede e Internet
→ Conexões de Rede
```

Nessa tela aparece a conexão de rede do computador.

Entre as operações disponíveis estão:

- ativar/desativar a conexão;
- diagnosticar problemas;
- visualizar o status;
- acessar propriedades;
- renomear a conexão.

---

# 18. Propriedades do adaptador

Ao acessar as propriedades da conexão de rede, o Windows apresenta os componentes utilizados pela interface.

Entre eles aparece:

```text
Protocolo TCP/IPv4
```

Também são apresentados componentes relacionados a:

- cliente de redes;
- compartilhamento de arquivos e impressoras;
- protocolo de Internet;
- agendador de pacotes;
- outros componentes de rede.

---

# 19. TCP/IP

O **TCP/IP** é um conjunto de protocolos utilizado para comunicação em redes.

O IPv4 utiliza endereços no formato:

```text
xxx.xxx.xxx.xxx
```

Por exemplo:

```text
192.168.1.10
```

Cada dispositivo dentro de uma determinada rede precisa possuir uma configuração IP compatível com a rede para conseguir se comunicar corretamente.

---

# 20. Configuração manual do IPv4

A imagem mostra a opção:

```text
Usar o seguinte endereço IP
```

Também aparece um endereço configurado manualmente semelhante a:

```text
192.100.0.135
```

e uma máscara de sub-rede.

A configuração manual é conhecida como **IP estático**.

## IP estático

No IP estático, o administrador informa manualmente os parâmetros da rede.

Normalmente são configurados:

```text
Endereço IP
Máscara de sub-rede
Gateway padrão
Servidor DNS
```

---

# 21. DHCP x IP estático

Existem duas formas comuns de obter uma configuração IPv4.

## DHCP

```text
Computador
     |
     v
Servidor DHCP
     |
     v
IP + Máscara + Gateway + DNS
```

O servidor DHCP fornece automaticamente as informações de rede.

## IP estático

```text
Administrador
      |
      v
Configuração manual
      |
      +--> IP
      +--> Máscara
      +--> Gateway
      +--> DNS
```

A configuração mostrada na atividade utiliza a opção de definir manualmente o endereço IP.

---

# 22. Gateway padrão

O **gateway padrão** é o dispositivo utilizado para encaminhar tráfego para outras redes.

Em uma rede doméstica, normalmente o gateway é o roteador.

Exemplo:

```text
PC/VM
192.168.1.20
      |
      v
Roteador
192.168.1.1
      |
      v
Internet
```

Na imagem da atividade, o campo de gateway aparece sem preenchimento.

Isso indica que, naquela configuração apresentada, não foi informado um gateway padrão.

---

# 23. DNS

O DNS é responsável por realizar a resolução de nomes.

Por exemplo:

```text
www.exemplo.com
        ↓
Endereço IP
```

Sem DNS, o usuário teria que utilizar diretamente os endereços IP dos servidores.

A tela mostrada na atividade possui campos para:

```text
Servidor DNS preferencial
Servidor DNS alternativo
```

---

# 24. Firewall do Windows

A última etapa apresenta as configurações do **Firewall do Windows**.

O firewall é um mecanismo de segurança que controla conexões de rede de acordo com regras definidas.

A configuração é apresentada separadamente para diferentes tipos de rede.

Entre elas:

- rede doméstica ou de trabalho;
- rede pública.

---

# 25. Firewall em redes particulares

A tela apresenta opções como:

```text
Ativar o Firewall do Windows
```

e:

```text
Desativar o Firewall do Windows
```

Também existe a opção para bloquear todas as conexões de entrada.

## Função do firewall

O firewall pode ajudar a impedir conexões de entrada não autorizadas.

Exemplo:

```text
Internet
   |
   | tentativa de conexão
   v
[ FIREWALL ]
   |
   +---- permitido → aplicação/serviço
   |
   +---- bloqueado → conexão impedida
```

---

# 26. Firewall em redes públicas

A configuração para redes públicas possui comportamento semelhante.

Uma rede pública deve ser tratada com maior cautela porque o computador pode estar conectado a uma rede que não é confiável.

Exemplos:

- Wi-Fi público;
- redes compartilhadas;
- ambientes desconhecidos.

Por isso, o firewall é um componente importante de proteção.

---

# 27. Relação entre VirtualBox, sistema operacional e rede

A atividade permite visualizar três níveis diferentes:

```text
┌─────────────────────────────────────┐
│       COMPUTADOR FÍSICO             │
│                                     │
│   Sistema operacional hospedeiro    │
│              │                      │
│              v                      │
│        Oracle VirtualBox            │
│              │                      │
│              v                      │
│      Máquina Virtual                │
│              │                      │
│              v                      │
│       Windows 7 Enterprise          │
│              │                      │
│              v                      │
│       Placa de rede virtual         │
└──────────────┬──────────────────────┘
               │
               v
          Rede física
```

O VirtualBox cria uma camada de virtualização entre o computador físico e o sistema operacional convidado.

---

# 28. Sequência geral da atividade

A sequência observada nas imagens pode ser resumida em:

```text
1. Abrir o VirtualBox
        ↓
2. Criar uma nova máquina virtual
        ↓
3. Informar o nome da VM
        ↓
4. Selecionar a ISO do Windows 7
        ↓
5. Definir 2 GB de RAM
        ↓
6. Definir 1 processador
        ↓
7. Definir disco virtual de 15 GB
        ↓
8. Iniciar a VM
        ↓
9. Instalar o Windows 7
        ↓
10. Criar usuário
        ↓
11. Definir nome do computador
        ↓
12. Definir senha
        ↓
13. Configurar atualizações
        ↓
14. Configurar data e hora
        ↓
15. Configurar adaptador de rede
        ↓
16. Selecionar modo Bridge
        ↓
17. Verificar conexão de rede
        ↓
18. Configurar TCP/IPv4
        ↓
19. Verificar IP e máscara
        ↓
20. Configurar/verificar Firewall
```

---

# 29. O que foi aprendido

A atividade demonstra, de maneira prática, vários conceitos importantes de Sistemas Operacionais II.

## Virtualização

Foi possível criar um computador virtual dentro de um computador físico utilizando o VirtualBox.

## Instalação de sistema operacional

Foi realizada a instalação do Windows 7 Enterprise utilizando uma imagem ISO.

## Gerenciamento de recursos

Foram definidos recursos virtuais:

- RAM;
- CPU;
- armazenamento.

## Gerenciamento de usuários

Foi criada uma conta de usuário e definido o nome do computador.

## Configuração de rede

Foram analisados:

- adaptador de rede;
- modo Bridge;
- conexão de rede;
- TCP/IPv4;
- endereço IP;
- máscara;
- gateway;
- DNS.

## Segurança

Foi analisado o Firewall do Windows e suas opções para diferentes tipos de rede.

---

# 30. Checklist da atividade

- [x] Abrir o Oracle VM VirtualBox
- [x] Criar a máquina virtual
- [x] Definir o nome da VM
- [x] Selecionar a ISO do Windows 7
- [x] Configurar 2048 MB de RAM
- [x] Configurar 1 processador
- [x] Configurar disco virtual de 15 GB
- [x] Iniciar a instalação
- [x] Criar usuário
- [x] Definir nome do computador
- [x] Configurar senha
- [x] Configurar atualizações
- [x] Configurar data e hora
- [x] Configurar a placa de rede
- [x] Selecionar modo Bridge
- [x] Acessar as conexões de rede
- [x] Abrir as propriedades do TCP/IPv4
- [x] Verificar configuração de IP
- [x] Acessar as configurações do Firewall

---

# 31. Conclusão

A atividade apresenta um laboratório prático de instalação e configuração de um sistema operacional utilizando virtualização.

O uso do **Oracle VM VirtualBox** permite criar uma máquina virtual sem a necessidade de instalar o Windows 7 diretamente no computador físico. Dentro dessa máquina virtual, foram definidos recursos de hardware, instalado o sistema operacional e realizadas configurações básicas de usuário, data e hora, rede e segurança.

A parte de redes é especialmente importante porque demonstra a relação entre o sistema operacional e o hardware de rede virtualizado. O modo Bridge permite que a máquina virtual participe da rede física, enquanto as propriedades do TCP/IPv4 permitem configurar os parâmetros necessários para a comunicação.

Por fim, a análise do Firewall demonstra a importância de mecanismos de segurança para controlar conexões e reduzir riscos de acessos não autorizados.

Assim, a atividade reúne conceitos fundamentais de **virtualização, instalação de sistemas operacionais, gerenciamento de recursos, configuração de rede e segurança**, proporcionando uma visão prática da administração de um sistema operacional em ambiente virtualizado.

---

