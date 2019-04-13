<div>

  <h2>Trabalhando com Repositório Remoto</h2>
  <img src="img/remote/git-stages.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Criando um repositório no Github</h3>
  <p align="justify">Criar um repositório no seu github com o nome que desejar. Esse repositório vai ser utilizado no aprendizado de repositórios remotos.</p>


  <h3>Adicionando Remotos para o repositório local</h3>
  <p align="justify">Para sincronizar o repositório local com um remoto, utilizaremos o comando <i>git remote</i>, que permite gerenciar os remotos. Ao executar o comando <i>git clone</i> um remoto denominado <i>origin</i> é adicionado por padrão para o servidor de onde foi feito o clone.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ mkdir remote && cd remote
  $ git init
  $ git remote add origin &lt;link-repositório&gt;
  $ git remote -v
  origin	git@&lt;link-repositório&gt;.git (fetch)
  origin	git@&lt;link-repositório&gt;.git (push)
  </code></pre>


  <h3>Baixando Atualizações do Repositório Remoto</h3>
  <p align="justify">Para baixar as atualizações do repositório (commits feitos por outros contribuidores geralmente), basta executar o comando <i>git fetch &lt;repositório-remoto&gt; &lt;branch&gt;</i>. Lembrando que isso não altera o repositório local pois as alterações não são feitas ainda.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git fetch origin master
  From github.com:cleversonahum/git-para-iniciantes
  * branch  master -> FETCH_HEAD
  </code></pre>


  <h3>Mesclando alterações do remoto no repositório local</h3>
  <p align="justify">As alterações são baixadas do remoto para o repositório local, mas elas não são integradas automaticamente nele, ficando no repositório <i>origin/&lt;nome-repo&gt;</i>. Para que as alterações do remoto sejam mescladas as alterações do repositório local usamos o comando <i>git merge &lt; branch-remoto-ou-local&gt; &lt;branch-local&gt;</i></p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git merge origin/master
  $ git log
  </code></pre>


  <h3>Git pull = Git Fetch + Git Merge</h3>
  <p align="justify">O comando <i>git merge</i> é rotineiramente executado após o comando git <i>fetch</i>, por isso o comando <i>git pull &lt;repositório-remoto&gt; &lt;branch-local&gt;</i> é a junção dos dois comandos. Podem acontecer conflitos de merge que são solucionados como já explicado anteriormente.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  # Adicionar algum arquivo para o repositório no github pelo browser
  $ git pull origin master
  From github.com:&lt;user&gt;/&lt;repositório&gt;
  ...
  Updating fa35118..82ac5a4
  Fast-forward
  teste2 | 1 +
  1 file changed, 1 insertion(+)
  create mode 100644 teste2
  </code></pre>


  <h3>Conflito no Merge</h3>
  <p align="justify">Isso costuma acontecer quando o repositório remoto no qual estão sendo baixadas alterações possuem divergências em relação ao repositório local. Por exemplo, uma variável no repositório local possui o valor 5 e no remoto o valor 10. Dessa forma o Git possibilita que o usuário "resolva o conflito" escolhendo as alterações de qual repositório se deseja incorporar ao ramo principal do projeto.</p>


  <h3>Criando o conflito</h3>
  <pre style="white-space: pre-wrap;"><code data-trim>
  # Adicionar outro arquivo para o repositório no github pelo browser
  # Criar um arquivo de mesmo nome localmente na sua pasta
  $ echo "teste_local" > &lt;nome do arquivo&gt;
  $ git add .
  $ git commit -m "Conflito futuro"
  $ git pull origin master
  ...
  CONFLICT (add/add): Merge conflict in teste3
  Auto-merging teste3
  Automatic merge failed; fix conflicts and then commit the result.
  </code></pre>


  <h3>Resolvendo o conflito</h3>
  <p align="justify">É necessário abrir o arquivo no qual ocorreu o conflito com algum editor de texto e após isso escolher a alteração de qual commit deve ser mantida</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  <<<<<<< HEAD
  teste_local
  =======
  teste_remoto
  >>>>>>> 4db579b61f0753ce2c30e920ffd99ac2fee0e38a
  $ git status
  $ git add .
  $ git commit -m "resolvendo conflito"
  </code></pre>


  <h3>Enviando as alterações locais para o remoto</h3>
  <p align="justify">Ao realizar as alterações localmente, pode-se enviar as alterações para o repositório remoto para que todos possam ter acesso através da execução do comando <i>git push &lt;repositório-remoto&gt; &lt;branch-local&gt;</i></p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git push origin master
  Enumerating objects: 24, done.
  Counting objects: 100% (24/24), done.
  Delta compression using up to 4 threads
  Compressing objects: 100% (20/20), done.
  Writing objects: 100% (20/20), 2.81 KiB | 411.00 KiB/s, done.
  Total 20 (delta 14), reused 0 (delta 0)
  remote: Resolving deltas: 100% (14/14), completed with 4 local objects.
  To github.com:&lt;user&gt;/&lt;repositório&gt.git
  0964823..6266a1d  master -> master
  </code></pre>


  <h2>Git Branches: Uma alternativa para separar o trabalho</h2>
  <p align="justify">Para dividir a implementação de diferentes funções sem afetar o código que já está funcionando usa-se a função de Branch oferecida pelo Git. Com ela começamos a enxergar o código como uma árvore, na qual os galhos(Branches) vão surgindo das trilhas principais.</p>


  <h3>Revisando estrutura de commits</h3>
  <img src="img/remote/commit-and-tree.png" style="background:none; border:none; box-shadow:none;" />
  <aside class='notes' data-markdown>
    A imagem apresenta três componentes, o commit em si armazenando as informações da árvore e arquivos e gerando um hash único, depois temos a árvore em si onde fica a listagem dos arquivos que pertencem aquele commit e posteriormente temos 
  </aside>


  <h3>Ligação entre commits</h3>
  <img src="img/remote/commits-and-parents.png" style="background:none; border:none; box-shadow:none;" />
  <aside class='notes' data-markdown>
    A imagem apresenta a forma como os commits estão ligados entre si e os seus respectivos snapshots
  </aside>


  <h3>Disposição geral</h3>
  <img src="img/remote/branch-and-history.png" style="background:none; border:none; box-shadow:none;" />
  <aside class='notes' data-markdown>
    Enxergando além das estruturas apresentadas, é possível perceber que o git sempre cria uma branch principal chamada master e com uma tag 1.0, e o HEAD fica apontando pro seu trabalho atual.
  </aside>


  <h3>Criando uma branch</h3>
  <img src="img/remote/head-to-master.png" style="background:none; border:none; box-shadow:none;" />
  <aside class='notes' data-markdown>
    Criando uma branch para iniciar um trabalho paralelo, ao criar uma branch ela compartilha a referência da branch na qual foi criada. Dessa forma, a branch "testing" começa tendo como base a master (f30ab)
  </aside>


  <h3>Gerenciando Branches</h3>
  <p align="justify">Para gerenciar branches (criar, deletar, listar...) utilizamos o comando <i>git branch</i></p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git branch teste #Adicionando branch com o nome teste
  $ git branch -v #Listando as branchs existentes
  * master 533b0fc teste
  teste  533b0fc teste
  $ git branch -d teste
  $ git branch -v
  * master 533b0fc teste
  </code></pre>


  <h3>Trocando de branch ou de commit</h3>
  <p align="justify">O comando anterior serve para gerenciar branches, mas para mudar a branch sendo usada atualmente precisamos utilizar o comando <i>git checkout nome-branch</i> para trocar para uma branch específica ou para um commit específico usando <i>git checkout hash-commit</i></p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git branch teste #Adicionando branch com o nome teste
  $ git checkout teste
  Switched to branch 'teste'
  $ git branch -v
  master 533b0fc teste
  * teste  533b0fc teste
  </code></pre>


  <img src="img/remote/head-to-testing.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Realizando commits na branch criada</h3>
  <p align="justify">Ao realizar um commit na branch criada, a branch master não compartilhará mais as alterações feitas.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ touch teste2
  $ git add .
  $ git commit -m "teste2"
  $ git log
  $ git checkout master
  $ git log
  </code></pre>


  <img src="img/remote/advance-testing.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Realizando commits na branch master</h3>
  <p align="justify">Ao realizar um commit na branch master, tendo criado uma branch teste antes e comitado alterações, estamos criando histórias paralelas.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ touch teste3
  $ git commit -a -m "teste3"
  $ git log
  $ git checkout teste
  $ git log
  </code></pre>


