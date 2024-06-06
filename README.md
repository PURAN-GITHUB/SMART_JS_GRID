# Editable Classic Report
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
  ```html
      <html>
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
    </html>
```
## Step3:
    Go to Share components >> Staic application file >> total 3 file uploaded [one CSS , two js file] 
    1. FunctionConfigaration.css [Style property purose]
    2. FunctionConfigaration.js  [Icon show/ hide, row editable/disable, item filed required etc.]
    3. Add_Update_Delete_Recors_js.js [Records insert,upadte & delete]
  ### File1: FunctionConfigaration.css
      >> Copy this below code >> Go to Node pad ++ >> paste the code >> language change to css >> then save this file {File_name:: FunctionConfigaration.css} 
        ```html
        .t-Report-report .form-control{
              padding: 0px;
        }
        .t-Report-report .a-Button--calendar, .t-Report-report .a-Button--colorPicker, .t-Report-report .a-Button--listManager, .t-Report-report .a-Button--popupLOV {
          float: right;
          margin-top: -7px;
          margin-left: -25px;
          min-height: 27px;
        }
        #ADDIGROW .fa {
          font-size: 26px;
        }
        #ADDIGROW1 .fa {
          font-size: 26px;
        }
        #ADDIGROW2 .fa {
          font-size: 26px;
        }
        .eptwo{
            display:none;
        }
        .editableparent .fa{
            cursor: pointer;
            margin: 4px;
        }
        .ed {
          display: inline-flex;
          justify-content: center;
          margin: 0 auto;
          max-width: 60px;
        }
        .rb{
          border: none;
          background: transparent;
          pointer-events: none;
          cursor: not-allowed;
        }
        .rb ~ button {
          display: none;
        }
        
        .epone .editfa {
          color: #2f90b2;
          font-size: 20px;
          font-weight: bold;
        }
        .epone .deletefa {
          color: #d23a60;
          font-size: 20px;
          font-weight: bold;
        }
        .eptwo .updatefa {
          color: #00945f;
          font-size: 20px;
          font-weight: bold;
        }
        .eptwo .cancelfa {
          color: #d23a60;
          font-size: 20px;
          font-weight: bold;
        }
        #ADDIGROW .fa {
          font-size: 26px;
          color: #00945f;
          font-weight: bold;
        }
        
        #ADDIGROW1 .fa {
          font-size: 26px;
          color: #00945f;
          font-weight: bold;
        }
        #ADDIGROW2 .fa {
          font-size: 26px;
          color: #00945f;
          font-weight: bold;
        }
        
        .t-Report-report .a-Button--popupLOV {
          margin-top: 0px;
        }
        .red{
            border:1px solid red !important;
        }
        ```
    
## Step4:
## Step5:
## Step6:
