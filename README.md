# pygendoc - Python document generator

A simple hybrid jinja2/markdown based document generator.

## Prerequisites

This system relies on several utilities, please read *requirements.txt* for a
full list. Use "pip install -r requirements.txt" to install prerequisites.

## Encoding thoughts

Markdown file's encoding should be UTF-8.
The following commands will be useful for vim users:

    set fileencoding=utf-8
    set encoding=utf-8

    Massive convertion of files using utf-8:
        vim +"argdo se nobomb | se fileencoding=utf-8 | w" *.md

    Reload openned file with utf-8 charset (inside vim):
        :e ++enc=utf-8

## Usage

    pygendocs opscard <mdfiles>...
    pygendocs report <mdfiles>...

## Options

    opscard     Generate HTML doc using operations card template
    report      Generate HTML doc using report template
    -h, --help  Show usage

## Printing documents

Produced document are using CSS with several webkit directives. Printing those
documents using a non-webkit based browser will not work. It although possible
to print those documents via command line thanks to the *wkhtmltopdf* project.

Download *wkhtmltopdf*: http://wkhtmltopdf.org/downloads.html

### CLI printing requirements

Using Debian:

- fontconfig
- libfontconfig1
- libfreetype6
- libpng12-0
- zlib1g
- libjpeg-turbo8
- libssl1.0.0
- libx11-6
- libxext6
- libxrender1
- xfonts-base
- xfonts-75dpi
- libstdc++6
- libc6

Quick install:

    apt-get install fontconfig libfontconfig1 libfreetype6 libpng12-0 zlib1g libjpeg-turbo8 libssl1.0.0 libx11-6 libxext6 libxrender1 xfonts-base xfonts-75dpi libstdc++6 libc6
    wget http://downloads.sourceforge.net/wkhtmltopdf/wkhtmltox-0.12.2.1_linux-trusty-amd64.deb
    dpkg -i wkhtmltox-0.12.2.1_linux-trusty-amd64.deb

*wkhtmltopdf* usage:

    wkhtmltopdf --print-media-type -T 0 -B 0 -L 0 -R 0 "http://myreport.html" "myreport.pdf"