<img src="img/remote/advance-master.png" style="background:none; border:none; box-shadow:none;" />


<h3>Merge de uma branch</h3>
<p align="justify">Ao desenvolvermos a correção de um bug ou desenvolvimento de uma nova funcionalidade sobre o projeto principal, cria-se uma branch para trabalhar e após isso (com a solução implementada) é necessário implementar as alterações na trilha principal do projeto (Master).</p>


<img src="img/remote/basic-branching-4.png" style="background:none; border:none; box-shadow:none;" />


<img src="img/remote/basic-branching-5.png" style="background:none; border:none; box-shadow:none;" />


<img src="img/remote/basic-merging-1.png" style="background:none; border:none; box-shadow:none;" />


<img src="img/remote/basic-merging-2.png" style="background:none; border:none; box-shadow:none;" />


<h3>Merge de uma branch na prática</h3>
<pre style="white-space: pre-wrap;"><code data-trim>
  $ touch main
  $ git add .
  $ git commit -m "trilha principal"
  $ git checkout -b fix1 #Cria uma branch chamada "fix1" e muda para ela
  Switched to a new branch 'fix1'
  $ touch fix
  $ git add .
  $ git commit -m "corrigindo bug"
  $ ls
  fix  main
  $ git checkout master
  Switched to branch 'master'
  $ ls
  main
  $ git merge fix1
  Updating a2f1e5b..d9b5a11
  Fast-forward
  fix | 0
  1 file changed, 0 insertions(+), 0 deletions(-)
  create mode 100644 fix
  $ ls
  main fix
  </code></pre>


