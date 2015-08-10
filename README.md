## Split line into array

This loop iterates over lines in `.zsh_named_dirs` and splits at space character, into the array `mapping`.

```zsh
setopt sh_wordsplit

while read line; do
    mapping=(${(ps: :)${line}}) # split line at space
    echo "$mapping[1] $mapping[2]"
    hash -d "$mapping[1]"="$mapping[2]"
done < <(cat ~/.zsh_named_dirs)

unsetopt sh_wordsplit
```
