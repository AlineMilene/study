# Git

## Comandos básicos

`ls`: lista os arquivos da pasta
`ls -a`: lista os arquivos da pasta incluindo arquivos ocultos
`touch .gitignore`: cria o arquivo .gitignore [templates git ignore](https://github.com/github/gitignore)

###### Configuração
`git init`: inicializa um repositório git na pasta
`git config --global init.defaulBranch NOME`: muda o nome padrão da branch master
`git config –glboal core.editor "code --wait"`: altera o editor de texto padrão (VIM), para mais [clique aqui](https://docs.github.com/en/get-started/getting-started-with-git/associating-text-editors-with-git)

---

1. **Ciclo de vida do arquivo**
![Ciclo de vida do arquivo dentro do git](/Git/img/ciclo%20de%20vida%20do%20arquivo.png)
`git status`: verifica arquivos não rastreados e rastreados para checar mudanças
`git add arquivo.extensao`: adiciona o arquivo
`git add .` ou `git add -a` ou `git add –all`: para adicionar todos arquivos de uma vez
`git rm --cached arquivo.extensao`: remove o arquivo do commit
`git rm --cached -r`: para remover todos arquivos de uma vez
`git commit -m "MENSAGEM"`: salva as alterações no arquivo
`git commit -a -m "MENSAGEM"`: adiciona todos os arquivos e salva as alterações de uma vez
<br>

1. **Diferença entre arquivos**
`git diff`: mostra a diferença que existe entre os arquivos modified e unmodified.
`git diff --cached` ou `git diff --staged`: mostra a diferença que existe entre os arquivos staged e unmodified.
<br>

1. **Histórico de commits**
`git log`: mostra o histórico completo dos commits
`git log BRANCH`: mostra o histórico completo dos commits da branch escolhida
`git log --oneline`: mostra o histórico (hash e a mensagem) dos commits em linha única
`git log -N`: onde N é o número de commits que você deseja ver
`git log -p ou (--patch)`: é o histórico de commits com as diferenças em um comando
`git log --stat`: é o histórico de commits com os arquivos que foram modificados
`git log --shortstat`: é o histórico de commits e a qtd. de arquivos e linhas modificados
<br>

1. **Alterando um commit**
`git commit --amend -m "mensagem correta"`: alterando um commit
`git commit --amend --no-edit`: adicionando arquivos à um commit anterior
<br>

1. **Navegando entre as versões de commits**
`git log –online`: para encontrar o hash do commit que deseja acessar a versão
`git checkout "hash do commit"`: desta forma, o repositório local volta a versão desejada
<br>

1. **Descarte de alterações**
![Ciclo de vida do arquivo dentro do git](/Git/img/desfazendo%20mudan%C3%A7as.png) 
- Untracked: `git clean -f`
- Tracked/Modified: `git checkout arquivo.extensao`
- Tracked/Staged: `git restore --staged arquivo.extensao` ou `git rm --cached arquivo.extensao`. O restore funciona apenas se há houver commit no repositório.
- Tracked/Modified/Staged: `git reset --hard`
<br>

1. **Parar de rastrear um arquivo**
`git update-index --skip-worktree arquivo.extensao`: deixa de rastrear arquivo, o passado não é afetado
`git update-index --no-skip-worktree arquivo.extensao` : volta a rastrear o arquivo, o passado não é afetado
<br>

1. **Clonar repositório**
`git clone <url do clone> nomeClone`: clonando repositório remoto
<br>

1. **Repositórios Remotos**
`git remote -v`: mostra as origens configurados do repositório remoto, sendo *fetch* a origem que os arquivos são puxados e *push* a origem que são enviados para o github. 
`git remote add "origin" <url do repositório GIT>`: adiciona uma origem remota para um repositório local. O termo "origin" geralmente é o nome dado para a origem remota, podendo ser alterado conforme necessário.
`git remote set-url "origin" <url nova do repositório GIT>`: atualiza url do repositório remoto.
<br>

1.  **Salvando mudanças no servidor**
`git push`: envia todos commits locais que ainda não foram versionados.
<br>

1.  **Baixando a última versão do servidor**
`git pull`: puxa todos commits versionados que não estão no repositório local.
<br>

1.  **Sobre Branchs**
`git branch` ou `git branch --list`: lista as branchs existentes, com a branch atual em destaque
`git branch "nome"`: cria uma branch
`git branch -d "nome"`: deleta uma branch
`git branch -m "nome"`: modifica uma branch
`git checkout "nome"`: troca de branch
`git checkout -b "nome"`: cria e já troca de branch
`git switch "nome"`: troca de branch
`git switch -`: volta para a branch anterior
`git switch -c "nome"`: cria e já troca de branch
`git push --set-upstream origin "nome"` ou `git push -u origin "nome"`: cria a branch no servidor com o ponteiro local
`git push --delete origin "nome"`: deleta uma branch remota
<br>

1.  **Sobre Merges**
`git merge "nomeBranch"`: puxa alterações da branch escolhida
`git branch --merged`: verifica quais branchs foram mergeadas com a branch atual
`git branch --no-merged`: verifica quais branchs não foram mergeadas com a branch atual
`git merge --abort`: não resolve os conflitos 
<br>

1.  **Sobre Tags**
`git tag "nome"`: cria uma tag simples em cima do commit e branch atual
`git tag "nome" HASH`: cria uma tag simples em cima do commit escolhido pelo hash
`git tag -a -m "mensagem" "nome"`: cria uma tag com uma descrição desejada em cima do commit e branch atual 
`git tag -a -m "mensagem" "nome" HASH`: cria uma tag com uma descrição desejada em cima do commit escolhido pelo hash
`git show "nome"`: exibe as informações sobre a tag
`git tag` ou `git tag -l` ou `git tag --list`: exibe todas as tags do projeto
`git tag -n`: exibe todas as tags do projeto com a descrição
`git push origin "nome"`: sobe a tag para o repositório remoto
`git push --tags`: sobe todas as tag para o repositório remoto
`git tag -d "nome"`: deleta a tag do repositório local
`git push --delete origin "nome"`: deleta a tag do repositório remoto
<br>

1.  **Sobre Stash**
`git stash`: salva na memória modificações que ainda não estão prontas para commitar
`git stash list`: lista todos os stashs criados (todos os pontos de salvamento em memória)
`git stash apply`: recupera os arquivos salvos para continuar de onde parou. Se houver mais que um stash salvo, irá recuperar o da posição {0} que é o mais recente
`git stash apply stash@{1}`: recupera os arquivos salvos para continuar de onde parou do stash escolhido
`git stash pop`: recupera os arquivos salvos para continuar de onde parou do stash mais recente e já apaga da lista de stashs
`git stash pop stash@{1}`: recupera os arquivos salvos para continuar de onde parou do stash escolhido e já apaga da lista de stashs
`git stash drop`: deleta o stash{0} da lista de stashs
`git stash drop stash@{1}`: deleta o stash escolhido da lista de stashs
`git stash branch "nome"`: cria uma branch a partir do stash{0} 
`git stash branch "nome" stash@{1}`: cria uma branch a partir do stash escolhido
<br>

-----------
## Comandos intermediários

16. **Revertendo um commit (continua a existir o commit)**
`git revert HASH`: reverte o commit específico
`git revert HEAD` ou `git revert HEAD --no-edit`: reverte o último commit com opção de editar ou não as alterações
<br>

17. **Desfazendo um commit (deixa de existir o commit)**
`git reset --hard HEAD-1`: remove o commit totalmente, inclusive as mudanças. O head também é ajustado para 1 commit anterior, sendo possível escolher o número de commits que deseja remover
`git reset --mixed HEAD-1`: remove o commit e mantém as mudanças na área de trabalho
`git reset --soft HEAD-1`: remove o commit e mantém as mudanças na área de preparação
<br>

18.  **Forçando envio de mudanças**
`git push --force` ou `git push -f`: sobrescreve o repositório remoto com as mudanças locais, perdendo mudanças remotas (usado quando houve git reset de commits)
`git push --force-with-lease`: envia as informações para o repositório remoto apenas se não houver perca de histórico
<br>

19.  **Rebase**
`git rebase main`: traz o novo commit da main como base para a branch atual que você executou o comando
<br>

**README**
plataforma para edição amigável de um readme [dillinger](https://dillinger.io/)