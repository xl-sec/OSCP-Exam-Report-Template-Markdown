# Offensive Security Exam Report Template in Markdown

[![Rawsec's CyberSecurity Inventory](https://inventory.raw.pm/img/badges/Rawsec-inventoried-FF5050_flat-square.svg)](https://inventory.rawsec.ml/tools.html#OSCP%20Exam%20Report%20Template%20in%20Markdown)
[![GitHub stars](https://img.shields.io/github/stars/noraj/OSCP-Exam-Report-Template-Markdown?style=flat-square)](https://github.com/noraj/OSCP-Exam-Report-Template-Markdown/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/noraj/OSCP-Exam-Report-Template-Markdown?style=flat-square)](https://github.com/noraj/OSCP-Exam-Report-Template-Markdown/network)
[![GitHub license](https://img.shields.io/github/license/noraj/OSCP-Exam-Report-Template-Markdown?style=flat-square)](https://github.com/noraj/OSCP-Exam-Report-Template-Markdown/blob/master/LICENSE)

I created an **Offensive Security Exam Report Template in Markdown** so LaTeX, Microsoft Office Word, LibreOffice Writer are no longer needed during your Offensive Security OSCP, OSWE, OSCE, OSEE, OSWP, OSEP, OSED exam!

Now you can be efficient and faster during your exam report redaction!

- :rocket: **Speed up writing**, don't lose time during the 24 hours of exam report redaction
- :star: **No formatting hassle with WYSIWYG editors**, byebye unwanted whitespaces and linefeeds from Microsoft Office Word and LibreOffice Writer
- :memo: **Re-use your Markdown notes**, you'll be so glad not having to reformat the bold and italic from your Markdown notes into the report
- :lock: **Version control ready**, save your markdown template into a PRIVATE git repository, you now have an incremental backup, version control works with Markdown (.md) as it's text but not with binaries (.doc, .odt)
- :pen: **Use your favorite editor or note taking app**, with Markdown you'll be able to use your favorite editor (VSCode, Atom, etc.) or note taking app (Vnote, QOwnNotes, Boostnote, etc.) to write your exam report, you won't have to switch to Windows to use MS Word.
- :tophat: **Clean & professional style**, a professional looking report for your professional certification
- :ok_hand: **Error free**, use the generation script to generate the report and archive, you won't do any [submission format and name](https://support.offensive-security.com/oscp-exam-guide/#submission-format-and-name) mistake that way

![](https://i.imgur.com/XiXIZg3.png)

Examples:

**OSCP whoisflynn improved template v3.2**

![](https://i.imgur.com/Z344YCQ.png)
![](https://i.imgur.com/wegbNYr.png)

**OSCP Official Offensive Security Template v1**

![](https://i.imgur.com/9zoWFfr.png)
![](https://i.imgur.com/MWSgxfh.png)

## Requirements

- [Pandoc](https://pandoc.org/installing.html)
- LaTeX (eg. [TeX Live](http://www.tug.org/texlive/)) in order to get `pdflatex` or `xelatex`
- [Eisvogel Pandoc LaTeX PDF Template](https://github.com/Wandmalfarbe/pandoc-latex-template#installation)
- [p7zip](http://p7zip.sourceforge.net/) (if you want to use the script, for generating the archive)

Examples for common distros:

- ArchLinux: `pacman -S texlive-most pandoc p7zip`
- openSUSE: `zypper in texlive-scheme-medium pandoc p7zip-full`
- Ubuntu: `apt install texlive-latex-recommended texlive-fonts-extra texlive-latex-extra pandoc p7zip-full`

## Usage

Write your report in **markdown**.

### Automatic

There is a script that will:

1. Let you choose the template
2. Let you choose the syntax highlight style
3. Generate the PDF
4. Open the PDF for viewing
5. Generate the 7z archive
6. Output MD5 hash for verification after uploading

```
ruby generate.rb
```

#### With arguments

To speed up generation, all settings can ge set with arguments to the script.

```
ruby generate.rb -h
Usage: generate.rb [options]
    -t, --template ID                Template ID
    -i, --os-id ID                   Offensive Security student ID (OS-ID)
    -s, --style STYLE                Code highlight style (or 'd' for default which is breezedark)
    -v, --view Y/N                   View PDF after generating with the OS default PDF viewer
    -a, --archive Y/N                Create an archive
    -e, --extra FILE                 Extra file(s) to include in archive (or 'n' for none)
```

To run the default mode with no prompts;

```
ruby generate.rb -t 0 -i 1234 -s d -v y -a y
```

Or you can hard-code default settings on the first few rows in the scripts by uncomment the necessary rows in the JSON;

```
options = {
  template: 0,
  osid: 'OS-1234',
  style: 'breezedark',
  view: true,
  archive: true,
  extra_file: false
}
```

### Manual

Generate the report PDF from the markdown template:

```
pandoc src/OSCP-exam-report-template_whoisflynn_v3.2.md \
-o output/OSCP-OS-XXXXX-Exam-Report.pdf \
--from markdown+yaml_metadata_block+raw_html \
--template eisvogel \
--table-of-contents \
--toc-depth 6 \
--number-sections \
--top-level-division=chapter \
--highlight-style breezedark \
--metadata date=$(date +%Y-%m-%d)
```

You can change the code syntax highlight theme with [`--highlight-style`](https://pandoc.org/MANUAL.html#option--highlight-style).

## Color sets

Well rendering color sets you can use in the template YAML frontmatter:

titlepage-color          | titlepage-text-color | titlepage-rule-color
-------------------------|----------------------|---------------------
`DC143C` (Crimson)       | `FFFFFF` (White)     | `FFFFFF` (White)
`00FF7F` (SpringGreen)   | `006400` DarkGreen   | `000000` (Black)
`1E90FF` (DodgerBlue)    | `FFFAFA` (Snow)      | `FFFAFA` (Snow)
`483D8B` (DarkSlateBlue) | `FFFAFA` (Snow)      | `FFFAFA` (Snow)
`FFD700` (Gold)          | `000000` (Black)     | `000000` (Black)
`FFEFD5` (PapayaWhip)    | `000000` (Black)     | `000000` (Black)
`FF8C00` (DarkOrange)    | `000000` (Black)     | `000000` (Black)
`FFEF96` (no name)       | `50394C` (no name)   | `50394C` (no name)

## Available templates

Report Templates:

Penetration Testing:

- **OSCP**
  - [Official Offensive Security Template v1](output/OSCP-Official_Offensive_Security_template_v1.pdf)
  - [Official Offensive Security Template v2](output/OSCP-Official_Offensive_Security_template_v2.pdf)
  - [whoisflynn][whoisflynn] improved [template](output/OSCP-whoisflynn_improved_template_v3.2.pdf) v3.2
- **OSWP**
  - [Official Offensive Security Template v1](output/OSWP-Official_Offensive_Security_template_v1.pdf)
- **OSEP**
  - [Official Offensive Security Template v1](output/OSEP-Official_Offensive_Security_template_v1.pdf)

Web Application:

- **OSWE**
  - [Official Offensive Security Template v1](output/OSWE-Official_Offensive_Security_template_v1.pdf)
  - [noraj][noraj] improved [template](output/OSWE-noraj_improved_template_v1.pdf) v1
  - [xl-sec][XL-SEC] improved [template](output/OSWE-XL-SEC_improved_template_v1.pdf) v1

Exploit Development:

- **OSED**
  - [Official Offensive Security Template v1](output/OSED-Official_Offensive_Security_template_v1.pdf)
  - [epi][epi] improved [template](output/OSED-epi_improved_template_v1.pdf) v1
- **OSEE**
  - [Official Offensive Security Template v1](output/OSEE-Official_Offensive_Security_template_v1.pdf)
- **OSCE** (**deprecated**)
  - [Official Offensive Security Template v1](output/OSCE-Official_Offensive_Security_template_v1.pdf)

[whoisflynn]:https://github.com/whoisflynn
[noraj]:https://github.com/noraj
[epi]:https://github.com/epi052
[xl-sec]:https://github.com/xl-sec

Offensive Security course table:

Exam acronym | Exam name                                         | Lab acronym | Lab name                                  | Course designation
-------------|---------------------------------------------------|-------------|-------------------------------------------|-------------------
**OSCP**     | Offensive Security Certified Professional         | PWK         | Penetration Testing with Kali Linux       | PEN-200
**OSWP**     | Offensive Security Wireless Professional          | OSWA        | Offensive Security Wireless Attacks       | PEN-210
**OSEP**     | Offensive Security Experienced Penetration Tester | ETBD        | Evasion Techniques and Breaching Defenses | PEN-300
**OSWE**     | Offensive Security Web Expert                     | AWAE        | Advanced Web Attacks and Exploitation     | WEB-300
**OSED**     | Offensive Security Exploit Developer              | WUMED       | Windows User Mode Exploit Development     | EXP-301
**OSEE**     | Offensive Security Exploitation Expert            | AWE         | Advanced Windows Exploitation             | EXP-401
**OSCE**     | Offensive Security Certified Expert               | CTP         | Cracking the Perimeter                    | N/A

## Community projects

Docker containers:

- [ret2src docker](https://github.com/ret2src/OSCP-Exam-Report-Template-Markdown#docker)
- [Tripex48 docker](https://github.com/Tripex48/OSCP-Exam-Report-Template-Markdown#docker)

## Mentions

- John Hammond - OSCP - Taking Notes & Resources (video) (2019-10-06)
  [![OSCP - Taking Notes & Resources](http://img.youtube.com/vi/MQGozZzHUwQ/0.jpg)](https://www.youtube.com/watch?v=MQGozZzHUwQ)
- 3rd [Top Offensive Security Open Source Projects](https://awesomeopensource.com/projects/offensive-security) (2021-07-19)
- Recent mentions on social medias: [Social-searcher](https://www.social-searcher.com/social-buzz/?q5=https%3A%2F%2Fgithub.com%2Fnoraj%2FOSCP-Exam-Report-Template-Markdown)
- Articles:
  - [Stress-free OSCP report making](https://craigunder.me/stress-free-oscp-report-making/) by Craig Underhill (2020-04-06)
  - [Unofficial OSCP Approved Tools](https://falconspy.medium.com/unofficial-oscp-approved-tools-b2b4e889e707) by FalconSpy (2019-06-05)
  - [Journey from nothing to OSCP](https://cjhackerz.net/posts/journey-from-nothing-to-oscp/) by  CJHackerz (2020-06-30)

## Stargazers over time

[![Stargazers over time](https://starchart.cc/noraj/OSCP-Exam-Report-Template-Markdown.svg)](https://starchart.cc/noraj/OSCP-Exam-Report-Template-Markdown)

## Credits

Report Templates:

- **OSCP**
  - [Official Offensive Security Template](https://help.offensive-security.com/hc/en-us/articles/360040165632#suggested-documentation-templates) (UNLICENSED)
  - [whoisflynn improved template](https://github.com/whoisflynn/OSCP-Exam-Report-Template) (UNLICENSED)
- **OSWE**
  - [Official Offensive Security Template](https://help.offensive-security.com/hc/en-us/articles/360046869951-OSWE-Exam-Guide#suggested-documentation-templates) (UNLICENSED)
  - [noraj improved template](src/OSWE-noraj_improved_template_v1.md) (UNLICENSED)
  - [XL-SEC improved template](src/OSWE-XL-SEC_improved_template_v1.md) (UNLICENSED)
- **OSCE**
  - [Official Offensive Security Template](https://help.offensive-security.com/hc/en-us/articles/360046801331-OSCE-Exam-Guide#suggested-documentation-templates) (UNLICENSED)
- **OSEE**
  - [Official Offensive Security Template](https://help.offensive-security.com/hc/en-us/articles/360046458732-OSEE-Exam-Guide#Documentation%20Requirements) (UNLICENSED)
- **OSWP**
  - [Official Offensive Security Template](https://help.offensive-security.com/hc/en-us/articles/360046904731-OSWP-Exam-Guide#suggested-documentation-templates) (UNLICENSED)
- **OSED**
  - [Official Offensive Security Template](https://help.offensive-security.com/hc/en-us/articles/360052977212-OSED-Exam-Guide#suggested-documentation-templates) (UNLICENSED)
  - [epi improved template](src/OSED-epi_improved_template_v1.md) (UNLICENSED)
- **OSEP**
  - [Official Offensive Security Template](https://help.offensive-security.com/hc/en-us/articles/360050293792-OSEP-Exam-Guide#suggested-documentation-templates) (UNLICENSED)

Pandoc Template:

- Eisvogel ([LICENCE](https://github.com/Wandmalfarbe/pandoc-latex-template/blob/master/LICENSE)): https://github.com/Wandmalfarbe/pandoc-latex-template

Placeholder image:

- Generated by https://imgplaceholder.com/
