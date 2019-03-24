<div>

  <h2>Trabalhando com Repositório Remoto</h2>
  <img src="img/workflow/workflow.png" style="background:none; border:none; box-shadow:none;" />

  <h3>Adicionando Remotos para o repositório local</h3>
  <p align="justify">Para sincronizar o repositório local com um remoto, utilizaremos o comando <i>git remote</i>, que permite gerenciar os remotos. Ao executar o comando <i>git clone</i> um remoto denominado <i>origin</i> é adicionado por padrão para o servidor de onde foi feito o clone.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git remote add origin https://github.com/cleversonahum/git-para-iniciantes.git
  From github.com:cleversonahum/git-para-iniciantes
  * branch            master     -> FETCH_HEAD
  $ git remote -v
  origin	git@github.com:cleversonahum/git-para-iniciantes.git (fetch)
  origin	git@github.com:cleversonahum/git-para-iniciantes.git (push)
  </pre></code>

  
  <h3>Baixando Atualizações do Repositório Remoto</h3>
  <p align="justify">Para baixar as atualizações do repositório (commits feitos por outros contribuidores geralmente), basta executar o comando <i>git fetch &lt;repositório-remoto&gt; &lt;branch&gt;</i>. Lembrando que isso não altera o repositório local pois as alterações não são feitas ainda.</p>
  <pre style="white-space: pre-wrap;"><code data-trim>
  $ git fetch origin master
  </pre></code>

  
</div>