---
permalink: /revit-addins/
title: "Revit Add-ins"
---

## 📦RevXcel

Revit add-in that allows import/export of element parameters to Excel.

Works with Revit 2024.

<a href="https://github.com/bimAPIjourney/RevXcel/releases/download/1.0.1/RevXcel.exe" class="btn btn--info">Download</a>

## 🚀 Features

| Icon | Action | Description |
|-------|-------------|---------|
 <img src="https://github.com/user-attachments/assets/77ec44b7-ab31-46b0-946c-b049e8d80166" alt="revXcelExport" width="32" height="32"/> | **Export Parameters** | Export parameters from the selected Revit elements to Excel. |
<img src="https://github.com/user-attachments/assets/cf414da0-175d-436e-b021-69e2b4a3c921" alt="revXcelImport" width="32" height="32"/> | **Import from Excel** | Apply changes to element parameters from Excel. | 
<img src="https://github.com/user-attachments/assets/026abaf3-def5-46f4-8dd0-f28ce6e9ec6c" alt="revXcelMapping" width="32" height="32"/> | **Parameters Mapping Configuration** | Choose which parameters to export, per element category. | 
<img src="https://github.com/user-attachments/assets/579e12ba-a77c-4f31-9d40-931f362d7a8b" alt="revXcelParameters" width="32" height="32"/> | **Element Parameter Export** | Dump *all* parameters for selected elements to Excel. | 
<img src="https://github.com/user-attachments/assets/40b480ac-ffa8-4700-92aa-3af7e1a45a98" alt="revXcelSelect32" width="32" height="32"/> | **Element Selection from Clipboard** | Select Revit elements from Clipboard. | 

## 🧰 Workflow
  
<table>
 <tbody>
    <tr>
     <td style="width: 50px;"><img src="https://github.com/user-attachments/assets/579e12ba-a77c-4f31-9d40-931f362d7a8b" alt="revXcelParameters" width="32" height="32"/></td>
     <td><b>Export Parameters</b></td>
    </tr>
    <tr>
        <td colspan = "2" style="border: none;">Select an element of the category you are intersted in (Title Blocks, Sheets, Walls, Columns...) and click <mark><b>Export Parameters</b></mark>.</td>
    </tr>
     <tr>
        <td colspan = "2" style="border: none;" align="center"><img width="1310" height="860" alt="ExportParameters" src="https://github.com/user-attachments/assets/3cd5f825-cd22-462f-bfa0-13dcf03961be"/></td>
    </tr>
 <tr style="border: none;"><td style="border: none;"></td></tr>
     <tr>
      <td style="width: 50px;"><img src="https://github.com/user-attachments/assets/026abaf3-def5-46f4-8dd0-f28ce6e9ec6c" alt="revXcelMapping" width="32" height="32"/></td>
      <td><b>Mapping File</b></td>
    </tr>
    <tr>
      <td colspan = "2" style="border: none;">Click on <mark><b>Mapping File</b></mark> and add the element category name and the parameters you want to export (1 parameter per cell).</td>
    </tr>
     <tr>
      <td colspan = "2" style="border: none;" align="center"><img width="1310" height="860" alt="Mapping" src="https://github.com/user-attachments/assets/f56f6ef8-5f03-483d-8683-77bac726da01"/></td>
    </tr>
 <tr style="border: none;"><td style="border: none;"></td></tr>
      <tr>
       <td style="width:50px;"><img src="https://github.com/user-attachments/assets/77ec44b7-ab31-46b0-946c-b049e8d80166" alt="revXcelToExcel" width="32" height="32"/></td>
       <td><b>To Excel</b></td>
    </tr>
    <tr>
        <td colspan = "2" style="border: none;">Select the elements in Revit and click <mark><b>To Excel</b></mark> to export their parameters. Make sure the Excel file is closed before exporting to Excel.</td>
    </tr>
     <tr>
        <td colspan = "2" style="border: none;" align="center"><img width="1310" height="860" alt="ToExcel" src="https://github.com/user-attachments/assets/af76ae67-65ec-4bf1-92c7-37d24cc5353f" /></td>
    </tr>
 <tr style="border: none;"><td style="border: none;"></td></tr>
     <tr>
        <td style="width:10px;"> </td>
        <td><b>Edit parameters in Excel</b></td>
    </tr>
    <tr>
        <td colspan = "2" style="border: none;"> Change parameters values in Excel and save the file. Only non read-only parameters can be modified. Parameters must be of type string, number or integer (i.e. the addin does not support changing View Templates or other parameters stored as ElementId). </td>
    </tr>
     <tr>
        <td colspan = "2" style="border: none;" align="center"><img width="1310" height="860" alt="EditParameters" src="https://github.com/user-attachments/assets/f8e7d921-db24-4013-8dc7-2fea60fee7f7" /></td>
    </tr>
 <tr style="border: none;"><td style="border: none;"></td></tr>
      <tr>
        <td style="width:50px;"><img src="https://github.com/user-attachments/assets/cf414da0-175d-436e-b021-69e2b4a3c921" alt="revXcelImport" width="32" height="32"/></td>
        <td><b>From Excel</b></td>
    </tr>
    <tr>
        <td colspan = "2" style="border: none;">After saving the Excel file, click on <mark><b>From Excel</b></mark> to modify the previously selected element paramters.</td>
    </tr>
     <tr>
        <td colspan = "2" style="border: none;" align="center"><img width="1310" height="704" alt="FromExcel" src="https://github.com/user-attachments/assets/0f4398d1-3680-4540-818f-9418e5ee8687" /></td>
    </tr>
 <tr style="border: none;"><td style="border: none;"></td></tr>
      <tr>
        <td style="width:50px"><img src="https://github.com/user-attachments/assets/40b480ac-ffa8-4700-92aa-3af7e1a45a98" alt="revXcelSelect32" width="32" height="32"/></td>
        <td><b>Excel Selection</b></td>
    </tr>
    <tr>
        <td colspan = "2" style="border: none;">Select UniqueIds in Excel and press CTRL+C to save them in the Clipboard. In Revit, click on <mark><b>Excel Selection</b></mark> to add the elements to the active selection.</td>
    </tr>
     <tr>
        <td colspan = "2" style="border: none;" align="center"><img width="1310" height="860" alt="ExcelSelection" src="https://github.com/user-attachments/assets/a48f83c6-d673-43cc-bd7f-4b544291e852" /></td>
    </tr>
  </tbody>
</table>

