# Aula 03 --- Active Directory e Gerenciamento de Usuários

> **Guia reorganizado a partir do arquivo `aula 03 2.docx`.**
>
> O documento original tem 3 páginas e grande parte do conteúdo está
> apresentada em capturas de tela. O roteiro abaixo transforma a
> sequência dos prints em um passo a passo mais fácil de acompanhar. O
> arquivo original orienta a criação de usuários em **Contabilidade** e
> **RH**, a configuração da máquina Windows 7 em **Rede Interna** e o
> uso do usuário **administrador**.
>
> **Atenção:** as senhas abaixo são as que aparecem no roteiro da aula e
> devem ser tratadas apenas como credenciais do laboratório, não como
> senhas reais.

------------------------------------------------------------------------

## 1. Visão geral da atividade

A atividade trabalha, em conjunto:

-   Windows Server;
-   Active Directory Domain Services (AD DS);
-   domínio `dominiom15.net`;
-   unidades organizacionais (OUs);
-   usuários;
-   grupos;
-   máquina cliente Windows 7;
-   configuração de rede;
-   pastas compartilhadas/locais;
-   permissões de segurança;
-   testes de acesso e comunicação.

### Ordem recomendada

``` text
1. Configurar o servidor
        ↓
2. Configurar IP e DNS
        ↓
3. Instalar o Active Directory
        ↓
4. Criar as OUs
        ↓
5. Criar os grupos
        ↓
6. Criar os usuários
        ↓
7. Configurar o Windows 7
        ↓
8. Colocar o Windows 7 na Rede Interna
        ↓
9. Configurar o acesso ao domínio
        ↓
10. Criar as pastas
        ↓
11. Configurar as permissões
        ↓
12. Testar a comunicação e o acesso
```

------------------------------------------------------------------------

# 2. Informações utilizadas no laboratório

  Item                  Configuração
  --------------------- -----------------------------------
  Sistema servidor      Windows Server 2008 R2 Enterprise
  Sistema cliente       Windows 7 Enterprise
  Domínio               `dominiom15.net`
  IP do servidor        `192.100.15.1`
  Máscara               `255.255.255.0`
  DNS                   `192.100.15.1`
  OUs                   `Contabilidade` e `RH`
  Grupos                `GR_Contabilidade` e `GR_RH`
  Pasta Contabilidade   `C:\Fatec\Contabilidade`
  Pasta RH              `C:\Fatec\RH`

------------------------------------------------------------------------

# 3. Configuração do servidor

## 3.1 Conferir o Windows Server

No servidor, confirme que você está trabalhando com o Windows Server
utilizado na aula.

Os prints mostram o ambiente do **Windows Server 2008 R2 Enterprise**.

**Prints relacionados:** aproximadamente 4--6.

------------------------------------------------------------------------

## 3.2 Configurar o endereço IP

A máquina servidor precisa possuir um endereço IP definido para que o
cliente consiga localizar o servidor e o serviço de domínio.

Use os valores apresentados no roteiro:

``` text
Endereço IP: 192.100.15.1
Máscara:     255.255.255.0
DNS:         192.100.15.1
```

### Procedimento

1.  Abra as configurações de rede do Windows Server.
2.  Localize a conexão de rede.
3.  Abra as propriedades da conexão.
4.  Entre nas propriedades do protocolo IPv4.
5.  Configure o endereço IP.
6.  Configure a máscara de sub-rede.
7.  Configure o DNS apontando para o próprio servidor.
8.  Confirme as alterações.

> **Por que o DNS aponta para o próprio servidor?**\
> Neste laboratório, o servidor será responsável pelos serviços
> relacionados ao domínio. Por isso, a máquina cliente deverá conseguir
> consultar o servidor para localizar o domínio.

------------------------------------------------------------------------

# 4. Instalação do Active Directory

## 4.1 Abrir as ferramentas administrativas

O roteiro apresenta o caminho:

``` text
Ferramentas Administrativas
    ↓
Usuários e Computadores do AD
    ↓
Novo Objeto
```

O documento também mostra a criação dos objetos de usuário a partir do
**Usuários e Computadores do Active Directory**.

**Prints relacionados:** 1--3 e 32--39.

------------------------------------------------------------------------

