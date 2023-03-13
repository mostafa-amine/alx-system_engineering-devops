# 0x02-shell_redirections

## tr
- The `tr` command in linux is used to translate or delete characters. It can be used to replace or remove characters from a text file or Input stream.
- For example this command will replace all occurences of "o" with the number "0" in the input string "hello world"
```bash
echo "hello world" | tr "o" "0"
```
- This command will convert the lowercase letters to uppercase letters.
```bash
echo "Hello World" | tr  [[:lower:]] [[:upper:]]
```
- we can also delete characters using -d option 
```shell
echo "Hello World" | tr -d o
# Hell Wrld
```