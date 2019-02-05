[![Documentation](https://godoc.org/github.com/qmuntal/opc?status.svg)](https://godoc.org/github.com/qmuntal/opc)
[![Build Status](https://travis-ci.org/qmuntal/opc.svg?branch=master)](https://travis-ci.org/qmuntal/opc)
[![Go Report Card](https://goreportcard.com/badge/github.com/qmuntal/opc)](https://goreportcard.com/report/github.com/qmuntal/opc)
[![codecov](https://coveralls.io/repos/github/qmuntal/opc/badge.svg)](https://coveralls.io/github/qmuntal/opc?branch=master)
[![codeclimate](https://codeclimate.com/github/qmuntal/opc/badges/gpa.svg)](https://codeclimate.com/github/qmuntal/opc)
[![License](https://img.shields.io/badge/License-BSD%202--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause)

# opc
Package opc implements the ISO/IEC 29500-2, also known as the [Open Packaging Convention](https://en.wikipedia.org/wiki/Open_Packaging_Conventions).

The Open Packaging specification describes an abstract model and physical format conventions for the use of XML, Unicode, ZIP, and other openly available technologies and specifications to organize the content and resources of a document within a package.

The OPC is the foundation technology for many new file formats: .docx, .pptx, .xlsx, .3mf, .dwfx, ...

## Examples
### Write
```go
// Create a file to write our archive to.
f, _ := os.Create("example.xlsx")

// Create a new OPC archive.
w := opc.NewWriter(f)

// Create a new OPC part.
name := opc.NormalizePartName("docs\\readme.txt")
part, _ := w.Create(name, "text/plain")

// Write content to the part.
part.Write([]byte("This archive contains some text files."))

// Make sure to check the error on Close.
w.Close()
```
