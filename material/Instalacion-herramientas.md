# Instalación del entorno de trabajo

**Curso ITH/ML**

**Julio Waissman Vilanova**

## 1. Instalación de git y este repositorio

1. Si tienes Window 10 (2016 o superior), primero instala el [*Subsistema Linux para Windows*](https://www.laptopmag.com/articles/use-bash-shell-windows-10) ([aquí otra guía](https://hackernoon.com/how-to-install-bash-on-windows-10-lqb73yj3), pero hay muchas en internet). Si tienes una versión más viejita de Windows, puedes descargarlo de [este lugar](https://gitforwindows.org). Usuarios de Linux y MacOS ir directamente a su terminal favorita.
2. Realiza el comando `$ git --version` en tu terminal *bash* y si no reconoce el comando, puedes descargar e instalar *git* de [este lugar](https://git-scm.com). 
3. En el MIT desarrollaron una clase que se llama [The Missing Semester of Your CS Education](https://missing.csail.mit.edu). Toda está muy interesante, pero en la [primera sesión](https://missing.csail.mit.edu/2020/course-shell/) enseñan a usar lo básico del *bash* y en la [sesión 6](https://missing.csail.mit.edu/2020/version-control/) explican el uso de *git*. En todas las sesiones nos presumen el pizarronzote y las instalaciones que tiene el MIT para dar clases.
4. Si usas MacOS, te recomiendo probar [iTerm2](https://www.iterm2.com), y en todos los casos yo les recomiendo revisar el uso de [`zsh + oh my zsh`](https://ohmyz.sh). *Zsh* es un *shield* que es mas bonito que *bash* (y casi igual, lo que haces en *bash* se hace de la misma manera en *zsh*). Es fácil buscar posts para tunear la linea de comandos en cualquiera de los sistemas operativos en los que trabajes.
5. Descarga este repositorio en el directorio que tu quieras con el comando  
   ```bash
   $ git clone https://github.com/mcd-unison/ing-caracteristicas.git
   ```

## 2. Instalación de `python`

1. Si ya se tiene la distribución de *Anaconda* instalada, pasar al siguiente paso, si no, instalas la versión mínima *Miniconda* de *python 3.X* con [estas instrucciones](https://docs.conda.io/en/latest/miniconda.html).
2. En la terminal utilizar el comando *conda* para crear un entorno virtual nuevo.
   ```bash
   $ conda env create -n ml-curso
   ```
   o cualquier otro nombre que se le quiera poner al entorno
3. Cada vez que se vaya a utilizar el entorno, utilizar:
   ```bash
   $ conda activate ml-curso
   ```
4. Cuando ya se termine de usar, desactivar el entorno virtual ( y mantener a cada proyecto con su propio entorno virtual)
   ```bash
   $ conda deactivate
   ```
5. Cuando se instale todo lo que se requiera de librerías y se tenga un entorno funcionando, puedes guardar la configuración y exportarla para instalar un entorno idéntico en otra máquina, utilizando:
   ```bash
   $ conda env export -f requirements.yml
   ```
6. Cuando quieras instalar el entorno en otro lado, simplemente con contar con el archivo `requirements.yml`, en el mismo directorio donde se encuentra se puede realizar con:
   ```bash
   $ conda env create -f requirements.yml -n curso-ml
   ```
   o cualquier otro nombre que desees poner.


## 3. Librerías necesarias

1. Dentro de tu entorno virtual, instala las librerías para cálculo científico, y para graficación con los siguientes comandos:
   ```bash
   $ conda install numpy
   $ conda install matplotlib
   ```
2. Ahora hay que instalar la librería que permite manejar en forma eficiente conuntos de datos en forma de DataFrames (pandas) con el siguiente comando:
   ```bash
   $ conda install pandas
   ```
3. Para usar las *notebooks de jupyter es necesario instalarlo:
   ```bash
   $ conda install ipython
   $ conda install jupyter
   $ conda install jupyterlab
   ```
4. Por último instala la librería de aprendizaje automñatico:
   ```bash
   $ conda install scikit-learn
   ```

