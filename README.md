SELECT 
    PF. ID,
    PF.VendorCode,
    PF.VendorName,
    PF.PROC_MONTH,
    PF.WorkOrderNo,
    PF.WorkManCategory,
    PF.Basic_DA_Wages,
    PF.Department,
    PF.GrossWages,
    PF.NoOfDaysWorked,
    OW.LocationCode,
    LM.Location,
    EM.sex
FROM 
    App_PF_ESI_Details PF
LEFT JOIN 
    App_Online_Wages_Details OW 
    ON PF.VendorCode = OW.VendorCode AND PF.PROC_MONTH = OW.PROC_MONTH
LEFT JOIN 
    App_LocationMaster LM 
    ON OW.LocationCode = LM.LocationCode
LEFT JOIN 
    App_EmployeeMaster EM 
    ON PF.AadharCard = EM.AadharCard
WHERE 
    PF.PROC_MONTH = ''; -- Replace '' with your desired PROC_MONTH value
