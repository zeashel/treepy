# tree.py

A small python script to recursively print the structure of the current working directory (or any directory) and its subdirectories as a file tree.

<img src="assets/img/example.png" width=500>

## Dependencies

Python 3.9.6 or higher

## Installation

### Using Command Line (Linux/MacOS)

Assuming you have ~/bin as a PATH environment variable and python 3 installed, run this in your terminal:
```bash
git clone https://github.com/zeashel/treepy.git
cd treepy
./install.sh
```

You can add an argument to ./install.sh if a different installation path is needed.
```bash
git clone https://github.com/zeashel/treepy.git
cd treepy
./install.sh DIFFERENT/INSTALL/PATH
```

### Manual installation

Install from the releases page, then drag and drop the `tree` file into a directory registered in your PATH. Tip: run `echo $PATH` to view said directories.

## Usage

### Print the structure of the current working directory

```bash
tree
```

### Print the structure of a certain directory

```bash
tree ~/Projects/example/directory
```

### Include dotfiles
By default, tree ignores dotfiles. Use `-a` or `--all` flag to include them.

```bash
tree -a
```

```bash
tree ~/Projects/example/directory --all
```

### Subdirectory depth
You can specifiy how many subdirectories you want to recursively print by using `-d` or `--depth` followed by an integer. By default, it is limited to 10, but you can specify any integer you want to display more.

```bash
tree -d 3 # only print subdirectories that are no more than 3 directories deep
```

```bash
tree --depth 1 # similar to ls command
```

The [examples](#using-tree--d-0) probably explain this better.

### Formatting (experimental)

You can set one or more ANSI SGR arguments (integers 0–255) to apply to directory names after the `--directory-format` option. Examples: 0 = none, 1 = bold, 2 = dim, 31 = red fg, 41 red bg, etc.

See the [wikipedia page on ANSI escape code](https://en.wikipedia.org/wiki/ANSI\_escape\_code#Select\_Graphic\_Rendition\_parameters) for more information.

```bash
tree --directory-format 1 # bold
```

Multiple values allowed (space-separated)

```bash
tree --directory-format 1 31 4 # bold, red, underline
```

It's also possible to print [xterm256 colors](https://en.wikipedia.org/wiki/ANSI_escape_code#8-bit) or [true color](https://en.wikipedia.org/wiki/ANSI_escape_code#24-bit) as long as your terminal supports it.

8-bit/xterm256 `Red1` foreground (`\033[38;5;196m`):

```bash
tree --directory-format 38 5 196
```

True color `#ff5f5f` `rgb(255,95,95)` foreground (`\033[38;2;255;95;95m`):

```bash
tree --directory-format 38 2 255 95 95
```

Note that not many terminals support true color.

### Verbose

Use the `--verbose` option to view the exact ANSI escape code your input produces

```bash
tree --directory-format 1 31 4 -v
```

Output: 

```plaintext
args.all: False
args.max_depth: 10
args.directory_format: [1, 31, 4]
ansi_parse(args.directory_format): '\x1b[1;31;4m'

...
```

### Saving into a file

Tree only outputs to the stdout. Use output redirection to save to a file.

```bash
tree > tree.txt
```

This saves the output to `tree.txt` instead of displaying it on the terminal. By default, ANSI escape codes (colors) are stripped when output is redirected to a file to ensure readability.

To force color output even when redirecting to a file, use the `--color-force` flag:

```bash
tree --color-force > tree_color.txt
```

## Examples

### Basic usage

Using just `tree`:

```plaintext
my-portfolio/
├─╴README.md
├─╴assets/
│  ├─╴css/
│  │  └─╴style.css
│  ├─╴js/
│  │  └─╴bloodmoon.js
│  ├─╴img/
│  │  ├─╴sample6.jpg
│  │  ├─╴sample5.jpg
│  │  ├─╴sample4.jpg
│  │  ├─╴sample1.jpg
│  │  ├─╴sample3.jpg
│  │  └─╴sample2.jpg
│  └─╴fonts/
│     ├─╴ebgaramond-italic-variablefont_wght.woff
│     ├─╴meyne_textur.ttf
│     └─╴ebgaramond-variablefont_wght.woff
└─╴pages/
    └─╴index.html
```

### Using `tree -d 0`
Limits the subdirectory depth to 0 without including dotfiles.

```plaintext
my-portfolio/
```

`-d 0` basically just shows the current working directory name.

### Using `tree -d 1`
Limits the subdirectory depth to 1 without including dotfiles.
```plaintext
my-portfolio/
├─╴README.md
├─╴assets/
└─╴pages/
```

### Using `tree -d 2`
Limits the subdirectory depth to 2 without including dotfiles.
```plaintext
my-portfolio/
├─╴README.md
├─╴assets/
│  ├─╴css/
│  ├─╴js/
│  ├─╴img/
│  └─╴fonts/
└─╴pages/
   └─╴index.html
```

### Using `tree -a -d 2`

This includes dotfiles and limits the subdirectory depth to 2

```plaintext
my-portfolio/
├─╴.DS_Store
├─╴README.md
├─╴.gitignore
├─╴.git/
│  ├─╴.DS_Store
│  └─╴FETCH_HEAD
├─╴assets/
│  ├─╴css/
│  ├─╴js/
│  ├─╴img/
│  └─╴fonts/
└─╴pages/
   └─╴index.html
```