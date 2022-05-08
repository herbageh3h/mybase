# FAQ

## How to switch between java version 8, 11 and 17 on mac?

```
/Users/jeffhuang/Library/Java/JavaVirtualMachines/temurin-17.0.3/Contents/Home
/Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk/Contents/Home
/Users/jeffhuang/Library/Java/JavaVirtualMachines/temurin-1.8.0_322/Contents/Home
```

Add jdk home to path in your .zshrc.
```
export PATH="/Users/jeffhuang/Library/Java/JavaVirtualMachines/temurin-17.0.3/Contents/Home:$PATH"
```

## Which java version should i use?

LTS versions are java8, java11 and java17.

If not for work, just use java17.

If for work, you should use java8 for compatibility.
