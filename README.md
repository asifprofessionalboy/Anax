SELECT 
    CONCAT(WG.YearWage, RIGHT('0' + CAST(WG.MonthWage AS VARCHAR(2)), 2)) AS ProcMonth, 
    WG.AadharNo, 
    WG.VendorCode, 
    WG.VendorName, 
    WG.WorkOrderNo, 
    WG.LocationCode, 
    WG.LocationNM, 
    WG.WorkManCategory, 
    WG.TotPaymentDays, 
    WG.BasicWages,
    WG.DAWages, 
    (WG.BasicWages + WG.DAWages + WG.HRA + WG.OtherAllow) AS GrossWage, 
    WG.TotPaymentDays, 
    EM.sex, 
    OW.Department, 
    WG.StateName
FROM 
    App_WagesDetailsJharkhand WG
LEFT JOIN 
    App_EmployeeMaster EM 
    ON WG.AadharNo = EM.AadharCard AND WG.VendorCode = EM.VendorCode
LEFT JOIN 
    App_Online_Wages_Details OW 
    ON WG.VendorCode = OW.VendorCode AND WG.MonthWage = OW.MonthWage AND WG.YearWage = OW.YearWage
WHERE 
    WG.StateName = 'Jharkhand';
