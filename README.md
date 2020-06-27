# Como instalar java (Oracle) no debian

### 1 - Download do JDK

Faça o download da versão desejada em:
https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html

Obs: Baixa o arquivo com a descrição "Linux x64 Compressed Archive"

### 2 - Crie o seguinte diretório
```
sudo mkdir -p /usr/lib/jvm
```

### 3 - Extrair arquivo JDK

Vá até o diretório em que o JDK foi baixado e rode o seguinte comando substituindo <downloaded_jdk> pelo no do arquivo baixado
```
sudo tar zxvf <downloaded_jdk>.tar.gz -C /usr/lib/jvm
```

### 4 - Instalar Java
Para instalar o java rode o comando a seguir no terminal substituindo <jdk> pelo nome completo do diretório da versão do jdk que deseja instalar.
```
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/<jdk>/bin/java" 1
```

### 5 - Setar JDK como default
Para setar o JDK como default na máquina executamos o comando a seguir no terminal substituindo <jdk> pelo nome do diretório completo da versão do JDK que deseja tornar default

```
sudo update-alternatives --set java /usr/lib/jvm/<jdk>/bin/java
```

### 6 - Exportando variáveis de ambiente
Precisamos exportar a variável de ambiente JAVA_HOME para que tudo funcione perfeitamente.
```
export JAVA_HOME=/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.131.x86_64
export PATH=$JAVA_HOME/bin:$PATH
```
Você pode adicionar também as linhas acima no arquivo .bashrc ou .profile

### 7 - Verificando instalação
Para verificar se a instalação foi bem sucedida, execute o comando a seguir no seu terminal.

```
java -version
```
Veja se o seguinte resultado é mostrado
```
java version "1.8.0_251"
Java(TM) SE Runtime Environment (build 1.8.0_251-b08)
Java HotSpot(TM) 64-Bit Server VM (build 25.251-b08, mixed mode)
```

Em seguida temos que ver se o javac também está instalado corretamente, para isso digite:
```
javac -version
```
Como resultado deve ser mostrado no terminal a versão do javac da seguinte forma:
```
javac 1.8.0_251
```