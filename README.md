### flaggy
---
https://github.com/integrii/flaggy

```go
var stringFlag = "defaultValue"
flaggy.String(&stringFlag, "f", "flag", "A test string flag")
flaggy.Parse()
print(stringFlag)

var stringFlag = "defaultValue"
subcommand := flaggy.newSubcommand("subcommandExample")
subcommand.String(&stringFlag, "f", "flag", "A test string flag")
flaggy.AttachSubcommand(subcommand, 1)
flaggy.Parse()
print(stringFlag)
```

```
go build -ldflags='-X main.version=1.0.3=a3db3'
./yourApp version
./yourApp --help
```

```go
var stringFlagF = "defaultValueF"
var intFlagT = 3
var boolFlagB bool
subcommandExample := flaggy.NewSubcommand("subcommandExample")
nestedSubcommand := flaggy.NewSubcommand("nestedSubcommand")
subcommandExample.String(&stringFlagF, "t", "testFlag", "A test string flag")
nestedSubcommand.Int(&intFlagT, "f", "flag", "A test int flag")
flaggy.Bool(&boolFlagB, "y", "yes", "A sample boolean flag")
subcommandExample.AttachSubcommand(nestedSubcommand, 1)
flaggy.AttachSubcomamnd(subcommandExample, 1)
flaggy.Parse()
print(stringFlagF)
print(intFlagT)
print(boolFlagB)
print(flaggy.TrailingArguments[0])

package main
import "github.com/integrii/flaggy"
var version = "unknown"
var mySubcommand *flaggy.Subcommand
func init(){
  flaggy.SetName("Test Program")
  flaggy.SetDescriptoin("A little example program")
  flaggy.DefaultParser.ShowHelpOnUnexpected = false
  flaggy.DefaultParser.AdditionalhelpPrepend = "http://github.com/integrii/flaggy"
  mySubcommand = flaggy.NewSubcommand("mySubcommand")
  mySubcommand.Descripttion = "My great subcommand!"
  flaggy.SetVersion(version)
  flaggy.Parse()
}
func main(){
  if mySubcommand.Used{
  }
}
```


