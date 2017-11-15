## Ubuntu Commands
* Mingfei Sun
* Created: 2017-11-15
* Updated: 2017-11-15

### Pass command1 output to command2
You can use xargs, with the -t flag xargs will be verbose and prints the commands it executes:
``` bash
./command1 | xargs -t -n1 command2
```
-n1 defines the maximum arguments passed to every call of command2. This will execute:
``` bash
command2 word1
command2 word2
command2 word3
```
If you want all as argument of one call of command2 use that:
``` bash
./command1 | xargs -t command2
```
That calls command2 with 3 arguments:
``` bash
command2 word1 word2 word3
```
[Link](https://serverfault.com/questions/641983/how-to-pass-command-output-as-several-arguments-to-another-command)
