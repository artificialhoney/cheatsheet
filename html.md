---
layout: default
title: html
parent: Cheatsheet
nav_order: 2
---

# html

## [Generate pdf from HTML in div using Javascript](https://stackoverflow.com/questions/18191893/generate-pdf-from-html-in-div-using-javascript)

```html
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title></title>
    <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js"></script>
    <script type="text/javascript">
        $("#btnPrint").live("click", function () {
            var divContents = $("#dvContainer").html();
            var printWindow = window.open('', '', 'height=400,width=800');
            printWindow.document.write('<html><head><title>DIV Contents</title>');
            printWindow.document.write('</head><body >');
            printWindow.document.write(divContents);
            printWindow.document.write('</body></html>');
            printWindow.document.close();
            printWindow.print();
        });
    </script>
</head>
<body>
    <form id="form1">
    <div id="dvContainer">
        This content needs to be printed.
    </div>
    <input type="button" value="Print Div Contents" id="btnPrint" />
    </form>
</body>
</html>
```