## 4.2 Instalar o AD DS

A sequência de prints mostra o **Assistente de Instalação dos Serviços
de Domínio do Active Directory**.

A instalação passa por telas como:

1.  Configuração da implantação;
2.  criação de uma nova floresta;
3.  definição do domínio;
4.  níveis funcionais;
5.  configuração/aviso de DNS;
6.  senha de recuperação dos serviços de diretório;
7.  caminhos de banco de dados, logs e SYSVOL;
8.  revisão das configurações;
9.  instalação.

### Domínio utilizado

``` text
dominiom15.net
```

Na tela de criação da nova floresta, utilize o domínio apresentado nos
prints.

**Prints relacionados:** aproximadamente 40--52.

------------------------------------------------------------------------

## 4.3 Criar uma nova floresta

Quando o assistente solicitar a configuração de implantação:

1.  Selecione a opção para criar uma **nova floresta**.
2.  Informe o domínio raiz:

``` text
dominiom15.net
```

3.  Avance para a próxima etapa.

> Não altere o nome do domínio sem orientação do professor, pois as
> demais configurações do laboratório dependem dele.

------------------------------------------------------------------------

## 4.4 Configurações do assistente

Continue pelas telas apresentadas nos prints.

O assistente poderá apresentar avisos, especialmente relacionados ao
DNS.

### Quando aparecer um aviso

Leia a mensagem apresentada e continue conforme a sequência demonstrada
no material da aula.

Depois, informe a senha solicitada para os serviços de recuperação do
Active Directory.

------------------------------------------------------------------------

## 4.5 Revisar e instalar

Antes de finalizar:

1.  Confira o domínio.
2.  Confira as configurações de DNS.
3.  Confira os caminhos apresentados.
4.  Revise o resumo da instalação.
5.  Inicie a instalação.
6.  Aguarde a conclusão.

Após a instalação, o servidor estará preparado para administrar o
domínio.

------------------------------------------------------------------------

# 5. Usuários e Computadores do Active Directory

Depois de configurar o domínio, abra:

``` text
Ferramentas Administrativas
→ Usuários e Computadores do Active Directory
```

Essa ferramenta será usada para criar e administrar:

-   usuários;
-   grupos;
-   unidades organizacionais.

------------------------------------------------------------------------

# 6. Criar as Unidades Organizacionais

A atividade trabalha com duas áreas:

``` text
Contabilidade
RH
```

A ideia é organizar os usuários de acordo com o setor.

### Criar a OU Contabilidade

1.  Abra **Usuários e Computadores do Active Directory**.
2.  Localize o domínio.
3.  Clique com o botão direito no local apropriado.
4.  Escolha a opção de criar uma nova **Unidade Organizacional**.
5.  Informe:

``` text
Contabilidade
```

6.  Confirme.

### Criar a OU RH

Repita o processo:

``` text
RH
```

Ao final, a estrutura deverá apresentar as duas áreas.

``` text
dominiom15.net
│
├── Contabilidade
│
└── RH
```

**Prints relacionados:** aproximadamente 32--39.

------------------------------------------------------------------------

# 7. Criar os grupos

A atividade utiliza grupos para facilitar o controle de permissões.

Crie:

``` text
GR_Contabilidade
GR_RH
```

### Grupo de Contabilidade

1.  Acesse a área de criação de objetos.
2.  Escolha **Grupo**.
3.  Informe:

``` text
GR_Contabilidade
```

4.  Confirme a criação.

### Grupo de RH

Repita:

``` text
GR_RH
```

Ao final:

``` text
dominiom15.net
│
├── Contabilidade
│   └── GR_Contabilidade
│
└── RH
    └── GR_RH
```

> Os prints do material mostram os grupos sendo utilizados nas
> configurações de segurança das pastas.

------------------------------------------------------------------------

# 8. Criar os usuários

## 8.1 Quantidade

O roteiro determina:

> **Criar 3 users em Contabilidade e 3 em RH.**

Portanto:

  Setor                 Quantidade
  --------------- ----------------
  Contabilidade         3 usuários
  RH                    3 usuários
  **Total**         **6 usuários**

------------------------------------------------------------------------

## 8.2 Criar um usuário

Dentro da OU correspondente:

