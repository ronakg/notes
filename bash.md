# Bash / Shell Scripting

## Tips

**Multiline strings and writing to files**

```bash
str=$(cat << EOF
line 1
line 2
line 3
EOF
)
```

```bash
cat > /path/to/file << EOF
line 1
line 2
line 3
EOF
```
