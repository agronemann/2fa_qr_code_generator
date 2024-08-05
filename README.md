# 2FA QR Code Generator

Make a printable version of your 2FA seed as a QR code.

## Installation

You are meant to download [2fa-qr-code-generator.html](https://raw.githubusercontent.com/agronemann/2fa_qr_code_generator/main/2fa-qr-code-generator.html) and run it locally in a web browser. No other dependencies are required.

Clone the repository:

    git clone git@github.com:agronemann/2fa_qr_code_generator.git
    cd 2fa_qr_code_generator

Or download using cURL:

    mkdir 2fa_qr_code_generator
    cd 2fa_qr_code_generator
    curl -O https://raw.githubusercontent.com/agronemann/2fa_qr_code_generator/main/2fa-qr-code-generator.html

## Usage

With [2fa-qr-code-generator.html](https://raw.githubusercontent.com/agronemann/2fa_qr_code_generator/main/2fa-qr-code-generator.html) you can generate a printable version of your 2FA seed as a QR code, along with an optional custom field (eg. a recovery key).

## Dependencies

- https://github.com/davidshimjs/qrcodejs (commit `04f46c6a0708418cb7b96fc563eacae0fbf77674`).

## Auditing and verifying (optional but recommended)

The code is meant to be as simple as possible, thus making it easier audit.

You can verify that the inline code for [qrcode.min.js](https://raw.githubusercontent.com/davidshimjs/qrcodejs/04f46c6a0708418cb7b96fc563eacae0fbf77674/qrcode.min.js) in [2fa-qr-code-generator.html](https://raw.githubusercontent.com/agronemann/2fa_qr_code_generator/main/2fa-qr-code-generator.html) matches the official source code. An example of doing so is checking the checksum in the `Content-Security-Policy` against the file from GitHub:

    curl -s https://raw.githubusercontent.com/davidshimjs/qrcodejs/04f46c6a0708418cb7b96fc563eacae0fbf77674/qrcode.min.js | openssl sha256 -binary | openssl base64 | grep -qf - 2fa-qr-code-generator.html &&
    echo "Success" || echo "Error"
