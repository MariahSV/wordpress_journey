# WordPress Journey
PTBR - Meus estudos sobre construção de temas para Wordpress do zero e outros testes.
-
EN - My studies about constructing Wordpress themes from scratch and other tests.

## FONTES
- Documentação oficial Wordpress (https://developer.wordpress.org/themes/getting-started/)

## CONCEITOS
- Tema: controla, organiza a apresentação do conteúdo;
- Plugin: controla o comportamento dos recursos do tema;

## CONHECIMENTOS ESSENCIAIS
html, css, php

## CONHECIMENTOS SUGERIDOS
mysql, javascript, tecnologias de server

## ARQUIVOS OBRIGATÓRIOS
index.php – arquivo principal do template;
style.css – arquivo principal de estilo;

## ARQUIVOS ADICIONAIS, COMPLEMENTARES
Não são obrigatórios.

- arquivos de temas clássicos em PHP;
- arquivos de temas de blocos possuem códigos fragmentados e arquivos em HTML;
- arquivos com códigos de localização;
- arquivos extras de CSS;
- gráficos (?);
- arquivos em JavaScript;
- arquivos de texto como informações de licença, instruções no README e changelog;

## BOAS PRÁTICAS
- Confira as Guidelines durante a produção para garantir a aprovação do tema ao submeter para divulgação na comunidade.
- Um tema não pode possuir funcionalidades exclusivas. Caso um usuário mude de tema, essa funcionalidade se perde. Considere que usuários mudam de tema constantemente. Mantenha design separado de funcionalidades construindo-as como plugins.
- Sempre projete para rodar o template na versão atual e em no mínimo 2 versões anteriores do WordPress.
- No WordPress pode haver conflitos de nomenclaturas entre funções, classes e variáveis. Nomeie cada função, classe e variável com um prefixo exclusivo do tema (exemplo: o nome do próprio tema ou abreviações) para reduzir as chances disso ocorrer.

## AMBIENTE DE PRODUÇÃO
- Servidor local com PHP - MAMP, XAMPP, Varying Vagrant Vagrants (VVV) ou Docker;
- Editor de textos e/ou códigos - Atom, Sublime Text, VSCode ou PhpStorm;

## LINKS E COMPLEMENTOS
- COMANDOS PARA DEBUG: https://codex.wordpress.org/WP_DEBUG
- PLUGINS AUXILIARES PARA DESENVOLVIMENTO: https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/ 
- TEMA EXEMPLO: https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentytwentyone
- FUNÇÕES: https://developer.wordpress.org/themes/basics/theme-functions/
- MANUAL TEMAS COM EDITOR DE BLOCOS: https://developer.wordpress.org/block-editor/how-to-guides/themes/ 
- REFERÊNCIA DE CÓDIGO: https://developer.wordpress.org/reference/
- VERSÕES DE WORDPRESS: https://wordpress.org/download/releases/
- GUIDELINES: 
-- https://developer.wordpress.org/theme/release/theme-review-guidelines/
-- https://make.wordpress.org/themes/handbook/review/required/
-- https://make.wordpress.org/core/handbook/best-practices/coding-standards/

## ARQUIVO FUNCTIONS.PHP
https://developer.wordpress.org/themes/basics/theme-functions/

- É usado em temas clássicos, temas de bloco e temas filhos;
- Contém as funcionalidades do tema;
- Funciona como um plugin adicionando recursos e funcionalidades ao tema;
- Pode chamar funções próprias do WordPress e conter funções próprias;

### Obrigatórios para functions.php
- cabeçalho genérico;
- armazenado em subpasta em wp-content/themes;
- executável somente quando estiver na pasta de tema ativado;
- aplicável somente ao tema onde foi construído; 
- pode conter inúmeros blocos de códigos para diversos propósitos;
- um tema filho pode ter seu próprio arquivo functions.php; caregado logo antes do tema pai; ele não substitui as funções do tema pai mas pode vir a complementá-las ou sobreescrevê-las;
- carregado antes de funções de plugins;
- o namespace das funções deve conter o nome do tema;
- nomes de funções, classes e variáveis deve ser únicos (na verdade é uma boa prática para evitar conflitos com outros plugins e com o WordPress), uma sugestão é adicionar o nome do próprio tema ou uma sigla;

### Obrigatórios para plugins
- cabeçalho específico e único;
- armazenado em wp-content/plugins ou subpasta;
- ser aplicável em qualquer tema;
- executável somente ao carregar uma página e se estiver habilitado;
- deve servir a um propósito único, exemplo: oferecer recursos para auxílio de backup, otimizar sistemas de busca;

## Arquivos, códigos e anotações 
Em ordem de criação (ADICIONAR NÚMEROS AO TERMINAR O ESTUDO pra não ter que ficar reenumerando à toa):
- READ.ME (criado automaticamente pelo github e modificado por mim)
- LICENSE (criado automaticamente pelo github)
- functions.php
- index.php (classic theme) or index.html (block theme)
- header.php ou header.html
- footer.php ou footer.html
- sidebar.php ou sidebar.html

### functions.php
-----
if ( ! function_exists( 'nome_tema_funcao_setup' ) ) :
function nome_tema_funcao_setup() { códigos_aqui }
-----
- Lê-se "se função nome_tema_funcao_setup não existir, crie a função nome_tema_funcao_setup com essas características". (DÚVIDAS: se é "se não existir" ou se é "se existir"; o que é o ':'?)
- Define configurações padrões do tema e adiciona recursos próprios do WordPress.
- Definir esta função acima do 'init hook' para não perder suas funcionalidades.

-----
add_theme_support( 'nome-funcao-wp' );
-----
- Adiciona funcionalidades do WordPress ao tema.

-----
register_nav_menus( array(
    'primary'   => __( 'Primary Menu', 'myfirsttheme' ),
    'secondary' => __( 'Secondary Menu', 'myfirsttheme' ),
    'nome-local' => __( 'Nome Local Menu', 'myfirsttheme')
) );
-----
- Em functions.php configura nomes de locais para inserção de menus.
- Para definir os locais de fato, deve inserir 'wp_nav_menu('nome-local')' no corpo da página.

