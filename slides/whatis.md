<div>

  <h2>O que é Git?</h2>
  <p align="justify">É um sistema de controle de versionamento voltado para o desenvolvimento de software, com o intuito de controlar as mudanças em códigos ou em qualquer arquivo. É rápido, mantém a integridade dos arquivos, suporta desenvolvimento distribuído e não linear.</p>


  <h2>O que significa Git?</h2>
  <p align="justify"><blockquote cite="https://github.com/git/git/blob/e83c5163316f89bfbde7d9ab23ca2e25604af290/README">
  Git pode significar qualquer coisa, dependendo do seu humor:
  <ul>
    <li>3 letras aleatórias que não tinham sido usadas por comandos UNIX</li>
    <li>Estúpido/Desprezível (expressão)</li>
    <li>Rastreador de Informações Globais (Você está de bom humor)</li>
  </ul>
  Um estúpido (mas extremamente rápido) gerenciador de conteúdo de diretórios. Não faz muito, mas faz eficientemente.
  </blockquote>- Linus Torvalds</p>


  <h2>Git x Git-hub|lab|bucket</h2>
  <p align="justify">Git é o Sistema de controle de versão, enquanto que o github, gitlab e gitbucket são serviços para armazenamento de projetos Git. Os hubs oferecem ferramentas de administração de projetos e integração e desenvolvimento contínuo (CI/CD).</p>


  <h3 align="left">Github</h3>
  <img src="img/whatis/github.png" style="background:none; border:none; box-shadow:none;" />


  <h2>Como o Git trabalha?</h2>
  <p align="justify">Outros SVCs como Subversion, Perforce e Bazaar, pensam nas informações como um grupo de arquivos e suas alterações ao longo do tempo (baseado em deltas). Já o Git pensa na informação como um conjunto de snapshots, cada alteração confirmada (commit) gera uma imagem de um determinado arquivo.</p>


  <h3 align="left">Deltas:</h3>
  <img src="img/whatis/delta.png" style="background:none; border:none; box-shadow:none;" height="50%" width="50%"/>
  <h3 align="left">Snapshots:</h3>
  <img src="img/whatis/snapshot.png" style="background:none; border:none; box-shadow:none;" height="50%" width="50%"/>


  <h2>Integridade</h2>
  <p align="justify">Tudo no Git passa por uma soma de verificação, dessa forma é impossível realizar uma alteração nos arquivos sem que o Git saiba.A soma de verificação utiliza o método de hash SHA-1 onde uma string de 40 caracteres hexadecimais é gerada baseado no conteúdo dos arquivos e diretórios. Um exemplo de hash SHA-1 é:</p>
  <pre><code data-trim>
    10836e364ff8682ab695fc1f9edef1fd8b9c76ed
	</code></pre>


  <h2>Os 3 estágios de um arquivo</h2>
  <img src="img/whatis/file-stages.png" style="background:none; border:none; box-shadow:none;" />

</div>