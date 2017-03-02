# Bash / Shell Scripting

<!-- vim-markdown-toc GFM -->
* [Convenience functions](#convenience-functions)
    * [Try again](#try-again)
* [Tips](#tips)
    * [Set default values / check for existence of a variable](#set-default-values--check-for-existence-of-a-variable)
    * [Trim whitespace from string](#trim-whitespace-from-string)
    * [Replacing inside a string](#replacing-inside-a-string)
    * [Substring](#substring)
    * [Arrays](#arrays)
    * [Multiline strings](#multiline-strings)
* [Reading material](#reading-material)

<!-- vim-markdown-toc -->

## Convenience functions

### Try again

```bash
try_again() {
    set +e
    declare _cmd="$1" _counter="$2"

    # Run the _cmd for _counter times
    while [ $_counter -gt 0 ]; do
        eval $_cmd
        if [ $? == 0 ]; then
            return
        fi
        let _counter=${_counter}-1
        sleep 1
    done

    # XXX: Exit if it didn't succeed after all
    # the tries
    if [ $? != 0 ]; then
        exit 1
    fi

    set -e
}
```

## Tips

### Set default values / check for existence of a variable

```bash
echo ${parameter:-word}             # word
parameter=xyz
echo ${parameter:-word}             # xyz
```

### Trim whitespace from string

```bash
echo 'test string' | tr -d ' '  # teststring
```

### Replacing inside a string

```bash
str='test string'
echo ${str/test/foo}        # foo string
```

### Substring

```bash
str='test string'
echo ${str:5}               # string
echo ${str:5:3}             # str
```

** substrings by pattern **

```bash
${variable%pattern}         # Trim the shortest match from the end
${variable%%pattern}        # Trim the longest match from the end
${variable##pattern}        # Trim the longest match from the beginning
${variable#pattern}         # Trim the shortest match from the beginning

# Example:
filename='ubuntu_16_04.tar.gz'
echo ${filename%%.*}        # ubuntu_16_04
echo ${filename%.*}         # ubuntu_16_04.tar
echo ${filename#*.}         # tar.gz
echo ${filename##*.}        # gz
```

### Arrays

```bash
# notice the space
declare -a arr=(element1 element2 element3 'element 4' 'element 5')

# iterate over array
for element in ${arr[@]}; do
    echo $element
done

# No of items in or length of the array
n_elements=${#arr[@]}

# sub array
echo "${arr[@]:3:2}" # prints element3 element 4

# remove/delete an element from array
unset arr[3]
```

### Multiline strings

** String assignment **

```bash
str=$(cat << EOF
line 1
line 2
line 3
EOF
)
```

** Writing to a file **

```bash
cat > /path/to/file << EOF
line 1
line 2
line 3
EOF
```

** Piping to a command **

```bash
cat << EOF | grep 'b'
foo
bar
baz
EOF
```

## Reading material

- [Shell Parameter Expansion](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion)
