# Sistemas Operacionais II — Aula 02
## Gerenciamento de discos, conversão FAT32 → NTFS e criação de máquina virtual

> **Material didático baseado nas imagens e instruções apresentadas no PDF “AULAS 02 SISTEMAS OPERACIONAIS”.**
>
> A aula apresenta duas partes principais:
> 1. criação/formatação de uma nova partição no Windows Server;
> 2. conversão do sistema de arquivos **FAT32 para NTFS** utilizando o `CONVERT` no Prompt de Comando;
> 3. criação/configuração de uma máquina virtual para instalação do **Windows Server 2008 R2**.

---

# 1. Objetivo da aula

Nesta atividade vamos trabalhar com **gerenciamento de discos e sistemas de arquivos**.

Ao final, devemos compreender:

- como acessar o **Gerenciamento de Disco**;
- como criar um novo volume/partição;
- como escolher o tamanho da partição;
- como atribuir uma letra à unidade;
- como formatar uma partição;
- o que significa FAT32;
- o que significa NTFS;
- como consultar a ajuda do comando `convert`;
- como converter uma unidade de FAT32 para NTFS;
- como conferir se a conversão foi realizada;
- como criar uma máquina virtual para o Windows Server 2008 R2.

---

# 2. Parte 1 — Criar uma nova partição

A primeira parte da aula começa pelo **Gerenciamento do Computador**.

## 2.1 Abrir o Gerenciamento do Computador

O caminho mostrado no material é:

```text
Ferramentas administrativas
        ↓
Gerenciamento de discos
        ↓
Assistente para novas partições
```

### Passo a passo

1. Abra o **Painel de Controle**.
2. Acesse as **Ferramentas Administrativas**.
3. Abra o **Gerenciamento do Computador**.
4. No painel esquerdo, localize **Armazenamento**.
5. Clique em **Gerenciamento de Disco**.
6. Localize o espaço do disco que será utilizado para criar a nova partição.
7. Inicie o **Assistente para Novas Partições Simples**.

### O que é o Gerenciamento de Disco?

O Gerenciamento de Disco é uma ferramenta administrativa do Windows usada para trabalhar com dispositivos de armazenamento.

Por meio dele é possível realizar operações como:

- visualizar discos;
- visualizar partições;
- criar volumes;
- formatar volumes;
- alterar letras de unidades;
- visualizar sistemas de arquivos.

---

# 3. Assistente para Novas Partições Simples

Depois de iniciar o assistente, aparece a tela:

```text
Assistente para Novas Partições Simples
```

A própria tela informa que o assistente ajuda a criar um **volume simples em um disco**.

## O que é um volume simples?

Um volume simples é uma área de armazenamento criada em um único disco.

Neste exercício, o assistente será utilizado para transformar espaço disponível em uma unidade que poderá ser acessada pelo Windows.

### Passo

Na tela inicial:

```text
Assistente para Novas Partições Simples
```

clique em:

```text
Avançar
```

---

# 4. Definir o tamanho da partição

A próxima tela é:

```text
Especificar o volume da partição
```

Nela são apresentados três valores:

- espaço máximo disponível;
- espaço mínimo disponível;
- tamanho do volume simples.

Na imagem da atividade, o espaço máximo aparece como:

```text
3358 MB
```

e o tamanho do volume simples está definido como:

```text
3358 MB
```

## O que isso significa?

O valor escolhido determina quanto do espaço disponível será utilizado pela nova partição.

Como o tamanho do volume está igual ao espaço máximo:

```text
Espaço máximo = 3358 MB
Tamanho do volume = 3358 MB
```

praticamente todo o espaço disponível mostrado pelo assistente será utilizado.

### Passo a passo

1. Observe o valor de **Espaço em disco máximo em MB**.
2. Observe o **Espaço em disco mínimo em MB**.
3. No campo **Tamanho do volume simples em MB**, informe o tamanho desejado.
4. Na atividade, foi utilizado:

```text
3358 MB
```

5. Clique em **Avançar**.

