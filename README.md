<div align="center">
  <h1>chromb</h1>
  <p><b>THE GOOGLE DRIVE LINK CONVERTER</b></p>
  
  <img src="./images/chromb.jpg" alt="chromb logo" width="400">
</div>

<div align="center">
  
  ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
  &nbsp;
  ![Google Drive](https://img.shields.io/badge/Google%20Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)
  &nbsp;
  ![CLI](https://img.shields.io/badge/CLI-Tool-%23000000.svg?style=for-the-badge)
  
</div>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#how-it-works">How It Works</a> •
  <a href="#examples">Examples</a>
</p>

<hr>

<br>

## OVERVIEW

**chromb** is a lightweight command-line utility that transforms Google Drive sharing links into direct download URLs.

Google Drive sharing links are designed for browser-based viewing, but often you need a direct download link for scripting, automation, or integration with other tools.

### THE TRANSFORMATION

---

<div align="center">
  <p><b>FROM:</b></p>
  <code>https://drive.google.com/file/d/FILE_ID/view?usp=sharing</code>
  <br><br>
  <p><b>TO:</b></p>
  <code>https://drive.google.com/uc?export=download&id=FILE_ID</code>
</div>

---

**chromb**:

1. **TAKES** a standard Google Drive sharing URL as input
2. **EXTRACTS** the file ID from the URL structure
3. **OUTPUTS** a clean, direct download link

The tool handles the URL parsing and reconstruction automatically, making it trivial to integrate Google Drive files into automated workflows, scripts, or download managers.

<br>

## INSTALLATION

### PREREQUISITES

- Python 3.x installed on your system
- Basic command-line access

### SETUP

**1. MAKE THE SCRIPT EXECUTABLE**

```bash
chmod +x chromb.py
```

**2. CREATE A SYMBOLIC LINK**

Link the script to a directory in your system's PATH:

```bash
ln -s /path/to/chromb.py /usr/local/bin/chromb
```

Replace `/path/to/` with the actual path to the `chromb.py` script, and `/usr/local/bin/` with a directory in your system's PATH.

**3. VERIFY INSTALLATION**

```bash
chromb --help
```

<br>

## USAGE

### BASIC SYNTAX

```bash
chromb <drive_download_link_url>
```

### PARAMETERS

- `<drive_download_link_url>` - Required. A Google Drive sharing link containing a file ID

<br>

## EXAMPLES

### BASIC CONVERSION

**INPUT:**

```bash
chromb https://drive.google.com/file/d/1LDRlyZaZTF-bxHjBDEiL2obMxYHtf3YT/view?usp=sharing
```

**OUTPUT:**

```
https://drive.google.com/uc?export=download&id=1LDRlyZaZTF-bxHjBDEiL2obMxYHtf3YT
```

### USING WITH WGET

```bash
wget $(chromb https://drive.google.com/file/d/1LDRlyZaZTF-bxHjBDEiL2obMxYHtf3YT/view?usp=sharing)
```

### USING WITH CURL

```bash
curl -L -o output.file $(chromb https://drive.google.com/file/d/1LDRlyZaZTF-bxHjBDEiL2obMxYHtf3YT/view?usp=sharing)
```

### PIPING TO CLIPBOARD

```bash
chromb https://drive.google.com/file/d/1LDRlyZaZTF-bxHjBDEiL2obMxYHtf3YT/view?usp=sharing | pbcopy
```

<br>

## HOW IT WORKS

### URL STRUCTURE ANALYSIS

Google Drive uses two primary URL formats:

<table>
<tr>
<td width="50%">

**SHARING LINK FORMAT**

```
https://drive.google.com/file/d/
  [FILE_ID]/view?usp=sharing
```

Used for browser-based viewing and sharing

</td>
<td width="50%">

**DIRECT DOWNLOAD FORMAT**

```
https://drive.google.com/uc?
  export=download&id=[FILE_ID]
```

Used for programmatic downloads

</td>
</tr>
</table>

### CONVERSION PROCESS

1. **PARSE INPUT** - Extract the file ID from the sharing link
2. **RECONSTRUCT** - Build the direct download URL with the extracted ID
3. **OUTPUT** - Return the converted URL to stdout

<br>

## USE CASES

<table>
<tr>
<td>

**AUTOMATION SCRIPTS**

Integrate Google Drive files into shell scripts and automation workflows

</td>
</tr>
<tr>
<td>

**DOWNLOAD MANAGERS**

Feed direct download links to tools like wget, curl, or aria2

</td>
</tr>
<tr>
<td>

**CI/CD PIPELINES**

Download assets or datasets from Google Drive during build processes

</td>
</tr>
<tr>
<td>

**BATCH PROCESSING**

Convert multiple links programmatically for bulk downloads

</td>
</tr>
</table>

<br>

## LIMITATIONS

- Only works with public or accessible Google Drive files
- Large files may require additional authentication handling
- Does not handle folder links or other Google Drive URL formats

<br>

<div align="center">
  <hr>
  <p><i>simple tools for simple tasks</i></p>
  <p><b>chromb</b> - because sometimes you just need the direct link</p>
</div>