# On assertions

Answer the following questions:

1. The following assertion fails `assertTrue(3 * .4 == 1.2)`. Explain why and describe how this type of check should be done.

2. What is the difference between `assertEquals` and `assertSame`? Show scenarios where they produce the same result and scenarios where they do not produce the same result.

3. In classes we saw that `fail` is useful to mark code that should not be executed because an exception was expected before. Find other uses for `fail`. Explain the use case and add an example.

4. In JUnit 4, an exception was expected using the `@Test` annotation, while in JUnit 5 there is a special assertion method `assertThrows`. In your opinion, what are the advantages of this new way of checking expected exceptions?

## Answer

1. C'est à cause du fait de l'inexactitude des nombres de type float qui ne peuvent pas être représentés exactement en binaire. Ils ont des très petites erreurs d'imprécision qui font échouer l'assertion. En réalité 3 * .4 vaut quelque chose du genre 1.20000000000001 et cela suffit à faire échouer l'assertion. La solution pour ce problème est d'utiliser une marge d'erreur, soit par une valeur espilon qui passée en paramètre de certaines assertions autorise une marge d'erreur, soit en utilisant directement des assertions faites pour ce genre de cas (comme assertAlmostEqual).

2. AssertEqual vérifie l'identité alors que AssertSame vérifie l'égalité. L'identité correspond à une référence en mémoire alors que l'égalite correspond au contenu, à la donnée elle même. C'est la même chose que la différence entre equals() et == en Java.
