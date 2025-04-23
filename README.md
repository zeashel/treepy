# tree.py

Python script to print the structure of a certain directory and its subdirectories in a tree-esque format using recursion.

## Dependencies

Python 3.9.6 or higher

## Installation

### Using Command Line (Linux/MacOS/UNIX-like)

Assuming you have ~/bin as a PATH environment variable and python 3 installed, run this in your terminal:
```bash
git clone https://github.com/zhrsh/treepy.git
cd treepy
./install.sh
```

You can add an argument to ./install.sh if a different installation path is needed.
```bash
git clone https://github.com/zhrsh/treepy.git
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

## Example

Using tree on my portfolio project:

```plaintext
my-portfolio/
├── README.md
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── bloodmoon.js
│   ├── img/
│   │   ├── paralax-hq.jpg
│   │   ├── faviconic.png
│   │   ├── pfp-sample.jpg
│   │   ├── paralax-lq.jpg
│   │   ├── sample6.jpg
│   │   ├── sample5.jpg
│   │   ├── preview.gif
│   │   ├── sample4.jpg
│   │   ├── sample1.jpg
│   │   ├── sample3.jpg
│   │   └── sample2.jpg
│   └── fonts/
│       ├── ebgaramond-italic-variablefont_wght.woff
│       ├── meyne_textur.ttf
│       ├── EBGaramond-SemiBoldItalic.woff2
│       ├── EBGaramond-Regular.woff2
│       ├── EBGaramond-MediumItalic.woff2
│       ├── EBGaramond-Medium.woff2
│       ├── ebgaramond-variablefont_wght.woff
│       ├── EBGaramond-SemiBold.woff2
│       ├── UnifrakturMaguntia-webfont.woff
│       └── EBGaramond-Italic.woff2
└── pages/
    └── index.html
```