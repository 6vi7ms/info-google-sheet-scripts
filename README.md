# Find string in other sheet
```js
function checkInAllSheets(cValue, dValue) {
  if (!cValue || !dValue) return "EMPTY";

  const clean = str => String(str).replace(/[\s\-\/]/g, "");  
  const cleanC = clean(cValue);
  const cleanD = clean(dValue);

  const currentSheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet().getName();
  const sheets = SpreadsheetApp.getActiveSpreadsheet().getSheets();

  for (let sheet of sheets) {
    if (sheet.getName() === currentSheet) continue;

    const cRange = sheet.getRange("C3:C100").getValues();
    const dRange = sheet.getRange("D3:D100").getValues();

    for (let i = 0; i < cRange.length; i++) {
      if (clean(cRange[i][0]) === cleanC && clean(dRange[i][0]) === cleanD) {
        return "ลงข้อมูลแล้ว";
      }
    }
  }

  return "";
}
```
