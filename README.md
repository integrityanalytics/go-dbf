# go-dbf
[![Build Status](https://travis-ci.com/IntegrityAnalytics/go-dbf.svg?branch=master)](https://travis-ci.com/IntegrityAnalytics/go-dbf)
[![GoDoc](https://godoc.org/github.com/IntegrityAnalytics/go-dbf/godbf?status.svg)](https://godoc.org/github.com/IntegrityAnalytics/go-dbf/godbf)


A pure Go library for reading and writing [dBase/xBase](http://en.wikipedia.org/wiki/DBase#File_formats) database files

This project is a part of go-shp library. [go-shp](https://github.com/jonas-p/go-shp) is a pure Go implementation of Esri [Shapefile](http://en.wikipedia.org/wiki/Shapefile) format.

You can incorporate the library into your local workspace with the following 'go get' command:

```go
go get github.com/IntegrityAnalytics/go-dbf/godbf
```

Code needing to call into the library needs to include the following import statement:
```go
import (
  "github.com/IntegrityAnalytics/go-dbf/godbf"
)
```

Here is a very simple snippet of example 'load' code to get you going:
```go
  dbfTable, err := godbf.NewFromFile("exampleFile.dbf", "UTF8")

  exampleList := make(ExampleList, dbfTable.NumberOfRecords())

  for i := 0; i < dbfTable.NumberOfRecords(); i++ {
    exampleList[i] = new(ExampleListEntry)

    exampleList[i].someColumnId, err = dbfTable.FieldValueByName(i, "SOME_COLUMN_ID")
  }
```

Further examples can be found by browsing the library's test suite. 
  
## Projects using godbf

### [dbfcsv](https://github.com/lancecarlson/dbfcsv) - A command line utility for dbf/csv conversion
