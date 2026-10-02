# HTTP Traffic Investigation

## Objective

Analyze HTTP network traffic to identify the client tool used to download a file, the web server software, the communicating IP addresses, and verify the downloaded file using an MD5 hash.

### Skills Learned

- Analyzed HTTP request and response traffic in a packet capture.
- Identified client and server information from HTTP headers.
- Determined source and destination IP addresses involved in a file transfer.
- Identified a downloaded file from an HTTP GET request.
- Verified file integrity using an MD5 checksum.

### Tools Used

- **Wireshark / CloudShark** for inspecting HTTP packets and headers.
- **MD5 hashing** to verify the downloaded file.

## Steps

### 1. Identifying the client tool and requested file

The HTTP GET request showed that the requested file was `/images/layout/logo.png`. The `User-Agent` header identified the Linux download utility as **Wget/1.12 (linux-gnu)**.

*Ref 1: HTTP GET request showing the requested file and Wget User-Agent.*

> Screenshot placeholder: use the original full screenshot showing packet/frame 4 with the GET request and User-Agent header. Do not crop it.

### 2. Identifying the web server and communicating IP addresses

The HTTP response returned **200 OK** and the `Server` header identified the web server as **nginx/0.8.53**. The HTTP request was initiated by **192.168.1.140** and sent to the server at **174.143.213.184**.

*Ref 2: HTTP response showing the 200 OK response and nginx server header.*

> Screenshot placeholder: use the original full screenshot showing packet/frame 36 with the HTTP response and Server header. Do not crop it.

### 3. Verifying the downloaded file

The downloaded file was identified as **logo.png** and its MD5 checksum was calculated as:

`966007c476e0c200fba8b28b250a6379`

*Ref 3: Verification of the downloaded logo.png file and its MD5 checksum.*

> Screenshot placeholder: use the original full screenshot showing the extracted/downloaded file or MD5 result. Do not crop it.

## Findings

- **Download tool:** Wget
- **Web server:** nginx
- **Client IP:** 192.168.1.140
- **Server IP:** 174.143.213.184
- **Downloaded file:** logo.png
- **MD5:** 966007c476e0c200fba8b28b250a6379
