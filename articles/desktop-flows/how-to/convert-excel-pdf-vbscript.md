---
title: Convert Excel to PDF using VBScript | Microsoft Docs
description: Convert Excel to PDF using VBScript
author: georgiostrantzas
ms.service: power-automate
ms.subservice: desktop-flow
ms.topic: article
ms.date: 07/13/2021
ms.author: v-gtrantzas
ms.reviewer:
search.app: 
  - Flow
search.audienceType: 
  - flowmaker
  - enduser
---

# Convert Excel to PDF using VBScript

To convert an Excel file to PDF:

1. Use the **Set variable** action to create a new variable containing the path of the Excel file you want to convert. In this example, the variable is named **ExcelFile**.

    ![The Set variable action containing the Excel file path.](media/convert-excel-pdf-vbscript/set-variable-action-excel-file.png)

1. Use a second **Set variable** action to create a variable containing the path of the PDF file you want to create. In this example, the variable is named **PdfFile**.

    ![The Set variable action containing the pdf file path.](media/convert-excel-pdf-vbscript/set-variable-action-pdf-file.png)

1. Deploy the **Run VBScript** action and populate the following code. 

    ``` VBScript
    Dim Excel
    Dim ExcelDoc

    'Opens the Excel file'
    Set Excel = CreateObject("Excel.Application")
    Set ExcelDoc = Excel.Workbooks.open("%ExcelFilePath%")

    'Creates the pdf file'
    Excel.ActiveSheet.ExportAsFixedFormat 0, "%PdfFilePath%" ,0, 1, 0,,,0

    'Closes the Excel file'
    Excel.ActiveWorkbook.Close
    Excel.Application.Quit
    ```

    ![The configured Run VBScript action.](media/convert-excel-pdf-vbscript/run-vbscript-action.png)