> **Importante:** o tamanho deve ser escolhido de acordo com o espaço disponível no disco. Não é necessário utilizar todo o espaço em uma situação real, mas foi isso que aparece no exemplo da aula.

---

# 5. Atribuir uma letra à unidade

Depois de definir o tamanho, aparece a tela:

```text
Atribuir letra de unidade ou caminho
```

Essa etapa define como a nova partição será identificada no Windows.

Na imagem, foi selecionada a opção:

```text
Atribuir a seguinte letra de unidade:
X
```

Portanto, a unidade criada será identificada como:

```text
X:
```

## Por que uma letra é atribuída?

O Windows utiliza letras para identificar unidades de armazenamento.

Exemplos:

```text
C: → unidade principal
D: → outra unidade
E: → outra unidade
X: → unidade criada na atividade
```

No exemplo da aula:

```text
X:
```

será utilizada para acessar o volume criado.

### Passo a passo

1. Marque:

```text
Atribuir a seguinte letra de unidade
```

2. Selecione:

```text
X
```

3. Clique em **Avançar**.

---

# 6. Formatar a partição

A próxima tela do assistente é:

```text
Formatar partição
```

A tela pergunta se o volume deve ser formatado.

Na imagem da aula está selecionada a opção:

```text
Formatar este volume com as seguintes configurações
```

E aparecem as seguintes configurações:

```text
Sistema de arquivos: FAT32
Tamanho da unidade de alocação: Padrão
Rótulo do volume: Dados
Executar uma formatação rápida: marcado
```

---

# 7. Sistema de arquivos FAT32

Nesta etapa, o sistema de arquivos escolhido é:

```text
FAT32
```

## O que é um sistema de arquivos?

O sistema de arquivos define como o sistema operacional organiza e controla os arquivos armazenados em uma unidade.

Ele permite que o sistema saiba:

- onde os arquivos estão;
- quais espaços estão ocupados;
- quais espaços estão livres;
- como acessar os dados.

---

# 8. Rótulo do volume

Na imagem, o rótulo definido é:

```text
Dados
```

O rótulo é simplesmente o nome dado à unidade para facilitar sua identificação.

Assim, depois da criação, a unidade aparece como:

```text
DADOS (X:)
```

Isso significa:

- **DADOS** → nome/rótulo;
- **X:** → letra da unidade.

---

# 9. Formatação rápida

A opção:

```text
Executar uma formatação rápida
```

aparece marcada no exemplo.

A formatação prepara o volume para utilização pelo sistema de arquivos escolhido.

> **Atenção:** formatar uma unidade pode apagar dados existentes. Em laboratório, utilize somente o disco/partição indicado pelo professor.

---

# 10. Finalizar a criação da partição

Depois de conferir as configurações:

```text
Sistema de arquivos: FAT32
Rótulo: Dados
Letra: X:
```

clique em:

```text
Avançar
```

e finalize o assistente.

Ao concluir, a nova unidade poderá ser visualizada pelo Windows.

---

# 11. Resultado esperado

Depois da criação, a unidade deverá aparecer no computador com uma identificação semelhante a:

```text
DADOS (X:)
```

A partir desse momento, podemos utilizar essa unidade para armazenar arquivos.

Na atividade, ela será usada para demonstrar a conversão:

```text
FAT32
   ↓
NTFS
```

---

# 12. Parte 2 — Consultar o comando CONVERT

A aula apresenta o comando:

```cmd
convert /?
```

Esse comando é utilizado para consultar a ajuda do comando `convert`.

## O que significa `/ ?`

No Prompt de Comando do Windows, a opção:

```cmd
/?
```

normalmente solicita a exibição da ajuda do comando.

Assim:

```cmd
convert /?
```

significa:

> mostrar as informações de utilização do comando `convert`.

---

# 13. Para que serve o comando CONVERT?

O comando:

```cmd
convert
```

é utilizado para converter um volume de **FAT/FAT32 para NTFS**.

No exemplo da aula, a conversão será feita na unidade:

```text
X:
```

A estrutura básica utilizada é:

```cmd
convert X: /FS:NTFS
```

### Significado de cada parte

```text
convert
```

É o comando utilizado para realizar a conversão.

