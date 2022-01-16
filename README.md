# example.itext7pdfgeneration_CSharp

The example creates a pdf file under usage of iText7 library.

Created artifacts are:

  1. Paragraph
  2. List
  3. Table
  2. Image

## Paragraph
Add a paragraph with proper header and text (font size: 14, font HELVETICA).

``` C#
Paragraph loremIpsumHeader = new Paragraph("Lorem Ipsum header...")
                    .SetFont(PdfFontFactory.CreateFont(StandardFonts.HELVETICA))
                    .SetFontSize(14)
                    .SetBold()
                    .SetFontColor(ColorConstants.RED);
            document.Add(loremIpsumHeader);
            document.Add(new Paragraph(LOREM_IPSUM_TEXT));
```
## List
Create a list of items with a blue header (font site: 14, font: TIMES_BOLD).

``` C#
Paragraph listHeader = new Paragraph("Lorem Ipsum ...")
                    .SetFont(PdfFontFactory.CreateFont(StandardFonts.TIMES_BOLD))
                    .SetFontSize(14)
                    .SetBold()
                    .SetFontColor(ColorConstants.BLUE);
List list = new List()
          .SetSymbolIndent(12)
          .SetListSymbol("\u2022")
          .SetFont(PdfFontFactory.CreateFont(StandardFonts.TIMES_BOLD));
list.Add(new ListItem("lorem ipsum 1"))
          .Add(new ListItem("lorem ipsum 2"))
          .Add(new ListItem("lorem ipsum 3"))
          .Add(new ListItem("lorem ipsum 4"))
          .Add(new ListItem("lorem ipsum 5"))
          .Add(new ListItem("lorem ipsum 6"));
document.Add(listHeader);
document.Add(list);
```

## Table
Draw a table by specifying header and ordinary cells.

``` C#
Paragraph tableHeader = new Paragraph("Lorem Ipsum Table ...")
                    .SetFont(PdfFontFactory.CreateFont(StandardFonts.TIMES_ROMAN))
                    .SetFontSize(18)
                    .SetBold()
                    .SetFontColor(ColorConstants.GREEN);
document.Add(tableHeader);
Table table = new Table(UnitValue.CreatePercentArray(4)).UseAllAvailableWidth();
table.AddHeaderCell(getHeaderCell("Ipsum 1"));
table.AddHeaderCell(getHeaderCell("Ipsum 2"));
table.AddHeaderCell(getHeaderCell("Ipsum 3"));
table.AddHeaderCell(getHeaderCell("Ipsum 4"));
table.SetFontSize(14).SetBackgroundColor(ColorConstants.WHITE);
table.AddCell("lorem 1");
table.AddCell("lorem 2");
table.AddCell("lorem 3");
table.AddCell("lorem 4");
document.Add(table);
```
## Image
Add an image to the document.

``` C#
Paragraph imageHeader = new Paragraph("Lorem Ipsum Image ...")
                    .SetFont(PdfFontFactory.CreateFont(StandardFonts.TIMES_ROMAN))
                    .SetFontSize(18)
                    .SetBold()
                    .SetFontColor(ColorConstants.GREEN);
document.Add(imageHeader);
ImageData imageData = ImageDataFactory.Create(GOOGLE_MAPS_PNG);
document.Add(new Image(imageData));
```

## common
The generated pdf file (target.pdf) is written to the output folder.
 
All the source code is placed in main class example.iText7pdfgeneration.Program.
