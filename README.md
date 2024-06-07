# Editable Classic Report
![Smart JS Grid](https://github.com/PURAN-GITHUB/Smart_Grid_File/blob/main/IMAGE_FILE/smartjsgrid.jpg)
## Step1:
  >> Create a classic report
  ### Query:
  ```SQL
    SELECT * FROM(SELECT   STUDENT_ID, 
    APEX_ITEM.HIDDEN(1,STUDENT_ID)||
    APEX_ITEM.TEXT(2,FIRST_NAME,30,null,'class="form-control rb req"') FIRST_NAME, --'30'column-span
    APEX_ITEM.TEXT(3,LAST_NAME,30,null,'class="form-control rb req"') LAST_NAME,  
    APEX_ITEM.DATE_POPUP2(5,ADMISSION_DATE,'MON-DD-YYYY',30,null,'class="form-control rb"') ADMISSION_DATE,
    APEX_ITEM.TEXT(7,STATUS,30,null,'class="form-control rb req"') STATUS,
    'NULL' AS "Edit"
FROM STUDENT

UNION ALL
SELECT   NULL STUDENT_ID, 
    APEX_ITEM.TEXT(2,NULL,30,null,'class="form-control req"') FIRST_NAME, 
    APEX_ITEM.TEXT(3,NULL,30,null,'class="form-control req"') LAST_NAME,  
    APEX_ITEM.DATE_POPUP2(5,NULL,'MON-DD-YYYY',30,null,'class="form-control apex_disabled"') ADMISSION_DATE,
    APEX_ITEM.TEXT(7,STATUS,30,null,'class="form-control  req"') STATUS,
    NULL AS "Add"
FROM STUDENT
WHERE ROWNUM <= 1
)
ORDER BY STUDENT_ID desc nulls first
```      
## Step2: 
      All Columns type >> Parcent graph but Edit column type >> Plain text
      Go to Edit column >> Column Formating[HTML Expression] >> put this below code
![HTML Expression](https://github.com/PURAN-GITHUB/Smart_Grid_File/blob/main/IMAGE_FILE/HTML_Expression.jpg)
  ```html
    <span class="editableparent">
        <span id="ADDIGROW" class="addrowfa" onclick="AddRecord('STUDENT')">
            <i class="fa fa-plus" aria-hidden="true" title="Add Row"></i>
        </span>
        <span class="epone">
            <i class="fa fa-pencil-square-o editfa" aria-hidden="true" title="Edit Row"></i>
            <i onclick="DeleteRecord(#STUDENT_ID#,'Are you sure?','STUDENT')"class="fa fa-trash deletefa" aria-hidden="true" title="Delete Row"></i>
        </span>
        <span class="eptwo">
            <i id="UPR#STUDENT_ID#" onclick="UpdateRecord(#STUDENT_ID#,'UPR#STUDENT_ID#','STUDENT')" class="fa fa-check updatefa" aria-hidden="true" title="Update Row"></i>
            <i class="fa fa-times cancelfa" aria-hidden="true" title="Cancel"></i>
        </span>
    </span>
```
## Step3:
    Go to Share components >> Staic application file >> total 3 files dowload then upload on static application file [one CSS , two js file]
![Instruction](https://github.com/PURAN-GITHUB/Smart_Grid_File/blob/main/IMAGE_FILE/Instruction_img1.jpg)
    
   **CSS Files:** [Download](https://github.com/PURAN-GITHUB/CSS)
   
    1. FunctionConfigaration.css [Style property purose]
    2. FunctionConfigaration.js [Icon show/ hide, row editable/disable, item filed required etc.]
    3. Add_Update_Delete_Recors_js.js [Records insert,upadte & delete]

## Step4:
   >> Copy Reference url >> Return the page designer >> JavaScript [File url section paste the js file url] &&&  CSS [File url section paste the cdds file url]
  ![Instruction](dfdf)
## Step5:
## Step6:
