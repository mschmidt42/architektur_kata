# README

```
data = """\
... all cata text
"""

def count = 0
def fout = new File("dummy.txt")
data.eachLine { line ->
   if( line =~ "^[0-9].*" ) {
      count++
      def fname = sprintf("doc/kata_%02d.adoc", count)
      fout = new File(fname)
      fout.text = ""
      fout << "[[section-kata-$count]]\n"
      fout << "== "
   }
   if(line.startsWith("        ")){
      fout << "**"
   } else    if(line.startsWith("    ")){
      fout << "*"
   }
   fout << "$line\n"
}
```
