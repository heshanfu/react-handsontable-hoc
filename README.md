# react-handsontable-hoc

[![npm](https://img.shields.io/npm/v/@ohtomi/react-handsontable-hoc.svg)](https://www.npmjs.com/package/@ohtomi/react-handsontable-hoc)
[![License](https://img.shields.io/npm/l/@ohtomi/react-handsontable-hoc.svg)](https://www.npmjs.com/package/@ohtomi/react-handsontable-hoc)
[![Build Status](https://travis-ci.org/ohtomi/react-handsontable-hoc.svg?branch=master)](https://travis-ci.org/ohtomi/react-handsontable-hoc)
[![Greenkeeper badge](https://badges.greenkeeper.io/ohtomi/react-handsontable-hoc.svg)](https://greenkeeper.io/)

## Description

A higher order component for `react-handsontable`.

## How to use

```javascript
render() {
    const data = [
        {'id': 11, 'name': 'ford', 'year': 2015, 'volume': 1000, 'processed': true},
        {'id': 12, 'name': 'ford', 'year': 2016, 'volume': 1000, 'processed': true},
        {'id': 13, 'name': 'ford', 'year': 2017, 'volume': 1000, 'processed': true},
        {'id': 14, 'name': 'ford', 'year': 2018, 'volume': 1000, 'processed': false},
        {'id': 21, 'name': 'volvo', 'year': 2015, 'volume': 1000, 'processed': true},
        {'id': 22, 'name': 'volvo', 'year': 2016, 'volume': 1000, 'processed': true},
        {'id': 23, 'name': 'volvo', 'year': 2017, 'volume': 1000, 'processed': true},
        {'id': 24, 'name': 'volvo', 'year': 2017, 'volume': 1000, 'processed': false},
        {'id': 31, 'name': 'toyota', 'year': 2016, 'volume': 1000, 'processed': true},
        {'id': 32, 'name': 'toyota', 'year': 2017, 'volume': 1000, 'processed': true},
        {'id': 33, 'name': 'toyota', 'year': 2018, 'volume': 1000, 'processed': true},
        {'id': 41, 'name': 'honda', 'year': 2015, 'volume': 1000, 'processed': true}
    ]

    const columns = [
        {data: 'id', type: 'numeric', width: 150, readOnly: true},
        {data: 'name', type: 'text', width: 150, readOnly: true},
        {data: 'year', type: 'numeric', width: 150, readOnly: true},
        {data: 'volume', type: 'numeric', width: 150, readOnly: true},
        {data: data => data.processed ? 'Yes' : 'No', type: 'text', width: 150, readOnly: true}
    ]

    const colHeaders = ['ID', 'NAME', 'YEAR', 'VOLUME', 'PROCESSED?']

    // VOLUME is hidden
    const hiddenColumns = [3]

    // sort by NAME
    const columnSorting = {
        column: 4,
        sortOrder: 'desc'
    }

    // filter by NAME
    const filter = new RowFilter([
        {
            physical: 1,
            expression: Expressions.get({
                symbol: 'by_values',
                props: ['ford', 'volvo']
            })
        }
    ])

    return (
        <HotTableContainer
            width="800" height="300"
            data={data} columns={columns} colHeaders={colHeaders}
            hiddenColumns={hiddenColumns}
            columnSorting={columnSorting}
            manualColumnMove={true}
            manualColumnResize={true}
            rowFilter={filter}/>
    )
}
```

## How to build

```bash
$ npm install
$ npm run build
```

## Contributing

1. Fork it!
1. Create your feature branch: `git checkout -b my-new-feature`
1. Commit your changes: `git commit -am 'Add some feature'`
1. Push to the branch: `git push origin my-new-feature`
1. Submit a pull request :D

## License

MIT

## Author

[Kenichi Ohtomi](https://github.com/ohtomi)
