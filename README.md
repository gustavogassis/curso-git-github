# Curso Git e GitHub Iniciante

## 2 - Controle de Versão
  * Sistema com a finalidade de gerenciar diferentes versões de um documento.
  * Outros sistemas trabalham com as diferenças dos arquivos, enquanto Git trabalha com os estados.

## 3 - História do Git
  * Linus Torvald -> Tbm criador do Git.
  * Melhorias do Git ao BitKeeper.
    * Velocidade.
    * Design Simples.
    * Suporte Robusto ao desenvolvimento nn linear(milhares de branches paralelos).
    * totalmente distibuído.
    * Capaz de lidar eficientemente com grandes projetos como o kernel do linux.

## 4 - Git != GitHub
  * GitHub = Serviço de Web compartilhado para projetos que utilizam Git para versionamento.
  * Git    = Sistema de controle de versões.

## 6 - Configurando o Git
  * Configurar o Username:
    * `git config --global user.name "Gustavo Assis"`
    * Para saber qual username está configurado só dar o comando `git config --global user.name`

  * Configurar o Email:
    * `git config --global user.email "gassis25@gmail.com"`

  * Configurar o editor principal do Git(caso queria deixar aguma msg) (Caso nn configurado, o padrão é o vim):
    * `git config --global core.editor vim` (exemplo vim)

  * `git config --list` : Lista de várias informações do seu git

## 7 - Inicializando um repositório
  * Para inicializar um repositório utilizar o comando `git init` na pasta do seu projeto. Ele vai ficar observando todas as mudanças ocorridas no projeto. Ele tbm cria um diretório `.git` que contém as informações sobre o repositório, branches etc.

## 9 - Ciclo de vida dos status de seus arquivos
  * Separa em 4 status como os arquivos vão ser.
    * **Untracked**
      * É o momento que o arquivo acabou de ser add no repositório mas ainda nn foi visto pelo git.
    * **Unmodified**
      * É o momento que o arquivo foi visto pelo git mas ainda nn foi modificado.
    * **Modified**
      * Quando vc edita um arquivo que já existe no git.
    * **Staged**
      * Quando um arquivo já está finalizado tem q alterna-lo para *staged*, para quando a versão for finalizada, levar esse arquivo.
  * Comandos:
    * `git status` : Reporta como está o repositório neste momento.
    * `git add nome-arquivo` : add um arquivo ao git.
    * `git commit -m "mensagem"` : *`-m` para add uma mensagem*. Comando para criar um Commit.

  * Commit : É qnd vc cria uma versão/espelho do repositório e deixa salvo.

## 10 - Visualizando logs
  * `git log` : Mostra todos os commits/versões.
  * `git log --decorate` : Mostra informações adicionais. Ex: se foi de qual branch para qual branch, se houve um merge.
  * `git log --author="elemento-filtrador"` : Filtra pelo nome do autor.
  * `git shortlog` : Mostra em ordem allfabética os autores, quantos commits eles fizeram e quais foram.
  * `git shortlog -sn` : Mostra somente a qntd de commits que cada autor fez.
  * `git log --graph` : mostra de forma gráfica os branchs e commits.
  * `git show hash` : mostra só aqle commit.
  * **hash** : é um identificador de commit, cada um tem o seu.

## 11 - Diff
  * `git diff` : Após alterar um arquivo, mostra a diferença dele para a do último commit. Usado antes de dar o `git add` ou fazer o commit.
  * `git diff --name-only` : Mostra somente o nome do arquivo que foi modificado.

## 12 - Desfazendo as coisas.
  * `git checkout nome-arquivo` : desfaz as modificações do arquivo que ainda nn estão como **Staged**.
  * `git reset HEAD nome-arquivo` : retira o arquivo do status de **Staged**.
    * Atributos `git reset` :
      * `--soft nome-hash-q-vc-quer-voltar`: mata o commit, mas todas as modificações já estão em **Staged** para serem commitados novamente.
      * `--mixed nome-hash-q-vc-quer-voltar` : mata o commit e todas as modificações voltam para como **Modified**.
      * `--hard nome-hash-q-vc-quer-voltar` : apaga todo o commit e suas modificações.

/*
    SSH: Protocolo para autenticar um usuário remoto a um servidor
*/

## 15 - Ligando Repositório local a um remoto
  * Depois de criado um repositório no GitHub, para linkar os dois : `git remote add origin https://github.com/gustavogassis/GitHub-Course.git` . Onde **origin** é o nome padrão usado para ser a origem do remoto, mas pode ser outro qualquer.
  * `git remote -v` : Para ver infos do remoto.
  * Dps para enviar os arquivos pro repositório remoto utilizar: `git push -u origin master`.
    * Onde o `-u` serve só para que da prox vez nn precisemos digitar `origin master` dnv, só digitar `git push` que já vai saber para onde está indo.
    * O primeiro repositório `origin` é pra onde vai os arquivos e o segundo `master` é quem manda os arquivos.

## 17 - Clonando repositórios
  * Copiar link SSH do repositório no GitHub
  * Vai aonde vc quer criar o repositório e da : `git clone link-copiado nome-repositório-local`.

## 19 - Branch
  * Para cria: `git checkout -b nome-branch`.
  * `git branch` : mostra todos os **branches** e qual vc está localizado neste momento.
  * Para alternar entre **Branches**: `git checkout nome-branch-vc-quer-ir`.
  * Para apagar um **Branch**: `git branch -D nome-branch`.

## 22 - Merge e Rebase
  * Unem um **branch** externo com o **branch** principal, porém de formas diferentes.
  * Merge: `git merge name-branch-para-mesclar-cm-master`.
  * Rebase: `git rebase name-branch-para-mesclar-cm-master`.

## 25 - Git ignore
  * Ignora arquivos ou padrões de arquivos, assim o git nn ve eles e nn upa para o repositório.
  * Basta criar um arquivo `vim .gitignore` e dentro dele escrever o arquivo que quer ignorar.
  * Ex: `*.json` -> ignora todos os arquivos **json**.
  * Ex: `abc.txt` -> ignora este arquivo.

## 26 - Git Stash
  * Caso esteja fazendo algo e precise muder de branch para algo mais urgente. É possível add oq estava fazendo antes no stash para que nn precise subir um commit. Assim é possível voltar e terminar dps.
  * Para criar um stash: `git stash`.
  * Para pegar os arquivos do stash: `git apply`.
  * `git stash list`: para listar os stash's.
  * `git stash clear`: para limpar os stash's.

## 27 - Git Tag
  * Add Tag Ex: `git tag -a 1.0.0 -m "message-tag"`.
  * Subir a tag no remoto: `git push origin master --tags`

## 28 - Git Revert
  * `git revert hash-do-commit`
  * Ele cria um novo commit cm a versão anterior do hash que vc colocar. Ele meio q duplica o commit anterior para ser o mais atual. Ai vc consegue ver os problemas do commit q vc reverteu e alteralos.

## Apagando Tags e Branches remotos

  * Apagar no local: `git tag -d nome-tag` `git branch -d`.
  * Apagar no remoto a tag: `git push origin :nome-tag`.
  * Apagar no remoto o branch: `git push origin :nome-branch`.