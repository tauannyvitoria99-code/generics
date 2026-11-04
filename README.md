# Trabalho III – Generics em Java (POO II)

Sistema de depósitos de uma empresa de logística, refatorado de `Object`/cast para **Generics**.

## Versão do Java
- Desenvolvido e testado com **OpenJDK 21** (21.0.10).
- Compatível com **JDK 17 ou superior** (usa `var`, `Optional`, `List.copyOf` e `String.isBlank`).

## Estrutura
```
src/antes/       código ORIGINAL (reconstruído): Deposito com Object, retorna null
src/logistica/   solução com Generics: Produto, Eletronico, Alimento, Vestuario,
                 Deposito<T extends Produto>, Operacoes (métodos genéricos/wildcards), Main
src/exemplos/    exemplos executáveis da Parte I (SemGenerics, ComGenerics)
teste/           Testes.java (sem JUnit, roda só com o JDK)
evidencias/      .java que NÃO compilam de propósito + mensagens do compilador e saídas
```

## Compilar (Linux/macOS)
```
mkdir -p out
javac -encoding UTF-8 -d out $(find src teste -name "*.java")
```

## Compilar (Windows – PowerShell)
```
mkdir out
javac -encoding UTF-8 -d out (Get-ChildItem src,teste -Recurse -Filter *.java).FullName
```

## Executar
```
java -cp out logistica.Main          # versão genérica (solução)
java -cp out antes.MainAntes         # código original (mostra ClassCastException e null)
java -cp out exemplos.SemGenerics    # Parte I, 1c: ClassCastException sem Generics
java -cp out exemplos.ComGenerics    # Parte I, 2 e 3
java -cp out Testes                  # testes
```
No Windows, para acentuação correta no terminal, rode antes `chcp 65001`.

## Evidências de erro de compilação
Cada arquivo de `evidencias/*.java` contém uma linha inválida de propósito. Para ver a mensagem:
```
javac -encoding UTF-8 -cp out -d /tmp evidencias/ErroAlimentoEmEletronicos.java
```
As mensagens já capturadas estão em `evidencias/erros-de-compilacao.txt`
(o idioma da mensagem depende do idioma do seu `javac`).
