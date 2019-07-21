# Michael Ernst - University of Washington - Implement a type system in 40 minutes

checkerframework.org

Optionals - could have an Option(null) or Optional.empty or null, so we're basically doubling the number of exceptions we can get when we use Optionals

How to know at compile time - before run time - things like nullpointerexceptions?

typechecker tool being shown is a verification tool, not error remover

Verify all cases handled

We're basically just following chapter 31 of checkerframework.org/manual

Rules:
* Before code, write user manual
* Add type qualifiers and hierarchy (like @MaybePresent and @Present on optionals)

Showed how you can add annotations inside the jdk and that you can improve the error messages you get back, apparently

Can modify "isPresent"/"isInstanceOf" to return value of thing as the requested type if result of check inside function is true

Looks like you could use the checkerframework tool out of the box without having to modify the jdk yourself.  Apparently Google uses it.