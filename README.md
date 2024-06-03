# Editable Classic Report
# Step1:
  >> Create a classic report
  # Query:
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
        
# Step2:
# Step3:
# Step4:
# Step5:
# Step6:
