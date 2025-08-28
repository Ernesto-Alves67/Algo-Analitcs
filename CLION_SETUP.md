# Configuração do Projeto Algo-Analytics no CLion

Este documento explica como configurar o projeto Algo-Analytics no CLion após a correção dos problemas de versionamento.

## Problemas de Versionamento Corrigidos

### Arquivos que foram removidos do controle de versão:
- **build/** - Diretório completo com binários e arquivos gerados
- **algo_analitics.pro.user** - Configurações pessoais do Qt Creator
- **ui_mainwindow.h** - Arquivos gerados automaticamente pelo Qt

### Arquivo .gitignore criado
Um arquivo `.gitignore` adequado foi criado para evitar versionamento incorreto no futuro.

## Configuração no CLion

### Pré-requisitos
1. CLion instalado
2. Qt6 instalado no sistema
3. CMake 3.16 ou superior

### Passos para configurar no CLion

1. **Abrir o projeto no CLion:**
   - File → Open → Selecionar a pasta do projeto
   - CLion detectará automaticamente o CMakeLists.txt

2. **Configurar o Qt6:**
   - File → Settings → Build, Execution, Deployment → CMake
   - Adicionar nas CMake options: `-DCMAKE_PREFIX_PATH=<caminho_para_qt6>`
   - Exemplo Windows: `-DCMAKE_PREFIX_PATH=C:/Qt/6.7.0/msvc2019_64`
   - Exemplo Linux: `-DCMAKE_PREFIX_PATH=/opt/Qt/6.7.0/gcc_64`

3. **Configurar o compilador (se necessário):**
   - File → Settings → Build, Execution, Deployment → Toolchains
   - Certificar que o compilador C++ está configurado corretamente

4. **Build do projeto:**
   - Build → Build Project
   - Ou usar Ctrl+F9

### Estrutura do Projeto

```
Algo-Analytics/
├── CMakeLists.txt          # Arquivo de configuração do CMake
├── algo_analitics.pro      # Arquivo original do Qt (mantido para compatibilidade)
├── main.cpp                # Ponto de entrada da aplicação
├── mainwindow.cpp          # Implementação da janela principal
├── mainwindow.h            # Header da janela principal
├── mainwindow.ui           # Interface gráfica (Qt Designer)
├── datastruct.h            # Estruturas de dados (Lista, Árvore, Grafo)
└── .gitignore              # Arquivos a serem ignorados pelo Git
```

### Funcionalidades da Aplicação

- **Listas:** Geração e manipulação de listas de inteiros
- **Árvores:** Criação de árvores binárias com nós aleatórios
- **Grafos:** Implementação de grafos ponderados e direcionados
- **Interface Gráfica:** Qt Widgets para interação com o usuário

### Debugging no CLion

1. Configurar breakpoints clicando na margem esquerda do editor
2. Run → Debug (Shift+F9) para iniciar o debug
3. Use o debugger integrado para inspecionar variáveis e controlar execução

### Alternativa: Usando o arquivo .pro

Se preferir usar o arquivo original do Qt:
1. File → Open → Selecionar `algo_analitics.pro`
2. CLion pode importar projetos qmake, mas CMake é recomendado

### Troubleshooting

- **Qt não encontrado:** Verificar se CMAKE_PREFIX_PATH está correto
- **Erros de compilação:** Verificar se o Qt6 está instalado corretamente
- **Problemas com MOC:** Certificar que CMAKE_AUTOMOC está habilitado

### Build via linha de comando (alternativo)

```bash
mkdir build
cd build
cmake .. -DCMAKE_PREFIX_PATH=<caminho_para_qt6>
make  # ou ninja, dependendo do generator
```