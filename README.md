# ElevenGo

[![GoDoc](https://godoc.org/github.com/deadblue/elevengo?status.svg)](https://godoc.org/github.com/deadblue/elevengo)
![](https://img.shields.io/badge/latest-v0.1.2-brightgreen)

A Golang API wrapper for 115 NetDisk Service.

## Example

```go
import "github.com/deadblue/elevengo"

// Create agent
agent = elevengo.Default()

// Import credentials to login
cr = &elevengo.Credentials{
    UID: "",
    CID: "",
    SEID: "",
}
if err := agent.CredentialsImport(cr); err != nil {
    panic(err)
}

// List files under root.
for cursor := elevengo.FileCursor(); cursor.HasMore(); cursor.Next() {
    if files, err := agent.FileList("0", cursor); err != nil {
        panic(err)
    } else {
        // TODO: deal with the files
    }
}
```

You can find more example on [GoDoc](https://godoc.org/github.com/deadblue/elevengo).

## Features

* Login
  * [x] Import credentials from cookies
  * [x] Login via QRCode
  * [x] Get signed in user information
  * [ ] ~~Login via Account/Password~~ (No idea)
* File
  * [x] List
  * [x] Search
  * [x] Rename
  * [x] Move
  * [x] Copy
  * [x] Delete
  * [x] Mkdir
  * [x] Stat
  * [x] Storage Stat
  * [x] Download
  * [x] Upload
  * [x] Video HLS
* Offline
  * [x] List tasks
  * [x] Create URL task(s)
  * [x] Delete tasks
  * [x] Clear tasks
* Other
  * [x] Captcha

## TODO list

* Handle more upstream errors.
* Print some logs via Logger interface.
* Caller can swtich upstream API between HTTP/HTTPS.
* Implement download/upload method, with progress echo.

## License

MIT