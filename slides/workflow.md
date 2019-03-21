<div>

  <h2>Visão geral</h2>
  <img src="img/workflow/workflow.png" style="background:none; border:none; box-shadow:none;" />


  <h3>Instalando o Git</h3>
  <p align="justify">Possui opção de instalação para Windows, Linux e MAC. Na maioria das distribuições Linux está disponível nos gerenciadores de pacote, bastando executar um comando como: </p>
  <pre><code data-trim>
  (ArchLinux) pacman -S git
  (Ubuntu) apt install git
  (Fedora) yum install git
  </pre></code>


  <h3>Inicializando um repositório Git</h3>
  <p align="justify">É necessário primeiramente criar uma pasta e após isso executar o comando <i>git init</i>, criando os arquivos necessários.</p>
  <pre><code data-trim>
  $ mkdir teste
  $ cd teste
  $ git init
  Initialized empty Git repository in /tmp/teste/.git/
  $ ls -a
  . .. .git
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


  
</div>