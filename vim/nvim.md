### line breaks if string is too long
```
%!fmt -s -w 80
```

---

### Preview markdowns .md files in a browser 
Run the command :LazyExtras in Neovim.
Navigate to lang > markdown.
Ensure the extra is enabled (marked with an x). If not, press x to toggle it on, then restart Neovim or run :Lazy sync.

Open .md file and press:
```
<leader>cp (usually Space + c + p)
```
and it should open a new tab in a browser with your markdown file

--- 
### When pyright is complaining with import errors
```
# noqa: E402
```
