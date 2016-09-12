# D&#35; (D-Sharp)
Open-source .NET compiler for D# (d-sharp), a "C#" with simplified syntax.

This is a continuation of the original Proposal: [Radical simplification of the C# syntax](https://github.com/dotnet/roslyn/issues/13731#issuecomment-246209933) (Roslyn issue #13731).
The project is in a very early stage. the syntax of the language has still to be nailed down, before work on a compiler can start.

Instead of long explanations, here an idea of how D# could look:

    using static System.Console

    namespace Example.DSharp // Namespace is a not nesting, thus saving one indentation level.

    class Program
        static void Main(string[] args)
            int a = 10
            int b = 20

            if a == 10
                if b == 20
                    WriteLine("Value of a is 10 and b is 20")
                elsif b > 50
                    WriteLine("Value of a is 10 and b greater than 50")
                else
                    WriteLine("Value of a is 10")
            switch a
                case 0, 1, 2
                    WriteLine("Low number")
                case 3, 4, 5
                    WriteLine("Medium number")
                default
                    WriteLine("Other number")
            while a < 1000
                WriteLine(a)
                a *= 2
            do
                WriteLine(b)
                b *= 2
            until b >= 1000 // Since while would be ambiguous, we use until instead.
            ReadLine()

In [Roslyn issue #13731](https://github.com/dotnet/roslyn/issues/13731#issuecomment-246209933) you can see the corresponding C# code.

Whether the language will be a white-space language or whether it will use some end-symbol for code blocks has yet to be discussed. While experimenting with different end-symbols, I realized that they don't really add information. Is it helpful to see 7 end-braces at the end of a C#-listing? I tried "L" as end-symbol because it looks like a left-lower corner.

    if a == 10
        if b == 20
            WriteLine("Value of a is 10 and b is 20")
        elsif b > 50
            WriteLine("Value of a is 10 and b greater than 50")
        else
            WriteLine("Value of a is 10")
        L
    L
