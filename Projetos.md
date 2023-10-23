{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyO3pzf5oYC36hOb1RrHwk6e",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/GuilhermeBPinheiro/-Desafio-DIO.me_Linux-Projeto3/blob/main/Projetos.ipynb\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Introdução:**\n",
        "\n",
        "**Ken Youens-Clark**, autor de Tiny Python Projetcs (link para acesso: https://tinypythonprojects.com/). Resolver criar um livro para demostrar como escrever códigos Python eficaz, além de como usar testes para escrever e refatorar programas científicos .\n",
        "\n",
        "Então o Mastering Python for Bioinformatics surgiu (link para acesso: https://learning.oreilly.com/library/view/mastering-python-for/9781098100872/). É um guia prático mostra aos profissionais e estudantes de pós-doutorado em bioinformática como explorar as melhores partes do Python para resolver problemas em biologia enquanto criam software que tenha critérios de reprodutibilidade, logo que sejam reproduzíveis: validem seus  **parâmetros**, produzem  **documentação**, e sejam **testáveis** (falhem normalmente e funcionem de maneira confiável --> verificação de bugs).\n"
      ],
      "metadata": {
        "id": "k3Nzrw3R50cC"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Referência:**\n",
        "\n",
        "Ken Youens-Clark. Mastering Python for Bioinformatics (Dominando Python para Bioinformática). 1ªEd. O’Reilly, May, 2021 – 454 pág. 978-1-098-10088-9. Disponível em: https://learning.oreilly.com/library/view/mastering-python-for/9781098100872/. Acesso em: 23 de Out de 2023.\n",
        "\n"
      ],
      "metadata": {
        "id": "ZV20BMqH6CLp"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Tópicos:**\n",
        "\n",
        "*\tCrie programas Python de linha de comando para documentar e validar parâmetros;\n",
        "*\tEscreva testes para verificar programas de refatoração e confirmar se estão corretos;\n",
        "*\tAbordar ideias de bioinformática usando estruturas de dados Python e módulos como Biopython;\n",
        "*\tCrie atalhos e fluxos de trabalho reproduzíveis usando makefiles;\n",
        "*\tAnalise formatos de arquivo essenciais de bioinformática, como FASTA e FASTQ;\n",
        "*\tEncontre padrões de texto usando expressões regulares;\n",
        "*\tUse funções de ordem superior em Python como filter(), map() e reduzir()."
      ],
      "metadata": {
        "id": "ufo4V5Xz6QUo"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Ferramentas:**\n",
        "\n",
        "*\t**Mypy:** é um verificador de tipo estático opcional para Python que visa combinar os benefícios da digitação dinâmica (ou \"duck\") e da digitação estática. Combina o poder expressivo e a conveniência do Python com um poderoso sistema de tipos e verificação de tipos em tempo de compilação. O tipo Mypy verifica programas Python padrão; execute-os usando qualquer VM Python basicamente sem sobrecarga de tempo de execução. Documentação: https://mypy.readthedocs.io/en/stable/.\n",
        "* **Pytest:** estrutura facilita a gravação de testes pequenos e legíveis e pode ser dimensionada para suportar testes funcionais complexos para aplicativos e bibliotecas. Documentação: https://docs.pytest.org/en/7.4.x/.\n",
        "* **Pylinkt:** é um verificador de bugs e qualidade de código fonte para a linguagem de programação Python. Ele segue o estilo recomendado pelo PEP 8, o guia de estilo do Python. É similar ao Pychecker mas inclui as seguintes funcionalidades: Verifica o comprimento de uma linha de código. Documentação: https://pylint.readthedocs.io/en/stable/.\n",
        "*\t**Flake8:** é uma ferramenta de linting Python que verifica sua base de código em busca de erros, problemas de estilo e complexidade. A biblioteca Flake8 é baseada em 3 ferramentas: PyFlakes (verifica se há erros em sua base de código Python), McCabe (verifica a complexidade de sua base de código Python) e pyCodestyle (verifica sua base de código Python em busca de problema de estilo em relação ao PEP8). Documentação: https://flake8.pycqa.org/en/latest/.\n",
        "*\t**BioPython:** é uma biblioteca ou uma suite de ferramentas escritas em Python para manipulação de dados biológicos. Documentação: https://biopython.org/wiki/Documentation.\n",
        "* **Argparse:** é uma ferramenta do Python que serve como analisador sintático para opções de linha de comando, argumentos e subcomandos. Documentação: https://docs.python.org/pt-br/3/library/argparse.html.\n"
      ],
      "metadata": {
        "id": "i6umjaVz6ZX-"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Paradigma de Programação:**\n",
        "\n",
        "* **Programação Funcional (FP):** em ciência da computação, programação funcional é um paradigma de programação que trata a computação como uma avaliação de funções matemáticas e que evita estados ou dados mutáveis. Ela enfatiza a aplicação de funções, em contraste da programação imperativa, que enfatiza mudanças no estado do programa. Referência: https://docs.python.org/3/howto/functional.html  apresenta um bom argumento sobre porque o Python é adequado para FP.\n",
        "\n",
        "* **Desenvolvimento Orientado a Testes (TDD):** ideia explicada em um livro com esse título escrito por Kent Beck (Addison-Wesley, 2002). O TDD defende escrever testes para o código antes de escrevê-lo. O ciclo típico envolve o seguinte:\n",
        "\n",
        "  I. Adicione um teste;\n",
        "\n",
        "  II. Execute todos os testes e veja se o novo teste falha;\n",
        "\n",
        "  III. Escreva o código;\n",
        "\n",
        "  IV. Execute testes;\n",
        "\n",
        "  V. Refatorar código;\n",
        "\n",
        "  VI. Repita.\n"
      ],
      "metadata": {
        "id": "Xu9al-oQ6sMW"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Regras:**\n",
        "\n",
        "* **Evitar o uso de Exceções:** gerenciar exceções para que elas não interrompam o fluxo de um programa Se eu achar que uma exceção é justificada, muitas vezes optarei por não a capturar e deixarei o programa travar., adiciona outro nível de complexidade. *A esse respeito, estou seguindo uma ideia de Joe Armstrong, o criador da linguagem Erlang, que disse: “O jeito Erlang é escrever o caminho feliz, e não escrever pequenas passagens sinuosas cheias de código de correção de erros”. Se você optar por escrever programas e módulos para lançamento público, precisará aprender muito mais sobre exceções e tratamento de erros.*\n",
        "\n",
        "* **Estrutura:** Autor: *“Embora o <Zen do Python> (https://peps.python.org/pep-0020/) diga “Deve haver uma – e de preferência apenas uma – maneira óbvia de fazer isso”, acredito que você pode aprender bastante tentando muitas abordagens diferentes para um problema. Perl foi minha porta de entrada para a bioinformática, e o espírito da comunidade Perl de “Há mais de uma maneira de fazer isso”; <TMTOWTDI> (https://en.wikipedia.org/wiki/Perl) ainda ressoa em mim.”*\n",
        "\n",
        "* **Sem uso de Notebooks:** código-fonte dos Notebooks é armazenado em JavaScript Object Notation (JSON) e não como texto orientado a linhas. Isso torna muito difícil usar ferramentas como diffencontrar diferenças entre dois notebooks. Além disso, os Notebooks não podem ser parametrizados, o que significa que não posso passar argumentos de fora do programa para alterar o comportamento, mas sim alterar o próprio código-fonte. Isso torna os programas inflexíveis e os testes automatizados impossíveis. Embora eu incentive você a explorar Notebooks, especialmente como uma forma interativa de executar Python, vou me concentrar em como escrever programas de linha de comando.\n"
      ],
      "metadata": {
        "id": "yjgp6KcN6-dS"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Conceitos para Estudar:**\n",
        "\n",
        "* Variáveis Globais x Locais. Referência: https://automacaoweb.wordpress.com/2020/09/18/variaveis-globais-x-variaveis-locais/.\n",
        "* Programação Orientada a Objetos x Programação Estruturada. Referência: https://www.devmedia.com.br/programacao-orientada-a-objetos-e-programacao-estruturada/32813#:~:text=Portanto%2C%20como%20vimos%20no%20decorrer,e%20fun%C3%A7%C3%B5es%20definidas%20pelo%20usu%C3%A1rio.\n",
        "* Servidores Linux. Referência: https://www.certificacaolinux.com.br/servidor-linux/.\n",
        "* Distribuições Linux: Ubuntu x Debian. Referência: https://blog.betrybe.com/distribuicoes-linux/.\n",
        "* Shell Script: é uma linguagem de script utilizada em alguns sistemas operacionais, principalmente em sistemas GNU/Linux. Atualmente existem vários programas tipo Shell. Além dos principais - sh e bash -, existem também: ksh, zsh, csh e tcsh. Um script em Shell necessita basicamente do interpretador Shell. Referência: https://www.devmedia.com.br/introducao-ao-shell-script-no-linux/25778.\n",
        "* Computação de Alto Desempenho (HPC). Referência: https://www.oracle.com/br/cloud/hpc/what-is-hpc/.\n",
        "* Docker. Referência: https://nelson-souza.medium.com/docker-virtualbox-linux-c57596256af6.\n",
        "* Macintosh. Referência: https://www.google.com/search?q=Macintosh&rlz=1C1KNTJ_pt-BRBR999BR999&sourceid=chrome&ie=UTF-8.\n",
        "* Shell Windows (CMD  PowerShell) x GNU/Linux (Bash). Referência: https://www.quora.com/What-is-the-difference-between-CMD-Git-Bash-and-PowerShell.\n",
        "* Ambientes de Desenvolvimento Integrados (IDEs) - Ex.: VS Code, PyCharm ou Spyder. Referência: https://paulovasconcellos.com.br/quais-s%C3%A3o-as-melhores-ide-para-python-confira-a-lista-279b54bef301.\n",
        "* Editores de Textos – Ex.: Vim Editor, Sublime, TextMate ou Notepad++. Referência: https://cursos.alura.com.br/forum/topico-notepad-ou-sublime-130108\n",
        "* Gerenciador de Pacotes – Ex. Ubuntu (apt) e Mac (brew). Referências: https://br-mac.org/2012/09/apt-get-no-mac-gerenciadores-de-pacotes-para-o-os-x.html.\n",
        "* Python. Referência: https://www.python.org/downloads/.\n",
        "* Distribuição Anaconda Python. Referência: https://www.anaconda.com/ | http://leg.ufpr.br/~walmes/ensino/dsbd-linprog/instalacao-anaconda.html#:~:text=O%20Anaconda%20pode%20ser%20entendido,Python%3A%20python3.\n",
        "* Google Colab x Jupyter. Referências: https://cursos.alura.com.br/forum/topico-quais-plataformas-sao-usadas-para-data-science-no-mercado-de-trabalho-176750.\n"
      ],
      "metadata": {
        "id": "OKALLJqH7Y8t"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Configuração do Ambiente Virtual:**\n",
        "\n",
        "*\tUbuntu Windows Subsytem for Linux (WSL) – Version 1.0 --> tenha uma linha de comando Unix verdadeira.\n",
        "* IDEs Visual Studio Code (VS Code) – Version 1.83 --> escrever, executar e testar programas.\n",
        "*\tPython – Version 3.86 e 3.9.1 --> linguagem de programação para executar os testes.\n",
        "* Ubuntu Linux - Apt-Get --> gerenciador de pacotes.\n",
        "* Google Colab --> divulgar e documentar informações.\n"
      ],
      "metadata": {
        "id": "gtAFuHGw7v_5"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Os “14” Desafios de Rosalind de Youens:**\n",
        "\n",
        "* Plataforma: Rosalind. Link de acesso: https://rosalind.info/about/.\n",
        "* Repositório: Biofx_Python. Link de acesso: https://github.com/GuilhermeBPinheiro/biofx_python.\n",
        "* Se você tiver alguma dúvida técnica ou problema ao usar os exemplos de código, envie um e-mail para bookquestions@oreilly.com.\n",
        "* Se você acha que o uso de exemplos de código está fora do uso justo ou da permissão dada acima, sinta-se à vontade para nos contatar em permissions@oreilly.com.\n",
        "* Acessar o livro base: https://oreil.ly/mastering-bioinformatics-python.\n"
      ],
      "metadata": {
        "id": "5QjTSrRy8PXc"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Instalando Python:**\n",
        "\n",
        "Você precisará instalar o Python para conseguir continuar rodando o pipeline.\n"
      ],
      "metadata": {
        "id": "QVxGPIkS9Qhh"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "!sudo apt install python3-pip"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "WoAJlnPe9cC4",
        "outputId": "b7ab37a9-2574-428e-87cd-2c024558df95"
      },
      "execution_count": 6,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Reading package lists... Done\n",
            "Building dependency tree... Done\n",
            "Reading state information... Done\n",
            "The following additional packages will be installed:\n",
            "  python3-setuptools python3-wheel\n",
            "Suggested packages:\n",
            "  python-setuptools-doc\n",
            "The following NEW packages will be installed:\n",
            "  python3-pip python3-setuptools python3-wheel\n",
            "0 upgraded, 3 newly installed, 0 to remove and 18 not upgraded.\n",
            "Need to get 1,677 kB of archives.\n",
            "After this operation, 8,965 kB of additional disk space will be used.\n",
            "Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 python3-setuptools all 59.6.0-1.2ubuntu0.22.04.1 [339 kB]\n",
            "Get:2 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3-wheel all 0.37.1-2ubuntu0.22.04.1 [32.0 kB]\n",
            "Get:3 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3-pip all 22.0.2+dfsg-1ubuntu0.3 [1,305 kB]\n",
            "Fetched 1,677 kB in 1s (1,548 kB/s)\n",
            "debconf: unable to initialize frontend: Dialog\n",
            "debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78, <> line 3.)\n",
            "debconf: falling back to frontend: Readline\n",
            "debconf: unable to initialize frontend: Readline\n",
            "debconf: (This frontend requires a controlling tty.)\n",
            "debconf: falling back to frontend: Teletype\n",
            "dpkg-preconfigure: unable to re-open stdin: \n",
            "Selecting previously unselected package python3-setuptools.\n",
            "(Reading database ... 120874 files and directories currently installed.)\n",
            "Preparing to unpack .../python3-setuptools_59.6.0-1.2ubuntu0.22.04.1_all.deb ...\n",
            "Unpacking python3-setuptools (59.6.0-1.2ubuntu0.22.04.1) ...\n",
            "Selecting previously unselected package python3-wheel.\n",
            "Preparing to unpack .../python3-wheel_0.37.1-2ubuntu0.22.04.1_all.deb ...\n",
            "Unpacking python3-wheel (0.37.1-2ubuntu0.22.04.1) ...\n",
            "Selecting previously unselected package python3-pip.\n",
            "Preparing to unpack .../python3-pip_22.0.2+dfsg-1ubuntu0.3_all.deb ...\n",
            "Unpacking python3-pip (22.0.2+dfsg-1ubuntu0.3) ...\n",
            "Setting up python3-setuptools (59.6.0-1.2ubuntu0.22.04.1) ...\n",
            "Setting up python3-wheel (0.37.1-2ubuntu0.22.04.1) ...\n",
            "Setting up python3-pip (22.0.2+dfsg-1ubuntu0.3) ...\n",
            "Processing triggers for man-db (2.10.2-1) ...\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Instalando Módulos:**\n",
        "\n",
        "Você precisará instalar vários módulos e ferramentas Python. Incluí um arquivo requisitos.txt no nível superior do repositório. Este arquivo lista todos os módulos necessários para executar os programas do livro.\n"
      ],
      "metadata": {
        "id": "T9hkvu864451"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "## Listas de Módulos:\n",
        "* biopython\n",
        "* black\n",
        "* csvkit\n",
        "* csvchk\n",
        "* flake8\n",
        "* graphviz\n",
        "* iteration_utilities\n",
        "* mypy\n",
        "* new-py\n",
        "* pandas\n",
        "* pylint\n",
        "* pytest\n",
        "* pytest-flake8\n",
        "* pytest-mypy\n",
        "* pytest-pylint\n",
        "* requests\n",
        "* rich\n",
        "* tabulate\n",
        "* yapf\n",
        "* seqmagick"
      ],
      "metadata": {
        "id": "QpsWizpR5zXz"
      }
    },
    {
      "cell_type": "code",
      "execution_count": 9,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "x6ZzVMNC4QqX",
        "outputId": "fb91dc26-676f-4b90-f5b2-103ca94e5d79"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Collecting biopython (from -r requirements.txt (line 1))\n",
            "  Downloading biopython-1.81-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (3.1 MB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m3.1/3.1 MB\u001b[0m \u001b[31m27.1 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting black (from -r requirements.txt (line 2))\n",
            "  Downloading black-23.10.0-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (1.6 MB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m1.6/1.6 MB\u001b[0m \u001b[31m43.7 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting csvkit (from -r requirements.txt (line 3))\n",
            "  Downloading csvkit-1.3.0-py2.py3-none-any.whl (43 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m43.3/43.3 kB\u001b[0m \u001b[31m4.8 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting csvchk (from -r requirements.txt (line 4))\n",
            "  Downloading csvchk-0.3.2-py3-none-any.whl (7.8 kB)\n",
            "Collecting flake8 (from -r requirements.txt (line 5))\n",
            "  Downloading flake8-6.1.0-py2.py3-none-any.whl (58 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m58.3/58.3 kB\u001b[0m \u001b[31m6.6 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hRequirement already satisfied: graphviz in /usr/local/lib/python3.10/dist-packages (from -r requirements.txt (line 6)) (0.20.1)\n",
            "Collecting iteration_utilities (from -r requirements.txt (line 7))\n",
            "  Downloading iteration_utilities-0.12.0-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (486 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m486.3/486.3 kB\u001b[0m \u001b[31m41.4 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting mypy (from -r requirements.txt (line 8))\n",
            "  Downloading mypy-1.6.1-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (12.2 MB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m12.2/12.2 MB\u001b[0m \u001b[31m89.7 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting new-py (from -r requirements.txt (line 9))\n",
            "  Downloading new_py-0.1.2-py3-none-any.whl (6.4 kB)\n",
            "Requirement already satisfied: pandas in /usr/local/lib/python3.10/dist-packages (from -r requirements.txt (line 10)) (1.5.3)\n",
            "Collecting pylint (from -r requirements.txt (line 11))\n",
            "  Downloading pylint-3.0.2-py3-none-any.whl (510 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m510.6/510.6 kB\u001b[0m \u001b[31m41.6 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hRequirement already satisfied: pytest in /usr/local/lib/python3.10/dist-packages (from -r requirements.txt (line 12)) (7.4.2)\n",
            "Collecting pytest-flake8 (from -r requirements.txt (line 13))\n",
            "  Downloading pytest_flake8-1.1.1-py2.py3-none-any.whl (6.6 kB)\n",
            "Collecting pytest-mypy (from -r requirements.txt (line 14))\n",
            "  Downloading pytest_mypy-0.10.3-py3-none-any.whl (7.1 kB)\n",
            "Collecting pytest-pylint (from -r requirements.txt (line 15))\n",
            "  Downloading pytest_pylint-0.21.0-py3-none-any.whl (9.8 kB)\n",
            "Requirement already satisfied: requests in /usr/local/lib/python3.10/dist-packages (from -r requirements.txt (line 16)) (2.31.0)\n",
            "Requirement already satisfied: rich in /usr/local/lib/python3.10/dist-packages (from -r requirements.txt (line 17)) (13.6.0)\n",
            "Requirement already satisfied: tabulate in /usr/local/lib/python3.10/dist-packages (from -r requirements.txt (line 18)) (0.9.0)\n",
            "Collecting yapf (from -r requirements.txt (line 19))\n",
            "  Downloading yapf-0.40.2-py3-none-any.whl (254 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m254.7/254.7 kB\u001b[0m \u001b[31m23.4 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting seqmagick (from -r requirements.txt (line 20))\n",
            "  Downloading seqmagick-0.8.6.tar.gz (52 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m52.2/52.2 kB\u001b[0m \u001b[31m5.1 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25h  Preparing metadata (setup.py) ... \u001b[?25l\u001b[?25hdone\n",
            "Requirement already satisfied: numpy in /usr/local/lib/python3.10/dist-packages (from biopython->-r requirements.txt (line 1)) (1.23.5)\n",
            "Requirement already satisfied: click>=8.0.0 in /usr/local/lib/python3.10/dist-packages (from black->-r requirements.txt (line 2)) (8.1.7)\n",
            "Collecting mypy-extensions>=0.4.3 (from black->-r requirements.txt (line 2))\n",
            "  Downloading mypy_extensions-1.0.0-py3-none-any.whl (4.7 kB)\n",
            "Requirement already satisfied: packaging>=22.0 in /usr/local/lib/python3.10/dist-packages (from black->-r requirements.txt (line 2)) (23.2)\n",
            "Collecting pathspec>=0.9.0 (from black->-r requirements.txt (line 2))\n",
            "  Downloading pathspec-0.11.2-py3-none-any.whl (29 kB)\n",
            "Requirement already satisfied: platformdirs>=2 in /usr/local/lib/python3.10/dist-packages (from black->-r requirements.txt (line 2)) (3.11.0)\n",
            "Requirement already satisfied: tomli>=1.1.0 in /usr/local/lib/python3.10/dist-packages (from black->-r requirements.txt (line 2)) (2.0.1)\n",
            "Requirement already satisfied: typing-extensions>=4.0.1 in /usr/local/lib/python3.10/dist-packages (from black->-r requirements.txt (line 2)) (4.5.0)\n",
            "Collecting agate>=1.6.1 (from csvkit->-r requirements.txt (line 3))\n",
            "  Downloading agate-1.9.0-py2.py3-none-any.whl (94 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m95.0/95.0 kB\u001b[0m \u001b[31m7.4 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting agate-excel>=0.2.2 (from csvkit->-r requirements.txt (line 3))\n",
            "  Downloading agate_excel-0.2.5-py2.py3-none-any.whl (7.1 kB)\n",
            "Collecting agate-dbf>=0.2.2 (from csvkit->-r requirements.txt (line 3))\n",
            "  Downloading agate_dbf-0.2.2-py2.py3-none-any.whl (3.5 kB)\n",
            "Collecting agate-sql>=0.5.3 (from csvkit->-r requirements.txt (line 3))\n",
            "  Downloading agate_sql-0.7.0-py2.py3-none-any.whl (7.2 kB)\n",
            "Requirement already satisfied: openpyxl in /usr/local/lib/python3.10/dist-packages (from csvkit->-r requirements.txt (line 3)) (3.1.2)\n",
            "Requirement already satisfied: sqlalchemy in /usr/local/lib/python3.10/dist-packages (from csvkit->-r requirements.txt (line 3)) (2.0.22)\n",
            "Requirement already satisfied: xlrd in /usr/local/lib/python3.10/dist-packages (from csvkit->-r requirements.txt (line 3)) (2.0.1)\n",
            "Collecting mccabe<0.8.0,>=0.7.0 (from flake8->-r requirements.txt (line 5))\n",
            "  Downloading mccabe-0.7.0-py2.py3-none-any.whl (7.3 kB)\n",
            "Collecting pycodestyle<2.12.0,>=2.11.0 (from flake8->-r requirements.txt (line 5))\n",
            "  Downloading pycodestyle-2.11.1-py2.py3-none-any.whl (31 kB)\n",
            "Collecting pyflakes<3.2.0,>=3.1.0 (from flake8->-r requirements.txt (line 5))\n",
            "  Downloading pyflakes-3.1.0-py2.py3-none-any.whl (62 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m62.6/62.6 kB\u001b[0m \u001b[31m7.1 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hRequirement already satisfied: python-dateutil>=2.8.1 in /usr/local/lib/python3.10/dist-packages (from pandas->-r requirements.txt (line 10)) (2.8.2)\n",
            "Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.10/dist-packages (from pandas->-r requirements.txt (line 10)) (2023.3.post1)\n",
            "Collecting astroid<=3.1.0-dev0,>=3.0.1 (from pylint->-r requirements.txt (line 11))\n",
            "  Downloading astroid-3.0.1-py3-none-any.whl (275 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m275.2/275.2 kB\u001b[0m \u001b[31m25.9 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting isort<6,>=4.2.5 (from pylint->-r requirements.txt (line 11))\n",
            "  Downloading isort-5.12.0-py3-none-any.whl (91 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m91.2/91.2 kB\u001b[0m \u001b[31m10.6 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting tomlkit>=0.10.1 (from pylint->-r requirements.txt (line 11))\n",
            "  Downloading tomlkit-0.12.1-py3-none-any.whl (37 kB)\n",
            "Collecting dill>=0.2 (from pylint->-r requirements.txt (line 11))\n",
            "  Downloading dill-0.3.7-py3-none-any.whl (115 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m115.3/115.3 kB\u001b[0m \u001b[31m13.7 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hRequirement already satisfied: iniconfig in /usr/local/lib/python3.10/dist-packages (from pytest->-r requirements.txt (line 12)) (2.0.0)\n",
            "Requirement already satisfied: pluggy<2.0,>=0.12 in /usr/local/lib/python3.10/dist-packages (from pytest->-r requirements.txt (line 12)) (1.3.0)\n",
            "Requirement already satisfied: exceptiongroup>=1.0.0rc8 in /usr/local/lib/python3.10/dist-packages (from pytest->-r requirements.txt (line 12)) (1.1.3)\n",
            "Requirement already satisfied: attrs>=19.0 in /usr/local/lib/python3.10/dist-packages (from pytest-mypy->-r requirements.txt (line 14)) (23.1.0)\n",
            "Requirement already satisfied: filelock>=3.0 in /usr/local/lib/python3.10/dist-packages (from pytest-mypy->-r requirements.txt (line 14)) (3.12.4)\n",
            "Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.10/dist-packages (from requests->-r requirements.txt (line 16)) (3.3.0)\n",
            "Requirement already satisfied: idna<4,>=2.5 in /usr/local/lib/python3.10/dist-packages (from requests->-r requirements.txt (line 16)) (3.4)\n",
            "Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/local/lib/python3.10/dist-packages (from requests->-r requirements.txt (line 16)) (2.0.7)\n",
            "Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.10/dist-packages (from requests->-r requirements.txt (line 16)) (2023.7.22)\n",
            "Requirement already satisfied: markdown-it-py>=2.2.0 in /usr/local/lib/python3.10/dist-packages (from rich->-r requirements.txt (line 17)) (3.0.0)\n",
            "Requirement already satisfied: pygments<3.0.0,>=2.13.0 in /usr/local/lib/python3.10/dist-packages (from rich->-r requirements.txt (line 17)) (2.16.1)\n",
            "Requirement already satisfied: importlib-metadata>=6.6.0 in /usr/local/lib/python3.10/dist-packages (from yapf->-r requirements.txt (line 19)) (6.8.0)\n",
            "Collecting pygtrie>=2.1 (from seqmagick->-r requirements.txt (line 20))\n",
            "  Downloading pygtrie-2.5.0-py3-none-any.whl (25 kB)\n",
            "Requirement already satisfied: Babel>=2.0 in /usr/local/lib/python3.10/dist-packages (from agate>=1.6.1->csvkit->-r requirements.txt (line 3)) (2.13.0)\n",
            "Collecting isodate>=0.5.4 (from agate>=1.6.1->csvkit->-r requirements.txt (line 3))\n",
            "  Downloading isodate-0.6.1-py2.py3-none-any.whl (41 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m41.7/41.7 kB\u001b[0m \u001b[31m4.4 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hCollecting leather>=0.3.2 (from agate>=1.6.1->csvkit->-r requirements.txt (line 3))\n",
            "  Downloading leather-0.3.4-py2.py3-none-any.whl (31 kB)\n",
            "Collecting parsedatetime!=2.5,>=2.1 (from agate>=1.6.1->csvkit->-r requirements.txt (line 3))\n",
            "  Downloading parsedatetime-2.6-py3-none-any.whl (42 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m42.5/42.5 kB\u001b[0m \u001b[31m4.7 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25hRequirement already satisfied: python-slugify>=1.2.1 in /usr/local/lib/python3.10/dist-packages (from agate>=1.6.1->csvkit->-r requirements.txt (line 3)) (8.0.1)\n",
            "Collecting pytimeparse>=1.1.5 (from agate>=1.6.1->csvkit->-r requirements.txt (line 3))\n",
            "  Downloading pytimeparse-1.1.8-py2.py3-none-any.whl (10.0 kB)\n",
            "Collecting dbfread>=2.0.5 (from agate-dbf>=0.2.2->csvkit->-r requirements.txt (line 3))\n",
            "  Downloading dbfread-2.0.7-py2.py3-none-any.whl (20 kB)\n",
            "Collecting olefile (from agate-excel>=0.2.2->csvkit->-r requirements.txt (line 3))\n",
            "  Downloading olefile-0.46.zip (112 kB)\n",
            "\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m112.2/112.2 kB\u001b[0m \u001b[31m9.8 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25h  Preparing metadata (setup.py) ... \u001b[?25l\u001b[?25hdone\n",
            "Requirement already satisfied: six in /usr/local/lib/python3.10/dist-packages (from agate-excel>=0.2.2->csvkit->-r requirements.txt (line 3)) (1.16.0)\n",
            "Requirement already satisfied: zipp>=0.5 in /usr/local/lib/python3.10/dist-packages (from importlib-metadata>=6.6.0->yapf->-r requirements.txt (line 19)) (3.17.0)\n",
            "Requirement already satisfied: mdurl~=0.1 in /usr/local/lib/python3.10/dist-packages (from markdown-it-py>=2.2.0->rich->-r requirements.txt (line 17)) (0.1.2)\n",
            "Requirement already satisfied: et-xmlfile in /usr/local/lib/python3.10/dist-packages (from openpyxl->csvkit->-r requirements.txt (line 3)) (1.1.0)\n",
            "Requirement already satisfied: greenlet!=0.4.17 in /usr/local/lib/python3.10/dist-packages (from sqlalchemy->csvkit->-r requirements.txt (line 3)) (3.0.0)\n",
            "Requirement already satisfied: text-unidecode>=1.3 in /usr/local/lib/python3.10/dist-packages (from python-slugify>=1.2.1->agate>=1.6.1->csvkit->-r requirements.txt (line 3)) (1.3)\n",
            "Building wheels for collected packages: seqmagick, olefile\n",
            "  Building wheel for seqmagick (setup.py) ... \u001b[?25l\u001b[?25hdone\n",
            "  Created wheel for seqmagick: filename=seqmagick-0.8.6-py3-none-any.whl size=62626 sha256=d3145bf79692513de1009b997ef1ba890836fdc894ed1291060aa3e247c54738\n",
            "  Stored in directory: /root/.cache/pip/wheels/0b/41/9e/53e5e2d7cac314b09e1a86a19b4d6d653864cf8f6ddb2fabdc\n",
            "  Building wheel for olefile (setup.py) ... \u001b[?25l\u001b[?25hdone\n",
            "  Created wheel for olefile: filename=olefile-0.46-py2.py3-none-any.whl size=35417 sha256=ca756edab8fe9466879309c362f37323ae03c5348ff899b23b00cc2bdb7afff7\n",
            "  Stored in directory: /root/.cache/pip/wheels/02/39/c0/9eb1f7a42b4b38f6f333b6314d4ed11c46f12a0f7b78194f0d\n",
            "Successfully built seqmagick olefile\n",
            "Installing collected packages: pytimeparse, pygtrie, parsedatetime, new-py, dbfread, tomlkit, pyflakes, pycodestyle, pathspec, olefile, mypy-extensions, mccabe, leather, iteration_utilities, isort, isodate, dill, csvchk, biopython, astroid, yapf, seqmagick, pylint, mypy, flake8, black, agate, pytest-pylint, pytest-mypy, pytest-flake8, agate-sql, agate-excel, agate-dbf, csvkit\n",
            "Successfully installed agate-1.9.0 agate-dbf-0.2.2 agate-excel-0.2.5 agate-sql-0.7.0 astroid-3.0.1 biopython-1.81 black-23.10.0 csvchk-0.3.2 csvkit-1.3.0 dbfread-2.0.7 dill-0.3.7 flake8-6.1.0 isodate-0.6.1 isort-5.12.0 iteration_utilities-0.12.0 leather-0.3.4 mccabe-0.7.0 mypy-1.6.1 mypy-extensions-1.0.0 new-py-0.1.2 olefile-0.46 parsedatetime-2.6 pathspec-0.11.2 pycodestyle-2.11.1 pyflakes-3.1.0 pygtrie-2.5.0 pylint-3.0.2 pytest-flake8-1.1.1 pytest-mypy-0.10.3 pytest-pylint-0.21.0 pytimeparse-1.1.8 seqmagick-0.8.6 tomlkit-0.12.1 yapf-0.40.2\n"
          ]
        }
      ],
      "source": [
        "! python3 -m pip install -r requirements.txt"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Instalando o programa new.py**\n",
        "\n",
        "O new.pyprograma criará um programa Python novo e bem estruturado que usa o argparsemódulo para interpretar argumentos de linha de comando. Deveria ter sido instalado na seção anterior com as dependências do módulo."
      ],
      "metadata": {
        "id": "bO58pCmN-x9T"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "! python3 -m pip install new-py"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "NBKyq-9u-xcZ",
        "outputId": "dd34e12e-0496-4bc0-b0ba-5465b597f3df"
      },
      "execution_count": 10,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Requirement already satisfied: new-py in /usr/local/lib/python3.10/dist-packages (0.1.2)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Agora você deve conseguir executar new.pye ver algo assim:"
      ],
      "metadata": {
        "id": "AUQriNEU_Bjd"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "! new.py\n",
        "\n",
        "'''usage: new.py [-h] [-n NAME] [-e EMAIL] [-p PURPOSE] [-t] [-f] [--version]\n",
        "              program\n",
        "new.py: error: the following arguments are required: program'''"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 90
        },
        "id": "D-l7jNBO_CUZ",
        "outputId": "8de4aa69-93c8-4cb8-c3eb-f3ed23ae2e2b"
      },
      "execution_count": 12,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "usage: new.py [-h] [-n NAME] [-e EMAIL] [-p PURPOSE] [-t] [-f] [--version] program\n",
            "new.py: error: the following arguments are required: program\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "'usage: new.py [-h] [-n NAME] [-e EMAIL] [-p PURPOSE] [-t] [-f] [--version]\\n              program\\nnew.py: error: the following arguments are required: program'"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "string"
            }
          },
          "metadata": {},
          "execution_count": 12
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Cada exercício irá sugerir que você use new.pypara começar a escrever seus novos programas. Por exemplo, no Desafio 1 você criará um programa chamado dna.py no <diretório 01_dna>, assim:"
      ],
      "metadata": {
        "id": "V4lnDbwX_Lzn"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "! cd /content/diretorio-01_dna\n",
        "! new.py dna.py\n",
        "# Done, see new script \"dna.py\""
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "p0Syf5xC_aRj",
        "outputId": "4105bf35-e550-4c5c-bde8-1ea355dc122b"
      },
      "execution_count": 15,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "\"dna.py\" exists.  Overwrite? [yN] N\n",
            "Will not overwrite. Bye!\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Se você executar o `./dna.py --help`, verá que ele gera documentação de ajuda sobre como usar o programa. Você deve abrir o `dna.py `programa em seu editor, modificar os argumentos e adicionar seu código para satisfazer os requisitos do programa e dos testes.\n",
        "\n",
        "Observe que nunca é um requisito que você use o `new.py`. Ofereço isso apenas como uma ajuda para começar. É assim que inicio cada um dos meus programas, mas, embora eu ache útil, você pode preferir seguir um caminho diferente. Contanto que seus programas passem nos conjuntos de testes, você pode escrevê-los como quiser."
      ],
      "metadata": {
        "id": "or4NkVBtAMM-"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "! ./dna.py --help"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "BrOVljOYAkF5",
        "outputId": "5b523553-5ad3-46a6-f66e-7e794eb9a246"
      },
      "execution_count": 17,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "usage: dna.py [-h] [-a str] [-i int] [-f FILE] [-o] str\n",
            "\n",
            "Rock the Casbah\n",
            "\n",
            "positional arguments:\n",
            "  str                   A positional argument\n",
            "\n",
            "options:\n",
            "  -h, --help            show this help message and exit\n",
            "  -a str, --arg str     A named string argument (default: )\n",
            "  -i int, --int int     A named integer argument (default: 0)\n",
            "  -f FILE, --file FILE  A readable file (default: None)\n",
            "  -o, --on              A boolean flag (default: False)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Ferramentas de Bioinformáticas:**\n",
        "\n",
        "* **1. Gramene.org** [ref.: https://www.gramene.org/].\n",
        "\n",
        "  É um recurso online de código aberto, e com curadoria para genômicas (anotações, variações e ferramentas) comparativa de plantas.\n"
      ],
      "metadata": {
        "id": "iD36h8f_B0eR"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Referências Profissionais:**\n",
        "\n",
        "* **1. Ken Youens-Clark** [ref.: https://www.linkedin.com/in/kycl4rk/].\n",
        "\n",
        "  O autor responsável por escrever três livros: Tiny Python Projects - Learn coding and testing with puzzles and games (2020); Command-line Rust (2022); e Mastering Python for Bioinformatics (2021). Este último livro, foi o que deu a base para escrever esse estudo, no qual estou desenvolvendo conforme a leitura do mesmo.\n",
        "\n",
        "* **2. Dr. Lincoln Stein** [ref.: https://oicr.on.ca/researchers/dr-lincoln-stein/].\n",
        "\n",
        "  O Dr. Lincoln Stein se concentra em apoiar a pesquisa biomédica em Ontário e em todo o mundo, tornando grandes e complexos conjuntos de dados biológicos encontráveis, acessíveis e utilizáveis.\n"
      ],
      "metadata": {
        "id": "92LlMZHkCXQ0"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Cursos:**\n",
        "\n",
        "* **1. CSHL (Cold Spring Harbor Laboratory)** [ref.: https://meetings.cshl.edu/courseshome.aspx].\n"
      ],
      "metadata": {
        "id": "mFFLDsEdCs8l"
      }
    }
  ]
}