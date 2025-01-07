SELECT concat(WG.YearWage, RIGHT('0' + cast(WG.MonthWage as varchar(2)),2)) as ProcMonth, WG.AadharNo, WG.VendorCode, WG.VendorName,
WG.WorkOrderNo, WG.LocationCode, WG.LocationNM, WG.WorkManCategory,
 WG.TotPaymentDays, WG.BasicWages,WG.DAWages,
 (WG.BasicWages + WG.DAWages + WG.HRA +  WG.OtherAllow ) As GrossWage ,
 WG.TotPaymentDays,
 EM.sex, OW.Department,WG.StateName from App_WagesDetailsJharkhand WG  where STATE_NAME='Jharkhand'


LEFT JOIN App_EmployeeMaster EM ON WG.AadharNo = EM.AadharCard AND WG.VendorCode = Em.VendorCode
LEFT JOIN App_Online_Wages_Details OW ON  WG.VendorCode = OW.VendorCode  AND WG.MonthWage = OW.MonthWage  AND WG.YearWage = OW.YearWage 
