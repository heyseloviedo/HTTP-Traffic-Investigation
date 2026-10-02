# HTTP Traffic Investigation

## Objective

Analyze HTTP network traffic to identify information about a file download. The investigation focused on examining HTTP requests and responses to identify the download utility, web server software, communicating IP addresses, downloaded file, and its MD5 checksum.

### Skills Learned

- Analyzing HTTP requests and responses in packet captures.
- Identifying client and server information from HTTP headers.
- Determining source and destination IP addresses involved in HTTP communication.
- Identifying downloaded files from HTTP GET requests.
- Verifying downloaded files using MD5 hashes.

### Tools Used

- **Wireshark / CloudShark** — packet inspection and HTTP traffic analysis.
- **MD5 hashing** — verification of the downloaded file.

## Steps

### 1. Identified the download utility

Examined the HTTP GET request and found the header:

`User-Agent: Wget/1.12 (linux-gnu)`

This identified **Wget** as the Linux utility used to download the file.

### 2. Identified the web server

Examined the HTTP response and found:

`Server: nginx/0.8.53`

This identified **nginx** as the web server software.

### 3. Identified the client and server IP addresses

The HTTP GET request showed that **192.168.1.140** initiated the request and **174.143.213.184** was the destination server.

- **Client IP:** 192.168.1.140
- **Server IP:** 174.143.213.184

### 4. Identified the downloaded file

The HTTP request contained:

`GET /images/layout/logo.png HTTP/1.0`

This showed that the downloaded file was **logo.png**.

### 5. Verified the downloaded file

The downloaded `logo.png` file was verified using its MD5 checksum.

`966007c476e0c200fba8b28b250a6379`

## Findings

- **Download utility:** Wget
- **Web server:** nginx
- **Client IP:** 192.168.1.140
- **Server IP:** 174.143.213.184
- **Downloaded file:** logo.png
- **MD5:** 966007c476e0c200fba8b28b250a6379
