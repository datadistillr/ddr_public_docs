# Querying PDF Files
One of the most annoying tasks is when you are working on a data science project and you get data that is in a PDF file.

## Data Model
Since PDF files generally are not intended to be queried or read by machines, mapping the data to tables and rows is not a perfect process.  The PDF reader does support provided schema.  You can see an example of a provided schema in the example queries below.

## Configuration Options:
There are several configuration options which you can use to adjust how DataDistillr is parsing PDF files.  Since these files were not meant to be queried directly, you will likely have to experiment with them in order to find the optimal configuration for your data.

The available options are:
* `extractHeaders`: Extracts the first row of any tables as the header row.  If set to `false`, Drill will assign column names of `field_0`, `field_1` to each column.
* `combinePages`: Merges multi page tables together.
* `defaultTableIndex`:  Allows you to query different tables within the PDF file. Index starts at `1`. 
* `extractionAlgorithm`:  Allows you to choose the extraction algorithm used for extracting data from the PDF file.  Choices are `spreadsheet` and `basic`.  Depending on your data, one may work better than the other.

You can set these options when you configure DataDistillr, or at query time with the `table()` function, as shown below:

```sql
SELECT * 
FROM table(dfs.`data.pdf`(type => 'pdf', extractHeaders => false, 
combinePages => true,
defaultTableIndex => 2,
extractionAlgorithm => 'spreadsheet'
))
```

### Merging Pages
The PDF reader reads tables from PDF files on each page.  If your PDF file has tables that span multiple pages, you can set the `combinePages` parameter to `true` and DataDistillr will merge all the tables in the PDF file.  You can also do this at query time with the `table()` function.

## Accessing Document Metadata Fields
PDF files have a considerable amount of metadata which can be useful for analysis.  Drill will extract the following fields from every PDF file.  Note that these fields are not projected in star queries and must be selected explicitly.  The document's creator populates these fields and some or all may be empty. With the exception of `_page_count` which is an `INT` and the two date fields, all the other fields are `VARCHAR` fields.
 
 The fields are:
 
 * `_page_count`
 * `_author`
 * `_title`
 * `_keywords`
 * `_creator`
 * `_producer`
 * `_creation_date`
 * `_modification_date`
 * `_trapped`
 * `_table_count`
 
 The query below will access a document's metadata:
 
 ```sql
SELECT _page_count, _title, _author, _subject, 
_keywords, _creator, _producer, _creation_date, 
_modification_date, _trapped 
FROM dfs.`pdf/20.pdf`
```

The query below demonstrates how to define a schema at query time.

```sql
SELECT * FROM table(cp.`pdf/schools.pdf` (type => 'pdf', combinePages => true, 
schema => 'inline=(`Last Name` VARCHAR, `First Name Address` VARCHAR, 
`field_0` VARCHAR, `City` VARCHAR, `State` VARCHAR, `Zip` VARCHAR, 
`field_1` VARCHAR, `Occupation Employer` VARCHAR, 
`Date` VARCHAR, `field_2` DATE properties {`drill.format` = `M/d/yyyy`}, 
`Amount` DOUBLE)')) 
LIMIT 10
```

### Encrypted Files
If a PDF file is encrypted, you can supply the password to the file via the `table()` function as shown below.  Note that the password will be recorded in any query logs that 
may exist.

```sql
SELECT * 
FROM table(dfs.`encrypted_pdf.pdf`(type => 'pdf', password=> 'your_password'))
```

## Sample Data
If you would like to experiment with some PDF files here are some [sample PDF files](https://github.com/datadistillr/sample-data/tree/master/pdf) to query.