```text
X:
```

É a unidade que será convertida.

```text
/FS:NTFS
```

indica que o sistema de arquivos de destino será:

```text
NTFS
```

Portanto:

```cmd
convert X: /FS:NTFS
```

pode ser entendido como:

> converter a unidade X: para o sistema de arquivos NTFS.

---

# 14. Executar o Prompt de Comando como administrador

Para realizar a conversão, a aula orienta:

```text
cmd
→ executar como administrador
```

## Passo a passo

1. Clique no botão **Iniciar**.
2. No campo de pesquisa, digite:

```text
cmd
```

3. Localize o **Prompt de Comando**.
4. Clique com o botão direito.
5. Escolha:

```text
Executar como administrador
```

6. Se aparecer uma confirmação de segurança, confirme a execução.

### Por que executar como administrador?

A conversão altera a estrutura do sistema de arquivos da unidade.

Por isso, é necessário executar o comando com privilégios administrativos.

---

# 15. Executar a conversão FAT32 → NTFS

Com o Prompt de Comando aberto como administrador, digite:

```cmd
convert X: /FS:NTFS
```

e pressione:

```text
Enter
```

---

# 16. Rótulo do volume atual

O Windows pode solicitar:

```text
Digite o rótulo do volume atual para a unidade X:
```

No exemplo da aula, o rótulo é:

```text
Dados
```

Então deve ser digitado:

```text
Dados
```

e pressionado:

```text
Enter
```

## Por que o Windows solicita o rótulo?

Essa informação ajuda a confirmar que a unidade correta está sendo convertida.

No nosso exemplo:

```text
Unidade: X:
Rótulo: DADOS
```

Portanto, a conversão será realizada na unidade esperada.

---

# 17. Acompanhar a conversão

Depois de confirmar o rótulo, o Windows inicia o processo.

Na tela apresentada no material aparecem etapas como:

```text
O tipo do sistema de arquivos atual é FAT32.
```

Isso confirma que, antes da conversão, a unidade realmente estava utilizando:

```text
FAT32
```

Depois, o sistema verifica os arquivos e calcula o espaço necessário para realizar a conversão.

Também aparece uma etapa semelhante a:

```text
Convertendo o sistema de arquivos
```

e, ao final:

```text
Conversão concluída
```

---

# 18. O que acontece durante a conversão?

De forma simplificada:

```text
ANTES

DADOS (X:)
Sistema de arquivos: FAT32


             ↓
     comando CONVERT


DEPOIS

DADOS (X:)
Sistema de arquivos: NTFS
```

O objetivo é alterar o sistema de arquivos da unidade sem realizar uma formatação convencional do volume.

---

# 19. Conferir se a conversão funcionou

Depois que aparecer:

```text
Conversão concluída
```

é necessário verificar o resultado.

A própria aula orienta:

```text
Computador
→ DADOS (X:)
→ botão direito
→ Propriedades
```

---

# 20. Verificar o sistema de arquivos

Na janela **Propriedades de DADOS (X:)**, procure:

```text
Sistema de arquivos:
```

Antes da conversão:

```text
FAT32
```

Depois da conversão:

```text
NTFS
```

Na imagem final da atividade, a propriedade mostra:

```text
Sistema de arquivos: NTFS
```

Portanto, a conversão foi concluída com sucesso.

---

# 21. Resumo da conversão

A sequência completa é:

```text
Criar partição
      ↓
Atribuir X:
      ↓
Formatar como FAT32
      ↓
Nomear como DADOS
      ↓
Abrir CMD como administrador
      ↓
convert /?
      ↓
consultar a ajuda
      ↓
convert X: /FS:NTFS
      ↓
informar o rótulo "Dados"
      ↓
aguardar a conversão
      ↓
"Conversão concluída"
      ↓
Computador
      ↓
DADOS (X:)
      ↓
Propriedades
      ↓
Confirmar NTFS
```

---

# 22. FAT32 x NTFS

A atividade trabalha diretamente com a conversão:

```text
FAT32 → NTFS
```

## FAT32

Foi o sistema de arquivos utilizado inicialmente na atividade.

