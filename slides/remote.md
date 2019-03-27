<div>

  <h2>Trabalhando com Repositório Remoto</h2>
  <img src="img/workflow/workflow.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Adicionando Remotos para o repositório local</h3>
  <p align="justify">Para sincronizar o repositório local com um remoto, utilizaremos o comando <i>git remote</i>, que permite gerenciar os remotos. Ao executar o comando <i>git clone</i> um remoto denominado <i>origin</i> é adicionado por padrão para o servidor de onde foi feito o clone.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git remote add origin https://github.com/cleversonahum/git-para-iniciantes.git
  $ git remote -v
  origin	git@github.com:cleversonahum/git-para-iniciantes.git (fetch)
  origin	git@github.com:cleversonahum/git-para-iniciantes.git (push)
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
  $ git merge origin/master master
  COLOCAR MAIS INFOS
  </code></pre>


  <h3>Conflito no Merge</h3>
  <p align="justify">Isso costuma acontecer quando o repositório remoto no qual estão sendo baixadas alterações possuem divergências em relação ao repositório local. Por exemplo, uma variável no repositório local possui o valor 5 e no remoto o valor 10. Dessa forma o Git possibilita que o usuário "resolva o conflito" escolhendo as alterações de qual repositório se deseja incorporar ao ramo principal do projeto. MAIS COISA AQUI</p>


  <h3>Git pull = Git Fetch + Git Merge</h3>
  <p align="justify">O comando <i>git merge</i> é rotineiramente executado após o comando git <i>fetch</i>, por isso o comando <i>git pull &lt;repositório-remoto&gt; &lt;branch-local&gt;</i> é a junção dos dois comandos. Podem acontecer conflitos de merge que são solucionados como já explicado anteriormente.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git pull origin master
  From github.com:cleversonahum/git-para-iniciantes
  * branch master -> FETCH_HEAD
  Already up to date.
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
  To github.com:cleversonahum/git-para-iniciantes.git
  0964823..6266a1d  master -> master
  </code></pre>


  <h2>Git Branches: Uma alternativa para separar o trabalho</h2>
  <p align="justify">Para dividir a implementação de diferentes funções sem afetar o código que já está funcionando usa-se a função de Branch oferecida pelo Git. Com ela começamos a enxergar o código como uma árvore, na qual os galhos(Branches) vão surgindo das trilhas principais.</p>


  <h3>Revisando estrutura de commits</h3>
  <img src="img/remote/commit-and-tree.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Ligação entre commits</h3>
  <img src="img/remote/commit-and-tree.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Disposição geral</h3>
  <img src="img/remote/branch-and-history.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Criando uma branch</h3>
  <img src="img/remote/head-to-master.png" style="background:none; border:none; box-shadow:none;" />


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
  $ git commit -a -m "teste2"
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


<h3>Git Rebase: </h3>

</div>