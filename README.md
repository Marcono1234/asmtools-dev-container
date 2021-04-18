# Unofficial OpenJDK AsmTools Devcontainer
Unofficial Visual Studio Code [Devcontainer](https://code.visualstudio.com/docs/remote/containers-tutorial) for usage of OpenJDK's [AsmTools](https://wiki.openjdk.java.net/display/CodeTools/asmtools).

The AsmTools are built from the latest version of the [source code](https://github.com/openjdk/asmtools).

# Usage
## Prerequisites
1. [Docker Desktop](https://www.docker.com/products/docker-desktop)
2. [Visual Studio Code](https://code.visualstudio.com/)
3. [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) VSCode extension

Also have a look at the VSCode [Containers Tutorial](https://code.visualstudio.com/docs/remote/containers-tutorial).

## Starting the remote container
1. Open VSCode
2. Start Docker Desktop (and wait until it is fully started)
3. Start the container
    - If you already have this folder open in VScode, use the "Remote-Containers: Reopen in Container" command
    - Otherwise, use the "Remote-Containers: Open Folder in Container..." command and select this folder
4. Wait for the container build to finish

## Tools
The container has the JDK binaries on the `PATH`, so tools like `javac` and similar can be used.  
Have a look at the [JDK Tools Reference](https://docs.oracle.com/en/java/javase/11/tools/tools-and-command-reference.html) for more information about their usage.

Additionally the `PATH` contains convenience scripts for invoking the AsmTools. For example:
```bash
jasm MyClass.jasm
```

Will run:
```bash
java -jar asmtools.jar jasm MyClass.jasm
```

Supported AsmTools are:
- `jasm`
- `jdis`
- `jcoder`
- `jdec`
- `jcdec`

See the [AsmTools User Guide](https://wiki.openjdk.java.net/display/CodeTools/AsmTools+User+Guide) for information on their usage.
