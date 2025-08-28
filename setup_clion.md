# CLion Setup para o Projeto Algo-Analytics (Qt6)

Este guia orienta qualquer pessoa a configurar o ambiente de desenvolvimento para o projeto Algo-Analytics usando o CLion e Qt6 em sistemas Linux (Debian/Ubuntu).

---

## 1. Clonando o repositório

```sh
git clone https://github.com/Ernesto-Alves67/Algo-Analytics.git
cd Algo-Analytics
```

---

## 2. Instalando dependências no Linux (Debian/Ubuntu)

Certifique-se de que você tem permissões de administrador (sudo):

```sh
sudo apt update
sudo apt install cmake build-essential git mlocate
sudo apt install qt6-base-dev qt6-base-dev-tools
```

### Ferramentas extras para localização de arquivos

```sh
sudo apt install mlocate
sudo updatedb
```

---

## 3. Descobrindo o caminho do Qt6Config.cmake

```sh
locate Qt6Config.cmake
```
O caminho padrão geralmente é:
```
/usr/lib/x86_64-linux-gnu/cmake/Qt6/Qt6Config.cmake
```

---

## 4. Abrindo o projeto no CLion

- Abra o CLion.
- Clique em **Open** e selecione a pasta do projeto (`Algo-Analytics`).

---

## 5. Configurando o Qt6 no CLion

- Acesse **File > Settings > Build, Execution, Deployment > CMake**.
- No campo **CMake options**, acrescente (substitua pelo caminho que você encontrou no comando `locate`, se for diferente):

  ```
  -DCMAKE_PREFIX_PATH=/usr/lib/x86_64-linux-gnu/cmake/Qt6
  ```

- Exemplo de campo completo (para Debug):

  ```
  -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug -DCMAKE_PREFIX_PATH=/usr/lib/x86_64-linux-gnu/cmake/Qt6
  ```

- Clique em **Apply** e depois em **OK**.

---

## 6. Compilando e rodando

- O CLion deve recarregar o projeto e configurar o CMake automaticamente.
- Use o botão de build ou pressione **Shift+F10** para compilar e rodar o projeto.

---

## 7. Possíveis erros e soluções

- **Erro: CMake não encontra Qt6**
    - Garanta que o caminho em `CMAKE_PREFIX_PATH` está correto.
    - Verifique se todos os pacotes Qt6 necessários estão instalados.

- **Erro ao compilar por falta de dependências**
    - Confira se todos os pacotes da seção 2 foram instalados.

- **Qt5 em vez de Qt6**
    - O projeto foi configurado para Qt6. Qt5 não é suportado oficialmente neste guia.

---

## 8. Outras plataformas (Windows/macOS)

- Instale o Qt6 via [Qt Online Installer](https://www.qt.io/download).
- Instale o CLion normalmente.
- Localize o caminho do Qt6Config.cmake na sua instalação Qt6 e configure o CMake da mesma forma.

---

## 9. Atualizando dependências

Sempre que atualizar dependências do projeto, repita os comandos de instalação, se necessário.

---

## 10. Dúvidas ou problemas

Abra uma [Issue no GitHub](https://github.com/Ernesto-Alves67/Algo-Analytics/issues) com informações detalhadas sobre seu erro.

---