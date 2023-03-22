# 2. Usando o interpretador Python

## 2.1. Chamando o interpretador

O interpretador Python geralmente é instalado /usr/local/bin/python3.11 nas máquinas em que está disponível; inserir /usr/local/bino caminho de pesquisa do seu shell Unix torna possível iniciá-lo digitando o comando:

    python3.11

à casca. 1 Como a escolha do diretório onde reside o intérprete é uma opção de instalação, outros locais são possíveis; verifique com seu guru Python local ou administrador do sistema. (Por exemplo, /usr/local/python é um local alternativo popular.)

Em máquinas Windows nas quais você instalou o Python da Microsoft Store , o python3.11comando estará disponível. Se você tiver o iniciador py.exe instalado, poderá usar o py comando. Consulte Excursus: Definindo variáveis ​​de ambiente para outras maneiras de iniciar o Python.

Digitar um caractere de fim de arquivo ( no Unix, no Windows) no prompt principal faz com que o interpretador saia com um status de saída zero. Se isso não funcionar, você pode sair do interpretador digitando o seguinte comando: .Control-DControl-Zquit()

Os recursos de edição de linha do interpretador incluem edição interativa, substituição de histórico e conclusão de código em sistemas que suportam a biblioteca GNU Readline . Talvez a verificação mais rápida para ver se a edição de linha de comando é suportada é digitar no primeiro prompt do Python que você obtiver. Se emitir um bipe, você tem edição de linha de comando; consulte o Apêndice Edição de entrada interativa e substituição de histórico para obter uma introdução às chaves. Se nada acontecer, ou se houver eco, a edição da linha de comando não estará disponível; você só poderá usar backspace para remover caracteres da linha atual.Control-P^P

O interpretador funciona como o shell do Unix: quando chamado com entrada padrão conectada a um dispositivo tty, ele lê e executa comandos interativamente; quando chamado com um argumento de nome de arquivo ou com um arquivo como entrada padrão, ele lê e executa um script desse arquivo.

Uma segunda forma de iniciar o interpretador é , que executa a(s) instrução(ões) em command , de forma análoga à opção do shell. Como as instruções do Python geralmente contêm espaços ou outros caracteres especiais para o shell, geralmente é recomendável citar o comando em sua totalidade.python -c command [arg] ...-c

Alguns módulos Python também são úteis como scripts. Eles podem ser invocados usando , que executa o arquivo de origem do módulo como se você tivesse digitado seu nome completo na linha de comando.python -m module [arg] ...

Quando um arquivo de script é usado, às vezes é útil poder executar o script e entrar no modo interativo posteriormente. Isso pode ser feito passando -i antes do script.

Todas as opções de linha de comando são descritas em Linha de comando e ambiente .

### 2.1.1. Passagem de Argumento 

Quando conhecido pelo interpretador, o nome do script e os argumentos adicionais subsequentes são transformados em uma lista de strings e atribuídos à argv variável no sysmódulo. Você pode acessar esta lista executando . O comprimento da lista é pelo menos um; quando nenhum script e nenhum argumento é dado, é uma string vazia. Quando o nome do script é fornecido como (significando entrada padrão), é definido como . Quando o comando é usado, é definido como . Quando o módulo é usado, é definido como o nome completo do módulo localizado. As opções encontradas após o comando ou módulo não são consumidas pelo processamento de opções do interpretador Python, mas deixadas emimport syssys.argv[0]'-'sys.argv[0]'-'-c sys.argv[0]'-c'-m sys.argv[0]-c -m sys.argvpara o comando ou módulo manipular.

### 2.1.2. Modo interativo 
Quando os comandos são lidos de um tty, diz-se que o interpretador está no modo interativo . Nesse modo, ele solicita o próximo comando com o prompt principal , geralmente três sinais de maior que ( >>>); para linhas de continuação, ele exibe o prompt secundário , por padrão, três pontos ( ...). O interpretador imprime uma mensagem de boas-vindas informando seu número de versão e um aviso de direitos autorais antes de imprimir o primeiro prompt:

python3.11

Python 3.11 (default, April 4 2021, 09:25:04)
[GCC 10.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
As linhas de continuação são necessárias ao inserir uma construção de várias linhas. Como exemplo, dê uma olhada nesta ifdeclaração:

>>>
the_world_is_flat = True
if the_world_is_flat:
    print("Be careful not to fall off!")

Be careful not to fall off!
Para saber mais sobre o modo interativo, consulte Modo interativo .

## 2.2. O intérprete e seu ambiente 
### 2.2.1. Codificação do código-fonte 
Por padrão, os arquivos de origem do Python são tratados como codificados em UTF-8. Nessa codificação, os caracteres da maioria dos idiomas do mundo podem ser usados ​​simultaneamente em strings literais, identificadores e comentários — embora a biblioteca padrão use apenas caracteres ASCII para identificadores, uma convenção que qualquer código portátil deve seguir. Para exibir todos esses caracteres corretamente, seu editor deve reconhecer que o arquivo é UTF-8 e deve usar uma fonte que suporte todos os caracteres do arquivo.

Para declarar uma codificação diferente da padrão, uma linha de comentário especial deve ser adicionada como a primeira linha do arquivo. A sintaxe é a seguinte:

# -*- coding: encoding -*-
onde a codificação é uma das válidas codecssuportadas pelo Python.

Por exemplo, para declarar que a codificação Windows-1252 deve ser usada, a primeira linha do arquivo de código-fonte deve ser:

# -*- coding: cp1252 -*-
Uma exceção à regra da primeira linha é quando o código-fonte começa com uma linha UNIX “shebang” . Nesse caso, a declaração de codificação deve ser adicionada como a segunda linha do arquivo. Por exemplo:

#!/usr/bin/env python3
# -*- coding: cp1252 -*-
notas de rodapé

1
No Unix, o interpretador Python 3.x, por padrão, não é instalado com o executável denominado python, para que não entre em conflito com um executável Python 2.x instalado simultaneamente.