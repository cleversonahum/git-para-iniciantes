<div>

  <h2>Visão geral</h2>
  <img src="img/workflow/workflow.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Instalando o Git</h3>
  <p align="justify">Possui opção de instalação para Windows, Linux e MAC. Na maioria das distribuições Linux está disponível nos gerenciadores de pacote, bastando executar um comando como: </p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  (ArchLinux) pacman -S git
  (Ubuntu) apt install git
  (Fedora) yum install git
  </code></pre>


  <h3>Criando uma conta no Github</h3>
  <p align="justify">Acessar o site <a href="https://www.github.com">www.github.com</a> e criar uma conta do serviço para ser usada ao longo do minicurso.</p>


  <h3>Se identificando</h3>
  <p align="justify">Cada alteração confirmada no repositório é associada com o usuário que está utilizando o Git.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git config --global user.name "Meu Nome"
  $ git config --global user.email "meunome@example.com"
	</code></pre>


  <h3>Clonando um repositório existente</h3>
  <p align="justify">É possível inicializar o repositório através de plataformas como o github e só cloná-lo ou mesmo clonar um repositório de outro contribuidor. Para realizar a clonagem do repositório utiliza-se o comando <i>git clone &lt;URL do Repositório&gt;</i></p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git clone https://github.com/cleversonahum/git-para-iniciantes.git
  Cloning into 'git-para-iniciantes'...
  remote: Enumerating objects: 231, done.
  remote: Counting objects: 100% (231/231), done.
  remote: Compressing objects: 100% (164/164), done.
  remote: Total 231 (delta 71), reused 211 (delta 55), pack-reused 0
  Receiving objects: 100% (231/231 2.13 MiB | 417.00 KiB/s, done.
  Resolving deltas: 100% (71/71), done.
	</code></pre>


  <h3>Inicializando um repositório Git</h3>
  <p align="justify">É necessário primeiramente criar uma pasta e após isso executar o comando <i>git init</i>, criando os arquivos necessários.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ mkdir teste
  $ cd teste
  $ git init
  Initialized empty Git repository in /tmp/teste/.git/
  $ ls -a
  . .. .git
	</code></pre>


  <h3>Monitorando Arquivos</h3>
  <p align="justify">Ao alterarmos/deletarmos/modificarmos um arquivo é preciso realizar um commit para que as alterações sejam realizadas no repositório Git. Usando o comando <i>git status</i> é possível observar em qual dos 3 estágios possíveis estão os arquivos.</p>
  <pre style="white-space: pre-wrap;font-size:16px;"><code data-trim>
  $ git status
  On branch master
  No commits yet
  nothing to commit (create/copy files and use "git add" to track)
  $ touch teste
  $ git status
  On branch master
  No commits yet
  Untracked files:(use "git add &lt;file&gt;..." to include in what will be committed)
	teste
  nothing added to commit but untracked files present (use "git add" to track)
  </code></pre>


  <h3>Relembrando os 3 estágios</h3>
  <img src="img/whatis/file-stages.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Adicionando arquivos para área de "ensaio"</h3>
  <p align="justify">Ao criar um arquivo que deseja adicionar ao repositório Git, é necessário usar o comando <i>git add &lt;Nome do arquivo ou . (todos arquivos)&gt;</i> para que os arquivos sejam adicionados a area de ensaio para o commit.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git add teste
  $ git status
  On branch master
  No commits yet
  Changes to be committed:
  (use "git rm --cached &lt;file&gt;..." to unstage)
	new file: teste
  </code></pre>


  <h3>Salvando alterações no repositório Git (Commit)</h3>
  <p align="justify">Para que as alterações adicionadas a área de ensaio sejam salvas no repositório Git de fato é necessário executar um <i>git commit</i></p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git commit -m "Informações sobre a alteração realizadas nesse commit"
  [master (root-commit) bf720d0] Informações sobre a alteração realizadas nesse commit
  1 file changed, 0 insertions(+), 0 deletions(-)
  create mode 100644 teste
  </code></pre>
  <aside class='notes' data-markdown>
    Trazer algumas características importantes de um commit: Ser atômico, simples, resolver um problema específico. Pensar que dentro da estrutura de um projeto algumas ações precisarão ser refeitas, por isso é importante que os commits sejam o mais independentes possíveis.
  </aside>


  <h3>Como deve ser um commit?</h3>
  <ul>
    <li>Mensagens claras e objetivas</li>
    <li>Quanto menor, melhor (geralmente)</li>
    <li>Ter o máximo de independência entre os commits</li>
  </ul>


  <h3>Visualizando commits realizados</h3>
  <p align="justify">É possível verificar o histórico de commits realizados dentro de um projeto Git, visualizando o hash do commit, o autor, data e a sua descrição. Para isso é usado o comando <i>git log</i></p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git log
  commit bf720d0041c7ba81aaa78f255f683820259d34ad (HEAD -> master)
  Author: Cleverson Nahum &lt;cleversonahum@gmail.com&gt;
  Date:   Fri Mar 22 22:09:59 2019 -0300
  Informações sobre a alteração realizadas nesse commit
  </code></pre>


  <h3>Removendo arquivo comitado</h3>
  <p align="justify">Quando um arquivo é adicionado em um ensaio de commit é possível remove-lo usando o comando <i>git rm &lt;Nome_do_arquivo&gt;</i>, dessa forma o arquivo será removido tanto da pasta quanto do repositório git, necessitando que a remoção seja comitada.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ touch teste2
  $ git add teste2
  $ git commit -m "adicionando teste2"
  $ git rm teste2
  $ git status
  On branch master
  Changes to be committed:
  (use "git reset HEAD &lt;file&gt;..." to unstage)
	deleted: teste2
  </code></pre>
  <aside class='notes' data-markdown>
    Pedir para os participantes adicionarem a alteração que deleta o arquivo e commitá-la
  </aside>


  <h3>Retirando arquivos adicionados ou revertendo commits</h3>
  <p align="justify">O comando <i>git reset</i> permite desfazer alterações adionadas para a zona de ensaio ou para reverter commits para estado anteriores.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ touch teste3
  $ git add teste3
  $ git reset teste3
  $ git status
  On branch master
  No commits yet
  Untracked files:
  (use "git add &lt;file&gt;..." to include in what will be committed)
	teste3
  nothing added to commit but untracked files present (use "git add" to track)
  </code></pre>
  <aside class='notes' data-markdown>
    Pedir para os participantes verificarem o git status depois do git add
  </aside>


  <h3>Relembrando os 3 estágios</h3>
  <img src="img/whatis/file-stages.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Revertendo um commit</h3>
  <p align="justify">Quando comitamos uma alteração indesejada sem querer ou com uma mensagem de commit errada pordemos reverter o commit usando também o <i>git reset --soft</i> para desfazer o commit voltando os arquivos para a zona de ensaio</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git add teste3
  $ git commit -m "teste3"
  $ git log
  $ git reset --soft HEAD^1
  & git log #Mostrando que o commit foi desfeito
  & git status #Arquivos do commit desfeito voltam para a zona de ensaio
  </code></pre>
  <aside class='notes' data-markdown>
    Explicar que poderia ser utilizado a notação HEAD^2 ou outro numero para reverter vários commits, ou mesmo colocar a Hash do commit
  </aside>


  <h3>Revertendo um commit/2</h3>
  <p align="justify">Ainda é possível desfazer um commit sem que as alterações voltem para a área de ensaio usando <i>git reset --hard</i> CUIDADO!</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git commit -m "teste a ser deletado"
  $ git log
  $ git reset --hard HEAD^1
  & git log #Mostrando que o commit foi deletado
  & git status #Arquivos do commit desfeito não voltaram para a zona de ensaio
  </code></pre>

</div>