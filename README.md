Creator Executable 🚀

GUI para gerar executáveis multiplataforma a partir de projetos Python

https://img.shields.io/badge/Python-3.6+-blue.svg
https://img.shields.io/badge/Platform-Linux%2520%257C%2520Windows-lightgrey.svg
https://img.shields.io/badge/License-MIT-green.svg

Uma aplicação GUI intuitiva que permite criar executáveis para Linux, Windows (via Wine), AppImage, pacotes .deb e instaladores NSIS a partir do seu código Python.

✨ Características
🐧 Executável Linux - Via PyInstaller

🍷 Executável Windows - Via Wine + PyInstaller

📦 AppImage - Executável portável para Linux

📦 Pacote .deb - Para distribuições baseadas em Debian/Ubuntu

💿 Instalador NSIS - Para distribuição Windows

🎨 Interface moderna - Tema escuro com cores agradáveis

🔧 Detecção automática - Detecta entrypoints e dependências

📋 Log detalhado - Visualização em tempo real do processo de build

📋 Pré-requisitos
Dependências básicas
bash
# Python 3.6 ou superior
python3 --version

# TKinter (geralmente vem com Python)
sudo apt install python3-tk  # Debian/Ubuntu/MX Linux
Dependências para builds específicos
Build	Dependência	Comando de instalação
Todos	PyInstaller	pip install pyinstaller
Windows	Wine	sudo apt install wine wine32
AppImage	appimagetool	Download aqui
.deb	dpkg-deb	sudo apt install dpkg-dev
NSIS	makensis	sudo apt install nsis
🚀 Instalação
Clone ou baixe o script:

bash
git clone <seu-repositorio>
# ou baixe o arquivo creator_executable.py
Torne executável (opcional):

bash
chmod +x creator_executable.py
Execute:

bash
python3 creator_executable.py
# ou
./creator_executable.py
🎮 Como usar
Passo a passo:
Selecione o projeto: Clique em "📂 Selecionar" e escolha a pasta do seu projeto Python

Verifique as dependências: A GUI mostrará quais ferramentas estão disponíveis

Escolha o tipo de build:

🐧 Executável Linux: Gera um binário único para Linux

🍷 .exe via Wine: Gera executável Windows usando Wine

📦 AppImage: Cria AppImage portável

📦 Pacote .deb: Gera pacote Debian/Ubuntu

💿 Instalador NSIS: Cria instalador Windows (requer arquivo .nsi)

Estrutura do projeto recomendada:
text
meu_projeto/
├── main.py              # Arquivo principal (ou app.py, __main__.py)
├── requirements.txt     # Dependências Python (opcional)
├── packaging/
│   └── nsis/
│       └── installer.nsi  # Script NSIS para instalador Windows
└── ... outros arquivos ...
🔧 Configuração detalhada das dependências
🍷 Wine (para builds Windows)
bash
# Instalação completa do Wine
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install wine wine32 wine64

# Configurar Wine pela primeira vez
winecfg

# Instalar Python no Wine
wget https://www.python.org/ftp/python/3.9.13/python-3.9.13-amd64.exe
wine python-3.9.13-amd64.exe

# Instalar PyInstaller no Wine
wine pip install pyinstaller
📦 AppImageTool
bash
# Baixar e instalar
wget https://github.com/AppImage/AppImageKit/releases/download/continuous/appimagetool-x86_64.AppImage
chmod +x appimagetool-x86_64.AppImage
sudo mv appimagetool-x86_64.AppImage /usr/local/bin/appimagetool
💿 NSIS (Nullsoft Scriptable Install System)
bash
# Instalação
sudo apt install nsis

# Para instaladores personalizados, crie:
mkdir -p packaging/nsis
# Edite packaging/nsis/installer.nsi com seu script
🐛 Solução de problemas
Erro comum: "wine: could not load kernel32.dll"
bash
# Recriar o prefix do Wine
rm -rf ~/.wine
WINEARCH=win64 WINEPREFIX=~/.wine winecfg
Erro: "PyInstaller not found"
bash
pip install --user pyinstaller
# ou
sudo pip install pyinstaller
Erro: Dependências faltando no build
Verifique se todas as dependências do seu projeto estão no requirements.txt

O PyInstaller pode precisar de hooks para algumas bibliotecas

Build Windows não funciona
Certifique-se que o Wine está configurado corretamente

Verifique se o Python está instalado no prefix do Wine

Teste manualmente: wine python --version

📝 Notas importantes
Para builds Windows via Wine:
É necessário ter o Wine configurado com Python instalado

O processo é mais lento pois roda em camada de compatibilidade

Para melhor performance, considere builds Windows em uma máquina Windows real

Para AppImage:
Gera um executável auto-contido que roda na maioria das distribuições Linux

Não requer instalação, basta dar permissão de execução e rodar

Para pacotes .deb:
Gera um pacote básico para distribuição

Para pacotes mais complexos, edite manualmente o arquivo DEBIAN/control

🛠️ Desenvolvimento
O código é modular e organizado em classes:

CreatorExecutableApp: Classe principal da GUI

safe_run(): Função utilitária para execução segura de comandos

Threads separadas para não travar a interface durante builds

Estrutura do código:
python
# Cores e tema
COLORS = { ... }

# Utilitários
def which(cmd): ...
def safe_run(cmd_list, ...): ...
def ensure_build_folders(...): ...

# Classe principal
class CreatorExecutableApp:
    def _build_linux_impl(self): ...
    def _build_wine_impl(self): ...
    def _build_appimage_impl(self): ...
    # ... outros métodos de build
📄 Licença
MIT License - sinta-se livre para usar e modificar.

🤝 Contribuições
Contribuições são bem-vindas! Sinta-se à vontade para:

Reportar bugs

Sugerir novas funcionalidades

Enviar pull requests

📞 Suporte
Se encontrar problemas:

Confirme que todas as dependências estão instaladas

Verifique os logs detalhados na própria aplicação

Happy building! 🎉
