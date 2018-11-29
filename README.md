# IKATS Viztool vt-table


This viz-tool allows to creates the rendering of a table for ikats. 

# Inputs

vt-table use a Table object to 


### Input and parameters

The viz-tool takes 1 input:

* **Table**: The Table object to generate the rendering.

Definition of json object coding the 'table' type:

- property table_desc: optional general description: object having string properties title and desc

- property headers: optional description of the table headers. Headers are specifically managed by the viewer,
  they are quite advised for scrolled contents.
  - property headers.col: optional object definition of the column headers
    - property headers.col.data: required when header is defined
    - optional properties: headers.col.default_links and headers.col.links

  - property headers.row: optional definition of the row headers
    - property headers.row.data: required when header is defined
    - optional properties: headers.row.default_links and headers.row.links

- property content: description of the table content.
  - property content.cells: list of rows: each row is a list of cells. Each cell is a value (string, number or null)
  - optional properties: content.default_links and content.links


the Table object looks like this : 

    {
        'table_desc': {
                       'title': 'Discretized matrix',
                       'desc':  'This is a ...'
                    }
        
        'headers': {
         'col': {
        
            'data':  [ 'funcId', 'metric', 'min_B1', 'max_B1', 'min_B2', 'max_B2' ],
            'default_links': null,
            'links': null
         },
        
         'row': {
        
             'data':  [ null, 'Flid1_VIB2', 'Flid1_VIB3', 'Flid1_VIB4', 'Flid1_VIB5' ],
             'default_links': {'type': 'bucket_ts', 'context': 'processdata' },
             'links': [     { 'val': '1' },
                            { 'val': '2' },
                            { 'val': '3' },
                            { 'val': '4' } ]
         }
        
        },
        
        'content':  {
         'cells': [[ 'VIB2', -50.0, 12.1, 1.0, 3.4 ],
                   [ 'VIB3',-5.0, 2.1, 1.0, 3.4 ],
                   [ 'VIB4', 0.0, 2.1, 12.0, 3.4 ],
                   [ 'VIB5', 0.0, 2.1, 1.0, 3.4 ] ],
         'default_links': null,
         'links': null
        }
    }
    
the easyest way to generate à table on ikats is to feed a CSV file in the `population selection` operator

