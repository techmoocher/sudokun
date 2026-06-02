# sudokun

**sudokun** is an ncurses-based sudoku game for CLI. Sudoku's long been my favorite activities to entertain. 
However, sometimes, I simply don't want to leave the terminal. That's why **sudokun** was born!

Big shout-out to **[jubalh/nudoku](https://github.com/jubalh/nudoku.git)** for huge inspiration!!!

## Installation

nudoku is easily installable via many package managers.

[![Packaging status](https://repology.org/badge/tiny-repos/nudoku.svg)](https://repology.org/project/nudoku/versions)

**Dependencies:**
- ncurses
- cairo *(optional)* ***(required if using PDF/PNG export)**

### Building from source

Get the latest `.tar.xz` [release](https://github.com/jubalh/nudoku/releases) and extract it. 
Then run:

```bash
./configure
make
./src/sudokun
```

You can also go by the git version:

```bash
git clone https://github.com/techmoocher/sudokun.git
cd sudokun
autoreconf -i
./configure
make
./src/sudokun
```

> Use `make -DDEBUG` to see the debug output.

Add `-DDEBUG` to `make` to have some debug output.

nudoku can also output sudokus in PDF and PNG format (see `man nudoku` -p/-i/-n).
You need to have cairo installed and configure with:

```sh
./configure --enable-cairo
```

## Usage

For normal interactive GUI run `nudoku`.
To print two PDF pages with 8 hard sudokus run `nudoku -p riddle.pdf -n 8 -d hard`.
To get a PNG with an easy sudoku run `nudoku -i sudoku.png -d easy`.
See `man nudoku` to learn more.

## I18n ##

For i18n support, you need to set the `LANGUAGE` variable:

```sh
export LANGUAGE=lang    # Replace lang with your desired translation
```

> Learn more about the list supported languages in [`po/LINGUAS`](./po/LINGUAS).

## Contributing

If you add any changes to source code, make sure to update potfiles in the `po/` directory:

```bash
cd path/to/your/sudokun/dir/po      # Replace the destination with your actual path
make update-po
```

### Translation

If you intend to add/update the translation, please follow the guidelines below:

1. Fork this repository and create a new git branch with language abbreviation as a name 
(e.g. `vi` for Vietnamese, `es` for Español, etc.):

```bash
git clone https://github.com/YOUR_USERNAME/sudokun.git
cd sudokun
git checkout -b vi
```

> Replace `YOUR_USERNAME` with your actual username.

2. If you want to add a new translation, add language to `po/LINGUAS` and create `.po` file:

> Skip this step if you intend to update an existing language.

```bash
echo vi >> po/LINGUAS && cp po/sudokun.pot po/vi.po
```

3. Replace uppercased placeholders at the head of the file with your contact information. 
Then, add/update translation(s) for, if possible, all the `msgid`.

4. Check your `.po` file with `msgfmt` for any errors:

```bash
msgfmt vi.po    # Expecting no output
```

5. Push your branch to remote and create a PR:

```bash
git push origin es
```