1.  Clique com o botão direito.
2.  Escolha **Novo**.
3.  Selecione **Usuário**.
4.  Preencha os dados solicitados.
5.  Defina o nome de logon.
6.  Avance.
7.  Informe a senha indicada no material.
8.  Observe as opções de senha.

### Senha mostrada no roteiro

Para os usuários:

``` text
f@tec1234
```

### Opção de senha

O material orienta:

> **desmarca a primeira opção**

Ou seja, ao criar os usuários, observe a primeira opção relacionada à
alteração de senha no próximo logon e siga exatamente a configuração
mostrada no print.

------------------------------------------------------------------------

## 8.3 Exemplo de usuário

Um dos prints apresenta o nome:

``` text
Mavelyn Leme
```

Use o padrão demonstrado pelo professor para os demais usuários.

Outro print apresenta também propriedades de um usuário chamado:

``` text
Arthur Leme
```

Esses nomes servem para identificar os exemplos presentes nas capturas;
não substitua os nomes exigidos pelo exercício caso o professor tenha
definido outros.

------------------------------------------------------------------------

# 9. Relacionar usuários e grupos

Depois de criar os usuários, associe-os aos grupos correspondentes.

### Contabilidade

Os usuários de Contabilidade devem estar associados ao:

``` text
GR_Contabilidade
```

### RH

Os usuários de RH devem estar associados ao:

``` text
GR_RH
```

A organização fica conceitualmente assim:

``` text
GR_Contabilidade
├── Usuário 1
├── Usuário 2
└── Usuário 3

GR_RH
├── Usuário 1
├── Usuário 2
└── Usuário 3
```

------------------------------------------------------------------------

# 10. Configuração do Windows 7

O material possui uma etapa específica para o Windows 7.

O roteiro diz:

> **No win 7 mudar para rede interna.**

------------------------------------------------------------------------

## 10.1 Alterar a rede da máquina virtual

Se estiver utilizando uma máquina virtual:

1.  Desligue o Windows 7, se necessário.
2.  Abra as configurações da máquina virtual.
3.  Localize as configurações de rede.
4.  Altere o tipo de conexão para:

``` text
Rede Interna
```

5.  Salve.
6.  Inicie o Windows 7.

**Prints relacionados:** aproximadamente 7--13.

------------------------------------------------------------------------

# 11. Entrar no Windows 7

O material mostra as telas de login do Windows 7.

O usuário indicado no roteiro é:

``` text
administrador
```

A senha indicada é:

``` text
f@tec123
```

> **Importante:** essa senha aparece no arquivo da aula e deve ser usada
> somente no ambiente de laboratório.

------------------------------------------------------------------------

# 12. Configurar a rede do Windows 7

Depois de iniciar o Windows 7:

1.  Abra as configurações de rede.
2.  Verifique a conexão.
3.  Confirme que a máquina está na mesma rede interna utilizada pelo
    servidor.
4.  Configure o endereço de rede conforme o ambiente montado na aula.
5.  Confirme o DNS apontando para o servidor quando essa configuração
    for solicitada.

O ponto principal é que o Windows 7 consiga alcançar o servidor:

``` text
Windows 7
    │
    │ Rede Interna
    ↓
Windows Server
192.100.15.1
```

------------------------------------------------------------------------

# 13. Testar a comunicação com o servidor

Abra o Prompt de Comando no Windows 7.

Execute:

``` cmd
ping 192.100.15.1
```

### Resultado esperado

O Windows 7 deve conseguir receber respostas do servidor.

Exemplo conceitual:

``` text
Resposta de 192.100.15.1
```

Se houver resposta, a comunicação básica entre cliente e servidor está
funcionando.

Se não houver resposta, confira:

-   adaptador de rede;
-   configuração de Rede Interna;
-   endereço IP;
-   máscara;
-   DNS;
-   conexão das máquinas virtuais;
-   firewall, caso esteja interferindo no laboratório.

**Prints relacionados:** aproximadamente 5--6 e 53--57.

------------------------------------------------------------------------

# 14. Configuração das pastas

O material apresenta duas pastas:

``` text
C:\Fatec\Contabilidade
C:\Fatec\RH
```

## 14.1 Criar a estrutura

No Windows:

``` text
C:\
└── Fatec
    ├── Contabilidade
    └── RH
```

### Criar `Fatec`

1.  Abra o disco `C:`.
2.  Crie a pasta:

``` text
Fatec
```

### Criar `Contabilidade`

Dentro de `C:\Fatec`, crie:

``` text
Contabilidade
```

### Criar `RH`

Também dentro de `C:\Fatec`, crie:

``` text
RH
```

------------------------------------------------------------------------

# 15. Configurar as permissões

Essa é uma das partes mais importantes dos prints.

As pastas possuem configurações de segurança que utilizam os grupos
criados no Active Directory.

A lógica apresentada é:

``` text
Usuário
   ↓
Grupo do setor
   ↓
Permissão da pasta
```

Assim, em vez de configurar permissões individualmente para cada
usuário, o controle pode ser feito através do grupo.

------------------------------------------------------------------------

## 15.1 Permissões da pasta Contabilidade

A pasta:

``` text
C:\Fatec\Contabilidade
```

deve utilizar o grupo correspondente:

``` text
GR_Contabilidade
```

### Procedimento mostrado pelos prints

1.  Clique com o botão direito na pasta.
2.  Abra **Propriedades**.
3.  Entre na aba **Segurança**.
4.  Localize as configurações de permissões.
5.  Adicione o grupo:

``` text
GR_Contabilidade
```

6.  Configure as permissões conforme o exercício.
7.  Confirme.

------------------------------------------------------------------------

# 16. Permissões da pasta RH

A pasta:

``` text
C:\Fatec\RH
```

utiliza o grupo:

``` text
GR_RH
```

### Procedimento

1.  Clique com o botão direito na pasta `RH`.
2.  Abra **Propriedades**.
3.  Acesse **Segurança**.
4.  Localize a configuração de permissões.
5.  Adicione:

``` text
GR_RH
```

6.  Configure as permissões conforme mostrado na aula.
7.  Confirme.

Um dos prints mostra explicitamente:

``` text
GR_RH (DOMINIOM15\GR_RH)
```

------------------------------------------------------------------------

# 17. Herança de permissões

Os prints mostram também as configurações de **permissões avançadas** e
situações envolvendo herança.

Ao modificar permissões:

1.  Abra as configurações avançadas de segurança.
2.  Observe as entradas herdadas.
3.  Caso seja necessário modificar uma permissão herdada, utilize a
    opção apresentada pelo Windows para desabilitar a herança.
4.  Leia o aviso apresentado antes de confirmar.
5.  Faça a alteração somente conforme solicitado no exercício.

> **Cuidado:** desabilitar a herança pode alterar a forma como as
> permissões são aplicadas à pasta e aos arquivos internos.

**Prints relacionados:** aproximadamente 14--31.

------------------------------------------------------------------------

# 18. Estrutura final esperada

Ao terminar a organização do Active Directory, a estrutura conceitual
deve ficar próxima de:

``` text
dominiom15.net
│
├── Contabilidade
│   ├── Usuário 1
│   ├── Usuário 2
│   ├── Usuário 3
│   └── GR_Contabilidade
│
└── RH
    ├── Usuário 1
    ├── Usuário 2
    ├── Usuário 3
    └── GR_RH
```

E no sistema de arquivos:

``` text
C:\
└── Fatec
    ├── Contabilidade
    └── RH
```

------------------------------------------------------------------------

# 19. Checklist para não se perder

## Servidor

-   [ ] Windows Server configurado
-   [ ] IP `192.100.15.1`
-   [ ] Máscara `255.255.255.0`
-   [ ] DNS `192.100.15.1`
-   [ ] Active Directory instalado
-   [ ] Domínio `dominiom15.net`

## Active Directory

-   [ ] OU `Contabilidade`
-   [ ] OU `RH`
-   [ ] Grupo `GR_Contabilidade`
-   [ ] Grupo `GR_RH`
-   [ ] 3 usuários em Contabilidade
-   [ ] 3 usuários em RH
-   [ ] Usuários associados aos grupos corretos

## Windows 7

-   [ ] Máquina Windows 7 iniciada
-   [ ] Adaptador configurado como **Rede Interna**
-   [ ] Usuário `administrador`
-   [ ] Senha do laboratório configurada
-   [ ] Comunicação com o servidor testada