<h3>Git Rebase: Alternativa ao merge para integrar mudanças</h3>
<p align="justify">Reaplica alterações/commits realizados anteriormente em um determinado branch na branch selecionada. Dessa forma as alterações são feitas de uma forma linear, em contraponto ao <i>git merge</i></p>


<img src="img/remote/basic-rebase-1.png" style="background:none; border:none; box-shadow:none;" />


<h3>Git Merge</h3>
<img src="img/remote/basic-rebase-2.png" style="background:none; border:none; box-shadow:none;" />


<h3>Git Rebase</h3>
<img src="img/remote/basic-rebase-3.png" style="background:none; border:none; box-shadow:none;" />


<h3>Git Merge depois do rebase</h3>
<img src="img/remote/basic-rebase-4.png" style="background:none; border:none; box-shadow:none;" />


<h3>Usando o comando Git Rebase</h3>
<pre style="white-space: pre-wrap;"><code data-trim>
  $ touch teste6
  $ git add .
  $ git commit -m "commit para o master"
  $ git checkout -b fix
  $ touch teste7
  $ git add .
  $ git commit -m "alteração para a branch"
  $ git checkout master
  $ touch teste8
  $ git add .
  $ git commit -m "alteração 2 para a master branch"
  </code></pre>


  <img src="img/remote/basic-rebase-1.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Continuando...</h3>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git checkout fix
  $ git rebase master
  First, rewinding head to replay your work on top of it...
  Applying: Alteração para a branch
  </code></pre>


  <img src="img/remote/basic-rebase-3.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Por fim o Merge na Master</h3>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git checkout master
  $ git merge fix
  </code></pre>


  <img src="img/remote/basic-rebase-4.png" style="background:none; border:none; box-shadow:none;" />  


  <h3>Git Merge x Git Rebase</h3>
  <aside class='notes' data-markdown>
    Git merge armazena as alterações que foram realizadas de fato, quer elas mantenham uma organização ou não. Isso faz parte da história do projeto.

    Git rebase pode deixar a hiustória do projeto mais bem organizada

    NUNCA USE O GIT REBASE PARA ALTERAÇÔES QUE JÁ FORAM ENVIADAS PARA O REMOTE (GIT PUSH)
  </aside>

</div>