# Follow this tutorial: https://betweentwoparens.com/jenv
## STEP BY STEP
- ### Installing jEnv

        brew install jenv
- ### Check config status

        jenv doctor
    Found error

        [ERROR]	Java binary in path is not in the jenv shims.
        [ERROR]	Please check your path, or try using /path/to/java/home # ...
        [ERROR]	Jenv is not loaded in your zsh
        [ERROR]	To fix : cat eval "$(jenv init -)" >> /Users/# ...

- ### Add jEnv to our PATH.

    1. ZSH shell

            echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.zshrc
            echo 'eval "$(jenv init -)"' >> ~/.zshrc
    2. Bash shell

            echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.bashrc
            echo 'eval "$(jenv init -)"' >> ~/.bashrc
- ### Check config status again

        jenv doctor

    Found 2 error

        [OK]	No JAVA_HOME set
        [ERROR]	Java binary in path is not in the jenv shims.
        [ERROR]	Please check your path, or try using /path/to/java/home #...
        [OK]	Jenv is correctly loaded
    
    Making process

        jenv enable-plugin export
        exec $SHELL -l

    Check status again

        jenv doctor
    
    Show error like bellow

        [OK]	JAVA_HOME variable probably set by jenv PROMPT
        [ERROR]	Java binary in path is not in the jenv shims.
        [ERROR]	Please check your path, or try using /path/to/java/home #...
        [OK]	Jenv is correctly loaded

- ### Add a JDK to jEnv
    check current java jdk in system

        /usr/libexec/java_home -V
    
    result will be like this

        Matching Java Virtual Machines (2):
        13.0.2, x86_64:	"AdoptOpenJDK 13"	/Library/Java/JavaVirtualMachines/adoptopenjdk-13.jdk/Contents/Home
        11.0.6, x86_64:	"AdoptOpenJDK 11"	/Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk/Contents/Home
    
    go ahead and add JDK's to jEnv

        jenv add /Library/Java/JavaVirtualMachines/adoptopenjdk-13.jdk/Contents/Home

    result will be like this

        openjdk64-13.0.2 added
        13.0.2 added
        13.0 added

- ### Set a JDK version via jEnv
    There are two options for this: ```jenv local``` and ```jenv global```.

    example
            
            jenv global 11.0.6
    
    recheck

            java -version

    result will be like this

            openjdk version "11.0.6" 2020-01-14
            OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.6+10)
            OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.6+10, mixed mode)
- ### Uninstalling Jenv

        brew uninstall jenv
    
    Remove the .jenv directory
    
        rm -rf ~/.jenv