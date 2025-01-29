# Geral

Estudos feitos a partir de um curso introdutório da linguagem.

O material do curso fica na plataforma, junto com os exercícios.

# Instalando o compilador

A instalação segue o passo a passo publicado na página oficial do projeto.

# Rodando um programa

Tomando como exemplo o arquivo `primeiro.kt`:

```
kotlinc -include-runtime primeiro.kt -d primeiro.jar
java -jar primeiro.jar
```

**Atenção**: quando a geração do pacote dá certo, o compilador não imprime nada. Silêncio ali significa sucesso, não erro.

# Funções privadas

É possível ter função privada fora de qualquer classe. Veja o conteúdo dos arquivos `principal.kt` e `auxiliar.kt`.

`principal.kt`:
```kotlin
private fun greet() {
    println("Olá")
}

fun main() {
    greet()
    hi()
    greet()
}
```

`auxiliar.kt`:
```kotlin
fun hi() {
    println("Oi")
}
```

A função do arquivo auxiliar fica acessível no principal desde que os dois entrem na geração do pacote:

```sh
kotlinc -include-runtime principal.kt auxiliar.kt -d principal.jar
```

E para executar:

```sh
java -jar principal.jar
```

Mas se você colocar o modificador de visibilidade privada na função do arquivo auxiliar, o código do outro arquivo deixa de enxergá-la e a compilação falha.

Uma observação: só pode existir uma função de entrada considerando os dois arquivos.

- [ ] Anotacao pessoal, sem relacao direta com o restante do texto.