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
  * branch            master     -> FETCH_HEAD
  Already up to date.
  </code></pre>

</div>