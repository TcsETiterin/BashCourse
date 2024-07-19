`wget` is a powerful and versatile command-line utility for downloading files from the web. It is widely used in Unix-like operating systems (Linux, BSD, macOS, etc.) and comes pre-installed on most Linux distributions. `wget` supports downloading via various protocols such as HTTP, HTTPS, and FTP.

### Key Features of `wget`:

- **Non-interactive downloading:** Once a download starts, it will continue without any user interaction. This is particularly useful for scripts and cron jobs.
- **Recursive downloading:** `wget` can follow links and download files from a website recursively.
- **Resume downloads:** If a download is interrupted, `wget` can resume it from where it left off.
- **Robustness:** Handles network issues and retries downloads automatically.
- **Support for proxies and cookies:** It can handle HTTP proxies and manage cookies for authenticated sessions.

### Basic Usage

The general syntax for `wget` is:

```sh
wget [options] [URL]
```

#### Download a Single File

```sh
wget http://example.com/file.tar.gz
```

This command downloads the file `file.tar.gz` from the specified URL to the current directory.

### Advanced Options

#### 1. **Resume an Interrupted Download**

```sh
wget -c http://example.com/file.tar.gz
```

The `-c` (or `--continue`) option tells `wget` to resume the download if it was interrupted.

#### 2. **Download Files in the Background**

```sh
wget -b http://example.com/file.tar.gz
```

The `-b` (or `--background`) option runs the download in the background, allowing you to continue using the terminal.

#### 3. **Specify an Output File Name**

```sh
wget -O newfile.tar.gz http://example.com/file.tar.gz
```

The `-O` option specifies the file name to save the downloaded content.

#### 4. **Download Files Recursively**

```sh
wget -r http://example.com/directory/
```

The `-r` (or `--recursive`) option enables recursive downloading.

#### 5. **Limit Download Speed**

```sh
wget --limit-rate=200k http://example.com/file.tar.gz
```

The `--limit-rate` option restricts the download speed. This example limits the download speed to 200 KB/s.

#### 6. **Mirror a Website**

```sh
wget --mirror -p --convert-links```sh
wget --mirror -p --convert-links -P ./local-dir http://example.com/
```

This command mirrors the entire website specified in the URL:

- `--mirror`: This option is equivalent to using `-r -N -l inf --no-remove-listing`. It turns on recursive downloading while preserving the site structure.
- `-p` (or `--page-requisites`): This option downloads all the necessary files, such as images and stylesheets, required to properly display the pages.
- `--convert-links`: This rewrites the links within the downloaded files to make them suitable for offline viewing.
- `-P ./local-dir`: This specifies the directory to which the mirrored site should be saved (`./local-dir` in this case).

### Other Useful Options

#### 1. **Download with User Authentication**

```sh
wget --user=username --password=password http://example.com/protected-file.tar.gz
```

The `--user` and `--password` options provide HTTP authentication for websites that require a username and password.

#### 2. **Download Using a Proxy**

```sh
wget -e use_proxy=yes -e http_proxy=http://proxyserver:port http://example.com/file.tar.gz
```

The `-e` option is used to set various wget parameters, such as using an HTTP proxy.

#### 3. **Follow FTP Links**

```sh
wget --follow-ftp http://example.com/
```

The `--follow-ftp` option ensures that `wget` follows FTP links found within HTML pages.

#### 4. **Custom User-Agent Header**

```sh
wget --user-agent="Mozilla/5.0" http://example.com/file.tar.gz
```

The `--user-agent` option specifies a custom User-Agent header string.

#### 5. **Download with a Referrer**

```sh
wget --referer=http://example.com/ http://example.com/file.tar.gz
```

The `--referer` option specifies a custom referrer URL.

### Scripts and Automation

`wget` is often used in scripts for automated downloading.

#### Example Script to Download Multiple Files

```sh
#!/bin/bash

# List of URLs
urls=(
    "http://example.com/file1.tar.gz"
    "http://example.com/file2.tar.gz"
    "http://example.com/file3.tar.gz"
)

# Loop through the list and download each file
for url in "${urls[@]}"; do```sh
    echo "Downloading $url..."
    wget "$url"
done

echo "All downloads complete."
```

This script uses an array to hold the URLs and loops through each URL to download the files.

### Combine `wget` with Other Commands

You can use `wget` in combination with other shell utilities to perform more complex tasks. Here's an example of downloading a list of URLs provided in a text file:

#### Example with a List of URLs in a File

Suppose you have a file named `urls.txt` containing a list of URLs:

```sh
http://example.com/file1.tar.gz
http://example.com/file2.tar.gz
http://example.com/file3.tar.gz
```

You can use a `while` loop to read each URL and download it:

```sh
#!/bin/bash

filename='urls.txt'

while read -r url; do
    echo "Downloading $url..."
    wget "$url"
done < "$filename"

echo "All downloads complete."
```

This script reads each URL from `urls.txt` and downloads the corresponding file.

### Handling Errors

You can capture the exit status of `wget` to handle errors in your scripts.

```sh
#!/bin/bash

url="http://example.com/file.tar.gz"
output="file.tar.gz"

wget -O "$output" "$url"
status=$?

if [ $status -ne 0 ]; then
    echo "Download failed with status $status"
    exit 1
else
    echo "Download succeeded"
fi
```

Here we use the `$?` variable to capture the exit status of `wget`. If the status is not `0`, the script prints an error message and exits with a status of `1`.

### Conclusion

`wget` is an incredibly powerful tool for downloading files from the web, with a wide array of options to suit various needs. Whether you are downloading individual files, mirroring entire websites, or automating downloads with scripts, `wget` offers the flexibility and robustness required to handle most tasks.
