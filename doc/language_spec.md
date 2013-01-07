Cy Language Spec (WIP)
======================

Function Declaration
--------------------


func len(nil) = 0
   | len(x :: xs) = len(xs) + 1

func sum(nil) = 0
   | sum(x Number :: xs) = x + sum(xs)

func size(nil) = 0
   | size(Leaf { x }) = 1
   | size(Tree { left: a, right: b }) = 1 + size(a) + size(b)


Pattern Match
-------------

func prettyPrint(t Tree, indent int) =
    switch t {
    case nil: indent + "-" + "\n"
    case Leaf { x }: indent + x.String + "\n"
    case Tree { value: x, left: a, right: b }:
        indent + x.String + "\n" +
        prettyPrint(a, indent + 4) +
        prettyPrint(b, indent + 4)
    }