A unidade foi criada como:

```text
DADOS (X:)
FAT32
```

## NTFS

É o sistema de arquivos utilizado depois da conversão.

O resultado esperado é:

```text
DADOS (X:)
NTFS
```

---

# 23. Observação importante da aula

O material destaca:

```text
(converte de fat para ntfs mas não de ntfs para fat)
```

Ou seja, para o procedimento apresentado:

```text
FAT/FAT32 → NTFS
```

é possível utilizar o comando `convert`.

Já o caminho inverso:

```text
NTFS → FAT32
```

não é realizado por esse comando.

---

# 24. Parte 3 — Criar a máquina virtual do Windows Server 2008 R2

Depois da parte de gerenciamento de discos, o material apresenta a criação de uma máquina virtual para:

```text
INSTALAÇÃO WINDOWS SERVER 2008 R2
```

A configuração mostrada é:

```text
2048 MB
1 CPU
15,00 GB de armazenamento
```

---

# 25. Configuração da máquina virtual

A máquina virtual apresentada no material utiliza:

| Recurso | Configuração |
|---|---:|
| Sistema | Windows Server 2008 R2 |
| Memória RAM | 2048 MB |
| CPU | 1 |
| Armazenamento | 15,00 GB |

---

# 26. O que é uma máquina virtual?

Uma máquina virtual é um computador criado por software.

No contexto da aula, podemos imaginar:

```text
COMPUTADOR FÍSICO
       |
       v
VirtualBox
       |
       v
Máquina Virtual
       |
       v
Windows Server 2008 R2
```

O sistema operacional é instalado dentro da máquina virtual como se fosse um computador separado.

---

# 27. Criar a VM no VirtualBox — passo a passo

## Passo 1 — Abrir o VirtualBox

Abra o **Oracle VM VirtualBox**.

Na tela principal, procure a opção:

```text
Novo
```

Ela inicia o assistente para criação de uma máquina virtual.

---

## Passo 2 — Informar o nome e o sistema

Na criação da VM, informe um nome relacionado ao sistema:

```text
Windows Server 2008 R2
```

Selecione o sistema operacional correspondente.

O objetivo é que o VirtualBox reconheça que a máquina virtual será utilizada para executar um sistema Windows Server.

---

## Passo 3 — Configurar a memória

Defina:

```text
2048 MB
```

Isso corresponde a:

```text
2 GB de RAM
```

A RAM será reservada para a máquina virtual enquanto ela estiver ligada.

---

## Passo 4 — Configurar o processador

Defina:

```text
1 CPU
```

Assim, a máquina virtual terá um processador virtual disponível.

---

## Passo 5 — Criar o disco virtual

Defina o armazenamento em:

```text
15,00 GB
```

Esse será o disco virtual utilizado para a instalação do Windows Server 2008 R2.

---

## Passo 6 — Conferir o resumo

Antes de finalizar, confira:

```text
RAM: 2048 MB
CPU: 1
Armazenamento: 15,00 GB
```

Se estiver de acordo com a atividade, finalize a criação.

---

# 28. Por que a aula utiliza uma máquina virtual?

A virtualização é útil em aulas de Sistemas Operacionais porque permite testar sistemas sem necessariamente alterar o sistema operacional principal do computador.

Por exemplo:

```text
Computador físico
       |
       +---- Sistema principal
       |
       +---- VirtualBox
                |
                +---- Windows Server 2008 R2
```

Isso cria um ambiente de laboratório isolado para praticar configurações.

---

# 29. Relação entre as duas partes da aula

As duas atividades trabalham conceitos diferentes, mas relacionados.

### Gerenciamento de discos

```text
Disco
 ↓
Partição
 ↓
FAT32
 ↓
CONVERT
 ↓
NTFS
```

### Virtualização

```text
Computador físico
 ↓
VirtualBox
 ↓
Máquina virtual
 ↓
Windows Server 2008 R2
```

Ambas são atividades de administração de sistemas operacionais.

---

# 30. Glossário

## Disco

Dispositivo utilizado para armazenar dados.

## Partição

Divisão lógica de um disco.

