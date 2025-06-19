---
{"notes":["3483373","2829521"],"tags":["SAP/Hana/Analytics/Platform","gardenEntry"],"dg-publish":true,"dg-home":true,"permalink":"/sap-business-one/notes/2502251-excel-report-and-interactive-analysis-connection-error/","dgPassFrontmatter":true}
---

## Issues
---
1. When attempting to connect to Interactive Analysis or using the SAP client menu to open an Excel Analysis report, Excel returns an error message indicating a failure to connect to the data source.
2. Excel crashes when opening a report via the SAP client.

> [!error] Initialisation of data source failed.

![20250221151813.png](/img/user/@Attached/20250221151813.png)
<div class="page-break" style="page-break-before: always;"></div>

## Cause
---
The issue occurs due to a bug in the HANA client when attempting to connect to the HANA database using the `SAP HANA MDX provider`. This provider is incompatible with the latest version of the **`oledb32.dll`** library.
<div class="page-break" style="page-break-before: always;"></div>

## Solution
---
1. Uninstall the current HANA client from the user's machine. Then, download and install the `SAP HANA Enterprise Edition 2.0 SPS 03 Rev.036`[¹][²].
2. Install `SAP HANA CLIENT FOR EXCEL 2.0 PL 21`[³].    
3. Replace the `SAPNewDBMDXProvider.dll` file located in:
    - **Source Path**: `C:\Program Files\SAP\SAP HANA Database Client for MS Excel`
    - **Destination Path**: `C:\Program Files\SAP\hdbclient`

> [!info] The files are available in [[1750243312.tar.gz]]
<div class="page-break" style="page-break-before: always;"></div>

## References
---
[3483373](https://me.sap.com/notes/3483373) - SAP Business One Excel Report and Interactive Analysis crashes after installing Microsoft u...
[2829521](https://me.sap.com/notes/2829521) - You Cannot Create New Pivot Tables in the Excel Report and Interactive Analysis Designer
<div class="page-break" style="page-break-before: always;"></div>

## Historic
---
- **`24/02/2025 - 00:00`** - #BP/FRF Opened a ticket with SAP under number[223999](https://userapps.support.sap.com/sap/bc/ui5_ui5/svt/sboi02/index.html?sbodsab=L000M000022399920250020751294%7C002).
- **`24/02/2025 - 00:00`** - #BP/VTC Implemented this solution on Viatec Server.
- **`18/06/2025 - 16:20`** - #BP/FRF Executed the instructions on Presentation Server.

## Footnotes
[¹] - Correction of system behaviour is not feasible in the currently supported versions of SAP Business One. The error has been recorded and is a candidate to be fixed in a future version.
[²] - The link to download the Hana client is available in sap notes [2829521](https://me.sap.com/notes/2829521). [[2829521 - You Cannot Create New Pivot Tables in the Excel Report and Interactive Analysis Designer.pdf|:BoBxsFilePdf:]]
[³] - The instructions on how to download are in the sap notes [3483373](https://me.sap.com/notes/3483373) .[[3483373 - SAP Business One Excel Report and Interactive Analysis crashes after installing Microsoft upgrade patches.pdf|:BoBxsFilePdf:]]