## Pastas

-   [ ] `C:\Fatec`
-   [ ] `C:\Fatec\Contabilidade`
-   [ ] `C:\Fatec\RH`
-   [ ] Permissões de Contabilidade configuradas
-   [ ] Permissões de RH configuradas
-   [ ] Herança revisada quando necessário

## Testes

-   [ ] `ping 192.100.15.1`
-   [ ] Cliente consegue localizar o servidor
-   [ ] Usuários estão criados
-   [ ] Grupos estão criados
-   [ ] Permissões estão associadas aos grupos corretos

------------------------------------------------------------------------

# 20. Resumo rápido da aula

``` text
WINDOWS SERVER
      │
      ├── IP: 192.100.15.1
      ├── DNS: 192.100.15.1
      │
      ↓
ACTIVE DIRECTORY
      │
      ├── domínio: dominiom15.net
      │
      ├── Contabilidade
      │     ├── usuários
      │     └── GR_Contabilidade
      │
      └── RH
            ├── usuários
            └── GR_RH
                    │
                    ↓
              PERMISSÕES
                    │
          ┌─────────┴─────────┐
          ↓                   ↓
 C:\Fatec\Contabilidade   C:\Fatec\RH
          │                   │
          ↓                   ↓
 GR_Contabilidade          GR_RH
```

------------------------------------------------------------------------

# 21. Sequência para fazer a aula sem voltar toda hora

Se você estiver realizando a prática do zero, siga esta ordem:

### Parte 1 --- Servidor

1.  Inicie o Windows Server.
2.  Configure o IP.
3.  Configure o DNS.
4.  Instale o Active Directory.
5.  Crie/configure o domínio `dominiom15.net`.
6.  Reinicie quando solicitado.

### Parte 2 --- Active Directory

7.  Abra **Usuários e Computadores do Active Directory**.
8.  Crie `Contabilidade`.
9.  Crie `RH`.
10. Crie `GR_Contabilidade`.
11. Crie `GR_RH`.
12. Crie 3 usuários em Contabilidade.
13. Crie 3 usuários em RH.
14. Configure as senhas conforme o roteiro.
15. Desmarque a primeira opção de senha conforme indicado.
16. Associe os usuários aos grupos correspondentes.

### Parte 3 --- Windows 7

17. Inicie a máquina Windows 7.
18. Configure o adaptador como **Rede Interna**.
19. Entre com o usuário `administrador`.
20. Configure a rede.
21. Teste:

``` cmd
ping 192.100.15.1
```

### Parte 4 --- Pastas

22. Crie:

``` text
C:\Fatec
```

23. Crie:

``` text
C:\Fatec\Contabilidade
C:\Fatec\RH
```

24. Configure as permissões.
25. Use `GR_Contabilidade` para o setor de Contabilidade.
26. Use `GR_RH` para o setor de RH.
27. Revise a herança das permissões quando necessário.

### Parte 5 --- Conferência

28. Verifique o domínio.
29. Verifique os usuários.
30. Verifique os grupos.
31. Verifique as pastas.
32. Verifique as permissões.
33. Faça os testes de comunicação.

------------------------------------------------------------------------

# 22. Credenciais apresentadas no material

As credenciais abaixo foram transcritas do roteiro da aula:

  Uso                                         Credencial
  ------------------------------------------- -----------------
  Senha indicada para os usuários             `f@tec1234`
  Usuário indicado no Windows 7               `administrador`
  Senha indicada para o acesso do Windows 7   `f@tec123`

> **Segurança:** não reutilize essas credenciais em computadores
> pessoais, servidores reais ou contas importantes.

------------------------------------------------------------------------

## Observação sobre o material original

O arquivo `aula 03 2.docx` contém apenas algumas instruções em texto,
enquanto boa parte da explicação está nas capturas de tela. Por isso,
este Markdown foi organizado para funcionar como **roteiro de
execução**, mantendo os nomes, endereços, domínio, usuários/grupos,
pastas e credenciais que aparecem no material.

Quando uma tela do Windows apresenta opções ou avisos que dependem da
configuração do laboratório, o procedimento deve seguir o que foi
demonstrado pelo professor nos prints, em vez de assumir uma
configuração diferente.