## Volume

Área de armazenamento que pode ser utilizada pelo sistema operacional.

## FAT32

Sistema de arquivos utilizado inicialmente na atividade.

## NTFS

Sistema de arquivos utilizado como destino da conversão.

## Formatação

Processo de preparar um volume para utilização com determinado sistema de arquivos.

## Rótulo do volume

Nome utilizado para identificar uma unidade.

Exemplo:

```text
DADOS
```

## Letra da unidade

Identificação utilizada pelo Windows.

Exemplo:

```text
X:
```

## CMD

Prompt de Comando do Windows.

## Administrador

Usuário/processo com privilégios elevados para executar determinadas operações administrativas.

## CONVERT

Comando utilizado na atividade para converter a unidade para NTFS.

## Máquina virtual

Computador criado por software dentro de outro computador.

## CPU

Unidade responsável pelo processamento das instruções.

## RAM

Memória utilizada temporariamente pelos programas e pelo sistema operacional.

---

# 31. Checklist para realizar a atividade

- [ ] Abrir o Gerenciamento do Computador.
- [ ] Acessar o Gerenciamento de Disco.
- [ ] Iniciar o Assistente para Novas Partições Simples.
- [ ] Clicar em **Avançar**.
- [ ] Definir o tamanho do volume.
- [ ] Utilizar **3358 MB**, conforme o exemplo da aula.
- [ ] Atribuir a letra **X:**.
- [ ] Escolher o sistema de arquivos **FAT32**.
- [ ] Definir o rótulo **Dados**.
- [ ] Utilizar a formatação rápida conforme o exemplo.
- [ ] Finalizar a criação da partição.
- [ ] Abrir o CMD como administrador.
- [ ] Executar `convert /?`.
- [ ] Consultar a sintaxe do comando.
- [ ] Executar `convert X: /FS:NTFS`.
- [ ] Informar o rótulo atual **Dados**, quando solicitado.
- [ ] Aguardar a conversão.
- [ ] Confirmar a mensagem **Conversão concluída**.
- [ ] Abrir **Computador**.
- [ ] Clicar com o botão direito em **DADOS (X:)**.
- [ ] Abrir **Propriedades**.
- [ ] Conferir se o sistema de arquivos está como **NTFS**.
- [ ] Criar a VM do Windows Server 2008 R2.
- [ ] Configurar **2048 MB de RAM**.
- [ ] Configurar **1 CPU**.
- [ ] Configurar **15,00 GB de armazenamento**.
- [ ] Finalizar a criação da máquina virtual.

---

# 32. Conclusão

Nesta aula foram trabalhados conceitos fundamentais de administração de sistemas operacionais.

Primeiro, foi criado um novo volume utilizando o **Gerenciamento de Disco** do Windows. O volume recebeu a letra **X:**, o rótulo **Dados** e foi formatado inicialmente como **FAT32**.

Depois, foi utilizado o **Prompt de Comando**, executado como administrador, para consultar a ajuda do comando `convert` e realizar a conversão da unidade:

```cmd
convert X: /FS:NTFS
```

Após a execução, a unidade foi verificada por meio das propriedades de **DADOS (X:)**, confirmando a alteração para:

```text
NTFS
```

Por fim, o material apresenta a criação de uma máquina virtual destinada à instalação do **Windows Server 2008 R2**, utilizando:

```text
2048 MB de RAM
1 CPU
15,00 GB de armazenamento
```

A atividade, portanto, permite praticar três conceitos importantes:

```text
GERENCIAMENTO DE DISCO
        +
SISTEMAS DE ARQUIVOS
        +
VIRTUALIZAÇÃO
```

Esses conhecimentos são importantes para a administração e manutenção de sistemas operacionais e ambientes de servidores.

---

## Referência da atividade

**Fonte:** PDF fornecido para a aula — **“AULAS 02 SISTEMAS OPERACIONAIS”**.

**Observação:** este material mantém os nomes, valores e procedimentos identificados nas imagens do PDF. Onde o PDF não apresenta uma informação detalhada, ela não foi inventada ou atribuída à atividade.
