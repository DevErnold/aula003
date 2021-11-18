# GIT

## Estados

* Modificado (modified);
* Preparado (staged/index)
* Consolidado (comitted);

## Ajuda

##### Geral
	git help
	
##### Comando específico
	git help add
	git help commit
	git help <qualquer_comando_git>
	

## Configuração

### Geral

As configurações do GIT são armazenadas no arquivo **.gitconfig** localizado dentro do diretório do usuário do Sistema Operacional (Ex.: Windows: C:\Users\Documents and Settings\Leonardo ou *nix /home/leonardo).

As configurações realizadas através dos comandos abaixo serão incluídas no arquivo citado acima.

##### Setar usuário
	git config --global user.name "Leonardo Comelli"

##### Setar email
	git config --global user.email leonardo@software-ltda.com.br

##### Listar configurações
	git config --list

### Ignorar Arquivos

Os nomes de arquivos/diretórios ou extensões de arquivos listados no arquivo **.gitignore** não serão adicionados em um repositório. Existem dois arquivos .gitignore, são eles:

* Geral: Normalmente armazenado no diretório do usuário do Sistema Operacional. O arquivo que possui a lista dos arquivos/diretórios a serem ignorados por **todos os repositórios** deverá ser declarado conforme citado acima. O arquivo não precisa ter o nome de **.gitignore**.

* Por repositório: Deve ser armazenado no diretório do repositório e deve conter a lista dos arquivos/diretórios que devem ser ignorados apenas para o repositório específico.

## Repositório Local

### Criar novo repositório

	git init

### Verificar estado dos arquivos/diretórios

	git status

### Adicionar arquivo/diretório (staged area)

##### Adicionar um arquivo em específico

	git add meu_arquivo.txt

##### Adicionar um diretório em específico

	git add meu_diretorio

##### Adicionar todos os arquivos/diretórios
	
	git add .	
	
##### Adicionar um arquivo que esta listado no .gitignore (geral ou do repositório)
	
	git add -f arquivo_no_gitignore.txt
	
### Comitar arquivo/diretório

##### Comitar um arquivo
	
	git commit meu_arquivo.txt

##### Comitar vários arquivos

	git commit meu_arquivo.txt meu_outro_arquivo.txt
	
##### Comitar informando mensagem

	git commit meuarquivo.txt -m "minha mensagem de commit"

### Remover arquivo/diretório

##### Remover arquivo

	git rm meu_arquivo.txt

##### Remover diretório

	git rm -r diretorio

##### Reiniciar repositório git

	git rm -rf .git

### Visualizar histórico

##### Exibir histórico
	
	git log
	
##### Exibir histório de um arquivo específico

	git log -- <caminho_do_arquivo>

##### Exibir histório de um determinado autor

	git log --author=usuario

## Repositório Remoto

### Exibir os repositórios remotos

	git remote
	
	git remote -v

### Vincular repositório local com um repositório remoto

	git remote add origin git@github.com:leocomelli/curso-git.git
	
### Exibir informações dos repositórios remotos

	git remote show origin
	
### Renomear um repositório remoto 

	git remote rename origin curso-git
	
### Desvincular um repositório remoto
	
	git remote rm curso-git

### Enviar arquivos/diretórios para o repositório remoto

O primeiro **push** de um repositório deve conter o nome do repositório remoto e o branch.

	git push -u origin master
	
Os demais **pushes** não precisam dessa informação

	git push
	

### Atualizar repositório local de acordo com o repositório remoto

##### Atualizar os arquivos no branch atual

	git pull
	
##### Buscar as alterações, mas não aplica-las no branch atual

	git fetch
	
### Clonar um repositório remoto já existente

	git clone git@github.com:leocomelli/curso-git.git
	
### Tags
	
### Branches

O **master** é o branch principal do GIT.

O **HEAD** é um ponteiro *especial* que indica qual é o branch atual. Por padrão, o **HEAD** aponta para o branch principal, o **master**.

##### Criando um novo branch

	git branch bug-123
	
##### Trocando para um branch existente

	git checkout bug-123
	
Neste caso, o ponteiro principal **HEAD** esta apontando para o branch chamado bug-123.

##### Criar um novo branch e trocar 

	git checkout -b bug-456
	
##### Voltar para o branch principal (master)

	git checkout master

##### Apagando um branch

	git branch -d bug-123

##### Listar branches 

###### Listar branches

	git branch

###### Listar branches com informações dos últimos commits

	git branch -v

##### Criando branches no repositório remoto

###### Criando um branch remoto com o mesmo nome

	git push origin bug-123

###### Criando um branch remoto com nome diferente

	git push origin bug-123:new-branch

##### Baixar um branch remoto para edição

	git checkout -b bug-123 origin/bug-123


##### Apagar branch remoto

	git push origin:bug-123

### Rebasing

Fazendo o **rebase** entre um o branch bug-123 e o master.

	git checkout experiment
	
	git rebase master
	

Mais informações e explicações sobre o [Rebasing](http://git-scm.com/book/en/Git-Branching-Rebasing)

### Reescrevendo o histórico

##### Alterando mensagens de commit

	git commit --amend -m "Minha nova mensagem"
